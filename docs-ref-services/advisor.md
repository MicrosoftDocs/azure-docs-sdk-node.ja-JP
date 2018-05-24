---
title: Node.js 用 Azure Advisor モジュール
description: Node.js 用 Azure Advisor モジュールのリファレンス
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 07b6369ef69343cc47cd38484ebb87d050264775
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="azure-advisor-modules-for-nodejs"></a>Node.js 用 Azure Advisor モジュール

## <a name="overview"></a>概要

Azure Advisor は、ベスト プラクティスに従って Azure デプロイメントを最適化できるようにする、個人用に設定されたクラウド コンサルタントです。 Azure のリソースの構成と利用統計情報を分析し、Azure リソースの費用対効果、パフォーマンス、高可用性、セキュリティを向上させるために役立つソリューションを推奨します。

Advisor では、以下の項目を実行できます。
- 先の見通しを持ち、処理が可能で、個人用に設定されたベスト プラクティスの推奨事項を取得する。
- リソースのパフォーマンス、セキュリティ、および高可用性を向上させながら、総合的な Azure の支出を削減する機会を捉える。
- アクション提案をインラインで含めた推奨事項を取得する。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure Advisor の npm モジュールをインストールします。

```bash
npm install azure-arm-advisor
```

### <a name="example"></a>例

この例では、Azure Advisor からの推奨事項を一覧表示します。

```javascript
const msRestAzure = require('ms-rest-azure');
const advisorManagement = require('azure-arm-advisor');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new advisorManagement(credentials, subscriptionId);
  client.recommendations.list().then(recommendations => {
    console.log('List of recommendations:');
    console.dir(recommendations, {depth: null, colors: true});
  });
});
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
