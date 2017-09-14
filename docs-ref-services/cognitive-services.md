---
title: "Node.js 用 Azure Cognitive Services モジュール"
description: "Node.js 用 Azure Cognitive Services モジュールのリファレンス"
keywords: Azure,SDK,API,Cognitive Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fba98930fccaf4fa40dd1d0224031276f5fb7f84
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a>Node.js 用 Azure Cognitive Services モジュール

## <a name="overview"></a>概要

Azure Cognitive Services は、よりインテリジェントで魅力的、かつ発見可能性を高めたアプリケーションの開発を支援する API、SDK、サービスをセットにしたものです。 Microsoft の絶えず進化する機械学習 API 群をさらに発展させた Microsoft Cognitive Services を通じて、開発者はそのアプリケーションに感情認識や映像検出、顔認識、音声認識、視覚認識、音声理解、言語理解など、インテリジェントな機能を簡単に追加することができます。 Microsoft が目指しているのは、見たり聞いたり話したり理解したりする機能、そして論理的な思考まで備えようとしているシステムを通じて、よりパーソナライズされたコンピューティング体験と生産性の向上を実現することです。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure Cognitive Services の npm モジュールをインストールします。

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a>例

この例では、すべての Cognitive Services アカウントを一覧表示します。

```javascript
const msRestAzure = require('ms-rest-azure');
const cognitiveServicesManagementClient = require('azure-arm-cognitiveservices');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const cognitiveServicesClient = new cognitiveServicesManagementClient(
      credentials,
      subscriptionId
    );
    return cognitiveServicesClient.cognitiveServicesAccounts.list();
  })
  .then(cognitiveServicesAccounts => {
    console.log('List of accounts:');
    console.dir(cognitiveServicesAccounts, { depth: null, colors: true });    
  });

```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
