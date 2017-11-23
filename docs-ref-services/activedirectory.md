---
title: "Node.js 用 Azure Active Directory モジュール"
description: "Node.js 用 Azure Active Directory モジュールのリファレンス"
keywords: "Azure, Node, SDK, API, ストレージ, nodejs, javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: d0084faa78986bd5518526c6eb84b9c13fdb10bf
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="9e023-104">Node.js 用 Azure Active Directory モジュール</span><span class="sxs-lookup"><span data-stu-id="9e023-104">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="9e023-105">概要</span><span class="sxs-lookup"><span data-stu-id="9e023-105">Overview</span></span>

<span data-ttu-id="9e023-106">Node.js アプリケーションで AAD に対して認証を行い、AAD によって保護された Web リソースにアクセスするには、[Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) を使用します。</span><span class="sxs-lookup"><span data-stu-id="9e023-106">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="9e023-107">クライアント パッケージ</span><span class="sxs-lookup"><span data-stu-id="9e023-107">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="9e023-108">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="9e023-108">Install the npm modules</span></span>

<span data-ttu-id="9e023-109">Azure Storage クライアントまたは管理モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="9e023-109">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="9e023-110">例</span><span class="sxs-lookup"><span data-stu-id="9e023-110">Example</span></span>

<span data-ttu-id="9e023-111">この例は、[クライアント資格情報サンプル](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js)からの抜粋で、クライアントの資格情報を使ってサーバー間の認証を行います。</span><span class="sxs-lookup"><span data-stu-id="9e023-111">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

```javascript
const adal = require('adal-node').AuthenticationContext;

const authorityHostUrl = 'https://login.windows.net';
const tenant = 'your-tenant-id';
const authorityUrl = authorityHostUrl + '/' + tenant;
const clientId = 'your-client-id';
const clientSecret = 'your-client-secret';
const resource = 'your-app-id-uri';

const context = new adal(authorityUrl);

context.acquireTokenWithClientCredentials(
  resource,
  clientId,
  clientSecret,
  (err, tokenResponse) => {
    if (err) {
      console.log(`Token generation failed due to ${err}`);
    } else {
      console.dir(tokenResponse, { depth: null, colors: true });
    }
  }
);
```

## <a name="samples"></a><span data-ttu-id="9e023-112">サンプル</span><span class="sxs-lookup"><span data-stu-id="9e023-112">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="9e023-113">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="9e023-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
