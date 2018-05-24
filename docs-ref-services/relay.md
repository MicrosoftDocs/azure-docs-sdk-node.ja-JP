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
ms.openlocfilehash: 1f9b4263b8ffae78fcf9f35b8ef0160095059693
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="8b7aa-103">Node.js 用 Azure Relay モジュール</span><span class="sxs-lookup"><span data-stu-id="8b7aa-103">Azure Relay modules for Node.js</span></span>

<span data-ttu-id="8b7aa-104">Azure Relay サービスでは、ファイアウォール接続の開放や企業ネットワーク インフラストラクチャの煩わしい変更を必要とせずに、企業のエンタープライズ ネットワーク内にあるサービスをパブリック クラウドに安全に公開できるハイブリッド アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="8b7aa-104">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="8b7aa-105">Relay では、多様なトランスポート プロトコルと Web サービス標準がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8b7aa-105">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="8b7aa-106">Azure Relay の詳細については、[こちら](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8b7aa-106">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="8b7aa-107">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="8b7aa-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="8b7aa-108">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="8b7aa-108">Install the npm module</span></span>

<span data-ttu-id="8b7aa-109">Azure Relay の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="8b7aa-109">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="8b7aa-110">例</span><span class="sxs-lookup"><span data-stu-id="8b7aa-110">Example</span></span>

<span data-ttu-id="8b7aa-111">この例では、Relay クライアントの名前空間をリストします。</span><span class="sxs-lookup"><span data-stu-id="8b7aa-111">This example lists the namespaces for a Relay client.</span></span>

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

## <a name="samples"></a><span data-ttu-id="8b7aa-112">サンプル</span><span class="sxs-lookup"><span data-stu-id="8b7aa-112">Samples</span></span>

<span data-ttu-id="8b7aa-113">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="8b7aa-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
