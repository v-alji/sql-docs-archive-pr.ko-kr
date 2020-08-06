---
title: 쿼리 및 필터 (브라우저 탭, 큐브 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.filterpane.f1
ms.assetid: f5cf0bb1-3afb-4856-a2ef-614deb4e7e49
author: minewiskan
ms.author: owend
ms.openlocfilehash: 66bd299e210b3d00384395177cdd6e89d1c00183
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649244"
---
# <a name="query-and-filter-browser-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="8d58d-102">쿼리 및 필터(브라우저 탭, 큐브 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="8d58d-102">Query and Filter (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="8d58d-103">큐브 디자이너 **브라우저** 탭의 이 영역에는 찾아보기 또는 쿼리에서 사용할 데이터를 큐브에서 선택할 수 있는 쿼리 및 필터 영역이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-103">This area of the **Browser** tab in Cube Designer contains a query and filter area, to help you choose data from the cube to use in browsing or in queries.</span></span> <span data-ttu-id="8d58d-104">원하는 수의 큐브 개체를 추가한 다음 데이터 영역에서 결과를 보거나 Excel에서 분석을 사용하여 결과를 보고서로 내보내 최종 사용자에게 데이터가 어떻게 표시되는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-104">You can add as many cube objects as you want, and then view the results in the data area, or export the results to a report using Analyze in Excel to visualize how the data would be viewed by end users.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="8d58d-105">이 영역의 데이터를 사용하는 경우 **브라우저** 는 기본적으로 그래픽 디자인 모드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-105">When you are working with data in this area, by default the **Browser** uses the graphical design mode.</span></span> <span data-ttu-id="8d58d-106">하지만 **디자인 모드** 토글 단추를 클릭하면 MDX를 사용하여 쿼리를 직접 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-106">However, you can edit the query directly using MDX, by clicking the **Design Mode** toggle button.</span></span> <span data-ttu-id="8d58d-107">이 경우 차원에서 필터를 디자인하는 창이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-107">When you do so, the pane that lets you design filters on dimensions disappears.</span></span> <span data-ttu-id="8d58d-108">필터를 추가하려면 그래픽 디자인 모드로 다시 전환하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-108">If you want to add a filter, you can switch back to graphical design mode.</span></span>  
  
 <span data-ttu-id="8d58d-109">기본적으로 쿼리를 실행할 때 **가장 정보** 페이지에 지정된 자격 증명이 아니라 현재 사용자의 자격 증명을 사용하여 데이터 원본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-109">By default, the credentials of the current user, not the credentials specified in the **Impersonation Information** page, are used to connect to the data source when a query is executed.</span></span> <span data-ttu-id="8d58d-110">하지만 **도구 모음** 에서 **사용자 변경**을 클릭하여 쿼리 또는 보고서의 사용자 컨텍스트를 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-110">However, you can also change the user context for the query or report by clicking **Change User** on the **Toolbar**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8d58d-111">옵션</span><span class="sxs-lookup"><span data-stu-id="8d58d-111">Options</span></span>  
 <span data-ttu-id="8d58d-112">**크기**</span><span class="sxs-lookup"><span data-stu-id="8d58d-112">**Dimension**</span></span>  
 <span data-ttu-id="8d58d-113">하위 큐브를 조각화할 차원을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-113">Select the dimension on which to slice the subcube.</span></span>  
  
 <span data-ttu-id="8d58d-114">**계층**</span><span class="sxs-lookup"><span data-stu-id="8d58d-114">**Hierarchy**</span></span>  
 <span data-ttu-id="8d58d-115">하위 큐브를 조각화할 계층을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-115">Select the hierarchy on which to slice the subcube.</span></span>  
  
 <span data-ttu-id="8d58d-116">**연산자**</span><span class="sxs-lookup"><span data-stu-id="8d58d-116">**Operator**</span></span>  
 <span data-ttu-id="8d58d-117">**필터 식** 의 식이 선택한 계층에 적용되는 방법을 정의하는 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-117">Select the operator that defines how the expression in **Filter Expression** is applied to the selected hierarchy.</span></span> <span data-ttu-id="8d58d-118">다음 표에서는 사용 가능한 연산자에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-118">The following table describes the available operators.</span></span>  
  
|<span data-ttu-id="8d58d-119">값</span><span class="sxs-lookup"><span data-stu-id="8d58d-119">Value</span></span>|<span data-ttu-id="8d58d-120">Description</span><span class="sxs-lookup"><span data-stu-id="8d58d-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8d58d-121">**같음**</span><span class="sxs-lookup"><span data-stu-id="8d58d-121">**Equal**</span></span>|<span data-ttu-id="8d58d-122">**필터 식**에서 정의한 집합으로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-122">The results are restricted to the set defined in **Filter Expression**.</span></span>|  
|<span data-ttu-id="8d58d-123">**같지 않음**</span><span class="sxs-lookup"><span data-stu-id="8d58d-123">**Not Equal**</span></span>|<span data-ttu-id="8d58d-124">**필터 식**에서 정의한 집합에서 제외된 멤버로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-124">The results are restricted to the members excluded by the set defined in **Filter Expression**.</span></span>|  
|<span data-ttu-id="8d58d-125">**진행**</span><span class="sxs-lookup"><span data-stu-id="8d58d-125">**In**</span></span>|<span data-ttu-id="8d58d-126">**필터 식**에서 선택한 명명된 집합으로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-126">The results are restricted to the named set chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="8d58d-127">**속하지 않음**</span><span class="sxs-lookup"><span data-stu-id="8d58d-127">**Not In**</span></span>|<span data-ttu-id="8d58d-128">**필터 식**에서 선택한 명명된 집합에서 제외된 멤버로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-128">The results are restricted to the members excluded by the named set chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="8d58d-129">**포함**</span><span class="sxs-lookup"><span data-stu-id="8d58d-129">**Contains**</span></span>|<span data-ttu-id="8d58d-130">이름에 **필터 식**의 문자열이 포함된 멤버로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-130">The results are restricted to members whose member names contain the string in **Filter Expression**.</span></span>|  
|<span data-ttu-id="8d58d-131">**시작 문자**</span><span class="sxs-lookup"><span data-stu-id="8d58d-131">**Begins With**</span></span>|<span data-ttu-id="8d58d-132">이름이 **필터 식**의 문자열로 시작하는 멤버로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-132">The results are restricted to members whose member names begin with the string in **Filter Expression**.</span></span>|  
|<span data-ttu-id="8d58d-133">**범위(포함)**</span><span class="sxs-lookup"><span data-stu-id="8d58d-133">**Range (Inclusive)**</span></span>|<span data-ttu-id="8d58d-134">**필터 식**에서 선택한 범위로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-134">The results are restricted to the range chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="8d58d-135">**범위(제외)**</span><span class="sxs-lookup"><span data-stu-id="8d58d-135">**Range (Exclusive)**</span></span>|<span data-ttu-id="8d58d-136">**필터 식**에서 선택한 범위에서 제외된 멤버로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-136">The results are restricted to the members excluded by the range chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="8d58d-137">**MDX**</span><span class="sxs-lookup"><span data-stu-id="8d58d-137">**MDX**</span></span>|<span data-ttu-id="8d58d-138">**필터 식**에서 설정한 MDX(Multidimensional Expression) 식으로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-138">The results are restricted to the Multidimensional Expressions (MDX) expression set in **Filter Expression**.</span></span>|  
  
 <span data-ttu-id="8d58d-139">**필터 식**</span><span class="sxs-lookup"><span data-stu-id="8d58d-139">**Filter Expression**</span></span>  
 <span data-ttu-id="8d58d-140">검색 결과가 제한되도록 **연산자**로 계산할 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-140">Type the expression that is to be evaluated by **Operator**, which restricts the results to be browsed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8d58d-141">이 필드는 선택한 연산자에 필요한 데이터 형식에 따라 모양이 변경되는 동적 데이터 입력 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8d58d-141">This field is a dynamic data entry element, changing appearance to reflect the types of data necessary for the selected operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d58d-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8d58d-142">See Also</span></span>  
 <span data-ttu-id="8d58d-143">[큐브 디자이너 &#40;Analysis Services 다차원 데이터&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8d58d-143">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="8d58d-144">[브라우저 &#40;큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8d58d-144">[Browser &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="8d58d-145">[도구 모음 &#40;브라우저 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8d58d-145">[Toolbar &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="8d58d-146">[Excel에서 분석 &#40;브라우저 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8d58d-146">[Analyze in Excel &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="8d58d-147">메타 데이터 &#40;브라우저 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="8d58d-147">Metadata &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md)  
  
  
