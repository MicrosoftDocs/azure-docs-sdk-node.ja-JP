---
title: Node.js 用 Azure DNS モジュール
description: Node.js 用 Azure DNS モジュールのリファレンス
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 93eec1890fc15d19c0545086a53b751d0886988a
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51494866"
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="b7593-103">Node.js 用 Azure DNS モジュール</span><span class="sxs-lookup"><span data-stu-id="b7593-103">Azure DNS modules for Node.js</span></span>

<span data-ttu-id="b7593-104">Azure DNS を使用して、お客様のドメイン ネーム システム (DNS) を Azure でホストしましょう。</span><span class="sxs-lookup"><span data-stu-id="b7593-104">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="b7593-105">他の Azure サービスと同じ資格情報、支払い方法、サポート契約で DNS レコードを管理します。</span><span class="sxs-lookup"><span data-stu-id="b7593-105">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="b7593-106">Azure ベースのサービスと対応する DNS 更新とをシームレスに統合し、エンドツーエンドのデプロイ プロセスを効率化できます。</span><span class="sxs-lookup"><span data-stu-id="b7593-106">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="b7593-107">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="b7593-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b7593-108">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="b7593-108">Install the npm module</span></span>

<span data-ttu-id="b7593-109">Azure DNS の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="b7593-109">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="b7593-110">例</span><span class="sxs-lookup"><span data-stu-id="b7593-110">Example</span></span>

<span data-ttu-id="b7593-111">この例では、DNS 管理ゾーンを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="b7593-111">This example lists the DNS Management zones.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b7593-112">サンプル</span><span class="sxs-lookup"><span data-stu-id="b7593-112">Samples</span></span>

<span data-ttu-id="b7593-113">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="b7593-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
