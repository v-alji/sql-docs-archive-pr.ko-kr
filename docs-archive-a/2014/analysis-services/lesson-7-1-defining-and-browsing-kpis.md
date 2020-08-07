---
title: Kpi 정의 및 찾아보기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 648b9a02-1278-4f11-b940-6f0de6a4042d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44febe6c6c5d432f0cdee43e8eaaa3401c54a2c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731040"
---
# <a name="defining-and-browsing-kpis"></a><span data-ttu-id="f5633-102">KPI 정의 및 찾아보기</span><span class="sxs-lookup"><span data-stu-id="f5633-102">Defining and Browsing KPIs</span></span>
  <span data-ttu-id="f5633-103">KPI(핵심 성과 지표)를 정의하려면 먼저 KPI 이름 및 KPI와 연관된 측정값 그룹을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-103">To define key performance indicators (KPIs), you first define a KPI name and the measure group to which the KPI is associated.</span></span> <span data-ttu-id="f5633-104">KPI는 모든 측정값 그룹 또는 단일 측정값 그룹과 연관될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-104">A KPI can be associated with all measure groups or with a single measure group.</span></span> <span data-ttu-id="f5633-105">그런 후 KPI의 다음 요소를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-105">You then define the following elements of the KPI:</span></span>

-   <span data-ttu-id="f5633-106">값 식</span><span class="sxs-lookup"><span data-stu-id="f5633-106">The value expression</span></span>

     <span data-ttu-id="f5633-107">값 식은 매출액과 같은 물리적 측정값, 수익과 같은 계산 측정값 또는 MDX(Multidimensional Expressions) 식을 사용하여 KPI 내에 정의되는 계산입니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-107">A value expression is a physical measure such as Sales, a calculated measure such as Profit, or a calculation that is defined within the KPI by using a Multidimensional Expressions (MDX) expression.</span></span>

-   <span data-ttu-id="f5633-108">목표 식</span><span class="sxs-lookup"><span data-stu-id="f5633-108">The goal expression</span></span>

     <span data-ttu-id="f5633-109">목표 식은 값 식이 정의하는 측정값의 목표를 정의하는 값 또는 값으로 해석되는 MDX 식입니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-109">A goal expression is a value, or an MDX expression that resolves to a value, that defines the target for the measure that the value expression defines.</span></span> <span data-ttu-id="f5633-110">예를 들어 회사의 비즈니스 관리자가 늘리려는 매출액이나 수익 금액이 바로 목표 식이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-110">For example, a goal expression could be the amount by which the business managers of a company want to increase sales or profit.</span></span>

-   <span data-ttu-id="f5633-111">상태 식</span><span class="sxs-lookup"><span data-stu-id="f5633-111">The status expression</span></span>

     <span data-ttu-id="f5633-112">상태 식은 목표 식과 비교하여 값 식의 현재 상태를 평가하기 위해 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 사용하는 MDX 식입니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-112">A status expression is an MDX expression that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to evaluate the current status of the value expression compared to the goal expression.</span></span> <span data-ttu-id="f5633-113">목표 식은 -1과 +1 사이의 정규화된 값으로, 여기에서 -1은 매우 불량, +1은 매우 양호를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-113">A goal expression is a normalized value in the range of -1 to +1, where -1 is very bad, and +1 is very good.</span></span> <span data-ttu-id="f5633-114">상태 식은 목표 식과 비교한 값 식의 상태를 쉽게 판단할 수 있도록 그래픽을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-114">The status expression displays a graphic to help you easily determine the status of the value expression compared to the goal expression.</span></span>

-   <span data-ttu-id="f5633-115">추세 식</span><span class="sxs-lookup"><span data-stu-id="f5633-115">The trend expression</span></span>

     <span data-ttu-id="f5633-116">추세 식은 목표 식과 비교하여 값 식의 현재 추세를 평가하기 위해 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 사용하는 MDX 식입니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-116">A trend expression is an MDX expression that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to evaluate the current trend of the value expression compared to the goal expression.</span></span> <span data-ttu-id="f5633-117">추세 식을 사용하면 비즈니스 사용자는 값 식이 목표 식과 비교하여 더 나아지는지, 아니면 더 나빠지는지를 신속하게 판단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-117">The trend expression helps the business user to quickly determine whether the value expression is becoming better or worse relative to the goal expression.</span></span> <span data-ttu-id="f5633-118">여러 그래픽 중 하나를 추세 식과 연결하여 비즈니스 사용자가 추세를 빠르게 이해하도록 도울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-118">You can associate one of several graphics with the trend expression to help business users be able to quickly understand the trend.</span></span>

 <span data-ttu-id="f5633-119">KPI에 대해 정의한 이러한 요소 외에 KPI의 속성을 추가로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-119">In addition to these elements that you define for a KPI, you also define several properties of a KPI.</span></span> <span data-ttu-id="f5633-120">이러한 속성으로는 표시 폴더, KPI가 다른 KPI로부터 계산될 경우 부모 KPI, 현재 시간 멤버(있는 경우), KPI의 가중치(있는 경우) 및 KPI에 대한 설명이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-120">These properties include a display folder, a parent KPI if the KPI is computed from other KPIs, the current time member if there is one, the weight of the KPI if it has one, and a description of the KPI.</span></span>

> [!NOTE]
>  <span data-ttu-id="f5633-121">KPI의 추가 예는 **Adventure Works DW 2012** DW 샘플 데이터 웨어하우스에 있는 예나 계산 도구 창의 템플릿 탭에 있는 KPI 예를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5633-121">For more examples of KPIs, see the KPI examples on the Templates tab in the Calculation Tools pane or in the examples in the **Adventure Works DW 2012** sample data warehouse.</span></span> <span data-ttu-id="f5633-122">이 데이터베이스를 설치하는 방법에 대한 자세한 내용은 [Analysis Services 다차원 모델링 자습서에 사용할 샘플 데이터 및 프로젝트 설치](install-sample-data-and-projects.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5633-122">For more information about how to install this database, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).</span></span>

 <span data-ttu-id="f5633-123">이 단원의 태스크에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트에 KPI를 정의한 후 이 KPI를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브를 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-123">In the task in this lesson, you define  KPIs in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, and you then browse the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube by using these KPIs.</span></span> <span data-ttu-id="f5633-124">다음과 같은 KPI를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-124">You will define the following KPIs:</span></span>

-   <span data-ttu-id="f5633-125">Reseller Revenue</span><span class="sxs-lookup"><span data-stu-id="f5633-125">Reseller Revenue</span></span>

     <span data-ttu-id="f5633-126">이 KPI는 실제 대리점 판매와 대리점 판매에 대한 판매 할당량을 비교한 결과, 판매액의 목표 근접 수준 및 목표 달성 추세를 측정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-126">This KPI is used to measure how actual reseller sales compare to sales quotas for reseller sales, how close the sales are to the goal, and what the trend is toward reaching the goal.</span></span>

-   <span data-ttu-id="f5633-127">Product Gross Profit Margin</span><span class="sxs-lookup"><span data-stu-id="f5633-127">Product Gross Profit Margin</span></span>

     <span data-ttu-id="f5633-128">이 KPI는 각 제품 범주의 매출이익률이 각 제품 범주의 지정된 목표에 얼마나 근접했는지 확인하고 이러한 목표 달성 추세를 파악하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-128">This KPI is used to determine how close the gross profit margin is for each product category to a specified goal for each product category, and also to determine the trend toward reaching this goal.</span></span>

## <a name="defining-the-reseller-revenue-kpi"></a><span data-ttu-id="f5633-129">Reseller Revenue KPI 정의</span><span class="sxs-lookup"><span data-stu-id="f5633-129">Defining the Reseller Revenue KPI</span></span>

1.  <span data-ttu-id="f5633-130">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 대한 큐브 디자이너를 열고 **KPI** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-130">Open Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **KPIs** tab.</span></span>

     <span data-ttu-id="f5633-131">**KPI** 탭에는 여러 개의 창이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-131">The **KPIs** tab includes several panes.</span></span> <span data-ttu-id="f5633-132">이 탭 왼쪽에는 **KPI 구성 도우미** 창과 **계산 도구** 창이 있고</span><span class="sxs-lookup"><span data-stu-id="f5633-132">On the left side of the tab are the **KPI Organizer** pane and the **Calculation Tools** pane.</span></span> <span data-ttu-id="f5633-133">탭 중간의 표시 창에는 **KPI 구성 도우미** 창에서 선택한 KPI에 대한 세부 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-133">The display pane in the middle of the tab contains the details of the KPI that is selected in the **KPI Organizer** pane.</span></span>

     <span data-ttu-id="f5633-134">다음 그림에서는 큐브 디자이너의 **KPI** 탭을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-134">The following image shows the **KPIs** tab of Cube Designer.</span></span>

     <span data-ttu-id="f5633-135">![큐브 디자이너의 KPI 탭](../../2014/tutorials/media/l7-kpi-1.gif "큐브 디자이너의 KPI 탭")</span><span class="sxs-lookup"><span data-stu-id="f5633-135">![KPIs tab of Cube Designer](../../2014/tutorials/media/l7-kpi-1.gif "KPIs tab of Cube Designer")</span></span>

2.  <span data-ttu-id="f5633-136">**KPI** 탭의 도구 모음에서 **새 KPI** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-136">On the toolbar of the **KPIs** tab, click the **New KPI** button.</span></span>

     <span data-ttu-id="f5633-137">다음 그림에 표시된 것처럼 표시 창에 빈 KPI 템플릿이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-137">A blank KPI template appears in the display pane, as shown in the following image.</span></span>

     <span data-ttu-id="f5633-138">![표시 창의 빈 KPI 템플릿](../../2014/tutorials/media/l7-kpi-2.gif "표시 창의 빈 KPI 템플릿")</span><span class="sxs-lookup"><span data-stu-id="f5633-138">![Blank KPI template in display pane](../../2014/tutorials/media/l7-kpi-2.gif "Blank KPI template in display pane")</span></span>

3.  <span data-ttu-id="f5633-139">**이름** 상자에를 입력 한 `Reseller Revenue` 다음 **관련 된 측정값 그룹** 목록에서 **재판매인 Sales** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-139">In the **Name** box, type `Reseller Revenue`, and then select **Reseller Sales** in the **Associated measure group** list.</span></span>

4.  <span data-ttu-id="f5633-140">**계산 도구** 창의 **메타데이터** 탭에서 **Measures**, **Reseller Sales**를 차례로 확장한 후 **Reseller Sales-Sales Amount** 측정값을 **값 식** 상자로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-140">On the **Metadata** tab in the **Calculation Tools** pane, expand **Measures**, expand **Reseller Sales**, and then drag the **Reseller Sales-Sales Amount** measure to the **Value Expression** box.</span></span>

5.  <span data-ttu-id="f5633-141">**계산 도구** 창의 **메타데이터** 탭에서 **Measures**, **Sales Quotas**를 차례로 확장한 후 **Sales Amount Quota** 측정값을 **목표 식** 상자로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-141">On the **Metadata** tab in the **Calculation Tools** pane, expand **Measures**, expand **Sales Quotas**, and then drag the **Sales Amount Quota** measure to the **Goal Expression** box.</span></span>

6.  <span data-ttu-id="f5633-142">**상태 표시** 목록에서 **계기** 가 선택되어 있는지 확인한 후 **상태 식** 상자에 다음 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-142">Verify that **Gauge** is selected in the **Status indicator** list, and then type the following MDX expression in the **Status expression** box:</span></span>

    ```
    Case
     When 
      KpiValue("Reseller Revenue")/KpiGoal("Reseller Revenue")>=.95
       Then 1
     When
      KpiValue("Reseller Revenue")/KpiGoal("Reseller Revenue")<.95
       And 
      KpiValue("Reseller Revenue")/KpiGoal("Reseller Revenue")>=.85
       Then 0
      Else-1
    End
    ```

     <span data-ttu-id="f5633-143">이 MDX 식은 목표의 진행률 평가를 위한 기본 사항을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-143">This MDX expression provides the basis for evaluating the progress toward the goal.</span></span> <span data-ttu-id="f5633-144">이 MDX 식에서 실제 대리점 판매가 목표액의 85%보다 많으면 선택된 그래픽이 0으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-144">In this MDX expression, if actual reseller sales are more than 85 percent of the goal, a value of 0 is used to populate the chosen graphic.</span></span> <span data-ttu-id="f5633-145">계기는 선택된 그래픽이므로 계기의 포인터는 빈 상태와 꽉 찬 상태의 중간을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-145">Because a gauge is the chosen graphic, the pointer in the gauge will be half-way between empty and full.</span></span> <span data-ttu-id="f5633-146">실제 대리점 판매가 90%보다 많으면 계기의 포인터는 빈 상태와 꽉 찬 상태의 3/4 위치를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-146">If actual reseller sales are more the 90 percent, the pointer on the gauge will be three-fourths of the way between empty and full.</span></span>

7.  <span data-ttu-id="f5633-147">**추세 표시** 목록에서 **일반 화살표** 가 선택되어 있는지 확인한 후 **추세 식** 상자에 다음 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-147">Verify that **Standard arrow** is selected in the **Trend indicator** list, and then type the following expression in the **Trend expression** box:</span></span>

    ```
    Case
     When IsEmpty
      (ParallelPeriod
       ([Date].[Calendar Date].[Calendar Year],1,
           [Date].[Calendar Date].CurrentMember))
      Then 0  
     When  (
      KpiValue("Reseller Revenue") - 
       (KpiValue("Reseller Revenue"), 
        ParallelPeriod
         ([Date].[Calendar Date].[Calendar Year],1,
           [Date].[Calendar Date].CurrentMember))
          /
          (KpiValue ("Reseller Revenue"),
           ParallelPeriod
            ([Date].[Calendar Date].[Calendar Year],1,
             [Date].[Calendar Date].CurrentMember)))
           >=.02
      Then 1
       When(
        KpiValue("Reseller Revenue") - 
         (KpiValue ( "Reseller Revenue" ),
          ParallelPeriod
           ([Date].[Calendar Date].[Calendar Year],1,
            [Date].[Calendar Date].CurrentMember))
           /
            (KpiValue("Reseller Revenue"),
             ParallelPeriod
              ([Date].[Calendar Date].[Calendar Year],1,
                [Date].[Calendar Date].CurrentMember)))
            <=.02
      Then -1
       Else 0
    End
    ```

     <span data-ttu-id="f5633-148">이 MDX 식은 정의한 목표 달성과 관련된 추세 평가를 위한 기본 사항을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-148">This MDX expression provides the basis for evaluating the trend toward achieving the defined goal.</span></span>

## <a name="browsing-the-cube-by-using-the-reseller-revenue-kpi"></a><span data-ttu-id="f5633-149">Reseller Revenue KPI를 사용하여 큐브 찾아보기</span><span class="sxs-lookup"><span data-stu-id="f5633-149">Browsing the Cube by Using the Reseller Revenue KPI</span></span>

1.  <span data-ttu-id="f5633-150">**의** 빌드 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-150">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Service Tutorial**.</span></span>

2.  <span data-ttu-id="f5633-151">배포가 성공적으로 완료되면 **KPI** 탭의 도구 모음에서 **브라우저 보기** 단추를 클릭한 후 **다시 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-151">When deployment has successfully completed, on the toolbar of the **KPIs** tab, click the **Browser View** button, and then click **Reconnect**.</span></span>

     <span data-ttu-id="f5633-152">**KPI 브라우저** 창에는 각 차원의 기본 멤버 값을 기반으로 하는 대리점 판매에 대한 상태 및 추세 계기와 해당 값 및 목표가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-152">The status and trend gauges are displayed in the **KPI Browser** pane for reseller sales based on the values for the default member of each dimension, together with the value for the value and the goal.</span></span> <span data-ttu-id="f5633-153">차원의 다른 어떤 멤버도 기본 멤버로 정의하지 않았으므로 각 차원의 기본 멤버는 All 수준의 All 멤버가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-153">The default member of each dimension is the All member of the All level, because you have not defined any other member of any dimension as the default member.</span></span>

3.  <span data-ttu-id="f5633-154">필터 창의 **차원** 목록에서 **Sales Territory** 를, **계층** 목록에서 **Sales Territories** 를, **연산자** 목록에서 **같음** 을, **필터 식** 목록에서 **North America** 확인란을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-154">In the filter pane, select **Sales Territory** in the **Dimension** list, select **Sales Territories** in the **Hierarchy** list, select **Equal** in the **Operator** list, select the **North America** check box in the **Filter Expression** list, and then click **OK**.</span></span>

4.  <span data-ttu-id="f5633-155">**필터** 창의 다음 행에서는 **차원** 목록에서 **Date** 를, **계층** 목록에서 **Calendar Date** 를, **연산자** 목록에서 **같음** 을, **필터 식** 목록에서 **Q3 CY 2007** 확인란을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-155">In the next row in the **Filter** pane, select **Date** in the **Dimension** list, select **Calendar Date** in the **Hierarchy** list, select **Equal** in the **Operator** list, select the **Q3 CY 2007** check box in the **Filter Expression** list, and then click **OK**.</span></span>

5.  <span data-ttu-id="f5633-156">**KPI 브라우저** 창을 클릭하여 **Reseller Revenue KPI**의 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-156">Click anywhere in the **KPI Browser** pane to update the values for the **Reseller Revenue KPI**.</span></span>

     <span data-ttu-id="f5633-157">KPI의 **값**, **목표**및 **상태** 섹션은 새 기간에 대한 값을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-157">Notice that the **Value**, **Goal**, and **Status** sections of the KPI reflect the values for the new time period</span></span>

## <a name="defining-the-product-gross-profit-margin-kpi"></a><span data-ttu-id="f5633-158">Product Gross Profit Margin KPI 정의</span><span class="sxs-lookup"><span data-stu-id="f5633-158">Defining the Product Gross Profit Margin KPI</span></span>

1.  <span data-ttu-id="f5633-159">**KPI** 탭의 도구 모음에서 **폼 보기** 단추를 클릭한 후 **새 KPI** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-159">Click the **Form View** button on the toolbar of the **KPIs** tab, and then click the **New KPI** button.</span></span>

2.  <span data-ttu-id="f5633-160">**이름** 상자에를 입력 한 `Product Gross Profit Margin` 다음 **\<All>** 관련 된 **측정값 그룹** 목록에가 나타나는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-160">In the **Name** box, type `Product Gross Profit Margin`, and then verify that **\<All>** appears in the **Associated measure group** list.</span></span>

3.  <span data-ttu-id="f5633-161">**계산 도구** 창의 **메타데이터** 탭에서 **Total GPM** 측정값을 **값 식** 상자로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-161">In the **Metadata** tab in the **Calculation Tools** pane, drag the **Total GPM** measure to the **Value Expression** box.</span></span>

4.  <span data-ttu-id="f5633-162">**목표 식** 상자에 다음 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-162">In the **Goal Expression** box, type the following expression:</span></span>

    ```
    Case
        When [Product].[Category].CurrentMember Is
          [Product].[Category].[Accessories]
        Then .40                 
        When [Product].[Category].CurrentMember 
          Is [Product].[Category].[Bikes]
        Then .12                
        When [Product].[Category].CurrentMember Is
          [Product].[Category].[Clothing]
        Then .20
        When [Product].[Category].CurrentMember Is
          [Product].[Category].[Components]
        Then .10
        Else .12            
    End
    ```

5.  <span data-ttu-id="f5633-163">**상태 표시** 목록에서 **실린더**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-163">In the **Status indicator** list, select **Cylinder**.</span></span>

6.  <span data-ttu-id="f5633-164">**상태 식** 상자에 다음 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-164">Type the following MDX expression in the **Status expression** box:</span></span>

    ```
    Case
        When KpiValue( "Product Gross Profit Margin" ) / 
             KpiGoal ( "Product Gross Profit Margin" ) >= .90
        Then 1
        When KpiValue( "Product Gross Profit Margin" ) / 
             KpiGoal ( "Product Gross Profit Margin" ) <  .90
             And 
             KpiValue( "Product Gross Profit Margin" ) / 
             KpiGoal ( "Product Gross Profit Margin" ) >= .80
        Then 0
        Else -1
    End
    ```

     <span data-ttu-id="f5633-165">이 MDX 식은 목표의 진행률 평가를 위한 기본 사항을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-165">This MDX expression provides the basis for evaluating the progress toward the goal.</span></span>

7.  <span data-ttu-id="f5633-166">**추세 표시** 목록에서 **일반 화살표** 가 선택되어 있는지 확인한 후 **추세 식** 상자에 다음 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-166">Verify that **Standard arrow** is selected in the **Trend indicator** list, and then type the following MDX expression in the **Trend expression** box:</span></span>

    ```
    Case
    When IsEmpty
      (ParallelPeriod
       ([Date].[Calendar Date].[Calendar Year],1,
           [Date].[Calendar Date].CurrentMember))
      Then 0  
       When VBA!Abs
        (
          KpiValue( "Product Gross Profit Margin" ) - 
           (
             KpiValue ( "Product Gross Profit Margin" ),
              ParallelPeriod
              ( 
                [Date].[ Calendar Date].[ Calendar Year],
                1,
                [Date].[ Calendar Date].CurrentMember
              )
            ) /
            (
              KpiValue ( "Product Gross Profit Margin" ),
              ParallelPeriod
              ( 
                [Date].[ Calendar Date].[ Calendar Year],
                1,
                [Date].[ Calendar Date].CurrentMember
              )
            )  
          ) <=.02
      Then 0
      When KpiValue( "Product Gross Profit Margin" ) - 
           (
             KpiValue ( "Product Gross Profit Margin" ),
             ParallelPeriod
             ( 
               [Date].[ Calendar Date].[ Calendar Year],
               1,
               [Date].[ Calendar Date].CurrentMember
             )
           ) /
           (
             KpiValue ( "Product Gross Profit Margin" ),
             ParallelPeriod
             ( 
               [Date].[Calendar Date].[Calendar Year],
               1,
               [Date].[Calendar Date].CurrentMember
             )
           )  >.02
      Then 1
      Else -1
    End
    ```

     <span data-ttu-id="f5633-167">이 MDX 식은 정의한 목표 달성과 관련된 추세 평가를 위한 기본 사항을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-167">This MDX expression provides the basis for evaluating the trend toward achieving the defined goal.</span></span>

## <a name="browsing-the-cube-by-using-the-total-gross-profit-margin-kpi"></a><span data-ttu-id="f5633-168">Total Gross Profit Margin KPI를 사용하여 큐브 찾아보기</span><span class="sxs-lookup"><span data-stu-id="f5633-168">Browsing the Cube by Using the Total Gross Profit Margin KPI</span></span>

1.  <span data-ttu-id="f5633-169">**빌드** 메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-169">On the **Build** menu, click **Deploy Analysis Service Tutorial**.</span></span>

2.  <span data-ttu-id="f5633-170">배포가 성공적으로 완료되면 **KPI** 탭의 도구 모음에서 **브라우저 보기** 를 클릭한 후 **다시 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-170">When deployment has successfully completed, click **Reconnect** on the toolbar of the **KPIs** tab, and then click **Browser View**.</span></span>

     <span data-ttu-id="f5633-171">`Product Gross Profit Margin`Kpi가 나타나고 **Q3 CY 2007** 및 **북아메리카** 판매 지역에 대 한 kpi 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-171">The `Product Gross Profit Margin` KPI appears and displays the KPI value for **Q3 CY 2007** and the **North America** sales territory.</span></span>

3.  <span data-ttu-id="f5633-172">**필터** 창의 **차원** 목록에서 **Product** 를, **계층** 목록에서 **Category** 를, **연산자** 목록에서 **같음** 을, **필터 식** 목록에서 **Bikes** 를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-172">In the **Filter** pane, select **Product** in the **Dimension** list, select **Category** in the **Hierarchy** list, select **Equal** in the **Operator** list, and then select **Bikes** in the **Filter Expression** list, and then click **OK**.</span></span>

     <span data-ttu-id="f5633-173">North America의 대리점별로 Q3 CY 2007에 해당하는 Bikes 판매의 매출이익률이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5633-173">The gross profit margin for the sale of Bikes by resellers in North America in Q3 CY 2007 appears.</span></span>

## <a name="next-lesson"></a><span data-ttu-id="f5633-174">다음 단원</span><span class="sxs-lookup"><span data-stu-id="f5633-174">Next Lesson</span></span>
 [<span data-ttu-id="f5633-175">8단원: 작업 정의</span><span class="sxs-lookup"><span data-stu-id="f5633-175">Lesson 8: Defining Actions</span></span>](lesson-8-defining-actions.md)


