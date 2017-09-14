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
# <a name="azure-active-directory-modules-for-nodejs"></a>Node.js 用 Azure Active Directory モジュール

## <a name="overview"></a>概要

Node.js アプリケーションで AAD に対して認証を行い、AAD によって保護された Web リソースにアクセスするには、[Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) を使用します。

## <a name="client-package"></a>クライアント パッケージ

### <a name="install-the-npm-modules"></a>npm モジュールのインストール

Azure Storage クライアントまたは管理モジュールをインストールするには npm を使用します。

```bash
npm install adal-node
```   

### <a name="example"></a>例

この例は、[クライアント資格情報サンプル](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js)からの抜粋で、クライアントの資格情報を使ってサーバー間の認証を行います。

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

## <a name="samples"></a>サンプル

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
