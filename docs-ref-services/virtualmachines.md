---
title: "Node.js 用仮想マシン モジュール - Azure"
description: "Node.js 用 Azure 仮想マシン モジュールのリファレンス ガイド"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 608a915499d7c32c2c8b04464f716fa4fd17243d
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2018
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a>Node.js 用 Azure 仮想マシン モジュール

## <a name="overview"></a>概要

コードから Node.js 用 Azure 管理モジュールを使用して、Windows と Linux の新しい仮想マシンおよび仮想マシン スケール セットを定義、構成、デプロイします。 これらのモジュールを使って、Azure サブスクリプション内の停止している VM にディスクをアタッチ (または停止している VM からディスクをデタッチ) したり、既存の仮想マシンを起動/停止したりすることができます。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure コンピューティングの npm モジュールをインストールします。

```bash
npm install azure-arm-compute
```   

### <a name="example"></a>例

次の例は、Azure にログインして管理クライアントを作成し、特定の場所、発行元、プラン、SKU のすべての VM イメージをリストする方法を示しています。

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'Canonical',   // publisher name
        'UbuntuServer',            // offer
        '16.04-LTS'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a>サンプル

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
