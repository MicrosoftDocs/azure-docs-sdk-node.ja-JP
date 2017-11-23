---
title: "Node.js 用 Azure DNS モジュール"
description: "Node.js 用 Azure DNS モジュールのリファレンス"
keywords: Azure,SDK,API,DNS, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 679c2d494b99244961f2fee61b0813c81eb8a8de
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="2c816-104">Node.js 用 Azure DNS モジュール</span><span class="sxs-lookup"><span data-stu-id="2c816-104">Azure DNS modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2c816-105">概要</span><span class="sxs-lookup"><span data-stu-id="2c816-105">Overview</span></span>

<span data-ttu-id="2c816-106">Azure DNS を使用して、お客様のドメイン ネーム システム (DNS) を Azure でホストしましょう。</span><span class="sxs-lookup"><span data-stu-id="2c816-106">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="2c816-107">他の Azure サービスと同じ資格情報、支払い方法、サポート契約で DNS レコードを管理します。</span><span class="sxs-lookup"><span data-stu-id="2c816-107">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="2c816-108">Azure ベースのサービスと対応する DNS 更新とをシームレスに統合し、エンドツーエンドのデプロイ プロセスを効率化できます。</span><span class="sxs-lookup"><span data-stu-id="2c816-108">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="2c816-109">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="2c816-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2c816-110">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="2c816-110">Install the npm module</span></span>

<span data-ttu-id="2c816-111">Azure DNS の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="2c816-111">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="2c816-112">例</span><span class="sxs-lookup"><span data-stu-id="2c816-112">Example</span></span>

<span data-ttu-id="2c816-113">この例では、DNS 管理ゾーンを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="2c816-113">This example lists the DNS Management zones.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const DNSManagement = require('azure-arm-dns');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DNSManagement(credentials, subscriptionId);
    return client.zones.list();
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="2c816-114">サンプル</span><span class="sxs-lookup"><span data-stu-id="2c816-114">Samples</span></span>

<span data-ttu-id="2c816-115">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="2c816-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
