---
title: Node.js 用 Azure Power BI Embedded モジュール
description: Node.js 用 Azure Power BI Embedded モジュールのリファレンス
author: markingmyname
ms.author: maghan
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 58251dd1cd3a672a5167193f74d311952d70e84e
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "49656259"
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a><span data-ttu-id="30375-103">Node.js 用 Azure Power BI Embedded モジュール</span><span class="sxs-lookup"><span data-stu-id="30375-103">Azure PowerBI Embedded modules for Node.js</span></span>

<span data-ttu-id="30375-104">Azure Power BI Embedded サービスを使用すると、ノード アプリケーションに Power BI レポートをすぐに統合し、グラフやレポートを作成または編集することができます。</span><span class="sxs-lookup"><span data-stu-id="30375-104">With the Power BI Embedded Azure service, you can integrate Power BI reports right into your node application to create or edit charts and reports.</span></span>

<span data-ttu-id="30375-105">Power BI Embedded の詳細については、[こちら](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30375-105">Learn more about [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span></span>

## <a name="management-package"></a><span data-ttu-id="30375-106">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="30375-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="30375-107">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="30375-107">Install the npm module</span></span>

<span data-ttu-id="30375-108">Azure Power BI の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="30375-108">Install the Azure Power BI npm module</span></span>

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a><span data-ttu-id="30375-109">例</span><span class="sxs-lookup"><span data-stu-id="30375-109">Example</span></span>

<span data-ttu-id="30375-110">この例では、既存のリソース グループにワークスペース コレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="30375-110">This example creates a workspace collection in an existing resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="30375-111">サンプル</span><span class="sxs-lookup"><span data-stu-id="30375-111">Samples</span></span>

<span data-ttu-id="30375-112">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="30375-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
