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
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2018
ms.locfileid: "50339980"
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="fddd7-103">Node.js 用 Azure Analysis Services モジュール</span><span class="sxs-lookup"><span data-stu-id="fddd7-103">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="fddd7-104">概要</span><span class="sxs-lookup"><span data-stu-id="fddd7-104">Overview</span></span>
<span data-ttu-id="fddd7-105">このパッケージには、Microsoft Azure Analysis Services の管理を省力化する Node.js モジュールが備わっています。</span><span class="sxs-lookup"><span data-stu-id="fddd7-105">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="fddd7-106">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="fddd7-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="fddd7-107">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="fddd7-107">Install the npm module</span></span>

<span data-ttu-id="fddd7-108">Azure Analysis Services の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="fddd7-108">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="fddd7-109">例</span><span class="sxs-lookup"><span data-stu-id="fddd7-109">Example</span></span>

<span data-ttu-id="fddd7-110">この例では、利用可能なすべての Analysis Services サーバーを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="fddd7-110">This example lists all available Analysis Service servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="fddd7-111">サンプル</span><span class="sxs-lookup"><span data-stu-id="fddd7-111">Samples</span></span>

<span data-ttu-id="fddd7-112">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="fddd7-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
