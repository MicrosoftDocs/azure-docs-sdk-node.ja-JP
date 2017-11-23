---
title: "Node.js 用 Azure Data Lake Analytics モジュール"
description: "Node.js 用 Azure Data Lake Analytics モジュールのリファレンス"
keywords: Azure,SDK,API,Data Lake Analytics, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Analytics
ms.openlocfilehash: 46f414ac6909de5bd956666baf51be1ca9d25ac7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a><span data-ttu-id="ed476-104">Node.js 用 Azure Data Lake Analytics モジュール</span><span class="sxs-lookup"><span data-stu-id="ed476-104">Azure Data Lake Analytics modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="ed476-105">概要</span><span class="sxs-lookup"><span data-stu-id="ed476-105">Overview</span></span>
<span data-ttu-id="ed476-106">Azure Data Lake Analytics は、ビッグ データ分析を簡略化するオンデマンド分析ジョブ サービスです。</span><span class="sxs-lookup"><span data-stu-id="ed476-106">Azure Data Lake Analytics is an on-demand analytics job service to simplify big data analytics.</span></span> <span data-ttu-id="ed476-107">分散インフラストラクチャの運用ではなく、ジョブの記述、実行、および管理に集中できます。</span><span class="sxs-lookup"><span data-stu-id="ed476-107">You can focus on writing, running, and managing jobs rather than on operating distributed infrastructure.</span></span> <span data-ttu-id="ed476-108">ハードウェアのデプロイ、構成、チューニングを行う代わりに、クエリを作成してデータを変換し、価値ある洞察を抽出します。</span><span class="sxs-lookup"><span data-stu-id="ed476-108">Instead of deploying, configuring, and tuning hardware, you write queries to transform your data and extract valuable insights.</span></span> <span data-ttu-id="ed476-109">この分析サービスでは、必要な性能をダイヤルで設定して、どのような規模のジョブでも即座に処理できます。</span><span class="sxs-lookup"><span data-stu-id="ed476-109">The analytics service can handle jobs of any scale instantly by setting the dial for how much power you need.</span></span> <span data-ttu-id="ed476-110">ジョブの実行中にのみ課金されるコスト効率の良いサービスです。</span><span class="sxs-lookup"><span data-stu-id="ed476-110">You only pay for your job when it is running, making it cost-effective.</span></span> <span data-ttu-id="ed476-111">この分析サービスは Azure Active Directory をサポートしているので、既存のオンプレミスの ID システムと統合してアクセス権限とロールを管理できます。</span><span class="sxs-lookup"><span data-stu-id="ed476-111">The analytics service supports Azure Active Directory letting you manage access and roles, integrated with your on-premises identity system.</span></span> <span data-ttu-id="ed476-112">また、SQL のメリットとユーザー コードの表現力を融合した U-SQL 言語が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="ed476-112">It also includes U-SQL, a language that unifies the benefits of SQL with the expressive power of user code.</span></span> <span data-ttu-id="ed476-113">U-SQL のスケーラブルな分散ランタイムで、Azure の SQL Server、Azure SQL Database、Azure SQL Data Warehouse にまたがるストア内のデータを効率良く分析できます。</span><span class="sxs-lookup"><span data-stu-id="ed476-113">U-SQL’s scalable distributed runtime enables you to efficiently analyze data in the store and across SQL Servers in Azure, Azure SQL Database, and Azure SQL Data Warehouse.</span></span>

### <a name="management-package"></a><span data-ttu-id="ed476-114">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="ed476-114">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ed476-115">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="ed476-115">Install the npm module</span></span>

<span data-ttu-id="ed476-116">Node.js 用 Azure Data Lake Analytics モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="ed476-116">Use npm to install the Azure Data Lake Analytics modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a><span data-ttu-id="ed476-117">例</span><span class="sxs-lookup"><span data-stu-id="ed476-117">Example</span></span>

<span data-ttu-id="ed476-118">この例では、特定のサブスクリプションのすべての Analytics アカウントを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ed476-118">This example lists all of the analytics accounts for a given subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-analytics');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeAnalyticsAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a><span data-ttu-id="ed476-119">サンプル</span><span class="sxs-lookup"><span data-stu-id="ed476-119">Samples</span></span>

<span data-ttu-id="ed476-120">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="ed476-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
