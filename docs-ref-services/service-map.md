---
title: Node.js 用 Azure Service Map モジュール
description: Node.js 用 Azure Service Map モジュールのリファレンス
author: bwren
ms.author: bwren
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 494d948896d65dd67b06f455386f500346862beb
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2018
ms.locfileid: "52067077"
---
# <a name="azure-service-map-modules-for-nodejs"></a><span data-ttu-id="02cfe-103">Node.js 用 Azure Service Map モジュール</span><span class="sxs-lookup"><span data-stu-id="02cfe-103">Azure Service Map modules for Node.js</span></span>

<span data-ttu-id="02cfe-104">サービス マップは、Windows および Linux システムのアプリケーション コンポーネントを自動的に検出し、サービス間の通信をマップします。</span><span class="sxs-lookup"><span data-stu-id="02cfe-104">Service Map automatically discovers application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="02cfe-105">Service Map は、TCP 接続アーキテクチャ全体におけるサーバー、プロセス、ポートの間の接続を表示します。エージェントのインストール以外の構成は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="02cfe-105">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture, with no configuration required other than the installation of an agent.</span></span>

<span data-ttu-id="02cfe-106">Azure Service Map の詳細については、[こちら](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02cfe-106">Learn more about [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span></span>

## <a name="management-package"></a><span data-ttu-id="02cfe-107">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="02cfe-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="02cfe-108">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="02cfe-108">Install the npm module</span></span>

<span data-ttu-id="02cfe-109">Azure Service Map の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="02cfe-109">Install the Azure Service Map npm module</span></span>

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a><span data-ttu-id="02cfe-110">例</span><span class="sxs-lookup"><span data-stu-id="02cfe-110">Example</span></span>

<span data-ttu-id="02cfe-111">この例では、指定したリソース グループおよびワークスペースのすべてのサービス マップを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="02cfe-111">This example lists all service maps for the specified resource group and workspace.</span></span>

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

## <a name="samples"></a><span data-ttu-id="02cfe-112">サンプル</span><span class="sxs-lookup"><span data-stu-id="02cfe-112">Samples</span></span>

<span data-ttu-id="02cfe-113">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="02cfe-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
