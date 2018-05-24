---
title: Node.js 用 Azure Cosmos DB モジュール
description: Node.js 用 Azure Cosmos DB モジュールのリファレンス
author: SnehaGunda
ms.author: sngun
manager: kfile
ms.date: 03/20/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 4064f9f6c0e1369c8d6261a70709102e7492b340
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="54f8f-103">Node.js 用 Azure Cosmos DB モジュール</span><span class="sxs-lookup"><span data-stu-id="54f8f-103">Azure Cosmos DB Modules for Node.js</span></span>

<span data-ttu-id="54f8f-104">Azure Cosmos DB は、Microsoft のグローバルに分散されたマルチモデル データベース サービスです。</span><span class="sxs-lookup"><span data-stu-id="54f8f-104">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="54f8f-105">Azure Cosmos DB では、Azure のリージョンをいくつでもまたいでスループットとストレージを柔軟かつ個別にスケーリングすることができます。</span><span class="sxs-lookup"><span data-stu-id="54f8f-105">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="54f8f-106">このサービスは包括的なサービス レベル アグリーメント (SLA) により、スループット、待ち時間、可用性、整合性が保証されています。この点は、他のどのデータベース サービスにもないメリットです。</span><span class="sxs-lookup"><span data-stu-id="54f8f-106">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="54f8f-107">Azure Cosmos DB は、書き込みのために最適化され、リソースが管理され、スキーマに関係なく使えるデータベース エンジンを採用しており、キーと値、ドキュメント、グラフ、列指向の 4 つのデータ モデルをネイティブでサポートしています。</span><span class="sxs-lookup"><span data-stu-id="54f8f-107">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="54f8f-108">また、MongoDB、SQL、Gremlin/Graph、Azure Tables、Cassandra (プレビュー) など、拡張可能な方法でデータにアクセスするためのさまざまな API もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="54f8f-108">It also supports many APIs for accessing data including MongoDB, SQL, Gremlin/Graph, Azure Tables, and Cassandra (preview) in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="54f8f-109">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="54f8f-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="54f8f-110">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="54f8f-110">Install the npm module</span></span> 

<span data-ttu-id="54f8f-111">Azure Cosmos DB の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="54f8f-111">Install the Azure Cosmos DB npm module.</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="54f8f-112">例</span><span class="sxs-lookup"><span data-stu-id="54f8f-112">Example</span></span>

<span data-ttu-id="54f8f-113">この例では、すべての Azure Cosmos DB アカウントを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="54f8f-113">This example lists all Azure Cosmos DB accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="54f8f-114">サンプル</span><span class="sxs-lookup"><span data-stu-id="54f8f-114">Samples</span></span>

* [<span data-ttu-id="54f8f-115">Azure Cosmos DB を使用して Node.js アプリを開発する</span><span class="sxs-lookup"><span data-stu-id="54f8f-115">Developing a Node.js app using Azure Cosmos DB</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [<span data-ttu-id="54f8f-116">Azure Cosmos DB の Gremlin を使用して Node.js アプリを開発する</span><span class="sxs-lookup"><span data-stu-id="54f8f-116">Developing a Node.js app using Azure Cosmos DB - Gremlin</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

<span data-ttu-id="54f8f-117">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="54f8f-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
