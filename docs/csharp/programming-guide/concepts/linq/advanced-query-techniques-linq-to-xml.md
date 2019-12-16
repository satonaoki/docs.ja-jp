---
title: "高度なクエリ手法 (LINQ to XML) (C#)"
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
ms.assetid: 028d978e-215b-4d50-ba70-adce0659386d
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 91460ed99854edda829503d451728c4274d7ba2b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="advanced-query-techniques-linq-to-xml-c"></a><span data-ttu-id="4faef-102">高度なクエリ手法 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4faef-102">Advanced Query Techniques (LINQ to XML) (C#)</span></span>
<span data-ttu-id="4faef-103">ここでは、高度な [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリ手法の例について説明します。</span><span class="sxs-lookup"><span data-stu-id="4faef-103">This section provides examples of more advanced [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query techniques.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4faef-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4faef-104">In This Section</span></span>  
  
|<span data-ttu-id="4faef-105">トピック</span><span class="sxs-lookup"><span data-stu-id="4faef-105">Topic</span></span>|<span data-ttu-id="4faef-106">説明</span><span class="sxs-lookup"><span data-stu-id="4faef-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4faef-107">方法: 2 つのコレクションを結合する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4faef-107">How to: Join Two Collections (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-join-two-collections-linq-to-xml.md)|<span data-ttu-id="4faef-108">`Join` 句を使用して XML データでリレーションシップを利用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4faef-108">Shows how to use the `Join` clause to take advantage of relationships in XML data.</span></span>|  
|[<span data-ttu-id="4faef-109">方法: グループ化を使用して階層を作成する (C#)</span><span class="sxs-lookup"><span data-stu-id="4faef-109">How to: Create Hierarchy Using Grouping (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-create-hierarchy-using-grouping.md)|<span data-ttu-id="4faef-110">データをグループ化する方法と、グループ化に基づいて XML を生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4faef-110">Shows how to group data, and then generate XML based on the grouping.</span></span>|  
|[<span data-ttu-id="4faef-111">方法: XPath を使用して LINQ to XML にクエリを実行する (C#)</span><span class="sxs-lookup"><span data-stu-id="4faef-111">How to: Query LINQ to XML Using XPath (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-linq-to-xml-using-xpath.md)|<span data-ttu-id="4faef-112">XPath クエリに基づいてコレクションを取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4faef-112">Shows how to retrieve collections based on XPath queries.</span></span>|  
|[<span data-ttu-id="4faef-113">方法: LINQ to XML 軸メソッドを記述する (C#)</span><span class="sxs-lookup"><span data-stu-id="4faef-113">How to: Write a LINQ to XML Axis Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md)|<span data-ttu-id="4faef-114">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 軸メソッドを記述する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4faef-114">Shows how to write a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axis method.</span></span>|  
|[<span data-ttu-id="4faef-115">方法: テキストから XML へのストリーミング変換を実行する (C#)</span><span class="sxs-lookup"><span data-stu-id="4faef-115">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transformations-of-text-to-xml.md)|<span data-ttu-id="4faef-116">メモリ使用量を低く抑えながら、非常に大きなテキスト ファイルを XML に変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4faef-116">Shows how to transform very large text files into XML while maintaining a small memory footprint.</span></span>|  
|[<span data-ttu-id="4faef-117">方法: ツリー内のすべてのノードを一覧表示する (C#)</span><span class="sxs-lookup"><span data-stu-id="4faef-117">How to: List All Nodes in a Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-list-all-nodes-in-a-tree.md)|<span data-ttu-id="4faef-118">XML ツリー内のすべてのノードを一覧表示するユーティリティ メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4faef-118">Presents a utility method that lists all nodes in an XML tree.</span></span> <span data-ttu-id="4faef-119">これは、XML ツリーを変更するコードをデバッグする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="4faef-119">This is useful for debugging code that modifies an XML tree.</span></span>|  
|[<span data-ttu-id="4faef-120">方法: Office Open XML ドキュメントから段落を取得する (C#)</span><span class="sxs-lookup"><span data-stu-id="4faef-120">How to: Retrieve Paragraphs from an Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-paragraphs-from-an-office-open-xml-document.md)|<span data-ttu-id="4faef-121">Office Open XML ドキュメントを開き、XElement オブジェクトのコレクション内の段落、段落のテキスト、および段落のスタイルを取得するコードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4faef-121">Presents code that opens an Office Open XML Document, retrieves the paragraphs in a collection of XElement objects, the text of the paragraphs, and the style of the paragraphs.</span></span>|  
|[<span data-ttu-id="4faef-122">方法: Office Open XML ドキュメントを変更する (C#)</span><span class="sxs-lookup"><span data-stu-id="4faef-122">How to: Modify an Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-modify-an-office-open-xml-document.md)|<span data-ttu-id="4faef-123">Office Open XML ドキュメントを開き、変更し、保存するコードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4faef-123">Presents code that opens, modifies, and saves an Office Open XML Document.</span></span>|  
|[<span data-ttu-id="4faef-124">方法: ファイル システムから XML ツリーを設定する (C#)</span><span class="sxs-lookup"><span data-stu-id="4faef-124">How to: Populate an XML Tree from the File System (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-an-xml-tree-from-the-file-system.md)|<span data-ttu-id="4faef-125">ファイル システムから XML ツリーを作成するコードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4faef-125">Presents code that creates an XML tree from the file system.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4faef-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="4faef-126">See Also</span></span>  
 [<span data-ttu-id="4faef-127">XML ツリーのクエリ (C#)</span><span class="sxs-lookup"><span data-stu-id="4faef-127">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
