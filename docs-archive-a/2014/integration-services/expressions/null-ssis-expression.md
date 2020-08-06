---
title: NULL(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- NULL function
- null values [Integration Services]
ms.assetid: df144237-3fbb-41ac-8624-efd92b6522b9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e14cd51b4e245ca6984a4c62eae2b9d5536ab1f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646555"
---
# <a name="null-ssis-expression"></a><span data-ttu-id="e6a67-102">NULL(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="e6a67-102">NULL (SSIS Expression)</span></span>
  <span data-ttu-id="e6a67-103">요청한 데이터 형식의 Null 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a67-103">Returns a null value of a requested data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6a67-104">구문</span><span class="sxs-lookup"><span data-stu-id="e6a67-104">Syntax</span></span>  
  
```  
  
NULL(typespec)  
```  
  
## <a name="arguments"></a><span data-ttu-id="e6a67-105">인수</span><span class="sxs-lookup"><span data-stu-id="e6a67-105">Arguments</span></span>  
 <span data-ttu-id="e6a67-106">*typespec*</span><span class="sxs-lookup"><span data-stu-id="e6a67-106">*typespec*</span></span>  
 <span data-ttu-id="e6a67-107">유효한 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="e6a67-107">Is a valid data type.</span></span> <span data-ttu-id="e6a67-108">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6a67-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e6a67-109">결과 형식</span><span class="sxs-lookup"><span data-stu-id="e6a67-109">Result Types</span></span>  
 <span data-ttu-id="e6a67-110">Null 값을 가진 유효한 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="e6a67-110">Any valid data type with a null value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6a67-111">설명</span><span class="sxs-lookup"><span data-stu-id="e6a67-111">Remarks</span></span>  
 <span data-ttu-id="e6a67-112">인수가 Null이면 NULL 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="e6a67-112">NULL returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="e6a67-113">일부 데이터 형식의 Null 값을 요청하려면 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a67-113">Parameters are required to request a null value for some data types.</span></span> <span data-ttu-id="e6a67-114">다음 표에서는 이러한 데이터 형식과 해당 매개 변수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e6a67-114">The following table lists these data types and their parameters.</span></span>  
  
|<span data-ttu-id="e6a67-115">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="e6a67-115">Data type</span></span>|<span data-ttu-id="e6a67-116">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6a67-116">Parameter</span></span>|<span data-ttu-id="e6a67-117">예제</span><span class="sxs-lookup"><span data-stu-id="e6a67-117">Example</span></span>|  
|---------------|---------------|-------------|  
|<span data-ttu-id="e6a67-118">DT_STR</span><span class="sxs-lookup"><span data-stu-id="e6a67-118">DT_STR</span></span>|<span data-ttu-id="e6a67-119">*charcount*</span><span class="sxs-lookup"><span data-stu-id="e6a67-119">*charcount*</span></span><br /><br /> <span data-ttu-id="e6a67-120">*codepage*</span><span class="sxs-lookup"><span data-stu-id="e6a67-120">*codepage*</span></span>|<span data-ttu-id="e6a67-121">(DT_STR,30,1252)는 1252 코드 페이지를 사용하여 30자를 DT_STR 데이터 형식으로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a67-121">(DT_STR,30,1252) casts 30 characters to the DT_STR data type using the 1252 code page.</span></span>|  
|<span data-ttu-id="e6a67-122">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="e6a67-122">DT_WSTR</span></span>|<span data-ttu-id="e6a67-123">*charcount*</span><span class="sxs-lookup"><span data-stu-id="e6a67-123">*charcount*</span></span>|<span data-ttu-id="e6a67-124">(DT_WSTR,20)은 20자를 DT_WSTR 데이터 형식으로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a67-124">(DT_WSTR,20) casts 20 characters to the DT_WSTR data type.</span></span>|  
|<span data-ttu-id="e6a67-125">DT_BYTES</span><span class="sxs-lookup"><span data-stu-id="e6a67-125">DT_BYTES</span></span>|<span data-ttu-id="e6a67-126">*bytecount*</span><span class="sxs-lookup"><span data-stu-id="e6a67-126">*bytecount*</span></span>|<span data-ttu-id="e6a67-127">(DT_BYTES,50)은 50바이트를 DT_BYTES 데이터 형식으로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a67-127">(DT_BYTES,50) casts 50 bytes to the DT_BYTES data type.</span></span>|  
|<span data-ttu-id="e6a67-128">DT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="e6a67-128">DT_DECIMAL</span></span>|<span data-ttu-id="e6a67-129">*scale*</span><span class="sxs-lookup"><span data-stu-id="e6a67-129">*scale*</span></span>|<span data-ttu-id="e6a67-130">(DT_DECIMAL,2)는 소수 자릿수 2를 사용하여 숫자 값을 DT_DECIMAL 데이터 형식으로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a67-130">(DT_DECIMAL,2) casts a numeric value to the DT_DECIMAL data type using a scale of 2.</span></span>|  
|<span data-ttu-id="e6a67-131">DT_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="e6a67-131">DT_NUMERIC</span></span>|<span data-ttu-id="e6a67-132">*전체 자릿수*</span><span class="sxs-lookup"><span data-stu-id="e6a67-132">*precision*</span></span><br /><br /> <span data-ttu-id="e6a67-133">*scale*</span><span class="sxs-lookup"><span data-stu-id="e6a67-133">*scale*</span></span>|<span data-ttu-id="e6a67-134">(DT_NUMERIC,10,3)은 전체 자릿수 10, 소수 자릿수 3을 사용하여 숫자 값을 DT_NUMERIC 데이터 형식으로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a67-134">(DT_NUMERIC,10,3) casts a numeric value to the DT_NUMERIC data type using a precision of 10 and a scale of 3.</span></span>|  
|<span data-ttu-id="e6a67-135">DT_TEXT</span><span class="sxs-lookup"><span data-stu-id="e6a67-135">DT_TEXT</span></span>|<span data-ttu-id="e6a67-136">*codepage*</span><span class="sxs-lookup"><span data-stu-id="e6a67-136">*codepage*</span></span>|<span data-ttu-id="e6a67-137">(DT_TEXT,1252)는 1252 코드 페이지를 사용하여 값을 DT_TEXT 데이터 형식으로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a67-137">(DT_TEXT,1252) casts a value to the DT_TEXT data type using the 1252 code page.</span></span>|  
  
## <a name="expression-examples"></a><span data-ttu-id="e6a67-138">식 예</span><span class="sxs-lookup"><span data-stu-id="e6a67-138">Expression Examples</span></span>  
 <span data-ttu-id="e6a67-139">이 예에서는 DT_STR, DT_DATE 및 DT_BOOL 데이터 형식의 Null 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a67-139">These examples return the null value of the data types: DT_STR, DT_DATE, and DT_BOOL.</span></span>  
  
```  
NULL(DT_STR,10,1252)  
NULL(DT_DATE)  
NULL(DT_BOOL)  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6a67-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e6a67-140">See Also</span></span>  
 <span data-ttu-id="e6a67-141">[ISNULL&#40;SSIS 식&#41;](null-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="e6a67-141">[ISNULL &#40;SSIS Expression&#41;](null-ssis-expression.md) </span></span>  
 [<span data-ttu-id="e6a67-142">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="e6a67-142">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
