---
title: Node.js 用 Azure Service Bus モジュール
description: Node.js 用 Azure Service Bus モジュールのリファレンス
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: fde02006fcf364071fcb866098dba7fcd3b1c07b
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260305"
---
# <a name="azure-service-bus-modules-for-nodejs"></a>Node.js 用 Azure Service Bus モジュール

Azure Service Bus は、分離されたシステム間でデータを送信できるようにする非同期メッセージング クラウド プラットフォームです。

Azure Service Bus の詳細については、[こちら](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)を参照してください。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Node.js 用 Azure Service Bus モジュールをインストールするには npm を使用します。

```bash
npm install azure-arm-sb
```

### <a name="example"></a>例

この例では、クライアントを作成した後、特定のサブスクリプションに関連付けられている Service Bus の名前空間をすべて一覧表示します。

```javascript
const msRestAzure = require('ms-rest-azure');
const ServicebusManagement = require('azure-arm-sb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new ServicebusManagement(credentials, subscriptionId);
    client.namespaces.listBySubscription().then(namespaces => {
        namespaces.map(ns => {
            console.log(`found ns : ${ns.name}`);
        });
    });
});
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
