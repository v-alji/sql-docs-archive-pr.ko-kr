---
title: Level 함수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dedbf00ce8330242c95e9592f649d95171f0987a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650710"
---
# <a name="level-function-report-builder-and-ssrs"></a><span data-ttu-id="1ffe0-102">Level 함수(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="1ffe0-102">Level Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1ffe0-103">재귀 계층의 현재 수준을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffe0-103">Returns the current level of depth in a recursive hierarchy.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="1ffe0-104">구문</span><span class="sxs-lookup"><span data-stu-id="1ffe0-104">Syntax</span></span>  
  
```  
  
Level(scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ffe0-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="1ffe0-105">Parameters</span></span>  
 <span data-ttu-id="1ffe0-106">*범위*</span><span class="sxs-lookup"><span data-stu-id="1ffe0-106">*scope*</span></span>  
 <span data-ttu-id="1ffe0-107">(`String`) 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="1ffe0-107">(`String`) (Optional).</span></span> <span data-ttu-id="1ffe0-108">집계 함수를 적용할 보고서 항목을 포함하는 데이터 세트, 그룹 또는 데이터 영역의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1ffe0-108">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="1ffe0-109">*scope* 를 지정하지 않은 경우 현재 범위가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ffe0-109">If *scope* is not specified, the current scope is used.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="1ffe0-110">반환 형식</span><span class="sxs-lookup"><span data-stu-id="1ffe0-110">Return Type</span></span>  
 <span data-ttu-id="1ffe0-111">`Integer`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffe0-111">Returns an `Integer`.</span></span> <span data-ttu-id="1ffe0-112">*Scope* 가 데이터 집합 또는 데이터 영역을 지정 하거나 비재귀 그룹화 (요소 없는 그룹화)를 지정 하는 경우는 `Parent` 0을 `Level` 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffe0-112">If *scope* specifies a dataset or data region, or specifies a nonrecursive grouping (that is, a grouping with no `Parent` element), `Level` returns 0.</span></span> <span data-ttu-id="1ffe0-113">*scope* 를 생략하면 현재 범위의 수준이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ffe0-113">If *scope* is omitted, it returns the level of the current scope.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ffe0-114">설명</span><span class="sxs-lookup"><span data-stu-id="1ffe0-114">Remarks</span></span>  
 <span data-ttu-id="1ffe0-115">`Level` 함수에서 반환되는 값은 0에서 시작합니다. 즉, 계층의 첫 수준은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="1ffe0-115">The value returned by the `Level` function is zero based; that is, the first level in a hierarchy is 0.</span></span>  
  
 <span data-ttu-id="1ffe0-116">`Level` 함수는 직원 목록과 같은 재귀 계층에서 들여쓰기를 제공하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ffe0-116">The `Level` function can be used to provide indentation in a recursive hierarchy, such as an employee list.</span></span>  
  
 <span data-ttu-id="1ffe0-117">재귀 계층 구조에 대한 자세한 내용은 [재귀 계층 구조 그룹 만들기&#40;보고서 작성기 및 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ffe0-117">For more information about recursive hierarchies, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ffe0-118">예제</span><span class="sxs-lookup"><span data-stu-id="1ffe0-118">Example</span></span>  
 <span data-ttu-id="1ffe0-119">다음 코드 예에서는 Employees 그룹에서 행 수준을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffe0-119">The following code example provides the level of row in the Employees group:</span></span>  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ffe0-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ffe0-120">See Also</span></span>  
 <span data-ttu-id="1ffe0-121">[보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1ffe0-121">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1ffe0-122">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1ffe0-122">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1ffe0-123">[식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1ffe0-123">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1ffe0-124">합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ffe0-124">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
