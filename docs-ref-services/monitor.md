---
title: Node.js 用 Azure Monitor モジュール
description: Node.js 用 Azure Monitor モジュールのリファレンス
author: rbouche
ms.author: robb
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: 8a9411b7979f3130a1aa24fd2a0b294fc7f67718
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259305"
---
# <a name="azure-monitor-modules-for-nodejs"></a>Node.js 用 Azure Monitor モジュール

クラウド アプリケーションは、動的なパーツを多数使った複雑な構成になっています。 監視では、アプリケーションを正常な状態で稼働させ続けるためのデータを取得できます。 また、潜在的な問題を防止したり、発生した問題をトラブルシューティングするのにも役立ちます。 さらに、監視データを使用して、アプリケーションに関する深い洞察を得ることもできます。 そのような知識は、アプリケーションのパフォーマンスや保守容易性を向上させたり、手作業での介入が必要な操作を自動化したりするうえで役立ちます。

## <a name="management-package"></a>管理パッケージ

### <a name="install-npm-module"></a>npm モジュールのインストール

```bash
npm install azure-arm-monitor
```

### <a name="example"></a>例

このコード例では、リソース グループに関連付けられているすべてのアラート ルールを出力します。

```javascript
const msRestAzure = require('ms-rest-azure');
const monitorManagementClient = require('azure-arm-monitor');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new monitorManagementClient(credentials, subscriptionId);
    client.alertRules.listByResourceGroup(resourceGroupName, rules => {
      console.log('List of rules:');
      console.dir(rules, { depth: null, colors: true });
    })
  });

```

### <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
