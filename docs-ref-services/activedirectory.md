---
title: "Node.js 用 Azure Active Directory モジュール"
description: "Node.js 用 Azure Active Directory モジュールのリファレンス"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: 59ef5321db6e5e7f3ad0e3b63aaa6a107207d3c2
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2018
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="a57c0-103">Node.js 用 Azure Active Directory モジュール</span><span class="sxs-lookup"><span data-stu-id="a57c0-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="a57c0-104">概要</span><span class="sxs-lookup"><span data-stu-id="a57c0-104">Overview</span></span>

<span data-ttu-id="a57c0-105">Node.js アプリケーションで AAD に対して認証を行い、AAD によって保護された Web リソースにアクセスするには、[Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) を使用します。</span><span class="sxs-lookup"><span data-stu-id="a57c0-105">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="a57c0-106">クライアント パッケージ</span><span class="sxs-lookup"><span data-stu-id="a57c0-106">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="a57c0-107">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="a57c0-107">Install the npm modules</span></span>

<span data-ttu-id="a57c0-108">Azure Storage クライアントまたは管理モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="a57c0-108">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="a57c0-109">例</span><span class="sxs-lookup"><span data-stu-id="a57c0-109">Example</span></span>

<span data-ttu-id="a57c0-110">この例は、[クライアント資格情報サンプル](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js)からの抜粋で、クライアントの資格情報を使ってサーバー間の認証を行います。</span><span class="sxs-lookup"><span data-stu-id="a57c0-110">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

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

## <a name="samples"></a><span data-ttu-id="a57c0-111">サンプル</span><span class="sxs-lookup"><span data-stu-id="a57c0-111">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="a57c0-112">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="a57c0-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
