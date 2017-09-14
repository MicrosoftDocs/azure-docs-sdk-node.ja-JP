---
title: "Node.js 用 Azure Cosmos DB モジュール"
description: "Node.js 用 Azure Cosmos DB モジュールのリファレンス"
keywords: Azure,SDK,API,Cosmos DB, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 1f545f89b5304b611dbe1ed9cb86052c112f13c1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a>Node.js 用 Azure Cosmos DB モジュール

## <a name="overview"></a>概要

Azure Cosmos DB は、Microsoft のグローバルに分散されたマルチモデル データベース サービスです。 Azure Cosmos DB では、Azure のリージョンをいくつでもまたいでスループットとストレージを柔軟かつ個別にスケーリングすることができます。 このサービスは包括的なサービス レベル アグリーメント (SLA) により、スループット、待ち時間、可用性、整合性が保証されています。この点は、他のどのデータベース サービスにもないメリットです。

Azure Cosmos DB は、書き込みのために最適化され、リソースが管理され、スキーマに関係なく使えるデータベース エンジンを採用しており、キーと値、ドキュメント、グラフ、列指向の 4 つのデータ モデルをネイティブでサポートしています。 また、MongoDB、DocumentDB SQL、Gremlin (プレビュー)、Azure Tables (プレビュー) など、データにアクセスするためのさまざまな API による拡張もサポートしています。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール 

Azure Cosmos DB の npm モジュールをインストールします。

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a>例

この例では、すべての Cosmos DB アカウントを一覧表示します。

```javascript
const msRestAzure = require('ms-rest-azure');
const documentDBManagementClient = require('azure-arm-documentdb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const documentDbClient = new documentDBManagementClient(credentials, subscriptionId);
  documentDbClient.databaseAccounts
    .list()
    .then(databaseAccounts => console.log('Retrieved database accounts: ', databaseAccounts));
});
```

## <a name="samples"></a>サンプル

* [Azure Cosmos DB の DocumentDB を使用して Node.js アプリを開発する](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [Azure Cosmos DB の Gremlin を使用して Node.js アプリを開発する](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
