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
ms.locfileid: "34220534"
---
# <a name="azure-modules-for-nodejs"></a>Node.js 用 Azure モジュール

Node.js アプリケーションから Node.js 用 Azure モジュールを使用して Azure リソースを管理し、サービスに接続します。 このコードは、プロジェクト内で [npm モジュール](node-sdk-azure-install.md)として使用することができます。 

## <a name="manage-azure-resources"></a>Azure のリソースを管理する

アプリからリソースを作成、照会したり、独自の Azure オートメーション ツールを作成したりするには、管理モジュールを使用します。 

たとえば既存のネットワーク インターフェイスを使って Linux VM を作成するコードは、次のようになります。

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

モジュールの全一覧については[インストール手順](node-sdk-azure-install.md)を参照してください。また、自分の Azure サブスクリプションに対して認証を設定したり、リソースの作成や更新を行うサンプル コードを実行したりする方法については、[概要の記事](node-sdk-azure-get-started.md)を参照してください。 

## <a name="connect-to-azure-services"></a>Azure サービスへの接続

Azure モジュールを使用して Azure 内のリソースを作成したり管理したりするだけでなく、パッケージを使用して、アプリで Azure クラウド サービスに接続して利用することもできます。 たとえば、SQL Database のテーブルを更新したり、Azure Storage にファイルをアップロードしたりすることもできます。 特定のサービスに必要なパッケージを[全一覧](node-sdk-azure-install.md)からお選びください。また、それらのモジュールをアプリ内で使用する方法について紹介したチュートリアルやサンプル コードは、[Node.js デベロッパー センター](https://azure.microsoft.com/develop/nodejs/)から入手できます。

たとえば、Azure ストレージ コンテナーに格納されているすべての BLOB のコンテンツを印刷するには、次のコードを使用します。

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a>サンプル コードとリファレンス

以下のサンプルには、Azure 管理モジュールを使った一般的なタスクが紹介されており、また、独自のアプリですぐに利用できるコードも用意されています。

- [仮想マシン](node-samples-services-compute.md)
- [Web アプリ](node-samples-services-web-and-mobile.md)
- [SQL Database](node-samples-services-database.md)
   
サービス モジュールと管理モジュールの全モジュールについて[リファレンス](https://docs.microsoft.com/javascript/api)が公開されています。 新機能、重大な変更、以前のバージョンからの移行手順については、[リリース ノート](https://github.com/Azure/azure-sdk-for-node/releases)を参照してください。