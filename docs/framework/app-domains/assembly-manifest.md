---
title: "アセンブリ マニフェスト"
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
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eb20bfac6717779f5394724617d247a6dc980c7e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="assembly-manifest"></a><span data-ttu-id="1905e-102">アセンブリ マニフェスト</span><span class="sxs-lookup"><span data-stu-id="1905e-102">Assembly Manifest</span></span>
<span data-ttu-id="1905e-103">静的であるか動的であるかにかかわらず、すべてのアセンブリは、アセンブリ内の要素の相互関係を記述したデータのコレクションを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="1905e-103">Every assembly, whether static or dynamic, contains a collection of data that describes how the elements in the assembly relate to each other.</span></span> <span data-ttu-id="1905e-104">このアセンブリ メタデータは、アセンブリ マニフェストに格納されています。</span><span class="sxs-lookup"><span data-stu-id="1905e-104">The assembly manifest contains this assembly metadata.</span></span> <span data-ttu-id="1905e-105">アセンブリ マニフェストには、アセンブリのバージョン要件およびセキュリティ ID を指定するために必要なすべてのメタデータと、アセンブリのスコープを定義したり、リソースやクラスへの参照を解決したりするために必要なすべてのメタデータが格納されています。</span><span class="sxs-lookup"><span data-stu-id="1905e-105">An assembly manifest contains all the metadata needed to specify the assembly's version requirements and security identity, and all metadata needed to define the scope of the assembly and resolve references to resources and classes.</span></span> <span data-ttu-id="1905e-106">アセンブリ マニフェストは、MSIL (Microsoft Intermediate Language) コードが記述されている PE ファイル (.exe または .dll)、またはアセンブリ マニフェスト情報だけを格納したスタンドアロンの PE ファイルに保存できます。</span><span class="sxs-lookup"><span data-stu-id="1905e-106">The assembly manifest can be stored in either a PE file (an .exe or .dll) with Microsoft intermediate language (MSIL) code or in a standalone PE file that contains only assembly manifest information.</span></span>  
  
 <span data-ttu-id="1905e-107">マニフェストを格納するさまざまな方法を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="1905e-107">The following illustration shows the different ways the manifest can be stored.</span></span>  
  
 <span data-ttu-id="1905e-108">![A single&#45;file assembly](../../../docs/framework/app-domains/media/assemblytypes.gif "assemblytypes")</span><span class="sxs-lookup"><span data-stu-id="1905e-108">![A single&#45;file assembly](../../../docs/framework/app-domains/media/assemblytypes.gif "assemblytypes")</span></span>  
<span data-ttu-id="1905e-109">アセンブリの種類</span><span class="sxs-lookup"><span data-stu-id="1905e-109">Types of assemblies</span></span>  
  
 <span data-ttu-id="1905e-110">関連付けられているファイルが 1 つだけのアセンブリの場合、マニフェストは PE ファイルに組み込まれ、シングルファイル アセンブリを形成します。</span><span class="sxs-lookup"><span data-stu-id="1905e-110">For an assembly with one associated file, the manifest is incorporated into the PE file to form a single-file assembly.</span></span> <span data-ttu-id="1905e-111">マルチファイル アセンブリを作成する場合は、スタンドアロンのマニフェスト ファイルか、またはそのアセンブリの PE ファイルのうちの 1 つに組み込んだマニフェストを使用します。</span><span class="sxs-lookup"><span data-stu-id="1905e-111">You can create a multifile assembly with a standalone manifest file or with the manifest incorporated into one of the PE files in the assembly.</span></span>  
  
 <span data-ttu-id="1905e-112">各アセンブリのマニフェストの機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1905e-112">Each assembly's manifest performs the following functions:</span></span>  
  
-   <span data-ttu-id="1905e-113">アセンブリを構成するファイルを列挙します。</span><span class="sxs-lookup"><span data-stu-id="1905e-113">Enumerates the files that make up the assembly.</span></span>  
  
-   <span data-ttu-id="1905e-114">アセンブリの型およびリソースへの参照を、それらの宣言と実装が格納されているファイルに割り当てる方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="1905e-114">Governs how references to the assembly's types and resources map to the files that contain their declarations and implementations.</span></span>  
  
-   <span data-ttu-id="1905e-115">そのアセンブリが依存するほかのアセンブリを列挙します。</span><span class="sxs-lookup"><span data-stu-id="1905e-115">Enumerates other assemblies on which the assembly depends.</span></span>  
  
-   <span data-ttu-id="1905e-116">アセンブリのコンシューマーと、アセンブリの詳細な実装との間に間接的な関係を確立します。</span><span class="sxs-lookup"><span data-stu-id="1905e-116">Provides a level of indirection between consumers of the assembly and the assembly's implementation details.</span></span>  
  
-   <span data-ttu-id="1905e-117">アセンブリを自己記述型にします。</span><span class="sxs-lookup"><span data-stu-id="1905e-117">Renders the assembly self-describing.</span></span>  
  
## <a name="assembly-manifest-contents"></a><span data-ttu-id="1905e-118">アセンブリ マニフェストの内容</span><span class="sxs-lookup"><span data-stu-id="1905e-118">Assembly Manifest Contents</span></span>  
 <span data-ttu-id="1905e-119">アセンブリ マニフェストに格納されている情報を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="1905e-119">The following table shows the information contained in the assembly manifest.</span></span> <span data-ttu-id="1905e-120">アセンブリ名、バージョン番号、カルチャ、厳密な名前情報という最初の 4 項目は、アセンブリの識別子を構成します。</span><span class="sxs-lookup"><span data-stu-id="1905e-120">The first four items—the assembly name, version number, culture, and strong name information—make up the assembly's identity.</span></span>  
  
|<span data-ttu-id="1905e-121">情報</span><span class="sxs-lookup"><span data-stu-id="1905e-121">Information</span></span>|<span data-ttu-id="1905e-122">説明</span><span class="sxs-lookup"><span data-stu-id="1905e-122">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="1905e-123">[アセンブリ名]</span><span class="sxs-lookup"><span data-stu-id="1905e-123">Assembly name</span></span>|<span data-ttu-id="1905e-124">アセンブリの名前を指定するテキスト文字列。</span><span class="sxs-lookup"><span data-stu-id="1905e-124">A text string specifying the assembly's name.</span></span>|  
|<span data-ttu-id="1905e-125">バージョン番号</span><span class="sxs-lookup"><span data-stu-id="1905e-125">Version number</span></span>|<span data-ttu-id="1905e-126">メジャー バージョン番号、マイナー バージョン番号、リビジョン番号、およびビルド番号。</span><span class="sxs-lookup"><span data-stu-id="1905e-126">A major and minor version number, and a revision and build number.</span></span> <span data-ttu-id="1905e-127">共通言語ランタイムは、これらの番号を使用してバージョン ポリシーを強制的に適用します。</span><span class="sxs-lookup"><span data-stu-id="1905e-127">The common language runtime uses these numbers to enforce version policy.</span></span>|  
|<span data-ttu-id="1905e-128">カルチャ</span><span class="sxs-lookup"><span data-stu-id="1905e-128">Culture</span></span>|<span data-ttu-id="1905e-129">アセンブリがサポートするカルチャや言語に関する情報。</span><span class="sxs-lookup"><span data-stu-id="1905e-129">Information on the culture or language the assembly supports.</span></span> <span data-ttu-id="1905e-130">この情報は、アセンブリをカルチャ固有または言語固有の情報を格納したサテライト アセンブリとして指定する場合にだけ使用します。</span><span class="sxs-lookup"><span data-stu-id="1905e-130">This information should be used only to designate an assembly as a satellite assembly containing culture- or language-specific information.</span></span> <span data-ttu-id="1905e-131">カルチャ情報を含むアセンブリは、自動的にサテライト アセンブリと見なされます。</span><span class="sxs-lookup"><span data-stu-id="1905e-131">(An assembly with culture information is automatically assumed to be a satellite assembly.)</span></span>|  
|<span data-ttu-id="1905e-132">厳密な名前情報</span><span class="sxs-lookup"><span data-stu-id="1905e-132">Strong name information</span></span>|<span data-ttu-id="1905e-133">アセンブリに厳密な名前が付いている場合の発行者からの公開キー。</span><span class="sxs-lookup"><span data-stu-id="1905e-133">The public key from the publisher if the assembly has been given a strong name.</span></span>|  
|<span data-ttu-id="1905e-134">アセンブリ内のすべてのファイルのリスト</span><span class="sxs-lookup"><span data-stu-id="1905e-134">List of all files in the assembly</span></span>|<span data-ttu-id="1905e-135">アセンブリに含まれている各ファイルのハッシュおよびファイル名。</span><span class="sxs-lookup"><span data-stu-id="1905e-135">A hash of each file contained in the assembly and a file name.</span></span> <span data-ttu-id="1905e-136">アセンブリを構成するすべてのファイルは、アセンブリ マニフェストが含まれているファイルと同じディレクトリに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1905e-136">Note that all files that make up the assembly must be in the same directory as the file containing the assembly manifest.</span></span>|  
|<span data-ttu-id="1905e-137">型参照情報</span><span class="sxs-lookup"><span data-stu-id="1905e-137">Type reference information</span></span>|<span data-ttu-id="1905e-138">型参照をその宣言と実装が格納されているファイルに割り当てるために、ランタイムが使用する情報。</span><span class="sxs-lookup"><span data-stu-id="1905e-138">Information used by the runtime to map a type reference to the file that contains its declaration and implementation.</span></span> <span data-ttu-id="1905e-139">この情報は、アセンブリからエクスポートされた型に対して使用されます。</span><span class="sxs-lookup"><span data-stu-id="1905e-139">This is used for types that are exported from the assembly.</span></span>|  
|<span data-ttu-id="1905e-140">参照先アセンブリに関する情報</span><span class="sxs-lookup"><span data-stu-id="1905e-140">Information on referenced assemblies</span></span>|<span data-ttu-id="1905e-141">このアセンブリによって静的に参照されるほかのアセンブリのリスト。</span><span class="sxs-lookup"><span data-stu-id="1905e-141">A list of other assemblies that are statically referenced by the assembly.</span></span> <span data-ttu-id="1905e-142">参照される各アセンブリ (依存アセンブリ) について、その名前、アセンブリ メタデータ (バージョン、カルチャ、オペレーティング システムなど)、アセンブリに厳密な名前が付いている場合は公開キーなどが示されます。</span><span class="sxs-lookup"><span data-stu-id="1905e-142">Each reference includes the dependent assembly's name, assembly metadata (version, culture, operating system, and so on), and public key, if the assembly is strong named.</span></span>|  
  
 <span data-ttu-id="1905e-143">アセンブリ マニフェストの一部の情報は、コード内でアセンブリ属性を使用することで、追加または変更できます。</span><span class="sxs-lookup"><span data-stu-id="1905e-143">You can add or change some information in the assembly manifest by using assembly attributes in your code.</span></span> <span data-ttu-id="1905e-144">バージョン情報や、商標、著作権、製品名、会社名、補足バージョンなどの情報属性は変更できます。</span><span class="sxs-lookup"><span data-stu-id="1905e-144">You can change version information and informational attributes, including Trademark, Copyright, Product, Company, and Informational Version.</span></span> <span data-ttu-id="1905e-145">アセンブリ属性の完全なリストについては、「[Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md)」 (アセンブリ属性の設定) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1905e-145">For a complete list of assembly attributes, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1905e-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="1905e-146">See Also</span></span>  
 <span data-ttu-id="1905e-147">[アセンブリの内容](../../../docs/framework/app-domains/assembly-contents.md) </span><span class="sxs-lookup"><span data-stu-id="1905e-147">[Assembly Contents](../../../docs/framework/app-domains/assembly-contents.md) </span></span>  
 <span data-ttu-id="1905e-148">[アセンブリのバージョン管理](../../../docs/framework/app-domains/assembly-versioning.md) </span><span class="sxs-lookup"><span data-stu-id="1905e-148">[Assembly Versioning](../../../docs/framework/app-domains/assembly-versioning.md) </span></span>  
 <span data-ttu-id="1905e-149">[サテライト アセンブリの作成](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md) </span><span class="sxs-lookup"><span data-stu-id="1905e-149">[Creating Satellite Assemblies](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md) </span></span>  
 [<span data-ttu-id="1905e-150">厳密な名前付きアセンブリ</span><span class="sxs-lookup"><span data-stu-id="1905e-150">Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/strong-named-assemblies.md)
