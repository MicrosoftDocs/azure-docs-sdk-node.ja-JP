---
title: Node.js 用 Azure SQL モジュール
description: Node.js 用 Azure SQL モジュールのリファレンス
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: sql-database
ms.subservice: development
ms.openlocfilehash: 00ba5984b5f8aef85570c54f23efefd1d741ca57
ms.sourcegitcommit: 0e294f7c4dcdfae9df18ff3e82b6563680ef2519
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55046432"
---
# <a name="azure-sql-modules-for-nodejs"></a>Node.js 用 Azure SQL モジュール

[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) に格納されているデータを Node.js から操作します。
Microsoft Azure SQL データベースを簡単に管理できるインターフェイスが管理ライブラリに用意されています。

## <a name="client-package"></a>クライアント パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

SQL Server クライアントの npm モジュールをインストールします。

```bash
npm install tedious
```

### <a name="example"></a>例

この例では、SQL Server データベースに接続して単純なクエリを実行します。

```javascript
const Connection = require('tedious').Connection;
const Request = require('tedious').Request;

const config = {
  userName: 'your-username',
  password: 'your-password',
  server: 'path-to-server',
  options: {
    database: 'database-name',
    encrypt: true
  }
};

const connection = new Connection(config);
connection.on('connect', err => {
  err ? console.log(err) : executeStatement();
});

const query = 'SELECT * from TableName';
const executeStatement = () => {
  const request = new Request(query, (err, rowCount) => {
    err ? console.log(err) : console.log(rowCount);
  });

  request.on('row', columns => {
    columns.forEach(column => console.log(column.value));
  });

  connection.execSql(request);
};
```

## <a name="management-package"></a>管理パッケージ

### <a name="install-npm-modules"></a>npm モジュールのインストール

Azure SQL Server 管理の npm モジュールをインストールします。

```
npm install azure-arm-sql
```   

### <a name="example"></a>例

認証を行ってクライアントを作成し、すべてのサーバーを一覧表示します。

```javascript
const msRestAzure = require('ms-rest-azure');
const SQLManagement = require('azure-arm-sql');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SQLManagement(credentials, 'your-subscription-id');
    return client.servers.list();
  })
  .then(servers => console.dir(servers, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>サンプル

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
