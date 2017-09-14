---
title: "Node.js 用 Azure Service Bus モジュール"
description: "Node.js 用 Azure Service Bus モジュールのリファレンス"
keywords: Azure,SDK,API,Service Bus, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 4d1bbe917512d2ad5383081bef2c28a33541f28c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-bus-modules-for-nodejs"></a>Node.js 用 Azure Service Bus モジュール

## <a name="overview"></a>概要

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
