---
title: 식의 연산자(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d22dc8b6-4353-40e7-91a1-65e8dae6325d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fa8042df39e535425a05414c1e39ee6a12ff2f39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650729"
---
# <a name="operators-in-expressions-report-builder-and-ssrs"></a><span data-ttu-id="f0c5c-102">식의 연산자(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f0c5c-102">Operators in Expressions (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f0c5c-103">연산자는 식에서 한 개 이상의 항목에 적용되는 동작을 나타내는 기호입니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-103">An operator is a symbol that represents actions applied to one or more terms in an expression.</span></span> <span data-ttu-id="f0c5c-104">식에서 지원되는 연산자의 범주는 산술 연산자, 비교 연산자, 연결 연산자, 논리 또는 비트 연산자, 비트 시프트 연산자입니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-104">The following categories of operators are supported in an expression: arithmetic, comparison, concatenation, logical or bitwise, and bit shift.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="arithmetic"></a><span data-ttu-id="f0c5c-105">산술</span><span class="sxs-lookup"><span data-stu-id="f0c5c-105">Arithmetic</span></span>  
 <span data-ttu-id="f0c5c-106">산술 연산자는 식에서 두 숫자 항목에 대한 수치 연산을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-106">Arithmetic operators perform mathematical operations on two numeric terms in an expression.</span></span>  
  
|<span data-ttu-id="f0c5c-107">연산자</span><span class="sxs-lookup"><span data-stu-id="f0c5c-107">Operator</span></span>|<span data-ttu-id="f0c5c-108">Description</span><span class="sxs-lookup"><span data-stu-id="f0c5c-108">Description</span></span>|  
|--------------|-----------------|  
|^|<span data-ttu-id="f0c5c-109">특정 숫자를 다른 숫자의 승수로 거듭제곱합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-109">Raises a number to the power of another number.</span></span>|  
|*|<span data-ttu-id="f0c5c-110">두 숫자를 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-110">Multiplies two numbers.</span></span>|  
|/|<span data-ttu-id="f0c5c-111">두 숫자를 나누고 부동 소수점 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-111">Divides two numbers and returns a floating-point result.</span></span>|  
|<span data-ttu-id="f0c5c-112">\|두 숫자를 나누고 정수 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-112">\|Divides two numbers and returns an integer result.</span></span>|  
|<span data-ttu-id="f0c5c-113">Mod</span><span class="sxs-lookup"><span data-stu-id="f0c5c-113">Mod</span></span>|<span data-ttu-id="f0c5c-114">나누기의 정수 나머지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-114">Returns the integer remainder of a division.</span></span> <span data-ttu-id="f0c5c-115">예를 들어 7을 5로 나누면 나머지가 2이므로 7 Mod 5는 2입니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-115">For example, 7 Mod 5 = 2 because the remainder of 7 divided by 5 is 2.</span></span>|  
|+|<span data-ttu-id="f0c5c-116">두 수를 더합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-116">Adds two numbers together.</span></span>|  
|-|<span data-ttu-id="f0c5c-117">두 숫자 사이의 차를 반환하거나 숫자 항목의 음수 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-117">Returns the difference between two numbers or indicates the negative value of a numeric term.</span></span>|  
  
### <a name="comparison"></a><span data-ttu-id="f0c5c-118">비교</span><span class="sxs-lookup"><span data-stu-id="f0c5c-118">Comparison</span></span>  
 <span data-ttu-id="f0c5c-119">비교 연산자는 두 식이 동일한지 여부를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-119">Comparison operators test whether two expressions are the same.</span></span>  
  
|<span data-ttu-id="f0c5c-120">연산자</span><span class="sxs-lookup"><span data-stu-id="f0c5c-120">Operator</span></span>|<span data-ttu-id="f0c5c-121">Description</span><span class="sxs-lookup"><span data-stu-id="f0c5c-121">Description</span></span>|  
|--------------|-----------------|  
|<|<span data-ttu-id="f0c5c-122">보다 작음</span><span class="sxs-lookup"><span data-stu-id="f0c5c-122">Less than.</span></span>|  
|\<=|<span data-ttu-id="f0c5c-123">작거나 같음</span><span class="sxs-lookup"><span data-stu-id="f0c5c-123">Less than or equal to.</span></span>|  
|>|<span data-ttu-id="f0c5c-124">보다 큼</span><span class="sxs-lookup"><span data-stu-id="f0c5c-124">Greater than.</span></span>|  
|>=|<span data-ttu-id="f0c5c-125">크거나 같음</span><span class="sxs-lookup"><span data-stu-id="f0c5c-125">Greater than or equal to.</span></span>|  
|=|<span data-ttu-id="f0c5c-126">같음</span><span class="sxs-lookup"><span data-stu-id="f0c5c-126">Equal to.</span></span>|  
|<>|<span data-ttu-id="f0c5c-127">같지 않음 -</span><span class="sxs-lookup"><span data-stu-id="f0c5c-127">Not equal to.</span></span>|  
|<span data-ttu-id="f0c5c-128">Like</span><span class="sxs-lookup"><span data-stu-id="f0c5c-128">Like</span></span>|<span data-ttu-id="f0c5c-129">특정 문자열이 지정된 패턴과 일치하는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-129">Determines whether a specific character string matches a specified pattern.</span></span> <span data-ttu-id="f0c5c-130">패턴은 일반 문자와 와일드카드 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-130">A pattern can include regular characters and wildcard characters.</span></span> <span data-ttu-id="f0c5c-131">패턴 일치에서 일반 문자는 문자열에 지정된 문자와 정확하게 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-131">During pattern matching, regular characters must exactly match the characters specified in the character string.</span></span> <span data-ttu-id="f0c5c-132">그러나 와일드카드 문자는 문자열에서 어느 한 부분만 일치하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-132">However, wildcard characters can be matched with arbitrary fragments of the character string.</span></span> <span data-ttu-id="f0c5c-133">LIKE 연산자에 와일드카드 문자를 사용할 경우 = 및 != 문자열 비교 연산자를 사용하는 것보다 훨씬 융통성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-133">Using wildcard characters makes the LIKE operator more flexible than using the = and != string comparison operators.</span></span><br /><br /> <span data-ttu-id="f0c5c-134">다음은 와일드 카드로 사용할 수 있는 문자를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-134">The following lists characters that can be used as wildcards:</span></span><br /><br /> <span data-ttu-id="f0c5c-135">**%**: 0 개 이상의 문자를 가진 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-135">**%**: Any string of zero or more characters.</span></span><br /><br /> <span data-ttu-id="f0c5c-136">**_**: 단일 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-136">**_**: Any single character.</span></span><br /><br /> <span data-ttu-id="f0c5c-137">**[]**: 지정 된 범위 (예: [a-f]) 또는 집합 (예: [aeiou])에 있는 단일 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-137">**[ ]**: Any single character within the specified range (for example, [a-f]) or set (for example, [aeiou]).</span></span><br /><br /> <span data-ttu-id="f0c5c-138">**[^]**: 지정 된 범위 (예: [^ a-f]) 또는 집합 (예: [^ aeiou])에 속하지 않는 단일 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-138">**[^]**: Any single character not within the specified range (for example, [^a-f]) or set (for example, [^aeiou]).</span></span>|  
|<span data-ttu-id="f0c5c-139">Is</span><span class="sxs-lookup"><span data-stu-id="f0c5c-139">Is</span></span>|<span data-ttu-id="f0c5c-140">두 개체 참조를 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-140">Compares two object references.</span></span>|  
  
### <a name="string-concatenation"></a><span data-ttu-id="f0c5c-141">문자열 연결</span><span class="sxs-lookup"><span data-stu-id="f0c5c-141">String Concatenation</span></span>  
 <span data-ttu-id="f0c5c-142">문자열 연결은 식에서 첫 번째 문자열에 두 번째 문자열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-142">String concatenation appends the second string to the first string in an expression.</span></span> <span data-ttu-id="f0c5c-143">다른 문자열 연산의 경우 기본 제공 함수를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-143">For other string operations, use built-in functions.</span></span>  
  
|<span data-ttu-id="f0c5c-144">연산자</span><span class="sxs-lookup"><span data-stu-id="f0c5c-144">Operator</span></span>|<span data-ttu-id="f0c5c-145">Description</span><span class="sxs-lookup"><span data-stu-id="f0c5c-145">Description</span></span>|  
|--------------|-----------------|  
|&|<span data-ttu-id="f0c5c-146">두 문자열을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-146">Concatenates two strings</span></span>|  
|+|<span data-ttu-id="f0c5c-147">두 문자열을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-147">Concatenates two strings</span></span>|  
  
### <a name="logical-and-bitwise"></a><span data-ttu-id="f0c5c-148">논리 및 비트</span><span class="sxs-lookup"><span data-stu-id="f0c5c-148">Logical and Bitwise</span></span>  
 <span data-ttu-id="f0c5c-149">논리 및 비트 연산자는 식에서 두 정수 항목 사이의 논리 조작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-149">Logical and bitwise operators perform logical manipulations between two integer terms in an expression.</span></span>  
  
|<span data-ttu-id="f0c5c-150">연산자</span><span class="sxs-lookup"><span data-stu-id="f0c5c-150">Operator</span></span>|<span data-ttu-id="f0c5c-151">Description</span><span class="sxs-lookup"><span data-stu-id="f0c5c-151">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="f0c5c-152">and</span><span class="sxs-lookup"><span data-stu-id="f0c5c-152">And</span></span>|<span data-ttu-id="f0c5c-153">두 부울 식에 논리 결합을 수행하거나 두 숫자 식에 비트 결합을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-153">Performs a logical conjunction on two Boolean expressions, or bitwise conjunction on two numeric expressions.</span></span>|  
|<span data-ttu-id="f0c5c-154">Not</span><span class="sxs-lookup"><span data-stu-id="f0c5c-154">Not</span></span>|<span data-ttu-id="f0c5c-155">부울 식에 논리 부정을 수행하거나 숫자 식에 비트 부정을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-155">Performs logical negation on a Boolean expression, or bitwise negation on a numeric expression.</span></span>|  
|<span data-ttu-id="f0c5c-156">또는</span><span class="sxs-lookup"><span data-stu-id="f0c5c-156">Or</span></span>|<span data-ttu-id="f0c5c-157">두 부울 식에 논리 분리를 수행하거나 두 숫자 값에 비트 분리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-157">Performs a logical disjunction on two Boolean expressions, or bitwise disjunction on two numeric values.</span></span>|  
|<span data-ttu-id="f0c5c-158">Xor</span><span class="sxs-lookup"><span data-stu-id="f0c5c-158">Xor</span></span>|<span data-ttu-id="f0c5c-159">두 부울 식에 논리 제외 연산을 수행하거나 두 숫자 식에 비트 제외를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-159">Performs a logical exclusion operation on two Boolean expressions, or a bitwise exclusion on two numeric expressions.</span></span>|  
|<span data-ttu-id="f0c5c-160">AndAlso</span><span class="sxs-lookup"><span data-stu-id="f0c5c-160">AndAlso</span></span>|<span data-ttu-id="f0c5c-161">두 식에 논리 결합을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-161">Performs logical conjunction on two expressions.</span></span>|  
|<span data-ttu-id="f0c5c-162">OrElse</span><span class="sxs-lookup"><span data-stu-id="f0c5c-162">OrElse</span></span>|<span data-ttu-id="f0c5c-163">두 식에 논리 분리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-163">Performs logical disjunction on two expressions.</span></span>|  
  
### <a name="bit-shift"></a><span data-ttu-id="f0c5c-164">비트 시프트</span><span class="sxs-lookup"><span data-stu-id="f0c5c-164">Bit Shift</span></span>  
 <span data-ttu-id="f0c5c-165">비트 연산자는 식에서 두 정수 항목 사이에 비트 조작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-165">Bitwise operators perform bit manipulations between two integer terms in an expression.</span></span>  
  
|<span data-ttu-id="f0c5c-166">연산자</span><span class="sxs-lookup"><span data-stu-id="f0c5c-166">Operator</span></span>|<span data-ttu-id="f0c5c-167">Description</span><span class="sxs-lookup"><span data-stu-id="f0c5c-167">Description</span></span>|  
|--------------|-----------------|  
|<\<|<span data-ttu-id="f0c5c-168">비트 패턴에 산술 왼쪽 시프트를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-168">Performs an arithmetic left-shift on a bit pattern.</span></span>|  
|>>|<span data-ttu-id="f0c5c-169">비트 패턴에 산술 오른쪽 시프트를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c5c-169">Performs an arithmetic right-shift on a bit pattern.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0c5c-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f0c5c-170">See Also</span></span>  
 <span data-ttu-id="f0c5c-171">[식 대화 상자](../expression-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="f0c5c-171">[Expression Dialog Box](../expression-dialog-box.md) </span></span>  
 <span data-ttu-id="f0c5c-172">[식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f0c5c-172">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f0c5c-173">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f0c5c-173">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f0c5c-174">[식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](data-types-in-expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f0c5c-174">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](data-types-in-expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f0c5c-175">식 대화 상자&#40;보고서 작성기&#41;</span><span class="sxs-lookup"><span data-stu-id="f0c5c-175">Expression Dialog Box &#40;Report Builder&#41;</span></span>](../expression-dialog-box-report-builder.md)  
  
  
