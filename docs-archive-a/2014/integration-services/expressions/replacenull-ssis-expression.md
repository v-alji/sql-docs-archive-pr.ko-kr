---
title: REPLACENULL(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 70db7832-b5a0-4db5-a8ad-42ad8630d8e8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f10bb6ef6102076fe7b1cc236461e2358ad96372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732820"
---
# <a name="replacenull-ssis-expression"></a><span data-ttu-id="19c0c-102">REPLACENULL(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="19c0c-102">REPLACENULL (SSIS Expression)</span></span>
  <span data-ttu-id="19c0c-103">첫 번째 식 매개 변수의 값이 NULL이면 두 번째 식 매개 변수의 값을 반환하고, 그렇지 않으면 첫 번째 식의 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="19c0c-103">Returns the value of second expression parameter if the value of first expression parameter is NULL; otherwise, returns the value of first expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19c0c-104">구문</span><span class="sxs-lookup"><span data-stu-id="19c0c-104">Syntax</span></span>  
  
```vb  
REPLACENULL(expression 1,expression 2)  
```  
  
## <a name="arguments"></a><span data-ttu-id="19c0c-105">인수</span><span class="sxs-lookup"><span data-stu-id="19c0c-105">Arguments</span></span>  
 <span data-ttu-id="19c0c-106">*expression 1*</span><span class="sxs-lookup"><span data-stu-id="19c0c-106">*expression 1*</span></span>  
 <span data-ttu-id="19c0c-107">이 식의 결과를 NULL과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="19c0c-107">The result of this expression is checked against NULL.</span></span>  
  
 <span data-ttu-id="19c0c-108">*expression 2*</span><span class="sxs-lookup"><span data-stu-id="19c0c-108">*expression 2*</span></span>  
 <span data-ttu-id="19c0c-109">첫 번째 식이 NULL로 평가되면 이 식의 결과가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="19c0c-109">The result of this expression is returned if the first expression evaluates to NULL.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="19c0c-110">결과 형식</span><span class="sxs-lookup"><span data-stu-id="19c0c-110">Result Types</span></span>  
 <span data-ttu-id="19c0c-111">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="19c0c-111">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19c0c-112">설명</span><span class="sxs-lookup"><span data-stu-id="19c0c-112">Remarks</span></span>  
  
-   <span data-ttu-id="19c0c-113">*expression 2* 길이는 0이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19c0c-113">The length of *expression 2* may be zero.</span></span>  
  
-   <span data-ttu-id="19c0c-114">인수가 Null이면 REPLACENULL은 Null을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="19c0c-114">REPLACENULL returns a null result if any argument is null.</span></span>  
  
-   <span data-ttu-id="19c0c-115">BLOB 열(DT_TEXT, DT_NTEXT, DT_IMAGE)은 이 두 매개 변수에 대해 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19c0c-115">BLOB columns (DT_TEXT, DT_NTEXT, DT_IMAGE) are not supported for either parameter.</span></span>  
  
-   <span data-ttu-id="19c0c-116">두 식은 반환 형식이 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19c0c-116">The two expressions are expected to have the same return type.</span></span> <span data-ttu-id="19c0c-117">동일하지 않으면 함수가 두 번째 식을 첫 번째 식의 반환 형식으로 캐스팅하려고 하므로 데이터 형식이 호환되지 않는 경우 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19c0c-117">If they do not, the function attempts to cast the 2nd expression to the return type of the 1st expression, which may result in an error if the data types are incompatible.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="19c0c-118">식 예</span><span class="sxs-lookup"><span data-stu-id="19c0c-118">Expression Examples</span></span>  
 <span data-ttu-id="19c0c-119">다음 예에서는 데이터베이스 열의 NULL 값을 문자열(1900-01-01)로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="19c0c-119">The following example replaces any NULL value in a database column with a string (1900-01-01).</span></span> <span data-ttu-id="19c0c-120">이 함수는 특히 NULL 값을 다른 값으로 바꾸려는 공용 파생 열 패턴에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="19c0c-120">This function is especially used in common Derived Column patterns where you want to replace NULL values with something else.</span></span>  
  
```  
REPLACENULL(MyColumn, "1900-01-01")  
```  
  
> [!NOTE]  
>  <span data-ttu-id="19c0c-121">다음 예에서는 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]/[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]에서 이 함수를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="19c0c-121">The following example shows how it was done in [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]/[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)].</span></span>  
  
```  
(DT_DBTIMESTAMP) (ISNULL(MyColumn) ? "1900-01-01" : MyColumn)   
```  
  
  
