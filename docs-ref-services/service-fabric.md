---
title: Node.js 用 Azure Service Fabric モジュール
description: Node.js 用 Azure Service Fabric モジュールのリファレンス
author: rwike77
ms.author: ryanwi
manager: timlt
ms.date: 11/12/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: 12fcc4af4a78cc01370355cba0b4c642f202a30c
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34261881"
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="7a93f-103">Node.js 用 Azure Service Fabric モジュール</span><span class="sxs-lookup"><span data-stu-id="7a93f-103">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="7a93f-104">概要</span><span class="sxs-lookup"><span data-stu-id="7a93f-104">Overview</span></span>

<span data-ttu-id="7a93f-105">Azure Service Fabric は、スケーラブルで信頼性に優れたマイクロサービスとコンテナーのパッケージ化とデプロイ、管理を簡単に行うことができる分散システム プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="7a93f-105">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="7a93f-106">Azure Service Fabric の詳細については、[こちら](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a93f-106">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="7a93f-107">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="7a93f-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="7a93f-108">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="7a93f-108">Install the npm module</span></span>

<span data-ttu-id="7a93f-109">Azure Service Fabric の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="7a93f-109">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="7a93f-110">例</span><span class="sxs-lookup"><span data-stu-id="7a93f-110">Example</span></span>

<span data-ttu-id="7a93f-111">この例では、Azure サブスクリプションのクラスターを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="7a93f-111">This example shows how you can list the clusters for an Azure subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="7a93f-112">サンプル</span><span class="sxs-lookup"><span data-stu-id="7a93f-112">Samples</span></span>

<span data-ttu-id="7a93f-113">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="7a93f-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
