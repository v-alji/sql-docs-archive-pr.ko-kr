---
title: GETDATE(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0acb384a8c3c3dfdae55c7172f341f9e32765e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649599"
---
# <a name="getdate-ssis-expression"></a><span data-ttu-id="dea2d-102">GETDATE(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="dea2d-102">GETDATE (SSIS Expression)</span></span>
  <span data-ttu-id="dea2d-103">시스템의 현재 날짜를 DT_DBTIMESTAMP 형식으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="dea2d-103">Returns the current date of the system in a DT_DBTIMESTAMP format.</span></span> <span data-ttu-id="dea2d-104">GETDATE 함수는 인수가 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dea2d-104">The GETDATE function takes no arguments.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dea2d-105">GETDATE 함수의 반환 결과 길이는 29자입니다.</span><span class="sxs-lookup"><span data-stu-id="dea2d-105">The length of the return result from the GETDATE function is 29 characters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dea2d-106">구문</span><span class="sxs-lookup"><span data-stu-id="dea2d-106">Syntax</span></span>  
  
```  
  
GETDATE()  
```  
  
## <a name="arguments"></a><span data-ttu-id="dea2d-107">인수</span><span class="sxs-lookup"><span data-stu-id="dea2d-107">Arguments</span></span>  
 <span data-ttu-id="dea2d-108">None</span><span class="sxs-lookup"><span data-stu-id="dea2d-108">None</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="dea2d-109">결과 형식</span><span class="sxs-lookup"><span data-stu-id="dea2d-109">Result Types</span></span>  
 <span data-ttu-id="dea2d-110">DT_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="dea2d-110">DT_DBTIMESTAMP</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="dea2d-111">식 예</span><span class="sxs-lookup"><span data-stu-id="dea2d-111">Expression Examples</span></span>  
 <span data-ttu-id="dea2d-112">이 예에서는 현재 날짜의 연도를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="dea2d-112">This example returns the year of the current date.</span></span>  
  
```  
DATEPART("year",GETDATE())  
```  
  
 <span data-ttu-id="dea2d-113">이 예에서는 **ModifiedDate** 열의 날짜와 현재 날짜 사이의 일 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="dea2d-113">This example returns the number of days between a date in the **ModifiedDate** column and the current date.</span></span>  
  
```  
DATEDIFF("dd",ModifiedDate,GETDATE())  
```  
  
 <span data-ttu-id="dea2d-114">이 예에서는 현재 날짜에 3개월을 더합니다.</span><span class="sxs-lookup"><span data-stu-id="dea2d-114">This example adds three months to the current date.</span></span>  
  
```  
DATEADD("Month",3,GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="dea2d-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dea2d-115">See Also</span></span>  
 <span data-ttu-id="dea2d-116">[GETUTCDATE&#40;SSIS 식&#41;](getutcdate-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="dea2d-116">[GETUTCDATE &#40;SSIS Expression&#41;](getutcdate-ssis-expression.md) </span></span>  
 [<span data-ttu-id="dea2d-117">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="dea2d-117">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
