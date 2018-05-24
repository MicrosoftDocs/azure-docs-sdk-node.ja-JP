---
title: Node.js 用 Azure Operational Insights モジュール
description: Node.js 用 Azure Operational Insights モジュールのリファレンス
author: MGoedtel
ms.author: magoedte
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: 2cd948a57925954ecddc077ead727b1a7689ce0e
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="azure-operational-insights-modules-for-nodejs"></a>Node.js 用 Azure Operational Insights モジュール

Node.js 用 Azure Operational Insights モジュールをインストールするには npm を使用します。

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a>例 

この例では、クライアントを作成して Operational Insights に接続し、指定したリソース グループの一連のワークスペースを取得しています。

```javascript
const msRestAzure = require('ms-rest-azure');
const OperationalInsightsManagement = require('azure-arm-operationalinsights');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new OperationalInsightsManagement(
        credentials,
        subscriptionId
    );
    return client.workspaces.listByResourceGroup('resource-group-name');
})
.then(workspaces => {
    console.log(workspaces);
});
``` 

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
