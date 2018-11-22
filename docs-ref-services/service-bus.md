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
ms.openlocfilehash: 76d7c615cbe64fa38f9c28ea8dfc6d1c854bb0c9
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2018
ms.locfileid: "52089717"
---
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="b0b62-103">Node.js 用 Azure Service Bus モジュール</span><span class="sxs-lookup"><span data-stu-id="b0b62-103">Azure Service Bus Modules for Node.js</span></span>

<span data-ttu-id="b0b62-104">Azure Service Bus は、分離されたシステム間でデータを送信できるようにする非同期メッセージング クラウド プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="b0b62-104">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="b0b62-105">Azure Service Bus の詳細については、[こちら](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0b62-105">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="b0b62-106">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="b0b62-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b0b62-107">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="b0b62-107">Install the npm module</span></span>

<span data-ttu-id="b0b62-108">Node.js 用 Azure Service Bus モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="b0b62-108">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="b0b62-109">例</span><span class="sxs-lookup"><span data-stu-id="b0b62-109">Example</span></span>

<span data-ttu-id="b0b62-110">この例では、クライアントを作成した後、特定のサブスクリプションに関連付けられている Service Bus の名前空間をすべて一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="b0b62-110">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b0b62-111">サンプル</span><span class="sxs-lookup"><span data-stu-id="b0b62-111">Samples</span></span>

<span data-ttu-id="b0b62-112">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="b0b62-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
