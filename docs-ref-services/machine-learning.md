---
title: Node.js 用 Azure Machine Learning モジュール
description: Node.js 用 Azure Machine Learning モジュールのリファレンス
author: hning86
ms.author: haining
manager: mwinkle
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 7dfa6d8fa633863fe834ce73462584e79c312c5d
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259891"
---
# <a name="azure-machine-learning-modules-for-nodejs"></a>Node.js 用 Azure Machine Learning モジュール

機械学習は、将来の動き、結果、傾向を予測するためにコンピューターで既存のデータからの学習を行う、データ サイエンスの手法の 1 つ です。 機械学習からのこうした予想や予測によってアプリやデバイスの機能性を高めることができます。 オンライン ショッピングでは、ユーザーが今までに購入した製品に基づいて他の商品をお勧めするのに機械学習が役立っています。 クレジット カードが読み取られると、機械学習は、トランザクションをトランザクションのデータベースと比較し、不正の検出を支援します。 ロボット掃除機が部屋を掃除するとき、機械学習は、作業が行われているかどうかを判断するのを支援します。

## <a name="management-package"></a>管理パッケージ


### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure Machine Learning の npm モジュールをインストールします。

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a>例

この例では、Machine Learning コミットメント プランをすべて一覧表示します。

```javascript
const msRestAzure = require('ms-rest-azure');
const MachineLearningManagement = require('azure-arm-machinelearning');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new MachineLearningManagement.CommitmentPlansManagementClient(
      credentials,
      subscriptionId
    );
    return client.commitmentPlans.list();
  })
  .then(commitmentPlans => {
    console.log('List of commitmentPlans:');
    console.dir(commitmentPlans, { depth: null, colors: true });
  });
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
