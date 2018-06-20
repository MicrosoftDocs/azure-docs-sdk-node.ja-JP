---
title: Node.js 用 Azure Site Recovery モジュール
description: Node.js 用 Azure Site Recovery モジュールのリファレンス
author: rayne-wiselman
ms.author: raynew
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: 470124eb69a48486fa54be6628c028399f0c038e
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259393"
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="62ef9-103">Node.js 用 Azure Site Recovery モジュール</span><span class="sxs-lookup"><span data-stu-id="62ef9-103">Azure Site Recovery modules for Node.js</span></span>

<span data-ttu-id="62ef9-104">Site Recovery は、Azure VM のリージョン間レプリケーション、オンプレミスの仮想マシンと物理サーバーの Azure へのレプリケーション、セカンダリ データセンターへのオンプレミス マシンのレプリケーションを自動化します。</span><span class="sxs-lookup"><span data-stu-id="62ef9-104">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="62ef9-105">Azure Site Recovery の詳細については、[こちら](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62ef9-105">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="62ef9-106">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="62ef9-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="62ef9-107">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="62ef9-107">Install the npm module</span></span>

<span data-ttu-id="62ef9-108">Azure Site Recovery サービスの npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="62ef9-108">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="62ef9-109">例</span><span class="sxs-lookup"><span data-stu-id="62ef9-109">Example</span></span>

<span data-ttu-id="62ef9-110">この例では、リソース グループの Site Recovery サービスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="62ef9-110">This example lists the Site Recovery service for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="62ef9-111">サンプル</span><span class="sxs-lookup"><span data-stu-id="62ef9-111">Samples</span></span>

<span data-ttu-id="62ef9-112">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="62ef9-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
