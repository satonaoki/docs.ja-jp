---
title: Visual Studio Code を使用して .NET Core Hello World アプリケーションを発行する
description: 発行では、.NET Core アプリケーションを実行するために必要なファイルのセットを作成します。
ms.date: 05/28/2020
ms.openlocfilehash: b49b12bf41e3ea7be8dbc459eb7d9b1fbef25790
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2020
ms.locfileid: "84246656"
---
# <a name="tutorial-publish-a-net-core-console-application-with-visual-studio-code"></a><span data-ttu-id="fa9ca-103">チュートリアル: Visual Studio Code を使用して .NET Core コンソール アプリケーションを発行する</span><span class="sxs-lookup"><span data-stu-id="fa9ca-103">Tutorial: Publish a .NET Core console application with Visual Studio Code</span></span>

<span data-ttu-id="fa9ca-104">このチュートリアルでは、他のユーザーが実行できるコンソール アプリを発行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="fa9ca-105">発行では、アプリケーションを実行するために必要なファイルのセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-105">Publishing creates the set of files that are needed to run an application.</span></span> <span data-ttu-id="fa9ca-106">ファイルを配置するには、それをターゲット マシンにコピーします。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-106">To deploy the files, copy them to the target machine.</span></span>

<span data-ttu-id="fa9ca-107">.NET Core CLI はアプリの発行に使用されるため、必要に応じて、Visual Studio Code 以外のコード エディターを使用してこのチュートリアルを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-107">The .NET Core CLI is used to publish the app, so you can follow this tutorial with a code editor other than Visual Studio Code if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fa9ca-108">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="fa9ca-108">Prerequisites</span></span>

- <span data-ttu-id="fa9ca-109">このチュートリアルでは、[Visual Studio Code での .NET Core コンソール アプリケーションの作成](with-visual-studio-code.md)に関するページで作成した、コンソール アプリを使用します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-109">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="fa9ca-110">アプリの発行</span><span class="sxs-lookup"><span data-stu-id="fa9ca-110">Publish the app</span></span>

1. <span data-ttu-id="fa9ca-111">Visual Studio Code を開きます。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-111">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="fa9ca-112">[Visual Studio Code での .NET Core コンソール アプリケーションの作成](with-visual-studio-code.md)に関する記事で作成した *HelloWorld* プロジェクト フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-112">Open the *HelloWorld* project folder that you created in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

1. <span data-ttu-id="fa9ca-113">メイン メニューから **[表示]**  >  **[ターミナル]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-113">Choose **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="fa9ca-114">*[HelloWorld]* フォルダーでターミナルが開きます。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-114">The terminal opens in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="fa9ca-115">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-115">Run the following command:</span></span>

   ```dotnetcli
   dotnet publish --configuration Release
   ```

   <span data-ttu-id="fa9ca-116">既定のビルド構成は "*デバッグ*" であるため、このコマンドでは "*リリース*" ビルド構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-116">The default build configuration is *Debug*, so this command specifies the *Release* build configuration.</span></span> <span data-ttu-id="fa9ca-117">リリース ビルド構成の出力には、最小限のシンボリック デバッグ情報が含まれており、完全に最適化されています。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-117">The output from the Release build configuration has minimal symbolic debug information and is fully optimized.</span></span>

   <span data-ttu-id="fa9ca-118">コマンドの出力は次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-118">The command output is similar to the following example:</span></span>

   ```
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

   Determining projects to restore...
   All projects are up-to-date for restore.
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\HelloWorld.dll
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

## <a name="inspect-the-files"></a><span data-ttu-id="fa9ca-119">ファイルを検査する</span><span class="sxs-lookup"><span data-stu-id="fa9ca-119">Inspect the files</span></span>

<span data-ttu-id="fa9ca-120">この発行プロセスでは、フレームワークに依存する配置が既定で作成されます。これは、.NET Core のランタイムがインストールされているコンピューターで、発行されたアプリケーションが実行される配置の種類です。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-120">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on a machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="fa9ca-121">発行されたアプリを実行するには、実行可能ファイルを使用するか、コマンド プロンプトから `dotnet HelloWorld.dll` コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-121">To run the published app you can use the executable file or run the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="fa9ca-122">次の手順で、発行プロセスによって作成されるファイルを確認します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-122">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="fa9ca-123">左側のナビゲーション バーで **[エクスプローラー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-123">Select the **Explorer** in the left navigation bar.</span></span>

1. <span data-ttu-id="fa9ca-124">*bin/Release/netcoreapp3.1/publish* を展開します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-124">Expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-code/published-files-output.png" alt-text="発行されたファイルを表示しているエクスプローラー":::

   <span data-ttu-id="fa9ca-126">この図に示すように、発行された出力には次のファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-126">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="fa9ca-127">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="fa9ca-127">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="fa9ca-128">このファイルは、アプリケーションのランタイム依存関係ファイルです。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-128">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="fa9ca-129">これは、アプリの実行に必要な .NET Core コンポーネントとライブラリ (アプリケーションが含まれる動的リンク ライブラリを含む) を定義します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-129">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="fa9ca-130">詳細については、「[ランタイム構成ファイル](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-130">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="fa9ca-131">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="fa9ca-131">*HelloWorld.dll*</span></span>

      <span data-ttu-id="fa9ca-132">これは、[フレームワークに依存する展開](../deploying/deploy-with-cli.md#framework-dependent-deployment)バージョンのアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-132">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="fa9ca-133">このダイナミック リンク ライブラリを実行するには、コマンド プロンプトで`dotnet HelloWorld.dll` を入力します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-133">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="fa9ca-134">アプリ実行のこの方法は、.NET Core ランタイムがインストールされている任意のプラットフォームで動作します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-134">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

   * <span data-ttu-id="fa9ca-135">*HelloWorld.exe* (Linux では *HelloWorld*、macOS では作成されません。)</span><span class="sxs-lookup"><span data-stu-id="fa9ca-135">*HelloWorld.exe* (*HelloWorld* on Linux, not created on macOS.)</span></span>

      <span data-ttu-id="fa9ca-136">これは、[フレームワークに依存する実行可能ファイル](../deploying/deploy-with-cli.md#framework-dependent-executable) バージョンのアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-136">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="fa9ca-137">ファイルはオペレーティング システム固有のものです。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-137">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="fa9ca-138">*HelloWorld.pdb* (配置は省略可能)</span><span class="sxs-lookup"><span data-stu-id="fa9ca-138">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="fa9ca-139">これは、デバッグ シンボル ファイルです。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-139">This is the debug symbols file.</span></span> <span data-ttu-id="fa9ca-140">このファイルはアプリケーションと一緒に配置する必要はありませんが、発行されるバージョンのアプリケーションをデバッグする必要がある場合に保存しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-140">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="fa9ca-141">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="fa9ca-141">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="fa9ca-142">これは、アプリケーションのランタイム構成ファイルです。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-142">This is the application's run-time configuration file.</span></span> <span data-ttu-id="fa9ca-143">ビルドされたアプリケーションが実行時に基盤とする .NET Core のバージョンを識別します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-143">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="fa9ca-144">構成オプションを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-144">You can also add configuration options to it.</span></span> <span data-ttu-id="fa9ca-145">詳細については、「[.NET Core ランタイム構成設定](../run-time-config/index.md#runtimeconfigjson)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-145">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="fa9ca-146">発行済みアプリを実行する</span><span class="sxs-lookup"><span data-stu-id="fa9ca-146">Run the published app</span></span>

1. <span data-ttu-id="fa9ca-147">**エクスプローラー**で、"*発行*" フォルダーを右クリックして (または、macOS では <kbd>Ctrl</kbd> キーを押しながらクリック)、 **[ターミナルで開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-147">In **Explorer**, right-click the *publish* folder (or <kbd>Ctrl</kbd>+click on macOS), and select **Open in Terminal**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-code/open-in-terminal.png" alt-text="[ターミナルで開く] を表示しているコンテキスト メニュー":::

1. <span data-ttu-id="fa9ca-149">Windows または Linux では、実行可能ファイルを使用してアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-149">On Windows or Linux, run the app by using the executable.</span></span>

   1. <span data-ttu-id="fa9ca-150">Windows では、`.\HelloWorld.exe` を入力して、<kbd>Enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-150">On Windows, enter `.\HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="fa9ca-151">Linux では、`./HelloWorld` を入力して、<kbd>Enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-151">On Linux, enter `./HelloWorld` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="fa9ca-152">プロンプトに応答して名前を入力し、任意のキーを押して終了します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-152">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="fa9ca-153">任意のプラットフォームで、[`dotnet`](../tools/dotnet.md) コマンドを使用してアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-153">On any platform, run the app by using the  [`dotnet`](../tools/dotnet.md) command:</span></span>

   1. <span data-ttu-id="fa9ca-154">「`dotnet HelloWorld.dll`」と入力して、<kbd>Enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-154">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="fa9ca-155">プロンプトに応答して名前を入力し、任意のキーを押して終了します。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-155">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="fa9ca-156">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="fa9ca-156">Additional resources</span></span>

- [<span data-ttu-id="fa9ca-157">.NET Core アプリケーションの展開</span><span class="sxs-lookup"><span data-stu-id="fa9ca-157">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="fa9ca-158">次の手順</span><span class="sxs-lookup"><span data-stu-id="fa9ca-158">Next steps</span></span>

<span data-ttu-id="fa9ca-159">このチュートリアルでは、コンソール アプリを発行しました。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-159">In this tutorial, you published a console app.</span></span> <span data-ttu-id="fa9ca-160">ライブラリを構築する方法については、「[.NET Core CLI を使用したライブラリの開発](libraries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa9ca-160">To learn how to build libraries, see [Develop libraries with the .NET Core CLI](libraries.md).</span></span>

<!--In the next tutorial, you create a class library.

> [!div class="nextstepaction"]
> [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md)
-->