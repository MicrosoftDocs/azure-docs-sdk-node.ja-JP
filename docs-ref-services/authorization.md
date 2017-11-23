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
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="09aa0-104">Node.js 用 Azure 承認モジュール</span><span class="sxs-lookup"><span data-stu-id="09aa0-104">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="09aa0-105">概要</span><span class="sxs-lookup"><span data-stu-id="09aa0-105">Overview</span></span>

<span data-ttu-id="09aa0-106">Azure App Service の認証/承認機能を利用すると、アプリケーションのバックエンド コードに変更を加えなくても、ユーザーのサインイン機能をアプリケーションに取り入れることができます。</span><span class="sxs-lookup"><span data-stu-id="09aa0-106">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="09aa0-107">承認により、アプリケーションの保護が容易になり、またユーザーごとのデータにも対応できるようになります。</span><span class="sxs-lookup"><span data-stu-id="09aa0-107">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="09aa0-108">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="09aa0-108">Management package</span></span>

<span data-ttu-id="09aa0-109">Node.js 用 Azure 承認モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="09aa0-109">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="09aa0-110">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="09aa0-110">Install the npm module</span></span>

<span data-ttu-id="09aa0-111">Azure 承認の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="09aa0-111">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="09aa0-112">例</span><span class="sxs-lookup"><span data-stu-id="09aa0-112">Example</span></span>

<span data-ttu-id="09aa0-113">この例では、要求されたリソース グループのロールの割り当てをすべて一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="09aa0-113">This example lists all role assignments for the requested resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="09aa0-114">サンプル</span><span class="sxs-lookup"><span data-stu-id="09aa0-114">Samples</span></span>

<span data-ttu-id="09aa0-115">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="09aa0-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
