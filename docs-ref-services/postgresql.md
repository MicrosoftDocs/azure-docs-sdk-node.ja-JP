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
# <a name="azure-postgresql-modules-for-nodejs"></a><span data-ttu-id="d2f5a-103">Node.js 用 Azure PostgreSQL モジュール</span><span class="sxs-lookup"><span data-stu-id="d2f5a-103">Azure PostgreSQL modules for Node.js</span></span>

<span data-ttu-id="d2f5a-104">Azure Database for PostgreSQL へのアクセスに推奨されるクライアント ライブラリは、オープンソースの [Azure Database for PostgreSQL 用 Node.js 接続ライブラリ](https://www.npmjs.com/package/pg)です。</span><span class="sxs-lookup"><span data-stu-id="d2f5a-104">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Node.js connection library for Azure Database for PostgreSQL](https://www.npmjs.com/package/pg).</span></span> <span data-ttu-id="d2f5a-105">このライブラリは Node.js 用の非ブロッキング PostgreSQL クライアントで、純粋な JavaScript をサポートするほか、オプションでネイティブの libpq バインディングをサポートします。</span><span class="sxs-lookup"><span data-stu-id="d2f5a-105">This library is a non-blocking PostgreSQL client for Node.js, supporting pure JavaScript and optional native libpq bindings.</span></span>

<span data-ttu-id="d2f5a-106">Azure Database for PostgreSQL の詳細については、[こちら](https://docs.microsoft.com/azure/postgresql/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2f5a-106">Learn more about [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span></span>

## <a name="client-package"></a><span data-ttu-id="d2f5a-107">クライアント パッケージ</span><span class="sxs-lookup"><span data-stu-id="d2f5a-107">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d2f5a-108">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="d2f5a-108">Install the npm module</span></span>

<span data-ttu-id="d2f5a-109">PostgreSQL クライアント モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="d2f5a-109">Use npm to install the PostgreSQL client module.</span></span>

```bash
npm install pg
```   

### <a name="example"></a><span data-ttu-id="d2f5a-110">例</span><span class="sxs-lookup"><span data-stu-id="d2f5a-110">Example</span></span>

<span data-ttu-id="d2f5a-111">この例では、クライアント接続を開いて、単純なクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="d2f5a-111">This example opens a client connection and executes a simple query.</span></span>

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

## <a name="samples"></a><span data-ttu-id="d2f5a-112">サンプル</span><span class="sxs-lookup"><span data-stu-id="d2f5a-112">Samples</span></span>

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

<span data-ttu-id="d2f5a-113">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="d2f5a-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
