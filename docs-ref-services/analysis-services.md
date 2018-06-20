---
title: Node.js 用 Azure Analysis Services モジュール
description: Node.js 用 Azure Analysis Services モジュールのリファレンス
author: Minewiskan
ms.author: owend
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: 166d0450ac9b2d005f3ce4ecba5ce36e1786ae09
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260365"
---
# <a name="azure-analysis-services-modules-for-nodejs"></a>Node.js 用 Azure Analysis Services モジュール

## <a name="overview"></a>概要
このパッケージには、Microsoft Azure Analysis Services の管理を省力化する Node.js モジュールが備わっています。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure Analysis Services の npm モジュールをインストールします。

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a>例

この例では、利用可能なすべての Analysis Services サーバーを一覧表示します。

```javascript
const msRestAzure = require('ms-rest-azure');
const analysisServicesManagement = require('azure-arm-analysisservices');

const subscriptionId = 'your-subscription-id';
let analysisServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  analysisServicesClient = new analysisServicesManagement(credentials, subscriptionId);

  analysisServicesClient.servers
    .list()
    .then(servers => console.log('Retrieved analysis services servers: ', servers));
});
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
