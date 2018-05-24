---
title: Node.js 用 Azure Virtual Network モジュール
description: Node.js 用 Azure Virtual Network モジュールのリファレンス
author: jimdial
ms.author: jdial
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: 456839dbecb9ddd1ad0d4b3f8aa7570a04c100b1
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="08812-103">Node.js 用 Azure Virtual Network モジュール</span><span class="sxs-lookup"><span data-stu-id="08812-103">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="08812-104">概要</span><span class="sxs-lookup"><span data-stu-id="08812-104">Overview</span></span>

<span data-ttu-id="08812-105">Azure Virtual Network サービスでは、仮想ネットワーク (VNet) を使用して Azure リソースを安全に相互接続することができます。</span><span class="sxs-lookup"><span data-stu-id="08812-105">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="08812-106">VNet とは、クラウド内のユーザー独自のネットワークを表したものです。</span><span class="sxs-lookup"><span data-stu-id="08812-106">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="08812-107">サブスクリプション専用に Azure クラウドが論理的に分離されています。</span><span class="sxs-lookup"><span data-stu-id="08812-107">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="08812-108">VNet は、オンプレミス ネットワークに接続することもできます。</span><span class="sxs-lookup"><span data-stu-id="08812-108">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="08812-109">Azure Virtual Network の詳細については、[こちら](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08812-109">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="08812-110">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="08812-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="08812-111">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="08812-111">Install the npm module</span></span>

<span data-ttu-id="08812-112">Azure Virtual Network の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="08812-112">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="08812-113">例</span><span class="sxs-lookup"><span data-stu-id="08812-113">Example</span></span>

<span data-ttu-id="08812-114">この例では、仮想ネットワークの一覧を取得して出力します。</span><span class="sxs-lookup"><span data-stu-id="08812-114">This example gets and prints the list of virtual networks</span></span>

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

## <a name="samples"></a><span data-ttu-id="08812-115">サンプル</span><span class="sxs-lookup"><span data-stu-id="08812-115">Samples</span></span>

<span data-ttu-id="08812-116">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="08812-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
