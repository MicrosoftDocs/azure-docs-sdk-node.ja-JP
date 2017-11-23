---
title: "Node.js 用 Azure Redis Cache モジュール"
description: "Node.js 用 Azure Redis Cache モジュールのリファレンス"
keywords: Azure,SDK,API,Redis Cache, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: 8a10e522e39461697b740750b63fc82a6cc320ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-redis-cache-modules-for-nodejs"></a><span data-ttu-id="cbaf5-104">Node.js 用 Azure Redis Cache モジュール</span><span class="sxs-lookup"><span data-stu-id="cbaf5-104">Azure Redis Cache modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="cbaf5-105">概要</span><span class="sxs-lookup"><span data-stu-id="cbaf5-105">Overview</span></span>

<span data-ttu-id="cbaf5-106">Azure Redis Cache は広く普及しているオープン ソースの Redis プロジェクトを基盤にしています。</span><span class="sxs-lookup"><span data-stu-id="cbaf5-106">Azure Redis Cache is based on the popular open source Redis project.</span></span> <span data-ttu-id="cbaf5-107">これを使用すると、Microsoft によって管理されている、セキュリティで保護された専用 Redis インスタンスに、ご利用の Azure アプリでアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="cbaf5-107">It gives you access to a secure, dedicated Redis instance, managed by Microsoft and accessible from your Azure apps.</span></span>

<span data-ttu-id="cbaf5-108">Redis は高度なキーと値のストアです。キーには、文字列、ハッシュ、リスト、セット、ソート済みセットなどのデータ構造を格納できます。</span><span class="sxs-lookup"><span data-stu-id="cbaf5-108">Redis is an advanced key-value store, where keys can contain data structures such as strings, hashes, lists, sets, and sorted sets.</span></span> <span data-ttu-id="cbaf5-109">Redis では、このようなデータ型に対する一連のアトミック操作がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="cbaf5-109">Redis supports a set of atomic operations on these data types.</span></span>

<span data-ttu-id="cbaf5-110">Azure Redis Cache の詳細については、[こちら](https://docs.microsoft.com/azure/redis-cache/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cbaf5-110">Learn more about [Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/).</span></span>

## <a name="client-package"></a><span data-ttu-id="cbaf5-111">クライアント パッケージ</span><span class="sxs-lookup"><span data-stu-id="cbaf5-111">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="cbaf5-112">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="cbaf5-112">Install the npm module</span></span>

<span data-ttu-id="cbaf5-113">Node.js 用 Redis モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="cbaf5-113">Use npm to install the Redis module for Node.js</span></span>

```bash
npm install redis
```

### <a name="example"></a><span data-ttu-id="cbaf5-114">例</span><span class="sxs-lookup"><span data-stu-id="cbaf5-114">Example</span></span>

<span data-ttu-id="cbaf5-115">この例では、Azure Redis Cache インスタンスに接続してキー/値のペアを保存した後、そのキーで、保存されている値を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="cbaf5-115">This example connects to an Azure Redis Cache instance, stores a key/value pair and then reads the stored value by its key.</span></span>

```javascript
const redis = require('redis');

const client = redis.createClient(6380, '<name>.redis.cache.windows.net', {
  auth_pass: '<key>',
  tls: { servername: '<name>.redis.cache.windows.net' }
});

client.set('key1', 'value', (err, reply) => {
  console.log(reply);
});

client.get('key1', (err, reply) => {
  console.log(reply);
});
```

## <a name="management-package"></a><span data-ttu-id="cbaf5-116">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="cbaf5-116">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="cbaf5-117">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="cbaf5-117">Install the npm module</span></span>

<span data-ttu-id="cbaf5-118">Node.js 用 Azure Redis Cache モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="cbaf5-118">Use npm to install the Azure Redis Cache modules for Node.js</span></span>

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a><span data-ttu-id="cbaf5-119">例</span><span class="sxs-lookup"><span data-stu-id="cbaf5-119">Example</span></span>

<span data-ttu-id="cbaf5-120">この例では、Azure に対して認証を行い、指定したリソース グループに含まれるすべての Redis Cache インスタンスをリストします。</span><span class="sxs-lookup"><span data-stu-id="cbaf5-120">This example authenticates to Azure and lists all Redis Cache instances in a specified resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const AzureMgmtRedisCache = require('azure-arm-rediscache');

msRestAzure.interactiveLogin().then(credentials => {
  const client = new AzureMgmtRedisCache(credentials, 'my-subscription-id');
  client.redis.listByResourceGroup('testResourceGroup').then(result => {
    console.log(result);
  });
});
```


## <a name="samples"></a><span data-ttu-id="cbaf5-121">サンプル</span><span class="sxs-lookup"><span data-stu-id="cbaf5-121">Samples</span></span>

* [<span data-ttu-id="cbaf5-122">Node.js で Azure Redis Cache を使用する方法</span><span class="sxs-lookup"><span data-stu-id="cbaf5-122">How to use Azure Redis Cache with Node.js</span></span>](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

<span data-ttu-id="cbaf5-123">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="cbaf5-123">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
