---
title: "Node.js 用 Azure Cognitive Services モジュール"
description: "Node.js 用 Azure Cognitive Services モジュールのリファレンス"
keywords: Azure,SDK,API,Cognitive Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fba98930fccaf4fa40dd1d0224031276f5fb7f84
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a><span data-ttu-id="d11bf-104">Node.js 用 Azure Cognitive Services モジュール</span><span class="sxs-lookup"><span data-stu-id="d11bf-104">Azure Cognitive Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d11bf-105">概要</span><span class="sxs-lookup"><span data-stu-id="d11bf-105">Overview</span></span>

<span data-ttu-id="d11bf-106">Azure Cognitive Services は、よりインテリジェントで魅力的、かつ発見可能性を高めたアプリケーションの開発を支援する API、SDK、サービスをセットにしたものです。</span><span class="sxs-lookup"><span data-stu-id="d11bf-106">Azure Cognitive Services is a set of APIs, SDKs, and services available to developers to make their applications more intelligent, engaging and discoverable.</span></span> <span data-ttu-id="d11bf-107">Microsoft の絶えず進化する機械学習 API 群をさらに発展させた Microsoft Cognitive Services を通じて、開発者はそのアプリケーションに感情認識や映像検出、顔認識、音声認識、視覚認識、音声理解、言語理解など、インテリジェントな機能を簡単に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="d11bf-107">Microsoft Cognitive Services expands on Microsoft’s evolving portfolio of machine learning APIs and enables developers to easily add intelligent features – such as emotion and video detection; facial, speech and vision recognition; and speech and language understanding – into their applications.</span></span> <span data-ttu-id="d11bf-108">Microsoft が目指しているのは、見たり聞いたり話したり理解したりする機能、そして論理的な思考まで備えようとしているシステムを通じて、よりパーソナライズされたコンピューティング体験と生産性の向上を実現することです。</span><span class="sxs-lookup"><span data-stu-id="d11bf-108">Our vision is for more personal computing experiences and enhanced productivity aided by systems that increasingly can see, hear, speak, understand and even begin to reason.</span></span>

## <a name="management-package"></a><span data-ttu-id="d11bf-109">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="d11bf-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d11bf-110">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="d11bf-110">Install the npm module</span></span>

<span data-ttu-id="d11bf-111">Azure Cognitive Services の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d11bf-111">Install the Azure Cognitive Services npm module</span></span>

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a><span data-ttu-id="d11bf-112">例</span><span class="sxs-lookup"><span data-stu-id="d11bf-112">Example</span></span>

<span data-ttu-id="d11bf-113">この例では、すべての Cognitive Services アカウントを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="d11bf-113">This example lists all cognitive service accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const cognitiveServicesManagementClient = require('azure-arm-cognitiveservices');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const cognitiveServicesClient = new cognitiveServicesManagementClient(
      credentials,
      subscriptionId
    );
    return cognitiveServicesClient.cognitiveServicesAccounts.list();
  })
  .then(cognitiveServicesAccounts => {
    console.log('List of accounts:');
    console.dir(cognitiveServicesAccounts, { depth: null, colors: true });    
  });

```

## <a name="samples"></a><span data-ttu-id="d11bf-114">サンプル</span><span class="sxs-lookup"><span data-stu-id="d11bf-114">Samples</span></span>

<span data-ttu-id="d11bf-115">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="d11bf-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
