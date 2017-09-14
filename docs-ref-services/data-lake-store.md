---
title: "Node.js 用 Azure Data Lake Store モジュール"
description: "Node.js 用 Azure Data Lake Store モジュールのリファレンス"
keywords: Azure,SDK,API,Data Lake Store, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: 5885bf8f073e4f4f1ac2be88b8691b092e8a21d3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="b4116-104">Node.js 用 Azure Data Lake Store モジュール</span><span class="sxs-lookup"><span data-stu-id="b4116-104">Azure Data Lake Store modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b4116-105">概要</span><span class="sxs-lookup"><span data-stu-id="b4116-105">Overview</span></span>
<span data-ttu-id="b4116-106">Azure Data Lake Store は、ビッグ データの分析ワークロードに対応するエンタープライズ規模のハイパースケール リポジトリです。</span><span class="sxs-lookup"><span data-stu-id="b4116-106">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="b4116-107">Azure Data Lake を使用すると、運用分析や調査分析を目的として任意のサイズ、種類、および取り込み速度のデータを 1 か所でキャプチャすることができます。</span><span class="sxs-lookup"><span data-stu-id="b4116-107">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="b4116-108">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="b4116-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b4116-109">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="b4116-109">Install the npm module</span></span>

<span data-ttu-id="b4116-110">Node.js 用 Azure Data Lake Store モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="b4116-110">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="b4116-111">例</span><span class="sxs-lookup"><span data-stu-id="b4116-111">Example</span></span>

<span data-ttu-id="b4116-112">この例では、特定の Azure サブスクリプション内のすべての Data Lake Store アカウントを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="b4116-112">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-store');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeStoreAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a><span data-ttu-id="b4116-113">サンプル</span><span class="sxs-lookup"><span data-stu-id="b4116-113">Samples</span></span>

<span data-ttu-id="b4116-114">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="b4116-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
