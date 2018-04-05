---
title: Node.js 用 Azure Cosmos DB モジュール
description: Node.js 用 Azure Cosmos DB モジュールのリファレンス
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 03/20/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 02d4729d72cba8628ac98de0bf41c30f54c75e85
ms.sourcegitcommit: 178734fbd3784ade4d8bdb5141be6d7ca7e017f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2018
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="d8a46-103">Node.js 用 Azure Cosmos DB モジュール</span><span class="sxs-lookup"><span data-stu-id="d8a46-103">Azure Cosmos DB Modules for Node.js</span></span>

<span data-ttu-id="d8a46-104">Azure Cosmos DB は、Microsoft のグローバルに分散されたマルチモデル データベース サービスです。</span><span class="sxs-lookup"><span data-stu-id="d8a46-104">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="d8a46-105">Azure Cosmos DB では、Azure のリージョンをいくつでもまたいでスループットとストレージを柔軟かつ個別にスケーリングすることができます。</span><span class="sxs-lookup"><span data-stu-id="d8a46-105">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="d8a46-106">このサービスは包括的なサービス レベル アグリーメント (SLA) により、スループット、待ち時間、可用性、整合性が保証されています。この点は、他のどのデータベース サービスにもないメリットです。</span><span class="sxs-lookup"><span data-stu-id="d8a46-106">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="d8a46-107">Azure Cosmos DB は、書き込みのために最適化され、リソースが管理され、スキーマに関係なく使えるデータベース エンジンを採用しており、キーと値、ドキュメント、グラフ、列指向の 4 つのデータ モデルをネイティブでサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d8a46-107">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="d8a46-108">また、MongoDB、SQL、Gremlin/Graph、Azure Tables、Cassandra (プレビュー) など、拡張可能な方法でデータにアクセスするためのさまざまな API もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d8a46-108">It also supports many APIs for accessing data including MongoDB, SQL, Gremlin/Graph, Azure Tables, and Cassandra (preview) in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="d8a46-109">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="d8a46-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d8a46-110">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="d8a46-110">Install the npm module</span></span> 

<span data-ttu-id="d8a46-111">Azure Cosmos DB の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d8a46-111">Install the Azure Cosmos DB npm module.</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="d8a46-112">例</span><span class="sxs-lookup"><span data-stu-id="d8a46-112">Example</span></span>

<span data-ttu-id="d8a46-113">この例では、すべての Azure Cosmos DB アカウントを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="d8a46-113">This example lists all Azure Cosmos DB accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="d8a46-114">サンプル</span><span class="sxs-lookup"><span data-stu-id="d8a46-114">Samples</span></span>

* [<span data-ttu-id="d8a46-115">Azure Cosmos DB を使用して Node.js アプリを開発する</span><span class="sxs-lookup"><span data-stu-id="d8a46-115">Developing a Node.js app using Azure Cosmos DB</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [<span data-ttu-id="d8a46-116">Azure Cosmos DB の Gremlin を使用して Node.js アプリを開発する</span><span class="sxs-lookup"><span data-stu-id="d8a46-116">Developing a Node.js app using Azure Cosmos DB - Gremlin</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

<span data-ttu-id="d8a46-117">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="d8a46-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
