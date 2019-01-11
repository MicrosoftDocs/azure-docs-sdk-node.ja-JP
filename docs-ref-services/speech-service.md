---
title: JavaScript 用 Cognitive Services Speech SDK
description: JavaScript 用 Cognitive Services Speech SDK のリファレンス
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 12/18/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.component: speech-service
ms.openlocfilehash: 43a6921d4ec782287cc041ecaabab4567b0fe677
ms.sourcegitcommit: 74417c10aee8987c3e0343728efac75823c902d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2019
ms.locfileid: "54185989"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a><span data-ttu-id="e02ee-103">JavaScript 用 Cognitive Services Speech SDK</span><span class="sxs-lookup"><span data-stu-id="e02ee-103">Cognitive Services Speech SDK for JavaScript</span></span>

## <a name="overview"></a><span data-ttu-id="e02ee-104">概要</span><span class="sxs-lookup"><span data-stu-id="e02ee-104">Overview</span></span>

<span data-ttu-id="e02ee-105">Microsoft では、音声対応アプリケーションの開発を簡素化するために、[Speech Service](https://aka.ms/csspeech) で使用する Speech SDK を提供しています。</span><span class="sxs-lookup"><span data-stu-id="e02ee-105">To simplify the development of speech-enabled applications, Microsoft provides the Speech SDK for use with the [Speech service](https://aka.ms/csspeech).</span></span>
<span data-ttu-id="e02ee-106">Speech SDK には、一貫性のあるネイティブな Speech-to-Text API と Speech Translation API が提供されています。</span><span class="sxs-lookup"><span data-stu-id="e02ee-106">The Speech SDK provides consistent native Speech-to-Text and Speech Translation APIs.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e02ee-107">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="e02ee-107">Install the npm module</span></span>

<span data-ttu-id="e02ee-108">Cognitive Services Speech SDK npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="e02ee-108">Install the Cognitive Services Speech SDK npm module</span></span>

```bash
npm install microsoft-cognitiveservices-speech-sdk
```

### <a name="example"></a><span data-ttu-id="e02ee-109">例</span><span class="sxs-lookup"><span data-stu-id="e02ee-109">Example</span></span> 

<span data-ttu-id="e02ee-110">次のコード スニペットは、ファイルからシンプルな音声認識を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e02ee-110">The following code snippets illustrates how to do simple speech recognition from a file:</span></span>

```javascript 
// Pull in the required packages.
var sdk = require("microsoft-cognitiveservices-speech-sdk");
var fs = require("fs");

// Replace with your own subscription key, service region (e.g., "westus"), and
// the name of the file you want to run through the speech recognizer.
var subscriptionKey = "YourSubscriptionKey";
var serviceRegion = "YourServiceRegion"; // e.g., "westus"
var filename = "YourAudioFile.wav"; // 16000 Hz, Mono

// Create the push stream we need for the speech sdk.
var pushStream = sdk.AudioInputStream.createPushStream();

// Open the file and push it to the push stream.
fs.createReadStream(filename).on('data', function(arrayBuffer) {
  pushStream.write(arrayBuffer.buffer);
}).on('end', function() {
  pushStream.close();
});

// We are done with the setup
console.log("Now recognizing from: " + filename);

// Create the audio-config pointing to our stream and
// the speech config specifying the language.
var audioConfig = sdk.AudioConfig.fromStreamInput(pushStream);
var speechConfig = sdk.SpeechConfig.fromSubscription(subscriptionKey, serviceRegion);

// Setting the recognition language to English.
speechConfig.speechRecognitionLanguage = "en-US";

// Create the speech recognizer.
var recognizer = new sdk.SpeechRecognizer(speechConfig, audioConfig);

// Start the recognizer and wait for a result.
recognizer.recognizeOnceAsync(
  function (result) {
    console.log(result);

    recognizer.close();
    recognizer = undefined;
  },
  function (err) {
    console.trace("err - " + err);

    recognizer.close();
    recognizer = undefined;
  });
``` 

<span data-ttu-id="e02ee-111">[詳細なクイック スタート](/azure/cognitive-services/speech-service/quickstart-js-node)をご確認ください。</span><span class="sxs-lookup"><span data-stu-id="e02ee-111">Check out our [step-by-step quickstart](/azure/cognitive-services/speech-service/quickstart-js-node).</span></span>

## <a name="samples"></a><span data-ttu-id="e02ee-112">サンプル</span><span class="sxs-lookup"><span data-stu-id="e02ee-112">Samples</span></span>

* <span data-ttu-id="e02ee-113">[Node.js 用の詳細なクイック スタート](/azure/cognitive-services/speech-service/quickstart-js-node)</span><span class="sxs-lookup"><span data-stu-id="e02ee-113">[Step-by-step quickstart for Node.js](/azure/cognitive-services/speech-service/quickstart-js-node).</span></span>
* <span data-ttu-id="e02ee-114">[ブラウザーの詳細なクイック スタート](/azure/cognitive-services/speech-service/quickstart-js-browser)</span><span class="sxs-lookup"><span data-stu-id="e02ee-114">[Step-by-step quickstart for the browser](/azure/cognitive-services/speech-service/quickstart-js-browser).</span></span>
* <span data-ttu-id="e02ee-115">その他のサンプルについては、[Speech SDK サンプル リポジトリ](https://aka.ms/csspeech/samples)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="e02ee-115">More samples can be found in our [Speech SDK sample repository](https://aka.ms/csspeech/samples).</span></span>
