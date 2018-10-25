---
title: Node.js 用 Azure Backup モジュール
description: Node.js 用 Azure Backup モジュールのリファレンス
author: markgalioto
ms.author: markgal
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: bf3e66ac8341cebd28dee20b6370ed3e5fbfbfa0
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "49728285"
---
# <a name="azure-backup-modules-for-nodejs"></a><span data-ttu-id="774d3-103">Node.js 用 Azure Backup モジュール</span><span class="sxs-lookup"><span data-stu-id="774d3-103">Azure Backup Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="774d3-104">概要</span><span class="sxs-lookup"><span data-stu-id="774d3-104">Overview</span></span>

<span data-ttu-id="774d3-105">Azure Backup は、Microsoft Cloud のデータのバックアップ (または保護) と復元に使用できる、Azure ベースのサービスです。</span><span class="sxs-lookup"><span data-stu-id="774d3-105">Azure Backup is the Azure-based service you can use to back up (or protect) and restore your data in the Microsoft cloud.</span></span> <span data-ttu-id="774d3-106">Azure Backup では、既存のオンプレミスまたはオフサイトのバックアップ ソリューションを、信頼性の高い、セキュリティで保護された、コスト競争力のあるクラウド ベースのソリューションに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="774d3-106">Azure Backup replaces your existing on-premises or off-site backup solution with a cloud-based solution that is reliable, secure, and cost-competitive.</span></span> <span data-ttu-id="774d3-107">Azure Backup には複数のコンポーネントが用意されており、これを適切なコンピューター、サーバー、またはクラウドにダウンロードしてデプロイします。</span><span class="sxs-lookup"><span data-stu-id="774d3-107">Azure Backup offers multiple components that you download and deploy on the appropriate computer, server, or in the cloud.</span></span> <span data-ttu-id="774d3-108">デプロイするコンポーネント (エージェント) は、何を保護するかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="774d3-108">The component, or agent, that you deploy depends on what you want to protect.</span></span> <span data-ttu-id="774d3-109">Azure の Recovery Services コンテナーにデータをバックアップするときは、すべての Azure Backup コンポーネントを使用できます (保護対象がオンプレミス データかクラウドのデータかに関係なく)。</span><span class="sxs-lookup"><span data-stu-id="774d3-109">All Azure Backup components (no matter whether you're protecting data on-premises or in the cloud) can be used to back up data to a Recovery Services vault in Azure.</span></span> 

## <a name="management-package"></a><span data-ttu-id="774d3-110">管理パッケージ</span><span class="sxs-lookup"><span data-stu-id="774d3-110">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="774d3-111">npm を使ったモジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="774d3-111">Install the modules with npm</span></span>

<span data-ttu-id="774d3-112">Node.js 用 Azure Backup モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="774d3-112">Use npm to install the Azure Backup modules for Node.js</span></span>

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a><span data-ttu-id="774d3-113">例</span><span class="sxs-lookup"><span data-stu-id="774d3-113">Example</span></span>

<span data-ttu-id="774d3-114">この例では、特定のコンテナーおよびリソース グループの回復ジョブを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="774d3-114">This example lists the recovery jobs for a given vault and resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesBackupManagement = require('azure-arm-recoveryservicesbackup');

const subcriptionId = 'your-subscription-id';
const vault = 'your-recovery-service-vault';
const resourceGroupName = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesBackupManagement(
      credentials,
      subcriptionId
    );
    return client.jobs.list(vault, resourceGroupName);
  })
  .then(jobs => console.dir(jobs, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="774d3-115">サンプル</span><span class="sxs-lookup"><span data-stu-id="774d3-115">Samples</span></span>

<span data-ttu-id="774d3-116">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="774d3-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
