---
title: Node.js 用 Azure Data Lake Store モジュール
description: Node.js 用 Azure Data Lake Store モジュールのリファレンス
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: da7e71a9ee1f6936924b1ec966b441756e9b0dfe
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2018
ms.locfileid: "52099027"
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="26148-103">Node.js 用 Azure Data Lake Store モジュール</span><span class="sxs-lookup"><span data-stu-id="26148-103">Azure Data Lake Store modules for Node.js</span></span>

<span data-ttu-id="26148-104">Azure Data Lake Store は、ビッグ データの分析ワークロードに対応するエンタープライズ規模のハイパースケール リポジトリです。</span><span class="sxs-lookup"><span data-stu-id="26148-104">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="26148-105">Azure Data Lake を使用すると、運用分析や調査分析を目的として任意のサイズ、種類、および取り込み速度のデータを 1 か所でキャプチャすることができます。</span><span class="sxs-lookup"><span data-stu-id="26148-105">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="26148-106">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="26148-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="26148-107">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="26148-107">Install the npm module</span></span>

<span data-ttu-id="26148-108">Node.js 用 Azure Data Lake Store モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="26148-108">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="26148-109">例</span><span class="sxs-lookup"><span data-stu-id="26148-109">Example</span></span>

<span data-ttu-id="26148-110">この例では、特定の Azure サブスクリプション内のすべての Data Lake Store アカウントを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="26148-110">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

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

## <a name="samples"></a><span data-ttu-id="26148-111">サンプル</span><span class="sxs-lookup"><span data-stu-id="26148-111">Samples</span></span>

<span data-ttu-id="26148-112">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="26148-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
