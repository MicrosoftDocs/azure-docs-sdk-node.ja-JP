---
title: "Node.js 用 Azure Site Recovery モジュール"
description: "Node.js 用 Azure Site Recovery モジュールのリファレンス"
keywords: Azure,SDK,API,Site Recovery, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: 3537503118a6fbe181c8cc4b26da545a4bdbd764
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-site-recovery-modules-for-nodejs"></a>Node.js 用 Azure Site Recovery モジュール

## <a name="overview"></a>概要

Site Recovery は、Azure VM のリージョン間レプリケーション、オンプレミスの仮想マシンと物理サーバーの Azure へのレプリケーション、セカンダリ データセンターへのオンプレミス マシンのレプリケーションを自動化します。

Azure Site Recovery の詳細については、[こちら](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)を参照してください。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure Site Recovery サービスの npm モジュールをインストールします。

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a>例

この例では、リソース グループの Site Recovery サービスを一覧表示します。

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesManagement = require('azure-arm-recoveryservices');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesManagement(credentials, subscriptionId);
    return client.vaults.listByResourceGroup(resourceGroupName);
  })
  .then(vaults => {
    console.log('List of vaults:');
    console.dir(vaults, { depth: null, colors: true });
  });
  
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
