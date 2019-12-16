---
title: "アセンブリとグローバル アセンブリ キャッシュ (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2b98bd872bfdcbebb34fff3d878b92f39e27bbe0
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="assemblies-and-the-global-assembly-cache-c"></a><span data-ttu-id="bbd41-102">アセンブリとグローバル アセンブリ キャッシュ (C#)</span><span class="sxs-lookup"><span data-stu-id="bbd41-102">Assemblies and the Global Assembly Cache (C#)</span></span>
<span data-ttu-id="bbd41-103">アセンブリは、.NET ベースのアプリケーションの配置、バージョン管理、再利用、アクティベーション スコープ、およびセキュリティ権限の基本単位です。</span><span class="sxs-lookup"><span data-stu-id="bbd41-103">Assemblies form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions for a .NET-based application.</span></span> <span data-ttu-id="bbd41-104">アセンブリは、実行可能 (.exe) ファイルまたはダイナミック リンク ライブラリ (.dll) ファイルの形を取る、.NET Framework の構成要素です。</span><span class="sxs-lookup"><span data-stu-id="bbd41-104">Assemblies take the form of an executable (.exe) file or dynamic link library (.dll) file, and are the building blocks of the .NET Framework.</span></span> <span data-ttu-id="bbd41-105">それらは、型の実装に関して必要な情報を共通言語ランタイムに提供します。</span><span class="sxs-lookup"><span data-stu-id="bbd41-105">They provide the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="bbd41-106">アセンブリは、機能的な論理的な単位を形成し、連携して動作するように構築された、型とリソースのコレクションと考えることができます。</span><span class="sxs-lookup"><span data-stu-id="bbd41-106">You can think of an assembly as a collection of types and resources that form a logical unit of functionality and are built to work together.</span></span>  
  
 <span data-ttu-id="bbd41-107">アセンブリには、1 つまたは複数のモジュールを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="bbd41-107">Assemblies can contain one or more modules.</span></span> <span data-ttu-id="bbd41-108">たとえば、大規模なプロジェクトを、複数の開発者が別々のモジュールで作業し、すべてのモジュールをまとめて 1 つのアセンブリを作成するように計画することができます。</span><span class="sxs-lookup"><span data-stu-id="bbd41-108">For example, larger projects may be planned in such a way that several individual developers work on separate modules, all coming together to create a single assembly.</span></span> <span data-ttu-id="bbd41-109">モジュールの詳細については、「[方法: マルチファイル アセンブリをビルドする](https://msdn.microsoft.com/library/226t7yxe)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbd41-109">For more information about modules, see the topic [How to: Build a Multifile Assembly](https://msdn.microsoft.com/library/226t7yxe).</span></span>  
  
 <span data-ttu-id="bbd41-110">アセンブリには、次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="bbd41-110">Assemblies have the following properties:</span></span>  
  
-   <span data-ttu-id="bbd41-111">アセンブリは、.exe または .dll ファイルとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="bbd41-111">Assemblies are implemented as .exe or .dll files.</span></span>  
  
-   <span data-ttu-id="bbd41-112">アセンブリは、グローバル アセンブリ キャッシュに配置することで、アプリケーション間で共有することができます。</span><span class="sxs-lookup"><span data-stu-id="bbd41-112">You can share an assembly between applications by putting it in the global assembly cache.</span></span> <span data-ttu-id="bbd41-113">グローバル アセンブリ キャッシュに含める前に、アセンブリに厳密な名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbd41-113">Assemblies must be strong-named before they can be included in the global assembly cache.</span></span> <span data-ttu-id="bbd41-114">詳細については、「[厳密な名前付きアセンブリ](https://msdn.microsoft.com/library/wd40t7ad)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbd41-114">For more information, see [Strong-Named Assemblies](https://msdn.microsoft.com/library/wd40t7ad).</span></span>  
  
-   <span data-ttu-id="bbd41-115">アセンブリは、必要な場合にのみメモリに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="bbd41-115">Assemblies are only loaded into memory if they are required.</span></span> <span data-ttu-id="bbd41-116">使用されない場合、読み込まれることはありません。</span><span class="sxs-lookup"><span data-stu-id="bbd41-116">If they are not used, they are not loaded.</span></span> <span data-ttu-id="bbd41-117">これは、アセンブリを使用すると、大規模なプロジェクト内のリソースを効率的に管理できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="bbd41-117">This means that assemblies can be an efficient way to manage resources in larger projects.</span></span>  
  
-   <span data-ttu-id="bbd41-118">リフレクションを使用して、アセンブリに関する情報をプログラムによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="bbd41-118">You can programmatically obtain information about an assembly by using reflection.</span></span> <span data-ttu-id="bbd41-119">詳細については、「[リフレクション (C#)](../../../../csharp/programming-guide/concepts/reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbd41-119">For more information, see [Reflection (C#)](../../../../csharp/programming-guide/concepts/reflection.md).</span></span>  
  
-   <span data-ttu-id="bbd41-120">アセンブリのみを読み込んで検査する場合は、<xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> などのメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="bbd41-120">If you want to load an assembly only to inspect it, use a method such as <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.</span></span>  
  
## <a name="assembly-manifest"></a><span data-ttu-id="bbd41-121">アセンブリ マニフェスト</span><span class="sxs-lookup"><span data-stu-id="bbd41-121">Assembly Manifest</span></span>  
 <span data-ttu-id="bbd41-122">すべてのアセンブリの中にあるのが "*アセンブリ マニフェスト*" です。</span><span class="sxs-lookup"><span data-stu-id="bbd41-122">Within every assembly is an *assembly manifest*.</span></span> <span data-ttu-id="bbd41-123">目次と同じように、アセンブリ マニフェストには次の項目が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bbd41-123">Similar to a table of contents, the assembly manifest contains the following:</span></span>  
  
-   <span data-ttu-id="bbd41-124">アセンブリの ID (名前とバージョン)。</span><span class="sxs-lookup"><span data-stu-id="bbd41-124">The assembly's identity (its name and version).</span></span>  
  
-   <span data-ttu-id="bbd41-125">アセンブリを構成するその他すべてのファイルについて記述するファイル テーブル。.exe または .dll ファイルが依存するアセンブリ、ビットマップ、Readme ファイルなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bbd41-125">A file table describing all the other files that make up the assembly, for example, any other assemblies you created that your .exe or .dll file relies on, or even bitmap or Readme files.</span></span>  
  
-   <span data-ttu-id="bbd41-126">"*アセンブリ参照リスト*"。これはすべての外部依存関係の一覧であり、アプリケーションが必要とする .dll ファイルやその他のファイルで、他の人物が作成している場合があるファイルです。</span><span class="sxs-lookup"><span data-stu-id="bbd41-126">An *assembly reference list*, which is a list of all external dependencies—.dlls or other files your application needs that may have been created by someone else.</span></span> <span data-ttu-id="bbd41-127">アセンブリ参照には、グローバルおよびプライベートの両方のオブジェクトへの参照が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bbd41-127">Assembly references contain references to both global and private objects.</span></span> <span data-ttu-id="bbd41-128">グローバル オブジェクトは、他のアプリケーションで使用できるグローバル アセンブリ キャッシュ内に存在します。</span><span class="sxs-lookup"><span data-stu-id="bbd41-128">Global objects reside in the global assembly cache, an area available to other applications.</span></span> <span data-ttu-id="bbd41-129">プライベート オブジェクトは、アプリケーションがインストールされているディレクトリと同じレベルまたはその下のディレクトリ内に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbd41-129">Private objects must be in a directory at either the same level as or below the directory in which your application is installed.</span></span>  
  
 <span data-ttu-id="bbd41-130">アセンブリには、コンテンツ、バージョン管理、および依存関係に関する情報が含まれているため、C# で作成するアプリケーションが、正常に機能するために Windows のレジストリ値に依存することはありません。</span><span class="sxs-lookup"><span data-stu-id="bbd41-130">Because assemblies contain information about content, versioning, and dependencies, the applications you create with C# do not rely on Windows registry values to function properly.</span></span> <span data-ttu-id="bbd41-131">アセンブリは、.dll の競合を減らし、アプリケーションの信頼性を高め、配置を容易にします。</span><span class="sxs-lookup"><span data-stu-id="bbd41-131">Assemblies reduce .dll conflicts and make your applications more reliable and easier to deploy.</span></span> <span data-ttu-id="bbd41-132">多くの場合、 NET ベースのアプリケーションは、対象のコンピュータにそのファイルをコピーするだけでインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="bbd41-132">In many cases, you can install a .NET-based application simply by copying its files to the target computer.</span></span>  
  
 <span data-ttu-id="bbd41-133">詳細については、「[アセンブリ マニフェスト](https://msdn.microsoft.com/library/1w45z383)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbd41-133">For more information see [Assembly Manifest](https://msdn.microsoft.com/library/1w45z383).</span></span>  
  
## <a name="adding-a-reference-to-an-assembly"></a><span data-ttu-id="bbd41-134">アセンブリへの参照の追加</span><span class="sxs-lookup"><span data-stu-id="bbd41-134">Adding a Reference to an Assembly</span></span>  
 <span data-ttu-id="bbd41-135">アセンブリを使用するには、アセンブリへの参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbd41-135">To use an assembly, you must add a reference to it.</span></span> <span data-ttu-id="bbd41-136">次に、[using ディレクティブ](../../../../csharp/language-reference/keywords/using-directive.md)を使用して、使用する項目の名前空間を選択します。</span><span class="sxs-lookup"><span data-stu-id="bbd41-136">Next, you use the [using directive](../../../../csharp/language-reference/keywords/using-directive.md) to choose the namespace of the items you want to use.</span></span> <span data-ttu-id="bbd41-137">アセンブリが参照されてインポートされた後、名前空間のアクセス可能なすべてのクラス、プロパティ、メソッド、およびのその他のメンバーのコードは、ソース ファイルの一部であるかのようにアプリケーションで使用することができます。</span><span class="sxs-lookup"><span data-stu-id="bbd41-137">Once an assembly is referenced and imported, all the accessible classes, properties, methods, and other members of its namespaces are available to your application as if their code were part of your source file.</span></span>  
  
 <span data-ttu-id="bbd41-138">C# では、1 つのアプリケーションで同じアセンブリの 2 つのバージョンを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="bbd41-138">In C#, you can also use two versions of the same assembly in a single application.</span></span> <span data-ttu-id="bbd41-139">詳細については、「[extern エイリアス](../../../../csharp/language-reference/keywords/extern-alias.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbd41-139">For more information, see [extern alias](../../../../csharp/language-reference/keywords/extern-alias.md).</span></span>  
  
## <a name="creating-an-assembly"></a><span data-ttu-id="bbd41-140">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="bbd41-140">Creating an Assembly</span></span>  
 <span data-ttu-id="bbd41-141">アプリケーションをコンパイルするには、**[ビルド]** メニューの **[ビルド]** をクリックするか、コマンド ライン コンパイラを使用してコマンド ラインからビルドします。</span><span class="sxs-lookup"><span data-stu-id="bbd41-141">Compile your application by clicking **Build** on the **Build** menu or by building it from the command line using the command-line compiler.</span></span> <span data-ttu-id="bbd41-142">コマンド ラインからのアセンブリのビルドの詳細については、「[csc.exe を使用したコマンド ラインからのビルド](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbd41-142">For details about building assemblies from the command line, see [Command-line Building With csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bbd41-143">Visual Studio でアセンブリをビルドするには、**[ビルド]** メニューの **[ビルド]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bbd41-143">To build an assembly in Visual Studio, on the **Build** menu choose **Build**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbd41-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbd41-144">See Also</span></span>  
 <span data-ttu-id="bbd41-145">[C# プログラミング ガイド](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="bbd41-145">[C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="bbd41-146">[共通言語ランタイムのアセンブリ](https://msdn.microsoft.com/library/k3677y81) </span><span class="sxs-lookup"><span data-stu-id="bbd41-146">[Assemblies in the Common Language Runtime](https://msdn.microsoft.com/library/k3677y81) </span></span>  
 <span data-ttu-id="bbd41-147">[フレンド アセンブリ (C++)](friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="bbd41-147">[Friend Assemblies (C#)](friend-assemblies.md) </span></span>  
 <span data-ttu-id="bbd41-148">[方法 : アセンブリを他のアプリケーションと共有する (C#)](how-to-share-an-assembly-with-other-applications.md) </span><span class="sxs-lookup"><span data-stu-id="bbd41-148">[How to: Share an Assembly with Other Applications (C#)](how-to-share-an-assembly-with-other-applications.md) </span></span>  
 <span data-ttu-id="bbd41-149">[方法: アセンブリを読み込み、アンロードする (C#)](how-to-load-and-unload-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="bbd41-149">[How to: Load and Unload Assemblies (C#)](how-to-load-and-unload-assemblies.md) </span></span>  
 <span data-ttu-id="bbd41-150">[方法: ファイルがアセンブリであるかどうかを確認する (C#)](how-to-determine-if-a-file-is-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="bbd41-150">[How to: Determine If a File Is an Assembly (C#)](how-to-determine-if-a-file-is-an-assembly.md) </span></span>  
 <span data-ttu-id="bbd41-151">[方法: コマンド ラインを使用してアセンブリを作成および使用する (C#)](how-to-create-and-use-assemblies-using-the-command-line.md) </span><span class="sxs-lookup"><span data-stu-id="bbd41-151">[How to: Create and Use Assemblies Using the Command Line (C#)](how-to-create-and-use-assemblies-using-the-command-line.md) </span></span>  
 <span data-ttu-id="bbd41-152">[チュートリアル: Visual Studio でマネージ アセンブリからの型を埋め込む (C#)](walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="bbd41-152">[Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)](walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) </span></span>  
 [<span data-ttu-id="bbd41-153">チュートリアル: Visual Studio で Microsoft Office アセンブリからの型情報を埋め込む (C#)</span><span class="sxs-lookup"><span data-stu-id="bbd41-153">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (C#)</span></span>](walkthrough-embedding-type-information-from-microsoft-office-assemblies.md)
