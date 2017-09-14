---
title: "Node.js 用 Azure DevTest Labs モジュール"
description: "Node.js 用 Azure DevTest Labs モジュールのリファレンス"
keywords: Azure,SDK,API,DevTest Labs, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 933ce8971e02c2898d296112282169b8c7dca1c7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a>Node.js 用 Azure DevTest Labs モジュール

## <a name="overview"></a>概要

Azure DevTest Labs は、無駄を最小限に抑え、コストを管理しつつ、Azure で迅速に環境を作成するためのサポートを開発者とテスト担当者に提供するサービスです。 再利用可能なテンプレートとアーティファクトを使用して Windows と Linux の環境を迅速にプロビジョニングすることで、アプリケーションの最新バージョンをテストできます。 デプロイ パイプラインと DevTest ラボを簡単に統合し、オンデマンドの環境をプロビジョニングします。 複数のテスト エージェントをプロビジョニングしてロード テストをスケール アップし、トレーニングおよびデモの事前プロビジョニング済み環境を作成します。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure DevTest Labs の npm モジュールをインストールします。

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a>例

この例では、ラボの詳細を取得して出力します。

```javascript
const msRestAzure = require('ms-rest-azure');
const DevTestLabsClient = require('azure-arm-devtestlabs');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';
const labName = 'your-lab-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DevTestLabsClient(credentials, subscriptionId);
    return client.labOperations.getResource(resourceGroupName, labName);
  })
  .then(lab => {
    console.log('Details of lab:');
    console.dir(lab, { depth: null, colors: true });
  });


```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
