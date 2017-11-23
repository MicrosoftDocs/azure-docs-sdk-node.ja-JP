---
title: "Node.js 用 Azure Automation モジュール"
description: "Node.js 用 Azure Automation モジュールのリファレンス"
keywords: Azure,SDK,API,Automation, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 96861efce8eb95f567aa25f2304cb271d932d949
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-automation-modules-for-nodejs"></a><span data-ttu-id="5b327-104">Node.js 用 Azure Automation モジュール</span><span class="sxs-lookup"><span data-stu-id="5b327-104">Azure Automation Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="5b327-105">概要</span><span class="sxs-lookup"><span data-stu-id="5b327-105">Overview</span></span>

<span data-ttu-id="5b327-106">ユーザーは Azure Automation を使用すると、クラウド環境およびエンタープライズ環境で一般的に実行される、手動で実行時間が長く、エラーが起こりやすく、頻繁に繰り返されるタスクを自動化する手段を得られます。</span><span class="sxs-lookup"><span data-stu-id="5b327-106">Azure Automation provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment.</span></span> <span data-ttu-id="5b327-107">Automation によって時間を節約し、普段の管理タスクの信頼性を高めることができるほか、一定の間隔で自動的に実行されるようにタスクのスケジュールを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="5b327-107">Automation saves time and increases the reliability of regular administrative tasks and even schedules them to be automatically performed at regular intervals.</span></span> <span data-ttu-id="5b327-108">Runbook を使用してプロセスを自動化したり、Desired State Configuration を使用して構成管理を自動化したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="5b327-108">You can automate processes using runbooks or automate configuration management using Desired State Configuration.</span></span>

## <a name="management-package"></a><span data-ttu-id="5b327-109">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="5b327-109">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="5b327-110">npm を使ったモジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="5b327-110">Install the modules with npm</span></span>

<span data-ttu-id="5b327-111">Node.js 用 Azure Automation モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="5b327-111">Use npm to install the Azure Automation modules for Node.js</span></span>

```bash
npm install azure-arm-automation
```

### <a name="example"></a><span data-ttu-id="5b327-112">例</span><span class="sxs-lookup"><span data-stu-id="5b327-112">Example</span></span>

<span data-ttu-id="5b327-113">この例では、Automation アカウントを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="5b327-113">This example lists the automation accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));

```

## <a name="samples"></a><span data-ttu-id="5b327-114">サンプル</span><span class="sxs-lookup"><span data-stu-id="5b327-114">Samples</span></span>

<span data-ttu-id="5b327-115">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="5b327-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
