---
title: Node.js 用 Azure Relay モジュール
description: Node.js 用 Azure Relay モジュールのリファレンス
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: e0bb24ac422d71bd8c957e94cceffd57bf121e48
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2018
ms.locfileid: "51062071"
---
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="03988-103">Node.js 用 Azure Relay モジュール</span><span class="sxs-lookup"><span data-stu-id="03988-103">Azure Relay modules for Node.js</span></span>

<span data-ttu-id="03988-104">Azure Relay サービスでは、ファイアウォール接続の開放や企業ネットワーク インフラストラクチャの煩わしい変更を必要とせずに、企業のエンタープライズ ネットワーク内にあるサービスをパブリック クラウドに安全に公開できるハイブリッド アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="03988-104">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="03988-105">Relay では、多様なトランスポート プロトコルと Web サービス標準がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="03988-105">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="03988-106">Azure Relay の詳細については、[こちら](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="03988-106">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="03988-107">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="03988-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="03988-108">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="03988-108">Install the npm module</span></span>

<span data-ttu-id="03988-109">Azure Relay の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="03988-109">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="03988-110">例</span><span class="sxs-lookup"><span data-stu-id="03988-110">Example</span></span>

<span data-ttu-id="03988-111">この例では、Relay クライアントの名前空間をリストします。</span><span class="sxs-lookup"><span data-stu-id="03988-111">This example lists the namespaces for a Relay client.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RelayManagement = require('azure-arm-relay');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RelayManagement(credentials, subscriptionId);
    return client.namespaces.list();
  })
  .then(namespaces => {
    console.dir(namespaces, { depth: null, colors: true });
  })
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="03988-112">サンプル</span><span class="sxs-lookup"><span data-stu-id="03988-112">Samples</span></span>

<span data-ttu-id="03988-113">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="03988-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
