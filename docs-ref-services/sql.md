---
title: "Node.js 用 Azure SQL モジュール"
description: "Node.js 用 Azure SQL モジュールのリファレンス"
keywords: Azure, Node, SDK, API, nodejs, javascript, sql
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: sql-database
ms.openlocfilehash: 65ee90b4e6ca248b9d19a3685163211ca547cad4
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-sql-modules-for-nodejs"></a><span data-ttu-id="51301-104">Node.js 用 Azure SQL モジュール</span><span class="sxs-lookup"><span data-stu-id="51301-104">Azure SQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="51301-105">概要</span><span class="sxs-lookup"><span data-stu-id="51301-105">Overview</span></span>

<span data-ttu-id="51301-106">[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) に格納されているデータを Node.js から操作します。</span><span class="sxs-lookup"><span data-stu-id="51301-106">Work with data stored in [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) from Node.js.</span></span>
<span data-ttu-id="51301-107">Microsoft Azure SQL データベースを簡単に管理できるインターフェイスが管理ライブラリに用意されています。</span><span class="sxs-lookup"><span data-stu-id="51301-107">The management library provides an interface to make it easy to manage Microsoft Azure SQL databases.</span></span>

## <a name="client-package"></a><span data-ttu-id="51301-108">クライアント パッケージ</span><span class="sxs-lookup"><span data-stu-id="51301-108">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="51301-109">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="51301-109">Install the npm module</span></span>

<span data-ttu-id="51301-110">SQL Server クライアントの npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="51301-110">Install the SQL Server client npm module</span></span>

```bash
npm install tedious
```

### <a name="example"></a><span data-ttu-id="51301-111">例</span><span class="sxs-lookup"><span data-stu-id="51301-111">Example</span></span>

<span data-ttu-id="51301-112">この例では、SQL Server データベースに接続して単純なクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="51301-112">This example connects to a SQL Server database and perform a simple query.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="51301-113">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="51301-113">Management package</span></span>

### <a name="install-npm-modules"></a><span data-ttu-id="51301-114">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="51301-114">Install npm modules</span></span>

<span data-ttu-id="51301-115">Azure SQL Server 管理の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="51301-115">Install the Azure SQL Server management npm module</span></span>

```
npm install azure-arm-sql
```   

### <a name="example"></a><span data-ttu-id="51301-116">例</span><span class="sxs-lookup"><span data-stu-id="51301-116">Example</span></span>

<span data-ttu-id="51301-117">認証を行ってクライアントを作成し、すべてのサーバーを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="51301-117">Authenticate, create a client, and list all servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="51301-118">サンプル</span><span class="sxs-lookup"><span data-stu-id="51301-118">Samples</span></span>

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

<span data-ttu-id="51301-119">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="51301-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
