---
title: "Node.js 用 Azure Cosmos DB モジュール"
description: "Node.js 用 Azure Cosmos DB モジュールのリファレンス"
keywords: Azure,SDK,API,Cosmos DB, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 1f545f89b5304b611dbe1ed9cb86052c112f13c1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="e4027-104">Node.js 用 Azure Cosmos DB モジュール</span><span class="sxs-lookup"><span data-stu-id="e4027-104">Azure Cosmos DB Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="e4027-105">概要</span><span class="sxs-lookup"><span data-stu-id="e4027-105">Overview</span></span>

<span data-ttu-id="e4027-106">Azure Cosmos DB は、Microsoft のグローバルに分散されたマルチモデル データベース サービスです。</span><span class="sxs-lookup"><span data-stu-id="e4027-106">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="e4027-107">Azure Cosmos DB では、Azure のリージョンをいくつでもまたいでスループットとストレージを柔軟かつ個別にスケーリングすることができます。</span><span class="sxs-lookup"><span data-stu-id="e4027-107">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="e4027-108">このサービスは包括的なサービス レベル アグリーメント (SLA) により、スループット、待ち時間、可用性、整合性が保証されています。この点は、他のどのデータベース サービスにもないメリットです。</span><span class="sxs-lookup"><span data-stu-id="e4027-108">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="e4027-109">Azure Cosmos DB は、書き込みのために最適化され、リソースが管理され、スキーマに関係なく使えるデータベース エンジンを採用しており、キーと値、ドキュメント、グラフ、列指向の 4 つのデータ モデルをネイティブでサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e4027-109">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="e4027-110">また、MongoDB、DocumentDB SQL、Gremlin (プレビュー)、Azure Tables (プレビュー) など、データにアクセスするためのさまざまな API による拡張もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e4027-110">It also supports many APIs for accessing data including MongoDB, DocumentDB SQL, Gremlin (preview), and Azure Tables (preview), in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="e4027-111">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="e4027-111">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e4027-112">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="e4027-112">Install the npm module</span></span> 

<span data-ttu-id="e4027-113">Azure Cosmos DB の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="e4027-113">Install the Azure Cosmos DB npm module</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="e4027-114">例</span><span class="sxs-lookup"><span data-stu-id="e4027-114">Example</span></span>

<span data-ttu-id="e4027-115">この例では、すべての Cosmos DB アカウントを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="e4027-115">This example lists all Cosmos DB accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="e4027-116">サンプル</span><span class="sxs-lookup"><span data-stu-id="e4027-116">Samples</span></span>

* [<span data-ttu-id="e4027-117">Azure Cosmos DB の DocumentDB を使用して Node.js アプリを開発する</span><span class="sxs-lookup"><span data-stu-id="e4027-117">Developing a Node.js app using Azure Cosmos DB - DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [<span data-ttu-id="e4027-118">Azure Cosmos DB の Gremlin を使用して Node.js アプリを開発する</span><span class="sxs-lookup"><span data-stu-id="e4027-118">Developing a Node.js app using Azure Cosmos DB - Gremlin</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

<span data-ttu-id="e4027-119">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="e4027-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
