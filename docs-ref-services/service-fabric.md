---
title: Node.js 用 Azure Service Fabric モジュール
description: Node.js 用 Azure Service Fabric モジュールのリファレンス
author: rwike77
ms.author: ryanwi
manager: timlt
ms.date: 11/12/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: 3fd2f73bc6fddf01548bbb92cce540775d4c7c76
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "49769797"
---
# <a name="azure-service-fabric-modules-for-nodejs"></a>Node.js 用 Azure Service Fabric モジュール

## <a name="overview"></a>概要

Azure Service Fabric は、スケーラブルで信頼性に優れたマイクロサービスとコンテナーのパッケージ化とデプロイ、管理を簡単に行うことができる分散システム プラットフォームです。

Azure Service Fabric の詳細については、[こちら](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)を参照してください。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure Service Fabric の npm モジュールをインストールします。

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a>例

この例では、Azure サブスクリプションのクラスターを一覧表示します。

```javascript
const msRestAzure = require('ms-rest-azure');
const ServiceFabricManagement = require('azure-arm-servicefabric');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new ServiceFabricManagement(
      credentials,
      subscriptionId
    );
    return client.clusters.list();
  })
  .then(clusters => {
    console.log('List of clusters:');
    console.dir(clusters, { depth: null, colors: true });
  });
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
