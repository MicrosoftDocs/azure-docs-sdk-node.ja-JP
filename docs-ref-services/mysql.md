---
title: Node.js 用 Azure MySQL モジュール
description: Node.js 用 Azure MySQL モジュールのリファレンス
author: ajlam
ms.author: andrela
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 557645774ecb0ea5e774f99d03251a303ad19660
ms.sourcegitcommit: da60ea91d4215d738b1e0df82066f0fc337ad85a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2018
ms.locfileid: "47358781"
---
# <a name="azure-mysql-modules-for-nodejs"></a><span data-ttu-id="37861-103">Node.js 用 Azure MySQL モジュール</span><span class="sxs-lookup"><span data-stu-id="37861-103">Azure MySQL modules for Node.js</span></span>

<span data-ttu-id="37861-104">Azure Database for MySQL へのアクセスに推奨されるクライアント ライブラリは、オープンソースの [Azure Database for MySQL 用 Node.js 接続ライブラリ](https://github.com/sidorares/node-mysql2)です。</span><span class="sxs-lookup"><span data-stu-id="37861-104">The recommended client library for accessing Azure Database for MySQL is the open-source [Node.js connection library for Azure Database for MySQL](https://github.com/sidorares/node-mysql2).</span></span> 

<span data-ttu-id="37861-105">Azure Database for MySQL の詳細については、[こちら](https://docs.microsoft.com/azure/MySQL/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37861-105">Learn more about [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span></span>

## <a name="client-package"></a><span data-ttu-id="37861-106">クライアント パッケージ</span><span class="sxs-lookup"><span data-stu-id="37861-106">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="37861-107">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="37861-107">Install the npm module</span></span>

<span data-ttu-id="37861-108">MySQL クライアント モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="37861-108">Use npm to install the MySQL client module.</span></span>

```bash
npm install mysql2
```   

### <a name="example"></a><span data-ttu-id="37861-109">例</span><span class="sxs-lookup"><span data-stu-id="37861-109">Example</span></span>

<span data-ttu-id="37861-110">この例では、MySQL データベースに接続して、すべての顧客を取得する単純なクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="37861-110">This example connects to a MySQL database and performs a simple query to retrieve all customers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="37861-111">サンプル</span><span class="sxs-lookup"><span data-stu-id="37861-111">Samples</span></span>

[!INCLUDE [node-mysql-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

<span data-ttu-id="37861-112">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="37861-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
