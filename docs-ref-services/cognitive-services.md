---
title: "Node.js 用 Azure Cognitive Services モジュール"
description: "Node.js 用 Azure Cognitive Services モジュールのリファレンス"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: df6ea913ca69341fbbb730b75f547ce9c10bd45f
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2018
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a><span data-ttu-id="8e863-103">Node.js 用 Azure Cognitive Services モジュール</span><span class="sxs-lookup"><span data-stu-id="8e863-103">Azure Cognitive Services modules for Node.js</span></span>

<span data-ttu-id="8e863-104">Azure Cognitive Services は、よりインテリジェントで魅力的、かつ発見可能性を高めたアプリケーションの開発を支援する API、SDK、サービスをセットにしたものです。</span><span class="sxs-lookup"><span data-stu-id="8e863-104">Azure Cognitive Services is a set of APIs, SDKs, and services available to developers to make their applications more intelligent, engaging and discoverable.</span></span> <span data-ttu-id="8e863-105">Microsoft の絶えず進化する機械学習 API 群をさらに発展させた Microsoft Cognitive Services を通じて、開発者はそのアプリケーションに感情認識や映像検出、顔認識、音声認識、視覚認識、音声理解、言語理解など、インテリジェントな機能を簡単に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="8e863-105">Microsoft Cognitive Services expands on Microsoft’s evolving portfolio of machine learning APIs and enables developers to easily add intelligent features – such as emotion and video detection; facial, speech and vision recognition; and speech and language understanding – into their applications.</span></span> <span data-ttu-id="8e863-106">Microsoft が目指しているのは、見たり聞いたり話したり理解したりする機能、そして論理的な思考まで備えようとしているシステムを通じて、よりパーソナライズされたコンピューティング体験と生産性の向上を実現することです。</span><span class="sxs-lookup"><span data-stu-id="8e863-106">Our vision is for more personal computing experiences and enhanced productivity aided by systems that increasingly can see, hear, speak, understand and even begin to reason.</span></span>

## <a name="management-package"></a><span data-ttu-id="8e863-107">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="8e863-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="8e863-108">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="8e863-108">Install the npm module</span></span>

<span data-ttu-id="8e863-109">Azure Cognitive Services の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="8e863-109">Install the Azure Cognitive Services npm module</span></span>

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a><span data-ttu-id="8e863-110">例</span><span class="sxs-lookup"><span data-stu-id="8e863-110">Example</span></span>

<span data-ttu-id="8e863-111">この例では、すべての Cognitive Services アカウントを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="8e863-111">This example lists all cognitive service accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="8e863-112">サンプル</span><span class="sxs-lookup"><span data-stu-id="8e863-112">Samples</span></span>

<span data-ttu-id="8e863-113">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="8e863-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
