---
title: Node.js 用 Azure Monitor モジュール
description: Node.js 用 Azure Monitor モジュールのリファレンス
author: rbouche
ms.author: robb
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: 8a9411b7979f3130a1aa24fd2a0b294fc7f67718
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259305"
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="16b15-103">Node.js 用 Azure Monitor モジュール</span><span class="sxs-lookup"><span data-stu-id="16b15-103">Azure Monitor modules for Node.js</span></span>

<span data-ttu-id="16b15-104">クラウド アプリケーションは、動的なパーツを多数使った複雑な構成になっています。</span><span class="sxs-lookup"><span data-stu-id="16b15-104">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="16b15-105">監視では、アプリケーションを正常な状態で稼働させ続けるためのデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="16b15-105">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="16b15-106">また、潜在的な問題を防止したり、発生した問題をトラブルシューティングするのにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="16b15-106">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="16b15-107">さらに、監視データを使用して、アプリケーションに関する深い洞察を得ることもできます。</span><span class="sxs-lookup"><span data-stu-id="16b15-107">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="16b15-108">そのような知識は、アプリケーションのパフォーマンスや保守容易性を向上させたり、手作業での介入が必要な操作を自動化したりするうえで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="16b15-108">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="16b15-109">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="16b15-109">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="16b15-110">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="16b15-110">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="16b15-111">例</span><span class="sxs-lookup"><span data-stu-id="16b15-111">Example</span></span>

<span data-ttu-id="16b15-112">このコード例では、リソース グループに関連付けられているすべてのアラート ルールを出力します。</span><span class="sxs-lookup"><span data-stu-id="16b15-112">This code example prints all the alerting rules associated with a resource group.</span></span>

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

### <a name="samples"></a><span data-ttu-id="16b15-113">サンプル</span><span class="sxs-lookup"><span data-stu-id="16b15-113">Samples</span></span>

<span data-ttu-id="16b15-114">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="16b15-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
