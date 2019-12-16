---
title: "高度な LINQ to XML プログラミング (C#)"
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
ms.assetid: 2e012d40-532b-49ea-b1fc-152e616bdfa3
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4419d05874f8e4883711d0f4abb98bc4a416b7fd
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="advanced-linq-to-xml-programming-c"></a><span data-ttu-id="88bd2-102">高度な LINQ to XML プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="88bd2-102">Advanced LINQ to XML Programming (C#)</span></span>
<span data-ttu-id="88bd2-103">ここでは、特定の [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] シナリオにおける上級開発者だけを対象とした情報を紹介します。</span><span class="sxs-lookup"><span data-stu-id="88bd2-103">This section provides information that will only be applicable to advanced developers in certain [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="88bd2-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="88bd2-104">In This Section</span></span>  
  
|<span data-ttu-id="88bd2-105">トピック</span><span class="sxs-lookup"><span data-stu-id="88bd2-105">Topic</span></span>|<span data-ttu-id="88bd2-106">説明</span><span class="sxs-lookup"><span data-stu-id="88bd2-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="88bd2-107">LINQ to XML の注釈</span><span class="sxs-lookup"><span data-stu-id="88bd2-107">LINQ to XML Annotations</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-annotations.md)|<span data-ttu-id="88bd2-108">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] のノードおよび属性に注釈を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="88bd2-108">Describes how to add annotations to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nodes and attributes.</span></span>|  
|[<span data-ttu-id="88bd2-109">LINQ to XML イベント (C#)</span><span class="sxs-lookup"><span data-stu-id="88bd2-109">LINQ to XML Events (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-events.md)|<span data-ttu-id="88bd2-110">XML ツリーを変更するときに発生するイベントのイベント ハンドラーを記述する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="88bd2-110">Describes how to write event handlers for events that occur when you alter an XML tree.</span></span>|  
|[<span data-ttu-id="88bd2-111">ノードでのプログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="88bd2-111">Programming with Nodes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-with-nodes.md)|<span data-ttu-id="88bd2-112">要素や属性よりも細かい粒度レベルでノードをクエリおよび操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="88bd2-112">Describes how to query and manipulate nodes at a finer level of granularity than elements and attributes.</span></span>|  
|[<span data-ttu-id="88bd2-113">宣言型コードと命令型コードの混在のバグ (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="88bd2-113">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md)|<span data-ttu-id="88bd2-114">宣言型コード (クエリ) と命令型コード (XML ツリーを変更するコード) を混在させた場合に発生する問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="88bd2-114">Describes the problems that appear when you mix declarative code (queries) with imperative code (code that modifies the XML tree).</span></span>|  
|[<span data-ttu-id="88bd2-115">方法: ヘッダー情報にアクセスして XML フラグメントをストリーム出力する (C#)</span><span class="sxs-lookup"><span data-stu-id="88bd2-115">How to: Stream XML Fragments with Access to Header Information (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)|<span data-ttu-id="88bd2-116"><xref:System.Xml.XmlReader> から XML フラグメントをストリーム出力する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="88bd2-116">Describes how to stream XML fragments from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="88bd2-117">この手法を使用してアプリケーションのメモリ使用量を制御できます。</span><span class="sxs-lookup"><span data-stu-id="88bd2-117">You can use this technique to control the memory footprint of your application.</span></span>|  
|[<span data-ttu-id="88bd2-118">方法: 大きな XML ドキュメントのストリーミング変換を実行する (C#)</span><span class="sxs-lookup"><span data-stu-id="88bd2-118">How to: Perform Streaming Transform of Large XML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md)|<span data-ttu-id="88bd2-119"><xref:System.Xml.XmlReader> から XML をストリーム出力し、XML フラグメントを変換して、<xref:System.Xml.Linq.XStreamingElement> によってその出力をストリームする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="88bd2-119">Describes how to stream XML from an <xref:System.Xml.XmlReader>, transform the XML fragment, and stream the output using <xref:System.Xml.Linq.XStreamingElement>.</span></span>|  
|[<span data-ttu-id="88bd2-120">方法: エンコードされたドキュメントを読み書きする (C#)</span><span class="sxs-lookup"><span data-stu-id="88bd2-120">How to: Read and Write an Encoded Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-read-and-write-an-encoded-document.md)|<span data-ttu-id="88bd2-121">エンコードされる XML ドキュメントの読み取りおよび書き込みを行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="88bd2-121">Describes how to read and write XML documents that are encoded.</span></span>|  
|[<span data-ttu-id="88bd2-122">XSLT を使用した XML ツリーの変換 (C#)</span><span class="sxs-lookup"><span data-stu-id="88bd2-122">Using XSLT to Transform an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/using-xslt-to-transform-an-xml-tree.md)|<span data-ttu-id="88bd2-123">XSLT を使用して XML ツリーを変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="88bd2-123">Describes how to transform an XML tree using XSLT.</span></span>|  
|[<span data-ttu-id="88bd2-124">方法: 注釈を使用して XSLT スタイルの LINQ to XML ツリーを変換する (C#)</span><span class="sxs-lookup"><span data-stu-id="88bd2-124">How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style.md)|<span data-ttu-id="88bd2-125">注釈を使用して XML ツリーの変換を容易にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="88bd2-125">Describes how annotations can be used to facilitate transforms of an XML tree.</span></span>|  
|[<span data-ttu-id="88bd2-126">XElement オブジェクトを含むオブジェクト グラフのシリアル化 (C#)</span><span class="sxs-lookup"><span data-stu-id="88bd2-126">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-object-graphs-that-contain-xelement-objects.md)|<span data-ttu-id="88bd2-127"><xref:System.Xml.Linq.XElement> オブジェクトおよび <xref:System.Xml.Linq.XDocument> オブジェクトを含むオブジェクト グラフをシリアル化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="88bd2-127">Describes how to serialize object graphs that contain <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|[<span data-ttu-id="88bd2-128">LINQ to XML による WPF のデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="88bd2-128">WPF Data Binding with LINQ to XML</span></span>](/visualstudio/designers/wpf-data-binding-with-linq-to-xml)|<span data-ttu-id="88bd2-129">Windows Presentation Foundation アプリケーションでのデータ バインディングのデータ ソースとして LINQ to XML を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="88bd2-129">Describes how to use LINQ to XML as the data source for data binding in Windows Presentation Foundation applications.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88bd2-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="88bd2-130">See Also</span></span>  
 [<span data-ttu-id="88bd2-131">プログラミング ガイド (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="88bd2-131">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
