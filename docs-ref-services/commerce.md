---
title: "Node.js 用 Azure コマース モジュール"
description: "Node.js 用 Azure コマース モジュールのリファレンス"
keywords: "Azure,SDK,API,コマース, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: b337e070ee7da0b852d8cad1d4e163d7f8130857
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-commerce-modules-for-nodejs"></a><span data-ttu-id="d87fe-104">Node.js 用 Azure コマース モジュール</span><span class="sxs-lookup"><span data-stu-id="d87fe-104">Azure Commerce modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d87fe-105">概要</span><span class="sxs-lookup"><span data-stu-id="d87fe-105">Overview</span></span>

<span data-ttu-id="d87fe-106">Azure コマース API を使用すると、使用状況やリソースに関するデータを、お使いのデータ分析ツールで取得できます。</span><span class="sxs-lookup"><span data-stu-id="d87fe-106">Use Azure Commerce APIs to pull usage and resource data into your preferred data analysis tools.</span></span> <span data-ttu-id="d87fe-107">Azure Resource Usage API と Azure Resource RateCard API は、コストを正確に予測して管理するうえで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d87fe-107">The Azure Resource Usage and RateCard APIs can help you accurately predict and manage your costs.</span></span> <span data-ttu-id="d87fe-108">これらの API は、Azure Resource Manager が公開している API ファミリに含まれ、リソース プロバイダーとして実装されています。</span><span class="sxs-lookup"><span data-stu-id="d87fe-108">The APIs are implemented as a Resource Provider and part of the family of APIs exposed by the Azure Resource Manager.</span></span>

## <a name="management-package"></a><span data-ttu-id="d87fe-109">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="d87fe-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d87fe-110">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="d87fe-110">Install the npm module</span></span>

<span data-ttu-id="d87fe-111">Azure コマースの npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d87fe-111">Install the Azure Commerce npm module</span></span>

```bash
npm install azure-arm-commerce
```

### <a name="example"></a><span data-ttu-id="d87fe-112">例</span><span class="sxs-lookup"><span data-stu-id="d87fe-112">Example</span></span>

<span data-ttu-id="d87fe-113">この例では、Azure の先月の推定消費量データを取得します。</span><span class="sxs-lookup"><span data-stu-id="d87fe-113">This example retrieves your estimated Azure consumption data for the last month.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const CommerceManagement = require('azure-arm-commerce');

const endDate = new Date();
endDate.setUTCHours(0, 0, 0, 0);
const startDate = new Date();
startDate.setMonth(startDate.getMonth() - 1);
startDate.setUTCHours(0, 0, 0, 0);

const subscriptionId = 'your-subscription-id';
const usageOptions = {
  showDetails: true,
  granularity: 'Daily'
};

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new CommerceManagement(credentials, subscriptionId);
    return client.usageAggregates.list(startDate, endDate, usageOptions);
  })
  .then(usage => {
    console.dir(usage, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="d87fe-114">サンプル</span><span class="sxs-lookup"><span data-stu-id="d87fe-114">Samples</span></span>

<span data-ttu-id="d87fe-115">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="d87fe-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
