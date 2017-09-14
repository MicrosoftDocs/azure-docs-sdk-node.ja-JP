---
title: "Node.js 用 Azure 管理モジュールを使った認証"
description: "Node.js 用 Azure 管理モジュールへの認証にサービス プリンシパルを使う方法について説明します。"
keywords: "Azure, Node, SDK, API, 認証, active directory, サービス プリンシパル"
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 3ad1f17435844852838d01115ad8326f141aa73c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="e5d11-104">Node.js 用 Azure モジュールを使った認証</span><span class="sxs-lookup"><span data-stu-id="e5d11-104">Authenticate with the Azure modules for Node.js</span></span> 

<span data-ttu-id="e5d11-105">すべてのサービス API は、インスタンス化する際に、`credentials` オブジェクトを介して認証を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5d11-105">All service APIs require authentication via a `credentials` object when being instantiated.</span></span> <span data-ttu-id="e5d11-106">必要な資格情報を Azure SDK for Node.js で認証したり作成したりするには、次の 3 とおりの方法があります。</span><span class="sxs-lookup"><span data-stu-id="e5d11-106">There are three ways of authenticating and creating the required credentials via the Azure SDK for Node.js:</span></span> 

- <span data-ttu-id="e5d11-107">基本認証</span><span class="sxs-lookup"><span data-stu-id="e5d11-107">Basic authentication</span></span>
- <span data-ttu-id="e5d11-108">対話型ログイン</span><span class="sxs-lookup"><span data-stu-id="e5d11-108">Interactive login</span></span>
- <span data-ttu-id="e5d11-109">サービス プリンシパルの認証</span><span class="sxs-lookup"><span data-stu-id="e5d11-109">Service principal authentication</span></span>

## <a name="basic-authentication"></a><span data-ttu-id="e5d11-110">基本認証</span><span class="sxs-lookup"><span data-stu-id="e5d11-110">Basic authentication</span></span>

<span data-ttu-id="e5d11-111">Azure アカウントの資格情報を使ってプログラムで認証するには、`loginWithUsernamePassword` 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="e5d11-111">To programmatically authenticate using your Azure account credentials, use the `loginWithUsernamePassword` function.</span></span> <span data-ttu-id="e5d11-112">次の JavaScript コード スニペットは、環境変数として格納された資格情報を使った基本認証の方法を示したものです。</span><span class="sxs-lookup"><span data-stu-id="e5d11-112">The following JavaScript code snippet illustrates how to use basic authentication using credentials that are stored as environment variables.</span></span> 

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithUsernamePassword(process.env.AZURE_USER, 
                                 process.env.AZURE_PASS, 
                                 (err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, 
                                                             '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="interactive-login"></a><span data-ttu-id="e5d11-113">対話型ログイン</span><span class="sxs-lookup"><span data-stu-id="e5d11-113">Interactive login</span></span>

<span data-ttu-id="e5d11-114">対話型ログインでは、ユーザーがブラウザーから認証を行うためのリンクとコードが提供されます。</span><span class="sxs-lookup"><span data-stu-id="e5d11-114">Interactive login provides a link and a code that allows the user to authenticate from a browser.</span></span> <span data-ttu-id="e5d11-115">この方法は、同じスクリプトで複数のアカウントが使用される場合や、ユーザーが介入した方が望ましい状況で使用します。</span><span class="sxs-lookup"><span data-stu-id="e5d11-115">Use this method when multiple accounts are used by the same script or when user intervention is preferred.</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a><span data-ttu-id="e5d11-116">サービス プリンシパルの認証</span><span class="sxs-lookup"><span data-stu-id="e5d11-116">Service principal authentication</span></span>

<span data-ttu-id="e5d11-117">認証方法としては、[対話型ログイン](#interactive-login)が最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="e5d11-117">[Interactive login](#interactive-login) is the easiest way to authenticate.</span></span> <span data-ttu-id="e5d11-118">ただし、Node.js SDK を使うときは、アカウントの資格情報を提供するよりも、サービス プリンシパル認証を使った方がよい場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e5d11-118">However, when using the Node.js SDK, you may want to use service principal authentication rather than providing your account credentials.</span></span> <span data-ttu-id="e5d11-119">サービス プリンシパルの作成 (および使用) に関するさまざまな手法については、「[Node.js を使った Azure サービス プリンシパルの作成](./node-sdk-azure-authenticate-principal.md)」というトピックで説明しています。</span><span class="sxs-lookup"><span data-stu-id="e5d11-119">The topic, [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md), explains various techniques for creating (and using) a service principal.</span></span> 