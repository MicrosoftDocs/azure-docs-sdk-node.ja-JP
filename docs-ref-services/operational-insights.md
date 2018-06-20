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
ms.openlocfilehash: 2cd948a57925954ecddc077ead727b1a7689ce0e
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34261971"
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="559cf-103">Node.js 用 Azure Operational Insights モジュール</span><span class="sxs-lookup"><span data-stu-id="559cf-103">Azure Operational Insights Modules for Node.js</span></span>

<span data-ttu-id="559cf-104">Node.js 用 Azure Operational Insights モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="559cf-104">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="559cf-105">例</span><span class="sxs-lookup"><span data-stu-id="559cf-105">Example</span></span> 

<span data-ttu-id="559cf-106">この例では、クライアントを作成して Operational Insights に接続し、指定したリソース グループの一連のワークスペースを取得しています。</span><span class="sxs-lookup"><span data-stu-id="559cf-106">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="559cf-107">サンプル</span><span class="sxs-lookup"><span data-stu-id="559cf-107">Samples</span></span>

<span data-ttu-id="559cf-108">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="559cf-108">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
