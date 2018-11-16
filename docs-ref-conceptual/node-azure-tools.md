---
title: Azure の JavaScript 開発者向けツール | Microsoft Docs
description: Azure での JavaScript 開発用の各ツールをインストールします。
services: multiple
author: rloutlaw
manager: routlaw
ms.service: azure-nodejs
ms.tgt_pltfrm: na
ms.devlang: nodejs
ms.topic: article
ms.date: 11/07/2017
ms.author: routlaw
ms.openlocfilehash: 1c676b1f31fde7b14a16031b78f767a2c59edd5a
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51502036"
---
# <a name="azure-tools-for-javascript-developers"></a><span data-ttu-id="827a4-103">JavaScript 開発者向け Azure ツール</span><span class="sxs-lookup"><span data-stu-id="827a4-103">Azure tools for JavaScript developers</span></span>
<span data-ttu-id="827a4-104">Azure での JavaScript アプリの開発には、次のツールが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="827a4-104">The following tools are recommended for developing JavaScript apps on Azure.</span></span>

## <a name="azure-cli"></a><span data-ttu-id="827a4-105">Azure CLI</span><span class="sxs-lookup"><span data-stu-id="827a4-105">Azure CLI</span></span>
<span data-ttu-id="827a4-106">Azure CLI は、コマンド ラインから Azure リソースを管理する目的に最適化されています。</span><span class="sxs-lookup"><span data-stu-id="827a4-106">Azure CLI is optimized for managing Azure resources from the command line.</span></span>

![CLI](media/node-azure-tools/cli.png)
 
> [!div class="nextstepaction"]
> [<span data-ttu-id="827a4-108">Azure CLI 2.0 をインストールします</span><span class="sxs-lookup"><span data-stu-id="827a4-108">Install the Azure CLI 2.0</span></span>](https://docs.microsoft.com/cli/azure/install-az-cli2)

## <a name="visual-studio-code"></a><span data-ttu-id="827a4-109">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="827a4-109">Visual Studio Code</span></span>
<span data-ttu-id="827a4-110">任意の OS で JavaScript アプリを編集してデバッグします。</span><span class="sxs-lookup"><span data-stu-id="827a4-110">Edit and debug JavaScript apps on any OS.</span></span>

![Visual Studio Code](media/node-azure-tools/vs-code.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="827a4-112">Visual Studio Code をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="827a4-112">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

### <a name="azure-extensions"></a><span data-ttu-id="827a4-113">Azure 拡張機能</span><span class="sxs-lookup"><span data-stu-id="827a4-113">Azure Extensions</span></span>
<span data-ttu-id="827a4-114">Visual Studio Code で直接 Azure サービスとやり取りするには、次の無料の拡張機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="827a4-114">Use the following free extensions to interface with Azure services directly in Visual Studio Code.</span></span>

| <span data-ttu-id="827a4-115">ツール</span><span class="sxs-lookup"><span data-stu-id="827a4-115">Tool</span></span> | <span data-ttu-id="827a4-116">説明</span><span class="sxs-lookup"><span data-stu-id="827a4-116">Description</span></span>  |
|:---------:|---------|
| [<span data-ttu-id="827a4-117">Azure Functions</span><span class="sxs-lookup"><span data-stu-id="827a4-117">Azure Functions</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions) <br> <span data-ttu-id="827a4-118">[![Azure Functions ツール](media/node-azure-tools/icon-azure-functions.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions)</span><span class="sxs-lookup"><span data-stu-id="827a4-118">[![Azure Functions Tools](media/node-azure-tools/icon-azure-functions.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions)</span></span> | <span data-ttu-id="827a4-119">関数の作成、管理、表示、デバッグ、およびデプロイを行います</span><span class="sxs-lookup"><span data-stu-id="827a4-119">Create, manage, view, debug, and deploy functions</span></span>|
| [<span data-ttu-id="827a4-120">Mobile Apps</span><span class="sxs-lookup"><span data-stu-id="827a4-120">Azure App Service</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice) <br> <span data-ttu-id="827a4-121">[![App Service ツール](media/node-azure-tools/icon-azure-app-service.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice)</span><span class="sxs-lookup"><span data-stu-id="827a4-121">[![App Service Tools](media/node-azure-tools/icon-azure-app-service.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice)</span></span> | <span data-ttu-id="827a4-122">サイトと Azure portal の参照、新しいサイトの作成、スロットへのデプロイを行います</span><span class="sxs-lookup"><span data-stu-id="827a4-122">Browse sites and the Azure portal, create new sites and deploy to slots</span></span> |
| [<span data-ttu-id="827a4-123">Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="827a4-123">Cosmos DB </span></span>](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb)  <br> <span data-ttu-id="827a4-124">[![Cosmos DB ツール](media/node-azure-tools/icon-cosmos-db.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb)</span><span class="sxs-lookup"><span data-stu-id="827a4-124">[![Cosmos DB Tools](media/node-azure-tools/icon-cosmos-db.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb)</span></span>| <span data-ttu-id="827a4-125">Azure でグローバル分散型のマルチモデル データベースを作成、参照、および更新します</span><span class="sxs-lookup"><span data-stu-id="827a4-125">Create, browse, and update globally distributed, multi-model databases in Azure</span></span> |
| [<span data-ttu-id="827a4-126">Docker</span><span class="sxs-lookup"><span data-stu-id="827a4-126">Docker</span></span>](https://marketplace.visualstudio.com/items?itemName=formulahendry.docker-explorer)   <br> <span data-ttu-id="827a4-127">[![Cosmos DB ツール](media/node-azure-tools/icon-docker.png)](https://marketplace.visualstudio.com/items?itemName=formulahendry.docker-explorer)</span><span class="sxs-lookup"><span data-stu-id="827a4-127">[![Cosmos DB Tools](media/node-azure-tools/icon-docker.png)](https://marketplace.visualstudio.com/items?itemName=formulahendry.docker-explorer)</span></span>| <span data-ttu-id="827a4-128">Docker コンテナーとイメージ、Docker Hub、および Azure コンテナー レジストリを管理します</span><span class="sxs-lookup"><span data-stu-id="827a4-128">Manage Docker containers and images, Docker Hub, and Azure container registry</span></span> |

> [!div class="nextstepaction"]
> [<span data-ttu-id="827a4-129">Visual Studio Code Marketplace のその他の Azure 拡張機能 を取得する</span><span class="sxs-lookup"><span data-stu-id="827a4-129">Get more Azure extensions in the Visual Studio Code marketplace</span></span>](https://marketplace.visualstudio.com/search?term=azure&target=VSCode&category=All%20categories&sortBy=Relevance)