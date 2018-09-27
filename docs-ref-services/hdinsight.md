---
title: Node.js 用 Azure HDInsight モジュール
description: Node.js 用 Azure HDInsight モジュールのリファレンス
ms.service: hdinsight
author: jasonwhowell
ms.author: jasonh
manager: kfile
ms.topic: article
ms.devlang: nodejs
ms.date: 07/18/2017
ms.openlocfilehash: 9a40830e7c5330d4e258840b1b1b2210acf891c5
ms.sourcegitcommit: da60ea91d4215d738b1e0df82066f0fc337ad85a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2018
ms.locfileid: "47325801"
---
# <a name="azure-hdinsight-modules-for-nodejs"></a>Node.js 用 Azure HDInsight モジュール

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
