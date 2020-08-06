---
title: '? :(조건부)(SSIS 식) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- conditional operator (?:)
- '?: (conditional operator)'
ms.assetid: d38e6890-7338-4ce0-a837-2dbb41823a37
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e607f9ed495184ef47ac2e4f1139b9a9566055ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660696"
---
# <a name="--conditional-ssis-expression"></a><span data-ttu-id="cf989-103">?</span><span class="sxs-lookup"><span data-stu-id="cf989-103">?</span></span> <span data-ttu-id="cf989-104">: (조건부)(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="cf989-104">: (Conditional) (SSIS Expression)</span></span>
  <span data-ttu-id="cf989-105">부울 식의 계산에 따라 두 식 중 하나를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-105">Returns one of two expressions based on the evaluation of a Boolean expression.</span></span> <span data-ttu-id="cf989-106">부울 식이 TRUE이면 첫 번째 식이 계산되고 반환 결과는 식의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-106">If the Boolean expression evaluates to TRUE, then the first expression is evaluated and the result is the expression result.</span></span> <span data-ttu-id="cf989-107">부울 식이 FALSE이면 두 번째 식이 계산되고 반환 결과는 식의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-107">If the Boolean expression evaluates to FALSE then the second expression is evaluated and its result is the expression result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf989-108">구문</span><span class="sxs-lookup"><span data-stu-id="cf989-108">Syntax</span></span>  
  
```  
  
boolean_expression?expression1:expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="cf989-109">인수</span><span class="sxs-lookup"><span data-stu-id="cf989-109">Arguments</span></span>  
 <span data-ttu-id="cf989-110">*boolean_expression*</span><span class="sxs-lookup"><span data-stu-id="cf989-110">*boolean_expression*</span></span>  
 <span data-ttu-id="cf989-111">TRUE, FALSE 또는 NULL로 계산되는 임의의 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-111">Is any valid expression that evaluates to TRUE, FALSE, or NULL.</span></span>  
  
 <span data-ttu-id="cf989-112">*expression1*</span><span class="sxs-lookup"><span data-stu-id="cf989-112">*expression1*</span></span>  
 <span data-ttu-id="cf989-113">유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-113">Is any valid expression.</span></span>  
  
 <span data-ttu-id="cf989-114">*expression2*</span><span class="sxs-lookup"><span data-stu-id="cf989-114">*expression2*</span></span>  
 <span data-ttu-id="cf989-115">유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-115">Is any valid expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="cf989-116">결과 형식</span><span class="sxs-lookup"><span data-stu-id="cf989-116">Result Types</span></span>  
 <span data-ttu-id="cf989-117">*expression1* 또는 *expression2*의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-117">The data type of *expression1* or *expression2*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf989-118">설명</span><span class="sxs-lookup"><span data-stu-id="cf989-118">Remarks</span></span>  
 <span data-ttu-id="cf989-119">*boolean_expression* 이 NULL이면 식 결과도 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-119">If the *boolean_expression* evaluates to NULL, the expression result is NULL.</span></span> <span data-ttu-id="cf989-120">*expression1* 또는 *expression2* 중에서 선택한 식이 NULL이면 결과도 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-120">If a selected expression, either *expression1* or *expression2* is NULL, the result is NULL.</span></span> <span data-ttu-id="cf989-121">선택한 식은 NULL이 아니지만 선택하지 않은 식이 NULL이면 결과는 선택한 식의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-121">If a selected expression is not NULL, but the one not selected is NULL, the result is the value of the selected expression.</span></span>  
  
 <span data-ttu-id="cf989-122">*expression1* 및 *expression2* 의 데이터 형식이 같으면 결과도 해당 데이터 형식이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-122">If *expression1* and *expression2* have the same data type, the result is that data type.</span></span> <span data-ttu-id="cf989-123">다음은 결과 형식에 적용되는 추가 규칙입니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-123">The following additional rules apply to result types:</span></span>  
  
-   <span data-ttu-id="cf989-124">DT_TEXT 데이터 형식은 *expression1* 및 *expression2* 의 코드 페이지가 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-124">The DT_TEXT data type requires that *expression1* and *expression2* have the same code page.</span></span>  
  
-   <span data-ttu-id="cf989-125">DT_BYTES 데이터 형식의 결과 길이는 둘 중에서 긴 인수의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-125">The length of a result with the DT_BYTES data type is the length of the longer argument.</span></span>  
  
 <span data-ttu-id="cf989-126">식 집합 *expression1* 및 *expression2*는 유효한 데이터 형식으로 계산되고 다음 규칙 중 하나를 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-126">The expression set, *expression1* and *expression2*, must evaluate to valid data types and follow one of these rules:</span></span>  
  
-   <span data-ttu-id="cf989-127">\**Numeric\*\*\*expression1* 및 *expression2* 모두 숫자 데이터 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-127">**Numeric** Both *expression1* and *expression2* must be a numeric data type.</span></span> <span data-ttu-id="cf989-128">데이터 형식의 교집합은 식 계산기가 수행하는 암시적 숫자 변환에 대한 규칙에 지정된 대로 숫자 데이터 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-128">The intersection of the data types must be a numeric data type as specified in the rules about the implicit numeric conversions that the expression evaluator performs.</span></span> <span data-ttu-id="cf989-129">두 숫자 데이터 형식의 교집합은 Null일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-129">The intersection of the two numeric data types cannot be null.</span></span> <span data-ttu-id="cf989-130">자세한 내용은 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf989-130">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
-   <span data-ttu-id="cf989-131">\**String\*\*\*expression1* 및 *expression2* 모두 문자열 데이터 형식(DT_STR 또는 DT_WSTR)이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-131">**String** Both *expression1* and *expression2* must be a string data type: DT_STR or DT_WSTR.</span></span> <span data-ttu-id="cf989-132">두 식이 서로 다른 문자열 데이터 형식으로 계산될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-132">The two expressions can evaluate to different string data types.</span></span> <span data-ttu-id="cf989-133">결과는 DT_WSTR 데이터 형식으로 둘 중에서 긴 인수의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-133">The result has the DT_WSTR data type with a length of the longer argument.</span></span>  
  
-   <span data-ttu-id="cf989-134">\**Date, Time 또는 Date/Time\*\*\*expression1* 및 *expression2* 모두는 DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET 또는 DT_FILETIME 데이터 형식 중 하나로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-134">**Date, Time, or Date/Time** Both *expression1* and *expression2* must evaluate to one of the following data types: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET, or DT_FILETIME.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cf989-135">시간 데이터 형식으로 계산되는 식과 날짜 또는 날짜/시간 데이터 형식 중 하나로 계산되는 식 사이의 비교는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-135">The system does not support comparisons between an expression that evaluates to a time data type and an expression that evaluates to either a date or a date/time data type.</span></span> <span data-ttu-id="cf989-136">시스템에서 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-136">The system generates an error.</span></span>  
  
     <span data-ttu-id="cf989-137">식을 비교하는 경우 시스템은 다음 변환 규칙을 나열된 순서대로 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-137">When comparing the expressions, the system applies the following conversion rules in the order listed:</span></span>  
  
    -   <span data-ttu-id="cf989-138">두 식이 같은 데이터 형식으로 계산되는 경우 해당 데이터 형식의 비교가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-138">When the two expressions evaluate to the same data type, a comparison of that data type is performed.</span></span>  
  
    -   <span data-ttu-id="cf989-139">하나의 식이 DT_DBTIMESTAMPOFFSET 데이터 형식인 경우 다른 식은 DT_DBTIMESTAMPOFFSET으로 암시적으로 변환되며 DT_DBTIMESTAMPOFFSET 비교가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-139">If one expression is a DT_DBTIMESTAMPOFFSET data type, the other expression is implicitly converted to DT_DBTIMESTAMPOFFSET and a DT_DBTIMESTAMPOFFSET comparison is performed.</span></span> <span data-ttu-id="cf989-140">자세한 내용은 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf989-140">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
    -   <span data-ttu-id="cf989-141">하나의 식이 DT_DBTIMESTAMP2 데이터 형식인 경우 다른 식은 DT_DBTIMESTAMP2로 암시적으로 변환되며 DT_DBTIMESTAMP2 비교가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-141">If one expression is a DT_DBTIMESTAMP2 data type, the other expression is implicitly converted to DT_DBTIMESTAMP2 and a DT_DBTIMESTAMP2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="cf989-142">하나의 식이 DT_DBTIME2 데이터 형식인 경우 다른 식은 DT_DBTIME2로 암시적으로 변환되며 DT_DBTIME2 비교가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-142">If one expression is a DT_DBTIME2 data type, the other expression is implicitly converted to DT_DBTIME2, and a DT_DBTIME2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="cf989-143">하나의 식이 DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2 또는 DT_DBTIME2 이외의 형식인 경우 다른 식은 DT_DBTIMESTAMP 데이터 형식으로 변환되어 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-143">If one expression is of a type other than DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2, or DT_DBTIME2, the expressions are converted to the DT_DBTIMESTAMP data type before they are compared.</span></span>  
  
     <span data-ttu-id="cf989-144">식을 비교할 때 시스템에서는 다음과 같이 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-144">When comparing the expressions, the system makes the following assumptions:</span></span>  
  
    -   <span data-ttu-id="cf989-145">각 식이 소수 자릿수 초를 포함하는 데이터 형식인 경우 시스템은 소수 자릿수 초의 자릿수가 가장 적은 데이터 형식의 나머지 자릿수를 0으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-145">If each expression is a data type that includes fractional seconds, the system assumes that the data type with the least number of digits for fractional seconds has zeros for the remaining digits.</span></span>  
  
    -   <span data-ttu-id="cf989-146">각 식이 날짜 데이터 형식이고 이 중 하나에만 표준 시간대 오프셋이 있는 경우 시스템은 표준 시간대 오프셋이 없는 날짜 데이터 형식을 UTC(Coordinated Universal Time)로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-146">If each expression is a date data type, but only one has a time zone offset, the system assumes that the date data type without the time zone offset is in Coordinated Universal Time (UTC).</span></span>  
  
 <span data-ttu-id="cf989-147">데이터 형식에 대한 자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf989-147">For more information about data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="cf989-148">식 예</span><span class="sxs-lookup"><span data-stu-id="cf989-148">Expression Examples</span></span>  
 <span data-ttu-id="cf989-149">이 예에서는 조건에 따라 `savannah` 또는 `unknown`으로 계산되는 식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-149">This example shows an expression that conditionally evaluates to `savannah` or `unknown`.</span></span>  
  
```  
@AnimalName == "Elephant"? "savannah": "unknown"  
```  
  
 <span data-ttu-id="cf989-150">이 예에서는 **ListPrice** 열을 참조하는 식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-150">This example shows an expression that references a **ListPrice** column.</span></span> <span data-ttu-id="cf989-151">**ListPrice** 는 DT_CY 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-151">**ListPrice** has the DT_CY data type.</span></span> <span data-ttu-id="cf989-152">이 식은 조건에 따라 **ListPrice** 에 .2 또는 .1을 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="cf989-152">The expression conditionally multiplies **ListPrice** by .2 or .1.</span></span>  
  
```  
ListPrice < 350.00 ? ListPrice * .2 : ListPrice * .1  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf989-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cf989-153">See Also</span></span>  
 <span data-ttu-id="cf989-154">[연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="cf989-154">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="cf989-155">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="cf989-155">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
