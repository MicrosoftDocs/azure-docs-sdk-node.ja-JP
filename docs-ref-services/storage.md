---
title: "Node.js 用 Azure Storage モジュール"
description: "Node.js 用 Azure Storage モジュールのリファレンス"
keywords: "Azure, Node, SDK, API, ストレージ, nodejs, javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: 61d3f3bb49d10e63a353c474067a155223bb6c76
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-storage-modules-for-nodejs"></a><span data-ttu-id="1c45d-104">Node.js 用 Azure Storage モジュール</span><span class="sxs-lookup"><span data-stu-id="1c45d-104">Azure Storage modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="1c45d-105">概要</span><span class="sxs-lookup"><span data-stu-id="1c45d-105">Overview</span></span>

<span data-ttu-id="1c45d-106">Azure Storage クライアント モジュールは、次のようなときに使用します。</span><span class="sxs-lookup"><span data-stu-id="1c45d-106">Use the Azure Storage client module to:</span></span>

- <span data-ttu-id="1c45d-107">[Azure Blob Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage) との間でオブジェクトとファイルの読み取りと書き込みを行う</span><span class="sxs-lookup"><span data-stu-id="1c45d-107">Read and write objects and files from [Azure Blob storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span></span>
- <span data-ttu-id="1c45d-108">クラウドに接続されているアプリケーション間で [Azure Queue Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues) を使ってメッセージを送受信する</span><span class="sxs-lookup"><span data-stu-id="1c45d-108">Send and receive messages between cloud-connected applications with [Azure Queue storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span></span>
- <span data-ttu-id="1c45d-109">[Azure Table Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage) を使って大きな構造化データの読み取りと書き込みを行う</span><span class="sxs-lookup"><span data-stu-id="1c45d-109">Read and write large structured data with [Azure Table storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span></span>

<span data-ttu-id="1c45d-110">Node.js アプリから管理モジュールを使って、Azure ストレージ アカウントの作成、更新、管理のほか、アクセス キーの照会と再生成を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1c45d-110">Create, update, and manage Azure Storage accounts and query and regenerate access keys from your Node.js apps with the management modules.</span></span>

## <a name="client-package"></a><span data-ttu-id="1c45d-111">クライアント パッケージ</span><span class="sxs-lookup"><span data-stu-id="1c45d-111">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="1c45d-112">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="1c45d-112">Install the npm module</span></span>

<span data-ttu-id="1c45d-113">Azure Storage クライアントの npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="1c45d-113">Install the Azure storage client npm module</span></span>

```bash
npm install azure-storage
```

### <a name="example"></a><span data-ttu-id="1c45d-114">例</span><span class="sxs-lookup"><span data-stu-id="1c45d-114">Example</span></span>

<span data-ttu-id="1c45d-115">この例では、ストレージ コンテナーを作成し、そこにローカル ファイル `data.txt` をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="1c45d-115">This example create a storage container and uploads a local file `data.txt` to it.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="1c45d-116">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="1c45d-116">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="1c45d-117">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="1c45d-117">Install the npm module</span></span> 

<span data-ttu-id="1c45d-118">Azure Storage 管理の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="1c45d-118">Install the Azure storage management npm module</span></span>

```bash
npm install azure-arm-storage
```

### <a name="example"></a><span data-ttu-id="1c45d-119">例</span><span class="sxs-lookup"><span data-stu-id="1c45d-119">Example</span></span>

<span data-ttu-id="1c45d-120">この例では、ストレージ アカウントをリストします。</span><span class="sxs-lookup"><span data-stu-id="1c45d-120">This example list the storage accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="1c45d-121">サンプル</span><span class="sxs-lookup"><span data-stu-id="1c45d-121">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

<span data-ttu-id="1c45d-122">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="1c45d-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
