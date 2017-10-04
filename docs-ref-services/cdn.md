---
title: "Node.js 用 Azure CDN モジュール"
description: "Node.js 用 Azure CDN モジュールのリファレンス"
keywords: Azure,SDK,API,CDN, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: ae44606510037fa3ba3d5b95196a40f8eeef3afe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cdn-modules-for-nodejs"></a>Node.js 用 Azure CDN モジュール

## <a name="overview"></a>概要

Azure Content Delivery Network (CDN) は、Azure または他の任意の場所でホストされている高帯域幅コンテンツを配信するためのグローバル ソリューションを開発者に提供します。 CDN を使用すると、Azure BLOB ストレージ、Web アプリケーション、仮想マシン、アプリケーション フォルダー、またはその他の HTTP/HTTPS の場所から読み込んだ一般公開されているオブジェクトをキャッシュすることができます。 CDN のキャッシュを戦略的な場所に配置することで、ユーザーへのコンテンツ配信に最大限の帯域幅を提供することができます。 CDN は、通常、イメージ、スタイル シート、ドキュメント、ファイル、クライアント側スクリプトでは、HTML ページなどの静的コンテンツの配信に使用されます。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure CDN の npm モジュールをインストールします。

```bash
npm install azure-arm-cdn
```

### <a name="example"></a>例

この例では、すべての CDN プロファイルを一覧表示します。

```javascript
const msRestAzure = require('ms-rest-azure');
const cdnManagementClient = require('azure-arm-cdn');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const cdnClient = new cdnManagementClient(credentials, subscriptionId);
  cdnClient.profiles
    .list()
    .then(profilesList => console.log('Retrieved profiles list: ', profilesList));
});
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。