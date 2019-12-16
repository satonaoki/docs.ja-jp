---
title: "false 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e12de403ca31952837913fdaaa8b221986f0e5fe
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="false-operator-c-reference"></a><span data-ttu-id="8baf7-102">false 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="8baf7-102">false Operator (C# Reference)</span></span>
<span data-ttu-id="8baf7-103">オペランドが `false` であることを示す[ブール](../../../csharp/language-reference/keywords/bool.md)値 `true` を返します。それ以外の場合は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="8baf7-103">Returns the [bool](../../../csharp/language-reference/keywords/bool.md) value `true` to indicate that an operand is `false` and returns `false` otherwise.</span></span>  
  
 <span data-ttu-id="8baf7-104">C# 2.0 より前のバージョンでは、`true` および `false` 演算子は、`SqlBool` などの型と互換性のあるユーザー定義の null 非許容の値型を作成するために使用されていました。</span><span class="sxs-lookup"><span data-stu-id="8baf7-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="8baf7-105">ただし、現在は null 許容の値型が組み込まれているため、可能な場合には、`true` 演算子と `false` 演算子のオーバーロードではなく、null 許容の値型を使用してください。</span><span class="sxs-lookup"><span data-stu-id="8baf7-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="8baf7-106">詳細については、「[null 許容型](../../../csharp/programming-guide/nullable-types/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8baf7-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="8baf7-107">null 許容のブール値では、必ずしも式 `a != b` が `!(a == b)` にならないことがあります。これは、いずれかの値が null の場合があるためです。</span><span class="sxs-lookup"><span data-stu-id="8baf7-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="8baf7-108">式内の null 値を適切に処理するには、`true` および `false` 演算子の両方を別にオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8baf7-108">You have to overload both the `true` and `false` operators separately to correctly handle the null values in the expression.</span></span> <span data-ttu-id="8baf7-109">次の例は、`true` および `false` 演算子をオーバーロードして使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8baf7-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>  
  
 <span data-ttu-id="8baf7-110">[!code-cs[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/false-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8baf7-110">[!code-cs[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/false-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="8baf7-111">`true` および `false` 演算子のオーバーロードする型は、[if](../../../csharp/language-reference/keywords/if-else.md)、[do](../../../csharp/language-reference/keywords/do.md)、[while](../../../csharp/language-reference/keywords/while.md)、[for](../../../csharp/language-reference/keywords/for.md) ステートメント内の制御式と、[条件式](../../../csharp/language-reference/operators/conditional-operator.md)で使用できます。</span><span class="sxs-lookup"><span data-stu-id="8baf7-111">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md), and [for](../../../csharp/language-reference/keywords/for.md) statements and in [conditional expressions](../../../csharp/language-reference/operators/conditional-operator.md).</span></span>  
  
 <span data-ttu-id="8baf7-112">型で演算子 `false` を定義する場合は、演算子の [true](../../../csharp/language-reference/keywords/true.md) も定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8baf7-112">If a type defines operator `false`, it must also define operator [true](../../../csharp/language-reference/keywords/true.md).</span></span>  
  
 <span data-ttu-id="8baf7-113">型では、条件付き論理演算子 [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) と [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) を直接オーバーロードできませんが、通常の論理演算子と演算子 `true` および `false` をオーバーロードすることで同等の効果を実現できます。</span><span class="sxs-lookup"><span data-stu-id="8baf7-113">A type cannot directly overload the conditional logical operators [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="8baf7-114">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="8baf7-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8baf7-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8baf7-115">See Also</span></span>  
 <span data-ttu-id="8baf7-116">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="8baf7-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="8baf7-117">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8baf7-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="8baf7-118">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="8baf7-118">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="8baf7-119">[C# 演算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="8baf7-119">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 [<span data-ttu-id="8baf7-120">true</span><span class="sxs-lookup"><span data-stu-id="8baf7-120">true</span></span>](../../../csharp/language-reference/keywords/true.md)
