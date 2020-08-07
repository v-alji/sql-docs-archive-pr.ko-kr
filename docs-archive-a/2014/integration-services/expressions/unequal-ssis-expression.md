---
title: '!=(같지 않음)(SSIS 식) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- unequal operator (!=)
- '!= (not equal to)'
ms.assetid: fad20e85-c0e6-42bf-af70-2bc80ee09be5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: be3eadbac77d76a2b3aac9555d9f40cb56e38949
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732755"
---
# <a name="-unequal-ssis-expression"></a><span data-ttu-id="3715d-102">!=(같지 않음)(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="3715d-102">!= (Unequal) (SSIS Expression)</span></span>
  <span data-ttu-id="3715d-103">호환 가능한 데이터 형식의 두 식이 같지 않은지 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-103">Performs a comparison to determine if two expressions with compatible data types are not equal.</span></span> <span data-ttu-id="3715d-104">식 계산기는 비교를 수행하기 전에 많은 데이터 형식을 자동으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-104">The expression evaluator automatically converts many data types before it performs the comparison.</span></span>  
  
 <span data-ttu-id="3715d-105">그러나 일부 데이터 형식을 사용할 경우 식이 성공적으로 계산되려면 식에 명시적 캐스트가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-105">However, some data types require that the expression include an explicit cast before the expression can be evaluated successfully.</span></span> <span data-ttu-id="3715d-106">데이터 형식 간 올바른 캐스트에 대한 자세한 내용은 [캐스트&#40;SSIS 식&#41;](cast-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3715d-106">For more information about legal casts between data types, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3715d-107">구문</span><span class="sxs-lookup"><span data-stu-id="3715d-107">Syntax</span></span>  
  
```  
  
expression1 != expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="3715d-108">인수</span><span class="sxs-lookup"><span data-stu-id="3715d-108">Arguments</span></span>  
 <span data-ttu-id="3715d-109">*expression1, expression2*</span><span class="sxs-lookup"><span data-stu-id="3715d-109">*expression1, expression2*</span></span>  
 <span data-ttu-id="3715d-110">유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-110">Is any valid expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="3715d-111">결과 형식</span><span class="sxs-lookup"><span data-stu-id="3715d-111">Result Types</span></span>  
 <span data-ttu-id="3715d-112">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="3715d-112">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3715d-113">설명</span><span class="sxs-lookup"><span data-stu-id="3715d-113">Remarks</span></span>  
 <span data-ttu-id="3715d-114">비교하는 두 식 중 하나가 Null이면 비교 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-114">If either expression in the comparison is null, the comparison result is null.</span></span> <span data-ttu-id="3715d-115">두 식이 모두 Null이면 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-115">If both expressions are null, the result is null.</span></span>  
  
 <span data-ttu-id="3715d-116">식 집합 *expression1* 및 *expression2*는 다음 규칙 중 하나를 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-116">The expression set, *expression1* and *expression2*, must follow one of these rules:</span></span>  
  
-   <span data-ttu-id="3715d-117">\**Numeric\*\*\*expression1* 및 *expression2* 모두 숫자 데이터 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-117">**Numeric** Both *expression1* and *expression2* must be a numeric data type.</span></span> <span data-ttu-id="3715d-118">데이터 형식의 교집합은 식 계산기가 수행하는 암시적 숫자 변환에 대한 규칙에 지정된 대로 숫자 데이터 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-118">The intersection of the data types must be a numeric data type, as specified in the rules about the implicit numeric conversions that the expression evaluator performs.</span></span> <span data-ttu-id="3715d-119">두 숫자 데이터 형식의 교집합은 Null일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-119">The intersection of the two numeric data types cannot be null.</span></span> <span data-ttu-id="3715d-120">자세한 내용은 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3715d-120">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
-   <span data-ttu-id="3715d-121">\**Character\*\*\*expression1* 및 *expression2* 모두 DT_STR 또는 DT_WSTR 데이터 형식으로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-121">**Character** Both *expression1* and *expression2* must evaluate to either a DT_STR or a DT_WSTR data type.</span></span> <span data-ttu-id="3715d-122">두 식이 서로 다른 문자열 데이터 형식으로 계산될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-122">The two expressions can evaluate to different string data types.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3715d-123">문자열 비교는 대/소문자, 악센트, 일본어 가나 및 전자/반자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-123">String comparisons are case, accent, kana, and width-sensitive.</span></span>  
  
-   <span data-ttu-id="3715d-124">\**Date, Time 또는 Date/Time\*\*\*expression1* 및 *expression2* 모두는 DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET 또는 DT_FILETIME 데이터 형식 중 하나로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-124">**Date, Time, or Date/Time** Both *expression1* and *expression2* must evaluate to one of the following data types: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET, or DT_FILETIME.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3715d-125">시간 데이터 형식으로 계산되는 식과 날짜 또는 날짜/시간 데이터 형식 중 하나로 계산되는 식 사이의 비교는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-125">The system does not support comparisons between an expression that evaluates to a time data type and an expression that evaluates to either a date or a date/time data type.</span></span> <span data-ttu-id="3715d-126">시스템에서 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-126">The system generates an error.</span></span>  
  
     <span data-ttu-id="3715d-127">식을 비교하는 경우 시스템은 다음 변환 규칙을 나열된 순서대로 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-127">When comparing the expressions, the system applies the following conversion rules in the order listed:</span></span>  
  
    -   <span data-ttu-id="3715d-128">두 식이 같은 데이터 형식으로 계산되는 경우 해당 데이터 형식의 비교가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-128">When the two expressions evaluate to the same data type, a comparison of that data type is performed.</span></span>  
  
    -   <span data-ttu-id="3715d-129">하나의 식이 DT_DBTIMESTAMPOFFSET 데이터 형식인 경우 다른 식은 DT_DBTIMESTAMPOFFSET으로 암시적으로 변환되며 DT_DBTIMESTAMPOFFSET 비교가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-129">If one expression is a DT_DBTIMESTAMPOFFSET data type, the other expression is implicitly converted to DT_DBTIMESTAMPOFFSET and a DT_DBTIMESTAMPOFFSET comparison is performed.</span></span> <span data-ttu-id="3715d-130">자세한 내용은 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3715d-130">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
    -   <span data-ttu-id="3715d-131">하나의 식이 DT_DBTIMESTAMP2 데이터 형식인 경우 다른 식은 DT_DBTIMESTAMP2로 암시적으로 변환되며 DT_DBTIMESTAMP2 비교가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-131">If one expression is a DT_DBTIMESTAMP2 data type, the other expression is implicitly converted to DT_DBTIMESTAMP2 and a DT_DBTIMESTAMP2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="3715d-132">하나의 식이 DT_DBTIME2 데이터 형식인 경우 다른 식은 DT_DBTIME2로 암시적으로 변환되며 DT_DBTIME2 비교가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-132">If one expression is a DT_DBTIME2 data type, the other expression is implicitly converted to DT_DBTIME2, and a DT_DBTIME2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="3715d-133">하나의 식이 DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2 또는 DT_DBTIME2 이외의 형식인 경우 다른 식은 DT_DBTIMESTAMP 데이터 형식으로 변환되어 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-133">If one expression is of a type other than DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2, or DT_DBTIME2, the expressions are converted to the DT_DBTIMESTAMP data type before they are compared.</span></span>  
  
     <span data-ttu-id="3715d-134">식을 비교할 때 시스템에서는 다음과 같이 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-134">When comparing the expressions, the system makes the following assumptions:</span></span>  
  
    -   <span data-ttu-id="3715d-135">각 식이 소수 자릿수 초를 포함하는 데이터 형식인 경우 시스템은 소수 자릿수 초의 자릿수가 가장 적은 데이터 형식의 나머지 자릿수를 0으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-135">If each expression is a data type that includes fractional seconds, the system assumes that the data type with the least number of digits for fractional seconds has zeros for the remaining digits.</span></span>  
  
    -   <span data-ttu-id="3715d-136">각 식이 날짜 데이터 형식이고 이 중 하나에만 표준 시간대 오프셋이 있는 경우 시스템은 표준 시간대 오프셋이 없는 날짜 데이터 형식을 UTC(Coordinated Universal Time)로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-136">If each expression is a date data type, but only one has a time zone offset, the system assumes that the date data type without the time zone offset is in Coordinated Universal Time (UTC).</span></span>  
  
-   <span data-ttu-id="3715d-137">\**Logical\*\*\*expression1* 과 *expression2* 는 모두 부울로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-137">**Logical** Both *expression1* and *expression2* must evaluate to a Boolean.</span></span>  
  
-   <span data-ttu-id="3715d-138">\**GUID\*\*\*expression1* 및 *expression2* 모두 DT_GUID 데이터 형식으로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-138">**GUID** Both *expression1* and *expression2* must evaluate to the DT_GUID data type.</span></span>  
  
-   <span data-ttu-id="3715d-139">\**Binary\*\*\*expression1* 및 *expression2* 모두 DT_BYTES 데이터 형식으로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-139">**Binary** Both *expression1* and *expression2* must evaluate to the DT_BYTES data type.</span></span>  
  
-   <span data-ttu-id="3715d-140">\**BLOB\*\*\*expression1* 및 *expression2* 모두 동일한 BLOB(Binary Large Object Block) 데이터 형식 DT_TEXT, DT_NTEXT 또는 DT_IMAGE로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-140">**BLOB** Both *expression1* and *expression2* must evaluate to the same Binary Large Object Block (BLOB) data type: DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span>  
  
 <span data-ttu-id="3715d-141">데이터 형식에 대한 자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3715d-141">For more information about data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="3715d-142">식 예</span><span class="sxs-lookup"><span data-stu-id="3715d-142">Expression Examples</span></span>  
 <span data-ttu-id="3715d-143">이 예에서는 현재 날짜가 2003년 7월 4일이 아닌 경우에만 TRUE가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-143">This example evaluates to TRUE only if the current date is not July 4, 2003.</span></span> <span data-ttu-id="3715d-144">자세한 내용은 [GETDATE&#40;SSIS 식&#41;](getdate-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3715d-144">For more information, see [GETDATE &#40;SSIS Expression&#41;](getdate-ssis-expression.md).</span></span>  
  
```  
"7/4/2003" != GETDATE()  
```  
  
 <span data-ttu-id="3715d-145">이 예에서는 **ListPrice** 열의 값이 500이 아니면 TRUE가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-145">This example evaluates to TRUE if the value in the **ListPrice** column is not 500.</span></span>  
  
```  
ListPrice != 500  
```  
  
 <span data-ttu-id="3715d-146">이 예에서는 변수 **LPrice**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-146">This example uses the variable **LPrice**.</span></span> <span data-ttu-id="3715d-147">**LPrice** 의 값이 500이 아니면 이 예는 TRUE가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-147">It evaluates to TRUE if the value of **LPrice** is not 500.</span></span> <span data-ttu-id="3715d-148">식을 구문 분석하려면 변수의 데이터 형식이 숫자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3715d-148">The data type on the variable must be numeric in order for the expression to parse.</span></span>  
  
```  
@LPrice != 500  
```  
  
## <a name="see-also"></a><span data-ttu-id="3715d-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3715d-149">See Also</span></span>  
 <span data-ttu-id="3715d-150">[== &#40;같음&#41;&#40;SSIS 식&#41;](equal-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="3715d-150">[== &#40;Equal&#41; &#40;SSIS Expression&#41;](equal-ssis-expression.md) </span></span>  
 <span data-ttu-id="3715d-151">[연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="3715d-151">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="3715d-152">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="3715d-152">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
