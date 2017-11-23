---
title: "Node.js 用 Azure Notification Hubs モジュール"
description: "Node.js 用 Azure Notification Hubs モジュールのリファレンス"
keywords: Azure,SDK,API,Notification Hubs, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 0141760cb93c77faed4a04893fe1376e4e75c361
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a><span data-ttu-id="e71a5-104">Node.js 用 Azure Notification Hubs モジュール</span><span class="sxs-lookup"><span data-stu-id="e71a5-104">Azure Notification Hubs modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="e71a5-105">概要</span><span class="sxs-lookup"><span data-stu-id="e71a5-105">Overview</span></span>

<span data-ttu-id="e71a5-106">Azure Notification Hubs は、使いやすいマルチプラットフォーム対応のスケール アウトされたプッシュ エンジンを提供します。</span><span class="sxs-lookup"><span data-stu-id="e71a5-106">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="e71a5-107">プラットフォームをまたぐ単一の API 呼び出しで、任意のバックエンド (クラウドまたはオンプレミス) から任意のモバイル プラットフォームに、対象を指定して個人用に設定したプッシュ通知を送信できます。</span><span class="sxs-lookup"><span data-stu-id="e71a5-107">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

<span data-ttu-id="e71a5-108">Notification Hubs は、エンタープライズ向けとコンシューマー向けのどちらのシナリオにも適しています。</span><span class="sxs-lookup"><span data-stu-id="e71a5-108">Notification Hubs works great for both enterprise and consumer scenarios.</span></span> <span data-ttu-id="e71a5-109">以下に、Notification Hubs の主な用途をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="e71a5-109">Here are a few examples customers use Notification Hubs for:</span></span>
- <span data-ttu-id="e71a5-110">ニュース速報の通知を数百万台のデバイスに速やかに送信する。</span><span class="sxs-lookup"><span data-stu-id="e71a5-110">Send breaking news notifications to millions with low latency.</span></span>
- <span data-ttu-id="e71a5-111">場所に基づいたクーポンを対象のユーザー セグメントに送信する。</span><span class="sxs-lookup"><span data-stu-id="e71a5-111">Send location-based coupons to interested user segments.</span></span>
- <span data-ttu-id="e71a5-112">イベント関連の通知を、メディア/スポーツ/金融/ゲーム アプリケーションのユーザーまたはグループに送信する。</span><span class="sxs-lookup"><span data-stu-id="e71a5-112">Send event-related notifications to users or groups for media/sports/finance/gaming applications.</span></span>
- <span data-ttu-id="e71a5-113">ユーザーの関心を惹き付けて利用を促すために、プロモーション コンテンツをアプリにプッシュする。</span><span class="sxs-lookup"><span data-stu-id="e71a5-113">Push promotional contents to apps to engage and market to customers.</span></span>
- <span data-ttu-id="e71a5-114">新着メッセージや作業項目などのエンタープライズ イベントをユーザーに通知する。</span><span class="sxs-lookup"><span data-stu-id="e71a5-114">Notify users of enterprise events like new messages and work items.</span></span>
- <span data-ttu-id="e71a5-115">多要素認証のコードを送信する。</span><span class="sxs-lookup"><span data-stu-id="e71a5-115">Send codes for multi-factor authentication.</span></span>

## <a name="management-package"></a><span data-ttu-id="e71a5-116">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="e71a5-116">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e71a5-117">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="e71a5-117">Install the npm module</span></span>

<span data-ttu-id="e71a5-118">Azure Notification Hubs モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="e71a5-118">Install the Azure Notification Hubs module</span></span> 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a><span data-ttu-id="e71a5-119">例</span><span class="sxs-lookup"><span data-stu-id="e71a5-119">Example</span></span>

<span data-ttu-id="e71a5-120">この例では、すべての通知ハブを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="e71a5-120">This example lists all notification hubs.</span></span>

 ```javascript
const msRestAzure = require('ms-rest-azure');
const notificationHubsManagementClient = require('azure-arm-notificationhubs');

const subscriptionId = 'your-subscription-id';
const notificationHubNamespace = 'your-hub-namespace';
const resourceGroup = 'your-resource-group';
let notificationHubsClient;

msRestAzure.interactiveLogin().then(credentials => {
  notificationHubsClient = new notificationHubsManagementClient(credentials, subscriptionId);
  notificationHubsClient.notificationHubs
    .list(resourceGroup, notificationHubNamespace)
    .then(notificationHubs => console.log('Retrieved notification hubs: ', notificationHubs));
});
```

## <a name="samples"></a><span data-ttu-id="e71a5-121">サンプル</span><span class="sxs-lookup"><span data-stu-id="e71a5-121">Samples</span></span>

* [<span data-ttu-id="e71a5-122">Node.js バックエンド用の App Service Mobile の完全なクイックスタート</span><span class="sxs-lookup"><span data-stu-id="e71a5-122">App Service Mobile completed quickstart for Node.js backend</span></span>](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* [<span data-ttu-id="e71a5-123">Node.js を実行する Intel Edison からのデータに関して Azure IoT サービスが検出した振動の異常をツイートする</span><span class="sxs-lookup"><span data-stu-id="e71a5-123">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="e71a5-124">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="e71a5-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
