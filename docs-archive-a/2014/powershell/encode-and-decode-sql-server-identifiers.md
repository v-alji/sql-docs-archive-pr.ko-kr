---
title: SQL Server 식별자 인코딩 및 디코딩 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: bb9fe0d3-e432-42d3-b324-64dc908b544a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 88e7ebbc81d9c3cb91b1bf678075c5b5d0884890
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729548"
---
# <a name="encode-and-decode-sql-server-identifiers"></a><span data-ttu-id="680fe-102">SQL Server 식별자 인코딩 및 디코딩</span><span class="sxs-lookup"><span data-stu-id="680fe-102">Encode and Decode SQL Server Identifiers</span></span>
  <span data-ttu-id="680fe-103">SQL Server 구분 식별자에 Windows PowerShell 경로 이름에서 지원되지 않는 문자가 사용되는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="680fe-103">SQL Server delimited identifiers sometimes contain characters not supported in Windows PowerShell paths.</span></span> <span data-ttu-id="680fe-104">이러한 문자는 16진수 값을 인코딩하여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="680fe-104">These characters can be specified by encoding their hexadecimal values.</span></span>  
  
1.  <span data-ttu-id="680fe-105">**시작하기 전에:**  [제한 사항](#LimitationsRestrictions)</span><span class="sxs-lookup"><span data-stu-id="680fe-105">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions)</span></span>  
  
2.  <span data-ttu-id="680fe-106">**특수 문자를 처리하려면:**  [식별자 인코딩](#EncodeIdent), [식별자 디코딩](#DecodeIdent)</span><span class="sxs-lookup"><span data-stu-id="680fe-106">**To process special characters:**  [Encoding an Identifier](#EncodeIdent), [Decoding an Identifier](#DecodeIdent)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="680fe-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="680fe-107">Before You Begin</span></span>  
 <span data-ttu-id="680fe-108">Windows PowerShell 경로 이름에서 지원 되지 않는 문자는 "%" 문자 뒤에 문자를 나타내는 비트 패턴의 16 진수 값 ("xx")으로 표시 되거나 인코딩될 수 있습니다 **%** .</span><span class="sxs-lookup"><span data-stu-id="680fe-108">Characters that are not supported in Windows PowerShell path names can be represented, or encoded, as the "%" character followed by the hexadecimal value for the bit pattern that represents the character, as in "**%** xx".</span></span> <span data-ttu-id="680fe-109">인코딩은 Windows PowerShell 경로에 지원되지 않는 모든 문자를 처리하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="680fe-109">Encoding can always be used to handle characters that are not supported in Windows PowerShell paths.</span></span>  
  
 <span data-ttu-id="680fe-110">**Encode-SqlName** cmdlet은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 식별자를 입력으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="680fe-110">The **Encode-SqlName** cmdlet takes as input a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifier.</span></span> <span data-ttu-id="680fe-111">Windows PowerShell 언어에서 지원하지 않는 모든 문자를 "%xx"로 인코딩하여 문자열을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="680fe-111">It outputs a string with all the characters that are not supported by the Windows PowerShell language encoded with "%xx".</span></span> <span data-ttu-id="680fe-112">**Decode-SqlName** cmdlet은 인코딩된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 식별자를 입력으로 사용하고 원래 식별자를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="680fe-112">The **Decode-SqlName** cmdlet takes as input an encoded [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifier and returns the original identifier.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="680fe-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="680fe-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="680fe-114">`Encode-Sqlname` 및 `Decode-Sqlname` cmdlet은 SQL Server 구분 식별자에서 허용되지만 PowerShell 경로에서 지원되지 않는 문자만 인코딩하거나 디코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="680fe-114">The `Encode-Sqlname` and `Decode-Sqlname` cmdlets only encode or decode the characters that are allowed in SQL Server delimited identifiers, but are not supported in PowerShell paths.</span></span> <span data-ttu-id="680fe-115">**Encode-SqlName** 으로 인코딩되고 **Decode-SqlName**으로 디코딩된 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="680fe-115">These are the characters encoded by **Encode-SqlName** and decoded by **Decode-SqlName**:</span></span>  
  
|||||||||||||  
|-|-|-|-|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="680fe-116">**문자**</span><span class="sxs-lookup"><span data-stu-id="680fe-116">**Character**</span></span>|\ |/|<span data-ttu-id="680fe-117">:</span><span class="sxs-lookup"><span data-stu-id="680fe-117">:</span></span>|%|\<|>|*|<span data-ttu-id="680fe-118">?</span><span class="sxs-lookup"><span data-stu-id="680fe-118">?</span></span>|<span data-ttu-id="680fe-119">[</span><span class="sxs-lookup"><span data-stu-id="680fe-119">[</span></span>|<span data-ttu-id="680fe-120">]</span><span class="sxs-lookup"><span data-stu-id="680fe-120">]</span></span>|<span data-ttu-id="680fe-121">&#124;</span><span class="sxs-lookup"><span data-stu-id="680fe-121">&#124;</span></span>|  
|<span data-ttu-id="680fe-122">**16진수 인코딩**</span><span class="sxs-lookup"><span data-stu-id="680fe-122">**Hexadecimal Encoding**</span></span>|<span data-ttu-id="680fe-123">%5C</span><span class="sxs-lookup"><span data-stu-id="680fe-123">%5C</span></span>|<span data-ttu-id="680fe-124">%2F</span><span class="sxs-lookup"><span data-stu-id="680fe-124">%2F</span></span>|<span data-ttu-id="680fe-125">%3A</span><span class="sxs-lookup"><span data-stu-id="680fe-125">%3A</span></span>|<span data-ttu-id="680fe-126">%25</span><span class="sxs-lookup"><span data-stu-id="680fe-126">%25</span></span>|<span data-ttu-id="680fe-127">%3C</span><span class="sxs-lookup"><span data-stu-id="680fe-127">%3C</span></span>|<span data-ttu-id="680fe-128">%3E</span><span class="sxs-lookup"><span data-stu-id="680fe-128">%3E</span></span>|<span data-ttu-id="680fe-129">%2A</span><span class="sxs-lookup"><span data-stu-id="680fe-129">%2A</span></span>|<span data-ttu-id="680fe-130">%3F</span><span class="sxs-lookup"><span data-stu-id="680fe-130">%3F</span></span>|<span data-ttu-id="680fe-131">%5B</span><span class="sxs-lookup"><span data-stu-id="680fe-131">%5B</span></span>|<span data-ttu-id="680fe-132">%5D</span><span class="sxs-lookup"><span data-stu-id="680fe-132">%5D</span></span>|<span data-ttu-id="680fe-133">%7C</span><span class="sxs-lookup"><span data-stu-id="680fe-133">%7C</span></span>|  
  
##  <a name="encoding-an-identifier"></a><a name="EncodeIdent"></a> <span data-ttu-id="680fe-134">식별자 인코딩</span><span class="sxs-lookup"><span data-stu-id="680fe-134">Encoding an Identifier</span></span>  
 <span data-ttu-id="680fe-135">**PowerShell 경로에서 SQL Server 식별자를 인코딩하려면**</span><span class="sxs-lookup"><span data-stu-id="680fe-135">**To encode a SQL Server identifier in a PowerShell path**</span></span>  
  
-   <span data-ttu-id="680fe-136">두 방법 중 하나를 사용하여 SQL Server 식별자를 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="680fe-136">Use one of two methods to encode a SQL Server identifier:</span></span>  
  
    -   <span data-ttu-id="680fe-137">%XX 구문을 사용하여 지원되지 않는 문자에 대한 16진수 코드를 지정합니다. 여기서 XX는 16진수 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="680fe-137">Specify the hexadecimal code for the unsupported character using the syntax %XX, where XX is the hexadecimal code.</span></span>  
  
    -   <span data-ttu-id="680fe-138">따옴표로 묶인 식별자를 `Encode-Sqlname` cmdlet에 전달</span><span class="sxs-lookup"><span data-stu-id="680fe-138">Pass the identifier as a quoted string to the `Encode-Sqlname` cmdlet</span></span>  
  
### <a name="examples-encoding"></a><span data-ttu-id="680fe-139">예(인코딩)</span><span class="sxs-lookup"><span data-stu-id="680fe-139">Examples (Encoding)</span></span>  
 <span data-ttu-id="680fe-140">이 예에서는 ":" 문자의 인코딩된 버전(%3A)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="680fe-140">This example specifies the encoded version of the ":" character (%3A):</span></span>  
  
```  
Set-Location Table%3ATest  
```  
  
 <span data-ttu-id="680fe-141">또는 **Encode-SqlName** 을 사용하여 Windows PowerShell에서 지원되는 이름을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="680fe-141">Alternatively, you can use **Encode-SqlName** to build a name supported by Windows PowerShell:</span></span>  
  
```powershell
Set-Location (Encode-SqlName "Table:Test")  
```  
  
##  <a name="decoding-an-identifier"></a><a name="DecodeIdent"></a> <span data-ttu-id="680fe-142">식별자 디코딩</span><span class="sxs-lookup"><span data-stu-id="680fe-142">Decoding an Identifier</span></span>  
 <span data-ttu-id="680fe-143">**PowerShell 경로에서 SQL Server 식별자를 디코딩하려면**</span><span class="sxs-lookup"><span data-stu-id="680fe-143">**To decode a SQL Server identifier from a PowerShell path**</span></span>  
  
 <span data-ttu-id="680fe-144">`Decode-Sqlname` cmdlet을 사용하여 16진수 인코딩을 인코딩에 의해 표시되는 문자로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="680fe-144">Use the `Decode-Sqlname` cmdlet to replace the hexadecimal encodings with the characters represented by the encoding.</span></span>  
  
### <a name="examples-decoding"></a><span data-ttu-id="680fe-145">예(디코딩)</span><span class="sxs-lookup"><span data-stu-id="680fe-145">Examples (Decoding)</span></span>  
 <span data-ttu-id="680fe-146">이 예제에서는 "Table:Test"를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="680fe-146">This example returns "Table:Test":</span></span>  
  
```powershell
Decode-SqlName "Table%3ATest"  
```  
  
## <a name="see-also"></a><span data-ttu-id="680fe-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="680fe-147">See Also</span></span>  
 <span data-ttu-id="680fe-148">[PowerShell에서 SQL Server 식별자](sql-server-identifiers-in-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="680fe-148">[SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md) </span></span>  
 <span data-ttu-id="680fe-149">[SQL Server PowerShell 공급자](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="680fe-149">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="680fe-150">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="680fe-150">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
