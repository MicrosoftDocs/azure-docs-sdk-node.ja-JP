---
title: Node.js 用 Azure Media Services モジュール
description: Node.js 用 Azure Media Services モジュールのリファレンス
author: Juliako
ms.author: juliako
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: bfd4402c215a81c9ed8753cfe9ad9dbfaa52bd6f
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2018
ms.locfileid: "52145807"
---
# <a name="azure-media-services-modules-for-nodejs"></a>Node.js 用 Azure Media Services モジュール

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
