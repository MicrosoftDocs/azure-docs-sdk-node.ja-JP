---
title: Node.js 用 Azure Power BI Embedded モジュール
description: Node.js 用 Azure Power BI Embedded モジュールのリファレンス
author: markingmyname
ms.author: maghan
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 58251dd1cd3a672a5167193f74d311952d70e84e
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2018
ms.locfileid: "51133991"
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a>Node.js 用 Azure Power BI Embedded モジュール

Azure Power BI Embedded サービスを使用すると、ノード アプリケーションに Power BI レポートをすぐに統合し、グラフやレポートを作成または編集することができます。

Power BI Embedded の詳細については、[こちら](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/)を参照してください。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure Power BI の npm モジュールをインストールします。

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a>例

この例では、既存のリソース グループにワークスペース コレクションを作成します。

```javascript
const msRestAzure = require('ms-rest-azure');
const PowerBIEmbeddedManagementClient = require('azure-arm-powerbiembedded');

const creationOptions = {
  location: 'northcentralus',
  tags: {
    key1: 'value1',
    key2: 'value2'
  },
  sku: {
    name: 'S1',
    teir: 'Standard'
  }
};

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';
const workspace = 'workspace-collection-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new PowerBIEmbeddedManagementClient(
      credentials,
      subscriptionId
    );
    return client.workspaceCollections.create(
      resourceGroup,
      workspace,
      creationOptions
    );
  })
  .then(workspaces => console.dir(workspaces, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
