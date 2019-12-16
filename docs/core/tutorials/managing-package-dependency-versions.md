---
title: ".NET Core 1.0 のパッケージ依存関係バージョンを管理する方法"
description: ".NET Core ライブラリとアプリにおけるパッケージの依存関係のバージョン管理について説明します。"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 4424a947-bdf9-4775-8d48-dc350a4e0aee
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7f31aeb3c07a75059a4f8cd9392dcea31eb5bf41
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a><span data-ttu-id="3bc6d-104">.NET Core 1.0 のパッケージ依存関係バージョンを管理する方法</span><span class="sxs-lookup"><span data-stu-id="3bc6d-104">How to Manage Package Dependency Versions for .NET Core 1.0</span></span>

<span data-ttu-id="3bc6d-105">この記事では、.NET Core ライブラリとアプリのパッケージ バージョンについて知っておくべき事項を説明します。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-105">This article covers what you need to know about package versions for your .NET Core libraries and apps.</span></span>

## <a name="glossary"></a><span data-ttu-id="3bc6d-106">用語集</span><span class="sxs-lookup"><span data-stu-id="3bc6d-106">Glossary</span></span>

<span data-ttu-id="3bc6d-107">**固定** - 依存関係を固定するとは、NuGet for .NET Core 1.0 でリリースされた同一 "ファミリ" のパッケージを使用することを意味します。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-107">**Fix** - Fixing dependencies means you are using the same "family" of packages released on NuGet for .NET Core 1.0.</span></span>

<span data-ttu-id="3bc6d-108">**メタパッケージ** - NuGet パッケージ セットを表す NuGet パッケージです。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-108">**Metapackage** - A NuGet package that represents a set of NuGet packages.</span></span>

<span data-ttu-id="3bc6d-109">**トリミング** - 依存しないパッケージをメタパッケージから削除する動作です。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-109">**Trimming** - The act of removing the packages you do not depend on from a metapackage.</span></span>  <span data-ttu-id="3bc6d-110">これは、NuGet パッケージの作成者に関連するものです。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-110">This is something relevant for NuGet package authors.</span></span>  <span data-ttu-id="3bc6d-111">詳細については、「[Reducing Package Dependencies with project.json](../deploying/reducing-dependencies.md)」 (project.json によるパッケージ依存関係の縮小) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-111">See [Reducing Package Dependencies with project.json](../deploying/reducing-dependencies.md) for more information.</span></span> 

## <a name="fix-your-dependencies-to-net-core-10"></a><span data-ttu-id="3bc6d-112">依存関係を .NET Core 1.0 に固定する</span><span class="sxs-lookup"><span data-stu-id="3bc6d-112">Fix your dependencies to .NET Core 1.0</span></span>

<span data-ttu-id="3bc6d-113">パッケージを確実に復元して信頼性の高いコードを記述するには、.NET Core 1.0 と共に配布されるパッケージのバージョンに依存関係を固定することが重要です。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-113">To reliably restore packages and write reliable code, it's important that you fix your dependencies to the versions of packages shipping alongside .NET Core 1.0.</span></span>  <span data-ttu-id="3bc6d-114">すなわち、どのパッケージのバージョンも、修飾子が付加されていない単一バージョンとする必要があるということです。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-114">This means every package should have a single version with no additional qualifiers.</span></span>

<span data-ttu-id="3bc6d-115">**1.0 に固定されたパッケージの例**</span><span class="sxs-lookup"><span data-stu-id="3bc6d-115">**Examples of packages fixed to 1.0**</span></span>

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

<span data-ttu-id="3bc6d-116">**1.0 に固定されていないパッケージの例**</span><span class="sxs-lookup"><span data-stu-id="3bc6d-116">**Examples of packages that are NOT fixed to 1.0**</span></span>

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a><span data-ttu-id="3bc6d-117">なぜこれが重要なのでしょうか?</span><span class="sxs-lookup"><span data-stu-id="3bc6d-117">Why does this matter?</span></span>

<span data-ttu-id="3bc6d-118">.NET Core 1.0 と共に配布されるバージョンに依存関係を固定すると、それらのパッケージはすべて確実に連携して動作します。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-118">We guarantee that if you fixed your dependencies to what ships alongside .NET Core 1.0, those packages will all work together.</span></span>  <span data-ttu-id="3bc6d-119">使用するパッケージがこのように固定されたものではない場合、パッケージの連携は保証されません。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-119">There is no such guarantee if you use packages which aren't fixed in this way.</span></span>

### <a name="scenarios"></a><span data-ttu-id="3bc6d-120">シナリオ</span><span class="sxs-lookup"><span data-stu-id="3bc6d-120">Scenarios</span></span>

<span data-ttu-id="3bc6d-121">.NET Core 1.0 でリリースされたすべてのパッケージとそのバージョンを掲載した一覧が長くても、コードが特定のシナリオに分類されている場合は、一覧を調べなくてもよい場合があります。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-121">Although there is a big list of all packages and their versions released with .NET Core 1.0, you may not have to look through it if your code falls under certain scenarios.</span></span>

<span data-ttu-id="3bc6d-122">`NETStandard.Library`**のみに依存しますか** **?**</span><span class="sxs-lookup"><span data-stu-id="3bc6d-122">**Are you depending only on** `NETStandard.Library`**?**</span></span>

<span data-ttu-id="3bc6d-123">そのようにする場合は、`NETStandard.Library` パッケージをバージョン `1.6` に固定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-123">If so, you should fixed your `NETStandard.Library` package to version `1.6`.</span></span>  <span data-ttu-id="3bc6d-124">これは選別されたメタパッケージであるため、そのパッケージ クロージャも 1.0 に固定されます。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-124">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="3bc6d-125">`Microsoft.NETCore.App`**のみに依存しますか** **?**</span><span class="sxs-lookup"><span data-stu-id="3bc6d-125">**Are you depending only on** `Microsoft.NETCore.App`**?**</span></span>

<span data-ttu-id="3bc6d-126">そのようにする場合は、`Microsoft.NETCore.App` パッケージをバージョン `1.0.0` に固定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-126">If so, you should fixed your `Microsoft.NETCore.App` package to version `1.0.0`.</span></span>  <span data-ttu-id="3bc6d-127">これは選別されたメタパッケージであるため、そのパッケージ クロージャも 1.0 に固定されます。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-127">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="3bc6d-128">**または** `Microsoft.NETCore.App` **メタパッケージ依存関係を** [トリミング](../deploying/reducing-dependencies.md) **する必要がありますか?**`NETStandard.Library`</span><span class="sxs-lookup"><span data-stu-id="3bc6d-128">**Are you [trimming](../deploying/reducing-dependencies.md) your** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackage dependencies?**</span></span>

<span data-ttu-id="3bc6d-129">そのようにする場合は、作業を開始するメタパッケージが 1.0 に固定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-129">If so, you should ensure that the metapackage you start with is fixed to 1.0.</span></span>  <span data-ttu-id="3bc6d-130">トリミングした後に依存する個々のパッケージも 1.0 に固定されます。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-130">The individual packages you depend on after trimming are also fixed to 1.0.</span></span>

<span data-ttu-id="3bc6d-131">**または** `Microsoft.NETCore.App` **メタパッケージ** **の外のパッケージに依存しますか?** `NETStandard.Library`</span><span class="sxs-lookup"><span data-stu-id="3bc6d-131">**Are you depending on packages outside the** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackages?**</span></span>

<span data-ttu-id="3bc6d-132">そのようにする場合は、ほかの依存関係を 1.0 に固定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-132">If so, you need to fix your other dependencies to 1.0.</span></span>  <span data-ttu-id="3bc6d-133">この記事の最後で、適切なパッケージ バージョンを確認し、数値をビルドします。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-133">See the correct package versions and build numbers at the end of this article.</span></span>

### <a name="a-note-on-using-a-splat-string--when-versioning"></a><span data-ttu-id="3bc6d-134">バージョン管理の際の記号文字列 (\*) の使用に関する注意事項</span><span class="sxs-lookup"><span data-stu-id="3bc6d-134">A note on using a splat string (\*) when versioning</span></span>

<span data-ttu-id="3bc6d-135">次のように、記号 (\*) 文字列を使用したバージョン管理パターンを採用している場合があるかもしれません。`"System.Collections":"4.0.11-*"`。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-135">You may have adopted a versioning pattern which uses a splat (\*) string like this: `"System.Collections":"4.0.11-*"`.</span></span>

<span data-ttu-id="3bc6d-136">**これはよくありません**。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-136">**You should not do this**.</span></span>  <span data-ttu-id="3bc6d-137">記号文字列を使用すると、さまざまなビルドからパッケージが復元される可能性があります。そのなかには、.NET Core 1.0 よりも前のものが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-137">Using the splat string could result in restoring packages from different builds, some of which may be further along than .NET Core 1.0.</span></span>  <span data-ttu-id="3bc6d-138">結果として、互換性のないパッケージが存在することになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-138">This could then result in some packages being incompatible.</span></span>

## <a name="packages-and-version-numbers-organized-by-metapackage"></a><span data-ttu-id="3bc6d-139">メタパッケージで整理されるパッケージとバージョン番号</span><span class="sxs-lookup"><span data-stu-id="3bc6d-139">Packages and Version Numbers organized by Metapackage</span></span>

<span data-ttu-id="3bc6d-140">[1.0 用の .NET Standard パッケージとそのバージョンの一覧](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt)。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-140">[List of all .NET Standard packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span></span>

<span data-ttu-id="3bc6d-141">[1.0 に対するすべてのランタイム パッケージとそのバージョンの一覧](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt)。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-141">[List of all runtime packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span></span>

<span data-ttu-id="3bc6d-142">[1.0 に対するすべての NET Core アプリケーション パッケージとそのバージョンの一覧](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt)。</span><span class="sxs-lookup"><span data-stu-id="3bc6d-142">[List of all .NET Core application packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span></span>
