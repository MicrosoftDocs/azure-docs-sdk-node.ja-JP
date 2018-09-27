---
title: Node.js 用 Azure Active Directory モジュール
description: Node.js 用 Azure Active Directory モジュールのリファレンス
author: celestedg
ms.author: celested
manager: mtillman
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.openlocfilehash: 1189bf084fc7d77a1e5eed7f01f2f9bee2295b45
ms.sourcegitcommit: da60ea91d4215d738b1e0df82066f0fc337ad85a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2018
ms.locfileid: "47292951"
---
# <a name="azure-active-directory-modules-for-nodejs"></a>Node.js 用 Azure Active Directory モジュール

## <a name="overview"></a>概要

> [!IMPORTANT]
> Azure Active Directory リソースにアクセスする場合、Azure AD Graph API ではなく [Microsoft Graph](https://graph.microsoft.io/) を使用することを強くお勧めします。 開発作業は現在 Microsoft Graph に集中しており、Azure AD Graph API の追加の機能強化は予定されていません。 Azure AD Graph API の使用が適切なシナリオの数は非常に限られています。詳しくは、Office デベロッパー センターのブログ投稿「[Microsoft Graph or the Azure AD Graph (Microsoft Graph または Azure AD Graph)](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph)」をご覧ください。

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
