---
title: "Docker でホストされているマイクロサービス - C"
description: "Docker コンテナーで実行される ASP.NET Core サービスを作成する方法を学ぶ"
keywords: ".NET, .NET Core, Docker, C#, ASP.NET, マイクロサービス"
author: BillWagner
ms.author: wiwagn
ms.date: 02/03/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: csharp
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5585db33fb5020ed18c26f32ce0b63f97353d20f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="microservices-hosted-in-docker"></a><span data-ttu-id="33857-104">Docker でホストされているマイクロサービス</span><span class="sxs-lookup"><span data-stu-id="33857-104">Microservices hosted in Docker</span></span>

## <a name="introduction"></a><span data-ttu-id="33857-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="33857-105">Introduction</span></span>

<span data-ttu-id="33857-106">このチュートリアルでは、Docker コンテナーにおける ASP.NET Core マイクロサービスの構築および展開に必要な作業について説明します。</span><span class="sxs-lookup"><span data-stu-id="33857-106">This tutorial details the tasks necessary to build and deploy an ASP.NET Core microservice in a Docker container.</span></span> <span data-ttu-id="33857-107">このチュートリアルを通して、以下のことを学びます。</span><span class="sxs-lookup"><span data-stu-id="33857-107">During the course of this tutorial, you'll learn:</span></span>

* <span data-ttu-id="33857-108">Yeoman を使用して ASP.NET Core アプリケーションを生成する方法</span><span class="sxs-lookup"><span data-stu-id="33857-108">How to generate an ASP.NET Core application using Yeoman</span></span>
* <span data-ttu-id="33857-109">Docker の開発環境を作成する方法</span><span class="sxs-lookup"><span data-stu-id="33857-109">How to create a development Docker environment</span></span>
* <span data-ttu-id="33857-110">既存のイメージに基づいて Docker イメージを構築する方法</span><span class="sxs-lookup"><span data-stu-id="33857-110">How to build a Docker image based on an existing image.</span></span>
* <span data-ttu-id="33857-111">Docker コンテナーにお使いのサービスを展開する方法</span><span class="sxs-lookup"><span data-stu-id="33857-111">How to deploy your service into a Docker container.</span></span>

<span data-ttu-id="33857-112">この過程で、C# 言語の機能もいくつか説明します。</span><span class="sxs-lookup"><span data-stu-id="33857-112">Along the way, you'll also see some C# language features:</span></span>

* <span data-ttu-id="33857-113">C# オブジェクトを JSON ペイロードに変換する方法</span><span class="sxs-lookup"><span data-stu-id="33857-113">How to convert C# objects into JSON payloads.</span></span>
* <span data-ttu-id="33857-114">変更できないデータ転送オブジェクトを構築する方法</span><span class="sxs-lookup"><span data-stu-id="33857-114">How to build immutable Data Transfer Objects</span></span>
* <span data-ttu-id="33857-115">受信 HTTP 要求を処理し、HTTP 応答を生成する方法</span><span class="sxs-lookup"><span data-stu-id="33857-115">How to process incoming HTTP Requests and generate the HTTP Response</span></span>
* <span data-ttu-id="33857-116">Null 許容の値型を操作する方法</span><span class="sxs-lookup"><span data-stu-id="33857-116">How to work with nullable value types</span></span>

<span data-ttu-id="33857-117">このトピックの[サンプル アプリを表示またはダウンロード](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/WeatherMicroservice)できます。</span><span class="sxs-lookup"><span data-stu-id="33857-117">You can [view or download the sample app](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/WeatherMicroservice) for this topic.</span></span> <span data-ttu-id="33857-118">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33857-118">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="why-docker"></a><span data-ttu-id="33857-119">Docker を使用する理由</span><span class="sxs-lookup"><span data-stu-id="33857-119">Why Docker?</span></span>

<span data-ttu-id="33857-120">Docker を使うと、簡単に標準的なコンピューター イメージを作成し、データ センターやパブリック クラウドでサービスをホストすることができます。</span><span class="sxs-lookup"><span data-stu-id="33857-120">Docker makes it easy to create standard machine images to host your services in a data center, or the public cloud.</span></span> <span data-ttu-id="33857-121">Docker ではイメージを構成することができ、必要に応じてイメージを複製してアプリケーションのインストール サイズを拡大縮小することができます。</span><span class="sxs-lookup"><span data-stu-id="33857-121">Docker enables you to configure the image, and replicate it as needed to scale the installation of your application.</span></span>

<span data-ttu-id="33857-122">このチュートリアルに含まれるコードはすべて、どんな .NET Core 環境でも動作します。</span><span class="sxs-lookup"><span data-stu-id="33857-122">All the code in this tutorial will work in any .NET Core environment.</span></span>
<span data-ttu-id="33857-123">Docker インストールの追加タスクは、ASP.NET Core アプリケーションで機能します。</span><span class="sxs-lookup"><span data-stu-id="33857-123">The additional tasks for a Docker installation will work for an ASP.NET Core application.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="33857-124">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="33857-124">Prerequisites</span></span>
<span data-ttu-id="33857-125">お使いのコンピューターを、.NET Core が実行されるように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33857-125">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="33857-126">インストールの手順については、[.NET Core](https://www.microsoft.com/net/core) のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="33857-126">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="33857-127">このアプリケーションは、Windows、Ubuntu Linux、macOS または Docker コンテナーで実行できます。</span><span class="sxs-lookup"><span data-stu-id="33857-127">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="33857-128">お好みのコード エディターをインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="33857-128">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="33857-129">次の説明では、オープン ソースのクロス プラットフォーム エディターである [Visual Studio Code](https://code.visualstudio.com/) を使用しています。</span><span class="sxs-lookup"><span data-stu-id="33857-129">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="33857-130">しかし、他の使い慣れたツールを使用しても構いません。</span><span class="sxs-lookup"><span data-stu-id="33857-130">However, you can use whatever tools you are comfortable with.</span></span>

<span data-ttu-id="33857-131">Docker エンジンをインストールする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="33857-131">You'll also need to install the Docker engine.</span></span> <span data-ttu-id="33857-132">お使いのプラットフォームに関する手順については、[Docker インストールのページ](http://www.docker.com/products/docker)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33857-132">See the [Docker Installation page](http://www.docker.com/products/docker) for instructions for your platform.</span></span>
<span data-ttu-id="33857-133">Docker は、多くの Linux ディストリビューション、macOS、または Windows にインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="33857-133">Docker can be installed in many Linux distributions, macOS, or Windows.</span></span> <span data-ttu-id="33857-134">上記のページには、インストールが可能なものについてそれぞれ説明が含まれています。</span><span class="sxs-lookup"><span data-stu-id="33857-134">The page referenced above contains sections to each of the available installations.</span></span>

<span data-ttu-id="33857-135">ほとんどのコンポーネントは、パッケージ マネージャーによってインストールされます。</span><span class="sxs-lookup"><span data-stu-id="33857-135">Most components to be installed are done by a package manager.</span></span> <span data-ttu-id="33857-136">Node.js のパッケージ マネージャー `npm` がインストールしてある場合は、この手順を省略できます。</span><span class="sxs-lookup"><span data-stu-id="33857-136">If you have node.js's package manager `npm` installed you can skip this step.</span></span> <span data-ttu-id="33857-137">そうでない場合は、[nodejs.org](https://nodejs.org) から最新の Node.Js をインストールしてください。npm パッケージ マネージャーがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="33857-137">Otherwise install the latest NodeJs from [nodejs.org](https://nodejs.org) which will install the npm package manager.</span></span> 

<span data-ttu-id="33857-138">この時点で、ASP.NET Core 開発をサポートする多数のコマンド ライン ツールをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="33857-138">At this point you will need to install a number of command line tools that support ASP.NET core development.</span></span> <span data-ttu-id="33857-139">コマンドライン テンプレートでは、Yeoman、Bower、Grunt、および Gulp が使用されています。</span><span class="sxs-lookup"><span data-stu-id="33857-139">The command line templates use Yeoman, Bower, Grunt, and Gulp.</span></span> <span data-ttu-id="33857-140">それらがインストール済みであれば問題ありませんが、そうでない場合はお使いのシェルに下記のとおり入力します。</span><span class="sxs-lookup"><span data-stu-id="33857-140">If you have them installed that is good, otherwise type the following into your favorite shell:</span></span>

`npm install -g yo bower grunt-cli gulp`

<span data-ttu-id="33857-141">`-g` オプションはグローバルのインストールであることを表し、これらのツールはシステム全体で利用可能です。</span><span class="sxs-lookup"><span data-stu-id="33857-141">The `-g` option indicates that it is a global install, and those tools are available system wide.</span></span> <span data-ttu-id="33857-142">(ローカルのインストールの場合、パッケージは単一のプロジェクトでのみ利用可能になります)</span><span class="sxs-lookup"><span data-stu-id="33857-142">(A local install scopes the package to a single project).</span></span> <span data-ttu-id="33857-143">これらのコア ツールをインストールしたら、Yeoman ASP.NET テンプレート ジェネレーターをインストールします。</span><span class="sxs-lookup"><span data-stu-id="33857-143">Once you've installed those core tools, you need to install the yeoman asp.net template generators:</span></span>

`npm install -g generator-aspnet`

## <a name="create-the-application"></a><span data-ttu-id="33857-144">アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="33857-144">Create the Application</span></span>

<span data-ttu-id="33857-145">すべてのツールをインストールしたら、新しい ASP.NET Core アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="33857-145">Now that you've installed all the tools, create a new asp.net core application.</span></span> <span data-ttu-id="33857-146">コマンド ライン ジェネレーターを使用するには、お使いのシェルで、次の Yeoman コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="33857-146">To use the command line generator, execute the following yeoman command in your favorite shell:</span></span>

`yo aspnet`

<span data-ttu-id="33857-147">このコマンドでは、作成するアプリケーションの種類を選択するように求められます。</span><span class="sxs-lookup"><span data-stu-id="33857-147">This command prompts you to select what Type of application you want to create.</span></span> <span data-ttu-id="33857-148">このマイクロサービスでは、できる限り単純で軽量な Web アプリケーションを作成したいので、'空の Web アプリケーション' を選択します。</span><span class="sxs-lookup"><span data-stu-id="33857-148">For this microservice, you want the simplest, most lightweight web application possible, so select 'Empty Web Application'.</span></span> <span data-ttu-id="33857-149">テンプレートで、名前が要求されます。</span><span class="sxs-lookup"><span data-stu-id="33857-149">The template will prompt you for a name.</span></span> <span data-ttu-id="33857-150">'WeatherMicroservice' を選択します。</span><span class="sxs-lookup"><span data-stu-id="33857-150">Select 'WeatherMicroservice'.</span></span> 

<span data-ttu-id="33857-151">テンプレートによって 8 つのファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="33857-151">The template creates eight files for you:</span></span>

* <span data-ttu-id="33857-152">.gitignore。ASP.NET Core アプリケーション用にカスタマイズされたもの。</span><span class="sxs-lookup"><span data-stu-id="33857-152">A .gitignore, customized for asp.net core applications.</span></span>
* <span data-ttu-id="33857-153">Startup.cs ファイル。</span><span class="sxs-lookup"><span data-stu-id="33857-153">A Startup.cs file.</span></span> <span data-ttu-id="33857-154">このファイルには、アプリケーションの基礎が含まれています。</span><span class="sxs-lookup"><span data-stu-id="33857-154">This contains the basis of the application.</span></span>
* <span data-ttu-id="33857-155">Program.cs ファイル。</span><span class="sxs-lookup"><span data-stu-id="33857-155">A Program.cs file.</span></span> <span data-ttu-id="33857-156">このファイルには、アプリケーションのエントリ ポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="33857-156">This contains the entry point of the application.</span></span>
* <span data-ttu-id="33857-157">WeatherMicroservice.csproj ファイル。</span><span class="sxs-lookup"><span data-stu-id="33857-157">A WeatherMicroservice.csproj file.</span></span> <span data-ttu-id="33857-158">これがアプリケーションのビルド ファイルです。</span><span class="sxs-lookup"><span data-stu-id="33857-158">This is the build file for the application.</span></span>
* <span data-ttu-id="33857-159">Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="33857-159">A Dockerfile.</span></span> <span data-ttu-id="33857-160">このスクリプトによって、アプリケーションの Docker イメージが作成されます。</span><span class="sxs-lookup"><span data-stu-id="33857-160">This script creates a Docker image for the application.</span></span>
* <span data-ttu-id="33857-161">README.md。</span><span class="sxs-lookup"><span data-stu-id="33857-161">A README.md.</span></span> <span data-ttu-id="33857-162">このファイルには、他の ASP.NET Core リソースへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="33857-162">This contains links to other asp.net core resources.</span></span>
* <span data-ttu-id="33857-163">Web.config ファイル。</span><span class="sxs-lookup"><span data-stu-id="33857-163">A web.config file.</span></span> <span data-ttu-id="33857-164">このファイルには、基本的な構成情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="33857-164">This contains basic configuration information.</span></span>
* <span data-ttu-id="33857-165">Runtimeconfig.template.json ファイル。</span><span class="sxs-lookup"><span data-stu-id="33857-165">A runtimeconfig.template.json file.</span></span> <span data-ttu-id="33857-166">このファイルには、IDE で使用されるデバッグの設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="33857-166">This contains debugging settings used by IDEs.</span></span>

<span data-ttu-id="33857-167">これで、テンプレートで生成されたアプリケーションを実行できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="33857-167">Now you can run the template generated application.</span></span> <span data-ttu-id="33857-168">これはコマンド ラインから一連のツールを使用して行います。</span><span class="sxs-lookup"><span data-stu-id="33857-168">That's done using a series of tools from the command line.</span></span> <span data-ttu-id="33857-169">`dotnet` コマンドは、.NET 開発に必要なツールを実行します。</span><span class="sxs-lookup"><span data-stu-id="33857-169">The `dotnet` command runs the tools necessary for .NET development.</span></span> <span data-ttu-id="33857-170">動詞はそれぞれ、別々のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="33857-170">Each verb executes a different command</span></span>

<span data-ttu-id="33857-171">はじめに、すべての依存関係を復元します。</span><span class="sxs-lookup"><span data-stu-id="33857-171">The first step is to restore all the dependencies:</span></span>

```console
dotnet restore
```

<span data-ttu-id="33857-172">Dotnet restore では NuGet パッケージ マネージャーを使用して、必要なすべてのパッケージをアプリケーション ディレクトリにインストールします。</span><span class="sxs-lookup"><span data-stu-id="33857-172">Dotnet restore uses the NuGet package manager to install all the necessary packages into the application directory.</span></span> <span data-ttu-id="33857-173">Project.json.lock ファイルも生成します。</span><span class="sxs-lookup"><span data-stu-id="33857-173">It also generates a project.json.lock file.</span></span> <span data-ttu-id="33857-174">このファイルには、参照される各パッケージの情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="33857-174">This file contains information about each package that is referenced.</span></span> <span data-ttu-id="33857-175">すべての依存関係を復元したら、アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="33857-175">After restoring all the dependencies, you build the application:</span></span>

```console
dotnet build
```

<span data-ttu-id="33857-176">アプリケーションをビルドしたら、それをコマンドラインから実行します。</span><span class="sxs-lookup"><span data-stu-id="33857-176">And once you build the application, you run it from the command line:</span></span>

```console
dotnet run
```

<span data-ttu-id="33857-177">既定の構成では http://localhost:5000 がリッスンされます。</span><span class="sxs-lookup"><span data-stu-id="33857-177">The default configuration listens to http://localhost:5000.</span></span> <span data-ttu-id="33857-178">ブラウザーを開いてそのページに移動すると、"Hello World!" という</span><span class="sxs-lookup"><span data-stu-id="33857-178">You can open a browser and navigate to that page and see a "Hello World!"</span></span> <span data-ttu-id="33857-179">メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="33857-179">message.</span></span>

### <a name="anatomy-of-an-aspnet-core-application"></a><span data-ttu-id="33857-180">ASP.NET Core アプリケーションの構造</span><span class="sxs-lookup"><span data-stu-id="33857-180">Anatomy of an ASP.NET Core application</span></span>

<span data-ttu-id="33857-181">アプリケーションがビルドされたので、この機能が実装される仕組みを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="33857-181">Now that you've built the application, let's look at how this functionality is implemented.</span></span> <span data-ttu-id="33857-182">生成されたファイルのうち、この時点で特に重要なのは、project.json と Startup.cs の 2 つです。</span><span class="sxs-lookup"><span data-stu-id="33857-182">There are two of the generated files that are particularly interesting at this point: project.json and Startup.cs.</span></span> 

<span data-ttu-id="33857-183">Project.json には、プロジェクトに関する情報が格納されています。</span><span class="sxs-lookup"><span data-stu-id="33857-183">Project.json contains information about the project.</span></span> <span data-ttu-id="33857-184">'dependencies' および 'frameworks' の 2 つのノードがよく使われることになります。</span><span class="sxs-lookup"><span data-stu-id="33857-184">The two nodes you'll often work with are 'dependencies' and 'frameworks'.</span></span> <span data-ttu-id="33857-185">'dependencies' ノードでは、このアプリケーションに必要なパッケージがすべて一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="33857-185">The dependencies node lists all the packages that are needed for this application.</span></span>
<span data-ttu-id="33857-186">現時点ではこれは、Web サーバーを実行するパッケージのみを必要とする小規模のノードです。</span><span class="sxs-lookup"><span data-stu-id="33857-186">At the moment, this is a small node, needing only the packages that run the web server.</span></span>

<span data-ttu-id="33857-187">'frameworks' ノードでは、このアプリケーションを実行する .NET framework のバージョンと構成が指定されます。</span><span class="sxs-lookup"><span data-stu-id="33857-187">The 'frameworks' node specifies the versions and configurations of the .NET framework that will run this application.</span></span>

<span data-ttu-id="33857-188">アプリケーションは Startup.cs に実装されます。</span><span class="sxs-lookup"><span data-stu-id="33857-188">The application is implemented in Startup.cs.</span></span> <span data-ttu-id="33857-189">このファイルにはスタートアップ クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="33857-189">This file contains the startup class.</span></span>

<span data-ttu-id="33857-190">これら 2 つのメソッドは ASP.NET Core インフラストラクチャによって呼び出され、アプリケーションを構成および実行します。</span><span class="sxs-lookup"><span data-stu-id="33857-190">The two methods are called by the asp.net core infrastructure to configure and run the application.</span></span> <span data-ttu-id="33857-191">`ConfigureServices` メソッドではこのアプリケーションに必要なサービスが記述されます。</span><span class="sxs-lookup"><span data-stu-id="33857-191">The `ConfigureServices` method describes the services that are necessary for this application.</span></span> <span data-ttu-id="33857-192">簡潔なマイクロサービスを作成するので、依存関係が構成される必要はありません。</span><span class="sxs-lookup"><span data-stu-id="33857-192">You're building a lean microservice, so it doesn't need to configure any dependencies.</span></span> <span data-ttu-id="33857-193">`Configure` メソッドでは受信 HTTP 要求のハンドラ―が構成されます。</span><span class="sxs-lookup"><span data-stu-id="33857-193">The `Configure` method configures the handlers for incoming HTTP Requests.</span></span> <span data-ttu-id="33857-194">このテンプレートでは、あらゆる要求に 'Hello World!' というテキストで応答する単純なハンドラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="33857-194">The template generates a simple handler that responds to any request with the text 'Hello World!'.</span></span>

## <a name="build-a-microservice"></a><span data-ttu-id="33857-195">マイクロサービスの構築</span><span class="sxs-lookup"><span data-stu-id="33857-195">Build a microservice</span></span>

<span data-ttu-id="33857-196">これから構築するサービスは、世界中のあらゆる場所から天気予報を提供するものです。</span><span class="sxs-lookup"><span data-stu-id="33857-196">The service you're going to build will deliver weather reports from anywhere around the globe.</span></span> <span data-ttu-id="33857-197">実際に稼働するアプリケーションでは、通常なんらかのサービスを呼び出して気象データを取得します。</span><span class="sxs-lookup"><span data-stu-id="33857-197">In a production application, you'd call some service to retrieve weather data.</span></span> <span data-ttu-id="33857-198">このサンプルでは、ランダムな天気予報を生成します。</span><span class="sxs-lookup"><span data-stu-id="33857-198">For our sample, we'll generate a random weather forecast.</span></span> 

<span data-ttu-id="33857-199">ランダムな天気予報サービスを実装するには、タスクをいくつか実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33857-199">There are a number of tasks you'll need to perform in order to implement our random weather service:</span></span>

* <span data-ttu-id="33857-200">受信要求を解析し、緯度と経度を読み取る。</span><span class="sxs-lookup"><span data-stu-id="33857-200">Parse the incoming request to read the latitude and longitude.</span></span>
* <span data-ttu-id="33857-201">ランダムな予報データを生成する。</span><span class="sxs-lookup"><span data-stu-id="33857-201">Generate some random forecast data.</span></span>
* <span data-ttu-id="33857-202">そのランダムな予報データを、C# オブジェクトから JSON パケットに変換する。</span><span class="sxs-lookup"><span data-stu-id="33857-202">Convert that random forecast data from C# objects into JSON packets.</span></span>
* <span data-ttu-id="33857-203">応答ヘッダーを設定して、サービスが JSON を送り返すことを示す。</span><span class="sxs-lookup"><span data-stu-id="33857-203">Set the response header to indicate that your service sends back JSON.</span></span>
* <span data-ttu-id="33857-204">応答を書き込む。</span><span class="sxs-lookup"><span data-stu-id="33857-204">Write the response.</span></span>

<span data-ttu-id="33857-205">以降のセクションで、これらの手順をそれぞれ順を追って説明します。</span><span class="sxs-lookup"><span data-stu-id="33857-205">The next sections walk you through each of these steps.</span></span>

### <a name="parsing-the-query-string"></a><span data-ttu-id="33857-206">クエリ文字列の解析</span><span class="sxs-lookup"><span data-stu-id="33857-206">Parsing the Query String.</span></span>

<span data-ttu-id="33857-207">クエリ文字列の解析から始めます。</span><span class="sxs-lookup"><span data-stu-id="33857-207">You'll begin by parsing the query string.</span></span> <span data-ttu-id="33857-208">サービスは、次の形式で、クエリ文字列の 'lat' 引数および 'long' 引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="33857-208">The service will accept 'lat' and 'long' arguments on the query string in this form:</span></span>

`http://localhost:5000/?lat=-35.55&long=-12.35`  

<span data-ttu-id="33857-209">変更が必要なものは、スタートアップ クラス内の `app.Run` への引数として定義されているラムダ式にすべてあります。</span><span class="sxs-lookup"><span data-stu-id="33857-209">All the changes you need to make are in the lambda expression defined as the argument to `app.Run` in your startup class.</span></span>

<span data-ttu-id="33857-210">ラムダ式の引数は、要求の `HttpContext` です。</span><span class="sxs-lookup"><span data-stu-id="33857-210">The argument on the lambda expression is the `HttpContext` for the request.</span></span> <span data-ttu-id="33857-211">そのプロパティの 1 つは `Request` オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="33857-211">One of its properties is the `Request` object.</span></span> <span data-ttu-id="33857-212">`Request` オブジェクトには `Query` プロパティが含まれており、このプロパティには、要求のクエリ文字列のすべての値のディクショナリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="33857-212">The `Request` object has a `Query` property that contains a dictionary of all the values on the query string for the request.</span></span> <span data-ttu-id="33857-213">最初に追加するのは、緯度の値と経度の値の検索です。</span><span class="sxs-lookup"><span data-stu-id="33857-213">The first addition is to find the latitude and longitude values:</span></span>

<span data-ttu-id="33857-214">[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "クエリ文字列から変数を読み取る")]</span><span class="sxs-lookup"><span data-stu-id="33857-214">[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]</span></span>

<span data-ttu-id="33857-215">クエリのディクショナリ値は `StringValue` 型です。</span><span class="sxs-lookup"><span data-stu-id="33857-215">The Query dictionary values are `StringValue` type.</span></span> <span data-ttu-id="33857-216">その型には、文字列のコレクションを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="33857-216">That type can contain a collection of strings.</span></span> <span data-ttu-id="33857-217">この天気予報サービスでは、各値は 1 つの文字列です。</span><span class="sxs-lookup"><span data-stu-id="33857-217">For your weather service, each value is a single string.</span></span> <span data-ttu-id="33857-218">そのために、上記のコードには `FirstOrDefault()` への呼び出しが含まれています。</span><span class="sxs-lookup"><span data-stu-id="33857-218">That's why there's the call to `FirstOrDefault()` in the code above.</span></span> 

<span data-ttu-id="33857-219">次に、文字列を double 型に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33857-219">Next, you need to convert the strings to doubles.</span></span> <span data-ttu-id="33857-220">文字列を double 型に変換するには `double.TryParse()` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="33857-220">The method you'll use to convert the string to a double is `double.TryParse()`:</span></span>

```csharp
bool TryParse(string s, out double result);
```

<span data-ttu-id="33857-221">このメソッドは C# の out パラメーターを活用して、入力文字列を double 型に変換できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="33857-221">This method leverages C# out parameters to indicate if the input string can be converted to a double.</span></span> <span data-ttu-id="33857-222">文字列が double 型の有効な表現を表している場合、メソッドは true を返し、`result` 引数にその値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="33857-222">If the string does represent a valid representation for a double, the method returns true, and the `result` argument contains the value.</span></span> <span data-ttu-id="33857-223">文字列が有効な double 型の値を表していない場合、メソッドは false を返します。</span><span class="sxs-lookup"><span data-stu-id="33857-223">If the string does not represent a valid double, the method returns false.</span></span>

<span data-ttu-id="33857-224">その API は、*null 許容の double 型*を返す*拡張メソッド*を使用して適応させることができます。</span><span class="sxs-lookup"><span data-stu-id="33857-224">You can adapt that API with the use of an *extension method* that returns a *nullable double*.</span></span> <span data-ttu-id="33857-225">*null 許容の値型*は、いくつかの値型を表す型で、欠落した値、すなわち null 値を保持できます。</span><span class="sxs-lookup"><span data-stu-id="33857-225">A *nullable value type* is a type that represents some value type, and can also hold a missing, or null value.</span></span> <span data-ttu-id="33857-226">null 許容型は、型宣言に `?` 文字を追加することで表されます。</span><span class="sxs-lookup"><span data-stu-id="33857-226">A nullable type is represented by appending the `?` character to the type declaration.</span></span> 

<span data-ttu-id="33857-227">拡張メソッドは静的メソッドとして定義されますが、最初のパラメーターに `this` 修飾子を追加することにより、そのクラスのメンバーとして呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="33857-227">Extension methods are methods that are defined as static methods, but by adding the `this` modifier on the first parameter, can be called as though they are members of that class.</span></span> <span data-ttu-id="33857-228">拡張メソッドは、静的クラスでのみ定義できます。</span><span class="sxs-lookup"><span data-stu-id="33857-228">Extension methods may only be defined in static classes.</span></span> <span data-ttu-id="33857-229">解析の拡張メソッドを含むクラスの定義を次に示します。</span><span class="sxs-lookup"><span data-stu-id="33857-229">Here's the definition of the class containing the extension method for parse:</span></span>

<span data-ttu-id="33857-230">[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "null 許容への解析を試行")]</span><span class="sxs-lookup"><span data-stu-id="33857-230">[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]</span></span>

<span data-ttu-id="33857-231">`default(double?)` 式は、`double?` 型の既定値を返します。</span><span class="sxs-lookup"><span data-stu-id="33857-231">The `default(double?)` expression returns the default value for the `double?` type.</span></span> <span data-ttu-id="33857-232">既定値は null 値 (値なし) です。</span><span class="sxs-lookup"><span data-stu-id="33857-232">That default value is the null (or missing) value.</span></span>

<span data-ttu-id="33857-233">この拡張メソッドを使用して、クエリ文字列の引数を double 型に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="33857-233">You can use this extension method to convert the query string arguments into the double type:</span></span>

<span data-ttu-id="33857-234">[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "try parse 拡張メソッドの使用")]</span><span class="sxs-lookup"><span data-stu-id="33857-234">[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]</span></span>

<span data-ttu-id="33857-235">解析コードを簡単にテストするために、引数の値が含まれるように応答を更新します。</span><span class="sxs-lookup"><span data-stu-id="33857-235">To easily test the parsing code, update the response to include the values of the arguments:</span></span>

<span data-ttu-id="33857-236">[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "出力応答を書き込む")]</span><span class="sxs-lookup"><span data-stu-id="33857-236">[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]</span></span>

<span data-ttu-id="33857-237">この時点で、Web アプリケーションを実行して、解析コードが機能しているかどうかを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="33857-237">At this point, you can run the web application and see if your parsing code is working.</span></span> <span data-ttu-id="33857-238">ブラウザーで Web 要求に値を追加すると、更新された結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="33857-238">Add values to the web request in a browser, and you should see the updated results.</span></span>

### <a name="build-a-random-weather-forecast"></a><span data-ttu-id="33857-239">ランダムな天気予報の構築</span><span class="sxs-lookup"><span data-stu-id="33857-239">Build a random weather forecast</span></span>

<span data-ttu-id="33857-240">次のタスクは、ランダムな天気予報の構築です。</span><span class="sxs-lookup"><span data-stu-id="33857-240">Your next task is to build a random weather forecast.</span></span> <span data-ttu-id="33857-241">天気予報に使用する値を格納するデータ コンテナーから始めましょう。</span><span class="sxs-lookup"><span data-stu-id="33857-241">Let's start with a data container that holds the values you'd want for a weather forecast:</span></span>

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions = new string[]
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HiTemperature { get; }
    public int LoTemperature { get; }
    public int AverageWindSpeed { get; }
    public string Conditions { get; }
}
```

<span data-ttu-id="33857-242">次に、これらの値をランダムに設定するコンストラクターを構築します。</span><span class="sxs-lookup"><span data-stu-id="33857-242">Next, build a constructor that randomly sets those values.</span></span> <span data-ttu-id="33857-243">このコンストラクターは、緯度と経度の値を使用して乱数ジェネレーターに値を設定します。</span><span class="sxs-lookup"><span data-stu-id="33857-243">This constructor uses the values for the latitude and longitude to seed the Random number generator.</span></span> <span data-ttu-id="33857-244">つまり同じ場所の予報は同じということになります。</span><span class="sxs-lookup"><span data-stu-id="33857-244">That means the forecast for the same location is the same.</span></span> <span data-ttu-id="33857-245">緯度と経度の引数を変更すると、異なる予報が得られます (異なる値を与えたため)。</span><span class="sxs-lookup"><span data-stu-id="33857-245">If you change the arguments for the latitude and longitude, you'll get a different forecast (because you start with a different seed.)</span></span>

<span data-ttu-id="33857-246">[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "天気予報コンストラクター")]</span><span class="sxs-lookup"><span data-stu-id="33857-246">[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]</span></span>

<span data-ttu-id="33857-247">これで、応答メソッドで 5 日間の予報を生成できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="33857-247">You can now generate the 5-day forecast in your response method:</span></span>

<span data-ttu-id="33857-248">[!code-csharp[GenerateRandomReport](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#GenerateRandomReport "ランダムな天気予報の生成")]</span><span class="sxs-lookup"><span data-stu-id="33857-248">[!code-csharp[GenerateRandomReport](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#GenerateRandomReport "Generate a random weather report")]</span></span>

### <a name="build-the-json-response"></a><span data-ttu-id="33857-249">JSON 応答の構築</span><span class="sxs-lookup"><span data-stu-id="33857-249">Build the JSON response.</span></span>

<span data-ttu-id="33857-250">サーバー上の最後のコード作業は、WeatherReport 配列を JSON パケットに変換し、それをクライアントに送信して返すことです。</span><span class="sxs-lookup"><span data-stu-id="33857-250">The final code task on the server is to convert the WeatherReport array into a JSON packet, and send that back to the client.</span></span> <span data-ttu-id="33857-251">まず JSON パケットを作成しましょう。</span><span class="sxs-lookup"><span data-stu-id="33857-251">Let's start by creating the JSON packet.</span></span> <span data-ttu-id="33857-252">NewtonSoft JSON シリアライザーを、依存関係の一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="33857-252">You'll add the NewtonSoft JSON Serializer to the list of dependencies.</span></span> <span data-ttu-id="33857-253">これは `dotnet` CLI を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="33857-253">You can do that using the `dotnet` CLI:</span></span>

```
dotnet add package Newtonsoft.Json
```

<span data-ttu-id="33857-254">すると、`JsonConvert` クラスを使用して、文字列にオブジェクトを書き込めるようになります。</span><span class="sxs-lookup"><span data-stu-id="33857-254">Then, you can use the `JsonConvert` class to write the object to a string:</span></span>

<span data-ttu-id="33857-255">[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "オブジェクトを JSON に変換")]</span><span class="sxs-lookup"><span data-stu-id="33857-255">[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]</span></span>

<span data-ttu-id="33857-256">上記のコードは、予報オブジェクト (一連の `WeatherForecast` オブジェクト) を JSON パケットに変換します。</span><span class="sxs-lookup"><span data-stu-id="33857-256">The code above converts the forecast object (a list of `WeatherForecast` objects) into a JSON packet.</span></span> <span data-ttu-id="33857-257">応答パケットを作成したら、コンテンツの種類を `application/json` に設定し、文字列を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="33857-257">After you've constructed the response packet, you set the content type to `application/json`, and write the string.</span></span>

<span data-ttu-id="33857-258">これで、アプリケーションが実行され、ランダムな予報が返されます。</span><span class="sxs-lookup"><span data-stu-id="33857-258">The application now runs and returns random forecasts.</span></span>

## <a name="build-a-docker-image"></a><span data-ttu-id="33857-259">Docker イメージの構築</span><span class="sxs-lookup"><span data-stu-id="33857-259">Build a Docker image</span></span>

<span data-ttu-id="33857-260">最後のタスクは、Docker でのアプリケーションの実行です。</span><span class="sxs-lookup"><span data-stu-id="33857-260">Our final task is to run the application in Docker.</span></span> <span data-ttu-id="33857-261">アプリケーションを表す Docker イメージを実行する Docker コンテナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="33857-261">We'll create a Docker container that runs a Docker image that represents our application.</span></span>

<span data-ttu-id="33857-262">***Docker イメージ***は、アプリケーションを実行するための環境を定義するファイルです。</span><span class="sxs-lookup"><span data-stu-id="33857-262">A ***Docker Image*** is a file that defines the environment for running the application.</span></span>

<span data-ttu-id="33857-263">***Docker コンテナー***は、Docker イメージの実行インスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="33857-263">A ***Docker Container*** represents a running instance of a Docker image.</span></span>

<span data-ttu-id="33857-264">たとえて言うと、*Docker イメージ*は*クラス*として、*Docker コンテナー*はオブジェクトまたはそのクラスのインスタンスとして、考えることができます。</span><span class="sxs-lookup"><span data-stu-id="33857-264">By analogy, you can think of the *Docker Image* as a *class*, and the *Docker Container* as an object, or an instance of that class.</span></span>  

<span data-ttu-id="33857-265">ASP.NET テンプレートで作成された Dockerfile は、ここで機能します。</span><span class="sxs-lookup"><span data-stu-id="33857-265">The Dockerfile created by the asp.net template will serve for our purposes.</span></span> <span data-ttu-id="33857-266">その内容を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="33857-266">Let's go over its contents.</span></span>

<span data-ttu-id="33857-267">最初の行はソース イメージを指定しています。</span><span class="sxs-lookup"><span data-stu-id="33857-267">The first line specifies the source image:</span></span>

```
FROM microsoft/dotnet:1.1-sdk-msbuild
```

<span data-ttu-id="33857-268">Docker では、ソース テンプレートに基づいてマシン イメージを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="33857-268">Docker allows you to configure a machine image based on a source template.</span></span> <span data-ttu-id="33857-269">つまり、開始時にすべてのマシン パラメーターを指定する必要はなく、変更箇所のみを指定すればよいことになります。</span><span class="sxs-lookup"><span data-stu-id="33857-269">That means you don't have to supply all the machine parameters when you start, you only need to supply any changes.</span></span> <span data-ttu-id="33857-270">ここでの変更は、このアプリケーションの組み込みです。</span><span class="sxs-lookup"><span data-stu-id="33857-270">The changes here will be to include our application.</span></span>

<span data-ttu-id="33857-271">この最初のサンプルでは、.Net イメージの `1.1-sdk-msbuild` バージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="33857-271">In this first sample, we'll use the `1.1-sdk-msbuild` version of the dotnet image.</span></span> <span data-ttu-id="33857-272">Docker の稼働環境を作成するにはこれが最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="33857-272">This is the easiest way to create a working Docker environment.</span></span> <span data-ttu-id="33857-273">このイメージには、.NET Core ランタイムと .Net SDK が含まれています。</span><span class="sxs-lookup"><span data-stu-id="33857-273">This image include the dotnet core runtime, and the dotnet SDK.</span></span> <span data-ttu-id="33857-274">これによって簡単にビルドを開始できますが、作成されるイメージは大きくなります。</span><span class="sxs-lookup"><span data-stu-id="33857-274">That makes it easier to get started and build, but does create a larger image.</span></span>

<span data-ttu-id="33857-275">次の 5 行のコードでは、アプリケーションが設定およびビルドされます。</span><span class="sxs-lookup"><span data-stu-id="33857-275">The next five lines setup and build your application:</span></span>

```
WORKDIR /app

# copy csproj and restore as distinct layers

COPY WeatherMicroservice.csproj .
RUN dotnet restore

# copy and build everything else

COPY . .

# RUN dotnet restore
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="33857-276">これでプロジェクト ファイルが現在のディレクトリから Docker VM にコピーされ、すべてのパッケージが復元されます。</span><span class="sxs-lookup"><span data-stu-id="33857-276">This will copy the project file from the  current directory to the docker VM, and restore all the packages.</span></span> <span data-ttu-id="33857-277">.Net CLI を使用するということは、Docker イメージに .NET Core SDK を含める必要があるということになります。</span><span class="sxs-lookup"><span data-stu-id="33857-277">Using the dotnet CLI means that the Docker image must include the .NET Core SDK.</span></span> <span data-ttu-id="33857-278">その後、アプリケーションの残りの部分がコピーされ、dotnet publish コマンドによってアプリケーションがビルドされパッケージ化されます。</span><span class="sxs-lookup"><span data-stu-id="33857-278">After that, the rest of your application gets copied, and the dotnet publish command builds and packages your application.</span></span>

<span data-ttu-id="33857-279">ファイルの最後の行で、アプリケーションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="33857-279">The final line of the file runs the application:</span></span>

```
ENTRYPOINT ["dotnet", "out/WeatherMicroservice.dll", "--server.urls", "http://0.0.0.0:5000"]
```

<span data-ttu-id="33857-280">この構成されたポートは、Dockerfile の最終行の `dotnet` への `--server.urls` 引数で参照されます。</span><span class="sxs-lookup"><span data-stu-id="33857-280">This configured port is referenced in the `--server.urls` argument to `dotnet` on the last  line of the Dockerfile.</span></span> <span data-ttu-id="33857-281">`ENTRYPOINT` コマンドは、どのコマンドとコマンド ラインのオプションによってサービスが開始されるかを、Docker に通知します。</span><span class="sxs-lookup"><span data-stu-id="33857-281">The `ENTRYPOINT` command informs Docker  what command and command line options start the service.</span></span> 

## <a name="building-and-running-the-image-in-a-container"></a><span data-ttu-id="33857-282">コンテナー内でのイメージの構築および実行</span><span class="sxs-lookup"><span data-stu-id="33857-282">Building and running the image in a container.</span></span>

<span data-ttu-id="33857-283">イメージを構築して Docker コンテナー内でサービスを実行しましょう。</span><span class="sxs-lookup"><span data-stu-id="33857-283">Let's build an image and run the service inside a Docker container.</span></span> <span data-ttu-id="33857-284">ローカル ディレクトリにあるすべてのファイルをイメージにコピーする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="33857-284">You don't want all the files from your local directory copied into the image.</span></span> <span data-ttu-id="33857-285">代わりに、コンテナーでアプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="33857-285">Instead, you'll build the application in the container.</span></span> <span data-ttu-id="33857-286">`.dockerignore` ファイルを作成して、イメージにコピーしないディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="33857-286">You'll create a `.dockerignore` file to specify the directories that are not copied into the image.</span></span> <span data-ttu-id="33857-287">ビルド資産はいっさいコピーしません。</span><span class="sxs-lookup"><span data-stu-id="33857-287">You don't want any of the build assets copied.</span></span> <span data-ttu-id="33857-288">`.dockerignore` ファイルに、ビルド ディレクトリおよび発行のディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="33857-288">Specify the build and publish directories in the `.dockerignore` file:</span></span>

```
bin/*
obj/*
out/*
```

<span data-ttu-id="33857-289">Docker のビルド コマンドを使用してイメージを作成します。</span><span class="sxs-lookup"><span data-stu-id="33857-289">You build the image using the docker build command.</span></span> <span data-ttu-id="33857-290">自分のコードが含まれているディレクトリで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="33857-290">Run the following command from the directory containing your code.</span></span>

```console
docker build -t weather-microservice .
```

<span data-ttu-id="33857-291">このコマンドは、Dockerfile 内のすべての情報を基にコンテナー イメージを作成するものです。</span><span class="sxs-lookup"><span data-stu-id="33857-291">This command builds the container image based on all the information in your Dockerfile.</span></span> <span data-ttu-id="33857-292">`-t` 引数によって、このコンテナー イメージのタグ、つまり名前が提供されます。</span><span class="sxs-lookup"><span data-stu-id="33857-292">The `-t` argument provides a tag, or name, for this container image.</span></span> <span data-ttu-id="33857-293">上記のコマンド ラインで Docker コンテナーに使用したタグは `weather-microservice` です。</span><span class="sxs-lookup"><span data-stu-id="33857-293">In the command line above, the tag used for the Docker container is `weather-microservice`.</span></span> <span data-ttu-id="33857-294">このコマンドが完了したら、新しいサービスを実行するコンテナーの準備は完了です。</span><span class="sxs-lookup"><span data-stu-id="33857-294">When this command completes, you have a container ready to run your new service.</span></span> 

<span data-ttu-id="33857-295">次のコマンドを実行して、コンテナーを起動しサービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="33857-295">Run the following command to start the container and launch your service:</span></span>

```console
docker run -d -p 80:5000 --name hello-docker weather-microservice
```

<span data-ttu-id="33857-296">`-d` オプションは、コンテナ―を現在のターミナルからデタッチして実行することを意味します。</span><span class="sxs-lookup"><span data-stu-id="33857-296">The `-d` option means to run the container detached from the current terminal.</span></span> <span data-ttu-id="33857-297">つまり、お使いの端末にはコマンドの出力は表示されないということです。</span><span class="sxs-lookup"><span data-stu-id="33857-297">That means you won't see the command output in your terminal.</span></span> <span data-ttu-id="33857-298">`-p` オプションは、サービスとホストの間のポート マッピングを示しています。</span><span class="sxs-lookup"><span data-stu-id="33857-298">The `-p` option indicates the port mapping between the service and the host.</span></span> <span data-ttu-id="33857-299">ここでは、コンテナー上でポート 80 上のすべての受信要求をポート 5000 に転送するように命令しています。</span><span class="sxs-lookup"><span data-stu-id="33857-299">Here it says that any incoming request on port 80 should be forwarded to port 5000 on the container.</span></span> <span data-ttu-id="33857-300">5000 を使用すると、上記の Dockerfile で指定されたコマンド ライン引数からサービスがリッスンしているポートと一致します。</span><span class="sxs-lookup"><span data-stu-id="33857-300">Using 5000 matches the port your service is listening on from the command line arguments specified in the Dockerfile above.</span></span> <span data-ttu-id="33857-301">`--name` 引数は実行中のコンテナーに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="33857-301">The `--name` argument names your running container.</span></span> <span data-ttu-id="33857-302">この名前は、そのコンテナーの操作に使用するのに便利です。</span><span class="sxs-lookup"><span data-stu-id="33857-302">It's a convenient name you can use to work with that container.</span></span> 

<span data-ttu-id="33857-303">次のコマンドにより、イメージが実行されているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="33857-303">You can see if the image is running by checking the command:</span></span>

```console
docker ps
```

<span data-ttu-id="33857-304">コンテナーが実行されている場合は、実行中のプロセスをリストした行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="33857-304">If your container is running, you'll see a line that lists it in the running processes.</span></span> <span data-ttu-id="33857-305">(1 つだけかもしれません。)</span><span class="sxs-lookup"><span data-stu-id="33857-305">(It may be the only one).</span></span>

<span data-ttu-id="33857-306">ブラウザーを開いて localhost に移動し、緯度と経度を指定して、サービスをテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="33857-306">You can test your service by opening a browser and navigating to localhost, and specifying a latitude and longitude:</span></span>

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a><span data-ttu-id="33857-307">実行中のコンテナーへのアタッチ</span><span class="sxs-lookup"><span data-stu-id="33857-307">Attaching to a running container</span></span>

<span data-ttu-id="33857-308">コマンド ウィンドウでサービスを実行したとき、要求ごとに診断情報が表示されました。</span><span class="sxs-lookup"><span data-stu-id="33857-308">When you ran your sevice in a command window, you could see diagnostic information printed for each request.</span></span> <span data-ttu-id="33857-309">この情報は、コンテナーがデタッチ モードで実行されているときは表示されません。</span><span class="sxs-lookup"><span data-stu-id="33857-309">You don't see that information when your container is running in detached mode.</span></span> <span data-ttu-id="33857-310">Docker の attach コマンドを使用すると、実行中のコンテナーにアタッチして、ログ情報が表示されるようにできます。</span><span class="sxs-lookup"><span data-stu-id="33857-310">The Docker attach command enables you to attach to a running container so that you can see the log information.</span></span>  <span data-ttu-id="33857-311">コマンド ウィンドウから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="33857-311">Run this command from a command window:</span></span>

```console
docker attach --sig-proxy=false hello-docker
```

<span data-ttu-id="33857-312">`--sig-proxy=false` 引数は、`Ctrl-C` コマンドがコンテナ― プロセスには送信されるのではなく、`docker attach` コマンドを停止するものであることを意味します。</span><span class="sxs-lookup"><span data-stu-id="33857-312">The `--sig-proxy=false` argument means that `Ctrl-C` commands do not get sent to the container process, but rather stop the `docker attach` command.</span></span> <span data-ttu-id="33857-313">最後の引数は、`docker run` コマンドでコンテナーに与えられた名前です。</span><span class="sxs-lookup"><span data-stu-id="33857-313">The final argument is the name given to the container in the `docker run` command.</span></span> 

> [!NOTE]
> <span data-ttu-id="33857-314">Docker が割り当てられたコンテナー ID を使用して、任意のコンテナーを参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="33857-314">You can also use the docker assigned container ID to refer to any container.</span></span> <span data-ttu-id="33857-315">`docker run` でコンテナ―に名前を指定していない場合は、コンテナ― ID を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33857-315">If you didn't specify a name for your container in `docker run` you must use the container id.</span></span>

<span data-ttu-id="33857-316">ブラウザーを開き、サービスに移動します。</span><span class="sxs-lookup"><span data-stu-id="33857-316">Open a browser and navigate to your service.</span></span> <span data-ttu-id="33857-317">アタッチされている実行中のコンテナーのコマンド ウィンドウ内で診断メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="33857-317">You'll see the diagnostic messages in the command windows from the attached running container.</span></span>

<span data-ttu-id="33857-318">`Ctrl-C` キーを押して、アタッチ プロセスを停止します。</span><span class="sxs-lookup"><span data-stu-id="33857-318">Press `Ctrl-C` to stop the attach process.</span></span>

<span data-ttu-id="33857-319">コンテナー操作を終了したら、停止することができます。</span><span class="sxs-lookup"><span data-stu-id="33857-319">When you are done working with your container, you can stop it:</span></span>

```console
docker stop hello-docker
```

<span data-ttu-id="33857-320">コンテナーとイメージは引き続き再起動できます。</span><span class="sxs-lookup"><span data-stu-id="33857-320">The container and image is still available for you to restart.</span></span>  <span data-ttu-id="33857-321">コンテナーをコンピューターから削除する場合は、このコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="33857-321">If you want to remove the container from your machine, you use this command:</span></span>

```console
docker rm hello-docker
```

<span data-ttu-id="33857-322">使用していないイメージをコンピューターから削除する場合は、このコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="33857-322">If you want to remove unused images from your machine, you use this command:</span></span>

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a><span data-ttu-id="33857-323">まとめ</span><span class="sxs-lookup"><span data-stu-id="33857-323">Conclusion</span></span> 

<span data-ttu-id="33857-324">このチュートリアルでは、ASP.NET Core マイクロサービスを構築し、単純な機能をいくつか追加しました。</span><span class="sxs-lookup"><span data-stu-id="33857-324">In this tutorial, you built an asp.net core microservice, and added a few simple features.</span></span>

<span data-ttu-id="33857-325">そのサービスの Docker コンテナー イメージを構築し、コンピューターでそのコンテナーを実行しました。</span><span class="sxs-lookup"><span data-stu-id="33857-325">You built a docker container image for that service, and ran that container on your machine.</span></span> <span data-ttu-id="33857-326">サービスにターミナル ウィンドウをアタッチし、サービスからの診断メッセージを確認しました。</span><span class="sxs-lookup"><span data-stu-id="33857-326">You attached a terminal window to the service, and saw the diagnostic messages from your service.</span></span>

<span data-ttu-id="33857-327">その流れで、C# 言語の機能のうちいくつかが実際に動作していることを確認しました。</span><span class="sxs-lookup"><span data-stu-id="33857-327">Along the way, you saw several features of the C# language in action.</span></span>
