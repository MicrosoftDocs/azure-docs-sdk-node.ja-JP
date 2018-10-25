---
title: Node.js 用 Azure コマース モジュール
description: Node.js 用 Azure コマース モジュールのリファレンス
author: rloutlaw
ms.author: ROutlaw
manager: angrobew
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: 87a0e8d689d8d782a705a4525fdbe9b681403c07
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "49757397"
---
# <a name="azure-commerce-modules-for-nodejs"></a><span data-ttu-id="a4157-103">Node.js 用 Azure コマース モジュール</span><span class="sxs-lookup"><span data-stu-id="a4157-103">Azure Commerce modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="a4157-104">概要</span><span class="sxs-lookup"><span data-stu-id="a4157-104">Overview</span></span>

<span data-ttu-id="a4157-105">Azure コマース API を使用すると、使用状況やリソースに関するデータを、お使いのデータ分析ツールで取得できます。</span><span class="sxs-lookup"><span data-stu-id="a4157-105">Use Azure Commerce APIs to pull usage and resource data into your preferred data analysis tools.</span></span> <span data-ttu-id="a4157-106">Azure Resource Usage API と Azure Resource RateCard API は、コストを正確に予測して管理するうえで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a4157-106">The Azure Resource Usage and RateCard APIs can help you accurately predict and manage your costs.</span></span> <span data-ttu-id="a4157-107">これらの API は、Azure Resource Manager が公開している API ファミリに含まれ、リソース プロバイダーとして実装されています。</span><span class="sxs-lookup"><span data-stu-id="a4157-107">The APIs are implemented as a Resource Provider and part of the family of APIs exposed by the Azure Resource Manager.</span></span>

## <a name="management-package"></a><span data-ttu-id="a4157-108">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="a4157-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a4157-109">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="a4157-109">Install the npm module</span></span>

<span data-ttu-id="a4157-110">Azure コマースの npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="a4157-110">Install the Azure Commerce npm module</span></span>

```bash
npm install azure-arm-commerce
```

### <a name="example"></a><span data-ttu-id="a4157-111">例</span><span class="sxs-lookup"><span data-stu-id="a4157-111">Example</span></span>

<span data-ttu-id="a4157-112">この例では、Azure の先月の推定消費量データを取得します。</span><span class="sxs-lookup"><span data-stu-id="a4157-112">This example retrieves your estimated Azure consumption data for the last month.</span></span>

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

## <a name="samples"></a><span data-ttu-id="a4157-113">サンプル</span><span class="sxs-lookup"><span data-stu-id="a4157-113">Samples</span></span>

<span data-ttu-id="a4157-114">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="a4157-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
