---
title: JavaScript 用 Cognitive Services Speech SDK
description: JavaScript 用 Cognitive Services Speech SDK のリファレンス
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 09/24/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.component: speech-service
ms.openlocfilehash: 69167faa5b2677fc15561ed33beccf7925efbe39
ms.sourcegitcommit: da60ea91d4215d738b1e0df82066f0fc337ad85a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2018
ms.locfileid: "47358702"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a><span data-ttu-id="4fd27-103">JavaScript 用 Cognitive Services Speech SDK</span><span class="sxs-lookup"><span data-stu-id="4fd27-103">Cognitive Services Speech SDK for JavaScript</span></span>

## <a name="overview"></a><span data-ttu-id="4fd27-104">概要</span><span class="sxs-lookup"><span data-stu-id="4fd27-104">Overview</span></span>

<span data-ttu-id="4fd27-105">Microsoft では、音声対応アプリケーションの開発を簡素化するために、[Speech Service](https://aka.ms/csspeech) で使用する Speech SDK を提供しています。</span><span class="sxs-lookup"><span data-stu-id="4fd27-105">To simplify the development of speech-enabled applications, Microsoft provides the Speech SDK for use with the [Speech service](https://aka.ms/csspeech).</span></span>
<span data-ttu-id="4fd27-106">Speech SDK には、一貫性のあるネイティブな Speech-to-Text API と Speech Translation API が提供されています。</span><span class="sxs-lookup"><span data-stu-id="4fd27-106">The Speech SDK provides consistent native Speech-to-Text and Speech Translation APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="4fd27-107">Cognitive Services Speech SDK は、現在ブラウザーでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="4fd27-107">The Cognitive Services Speech SDK is currently available only for browsers.</span></span>
> <span data-ttu-id="4fd27-108">NPM パッケージは追って利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4fd27-108">An NPM package will follow soon.</span></span>

### <a name="install-the-speech-sdk"></a><span data-ttu-id="4fd27-109">Speech SDK のインストール</span><span class="sxs-lookup"><span data-stu-id="4fd27-109">Install the Speech SDK</span></span>

<span data-ttu-id="4fd27-110">Speech SDK を [.zip パッケージ](https://aka.ms/csspeech/jsbrowserpackage)としてダウンロードし、展開します。</span><span class="sxs-lookup"><span data-stu-id="4fd27-110">Download the Speech SDK as a [.zip package](https://aka.ms/csspeech/jsbrowserpackage) and unpack it.</span></span>
<span data-ttu-id="4fd27-111">これにより `microsoft.cognitiveservices.speech.sdk.bundle.js` という名前のファイルを含め、複数のファイルが展開されます。</span><span class="sxs-lookup"><span data-stu-id="4fd27-111">This should result in a number of files being unpacked including a file named `microsoft.cognitiveservices.speech.sdk.bundle.js`.</span></span>
<span data-ttu-id="4fd27-112">Speech SDK の使用を開始するには、このファイルをスクリプト リソースとして Web ページに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="4fd27-112">Load this file as a script resource in your web page to start using the Speech SDK:</span></span>

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a><span data-ttu-id="4fd27-113">例</span><span class="sxs-lookup"><span data-stu-id="4fd27-113">Example</span></span> 

<span data-ttu-id="4fd27-114">次のコード スニペットは、お使いのブラウザーからシンプルな音声認識を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4fd27-114">The following code snippets illustrates how to do simple speech recognition from your browser:</span></span>

```javascript 
var SpeechSDK = window.SpeechSDK;
var speechConfig = SpeechSDK.SpeechConfig.fromSubscription("your-subscription-key", "your-service-region");
speechConfig.language = "en-US";
var audioConfig = SpeechSDK.AudioConfig.fromDefaultMicrophoneInput();
recognizer = new SpeechSDK.SpeechRecognizer(speechConfig, audioConfig);

recognizer.recognizeOnceAsync(
  function (result) {
    alert("Recognition result:" + JSON.stringify(result));
    recognizer.close();
  },
  function (err) {
    alert("An error occurred:" + JSON.stringify(err));
    recognizer.close();
  }
);
``` 

<span data-ttu-id="4fd27-115">[詳細なクイック スタート](/azure/cognitive-services/speech-service/quickstart-js-browser)をご確認ください。</span><span class="sxs-lookup"><span data-stu-id="4fd27-115">Check out our [step-by-step quickstart](/azure/cognitive-services/speech-service/quickstart-js-browser).</span></span>

## <a name="samples"></a><span data-ttu-id="4fd27-116">サンプル</span><span class="sxs-lookup"><span data-stu-id="4fd27-116">Samples</span></span>

<span data-ttu-id="4fd27-117">その他のサンプルについては、[Speech SDK サンプル リポジトリ](https://aka.ms/csspeech/samples)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="4fd27-117">Explore more samples in our [Speech SDK sample repository](https://aka.ms/csspeech/samples).</span></span>
