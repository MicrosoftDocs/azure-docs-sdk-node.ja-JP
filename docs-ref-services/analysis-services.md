---
title: Node.js 用 Azure Analysis Services モジュール
description: Node.js 用 Azure Analysis Services モジュールのリファレンス
author: Minewiskan
ms.author: owend
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: 5214cd2f171074ba330bc639643dfba490540856
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2018
ms.locfileid: "52008666"
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="69af0-103">Node.js 用 Azure Analysis Services モジュール</span><span class="sxs-lookup"><span data-stu-id="69af0-103">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="69af0-104">概要</span><span class="sxs-lookup"><span data-stu-id="69af0-104">Overview</span></span>
<span data-ttu-id="69af0-105">このパッケージには、Microsoft Azure Analysis Services の管理を省力化する Node.js モジュールが備わっています。</span><span class="sxs-lookup"><span data-stu-id="69af0-105">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="69af0-106">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="69af0-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="69af0-107">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="69af0-107">Install the npm module</span></span>

<span data-ttu-id="69af0-108">Azure Analysis Services の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="69af0-108">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="69af0-109">例</span><span class="sxs-lookup"><span data-stu-id="69af0-109">Example</span></span>

<span data-ttu-id="69af0-110">この例では、利用可能なすべての Analysis Services サーバーを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="69af0-110">This example lists all available Analysis Service servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="69af0-111">サンプル</span><span class="sxs-lookup"><span data-stu-id="69af0-111">Samples</span></span>

<span data-ttu-id="69af0-112">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="69af0-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
