---
title: GETUTCDATE(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], GETUTCDATE
- current date
- UTC time
- GETUTCDATE function
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f157ab5641e521a42cb3c96c96446b31de5dfa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732852"
---
# <a name="getutcdate-ssis-expression"></a><span data-ttu-id="7c966-102">GETUTCDATE(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="7c966-102">GETUTCDATE (SSIS Expression)</span></span>
  <span data-ttu-id="7c966-103">DT_DBTIMESTAMP 형식을 사용하여 현재 시스템 날짜를 UTC 시간(국제 표준시 또는 그리니치 표준시)으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7c966-103">Returns the current date of the system in UTC time (Universal Time Coordinate or Greenwich Mean Time) using a DT_DBTIMESTAMP format.</span></span> <span data-ttu-id="7c966-104">GETUTCDATE 함수는 인수가 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7c966-104">The GETUTCDATE function takes no arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c966-105">구문</span><span class="sxs-lookup"><span data-stu-id="7c966-105">Syntax</span></span>  
  
```  
  
GETUTCDATE()  
```  
  
## <a name="arguments"></a><span data-ttu-id="7c966-106">인수</span><span class="sxs-lookup"><span data-stu-id="7c966-106">Arguments</span></span>  
 <span data-ttu-id="7c966-107">None</span><span class="sxs-lookup"><span data-stu-id="7c966-107">None</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="7c966-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="7c966-108">Result Types</span></span>  
 <span data-ttu-id="7c966-109">DT_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="7c966-109">DT_DBTIMESTAMP</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="7c966-110">식 예</span><span class="sxs-lookup"><span data-stu-id="7c966-110">Expression Examples</span></span>  
 <span data-ttu-id="7c966-111">이 예에서는 현재 날짜의 연도가 UTC 시간으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c966-111">This example returns the year of the current date in UTC time.</span></span>  
  
```  
DATEPART("year",GETUTCDATE())  
```  
  
 <span data-ttu-id="7c966-112">이 예에서는 **ModifiedDate** 열의 날짜와 현재 UTC 날짜 사이의 일 수가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c966-112">This example returns the number of days between a date in the **ModifiedDate** column and the current UTC date.</span></span>  
  
```  
DATEDIFF("dd",ModifiedDate,GETUTCDATE())  
```  
  
 <span data-ttu-id="7c966-113">이 예에서는 현재 UTC 날짜에 3개월을 더합니다.</span><span class="sxs-lookup"><span data-stu-id="7c966-113">This example adds three months to the current UTC date.</span></span>  
  
```  
DATEADD("Month",3,GETUTCDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c966-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7c966-114">See Also</span></span>  
 <span data-ttu-id="7c966-115">[GETDATE&#40;SSIS 식&#41;](getdate-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="7c966-115">[GETDATE &#40;SSIS Expression&#41;](getdate-ssis-expression.md) </span></span>  
 [<span data-ttu-id="7c966-116">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="7c966-116">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
