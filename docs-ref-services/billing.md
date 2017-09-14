---
title: "Node.js 用 Azure 課金モジュール"
description: "Node.js 用 Azure 課金モジュールのリファレンス"
keywords: "Azure,SDK,API,課金, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: fa861aebbd5cbced6477ceeb67dbb5acc7eb233e
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-billing-modules-for-nodejs"></a>Node.js 用 Azure 課金モジュール

## <a name="overview"></a>概要
Azure の課金情報や請求書には、Azure Billing API でアクセスできます。

この API を使うには、アカウント管理者が Azure Portal でオプトインする必要があります。 「[ロールを使用した Azure 課金情報へのアクセスの管理](https://docs.microsoft.com/azure/billing/billing-manage-access)」を参照してください。

### <a name="install-the-npm-module"></a>npm モジュールのインストール 

Azure 課金の npm モジュールをインストールします。 

```bash
npm install azure-arm-billing
```
### <a name="example"></a>例 
 
この例では、過去の全請求書の一覧を出力します。
 
```javascript 
const msRestAzure = require('ms-rest-azure');
const BillingManagement = require('azure-arm-billing');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    let client = new BillingManagement(credentials, subscriptionId);
    return client.invoices.list();
  })
  .then(invoices => {
    console.log('List of invoices:');
    console.dir(invoices, { depth: null, colors: true });
  });
``` 


## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
