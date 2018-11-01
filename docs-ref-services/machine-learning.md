---
title: Node.js 用 Azure Machine Learning モジュール
description: Node.js 用 Azure Machine Learning モジュールのリファレンス
author: hning86
ms.author: haining
manager: mwinkle
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 7e39084c65a40e47ed61cc01daf994aff447690e
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2018
ms.locfileid: "50270561"
---
# <a name="azure-machine-learning-modules-for-nodejs"></a><span data-ttu-id="de66b-103">Node.js 用 Azure Machine Learning モジュール</span><span class="sxs-lookup"><span data-stu-id="de66b-103">Azure Machine Learning modules for Node.js</span></span>

<span data-ttu-id="de66b-104">機械学習は、将来の動き、結果、傾向を予測するためにコンピューターで既存のデータからの学習を行う、データ サイエンスの手法の 1 つ です。</span><span class="sxs-lookup"><span data-stu-id="de66b-104">Machine learning is a technique of data science that helps computers learn from existing data in order to forecast future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="de66b-105">機械学習からのこうした予想や予測によってアプリやデバイスの機能性を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="de66b-105">These forecasts or predictions from machine learning can make apps and devices smarter.</span></span> <span data-ttu-id="de66b-106">オンライン ショッピングでは、ユーザーが今までに購入した製品に基づいて他の商品をお勧めするのに機械学習が役立っています。</span><span class="sxs-lookup"><span data-stu-id="de66b-106">When you shop online, machine learning helps recommend other products you might like based on what you've purchased.</span></span> <span data-ttu-id="de66b-107">クレジット カードが読み取られると、機械学習は、トランザクションをトランザクションのデータベースと比較し、不正の検出を支援します。</span><span class="sxs-lookup"><span data-stu-id="de66b-107">When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud.</span></span> <span data-ttu-id="de66b-108">ロボット掃除機が部屋を掃除するとき、機械学習は、作業が行われているかどうかを判断するのを支援します。</span><span class="sxs-lookup"><span data-stu-id="de66b-108">When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.</span></span>

## <a name="management-package"></a><span data-ttu-id="de66b-109">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="de66b-109">Management Package</span></span>


### <a name="install-the-npm-module"></a><span data-ttu-id="de66b-110">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="de66b-110">Install the npm module</span></span>

<span data-ttu-id="de66b-111">Azure Machine Learning の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="de66b-111">Install the Azure Machine Learning npm module</span></span>

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a><span data-ttu-id="de66b-112">例</span><span class="sxs-lookup"><span data-stu-id="de66b-112">Example</span></span>

<span data-ttu-id="de66b-113">この例では、Machine Learning コミットメント プランをすべて一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="de66b-113">This example lists all machine learning committment plans.</span></span>

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

## <a name="samples"></a><span data-ttu-id="de66b-114">サンプル</span><span class="sxs-lookup"><span data-stu-id="de66b-114">Samples</span></span>

<span data-ttu-id="de66b-115">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="de66b-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
