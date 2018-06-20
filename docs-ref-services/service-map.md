---
title: Node.js 用 Azure Service Map モジュール
description: Node.js 用 Azure Service Map モジュールのリファレンス
author: bwren
ms.author: bwren
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: db064603e32446ba2f094da2a1601520b99a7304
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265983"
---
# <a name="azure-service-map-modules-for-nodejs"></a>Node.js 用 Azure Service Map モジュール

サービス マップは、Windows および Linux システムのアプリケーション コンポーネントを自動的に検出し、サービス間の通信をマップします。 Service Map は、TCP 接続アーキテクチャ全体におけるサーバー、プロセス、ポートの間の接続を表示します。エージェントのインストール以外の構成は必要ありません。

Azure Service Map の詳細については、[こちら](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map)を参照してください。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure Service Map の npm モジュールをインストールします。

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a>例

この例では、指定したリソース グループおよびワークスペースのすべてのサービス マップを一覧表示します。

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
