---
title: "Node.js 用 Azure 管理モジュールを使った認証"
description: "Node.js 用 Azure 管理モジュールへの認証にサービス プリンシパルを使う方法について説明します。"
author: craigshoemaker
manager: routlaw
ms.author: cshoe
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: c93e5205c43c78d1c9e94d59a362cda336cd8310
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2018
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="eaa2e-103">Node.js 用 Azure モジュールを使った認証</span><span class="sxs-lookup"><span data-stu-id="eaa2e-103">Authenticate with the Azure modules for Node.js</span></span> 

<span data-ttu-id="eaa2e-104">すべてのサービス API は、インスタンス化する際に、`credentials` オブジェクトを介して認証を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="eaa2e-104">All service APIs require authentication via a `credentials` object when being instantiated.</span></span> <span data-ttu-id="eaa2e-105">必要な資格情報を Azure SDK for Node.js で認証したり作成したりするには、次の 3 とおりの方法があります。</span><span class="sxs-lookup"><span data-stu-id="eaa2e-105">There are three ways of authenticating and creating the required credentials via the Azure SDK for Node.js:</span></span> 

- <span data-ttu-id="eaa2e-106">基本認証</span><span class="sxs-lookup"><span data-stu-id="eaa2e-106">Basic authentication</span></span>
- <span data-ttu-id="eaa2e-107">対話型ログイン</span><span class="sxs-lookup"><span data-stu-id="eaa2e-107">Interactive login</span></span>
- <span data-ttu-id="eaa2e-108">サービス プリンシパルの認証</span><span class="sxs-lookup"><span data-stu-id="eaa2e-108">Service principal authentication</span></span>

## <a name="basic-authentication"></a><span data-ttu-id="eaa2e-109">基本認証</span><span class="sxs-lookup"><span data-stu-id="eaa2e-109">Basic authentication</span></span>

<span data-ttu-id="eaa2e-110">Azure アカウントの資格情報を使ってプログラムで認証するには、`loginWithUsernamePassword` 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="eaa2e-110">To programmatically authenticate using your Azure account credentials, use the `loginWithUsernamePassword` function.</span></span> <span data-ttu-id="eaa2e-111">次の JavaScript コード スニペットは、環境変数として格納された資格情報を使った基本認証の方法を示したものです。</span><span class="sxs-lookup"><span data-stu-id="eaa2e-111">The following JavaScript code snippet illustrates how to use basic authentication using credentials that are stored as environment variables.</span></span> 

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

## <a name="interactive-login"></a><span data-ttu-id="eaa2e-112">対話型ログイン</span><span class="sxs-lookup"><span data-stu-id="eaa2e-112">Interactive login</span></span>

<span data-ttu-id="eaa2e-113">対話型ログインでは、ユーザーがブラウザーから認証を行うためのリンクとコードが提供されます。</span><span class="sxs-lookup"><span data-stu-id="eaa2e-113">Interactive login provides a link and a code that allows the user to authenticate from a browser.</span></span> <span data-ttu-id="eaa2e-114">この方法は、同じスクリプトで複数のアカウントが使用される場合や、ユーザーが介入した方が望ましい状況で使用します。</span><span class="sxs-lookup"><span data-stu-id="eaa2e-114">Use this method when multiple accounts are used by the same script or when user intervention is preferred.</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a><span data-ttu-id="eaa2e-115">サービス プリンシパルの認証</span><span class="sxs-lookup"><span data-stu-id="eaa2e-115">Service principal authentication</span></span>

<span data-ttu-id="eaa2e-116">認証方法としては、[対話型ログイン](#interactive-login)が最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="eaa2e-116">[Interactive login](#interactive-login) is the easiest way to authenticate.</span></span> <span data-ttu-id="eaa2e-117">ただし、Node.js SDK を使うときは、アカウントの資格情報を提供するよりも、サービス プリンシパル認証を使った方がよい場合もあります。</span><span class="sxs-lookup"><span data-stu-id="eaa2e-117">However, when using the Node.js SDK, you may want to use service principal authentication rather than providing your account credentials.</span></span> <span data-ttu-id="eaa2e-118">サービス プリンシパルの作成 (および使用) に関するさまざまな手法については、「[Node.js を使った Azure サービス プリンシパルの作成](./node-sdk-azure-authenticate-principal.md)」というトピックで説明しています。</span><span class="sxs-lookup"><span data-stu-id="eaa2e-118">The topic, [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md), explains various techniques for creating (and using) a service principal.</span></span> 