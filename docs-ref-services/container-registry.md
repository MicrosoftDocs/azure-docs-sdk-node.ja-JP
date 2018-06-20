---
title: Node.js 用 Azure Container Registry モジュール
description: Node.js 用 Azure Container Registry モジュールのリファレンス
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: ca83b97e94312498f4f93c587cf0c90485136841
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259941"
---
# <a name="azure-container-registry-modules-for-nodejs"></a>Node.js 用 Azure Container Registry モジュール

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
