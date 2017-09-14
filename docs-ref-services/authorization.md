---
title: "Node.js 用 Azure 承認モジュール"
description: "Node.js 用 Azure 承認モジュールのリファレンス"
keywords: "Azure,SDK,API,承認, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: de843bf1afed77afdb9bde035962a1c151d9c1bb
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
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
