---
title: Node.js 用 Azure Redis Cache モジュール
description: Node.js 用 Azure Redis Cache モジュールのリファレンス
author: wesmc7777
ms.author: wesmc
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: afeee19cb79b54561b6cbef4a79de8b1606adb4d
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265063"
---
# <a name="azure-redis-cache-modules-for-nodejs"></a>Node.js 用 Azure Redis Cache モジュール

Azure Redis Cache は広く普及しているオープン ソースの Redis プロジェクトを基盤にしています。 これを使用すると、Microsoft によって管理されている、セキュリティで保護された専用 Redis インスタンスに、ご利用の Azure アプリでアクセスできます。

Redis は高度なキーと値のストアです。キーには、文字列、ハッシュ、リスト、セット、ソート済みセットなどのデータ構造を格納できます。 Redis では、このようなデータ型に対する一連のアトミック操作がサポートされています。

Azure Redis Cache の詳細については、[こちら](https://docs.microsoft.com/azure/redis-cache/)を参照してください。

## <a name="client-package"></a>クライアント パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Node.js 用 Redis モジュールをインストールするには npm を使用します。

```bash
npm install redis
```

### <a name="example"></a>例

この例では、Azure Redis Cache インスタンスに接続してキー/値のペアを保存した後、そのキーで、保存されている値を読み取ります。

```javascript
const redis = require('redis');

const client = redis.createClient(6380, '<name>.redis.cache.windows.net', {
  auth_pass: '<key>',
  tls: { servername: '<name>.redis.cache.windows.net' }
});

client.set('key1', 'value', (err, reply) => {
  console.log(reply);
});

client.get('key1', (err, reply) => {
  console.log(reply);
});
```

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Node.js 用 Azure Redis Cache モジュールをインストールするには npm を使用します。

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a>例

この例では、Azure に対して認証を行い、指定したリソース グループに含まれるすべての Redis Cache インスタンスをリストします。

```javascript
const msRestAzure = require('ms-rest-azure');
const AzureMgmtRedisCache = require('azure-arm-rediscache');

msRestAzure.interactiveLogin().then(credentials => {
  const client = new AzureMgmtRedisCache(credentials, 'my-subscription-id');
  client.redis.listByResourceGroup('testResourceGroup').then(result => {
    console.log(result);
  });
});
```


## <a name="samples"></a>サンプル

* [Node.js で Azure Redis Cache を使用する方法](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
