---
title: Node.js 用 Azure 管理モジュールを使った認証
description: Node.js 用 Azure 管理モジュールへの認証にサービス プリンシパルを使う方法について説明します。
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: b665c537bf17d08c44357009552054d6b2e609d2
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34220514"
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a>Node.js 用 Azure モジュールを使った認証 

すべてのサービス API は、インスタンス化する際に、`credentials` オブジェクトを介して認証を行う必要があります。 必要な資格情報を Azure SDK for Node.js で認証したり作成したりするには、次の 3 とおりの方法があります。 

- 基本認証
- 対話型ログイン
- サービス プリンシパルの認証

## <a name="basic-authentication"></a>基本認証

Azure アカウントの資格情報を使ってプログラムで認証するには、`loginWithUsernamePassword` 関数を使用します。 次の JavaScript コード スニペットは、環境変数として格納された資格情報を使った基本認証の方法を示したものです。 

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithUsernamePassword(process.env.AZURE_USER, 
                                 process.env.AZURE_PASS, 
                                 (err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, 
                                                             '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="interactive-login"></a>対話型ログイン

対話型ログインでは、ユーザーがブラウザーから認証を行うためのリンクとコードが提供されます。 この方法は、同じスクリプトで複数のアカウントが使用される場合や、ユーザーが介入した方が望ましい状況で使用します。

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a>サービス プリンシパルの認証

認証方法としては、[対話型ログイン](#interactive-login)が最も簡単です。 ただし、Node.js SDK を使うときは、アカウントの資格情報を提供するよりも、サービス プリンシパル認証を使った方がよい場合もあります。 サービス プリンシパルの作成 (および使用) に関するさまざまな手法については、「[Node.js を使った Azure サービス プリンシパルの作成](./node-sdk-azure-authenticate-principal.md)」というトピックで説明しています。 