---
title: CountRows 함수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5b1c403d-6afd-44c8-b5f6-5ecff2a29a45
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6d5311dfc5dfcb89449a4039fdac4100fc5a3b47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650719"
---
# <a name="countrows-function-report-builder-and-ssrs"></a><span data-ttu-id="45f75-102">CountRows 함수(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="45f75-102">CountRows Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="45f75-103">Null 값을 가진 행을 포함하여 지정된 범위의 행 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="45f75-103">Returns the number of rows in the specified scope, including rows with null values.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="45f75-104">구문</span><span class="sxs-lookup"><span data-stu-id="45f75-104">Syntax</span></span>  
  
```  
  
CountRows(scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45f75-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="45f75-105">Parameters</span></span>  
 <span data-ttu-id="45f75-106">*범위*</span><span class="sxs-lookup"><span data-stu-id="45f75-106">*scope*</span></span>  
 <span data-ttu-id="45f75-107">(`String`) 계산할 보고서 항목이 포함된 데이터 세트, 데이터 영역 또는 그룹의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="45f75-107">(`String`) The name of a dataset, data region, or group that contains the report items to count.</span></span>  
  
 <span data-ttu-id="45f75-108">*재귀*</span><span class="sxs-lookup"><span data-stu-id="45f75-108">*recursive*</span></span>  
 <span data-ttu-id="45f75-109">(**열거 형식**) 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="45f75-109">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="45f75-110">`Simple`(기본값) 또는 `RdlRecursive`로,</span><span class="sxs-lookup"><span data-stu-id="45f75-110">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="45f75-111">집계를 재귀적으로 수행할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="45f75-111">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="45f75-112">반환 형식</span><span class="sxs-lookup"><span data-stu-id="45f75-112">Return Type</span></span>  
 <span data-ttu-id="45f75-113">`Integer`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="45f75-113">Returns an `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45f75-114">설명</span><span class="sxs-lookup"><span data-stu-id="45f75-114">Remarks</span></span>  
 <span data-ttu-id="45f75-115">`CountRows`는 Null 값을 가진 행을 포함하여 지정된 범위의 모든 행을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="45f75-115">`CountRows` counts all rows in the specified scope, including rows that have null values.</span></span>  
  
 <span data-ttu-id="45f75-116">*scope* 값은 식이 될 수 없으며 현재 범위 또는 포함하는 범위를 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45f75-116">The value of *scope* cannot be an expression and must refer to the current scope or a containing scope.</span></span>  
  
 <span data-ttu-id="45f75-117">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 및 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45f75-117">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="45f75-118">재귀 집계에 대한 자세한 내용은 [재귀 계층 구조 그룹 만들기&#40;보고서 작성기 및 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45f75-118">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="45f75-119">예제</span><span class="sxs-lookup"><span data-stu-id="45f75-119">Example</span></span>  
 <span data-ttu-id="45f75-120">다음 코드 예에서는 `GroupbyCategory` 라는 행 그룹에 있는 행의 수를 계산하는 식을 보여 줍니다( `[Category]`식 기반).</span><span class="sxs-lookup"><span data-stu-id="45f75-120">The following code example shows an expression that calculates the number of rows in a row group named `GroupbyCategory` (based on the expression `[Category]`).</span></span>  
  
```  
="Number of rows: " & CountRows("GroupbyCategory")  
```  
  
## <a name="see-also"></a><span data-ttu-id="45f75-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45f75-121">See Also</span></span>  
 <span data-ttu-id="45f75-122">[보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="45f75-122">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="45f75-123">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="45f75-123">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="45f75-124">[식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="45f75-124">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="45f75-125">합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="45f75-125">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
