---
title: "プログラミング ガイド (LINQ to XML) (C#)"
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
ms.assetid: 4b1ffd10-ab81-4a0d-a0ca-e9876478d924
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
ms.openlocfilehash: ed4b0aff72654b9ac0928fae933e34268aede7fe
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="programming-guide-linq-to-xml-c"></a><span data-ttu-id="7e2e0-102">プログラミング ガイド (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7e2e0-102">Programming Guide (LINQ to XML) (C#)</span></span>
<span data-ttu-id="7e2e0-103">ここでは、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] を使用したプログラミングに関する概念と方法の情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-103">This section provides conceptual and how-to information about programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
## <a name="who-should-read-this-documentation"></a><span data-ttu-id="7e2e0-104">このドキュメントの対象読者</span><span class="sxs-lookup"><span data-stu-id="7e2e0-104">Who Should Read This Documentation</span></span>  
 <span data-ttu-id="7e2e0-105">このドキュメントは、C# や [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] の基本的な側面について既に理解している開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-105">This documentation targets developers who already understand C# and some basic aspects of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="7e2e0-106">このドキュメントの目的は、多数の開発者が [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] を簡単に使用できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-106">The goal of this documentation is to make [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] easy to use for all kinds of developers.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7e2e0-107"> によって、XML プログラミングが容易になります。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-107"> makes XML programming easier.</span></span> <span data-ttu-id="7e2e0-108">
           を使用するために上級開発者になる必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-108">You do not have to be an expert developer to use it.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7e2e0-109"> は、ジェネリック クラスに大きく依存しています。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-109"> relies heavily on generic classes.</span></span> <span data-ttu-id="7e2e0-110">そのため、ジェネリック クラスの使用について理解することが非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-110">Therefore, is very important that you understand the use of generic classes.</span></span> <span data-ttu-id="7e2e0-111">また、パラメーター化された型として宣言されるデリゲートに関する知識があると役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-111">Further, it is helpful if you are familiar with delegates that are declared as parameterized types.</span></span> <span data-ttu-id="7e2e0-112">C# のジェネリック クラスに慣れていない場合は、「[ジェネリック クラス](../../../../csharp/programming-guide/generics/generic-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-112">If you are not familiar with C# generic classes, see [Generic Classes](../../../../csharp/programming-guide/generics/generic-classes.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7e2e0-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7e2e0-113">In This Section</span></span>  
  
|<span data-ttu-id="7e2e0-114">トピック</span><span class="sxs-lookup"><span data-stu-id="7e2e0-114">Topic</span></span>|<span data-ttu-id="7e2e0-115">説明</span><span class="sxs-lookup"><span data-stu-id="7e2e0-115">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7e2e0-116">LINQ to XML プログラミングの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="7e2e0-116">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)|<span data-ttu-id="7e2e0-117">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クラスの概要と、最も重要な 3 つのクラス (<xref:System.Xml.Linq.XElement>、<xref:System.Xml.Linq.XAttribute>、<xref:System.Xml.Linq.XDocument>) に関する詳細情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-117">Provides an overview of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes, and detailed information about three of the most important classes: <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, and <xref:System.Xml.Linq.XDocument>.</span></span>|  
|[<span data-ttu-id="7e2e0-118">XML ツリーの作成 (C#)</span><span class="sxs-lookup"><span data-stu-id="7e2e0-118">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)|<span data-ttu-id="7e2e0-119">XML ツリーの作成に関する概念とタスク ベースの情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-119">Provides conceptual and task-based information about creating XML trees.</span></span> <span data-ttu-id="7e2e0-120">XML ツリーを作成するには、関数型構築を使用するか、文字列またはファイルから XML テキストを解析します。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-120">You can create XML trees by using functional construction, or by parsing XML text from a string or a file.</span></span> <span data-ttu-id="7e2e0-121"><xref:System.Xml.XmlReader> を使用してツリーを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-121">You can also use an <xref:System.Xml.XmlReader> to populate an XML tree.</span></span>|  
|[<span data-ttu-id="7e2e0-122">XML 名前空間の使用 (C#)</span><span class="sxs-lookup"><span data-stu-id="7e2e0-122">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)|<span data-ttu-id="7e2e0-123">名前空間を使用する XML ツリーの作成に関する詳細情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-123">Provides detailed information about creating XML trees that use namespaces.</span></span>|  
|[<span data-ttu-id="7e2e0-124">XML ツリーのシリアル化 (C#)</span><span class="sxs-lookup"><span data-stu-id="7e2e0-124">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)|<span data-ttu-id="7e2e0-125">XML ツリーをシリアル化する複数の方法について説明し、どの方法を使用するかについてのガイダンスを紹介します。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-125">Describes multiple approaches to serializing an XML tree, and gives guidance on which approach to use.</span></span>|  
|[<span data-ttu-id="7e2e0-126">LINQ to XML 軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="7e2e0-126">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)|<span data-ttu-id="7e2e0-127">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 軸メソッドを列挙して説明します。[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリを記述する場合は、あらかじめこれらの軸メソッドについて理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-127">Enumerates and describes the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axis methods, which you must understand before you can write [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>|  
|[<span data-ttu-id="7e2e0-128">XML ツリーのクエリ (C#)</span><span class="sxs-lookup"><span data-stu-id="7e2e0-128">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)|<span data-ttu-id="7e2e0-129">XML ツリーのクエリの一般的な例について説明します。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-129">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="7e2e0-130">XML ツリーの変更 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7e2e0-130">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)|<span data-ttu-id="7e2e0-131">ドキュメント オブジェクト モデル (DOM) と同様、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] では XML ツリーを直接変更できます。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-131">Like the Document Object Model (DOM), [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enables you to modify an XML tree in place.</span></span>|  
|[<span data-ttu-id="7e2e0-132">高度な LINQ to XML プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="7e2e0-132">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)|<span data-ttu-id="7e2e0-133">注釈、イベント、ストリーミング、およびその他の高度なシナリオに関する情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-133">Provides information about annotations, events, streaming, and other advanced scenarios.</span></span>|  
|[<span data-ttu-id="7e2e0-134">LINQ to XML のセキュリティ (C#)</span><span class="sxs-lookup"><span data-stu-id="7e2e0-134">LINQ to XML Security (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-security.md)|<span data-ttu-id="7e2e0-135">LINQ to XML に関連するセキュリティの問題について説明し、セキュリティ上の脆弱性を改善するためのガイダンスを紹介します。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-135">Describes security issues associated with LINQ to XML and provides some guidance for mitigating security exposure.</span></span>|  
|[<span data-ttu-id="7e2e0-136">サンプル XML ドキュメント (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="7e2e0-136">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)|<span data-ttu-id="7e2e0-137">このドキュメントの多数の例で使用されているサンプル XML ドキュメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7e2e0-137">Contains the sample XML documents that are used by many examples in this documentation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7e2e0-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e2e0-138">See Also</span></span>  
 <span data-ttu-id="7e2e0-139">[はじめに (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="7e2e0-139">[Getting Started (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md) </span></span>  
 [<span data-ttu-id="7e2e0-140">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7e2e0-140">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)
