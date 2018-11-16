---
title: Node.js 用 Azure Virtual Network モジュール
description: Node.js 用 Azure Virtual Network モジュールのリファレンス
author: jimdial
ms.author: jdial
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: 11341fdff5df3b7521319d841707493db1d07732
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51444346"
---
# <a name="azure-virtual-network-modules-for-nodejs"></a>Node.js 用 Azure Virtual Network モジュール

## <a name="overview"></a>概要

Azure Virtual Network サービスでは、仮想ネットワーク (VNet) を使用して Azure リソースを安全に相互接続することができます。 VNet とは、クラウド内のユーザー独自のネットワークを表したものです。 サブスクリプション専用に Azure クラウドが論理的に分離されています。 VNet は、オンプレミス ネットワークに接続することもできます。

Azure Virtual Network の詳細については、[こちら](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)を参照してください。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure Virtual Network の npm モジュールをインストールします。

```bash
npm install azure-arm-network
```

### <a name="example"></a>例

この例では、仮想ネットワークの一覧を取得して出力します。

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
