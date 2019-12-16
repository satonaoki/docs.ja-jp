---
title: "XPath と LINQ to XML1 の比較 |Microsoft ドキュメント"
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
ms.assetid: c3fd07c1-6761-4e4b-8eb1-ddd780ed8d44
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0cd533442604a8fff23e5573f907aa157a723f11
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="855b1-102">XPath と LINQ to XML の比較</span><span class="sxs-lookup"><span data-stu-id="855b1-102">Comparison of XPath and LINQ to XML</span></span>
<span data-ttu-id="855b1-103">XPath と [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] の機能はある程度似ています。</span><span class="sxs-lookup"><span data-stu-id="855b1-103">XPath and [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] offer some similar functionality.</span></span> <span data-ttu-id="855b1-104">どちらも XML ツリーに対してクエリを実行するために使用され、結果として、要素のコレクション、属性のコレクション、ノードのコレクション、要素や属性の値などを返します。</span><span class="sxs-lookup"><span data-stu-id="855b1-104">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="855b1-105">ただし、相違点もいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="855b1-105">However, there are also some differences.</span></span>  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="855b1-106">XPath と LINQ to XML の違い</span><span class="sxs-lookup"><span data-stu-id="855b1-106">Differences Between XPath and LINQ to XML</span></span>  
 <span data-ttu-id="855b1-107">XPath では、新しい型を射影できません。</span><span class="sxs-lookup"><span data-stu-id="855b1-107">XPath does not allow projection of new types.</span></span> <span data-ttu-id="855b1-108">XPath では、ツリーからノードのコレクションが返されるだけですが、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] では、クエリを実行し、オブジェクト グラフまたは XML ツリーを新しい構造に射影できます。</span><span class="sxs-lookup"><span data-stu-id="855b1-108">It can only return collections of nodes from the tree, whereas [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] can execute a query and project an object graph or an XML tree in a new shape.</span></span> [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="855b1-109"> クエリは、XPath 式と比べて、はるかに多機能かつ強力です。</span><span class="sxs-lookup"><span data-stu-id="855b1-109"> queries encompass much more functionality and are much more powerful than XPath expressions.</span></span>  
  
 <span data-ttu-id="855b1-110">XPath 式は、文字列内に独立して存在します。</span><span class="sxs-lookup"><span data-stu-id="855b1-110">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="855b1-111">Visual Basic コンパイラは、コンパイル時に XPath 式を解析することはできません。</span><span class="sxs-lookup"><span data-stu-id="855b1-111">The Visual Basic compiler cannot help parse the XPath expression at compile time.</span></span> <span data-ttu-id="855b1-112">これに対し、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]クエリが解析され、ビジュアルの基本的なコンパイラでコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="855b1-112">By contrast, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] queries are parsed and compiled by theVisual Basic compiler.</span></span> <span data-ttu-id="855b1-113">コンパイラを使用することにより、多くのクエリ エラーを検出できます。</span><span class="sxs-lookup"><span data-stu-id="855b1-113">The compiler is able to catch many query errors.</span></span>  
  
 <span data-ttu-id="855b1-114">XPath の結果は厳密に型指定されません。</span><span class="sxs-lookup"><span data-stu-id="855b1-114">XPath results are not strongly typed.</span></span> <span data-ttu-id="855b1-115">多くの場合、XPath 式を評価した結果はオブジェクトであり、開発者が適切な型を決定し、必要に応じて結果をキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="855b1-115">In a number of circumstances, the result of evaluating an XPath expression is an object, and it is up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="855b1-116">一方、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] クエリからの射影は厳密に型指定されます。</span><span class="sxs-lookup"><span data-stu-id="855b1-116">By contrast, the projections from a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query are strongly typed.</span></span>  
  
## <a name="result-ordering"></a><span data-ttu-id="855b1-117">結果の順序付け</span><span class="sxs-lookup"><span data-stu-id="855b1-117">Result Ordering</span></span>  
 <span data-ttu-id="855b1-118">XPath 1.0 勧告には、XPath 式の評価結果であるコレクションは順序付けされないことが記載されています。</span><span class="sxs-lookup"><span data-stu-id="855b1-118">The XPath 1.0 Recommendation states that a collection that is the result of evaluating an XPath expression is unordered.</span></span>  
  
 <span data-ttu-id="855b1-119">ただし、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] の XPath 軸メソッドから返されるコレクションを反復処理すると、コレクション内のノードがドキュメント順に返されます。</span><span class="sxs-lookup"><span data-stu-id="855b1-119">However, when iterating through a collection returned by a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="855b1-120">これは、ドキュメントの逆順として述語が表現されている `preceding` や `preceding-sibling` などの XPath 軸にアクセスする場合でも同様です。</span><span class="sxs-lookup"><span data-stu-id="855b1-120">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>  
  
 <span data-ttu-id="855b1-121">一方、ほとんどの[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]軸がドキュメントの順序はなく、これらの&2; つのコレクションを返す<xref:System.Xml.Linq.XNode.Ancestors%2A>と<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>、コレクションをドキュメントの逆順に返します</xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A></xref:System.Xml.Linq.XNode.Ancestors%2A>。</span><span class="sxs-lookup"><span data-stu-id="855b1-121">By contrast, most of the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] axes return collections in document order, but two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="855b1-122">次の表では、軸を列挙し、それぞれのコレクションの順序を示します。</span><span class="sxs-lookup"><span data-stu-id="855b1-122">The following table enumerates the axes, and indicates collection order for each:</span></span>  
  
|<span data-ttu-id="855b1-123">LINQ to XML 軸</span><span class="sxs-lookup"><span data-stu-id="855b1-123">LINQ to XML axis</span></span>|<span data-ttu-id="855b1-124">並べ替え</span><span class="sxs-lookup"><span data-stu-id="855b1-124">Ordering</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="855b1-125">XContainer.DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="855b1-125">XContainer.DescendantNodes</span></span>|<span data-ttu-id="855b1-126">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="855b1-126">Document order</span></span>|  
|<span data-ttu-id="855b1-127">XContainer.Descendants</span><span class="sxs-lookup"><span data-stu-id="855b1-127">XContainer.Descendants</span></span>|<span data-ttu-id="855b1-128">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="855b1-128">Document order</span></span>|  
|<span data-ttu-id="855b1-129">XContainer.Elements</span><span class="sxs-lookup"><span data-stu-id="855b1-129">XContainer.Elements</span></span>|<span data-ttu-id="855b1-130">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="855b1-130">Document order</span></span>|  
|<span data-ttu-id="855b1-131">XContainer.Nodes</span><span class="sxs-lookup"><span data-stu-id="855b1-131">XContainer.Nodes</span></span>|<span data-ttu-id="855b1-132">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="855b1-132">Document order</span></span>|  
|<span data-ttu-id="855b1-133">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="855b1-133">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="855b1-134">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="855b1-134">Document order</span></span>|  
|<span data-ttu-id="855b1-135">XContainer.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="855b1-135">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="855b1-136">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="855b1-136">Document order</span></span>|  
|<span data-ttu-id="855b1-137">XElement.AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="855b1-137">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="855b1-138">ドキュメントの逆順</span><span class="sxs-lookup"><span data-stu-id="855b1-138">Reverse document order</span></span>|  
|<span data-ttu-id="855b1-139">XElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="855b1-139">XElement.Attributes</span></span>|<span data-ttu-id="855b1-140">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="855b1-140">Document order</span></span>|  
|<span data-ttu-id="855b1-141">XElement.DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="855b1-141">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="855b1-142">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="855b1-142">Document order</span></span>|  
|<span data-ttu-id="855b1-143">XElement.DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="855b1-143">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="855b1-144">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="855b1-144">Document order</span></span>|  
|<span data-ttu-id="855b1-145">XNode.Ancestors</span><span class="sxs-lookup"><span data-stu-id="855b1-145">XNode.Ancestors</span></span>|<span data-ttu-id="855b1-146">ドキュメントの逆順</span><span class="sxs-lookup"><span data-stu-id="855b1-146">Reverse document order</span></span>|  
|<span data-ttu-id="855b1-147">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="855b1-147">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="855b1-148">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="855b1-148">Document order</span></span>|  
|<span data-ttu-id="855b1-149">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="855b1-149">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="855b1-150">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="855b1-150">Document order</span></span>|  
|<span data-ttu-id="855b1-151">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="855b1-151">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="855b1-152">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="855b1-152">Document order</span></span>|  
|<span data-ttu-id="855b1-153">XNode.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="855b1-153">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="855b1-154">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="855b1-154">Document order</span></span>|  
  
## <a name="positional-predicates"></a><span data-ttu-id="855b1-155">位置述語</span><span class="sxs-lookup"><span data-stu-id="855b1-155">Positional Predicates</span></span>  
 <span data-ttu-id="855b1-156">XPath 式では、多くの軸で位置述語がドキュメント順として表現されますが、逆方向軸つまり `preceding`、`preceding-sibling`、`ancestor`、および `ancestor-or-self` の場合は、ドキュメントの逆順で表現されます。</span><span class="sxs-lookup"><span data-stu-id="855b1-156">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes, which are `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="855b1-157">たとえば、XPath 式 `preceding-sibling::*[1]` は、直前の兄弟を返します。</span><span class="sxs-lookup"><span data-stu-id="855b1-157">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="855b1-158">これは、最終的な結果セットがドキュメント順で表される場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="855b1-158">This is the case even though the final result set is presented in document order.</span></span>  
  
 <span data-ttu-id="855b1-159">一方、LINQ to XML の位置述語は、常に軸の順序として表現されます。</span><span class="sxs-lookup"><span data-stu-id="855b1-159">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="855b1-160">たとえば、`anElement.ElementsBeforeSelf().ToList()[0]` は、直前の兄弟ではなく、クエリされる要素の親の最初の子要素を返します。</span><span class="sxs-lookup"><span data-stu-id="855b1-160">For example, `anElement.ElementsBeforeSelf().ToList()[0]` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="855b1-161">別の例として、`anElement.Ancestors().ToList()[0]` は親要素を返します。</span><span class="sxs-lookup"><span data-stu-id="855b1-161">Another example: `anElement.Ancestors().ToList()[0]` returns the parent element.</span></span>  
  
 <span data-ttu-id="855b1-162">上記の方法では、コレクション全体が具体化されます。</span><span class="sxs-lookup"><span data-stu-id="855b1-162">Note that the above approach materializes the entire collection.</span></span> <span data-ttu-id="855b1-163">これは、このクエリを記述する方法としては、最も効率的な方法とはいえません。</span><span class="sxs-lookup"><span data-stu-id="855b1-163">This is not the most efficient way to write that query.</span></span> <span data-ttu-id="855b1-164">このように記述されているのは、位置述語の動作を明らかにするためです。</span><span class="sxs-lookup"><span data-stu-id="855b1-164">It was written in that way to demonstrate the behavior of positional predicates.</span></span> <span data-ttu-id="855b1-165">同じクエリを作成するより適切な方法を使用して、<xref:System.Linq.Enumerable.First%2A>メソッドを次のとおりです: `anElement.ElementsBeforeSelf().First()`</xref:System.Linq.Enumerable.First%2A> 。</span><span class="sxs-lookup"><span data-stu-id="855b1-165">A more appropriate way to write the same query is to use the <xref:System.Linq.Enumerable.First%2A> method, as follows: `anElement.ElementsBeforeSelf().First()`.</span></span>  
  
 <span data-ttu-id="855b1-166">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] で直前の要素を検索する場合は、次の式を記述します。</span><span class="sxs-lookup"><span data-stu-id="855b1-166">If you wanted to find the immediately preceding element in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], you would write the following expression:</span></span>  
  
 `ElementsBeforeSelf().Last()`  
  
## <a name="performance-differences"></a><span data-ttu-id="855b1-167">パフォーマンスの違い</span><span class="sxs-lookup"><span data-stu-id="855b1-167">Performance Differences</span></span>  
 <span data-ttu-id="855b1-168">XPath 機能を使用する XPath クエリ[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]は実行しませんだけでなく[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]クエリ。</span><span class="sxs-lookup"><span data-stu-id="855b1-168">XPath queries that use the XPath functionality in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] will not perform as well as [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] queries.</span></span>  
  
## <a name="comparison-of-composition"></a><span data-ttu-id="855b1-169">構成の比較</span><span class="sxs-lookup"><span data-stu-id="855b1-169">Comparison of Composition</span></span>  
 <span data-ttu-id="855b1-170">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] クエリの構成は、XPath 式の構成に似ている部分がありますが、構文はかなり異なります。</span><span class="sxs-lookup"><span data-stu-id="855b1-170">Composition of a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query is somewhat parallel to composition of an XPath expression, although very different in syntax.</span></span>  
  
 <span data-ttu-id="855b1-171">たとえば、`customers` という変数に要素があり、`CompanyName` というすべての子要素の下で `Customer` という孫要素を検索する場合は、次のように XPath 式を記述します。</span><span class="sxs-lookup"><span data-stu-id="855b1-171">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write an XPath expression as follows:</span></span>  
  
```vb  
customers.XPathSelectElements("./Customer/CompanyName")  
```  
  
 <span data-ttu-id="855b1-172">これと同等の [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] クエリは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="855b1-172">The equivalent [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query is:</span></span>  
  
```vb  
customers.Element("Customer").Elements("CompanyName")  
```  
  
 <span data-ttu-id="855b1-173">同様の対応関係が XPath 軸ごとに存在します。</span><span class="sxs-lookup"><span data-stu-id="855b1-173">There are similar parallels for each of the XPath axes.</span></span>  
  
|<span data-ttu-id="855b1-174">XPath 軸</span><span class="sxs-lookup"><span data-stu-id="855b1-174">XPath axis</span></span>|<span data-ttu-id="855b1-175">LINQ to XML 軸</span><span class="sxs-lookup"><span data-stu-id="855b1-175">LINQ to XML axis</span></span>|  
|----------------|----------------------|  
|<span data-ttu-id="855b1-176">child (既定の軸)</span><span class="sxs-lookup"><span data-stu-id="855b1-176">child (the default axis)</span></span>|<span data-ttu-id="855b1-177"><xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="855b1-177"><xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="855b1-178">Parent (..)</span><span class="sxs-lookup"><span data-stu-id="855b1-178">Parent (..)</span></span>|<span data-ttu-id="855b1-179"><xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=fullName></xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="855b1-179"><xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="855b1-180">attribute 軸 (@)</span><span class="sxs-lookup"><span data-stu-id="855b1-180">attribute axis (@)</span></span>|<span data-ttu-id="855b1-181"><xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="855b1-181"><xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="855b1-182">または</span><span class="sxs-lookup"><span data-stu-id="855b1-182">or</span></span><br /><br /> <span data-ttu-id="855b1-183"><xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="855b1-183"><xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="855b1-184">ancestor 軸</span><span class="sxs-lookup"><span data-stu-id="855b1-184">ancestor axis</span></span>|<span data-ttu-id="855b1-185"><xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="855b1-185"><xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="855b1-186">ancestor-or-self 軸</span><span class="sxs-lookup"><span data-stu-id="855b1-186">ancestor-or-self axis</span></span>|<span data-ttu-id="855b1-187"><xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="855b1-187"><xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="855b1-188">descendant 軸 (//)</span><span class="sxs-lookup"><span data-stu-id="855b1-188">descendant axis (//)</span></span>|<span data-ttu-id="855b1-189"><xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="855b1-189"><xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="855b1-190">または</span><span class="sxs-lookup"><span data-stu-id="855b1-190">or</span></span><br /><br /> <span data-ttu-id="855b1-191"><xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="855b1-191"><xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="855b1-192">descendant-or-self</span><span class="sxs-lookup"><span data-stu-id="855b1-192">descendant-or-self</span></span>|<span data-ttu-id="855b1-193"><xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="855b1-193"><xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="855b1-194">または</span><span class="sxs-lookup"><span data-stu-id="855b1-194">or</span></span><br /><br /> <span data-ttu-id="855b1-195"><xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="855b1-195"><xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="855b1-196">following-sibling</span><span class="sxs-lookup"><span data-stu-id="855b1-196">following-sibling</span></span>|<span data-ttu-id="855b1-197"><xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="855b1-197"><xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="855b1-198">または</span><span class="sxs-lookup"><span data-stu-id="855b1-198">or</span></span><br /><br /> <span data-ttu-id="855b1-199"><xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="855b1-199"><xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="855b1-200">preceding-sibling</span><span class="sxs-lookup"><span data-stu-id="855b1-200">preceding-sibling</span></span>|<span data-ttu-id="855b1-201"><xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="855b1-201"><xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="855b1-202">または</span><span class="sxs-lookup"><span data-stu-id="855b1-202">or</span></span><br /><br /> <span data-ttu-id="855b1-203"><xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="855b1-203"><xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="855b1-204">following</span><span class="sxs-lookup"><span data-stu-id="855b1-204">following</span></span>|<span data-ttu-id="855b1-205">同等の軸はありません。</span><span class="sxs-lookup"><span data-stu-id="855b1-205">No direct equivalent.</span></span>|  
|<span data-ttu-id="855b1-206">preceding</span><span class="sxs-lookup"><span data-stu-id="855b1-206">preceding</span></span>|<span data-ttu-id="855b1-207">同等の軸はありません。</span><span class="sxs-lookup"><span data-stu-id="855b1-207">No direct equivalent.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="855b1-208">関連項目</span><span class="sxs-lookup"><span data-stu-id="855b1-208">See Also</span></span>  
 [<span data-ttu-id="855b1-209">LINQ to XML の XPath ユーザー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="855b1-209">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)