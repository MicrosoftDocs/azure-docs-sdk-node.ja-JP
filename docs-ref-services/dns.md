---
title: "Node.js 用 Azure DNS モジュール"
description: "Node.js 用 Azure DNS モジュールのリファレンス"
keywords: Azure,SDK,API,DNS, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 679c2d494b99244961f2fee61b0813c81eb8a8de
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-dns-modules-for-nodejs"></a>Node.js 用 Azure DNS モジュール

## <a name="overview"></a>概要

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
