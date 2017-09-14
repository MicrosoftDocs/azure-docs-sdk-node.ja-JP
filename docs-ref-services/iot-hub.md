---
title: "Node.js 用 Azure IoT Hub モジュール"
description: "Node.js 用 Azure IoT Hub モジュールのリファレンス"
keywords: Azure,SDK,API,IoT Hub, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: IoT Hub
ms.openlocfilehash: 44d01ceb833d2acbef6f9f22b32d4ad66b1fd5ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-iot-hub-modules-for-nodejs"></a><span data-ttu-id="57787-104">Node.js 用 Azure IoT Hub モジュール</span><span class="sxs-lookup"><span data-stu-id="57787-104">Azure IoT Hub modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="57787-105">概要</span><span class="sxs-lookup"><span data-stu-id="57787-105">Overview</span></span>

<span data-ttu-id="57787-106">Azure IoT Hub は、何百万もの IoT デバイスとソリューション バックエンド間で、セキュリティで保護された信頼性のある双方向通信を実現する、完全に管理されたサービスです。</span><span class="sxs-lookup"><span data-stu-id="57787-106">Azure IoT Hub is a fully managed service that enables reliable and secure bidirectional communications between millions of IoT devices and a solution back end.</span></span> <span data-ttu-id="57787-107">Azure IoT Hub の特長は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="57787-107">Azure IoT Hub:</span></span>
- <span data-ttu-id="57787-108">一方向メッセージング、ファイル転送、要求/応答メソッドなど、デバイスからクラウドとクラウドからデバイスの複数の通信オプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="57787-108">Provides multiple device-to-cloud and cloud-to-device communication options, including one-way messaging, file transfer, and request-reply methods.</span></span>
- <span data-ttu-id="57787-109">組み込みの宣言型メッセージ ルーティングを他の Azure サービスに提供します。</span><span class="sxs-lookup"><span data-stu-id="57787-109">Provides built-in declarative message routing to other Azure services.</span></span>
- <span data-ttu-id="57787-110">デバイス メタデータと同期状態情報用にクエリ実行可能なストアを提供します。</span><span class="sxs-lookup"><span data-stu-id="57787-110">Provides a queryable store for device metadata and synchronized state information.</span></span>
- <span data-ttu-id="57787-111">デバイスごとのセキュリティ キーまたは X.509 証明書を使用して、セキュリティ保護された通信とアクセス制御を実現します。</span><span class="sxs-lookup"><span data-stu-id="57787-111">Enables secure communications and access control using per-device security keys or X.509 certificates.</span></span>
- <span data-ttu-id="57787-112">デバイス接続イベントおよびデバイス ID 管理イベントの詳細な監視を実現します。</span><span class="sxs-lookup"><span data-stu-id="57787-112">Provides extensive monitoring for device connectivity and device identity management events.</span></span>
- <span data-ttu-id="57787-113">最も一般的な言語とプラットフォームのデバイスのライブラリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="57787-113">Includes device libraries for the most popular languages and platforms.</span></span>

<span data-ttu-id="57787-114">Node.js 用 Azure IoT Hub モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="57787-114">Use npm to install the Azure IoT Hub modules for Node.js</span></span>

## <a name="management-package"></a><span data-ttu-id="57787-115">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="57787-115">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="57787-116">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="57787-116">Install the npm module</span></span>

<span data-ttu-id="57787-117">Azure IoT Hub の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="57787-117">Install the Azure IoT Hub npm module</span></span>

```bash
npm install azure-arm-iothub
```

### <a name="example"></a><span data-ttu-id="57787-118">例</span><span class="sxs-lookup"><span data-stu-id="57787-118">Example</span></span>

<span data-ttu-id="57787-119">この例では、IoT ハブを作成して名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="57787-119">This example creates and names an IoT hub.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const IoTHubClient = require('azure-arm-iothub');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';
const location = 'East US';

// Describe the IoT hub you want to create
const hubDescription = {
  name: hubName,
  location: location,
  subscriptionid: subscriptionId,
  resourcegroup: resourceGroup,
  sku: { name: 'S1', capacity: 2 },
  properties: {
    enableFileUploadNotifications: false,
    ipFilterRules: [{ filterName: 'ipfilterrule', action: 'accept', ipMask: '0.0.0.0/0' }],
    operationsMonitoringProperties: {
      events: {
        C2DCommands: 'Error',
        DeviceTelemetry: 'Error',
        DeviceIdentityOperations: 'Error',
        Connections: 'Error, Information'
      }
    },
    features: 'None'
  }
};

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .createOrUpdate(resourceGroup, hubName, hubDescription)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

<span data-ttu-id="57787-120">この例では、既存の IoT ハブを名前で取得します。</span><span class="sxs-lookup"><span data-stu-id="57787-120">This example gets the existing IoT hub, by name.</span></span>

```javascript
const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .get(resourceGroup, hubName)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

## <a name="samples"></a><span data-ttu-id="57787-121">サンプル</span><span class="sxs-lookup"><span data-stu-id="57787-121">Samples</span></span>

- [<span data-ttu-id="57787-122">Raspberry Pi Azure IoT スタート キットの概要</span><span class="sxs-lookup"><span data-stu-id="57787-122">Get started with the Raspberry Pi Azure IoT Starter Kit</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [<span data-ttu-id="57787-123">Node.js を実行する Intel Edison からのデータに関して Azure IoT サービスが検出した振動の異常をツイートする</span><span class="sxs-lookup"><span data-stu-id="57787-123">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="57787-124">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="57787-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
