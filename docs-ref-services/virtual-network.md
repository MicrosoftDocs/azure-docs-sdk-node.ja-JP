---
title: "Node.js 用 Azure Virtual Network モジュール"
description: "Node.js 用 Azure Virtual Network モジュールのリファレンス"
keywords: Azure,SDK,API,Virtual Network, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: a17615a832c6dddeb7fef0a8a327dbf86ae281a7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="d029d-104">Node.js 用 Azure Virtual Network モジュール</span><span class="sxs-lookup"><span data-stu-id="d029d-104">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d029d-105">概要</span><span class="sxs-lookup"><span data-stu-id="d029d-105">Overview</span></span>

<span data-ttu-id="d029d-106">Azure Virtual Network サービスでは、仮想ネットワーク (VNet) を使用して Azure リソースを安全に相互接続することができます。</span><span class="sxs-lookup"><span data-stu-id="d029d-106">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="d029d-107">VNet とは、クラウド内のユーザー独自のネットワークを表したものです。</span><span class="sxs-lookup"><span data-stu-id="d029d-107">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="d029d-108">サブスクリプション専用に Azure クラウドが論理的に分離されています。</span><span class="sxs-lookup"><span data-stu-id="d029d-108">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="d029d-109">VNet は、オンプレミス ネットワークに接続することもできます。</span><span class="sxs-lookup"><span data-stu-id="d029d-109">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="d029d-110">Azure Virtual Network の詳細については、[こちら](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d029d-110">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="d029d-111">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="d029d-111">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d029d-112">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="d029d-112">Install the npm module</span></span>

<span data-ttu-id="d029d-113">Azure Virtual Network の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d029d-113">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="d029d-114">例</span><span class="sxs-lookup"><span data-stu-id="d029d-114">Example</span></span>

<span data-ttu-id="d029d-115">この例では、仮想ネットワークの一覧を取得して出力します。</span><span class="sxs-lookup"><span data-stu-id="d029d-115">This example gets and prints the list of virtual networks</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });

```

## <a name="samples"></a><span data-ttu-id="d029d-116">サンプル</span><span class="sxs-lookup"><span data-stu-id="d029d-116">Samples</span></span>

<span data-ttu-id="d029d-117">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="d029d-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
