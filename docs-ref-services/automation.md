---
title: Node.js 用 Azure Automation モジュール
description: Node.js 用 Azure Automation モジュールのリファレンス
author: eamonoreilly
ms.author: eamono
manager: nirb
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 281b5081163fc3b0b74219c766ff9be5c421296b
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052595"
---
# <a name="azure-automation-modules-for-nodejs"></a><span data-ttu-id="78915-103">Node.js 用 Azure Automation モジュール</span><span class="sxs-lookup"><span data-stu-id="78915-103">Azure Automation Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="78915-104">概要</span><span class="sxs-lookup"><span data-stu-id="78915-104">Overview</span></span>

<span data-ttu-id="78915-105">ユーザーは Azure Automation を使用すると、クラウド環境およびエンタープライズ環境で一般的に実行される、手動で実行時間が長く、エラーが起こりやすく、頻繁に繰り返されるタスクを自動化する手段を得られます。</span><span class="sxs-lookup"><span data-stu-id="78915-105">Azure Automation provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment.</span></span> <span data-ttu-id="78915-106">Automation によって時間を節約し、普段の管理タスクの信頼性を高めることができるほか、一定の間隔で自動的に実行されるようにタスクのスケジュールを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="78915-106">Automation saves time and increases the reliability of regular administrative tasks and even schedules them to be automatically performed at regular intervals.</span></span> <span data-ttu-id="78915-107">Runbook を使用してプロセスを自動化したり、Desired State Configuration を使用して構成管理を自動化したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="78915-107">You can automate processes using runbooks or automate configuration management using Desired State Configuration.</span></span>

## <a name="management-package"></a><span data-ttu-id="78915-108">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="78915-108">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="78915-109">npm を使ったモジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="78915-109">Install the modules with npm</span></span>

<span data-ttu-id="78915-110">Node.js 用 Azure Automation モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="78915-110">Use npm to install the Azure Automation modules for Node.js</span></span>

```bash
npm install azure-arm-automation
```

### <a name="example"></a><span data-ttu-id="78915-111">例</span><span class="sxs-lookup"><span data-stu-id="78915-111">Example</span></span>

<span data-ttu-id="78915-112">この例では、Automation アカウントを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="78915-112">This example lists the automation accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="78915-113">サンプル</span><span class="sxs-lookup"><span data-stu-id="78915-113">Samples</span></span>

<span data-ttu-id="78915-114">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="78915-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
