---
title: "Node.js 用 Azure イベント ハブ モジュール"
description: "Node.js 用 Azure イベント ハブ モジュールのリファレンス"
keywords: "Azure,SDK,API,イベント ハブ, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: 5ac6fc3f86419602756c354393078b399a6cba23
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-event-hub-modules-for-nodejs"></a><span data-ttu-id="aea07-104">Node.js 用 Azure イベント ハブ モジュール</span><span class="sxs-lookup"><span data-stu-id="aea07-104">Azure Event Hub modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="aea07-105">概要</span><span class="sxs-lookup"><span data-stu-id="aea07-105">Overview</span></span>
<span data-ttu-id="aea07-106">Azure Event Hubs は高度にスケーラブルなデータ ストリーミング プラットフォームであり、毎秒数百万のイベントを受け取って処理できるイベント インジェスト サービスでもあります。</span><span class="sxs-lookup"><span data-stu-id="aea07-106">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service capable of receiving and processing millions of events per second.</span></span> <span data-ttu-id="aea07-107">Event Hubs では、分散されたソフトウェアやデバイスから生成されるイベント、データ、またはテレメトリを処理および格納できます。</span><span class="sxs-lookup"><span data-stu-id="aea07-107">Event Hubs can process and store events, data, or telemetry produced by distributed software and devices.</span></span> <span data-ttu-id="aea07-108">イベント ハブに送信されたデータは、任意のリアルタイム分析プロバイダーやバッチ処理/ストレージ アダプターを使用して、変換および保存できます。</span><span class="sxs-lookup"><span data-stu-id="aea07-108">Data sent to an event hub can be transformed and stored using any real-time analytics provider or batching/storage adapters.</span></span> <span data-ttu-id="aea07-109">短い待機時間かつ大きなスケールでパブリッシュ/サブスクライブ機能を実現できるので、Event Hubs はビッグ データの "オン ランプ" として機能します。</span><span class="sxs-lookup"><span data-stu-id="aea07-109">With the ability to provide publish-subscribe capabilities with low latency and at massive scale, Event Hubs serves as the "on ramp" for Big Data.</span></span>

## <a name="management-package"></a><span data-ttu-id="aea07-110">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="aea07-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="aea07-111">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="aea07-111">Install the npm module</span></span> 

<span data-ttu-id="aea07-112">Node.js 用 Azure イベント ハブ モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="aea07-112">Use npm to install the Azure Event Hub modules for Node.js</span></span>

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a><span data-ttu-id="aea07-113">例</span><span class="sxs-lookup"><span data-stu-id="aea07-113">Example</span></span>

<span data-ttu-id="aea07-114">この例では、既存のイベント ハブに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="aea07-114">This example retrieves information about an existing event hub.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const EventHubManagement = require('azure-arm-eventhub');

const resourceGroupName = 'testRG';
const namespaceName = 'testNS';
const eventHubName = 'testEH';
const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new EventHubManagement(credentials, subscriptionId);
    return client.eventHubs.get(resourceGroupName, namespaceName, eventHubName);
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="aea07-115">サンプル</span><span class="sxs-lookup"><span data-stu-id="aea07-115">Samples</span></span>

<span data-ttu-id="aea07-116">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="aea07-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
