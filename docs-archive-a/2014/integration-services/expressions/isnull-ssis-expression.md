---
title: ISNULL(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- null values [Integration Services]
- ISNULL function
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 51eda21b5c9b85c5f9cfd613d0d92df9729fe620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732828"
---
# <a name="isnull-ssis-expression"></a><span data-ttu-id="f2527-102">ISNULL(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="f2527-102">ISNULL (SSIS Expression)</span></span>
  <span data-ttu-id="f2527-103">식이 Null인지 여부에 따라 부울 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f2527-103">Returns a Boolean result based on whether an expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2527-104">구문</span><span class="sxs-lookup"><span data-stu-id="f2527-104">Syntax</span></span>  
  
```  
  
ISNULL(expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="f2527-105">인수</span><span class="sxs-lookup"><span data-stu-id="f2527-105">Arguments</span></span>  
 <span data-ttu-id="f2527-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="f2527-106">*expression*</span></span>  
 <span data-ttu-id="f2527-107">임의 데이터 형식의 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="f2527-107">Is a valid expression of any data type.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f2527-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="f2527-108">Result Types</span></span>  
 <span data-ttu-id="f2527-109">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="f2527-109">DT_BOOL</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="f2527-110">식 예</span><span class="sxs-lookup"><span data-stu-id="f2527-110">Expression Examples</span></span>  
 <span data-ttu-id="f2527-111">이 예에서는 **DiscontinuedDate** 열에 Null 값이 포함되어 있을 경우 TRUE를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f2527-111">This example returns TRUE if the **DiscontinuedDate** column contains a null value.</span></span>  
  
```  
ISNULL(DiscontinuedDate)  
```  
  
 <span data-ttu-id="f2527-112">이 예에서는 **LastName** 열에 Null 값이 포함되어 있을 경우 "Unknown last name"을 반환합니다. 그렇지 않으면 **LastName**이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2527-112">This example returns "Unknown last name" if the value in the **LastName** column is null, otherwise it returns the value in **LastName**.</span></span>  
  
```  
ISNULL(LastName)? "Unknown last name":LastName  
```  
  
 <span data-ttu-id="f2527-113">이 예에서는 **DaysToManufacture** 열에 Null 값이 포함되어 있을 경우 **AddDays**변수 값에 관계없이 항상 TRUE를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f2527-113">This example always returns TRUE if the **DaysToManufacture** column is null, regardless of the value of the variable **AddDays**.</span></span>  
  
```  
ISNULL(DaysToManufacture + @AddDays)  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2527-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2527-114">See Also</span></span>  
 <span data-ttu-id="f2527-115">[함수&#40;SSIS 식&#41;](functions-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="f2527-115">[Functions &#40;SSIS Expression&#41;](functions-ssis-expression.md) </span></span>  
 [<span data-ttu-id="f2527-116">COALESCE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f2527-116">COALESCE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/coalesce-transact-sql)  
  
  
