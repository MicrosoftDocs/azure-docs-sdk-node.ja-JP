---
title: Node.js 用 Azure DNS モジュール
description: Node.js 用 Azure DNS モジュールのリファレンス
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 93eec1890fc15d19c0545086a53b751d0886988a
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2018
ms.locfileid: "50324269"
---
# <a name="azure-dns-modules-for-nodejs"></a>Node.js 用 Azure DNS モジュール

Azure DNS を使用して、お客様のドメイン ネーム システム (DNS) を Azure でホストしましょう。 他の Azure サービスと同じ資格情報、支払い方法、サポート契約で DNS レコードを管理します。 Azure ベースのサービスと対応する DNS 更新とをシームレスに統合し、エンドツーエンドのデプロイ プロセスを効率化できます。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure DNS の npm モジュールをインストールします。

```bash
npm install azure-arm-dns
```

### <a name="example"></a>例

この例では、DNS 管理ゾーンを一覧表示します。

```javascript
const msRestAzure = require('ms-rest-azure');
const DNSManagement = require('azure-arm-dns');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DNSManagement(credentials, subscriptionId);
    return client.zones.list();
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
