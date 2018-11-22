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
ms.openlocfilehash: a9c34a57d7964de1713ebf4d6c0f9c000df33042
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2018
ms.locfileid: "52005906"
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="ba7c5-103">Node.js 用 Azure Search モジュール</span><span class="sxs-lookup"><span data-stu-id="ba7c5-103">Azure Search modules for Node.js</span></span>

<span data-ttu-id="ba7c5-104">Azure Search は、サーバーとインフラストラクチャの管理を Microsoft に委任するクラウドの Search-as-a-service (サービスとしての検索) ソリューションです。データを取り込んだら、アプリケーションに検索機能を追加して、すぐに利用を開始できます。</span><span class="sxs-lookup"><span data-stu-id="ba7c5-104">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="ba7c5-105">Azure Search の詳細については、[こちら](https://docs.microsoft.com/azure/search/search-what-is-azure-search)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba7c5-105">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="ba7c5-106">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="ba7c5-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ba7c5-107">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="ba7c5-107">Install the npm module</span></span>

<span data-ttu-id="ba7c5-108">Azure Search の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="ba7c5-108">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="ba7c5-109">例</span><span class="sxs-lookup"><span data-stu-id="ba7c5-109">Example</span></span>

<span data-ttu-id="ba7c5-110">この例では、Azure に新しい Search サービスを作成し、そのリソース グループに含まれるリソースを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ba7c5-110">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="ba7c5-111">サンプル</span><span class="sxs-lookup"><span data-stu-id="ba7c5-111">Samples</span></span>

<span data-ttu-id="ba7c5-112">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="ba7c5-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
