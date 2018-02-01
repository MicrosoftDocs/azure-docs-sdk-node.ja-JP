---
title: "Node.js 用 Azure Virtual Network モジュール"
description: "Node.js 用 Azure Virtual Network モジュールのリファレンス"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: f073c700c8df7f7aa05c93d725051d3a9976bebc
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2018
---
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="0f1fd-103">Node.js 用 Azure Virtual Network モジュール</span><span class="sxs-lookup"><span data-stu-id="0f1fd-103">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="0f1fd-104">概要</span><span class="sxs-lookup"><span data-stu-id="0f1fd-104">Overview</span></span>

<span data-ttu-id="0f1fd-105">Azure Virtual Network サービスでは、仮想ネットワーク (VNet) を使用して Azure リソースを安全に相互接続することができます。</span><span class="sxs-lookup"><span data-stu-id="0f1fd-105">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="0f1fd-106">VNet とは、クラウド内のユーザー独自のネットワークを表したものです。</span><span class="sxs-lookup"><span data-stu-id="0f1fd-106">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="0f1fd-107">サブスクリプション専用に Azure クラウドが論理的に分離されています。</span><span class="sxs-lookup"><span data-stu-id="0f1fd-107">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="0f1fd-108">VNet は、オンプレミス ネットワークに接続することもできます。</span><span class="sxs-lookup"><span data-stu-id="0f1fd-108">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="0f1fd-109">Azure Virtual Network の詳細については、[こちら](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f1fd-109">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="0f1fd-110">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="0f1fd-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0f1fd-111">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="0f1fd-111">Install the npm module</span></span>

<span data-ttu-id="0f1fd-112">Azure Virtual Network の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="0f1fd-112">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="0f1fd-113">例</span><span class="sxs-lookup"><span data-stu-id="0f1fd-113">Example</span></span>

<span data-ttu-id="0f1fd-114">この例では、仮想ネットワークの一覧を取得して出力します。</span><span class="sxs-lookup"><span data-stu-id="0f1fd-114">This example gets and prints the list of virtual networks</span></span>

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

## <a name="samples"></a><span data-ttu-id="0f1fd-115">サンプル</span><span class="sxs-lookup"><span data-stu-id="0f1fd-115">Samples</span></span>

<span data-ttu-id="0f1fd-116">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="0f1fd-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
