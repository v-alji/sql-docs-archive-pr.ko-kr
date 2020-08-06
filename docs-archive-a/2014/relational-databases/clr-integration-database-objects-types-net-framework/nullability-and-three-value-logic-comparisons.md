---
title: Null 허용 여부 및 3 개의 값 논리 비교 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- precision [CLR integration]
- overflow detections [CLR integration]
- null values [CLR integration]
- three-value logic comparisons [CLR integration]
- data types [CLR integration]
- SqlBoolean data type
ms.assetid: 13da4c7f-1010-4b2d-a63c-c69b6bfd96f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b8000c1c28d5a1d3d129b6e8d01c4ab2fbbbc7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742272"
---
# <a name="nullability-and-three-value-logic-comparisons"></a><span data-ttu-id="080ae-102">Null 허용 여부 및 3개의 값 논리 비교</span><span class="sxs-lookup"><span data-stu-id="080ae-102">Nullability and Three-Value Logic Comparisons</span></span>
  <span data-ttu-id="080ae-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식에 대해 잘 아는 경우 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]의 `System.Data.SqlTypes` 네임스페이스와 의미 체계 및 전체 자릿수가 유사하다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="080ae-103">If you are familiar with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, you will find similar semantics and precision in the `System.Data.SqlTypes` namespace in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="080ae-104">그러나 약간의 차이가 있으며 이 항목에서는 이러한 차이 중 가장 중요한 점에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="080ae-104">There are some differences, however, and this topic covers the most important of these differences.</span></span>  
  
## <a name="null-values"></a><span data-ttu-id="080ae-105">NULL 값</span><span class="sxs-lookup"><span data-stu-id="080ae-105">NULL Values</span></span>  
 <span data-ttu-id="080ae-106">기본 CLR(공용 언어 런타임) 데이터 형식과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식 간의 주된 차이점은 전자에서는 NULL 값을 허용하지 않는 반면 후자에서는 완전한 NULL 의미 체계를 제공한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="080ae-106">A primary difference between native common language runtime (CLR) data types and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types is that the former do not allow for NULL values, while the latter provide full NULL semantics.</span></span>  
  
 <span data-ttu-id="080ae-107">비교는 NULL 값의 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="080ae-107">Comparisons are affected by NULL values.</span></span> <span data-ttu-id="080ae-108">두 값 x와 y를 비교할 때 x 또는 y 중 하나가 NULL이면 일부 논리적 비교가 true 또는 false가 아닌 UNKNOWN으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="080ae-108">When comparing two values x and y, if either x or y is NULL, then some logical comparisons evaluate to an UNKNOWN value rather than true or false.</span></span>  
  
## <a name="sqlboolean-data-type"></a><span data-ttu-id="080ae-109">SqlBoolean 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="080ae-109">SqlBoolean Data Type</span></span>  
 <span data-ttu-id="080ae-110">`System.Data.SqlTypes` 네임스페이스에서는 이 3값 논리를 나타내기 위해 `SqlBoolean` 형식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="080ae-110">The `System.Data.SqlTypes` namespace introduces a `SqlBoolean` type to represent this 3-value logic.</span></span> <span data-ttu-id="080ae-111">`SqlTypes` 간을 비교하면 `SqlBoolean` 값 형식이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="080ae-111">Comparisons between any `SqlTypes` return a `SqlBoolean` value type.</span></span> <span data-ttu-id="080ae-112">UNKNOWN 값은 `SqlBoolean` 형식의 null 값으로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="080ae-112">The UNKNOWN value is represented by the null value of the `SqlBoolean` type.</span></span> <span data-ttu-id="080ae-113">`IsTrue` 형식의 값을 확인하기 위해 `IsFalse`, `IsNull` 및 `SqlBoolean` 속성이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="080ae-113">The properties `IsTrue`, `IsFalse`, and `IsNull` are provided to check the value of a `SqlBoolean` type.</span></span>  
  
## <a name="operations-functions-and-null-values"></a><span data-ttu-id="080ae-114">연산, 함수 및 NULL 값</span><span class="sxs-lookup"><span data-stu-id="080ae-114">Operations, Functions, and NULL Values</span></span>  
 <span data-ttu-id="080ae-115">모든 산술 연산자 (+,-, \* ,/,%), 비트 연산자 (~, & 및 |) 및 대부분의 함수는의 피연산자 또는 인수 중 하나가 null 인 경우 null을 반환 `SqlTypes` 합니다.</span><span class="sxs-lookup"><span data-stu-id="080ae-115">All arithmetic operators (+, -, \*, /, %), bitwise operators (~, &, and |), and most functions return NULL if any of the operands or arguments of `SqlTypes` are NULL.</span></span> <span data-ttu-id="080ae-116">`IsNull` 속성은 항상 true 또는 false 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="080ae-116">The `IsNull` property always returns a true or false value.</span></span>  
  
## <a name="precision"></a><span data-ttu-id="080ae-117">전체 자릿수</span><span class="sxs-lookup"><span data-stu-id="080ae-117">Precision</span></span>  
 <span data-ttu-id="080ae-118">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR의 decimal 데이터 형식에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 숫자 및 decimal 데이터 형식의 최대값과는 다른 최대값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="080ae-118">Decimal data types in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR have different maximum values than those of the numeric and decimal data types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="080ae-119">또한 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR decimal 데이터 형식에는 최대 전체 자릿수가 있는 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="080ae-119">In addition, in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR decimal data types assume the maximum precision.</span></span> <span data-ttu-id="080ae-120">그러나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]용 CLR의 `SqlDecimal`은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 decimal 데이터 형식과 동일한 전체 자릿수, 소수 자릿수 및 의미 체계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="080ae-120">In the CLR for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], however, `SqlDecimal` provides the same maximum precision and scale, and the same semantics as the decimal data type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="overflow-detection"></a><span data-ttu-id="080ae-121">오버플로 검색</span><span class="sxs-lookup"><span data-stu-id="080ae-121">Overflow Detection</span></span>  
 <span data-ttu-id="080ae-122">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR에서 아주 큰 두 수를 더하면 예외가 throw되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="080ae-122">In the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR, the addition of two very large numbers may not throw an exception.</span></span> <span data-ttu-id="080ae-123">대신 확인 연산자를 사용하지 않는 경우 반환된 결과가 음의 정수로 "래핑"될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="080ae-123">Instead, if no check operator has been used, the returned result may "wrap around" as a negative integer.</span></span> <span data-ttu-id="080ae-124">`System.Data.SqlTypes`에서는 모든 오버플로 및 언더플로 오류와 0으로 나누기 오류에 대해 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="080ae-124">In `System.Data.SqlTypes`, exceptions are thrown for all overflow and underflow errors, and divide-by-zero errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="080ae-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="080ae-125">See Also</span></span>  
 [<span data-ttu-id="080ae-126">.NET Framework의 SQL Server 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="080ae-126">SQL Server Data Types in the .NET Framework</span></span>](sql-server-data-types-in-the-net-framework.md)  
  
  
