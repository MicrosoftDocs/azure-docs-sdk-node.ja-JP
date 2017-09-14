---
title: "Node.js 用 Azure Monitor モジュール"
description: "Node.js 用 Azure Monitor モジュールのリファレンス"
keywords: Azure,SDK,API,Monitor, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: 8d27d837bddaa5258dde47b769cf601f6f5a861f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="f22e5-104">Node.js 用 Azure Monitor モジュール</span><span class="sxs-lookup"><span data-stu-id="f22e5-104">Azure Monitor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f22e5-105">概要</span><span class="sxs-lookup"><span data-stu-id="f22e5-105">Overview</span></span>
<span data-ttu-id="f22e5-106">クラウド アプリケーションは、動的なパーツを多数使った複雑な構成になっています。</span><span class="sxs-lookup"><span data-stu-id="f22e5-106">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="f22e5-107">監視では、アプリケーションを正常な状態で稼働させ続けるためのデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="f22e5-107">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="f22e5-108">また、潜在的な問題を防止したり、発生した問題をトラブルシューティングするのにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f22e5-108">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="f22e5-109">さらに、監視データを使用して、アプリケーションに関する深い洞察を得ることもできます。</span><span class="sxs-lookup"><span data-stu-id="f22e5-109">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="f22e5-110">そのような知識は、アプリケーションのパフォーマンスや保守容易性を向上させたり、手作業での介入が必要な操作を自動化したりするうえで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f22e5-110">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="f22e5-111">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="f22e5-111">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="f22e5-112">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="f22e5-112">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="f22e5-113">例</span><span class="sxs-lookup"><span data-stu-id="f22e5-113">Example</span></span>

<span data-ttu-id="f22e5-114">このコード例では、リソース グループに関連付けられているすべてのアラート ルールを出力します。</span><span class="sxs-lookup"><span data-stu-id="f22e5-114">This code example prints all the alerting rules associated with a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const monitorManagementClient = require('azure-arm-monitor');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new monitorManagementClient(credentials, subscriptionId);
    client.alertRules.listByResourceGroup(resourceGroupName, rules => {
      console.log('List of rules:');
      console.dir(rules, { depth: null, colors: true });
    })
  });

```

### <a name="samples"></a><span data-ttu-id="f22e5-115">サンプル</span><span class="sxs-lookup"><span data-stu-id="f22e5-115">Samples</span></span>

<span data-ttu-id="f22e5-116">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="f22e5-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
