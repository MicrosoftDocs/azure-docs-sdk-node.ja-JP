---
title: Node.js 用 Azure Advisor モジュール
description: Node.js 用 Azure Advisor モジュールのリファレンス
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 54686220006d27341dbb50a249d0b2f44411b112
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2018
ms.locfileid: "50310929"
---
# <a name="azure-advisor-modules-for-nodejs"></a><span data-ttu-id="0a6d6-103">Node.js 用 Azure Advisor モジュール</span><span class="sxs-lookup"><span data-stu-id="0a6d6-103">Azure Advisor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="0a6d6-104">概要</span><span class="sxs-lookup"><span data-stu-id="0a6d6-104">Overview</span></span>

<span data-ttu-id="0a6d6-105">Azure Advisor は、ベスト プラクティスに従って Azure デプロイメントを最適化できるようにする、個人用に設定されたクラウド コンサルタントです。</span><span class="sxs-lookup"><span data-stu-id="0a6d6-105">Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments.</span></span> <span data-ttu-id="0a6d6-106">Azure のリソースの構成と利用統計情報を分析し、Azure リソースの費用対効果、パフォーマンス、高可用性、セキュリティを向上させるために役立つソリューションを推奨します。</span><span class="sxs-lookup"><span data-stu-id="0a6d6-106">Advisor analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve the cost effectiveness, performance, high availability, and security of your Azure resources.</span></span>

<span data-ttu-id="0a6d6-107">Advisor では、以下の項目を実行できます。</span><span class="sxs-lookup"><span data-stu-id="0a6d6-107">With Advisor, you can:</span></span>
- <span data-ttu-id="0a6d6-108">先の見通しを持ち、処理が可能で、個人用に設定されたベスト プラクティスの推奨事項を取得する。</span><span class="sxs-lookup"><span data-stu-id="0a6d6-108">Get proactive, actionable, and personalized best practices recommendations.</span></span>
- <span data-ttu-id="0a6d6-109">リソースのパフォーマンス、セキュリティ、および高可用性を向上させながら、総合的な Azure の支出を削減する機会を捉える。</span><span class="sxs-lookup"><span data-stu-id="0a6d6-109">Improve the performance, security, and high availability of your resources, as you identify opportunities to reduce your overall Azure spend.</span></span>
- <span data-ttu-id="0a6d6-110">アクション提案をインラインで含めた推奨事項を取得する。</span><span class="sxs-lookup"><span data-stu-id="0a6d6-110">Get recommendations with proposed actions inline.</span></span>

## <a name="management-package"></a><span data-ttu-id="0a6d6-111">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="0a6d6-111">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0a6d6-112">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="0a6d6-112">Install the npm module</span></span>

<span data-ttu-id="0a6d6-113">Azure Advisor の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="0a6d6-113">Install the Azure Advisor npm module</span></span>

```bash
npm install azure-arm-advisor
```

### <a name="example"></a><span data-ttu-id="0a6d6-114">例</span><span class="sxs-lookup"><span data-stu-id="0a6d6-114">Example</span></span>

<span data-ttu-id="0a6d6-115">この例では、Azure Advisor からの推奨事項を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="0a6d6-115">This example displays the list of recommendations from Azure Advisor.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const advisorManagement = require('azure-arm-advisor');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new advisorManagement(credentials, subscriptionId);
  client.recommendations.list().then(recommendations => {
    console.log('List of recommendations:');
    console.dir(recommendations, {depth: null, colors: true});
  });
});
```

## <a name="samples"></a><span data-ttu-id="0a6d6-116">サンプル</span><span class="sxs-lookup"><span data-stu-id="0a6d6-116">Samples</span></span>

<span data-ttu-id="0a6d6-117">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="0a6d6-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
