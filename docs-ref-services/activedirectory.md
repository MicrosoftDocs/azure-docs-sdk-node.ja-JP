---
title: "Node.js 用 Azure Active Directory モジュール"
description: "Node.js 用 Azure Active Directory モジュールのリファレンス"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: c91b8396dbfeb766887b650541044f7ce2e7bde6
ms.sourcegitcommit: 79213a25192d8913bf8ec16c19fbec6a8eb691f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="3ace3-103">Node.js 用 Azure Active Directory モジュール</span><span class="sxs-lookup"><span data-stu-id="3ace3-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="3ace3-104">概要</span><span class="sxs-lookup"><span data-stu-id="3ace3-104">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3ace3-105">Azure Active Directory リソースにアクセスする場合、Azure AD Graph API ではなく [Microsoft Graph](https://graph.microsoft.io/) を使用することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3ace3-105">We strongly recommend that you use [Microsoft Graph](https://graph.microsoft.io/) instead of Azure AD Graph API to access Azure Active Directory resources.</span></span> <span data-ttu-id="3ace3-106">開発作業は現在 Microsoft Graph に集中しており、Azure AD Graph API の追加の機能強化は予定されていません。</span><span class="sxs-lookup"><span data-stu-id="3ace3-106">Our development efforts are now concentrated on Microsoft Graph and no further enhancements are planned for Azure AD Graph API.</span></span> <span data-ttu-id="3ace3-107">Azure AD Graph API の使用が適切なシナリオの数は非常に限られています。詳しくは、Office デベロッパー センターのブログ投稿「[Microsoft Graph or the Azure AD Graph (Microsoft Graph または Azure AD Graph)](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3ace3-107">There are a very limited number of scenarios for which Azure AD Graph API might still be appropriate; for more information, see the [Microsoft Graph or the Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) blog post in the Office Dev Center.</span></span>

<span data-ttu-id="3ace3-108">Node.js アプリケーションで AAD に対して認証を行い、AAD によって保護された Web リソースにアクセスするには、[Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) を使用します。</span><span class="sxs-lookup"><span data-stu-id="3ace3-108">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="3ace3-109">クライアント パッケージ</span><span class="sxs-lookup"><span data-stu-id="3ace3-109">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="3ace3-110">npm モジュールのインストール</span><span class="sxs-lookup"><span data-stu-id="3ace3-110">Install the npm modules</span></span>

<span data-ttu-id="3ace3-111">Azure Storage クライアントまたは管理モジュールをインストールするには npm を使用します。</span><span class="sxs-lookup"><span data-stu-id="3ace3-111">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="3ace3-112">例</span><span class="sxs-lookup"><span data-stu-id="3ace3-112">Example</span></span>

<span data-ttu-id="3ace3-113">この例は、[クライアント資格情報サンプル](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js)からの抜粋で、クライアントの資格情報を使ってサーバー間の認証を行います。</span><span class="sxs-lookup"><span data-stu-id="3ace3-113">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

```javascript
const adal = require('adal-node').AuthenticationContext;

const authorityHostUrl = 'https://login.windows.net';
const tenant = 'your-tenant-id';
const authorityUrl = authorityHostUrl + '/' + tenant;
const clientId = 'your-client-id';
const clientSecret = 'your-client-secret';
const resource = 'your-app-id-uri';

const context = new adal(authorityUrl);

context.acquireTokenWithClientCredentials(
  resource,
  clientId,
  clientSecret,
  (err, tokenResponse) => {
    if (err) {
      console.log(`Token generation failed due to ${err}`);
    } else {
      console.dir(tokenResponse, { depth: null, colors: true });
    }
  }
);
```

## <a name="samples"></a><span data-ttu-id="3ace3-114">サンプル</span><span class="sxs-lookup"><span data-stu-id="3ace3-114">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="3ace3-115">アプリで使用できるその他の[サンプル Node.js コード](https://azure.microsoft.com/resources/samples/?platform=nodejs)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="3ace3-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
