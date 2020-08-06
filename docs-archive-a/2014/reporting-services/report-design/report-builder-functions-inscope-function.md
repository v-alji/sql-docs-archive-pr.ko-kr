---
title: InScope 함수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62c4ad5de7af1ac0762df29deaa17953a8a378db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650712"
---
# <a name="inscope-function-report-builder-and-ssrs"></a><span data-ttu-id="59845-102">InScope 함수(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="59845-102">InScope Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="59845-103">항목의 현재 인스턴스가 지정한 범위 내에 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="59845-103">Indicates whether the current instance of an item is in the specified scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="59845-104">구문</span><span class="sxs-lookup"><span data-stu-id="59845-104">Syntax</span></span>  
  
```  
InScope(scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59845-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="59845-105">Parameters</span></span>  
 <span data-ttu-id="59845-106">*범위*</span><span class="sxs-lookup"><span data-stu-id="59845-106">*scope*</span></span>  
 <span data-ttu-id="59845-107">(`String`) 범위를 지정하는 데이터 세트, 데이터 영역 또는 그룹의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="59845-107">(`String`) The name of a dataset, data region, or group that specifies a scope.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="59845-108">반환 형식</span><span class="sxs-lookup"><span data-stu-id="59845-108">Return Type</span></span>  
 <span data-ttu-id="59845-109">`Boolean`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="59845-109">Returns a `Boolean`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59845-110">설명</span><span class="sxs-lookup"><span data-stu-id="59845-110">Remarks</span></span>  
 <span data-ttu-id="59845-111">`InScope`함수는 *범위*매개 변수로 지정 된 범위의 멤버 자격에 대해 보고서 항목의 현재 인스턴스 범위를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="59845-111">The `InScope` function tests the scope of the current instance of a report item for membership in the scope specified by the *scope*parameter.</span></span>  
  
 <span data-ttu-id="59845-112">*Scope* 는 식이 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59845-112">*Scope* cannot be an expression.</span></span>  
  
 <span data-ttu-id="59845-113">`InScope` 함수는 일반적으로 동적으로 범위가 지정되는 데이터 영역에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="59845-113">A typical use for the `InScope` function is in data regions that have dynamic scoping.</span></span> <span data-ttu-id="59845-114">예를 들어 데이터 영역 셀의 드릴스루 링크에 `InScope`를 사용하여 클릭한 셀에 따라 다양한 보고서 이름과 다양한 매개 변수 집합을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59845-114">For example, `InScope` can be used in a drillthrough link in a data region cells to provide a different report name and different sets of parameters depending on which cell is clicked.</span></span> <span data-ttu-id="59845-115">이러한 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="59845-115">An example of this is as follows:</span></span>  
  
-   <span data-ttu-id="59845-116">드릴스루 링크의 보고서 이름으로 사용된 다음 식은 클릭한 셀이 `ProductDetail` 그룹에 있으면 `Month` 보고서를 열고 그렇지 않으면 `ProductSummary` 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="59845-116">The following expression, used as the report name in a drillthrough link, opens the `ProductDetail` report if the clicked cell is in the `Month` group, and the `ProductSummary` report if it is not.</span></span>  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   <span data-ttu-id="59845-117">드릴스루 보고서 매개 변수의 `Omit` 속성에 사용된 다음 식은 클릭한 셀이 `Product` 그룹에 있는 경우에만 대상 보고서에 매개 변수를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="59845-117">The following expression, used in the `Omit` property of a drillthrough report parameter, will pass the parameter to the target report only if the clicked cell is in the `Product` group.</span></span>  
  
    ```  
    =Not(InScope("Product"))  
    ```  
  
 <span data-ttu-id="59845-118">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 및 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59845-118">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="59845-119">예제</span><span class="sxs-lookup"><span data-stu-id="59845-119">Example</span></span>  
 <span data-ttu-id="59845-120">다음 코드 예에서는 항목의 현재 인스턴스가 `Product` 데이터 세트, 데이터 영역 또는 그룹 범위 내에 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="59845-120">The following code example indicates whether the current instance of the item is in the `Product` dataset, data region, or group scope.</span></span>  
  
```  
=InScope("Product")  
```  
  
## <a name="see-also"></a><span data-ttu-id="59845-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="59845-121">See Also</span></span>  
 <span data-ttu-id="59845-122">[보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="59845-122">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="59845-123">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="59845-123">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="59845-124">[식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="59845-124">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="59845-125">합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="59845-125">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
