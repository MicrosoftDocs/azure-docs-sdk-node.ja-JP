---
title: Node.js 用 Azure Data Lake Analytics モジュール
description: Node.js 用 Azure Data Lake Analytics モジュールのリファレンス
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Analytics
ms.openlocfilehash: 97a846d9970310931e05e681b23b5787c97260b6
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2018
ms.locfileid: "51134331"
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a>Node.js 用 Azure Data Lake Analytics モジュール

Azure Data Lake Analytics は、ビッグ データ分析を簡略化するオンデマンド分析ジョブ サービスです。 分散インフラストラクチャの運用ではなく、ジョブの記述、実行、および管理に集中できます。 ハードウェアのデプロイ、構成、チューニングを行う代わりに、クエリを作成してデータを変換し、価値ある洞察を抽出します。 この分析サービスでは、必要な性能をダイヤルで設定して、どのような規模のジョブでも即座に処理できます。 ジョブの実行中にのみ課金されるコスト効率の良いサービスです。 この分析サービスは Azure Active Directory をサポートしているので、既存のオンプレミスの ID システムと統合してアクセス権限とロールを管理できます。 また、SQL のメリットとユーザー コードの表現力を融合した U-SQL 言語が組み込まれています。 U-SQL のスケーラブルな分散ランタイムで、Azure の SQL Server、Azure SQL Database、Azure SQL Data Warehouse にまたがるストア内のデータを効率良く分析できます。

### <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Node.js 用 Azure Data Lake Analytics モジュールをインストールするには npm を使用します。

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a>例

この例では、特定のサブスクリプションのすべての Analytics アカウントを一覧表示します。

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-analytics');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeAnalyticsAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
