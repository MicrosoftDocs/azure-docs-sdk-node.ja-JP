---
title: Node.js 用 Azure CDN モジュール
description: Node.js 用 Azure CDN モジュールのリファレンス
author: dksimpson
ms.author: v-deasim
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: 1117f8fabfe364d3e5602ee89f652fe98851fef4
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2018
ms.locfileid: "52021976"
---
# <a name="azure-cdn-modules-for-nodejs"></a><span data-ttu-id="5c61d-103">Node.js 用 Azure CDN モジュール</span><span class="sxs-lookup"><span data-stu-id="5c61d-103">Azure CDN modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="5c61d-104">概要</span><span class="sxs-lookup"><span data-stu-id="5c61d-104">Overview</span></span>

<span data-ttu-id="5c61d-105">Azure Content Delivery Network (CDN) は、Azure または他の任意の場所でホストされている高帯域幅コンテンツを配信するためのグローバル ソリューションを開発者に提供します。</span><span class="sxs-lookup"><span data-stu-id="5c61d-105">The Azure Content Delivery Network (CDN) offers developers a global solution for delivering high-bandwidth content that is hosted in Azure or any other location.</span></span> <span data-ttu-id="5c61d-106">CDN を使用すると、Azure BLOB ストレージ、Web アプリケーション、仮想マシン、アプリケーション フォルダー、またはその他の HTTP/HTTPS の場所から読み込んだ一般公開されているオブジェクトをキャッシュすることができます。</span><span class="sxs-lookup"><span data-stu-id="5c61d-106">Using the CDN, you can cache publicly available objects loaded from Azure blob storage, a web application, virtual machine, application folder, or other HTTP/HTTPS location.</span></span> <span data-ttu-id="5c61d-107">CDN のキャッシュを戦略的な場所に配置することで、ユーザーへのコンテンツ配信に最大限の帯域幅を提供することができます。</span><span class="sxs-lookup"><span data-stu-id="5c61d-107">The CDN cache can be held at strategic locations to provide maximum bandwidth for delivering content to users.</span></span> <span data-ttu-id="5c61d-108">CDN は、通常、イメージ、スタイル シート、ドキュメント、ファイル、クライアント側スクリプトでは、HTML ページなどの静的コンテンツの配信に使用されます。</span><span class="sxs-lookup"><span data-stu-id="5c61d-108">The CDN is typically used for delivering static content such as images, style sheets, documents, files, client-side scripts, and HTML pages.</span></span>

## <a name="management-package"></a><span data-ttu-id="5c61d-109">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="5c61d-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="5c61d-110">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="5c61d-110">Install the npm module</span></span>

<span data-ttu-id="5c61d-111">Azure CDN の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="5c61d-111">Install the Azure CDN npm module</span></span>

```bash
npm install azure-arm-cdn
```

### <a name="example"></a><span data-ttu-id="5c61d-112">例</span><span class="sxs-lookup"><span data-stu-id="5c61d-112">Example</span></span>

<span data-ttu-id="5c61d-113">この例では、すべての CDN プロファイルを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="5c61d-113">This example lists all of the CDN profiles.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const cdnManagementClient = require('azure-arm-cdn');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const cdnClient = new cdnManagementClient(credentials, subscriptionId);
  cdnClient.profiles
    .list()
    .then(profilesList => console.log('Retrieved profiles list: ', profilesList));
});
```

## <a name="samples"></a><span data-ttu-id="5c61d-114">サンプル</span><span class="sxs-lookup"><span data-stu-id="5c61d-114">Samples</span></span>

<span data-ttu-id="5c61d-115">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="5c61d-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
