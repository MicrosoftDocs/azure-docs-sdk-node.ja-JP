---
title: Node.js 用 Azure Data Lake Analytics モジュール
description: Node.js 用 Azure Data Lake Analytics モジュールのリファレンス
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Analytics
ms.openlocfilehash: 28dae604ae9977eb33470757e207ac12a592c676
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2018
ms.locfileid: "28116967"
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a><span data-ttu-id="0c723-103">Node.js 用 Azure Data Lake Analytics モジュール</span><span class="sxs-lookup"><span data-stu-id="0c723-103">Azure Data Lake Analytics modules for Node.js</span></span>

<span data-ttu-id="0c723-104">Azure Data Lake Analytics は、ビッグ データ分析を簡略化するオンデマンド分析ジョブ サービスです。</span><span class="sxs-lookup"><span data-stu-id="0c723-104">Azure Data Lake Analytics is an on-demand analytics job service to simplify big data analytics.</span></span> <span data-ttu-id="0c723-105">分散インフラストラクチャの運用ではなく、ジョブの記述、実行、および管理に集中できます。</span><span class="sxs-lookup"><span data-stu-id="0c723-105">You can focus on writing, running, and managing jobs rather than on operating distributed infrastructure.</span></span> <span data-ttu-id="0c723-106">ハードウェアのデプロイ、構成、チューニングを行う代わりに、クエリを作成してデータを変換し、価値ある洞察を抽出します。</span><span class="sxs-lookup"><span data-stu-id="0c723-106">Instead of deploying, configuring, and tuning hardware, you write queries to transform your data and extract valuable insights.</span></span> <span data-ttu-id="0c723-107">この分析サービスでは、必要な性能をダイヤルで設定して、どのような規模のジョブでも即座に処理できます。</span><span class="sxs-lookup"><span data-stu-id="0c723-107">The analytics service can handle jobs of any scale instantly by setting the dial for how much power you need.</span></span> <span data-ttu-id="0c723-108">ジョブの実行中にのみ課金されるコスト効率の良いサービスです。</span><span class="sxs-lookup"><span data-stu-id="0c723-108">You only pay for your job when it is running, making it cost-effective.</span></span> <span data-ttu-id="0c723-109">この分析サービスは Azure Active Directory をサポートしているので、既存のオンプレミスの ID システムと統合してアクセス権限とロールを管理できます。</span><span class="sxs-lookup"><span data-stu-id="0c723-109">The analytics service supports Azure Active Directory letting you manage access and roles, integrated with your on-premises identity system.</span></span> <span data-ttu-id="0c723-110">また、SQL のメリットとユーザー コードの表現力を融合した U-SQL 言語が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="0c723-110">It also includes U-SQL, a language that unifies the benefits of SQL with the expressive power of user code.</span></span> <span data-ttu-id="0c723-111">U-SQL のスケーラブルな分散ランタイムで、Azure の SQL Server、Azure SQL Database、Azure SQL Data Warehouse にまたがるストア内のデータを効率良く分析できます。</span><span class="sxs-lookup"><span data-stu-id="0c723-111">U-SQL’s scalable distributed runtime enables you to efficiently analyze data in the store and across SQL Servers in Azure, Azure SQL Database, and Azure SQL Data Warehouse.</span></span>

### <a name="management-package"></a><span data-ttu-id="0c723-112">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="0c723-112">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0c723-113">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="0c723-113">Install the npm module</span></span>

<span data-ttu-id="0c723-114">Node.js 用 Azure Data Lake Analytics モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="0c723-114">Use npm to install the Azure Data Lake Analytics modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a><span data-ttu-id="0c723-115">例</span><span class="sxs-lookup"><span data-stu-id="0c723-115">Example</span></span>

<span data-ttu-id="0c723-116">この例では、特定のサブスクリプションのすべての Analytics アカウントを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="0c723-116">This example lists all of the analytics accounts for a given subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="0c723-117">サンプル</span><span class="sxs-lookup"><span data-stu-id="0c723-117">Samples</span></span>

<span data-ttu-id="0c723-118">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="0c723-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
