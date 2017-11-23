---
title: "Node.js 用 Azure Analysis Services モジュール"
description: "Node.js 用 Azure Analysis Services モジュールのリファレンス"
keywords: Azure,SDK,API,Analysis Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: ff38883eed2de5d95fb5bd5fd951c6b9564a4b35
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="4cb3d-104">Node.js 用 Azure Analysis Services モジュール</span><span class="sxs-lookup"><span data-stu-id="4cb3d-104">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="4cb3d-105">概要</span><span class="sxs-lookup"><span data-stu-id="4cb3d-105">Overview</span></span>
<span data-ttu-id="4cb3d-106">このパッケージには、Microsoft Azure Analysis Services の管理を省力化する Node.js モジュールが備わっています。</span><span class="sxs-lookup"><span data-stu-id="4cb3d-106">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="4cb3d-107">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="4cb3d-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="4cb3d-108">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="4cb3d-108">Install the npm module</span></span>

<span data-ttu-id="4cb3d-109">Azure Analysis Services の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="4cb3d-109">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="4cb3d-110">例</span><span class="sxs-lookup"><span data-stu-id="4cb3d-110">Example</span></span>

<span data-ttu-id="4cb3d-111">この例では、利用可能なすべての Analysis Services サーバーを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="4cb3d-111">This example lists all available Analysis Service servers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const analysisServicesManagement = require('azure-arm-analysisservices');

const subscriptionId = 'your-subscription-id';
let analysisServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  analysisServicesClient = new analysisServicesManagement(credentials, subscriptionId);

  analysisServicesClient.servers
    .list()
    .then(servers => console.log('Retrieved analysis services servers: ', servers));
});
```

## <a name="samples"></a><span data-ttu-id="4cb3d-112">サンプル</span><span class="sxs-lookup"><span data-stu-id="4cb3d-112">Samples</span></span>

<span data-ttu-id="4cb3d-113">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="4cb3d-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
