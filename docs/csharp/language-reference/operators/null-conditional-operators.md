---
title: "Null 条件演算子 (C# および Visual Basic)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
caps.latest.revision: 3
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
ms.sourcegitcommit: 6118956a5681ddbeb110f6e01f090b85cdd65089
ms.openlocfilehash: 465a395a33c027132b7890e02d540438096e2073
ms.contentlocale: ja-jp
ms.lasthandoff: 08/23/2017

---
# <a name="null-conditional-operators-c-and-visual-basic"></a><span data-ttu-id="c5eb2-102">Null 条件演算子 (C# および Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5eb2-102">Null-conditional Operators (C# and Visual Basic)</span></span>
<span data-ttu-id="c5eb2-103">メンバー アクセス (`?.`) またはインデックス (`?[`) 操作を実行する前に、null をテストするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c5eb2-103">Used to test for null before performing a member access (`?.`) or index (`?[`) operation.</span></span>  <span data-ttu-id="c5eb2-104">これらの演算子を使用すると、null チェックの処理のために記述するコードを少なくすることができます (特に、データ構造を下っていく場合)。</span><span class="sxs-lookup"><span data-stu-id="c5eb2-104">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
```  
  
```vb  
Dim length = customers?.Length  ' null if customers is null  
Dim first as Customer = customers?(0)  ' null if customers is null  
Dim count as Integer? = customers?(0)?.Orders?.Count()  ' null if customers, the first customer, or Orders is null  
```  
  
 <span data-ttu-id="c5eb2-105">最後の例は、null 条件演算子がショート サーキットであることを示します。</span><span class="sxs-lookup"><span data-stu-id="c5eb2-105">The last example demonstrates that the null-condition operators are short-circuiting.</span></span>  <span data-ttu-id="c5eb2-106">条件付きのメンバー アクセスおよびインデックス操作のチェーンの 1 つの演算が null を返す場合、チェーンの実行の残りの部分は停止します。</span><span class="sxs-lookup"><span data-stu-id="c5eb2-106">If one operation in a chain of conditional member access and index operation returns null, then the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="c5eb2-107">式内の優先度の低い他の演算は続行されます。</span><span class="sxs-lookup"><span data-stu-id="c5eb2-107">Other operations with lower precedence in the expression continue.</span></span>  <span data-ttu-id="c5eb2-108">たとえば、次の 2 行目にある `E` が実行され、`??` 演算と `==` 演算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="c5eb2-108">For example, `E` in the following executes in the second line, and the `??` and `==` operations execute.</span></span>  <span data-ttu-id="c5eb2-109">1 行目の `??` はショート サーキットであり、左辺が null 以外に評価されると、`E` は実行されません。</span><span class="sxs-lookup"><span data-stu-id="c5eb2-109">In the first line, the `??` short circuits and `E` does not execute when the left side evaluates to non-null.</span></span>
  
```csharp
A?.B?.C?[0] ?? E  
A?.B?.C?[0] == E  
```

```vb
A?.B?.C?(0) ?? E  
A?.B?.C?(0) == E  
```  
  
 <span data-ttu-id="c5eb2-110">null 条件メンバー アクセスの別の用途は、はるかに少ないコードのスレッド セーフな方法でデリゲートを呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="c5eb2-110">Another use for the null-condition member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="c5eb2-111">従来の方法には、次のようなコードが必要です。</span><span class="sxs-lookup"><span data-stu-id="c5eb2-111">The old way requires code like the following:</span></span>  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…);
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```  
  
 <span data-ttu-id="c5eb2-112">新しい方法は格段に単純です。</span><span class="sxs-lookup"><span data-stu-id="c5eb2-112">The new way is much simpler:</span></span>  
  
```csharp
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 <span data-ttu-id="c5eb2-113">コンパイラが `PropertyChanged` を評価するためのコードを一度しか生成せず、一時変数に結果が保持されるため、新しい方法はスレッド セーフです。</span><span class="sxs-lookup"><span data-stu-id="c5eb2-113">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span>  
  
 <span data-ttu-id="c5eb2-114">null 条件デリゲート呼び出し構文 `PropertyChanged?(e)` がないため、`Invoke` メソッドを明示的に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5eb2-114">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  <span data-ttu-id="c5eb2-115">それを許可するためのあいまいな解析状況が多すぎました。</span><span class="sxs-lookup"><span data-stu-id="c5eb2-115">There were too many ambiguous parsing situations to allow it.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="c5eb2-116">言語仕様</span><span class="sxs-lookup"><span data-stu-id="c5eb2-116">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 <span data-ttu-id="c5eb2-117">詳しくは、「[Visual Basic 言語リファレンス](../../../visual-basic/language-reference/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c5eb2-117">For more information, see the [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5eb2-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5eb2-118">See Also</span></span>  
 <span data-ttu-id="c5eb2-119">[?? (Null 合体演算子)](null-conditional-operator.md) </span><span class="sxs-lookup"><span data-stu-id="c5eb2-119">[?? (null-coalescing operator)](null-conditional-operator.md) </span></span>  
 <span data-ttu-id="c5eb2-120">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="c5eb2-120">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="c5eb2-121">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c5eb2-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c5eb2-122">[Visual Basic の言語リファレンス](../../../visual-basic/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="c5eb2-122">[Visual Basic Language Reference](../../../visual-basic/language-reference/index.md) </span></span>  
 [<span data-ttu-id="c5eb2-123">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="c5eb2-123">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
