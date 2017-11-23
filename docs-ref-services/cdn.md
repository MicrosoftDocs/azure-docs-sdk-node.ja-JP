---
title: "Node.js 用 Azure CDN モジュール"
description: "Node.js 用 Azure CDN モジュールのリファレンス"
keywords: Azure,SDK,API,CDN, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: ae44606510037fa3ba3d5b95196a40f8eeef3afe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cdn-modules-for-nodejs"></a><span data-ttu-id="ea7df-104">Node.js 用 Azure CDN モジュール</span><span class="sxs-lookup"><span data-stu-id="ea7df-104">Azure CDN modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="ea7df-105">概要</span><span class="sxs-lookup"><span data-stu-id="ea7df-105">Overview</span></span>

<span data-ttu-id="ea7df-106">Azure Content Delivery Network (CDN) は、Azure または他の任意の場所でホストされている高帯域幅コンテンツを配信するためのグローバル ソリューションを開発者に提供します。</span><span class="sxs-lookup"><span data-stu-id="ea7df-106">The Azure Content Delivery Network (CDN) offers developers a global solution for delivering high-bandwidth content that is hosted in Azure or any other location.</span></span> <span data-ttu-id="ea7df-107">CDN を使用すると、Azure BLOB ストレージ、Web アプリケーション、仮想マシン、アプリケーション フォルダー、またはその他の HTTP/HTTPS の場所から読み込んだ一般公開されているオブジェクトをキャッシュすることができます。</span><span class="sxs-lookup"><span data-stu-id="ea7df-107">Using the CDN, you can cache publicly available objects loaded from Azure blob storage, a web application, virtual machine, application folder, or other HTTP/HTTPS location.</span></span> <span data-ttu-id="ea7df-108">CDN のキャッシュを戦略的な場所に配置することで、ユーザーへのコンテンツ配信に最大限の帯域幅を提供することができます。</span><span class="sxs-lookup"><span data-stu-id="ea7df-108">The CDN cache can be held at strategic locations to provide maximum bandwidth for delivering content to users.</span></span> <span data-ttu-id="ea7df-109">CDN は、通常、イメージ、スタイル シート、ドキュメント、ファイル、クライアント側スクリプトでは、HTML ページなどの静的コンテンツの配信に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ea7df-109">The CDN is typically used for delivering static content such as images, style sheets, documents, files, client-side scripts, and HTML pages.</span></span>

## <a name="management-package"></a><span data-ttu-id="ea7df-110">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="ea7df-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ea7df-111">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="ea7df-111">Install the npm module</span></span>

<span data-ttu-id="ea7df-112">Azure CDN の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="ea7df-112">Install the Azure CDN npm module</span></span>

```bash
npm install azure-arm-cdn
```

### <a name="example"></a><span data-ttu-id="ea7df-113">例</span><span class="sxs-lookup"><span data-stu-id="ea7df-113">Example</span></span>

<span data-ttu-id="ea7df-114">この例では、すべての CDN プロファイルを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ea7df-114">This example lists all of the CDN profiles.</span></span>

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

## <a name="samples"></a><span data-ttu-id="ea7df-115">サンプル</span><span class="sxs-lookup"><span data-stu-id="ea7df-115">Samples</span></span>

<span data-ttu-id="ea7df-116">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="ea7df-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
