---
title: MONTH(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], MONTH
- MONTH function
ms.assetid: b5a47a11-c2ef-49bd-bd70-235632ff7bf6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d1f56906b4d25f2ba01f54fbdbc404d2c9ae4704
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650194"
---
# <a name="month-ssis-expression"></a><span data-ttu-id="69c60-102">MONTH(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="69c60-102">MONTH (SSIS Expression)</span></span>
  <span data-ttu-id="69c60-103">날짜의 월 부분을 나타내는 정수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="69c60-103">Returns an integer that represents the month datepart of a date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69c60-104">구문</span><span class="sxs-lookup"><span data-stu-id="69c60-104">Syntax</span></span>  
  
```  
  
MONTH(date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="69c60-105">인수</span><span class="sxs-lookup"><span data-stu-id="69c60-105">Arguments</span></span>  
 <span data-ttu-id="69c60-106">*date*</span><span class="sxs-lookup"><span data-stu-id="69c60-106">*date*</span></span>  
 <span data-ttu-id="69c60-107">임의의 날짜 형식을 갖는 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="69c60-107">Is a date in any date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="69c60-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="69c60-108">Result Types</span></span>  
 <span data-ttu-id="69c60-109">DT_I4</span><span class="sxs-lookup"><span data-stu-id="69c60-109">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69c60-110">설명</span><span class="sxs-lookup"><span data-stu-id="69c60-110">Remarks</span></span>  
 <span data-ttu-id="69c60-111">인수가 Null이면 MONTH 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="69c60-111">MONTH returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="69c60-112">날짜 리터럴은 다음의 날짜 데이터 형식 중 하나로 명시적 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69c60-112">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="69c60-113">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69c60-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69c60-114">날짜 리터럴이 DT_DBTIMESTAMPOFFSET 및 DT_DBTIMESTAMP2 날짜 데이터 형식 중 하나로 명시적 캐스팅되면 식의 유효성 검사가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="69c60-114">The expression fails to validate when a date literal is explicitly cast to one of these date data types: DT_DBTIMESTAMPOFFSET and DT_DBTIMESTAMP2.</span></span>  
  
 <span data-ttu-id="69c60-115">MONTH 함수는 DATEPART("Month", date) 함수보다 간단하지만 동일한 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="69c60-115">Using the MONTH function is briefer but equivalent to using DATEPART("Month", date).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="69c60-116">식 예</span><span class="sxs-lookup"><span data-stu-id="69c60-116">Expression Examples</span></span>  
 <span data-ttu-id="69c60-117">이 예에서는 날짜 리터럴의 월을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="69c60-117">This example returns the number of the month in a date literal.</span></span> <span data-ttu-id="69c60-118">날짜 형식이 "mm/dd/yyyy"이면 11이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="69c60-118">If the date is in "mm/dd/yyyy" format, this example returns 11.</span></span>  
  
```  
MONTH((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 <span data-ttu-id="69c60-119">이 예에서는 **ModifiedDate** 열의 월을 나타내는 정수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="69c60-119">This example returns the integer that represents the month in the **ModifiedDate** column.</span></span>  
  
```  
MONTH(ModifiedDate)  
```  
  
 <span data-ttu-id="69c60-120">이 예에서는 현재 날짜의 월을 나타내는 정수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="69c60-120">This example returns the integer that represents the month of the current date.</span></span>  
  
```  
MONTH(GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="69c60-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69c60-121">See Also</span></span>  
 <span data-ttu-id="69c60-122">[DATEADD&#40;SSIS 식&#41;](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="69c60-122">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="69c60-123">[DATEDIFF&#40;SSIS 식&#41;](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="69c60-123">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="69c60-124">[DATEPART&#40;SSIS 식&#41;](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="69c60-124">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="69c60-125">[DAY&#40;SSIS 식&#41;](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="69c60-125">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="69c60-126">[YEAR&#40;SSIS 식&#41;](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="69c60-126">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="69c60-127">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="69c60-127">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
