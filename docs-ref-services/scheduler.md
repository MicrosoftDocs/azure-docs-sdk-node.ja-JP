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
ms.openlocfilehash: 9a842919fddb3d6448d5a4e951dc58dd0d3211e0
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2018
ms.locfileid: "52094267"
---
# <a name="azure-scheduler-modules-for-nodejs"></a>Node.js 用 Azure Scheduler モジュール

Azure Scheduler は、スケジュール設定された作業を作成、保守し、HTTP、HTTPS、ストレージ キュー、[Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview) のいずれかを介して呼び出します。

Azure Scheduler の詳細については、[こちら](/azure/scheduler/scheduler-intro)を参照してください。

## <a name="management-package"></a>管理パッケージ

Management API を使って、スケジュール設定された作業を作成、保守し、さまざまな通信チャネルを介して呼び出します。

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure Scheduler の npm モジュールをインストールします。

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a>例

この例では、現在のスケジューラを一覧表示します。

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

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
