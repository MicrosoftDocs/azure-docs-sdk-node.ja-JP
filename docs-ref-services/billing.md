---
title: Node.js 用 Azure 課金モジュール
description: Node.js 用 Azure 課金モジュールのリファレンス
author: tfitzmac
ms.author: tomfitz
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: 111ca8d4ed40200a307b608915d71d2fa6944ed2
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260345"
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
