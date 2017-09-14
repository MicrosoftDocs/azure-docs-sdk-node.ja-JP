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
# <a name="azure-media-services-modules-for-nodejs"></a>Node.js 用 Azure Media Services モジュール

## <a name="overview"></a>概要

Azure Media Services は拡張可能なクラウドベースのプラットフォームです。これにより、開発者はスケーラブルなメディア管理の構築、アプリケーションの配信を実行できます。 Media Services は、各種クライアント (TV、PC、モバイル デバイスなど) へのオンデマンドとライブ ストリーミングでの配信でビデオやオーディオのコンテンツの安全なアップロード、格納、エンコード、パッケージ化を可能にする REST API に基づいています。

Azure Media Services を使用すると、次のことができます。
- Media Services を全面的に使ってエンドツーエンドのワークフローを構築する。 
- ワークフローの一部にサード パーティのコンポーネントを使用する。 たとえば、サード パーティのエンコーダーを使用してエンコードしてから、 Media Services を使用してアップロード、保護、パッケージ化、配信などを行うことができます。
- コンテンツをライブ ストリーム配信したり、オンデマンドで配信したりする。 このトピックでは、その他の関連トピックのリンクも提供します。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure Media Services の npm モジュールをインストールします。

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a>例

この例では、リソース グループのすべてのメディア サービスを一覧表示します。

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

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
