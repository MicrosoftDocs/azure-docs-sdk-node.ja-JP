---
title: "Node.js 用 Azure Machine Learning モジュール"
description: "Node.js 用 Azure Machine Learning モジュールのリファレンス"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 82f731971505250f1d637ae32b4c7a83ff24fccf
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2018
---
# <a name="azure-machine-learning-modules-for-nodejs"></a><span data-ttu-id="0686c-103">Node.js 用 Azure Machine Learning モジュール</span><span class="sxs-lookup"><span data-stu-id="0686c-103">Azure Machine Learning modules for Node.js</span></span>

<span data-ttu-id="0686c-104">機械学習は、将来の動き、結果、傾向を予測するためにコンピューターで既存のデータからの学習を行う、データ サイエンスの手法の 1 つ です。</span><span class="sxs-lookup"><span data-stu-id="0686c-104">Machine learning is a technique of data science that helps computers learn from existing data in order to forecast future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="0686c-105">機械学習からのこうした予想や予測によってアプリやデバイスの機能性を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="0686c-105">These forecasts or predictions from machine learning can make apps and devices smarter.</span></span> <span data-ttu-id="0686c-106">オンライン ショッピングでは、ユーザーが今までに購入した製品に基づいて他の商品をお勧めするのに機械学習が役立っています。</span><span class="sxs-lookup"><span data-stu-id="0686c-106">When you shop online, machine learning helps recommend other products you might like based on what you've purchased.</span></span> <span data-ttu-id="0686c-107">クレジット カードが読み取られると、機械学習は、トランザクションをトランザクションのデータベースと比較し、不正の検出を支援します。</span><span class="sxs-lookup"><span data-stu-id="0686c-107">When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud.</span></span> <span data-ttu-id="0686c-108">ロボット掃除機が部屋を掃除するとき、機械学習は、作業が行われているかどうかを判断するのを支援します。</span><span class="sxs-lookup"><span data-stu-id="0686c-108">When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.</span></span>

## <a name="management-package"></a><span data-ttu-id="0686c-109">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="0686c-109">Management Package</span></span>


### <a name="install-the-npm-module"></a><span data-ttu-id="0686c-110">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="0686c-110">Install the npm module</span></span>

<span data-ttu-id="0686c-111">Azure Machine Learning の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="0686c-111">Install the Azure Machine Learning npm module</span></span>

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a><span data-ttu-id="0686c-112">例</span><span class="sxs-lookup"><span data-stu-id="0686c-112">Example</span></span>

<span data-ttu-id="0686c-113">この例では、Machine Learning コミットメント プランをすべて一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="0686c-113">This example lists all machine learning committment plans.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const MachineLearningManagement = require('azure-arm-machinelearning');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new MachineLearningManagement.CommitmentPlansManagementClient(
      credentials,
      subscriptionId
    );
    return client.commitmentPlans.list();
  })
  .then(commitmentPlans => {
    console.log('List of commitmentPlans:');
    console.dir(commitmentPlans, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="0686c-114">サンプル</span><span class="sxs-lookup"><span data-stu-id="0686c-114">Samples</span></span>

<span data-ttu-id="0686c-115">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="0686c-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
