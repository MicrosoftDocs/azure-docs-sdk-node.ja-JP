---
title: Node.js 用 Azure DevTest Labs モジュール
description: Node.js 用 Azure DevTest Labs モジュールのリファレンス
author: craigcaseyMSFT
ms.author: v-craic
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 4528bf6a09bc86d23bfec982988added1aa3e257
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2018
ms.locfileid: "52133755"
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a><span data-ttu-id="0e496-103">Node.js 用 Azure DevTest Labs モジュール</span><span class="sxs-lookup"><span data-stu-id="0e496-103">Azure DevTest Labs modules for Node.js</span></span>

<span data-ttu-id="0e496-104">Azure DevTest Labs は、無駄を最小限に抑え、コストを管理しつつ、Azure で迅速に環境を作成するためのサポートを開発者とテスト担当者に提供するサービスです。</span><span class="sxs-lookup"><span data-stu-id="0e496-104">Azure DevTest Labs is a service that helps developers and testers quickly create environments in Azure while minimizing waste and controlling cost.</span></span> <span data-ttu-id="0e496-105">再利用可能なテンプレートとアーティファクトを使用して Windows と Linux の環境を迅速にプロビジョニングすることで、アプリケーションの最新バージョンをテストできます。</span><span class="sxs-lookup"><span data-stu-id="0e496-105">You can test the latest version of your application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.</span></span> <span data-ttu-id="0e496-106">デプロイ パイプラインと DevTest ラボを簡単に統合し、オンデマンドの環境をプロビジョニングします。</span><span class="sxs-lookup"><span data-stu-id="0e496-106">Easily integrate your deployment pipeline with DevTest Labs to provision on-demand environments.</span></span> <span data-ttu-id="0e496-107">複数のテスト エージェントをプロビジョニングしてロード テストをスケール アップし、トレーニングおよびデモの事前プロビジョニング済み環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="0e496-107">Scale up your load testing by provisioning multiple test agents, and create pre-provisioned environments for training and demos.</span></span>

## <a name="management-package"></a><span data-ttu-id="0e496-108">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="0e496-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0e496-109">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="0e496-109">Install the npm module</span></span>

<span data-ttu-id="0e496-110">Azure DevTest Labs の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="0e496-110">Install the Azure DevTest Labs npm module</span></span>

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a><span data-ttu-id="0e496-111">例</span><span class="sxs-lookup"><span data-stu-id="0e496-111">Example</span></span>

<span data-ttu-id="0e496-112">この例では、ラボの詳細を取得して出力します。</span><span class="sxs-lookup"><span data-stu-id="0e496-112">This example gets and prints the details of a lab.</span></span>

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

## <a name="samples"></a><span data-ttu-id="0e496-113">サンプル</span><span class="sxs-lookup"><span data-stu-id="0e496-113">Samples</span></span>

<span data-ttu-id="0e496-114">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="0e496-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
