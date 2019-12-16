---
title: "アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: fcf78ff1-f1ab-4a5d-b6d8-00d2046b6c80
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c5a1a3a651fc7d2b42f8ac55ab6f2d832f258bb0
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="assemblies-and-the-global-assembly-cache-visual-basic"></a><span data-ttu-id="aa071-102">アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa071-102">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>
<span data-ttu-id="aa071-103">アセンブリは、.NET ベースのアプリケーションの配置、バージョン管理、再利用、アクティベーション スコープ、およびセキュリティ権限の基本単位です。</span><span class="sxs-lookup"><span data-stu-id="aa071-103">Assemblies form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions for a .NET-based application.</span></span> <span data-ttu-id="aa071-104">アセンブリは、実行可能 (.exe) ファイルまたはダイナミック リンク ライブラリ (.dll) ファイルの形を取る、.NET Framework の構成要素です。</span><span class="sxs-lookup"><span data-stu-id="aa071-104">Assemblies take the form of an executable (.exe) file or dynamic link library (.dll) file, and are the building blocks of the .NET Framework.</span></span> <span data-ttu-id="aa071-105">それらは、型の実装に関して必要な情報を共通言語ランタイムに提供します。</span><span class="sxs-lookup"><span data-stu-id="aa071-105">They provide the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="aa071-106">アセンブリは、機能的な論理的な単位を形成し、連携して動作するように構築された、型とリソースのコレクションと考えることができます。</span><span class="sxs-lookup"><span data-stu-id="aa071-106">You can think of an assembly as a collection of types and resources that form a logical unit of functionality and are built to work together.</span></span>  
  
 <span data-ttu-id="aa071-107">アセンブリには、1 つまたは複数のモジュールを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="aa071-107">Assemblies can contain one or more modules.</span></span> <span data-ttu-id="aa071-108">たとえば、大規模なプロジェクトを、複数の開発者が別々のモジュールで作業し、すべてのモジュールをまとめて 1 つのアセンブリを作成するように計画することができます。</span><span class="sxs-lookup"><span data-stu-id="aa071-108">For example, larger projects may be planned in such a way that several individual developers work on separate modules, all coming together to create a single assembly.</span></span> <span data-ttu-id="aa071-109">モジュールの詳細については、「[方法: マルチファイル アセンブリをビルドする](https://msdn.microsoft.com/library/226t7yxe)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa071-109">For more information about modules, see the topic [How to: Build a Multifile Assembly](https://msdn.microsoft.com/library/226t7yxe).</span></span>  
  
 <span data-ttu-id="aa071-110">アセンブリには、次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="aa071-110">Assemblies have the following properties:</span></span>  
  
-   <span data-ttu-id="aa071-111">アセンブリは、.exe または .dll ファイルとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="aa071-111">Assemblies are implemented as .exe or .dll files.</span></span>  
  
-   <span data-ttu-id="aa071-112">アセンブリは、グローバル アセンブリ キャッシュに配置することで、アプリケーション間で共有することができます。</span><span class="sxs-lookup"><span data-stu-id="aa071-112">You can share an assembly between applications by putting it in the global assembly cache.</span></span> <span data-ttu-id="aa071-113">グローバル アセンブリ キャッシュに含める前に、アセンブリに厳密な名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa071-113">Assemblies must be strong-named before they can be included in the global assembly cache.</span></span> <span data-ttu-id="aa071-114">詳細については、「[厳密な名前付きアセンブリ](https://msdn.microsoft.com/library/wd40t7ad)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa071-114">For more information, see [Strong-Named Assemblies](https://msdn.microsoft.com/library/wd40t7ad).</span></span>  
  
-   <span data-ttu-id="aa071-115">アセンブリは、必要な場合にのみメモリに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="aa071-115">Assemblies are only loaded into memory if they are required.</span></span> <span data-ttu-id="aa071-116">使用されない場合、読み込まれることはありません。</span><span class="sxs-lookup"><span data-stu-id="aa071-116">If they are not used, they are not loaded.</span></span> <span data-ttu-id="aa071-117">これは、アセンブリを使用すると、大規模なプロジェクト内のリソースを効率的に管理できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="aa071-117">This means that assemblies can be an efficient way to manage resources in larger projects.</span></span>  
  
-   <span data-ttu-id="aa071-118">リフレクションを使用して、アセンブリに関する情報をプログラムによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="aa071-118">You can programmatically obtain information about an assembly by using reflection.</span></span> <span data-ttu-id="aa071-119">詳細については、「[リフレクション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa071-119">For more information, see [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span></span>  
  
-   <span data-ttu-id="aa071-120">アセンブリのみを読み込んで検査する場合は、<xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> などのメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="aa071-120">If you want to load an assembly only to inspect it, use a method such as <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.</span></span>  
  
## <a name="assembly-manifest"></a><span data-ttu-id="aa071-121">アセンブリ マニフェスト</span><span class="sxs-lookup"><span data-stu-id="aa071-121">Assembly Manifest</span></span>  
 <span data-ttu-id="aa071-122">すべてのアセンブリの中にあるのが "*アセンブリ マニフェスト*" です。</span><span class="sxs-lookup"><span data-stu-id="aa071-122">Within every assembly is an *assembly manifest*.</span></span> <span data-ttu-id="aa071-123">目次と同じように、アセンブリ マニフェストには次の項目が含まれます。</span><span class="sxs-lookup"><span data-stu-id="aa071-123">Similar to a table of contents, the assembly manifest contains the following:</span></span>  
  
-   <span data-ttu-id="aa071-124">アセンブリの ID (名前とバージョン)。</span><span class="sxs-lookup"><span data-stu-id="aa071-124">The assembly's identity (its name and version).</span></span>  
  
-   <span data-ttu-id="aa071-125">アセンブリを構成するその他すべてのファイルについて記述するファイル テーブル。.exe または .dll ファイルが依存するアセンブリ、ビットマップ、Readme ファイルなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="aa071-125">A file table describing all the other files that make up the assembly, for example, any other assemblies you created that your .exe or .dll file relies on, or even bitmap or Readme files.</span></span>  
  
-   <span data-ttu-id="aa071-126">"*アセンブリ参照リスト*"。これはすべての外部依存関係の一覧であり、アプリケーションが必要とする .dll ファイルやその他のファイルで、他の人物が作成している場合があるファイルです。</span><span class="sxs-lookup"><span data-stu-id="aa071-126">An *assembly reference list*, which is a list of all external dependencies—.dlls or other files your application needs that may have been created by someone else.</span></span> <span data-ttu-id="aa071-127">アセンブリ参照には、グローバルおよびプライベートの両方のオブジェクトへの参照が含まれます。</span><span class="sxs-lookup"><span data-stu-id="aa071-127">Assembly references contain references to both global and private objects.</span></span> <span data-ttu-id="aa071-128">グローバル オブジェクトは、System32 ディレクトリのような、他のアプリケーションが使用できるグローバル アセンブリ キャッシュ内に存在します。</span><span class="sxs-lookup"><span data-stu-id="aa071-128">Global objects reside in the global assembly cache, an area available to other applications, somewhat like the System32 directory.</span></span> <span data-ttu-id="aa071-129"><xref:Microsoft.VisualBasic?displayProperty=fullName> 名前空間は、グローバル アセンブリ キャッシュ内のアセンブリの例です。</span><span class="sxs-lookup"><span data-stu-id="aa071-129">The <xref:Microsoft.VisualBasic?displayProperty=fullName> namespace is an example of an assembly in the global assembly cache.</span></span> <span data-ttu-id="aa071-130">プライベート オブジェクトは、アプリケーションがインストールされているディレクトリと同じレベルまたはその下のディレクトリ内に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa071-130">Private objects must be in a directory at either the same level as or below the directory in which your application is installed.</span></span>  
  
 <span data-ttu-id="aa071-131">アセンブリには、コンテンツ、バージョン管理、および依存関係に関する情報が含まれているため、Visual Basic で作成するアプリケーションは、正常に機能するために Windows のレジストリ値に依存するはありません。</span><span class="sxs-lookup"><span data-stu-id="aa071-131">Because assemblies contain information about content, versioning, and dependencies, the applications you create with Visual Basic do not rely on Windows registry values to function properly.</span></span> <span data-ttu-id="aa071-132">アセンブリは、.dll の競合を減らし、アプリケーションの信頼性を高め、配置を容易にします。</span><span class="sxs-lookup"><span data-stu-id="aa071-132">Assemblies reduce .dll conflicts and make your applications more reliable and easier to deploy.</span></span> <span data-ttu-id="aa071-133">多くの場合、 NET ベースのアプリケーションは、対象のコンピュータにそのファイルをコピーするだけでインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="aa071-133">In many cases, you can install a .NET-based application simply by copying its files to the target computer.</span></span>  
  
 <span data-ttu-id="aa071-134">詳細については、「[アセンブリ マニフェスト](https://msdn.microsoft.com/library/1w45z383)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa071-134">For more information see [Assembly Manifest](https://msdn.microsoft.com/library/1w45z383).</span></span>  
  
## <a name="adding-a-reference-to-an-assembly"></a><span data-ttu-id="aa071-135">アセンブリへの参照の追加</span><span class="sxs-lookup"><span data-stu-id="aa071-135">Adding a Reference to an Assembly</span></span>  
 <span data-ttu-id="aa071-136">アセンブリを使用するには、アセンブリへの参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa071-136">To use an assembly, you must add a reference to it.</span></span> <span data-ttu-id="aa071-137">次に、[Imports ステートメント](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)を使用して、使用する項目の名前空間を選択します。</span><span class="sxs-lookup"><span data-stu-id="aa071-137">Next, you use the [Imports statement](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to choose the namespace of the items you want to use.</span></span> <span data-ttu-id="aa071-138">アセンブリが参照されてインポートされた後、名前空間のアクセス可能なすべてのクラス、プロパティ、メソッド、およびのその他のメンバーのコードは、ソース ファイルの一部であるかのようにアプリケーションで使用することができます。</span><span class="sxs-lookup"><span data-stu-id="aa071-138">Once an assembly is referenced and imported, all the accessible classes, properties, methods, and other members of its namespaces are available to your application as if their code were part of your source file.</span></span>  
  
## <a name="creating-an-assembly"></a><span data-ttu-id="aa071-139">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="aa071-139">Creating an Assembly</span></span>  
 <span data-ttu-id="aa071-140">アプリケーションをコンパイルするには、コマンド ライン コンパイラを使用してコマンドラインからビルドします。</span><span class="sxs-lookup"><span data-stu-id="aa071-140">Compile your application by building it from the command line using the command-line compiler.</span></span> <span data-ttu-id="aa071-141">コマンドラインからのアセンブリのビルドの詳細については、「[コマンドラインからのビルド](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa071-141">For details about building assemblies from the command line, see [Building from the Command Line](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa071-142">Visual Studio でアセンブリをビルドするには、**[ビルド]** メニューの **[ビルド]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aa071-142">To build an assembly in Visual Studio, on the **Build** menu choose **Build**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa071-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa071-143">See Also</span></span>  
 <span data-ttu-id="aa071-144">[共通言語ランタイムのアセンブリ](https://msdn.microsoft.com/library/k3677y81) </span><span class="sxs-lookup"><span data-stu-id="aa071-144">[Assemblies in the Common Language Runtime](https://msdn.microsoft.com/library/k3677y81) </span></span>  
 <span data-ttu-id="aa071-145">[フレンド アセンブリ (Visual Basic)](friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="aa071-145">[Friend Assemblies (Visual Basic)](friend-assemblies.md) </span></span>  
 <span data-ttu-id="aa071-146">[方法: アセンブリを他のアプリケーションと共有する (Visual Basic)](how-to-share-an-assembly-with-other-applications.md) </span><span class="sxs-lookup"><span data-stu-id="aa071-146">[How to: Share an Assembly with Other Applications (Visual Basic)](how-to-share-an-assembly-with-other-applications.md) </span></span>  
 <span data-ttu-id="aa071-147">[方法: アセンブリを読み込み、アンロードする (Visual Basic)](how-to-load-and-unload-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="aa071-147">[How to: Load and Unload Assemblies (Visual Basic)](how-to-load-and-unload-assemblies.md) </span></span>  
 <span data-ttu-id="aa071-148">[方法: ファイルがアセンブリであるかどうかを確認する (Visual Basic)](how-to-determine-if-a-file-is-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="aa071-148">[How to: Determine If a File Is an Assembly (Visual Basic)](how-to-determine-if-a-file-is-an-assembly.md) </span></span>  
 <span data-ttu-id="aa071-149">[方法: コマンド ラインを使用してアセンブリを作成および使用する (Visual Basic)](how-to-create-and-use-assemblies-using-the-command-line.md) </span><span class="sxs-lookup"><span data-stu-id="aa071-149">[How to: Create and Use Assemblies Using the Command Line (Visual Basic)](how-to-create-and-use-assemblies-using-the-command-line.md) </span></span>  
 <span data-ttu-id="aa071-150">[チュートリアル: Visual Studio でマネージ アセンブリからの型を埋め込む (Visual Basic)](walkthrough-embedding-types-from-managed-assemblies-in-vs.md) </span><span class="sxs-lookup"><span data-stu-id="aa071-150">[Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)](walkthrough-embedding-types-from-managed-assemblies-in-vs.md) </span></span>  
 [<span data-ttu-id="aa071-151">チュートリアル: Visual Studio で Microsoft Office アセンブリからの型情報を埋め込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa071-151">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (Visual Basic)</span></span>](walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-vs.md)
