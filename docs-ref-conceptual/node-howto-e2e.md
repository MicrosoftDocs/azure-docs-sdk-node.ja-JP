---
title: "Visual Studio Code と Azure での Node.js 開発"
description: "Node.js アプリの作成、Docker 化、Azure へのデプロイの方法を紹介する完全なエンド ツー エンドのチュートリアル"
services: multiple
author: tomarcher
manager: douge
ms.service: azure-nodejs
ms.tgt_pltfrm: na
ms.devlang: nodejs
ms.topic: article
ms.date: 06/25/2017
ms.author: joncart
ms.openlocfilehash: 1b43502394b7224c5791ee870999cdb958a0969d
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="nodejs-development-with-visual-studio-code-and-azure"></a><span data-ttu-id="934b8-103">Visual Studio Code と Azure での Node.js 開発</span><span class="sxs-lookup"><span data-stu-id="934b8-103">Node.js development with Visual Studio Code and Azure</span></span>

<span data-ttu-id="934b8-104">このチュートリアルでは、既存の Node.js アプリを (Docker で) "コンテナー化" したうえで、Visual Studio Code を使って Azure にデプロイします。</span><span class="sxs-lookup"><span data-stu-id="934b8-104">This tutorial illustrates taking an existing Node.js app, "containerizing" it (with Docker), and then deploying the app to Azure using Visual Studio Code.</span></span>

<span data-ttu-id="934b8-105">チュートリアルでは、[Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular) によって作成、公開されている単純な todo アプリを使用します。</span><span class="sxs-lookup"><span data-stu-id="934b8-105">The tutorial makes use of a simple todo app created by and published by [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular).</span></span> <span data-ttu-id="934b8-106">これは単一ページの MEAN アプリです。データベースには MongoDB が、REST API/Web サーバーには Node/Express が、フロントエンド UI には Angular.js 1.x が使用されています。</span><span class="sxs-lookup"><span data-stu-id="934b8-106">It is a single-page MEAN app, and therefore, uses MongoDB as its database, Node/Express for the REST API/web server, and Angular.js 1.x for the front-end UI.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="934b8-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="934b8-107">Prerequisites</span></span>

<span data-ttu-id="934b8-108">このデモに沿って作業するためには、次のソフトウェアがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="934b8-108">In order to follow along with the demo, you'll need to have the following software installed:</span></span>

- [<span data-ttu-id="934b8-109">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="934b8-109">Visual Studio Code</span></span>](https://code.visualstudio.com/)
- [<span data-ttu-id="934b8-110">Docker</span><span class="sxs-lookup"><span data-stu-id="934b8-110">Docker</span></span>](https://www.docker.com/products/docker)
- [<span data-ttu-id="934b8-111">DockerHub アカウント</span><span class="sxs-lookup"><span data-stu-id="934b8-111">DockerHub account</span></span>](https://hub.docker.com/)
- [<span data-ttu-id="934b8-112">Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="934b8-112">Azure CLI 2.0</span></span>](https://docs.microsoft.com/cli/azure/install-az-cli2)
- [<span data-ttu-id="934b8-113">Azure アカウント</span><span class="sxs-lookup"><span data-stu-id="934b8-113">Azure account</span></span>](https://azure.microsoft.com/free/)
- [<span data-ttu-id="934b8-114">Yarn</span><span class="sxs-lookup"><span data-stu-id="934b8-114">Yarn</span></span>](https://yarnpkg.com/en/docs/install)
- <span data-ttu-id="934b8-115">[Chrome](https://www.google.com/chrome/browser/desktop/) - デモ アプリのフロントエンドをデバッグするために使用します。</span><span class="sxs-lookup"><span data-stu-id="934b8-115">[Chrome](https://www.google.com/chrome/browser/desktop/) - Used for debugging the demo app's front-end.</span></span>
- <span data-ttu-id="934b8-116">MongoDB - デモ アプリでは MongoDB を使用しているため、MongoDB インスタンスがローカルで実行され、標準 `27017` ポートでリッスンしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="934b8-116">MongoDB - Since the demo app uses MongoDB, you need to have a locally running MongoDB instance that is listening on the standard `27017` port.</span></span> <span data-ttu-id="934b8-117">この要件は、2 つのコマンドを実行することによってごく簡単に満たすことができます。Docker のインストール後、`docker pull mongo` コマンドに続けて `docker run -it -p 27017:27017 mongo` コマンドを実行してください。</span><span class="sxs-lookup"><span data-stu-id="934b8-117">The simplest way to achieve this is by running the following two commands after Docker is installed: `docker pull mongo` followed by `docker run -it -p 27017:27017 mongo`.</span></span>

## <a name="project-setup"></a><span data-ttu-id="934b8-118">プロジェクトのセットアップ</span><span class="sxs-lookup"><span data-stu-id="934b8-118">Project setup</span></span>

<span data-ttu-id="934b8-119">最初に、次の手順でサンプル プロジェクトをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="934b8-119">To get started, download the sample project using the following steps:</span></span>

1. <span data-ttu-id="934b8-120">Visual Studio Code を開きます。</span><span class="sxs-lookup"><span data-stu-id="934b8-120">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="934b8-121">**F1** キーを押してコマンド パレットを表示します。</span><span class="sxs-lookup"><span data-stu-id="934b8-121">Press **&lt;F1>** to display the command palette.</span></span>

1. <span data-ttu-id="934b8-122">コマンド パレットのプロンプトに「`gitcl`」と入力し、**Git: Clone** コマンドを選択して、**Enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="934b8-122">At the command palette prompt, enter `gitcl`, select the **Git: Clone** command, and press **&lt;Enter>**.</span></span>

    ![Visual Studio Code コマンド パレットのプロンプトに gitcl コマンドを入力](./media/node-howto-e2e/git-clone.png)

1. <span data-ttu-id="934b8-124">**リポジトリの URL** を求められたら、「`https://github.com/scotch-io/node-todo`」と入力し、**Enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="934b8-124">When prompted for the **Repository URL**, enter `https://github.com/scotch-io/node-todo`, then press **&lt;Enter>**.</span></span>

1. <span data-ttu-id="934b8-125">プロジェクトの複製先となるローカル ディレクトリを選択 (または作成) します。</span><span class="sxs-lookup"><span data-stu-id="934b8-125">Select (or create) the local directory into which you want to clone the project.</span></span>

    ![Visual Studio Code エクスプローラー](./media/node-howto-e2e/explorer.png)

## <a name="integrated-terminal"></a><span data-ttu-id="934b8-127">統合ターミナル</span><span class="sxs-lookup"><span data-stu-id="934b8-127">Integrated terminal</span></span>

<span data-ttu-id="934b8-128">Node.js プロジェクトであるため、最初に npm からプロジェクトのすべての依存関係をインストールしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="934b8-128">Since this is a Node.js project, the first thing you need to do is ensure that all of the project's dependencies are installed from npm.</span></span>  

1. <span data-ttu-id="934b8-129">**Ctrl** キーを押して Visual Studio Code の統合ターミナルを表示します。</span><span class="sxs-lookup"><span data-stu-id="934b8-129">Press **&lt;Ctrl>\`** to display the Visual Studio Code integrated terminal.</span></span> 

1. <span data-ttu-id="934b8-130">「`yarn`」と入力し、**Enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="934b8-130">Enter `yarn`, and press **&lt;Enter>**.</span></span>  

    ![Visual Studio Code 内で yarn コマンドを実行](./media/node-howto-e2e/terminal.png)

## <a name="integrated-git-version-control"></a><span data-ttu-id="934b8-132">Git バージョン コントロールの統合</span><span class="sxs-lookup"><span data-stu-id="934b8-132">Integrated Git version control</span></span>

<span data-ttu-id="934b8-133">Yarn でアプリの依存関係をインストールすると、`yarn.lock` ファイルが作成されます。このファイルによって、将来、CI (継続的インテグレーション) ビルドや運用環境、他の開発者のマシンに不測の事態を招くことなく、まったく同じ依存関係を確実にインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-133">After installing the app's dependencies via Yarn, a `yarn.lock` file is created that provides a predictable way to reacquire the exact same dependencies in the future, without any surprises in either CI (continuous integration) builds, production deployments, or other developer machines.</span></span>

<span data-ttu-id="934b8-134">次の手順で、`yarn.lock` ファイルをソース管理にチェックインする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="934b8-134">The following steps illustrate how to check the `yarn.lock` file into source control:</span></span>

1. <span data-ttu-id="934b8-135">Visual Studio Code 内で、統合された Git タブ (Git ロゴのあるタブ) に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="934b8-135">Within Visual Studio Code, switch to the integrated Git tab (the tab with the Git logo).</span></span>

1. <span data-ttu-id="934b8-136">**[メッセージ]** ボックスにコミット メッセージを入力し、**Ctrl + Enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="934b8-136">In the **Message** box, enter a commit message, and press **&lt;Ctrl>&lt;Enter>**.</span></span> 

    ![yarn.lock ファイルを Git に追加](./media/node-howto-e2e/git.png)

## <a name="project-and-code-navigation"></a><span data-ttu-id="934b8-138">プロジェクトとコードのナビゲーション</span><span class="sxs-lookup"><span data-stu-id="934b8-138">Project and code navigation</span></span>

<span data-ttu-id="934b8-139">コードベースの操作に慣れるために、Visual Studio Code に備わっているナビゲーション機能の例をいくつか紹介します。</span><span class="sxs-lookup"><span data-stu-id="934b8-139">In order to orient ourselves within the codebase, let's play around with some examples of some of the navigation capabilities that Visual Studio Code provides.</span></span>

1. <span data-ttu-id="934b8-140">**Ctrl + P** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="934b8-140">Press **&lt;Ctrl>P**.</span></span>

1. <span data-ttu-id="934b8-141">「`.js`」と入力すると、プロジェクトに含まれているすべての JavaScript/JSON ファイルが、各ファイルの親ディレクトリと共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="934b8-141">Enter `.js` to display all the JavaScript/JSON files in the project along with each file's parent directory</span></span> 

    ![すべての .js* ファイルを表示](./media/node-howto-e2e/git-output.png)

1. <span data-ttu-id="934b8-143">`server.js` (アプリのスタートアップ スクリプト) を選択します。</span><span class="sxs-lookup"><span data-stu-id="934b8-143">Select `server.js`, which is the startup script for the app.</span></span> 

1. <span data-ttu-id="934b8-144">**database** 変数 (6 行目のインポート) にマウス カーソルを合わせると、該当する型が表示されます。</span><span class="sxs-lookup"><span data-stu-id="934b8-144">Hover your mouse over the **database** variable (imported on line 6) to see its type.</span></span> <span data-ttu-id="934b8-145">ファイル内の変数/モジュール/型をすぐに調べることができるので、プロジェクトの開発時にとても役立ちます。</span><span class="sxs-lookup"><span data-stu-id="934b8-145">This ability to quickly inspect variables/modules/types within a file is very useful during the development of your projects.</span></span> 

    ![型の調査](./media/node-howto-e2e/hover-help.png)

1. <span data-ttu-id="934b8-147">変数 (**database** など) 内のどこかでマウスをクリックすると、同じファイル内でその変数が使われている箇所をすべて確認できます。</span><span class="sxs-lookup"><span data-stu-id="934b8-147">Clicking your mouse within the span of a variable - such as **database** - allows you to see all references to that variable within the same file.</span></span> <span data-ttu-id="934b8-148">プロジェクト内である変数が使われている箇所をすべて表示するには、その変数を右クリックし、コンテキスト メニューから、**[すべての参照の検索]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="934b8-148">To view all references to a variable within the project, right-click the variable, and from the context menu, and select **Find All References**.</span></span>

    ![変数が使われている箇所を探す](./media/node-howto-e2e/word-hilight.png)

1. <span data-ttu-id="934b8-150">マウス カーソルを変数に合わせることによってその型を調べることに加え、変数の定義を調べることもできます。別のファイルに存在していても問題ありません。</span><span class="sxs-lookup"><span data-stu-id="934b8-150">In addition to being to hover your mouse over a variable to discover its type, you can also inspect the definition of a variable, even if it's in another file.</span></span> <span data-ttu-id="934b8-151">この機能の働きを確かめるには、**database.localUrl** (12 行目) を右クリックしてコンテキスト メニューから **[定義をここに表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="934b8-151">To see this in action, right-click **database.localUrl** (line 12), and, from the context menu, select **Peek Definition**.</span></span> 

    ![変数の定義をプレビュー](./media/node-howto-e2e/code-peek.png)

## <a name="modifying-the-code-and-using-autocompletion"></a><span data-ttu-id="934b8-153">コードの変更とオートコンプリートの使用</span><span class="sxs-lookup"><span data-stu-id="934b8-153">Modifying the code and using autocompletion</span></span>

<span data-ttu-id="934b8-154">**database.localUrl** の宣言には、MongoDB の接続文字列がハードコーディングされています。</span><span class="sxs-lookup"><span data-stu-id="934b8-154">The MongoDB connection string is hard-coded in declaration of the **database.localUrl**.</span></span> <span data-ttu-id="934b8-155">このセクションでは、環境変数から接続文字列を取得するようにコードを変更すると共に、Visual Studio Code のオートコンプリート機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="934b8-155">In this section, you'll modify the code to retrieve the connection string from an environment variable, and learn about Visual Studio Code's autocompetion feature.</span></span>  

1. <span data-ttu-id="934b8-156">`server.js` ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="934b8-156">Open the `server.js` file</span></span>

1. <span data-ttu-id="934b8-157">次のコードを探してください。</span><span class="sxs-lookup"><span data-stu-id="934b8-157">Replace the following code:</span></span> 

    ```javascript
    mongoose.connect(database.localUrl);
    ```

    <span data-ttu-id="934b8-158">次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="934b8-158">with this code:</span></span>

    ```javascript
    mongoose.connect(process.env.MONGODB_URL || database.localUrl);
    ```

<span data-ttu-id="934b8-159">コードを (コピーして貼り付けるのではなく) 手動で入力した場合、`process` の後にピリオドを入力すると自動的に、Node.js の **process** グローバル API で使用できるメンバーが表示されることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="934b8-159">Note that if you type the code in manually (instead of copy and paste), when you type the period after `process`, Visual Studio Code displays the available members of the Node.js **process** global API.</span></span>

![オートコンプリートによって API のメンバーが自動的に表示される](./media/node-howto-e2e/process-env.png)

<span data-ttu-id="934b8-161">オートコンプリートは、Visual Studio Code がバックグラウンドで TypeScript (JavaScript にも対応) を使用し、型情報を提供することによって実現されています。その型情報が、ユーザーが何か入力したときに、入力候補一覧に伝えられます。</span><span class="sxs-lookup"><span data-stu-id="934b8-161">Autocompetion works because Visual Studio Code uses TypeScript behind the scenes - even for JavaScript - to provide type information that can then be used to inform the completion list as you type.</span></span> <span data-ttu-id="934b8-162">Visual Studio Code は、Node.js プロジェクトを認識し、[Node.js に使用される TypeScript の型指定ファイルを NPM から](https://www.npmjs.com/package/@types/node)自動的にダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="934b8-162">Visual Studio Code is able to detect that this is a Node.js project, and as a result, automatically downloaded the TypeScript typings file for [Node.js from NPM](https://www.npmjs.com/package/@types/node).</span></span> <span data-ttu-id="934b8-163">この型指定ファイルの存在によって、他の Node.js グローバル (**Buffer**、**setTimeout** など) や組み込みモジュール (**fs**、**http** など) でオートコンプリートが利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="934b8-163">The typings file allows you to get autocompletion for other Node.js globals - such as **Buffer** and **setTimeout** - as well as all of the built-in modules such as **fs** and **http**.</span></span>

<span data-ttu-id="934b8-164">型指定の自動取得は、Node.js の組み込み API に対してだけでなく、React、Underscore、Express など、2,000 を超えるサード パーティ モジュールに対しても機能します。</span><span class="sxs-lookup"><span data-stu-id="934b8-164">In addition to the built-in Node.js APIs, this auto-acquisition of typings also works for over 2,000 3rd party modules, such as React, Underscore and Express.</span></span> <span data-ttu-id="934b8-165">たとえば、構成されている MongoDB データベース インスタンスに Mongoose が接続できなかった場合に、サンプル アプリがクラッシュしないようにするためには、次のコード行を 13 行目に挿入します。</span><span class="sxs-lookup"><span data-stu-id="934b8-165">For example, in order to disable Mongoose from crashing the sample app if it can't connect to the configured MongoDB database instance, insert the following line of code at  line 13:</span></span>

```javascript
mongoose.connection.on("error", () => { console.log("DB connection error"); });
```

<span data-ttu-id="934b8-166">先ほどのコードと同様、何もしなくてもオートコンプリートが作動することがわかります。</span><span class="sxs-lookup"><span data-stu-id="934b8-166">As with the previous code, you'll notice that you get autocompletion without any work on your part.</span></span>

![オートコンプリートによって API のメンバーが自動的に表示される](./media/node-howto-e2e/mongoose.png)

<span data-ttu-id="934b8-168">このオートコンプリート機能がどのモジュールでサポートされているかについては、[DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) プロジェクトを参照すると確認できます。このプロジェクトは、TypeScript のすべての型定義のソースとなるもので、コミュニティが中心となって作成しています。</span><span class="sxs-lookup"><span data-stu-id="934b8-168">You can see which modules support this auto-complete capability by browsing the [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) project, which is the community-driven source of all TypeScript type definitions.</span></span>

## <a name="running-the-app"></a><span data-ttu-id="934b8-169">アプリの実行</span><span class="sxs-lookup"><span data-stu-id="934b8-169">Running the app</span></span>

<span data-ttu-id="934b8-170">コードをひととおり確認したら、実際にアプリを実行してみましょう。</span><span class="sxs-lookup"><span data-stu-id="934b8-170">Once you've explored the code a bit, it's time to run the app.</span></span> <span data-ttu-id="934b8-171">Visual Studio Code でアプリを実行するには、**F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="934b8-171">To run the app from Visual Studio Code, press **&lt;F5>**.</span></span> <span data-ttu-id="934b8-172">**F5** (デバッグ モード) でコードを実行すると、Visual Studio Code によってアプリが起動され、**[デバッグ コンソール]** ウィンドウが表示されて、アプリの StdOut が表示されます。</span><span class="sxs-lookup"><span data-stu-id="934b8-172">When running the code via **&lt;F5>** (debug mode), Visual Studio Code launches the app and displays the **Debug Console** window that displays stdout for the app.</span></span>

![デバッグ コンソールでアプリの StdOut を監視](./media/node-howto-e2e/console.png)

<span data-ttu-id="934b8-174">また、**デバッグ コンソール**は最近実行したアプリにアタッチされるので、JavaScript の式を入力すれば、そのアプリ内で評価されます。オートコンプリートも機能します。</span><span class="sxs-lookup"><span data-stu-id="934b8-174">Additionally, the **Debug Console** is attached to the newly running app so you can type JavaScript expressions, which will be evaluated in the app, and also includes auto-completion.</span></span> <span data-ttu-id="934b8-175">その働きを確かめるために、コンソールに「`process.env`」と入力してみましょう。</span><span class="sxs-lookup"><span data-stu-id="934b8-175">To see this in action, type `process.env` in the console:</span></span>

![デバッグ コンソールにコードを入力](./media/node-howto-e2e/console-code.png)

<span data-ttu-id="934b8-177">先ほど **F5** キーを押してアプリを実行できたのは、現在開いているファイルが JavaScript ファイル (`server.js`) であるためです。</span><span class="sxs-lookup"><span data-stu-id="934b8-177">You were able to press **&lt;F5>** to run the app because the currently open file is a JavaScript file (`server.js`).</span></span> <span data-ttu-id="934b8-178">その結果、プロジェクトが Node.js アプリであると Visual Studio Code によって認識されました。</span><span class="sxs-lookup"><span data-stu-id="934b8-178">As a result, Visual Studio Code assumes that the project is a Node.js app.</span></span> <span data-ttu-id="934b8-179">Visual Studio Code で JavaScript ファイルをすべて閉じて、**F5** キーを押した場合は、環境を選択するように求められます。</span><span class="sxs-lookup"><span data-stu-id="934b8-179">If you close all JavaScript files in Visual Studio Code, and then press **&lt;F5>**, Visual Studio Code will query you as the environment:</span></span>

![ランタイム環境の指定](./media/node-howto-e2e/select-env.png)

<span data-ttu-id="934b8-181">ブラウザーを開いて `http://localhost:8080` に移動し、実行中のアプリを表示します。</span><span class="sxs-lookup"><span data-stu-id="934b8-181">Open a browser, and navigate to `http://localhost:8080` to see the running app.</span></span> <span data-ttu-id="934b8-182">テキスト ボックスにメッセージを入力し、いくつかの todo を追加/削除しながら、アプリの動作を確かめます。</span><span class="sxs-lookup"><span data-stu-id="934b8-182">Type a message into the textbox and add/remove a few todos to get a feel for how the app works.</span></span>

![実行中の todo アプリ](./media/node-howto-e2e/todo.png)

## <a name="debugging"></a><span data-ttu-id="934b8-184">デバッグ</span><span class="sxs-lookup"><span data-stu-id="934b8-184">Debugging</span></span>

<span data-ttu-id="934b8-185">Visual Studio Code では、統合コンソールでアプリを実行したり対話的に操作したりすることに加え、コード内に直接ブレークポイントを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-185">In addition to being able to run the app and interact with it via the integrated console, Visual Studio Code provides the ability to set breakpoints directly within your code.</span></span> <span data-ttu-id="934b8-186">試しに **Ctrl + P** キーを押して、ファイル ピッカーを表示してください。</span><span class="sxs-lookup"><span data-stu-id="934b8-186">For example, press **&lt;Ctrl>P** to display the file picker.</span></span> <span data-ttu-id="934b8-187">ファイル ピッカーが表示されたら、「`route`」と入力して `route.js` ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="934b8-187">Once the file picker displays, type `route`, and select the `route.js` file.</span></span>

<span data-ttu-id="934b8-188">28 行目にブレークポイントを設定します。この行は、アプリが todo エントリを追加しようとしたときに呼び出される Express ルートを表します。</span><span class="sxs-lookup"><span data-stu-id="934b8-188">Set a breakpoint on line 28, which represents the Express route that is called when the app tries to add a todo entry.</span></span> <span data-ttu-id="934b8-189">ブレークポイントは、次の図のようにエディター内で行番号の左側の領域をクリックするだけで設定できます。</span><span class="sxs-lookup"><span data-stu-id="934b8-189">To set a breakpoint, simply click the area to the left of the line number within the editor as shown in the following figure.</span></span>

![Visual Studio Code 内でブレークポイントを設定](./media/node-howto-e2e/breakpoint.png)

> [!NOTE]
> <span data-ttu-id="934b8-191">Visual Studio Code では標準的なブレークポイントに加え、条件付きブレークポイントもサポートされており、アプリの実行を一時停止するタイミングをカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-191">In addition to standard breakpoints, Visual Studio Code supports conditional breakpoints that allow you to customize when the app should suspend execution.</span></span> <span data-ttu-id="934b8-192">条件付きブレークポイントを設定するには、実行を一時停止する行の左側の領域を右クリックし、**[条件付きブレークポイントの追加]** を選択します。次に、JavaScript の式 (例: `foo = "bar"`) または実行回数を指定して、実行を一時停止する条件を定義します。</span><span class="sxs-lookup"><span data-stu-id="934b8-192">To set a conditional breakpoint, right-click the area to the left of the line on which you wish to pause execution, select **Add Conditional Breakpoint...**, and specify either a JavaScript expression (e.g. `foo = "bar"`) or execution count that defines the condition under which you want to pause execution.</span></span>
> 
> 

<span data-ttu-id="934b8-193">ブレークポイントを設定したら、実行中のアプリに戻って、todo エントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="934b8-193">Once the breakpoint has been set, return to the running app and add a todo entry.</span></span> <span data-ttu-id="934b8-194">todo エントリを追加するとすぐに、ブレークポイントを設定した 28 行目でアプリの実行が一時停止されます。</span><span class="sxs-lookup"><span data-stu-id="934b8-194">Adding a todo entry immediately causes the app to suspend execution on line 28 where you set the breakpoint:</span></span>

![Visual Studio Code によりブレークポイントで実行が一時停止される](./media/node-howto-e2e/debugger.png)

<span data-ttu-id="934b8-196">アプリケーションが一時停止された後、コードの式にマウス カーソルを合わせると、現在の値を表示することができます。さらに、ローカル変数/ウォッチ式や呼び出し履歴を調べたり、デバッグ ツール バーを使ってコードをステップ実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="934b8-196">Once the application has been paused, you can hover your mouse over the code's expressions to view their current value, inspect the locals/watches and call stack, and use the debug toolbar to step through the code execution.</span></span> <span data-ttu-id="934b8-197">**F5** キーを押すと、アプリの実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="934b8-197">Press **&lt;F5>** to resume execution of the app.</span></span>

## <a name="full-stack-debugging"></a><span data-ttu-id="934b8-198">フルスタック デバッグ</span><span class="sxs-lookup"><span data-stu-id="934b8-198">Full-stack debugging</span></span>

<span data-ttu-id="934b8-199">このトピックの最初に述べたように、この todo アプリは MEAN アプリです。つまり、そのフロントエンドとバックエンドはどちらも JavaScript で記述されています。</span><span class="sxs-lookup"><span data-stu-id="934b8-199">As mentioned earlier in the topic, the TODO app is a MEAN app - meaning that its front-end and back-end are both written using JavaScript.</span></span> <span data-ttu-id="934b8-200">そのため現在はバックエンド (Node/Express) コードをデバッグしていますが、いずれフロントエンド (Angular) コードのデバッグが必要になることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="934b8-200">So, while you're currently debugging the back-end (Node/Express) code, at some point, you may need to debug the front-end (Angular) code.</span></span> <span data-ttu-id="934b8-201">そのため、Visual Studio Code には広大な拡張機能のエコシステムが存在します。その例として統合 Chrome デバッグが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="934b8-201">For that purpose, Visual Studio Code has a huge ecosystem of extensions, including integrated Chrome debugging.</span></span>

<span data-ttu-id="934b8-202">**[拡張機能]** タブに切り替えて、検索ボックスに「`chrome`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="934b8-202">Switch to the **Extensions** tab, and type `chrome` into the search box:</span></span>

![Visual Studio Code 用の Chrome デバッグ拡張機能](./media/node-howto-e2e/chrome.png)

<span data-ttu-id="934b8-204">**Debugger for Chrome** という名前の拡張機能を選択し、**[インストール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="934b8-204">Select the extension named **Debugger for Chrome**, and select **Install**.</span></span> <span data-ttu-id="934b8-205">Chrome デバッグ拡張機能をインストールしたら、**[再読み込み]** を選択してください。拡張機能をアクティブ化するために、Visual Studio Code を一度閉じて開き直します。</span><span class="sxs-lookup"><span data-stu-id="934b8-205">After installing the Chrome debugging extension, select **Reload** to close and reopen Visual Studio Code in order to activate the extension.</span></span> 

![Chrome デバッグ拡張機能をインストールした後で Visual Studio Code を再度読み込む](./media/node-howto-e2e/chrome-extension-reload-vscode.png)

<span data-ttu-id="934b8-207">Node.js コードの実行とデバッグを行ううえで Visual Studio Code に特別な構成は必要ありませんでしたが、フロントエンド Web アプリをデバッグするためには、アプリの実行方法を Visual Studio Code に伝える `launch.json` ファイルを生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="934b8-207">While you were able to run and debug the Node.js code without any Visual Stdio Code-specific configuration, in order to debug a front-end web app, you need to generate a `launch.json` file that instructs Visual Studio Code how to run the app.</span></span> 

<span data-ttu-id="934b8-208">`launch.json` ファイルを生成するためには、**[デバッグ]** タブに切り替えて、歯車アイコン (上部に小さな赤色の点が表示されます) をクリックし、**node.js** 環境を選択します。</span><span class="sxs-lookup"><span data-stu-id="934b8-208">To generate the `launch.json` file, switch to the **Debug** tab, click the gear icon (which should have a little red dot on top of it), and select the **node.js** environment.</span></span>

![launch.json ファイルを構成するための Visual Studio Code オプション](./media/node-howto-e2e/debug-gear.png)

<span data-ttu-id="934b8-210">生成された `launch.json` ファイルは、次のようになります。アプリをデバッグするために、それをどのように起動し、どのようにアタッチするかが、このファイルによって Visual Studio Code に伝えられます。</span><span class="sxs-lookup"><span data-stu-id="934b8-210">Once created, the `launch.json` file looks similar to the following, and tells Visual Studio Code how to launch and/or attach to the app in order to debug it.</span></span> 

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "launch",
            "name": "Launch Program",
            "program": "${workspaceRoot}/server.js"
        },
        {
            "type": "node",
            "request": "attach",
            "name": "Attach to Port",
            "address": "localhost",
            "port": 5858
        }
    ]
}
```

<span data-ttu-id="934b8-211">先ほど、このアプリのスタートアップ スクリプトが `server.js` であることを Visual Studio Code が検出できたことを思い出してください。</span><span class="sxs-lookup"><span data-stu-id="934b8-211">Note that Visual Studio Code was able to detect that the app's startup script is `server.js`.</span></span> 

<span data-ttu-id="934b8-212">`launch.json` ファイルを開いた状態で、**[構成の追加]** (右下) を選択し、**Chrome: Launch with userDataDir** を選択します。</span><span class="sxs-lookup"><span data-stu-id="934b8-212">With the `launch.json` file open, select **Add Configuration** (bottom right), and select **Chrome: Launch with userDataDir**.</span></span>

![Chrome の構成を Visual Studio Code に追加](./media/node-howto-e2e/add-chrome-config.png)

<span data-ttu-id="934b8-214">Chrome 用に新しい実行構成を追加することで、フロントエンド JavaScript コードをデバッグできるようになります。</span><span class="sxs-lookup"><span data-stu-id="934b8-214">Adding a new run configuration for Chrome allows you to debug the front-end JavaScript code.</span></span> 

<span data-ttu-id="934b8-215">指定されているいずれかの設定にマウス カーソルを合わせると、その設定の内容についてのドキュメントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="934b8-215">You can hover your mouse over any of the settings that are specified to view documentation about what the setting does.</span></span> <span data-ttu-id="934b8-216">さらに、アプリの URL が Visual Studio Code によって自動的に検出されることがわかります。</span><span class="sxs-lookup"><span data-stu-id="934b8-216">Additionally, notice that Visual Studio Code automatically detects the URL of the app.</span></span> <span data-ttu-id="934b8-217">アプリのフロントエンド アセットの検索対象となる場所を Chrome デバッガーが認識できるように、**webRoot** プロパティを `${workspaceRoot}/public` に更新します。</span><span class="sxs-lookup"><span data-stu-id="934b8-217">Update the **webRoot** property to `${workspaceRoot}/public` so that the Chrome debugger will know where to find the app's front-end assets:</span></span>

```json
{
   "type": "chrome",
   "request": "launch",
   "name": "Launch Chrome",
   "url": "http://localhost:8080",
   "webRoot": "${workspaceRoot}/public",
   "userDataDir": "${workspaceRoot}/.vscode/chrome"
}
```

<span data-ttu-id="934b8-218">フロントエンドとバックエンドの両方を同時に起動/デバッグするためには、"*複合*" 実行構成を作成して、並列実行する一連の構成を Visual Studio Code に伝える必要があります。</span><span class="sxs-lookup"><span data-stu-id="934b8-218">In order to launch/debug both the front and back-end at the same time, you need to create a *compound* run configuration that tells Visual Studio Code which set of configurations to run in parallel.</span></span> 

<span data-ttu-id="934b8-219">次のスニペットを `launch.json` ファイル内の最上位のプロパティとして (既存の **configurations** プロパティの兄弟として) 追加します。</span><span class="sxs-lookup"><span data-stu-id="934b8-219">Add the following snippet as a top-level property within the `launch.json` file (as a sibling of the existing **configurations** property).</span></span>

```json
"compounds": [
   {
      "name": "Full-Stack",
      "configurations": ["Launch Program", "Launch Chrome"]
   }
]
```

<span data-ttu-id="934b8-220">**compounds.configurations** 配列に指定した文字列値は、**configurations** のリストに含まれる各エントリの **name** を表します。</span><span class="sxs-lookup"><span data-stu-id="934b8-220">The string values specified in the **compounds.configurations** array refer to the **name** of individual entries in the list of **configurations**.</span></span> <span data-ttu-id="934b8-221">これらの名前を変更した場合は、適宜配列に変更を加える必要があります。</span><span class="sxs-lookup"><span data-stu-id="934b8-221">If you've modfied those names, you'll need to make the appropriate changes in the array.</span></span> <span data-ttu-id="934b8-222">この動作を確かめるには、[デバッグ] タブに切り替えて、選択構成を **[Full-Stack]** (複合構成の名前) に変更し、**F5** キーを押して実行します。</span><span class="sxs-lookup"><span data-stu-id="934b8-222">To see this in action, switch to the debug tab, and change the selected configuration to **Full-Stack** (the name of the compound configuration), and press **&lt;F5>** to run it.</span></span>

![Visual Studio Code での構成の実行](./media/node-howto-e2e/full-stack-profile.png)

<span data-ttu-id="934b8-224">この構成を実行すると、デバッグ コンソール出力に見られるような Node.js アプリと、`http://localhost:8080` の Node.js アプリに移動するように構成された Chrome が起動します。</span><span class="sxs-lookup"><span data-stu-id="934b8-224">Running the configuration launches the Node.js app (as can be seen in the debug console output) and Chrome (configured to navigate to the Node.js app at `http://localhost:8080`).</span></span>

<span data-ttu-id="934b8-225">**Ctrl + P** キーを押して、`todos.js` を入力 (または選択) します。これが、アプリのフロントエンドに使用されるメイン Angular コントローラーになります。</span><span class="sxs-lookup"><span data-stu-id="934b8-225">Press **&lt;Ctrl>P**, and enter (or select) `todos.js`, which is the main Angular controller for the app's front-end.</span></span> 

<span data-ttu-id="934b8-226">11 行目 (新しい todo エントリ作成のエントリ ポイント) にブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="934b8-226">Set a breakpoint on line 11, which is the entry-point for a new todo entry being created.</span></span>

<span data-ttu-id="934b8-227">実行中のアプリに戻って新しい todo エントリを追加すると、Visual Studio Code の実行が Angular コード内で中断されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="934b8-227">Return to the running app, add a new todo entry, and notice that Visual Studio Code has now suspended execution within the Angular code.</span></span>

![Visual Studio Code でのフロントエンド コードのデバッグ](./media/node-howto-e2e/chrome-pause.png)

<span data-ttu-id="934b8-229">Node.js のデバッグと同様、式にマウス カーソルを置くことでローカル変数/ウォッチ式を確認したり、コンソール内で式を評価したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-229">Like Node.js debugging, you can hover your mouse over expressions, view locals/watches, evaluate expressions in the console, and so on.</span></span> 

<span data-ttu-id="934b8-230">ここで便利な機能を 2 つ紹介します。</span><span class="sxs-lookup"><span data-stu-id="934b8-230">There are two cools things to note:</span></span>

1. <span data-ttu-id="934b8-231">**[呼び出し履歴]** ウィンドウには、**Node** と **Chrome** の 2 種類のスタックが表示され、現在どちらが一時停止されているのかを把握できます。</span><span class="sxs-lookup"><span data-stu-id="934b8-231">The **Call Stack** pane displays two different stacks: **Node** and **Chrome**, and indicates which one is currently paused.</span></span>

1. <span data-ttu-id="934b8-232">フロントエンド コードとバックエンド コードの間でステップ実行することができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-232">You can step between front and back-end code.</span></span> <span data-ttu-id="934b8-233">試しに **F5** キーを押してみてください。先ほど設定した Express ルートのブレークポイントに到達します。</span><span class="sxs-lookup"><span data-stu-id="934b8-233">To test this, press **&lt;F5>**, which will run and hit the breakpoint previously set in the Express route.</span></span>

<span data-ttu-id="934b8-234">この設定によって、フロントエンド、バックエンド、またはフルスタックの JavaScript コードを Visual Studio Code 内から直接効率的にデバッグすることができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-234">With this setup, you can now efficiently debug front, back, or full-stack JavaScript code directly within Visual Studio Code.</span></span> 

<span data-ttu-id="934b8-235">また、複合デバッガーの概念は、2 つのターゲット プロセスに限定されたものではなく、また JavaScript に限定されたものでもありません。</span><span class="sxs-lookup"><span data-stu-id="934b8-235">In addition, the compound debugger concept is not limited to just two target processes, and also isn't just limited to JavaScript.</span></span> <span data-ttu-id="934b8-236">したがってマイクロサービス アプリ (多言語も含む) の開発を行う場合も、(言語/フレームワークの適切な拡張機能をインストールしたうえで) まったく同じワークフローを利用することができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-236">Therefore, if work on a microservice app (that is potentially polyglot), you can use the exact same workflow (once you've installed the appropriate extensions for the language/framework).</span></span>

## <a name="dockerizing-the-app"></a><span data-ttu-id="934b8-237">アプリの Docker 化</span><span class="sxs-lookup"><span data-stu-id="934b8-237">Dockerizing the app</span></span>

<span data-ttu-id="934b8-238">このセクションでは、[Docker](https://www.docker.com/) を使った開発のために Visual Studio Code が備えている機能について重点的に説明します。</span><span class="sxs-lookup"><span data-stu-id="934b8-238">This section focuses on the experience that Visual Studio Code provides for developing with [Docker](https://www.docker.com/).</span></span> <span data-ttu-id="934b8-239">Node.js の開発者は、CI (継続的インテグレーション) と運用環境のどちらの開発においても、Docker を使ってポータブルなアプリのデプロイを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-239">Node.js developers use Docker to provide portable app deployments for both development, CI (continuous integration), and production environments.</span></span> <span data-ttu-id="934b8-240">Docker は習得が容易であることから、Visual Studio Code には、アプリに Docker を使って作業を単純化する拡張機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="934b8-240">As Docker presents a steep-learning curve to some, Visual Studio Code provides an extension that tries to help simplify some using Docker in your apps.</span></span>

<span data-ttu-id="934b8-241">**[拡張機能]** タブに切り替え、「`docker`」を検索して、**Docker** 拡張機能を選択します。</span><span class="sxs-lookup"><span data-stu-id="934b8-241">Switch back to the **Extensions** tab, search for `docker`, and select the **Docker** extension.</span></span> 

<span data-ttu-id="934b8-242">Docker 拡張機能をインストールし、Visual Studio Code を再度読み込みます。</span><span class="sxs-lookup"><span data-stu-id="934b8-242">Install the Docker extension, and then reload Visual Studio Code.</span></span>

![Visual Studio Code 用の Docker 拡張機能をインストール](./media/node-howto-e2e/docker-search.png)

<span data-ttu-id="934b8-244">Visual Studio Code 用 Docker 拡張機能には、*Dockerfile* や、既存のプロジェクト用の `docker-compose.yml` ファイルを生成するためのコマンドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="934b8-244">The Docker extension for Visual Studio Code includes a command for generating a *Dockerfile* and the `docker-compose.yml` file for an existing project.</span></span> 

<span data-ttu-id="934b8-245">利用可能な Docker コマンドを確認するには、**F1** キーを押してコマンド パレットを表示し、「`docker`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="934b8-245">To see the available Docker commands, display the command palette - via **&lt;F1>** - and type `docker`.</span></span>

![<span data-ttu-id="934b8-246">Visual Studio 用 Docker 拡張機能でサポートされているコマンド</span><span class="sxs-lookup"><span data-stu-id="934b8-246">Commands supported by the Docker extension for Visual Studio</span></span> ](./media/node-howto-e2e/docker-commands.png)

<span data-ttu-id="934b8-247">**Docker: Add docker files to workspace** を選択してアプリのプラットフォームに **Node.js** を選択し、アプリで公開するポートとして `8080` を指定します。</span><span class="sxs-lookup"><span data-stu-id="934b8-247">Select **Docker: Add docker files to workspace**, select **Node.js** as the app platform, and specify that the app exposes port `8080`.</span></span> 

<span data-ttu-id="934b8-248">この Docker コマンドによって、そのまま使うことができる完全な `Dockerfile` と Docker-compose ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="934b8-248">The Docker command generates a complete `Dockerfile` and Docker-compose files that you can begin using immediately.</span></span>

![生成された Dockerfile](./media/node-howto-e2e/docker-file.png)

<span data-ttu-id="934b8-250">また、この Docker 拡張機能によって、`Dockerfiles` ファイルと `docker-compose.yml` ファイルでオートコンプリートを利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="934b8-250">The Docker extension also provides auto-completion for your `Dockerfiles` and `docker-compose.yml` files.</span></span> 

<span data-ttu-id="934b8-251">実際にその動作を確かめるために、`Dockerfile` を開いて 2 行目 (下記) に変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="934b8-251">To see this in action, open the `Dockerfile` and change line 2 from:</span></span>

```docker
FROM node:latest
```

<span data-ttu-id="934b8-252">変更後:</span><span class="sxs-lookup"><span data-stu-id="934b8-252">To:</span></span>

```docker
FROM mhart
```

<span data-ttu-id="934b8-253">`mhart` の `t` の後にカーソルを置いて、**Ctrl + Space** キーを押すと、`mhart` が DockerHub に公開しているすべてのイメージ リポジトリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="934b8-253">With your cursor positioned after the `t` in `mhart`, press **&lt;Ctrl>&lt;Space>** to view all the image repositories that `mhart` has published on DockerHub.</span></span>

![Docker 拡張機能のオートコンプリート](./media/node-howto-e2e/docker-completion.png)

<span data-ttu-id="934b8-255">`mhart/alpine-node` を選択します。このアプリに必要なあらゆるものが、ここから得られます。</span><span class="sxs-lookup"><span data-stu-id="934b8-255">Select `mhart/alpine-node`, which provides everything that this app needs.</span></span> 

<span data-ttu-id="934b8-256">通常、イメージはできるだけ小さくすることをお勧めします。アプリのビルドとデプロイにかかる時間が最小限で済み、配布とスケーリングを迅速に行うことができるためです。</span><span class="sxs-lookup"><span data-stu-id="934b8-256">Smaller images are typically better since you want your app builds and deployments to be as fast as possible, which makes distribution and scaling quicker.</span></span>

<span data-ttu-id="934b8-257">`Dockerfile` を生成したら、実際の Docker イメージを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="934b8-257">Now, that you have generated the `Dockerfile`, you need to build the actual Docker image.</span></span> <span data-ttu-id="934b8-258">ここでも、Docker 拡張機能によって Visual Studio Code にインストールされたコマンドを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-258">Once again, you can use a command that the Docker extension installed in Visual Studio Code.</span></span> <span data-ttu-id="934b8-259">**F1** キーを押し、コマンド パレットに「`dockerb`」と入力して、**Docker: Build Image** コマンドを選択します。</span><span class="sxs-lookup"><span data-stu-id="934b8-259">Press **&lt;F1>**, enter `dockerb` at the command palette, and select the **Docker: Build Image** command.</span></span> <span data-ttu-id="934b8-260">先ほど生成して編集した `/Dockerfile` を選択してください。</span><span class="sxs-lookup"><span data-stu-id="934b8-260">Choose the `/Dockerfile` that you just generated and modified.</span></span> <span data-ttu-id="934b8-261">DockerHub のユーザー名が含まれたタグを指定します (例: `lostintangent/node`)。</span><span class="sxs-lookup"><span data-stu-id="934b8-261">Specify a tag that includes your DockerHub username (e.g. `lostintangent/node`).</span></span> <span data-ttu-id="934b8-262">**ENTER** キーを押して統合ターミナル ウィンドウを起動し、作成中の Docker イメージの出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="934b8-262">Press **&lt;ENTER>** to launch the integrated terminal window that displays the output of your Docker image being built.</span></span>

![Docker イメージの作成ステータス](./media/node-howto-e2e/docker-build.png)

<span data-ttu-id="934b8-264">このコマンドによって、`docker build` を実行するプロセスが自動化され、ここでも高い生産性が実現されていることに注目してください。この方法を選ばずに、単に Docker CLI を直接使用してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="934b8-264">Notice that the command automated the process of running `docker build` for you, which is another example of a productivity enhancer that you can either choose to use, or you can just use the Docker CLI directly.</span></span> 

<span data-ttu-id="934b8-265">この時点で、このイメージを簡単に取得してデプロイできるようにするために、DockerHub にイメージをプッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="934b8-265">At this point, to make this image easily acquirable for deployments, you need only push the image to DockerHub.</span></span> <span data-ttu-id="934b8-266">そのためには、CLI から `docker login` を実行し、アカウントの資格情報を入力して、あらかじめ DockerHub に対して認証を行っておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="934b8-266">To do this, make sure you have already autheticated with DockerHub by running `docker login` from the CLI and entering your account credentials.</span></span> <span data-ttu-id="934b8-267">そのうえで、Visual Studio Code でコマンド パレットを呼び出し、「`dockerpush`」を入力して、`Docker: Push` コマンドを選択します。</span><span class="sxs-lookup"><span data-stu-id="934b8-267">Then, in Visual Studio Code, you can bring up the command palette, enter `dockerpush`, and select the `Docker: Push` command.</span></span> <span data-ttu-id="934b8-268">先ほど作成したイメージ タグ (例: `lostintangent/node`) を選択して、**Enter** キーを押してください。</span><span class="sxs-lookup"><span data-stu-id="934b8-268">Select the image tag that you just built (e.g. `lostintangent/node`) and press **&lt;Enter>**.</span></span> <span data-ttu-id="934b8-269">このコマンドによって自動的に `docker push` が呼び出され、統合ターミナルに出力結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="934b8-269">The command automates the calling of `docker push` and displays the output in the integrated terminal.</span></span>

## <a name="deploying-the-app"></a><span data-ttu-id="934b8-270">アプリのデプロイ</span><span class="sxs-lookup"><span data-stu-id="934b8-270">Deploying the app</span></span>

<span data-ttu-id="934b8-271">アプリを Docker 化して DockerHub にプッシュしたところで、それをクラウドにデプロイして公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="934b8-271">Now that you the app Dockerized and pushed to DockerHub, you need to deploy it to the cloud so the world can see it.</span></span> <span data-ttu-id="934b8-272">この作業には、Azure の PaaS サービスである Azure App Service を使用できます。</span><span class="sxs-lookup"><span data-stu-id="934b8-272">For this, you can use Azure App Service, which is Azure's PaaS offering.</span></span> <span data-ttu-id="934b8-273">App Service には、Node.js の開発者に関係した 2 つの機能があります。</span><span class="sxs-lookup"><span data-stu-id="934b8-273">App Service has two capabilities that are relevant to Node.js developers:</span></span>

- <span data-ttu-id="934b8-274">Linux ベースの VM のサポート。ネイティブの Node モジュールを使って作成されたアプリや Windows をサポートしていない (または動作が異なる) 可能性のある各種ツールの互換性の問題が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="934b8-274">Support for Linux-based VMs, which reduces incompatibilities for apps which are built using native Node modules, or other tools which might not support Windows and/or may behave differently.</span></span>
- <span data-ttu-id="934b8-275">Docker ベースのデプロイのサポート。Docker イメージの名前を指定して、そのイメージを App Service で自動的にプル、デプロイ、スケーリングすることができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-275">Support for Docker-based deployments, which allows you to specify the name of your Docker image, and allow App Service to pull, deploy, and scale the image automatically.</span></span>

<span data-ttu-id="934b8-276">最初に、Visual Studio ターミナルを開きます。</span><span class="sxs-lookup"><span data-stu-id="934b8-276">To get started, open up the Visual Studio terminal.</span></span> <span data-ttu-id="934b8-277">Azure アカウントを管理したり、必要なインフラストラクチャをプロビジョニングして todo アプリを実行したりするには、新しい Azure CLI 2.0 を使います。</span><span class="sxs-lookup"><span data-stu-id="934b8-277">You'll use the new Azure CLI 2.0 to manage your Azure account and provision the necessary infrastructure to run the todo app.</span></span> <span data-ttu-id="934b8-278">「前提条件」で触れたように、この CLI で `az login` コマンドを使ってアカウントにログインした後、次の手順に従って App Service インスタンスをプロビジョニングし、todo アプリのコンテナーをデプロイします。</span><span class="sxs-lookup"><span data-stu-id="934b8-278">Once you've logged into your account from the CLI using the `az login` command (as mentioned in the pre-reqs), perform the following steps to provision the App Service instance and deploy the todo app container:</span></span>

1. <span data-ttu-id="934b8-279">リソース グループを作成します。リソース グループは、Azure リソースを効率的に体系化するための "*名前空間*" または "*ディレクトリ*" と考えることができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-279">Create a resource group, which you can think of as a *namespace* or *directory* for helping to organize Azure resources.</span></span> <span data-ttu-id="934b8-280">グループの名前は `-n` オプションで指定します。任意の名前を使用できます。</span><span class="sxs-lookup"><span data-stu-id="934b8-280">The `-n` option is used to specify the name of the group and can be anything you want.</span></span>

    ```shell
    az group create -n nina-demo -l westus
    ```

    > [!NOTE]
    > <span data-ttu-id="934b8-281">`-l` オプションは、リソース グループの場所を示します。</span><span class="sxs-lookup"><span data-stu-id="934b8-281">The `-l` option indicates the location of the resource group.</span></span> <span data-ttu-id="934b8-282">プレビュー段階では、Linux における App Service のサポートが一部のリージョンに限られます。</span><span class="sxs-lookup"><span data-stu-id="934b8-282">While in preview, the App Service on Linux support is available only in select regions.</span></span> <span data-ttu-id="934b8-283">したがって、ご利用のリージョンが米国西部以外の場合に、他にどのリージョンが利用できるかを調べるには、CLI で `az appservice list-locations --linux-workers-enabled` を実行して、選択可能なデータセンターを確認してください。</span><span class="sxs-lookup"><span data-stu-id="934b8-283">Therefore, if you aren't located in the Western US, and you want to check which other regions are available, run `az appservice list-locations --linux-workers-enabled` from the CLI to view your datacenter options.</span></span>

2. <span data-ttu-id="934b8-284">今後 CLI でコマンドを呼び出すときに毎回明示的にリソース グループを指定しなくて済むよう、新たに作成したリソース グループを既定のリソース グループとして設定します。</span><span class="sxs-lookup"><span data-stu-id="934b8-284">Set the newly created resource group as the default resource group so that you can continue to use the CLI without needing to explicitly specify the resource group with each CLI call:</span></span>

   ```shell
   az configure -d group=nina-demo
   ```
   
3. <span data-ttu-id="934b8-285">App Service "*プラン*" を作成します。アプリのデプロイ先となるベースの仮想マシンの作成とスケーリングは、このプランによって管理されます。</span><span class="sxs-lookup"><span data-stu-id="934b8-285">Create the App Service *plan*, which manages the creation and scaling of the underlying virtual machines to which your app is deployed.</span></span> <span data-ttu-id="934b8-286">この場合も、`n` オプションには任意の値を指定してください。</span><span class="sxs-lookup"><span data-stu-id="934b8-286">Once again, specify any value that you'd like for the `n` option.</span></span>

    ```shell
    az appservice plan create -n nina-demo-plan --is-linux
    ```

    > [!NOTE]
    > <span data-ttu-id="934b8-287">--is-linux は、Linux ベースの仮想マシンを希望するかどうかを指定するオプションです。</span><span class="sxs-lookup"><span data-stu-id="934b8-287">The --is-linux option is indicates that you want Linux-based virtual machines.</span></span> <span data-ttu-id="934b8-288">指定しなかった場合は、既定で Windows ベースの仮想マシンがプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="934b8-288">Without it, the CLI defaults to provisioning Windows-based virtual machines.</span></span>

4. <span data-ttu-id="934b8-289">App Service Web アプリを作成します。これは、先ほど作成したプランとリソース グループ内で実行される実際の todo アプリを表します。</span><span class="sxs-lookup"><span data-stu-id="934b8-289">Create the App Service web app, which represents the actual todo app that will be running within the plan and resource group just created.</span></span> <span data-ttu-id="934b8-290">Web アプリとプランはそれぞれ、プロセス (またはコンテナー) とそれらが実行される仮想マシン (またはコンテナー ホスト) と同義と考えることができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-290">You can think of a web app as being synonymous with a process or container, and the plan as being the virtual machine/container host that they're running on.</span></span> <span data-ttu-id="934b8-291">さらに、Web アプリを作成する過程で、DockerHub に公開した Docker イメージを使うための構成を、その Web アプリに対して行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="934b8-291">Additionally, as part of creating the web app, you'll need to configure it to use the Docker image you published to DockerHub:</span></span>

    ```shell
    az webapp create -n nina-demo-app -p nina-demo-plan -i lostintangent/node
    ``` 

    > [!NOTE]
    > <span data-ttu-id="934b8-292">カスタム コンテナーではなく Git デプロイを使いたい場合は、記事「[Azure で Node.js Web アプリを作成する](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="934b8-292">If instead of using a custom container, you'd prefer a Git deployment, refer to the article, [Create a Node.js web app in Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).</span></span>

5. <span data-ttu-id="934b8-293">Web アプリを既定の Web インスタンスとして設定します。</span><span class="sxs-lookup"><span data-stu-id="934b8-293">Set the web app as the default web instance:</span></span>

    ```shell
    az configure -d web=nina-demo-app
    ```

6. <span data-ttu-id="934b8-294">アプリを起動して、デプロイしたコンテナーを表示します。コンテナーには、`*.azurewebsites.net` という URL でアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="934b8-294">Launch the app to view the deployed container, which will be available at an `*.azurewebsites.net` URL:</span></span>

    ```shell
    az webapp browse
    ```

    ![ブラウザーで実行中の todo アプリ](./media/node-howto-e2e/browse-app.png)

    > [!NOTE]
    > <span data-ttu-id="934b8-296">初回は、App Service が Docker イメージを DockerHub からプルして起動する必要があるために、アプリの読み込みに数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="934b8-296">It may take few minutes to load app the first time as App Service has to pull the Docker image from DockerHub and then start it.</span></span>

<span data-ttu-id="934b8-297">この時点で、todo アプリのデプロイと実行は完了しています。</span><span class="sxs-lookup"><span data-stu-id="934b8-297">At this point, you've just deployed and run the todo app.</span></span> 

<span data-ttu-id="934b8-298">実際、今 todo アプリをデプロイしたところですが、</span><span class="sxs-lookup"><span data-stu-id="934b8-298">You have now deployed the todo app.</span></span> <span data-ttu-id="934b8-299">回転するアイコンが表示されています。これは、アプリがデータベースに接続できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="934b8-299">However, the spinning icon indicates that the app can't connect to the database.</span></span> <span data-ttu-id="934b8-300">その原因は、開発中に MongoDB のローカル インスタンスを使用していたためです。当然、Azure データセンター内からローカル インスタンスに到達することはできません。</span><span class="sxs-lookup"><span data-stu-id="934b8-300">This is due to the fact that you were using a local instance of MongoDB during development, which obviously isn't reachable from within the Azure datacenters.</span></span> <span data-ttu-id="934b8-301">先ほどアプリに変更を加え、環境変数を介して接続文字列を取得できるようにしたので、後は MongoDB サーバーを起動し、環境変数を参照するように App Service インスタンスを再構成するだけです。</span><span class="sxs-lookup"><span data-stu-id="934b8-301">Since you modified the app to accept the connection string via an environment variable, you need only to start a MongoDB server and re-configure the App Service instance to reference the environment variable.</span></span> <span data-ttu-id="934b8-302">この点について、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="934b8-302">This is illustrated in the next section.</span></span>

## <a name="provisioning-a-mongodb-server"></a><span data-ttu-id="934b8-303">MongoDB サーバーのプロビジョニング</span><span class="sxs-lookup"><span data-stu-id="934b8-303">Provisioning a MongoDB server</span></span>

<span data-ttu-id="934b8-304">MongoDB サーバー (またはレプリカ セット) を構成し、そのインフラストラクチャを自分で管理することもできますが、Azure には、[Cosmos DB](https://azure.microsoft.com/services/documentdb/) というソリューションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="934b8-304">While you could configure a MongoDB server, or replica set, and manage that infrastructure yourself, Azure provides a solution called [Cosmos DB](https://azure.microsoft.com/services/documentdb/).</span></span> <span data-ttu-id="934b8-305">Cosmos DB は、完全に管理された、geo レプリケーション対応のハイパフォーマンス NoSQL データベースで、MongoDB 互換のレイヤーを備えています。</span><span class="sxs-lookup"><span data-stu-id="934b8-305">Cosmos DB is a fully-managed, geo-replicable, high-performance, NoSQL database that provides a MongoDB-compatibility layer.</span></span> <span data-ttu-id="934b8-306">つまり接続文字列の変更だけで、既存の MEAN アプリ (または [Studio 3T](https://studio3t.com/) などの MongoDB クライアント/ツール) を接続できるということです。</span><span class="sxs-lookup"><span data-stu-id="934b8-306">This means that you can point an existing MEAN app at it (or any MongoDB client/tool such as [Studio 3T](https://studio3t.com/)) without needing to change anything but the connection string.</span></span> <span data-ttu-id="934b8-307">その方法を次の手順で説明します。</span><span class="sxs-lookup"><span data-stu-id="934b8-307">The following steps illustrate how this is done:</span></span>

1. <span data-ttu-id="934b8-308">Visual Studio Code ターミナルで次のコマンドを実行して、MongoDB 互換の Cosmos DB サービス インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="934b8-308">From the Visual Studio Code terminal, run the following command to create a MongoDB-compatible instance of the Cosmos DB service.</span></span> <span data-ttu-id="934b8-309">**<NAME>** プレースホルダーには、グローバルに一意となる値を指定してください (この名前は、Cosmos DB がデータベースのサーバー URL を生成するときに使用されます)。</span><span class="sxs-lookup"><span data-stu-id="934b8-309">Replace the **<NAME>** placeholder with a globally unique value (Cosmos DB uses this name to generate the database's server URL):</span></span>

   ```shell
   COSMOSDB_NAME=<NAME>
   az cosmosdb create -n $COSMOSDB_NAME --kind MongoDB
   ```

2. <span data-ttu-id="934b8-310">このインスタンスの MongoDB 接続文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="934b8-310">Retrieve the MongoDB connection string for this instance:</span></span>

   ```shell
   MONGODB_URL=$(az cosmosdb list-connection-strings -n $COSMOSDB_NAME -otsv --query "connectionStrings[0].connectionString")
   ```

3. <span data-ttu-id="934b8-311">ローカルで実行されている (実際には存在しない) MongoDB サーバーに接続を試みるのではなく、新しくプロビジョニングした Cosmos DB インスタンスが接続先となるように、Web アプリの **MONGODB_URL** 環境変数を更新します。</span><span class="sxs-lookup"><span data-stu-id="934b8-311">Update your web app's **MONGODB_URL** environment variable so that it connects to the newly provisioned Cosmos DB instance instead of attempting to connect to a locally running MongoDB server (that doesn't exist!):</span></span>

    ```shell
    az webapp config appsettings set --settings MONGODB_URL=$MONGODB_URL
    ```

4. <span data-ttu-id="934b8-312">ブラウザーに戻って最新の情報に更新します。</span><span class="sxs-lookup"><span data-stu-id="934b8-312">Return to your browser and refresh it.</span></span> <span data-ttu-id="934b8-313">todo 項目の追加と削除を試しながら、(何も変更しなくても) アプリが正常に動作することを確かめます。</span><span class="sxs-lookup"><span data-stu-id="934b8-313">Try adding and removing a todo item to prove that the app now works without needing to change anything!</span></span> <span data-ttu-id="934b8-314">作成済みの Cosmos DB インスタンスを環境変数に設定します。MongoDB データベースは、この Cosmos DB インスタンスによって完全にエミュレートされます。</span><span class="sxs-lookup"><span data-stu-id="934b8-314">Set the environment variable to the created Cosmos DB instance, which is fully emulating a MongoDB database.</span></span>

    ![データベースに接続した後のデモ アプリ](./media/node-howto-e2e/finished-demo.png)

<span data-ttu-id="934b8-316">必要に応じて Cosmos DB インスタンスに戻り、MongoDB インスタンスが必要とする予約済みスループットをスケールアップ (またはスケールダウン) すれば、インフラストラクチャを手動で管理することなく、トラフィックの増大に対応できるメリットを活かすことができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-316">When needed, you can switch back to the Cosmos DB instance and scale up (or down) the reserved throughput that the MongoDB instance needs, and benefit from the added traffic without needing to manage any infrastructure manually.</span></span>

<span data-ttu-id="934b8-317">さらに、Cosmos DB では、あらゆるドキュメントおよびプロパティのインデックスが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="934b8-317">Additionally, Cosmos DB automatically indexes every single document and property for you.</span></span> <span data-ttu-id="934b8-318">そのため低速クエリを自分でプロファイリングしたり、インデックスを手動で微調整したりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="934b8-318">That way, you don't need to profile slow queries or manually fine-tune your indexes.</span></span> <span data-ttu-id="934b8-319">プロビジョニングして、必要に応じてスケーリングを行うだけで、後は Cosmos DB が対処します。</span><span class="sxs-lookup"><span data-stu-id="934b8-319">Just provision and scale as needed, and let Cosmos DB handle the rest.</span></span>

## <a name="hosting-a-private-docker-registry"></a><span data-ttu-id="934b8-320">プライベート Docker レジストリのホスティング</span><span class="sxs-lookup"><span data-stu-id="934b8-320">Hosting a private Docker registry</span></span>

<span data-ttu-id="934b8-321">DockerHub は、コンテナー イメージを配布する手段としてきわめて高い利便性を備えていますが、状況によっては、独自のプライベート Docker レジストリをホスティングした方が都合がよい場合もあります (セキュリティやガバナンス、パフォーマンス上の優位性など)。</span><span class="sxs-lookup"><span data-stu-id="934b8-321">DockerHub provides an amazing experience for distributing your container images, but there may be scenarios where you'd prefer to host your own private Docker registry - such as for security/governance or performance benefits.</span></span> <span data-ttu-id="934b8-322">そのため Azure には、独自の Docker レジストリを立ち上げることができる [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR) が用意されています。ACR ではバッキング ストレージが Web アプリと同じデータ センターに置かれるため、プルにかかる時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="934b8-322">For this purpose, Azure provides the [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR) that allows you to spin up your own Docker registry whose backing storage is located in the same data center as your web app (which makes pulls quicker).</span></span> <span data-ttu-id="934b8-323">また ACR では、コンテンツとアクセス管理 (イメージのプッシュまたはプルをだれに許可するかなど) を完全に自分で制御することができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-323">The ACR also provides you with full control over the contents and access controls - such as who can push or pull images.</span></span> 

<span data-ttu-id="934b8-324">カスタム レジストリをプロビジョニングするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="934b8-324">Provisioning a custom registry can be accomplished by running the following command.</span></span> <span data-ttu-id="934b8-325">**<NAME>** プレースホルダーには、グローバルに一意となる値を指定してください。指定した値は、ACR がレジストリのログイン サーバー URL を生成するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="934b8-325">(Replace the **<NAME>** placeholder with a globally unique value as ACR uses specified value to generate the registry's login server URL.</span></span>

```shell
ACR_NAME=<NAME>
az acr create -n $ACR_NAME -l westus --admin-enabled
```

> [!NOTE]
> <span data-ttu-id="934b8-326">このトピックの例では、単純化するために**管理者アカウント**を使っていますが、運用環境のレジストリではお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="934b8-326">While this topic's example uses the **admin account** to keep things simple, it is not recommended for production registries.</span></span> 

<span data-ttu-id="934b8-327">`az acr create` コマンドは、Docker CLI でログインするときに使用するログイン サーバー URL を (`LOGIN SERVER` 列に) 表示します (例: `ninademo.azurecr.io`)。</span><span class="sxs-lookup"><span data-stu-id="934b8-327">The `az acr create` commands displays the login server URL (via the `LOGIN SERVER` column) that you use to log in using the Docker CLI (e.g. `ninademo.azurecr.io`).</span></span> <span data-ttu-id="934b8-328">また、このコマンドを実行すると、管理者の認証に使用するための資格情報が生成されます。</span><span class="sxs-lookup"><span data-stu-id="934b8-328">Additionally, the command generates admin credentials that you can use in order to authenticate against it.</span></span> <span data-ttu-id="934b8-329">それらの資格情報を取得するには、次のコマンドを実行し、表示されたユーザー名とパスワードをメモしてください。</span><span class="sxs-lookup"><span data-stu-id="934b8-329">To retrieve those credentials, run the following command and note the displayed username and password:</span></span>

```shell
az acr credential show -n $ACR_NAME
```

<span data-ttu-id="934b8-330">レジストリには、前の手順で取得した資格情報と、個々に割り当てられたログイン サーバーを使い、標準的な Docker CLI ワークフローでログインすることができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-330">Using the credentials from the previous step, and your individual login server, you can log in to the registry using the standard Docker CLI workflow.</span></span>

```shell
docker login <LOGIN_SERVER> -u <USERNAME> -p <PASSWORD>
```

<span data-ttu-id="934b8-331">Docker コンテナーにタグ付けし、プライベート レジストリに関連付けられていることを示すには、次のコマンドを使用します。`lostintangent/node` には、実際のコンテナー イメージに付けた名前を指定してください。</span><span class="sxs-lookup"><span data-stu-id="934b8-331">You can now tag your Docker container to indicate that it's associated with your private registry using the following command (replacing `lostintangent/node` with the name you gave the container image.</span></span>

```shell
docker tag lostintangent/node <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="934b8-332">最後に、タグ付けしたイメージをプライベート Docker レジストリにプッシュします。</span><span class="sxs-lookup"><span data-stu-id="934b8-332">Finally, push the tagged image to your private Docker registry.</span></span>

```shell
docker push <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="934b8-333">これでコンテナーが独自のプライベート レジストリに格納されました。また Docker CLI は、DockerHub を使用していたときと同じように利用することができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-333">Your container is now stored in your own private registry, and the Docker CLI was happy to allow you to continue working in the same way as you did when using DockerHub.</span></span> <span data-ttu-id="934b8-334">プライベート レジストリからプルするよう App Service Web アプリに命令するには、次のコマンドを実行するだけです。</span><span class="sxs-lookup"><span data-stu-id="934b8-334">In order to instruct the App Service web app to pull from your private registry, you need only run the following command:</span></span>

```shell
az appservice web config container set \
    -r <LOGIN_SERVER> \
    -c <LOGIN_SERVER>/lostintangent/node \
    -u <USERNAME> \
    -p <PASSWORD> 
```

> [!NOTE]
> <span data-ttu-id="934b8-335">`-r` オプションの先頭には、必ず `https://` プレフィックスを追加してください。</span><span class="sxs-lookup"><span data-stu-id="934b8-335">Make sure to add the `https://` prefix to the beginning of the `-r` option.</span></span> <span data-ttu-id="934b8-336">一方、コンテナー イメージの名前にはプレフィックスを追加しないでください。</span><span class="sxs-lookup"><span data-stu-id="934b8-336">However, don't add the prefix to the container image name.</span></span>

<span data-ttu-id="934b8-337">ブラウザーでアプリを最新の情報に更新しても、一見、変わったところがないように見えます。</span><span class="sxs-lookup"><span data-stu-id="934b8-337">If you refresh the app in your browser, everything should look and work the same.</span></span> <span data-ttu-id="934b8-338">しかし現在は、アプリがプライベート Docker レジストリを介して実行されています。</span><span class="sxs-lookup"><span data-stu-id="934b8-338">However, it's now running your app via your private Docker registry.</span></span> <span data-ttu-id="934b8-339">アプリを更新したら、先ほどと同じようにタグ付けして変更をプッシュし、App Service コンテナーの構成でタグを更新してください。</span><span class="sxs-lookup"><span data-stu-id="934b8-339">Once you update your app, tag and push the changes as done above, and update the tag in your App Service container configuration.</span></span>

## <a name="configuring-a-custom-domain-name"></a><span data-ttu-id="934b8-340">カスタム ドメイン名の構成</span><span class="sxs-lookup"><span data-stu-id="934b8-340">Configuring a custom domain name</span></span>

<span data-ttu-id="934b8-341">テスト目的であれば、`*.azurewebsites.net` という URL でまったく問題ありませんが、いずれはカスタム ドメイン名を Web アプリに追加することが必要になると考えられます。</span><span class="sxs-lookup"><span data-stu-id="934b8-341">While the `*.azurewebsites.net` URL is great for testing, at some point you may want to add a custom domain name to your web app.</span></span> <span data-ttu-id="934b8-342">レジストラーからドメイン名を取得したら、Web アプリの外部 IP (実際にはロード バランサー) を指す `A` レコードをそこに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="934b8-342">Once you have a domain name from a registrar, you need only add an `A` record to it  that points at your web app's external IP (which is actually a load balancer).</span></span> <span data-ttu-id="934b8-343">この IP は、次のコマンドを実行することで取得できます。</span><span class="sxs-lookup"><span data-stu-id="934b8-343">You can retrieve this IP by running the following command:</span></span>

```shell
az webapp config hostname get-external-ip
```

<span data-ttu-id="934b8-344">`A` レコードを追加することに加え、これまで使用してきた `*.azurewebsites.net` ドメインを指す `TXT` レコードをドメインに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="934b8-344">In addition to add an `A` record, you also need to add a `TXT` record to your domain that points at the `*.azurewebsites.net` domain you've been using thus far.</span></span> <span data-ttu-id="934b8-345">Azure では、ユーザーがドメインを所有していることが `A` レコードと `TXT` レコードの組み合わせによって確認されます。</span><span class="sxs-lookup"><span data-stu-id="934b8-345">The combination of the `A` and `TXT` records allows Azure to verify that you own the domain.</span></span>

<span data-ttu-id="934b8-346">これらのレコードが作成されたら (なおかつ DNS の変更が反映されたら)、そのカスタム ドメインを Azure に登録して、受信トラフィックを Azure が正しく認識できるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="934b8-346">Once those records are created - and the DNS changes have propagated - register the custom domain with Azure so that it knows to expect the incoming traffic correctly.</span></span> 

```shell
az webapp config hostname add --hostname <DOMAIN>
```

> [!NOTE]
> <span data-ttu-id="934b8-347">このコマンドは、DNS の変更が反映されるまで正しく機能しません。</span><span class="sxs-lookup"><span data-stu-id="934b8-347">The command will not work until the DNS changes have propagated.</span></span>

<span data-ttu-id="934b8-348">ブラウザーを開いてカスタム ドメインにアクセスし、Azure 上にデプロイされているアプリへと解決されることを確かめましょう。</span><span class="sxs-lookup"><span data-stu-id="934b8-348">Open a browser and navigate to your custom domain to see that it now resolves to your deployed app on Azure.</span></span>

## <a name="scaling-up-and-out"></a><span data-ttu-id="934b8-349">スケールアップとスケールアウト</span><span class="sxs-lookup"><span data-stu-id="934b8-349">Scaling up and out</span></span>

<span data-ttu-id="934b8-350">将来的に Web アプリの利用者が増えてくると、割り当て済みのリソース (CPU と RAM) では、運用上の需要やトラフィックの増大に追い付かなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="934b8-350">At some point, your web app may become popular enough that its allocated resources (CPU and RAM) aren't sufficient for handling the increase in traffic and operational demands.</span></span> <span data-ttu-id="934b8-351">先ほど作成した App Service プラン (**B1**) で利用できるのは 1 CPU コアと 1.75 GB の RAM であり、これではかなり早い段階で処理能力の限界に達すると考えられます。</span><span class="sxs-lookup"><span data-stu-id="934b8-351">The App Service Plan that you created earlier (**B1**) comes with 1 CPU core and 1.75 GB of RAM, which can get maxed out fairly quickly.</span></span> <span data-ttu-id="934b8-352">**B2** プランであれば、その 2 倍の RAM と CPU が利用できます。アプリのリソースが不足し始めていると感じたら、次のコマンドを実行して、基になる仮想マシンをスケールアップしてください。</span><span class="sxs-lookup"><span data-stu-id="934b8-352">The **B2** plan come swith twice as much RAM and CPU, so if you notice that your app is beginning to run out of either, you can scale up the underlying virtual machine by running the following command:</span></span>

```shell
az appservice plan update -n nina-demo-plan --sku B2
```

> [!NOTE]
> <span data-ttu-id="934b8-353">Azure アプリ プランの料金の詳細と仕様については、記事「[App Service の価格](https://azure.microsoft.com/pricing/details/app-service/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="934b8-353">For Azure App Plan pricing details and specs, see the article, [App Service Pricing](https://azure.microsoft.com/pricing/details/app-service/)</span></span>

<span data-ttu-id="934b8-354">少しすると、要求したハードウェアに Web アプリが移行され、そのリソースを活用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="934b8-354">After just a few moments, your web app will be migrated to the requested hardware, and can begin taking advantage of the associated resources.</span></span> <span data-ttu-id="934b8-355">スケールアップだけではありません。より少ないリソースをより低価格で利用できる `--sku` オプションを指定して、先ほどと同じコマンドを実行すれば、スケールダウンすることもできます。</span><span class="sxs-lookup"><span data-stu-id="934b8-355">In addition to scaling up, you can also scale down by running the same command as above, specifying a `--sku` option that provides less resources at a lower price.</span></span> 

<span data-ttu-id="934b8-356">また、仮想マシンの仕様をスケールアップする以外にも、Web アプリがステートレスであれば、基になる仮想マシン インスタンスを増やすことによる "*スケールアウト*" を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="934b8-356">In addition to scaling up the virtual machine specs, as long as your web app is stateless, you also have the option to *scale out* by adding more underlying virtual machine instances.</span></span> <span data-ttu-id="934b8-357">先ほど作成した App Service プランには仮想マシンが 1 つ (*worker*) しか含まれていないので、結局のところ、その 1 つのインスタンスで利用できるリソースの上限が、全受信トラフィックの限界となります。</span><span class="sxs-lookup"><span data-stu-id="934b8-357">The App Service Plan you created earlier included only a single virtual machine (a *worker*), and therefore, all incoming traffic is ultimately bound by the limits of the available resources of that one instance.</span></span> <span data-ttu-id="934b8-358">仮想マシン インスタンスをもう 1 つ追加する必要がある場合も、先ほどと同じコマンドを使用できます。ただし、SKU をスケールアップするのではなく、worker 仮想マシンの数をスケールアウトします。</span><span class="sxs-lookup"><span data-stu-id="934b8-358">If you want to add a second virtual machine instance, you could run the same command you ran earlier, but instead of scaling up the SKU, you scale out the number of worker virtual machines.</span></span>

```shell
az appservice plan update -n nina-demo-plan --number-of-workers 2
```

<span data-ttu-id="934b8-359">このように Web アプリをスケールアウトすると、すべてのインスタンス間で受信トラフィックが透過的に負荷分散されるので、コードに変更を加えたり必要なインフラストラクチャについて心配したりすることなく、キャパシティをすぐに増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-359">When you scale out a web app like this, incoming traffic will be transparently load balanced between all instances, which allows you to immediately increase your capacity without any code changes or worrying about the needed infrastructure.</span></span> 

<span data-ttu-id="934b8-360">Web アプリはステートレスにすることをお勧めします。正常に機能するうえで必要な状態が、どれか 1 つの仮想マシンまたはアプリ インスタンスに格納されることがないため、そのときの状況に合わせて自在にスケーリング (スケールアップ、スケールダウン、スケールアウト) を行えます。</span><span class="sxs-lookup"><span data-stu-id="934b8-360">Stateless web apps are considered a best practice as they make the ability to scale them (up, down, out) entirely deterministic as no single virtual machine or app instance includes state that is neccessary in order to function.</span></span> 

> [!NOTE]
> <span data-ttu-id="934b8-361">このトピックのチュートリアルでは、App Service プランで実行する Web アプリは 1 つだけですが、同じプランに複数の Web アプリを作成してデプロイすることもできます。そうすれば、プロビジョニングと料金の支払い対象を 1 つのプランにまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-361">While this topic's tutorial illustrates running a single web app as part of an App Service Plan, you can create and deploy multiple web apps into the same plan, allowing you to provision and pay for a single plan.</span></span> 

## <a name="clean-up"></a><span data-ttu-id="934b8-362">クリーンアップ</span><span class="sxs-lookup"><span data-stu-id="934b8-362">Clean-up</span></span>

<span data-ttu-id="934b8-363">使用しない Azure リソースに対して料金が請求されないように、Visual Studio Code ターミナルで次のコマンドを実行して、このチュートリアルでプロビジョニングしたリソースをすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="934b8-363">To ensure that you don't get charged for any Azure resources you aren't using, run the following command from your Visual Studio Code terminal to delete all of the resources provisioned during this tutorial.</span></span>

```shell
az group delete
```

> [!NOTE]
> <span data-ttu-id="934b8-364">クリーンアップ プロセスは、完了までに数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="934b8-364">The clean-up process can take several minutes to complete.</span></span> 

<span data-ttu-id="934b8-365">完了後、`az group delete` コマンドを実行することで、チュートリアルを開始する前の状態に Azure アカウントを戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="934b8-365">Once finished, the `az group delete` command leaves your Azure account in the same state it was before you started the tutorial.</span></span> <span data-ttu-id="934b8-366">複数の Azure リソースを 1 つの単位にまとめ、デプロイし、削除できるのは、リソース グループの大きな利点です。</span><span class="sxs-lookup"><span data-stu-id="934b8-366">The ability to organize, deploy, and delete Azure resources as a single unit is one of the primary benefits of resource groups.</span></span> <span data-ttu-id="934b8-367">そのため、使用期間が同じであると考えられるリソースは、グループ化することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="934b8-367">Therefore, as a recommended practice,  you should group your resources together that you anticipate having the same lifespan.</span></span>