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
# <a name="cognitive-services-speech-sdk-for-javascript"></a>JavaScript 用 Cognitive Services Speech SDK

## <a name="overview"></a>概要

Microsoft では、音声対応アプリケーションの開発を簡素化するために、[Speech Service](https://aka.ms/csspeech) で使用する Speech SDK を提供しています。
Speech SDK には、一貫性のあるネイティブな Speech-to-Text API と Speech Translation API が提供されています。

> [!NOTE]
> Cognitive Services Speech SDK は、現在ブラウザーでのみ使用できます。
> NPM パッケージは追って利用できるようになります。

### <a name="install-the-speech-sdk"></a>Speech SDK のインストール

Speech SDK を [.zip パッケージ](https://aka.ms/csspeech/jsbrowserpackage)としてダウンロードし、展開します。
これにより `microsoft.cognitiveservices.speech.sdk.bundle.js` という名前のファイルを含め、複数のファイルが展開されます。
Speech SDK の使用を開始するには、このファイルをスクリプト リソースとして Web ページに読み込みます。

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a>例 

次のコード スニペットは、お使いのブラウザーからシンプルな音声認識を実行する方法を示しています。

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

[詳細なクイック スタート](/azure/cognitive-services/speech-service/quickstart-js-browser)をご確認ください。

## <a name="samples"></a>サンプル

その他のサンプルについては、[Speech SDK サンプル リポジトリ](https://aka.ms/csspeech/samples)を確認してください。
