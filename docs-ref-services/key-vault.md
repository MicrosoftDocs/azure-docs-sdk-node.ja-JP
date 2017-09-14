---
title: "Node.js 用 Azure Key Vault モジュール"
description: "Node.js 用 Azure Key Vault モジュールのリファレンス"
keywords: Azure,SDK,API,Key Vault, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Key Vault
ms.openlocfilehash: e497e1e0e369dfd975fe5a2d7759ec893fbf6aff
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="azure-key-vault-modules-for-nodejs"></a><span data-ttu-id="d5df8-104">Node.js 用 Azure Key Vault モジュール</span><span class="sxs-lookup"><span data-stu-id="d5df8-104">Azure Key Vault modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d5df8-105">概要</span><span class="sxs-lookup"><span data-stu-id="d5df8-105">Overview</span></span>

<span data-ttu-id="d5df8-106">Azure Key Vault は、クラウド アプリケーションやサービスで使用される暗号化キーとシークレットをセキュリティで保護するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d5df8-106">Azure Key Vault helps safeguard cryptographic keys and secrets used by cloud applications and services.</span></span> <span data-ttu-id="d5df8-107">Key Vault を使用すると、キーとシークレット (認証キー、ストレージ アカウント キー、データ暗号化キー、PFX ファイル、パスワードなど) をハードウェア セキュリティ モジュール (HSM) で保護されたキーを使用して暗号化できます。</span><span class="sxs-lookup"><span data-stu-id="d5df8-107">By using Key Vault, you can encrypt keys and secrets (such as authentication keys, storage account keys, data encryption keys, .PFX files, and passwords) by using keys that are protected by hardware security modules (HSMs).</span></span> <span data-ttu-id="d5df8-108">さらに安心感を高めたい場合には、HSM でキーのインポートや生成を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d5df8-108">For added assurance, you can import or generate keys in HSMs.</span></span> <span data-ttu-id="d5df8-109">その場合、FIPS 140-2 Level 2 適合の HSM (ハードウェアおよびファームウェア) でマイクロソフトがお客様のキーを処理します。</span><span class="sxs-lookup"><span data-stu-id="d5df8-109">If you choose to do this, Microsoft processes your keys in FIPS 140-2 Level 2 validated HSMs (hardware and firmware).</span></span>

<span data-ttu-id="d5df8-110">Key Vault は、キー管理プロセスを合理化し、データにアクセスして暗号化するキーの制御を維持できます。</span><span class="sxs-lookup"><span data-stu-id="d5df8-110">Key Vault streamlines the key management process and enables you to maintain control of keys that access and encrypt your data.</span></span> <span data-ttu-id="d5df8-111">開発者は、開発やテスト用のキーを数分で作成し、それらをシームレスに実稼働キーに移行できます。</span><span class="sxs-lookup"><span data-stu-id="d5df8-111">Developers can create keys for development and testing in minutes, and then seamlessly migrate them to production keys.</span></span> <span data-ttu-id="d5df8-112">セキュリティ管理者は、必要に応じて、キーに権限を付与する (取り消す) ことができます。</span><span class="sxs-lookup"><span data-stu-id="d5df8-112">Security administrators can grant (and revoke) permission to keys, as needed.</span></span>

## <a name="management-package"></a><span data-ttu-id="d5df8-113">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="d5df8-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d5df8-114">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="d5df8-114">Install the npm module</span></span> 

<span data-ttu-id="d5df8-115">Azure Key Vault の npm モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d5df8-115">Install the Azure Key Vault npm module</span></span>

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a><span data-ttu-id="d5df8-116">例</span><span class="sxs-lookup"><span data-stu-id="d5df8-116">Example</span></span>

<span data-ttu-id="d5df8-117">この例では、Azure に新しい Key Vault サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d5df8-117">This example creates a new Key Vault service in Azure.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const KeyVaultManagementClient = require('azure-arm-keyvault');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const vaultName = 'your-new-vault';
const tenantGUID = 'your-tenant-guid';

// Interactive Login
let client;
msRestAzure
  .interactiveLogin()
  .then(credentials => {
    client = new KeyVaultManagementClient(credentials, subscriptionId);
    return client.vaults.list();
  })
  .then(vaults => {
    console.dir(vaults, { depth: null, colors: true });
    const parameters = {
      location: 'East US',
      properties: {
        sku: { family: 'A', name: 'standard' },
        accessPolicies: [],
        enabledForDeployment: false,
        tenantId: tenantGUID
      }
    };
    console.info('Creating vault ${vaultName} ...');
    return client.vaults.createOrUpdate(resourceGroup, vaultName, parameters);
  })
  .then(vault => console.dir(vault, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error occured');
    console.dir(err, { depth: null, colors: true });
    return err;
  });
```

## <a name="samples"></a><span data-ttu-id="d5df8-118">サンプル</span><span class="sxs-lookup"><span data-stu-id="d5df8-118">Samples</span></span>

- [<span data-ttu-id="d5df8-119">Node.js を使用した Key Vault の概要</span><span class="sxs-lookup"><span data-stu-id="d5df8-119">Getting started with Key Vault in Node.js</span></span>](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [<span data-ttu-id="d5df8-120">Azure のリソースとリソース グループを Node.js で管理する</span><span class="sxs-lookup"><span data-stu-id="d5df8-120">Manage Azure resources and resource groups with Node.js</span></span>](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [<span data-ttu-id="d5df8-121">NodeJS Web アプリケーションへの Azure AD の統合</span><span class="sxs-lookup"><span data-stu-id="d5df8-121">Integrating Azure AD into a NodeJS web application</span></span>](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) 

<span data-ttu-id="d5df8-122">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="d5df8-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
