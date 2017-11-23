---
title: "Node.js 用 Azure 課金モジュール"
description: "Node.js 用 Azure 課金モジュールのリファレンス"
keywords: "Azure,SDK,API,課金, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: fa861aebbd5cbced6477ceeb67dbb5acc7eb233e
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="68ec2-104">Node.js 用 Azure 課金モジュール</span><span class="sxs-lookup"><span data-stu-id="68ec2-104">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="68ec2-105">概要</span><span class="sxs-lookup"><span data-stu-id="68ec2-105">Overview</span></span>
<span data-ttu-id="68ec2-106">Azure の課金情報や請求書には、Azure Billing API でアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-106">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="68ec2-107">この API を使うには、アカウント管理者が Azure Portal でオプトインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-107">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="68ec2-108">「[ロールを使用した Azure 課金情報へのアクセスの管理](https://docs.microsoft.com/azure/billing/billing-manage-access)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68ec2-108">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="68ec2-109">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="68ec2-109">Install the npm module</span></span> 

<span data-ttu-id="68ec2-110">Azure 課金の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-110">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="68ec2-111">例</span><span class="sxs-lookup"><span data-stu-id="68ec2-111">Example</span></span> 
 
<span data-ttu-id="68ec2-112">この例では、過去の全請求書の一覧を出力します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-112">This example prints a list of all of your past invoices.</span></span>
 
```javascript 
const msRestAzure = require('ms-rest-azure');
const BillingManagement = require('azure-arm-billing');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    let client = new BillingManagement(credentials, subscriptionId);
    return client.invoices.list();
  })
  .then(invoices => {
    console.log('List of invoices:');
    console.dir(invoices, { depth: null, colors: true });
  });
``` 


## <a name="samples"></a><span data-ttu-id="68ec2-113">サンプル</span><span class="sxs-lookup"><span data-stu-id="68ec2-113">Samples</span></span>

<span data-ttu-id="68ec2-114">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="68ec2-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
