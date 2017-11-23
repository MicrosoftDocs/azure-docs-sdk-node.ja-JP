---
title: "Node.js 用 Azure DevTest Labs モジュール"
description: "Node.js 用 Azure DevTest Labs モジュールのリファレンス"
keywords: Azure,SDK,API,DevTest Labs, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 933ce8971e02c2898d296112282169b8c7dca1c7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a><span data-ttu-id="f8468-104">Node.js 用 Azure DevTest Labs モジュール</span><span class="sxs-lookup"><span data-stu-id="f8468-104">Azure DevTest Labs modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f8468-105">概要</span><span class="sxs-lookup"><span data-stu-id="f8468-105">Overview</span></span>

<span data-ttu-id="f8468-106">Azure DevTest Labs は、無駄を最小限に抑え、コストを管理しつつ、Azure で迅速に環境を作成するためのサポートを開発者とテスト担当者に提供するサービスです。</span><span class="sxs-lookup"><span data-stu-id="f8468-106">Azure DevTest Labs is a service that helps developers and testers quickly create environments in Azure while minimizing waste and controlling cost.</span></span> <span data-ttu-id="f8468-107">再利用可能なテンプレートとアーティファクトを使用して Windows と Linux の環境を迅速にプロビジョニングすることで、アプリケーションの最新バージョンをテストできます。</span><span class="sxs-lookup"><span data-stu-id="f8468-107">You can test the latest version of your application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.</span></span> <span data-ttu-id="f8468-108">デプロイ パイプラインと DevTest ラボを簡単に統合し、オンデマンドの環境をプロビジョニングします。</span><span class="sxs-lookup"><span data-stu-id="f8468-108">Easily integrate your deployment pipeline with DevTest Labs to provision on-demand environments.</span></span> <span data-ttu-id="f8468-109">複数のテスト エージェントをプロビジョニングしてロード テストをスケール アップし、トレーニングおよびデモの事前プロビジョニング済み環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="f8468-109">Scale up your load testing by provisioning multiple test agents, and create pre-provisioned environments for training and demos.</span></span>

## <a name="management-package"></a><span data-ttu-id="f8468-110">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="f8468-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f8468-111">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="f8468-111">Install the npm module</span></span>

<span data-ttu-id="f8468-112">Azure DevTest Labs の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="f8468-112">Install the Azure DevTest Labs npm module</span></span>

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a><span data-ttu-id="f8468-113">例</span><span class="sxs-lookup"><span data-stu-id="f8468-113">Example</span></span>

<span data-ttu-id="f8468-114">この例では、ラボの詳細を取得して出力します。</span><span class="sxs-lookup"><span data-stu-id="f8468-114">This example gets and prints the details of a lab.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const DevTestLabsClient = require('azure-arm-devtestlabs');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';
const labName = 'your-lab-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DevTestLabsClient(credentials, subscriptionId);
    return client.labOperations.getResource(resourceGroupName, labName);
  })
  .then(lab => {
    console.log('Details of lab:');
    console.dir(lab, { depth: null, colors: true });
  });


```

## <a name="samples"></a><span data-ttu-id="f8468-115">サンプル</span><span class="sxs-lookup"><span data-stu-id="f8468-115">Samples</span></span>

<span data-ttu-id="f8468-116">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="f8468-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
