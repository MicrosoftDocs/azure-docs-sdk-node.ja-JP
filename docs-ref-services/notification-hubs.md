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
# <a name="azure-notification-hubs-modules-for-nodejs"></a>Node.js 用 Azure Notification Hubs モジュール

## <a name="overview"></a>概要

Azure Notification Hubs は、使いやすいマルチプラットフォーム対応のスケール アウトされたプッシュ エンジンを提供します。 プラットフォームをまたぐ単一の API 呼び出しで、任意のバックエンド (クラウドまたはオンプレミス) から任意のモバイル プラットフォームに、対象を指定して個人用に設定したプッシュ通知を送信できます。

Notification Hubs は、エンタープライズ向けとコンシューマー向けのどちらのシナリオにも適しています。 以下に、Notification Hubs の主な用途をいくつか示します。
- ニュース速報の通知を数百万台のデバイスに速やかに送信する。
- 場所に基づいたクーポンを対象のユーザー セグメントに送信する。
- イベント関連の通知を、メディア/スポーツ/金融/ゲーム アプリケーションのユーザーまたはグループに送信する。
- ユーザーの関心を惹き付けて利用を促すために、プロモーション コンテンツをアプリにプッシュする。
- 新着メッセージや作業項目などのエンタープライズ イベントをユーザーに通知する。
- 多要素認証のコードを送信する。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure Notification Hubs モジュールをインストールします。 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a>例

この例では、すべての通知ハブを一覧表示します。

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

## <a name="samples"></a>サンプル

* [Node.js バックエンド用の App Service Mobile の完全なクイックスタート](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* [Node.js を実行する Intel Edison からのデータに関して Azure IoT サービスが検出した振動の異常をツイートする](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。