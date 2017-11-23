---
title: "Node.js 用 Azure PostgreSQL モジュール"
description: "Node.js 用 Azure PostgreSQL モジュールのリファレンス"
keywords: "Azure, Node, SDK, API, nodejs, javascript, データベース, PostgreSQL"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: a5130c96b3ae922358b6898c15510282fbaa97f0
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-postgresql-modules-for-nodejs"></a><span data-ttu-id="73f29-104">Node.js 用 Azure PostgreSQL モジュール</span><span class="sxs-lookup"><span data-stu-id="73f29-104">Azure PostgreSQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="73f29-105">概要</span><span class="sxs-lookup"><span data-stu-id="73f29-105">Overview</span></span>

<span data-ttu-id="73f29-106">Azure Database for PostgreSQL へのアクセスに推奨されるクライアント ライブラリは、オープンソースの [Azure Database for PostgreSQL 用 Node.js 接続ライブラリ](https://www.npmjs.com/package/pg)です。</span><span class="sxs-lookup"><span data-stu-id="73f29-106">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Node.js connection library for Azure Database for PostgreSQL](https://www.npmjs.com/package/pg).</span></span> <span data-ttu-id="73f29-107">このライブラリは Node.js 用の非ブロッキング PostgreSQL クライアントで、純粋な JavaScript をサポートするほか、オプションでネイティブの libpq バインディングをサポートします。</span><span class="sxs-lookup"><span data-stu-id="73f29-107">This library is a non-blocking PostgreSQL client for Node.js, supporting pure JavaScript and optional native libpq bindings.</span></span>

<span data-ttu-id="73f29-108">Azure Database for PostgreSQL の詳細については、[こちら](https://docs.microsoft.com/azure/postgresql/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73f29-108">Learn more about [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span></span>

## <a name="client-package"></a><span data-ttu-id="73f29-109">クライアント パッケージ</span><span class="sxs-lookup"><span data-stu-id="73f29-109">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="73f29-110">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="73f29-110">Install the npm module</span></span>

<span data-ttu-id="73f29-111">PostgreSQL クライアント モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="73f29-111">Use npm to install the PostgreSQL client module.</span></span>

```bash
npm install pg
```   

### <a name="example"></a><span data-ttu-id="73f29-112">例</span><span class="sxs-lookup"><span data-stu-id="73f29-112">Example</span></span>

<span data-ttu-id="73f29-113">この例では、クライアント接続を開いて、単純なクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="73f29-113">This example opens a client connection and executes a simple query.</span></span>

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

## <a name="samples"></a><span data-ttu-id="73f29-114">サンプル</span><span class="sxs-lookup"><span data-stu-id="73f29-114">Samples</span></span>

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

<span data-ttu-id="73f29-115">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="73f29-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
