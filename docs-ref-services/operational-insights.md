---
title: "Node.js 用 Azure Operational Insights モジュール"
description: "Node.js 用 Azure Operational Insights モジュールのリファレンス"
keywords: Azure,SDK,API,Operational Insights, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: e7f7ee30509125a131346039c1245eb9fa6cb6b1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="aebb4-104">Node.js 用 Azure Operational Insights モジュール</span><span class="sxs-lookup"><span data-stu-id="aebb4-104">Azure Operational Insights Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="aebb4-105">概要</span><span class="sxs-lookup"><span data-stu-id="aebb4-105">Overview</span></span>

## <a name="management-package"></a><span data-ttu-id="aebb4-106">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="aebb4-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="aebb4-107">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="aebb4-107">Install the npm module</span></span>

<span data-ttu-id="aebb4-108">Node.js 用 Azure Operational Insights モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="aebb4-108">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="aebb4-109">例</span><span class="sxs-lookup"><span data-stu-id="aebb4-109">Example</span></span> 

<span data-ttu-id="aebb4-110">この例では、クライアントを作成して Operational Insights に接続し、指定したリソース グループの一連のワークスペースを取得しています。</span><span class="sxs-lookup"><span data-stu-id="aebb4-110">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const OperationalInsightsManagement = require('azure-arm-operationalinsights');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new OperationalInsightsManagement(
        credentials,
        subscriptionId
    );
    return client.workspaces.listByResourceGroup('resource-group-name');
})
.then(workspaces => {
    console.log(workspaces);
});
``` 

## <a name="samples"></a><span data-ttu-id="aebb4-111">サンプル</span><span class="sxs-lookup"><span data-stu-id="aebb4-111">Samples</span></span>

<span data-ttu-id="aebb4-112">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="aebb4-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
