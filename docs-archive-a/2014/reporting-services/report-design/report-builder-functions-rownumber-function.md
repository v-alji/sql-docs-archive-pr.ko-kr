---
title: RowNumber 함수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9d718ba8-d323-49fb-aac8-e7013a117b75
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9f3d16188138c2f268305fddb092d56be870a3f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650694"
---
# <a name="rownumber-function-report-builder-and-ssrs"></a><span data-ttu-id="c7999-102">RowNumber 함수(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="c7999-102">RowNumber Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c7999-103">지정한 범위에서 행 개수의 실행 개수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7999-103">Returns a running count of the number of rows for the specified scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="c7999-104">구문</span><span class="sxs-lookup"><span data-stu-id="c7999-104">Syntax</span></span>  
  
```  
  
RowNumber(scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7999-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7999-105">Parameters</span></span>  
 <span data-ttu-id="c7999-106">*범위*</span><span class="sxs-lookup"><span data-stu-id="c7999-106">*scope*</span></span>  
 <span data-ttu-id="c7999-107">(`String`) 행 개수를 계산할 컨텍스트를 지정하는 데이터 세트, 데이터 영역, 그룹의 이름 또는 Null([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]의 `Nothing`)입니다.</span><span class="sxs-lookup"><span data-stu-id="c7999-107">(`String`) The name of a dataset, data region, or group, or null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), that specifies the context in which to evaluate the number of rows.</span></span> <span data-ttu-id="c7999-108">`Nothing`은 가장 바깥쪽 컨텍스트를 지정하며 이는 일반적으로 보고서 데이터 세트입니다.</span><span class="sxs-lookup"><span data-stu-id="c7999-108">`Nothing` specifies the outermost context, usually the report dataset.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7999-109">설명</span><span class="sxs-lookup"><span data-stu-id="c7999-109">Remarks</span></span>  
 <span data-ttu-id="c7999-110">`RowNumber`[RunningValue](report-builder-functions-runningvalue-function.md) 가 집계 함수의 실행 값을 반환 하는 것 처럼 지정 된 범위 내에서 행 개수의 실행 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7999-110">`RowNumber` returns a running value of the count of rows within the specified scope, just as [RunningValue](report-builder-functions-runningvalue-function.md) returns the running value of an aggregate function.</span></span> <span data-ttu-id="c7999-111">범위를 지정할 때 행 개수를 1로 다시 설정할 시점을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7999-111">When you specify a scope, you specify when to reset the row count to 1.</span></span>  
  
 <span data-ttu-id="c7999-112">*scope* 는 식이 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7999-112">*scope* cannot be an expression.</span></span> <span data-ttu-id="c7999-113">*scope* 는 포함하는 범위여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7999-113">*scope* must be a containing scope.</span></span> <span data-ttu-id="c7999-114">가장 바깥쪽에서 가장 안쪽 포함까지의 일반적인 범위는 보고서 데이터 세트, 데이터 영역, 행 그룹 또는 열 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="c7999-114">Typical scopes, from the outermost to the innermost containment, are report dataset, data region, row groups or column groups.</span></span>  
  
 <span data-ttu-id="c7999-115">열에 걸쳐 값을 증가시키려면 열 그룹의 이름인 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7999-115">To increment values across columns, specify a scope that is the name of a column group.</span></span> <span data-ttu-id="c7999-116">행에 따라 수를 증가시키려면 행 그룹의 이름인 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7999-116">To increment numbers down rows, specify a scope that is the name of a row group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c7999-117">행 그룹과 열 그룹 모두를 지정하는 집계를 하나의 식에 포함하는 것은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7999-117">Including aggregates that specify both a row group and a column group in a single expression is not supported.</span></span>  
  
 <span data-ttu-id="c7999-118">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 및 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7999-118">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="code-example"></a><span data-ttu-id="c7999-119">코드 예</span><span class="sxs-lookup"><span data-stu-id="c7999-119">Code Example</span></span>  
 <span data-ttu-id="c7999-120">다음은 항상 흰색으로 시작되는 각 그룹의 정보 행 색을 대체하기 위해 테이블릭스 데이터 영역 정보 행의 `BackgroundColor` 속성에 사용할 수 있는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="c7999-120">The following is an expression that you can use for the `BackgroundColor` property of a Tablix data region detail row to alternate the color of detail rows for each group, always beginning with White.</span></span>  
  
```  
=IIF(RowNumber("GroupbyCategory") Mod 2, "White", "PaleGreen")  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7999-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7999-121">See Also</span></span>  
 <span data-ttu-id="c7999-122">[보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c7999-122">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c7999-123">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c7999-123">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c7999-124">[식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c7999-124">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c7999-125">합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c7999-125">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
