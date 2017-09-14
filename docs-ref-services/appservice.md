---
title: "Node.js 用 Azure App Service モジュール"
description: "Node.js 用 Azure App Service モジュールのリファレンス"
keywords: "Azure, Node, SDK, API, Web アプリ, モバイル, nodejs, javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: c695ae6d523ea731b18382ba0906f78b40ce301f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-app-service-modules-for-nodejs"></a><span data-ttu-id="514b8-104">Node.js 用 Azure App Service モジュール</span><span class="sxs-lookup"><span data-stu-id="514b8-104">Azure App Service modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="514b8-105">概要</span><span class="sxs-lookup"><span data-stu-id="514b8-105">Overview</span></span>

<span data-ttu-id="514b8-106">Azure App Service は、Microsoft Azure が提供するサービスとしてのプラットフォーム (PaaS) です。</span><span class="sxs-lookup"><span data-stu-id="514b8-106">Azure App Service is a platform-as-a-service (PaaS) offering of Microsoft Azure.</span></span> <span data-ttu-id="514b8-107">任意のプラットフォームまたはデバイスを対象として Web アプリとモバイル アプリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="514b8-107">Create web and mobile apps for any platform or device.</span></span> <span data-ttu-id="514b8-108">作成したアプリと SaaS ソリューションの統合、オンプレミス アプリケーションへの接続、ビジネス プロセスの自動化を実行できます。</span><span class="sxs-lookup"><span data-stu-id="514b8-108">Integrate your apps with SaaS solutions, connect with on-premises applications, and automate your business processes.</span></span> <span data-ttu-id="514b8-109">Azure では、指定した共有仮想マシン (VM) リソースまたは専用 VM を使用して、完全に管理された VM 上で、アプリが実行されます。</span><span class="sxs-lookup"><span data-stu-id="514b8-109">Azure runs your apps on fully managed virtual machines (VMs), with your choice of shared VM resources or dedicated VMs.</span></span>

<span data-ttu-id="514b8-110">App Service には、以前は Azure Websites および Azure Mobile Services として個別に提供されていた Web 機能とモバイル機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="514b8-110">App Service includes the web and mobile capabilities that we previously delivered separately as Azure Websites and Azure Mobile Services.</span></span> <span data-ttu-id="514b8-111">さらに、ビジネス プロセスの自動化やクラウド API のホストに利用できる新しい機能も備えています。</span><span class="sxs-lookup"><span data-stu-id="514b8-111">It also includes new capabilities for automating business processes and hosting cloud APIs.</span></span> <span data-ttu-id="514b8-112">単一の統合サービスである App Service では、さまざまなコンポーネント (Web サイト、モバイル アプリのバック エンド、RESTful API、ビジネス プロセス) を 1 つのソリューションにまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="514b8-112">As a single integrated service, App Service lets you compose various components -- websites, mobile app back ends, RESTful APIs, and business processes -- into a single solution.</span></span>

## <a name="management-package"></a><span data-ttu-id="514b8-113">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="514b8-113">Management Package</span></span>

### <a name="install-the-npm-package"></a><span data-ttu-id="514b8-114">npm パッケージのインストール</span><span class="sxs-lookup"><span data-stu-id="514b8-114">Install the npm package</span></span>

<span data-ttu-id="514b8-115">Node.js 用 Azure App Service モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="514b8-115">Install the Azure App Service module for Node.js</span></span>

```bash
npm install azure-arm-website
```

### <a name="example"></a><span data-ttu-id="514b8-116">例</span><span class="sxs-lookup"><span data-stu-id="514b8-116">Example</span></span>

<span data-ttu-id="514b8-117">この例では、Node.js を使って Azure に Web サイトを作成します。</span><span class="sxs-lookup"><span data-stu-id="514b8-117">This example creates a website on Azure using Node.js.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const webSiteManagementClient = require('azure-arm-website');

const subscriptionId = 'your-subscription-id';
const website = 'website001';
const resourceGroup = 'your-resource-group';
const hostingPlan = 'testHostingPlan';
let webSiteClient;

msRestAzure.interactiveLogin().then(credentials => {
  webSiteClient = new webSiteManagementClient(credentials, subscriptionId);
  createWebSite(website).then(website => console.log('Web Site created successfully', website));
});

function createWebSite(webSiteName) {
  const parameters = { location: 'westus', serverFarmId: hostingPlan };
  console.log(`Creating web site:  ${webSiteName}`);
  return webSiteClient.webApps.createOrUpdate(resourceGroup, webSiteName, parameters, null);
}
```

## <a name="samples"></a><span data-ttu-id="514b8-118">サンプル</span><span class="sxs-lookup"><span data-stu-id="514b8-118">Samples</span></span>

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

<span data-ttu-id="514b8-119">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="514b8-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
