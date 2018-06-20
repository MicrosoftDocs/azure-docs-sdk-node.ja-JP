---
title: Node.js 用 Azure Automation モジュール
description: Node.js 用 Azure Automation モジュールのリファレンス
author: eamonoreilly
ms.author: eamono
manager: nirb
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 5efe0c0633313bcf489b05b8a54f71bba9a00da5
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264713"
---
# <a name="azure-automation-modules-for-nodejs"></a>Node.js 用 Azure Automation モジュール

## <a name="overview"></a>概要

ユーザーは Azure Automation を使用すると、クラウド環境およびエンタープライズ環境で一般的に実行される、手動で実行時間が長く、エラーが起こりやすく、頻繁に繰り返されるタスクを自動化する手段を得られます。 Automation によって時間を節約し、普段の管理タスクの信頼性を高めることができるほか、一定の間隔で自動的に実行されるようにタスクのスケジュールを設定することもできます。 Runbook を使用してプロセスを自動化したり、Desired State Configuration を使用して構成管理を自動化したりすることができます。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-modules-with-npm"></a>npm を使ったモジュールのインストール

Node.js 用 Azure Automation モジュールをインストールするには npm を使用します。

```bash
npm install azure-arm-automation
```

### <a name="example"></a>例

この例では、Automation アカウントを一覧表示します。

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));

```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
