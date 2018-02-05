---
title: "Node.js 用 Azure Traffic Manager モジュール"
description: "Node.js 用 Azure Traffic Manager モジュールのリファレンス"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: cf0834a0eadc67868efb165d60d39c681d4435eb
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2018
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a><span data-ttu-id="5b34e-103">Node.js 用 Azure Traffic Manager モジュール</span><span class="sxs-lookup"><span data-stu-id="5b34e-103">Azure Traffic Manager modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="5b34e-104">概要</span><span class="sxs-lookup"><span data-stu-id="5b34e-104">Overview</span></span>

<span data-ttu-id="5b34e-105">Microsoft Azure Traffic Manager では、さまざまなデータセンターのサービス エンドポイントへのユーザー トラフィックの分散を制御できます。</span><span class="sxs-lookup"><span data-stu-id="5b34e-105">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="5b34e-106">Traffic Manager でサポートされるサービス エンドポイントには、Azure VM、Web Apps、およびクラウド サービスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5b34e-106">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="5b34e-107">Azure 以外の外部エンドポイントで Traffic Manager を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5b34e-107">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="5b34e-108">Azure Traffic Manager の詳細については、[こちら](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5b34e-108">Learn more about [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="5b34e-109">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="5b34e-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="5b34e-110">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="5b34e-110">Install the npm module</span></span>

<span data-ttu-id="5b34e-111">Azure Traffic Manager の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="5b34e-111">Install the Azure traffic manager npm module</span></span>

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a><span data-ttu-id="5b34e-112">例</span><span class="sxs-lookup"><span data-stu-id="5b34e-112">Example</span></span>

<span data-ttu-id="5b34e-113">この例では、特定のリソース グループのすべての Traffic Manager を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="5b34e-113">This example lists all Traffic Managers for a given resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a><span data-ttu-id="5b34e-114">サンプル</span><span class="sxs-lookup"><span data-stu-id="5b34e-114">Samples</span></span>

<span data-ttu-id="5b34e-115">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="5b34e-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
