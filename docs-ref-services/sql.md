---
title: "Node.js 用 Azure SQL モジュール"
description: "Node.js 用 Azure SQL モジュールのリファレンス"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: sql-database
ms.openlocfilehash: 8ebcfbcbf39def1774a702c9f18a4e3f5ab86931
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2018
---
# <a name="azure-sql-modules-for-nodejs"></a><span data-ttu-id="b0d4d-103">Node.js 用 Azure SQL モジュール</span><span class="sxs-lookup"><span data-stu-id="b0d4d-103">Azure SQL modules for Node.js</span></span>

<span data-ttu-id="b0d4d-104">[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) に格納されているデータを Node.js から操作します。</span><span class="sxs-lookup"><span data-stu-id="b0d4d-104">Work with data stored in [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) from Node.js.</span></span>
<span data-ttu-id="b0d4d-105">Microsoft Azure SQL データベースを簡単に管理できるインターフェイスが管理ライブラリに用意されています。</span><span class="sxs-lookup"><span data-stu-id="b0d4d-105">The management library provides an interface to make it easy to manage Microsoft Azure SQL databases.</span></span>

## <a name="client-package"></a><span data-ttu-id="b0d4d-106">クライアント パッケージ</span><span class="sxs-lookup"><span data-stu-id="b0d4d-106">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b0d4d-107">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="b0d4d-107">Install the npm module</span></span>

<span data-ttu-id="b0d4d-108">SQL Server クライアントの npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="b0d4d-108">Install the SQL Server client npm module</span></span>

```bash
npm install tedious
```

### <a name="example"></a><span data-ttu-id="b0d4d-109">例</span><span class="sxs-lookup"><span data-stu-id="b0d4d-109">Example</span></span>

<span data-ttu-id="b0d4d-110">この例では、SQL Server データベースに接続して単純なクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="b0d4d-110">This example connects to a SQL Server database and perform a simple query.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="b0d4d-111">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="b0d4d-111">Management package</span></span>

### <a name="install-npm-modules"></a><span data-ttu-id="b0d4d-112">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="b0d4d-112">Install npm modules</span></span>

<span data-ttu-id="b0d4d-113">Azure SQL Server 管理の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="b0d4d-113">Install the Azure SQL Server management npm module</span></span>

```
npm install azure-arm-sql
```   

### <a name="example"></a><span data-ttu-id="b0d4d-114">例</span><span class="sxs-lookup"><span data-stu-id="b0d4d-114">Example</span></span>

<span data-ttu-id="b0d4d-115">認証を行ってクライアントを作成し、すべてのサーバーを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="b0d4d-115">Authenticate, create a client, and list all servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b0d4d-116">サンプル</span><span class="sxs-lookup"><span data-stu-id="b0d4d-116">Samples</span></span>

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

<span data-ttu-id="b0d4d-117">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="b0d4d-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
