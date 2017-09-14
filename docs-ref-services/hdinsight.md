---
title: "Node.js 用 Azure HDInsight モジュール"
description: "Node.js 用 Azure HDInsight モジュールのリファレンス"
keywords: Azure,SDK,API,HDInsight, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 1df988e98def42dcf33e90b4c3debece8cbe85e3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="ebe2e-104">Node.js 用 Azure HDInsight モジュール</span><span class="sxs-lookup"><span data-stu-id="ebe2e-104">Azure HDInsight Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="ebe2e-105">概要</span><span class="sxs-lookup"><span data-stu-id="ebe2e-105">Overview</span></span>

<span data-ttu-id="ebe2e-106">Azure HDInsight は、Hortonworks Data Platform (HDP) の Hadoop コンポーネントのクラウド ディストリビューションです。</span><span class="sxs-lookup"><span data-stu-id="ebe2e-106">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="ebe2e-107">Apache Hadoop は本来、コンピューターのクラスターでのビッグ データ セットの分散処理および分析のためのオープンソース フレームワークでした。</span><span class="sxs-lookup"><span data-stu-id="ebe2e-107">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="ebe2e-108">HDInsight は、Hadoop テクノロジを使いやすくしたもので、次の特徴を備えています。</span><span class="sxs-lookup"><span data-stu-id="ebe2e-108">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="ebe2e-109">簡単なセットアップと構成。</span><span class="sxs-lookup"><span data-stu-id="ebe2e-109">Less setup and configuration.</span></span> <span data-ttu-id="ebe2e-110">HDInsight での Hadoop クラスターのプロビジョニングに関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebe2e-110">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="ebe2e-111">高い可用性と信頼性。</span><span class="sxs-lookup"><span data-stu-id="ebe2e-111">High availability and reliability.</span></span> <span data-ttu-id="ebe2e-112">HDInsight の可用性と信頼性に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebe2e-112">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="ebe2e-113">Active Directory との統合を通じたセキュリティとガバナンス。</span><span class="sxs-lookup"><span data-stu-id="ebe2e-113">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="ebe2e-114">ドメインに参加しているクラスターに関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebe2e-114">See Domain-joined clusters.</span></span>
- <span data-ttu-id="ebe2e-115">ジョブの中断のない動的スケーリング</span><span class="sxs-lookup"><span data-stu-id="ebe2e-115">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="ebe2e-116">コンポーネントの更新と現在のバージョン。</span><span class="sxs-lookup"><span data-stu-id="ebe2e-116">Component updates and current versions.</span></span> <span data-ttu-id="ebe2e-117">HDInsight での Hadoop のコンポーネントとバージョンに関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebe2e-117">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="ebe2e-118">Web Apps や SQL Database などの他の Azure サービスとの統合</span><span class="sxs-lookup"><span data-stu-id="ebe2e-118">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="ebe2e-119">Hadoop テクノロジ スタックには、Apache Hive、HBase、Spark、Kafka、その他の多くの関連するソフトウェアおよびユーティリティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ebe2e-119">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="ebe2e-120">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="ebe2e-120">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="ebe2e-121">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="ebe2e-121">Install the npm modules</span></span>

<span data-ttu-id="ebe2e-122">Node.js 用 Azure HDInsight モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="ebe2e-122">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="ebe2e-123">例</span><span class="sxs-lookup"><span data-stu-id="ebe2e-123">Example</span></span> 

<span data-ttu-id="ebe2e-124">この例では、HD Insight クライアントを作成し、利用可能なクラスターをすべて一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ebe2e-124">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

```javascript
const msRestAzure = require('ms-rest-azure');
const HDInsightManagementClient = require('azure-arm-hdinsight');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = HDInsightManagementClient.createHDInsightManagementClient(
        credentials
    );

    credentials.subscriptionId = subscriptionId;

    client.clusters.list((err, result) => {
        console.log(result);
    });
});
```

## <a name="samples"></a><span data-ttu-id="ebe2e-125">サンプル</span><span class="sxs-lookup"><span data-stu-id="ebe2e-125">Samples</span></span>

<span data-ttu-id="ebe2e-126">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="ebe2e-126">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
