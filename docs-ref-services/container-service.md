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
# <a name="microsoft-azure-sdk-for-nodejs---containerserviceclient"></a>Node.js 用 Microsoft Azure SDK - ContainerServiceClient
このプロジェクトには、Azure にアクセスするための Node.js パッケージが用意されています。 現時点では、以下がサポートされています。
- **Node.js バージョン 6.x.x 以上**

## <a name="features"></a>機能


## <a name="how-to-install"></a>インストール方法

```bash
npm install azure-arm-containerservice
```

## <a name="how-to-use"></a>使用方法

### <a name="authentication-client-creation-and-list-containerservices-as-an-example"></a>認証、クライアント作成、例として containerServices を一覧表示。

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

## <a name="related-projects"></a>関連プロジェクト

- [Microsoft Azure SDK for Node.js](https://github.com/Azure/azure-sdk-for-node)