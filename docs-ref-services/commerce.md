---
title: "Node.js 用 Azure コマース モジュール"
description: "Node.js 用 Azure コマース モジュールのリファレンス"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: 0597765543cd838049d3946b90ae128875edd4e5
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2018
---
# <a name="azure-commerce-modules-for-nodejs"></a>Node.js 用 Azure コマース モジュール

## <a name="overview"></a>概要

Azure コマース API を使用すると、使用状況やリソースに関するデータを、お使いのデータ分析ツールで取得できます。 Azure Resource Usage API と Azure Resource RateCard API は、コストを正確に予測して管理するうえで役立ちます。 これらの API は、Azure Resource Manager が公開している API ファミリに含まれ、リソース プロバイダーとして実装されています。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure コマースの npm モジュールをインストールします。

```bash
npm install azure-arm-commerce
```

### <a name="example"></a>例

この例では、Azure の先月の推定消費量データを取得します。

```javascript
const msRestAzure = require('ms-rest-azure');
const CommerceManagement = require('azure-arm-commerce');

const endDate = new Date();
endDate.setUTCHours(0, 0, 0, 0);
const startDate = new Date();
startDate.setMonth(startDate.getMonth() - 1);
startDate.setUTCHours(0, 0, 0, 0);

const subscriptionId = 'your-subscription-id';
const usageOptions = {
  showDetails: true,
  granularity: 'Daily'
};

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new CommerceManagement(credentials, subscriptionId);
    return client.usageAggregates.list(startDate, endDate, usageOptions);
  })
  .then(usage => {
    console.dir(usage, { depth: null, colors: true });
  });
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
