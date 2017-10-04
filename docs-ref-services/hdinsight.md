---
title: "Node.js 用 Azure HDInsight モジュール"
description: "Node.js 用 Azure HDInsight モジュールのリファレンス"
keywords: Azure,SDK,API,HDInsight, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 1df988e98def42dcf33e90b4c3debece8cbe85e3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-hdinsight-modules-for-nodejs"></a>Node.js 用 Azure HDInsight モジュール

## <a name="overview"></a>概要

Azure HDInsight は、Hortonworks Data Platform (HDP) の Hadoop コンポーネントのクラウド ディストリビューションです。 Apache Hadoop は本来、コンピューターのクラスターでのビッグ データ セットの分散処理および分析のためのオープンソース フレームワークでした。

HDInsight は、Hadoop テクノロジを使いやすくしたもので、次の特徴を備えています。
- 簡単なセットアップと構成。 HDInsight での Hadoop クラスターのプロビジョニングに関するページを参照してください。
- 高い可用性と信頼性。 HDInsight の可用性と信頼性に関するページを参照してください。
- Active Directory との統合を通じたセキュリティとガバナンス。 ドメインに参加しているクラスターに関するページを参照してください。
- ジョブの中断のない動的スケーリング
- コンポーネントの更新と現在のバージョン。 HDInsight での Hadoop のコンポーネントとバージョンに関するページを参照してください。
- Web Apps や SQL Database などの他の Azure サービスとの統合

Hadoop テクノロジ スタックには、Apache Hive、HBase、Spark、Kafka、その他の多くの関連するソフトウェアおよびユーティリティが含まれます。 

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-modules"></a>npm モジュールのインストール

Node.js 用 Azure HDInsight モジュールをインストールするには npm を使用します。

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a>例 

この例では、HD Insight クライアントを作成し、利用可能なクラスターをすべて一覧表示します。 

```javascript
const msRestAzure = require('ms-rest-azure');
const HDInsightManagementClient = require('azure-arm-hdinsight');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = HDInsightManagementClient.createHDInsightManagementClient(
        credentials
    );

    credentials.subscriptionId = subscriptionId;

    client.clusters.list((err, result) => {
        console.log(result);
    });
});
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。