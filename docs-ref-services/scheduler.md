---
title: Node.js 用 Azure Scheduler モジュール
description: Node.js 用 Azure Scheduler モジュールのリファレンス
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: d52a61a786a86b21bc48752e6531a000ae1aefde
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260795"
---
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="f299a-103">Node.js 用 Azure Scheduler モジュール</span><span class="sxs-lookup"><span data-stu-id="f299a-103">Azure Scheduler modules for Node.js</span></span>

<span data-ttu-id="f299a-104">Azure Scheduler は、スケジュール設定された作業を作成、保守し、HTTP、HTTPS、ストレージ キュー、[Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview) のいずれかを介して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f299a-104">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="f299a-105">Azure Scheduler の詳細については、[こちら](/azure/scheduler/scheduler-intro)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f299a-105">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="f299a-106">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="f299a-106">Management package</span></span>

<span data-ttu-id="f299a-107">Management API を使って、スケジュール設定された作業を作成、保守し、さまざまな通信チャネルを介して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f299a-107">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f299a-108">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="f299a-108">Install the npm module</span></span>

<span data-ttu-id="f299a-109">Azure Scheduler の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="f299a-109">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="f299a-110">例</span><span class="sxs-lookup"><span data-stu-id="f299a-110">Example</span></span>

<span data-ttu-id="f299a-111">この例では、現在のスケジューラを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="f299a-111">This examples lists the current schedulers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="f299a-112">サンプル</span><span class="sxs-lookup"><span data-stu-id="f299a-112">Samples</span></span>

<span data-ttu-id="f299a-113">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="f299a-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
