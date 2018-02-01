---
title: "Node.js 用 Azure Media Services モジュール"
description: "Node.js 用 Azure Media Services モジュールのリファレンス"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: 77a6716d4ef0d566690325a86e85d66c5ac234d6
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2018
---
# <a name="azure-media-services-modules-for-nodejs"></a><span data-ttu-id="6b1d5-103">Node.js 用 Azure Media Services モジュール</span><span class="sxs-lookup"><span data-stu-id="6b1d5-103">Azure Media Services modules for Node.js</span></span>

<span data-ttu-id="6b1d5-104">Azure Media Services は拡張可能なクラウドベースのプラットフォームです。これにより、開発者はスケーラブルなメディア管理の構築、アプリケーションの配信を実行できます。</span><span class="sxs-lookup"><span data-stu-id="6b1d5-104">Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="6b1d5-105">Media Services は、各種クライアント (TV、PC、モバイル デバイスなど) へのオンデマンドとライブ ストリーミングでの配信でビデオやオーディオのコンテンツの安全なアップロード、格納、エンコード、パッケージ化を可能にする REST API に基づいています。</span><span class="sxs-lookup"><span data-stu-id="6b1d5-105">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span>

<span data-ttu-id="6b1d5-106">Azure Media Services を使用すると、次のことができます。</span><span class="sxs-lookup"><span data-stu-id="6b1d5-106">With Azure Media Services, you can:</span></span>
- <span data-ttu-id="6b1d5-107">Media Services を全面的に使ってエンドツーエンドのワークフローを構築する。</span><span class="sxs-lookup"><span data-stu-id="6b1d5-107">Build end-to-end workflows using entirely Media Services.</span></span> 
- <span data-ttu-id="6b1d5-108">ワークフローの一部にサード パーティのコンポーネントを使用する。</span><span class="sxs-lookup"><span data-stu-id="6b1d5-108">Use third-party components for some parts of your workflow.</span></span> <span data-ttu-id="6b1d5-109">たとえば、サード パーティのエンコーダーを使用してエンコードしてから、</span><span class="sxs-lookup"><span data-stu-id="6b1d5-109">For example, encode using a third-party encoder.</span></span> <span data-ttu-id="6b1d5-110">Media Services を使用してアップロード、保護、パッケージ化、配信などを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6b1d5-110">Then, upload, protect, package, deliver using Media Services.</span></span>
- <span data-ttu-id="6b1d5-111">コンテンツをライブ ストリーム配信したり、オンデマンドで配信したりする。</span><span class="sxs-lookup"><span data-stu-id="6b1d5-111">Stream your content live or deliver content on-demand.</span></span> <span data-ttu-id="6b1d5-112">このトピックでは、その他の関連トピックのリンクも提供します。</span><span class="sxs-lookup"><span data-stu-id="6b1d5-112">The topic also links to other relevant topics.</span></span>

## <a name="management-package"></a><span data-ttu-id="6b1d5-113">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="6b1d5-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="6b1d5-114">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="6b1d5-114">Install the npm module</span></span>

<span data-ttu-id="6b1d5-115">Azure Media Services の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="6b1d5-115">Install the Azure media services npm module</span></span>

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a><span data-ttu-id="6b1d5-116">例</span><span class="sxs-lookup"><span data-stu-id="6b1d5-116">Example</span></span>

<span data-ttu-id="6b1d5-117">この例では、リソース グループのすべてのメディア サービスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="6b1d5-117">This example lists all media services for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const mediaServicesManagement = require('azure-arm-mediaservices');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
let mediaServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  mediaServicesClient = new mediaServicesManagement(credentials, subscriptionId);
  mediaServicesClient.mediaServiceOperations
    .listByResourceGroup(resourceGroup)
    .then(mediaServices => console.log('Retrieved media services: ', mediaServices));
});
```

## <a name="samples"></a><span data-ttu-id="6b1d5-118">サンプル</span><span class="sxs-lookup"><span data-stu-id="6b1d5-118">Samples</span></span>

<span data-ttu-id="6b1d5-119">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="6b1d5-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
