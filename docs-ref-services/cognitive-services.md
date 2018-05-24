---
title: Node.js 用 Azure Cognitive Services モジュール
description: Node.js 用 Azure Cognitive Services モジュールのリファレンス
author: brapel
ms.author: v-brapel
manager: ehansen
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fd0870f4b38928c23145a50d4c71456b4c94c3e9
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="javascript-azure-cognitive-services-modules"></a><span data-ttu-id="3e8e9-103">JavaScript Azure Cognitive Services モジュール</span><span class="sxs-lookup"><span data-stu-id="3e8e9-103">JavaScript Azure Cognitive Services modules</span></span>

## <a name="vision-modules"></a><span data-ttu-id="3e8e9-104">Vision モジュール</span><span class="sxs-lookup"><span data-stu-id="3e8e9-104">Vision modules</span></span>

### <a name="computer-vision"></a><span data-ttu-id="3e8e9-105">Computer Vision</span><span class="sxs-lookup"><span data-stu-id="3e8e9-105">Computer Vision</span></span> 

<span data-ttu-id="3e8e9-106">画像内にあるビジュアル コンテンツに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-106">Returns information about visual content found in an image:</span></span>

- <span data-ttu-id="3e8e9-107">タグ付け、説明、ドメイン固有モデルを使用してコンテンツを特定し、確実にラベル付けします。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-107">Use tagging, descriptions, and domain-specific models to identify content and label it with confidence.</span></span>
- <span data-ttu-id="3e8e9-108">成人向け/わいせつな描写に対する設定を適用すれば、アダルト コンテンツの自動制限を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-108">Apply adult/racy settings to enable automated restriction of adult content.</span></span>
- <span data-ttu-id="3e8e9-109">画像の種類や写真内の配色を特定します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-109">Identify image types and color schemes in pictures.</span></span>

<span data-ttu-id="3e8e9-110">お使いのブラウザーで無料の [Computer Vision を試す](https://azure.microsoft.com/en-us/services/cognitive-services/computer-vision/)。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-110">[Try Computer Vision](https://azure.microsoft.com/en-us/services/cognitive-services/computer-vision/) for free in your browser.</span></span>

<span data-ttu-id="3e8e9-111">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-111">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-computervision
```

<span data-ttu-id="3e8e9-112">Computer Vision API の[詳細](/azure/cognitive-services/computer-vision/home)を確認し、[Computer Vision API JavaScript クイックスタート](/azure/cognitive-services/computer-vision/quickstarts/javascript)を開始する。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-112">[Learn more](/azure/cognitive-services/computer-vision/home) about the Computer Vision API and get started with the [Computer Vision API JavaScript quickstart](/azure/cognitive-services/computer-vision/quickstarts/javascript).</span></span>

### <a name="content-moderator"></a><span data-ttu-id="3e8e9-113">Content Moderator</span><span class="sxs-lookup"><span data-stu-id="3e8e9-113">Content Moderator</span></span>

<span data-ttu-id="3e8e9-114">マシンによるテキスト、ビデオ、および画像のモデレート機能を、人によるレビュー ツールで強化します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-114">Machine-assisted moderation of text, video and images, augmented with human review tools.</span></span>

<span data-ttu-id="3e8e9-115">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-115">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-contentmoderator
```

<span data-ttu-id="3e8e9-116">Content Moderator サービスの[詳細](/azure/cognitive-services/content-moderator/overview)を確認する。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-116">[Learn more](/azure/cognitive-services/content-moderator/overview) about the Content Moderator service.</span></span>

### <a name="face-api"></a><span data-ttu-id="3e8e9-117">Face API</span><span class="sxs-lookup"><span data-stu-id="3e8e9-117">Face API</span></span>

<span data-ttu-id="3e8e9-118">写真に含まれる顔を検出、識別、分析、グループ化、タグ付けします。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-118">Detect, identify, analyze, organize, and tag faces in photos.</span></span> 

<span data-ttu-id="3e8e9-119">お使いのブラウザーで [Face API を試す](https://azure.microsoft.com/en-us/services/cognitive-services/face/)。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-119">[Try the Face API](https://azure.microsoft.com/en-us/services/cognitive-services/face/) in your browser.</span></span>

<span data-ttu-id="3e8e9-120">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-120">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-face
```

<span data-ttu-id="3e8e9-121">Face API の[詳細](/azure/cognitive-services/face/overview)を確認し、[Face API JavaScript クイックスタート](/azure/cognitive-services/Face/quickstarts/javascript)を開始する。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-121">[Learn more](/azure/cognitive-services/face/overview) about the Face API and get started with the [Face API JavaScript quickstart](/azure/cognitive-services/Face/quickstarts/javascript).</span></span>

## <a name="search-modules"></a><span data-ttu-id="3e8e9-122">Search モジュール</span><span class="sxs-lookup"><span data-stu-id="3e8e9-122">Search modules</span></span>

### <a name="web-search"></a><span data-ttu-id="3e8e9-123">Web 検索</span><span class="sxs-lookup"><span data-stu-id="3e8e9-123">Web search</span></span>

<span data-ttu-id="3e8e9-124">Bing Web Search API でインデックス設定された Web ドキュメントを取得し、結果の種類、新しさなどで結果を絞り込みます。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-124">Retrieve web documents indexed by the Bing Web Search API and narrow down the results by result type, freshness and more.</span></span> 

<span data-ttu-id="3e8e9-125">お使いのブラウザーで [Web Search API を試す](https://azure.microsoft.com/en-us/services/cognitive-services/bing-web-search-api/)。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-125">[Try the Web Search API](https://azure.microsoft.com/en-us/services/cognitive-services/bing-web-search-api/) in your browser.</span></span>

<span data-ttu-id="3e8e9-126">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-126">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-websearch
```

<span data-ttu-id="3e8e9-127">Bing Web Search API の[詳細](/azure/cognitive-services/bing-web-search/overview)を確認し、[Web Search API Node.js クイックスタート](/azure/cognitive-services/bing-web-search/quickstarts/nodejs)を開始する。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-127">[Learn more](/azure/cognitive-services/bing-web-search/overview) about the Bing Web Search API and get started with the [Web Search API Node.js quickstart](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).</span></span>

### <a name="image-search"></a><span data-ttu-id="3e8e9-128">イメージの検索</span><span class="sxs-lookup"><span data-stu-id="3e8e9-128">Image search</span></span>

<span data-ttu-id="3e8e9-129">画像を検索し、検索結果として、サムネイル、完全な画像 URL、画像のメタデータなどを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-129">Search for images and get thumbnails, full image URLs, image metadata and more in your results.</span></span>

<span data-ttu-id="3e8e9-130">お使いのブラウザーで [Image Search API を試す](https://azure.microsoft.com/en-us/services/cognitive-services/bing-image-search-api/)。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-130">[Try the Image Search API](https://azure.microsoft.com/en-us/services/cognitive-services/bing-image-search-api/) in your browser.</span></span>

<span data-ttu-id="3e8e9-131">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-131">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-imagesearch
```

<span data-ttu-id="3e8e9-132">Bing Image Search API の[詳細](/azure/cognitive-services/bing-image-search/overview)を確認し、[Image Search API Node.js クイックスタート](/azure/cognitive-services/bing-image-search/quickstarts/nodejs)を開始する。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-132">[Learn more](/azure/cognitive-services/bing-image-search/overview) about the Bing Image Search API and get started with the [Image Search API Node.js quickstart](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).</span></span>


### <a name="entity-search"></a><span data-ttu-id="3e8e9-133">エンティティ検索</span><span class="sxs-lookup"><span data-stu-id="3e8e9-133">Entity search</span></span>

<span data-ttu-id="3e8e9-134">指定した検索用語または場所に最も関連性のあるエンティティ (場所、人、または物事) を検索します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-134">Search for the most relevant entity (place, person, or thing) for a given search term or location.</span></span>

<span data-ttu-id="3e8e9-135">お使いのブラウザーで [Entity Search API を試す](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/)。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-135">[Try the Entity Search API](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) in your browser.</span></span>

<span data-ttu-id="3e8e9-136">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-136">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-entitysearch
```

<span data-ttu-id="3e8e9-137">Bing Entity Search API の[詳細](/azure/cognitive-services/bing-entities-search/search-the-web)を確認し、[Entity Search API Node.js クイックスタート](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs)を開始する。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-137">[Learn more](/azure/cognitive-services/bing-entities-search/search-the-web) about the Bing Entity Search API and get started with the [Entity Search API Node.js quickstart](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).</span></span>

### <a name="custom-search"></a><span data-ttu-id="3e8e9-138">カスタム検索</span><span class="sxs-lookup"><span data-stu-id="3e8e9-138">Custom search</span></span>

<span data-ttu-id="3e8e9-139">ご自身の特定の検索ドメインに対応するカスタム Web 検索を作成します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-139">Build and a custom web search that meets your specific search domain.</span></span>

<span data-ttu-id="3e8e9-140">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-140">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-customsearch
```

<span data-ttu-id="3e8e9-141">Bing Custom Search サービスの[詳細](/azure/cognitive-services/bing-custom-search/)を確認し、[Custom Search API Node.js クイックスタート](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs)でアプリからご自身のカスタム検索のクエリを開始する。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-141">[Learn more](/azure/cognitive-services/bing-custom-search/) about the Bing Custom Search service and get started with querying your custom search from your apps with the [Custom Search API Node.js quickstart](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs).</span></span>

### <a name="video-search"></a><span data-ttu-id="3e8e9-142">ビデオ検索</span><span class="sxs-lookup"><span data-stu-id="3e8e9-142">Video search</span></span>

<span data-ttu-id="3e8e9-143">Web 上のビデオを検索し、作成者、エンコード、長さ、および閲覧数のメタデータを含む結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-143">Find videos across the web and get results with creator, encoding, length, and view count metadata.</span></span>

<span data-ttu-id="3e8e9-144">お使いのブラウザーで [Video Search API を試す](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/)。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-144">[Try the Video Search API](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) in your browser.</span></span>

<span data-ttu-id="3e8e9-145">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-145">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-videosearch
```

<span data-ttu-id="3e8e9-146">Bing Video Search サービスの[詳細](/azure/cognitive-services/bing-video-search/search-the-web)を確認し、[Video Search API Node.js クイックスタート](/azure/cognitive-services/bing-video-search/nodejs)を開始する。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-146">[Learn more](/azure/cognitive-services/bing-video-search/search-the-web) about the Bing Video Search service and get started with the [Video Search API Node.js quickstart](/azure/cognitive-services/bing-video-search/nodejs).</span></span>


### <a name="news-search"></a><span data-ttu-id="3e8e9-147">ニュース検索</span><span class="sxs-lookup"><span data-stu-id="3e8e9-147">News search</span></span>

<span data-ttu-id="3e8e9-148">Web 上のニュース記事を検索し、記事、関連するニュース、画像、およびプロバイダー情報のメタデータを操作します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-148">Search the web for news articles and work with article, related news, images, and provider info metadata.</span></span>

<span data-ttu-id="3e8e9-149">お使いのブラウザーで [News Search API を試す](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/)。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-149">[Try the News Search API](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) in your browser.</span></span>

<span data-ttu-id="3e8e9-150">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-150">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-newssearch
```

<span data-ttu-id="3e8e9-151">Bing News Search サービスの[詳細](/azure/cognitive-services/bing-news-search/search-the-web)を確認し、[News Search API JavaScript クイックスタート](/azure/cognitive-services/bing-news-search/nodejs)を開始する。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-151">[Learn more](/azure/cognitive-services/bing-news-search/search-the-web) about the Bing News Search service and get started with the [News Search API JavaScript quickstart](/azure/cognitive-services/bing-news-search/nodejs).</span></span>


## <a name="language-modules"></a><span data-ttu-id="3e8e9-152">言語モジュール</span><span class="sxs-lookup"><span data-stu-id="3e8e9-152">Language modules</span></span>

### <a name="text-analytics"></a><span data-ttu-id="3e8e9-153">Text Analytics</span><span class="sxs-lookup"><span data-stu-id="3e8e9-153">Text Analytics</span></span> 

<span data-ttu-id="3e8e9-154">Text Analytics API は、未加工のテキストに対する自然言語処理を提供するクラウドベースのサービスです。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-154">The Text Analytics API is a cloud-based service that provides  natural language processing over raw text.</span></span> <span data-ttu-id="3e8e9-155">この API の主要機能は次の 3 つです。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-155">The API includes three main functions:</span></span>

- <span data-ttu-id="3e8e9-156">センチメント分析</span><span class="sxs-lookup"><span data-stu-id="3e8e9-156">Sentiment analysis</span></span>
- <span data-ttu-id="3e8e9-157">キー フレーズの抽出</span><span class="sxs-lookup"><span data-stu-id="3e8e9-157">Key phrase extraction</span></span>
- <span data-ttu-id="3e8e9-158">言語検出</span><span class="sxs-lookup"><span data-stu-id="3e8e9-158">Language detection</span></span>

<span data-ttu-id="3e8e9-159">お使いのブラウザーで [Text Analytics API を試す](https://azure.microsoft.com/en-us/services/cognitive-services/text-analytics/)。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-159">[Try the Text Analytics API](https://azure.microsoft.com/en-us/services/cognitive-services/text-analytics/) in your browser.</span></span>

<span data-ttu-id="3e8e9-160">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-160">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-textanalytics
```

<span data-ttu-id="3e8e9-161">Text Analytics API の[詳細](/azure/cognitive-services/text-analytics/overview)を確認し、[Text Analytics API Node.js クイックスタート](/azure/cognitive-services/text-analytics/quickstarts/nodejs)を開始する。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-161">[Learn more](/azure/cognitive-services/text-analytics/overview) about the Text Analytics API and get started with the [Text Analytics API Node.js quickstart](/azure/cognitive-services/text-analytics/quickstarts/nodejs).</span></span>


### <a name="spell-check"></a><span data-ttu-id="3e8e9-162">スペル チェック</span><span class="sxs-lookup"><span data-stu-id="3e8e9-162">Spell Check</span></span>

<span data-ttu-id="3e8e9-163">Bing Spell Check API を使用して、コンテキストに応じた文法およびスペル チェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-163">Perform contextual grammar and spell checking with the Bing Spell Check API.</span></span>

<span data-ttu-id="3e8e9-164">お使いのブラウザーで [Spell Check API を試す](https://azure.microsoft.com/en-us/services/cognitive-services/spell-check/)。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-164">[Try the Spell Check API](https://azure.microsoft.com/en-us/services/cognitive-services/spell-check/) in your browser.</span></span>

<span data-ttu-id="3e8e9-165">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-165">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-spellcheck
```

<span data-ttu-id="3e8e9-166">Spell Check API の[詳細](/azure/cognitive-services/bing-spell-check/proof-text)を確認し、[Spell Check API Node.js クイックスタート](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs)を開始する。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-166">[Learn more](/azure/cognitive-services/bing-spell-check/proof-text) about the Spell Check API and get started with the [Spell Check API Node.js quickstart](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).</span></span>

## <a name="samples"></a><span data-ttu-id="3e8e9-167">サンプル</span><span class="sxs-lookup"><span data-stu-id="3e8e9-167">Samples</span></span>

<span data-ttu-id="3e8e9-168">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="3e8e9-168">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
