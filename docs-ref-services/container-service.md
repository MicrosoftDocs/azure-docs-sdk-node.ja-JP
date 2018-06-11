---
title: Node.js 用 Azure Container Service モジュール
description: Node.js 用 Azure Container Service モジュールのリファレンス
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Service
ms.openlocfilehash: 2d0aac2f7f6cc70ab3e40f7b3ccee6f64a011b55
ms.sourcegitcommit: 702a716434eb42f55d8782feb62ae2c6d8147aa9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34689828"
---
# <a name="microsoft-azure-sdk-for-nodejs---containerserviceclient"></a><span data-ttu-id="d962c-103">Node.js 用 Microsoft Azure SDK - ContainerServiceClient</span><span class="sxs-lookup"><span data-stu-id="d962c-103">Microsoft Azure SDK for Node.js - ContainerServiceClient</span></span>
<span data-ttu-id="d962c-104">このプロジェクトには、Azure にアクセスするための Node.js パッケージが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d962c-104">This project provides a Node.js package for accessing Azure.</span></span> <span data-ttu-id="d962c-105">現時点では、以下がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d962c-105">Right now it supports:</span></span>
- <span data-ttu-id="d962c-106">**Node.js バージョン 6.x.x 以上**</span><span class="sxs-lookup"><span data-stu-id="d962c-106">**Node.js version 6.x.x or higher**</span></span>

## <a name="features"></a><span data-ttu-id="d962c-107">機能</span><span class="sxs-lookup"><span data-stu-id="d962c-107">Features</span></span>


## <a name="how-to-install"></a><span data-ttu-id="d962c-108">インストール方法</span><span class="sxs-lookup"><span data-stu-id="d962c-108">How to Install</span></span>

```bash
npm install azure-arm-containerservice
```

## <a name="how-to-use"></a><span data-ttu-id="d962c-109">使用方法</span><span class="sxs-lookup"><span data-stu-id="d962c-109">How to use</span></span>

### <a name="authentication-client-creation-and-list-containerservices-as-an-example"></a><span data-ttu-id="d962c-110">認証、クライアント作成、例として containerServices を一覧表示。</span><span class="sxs-lookup"><span data-stu-id="d962c-110">Authentication, client creation and list containerServices as an example.</span></span>

```javascript
const msRestAzure = require("ms-rest-azure");
const ContainerServiceClient = require("azure-arm-containerservice");
msRestAzure.interactiveLogin().then((creds) => {
    const subscriptionId = "<Subscription_Id>";
    const client = new ContainerServiceClient(creds, subscriptionId);
    return client.containerServices.list().then((result) => {
      console.log("The result is:");
      console.log(result);
    });
}).catch((err) => {
  console.log('An error ocurred:');
  console.dir(err, {depth: null, colors: true});
});
```

## <a name="related-projects"></a><span data-ttu-id="d962c-111">関連プロジェクト</span><span class="sxs-lookup"><span data-stu-id="d962c-111">Related projects</span></span>

- [<span data-ttu-id="d962c-112">Microsoft Azure SDK for Node.js</span><span class="sxs-lookup"><span data-stu-id="d962c-112">Microsoft Azure SDK for Node.js</span></span>](https://github.com/Azure/azure-sdk-for-node)