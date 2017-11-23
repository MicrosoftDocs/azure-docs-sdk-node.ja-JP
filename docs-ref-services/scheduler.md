---
title: "Node.js 用 Azure Scheduler モジュール"
description: "Node.js 用 Azure Scheduler モジュールのリファレンス"
keywords: Azure,SDK,API,Scheduler, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 3070612721dc434b8c3d7c3200f0666755fd4ce8
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="944d6-104">Node.js 用 Azure Scheduler モジュール</span><span class="sxs-lookup"><span data-stu-id="944d6-104">Azure Scheduler modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="944d6-105">概要</span><span class="sxs-lookup"><span data-stu-id="944d6-105">Overview</span></span>

<span data-ttu-id="944d6-106">Azure Scheduler は、スケジュール設定された作業を作成、保守し、HTTP、HTTPS、ストレージ キュー、[Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview) のいずれかを介して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="944d6-106">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="944d6-107">Azure Scheduler の詳細については、[こちら](/azure/scheduler/scheduler-intro)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="944d6-107">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="944d6-108">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="944d6-108">Management package</span></span>

<span data-ttu-id="944d6-109">Management API を使って、スケジュール設定された作業を作成、保守し、さまざまな通信チャネルを介して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="944d6-109">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="944d6-110">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="944d6-110">Install the npm module</span></span>

<span data-ttu-id="944d6-111">Azure Scheduler の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="944d6-111">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="944d6-112">例</span><span class="sxs-lookup"><span data-stu-id="944d6-112">Example</span></span>

<span data-ttu-id="944d6-113">この例では、現在のスケジューラを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="944d6-113">This examples lists the current schedulers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure')
const SchedulerManagement = require('azure-arm-scheduler')

msRestAzure.interactiveLogin().then(credentials => {
    // Create a scheduler from the login credentials
    let client = new SchedulerManagement(credentials, 'your-subscription-id')
    // Get the full list of current jobs for the subscription
    return client.jobCollections.listBySubscription()
}).then(currentJobs => {
    console.log("Current jobs:")
    console.dir(currentJobs, {depth:null, colors:true})
}).catch(error => {
    console.log("An error occurred:")
    console.dir(error, {depth:null, colors:true})
})
```

## <a name="samples"></a><span data-ttu-id="944d6-114">サンプル</span><span class="sxs-lookup"><span data-stu-id="944d6-114">Samples</span></span>

<span data-ttu-id="944d6-115">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="944d6-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
