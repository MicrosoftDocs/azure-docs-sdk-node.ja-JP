---
title: "Node.js 用 Azure Logic Apps モジュール"
description: "Node.js 用 Azure Logic Apps モジュールのリファレンス"
keywords: Azure,SDK,API,Logic Apps, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 70380dbf1fd199ba4909975b05ade72efaa4e0ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-logic-apps-modules-for-nodejs"></a><span data-ttu-id="3937c-104">Node.js 用 Azure Logic Apps モジュール</span><span class="sxs-lookup"><span data-stu-id="3937c-104">Azure Logic Apps modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="3937c-105">概要</span><span class="sxs-lookup"><span data-stu-id="3937c-105">Overview</span></span>
<span data-ttu-id="3937c-106">Logic Apps では、クラウド上でのスケーラブルな統合やワークフローを簡略化し、実装するための手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="3937c-106">Logic Apps provide a way to simplify and implement scalable integrations and workflows in the cloud.</span></span> <span data-ttu-id="3937c-107">また、ワークフローと呼ばれる一連のステップとしてプロセスをモデル化し、自動化するためのビジュアル デザイナーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="3937c-107">It provides a visual designer to model and automate your process as a series of steps known as a workflow.</span></span> <span data-ttu-id="3937c-108">サービスとプロトコルをまたいだ迅速な統合のために、クラウドとオンプレミスの両方で数多くのコネクタが提供されています。</span><span class="sxs-lookup"><span data-stu-id="3937c-108">There are many connectors across the cloud and on-premises to quickly integrate across services and protocols.</span></span> <span data-ttu-id="3937c-109">ロジック アプリはトリガー ("Dynamics CRM にアカウントが追加されたとき" など) によって起動することができ、その後も数多くのアクション、変換、条件ロジックを組み合わせて開始することができます。</span><span class="sxs-lookup"><span data-stu-id="3937c-109">A logic app begins with a trigger (like 'When an account is added to Dynamics CRM') and after firing can begin many combinations of actions, conversions, and condition logic.</span></span>

<span data-ttu-id="3937c-110">Logic Apps を使用する利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3937c-110">The advantages of using Logic Apps include the following:</span></span>
- <span data-ttu-id="3937c-111">わかりやすい設計ツールを使って複雑なプロセスを設計できるため、時間を節約できる</span><span class="sxs-lookup"><span data-stu-id="3937c-111">Saving time by designing complex processes using easy to understand design tools</span></span>
- <span data-ttu-id="3937c-112">コードでは実装が難しいパターンやワークフローをシームレスに実装できる</span><span class="sxs-lookup"><span data-stu-id="3937c-112">Implementing patterns and workflows seamlessly, that would otherwise be difficult to implement in code</span></span>
- <span data-ttu-id="3937c-113">テンプレートを基に簡単に設計を開始できる</span><span class="sxs-lookup"><span data-stu-id="3937c-113">Getting started quickly from templates</span></span>
- <span data-ttu-id="3937c-114">独自のカスタム API、コード、アクションでロジック アプリをカスタマイズできる</span><span class="sxs-lookup"><span data-stu-id="3937c-114">Customizing your logic app with your own custom APIs, code, and actions</span></span>
- <span data-ttu-id="3937c-115">オンプレミスとクラウドにまたがる異なるシステム間で接続や同期ができる</span><span class="sxs-lookup"><span data-stu-id="3937c-115">Connect and synchronise disparate systems across on-premises and the cloud</span></span>
- <span data-ttu-id="3937c-116">BizTalk Server、API Management、Azure Functions、Azure Service Bus を基に作成でき、最上級の統合サポートが得られる</span><span class="sxs-lookup"><span data-stu-id="3937c-116">Build off of BizTalk server, API Management, Azure Functions, and Azure Service Bus with first-class integration support</span></span>

<span data-ttu-id="3937c-117">Logic Apps は完全に管理された iPaaS (サービスとしての統合プラットフォーム) であり、開発者はホスティング、スケーラビリティ、可用性、管理能力の構築について頭を悩ます必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="3937c-117">Logic Apps is a fully managed iPaaS (integration Platform as a Service) allowing developers not to have to worry about building hosting, scalability, availability and management.</span></span> <span data-ttu-id="3937c-118">Logic Apps は需要に合わせて自動的にスケールアップします。</span><span class="sxs-lookup"><span data-stu-id="3937c-118">Logic Apps will scale up automatically to meet demand.</span></span>

## <a name="management-package"></a><span data-ttu-id="3937c-119">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="3937c-119">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="3937c-120">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="3937c-120">Install the npm module</span></span>

<span data-ttu-id="3937c-121">Node.js 用 Azure ロジック モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="3937c-121">Install the Azure logic module for Node.js</span></span>

```bash
npm install azure-arm-logic
```

### <a name="example"></a><span data-ttu-id="3937c-122">例</span><span class="sxs-lookup"><span data-stu-id="3937c-122">Example</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const LogicManagement = require('azure-arm-logic');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const subscriptionId = 'subscription-id';
    const client = new LogicManagement(credentials, subscriptionId);
    return client.workflows.listBySubscription();
  })
  .then(workflows => console.log(workflows));
```

### <a name="samples"></a><span data-ttu-id="3937c-123">サンプル</span><span class="sxs-lookup"><span data-stu-id="3937c-123">Samples</span></span>

<span data-ttu-id="3937c-124">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="3937c-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
