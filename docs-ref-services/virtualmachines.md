---
title: "Node.js 用 Azure 仮想マシン モジュール"
description: "Node.js 用 Azure 仮想マシン モジュールのリファレンス"
keywords: "Azure, Node, SDK, API, 仮想マシン, vm, nodejs, javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 816714f5c286ee82f61502978c5d811e9f283432
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="dd87a-104">Node.js 用 Azure 仮想マシン モジュール</span><span class="sxs-lookup"><span data-stu-id="dd87a-104">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="dd87a-105">概要</span><span class="sxs-lookup"><span data-stu-id="dd87a-105">Overview</span></span>

<span data-ttu-id="dd87a-106">コードから Node.js 用 Azure 管理モジュールを使用して、Windows と Linux の新しい仮想マシンおよび仮想マシン スケール セットを定義、構成、デプロイします。</span><span class="sxs-lookup"><span data-stu-id="dd87a-106">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="dd87a-107">これらのモジュールを使って、Azure サブスクリプション内の停止している VM にディスクをアタッチ (または停止している VM からディスクをデタッチ) したり、既存の仮想マシンを起動/停止したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="dd87a-107">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="dd87a-108">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="dd87a-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="dd87a-109">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="dd87a-109">Install the npm module</span></span>

<span data-ttu-id="dd87a-110">Azure コンピューティングの npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="dd87a-110">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="dd87a-111">例</span><span class="sxs-lookup"><span data-stu-id="dd87a-111">Example</span></span>

<span data-ttu-id="dd87a-112">次の例は、Azure にログインして管理クライアントを作成し、特定の場所、発行元、プラン、SKU のすべての VM イメージをリストする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="dd87a-112">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'MicrosoftWindowsServer',   // publisher name
        'WindowsServer',            // offer
        '2012-R2-Datacenter'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a><span data-ttu-id="dd87a-113">サンプル</span><span class="sxs-lookup"><span data-stu-id="dd87a-113">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="dd87a-114">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="dd87a-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
