---
title: "Node.js 用 Azure Container Registry モジュール"
description: "Node.js 用 Azure Container Registry モジュールのリファレンス"
keywords: Azure,SDK,API,Container Registry, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: 6ded68c19971a8fe580f440862d0fe05a1def6a2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-container-registry-modules-for-nodejs"></a>Node.js 用 Azure Container Registry モジュール

## <a name="overview"></a>概要

Azure Container Registry は、オープンソースの Docker Registry 2.0 に基づいた、管理された Docker レジストリ サービスです。 プライベート Docker コンテナー イメージを保存および管理する Azure コンテナー レジストリを作成および管理します。 既存のコンテナーの開発とデプロイ パイプラインで Azure のコンテナー レジストリを使用し、Docker コミュニティの専門知識を活用します。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure Container Registry の npm モジュールをインストールします。

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a>例

この例では、利用可能なコンテナーの一覧を取得します。

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
