---
title: Node.js 用 Azure Logic Apps モジュール
description: Node.js 用 Azure Logic Apps モジュールのリファレンス
author: ecfan
ms.author: estfan
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 021f57c7f4f1b86a3c0e97f345d2f934351669b8
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2018
ms.locfileid: "51111171"
---
# <a name="azure-logic-apps-modules-for-nodejs"></a><span data-ttu-id="58260-103">Node.js 用 Azure Logic Apps モジュール</span><span class="sxs-lookup"><span data-stu-id="58260-103">Azure Logic Apps modules for Node.js</span></span>

<span data-ttu-id="58260-104">Logic Apps では、クラウド上でのスケーラブルな統合やワークフローを簡略化し、実装するための手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="58260-104">Logic Apps provide a way to simplify and implement scalable integrations and workflows in the cloud.</span></span> <span data-ttu-id="58260-105">また、ワークフローと呼ばれる一連のステップとしてプロセスをモデル化し、自動化するためのビジュアル デザイナーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="58260-105">It provides a visual designer to model and automate your process as a series of steps known as a workflow.</span></span> <span data-ttu-id="58260-106">サービスとプロトコルをまたいだ迅速な統合のために、クラウドとオンプレミスの両方で数多くのコネクタが提供されています。</span><span class="sxs-lookup"><span data-stu-id="58260-106">There are many connectors across the cloud and on-premises to quickly integrate across services and protocols.</span></span> <span data-ttu-id="58260-107">ロジック アプリはトリガー ("Dynamics CRM にアカウントが追加されたとき" など) によって起動することができ、その後も数多くのアクション、変換、条件ロジックを組み合わせて開始することができます。</span><span class="sxs-lookup"><span data-stu-id="58260-107">A logic app begins with a trigger (like 'When an account is added to Dynamics CRM') and after firing can begin many combinations of actions, conversions, and condition logic.</span></span>

<span data-ttu-id="58260-108">Logic Apps を使用する利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="58260-108">The advantages of using Logic Apps include the following:</span></span>
- <span data-ttu-id="58260-109">わかりやすい設計ツールを使って複雑なプロセスを設計できるため、時間を節約できる</span><span class="sxs-lookup"><span data-stu-id="58260-109">Saving time by designing complex processes using easy to understand design tools</span></span>
- <span data-ttu-id="58260-110">コードでは実装が難しいパターンやワークフローをシームレスに実装できる</span><span class="sxs-lookup"><span data-stu-id="58260-110">Implementing patterns and workflows seamlessly, that would otherwise be difficult to implement in code</span></span>
- <span data-ttu-id="58260-111">テンプレートを基に簡単に設計を開始できる</span><span class="sxs-lookup"><span data-stu-id="58260-111">Getting started quickly from templates</span></span>
- <span data-ttu-id="58260-112">独自のカスタム API、コード、アクションでロジック アプリをカスタマイズできる</span><span class="sxs-lookup"><span data-stu-id="58260-112">Customizing your logic app with your own custom APIs, code, and actions</span></span>
- <span data-ttu-id="58260-113">オンプレミスとクラウドにまたがる異なるシステム間で接続や同期ができる</span><span class="sxs-lookup"><span data-stu-id="58260-113">Connect and synchronise disparate systems across on-premises and the cloud</span></span>
- <span data-ttu-id="58260-114">BizTalk Server、API Management、Azure Functions、Azure Service Bus を基に作成でき、最上級の統合サポートが得られる</span><span class="sxs-lookup"><span data-stu-id="58260-114">Build off of BizTalk server, API Management, Azure Functions, and Azure Service Bus with first-class integration support</span></span>

<span data-ttu-id="58260-115">Logic Apps はフル マネージドの iPaaS (サービスとしての統合プラットフォーム) であり、開発者はホスティング、スケーラビリティ、可用性、管理能力の構築について頭を悩ます必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="58260-115">Logic Apps is a fully managed iPaaS (integration Platform as a Service) allowing developers not to have to worry about building hosting, scalability, availability and management.</span></span> <span data-ttu-id="58260-116">Logic Apps は需要に合わせて自動的にスケールアップします。</span><span class="sxs-lookup"><span data-stu-id="58260-116">Logic Apps will scale up automatically to meet demand.</span></span>

## <a name="management-package"></a><span data-ttu-id="58260-117">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="58260-117">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="58260-118">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="58260-118">Install the npm module</span></span>

<span data-ttu-id="58260-119">Node.js 用 Azure ロジック モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="58260-119">Install the Azure logic module for Node.js</span></span>

```bash
npm install azure-arm-logic
```

### <a name="example"></a><span data-ttu-id="58260-120">例</span><span class="sxs-lookup"><span data-stu-id="58260-120">Example</span></span>

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

### <a name="samples"></a><span data-ttu-id="58260-121">サンプル</span><span class="sxs-lookup"><span data-stu-id="58260-121">Samples</span></span>

<span data-ttu-id="58260-122">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="58260-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
