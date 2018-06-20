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
ms.openlocfilehash: 610bc878acba978b7be25ea2caee4000cef3b452
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262219"
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
