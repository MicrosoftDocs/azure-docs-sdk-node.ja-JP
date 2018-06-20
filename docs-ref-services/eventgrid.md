---
title: Node.js 用 Azure Event Grid ライブラリ
description: Node.js 用 Azure Event Grid ライブラリのリファレンス
author: rloutlaw
ms.author: routlaw
manager: angerobe
ms.date: 05/03/2018
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: event-grid
ms.custom: devcenter
ms.openlocfilehash: 165845f0c94b4e6fd0f385f2262903e44845d09a
ms.sourcegitcommit: b4cf45cb23da56718b482cf7fc240c592e15206b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2018
ms.locfileid: "33849955"
---
# <a name="azure-event-grid-libraries-for-nodejs"></a><span data-ttu-id="9bb82-103">Node.js 用 Azure Event Grid ライブラリ</span><span class="sxs-lookup"><span data-stu-id="9bb82-103">Azure Event Grid libraries for Node.js</span></span>

<span data-ttu-id="9bb82-104">Azure Event Grid で簡単な HTTP ベースのイベント処理を使用して、Azure サービスやカスタム ソースのイベントをリッスンして対応するイベント ドリブン アプリケーションを構築します。</span><span class="sxs-lookup"><span data-stu-id="9bb82-104">Build event-driven applications that listen and react to events from Azure services and custom sources using simple HTTP-based event handling with Azure Event Grid.</span></span>

<span data-ttu-id="9bb82-105">Azure Event Grid の[詳細を確認](/azure/event-grid/overview)し、[Azure Blob Storage イベントのチュートリアル](/azure/storage/blobs/storage-blob-event-quickstart)を開始してください。</span><span class="sxs-lookup"><span data-stu-id="9bb82-105">[Learn more](/azure/event-grid/overview) about Azure Event Grid and get started with the [Azure Blob storage event tutorial](/azure/storage/blobs/storage-blob-event-quickstart).</span></span> 

## <a name="publish-sdk"></a><span data-ttu-id="9bb82-106">発行 SDK</span><span class="sxs-lookup"><span data-stu-id="9bb82-106">Publish SDK</span></span>

<span data-ttu-id="9bb82-107">Azure Event Grid 発行 SDK を使用して、イベントの作成、認証、トピックへの投稿を行います。</span><span class="sxs-lookup"><span data-stu-id="9bb82-107">Create events, authenticate, and post to topics using the Azure Event Grid publish SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="9bb82-108">インストール</span><span class="sxs-lookup"><span data-stu-id="9bb82-108">Installation</span></span>

<span data-ttu-id="9bb82-109">npm を使用して、モジュールをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="9bb82-109">Add the module to your project with npm:</span></span>

```bash
npm install azure-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="9bb82-110">コード例</span><span class="sxs-lookup"><span data-stu-id="9bb82-110">Example code</span></span>

<span data-ttu-id="9bb82-111">次のコード セグメントでは、モック イベントを Event Grid トピックに発行します。</span><span class="sxs-lookup"><span data-stu-id="9bb82-111">The following code segment publishes a mock event to a Event Grid topic.</span></span> <span data-ttu-id="9bb82-112">エンドポイントとトピックのアクセス キーは、Azure Portal または Azure CLI を使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="9bb82-112">You can retrieve the endpoint and topic access keys from the Azure Portal or through the Azure CLI:</span></span>

```azurecli-interactive
endpoint=$(az eventgrid topic show --name <topic_name> -g gridResourceGroup --query "endpoint" --output tsv)
key=$(az eventgrid topic key list --name <topic_name> -g gridResourceGroup --query "key1" --output tsv)
```

```javascript
var EventGridClient = require("azure-eventgrid");
var msRestAzure = require('ms-rest-azure');
var uuid = require('uuid').v4;

let topicCreds = new msRestAzure.TopicCredentials('your-topic-key');
let EGClient = new EventGridClient(topicCreds, 'your-subscription-id');
let topicHostName = 'your-topic-endpoint';
let events = [
   {
   id: uuid(),
   subject: 'TestSubject',
   dataVersion: '1.0',
   eventType: 'Microsoft.MockPublisher.TestEvent',
   data: {
        field1: 'value1',
        filed2: 'value2'
        }
    }
];
return EGClient.publishEvents(topicHostName, events).then((result) => {
   return Promise.resolve(console.log('Published events successfully.'));
 }).catch((err) => {
  console.log('An error ocurred');
  console.dir(err, {depth: null, colors: true});
});
```

<span data-ttu-id="9bb82-113">次のサンプルは、Azure Storage のイベントを処理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9bb82-113">This sample shows how to handle an event from Azure Storage:</span></span>

```javascript
var http = require('http');

module.exports = function (context, req) {
    context.log('JavaScript HTTP trigger function begun');
    var validationEventType = "Microsoft.EventGrid.SubscriptionValidationEvent";
    var storageBlobCreatedEvent = "Microsoft.Storage.BlobCreated";

    for (var events in req.body) {
        var body = req.body[events];
        // Deserialize the event data into the appropriate type based on event type  
        if (body.data && body.eventType == validationEventType) {
            context.log("Got SubscriptionValidation event data, validation code: " + body.data.validationCode + " topic: " + body.topic);

            // Do any additional validation (as required) and then return back the below response
            var code = body.data.validationCode;
            context.res = { status: 200, body: { "ValidationResponse": code } };
        }

        else if (body.data && body.eventType == storageBlobCreatedEvent) {
            var blobCreatedEventData = body.data;
            context.log("Relaying received blob created event payload:" + JSON.stringify(blobCreatedEventData));
        }
    }
    context.done();
};
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="9bb82-114">クライアント API を探す</span><span class="sxs-lookup"><span data-stu-id="9bb82-114">Explore the client APIs</span></span>](/javascript/api/overview/azure/eventgrid/client)

## <a name="management-sdk"></a><span data-ttu-id="9bb82-115">管理 SDK</span><span class="sxs-lookup"><span data-stu-id="9bb82-115">Management SDK</span></span>

<span data-ttu-id="9bb82-116">管理 SDK を使用して、Event Grid のインスタンス、トピック、サブスクリプションを作成、更新、削除します。</span><span class="sxs-lookup"><span data-stu-id="9bb82-116">Create, update, or delete Event Grid instances, topics, and subscriptions with the management SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="9bb82-117">インストール</span><span class="sxs-lookup"><span data-stu-id="9bb82-117">Installation</span></span>

```
npm install azure-arm-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="9bb82-118">コード例</span><span class="sxs-lookup"><span data-stu-id="9bb82-118">Example code</span></span>

<span data-ttu-id="9bb82-119">次のコードでは、Event Grid トピック `topic1` を作成し、新しく作成されたトピックに関連付けられたアクセス キーを返します。</span><span class="sxs-lookup"><span data-stu-id="9bb82-119">The following code creates an Event Grid topic `topic1` and returns the access keys associated with the newly created topic.</span></span>

```javascript
var msRestAzure = require('ms-rest-azure');
var EventGridManagementClient = require("azure-arm-eventgrid");

msRestAzure.interactiveLogin(function(err, credentials) {
    // Created the management client
    let EGMClient = new EventGridManagementClient(credentials, 'your-subscription-id');
    let topicResponse;
    // created an enventgrid topic
    return EGMClient.topics.createOrUpdate('resourceGroup', 'topic1', { location: 'westus' }).then((topicResponse) => {
        return Promise.resolve(console.log('Created topic ', topicResponse));
    }).then(() => {
        // listed the access keys
        return EGMClient.topics.listSharedAccessKeys('resourceGroup', 'topic1')}
)};
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="9bb82-120">Management API を探す</span><span class="sxs-lookup"><span data-stu-id="9bb82-120">Explore the management APIs</span></span>](/javascript/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a><span data-ttu-id="9bb82-121">詳細情報</span><span class="sxs-lookup"><span data-stu-id="9bb82-121">Learn more</span></span>

- [<span data-ttu-id="9bb82-122">Event Grid SDK を使用してイベントを受信する</span><span class="sxs-lookup"><span data-stu-id="9bb82-122">Receive events using the Event Grid SDK</span></span>](/azure/event-grid/receive-events)