---
title: KPI 브라우저 (Kpi 탭, 큐브 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpibrowserpane.f1
ms.assetid: 2f61bde6-e6ec-4511-8645-c272374014ad
author: minewiskan
ms.author: owend
ms.openlocfilehash: 591dfb7c27842e365b78484153dbbde3713b452e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647949"
---
# <a name="kpi-browser-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="e2648-102">KPI 브라우저(KPI 탭, 큐브 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="e2648-102">KPI Browser (KPIs Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="e2648-103">큐브 디자이너의 **KPI** 탭에 있는 **KPI 브라우저** 창을 사용하여 KPI(핵심 성과 지표)의 결과를 보고 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-103">Use the **KPI Browser** pane on the **KPIs** tab in Cube Designer to view and test the results of Key Performance Indicators (KPIs).</span></span> <span data-ttu-id="e2648-104">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 검색 하기 전에 먼저 kpi를 인스턴스에 배포 해야 합니다 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e2648-104">KPIs must first be deployed to a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance before browsing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2648-105">이 창은 브라우저 보기에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-105">This pane is displayed only in browser view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e2648-106">옵션</span><span class="sxs-lookup"><span data-stu-id="e2648-106">Options</span></span>  
 <span data-ttu-id="e2648-107">**하위 큐브 표**</span><span class="sxs-lookup"><span data-stu-id="e2648-107">**Subcube grid**</span></span>  
 <span data-ttu-id="e2648-108">하위 큐브를 정의하고 **결과** 창에 표시할 KPI 결과를 제한하려면 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-108">Use to define a subcube and restrict the results of the KPIs to be displayed in the **Results** pane.</span></span> <span data-ttu-id="e2648-109">표에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-109">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="e2648-110">**크기**</span><span class="sxs-lookup"><span data-stu-id="e2648-110">**Dimension**</span></span>  
 <span data-ttu-id="e2648-111">이 필터를 적용할 차원을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-111">Select the dimension to which this filter applies.</span></span>  
  
 <span data-ttu-id="e2648-112">**계층**</span><span class="sxs-lookup"><span data-stu-id="e2648-112">**Hierarchy**</span></span>  
 <span data-ttu-id="e2648-113">이 필터를 적용할 계층을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-113">Select the hierarchy to which this filter applies.</span></span>  
  
 <span data-ttu-id="e2648-114">**연산자**</span><span class="sxs-lookup"><span data-stu-id="e2648-114">**Operator**</span></span>  
 <span data-ttu-id="e2648-115">**필터 식** 의 식이 선택한 계층에 적용되는 방법을 정의하는 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-115">Select the operator that defines how the expression in **Filter Expression** is applied to the selected hierarchy.</span></span> <span data-ttu-id="e2648-116">다음 표에서는 사용 가능한 연산자에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-116">The following table describes the available operators.</span></span>  
  
|<span data-ttu-id="e2648-117">값</span><span class="sxs-lookup"><span data-stu-id="e2648-117">Value</span></span>|<span data-ttu-id="e2648-118">Description</span><span class="sxs-lookup"><span data-stu-id="e2648-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e2648-119">**같음**</span><span class="sxs-lookup"><span data-stu-id="e2648-119">**Equal**</span></span>|<span data-ttu-id="e2648-120">**필터 식**에서 정의한 집합으로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-120">The results are restricted to the set defined in **Filter Expression**.</span></span>|  
|<span data-ttu-id="e2648-121">**같지 않음**</span><span class="sxs-lookup"><span data-stu-id="e2648-121">**Not Equal**</span></span>|<span data-ttu-id="e2648-122">**필터 식**에서 정의한 집합에서 제외된 멤버로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-122">The results are restricted to the members excluded by the set defined in **Filter Expression**.</span></span>|  
|<span data-ttu-id="e2648-123">**진행**</span><span class="sxs-lookup"><span data-stu-id="e2648-123">**In**</span></span>|<span data-ttu-id="e2648-124">**필터 식**에서 선택한 명명된 집합으로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-124">The results are restricted to the named set chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="e2648-125">**속하지 않음**</span><span class="sxs-lookup"><span data-stu-id="e2648-125">**Not In**</span></span>|<span data-ttu-id="e2648-126">**필터 식**에서 선택한 명명된 집합에서 제외된 멤버로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-126">The results are restricted to the members excluded by the named set chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="e2648-127">**포함**</span><span class="sxs-lookup"><span data-stu-id="e2648-127">**Contains**</span></span>|<span data-ttu-id="e2648-128">이름에 **필터 식**의 문자열이 포함된 멤버로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-128">The results are restricted to members whose member names contain the string in **Filter Expression**.</span></span>|  
|<span data-ttu-id="e2648-129">**시작 문자**</span><span class="sxs-lookup"><span data-stu-id="e2648-129">**Begins With**</span></span>|<span data-ttu-id="e2648-130">이름이 **필터 식**의 문자열로 시작하는 멤버로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-130">The results are restricted to members whose member names begin with the string in **Filter Expression**.</span></span>|  
|<span data-ttu-id="e2648-131">**범위(포함)**</span><span class="sxs-lookup"><span data-stu-id="e2648-131">**Range (Inclusive)**</span></span>|<span data-ttu-id="e2648-132">**필터 식**에서 선택한 범위로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-132">The results are restricted to the range chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="e2648-133">**범위(제외)**</span><span class="sxs-lookup"><span data-stu-id="e2648-133">**Range (Exclusive)**</span></span>|<span data-ttu-id="e2648-134">**필터 식**에서 선택한 범위에서 제외된 멤버로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-134">The results are restricted to the members excluded by the range chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="e2648-135">**MDX**</span><span class="sxs-lookup"><span data-stu-id="e2648-135">**MDX**</span></span>|<span data-ttu-id="e2648-136">**필터 식**에서 설정한 MDX(Multidimensional Expression) 식으로 결과가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-136">The results are restricted to the Multidimensional Expressions (MDX) expression set in **Filter Expression**.</span></span>|  
  
 <span data-ttu-id="e2648-137">**필터 식**</span><span class="sxs-lookup"><span data-stu-id="e2648-137">**Filter Expression**</span></span>  
 <span data-ttu-id="e2648-138">**연산자**를 사용하여 계산할 식을 입력합니다. 이 식은 검색할 KPI를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-138">Type the expression that is to be evaluated by **Operator**, which restricts the KPI results to be browsed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2648-139">이 필드는 선택한 연산자에 필요한 데이터 형식에 따라 모양이 변경되는 동적 데이터 입력 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-139">This field is a dynamic data entry element, changing appearance to reflect the types of data necessary for the selected operator.</span></span>  
  
 <span data-ttu-id="e2648-140">**결과 표**</span><span class="sxs-lookup"><span data-stu-id="e2648-140">**Results grid**</span></span>  
 <span data-ttu-id="e2648-141">**필터 표**에 정의된 필터를 기준으로 평가한 KPI의 값, 목표, 상태 및 추세를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-141">Displays the evaluated value, goal, status, and trend for the KPIs, based on the filter defined in **Filter grid**.</span></span> <span data-ttu-id="e2648-142">표에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-142">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="e2648-143">**표시 구조**</span><span class="sxs-lookup"><span data-stu-id="e2648-143">**Display Structure**</span></span>  
 <span data-ttu-id="e2648-144">큐브에 포함된 KPI를 각 KPI에 대한 **표시 폴더** 또는 **부모 KPI** 값에 따라 계층적으로 구성하여 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-144">Displays the KPIs contained by the cube, hierarchically organized according to the **Display folder** or **Parent KPI** values for each KPI.</span></span>  
  
 <span data-ttu-id="e2648-145">**값**</span><span class="sxs-lookup"><span data-stu-id="e2648-145">**Value**</span></span>  
 <span data-ttu-id="e2648-146">KPI 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-146">Displays the value of the KPI.</span></span>  
  
 <span data-ttu-id="e2648-147">**Goal**</span><span class="sxs-lookup"><span data-stu-id="e2648-147">**Goal**</span></span>  
 <span data-ttu-id="e2648-148">KPI의 목표 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-148">Displays the goal value of the KPI.</span></span>  
  
 <span data-ttu-id="e2648-149">**상태**</span><span class="sxs-lookup"><span data-stu-id="e2648-149">**Status**</span></span>  
 <span data-ttu-id="e2648-150">KPI의 상태 그래픽을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-150">Displays the status graphic of the KPI.</span></span>  
  
 <span data-ttu-id="e2648-151">**추세**</span><span class="sxs-lookup"><span data-stu-id="e2648-151">**Trend**</span></span>  
 <span data-ttu-id="e2648-152">KPI의 추세 그래픽을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-152">Displays the trend graphic of the KPI.</span></span>  
  
 <span data-ttu-id="e2648-153">**Weight**</span><span class="sxs-lookup"><span data-stu-id="e2648-153">**Weight**</span></span>  
 <span data-ttu-id="e2648-154">KPI의 가중치 요인을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-154">Displays the weight factor of the KPI.</span></span>  
  
 <span data-ttu-id="e2648-155">**한**</span><span class="sxs-lookup"><span data-stu-id="e2648-155">**(Description)**</span></span>  
 <span data-ttu-id="e2648-156">KPI에 대한 설명이 제공된 경우 정보 아이콘을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-156">Displays an information icon if a description is provided for a KPI.</span></span>  
  
 <span data-ttu-id="e2648-157">정보 아이콘을 마우스로 가리키면 KPI에 대한 설명이 포함된 도구 설명이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-157">Hover the mouse over the information icon to display a ToolTip containing the description for the KPI.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2648-158">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에서 KPI를 계산하는 동안 오류가 발생하면 이 옵션은 해당 오류와 관련된 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2648-158">If an error occurs while calculating a KPI on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, this option displays information associated with the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2648-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2648-159">See Also</span></span>  
 [<span data-ttu-id="e2648-160">큐브 디자이너 &#40;Kpi&#41; &#40;Analysis Services-다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="e2648-160">KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](kpis-cube-designer-analysis-services-multidimensional-data.md)  
  
  
