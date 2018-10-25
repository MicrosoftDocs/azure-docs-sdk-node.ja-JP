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
ms.openlocfilehash: fb0319965f7ea9d1bcab25e0e213998052b78ae0
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "49714627"
---
# <a name="javascript-azure-cognitive-services-modules"></a>JavaScript Azure Cognitive Services モジュール

## <a name="vision-modules"></a>Vision モジュール

### <a name="computer-vision"></a>Computer Vision 

画像内にあるビジュアル コンテンツに関する情報を返します。

- タグ付け、説明、ドメイン固有モデルを使用してコンテンツを特定し、確実にラベル付けします。
- 成人向け/わいせつな描写に対する設定を適用すれば、アダルト コンテンツの自動制限を有効にできます。
- 画像の種類や写真内の配色を特定します。

お使いのブラウザーで無料の [Computer Vision を試す](https://azure.microsoft.com/services/cognitive-services/computer-vision/)。

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。

```
npm install azure-cognitiveservices-computervision
```

Computer Vision API の[詳細](/azure/cognitive-services/computer-vision/home)を確認し、[Computer Vision API JavaScript クイックスタート](/azure/cognitive-services/computer-vision/quickstarts/javascript)を開始する。

### <a name="content-moderator"></a>Content Moderator

マシンによるテキスト、ビデオ、および画像のモデレート機能を、人によるレビュー ツールで強化します。

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。

```
npm install azure-cognitiveservices-contentmoderator
```

Content Moderator サービスの[詳細](/azure/cognitive-services/content-moderator/overview)を確認する。

### <a name="face-api"></a>Face API

写真に含まれる顔を検出、識別、分析、グループ化、タグ付けします。 

お使いのブラウザーで [Face API を試す](https://azure.microsoft.com/services/cognitive-services/face/)。

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。

```
npm install azure-cognitiveservices-face
```

Face API の[詳細](/azure/cognitive-services/face/overview)を確認し、[Face API JavaScript クイックスタート](/azure/cognitive-services/Face/quickstarts/javascript)を開始する。

## <a name="search-modules"></a>Search モジュール

### <a name="web-search"></a>Web 検索

Bing Web Search API でインデックス設定された Web ドキュメントを取得し、結果の種類、新しさなどで結果を絞り込みます。 

お使いのブラウザーで [Web Search API を試す](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/)。

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。

```
npm install azure-cognitiveservices-websearch
```

Bing Web Search API の[詳細](/azure/cognitive-services/bing-web-search/overview)を確認し、[Web Search API Node.js クイックスタート](/azure/cognitive-services/bing-web-search/quickstarts/nodejs)を開始する。

### <a name="image-search"></a>イメージの検索

画像を検索し、検索結果として、サムネイル、完全な画像 URL、画像のメタデータなどを取得します。

お使いのブラウザーで [Image Search API を試す](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/)。

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。

```
npm install azure-cognitiveservices-imagesearch
```

Bing Image Search API の[詳細](/azure/cognitive-services/bing-image-search/overview)を確認し、[Image Search API Node.js クイックスタート](/azure/cognitive-services/bing-image-search/quickstarts/nodejs)を開始する。


### <a name="entity-search"></a>エンティティ検索

指定した検索用語または場所に最も関連性のあるエンティティ (場所、人、または物事) を検索します。

お使いのブラウザーで [Entity Search API を試す](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/)。

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。

```
npm install azure-cognitiveservices-entitysearch
```

Bing Entity Search API の[詳細](/azure/cognitive-services/bing-entities-search/search-the-web)を確認し、[Entity Search API Node.js クイックスタート](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs)を開始する。

### <a name="custom-search"></a>カスタム検索

ご自身の特定の検索ドメインに対応するカスタム Web 検索を作成します。

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。

```
npm install azure-cognitiveservices-customsearch
```

Bing Custom Search サービスの[詳細](/azure/cognitive-services/bing-custom-search/)を確認し、[Custom Search API Node.js クイックスタート](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs)でアプリからご自身のカスタム検索のクエリを開始する。

### <a name="video-search"></a>ビデオ検索

Web 上のビデオを検索し、作成者、エンコード、長さ、および閲覧数のメタデータを含む結果を取得します。

お使いのブラウザーで [Video Search API を試す](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/)。

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。

```
npm install azure-cognitiveservices-videosearch
```

Bing Video Search サービスの[詳細](/azure/cognitive-services/bing-video-search/search-the-web)を確認し、[Video Search API Node.js クイックスタート](/azure/cognitive-services/bing-video-search/nodejs)を開始する。


### <a name="news-search"></a>ニュース検索

Web 上のニュース記事を検索し、記事、関連するニュース、画像、およびプロバイダー情報のメタデータを操作します。

お使いのブラウザーで [News Search API を試す](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/)。

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。

```
npm install azure-cognitiveservices-newssearch
```

Bing News Search サービスの[詳細](/azure/cognitive-services/bing-news-search/search-the-web)を確認し、[News Search API JavaScript クイックスタート](/azure/cognitive-services/bing-news-search/nodejs)を開始する。


## <a name="language-modules"></a>言語モジュール

### <a name="text-analytics"></a>Text Analytics 

Text Analytics API は、未加工のテキストに対する自然言語処理を提供するクラウドベースのサービスです。 この API の主要機能は次の 3 つです。

- センチメント分析
- キー フレーズの抽出
- 言語検出

お使いのブラウザーで [Text Analytics API を試す](https://azure.microsoft.com/services/cognitive-services/text-analytics/)。

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。

```
npm install azure-cognitiveservices-textanalytics
```

Text Analytics API の[詳細](/azure/cognitive-services/text-analytics/overview)を確認し、[Text Analytics API Node.js クイックスタート](/azure/cognitive-services/text-analytics/quickstarts/nodejs)を開始する。


### <a name="spell-check"></a>スペル チェック

Bing Spell Check API を使用して、コンテキストに応じた文法およびスペル チェックを実行します。

お使いのブラウザーで [Spell Check API を試す](https://azure.microsoft.com/services/cognitive-services/spell-check/)。

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) を使用して次の JavaScript モジュールを取得します。

```
npm install azure-cognitiveservices-spellcheck
```

Spell Check API の[詳細](/azure/cognitive-services/bing-spell-check/proof-text)を確認し、[Spell Check API Node.js クイックスタート](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs)を開始する。

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
