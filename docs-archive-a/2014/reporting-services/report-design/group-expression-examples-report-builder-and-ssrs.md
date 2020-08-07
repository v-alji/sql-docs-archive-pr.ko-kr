---
title: 그룹 식 예(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data [Reporting Services], grouping
- grouping data
- expressions [Reporting Services], adding
- groups [Reporting Services], expressions
ms.assetid: 34cd0249-fc74-4cf2-ba11-7b072992bfd2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 128e3fa7aed189fd00072c2c3e961b80f8137c99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727976"
---
# <a name="group-expression-examples-report-builder-and-ssrs"></a><span data-ttu-id="3c125-102">그룹 식 예(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="3c125-102">Group Expression Examples (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3c125-103">데이터 영역에서 단일 필드를 기준으로 데이터를 그룹화하거나 그룹화할 데이터를 식별하는 보다 복잡한 식을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c125-103">In a data region, you can group data by a single field, or create more complex expressions that identify the data on which to group.</span></span> <span data-ttu-id="3c125-104">복잡한 식에는 여러 필드 또는 매개 변수에 대한 참조, 조건문 또는 사용자 지정 코드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c125-104">Complex expressions include references to multiple fields or parameters, conditional statements, or custom code.</span></span> <span data-ttu-id="3c125-105">데이터 영역에 대해 그룹을 정의할 때 이러한 식을 **그룹** 속성에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3c125-105">When you define a group for a data region, you add these expressions to the **Group** properties.</span></span> <span data-ttu-id="3c125-106">자세한 내용은 [데이터 영역에서 그룹 추가 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c125-106">For more information, see [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="3c125-107">간단한 필드 식을 기반으로 하는 둘 이상의 그룹을 병합하려면 각 필드를 그룹 정의의 그룹 식 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3c125-107">To merge two or more groups that are based on simple field expressions, add each field to the group expressions list in the group definition.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="examples-of-group-expressions"></a><span data-ttu-id="3c125-108">그룹 식 예</span><span class="sxs-lookup"><span data-stu-id="3c125-108">Examples of Group Expressions</span></span>  
 <span data-ttu-id="3c125-109">다음 표에서는 그룹을 정의하는 데 사용할 수 있는 그룹 식의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3c125-109">The following table provides examples of group expressions that you can use to define a group.</span></span>  
  
|<span data-ttu-id="3c125-110">Description</span><span class="sxs-lookup"><span data-stu-id="3c125-110">Description</span></span>|<span data-ttu-id="3c125-111">식</span><span class="sxs-lookup"><span data-stu-id="3c125-111">Expression</span></span>|  
|-----------------|----------------|  
|<span data-ttu-id="3c125-112">`Region` 필드를 기준으로 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="3c125-112">Group by the `Region` field.</span></span>|`=Fields!Region.Value`|  
|<span data-ttu-id="3c125-113">성 및 이름을 기준으로 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="3c125-113">Group by last name and first name.</span></span>|`=Fields!LastName.Value`<br /><br /> `=Fields!FirstName.Value`|  
|<span data-ttu-id="3c125-114">성의 첫 문자를 기준으로 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="3c125-114">Group by the first letter of the last name.</span></span>|`=Fields!LastName.Value.Substring(0,1)`|  
|<span data-ttu-id="3c125-115">매개 변수를 기준으로 그룹화합니다(사용자 선택 기반).</span><span class="sxs-lookup"><span data-stu-id="3c125-115">Group by parameter, based on user selection.</span></span><br /><br /> <span data-ttu-id="3c125-116">이 예에서 매개 변수 `GroupBy` 는 그룹화할 유효 선택 항목을 제공하는 사용 가능한 값 목록을 기반으로 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c125-116">In this example, the parameter `GroupBy` must be based on an available values list that provides a valid choice to group on.</span></span>|`=Fields(Parameters!GroupBy.Value).Value`|  
|<span data-ttu-id="3c125-117">다음과 같은 세 나이 범위를 기준으로 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="3c125-117">Group by three separate age ranges:</span></span><br /><br /> <span data-ttu-id="3c125-118">"21세 미만", "21-50세", "51세 이상"</span><span class="sxs-lookup"><span data-stu-id="3c125-118">"Under 21", "Between 21 and 50", and "Over 50".</span></span>|`=IIF(First(Fields!Age.Value)<21,"Under 21",(IIF(First(Fields!Age.Value)>=21 AND First(Fields!Age.Value)<=50,"Between 21 and 50","Over 50")))`|  
|<span data-ttu-id="3c125-119">많은 나이 범위를 기준으로 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="3c125-119">Group by many age ranges.</span></span> <span data-ttu-id="3c125-120">이 예에서는 다음 범위에 대한 문자열을 반환하는 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET으로 작성된 사용자 지정 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3c125-120">This example shows custom code, written in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET, that returns a string for the following ranges:</span></span><br /><br /> <span data-ttu-id="3c125-121">25세 이하</span><span class="sxs-lookup"><span data-stu-id="3c125-121">25 or Under</span></span><br /><br /> <span data-ttu-id="3c125-122">26-50세</span><span class="sxs-lookup"><span data-stu-id="3c125-122">26 to 50</span></span><br /><br /> <span data-ttu-id="3c125-123">51 ~ 75</span><span class="sxs-lookup"><span data-stu-id="3c125-123">51 to 75</span></span><br /><br /> <span data-ttu-id="3c125-124">76세 이상</span><span class="sxs-lookup"><span data-stu-id="3c125-124">Over 75</span></span>|`=Code.GetRangeValueByAge(Fields!Age.Value)`<br /><br /> <span data-ttu-id="3c125-125">사용자 지정 코드:</span><span class="sxs-lookup"><span data-stu-id="3c125-125">Custom code:</span></span><br /><br /> `Function GetRangeValueByAge(ByVal age As Integer) As String`<br /><br /> `Select Case age`<br /><br /> `Case 0 To 25`<br /><br /> `GetRangeValueByByAge = "25 or Under"`<br /><br /> `Case 26 To 50`<br /><br /> `GetRangeValueByByAge = "26 to 50"`<br /><br /> `Case 51 to 75`<br /><br /> `GetRangeValueByByAge = "51 to 75"`<br /><br /> `Case Else`<br /><br /> `GetRangeValueByByAge = "Over 75"`<br /><br /> `End Select`<br /><br /> `Return GetRangeValueByByAge`<br /><br /> `End Function`|  
  
## <a name="see-also"></a><span data-ttu-id="3c125-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c125-126">See Also</span></span>  
 <span data-ttu-id="3c125-127">[데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3c125-127">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3c125-128">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3c125-128">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3c125-129">보고서 디자이너의 식에 포함된 사용자 지정 코드 및 어셈블리 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3c125-129">Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;</span></span>](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)  
  
  
