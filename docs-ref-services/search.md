---
title: Node.js 用 Azure Search モジュール
description: Node.js 用 Azure Search モジュールのリファレンス
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: 895281acd2359240f3d483e4205c628e1f85f724
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264989"
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="0c67d-103">Node.js 用 Azure Search モジュール</span><span class="sxs-lookup"><span data-stu-id="0c67d-103">Azure Search modules for Node.js</span></span>

<span data-ttu-id="0c67d-104">Azure Search は、サーバーとインフラストラクチャの管理を Microsoft に委任するクラウドの Search-as-a-service (サービスとしての検索) ソリューションです。データを取り込んだら、アプリケーションに検索機能を追加して、すぐに利用を開始できます。</span><span class="sxs-lookup"><span data-stu-id="0c67d-104">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="0c67d-105">Azure Search の詳細については、[こちら](https://docs.microsoft.com/azure/search/search-what-is-azure-search)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c67d-105">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="0c67d-106">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="0c67d-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0c67d-107">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="0c67d-107">Install the npm module</span></span>

<span data-ttu-id="0c67d-108">Azure Search の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="0c67d-108">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="0c67d-109">例</span><span class="sxs-lookup"><span data-stu-id="0c67d-109">Example</span></span>

<span data-ttu-id="0c67d-110">この例では、Azure に新しい Search サービスを作成し、そのリソース グループに含まれるリソースを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="0c67d-110">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const SearchManagement = require('azure-arm-search');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'yourResourceGroup';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SearchManagement(credentials, subscriptionId);
    return client.services.listByResourceGroup(resourceGroup);
  })
  .then(services => console.dir(services, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error ocurred');
    console.dir(err, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="0c67d-111">サンプル</span><span class="sxs-lookup"><span data-stu-id="0c67d-111">Samples</span></span>

<span data-ttu-id="0c67d-112">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="0c67d-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
