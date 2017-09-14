---
title: "Node.js 用 Azure Service Fabric モジュール"
description: "Node.js 用 Azure Service Fabric モジュールのリファレンス"
keywords: Azure,SDK,API,Service Fabric, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: d3de9af4e8ca834963cf2ac0275ed02b8021f29f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="08aa3-104">Node.js 用 Azure Service Fabric モジュール</span><span class="sxs-lookup"><span data-stu-id="08aa3-104">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="08aa3-105">概要</span><span class="sxs-lookup"><span data-stu-id="08aa3-105">Overview</span></span>

<span data-ttu-id="08aa3-106">Azure Service Fabric は、スケーラブルで信頼性に優れたマイクロサービスとコンテナーのパッケージ化とデプロイ、管理を簡単に行うことができる分散システム プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="08aa3-106">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="08aa3-107">Azure Service Fabric の詳細については、[こちら](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08aa3-107">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="08aa3-108">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="08aa3-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="08aa3-109">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="08aa3-109">Install the npm module</span></span>

<span data-ttu-id="08aa3-110">Azure Service Fabric の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="08aa3-110">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="08aa3-111">例</span><span class="sxs-lookup"><span data-stu-id="08aa3-111">Example</span></span>

<span data-ttu-id="08aa3-112">この例では、Azure サブスクリプションのクラスターを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="08aa3-112">This example shows how you can list the clusters for an Azure subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ServiceFabricManagement = require('azure-arm-servicefabric');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new ServiceFabricManagement(
      credentials,
      subscriptionId
    );
    return client.clusters.list();
  })
  .then(clusters => {
    console.log('List of clusters:');
    console.dir(clusters, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="08aa3-113">サンプル</span><span class="sxs-lookup"><span data-stu-id="08aa3-113">Samples</span></span>

<span data-ttu-id="08aa3-114">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="08aa3-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
