---
title: Node.js 用 Azure 課金モジュール
description: Node.js 用 Azure 課金モジュールのリファレンス
author: tfitzmac
ms.author: tomfitz
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: billing
ms.product: ''
ms.technology: ''
ms.openlocfilehash: 20df85ae5e504e460a501737aa07b6692a0da3c7
ms.sourcegitcommit: 0d439a88f38a085e2be0616c8bdb0ffcca2e54ad
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2018
ms.locfileid: "49057646"
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="6a64a-103">Node.js 用 Azure 課金モジュール</span><span class="sxs-lookup"><span data-stu-id="6a64a-103">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="6a64a-104">概要</span><span class="sxs-lookup"><span data-stu-id="6a64a-104">Overview</span></span>
<span data-ttu-id="6a64a-105">Azure の課金情報や請求書には、Azure Billing API でアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6a64a-105">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="6a64a-106">この API を使うには、アカウント管理者が Azure Portal でオプトインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a64a-106">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="6a64a-107">「[ロールを使用した Azure 課金情報へのアクセスの管理](https://docs.microsoft.com/azure/billing/billing-manage-access)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a64a-107">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="6a64a-108">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="6a64a-108">Install the npm module</span></span> 

<span data-ttu-id="6a64a-109">Azure 課金の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="6a64a-109">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="6a64a-110">例</span><span class="sxs-lookup"><span data-stu-id="6a64a-110">Example</span></span> 
 
<span data-ttu-id="6a64a-111">この例では、過去の全請求書の一覧を出力します。</span><span class="sxs-lookup"><span data-stu-id="6a64a-111">This example prints a list of all of your past invoices.</span></span>
 
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


## <a name="samples"></a><span data-ttu-id="6a64a-112">サンプル</span><span class="sxs-lookup"><span data-stu-id="6a64a-112">Samples</span></span>

<span data-ttu-id="6a64a-113">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="6a64a-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
