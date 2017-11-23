---
title: "Node.js 用 Azure Power BI Embedded モジュール"
description: "Node.js 用 Azure Power BI Embedded モジュールのリファレンス"
keywords: Azure,SDK,API,Power BI Embedded, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 74e69421d372ff4ccaebf2b811152dd83b9b4e7b
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a><span data-ttu-id="d7ff1-104">Node.js 用 Azure Power BI Embedded モジュール</span><span class="sxs-lookup"><span data-stu-id="d7ff1-104">Azure PowerBI Embedded modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d7ff1-105">概要</span><span class="sxs-lookup"><span data-stu-id="d7ff1-105">Overview</span></span>

<span data-ttu-id="d7ff1-106">Azure Power BI Embedded サービスを使用すると、ノード アプリケーションに Power BI レポートをすぐに統合し、グラフやレポートを作成または編集することができます。</span><span class="sxs-lookup"><span data-stu-id="d7ff1-106">With the Power BI Embedded Azure service, you can integrate Power BI reports right into your node application to create or edit charts and reports.</span></span>

<span data-ttu-id="d7ff1-107">Power BI Embedded の詳細については、[こちら](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7ff1-107">Learn more about [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span></span>

## <a name="management-package"></a><span data-ttu-id="d7ff1-108">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="d7ff1-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d7ff1-109">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="d7ff1-109">Install the npm module</span></span>

<span data-ttu-id="d7ff1-110">Azure Power BI の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d7ff1-110">Install the Azure Power BI npm module</span></span>

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a><span data-ttu-id="d7ff1-111">例</span><span class="sxs-lookup"><span data-stu-id="d7ff1-111">Example</span></span>

<span data-ttu-id="d7ff1-112">この例では、既存のリソース グループにワークスペース コレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d7ff1-112">This example creates a workspace collection in an existing resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const PowerBIEmbeddedManagementClient = require('azure-arm-powerbiembedded');

const creationOptions = {
  location: 'northcentralus',
  tags: {
    key1: 'value1',
    key2: 'value2'
  },
  sku: {
    name: 'S1',
    teir: 'Standard'
  }
};

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';
const workspace = 'workspace-collection-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new PowerBIEmbeddedManagementClient(
      credentials,
      subscriptionId
    );
    return client.workspaceCollections.create(
      resourceGroup,
      workspace,
      creationOptions
    );
  })
  .then(workspaces => console.dir(workspaces, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="d7ff1-113">サンプル</span><span class="sxs-lookup"><span data-stu-id="d7ff1-113">Samples</span></span>

<span data-ttu-id="d7ff1-114">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="d7ff1-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
