---
title: "Node.js 用 Azure Site Recovery モジュール"
description: "Node.js 用 Azure Site Recovery モジュールのリファレンス"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: a1f3e1c18be68dd7e68f38e353e0c2ba224fbaa1
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2018
---
# <a name="azure-site-recovery-modules-for-nodejs"></a>Node.js 用 Azure Site Recovery モジュール

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
