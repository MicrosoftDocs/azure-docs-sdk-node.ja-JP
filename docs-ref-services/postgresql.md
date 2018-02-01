---
title: "Node.js 用 Azure PostgreSQL モジュール"
description: "Node.js 用 Azure PostgreSQL モジュールのリファレンス"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: d8a2c7fe90746def7e50a7af3a0f470213eed197
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2018
---
# <a name="azure-postgresql-modules-for-nodejs"></a>Node.js 用 Azure PostgreSQL モジュール

Azure Database for PostgreSQL へのアクセスに推奨されるクライアント ライブラリは、オープンソースの [Azure Database for PostgreSQL 用 Node.js 接続ライブラリ](https://www.npmjs.com/package/pg)です。 このライブラリは Node.js 用の非ブロッキング PostgreSQL クライアントで、純粋な JavaScript をサポートするほか、オプションでネイティブの libpq バインディングをサポートします。

Azure Database for PostgreSQL の詳細については、[こちら](https://docs.microsoft.com/azure/postgresql/)を参照してください。

## <a name="client-package"></a>クライアント パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

PostgreSQL クライアント モジュールをインストールするには npm を使用します。

```bash
npm install pg
```   

### <a name="example"></a>例

この例では、クライアント接続を開いて、単純なクエリを実行します。

```javascript
const pg = require('pg');

const connectionString =
  'postgres://{username}@{server-name}:{password}@{server-name}.postgres.database.azure.com:5432/{database-name}?ssl=true';

const client = new pg.Client(connectionString);
client.connect();

const query = 'SELECT * FROM {table-name}';
client.query(query, (err, res) => {
  console.log(res);
});
```

## <a name="samples"></a>サンプル

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
