---
title: Node.js 用 Azure PostgreSQL モジュール
description: Node.js 用 Azure PostgreSQL モジュールのリファレンス
author: rachel-msft
ms.author: raagyema
manager: sukamat
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: ed9373b767684e4893ca84de1030d062178b7ea4
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51465696"
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
