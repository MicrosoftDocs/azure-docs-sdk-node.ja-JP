---
title: Node.js 用 Azure モジュール
description: Node.js 用 Azure 管理/サービス モジュールの概要
author: rloutlaw
ms.author: routlaw
manager: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 165e1580e408b71b6147e51c41e22bc8fe7277a1
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="azure-modules-for-nodejs"></a><span data-ttu-id="56290-103">Node.js 用 Azure モジュール</span><span class="sxs-lookup"><span data-stu-id="56290-103">Azure modules for Node.js</span></span>

<span data-ttu-id="56290-104">Node.js アプリケーションから Node.js 用 Azure モジュールを使用して Azure リソースを管理し、サービスに接続します。</span><span class="sxs-lookup"><span data-stu-id="56290-104">Manage Azure resources and connect to services from your Node.js applications with the Azure modules for Node.js.</span></span> <span data-ttu-id="56290-105">このコードは、プロジェクト内で [npm モジュール](node-sdk-azure-install.md)として使用することができます。</span><span class="sxs-lookup"><span data-stu-id="56290-105">The code is available as [npm modules](node-sdk-azure-install.md) for use in your projects.</span></span> 

## <a name="manage-azure-resources"></a><span data-ttu-id="56290-106">Azure のリソースを管理する</span><span class="sxs-lookup"><span data-stu-id="56290-106">Manage Azure resources</span></span>

<span data-ttu-id="56290-107">アプリからリソースを作成、照会したり、独自の Azure オートメーション ツールを作成したりするには、管理モジュールを使用します。</span><span class="sxs-lookup"><span data-stu-id="56290-107">Use management modules to create and query resources from your apps or to build your own Azure automation tools.</span></span> 

<span data-ttu-id="56290-108">たとえば既存のネットワーク インターフェイスを使って Linux VM を作成するコードは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="56290-108">For example, to create a Linux VM using an existing network interface, you would write the following code:</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');

// read in service principal values from env variables
const clientId = process.env['CLIENT_ID'];
const domain = process.env['DOMAIN'];
const secret = process.env['APPLICATION_SECRET'];
const subscriptionId = process.env['AZURE_SUBSCRIPTION_ID'];

msRestAzure.loginWithServicePrincipalSecret(clientId, secret, domain, function (err, credentials, subscriptions) {
    if (err) return console.log(err);
    const computeClient = new ComputeManagementClient(credentials, subscriptionId);
    // customize the VM 
    const vmParameters = {
        location: "eastus",
        osProfile: {
            computerName: "newLinuxVM",
            adminUsername: adminUsername,
            adminPassword: adminPassword
        },
        linuxConfiguration: {
            ssh: {
                publicKeys: [mySshKey]
            }
        },
        hardwareProfile: {
            vmSize: 'Basic_A1'
        },
        networkProfile: {
            networkInterfaces: [
                {
                    id: myNetworkInterfaceId,
                    primary: true
                }
            ]
        },
        storageProfile: {
            imageReference: {
                publisher: 'Canonical',
                offer: 'UbuntuServer',
                sku: '16.04-LTS',
                version: 'latest'
            },
        }
    };
 
    // create the VM
    computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, function (err, data) {
        if (err) return console.log(err);
    });

});
```

<span data-ttu-id="56290-109">モジュールの全一覧については[インストール手順](node-sdk-azure-install.md)を参照してください。また、自分の Azure サブスクリプションに対して認証を設定したり、リソースの作成や更新を行うサンプル コードを実行したりする方法については、[概要の記事](node-sdk-azure-get-started.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56290-109">Review the [install instructions](node-sdk-azure-install.md) for a full list of the modules and the [get started article](node-sdk-azure-get-started.md) to set up authentication and run sample code to create and update resources against your own Azure subscription.</span></span> 

## <a name="connect-to-azure-services"></a><span data-ttu-id="56290-110">Azure サービスへの接続</span><span class="sxs-lookup"><span data-stu-id="56290-110">Connect to Azure services</span></span>

<span data-ttu-id="56290-111">Azure モジュールを使用して Azure 内のリソースを作成したり管理したりするだけでなく、パッケージを使用して、アプリで Azure クラウド サービスに接続して利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="56290-111">In addition to using the Azure modules to create and manage resources within Azure, you can also use packages to connect and use Azure cloud services in your apps.</span></span> <span data-ttu-id="56290-112">たとえば、SQL Database のテーブルを更新したり、Azure Storage にファイルをアップロードしたりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="56290-112">For example, you might update a table SQL Database or upload files to Azure Storage.</span></span> <span data-ttu-id="56290-113">特定のサービスに必要なパッケージを[全一覧](node-sdk-azure-install.md)からお選びください。また、それらのモジュールをアプリ内で使用する方法について紹介したチュートリアルやサンプル コードは、[Node.js デベロッパー センター](https://azure.microsoft.com/develop/nodejs/)から入手できます。</span><span class="sxs-lookup"><span data-stu-id="56290-113">Select the package you need for a particular service from the [complete list](node-sdk-azure-install.md) and visit the [Node.js developer center](https://azure.microsoft.com/develop/nodejs/) for tutorials and sample code to learn how to use the modules in your apps.</span></span>

<span data-ttu-id="56290-114">たとえば、Azure ストレージ コンテナーに格納されているすべての BLOB のコンテンツを印刷するには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="56290-114">For example, to print out the contents of every blob in an Azure storage container:</span></span>

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a><span data-ttu-id="56290-115">サンプル コードとリファレンス</span><span class="sxs-lookup"><span data-stu-id="56290-115">Sample code and reference</span></span>

<span data-ttu-id="56290-116">以下のサンプルには、Azure 管理モジュールを使った一般的なタスクが紹介されており、また、独自のアプリですぐに利用できるコードも用意されています。</span><span class="sxs-lookup"><span data-stu-id="56290-116">The following samples cover common tasks with the Azure management modules and have code ready to use in your own apps:</span></span>

- [<span data-ttu-id="56290-117">仮想マシン</span><span class="sxs-lookup"><span data-stu-id="56290-117">Virtual machines</span></span>](node-samples-services-compute.md)
- [<span data-ttu-id="56290-118">Web アプリ</span><span class="sxs-lookup"><span data-stu-id="56290-118">Web apps</span></span>](node-samples-services-web-and-mobile.md)
- [<span data-ttu-id="56290-119">SQL Database</span><span class="sxs-lookup"><span data-stu-id="56290-119">SQL Database</span></span>](node-samples-services-database.md)
   
<span data-ttu-id="56290-120">サービス モジュールと管理モジュールの全モジュールについて[リファレンス](https://docs.microsoft.com/javascript/api)が公開されています。</span><span class="sxs-lookup"><span data-stu-id="56290-120">A [reference](https://docs.microsoft.com/javascript/api) is available for all modules in both the service and management modules.</span></span> <span data-ttu-id="56290-121">新機能、重大な変更、以前のバージョンからの移行手順については、[リリース ノート](https://github.com/Azure/azure-sdk-for-node/releases)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56290-121">New features, breaking changes, and migration instructions from previous versions are available in the [release notes](https://github.com/Azure/azure-sdk-for-node/releases).</span></span>