---
title: Node.js 用 Azure IoT Hub モジュール
description: Node.js 用 Azure IoT Hub モジュールのリファレンス
author: dominicbetts
ms.author: dobett
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: IoT Hub
ms.openlocfilehash: 1f83e016023722f149384ac015726e9257a9f3af
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2018
ms.locfileid: "52151327"
---
# <a name="azure-iot-hub-modules-for-nodejs"></a><span data-ttu-id="eb637-103">Node.js 用 Azure IoT Hub モジュール</span><span class="sxs-lookup"><span data-stu-id="eb637-103">Azure IoT Hub modules for Node.js</span></span>

<span data-ttu-id="eb637-104">Azure IoT Hub は、何百万もの IoT デバイスとソリューション バックエンド間で、セキュリティで保護された信頼性のある双方向通信を実現する、フル マネージドのサービスです。</span><span class="sxs-lookup"><span data-stu-id="eb637-104">Azure IoT Hub is a fully managed service that enables reliable and secure bidirectional communications between millions of IoT devices and a solution back end.</span></span> <span data-ttu-id="eb637-105">Azure IoT Hub の特長は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="eb637-105">Azure IoT Hub:</span></span>
- <span data-ttu-id="eb637-106">一方向メッセージング、ファイル転送、要求/応答メソッドなど、デバイスからクラウドとクラウドからデバイスの複数の通信オプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="eb637-106">Provides multiple device-to-cloud and cloud-to-device communication options, including one-way messaging, file transfer, and request-reply methods.</span></span>
- <span data-ttu-id="eb637-107">組み込みの宣言型メッセージ ルーティングを他の Azure サービスに提供します。</span><span class="sxs-lookup"><span data-stu-id="eb637-107">Provides built-in declarative message routing to other Azure services.</span></span>
- <span data-ttu-id="eb637-108">デバイス メタデータと同期状態情報用にクエリ実行可能なストアを提供します。</span><span class="sxs-lookup"><span data-stu-id="eb637-108">Provides a queryable store for device metadata and synchronized state information.</span></span>
- <span data-ttu-id="eb637-109">デバイスごとのセキュリティ キーまたは X.509 証明書を使用して、セキュリティ保護された通信とアクセス制御を実現します。</span><span class="sxs-lookup"><span data-stu-id="eb637-109">Enables secure communications and access control using per-device security keys or X.509 certificates.</span></span>
- <span data-ttu-id="eb637-110">デバイス接続イベントおよびデバイス ID 管理イベントの詳細な監視を実現します。</span><span class="sxs-lookup"><span data-stu-id="eb637-110">Provides extensive monitoring for device connectivity and device identity management events.</span></span>
- <span data-ttu-id="eb637-111">最も一般的な言語とプラットフォームのデバイスのライブラリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="eb637-111">Includes device libraries for the most popular languages and platforms.</span></span>

<span data-ttu-id="eb637-112">Node.js 用 Azure IoT Hub モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="eb637-112">Use npm to install the Azure IoT Hub modules for Node.js</span></span>

## <a name="management-package"></a><span data-ttu-id="eb637-113">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="eb637-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="eb637-114">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="eb637-114">Install the npm module</span></span>

<span data-ttu-id="eb637-115">Azure IoT Hub の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="eb637-115">Install the Azure IoT Hub npm module</span></span>

```bash
npm install azure-arm-iothub
```

### <a name="example"></a><span data-ttu-id="eb637-116">例</span><span class="sxs-lookup"><span data-stu-id="eb637-116">Example</span></span>

<span data-ttu-id="eb637-117">この例では、IoT ハブを作成して名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="eb637-117">This example creates and names an IoT hub.</span></span>

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

<span data-ttu-id="eb637-118">この例では、既存の IoT ハブを名前で取得します。</span><span class="sxs-lookup"><span data-stu-id="eb637-118">This example gets the existing IoT hub, by name.</span></span>

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

## <a name="samples"></a><span data-ttu-id="eb637-119">サンプル</span><span class="sxs-lookup"><span data-stu-id="eb637-119">Samples</span></span>

- [<span data-ttu-id="eb637-120">Raspberry Pi Azure IoT スタート キットの概要</span><span class="sxs-lookup"><span data-stu-id="eb637-120">Get started with the Raspberry Pi Azure IoT Starter Kit</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [<span data-ttu-id="eb637-121">Node.js を実行する Intel Edison からのデータに関して Azure IoT サービスが検出した振動の異常をツイートする</span><span class="sxs-lookup"><span data-stu-id="eb637-121">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="eb637-122">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="eb637-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
