---
title: "Node.js 用 Azure Notification Hubs モジュール"
description: "Node.js 用 Azure Notification Hubs モジュールのリファレンス"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: c353bdc0fff7784881b5cd4f1d3b4dda5268f1ea
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2018
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a><span data-ttu-id="07df7-103">Node.js 用 Azure Notification Hubs モジュール</span><span class="sxs-lookup"><span data-stu-id="07df7-103">Azure Notification Hubs modules for Node.js</span></span>

<span data-ttu-id="07df7-104">Azure Notification Hubs は、使いやすいマルチプラットフォーム対応のスケール アウトされたプッシュ エンジンを提供します。</span><span class="sxs-lookup"><span data-stu-id="07df7-104">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="07df7-105">プラットフォームをまたぐ単一の API 呼び出しで、任意のバックエンド (クラウドまたはオンプレミス) から任意のモバイル プラットフォームに、対象を指定して個人用に設定したプッシュ通知を送信できます。</span><span class="sxs-lookup"><span data-stu-id="07df7-105">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

<span data-ttu-id="07df7-106">Notification Hubs は、エンタープライズ向けとコンシューマー向けのどちらのシナリオにも適しています。</span><span class="sxs-lookup"><span data-stu-id="07df7-106">Notification Hubs works great for both enterprise and consumer scenarios.</span></span> <span data-ttu-id="07df7-107">以下に、Notification Hubs の主な用途をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="07df7-107">Here are a few examples customers use Notification Hubs for:</span></span>
- <span data-ttu-id="07df7-108">ニュース速報の通知を数百万台のデバイスに速やかに送信する。</span><span class="sxs-lookup"><span data-stu-id="07df7-108">Send breaking news notifications to millions with low latency.</span></span>
- <span data-ttu-id="07df7-109">場所に基づいたクーポンを対象のユーザー セグメントに送信する。</span><span class="sxs-lookup"><span data-stu-id="07df7-109">Send location-based coupons to interested user segments.</span></span>
- <span data-ttu-id="07df7-110">イベント関連の通知を、メディア/スポーツ/金融/ゲーム アプリケーションのユーザーまたはグループに送信する。</span><span class="sxs-lookup"><span data-stu-id="07df7-110">Send event-related notifications to users or groups for media/sports/finance/gaming applications.</span></span>
- <span data-ttu-id="07df7-111">ユーザーの関心を惹き付けて利用を促すために、プロモーション コンテンツをアプリにプッシュする。</span><span class="sxs-lookup"><span data-stu-id="07df7-111">Push promotional contents to apps to engage and market to customers.</span></span>
- <span data-ttu-id="07df7-112">新着メッセージや作業項目などのエンタープライズ イベントをユーザーに通知する。</span><span class="sxs-lookup"><span data-stu-id="07df7-112">Notify users of enterprise events like new messages and work items.</span></span>
- <span data-ttu-id="07df7-113">多要素認証のコードを送信する。</span><span class="sxs-lookup"><span data-stu-id="07df7-113">Send codes for multi-factor authentication.</span></span>

## <a name="management-package"></a><span data-ttu-id="07df7-114">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="07df7-114">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="07df7-115">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="07df7-115">Install the npm module</span></span>

<span data-ttu-id="07df7-116">Azure Notification Hubs モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="07df7-116">Install the Azure Notification Hubs module</span></span> 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a><span data-ttu-id="07df7-117">例</span><span class="sxs-lookup"><span data-stu-id="07df7-117">Example</span></span>

<span data-ttu-id="07df7-118">この例では、すべての通知ハブを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="07df7-118">This example lists all notification hubs.</span></span>

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

## <a name="samples"></a><span data-ttu-id="07df7-119">サンプル</span><span class="sxs-lookup"><span data-stu-id="07df7-119">Samples</span></span>

* [<span data-ttu-id="07df7-120">Node.js バックエンド用の App Service Mobile の完全なクイックスタート</span><span class="sxs-lookup"><span data-stu-id="07df7-120">App Service Mobile completed quickstart for Node.js backend</span></span>](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* [<span data-ttu-id="07df7-121">Node.js を実行する Intel Edison からのデータに関して Azure IoT サービスが検出した振動の異常をツイートする</span><span class="sxs-lookup"><span data-stu-id="07df7-121">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="07df7-122">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="07df7-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
