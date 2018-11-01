---
title: Node.js を使った Azure サービス プリンシパルの作成
description: Node.js でのサービス プリンシパル認証の方法について説明します。
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 98d52e21332138512d40ff2de9f5d3388fa596e4
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2018
ms.locfileid: "50406538"
---
# <a name="create-an-azure-service-principal-with-nodejs"></a><span data-ttu-id="dc82a-103">Node.js を使った Azure サービス プリンシパルの作成</span><span class="sxs-lookup"><span data-stu-id="dc82a-103">Create an Azure service principal with Node.js</span></span> 

<span data-ttu-id="dc82a-104">リソースへのアクセスを必要とするアプリには、ID を設定し、アプリをそれ自体の資格情報で認証できます。</span><span class="sxs-lookup"><span data-stu-id="dc82a-104">When an app needs to access resources, you can set up an identity for the app and authenticate the app with its own credentials.</span></span> <span data-ttu-id="dc82a-105">この ID は、"*サービス プリンシパル*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="dc82a-105">This identity is known as a *service principal*.</span></span> <span data-ttu-id="dc82a-106">ユーザーの介入やユーザー名/パスワードの入力を求めるのではなく、SDK に与える Azure Active Directory アカウントのキーを認証用に作成するのが基本的な原理となります。</span><span class="sxs-lookup"><span data-stu-id="dc82a-106">Essentially, you create keys for your Azure Active Directory account that you provide to the SDK to authenticate rather than requiring user intervention or username/password.</span></span>

<span data-ttu-id="dc82a-107">サービス プリンシパルを使ったアプローチによって次のことが可能となります。</span><span class="sxs-lookup"><span data-stu-id="dc82a-107">The service principal approach enables you to:</span></span>
- <span data-ttu-id="dc82a-108">ユーザー自身のアクセス許可とは異なるアクセス許可を、アプリケーション ID に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="dc82a-108">Assign permissions to the app identity that are different than your own permissions.</span></span> <span data-ttu-id="dc82a-109">通常、こうしたアクセス許可は、アプリが行う必要があることに制限されます。</span><span class="sxs-lookup"><span data-stu-id="dc82a-109">Typically, these permissions are restricted to exactly what the app needs to do.</span></span>
- <span data-ttu-id="dc82a-110">無人スクリプトを実行するときに、証明書を使用して認証できます。</span><span class="sxs-lookup"><span data-stu-id="dc82a-110">Use a certificate for authentication when running an unattended script.</span></span>

<span data-ttu-id="dc82a-111">このトピックでは、サービス プリンシパルを作成するための 3 つの手法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="dc82a-111">This topic shows you three techniques for creating a service principal.</span></span>

- <span data-ttu-id="dc82a-112">Azure ポータル</span><span class="sxs-lookup"><span data-stu-id="dc82a-112">Azure portal</span></span>
- <span data-ttu-id="dc82a-113">Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="dc82a-113">Azure CLI 2.0</span></span>
- <span data-ttu-id="dc82a-114">Azure SDK for Node.js</span><span class="sxs-lookup"><span data-stu-id="dc82a-114">Azure SDK for Node.js</span></span>

## <a name="create-a-service-principal-using-the-azure-portal"></a><span data-ttu-id="dc82a-115">Azure Portal を使用してサービス プリンシパルを作成する</span><span class="sxs-lookup"><span data-stu-id="dc82a-115">Create a service principal using the Azure portal</span></span>

<span data-ttu-id="dc82a-116">サービス プリンシパルの作成については、「[リソースにアクセスできる Azure Active Directory アプリケーションとサービス プリンシパルをポータルで作成する](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/)」のトピックで説明されている手順を参考にしてください。</span><span class="sxs-lookup"><span data-stu-id="dc82a-116">Follow the steps outlined in the topic, [Use portal to create an Azure Active Directory application and service principal that can access resources](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/), to generate the service principal.</span></span>

## <a name="create-a-service-principal-using-the-azure-cli-20"></a><span data-ttu-id="dc82a-117">Azure CLI 2.0 を使用してサービス プリンシパルを作成する</span><span class="sxs-lookup"><span data-stu-id="dc82a-117">Create a service principal using the Azure CLI 2.0</span></span>

<span data-ttu-id="dc82a-118">[Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) を使ってサービス プリンシパルを作成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="dc82a-118">Creating a service principal using the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) can be accomplished with the following steps:</span></span>

1. <span data-ttu-id="dc82a-119">[Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="dc82a-119">Download the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

2. <span data-ttu-id="dc82a-120">ターミナル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="dc82a-120">Open a terminal window.</span></span>

3. <span data-ttu-id="dc82a-121">次のコマンドを入力してログイン プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="dc82a-121">Type the following command to start the login process:</span></span>

    ```shell
    $ az login
    ```

4. <span data-ttu-id="dc82a-122">`az login` を呼び出すと、URL とコードが返されます。</span><span class="sxs-lookup"><span data-stu-id="dc82a-122">Calling `az login` results in a URL and a code.</span></span> <span data-ttu-id="dc82a-123">指定された URL にブラウザーでアクセスし、コードを入力して、自分の Azure ID でログインします (既にログインしている場合は自動的に実行されます)。</span><span class="sxs-lookup"><span data-stu-id="dc82a-123">Browse to the specified URL, enter the code, and login with your Azure identity (this may happen automatically if you're already logged in).</span></span> <span data-ttu-id="dc82a-124">その後は CLI から自分のアカウントにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="dc82a-124">You'll then be able to access your account via the CLI.</span></span>

5. <span data-ttu-id="dc82a-125">サブスクリプション ID とテナント ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="dc82a-125">Get your subscription and tenant id:</span></span>

    ```shell
    $ az account list
    ```

    <span data-ttu-id="dc82a-126">出力例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dc82a-126">The following shows an example of the output:</span></span>

    ```shell
    {
    "cloudName": "AzureCloud",
    "id": "<subscriptionId>",
    "isDefault": true,
    "name": "<subscriptionName>",
    "registeredProviders": [],
    "state": "Enabled",
    "tenantId": "<tenantId>",
        "user": {
            "name": "hello@example.com",
            "type": "user"
        }
    }
    ```

    <span data-ttu-id="dc82a-127">**サブスクリプション ID を書き留めてください。手順 7. で必要になります。**</span><span class="sxs-lookup"><span data-stu-id="dc82a-127">**Note the subscription ID as it will be used in Step 7.**</span></span>

6. <span data-ttu-id="dc82a-128">サービス プリンシパルを作成すると、Azure への認証に必要な他の情報を含んだ JSON オブジェクトが得られます。</span><span class="sxs-lookup"><span data-stu-id="dc82a-128">Create a service principal to get a JSON object containing the other pieces of information you need to authenticate with Azure.</span></span>

    ```shell
    $ az ad sp create-for-rbac
    ```

    <span data-ttu-id="dc82a-129">出力例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dc82a-129">The following shows an example of the output:</span></span>

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    <span data-ttu-id="dc82a-130">**テナント、名前、パスワードの値を書き留めてください。手順 7. で必要になります。**</span><span class="sxs-lookup"><span data-stu-id="dc82a-130">**Note the tenant, name, and password values as they'll be used in Step 7.**</span></span>

7. <span data-ttu-id="dc82a-131">環境変数を設定します。&lt;subscriptionId>、&lt;tenant>、&lt;name>、&lt;password> の各プレースホルダーには、手順 4. と手順 5. で得た値を指定してください。</span><span class="sxs-lookup"><span data-stu-id="dc82a-131">Set up the environment variables - replacing the &lt;subscriptionId>, &lt;tenant>, &lt;name>, and &lt;password> placeholders with the values you obtained in steps 4 and 5.</span></span> 

    <span data-ttu-id="dc82a-132">**bash の使用**</span><span class="sxs-lookup"><span data-stu-id="dc82a-132">**Using bash**</span></span>

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    <span data-ttu-id="dc82a-133">**PowerShell の使用**</span><span class="sxs-lookup"><span data-stu-id="dc82a-133">**Using PowerShell**</span></span>

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a><span data-ttu-id="dc82a-134">Azure SDK for Node.js を使用してサービス プリンシパルを作成する</span><span class="sxs-lookup"><span data-stu-id="dc82a-134">Create a service principal using the Azure SDK for Node.js</span></span>

<span data-ttu-id="dc82a-135">JavaScript を使ってプログラムでサービス プリンシパルを作成するには、[ServicePrincipal スクリプト](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal)を使用します。</span><span class="sxs-lookup"><span data-stu-id="dc82a-135">To programmatically create a service principal using JavaScript, use the [ServicePrincipal script](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span></span>   

## <a name="using-the-service-principal"></a><span data-ttu-id="dc82a-136">サービス プリンシパルの使用</span><span class="sxs-lookup"><span data-stu-id="dc82a-136">Using the service principal</span></span>

<span data-ttu-id="dc82a-137">次の JavaScript コード スニペットは、サービス プリンシパルの作成後、Azure SDK for Node.js でサービス プリンシパル キーを使って認証を行う方法を示したものです。</span><span class="sxs-lookup"><span data-stu-id="dc82a-137">Once you have a service principal, the following JavaScript code snippet illustrates how to use the service principal keys to authenticate with the Azure SDK for Node.js.</span></span> <span data-ttu-id="dc82a-138">&lt;clientId or appId>、&lt;secret or password>、&lt;domain or tenant> の各プレースホルダーには、実際の値を指定してください。</span><span class="sxs-lookup"><span data-stu-id="dc82a-138">Modify the following placeholders: &lt;clientId or appId>, &lt;secret or password>, and &lt;domain or tenant>,</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithServicePrincipalSecret(
  <clientId or appId>,
  <secret or password>,
  <domain or tenant>,
  (err, credentials) => {
    if (err) throw err

    let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

    // ..use the client instance to manage service resources.
  }
);
```
