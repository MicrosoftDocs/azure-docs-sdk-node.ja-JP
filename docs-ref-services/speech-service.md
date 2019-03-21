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
ms.subservice: speech-service
ms.openlocfilehash: b1375b6beb478cab2475539c03b6bac9f0ea99e0
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052573"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a>JavaScript 用 Cognitive Services Speech SDK

## <a name="overview"></a>概要

Microsoft では、音声対応アプリケーションの開発を簡素化するために、[Speech Service](https://aka.ms/csspeech) で使用する Speech SDK を提供しています。
Speech SDK には、一貫性のあるネイティブな Speech-to-Text API と Speech Translation API が提供されています。

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Cognitive Services Speech SDK npm モジュールのインストール

```bash
npm install microsoft-cognitiveservices-speech-sdk
```

### <a name="example"></a>例 

次のコード スニペットは、ファイルからシンプルな音声認識を実行する方法を示しています。

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

[詳細なクイック スタート](/azure/cognitive-services/speech-service/quickstart-js-node)をご確認ください。

## <a name="samples"></a>サンプル

* [Node.js 用の詳細なクイック スタート](/azure/cognitive-services/speech-service/quickstart-js-node)
* [ブラウザーの詳細なクイック スタート](/azure/cognitive-services/speech-service/quickstart-js-browser)
* その他のサンプルについては、[Speech SDK サンプル リポジトリ](https://aka.ms/csspeech/samples)を確認してください。
