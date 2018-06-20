---
title: Node.js 用 Azure App Service モジュール
description: Node.js 用 Azure App Service モジュールのリファレンス
author: SyntaxC4
ms.author: cfowler
manager: jhubbard
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: d9cb33e9aead2878fc9571b1ccb3a34b8990af74
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34266613"
---
# <a name="azure-app-service-modules-for-nodejs"></a>Node.js 用 Azure App Service モジュール

## <a name="overview"></a>概要

Azure App Service は、Microsoft Azure が提供するサービスとしてのプラットフォーム (PaaS) です。 任意のプラットフォームまたはデバイスを対象として Web アプリとモバイル アプリを作成できます。 作成したアプリと SaaS ソリューションの統合、オンプレミス アプリケーションへの接続、ビジネス プロセスの自動化を実行できます。 Azure では、指定した共有仮想マシン (VM) リソースまたは専用 VM を使用して、完全に管理された VM 上で、アプリが実行されます。

App Service には、以前は Azure Websites および Azure Mobile Services として個別に提供されていた Web 機能とモバイル機能が含まれています。 さらに、ビジネス プロセスの自動化やクラウド API のホストに利用できる新しい機能も備えています。 単一の統合サービスである App Service では、さまざまなコンポーネント (Web サイト、モバイル アプリのバック エンド、RESTful API、ビジネス プロセス) を 1 つのソリューションにまとめることができます。

## <a name="management-package"></a>管理パッケージ

### <a name="install-the-npm-package"></a>npm パッケージのインストール

Node.js 用 Azure App Service モジュールをインストールします。

```bash
npm install azure-arm-website
```

### <a name="example"></a>例

この例では、Node.js を使って Azure に Web サイトを作成します。

```javascript
const msRestAzure = require('ms-rest-azure');
const webSiteManagementClient = require('azure-arm-website');

const subscriptionId = 'your-subscription-id';
const website = 'website001';
const resourceGroup = 'your-resource-group';
const hostingPlan = 'testHostingPlan';
let webSiteClient;

msRestAzure.interactiveLogin().then(credentials => {
  webSiteClient = new webSiteManagementClient(credentials, subscriptionId);
  createWebSite(website).then(website => console.log('Web Site created successfully', website));
});

function createWebSite(webSiteName) {
  const parameters = { location: 'westus', serverFarmId: hostingPlan };
  console.log(`Creating web site:  ${webSiteName}`);
  return webSiteClient.webApps.createOrUpdate(resourceGroup, webSiteName, parameters, null);
}
```

## <a name="samples"></a>サンプル

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。
