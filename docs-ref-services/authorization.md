---
title: Node.js 用 Azure 承認モジュール
description: Node.js 用 Azure 承認モジュールのリファレンス
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: 5be0e069d0acf72de65e891e6304ef1ca78e967a
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260405"
---
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="2fcf5-103">Node.js 用 Azure 承認モジュール</span><span class="sxs-lookup"><span data-stu-id="2fcf5-103">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2fcf5-104">概要</span><span class="sxs-lookup"><span data-stu-id="2fcf5-104">Overview</span></span>

<span data-ttu-id="2fcf5-105">Azure App Service の認証/承認機能を利用すると、アプリケーションのバックエンド コードに変更を加えなくても、ユーザーのサインイン機能をアプリケーションに取り入れることができます。</span><span class="sxs-lookup"><span data-stu-id="2fcf5-105">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="2fcf5-106">承認により、アプリケーションの保護が容易になり、またユーザーごとのデータにも対応できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2fcf5-106">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="2fcf5-107">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="2fcf5-107">Management package</span></span>

<span data-ttu-id="2fcf5-108">Node.js 用 Azure 承認モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="2fcf5-108">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2fcf5-109">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="2fcf5-109">Install the npm module</span></span>

<span data-ttu-id="2fcf5-110">Azure 承認の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="2fcf5-110">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="2fcf5-111">例</span><span class="sxs-lookup"><span data-stu-id="2fcf5-111">Example</span></span>

<span data-ttu-id="2fcf5-112">この例では、要求されたリソース グループのロールの割り当てをすべて一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="2fcf5-112">This example lists all role assignments for the requested resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="2fcf5-113">サンプル</span><span class="sxs-lookup"><span data-stu-id="2fcf5-113">Samples</span></span>

<span data-ttu-id="2fcf5-114">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="2fcf5-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
