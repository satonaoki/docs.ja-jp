---
title: Mailaddressparc Ser クラス (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.MailAddressParser
- System.Net.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 2c17970614ff9b6f1e6793a064a956da7248d693
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990541"
---
# <a name="mailaddressparser-class"></a><span data-ttu-id="120c1-102">Mailaddressparc Ser クラス</span><span class="sxs-lookup"><span data-stu-id="120c1-102">MailAddressParser class</span></span>

<span data-ttu-id="120c1-103">RFC 2822 で説明されているように、電子メールアドレスを解析します。</span><span class="sxs-lookup"><span data-stu-id="120c1-103">Parses email addresses as described in RFC 2822.</span></span> <span data-ttu-id="120c1-104">このクラスは継承できません。</span><span class="sxs-lookup"><span data-stu-id="120c1-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> <span data-ttu-id="120c1-105">このクラスは内部的なものであり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="120c1-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="120c1-106">Microsoft では、どのような状況でも、実稼働アプリケーションでのこのクラスの使用はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="120c1-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="parseaddress-method"></a><span data-ttu-id="120c1-107">ParseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="120c1-107">ParseAddress method</span></span>

<span data-ttu-id="120c1-108">指定した文字列から1つの電子メールアドレスを解析します。</span><span class="sxs-lookup"><span data-stu-id="120c1-108">Parses a single email address from the specified string.</span></span>

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a><span data-ttu-id="120c1-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="120c1-109">Parameters</span></span>

<span data-ttu-id="120c1-110">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="120c1-110">`data` <xref:System.String></span></span>

<span data-ttu-id="120c1-111">解析する電子メールアドレスを含む文字列。</span><span class="sxs-lookup"><span data-stu-id="120c1-111">The string that contains an email address to be parsed.</span></span>

### <a name="return-value"></a><span data-ttu-id="120c1-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="120c1-112">Return value</span></span>

<xref:System.Net.Mail.MailAddress>

<span data-ttu-id="120c1-113">有効な電子メールアドレス。</span><span class="sxs-lookup"><span data-stu-id="120c1-113">A valid email address.</span></span>

### <a name="exceptions"></a><span data-ttu-id="120c1-114">例外</span><span class="sxs-lookup"><span data-stu-id="120c1-114">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="120c1-115">電子メールアドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="120c1-115">The email address is invalid.</span></span>

## <a name="requirements"></a><span data-ttu-id="120c1-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="120c1-116">Requirements</span></span>

<span data-ttu-id="120c1-117">**名前空間:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="120c1-117">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="120c1-118">**アセンブリ:** システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="120c1-118">**Assembly:** System (in System.dll)</span></span>