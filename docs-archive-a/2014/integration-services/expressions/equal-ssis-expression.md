---
title: ==(같음)(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- equal operator (==)
- == (equal operator)
ms.assetid: 36fd2354-7b93-4c95-9cf3-51ee24568950
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 12f92a267543c366dee4905010aeb84d93c4f408
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732859"
---
# <a name="-equal-ssis-expression"></a><span data-ttu-id="fbfdc-102">==(같음)(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="fbfdc-102">== (Equal) (SSIS Expression)</span></span>
  <span data-ttu-id="fbfdc-103">두 식이 같은지 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-103">Performs a comparison to determine if two expressions are equal.</span></span> <span data-ttu-id="fbfdc-104">식 계산기는 비교를 수행하기 전에 많은 데이터 형식을 자동으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-104">The expression evaluator automatically converts many data types before it performs the comparison.</span></span> <span data-ttu-id="fbfdc-105">자세한 내용은 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-105">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
 <span data-ttu-id="fbfdc-106">그러나 일부 데이터 형식을 사용할 경우 식이 성공적으로 계산되려면 식에 명시적 캐스트가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-106">However, some data types require that the expression include an explicit cast before the expression can be evaluated successfully.</span></span> <span data-ttu-id="fbfdc-107">데이터 형식 간 올바른 캐스트에 대한 자세한 내용은 [캐스트&#40;SSIS 식&#41;](cast-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-107">For more information about legal casts between data types, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbfdc-108">구문</span><span class="sxs-lookup"><span data-stu-id="fbfdc-108">Syntax</span></span>  
  
```  
  
expression1 == expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="fbfdc-109">인수</span><span class="sxs-lookup"><span data-stu-id="fbfdc-109">Arguments</span></span>  
 <span data-ttu-id="fbfdc-110">*expression1, expression2*</span><span class="sxs-lookup"><span data-stu-id="fbfdc-110">*expression1, expression2*</span></span>  
 <span data-ttu-id="fbfdc-111">유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-111">Is any valid expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="fbfdc-112">결과 형식</span><span class="sxs-lookup"><span data-stu-id="fbfdc-112">Result Types</span></span>  
 <span data-ttu-id="fbfdc-113">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="fbfdc-113">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbfdc-114">설명</span><span class="sxs-lookup"><span data-stu-id="fbfdc-114">Remarks</span></span>  
 <span data-ttu-id="fbfdc-115">비교하는 두 식 중 하나가 Null이면 비교 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-115">If either expression in the comparison is null, the comparison result is null.</span></span> <span data-ttu-id="fbfdc-116">두 식이 모두 Null이면 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-116">If both expressions are null, the result is null.</span></span>  
  
 <span data-ttu-id="fbfdc-117">식 집합 *expression1* 및 *expression2*는 다음 규칙 중 하나를 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-117">The expression set, *expression1* and *expression2*, must follow one of these rules:</span></span>  
  
-   <span data-ttu-id="fbfdc-118">\**Numeric\*\*\*expression1* 및 *expression2* 모두 숫자 데이터 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-118">**Numeric** Both *expression1* and *expression2* must be a numeric data type.</span></span> <span data-ttu-id="fbfdc-119">데이터 형식의 교집합은 식 계산기가 수행하는 암시적 숫자 변환에 대한 규칙에 지정된 대로 숫자 데이터 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-119">The intersection of the data types must be a numeric data type, as specified in the rules about the implicit numeric conversions that the expression evaluator performs.</span></span> <span data-ttu-id="fbfdc-120">두 숫자 데이터 형식의 교집합은 Null일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-120">The intersection of the two numeric data types cannot be null.</span></span> <span data-ttu-id="fbfdc-121">자세한 내용은 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-121">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
-   <span data-ttu-id="fbfdc-122">\**Character\*\*\*expression1* 및 *expression2* 모두 DT_STR 또는 DT_WSTR 데이터 형식으로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-122">**Character** Both *expression1* and *expression2* must evaluate to either a DT_STR or a DT_WSTR data type.</span></span> <span data-ttu-id="fbfdc-123">두 식이 서로 다른 문자열 데이터 형식으로 계산될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-123">The two expressions can evaluate to different string data types.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fbfdc-124">문자열 비교는 대/소문자, 악센트, 일본어 가나 및 전자/반자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-124">String comparisons are case, accent, kana, and width-sensitive.</span></span>  
  
-   <span data-ttu-id="fbfdc-125">\**Date, Time 또는 Date/Time\*\*\*expression1* 및 *expression2* 모두는 DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET 또는 DT_FILETIME 데이터 형식 중 하나로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-125">**Date, Time, or Date/Time** Both *expression1* and *expression2* must evaluate to one of the following data types: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET, or DT_FILETIME.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fbfdc-126">시간 데이터 형식으로 계산되는 식과 날짜 또는 날짜/시간 데이터 형식 중 하나로 계산되는 식 사이의 비교는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-126">The system does not support comparisons between an expression that evaluates to a time data type and an expression that evaluates to either a date or a date/time data type.</span></span> <span data-ttu-id="fbfdc-127">시스템에서 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-127">The system generates an error.</span></span>  
  
     <span data-ttu-id="fbfdc-128">식을 비교하는 경우 시스템은 다음 변환 규칙을 나열된 순서대로 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-128">When comparing the expressions, the system applies the following conversion rules in the order listed:</span></span>  
  
    -   <span data-ttu-id="fbfdc-129">두 식이 같은 데이터 형식으로 계산되는 경우 해당 데이터 형식의 비교가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-129">When the two expressions evaluate to the same data type, a comparison of that data type is performed.</span></span>  
  
    -   <span data-ttu-id="fbfdc-130">하나의 식이 DT_DBTIMESTAMPOFFSET 데이터 형식인 경우 다른 식은 DT_DBTIMESTAMPOFFSET으로 암시적으로 변환되며 DT_DBTIMESTAMPOFFSET 비교가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-130">If one expression is a DT_DBTIMESTAMPOFFSET data type, the other expression is implicitly converted to DT_DBTIMESTAMPOFFSET and a DT_DBTIMESTAMPOFFSET comparison is performed.</span></span> <span data-ttu-id="fbfdc-131">자세한 내용은 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-131">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
    -   <span data-ttu-id="fbfdc-132">하나의 식이 DT_DBTIMESTAMP2 데이터 형식인 경우 다른 식은 DT_DBTIMESTAMP2로 암시적으로 변환되며 DT_DBTIMESTAMP2 비교가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-132">If one expression is a DT_DBTIMESTAMP2 data type, the other expression is implicitly converted to DT_DBTIMESTAMP2 and a DT_DBTIMESTAMP2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="fbfdc-133">하나의 식이 DT_DBTIME2 데이터 형식인 경우 다른 식은 DT_DBTIME2로 암시적으로 변환되며 DT_DBTIME2 비교가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-133">If one expression is a DT_DBTIME2 data type, the other expression is implicitly converted to DT_DBTIME2, and a DT_DBTIME2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="fbfdc-134">하나의 식이 DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2 또는 DT_DBTIME2 이외의 형식인 경우 다른 식은 DT_DBTIMESTAMP 데이터 형식으로 변환되어 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-134">If one expression is of a type other than DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2, or DT_DBTIME2, the expressions are converted to the DT_DBTIMESTAMP data type before they are compared.</span></span>  
  
     <span data-ttu-id="fbfdc-135">식을 비교할 때 시스템에서는 다음과 같이 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-135">When comparing the expressions, the system makes the following assumptions:</span></span>  
  
    -   <span data-ttu-id="fbfdc-136">각 식이 소수 자릿수 초를 포함하는 데이터 형식인 경우 시스템은 소수 자릿수 초의 자릿수가 가장 적은 데이터 형식의 나머지 자릿수를 0으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-136">If each expression is a data type that includes fractional seconds, the system assumes that the data type with the least number of digits for fractional seconds has zeros for the remaining digits.</span></span>  
  
    -   <span data-ttu-id="fbfdc-137">각 식이 날짜 데이터 형식이고 이 중 하나에만 표준 시간대 오프셋이 있는 경우 시스템은 표준 시간대 오프셋이 없는 날짜 데이터 형식을 UTC(Coordinated Universal Time)로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-137">If each expression is a date data type, but only one has a time zone offset, the system assumes that the date data type without the time zone offset is in Coordinated Universal Time (UTC).</span></span>  
  
-   <span data-ttu-id="fbfdc-138">\**Logical\*\*\*expression1* 과 *expression2* 는 모두 부울로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-138">**Logical** Both *expression1* and *expression2* must evaluate to a Boolean.</span></span>  
  
-   <span data-ttu-id="fbfdc-139">\**GUID\*\*\*expression1* 및 *expression2* 모두 DT_GUID 데이터 형식으로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-139">**GUID** Both *expression1* and *expression2* must evaluate to the DT_GUID data type.</span></span>  
  
-   <span data-ttu-id="fbfdc-140">\**Binary\*\*\*expression1* 및 *expression2* 모두 DT_BYTES 데이터 형식으로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-140">**Binary** Both *expression1* and *expression2* must evaluate to the DT_BYTES data type.</span></span>  
  
-   <span data-ttu-id="fbfdc-141">\**BLOB\*\*\*expression1* 및 *expression2* 모두 동일한 BLOB(Binary Large Object Block) 데이터 형식 DT_TEXT, DT_NTEXT 또는 DT_IMAGE로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-141">**BLOB** Both *expression1* and *expression2* must evaluate to the same Binary Large Object Block (BLOB) data type: DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span>  
  
 <span data-ttu-id="fbfdc-142">데이터 형식에 대한 자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-142">For more information about data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="fbfdc-143">식 예</span><span class="sxs-lookup"><span data-stu-id="fbfdc-143">Expression Examples</span></span>  
 <span data-ttu-id="fbfdc-144">현재 날짜가 2003년 7월 4일이면 이 예는 TRUE가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-144">This example evaluates to TRUE if the current date is July 4, 2003.</span></span> <span data-ttu-id="fbfdc-145">자세한 내용은 [GETDATE&#40;SSIS 식&#41;](getdate-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-145">For more information, see [GETDATE &#40;SSIS Expression&#41;](getdate-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="fbfdc-146">"7/4/2003" == GETDATE()</span><span class="sxs-lookup"><span data-stu-id="fbfdc-146">"7/4/2003" == GETDATE()</span></span>  
  
 <span data-ttu-id="fbfdc-147">**ListPrice** 열의 값이 500이면 이 예는 TRUE가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-147">This example evaluates to TRUE if the value in the **ListPrice** column is 500.</span></span>  
  
```  
ListPrice == 500  
```  
  
 <span data-ttu-id="fbfdc-148">이 예에서는 변수 **LPrice**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-148">This example uses the variable **LPrice**.</span></span> <span data-ttu-id="fbfdc-149">**LPrice** 의 값이 500보다 크면 이 예는 TRUE가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-149">It evaluates to TRUE if the value of **LPrice** is 500.</span></span> <span data-ttu-id="fbfdc-150">식을 구문 분석하려면 변수의 데이터 형식이 숫자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfdc-150">The data type of the variable must be numeric for the expression to parse successfully.</span></span>  
  
```  
@LPrice == 500  
```  
  
## <a name="see-also"></a><span data-ttu-id="fbfdc-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fbfdc-151">See Also</span></span>  
 <span data-ttu-id="fbfdc-152">[\!= &#40;같지 않음&#41;&#40;SSIS 식&#41;](equal-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="fbfdc-152">[!= &#40;Unequal&#41; &#40;SSIS Expression&#41;](equal-ssis-expression.md) </span></span>  
 <span data-ttu-id="fbfdc-153">[연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="fbfdc-153">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="fbfdc-154">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="fbfdc-154">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
