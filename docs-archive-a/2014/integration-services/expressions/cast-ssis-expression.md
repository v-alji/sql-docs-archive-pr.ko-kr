---
title: 캐스트(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- CAST function
- cast operator
- converting data types [Integration Services]
- data types [Integration Services], expressions
- data types [Integration Services], converting
ms.assetid: d4e915cc-1c7b-4b2e-93b0-13a8b0cb9242
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 65d60eca4340b65b8a82855c3f2b29a6cda56e15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736664"
---
# <a name="cast-ssis-expression"></a><span data-ttu-id="4fe13-102">캐스트(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="4fe13-102">Cast (SSIS Expression)</span></span>
  <span data-ttu-id="4fe13-103">식의 데이터 형식을 다른 데이터 형식으로 명시적으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-103">Explicitly converts an expression from one data type to a different data type.</span></span> <span data-ttu-id="4fe13-104">캐스트 연산자는 잘라내기 연산자로 실행될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-104">The cast operator can also function as a truncation operator.</span></span>

## <a name="syntax"></a><span data-ttu-id="4fe13-105">구문</span><span class="sxs-lookup"><span data-stu-id="4fe13-105">Syntax</span></span>

```

(type_spec) expression

```

## <a name="arguments"></a><span data-ttu-id="4fe13-106">인수</span><span class="sxs-lookup"><span data-stu-id="4fe13-106">Arguments</span></span>
 <span data-ttu-id="4fe13-107">*type_spec* 는 유효한 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-107">*type_spec* Is a valid [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type.</span></span>

 <span data-ttu-id="4fe13-108">*식* 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-108">*expression* Is a valid expression.</span></span>

## <a name="result-types"></a><span data-ttu-id="4fe13-109">결과 형식</span><span class="sxs-lookup"><span data-stu-id="4fe13-109">Result Types</span></span>
 <span data-ttu-id="4fe13-110">*type_spec*데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-110">The data type of *type_spec*.</span></span> <span data-ttu-id="4fe13-111">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fe13-111">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="4fe13-112">설명</span><span class="sxs-lookup"><span data-stu-id="4fe13-112">Remarks</span></span>
 <span data-ttu-id="4fe13-113">다음 다이어그램에서는 유효한 캐스트 연산을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-113">The following diagram shows legal cast operations.</span></span>

 <span data-ttu-id="4fe13-114">![데이터 형식 간 유효한 캐스트 및 유효하지 않은 캐스트](../media/data-conversion.gif "데이터 형식 간 유효한 캐스트 및 유효하지 않은 캐스트")</span><span class="sxs-lookup"><span data-stu-id="4fe13-114">![Legal and not legal casts between data types](../media/data-conversion.gif "Legal and not legal casts between data types")</span></span>

 <span data-ttu-id="4fe13-115">일부 데이터 형식으로의 캐스트는 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-115">Casting to some data types requires parameters.</span></span> <span data-ttu-id="4fe13-116">다음 표에서는 이러한 데이터 형식과 해당 매개 변수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-116">The following table lists these data types and their parameters.</span></span>

|<span data-ttu-id="4fe13-117">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="4fe13-117">Data type</span></span>|<span data-ttu-id="4fe13-118">매개 변수</span><span class="sxs-lookup"><span data-stu-id="4fe13-118">Parameter</span></span>|<span data-ttu-id="4fe13-119">예제</span><span class="sxs-lookup"><span data-stu-id="4fe13-119">Example</span></span>|
|---------------|---------------|-------------|
|<span data-ttu-id="4fe13-120">DT_STR</span><span class="sxs-lookup"><span data-stu-id="4fe13-120">DT_STR</span></span>|<span data-ttu-id="4fe13-121">*charcount*</span><span class="sxs-lookup"><span data-stu-id="4fe13-121">*charcount*</span></span><br /><br /> <span data-ttu-id="4fe13-122">*코드 페이지*</span><span class="sxs-lookup"><span data-stu-id="4fe13-122">*codepage*</span></span>|<span data-ttu-id="4fe13-123">(DT_STR,30,1252)는 1252 코드 페이지를 사용하여 30바이트 또는 30자의 단일 문자를 DT_STR 데이터 형식으로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-123">(DT_STR,30,1252) casts 30 bytes, or 30 single characters, to the DT_STR data type using the 1252 code page.</span></span>|
|<span data-ttu-id="4fe13-124">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="4fe13-124">DT_WSTR</span></span>|<span data-ttu-id="4fe13-125">*Charcount*</span><span class="sxs-lookup"><span data-stu-id="4fe13-125">*Charcount*</span></span>|<span data-ttu-id="4fe13-126">(DT_WSTR,20)은 20바이트 쌍 또는 20자의 유니코드 문자를 DT_WSTR 데이터 형식으로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-126">(DT_WSTR,20) casts 20 byte pairs, or 20 Unicode characters, to the DT_WSTR data type.</span></span>|
|<span data-ttu-id="4fe13-127">DT_BYTES</span><span class="sxs-lookup"><span data-stu-id="4fe13-127">DT_BYTES</span></span>|<span data-ttu-id="4fe13-128">*Bytecount*</span><span class="sxs-lookup"><span data-stu-id="4fe13-128">*Bytecount*</span></span>|<span data-ttu-id="4fe13-129">(DT_BYTES,50)은 50바이트를 DT_BYTES 데이터 형식으로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-129">(DT_BYTES,50) casts 50 bytes to the DT_BYTES data type.</span></span>|
|<span data-ttu-id="4fe13-130">DT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="4fe13-130">DT_DECIMAL</span></span>|<span data-ttu-id="4fe13-131">*크기 조정*</span><span class="sxs-lookup"><span data-stu-id="4fe13-131">*Scale*</span></span>|<span data-ttu-id="4fe13-132">(DT_DECIMAL,2)는 소수 자릿수 2를 사용하여 숫자 값을 DT_DECIMAL 데이터 형식으로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-132">(DT_DECIMAL,2) casts a numeric value to the DT_DECIMAL data type using a scale of 2.</span></span>|
|<span data-ttu-id="4fe13-133">DT_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="4fe13-133">DT_NUMERIC</span></span>|<span data-ttu-id="4fe13-134">*정밀도*</span><span class="sxs-lookup"><span data-stu-id="4fe13-134">*Precision*</span></span><br /><br /> <span data-ttu-id="4fe13-135">*크기 조정*</span><span class="sxs-lookup"><span data-stu-id="4fe13-135">*Scale*</span></span>|<span data-ttu-id="4fe13-136">(DT_NUMERIC,10,3)은 전체 자릿수 10, 소수 자릿수 3을 사용하여 숫자 값을 DT_NUMERIC 데이터 형식으로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-136">(DT_NUMERIC,10,3) casts a numeric value to the DT_NUMERIC data type using a precision of 10 and a scale of 3.</span></span>|
|<span data-ttu-id="4fe13-137">DT_TEXT</span><span class="sxs-lookup"><span data-stu-id="4fe13-137">DT_TEXT</span></span>|<span data-ttu-id="4fe13-138">*코드 페이지*</span><span class="sxs-lookup"><span data-stu-id="4fe13-138">*Codepage*</span></span>|<span data-ttu-id="4fe13-139">(DT_TEXT,1252)는 1252 코드 페이지를 사용하여 값을 DT_TEXT 데이터 형식으로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-139">(DT_TEXT,1252) casts a value to the DT_TEXT data type using the 1252 code page.</span></span>|

 <span data-ttu-id="4fe13-140">문자열을 DT_DATE로 캐스팅하거나 그 반대의 경우 변환 로캘이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-140">When a string is cast to a DT_DATE, or vice versa, the locale of the transformation is used.</span></span> <span data-ttu-id="4fe13-141">단, 로캘 기본 설정이 ISO 형식을 사용하는지 여부에 관계없이 날짜는 ISO 형식 YYYY-MM-DD로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-141">However, the date is in the ISO format of YYYY-MM-DD, regardless of whether the locale preference uses the ISO format.</span></span>

> [!NOTE]
>  <span data-ttu-id="4fe13-142">문자열을 DT_DATE가 아닌 다른 날짜 데이터 형식으로 변환하려면 [Integration Services 데이터 형식](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fe13-142">To convert a string to a date data type other than DT_DATE, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>

 <span data-ttu-id="4fe13-143">코드 페이지가 멀티바이트 문자 코드 페이지이면 바이트 수와 문자 수가 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-143">If the code page is a multibyte character code page, the number of bytes and characters may differ.</span></span> <span data-ttu-id="4fe13-144">동일한 *charcount* 값을 사용하여 DT_WSTR에서 DT_STR로 캐스팅하면 변환된 문자열의 마지막 문자가 잘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-144">Casting from a DT_WSTR to a DT_STR with the same *charcount* value may cause truncation of the final characters in the converted string.</span></span> <span data-ttu-id="4fe13-145">대상 테이블의 열에 사용 가능한 스토리지 공간이 충분한 경우 멀티바이트 코드 페이지에 필요한 바이트 수를 반영하여 *charcount* 매개 변수의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-145">If sufficient storage is available in the column of the destination table, set the value of the *charcount* parameter to reflect the number of bytes that the multibyte code page requires.</span></span> <span data-ttu-id="4fe13-146">예를 들어 936 코드 페이지를 사용하여 문자 데이터를 DT_STR 데이터 형식으로 캐스팅하는 경우 *charcount* 를 데이터에 포함될 예상 문자 수보다 최대 2배의 값으로 설정해야 합니다. UTF-8 코드 페이지를 사용하여 문자 데이터를 캐스팅하는 경우에는 *charcount* 를 최대 4배의 값으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-146">For example, if you cast character data to a DT_STR data type using the 936 code page, you should set *charcount* to a value up to two times greater than the number of characters that you expect the data to contain; if you cast character data using the UTF-8 code page, you should set *charcount* to a value up to four times greater.</span></span>

 <span data-ttu-id="4fe13-147">날짜 데이터 형식의 구조에 대한 자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4fe13-147">For more information about the structure of date data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>

## <a name="ssis-expression-examples"></a><span data-ttu-id="4fe13-148">SSIS 식 예</span><span class="sxs-lookup"><span data-stu-id="4fe13-148">SSIS Expression Examples</span></span>
 <span data-ttu-id="4fe13-149">이 예에서는 숫자 값을 정수로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-149">This example casts a numeric value to an integer.</span></span>

```
(DT_I4) 3.57
```

 <span data-ttu-id="4fe13-150">이 예에서는 1252 코드 페이지를 사용하여 정수를 문자열로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-150">This example casts an integer to a character string using the 1252 code page.</span></span>

```
(DT_STR,1,1252)5
```

 <span data-ttu-id="4fe13-151">이 예에서는 3자 문자열을 더블바이트 문자로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-151">This example casts a three-character string to double-byte characters.</span></span>

```
(DT_WSTR,3)"Cat"
```

 <span data-ttu-id="4fe13-152">이 예에서는 정수를 소수 자릿수 2의 10진수로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-152">This example casts an integer to a decimal with a scale of two.</span></span>

```
(DT_DECIMAl,2)500
```

 <span data-ttu-id="4fe13-153">이 예에서는 정수를 전체 자릿수가 7이고 소수 자릿수가 3인 정수로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-153">This example casts an integer to a numeric with a precision of seven and scale of three.</span></span>

```
(DT_NUMERIC,7,3)4000
```

 <span data-ttu-id="4fe13-154">이 예에서는 1252 코드 페이지를 사용하여 **nvarchar** 데이터 형식과 길이 50으로 정의된 **FirstName** 열의 값을 문자열로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-154">This example casts values in the **FirstName** column, defined with an **nvarchar** data type and a length of 50, to a character string using the 1252 code page.</span></span>

```
(DT_STR,50,1252)FirstName
```

 <span data-ttu-id="4fe13-155">이 예에서는 DT_DBDATE 형식의 **DateFirstPurchase** 열에 있는 값을 길이가 20인 유니코드 문자열에 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-155">This example casts values in the **DateFirstPurchase** column of type DT_DBDATE, to a Unicode character string with a length of 20.</span></span>

```
(DT_WSTR,20)DateFirstPurchase
```

 <span data-ttu-id="4fe13-156">이 예에서는 문자열 "True"를 부울로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-156">This example casts the string literal "True" to a Boolean.</span></span>

```
(DT_BOOL)"True"
```

 <span data-ttu-id="4fe13-157">이 예에서는 문자열 리터럴을 DT_DBDATE로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-157">This example casts a string literal to DT_DBDATE.</span></span>

```
(DT_DBDATE) "1999-10-11"
```

 <span data-ttu-id="4fe13-158">이 예에서는 문자열 리터럴을 소수 자릿수 초에 5자리를 사용하는 DT_DBTIME2 데이터 형식으로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-158">This example casts a string literal to the DT_DBTIME2 data type that uses 5 digits for fractional seconds.</span></span> <span data-ttu-id="4fe13-159">DT_DBTIME2 데이터 형식은 소수 자릿수 초에 지정된 0부터 7자리까지 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-159">(The DT_DBTIME2 data type can have between 0 and 7 digits specified for fractional seconds.)</span></span>

```
(DT_DBTIME2, 5) "16:34:52.12345"
```

 <span data-ttu-id="4fe13-160">이 예에서는 문자열 리터럴을 소수 자릿수 초에 4자리를 사용하는 DT_DBTIMESTAMP2 데이터 형식으로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-160">This example casts a string literal to the DT_DBTIMESTAMP2 data type that uses 4 digits for fractional seconds.</span></span> <span data-ttu-id="4fe13-161">DT_DBTIMESTAMP2 데이터 형식은 소수 자릿수 초에 지정된 0부터 7자리까지 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-161">(The DT_DBTIMESTAMP2 data type can have between 0 and 7 digits specified for fractional seconds.)</span></span>

```
(DT_DBTIMESTAMP2, 4) "1999-10-11 16:34:52.1234"
```

 <span data-ttu-id="4fe13-162">이 예에서는 문자열 리터럴을 소수 자릿수 초에 7자리를 사용하는 DT_DBTIMESTAMPOFFSET 데이터 형식으로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-162">This example casts a string literal to the DT_DBTIMESTAMPOFFSET data type that uses 7 digits for fractional seconds.</span></span> <span data-ttu-id="4fe13-163">DT_DBTIMESTAMPOFFSET 데이터 형식은 소수 자릿수 초에 지정된 0부터 7자리까지 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fe13-163">(The DT_DBTIMESTAMPOFFSET data typecan have between 0 and 7 digits specified for fractional seconds.)</span></span>

```
(DT_DBTIMESTAMPOFFSET, 7) "1999-10-11 16:34:52.1234567 + 5:35"
```

## <a name="see-also"></a><span data-ttu-id="4fe13-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4fe13-164">See Also</span></span>
 <span data-ttu-id="4fe13-165">[연산자 우선 순위 및 결합성](operator-precedence-and-associativity.md) [연산자 &#40;ssis 식&#41;](operators-ssis-expression.md) [Integration Services &#40;Ssis&#41;](integration-services-ssis-expressions.md) 식 [의 데이터 형식 Integration Services](integration-services-data-types-in-expressions.md)</span><span class="sxs-lookup"><span data-stu-id="4fe13-165">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) [Operators &#40;SSIS Expression&#41;](operators-ssis-expression.md) [Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md) [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)</span></span>


