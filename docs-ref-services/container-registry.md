---
title: "Node.js 用 Azure Container Registry モジュール"
description: "Node.js 用 Azure Container Registry モジュールのリファレンス"
keywords: Azure,SDK,API,Container Registry, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: 6ded68c19971a8fe580f440862d0fe05a1def6a2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="28ade-104">Node.js 用 Azure Container Registry モジュール</span><span class="sxs-lookup"><span data-stu-id="28ade-104">Azure Container Registry modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="28ade-105">概要</span><span class="sxs-lookup"><span data-stu-id="28ade-105">Overview</span></span>

<span data-ttu-id="28ade-106">Azure Container Registry は、オープンソースの Docker Registry 2.0 に基づいた、管理された Docker レジストリ サービスです。</span><span class="sxs-lookup"><span data-stu-id="28ade-106">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="28ade-107">プライベート Docker コンテナー イメージを保存および管理する Azure コンテナー レジストリを作成および管理します。</span><span class="sxs-lookup"><span data-stu-id="28ade-107">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="28ade-108">既存のコンテナーの開発とデプロイ パイプラインで Azure のコンテナー レジストリを使用し、Docker コミュニティの専門知識を活用します。</span><span class="sxs-lookup"><span data-stu-id="28ade-108">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="28ade-109">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="28ade-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="28ade-110">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="28ade-110">Install the npm module</span></span>

<span data-ttu-id="28ade-111">Azure Container Registry の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="28ade-111">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="28ade-112">例</span><span class="sxs-lookup"><span data-stu-id="28ade-112">Example</span></span>

<span data-ttu-id="28ade-113">この例では、利用可能なコンテナーの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="28ade-113">This example gets a list of the available containers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="28ade-114">サンプル</span><span class="sxs-lookup"><span data-stu-id="28ade-114">Samples</span></span>

<span data-ttu-id="28ade-115">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="28ade-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
