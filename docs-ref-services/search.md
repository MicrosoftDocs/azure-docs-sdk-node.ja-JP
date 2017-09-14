---
title: "Node.js 用 Azure Search モジュール"
description: "Node.js 用 Azure Search モジュールのリファレンス"
keywords: Azure,SDK,API,Search, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: dc9d4c5128c99a9518bd059e191bb11e4de4b78f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-search-modules-for-nodejs"></a>Node.js 用 Azure Search モジュール

## <a name="overview"></a>概要

Azure Search は、サーバーとインフラストラクチャの管理を Microsoft に委任するクラウドの Search-as-a-service (サービスとしての検索) ソリューションです。データを取り込んだら、アプリケーションに検索機能を追加して、すぐに利用を開始できます。

Azure Search の詳細については、[こちら](https://docs.microsoft.com/azure/search/search-what-is-azure-search)を参照してください。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure Search の npm モジュールをインストールします。

```bash
npm install azure-arm-search
```

### <a name="example"></a>例

この例では、Azure に新しい Search サービスを作成し、そのリソース グループに含まれるリソースを一覧表示します。

```javascript
const msRestAzure = require('ms-rest-azure');
const SearchManagement = require('azure-arm-search');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'yourResourceGroup';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SearchManagement(credentials, subscriptionId);
    return client.services.listByResourceGroup(resourceGroup);
  })
  .then(services => console.dir(services, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error ocurred');
    console.dir(err, { depth: null, colors: true });
  });
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
