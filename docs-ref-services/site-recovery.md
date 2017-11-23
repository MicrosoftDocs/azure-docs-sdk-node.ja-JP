---
title: "Node.js 用 Azure Site Recovery モジュール"
description: "Node.js 用 Azure Site Recovery モジュールのリファレンス"
keywords: Azure,SDK,API,Site Recovery, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: 3537503118a6fbe181c8cc4b26da545a4bdbd764
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="fe541-104">Node.js 用 Azure Site Recovery モジュール</span><span class="sxs-lookup"><span data-stu-id="fe541-104">Azure Site Recovery modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="fe541-105">概要</span><span class="sxs-lookup"><span data-stu-id="fe541-105">Overview</span></span>

<span data-ttu-id="fe541-106">Site Recovery は、Azure VM のリージョン間レプリケーション、オンプレミスの仮想マシンと物理サーバーの Azure へのレプリケーション、セカンダリ データセンターへのオンプレミス マシンのレプリケーションを自動化します。</span><span class="sxs-lookup"><span data-stu-id="fe541-106">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="fe541-107">Azure Site Recovery の詳細については、[こちら](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe541-107">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="fe541-108">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="fe541-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="fe541-109">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="fe541-109">Install the npm module</span></span>

<span data-ttu-id="fe541-110">Azure Site Recovery サービスの npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="fe541-110">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="fe541-111">例</span><span class="sxs-lookup"><span data-stu-id="fe541-111">Example</span></span>

<span data-ttu-id="fe541-112">この例では、リソース グループの Site Recovery サービスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="fe541-112">This example lists the Site Recovery service for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesManagement = require('azure-arm-recoveryservices');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesManagement(credentials, subscriptionId);
    return client.vaults.listByResourceGroup(resourceGroupName);
  })
  .then(vaults => {
    console.log('List of vaults:');
    console.dir(vaults, { depth: null, colors: true });
  });
  
```

## <a name="samples"></a><span data-ttu-id="fe541-113">サンプル</span><span class="sxs-lookup"><span data-stu-id="fe541-113">Samples</span></span>

<span data-ttu-id="fe541-114">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="fe541-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
