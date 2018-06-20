---
title: Node.js 用仮想マシン モジュール - Azure
description: Node.js 用 Azure 仮想マシン モジュールのリファレンス ガイド
author: iainfoulds
ms.author: iainfou
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 891b441d25369db0f0a67d791d527e6644415434
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259844"
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="c95dc-103">Node.js 用 Azure 仮想マシン モジュール</span><span class="sxs-lookup"><span data-stu-id="c95dc-103">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c95dc-104">概要</span><span class="sxs-lookup"><span data-stu-id="c95dc-104">Overview</span></span>

<span data-ttu-id="c95dc-105">コードから Node.js 用 Azure 管理モジュールを使用して、Windows と Linux の新しい仮想マシンおよび仮想マシン スケール セットを定義、構成、デプロイします。</span><span class="sxs-lookup"><span data-stu-id="c95dc-105">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="c95dc-106">これらのモジュールを使って、Azure サブスクリプション内の停止している VM にディスクをアタッチ (または停止している VM からディスクをデタッチ) したり、既存の仮想マシンを起動/停止したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="c95dc-106">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="c95dc-107">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="c95dc-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c95dc-108">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="c95dc-108">Install the npm module</span></span>

<span data-ttu-id="c95dc-109">Azure コンピューティングの npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="c95dc-109">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="c95dc-110">例</span><span class="sxs-lookup"><span data-stu-id="c95dc-110">Example</span></span>

<span data-ttu-id="c95dc-111">次の例は、Azure にログインして管理クライアントを作成し、特定の場所、発行元、プラン、SKU のすべての VM イメージをリストする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c95dc-111">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'Canonical',   // publisher name
        'UbuntuServer',            // offer
        '16.04-LTS'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a><span data-ttu-id="c95dc-112">サンプル</span><span class="sxs-lookup"><span data-stu-id="c95dc-112">Samples</span></span>

[!INCLUDE [node-virtualmachines-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="c95dc-113">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="c95dc-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
