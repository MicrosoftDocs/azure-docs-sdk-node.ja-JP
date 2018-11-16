---
title: Node.js 用 Azure Operational Insights モジュール
description: Node.js 用 Azure Operational Insights モジュールのリファレンス
author: MGoedtel
ms.author: magoedte
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: c8a137c4759982e0551d9048ac271780e6a68afe
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51497506"
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="83023-103">Node.js 用 Azure Operational Insights モジュール</span><span class="sxs-lookup"><span data-stu-id="83023-103">Azure Operational Insights Modules for Node.js</span></span>

<span data-ttu-id="83023-104">Node.js 用 Azure Operational Insights モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="83023-104">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="83023-105">例</span><span class="sxs-lookup"><span data-stu-id="83023-105">Example</span></span> 

<span data-ttu-id="83023-106">この例では、クライアントを作成して Operational Insights に接続し、指定したリソース グループの一連のワークスペースを取得しています。</span><span class="sxs-lookup"><span data-stu-id="83023-106">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="83023-107">サンプル</span><span class="sxs-lookup"><span data-stu-id="83023-107">Samples</span></span>

<span data-ttu-id="83023-108">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="83023-108">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
