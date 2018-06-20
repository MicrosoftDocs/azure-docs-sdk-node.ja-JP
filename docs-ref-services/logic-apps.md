---
title: Node.js 用 Azure Logic Apps モジュール
description: Node.js 用 Azure Logic Apps モジュールのリファレンス
author: ecfan
ms.author: estfan
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 2de867fdd0aa31b63b9680cc3f0c2e7f6301e632
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34261553"
---
# <a name="azure-logic-apps-modules-for-nodejs"></a>Node.js 用 Azure Logic Apps モジュール

Logic Apps では、クラウド上でのスケーラブルな統合やワークフローを簡略化し、実装するための手段を提供します。 また、ワークフローと呼ばれる一連のステップとしてプロセスをモデル化し、自動化するためのビジュアル デザイナーが用意されています。 サービスとプロトコルをまたいだ迅速な統合のために、クラウドとオンプレミスの両方で数多くのコネクタが提供されています。 ロジック アプリはトリガー ("Dynamics CRM にアカウントが追加されたとき" など) によって起動することができ、その後も数多くのアクション、変換、条件ロジックを組み合わせて開始することができます。

Logic Apps を使用する利点は次のとおりです。
- わかりやすい設計ツールを使って複雑なプロセスを設計できるため、時間を節約できる
- コードでは実装が難しいパターンやワークフローをシームレスに実装できる
- テンプレートを基に簡単に設計を開始できる
- 独自のカスタム API、コード、アクションでロジック アプリをカスタマイズできる
- オンプレミスとクラウドにまたがる異なるシステム間で接続や同期ができる
- BizTalk Server、API Management、Azure Functions、Azure Service Bus を基に作成でき、最上級の統合サポートが得られる

Logic Apps は完全に管理された iPaaS (サービスとしての統合プラットフォーム) であり、開発者はホスティング、スケーラビリティ、可用性、管理能力の構築について頭を悩ます必要がなくなります。 Logic Apps は需要に合わせて自動的にスケールアップします。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Node.js 用 Azure ロジック モジュールをインストールします。

```bash
npm install azure-arm-logic
```

### <a name="example"></a>例

```javascript
const msRestAzure = require('ms-rest-azure');
const LogicManagement = require('azure-arm-logic');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const subscriptionId = 'subscription-id';
    const client = new LogicManagement(credentials, subscriptionId);
    return client.workflows.listBySubscription();
  })
  .then(workflows => console.log(workflows));
```

### <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
