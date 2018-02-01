---
title: "Node.js 用 Azure Storage モジュール"
description: "Node.js 用 Azure Storage モジュールのリファレンス"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: b94c6fbb50e656e0dcc542236afe791c7ddc9be4
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2018
---
# <a name="azure-storage-modules-for-nodejs"></a>Node.js 用 Azure Storage モジュール

Azure Storage クライアント モジュールは、次のようなときに使用します。

- [Azure Blob Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage) との間でオブジェクトとファイルの読み取りと書き込みを行う
- クラウドに接続されているアプリケーションの間で [Azure Queue Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues) を使ってメッセージを送受信する
- [Azure Table Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage) を使って大きな構造化データの読み取りと書き込みを行う

Node.js アプリから管理モジュールを使って、Azure ストレージ アカウントの作成、更新、管理のほか、アクセス キーの照会と再生成を行うことができます。

## <a name="client-package"></a>クライアント パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール

Azure Storage クライアントの npm モジュールをインストールします。

```bash
npm install azure-storage
```

### <a name="example"></a>例

この例では、ストレージ コンテナーを作成し、そこにローカル ファイル `data.txt` をアップロードします。

```javascript
const azure = require('azure-storage');
const blobService = azure.createBlobService(storageConnectionString);

const container = 'taskcontainer';
const task = 'taskblob';
const filename = 'data.txt';

blobService.createContainerIfNotExists(container, error => {
  if (error) return console.log(error);
  blobService.createBlockBlobFromLocalFile(
    container,
    task,
    filename,
    (error, result) => {
      if (error) return console.log(error);
      console.dir(result, { depth: null, colors: true });
    }
  );
});
```

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール 

Azure Storage 管理の npm モジュールをインストールします。

```bash
npm install azure-arm-storage
```

### <a name="example"></a>例

この例では、ストレージ アカウントをリストします。

```javascript
const msRestAzure = require('ms-rest-azure');
const storageManagementClient = require('azure-arm-storage');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new storageManagementClient(
      credentials,
      subscriptionId
    );
    return client.storageAccounts.list();
  })
  .then(accounts => console.dir(accounts, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>サンプル

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
