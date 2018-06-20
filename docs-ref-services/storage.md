---
title: Node.js 用 Azure Storage モジュール
description: Node.js 用 Azure Storage モジュールのリファレンス
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
ms.locfileid: "28116900"
---
# <a name="azure-storage-modules-for-nodejs"></a><span data-ttu-id="5e18d-103">Node.js 用 Azure Storage モジュール</span><span class="sxs-lookup"><span data-stu-id="5e18d-103">Azure Storage modules for Node.js</span></span>

<span data-ttu-id="5e18d-104">Azure Storage クライアント モジュールは、次のようなときに使用します。</span><span class="sxs-lookup"><span data-stu-id="5e18d-104">Use the Azure Storage client module to:</span></span>

- <span data-ttu-id="5e18d-105">[Azure Blob Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage) との間でオブジェクトとファイルの読み取りと書き込みを行う</span><span class="sxs-lookup"><span data-stu-id="5e18d-105">Read and write objects and files from [Azure Blob storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span></span>
- <span data-ttu-id="5e18d-106">クラウドに接続されているアプリケーションの間で [Azure Queue Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues) を使ってメッセージを送受信する</span><span class="sxs-lookup"><span data-stu-id="5e18d-106">Send and receive messages between cloud-connected applications with [Azure Queue storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span></span>
- <span data-ttu-id="5e18d-107">[Azure Table Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage) を使って大きな構造化データの読み取りと書き込みを行う</span><span class="sxs-lookup"><span data-stu-id="5e18d-107">Read and write large structured data with [Azure Table storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span></span>

<span data-ttu-id="5e18d-108">Node.js アプリから管理モジュールを使って、Azure ストレージ アカウントの作成、更新、管理のほか、アクセス キーの照会と再生成を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="5e18d-108">Create, update, and manage Azure Storage accounts and query and regenerate access keys from your Node.js apps with the management modules.</span></span>

## <a name="client-package"></a><span data-ttu-id="5e18d-109">クライアント パッケージ</span><span class="sxs-lookup"><span data-stu-id="5e18d-109">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="5e18d-110">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="5e18d-110">Install the npm module</span></span>

<span data-ttu-id="5e18d-111">Azure Storage クライアントの npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="5e18d-111">Install the Azure storage client npm module</span></span>

```bash
npm install azure-storage
```

### <a name="example"></a><span data-ttu-id="5e18d-112">例</span><span class="sxs-lookup"><span data-stu-id="5e18d-112">Example</span></span>

<span data-ttu-id="5e18d-113">この例では、ストレージ コンテナーを作成し、そこにローカル ファイル `data.txt` をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="5e18d-113">This example create a storage container and uploads a local file `data.txt` to it.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="5e18d-114">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="5e18d-114">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="5e18d-115">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="5e18d-115">Install the npm module</span></span> 

<span data-ttu-id="5e18d-116">Azure Storage 管理の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="5e18d-116">Install the Azure storage management npm module</span></span>

```bash
npm install azure-arm-storage
```

### <a name="example"></a><span data-ttu-id="5e18d-117">例</span><span class="sxs-lookup"><span data-stu-id="5e18d-117">Example</span></span>

<span data-ttu-id="5e18d-118">この例では、ストレージ アカウントをリストします。</span><span class="sxs-lookup"><span data-stu-id="5e18d-118">This example list the storage accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="5e18d-119">サンプル</span><span class="sxs-lookup"><span data-stu-id="5e18d-119">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

<span data-ttu-id="5e18d-120">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="5e18d-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
