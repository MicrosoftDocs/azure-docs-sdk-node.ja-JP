---
title: "Node.js 用 Azure 承認モジュール"
description: "Node.js 用 Azure 承認モジュールのリファレンス"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: 6fbaaeba28cac81d360e93c5066791adfa51bcd5
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2018
---
# <a name="azure-authorization-modules-for-nodejs"></a>Node.js 用 Azure 承認モジュール

## <a name="overview"></a>概要

Azure App Service の認証/承認機能を利用すると、アプリケーションのバックエンド コードに変更を加えなくても、ユーザーのサインイン機能をアプリケーションに取り入れることができます。 承認により、アプリケーションの保護が容易になり、またユーザーごとのデータにも対応できるようになります。

## <a name="management-package"></a>管理パッケージ

Node.js 用 Azure 承認モジュールをインストールするには npm を使用します。

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure 承認の npm モジュールをインストールします。

```bash
npm install azure-arm-authorization
```

### <a name="example"></a>例

この例では、要求されたリソース グループのロールの割り当てをすべて一覧表示します。

```javascript
const msRestAzure = require('ms-rest-azure');
const authorizationManagement = require('azure-arm-authorization');

const resourceGroup = 'resource-group-name';
const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
 const client = new authorizationManagement(credentials, subscriptionId);
 client.roleAssignments.listForResourceGroup(resourceGroupName).then(result => {
   console.log(result);
 });
});
```

## <a name="samples"></a>サンプル

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
