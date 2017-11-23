---
title: "Node.js で Azure データベースを使用するためのサンプル コード"
description: "Node.js で Azure データベースを使用する方法を紹介したサンプル コード。"
author: tomarcher
manager: douge
ms.devlang: nodejs
ms.topic: article
ms.service: azure-nodejs
ms.date: 06/17/2017
ms.author: tarcher
ms.openlocfilehash: 8292a8fd0353ae84ac2b1622e5c622e60be04c9b
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="sample-code-for-using-azure-databases-with-nodejs"></a><span data-ttu-id="e7b11-103">Node.js で Azure データベースを使用するためのサンプル コード</span><span class="sxs-lookup"><span data-stu-id="e7b11-103">Sample code for using Azure databases with Node.js</span></span>

<span data-ttu-id="e7b11-104">以下のサンプル コードでは、Node.js で Azure データベースを使用する方法を紹介しています。</span><span class="sxs-lookup"><span data-stu-id="e7b11-104">The following sample code illustrate using Azure databases with Node.js.</span></span>

<span data-ttu-id="e7b11-105">他のタスクのコードが必要な場合は、[Azure Node.js サンプル](https://azure.microsoft.com/resources/samples/?term=nodejs)の完全な一覧を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7b11-105">If you need code for other tasks, you can browse the full list of [Azure Node.js samples](https://azure.microsoft.com/resources/samples/?term=nodejs).</span></span>

| | |
|---|---|
| <span data-ttu-id="e7b11-106">**Cosmos DB**</span><span class="sxs-lookup"><span data-stu-id="e7b11-106">**Cosmos DB**</span></span> ||
| [<span data-ttu-id="e7b11-107">Azure Cosmos DB と Graph API を使用する</span><span class="sxs-lookup"><span data-stu-id="e7b11-107">Use the Azure Cosmos DB and Graph API</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/) | <span data-ttu-id="e7b11-108">Node.js アプリケーションから Azure Cosmos DB と Graph API を使用してデータを格納する方法やデータにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7b11-108">Shows you how to use the Azure Cosmos DB with the Graph API to store and access data from a Node.js application.</span></span> |
| [<span data-ttu-id="e7b11-109">Azure Cosmos DB と DocumentDB API を使用する</span><span class="sxs-lookup"><span data-stu-id="e7b11-109">Use the Azure Cosmos DB and Document DB API</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/) | <span data-ttu-id="e7b11-110">Node.js アプリケーションから Azure Cosmos DB と DocumentDB API を使用してデータを格納する方法やデータにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7b11-110">Shows you how to use the Azure Cosmos DB with the DocumentDB API to store and access data from a Node.js application.</span></span> |
| <span data-ttu-id="e7b11-111">**DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="e7b11-111">**DocumentDB**</span></span> ||
| [<span data-ttu-id="e7b11-112">DocumentDB を使用した Node.js および Express での Web アプリケーション開発</span><span class="sxs-lookup"><span data-stu-id="e7b11-112">Web application development with Node.js and Express using DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/documentdb-node-todo-app/) | <span data-ttu-id="e7b11-113">Azure 上の Node.js Express アプリケーションから Azure DocumentDB を使用してデータを格納する方法やデータにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7b11-113">Shows how to use Azure DocumentDB to store and access data from a Node.js Express application on Azure.</span></span> |
| [<span data-ttu-id="e7b11-114">DocumentDB を使用した Node.js コンソール アプリの開発</span><span class="sxs-lookup"><span data-stu-id="e7b11-114">Developing a Node.js console app using DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/documentdb-node-getting-started/) | <span data-ttu-id="e7b11-115">このサンプルは、Microsoft Azure DocumentDB サービスと Node.js の基本的な操作を短時間で身に付けることができるように作られています。</span><span class="sxs-lookup"><span data-stu-id="e7b11-115">This sample shows you how get started quickly with Microsoft Azure DocumentDB service and Node.js.</span></span> |
| <span data-ttu-id="e7b11-116">**MongoDB**</span><span class="sxs-lookup"><span data-stu-id="e7b11-116">**MongoDB**</span></span> ||
| [<span data-ttu-id="e7b11-117">Azure における Node.js と MongoDB Web アプリ</span><span class="sxs-lookup"><span data-stu-id="e7b11-117">Node.js and MongoDB web app in Azure</span></span>](https://azure.microsoft.com/resources/samples/meanjs/) | <span data-ttu-id="e7b11-118">「[Azure で Node.js と MongoDB Web アプリを構築する](http://docs.microsoft.com/azure/app-service-web/app-service-web-tutorial-nodejs-mongodb-app?toc=/azure/node/toc.json&bc=/azure/node/toc.json)」のチュートリアルに沿って利用できるサンプル アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="e7b11-118">Sample application that you can use to follow along with the tutorial, [Build a Node.js and MongoDB web app in Azure](http://docs.microsoft.com/azure/app-service-web/app-service-web-tutorial-nodejs-mongodb-app?toc=/azure/node/toc.json&bc=/azure/node/toc.json).</span></span> |
| <span data-ttu-id="e7b11-119">**SQL Database**</span><span class="sxs-lookup"><span data-stu-id="e7b11-119">**SQL Database**</span></span> ||
| [<span data-ttu-id="e7b11-120">Azure SQL Database: Node.js を使用して Azure SQL Database に照会する</span><span class="sxs-lookup"><span data-stu-id="e7b11-120">Azure SQL Database: Use Node.js to connect and query data</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs) | <span data-ttu-id="e7b11-121">Windows、Ubuntu Linux、Mac の各プラットフォームから Node.js を使用して Azure SQL データベースに接続し、Transact-SQL ステートメントを使用してデータベース内のデータを照会、挿入、更新、削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7b11-121">Demonstrates how to connect to an Azure SQL database using Node.js; then use Transact-SQL statements to query, insert, update, and delete data in the database from Windows, Ubuntu Linux, and Mac platforms.</span></span> |