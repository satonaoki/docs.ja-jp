---
title: "方法 : アセンブリの内容を表示する"
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
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3583e69e90080eb830bb61a5e0c7b6e944f7d654
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="7995e-102">方法 : アセンブリの内容を表示する</span><span class="sxs-lookup"><span data-stu-id="7995e-102">How to: View Assembly Contents</span></span>
<span data-ttu-id="7995e-103">[Ildasm.exe (IL 逆アセンブラー)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) を使用して、ファイル内の MSIL (Microsoft Intermediate Language) 情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="7995e-103">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="7995e-104">内容を調べる対象のファイルがアセンブリの場合、この情報にはアセンブリの属性と共に他のモジュールやアセンブリへの参照が含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="7995e-104">If the file being examined is an assembly, this information can include the assembly's attributes, as well as references to other modules and assemblies.</span></span> <span data-ttu-id="7995e-105">この情報は、ファイルがアセンブリまたはアセンブリの一部かどうか、およびファイルに他のモジュールまたはアセンブリへの参照があるかどうかを判断するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7995e-105">This information can be helpful in determining whether a file is an assembly or part of an assembly, and whether the file has references to other modules or assemblies.</span></span>  
  
### <a name="to-display-the-contents-of-an-assembly-using-ildasmexe"></a><span data-ttu-id="7995e-106">Ildasm.exe を使用してアセンブリの内容を表示するには</span><span class="sxs-lookup"><span data-stu-id="7995e-106">To display the contents of an assembly using Ildasm.exe</span></span>  
  
1.  <span data-ttu-id="7995e-107">コマンド プロンプトに「**ildasm** \<*assembly name*>」と入力します。</span><span class="sxs-lookup"><span data-stu-id="7995e-107">Type **ildasm** \<*assembly name*> at the command prompt.</span></span> <span data-ttu-id="7995e-108">たとえば、次のコマンドでは、`Hello.exe` アセンブリが逆アセンブルされます。</span><span class="sxs-lookup"><span data-stu-id="7995e-108">For example, the following command disassembles the `Hello.exe` assembly.</span></span>  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### <a name="to-view-assembly-manifest-information"></a><span data-ttu-id="7995e-109">アセンブリ マニフェストの情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="7995e-109">To view assembly manifest information</span></span>  
  
1.  <span data-ttu-id="7995e-110">MSIL 逆アセンブラー ウィンドウで、マニフェストのアイコンをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="7995e-110">Double-click the MANIFEST icon in the MSIL Disassembler window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7995e-111">例</span><span class="sxs-lookup"><span data-stu-id="7995e-111">Example</span></span>  
 <span data-ttu-id="7995e-112">次の例では、基本の "Hello, World" プログラムを使用します。</span><span class="sxs-lookup"><span data-stu-id="7995e-112">The following example starts with a basic "Hello, World" program.</span></span> <span data-ttu-id="7995e-113">プログラムをコンパイルした後、Ildasm.exe を使用して Hello.exe アセンブリを逆アセンブルし、アセンブリ マニフェストを表示します。</span><span class="sxs-lookup"><span data-stu-id="7995e-113">After compiling the program, use Ildasm.exe to disassemble the Hello.exe assembly and view the assembly manifest.</span></span>  
  
 <span data-ttu-id="7995e-114">[!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)] [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)] [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="7995e-114">[!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)] [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)] [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]</span></span>  
  
 <span data-ttu-id="7995e-115">Hello.exe アセンブリに対して ildasm.exe コマンドを実行し、IL DASM ウィンドウでマニフェストのアイコンをダブルクリックすると、次の内容が出力されます。</span><span class="sxs-lookup"><span data-stu-id="7995e-115">Running the command ildasm.exe on the Hello.exe assembly and double-clicking the MANIFEST icon in the IL DASM window produces the following output:</span></span>  
  
```  
// Metadata version: v4.0.30319  
.assembly extern mscorlib  
{  
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..  
  .ver 4:0:0:0  
}  
.assembly Hello  
{  
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )   
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx  
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.  
  .hash algorithm 0x00008004  
  .ver 0:0:0:0  
}  
.module Hello.exe  
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}  
.imagebase 0x00400000  
.file alignment 0x00000200  
.stackreserve 0x00100000  
.subsystem 0x0003       // WINDOWS_CUI  
.corflags 0x00000001    //  ILONLY  
// Image base: 0x00600000  
```  
  
 <span data-ttu-id="7995e-116">次の表は、例で使用した Hello.exe アセンブリのアセンブリ マニフェストにある各ディレクティブの説明です。</span><span class="sxs-lookup"><span data-stu-id="7995e-116">The following table describes each directive in the assembly manifest of the Hello.exe assembly used in the example.</span></span>  
  
|<span data-ttu-id="7995e-117">ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="7995e-117">Directive</span></span>|<span data-ttu-id="7995e-118">説明</span><span class="sxs-lookup"><span data-stu-id="7995e-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7995e-119">**.assembly extern \<** *assembly name* **>**</span><span class="sxs-lookup"><span data-stu-id="7995e-119">**.assembly extern \<** *assembly name* **>**</span></span>|<span data-ttu-id="7995e-120">現在のモジュールによって参照される項目を含む別のアセンブリを指定します (この例では `mscorlib`)。</span><span class="sxs-lookup"><span data-stu-id="7995e-120">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|  
|<span data-ttu-id="7995e-121">**.publickeytoken \<** *token* **>**</span><span class="sxs-lookup"><span data-stu-id="7995e-121">**.publickeytoken \<** *token* **>**</span></span>|<span data-ttu-id="7995e-122">参照されるアセンブリの実際のキーのトークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="7995e-122">Specifies the token of the actual key of the referenced assembly.</span></span>|  
|<span data-ttu-id="7995e-123">**.ver \<** *version number* **>**</span><span class="sxs-lookup"><span data-stu-id="7995e-123">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="7995e-124">参照されるアセンブリのバージョン番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="7995e-124">Specifies the version number of the referenced assembly.</span></span>|  
|<span data-ttu-id="7995e-125">**.assembly \<** *assembly name* **>**</span><span class="sxs-lookup"><span data-stu-id="7995e-125">**.assembly \<** *assembly name* **>**</span></span>|<span data-ttu-id="7995e-126">アセンブリ名を指定します。</span><span class="sxs-lookup"><span data-stu-id="7995e-126">Specifies the assembly name.</span></span>|  
|<span data-ttu-id="7995e-127">**.hash algorithm \<** *int32 value* **>**</span><span class="sxs-lookup"><span data-stu-id="7995e-127">**.hash algorithm \<** *int32 value* **>**</span></span>|<span data-ttu-id="7995e-128">使用されるハッシュ アルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="7995e-128">Specifies the hash algorithm used.</span></span>|  
|<span data-ttu-id="7995e-129">**.ver \<** *version number* **>**</span><span class="sxs-lookup"><span data-stu-id="7995e-129">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="7995e-130">アセンブリのバージョン番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="7995e-130">Specifies the version number of the assembly.</span></span>|  
|<span data-ttu-id="7995e-131">**.module \<** *file name* **>**</span><span class="sxs-lookup"><span data-stu-id="7995e-131">**.module \<** *file name* **>**</span></span>|<span data-ttu-id="7995e-132">アセンブリを構成するモジュールの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7995e-132">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="7995e-133">この例では、アセンブリは 1 つのファイルだけで構成されています。</span><span class="sxs-lookup"><span data-stu-id="7995e-133">In this example, the assembly consists of only one file.</span></span>|  
|<span data-ttu-id="7995e-134">**.subsystem \<** *value* **>**</span><span class="sxs-lookup"><span data-stu-id="7995e-134">**.subsystem \<** *value* **>**</span></span>|<span data-ttu-id="7995e-135">プログラムに必要なアプリケーション環境を指定します。</span><span class="sxs-lookup"><span data-stu-id="7995e-135">Specifies the application environment required for the program.</span></span> <span data-ttu-id="7995e-136">この例では、値 3 は、この実行可能ファイルがコンソールで実行されることを示します。</span><span class="sxs-lookup"><span data-stu-id="7995e-136">In this example, the value 3 indicates that this executable is run from a console.</span></span>|  
|<span data-ttu-id="7995e-137">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="7995e-137">**.corflags**</span></span>|<span data-ttu-id="7995e-138">現在メタデータ内で予約済みのフィールドです。</span><span class="sxs-lookup"><span data-stu-id="7995e-138">Currently a reserved field in the metadata.</span></span>|  
  
 <span data-ttu-id="7995e-139">アセンブリ マニフェストは、アセンブリの内容に応じて、多くの異なるディレクティブを格納できます。</span><span class="sxs-lookup"><span data-stu-id="7995e-139">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="7995e-140">アセンブリ マニフェストに含まれる多様なディレクティブの一覧については、ヨーロッパ電子計算機工業会 (ECMA: European Computer Manufacturer Association) のドキュメント、特に「Partition II: Metadata Definition and Semantics」および「Partition III: CIL Instruction Set」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7995e-140">For an extensive list of the directives in the assembly manifest, see the ECMA documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="7995e-141">ドキュメントはオンラインで入手できます。MSDN の「[ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212)」 (ECMA の C# および共通言語基盤の標準規格) と、ECMA のインターナショナル Web サイトにある「[Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7995e-141">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7995e-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="7995e-142">See Also</span></span>  
 <span data-ttu-id="7995e-143">[アプリケーション ドメインとアセンブリ](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346) </span><span class="sxs-lookup"><span data-stu-id="7995e-143">[Application Domains and Assemblies](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346) </span></span>  
 <span data-ttu-id="7995e-144">[アプリケーション ドメインとアセンブリに関する方法のトピック](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="7995e-144">[Application Domains and Assemblies How-to Topics](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md) </span></span>  
 [<span data-ttu-id="7995e-145">Ildasm.exe (IL 逆アセンブラー)</span><span class="sxs-lookup"><span data-stu-id="7995e-145">Ildasm.exe (IL Disassembler)</span></span>](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
