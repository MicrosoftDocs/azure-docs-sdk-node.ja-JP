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
# <a name="azure-key-vault-modules-for-nodejs"></a>Node.js 用 Azure Key Vault モジュール

## <a name="overview"></a>概要

Azure Key Vault は、クラウド アプリケーションやサービスで使用される暗号化キーとシークレットをセキュリティで保護するために役立ちます。 Key Vault を使用すると、キーとシークレット (認証キー、ストレージ アカウント キー、データ暗号化キー、PFX ファイル、パスワードなど) をハードウェア セキュリティ モジュール (HSM) で保護されたキーを使用して暗号化できます。 さらに安心感を高めたい場合には、HSM でキーのインポートや生成を行うことができます。 その場合、FIPS 140-2 Level 2 適合の HSM (ハードウェアおよびファームウェア) でマイクロソフトがお客様のキーを処理します。

Key Vault は、キー管理プロセスを合理化し、データにアクセスして暗号化するキーの制御を維持できます。 開発者は、開発やテスト用のキーを数分で作成し、それらをシームレスに実稼働キーに移行できます。 セキュリティ管理者は、必要に応じて、キーに権限を付与する (取り消す) ことができます。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-module"></a>npm モジュールのインストール 

Azure Key Vault の npm モジュールをインストールします。

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a>例

この例では、Azure に新しい Key Vault サービスを作成します。

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

## <a name="samples"></a>サンプル

- [Node.js を使用した Key Vault の概要](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [Azure のリソースとリソース グループを Node.js で管理する](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [NodeJS Web アプリケーションへの Azure AD の統合](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) 

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
