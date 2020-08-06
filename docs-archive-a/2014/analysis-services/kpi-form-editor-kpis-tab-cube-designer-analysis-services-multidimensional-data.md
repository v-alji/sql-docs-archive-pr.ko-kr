---
title: KPI 폼 편집기 (Kpi 탭, 큐브 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpidefinitionpane.f1
ms.assetid: 45c6453a-bbe2-4ca5-836e-c7ef11cfcb65
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c88d6fcec60634f37ddad8b6d0f5cb2124fa1cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647946"
---
# <a name="kpi-form-editor-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="e62db-102">KPI 폼 편집기(KPI 탭, 큐브 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="e62db-102">KPI Form Editor (KPIs Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="e62db-103">큐브 디자이너의 **KPI** 탭에 있는 **KPI 폼 편집기** 창을 사용하여 선택한 KPI(핵심 성과 지표)를 생성하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-103">Use the **KPI Form Editor** pane on the **KPIs** tab in Cube Designer to create or modify the selected Key Performance Indicator (KPI).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e62db-104">이 창은 폼 보기에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-104">This pane is displayed only in form view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e62db-105">옵션</span><span class="sxs-lookup"><span data-stu-id="e62db-105">Options</span></span>  
 <span data-ttu-id="e62db-106">**이름**</span><span class="sxs-lookup"><span data-stu-id="e62db-106">**Name**</span></span>  
 <span data-ttu-id="e62db-107">KPI의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-107">Type the name of the KPI.</span></span>  
  
 <span data-ttu-id="e62db-108">**관련된 측정값 그룹**</span><span class="sxs-lookup"><span data-stu-id="e62db-108">**Associated measure group**</span></span>  
 <span data-ttu-id="e62db-109">KPI와 관련된 측정값 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-109">Select the measure group associated with the KPI.</span></span> <span data-ttu-id="e62db-110">클라이언트 애플리케이션에서는 이 정보를 사용하여 사용자가 이 KPI를 찾아볼 때 사용할 수 있는 차원을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-110">The client application can use this information to determine which dimensions are available when the user browses this KPI.</span></span>  
  
 <span data-ttu-id="e62db-111">**값 식**</span><span class="sxs-lookup"><span data-stu-id="e62db-111">**Value Expression**</span></span>  
 <span data-ttu-id="e62db-112">KPI 값에 대한 MDX(Multidimensional Expression) 식을 보거나 편집하려면 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-112">Expand to view or edit the Multidimensional Expressions (MDX) expression for the value of the KPI.</span></span>  
  
 <span data-ttu-id="e62db-113">KPI 값을 반환하는 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-113">Type the MDX expression that returns the value of the KPI.</span></span>  
  
 <span data-ttu-id="e62db-114">**계산 도구** 창에서 선택한 요소를 이 옵션으로 끌어서 놓으면 선택한 요소의 MDX 구문을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-114">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="e62db-115">**목표 식**</span><span class="sxs-lookup"><span data-stu-id="e62db-115">**Goal Expression**</span></span>  
 <span data-ttu-id="e62db-116">KPI의 목표 값에 대한 MDX 식을 보거나 편집하려면 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-116">Expand to view or edit the MDX expression for the goal value of the KPI.</span></span>  
  
 <span data-ttu-id="e62db-117">KPI 실행 시 KPI의 목표 값을 반환하는 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-117">Type the MDX expression that returns the goal value of the KPI when the KPI is run.</span></span>  
  
 <span data-ttu-id="e62db-118">**계산 도구** 창에서 선택한 요소를 이 옵션으로 끌어서 놓으면 선택한 요소의 MDX 구문을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-118">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="e62db-119">**상태**</span><span class="sxs-lookup"><span data-stu-id="e62db-119">**Status**</span></span>  
 <span data-ttu-id="e62db-120">**상태 그래픽** 및 **상태 식** 옵션을 보려면 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-120">Expand to view the **Status graphic** and **Status expression** options.</span></span>  
  
 <span data-ttu-id="e62db-121">**상태 그래픽**</span><span class="sxs-lookup"><span data-stu-id="e62db-121">**Status graphic**</span></span>  
 <span data-ttu-id="e62db-122">클라이언트 애플리케이션에서 상태 값을 그래픽 형식으로 나타내기 위해 사용할 그래픽을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-122">Select the graphic to be used by the client application to represent the status value in graphical form.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e62db-123">클라이언트 애플리케이션에서 선택한 그래픽을 지원할 수도 있고 적절한 다른 항목으로 대체할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-123">The client application can support the selected graphic or replace it with an appropriate alternative.</span></span>  
  
 <span data-ttu-id="e62db-124">**상태 식**</span><span class="sxs-lookup"><span data-stu-id="e62db-124">**Status expression**</span></span>  
 <span data-ttu-id="e62db-125">KPI 실행 시 KPI의 상태 값을 반환하는 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-125">Type the MDX expression that returns the status value of the KPI when the KPI is run.</span></span>  
  
 <span data-ttu-id="e62db-126">**계산 도구** 창에서 선택한 요소를 이 옵션으로 끌어서 놓으면 선택한 요소의 MDX 구문을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-126">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="e62db-127">이 식은-1과 1 사이의 10 진수를 반환 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-127">It is recommended that this expression returns a decimal number between -1 and 1.</span></span> <span data-ttu-id="e62db-128">값이 작으면 부정적인 추세를 나타내고 값이 크면 긍정적인 추세를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-128">A lower number represents a negative situation, while a higher number represents a positive situation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e62db-129">-1 보다 낮은 값이 가능 하지만 타사 클라이언트 응용 프로그램에서는이 값을 올바르게 해석할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-129">Values below -1 and above 1 are possible but may not be interpreted correctly by third-party client applications.</span></span>  
  
 <span data-ttu-id="e62db-130">**추세**</span><span class="sxs-lookup"><span data-stu-id="e62db-130">**Trend**</span></span>  
 <span data-ttu-id="e62db-131">**추세 그래픽** 및 **추세 식** 옵션을 보려면 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-131">Expand to view the **Trend graphic** and **Trend expression** options.</span></span>  
  
 <span data-ttu-id="e62db-132">**추세 그래픽**</span><span class="sxs-lookup"><span data-stu-id="e62db-132">**Trend graphic**</span></span>  
 <span data-ttu-id="e62db-133">클라이언트 애플리케이션에서 추세 값을 그래픽 형식으로 나타내기 위해 사용할 그래픽을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-133">Select the graphic to be used by the client application to represent the trend value in graphical form.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e62db-134">클라이언트 애플리케이션에서 선택한 그래픽을 지원할 수도 있고 적절한 다른 항목으로 대체할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-134">The client application can support the selected graphic or replace it with an appropriate alternative.</span></span>  
  
 <span data-ttu-id="e62db-135">**추세 식**</span><span class="sxs-lookup"><span data-stu-id="e62db-135">**Trend expression**</span></span>  
 <span data-ttu-id="e62db-136">KPI의 추세 값을 반환하는 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-136">Type the MDX expression that returns the trend value of the KPI.</span></span>  
  
 <span data-ttu-id="e62db-137">**계산 도구** 창에서 선택한 요소를 이 옵션으로 끌어서 놓으면 선택한 요소의 MDX 구문을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-137">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="e62db-138">추세 식은 지정한 비즈니스 컨텍스트에 맞는 모든 시간 기반 조건을 사용하여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-138">The trend expression can be based on any time-based criteria that makes sense in a given business context.</span></span> <span data-ttu-id="e62db-139">이 식은-1과 1 사이의 10 진수를 반환 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-139">It is recommended that this expression returns a decimal number between -1 and 1.</span></span> <span data-ttu-id="e62db-140">값이 작으면 시간에 따른 부정적인 추세를 나타내고 값이 크면 시간에 따른 긍정적인 추세를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-140">A lower number represents a negative trend over time; a higher number represents a positive trend over time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e62db-141">-1 보다 낮은 값이 가능 하지만 타사 클라이언트 응용 프로그램에서는이 값을 올바르게 해석할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-141">Values below -1 and above 1 are possible but may not be interpreted correctly by third-party client applications.</span></span>  
  
 <span data-ttu-id="e62db-142">**추가 속성**</span><span class="sxs-lookup"><span data-stu-id="e62db-142">**Additional Properties**</span></span>  
 <span data-ttu-id="e62db-143">**표시 폴더**, **부모 KPI**, **현재 시간 멤버**, **가중치**및 **설명** 옵션을 보려면 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-143">Expand to view the **Display folder**, **Parent KPI**, **Current time member**, **Weight**, and **Description** options.</span></span>  
  
 <span data-ttu-id="e62db-144">**표시 폴더**</span><span class="sxs-lookup"><span data-stu-id="e62db-144">**Display folder**</span></span>  
 <span data-ttu-id="e62db-145">클라이언트 애플리케이션에서 표시를 위해 사용할 KPI 분류를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-145">Type the categorization of the KPI for use by the client application for display purposes.</span></span>  
  
 <span data-ttu-id="e62db-146">백슬래시(\\)를 사용하여 표시 폴더 내의 폴더 이름을 구분하고 세미콜론(;)을 사용하여 여러 표시 폴더를 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-146">Use a backward slash (\\) to separate folder names in a display folder and a semicolon (;) to separate multiple display folders.</span></span> <span data-ttu-id="e62db-147">예를 들어 `Category\Goal\Scientific;Category\Goal\Metric`을(를) 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-147">For example, type `Category\Goal\Scientific;Category\Goal\Metric`.</span></span>  
  
 <span data-ttu-id="e62db-148">**부모 KPI**</span><span class="sxs-lookup"><span data-stu-id="e62db-148">**Parent KPI**</span></span>  
 <span data-ttu-id="e62db-149">클라이언트 애플리케이션에서 사용할 KPI를 분류할 기존 상위 KPI를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-149">Select an existing KPI under which to categorize the KPI for use by the client application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e62db-150">이 옵션을 기존 KPI로 설정하면 **표시 폴더** 는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-150">If this option is set to an existing KPI, **Display folder** is ignored.</span></span>  
  
 <span data-ttu-id="e62db-151">**현재 시간 멤버**</span><span class="sxs-lookup"><span data-stu-id="e62db-151">**Current time member**</span></span>  
 <span data-ttu-id="e62db-152">KPI의 임시 컨텍스트를 식별하는 멤버를 반환하는 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-152">Type the MDX expression that returns the member that identifies the temporal context of the KPI.</span></span>  
  
 <span data-ttu-id="e62db-153">**계산 도구** 창에서 선택한 요소를 이 옵션으로 끌어서 놓으면 선택한 요소의 MDX 구문을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-153">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e62db-154">MDX 식은 **관련된 측정값 그룹**에서 지정한 측정값 그룹과 관련된 시간 차원 내에서 멤버의 고유 이름을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-154">The MDX expression must return the unique name of a member within a time dimension associated with the measure group specified in **Associated measure group**.</span></span>  
  
 <span data-ttu-id="e62db-155">**Weight**</span><span class="sxs-lookup"><span data-stu-id="e62db-155">**Weight**</span></span>  
 <span data-ttu-id="e62db-156">KPI의 가중 요인에 대한 MDX 식을 보거나 편집하려면 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-156">Expand to view or edit the MDX expression for the weighting factor of the KPI.</span></span>  
  
 <span data-ttu-id="e62db-157">**계산 도구** 창에서 선택한 요소를 이 옵션으로 끌어서 놓으면 선택한 요소의 MDX 구문을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-157">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="e62db-158">**설명**</span><span class="sxs-lookup"><span data-stu-id="e62db-158">**Description**</span></span>  
 <span data-ttu-id="e62db-159">KPI에 대한 선택적 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e62db-159">Type the optional description of the KPI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e62db-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e62db-160">See Also</span></span>  
 [<span data-ttu-id="e62db-161">큐브 디자이너 &#40;Kpi&#41; &#40;Analysis Services-다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="e62db-161">KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](kpis-cube-designer-analysis-services-multidimensional-data.md)  
  
  
