---
title: "Node.js 用 Azure MySQL モジュール"
description: "Node.js 用 Azure MySQL モジュールのリファレンス"
keywords: "Azure, Node, SDK, API, nodejs, javascript, データベース, MySQL"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 3efc0fcccb7cb01711ad1ce98e9ff9a2d87b77fe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-mysql-modules-for-nodejs"></a>Node.js 用 Azure MySQL モジュール

## <a name="overview"></a>概要

Azure Database for MySQL へのアクセスに推奨されるクライアント ライブラリは、オープンソースの [Azure Database for MySQL 用 Node.js 接続ライブラリ](https://github.com/sidorares/node-mysql2)です。 

Azure Database for MySQL の詳細については、[こちら](https://docs.microsoft.com/azure/MySQL/)を参照してください。

## <a name="client-package"></a>クライアント パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

MySQL クライアント モジュールをインストールするには npm を使用します。

```bash
npm install mysql2
```   

### <a name="example"></a>例

この例では、MySQL データベースに接続して、すべての顧客を取得する単純なクエリを実行します。

```javascript
const mysql = require('mysql2');

const connection = mysql.createConnection({
  host: 'mysqldemo.mysql.database.azure.com',
  user: 'myadmin@mysqldemo',
  password: 'your_password',
  database: 'my_db',
  port: 3306,
  ssl: true
});

connection.connect();
const query = 'SELECT * FROM customers';
connection.query(query, (err, res) =>
  console.log(`We have ${res.length} customers`)
);

connection.end();
```

## <a name="samples"></a>サンプル

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
