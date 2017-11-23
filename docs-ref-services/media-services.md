---
title: "Node.js 用 Azure Media Services モジュール"
description: "Node.js 用 Azure Media Services モジュールのリファレンス"
keywords: Azure,SDK,API,Media Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: 9b304ceb0c2d0580534ae1bee5a44d01fd4d8b33
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-media-services-modules-for-nodejs"></a><span data-ttu-id="1fd64-104">Node.js 用 Azure Media Services モジュール</span><span class="sxs-lookup"><span data-stu-id="1fd64-104">Azure Media Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="1fd64-105">概要</span><span class="sxs-lookup"><span data-stu-id="1fd64-105">Overview</span></span>

<span data-ttu-id="1fd64-106">Azure Media Services は拡張可能なクラウドベースのプラットフォームです。これにより、開発者はスケーラブルなメディア管理の構築、アプリケーションの配信を実行できます。</span><span class="sxs-lookup"><span data-stu-id="1fd64-106">Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="1fd64-107">Media Services は、各種クライアント (TV、PC、モバイル デバイスなど) へのオンデマンドとライブ ストリーミングでの配信でビデオやオーディオのコンテンツの安全なアップロード、格納、エンコード、パッケージ化を可能にする REST API に基づいています。</span><span class="sxs-lookup"><span data-stu-id="1fd64-107">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span>

<span data-ttu-id="1fd64-108">Azure Media Services を使用すると、次のことができます。</span><span class="sxs-lookup"><span data-stu-id="1fd64-108">With Azure Media Services, you can:</span></span>
- <span data-ttu-id="1fd64-109">Media Services を全面的に使ってエンドツーエンドのワークフローを構築する。</span><span class="sxs-lookup"><span data-stu-id="1fd64-109">Build end-to-end workflows using entirely Media Services.</span></span> 
- <span data-ttu-id="1fd64-110">ワークフローの一部にサード パーティのコンポーネントを使用する。</span><span class="sxs-lookup"><span data-stu-id="1fd64-110">Use third-party components for some parts of your workflow.</span></span> <span data-ttu-id="1fd64-111">たとえば、サード パーティのエンコーダーを使用してエンコードしてから、</span><span class="sxs-lookup"><span data-stu-id="1fd64-111">For example, encode using a third-party encoder.</span></span> <span data-ttu-id="1fd64-112">Media Services を使用してアップロード、保護、パッケージ化、配信などを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1fd64-112">Then, upload, protect, package, deliver using Media Services.</span></span>
- <span data-ttu-id="1fd64-113">コンテンツをライブ ストリーム配信したり、オンデマンドで配信したりする。</span><span class="sxs-lookup"><span data-stu-id="1fd64-113">Stream your content live or deliver content on-demand.</span></span> <span data-ttu-id="1fd64-114">このトピックでは、その他の関連トピックのリンクも提供します。</span><span class="sxs-lookup"><span data-stu-id="1fd64-114">The topic also links to other relevant topics.</span></span>

## <a name="management-package"></a><span data-ttu-id="1fd64-115">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="1fd64-115">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="1fd64-116">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="1fd64-116">Install the npm module</span></span>

<span data-ttu-id="1fd64-117">Azure Media Services の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="1fd64-117">Install the Azure media services npm module</span></span>

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a><span data-ttu-id="1fd64-118">例</span><span class="sxs-lookup"><span data-stu-id="1fd64-118">Example</span></span>

<span data-ttu-id="1fd64-119">この例では、リソース グループのすべてのメディア サービスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="1fd64-119">This example lists all media services for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="1fd64-120">サンプル</span><span class="sxs-lookup"><span data-stu-id="1fd64-120">Samples</span></span>

<span data-ttu-id="1fd64-121">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="1fd64-121">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
