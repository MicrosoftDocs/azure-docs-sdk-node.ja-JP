---
title: Node.js 用 Azure モジュールの概要
description: Node.js 用の Azure モジュールを使用した認証およびリソース管理の概要
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: conceptual
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 73f115373c33423b7ad8895e73f5a2170b753f8f
ms.sourcegitcommit: 8c9462a8538ea3d7d3fbb27454d26755abbad001
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57327373"
---
# <a name="get-started-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="3928b-103">Node.js 用 Azure モジュールの概要</span><span class="sxs-lookup"><span data-stu-id="3928b-103">Get started with the Azure modules for Node.js</span></span>

<span data-ttu-id="3928b-104">このガイドでは、Azure Node.js モジュールのインストール方法や、サービス プリンシパルを使って Azure に対して認証を行う方法のほか、Azure サブスクリプションにリソースを作成したり Azure クラウド サービスに接続したりするサンプル コードの実行方法について、わかりやすく説明しています。</span><span class="sxs-lookup"><span data-stu-id="3928b-104">This guide walks you through installing Azure Node.js modules, authenticating to Azure with a service principal, and running sample code that creates resources in your Azure subscription and connects to Azure cloud services.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3928b-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="3928b-105">Prerequisites</span></span>

- <span data-ttu-id="3928b-106">Azure アカウント。</span><span class="sxs-lookup"><span data-stu-id="3928b-106">An Azure account.</span></span> <span data-ttu-id="3928b-107">所有していない場合は、[無料試用版を入手](https://azure.microsoft.com/free/)してください。</span><span class="sxs-lookup"><span data-stu-id="3928b-107">If you don't have one , [get a free trial](https://azure.microsoft.com/free/)</span></span>
- [<span data-ttu-id="3928b-108">Node.js</span><span class="sxs-lookup"><span data-stu-id="3928b-108">Node.js</span></span>](https://nodejs.org)
- <span data-ttu-id="3928b-109">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) または [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2)。</span><span class="sxs-lookup"><span data-stu-id="3928b-109">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) or [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

[!INCLUDE [azure-cloud-shell](../docs-ref-conceptual/includes/cloud-shell-try-it.md)]

## <a name="prepare-your-environment"></a><span data-ttu-id="3928b-110">環境を準備する</span><span class="sxs-lookup"><span data-stu-id="3928b-110">Prepare your environment</span></span>

<span data-ttu-id="3928b-111">空のディレクトリに新しいプロジェクトを作成し、次の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="3928b-111">Create a new project in an empty directory and install the following npm modules:</span></span>

```bash
cd azure-node-quickstart
npm init -y
npm install --save azure ms-rest-azure azure-arm-compute azure-arm-network azure-storage azure-arm-storage
```

## <a name="set-up-authentication"></a><span data-ttu-id="3928b-112">認証の設定</span><span class="sxs-lookup"><span data-stu-id="3928b-112">Set up authentication</span></span>

<span data-ttu-id="3928b-113">このガイドのサンプル コードを実行する Node.js アプリケーションには、Azure サブスクリプションの読み取りと作成のアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="3928b-113">Your Node.js applications need read and create permissions in your Azure subscription to run the sample code in this guide.</span></span> <span data-ttu-id="3928b-114">サービス プリンシパルを作成し、その資格情報で動作するようにアプリケーションを構成してください。</span><span class="sxs-lookup"><span data-stu-id="3928b-114">Create a service principal and configure your application to run with its credentials.</span></span> <span data-ttu-id="3928b-115">サービス プリンシパルは、自分の ID に関連付けられた非対話型のアカウントです。アプリの実行に必要な権限だけを付与することができます。</span><span class="sxs-lookup"><span data-stu-id="3928b-115">Service principals are a non-interactive account associated with your identity to which you grant only the privileges your app needs to run.</span></span>

<span data-ttu-id="3928b-116">[Azure CLI 2.0 を使ってサービス プリンシパルを作成](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli)し、その出力をキャプチャしてください。</span><span class="sxs-lookup"><span data-stu-id="3928b-116">[Create a service principal using the Azure CLI 2.0](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli) and capture the output.</span></span> <span data-ttu-id="3928b-117">password 引数には、`MY_SECURE_PASSWORD` ではなく、[セキュリティで保護されたパスワード](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy)を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3928b-117">You'll need to provide a [secure password](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy) in the password argument instead of `MY_SECURE_PASSWORD`.</span></span>

```azurecli-interactive
az ad sp create-for-rbac --name AzureNodeTest --password MY_SECURE_PASSWORD
```

```json
{
  "appId": "a487e0c1-82af-47d9-9a0b-af184eb87646d",
  "displayName": "AzureNodeTest",
  "name": "http://AzureNodeTest",
  "password": password,
  "tenant": ""
}
```

<span data-ttu-id="3928b-118">*appId*、*password*、*tenant* の値を環境変数としてエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="3928b-118">Export the values for *appId*, *password* and *tenant* as environment variables:</span></span>

```bash
export AZURE_ID a487e0c1-82af-47d9-9a0b-af184eb87646d
export AZURE_PASS password
export AZURE_TENANT XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

<span data-ttu-id="3928b-119">[az account show](https://docs.microsoft.com/cli/azure/account#show) でサブスクリプションの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="3928b-119">Get the ID for your subscription with [az account show](https://docs.microsoft.com/cli/azure/account#show)</span></span>

```azurecli-interactive
az account show
```

```json
{
   "environmentName": "AzureCloud",
   "id": "306943934-0323-4ae4d-a42b-f6613d1664ac",
   "isDefault": true
}
```

<span data-ttu-id="3928b-120">サブスクリプション ID を環境変数としてエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="3928b-120">Export the subscription ID as an environment variable</span></span>

```bash
export AZURE_SUB 306943934-0323-4ae4d-a42b-f6613d1664ac
```

## <a name="create-a-linux-virtual-machine"></a><span data-ttu-id="3928b-121">Linux 仮想マシンの作成</span><span class="sxs-lookup"><span data-stu-id="3928b-121">Create a Linux virtual machine</span></span>

<span data-ttu-id="3928b-122">次のコードで現在のディレクトリに新しいファイル *createVM.js* を作成します。</span><span class="sxs-lookup"><span data-stu-id="3928b-122">Create a new file *createVM.js* in the current directory with the following code.</span></span> <span data-ttu-id="3928b-123">`adminPass` の値は、適切なパスワードに置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="3928b-123">Update the value of `adminPass` with a good password.</span></span>

```javascript
'use strict';

const MsRest = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');
const NetworkManagementClient = require('azure-arm-network');

MsRest.loginWithServicePrincipalSecret(
    process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {

        let adminPass = YOUR_VALUE_HERE;
        const networkClient = new NetworkManagementClient(credentials, process.env.AZURE_SUB);
        const computeClient = new ComputeManagementClient(credentials, process.env.AZURE_SUB);

        let nicParameters = {
            location: "eastus",
            ipConfigurations: [
                {
                    name: "vmnetinterface",
                    privateIPAllocationMethod: 'Dynamic',
                }
            ]
        };

        const vnetParameters = {
            location: "eastus",
            addressSpace: {
                addressPrefixes: ['10.0.0.0/16']
            },
            dhcpOptions: {
                dnsServers: ['10.1.1.1', '10.1.2.4']
            },
            subnets: [{ name: "mynodesubnet", addressPrefix: '10.0.0.0/24' }],
        };

        let vmParameters = {
            location: "eastus",
            osProfile: {
                computerName: "newLinuxVM",
                adminUsername: "testadmin",
                adminPassword: admin_password
            },
            hardwareProfile: {
                vmSize: 'Basic_A1'
            },
            networkProfile: {
                networkInterfaces: [
                    {
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

        let publicIPParameters = {
            location: "eastus",
            publicIPAllocationMethod: 'Dynamic'
        };

        networkClient.virtualNetworks.createOrUpdate("myResourceGroup", "mynodevnet", vnetParameters)
            .then(function (vnetwork) {
                networkClient.subnets.get("myResourceGroup", "mynodevnet", "mynodesubnet")
                    .then(function (subnetInfo) {
                        nicParameters.ipConfigurations[0].subnet = subnetInfo;
                        networkClient.publicIPAddresses.createOrUpdate("myResourceGroup", "myLinuxPublicIP", publicIPParameters)
                            .then(function (publicIP) {
                                nicParameters.ipConfigurations[0].publicIPAddress = publicIP;
                                networkClient.networkInterfaces.createOrUpdate("myResourceGroup", "vmnetinterface", nicParameters)
                                    .then(function (vmNetworkInterface) {
                                        vmParameters.networkProfile.networkInterfaces[0].id = vmNetworkInterface.id;
                                        computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, (err, data) => {
                                            if (err) return console.log(err);
                                            console.log("Created new Linux VM");
                                        });
                                    });
                            });
                    });
            });
    });
```

<span data-ttu-id="3928b-124">コマンド ラインでコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="3928b-124">Run the code from the command line:</span></span>

```bash
node createVM.js
```

<span data-ttu-id="3928b-125">このコードの実行後、新しい仮想マシンの IP を取得し、コードの `adminPass` の値を使って SSH でログインします。</span><span class="sxs-lookup"><span data-stu-id="3928b-125">Once the code completes, get the IP of your new virtual machine and log in with SSH using the value for `adminPass` from your code.</span></span>

```azurecli-interactive
az vm list-ip-addresses --name newLinuxVM
```

```bash
ssh testadmin@*vm_ip_address*
```

## <a name="write-a-blob-to-azure-storage"></a><span data-ttu-id="3928b-126">Azure Storage への BLOB の書き込み</span><span class="sxs-lookup"><span data-stu-id="3928b-126">Write a blob to Azure Storage</span></span>

<span data-ttu-id="3928b-127">次のコードで現在のディレクトリに新しいファイル *uploadFile.js* を作成します。</span><span class="sxs-lookup"><span data-stu-id="3928b-127">Create a new file *uploadFile.js* in the current directory with the following code.</span></span>

```javascript
'use strict'

const MsRest = require('ms-rest-azure');
const storage = require('azure-storage');
const storageManagementClient = require('azure-arm-storage');

MsRest.loginWithServicePrincipalSecret(process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {
    const client = new storageManagementClient(credentials, process.env.AZURE_SUB);

    const createParameters = {
        location: 'eastus',
        sku: {
            name: 'Standard_LRS'
        },
        kind: 'BlobStorage',
        accessTier: 'Hot'
    };

    const blobAccountName = "nodedemo" + Math.random().toString(10).substr(4, 7);

    client.storageAccounts.create("myResourceGroup", blobAccountName, createParameters, (err, result, httpRequest, response) => {
        if (err) console.log(err);

        // get a connection string for the account
        client.storageAccounts.listKeys("myResourceGroup", blobAccountName, (err, result) => {
            if (err) console.log(err);

            // get a storage key and use it to connect to the azure-storage module
            const blobSvc = storage.createBlobService(blobAccountName, result.keys[0].value);
            blobSvc.createContainerIfNotExists('mycontainer', { publicAccessLevel: 'blob' }, function (error, result, response) {
                if (!error) {
                    blobSvc.createBlockBlobFromText('mycontainer', 'myblob', 'Hello Azure!', function (error, result, response) {
                        if (!error) {
                            console.log("File uploaded to " + "https://" + blobAccountName + ".blob.core.windows.net/mycontainer/myblob");
                        }
                    });
                }
            });

        });
    });
});
```

<span data-ttu-id="3928b-128">コマンドを実行したら出力結果から URL をコピーし、Web ブラウザーに貼り付けて Azure Storage 内のファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="3928b-128">Run the command and then copy and paste the URL from the output into your web browser to view the file in Azure Storage:</span></span>

```bash
node uploadFile.js
```

## <a name="clean-up-resources"></a><span data-ttu-id="3928b-129">リソースのクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="3928b-129">Clean up resources</span></span>

<span data-ttu-id="3928b-130">リソース グループを削除して、このガイドで作成したリソースを削除してください。</span><span class="sxs-lookup"><span data-stu-id="3928b-130">Delete the resource group to remove the resources created in this guide.</span></span>

```azurecli-interactive
az group delete --name myResourceGroup
```

## <a name="next-steps"></a><span data-ttu-id="3928b-131">次の手順</span><span class="sxs-lookup"><span data-stu-id="3928b-131">Next steps</span></span>

<span data-ttu-id="3928b-132">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="3928b-132">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>

## <a name="reference"></a><span data-ttu-id="3928b-133">リファレンス</span><span class="sxs-lookup"><span data-stu-id="3928b-133">Reference</span></span> 

<span data-ttu-id="3928b-134">すべてのパッケージには、[リファレンス](/javascript/api/overview/azure/)が提供されています。</span><span class="sxs-lookup"><span data-stu-id="3928b-134">A [reference](/javascript/api/overview/azure/) is available for all packages.</span></span>

## <a name="get-help-and-give-feedback"></a><span data-ttu-id="3928b-135">質問とフィードバック</span><span class="sxs-lookup"><span data-stu-id="3928b-135">Get help and give feedback</span></span>

<span data-ttu-id="3928b-136">ご質問は、[Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js) のコミュニティに投稿してください。</span><span class="sxs-lookup"><span data-stu-id="3928b-136">Post questions to the community on [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js).</span></span> <span data-ttu-id="3928b-137">Node.js 用 Azure モジュールに関する未解決の問題やバグは、[プロジェクト GitHub](https://github.com/Azure/azure-sdk-for-node) にご報告ください。</span><span class="sxs-lookup"><span data-stu-id="3928b-137">Report bugs and open issues against the Azure modules for Node.js on the [project GitHub](https://github.com/Azure/azure-sdk-for-node).</span></span>

