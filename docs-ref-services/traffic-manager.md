---
title: Node.js 用 Azure Traffic Manager モジュール
description: Node.js 用 Azure Traffic Manager モジュールのリファレンス
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: 2a32eed460c6076011fdcf31d77200502ef61a3d
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "49675757"
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a>Node.js 用 Azure Traffic Manager モジュール

## <a name="overview"></a>概要

Microsoft Azure Traffic Manager では、さまざまなデータセンターのサービス エンドポイントへのユーザー トラフィックの分散を制御できます。 Traffic Manager でサポートされるサービス エンドポイントには、Azure VM、Web Apps、およびクラウド サービスが含まれます。 Azure 以外の外部エンドポイントで Traffic Manager を使用することもできます。

Azure Traffic Manager の詳細については、[こちら](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)をご覧ください。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure Traffic Manager の npm モジュールをインストールします。

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a>例

この例では、特定のリソース グループのすべての Traffic Manager を一覧表示します。

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
