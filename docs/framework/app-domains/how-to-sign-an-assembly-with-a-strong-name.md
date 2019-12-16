---
title: "方法 : 厳密な名前でアセンブリに署名する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
caps.latest.revision: 23
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7758871a22b8b58d7df5cf2df481db185c07a987
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="bead0-102">方法 : 厳密な名前でアセンブリに署名する</span><span class="sxs-lookup"><span data-stu-id="bead0-102">How to: Sign an Assembly with a Strong Name</span></span>
<span data-ttu-id="bead0-103">厳密な名前でアセンブリに署名するには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="bead0-103">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
-   <span data-ttu-id="bead0-104">Visual Studio でプロジェクトの **[プロパティ]** ダイアログ ボックスにある **[署名]** タブを使用する。</span><span class="sxs-lookup"><span data-stu-id="bead0-104">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="bead0-105">これは、厳密な名前でアセンブリに署名するための最も簡単で便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="bead0-105">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
-   <span data-ttu-id="bead0-106">[アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) を使用して、.NET Framework のコード モジュール (.netmodule ファイル) をキー ファイルにリンクする。</span><span class="sxs-lookup"><span data-stu-id="bead0-106">By using the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a .netmodule file) with a key file.</span></span>  
  
-   <span data-ttu-id="bead0-107">アセンブリ属性を使用して、厳密な名前情報をコードに挿入する。</span><span class="sxs-lookup"><span data-stu-id="bead0-107">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="bead0-108">使用するキー ファイルが配置されている場所に応じて、 <xref:System.Reflection.AssemblyKeyFileAttribute> または <xref:System.Reflection.AssemblyKeyNameAttribute> 属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bead0-108">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
-   <span data-ttu-id="bead0-109">コンパイラ オプションを使用する。</span><span class="sxs-lookup"><span data-stu-id="bead0-109">By using compiler options.</span></span>  
  
 <span data-ttu-id="bead0-110">厳密な名前でアセンブリに署名するには、暗号キー ペアが必要です。</span><span class="sxs-lookup"><span data-stu-id="bead0-110">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="bead0-111">キー ペアの作成の詳細については、「[方法: 公開キーと秘密キーのキー ペアを作成する](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bead0-111">For more information about creating a key pair, see [How to: Create a Public-Private Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="bead0-112">Visual Studio を使用してアセンブリを作成し、厳密な名前でそのアセンブリに署名するには</span><span class="sxs-lookup"><span data-stu-id="bead0-112">To create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1.  <span data-ttu-id="bead0-113">**ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、 **[プロパティ]**を選択します。</span><span class="sxs-lookup"><span data-stu-id="bead0-113">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="bead0-114">**[署名]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="bead0-114">Choose the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="bead0-115">**[アセンブリの署名]** ボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="bead0-115">Select the **Sign the assembly** box.</span></span>  
  
4.  <span data-ttu-id="bead0-116">**[厳密な名前のキー ファイルを選択してください]** ボックスで **[\<参照>]** をクリックし、キー ファイルに移動します。</span><span class="sxs-lookup"><span data-stu-id="bead0-116">In the **Choose a strong name key file** box, choose **\<Browse…>**, and then navigate to the key file.</span></span> <span data-ttu-id="bead0-117">新しいキー ファイルを作成するには、**[\<新規作成>]** を選択し、**[厳密な名前キーの作成]** ダイアログ ボックスでその名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="bead0-117">To create a new key file, choose **\<New…>** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="bead0-118">アセンブリ リンカーを使用してアセンブリを作成し、厳密な名前でそのアセンブリに署名するには</span><span class="sxs-lookup"><span data-stu-id="bead0-118">To create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
-   <span data-ttu-id="bead0-119">[Visual Studio コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)で次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="bead0-119">At the [Visual Studio Command Prompt](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="bead0-120">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span><span class="sxs-lookup"><span data-stu-id="bead0-120">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  
  
     <span data-ttu-id="bead0-121">ここで、</span><span class="sxs-lookup"><span data-stu-id="bead0-121">where:</span></span>  
  
     <span data-ttu-id="bead0-122">*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="bead0-122">*assemblyName*</span></span>  
     <span data-ttu-id="bead0-123">アセンブリ リンカーが生成する、厳密な名前で署名されたアセンブリ (.dll ファイルまたは .exe ファイル) の名前。</span><span class="sxs-lookup"><span data-stu-id="bead0-123">The name of the strongly signed assembly (a .dll or .exe file) that Assembly Linker will emit.</span></span>  
  
     <span data-ttu-id="bead0-124">*moduleName*</span><span class="sxs-lookup"><span data-stu-id="bead0-124">*moduleName*</span></span>  
     <span data-ttu-id="bead0-125">1 つ以上の型を含む、.NET Framework コード モジュール (.netmodule ファイル) の名前。</span><span class="sxs-lookup"><span data-stu-id="bead0-125">The name of a .NET Framework code module (a .netmodule file) that includes one or more types.</span></span> <span data-ttu-id="bead0-126">C# または Visual Basic で `/target:module` スイッチを使ってコードをコンパイルすることにより、.netmodule ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="bead0-126">You can create a .netmodule file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>  
  
     <span data-ttu-id="bead0-127">*keyfileName*</span><span class="sxs-lookup"><span data-stu-id="bead0-127">*keyfileName*</span></span>  
     <span data-ttu-id="bead0-128">キー ペアを格納しているコンテナーまたはファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="bead0-128">The name of the container or file that contains the key pair.</span></span> <span data-ttu-id="bead0-129">アセンブリ リンカーは、関係の相対パスを現在のディレクトリとして解釈します。</span><span class="sxs-lookup"><span data-stu-id="bead0-129">Assembly Linker interprets a relative path in relationship to the current directory.</span></span>  
  
 <span data-ttu-id="bead0-130">次の例は、キー ファイル `MyAssembly.dll` を使用して厳密な名前でアセンブリ `sgKey.snk`に署名します。</span><span class="sxs-lookup"><span data-stu-id="bead0-130">The following example signs the assembly `MyAssembly.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 <span data-ttu-id="bead0-131">このツールの詳細については、「 [アセンブリ リカー](../../../docs/framework/tools/al-exe-assembly-linker.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bead0-131">For more information about this tool, see [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="bead0-132">属性を使用して厳密な名前でアセンブリに署名するには</span><span class="sxs-lookup"><span data-stu-id="bead0-132">To sign an assembly with a strong name by using attributes</span></span>  
  
1.  <span data-ttu-id="bead0-133"><xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> または <xref:System.Reflection.AssemblyKeyNameAttribute> 属性をソース コード ファイルに追加して、厳密な名前でアセンブリに署名するときに使用するキー ペアを格納するファイルまたはコンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="bead0-133">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  
  
2.  <span data-ttu-id="bead0-134">ソース コード ファイルを通常どおりにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="bead0-134">Compile the source code file normally.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bead0-135">C# および Visual Basic コンパイラは、ソース コードで <xref:System.Reflection.AssemblyKeyFileAttribute> または <xref:System.Reflection.AssemblyKeyNameAttribute> 属性が見つかった場合、コンパイラ警告を発行します (CS1699 と BC41008)。</span><span class="sxs-lookup"><span data-stu-id="bead0-135">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="bead0-136">この警告は無視してかまいません。</span><span class="sxs-lookup"><span data-stu-id="bead0-136">You can ignore the warnings.</span></span>  
  
 <span data-ttu-id="bead0-137">次の例は、<xref:System.Reflection.AssemblyKeyFileAttribute> という名前のキー ファイルを指定して、`keyfile.snk` 属性を使用します。このキー ファイルは、アセンブリがコンパイルされるディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="bead0-137">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called `keyfile.snk`, which is located in the directory where the assembly is compiled.</span></span>  
  
 <span data-ttu-id="bead0-138">[!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)] [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)] [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]</span><span class="sxs-lookup"><span data-stu-id="bead0-138">[!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)] [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)] [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]</span></span>  
  
 <span data-ttu-id="bead0-139">ソース ファイルのコンパイル時に、アセンブリに遅延署名することもできます。</span><span class="sxs-lookup"><span data-stu-id="bead0-139">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="bead0-140">詳細については、「 [アセンブリへの遅延署名](../../../docs/framework/app-domains/delay-sign-assembly.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bead0-140">For more information, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="bead0-141">コンパイラを使用して厳密な名前でアセンブリに署名するには</span><span class="sxs-lookup"><span data-stu-id="bead0-141">To sign an assembly with a strong name by using the compiler</span></span>  
  
-   <span data-ttu-id="bead0-142">C# と Visual Basic では `/keyfile` または `/delaysign` コンパイラ オプションを使用し、C++ では `/KEYFILE` または `/DELAYSIGN` リンカー オプションを使用して、ソース コード ファイルをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="bead0-142">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="bead0-143">オプション名の後に、コロンと、キー ファイルの名前を追加します。</span><span class="sxs-lookup"><span data-stu-id="bead0-143">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="bead0-144">コマンド ライン コンパイラを使用する場合は、ソース コード ファイルを格納するディレクトリにキー ファイルをコピーできます。</span><span class="sxs-lookup"><span data-stu-id="bead0-144">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  
  
     <span data-ttu-id="bead0-145">遅延署名については、「 [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bead0-145">For information on delay signing, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
     <span data-ttu-id="bead0-146">次の例は、C# コンパイラを使用し、アセンブリ `UtilityLibrary.dll` にキー ファイル `sgKey.snk` を使用して厳密な名前で署名します。</span><span class="sxs-lookup"><span data-stu-id="bead0-146">The following example uses the C# compiler and signs the assembly `UtilityLibrary.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bead0-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="bead0-147">See Also</span></span>  
 <span data-ttu-id="bead0-148">[厳密な名前付きアセンブリの作成と使用](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="bead0-148">[Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md) </span></span>  
 <span data-ttu-id="bead0-149">[方法 : 公開キーと秘密キーのキー ペアを作成する](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md) </span><span class="sxs-lookup"><span data-stu-id="bead0-149">[How to: Create a Public-Private Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md) </span></span>  
 <span data-ttu-id="bead0-150">[Al.exe (アセンブリ リンカー)](../../../docs/framework/tools/al-exe-assembly-linker.md) </span><span class="sxs-lookup"><span data-stu-id="bead0-150">[Al.exe (Assembly Linker)](../../../docs/framework/tools/al-exe-assembly-linker.md) </span></span>  
 <span data-ttu-id="bead0-151">[アセンブリへの遅延署名](../../../docs/framework/app-domains/delay-sign-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="bead0-151">[Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md) </span></span>  
 <span data-ttu-id="bead0-152">[アセンブリおよびマニフェストへの署名の管理](/visualstudio/ide/managing-assembly-and-manifest-signing) </span><span class="sxs-lookup"><span data-stu-id="bead0-152">[Managing Assembly and Manifest Signing](/visualstudio/ide/managing-assembly-and-manifest-signing) </span></span>  
 <span data-ttu-id="bead0-153">[[署名] ページ (プロジェクト デザイナー)](https://msdn.microsoft.com/library/0k50fs3b)</span><span class="sxs-lookup"><span data-stu-id="bead0-153">[Signing Page, Project Designer](https://msdn.microsoft.com/library/0k50fs3b)</span></span>
