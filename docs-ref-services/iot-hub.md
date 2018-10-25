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
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "49702847"
---
# <a name="azure-iot-hub-modules-for-nodejs"></a>Node.js 用 Azure IoT Hub モジュール

Azure IoT Hub は、何百万もの IoT デバイスとソリューション バックエンド間で、セキュリティで保護された信頼性のある双方向通信を実現する、フル マネージドのサービスです。 Azure IoT Hub の特長は次のとおりです。
- 一方向メッセージング、ファイル転送、要求/応答メソッドなど、デバイスからクラウドとクラウドからデバイスの複数の通信オプションを提供します。
- 組み込みの宣言型メッセージ ルーティングを他の Azure サービスに提供します。
- デバイス メタデータと同期状態情報用にクエリ実行可能なストアを提供します。
- デバイスごとのセキュリティ キーまたは X.509 証明書を使用して、セキュリティ保護された通信とアクセス制御を実現します。
- デバイス接続イベントおよびデバイス ID 管理イベントの詳細な監視を実現します。
- 最も一般的な言語とプラットフォームのデバイスのライブラリが含まれます。

Node.js 用 Azure IoT Hub モジュールをインストールするには npm を使用します。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure IoT Hub の npm モジュールをインストールします。

```bash
npm install azure-arm-iothub
```

### <a name="example"></a>例

この例では、IoT ハブを作成して名前を付けます。

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

この例では、既存の IoT ハブを名前で取得します。

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

## <a name="samples"></a>サンプル

- [Raspberry Pi Azure IoT スタート キットの概要](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [Node.js を実行する Intel Edison からのデータに関して Azure IoT サービスが検出した振動の異常をツイートする](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
