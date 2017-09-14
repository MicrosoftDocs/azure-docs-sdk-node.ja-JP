---
title: "Node.js 用 Azure Service Map モジュール"
description: "Node.js 用 Azure Service Map モジュールのリファレンス"
keywords: Azure,SDK,API,Service Map, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 330cbceb07ba8bea65c1059a1edb3cd9c69653bc
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-map-modules-for-nodejs"></a><span data-ttu-id="78201-104">Node.js 用 Azure Service Map モジュール</span><span class="sxs-lookup"><span data-stu-id="78201-104">Azure Service Map modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="78201-105">概要</span><span class="sxs-lookup"><span data-stu-id="78201-105">Overview</span></span>

<span data-ttu-id="78201-106">サービス マップは、Windows および Linux システムのアプリケーション コンポーネントを自動的に検出し、サービス間の通信をマップします。</span><span class="sxs-lookup"><span data-stu-id="78201-106">Service Map automatically discovers application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="78201-107">Service Map は、TCP 接続アーキテクチャ全体におけるサーバー、プロセス、ポートの間の接続を表示します。エージェントのインストール以外の構成は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="78201-107">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture, with no configuration required other than the installation of an agent.</span></span>

<span data-ttu-id="78201-108">Azure Service Map の詳細については、[こちら](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78201-108">Learn more about [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span></span>

## <a name="management-package"></a><span data-ttu-id="78201-109">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="78201-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="78201-110">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="78201-110">Install the npm module</span></span>

<span data-ttu-id="78201-111">Azure Service Map の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="78201-111">Install the Azure Service Map npm module</span></span>

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a><span data-ttu-id="78201-112">例</span><span class="sxs-lookup"><span data-stu-id="78201-112">Example</span></span>

<span data-ttu-id="78201-113">この例では、指定したリソース グループおよびワークスペースのすべてのサービス マップを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="78201-113">This example lists all service maps for the specified resource group and workspace.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a><span data-ttu-id="78201-114">サンプル</span><span class="sxs-lookup"><span data-stu-id="78201-114">Samples</span></span>

<span data-ttu-id="78201-115">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="78201-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
