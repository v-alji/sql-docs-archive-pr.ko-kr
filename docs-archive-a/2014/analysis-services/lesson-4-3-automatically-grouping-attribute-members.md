---
title: 자동으로 특성 멤버 그룹화 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9fb2cda3-a122-4a4c-82e0-3454865eef04
author: minewiskan
ms.author: owend
ms.openlocfilehash: 820231263362a92584a15556e999d69f286349b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742652"
---
# <a name="automatically-grouping-attribute-members"></a><span data-ttu-id="9b4aa-102">자동으로 특성 멤버 그룹화</span><span class="sxs-lookup"><span data-stu-id="9b4aa-102">Automatically Grouping Attribute Members</span></span>
  <span data-ttu-id="9b4aa-103">큐브를 찾아볼 때 일반적으로 한 특성 계층의 멤버 차원은 다른 특성 계층의 멤버별로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-103">When you browse a cube, you typically dimension the members of one attribute hierarchy by the members of another attribute hierarchy.</span></span> <span data-ttu-id="9b4aa-104">예를 들어 고객 판매를 도시별, 구매 제품별 또는 성별로 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-104">For example, you might group customer sales by city, by product purchased, or by gender.</span></span> <span data-ttu-id="9b4aa-105">그러나 특정 형식의 특성을 사용 하면 특성 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 계층 내에서 멤버의 분포에 따라 특성 멤버 그룹을 자동으로 만드는 것이 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-105">However, with certain types of attributes, it is useful to have [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] automatically create groupings of attribute members based on the distribution of the members within an attribute hierarchy.</span></span> <span data-ttu-id="9b4aa-106">예를 들어 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 고객의 연간 소득 값 그룹을 만들도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-106">For example, you can have [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] create groups of yearly income values for customers.</span></span> <span data-ttu-id="9b4aa-107">이 작업을 수행하면 특성 계층을 찾아보는 사용자는 멤버 자체가 아니라 그룹의 이름과 값을 보게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-107">When you do this, users who browse the attribute hierarchy will see the names and values of the groups instead of the members themselves.</span></span> <span data-ttu-id="9b4aa-108">이렇게 하면 사용자에게 표시되는 수준 수가 제한되므로 분석하는 데 보다 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-108">This limits the number of levels that are presented to users, which can be more useful for analysis.</span></span>

 <span data-ttu-id="9b4aa-109">**DiscretizationMethod** 속성은 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 의 그룹화 생성 여부 및 수행되는 그룹화 유형을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-109">The **DiscretizationMethod** property determines whether [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates groupings, and determines the type of grouping that is performed.</span></span> <span data-ttu-id="9b4aa-110">기본적으로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서는 그룹화를 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-110">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] does not perform any groupings.</span></span> <span data-ttu-id="9b4aa-111">자동 그룹화를 사용하면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 특성 구조에 따라 최적의 그룹화 방법을 자동으로 결정하도록 허용하거나 다음 목록에서 그룹화 알고리즘 중 하나를 선택하여 그룹화 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-111">When you enable automatic groupings, you can allow [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to automatically determine the best grouping method based on the structure of the attribute, or you can choose one of the grouping algorithms in the following list to specify the grouping method:</span></span>

 <span data-ttu-id="9b4aa-112">**EqualAreas** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서는 차원 멤버의 전체 채우기가 그룹 전체에 동일 하 게 분산 되도록 그룹 범위를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-112">**EqualAreas** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates group ranges so that the total population of dimension members is distributed equally across the groups.</span></span>

 <span data-ttu-id="9b4aa-113">**클러스터** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 가우스 분포를 사용 하 여 K-수단 클러스터링 메서드를 사용 하 여 입력 값에 단일 차원 클러스터링을 수행 하는 방식으로 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-113">**Clusters** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates groups by performing single-dimensional clustering on the input values by using the K-Means clustering method with Gaussian distributions.</span></span> <span data-ttu-id="9b4aa-114">이 옵션은 숫자 열에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-114">This option is valid only for numeric columns.</span></span>

 <span data-ttu-id="9b4aa-115">그룹화 방법을 지정한 후에 **DiscretizationBucketCount** 속성을 사용하여 그룹 수를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-115">After you specify a grouping method, you must specify the number of groups, by using the **DiscretizationBucketCount** property.</span></span> <span data-ttu-id="9b4aa-116">자세한 내용은 [특성 멤버 그룹화 &#40;](multidimensional-models/attribute-properties-group-attribute-members.md) 분할을 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="9b4aa-116">For more information, see [Group Attribute Members &#40;Discretization&#41;](multidimensional-models/attribute-properties-group-attribute-members.md)</span></span>

 <span data-ttu-id="9b4aa-117">이 항목의 태스크에서는 **Customer** 차원의 연간 소득 값, **Employees** 차원의 직원 병가 시간 및 **Employees** 차원의 직원 휴가 시간에 대해 서로 다른 유형의 그룹화를 사용하도록 설정한 다음</span><span class="sxs-lookup"><span data-stu-id="9b4aa-117">In the tasks in this topic, you will enable different types of groupings for the following: the yearly income values in the **Customer** dimension; the number of employee sick leave hours in the **Employees** dimension; and the number of employee vacation hours in the **Employees** dimension.</span></span> <span data-ttu-id="9b4aa-118">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브를 처리하고 검색하여 멤버 그룹의 결과를 표시하고,</span><span class="sxs-lookup"><span data-stu-id="9b4aa-118">You will then process and browse the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube to view the effect of the member groups.</span></span> <span data-ttu-id="9b4aa-119">마지막으로 멤버 그룹 속성을 수정하여 그룹화 유형의 변경 결과를 표시하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-119">Finally, you will modify the member group properties to see the effect of the change in grouping type.</span></span>

## <a name="grouping-attribute-hierarchy-members-in-the-customer-dimension"></a><span data-ttu-id="9b4aa-120">Customer 차원의 특성 계층 멤버 그룹화</span><span class="sxs-lookup"><span data-stu-id="9b4aa-120">Grouping Attribute Hierarchy Members in the Customer Dimension</span></span>

1.  <span data-ttu-id="9b4aa-121">솔루션 탐색기의 **차원** 폴더에서 **Customer** 를 두 번 클릭하여 Customer 차원에 대한 차원 디자이너를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-121">In Solution Explorer, double-click **Customer** in the **Dimensions** folder to open Dimension Designer for the Customer dimension.</span></span>

2.  <span data-ttu-id="9b4aa-122">**데이터 원본 뷰** 창에서 **Customer** 테이블을 마우스 오른쪽 단추로 클릭한 다음 **데이터 탐색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-122">In the **Data Source View** pane, right-click the **Customer** table, and then click **Explore Data**.</span></span>

     <span data-ttu-id="9b4aa-123">**YearlyIncome** 열의 값 범위가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-123">Notice the range of values for the **YearlyIncome** column.</span></span> <span data-ttu-id="9b4aa-124">멤버 그룹화를 사용하도록 설정하지 않으면 이러한 값은 **Yearly Income** 특성 계층의 멤버가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-124">These values become the members of the **Yearly Income** attribute hierarchy, unless you enable member grouping.</span></span>

3.  <span data-ttu-id="9b4aa-125">**Customer 테이블 탐색** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-125">Close the **Explore Customer Table** tab.</span></span>

4.  <span data-ttu-id="9b4aa-126">**특성** 창에서 **Yearly Income**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-126">In the **Attributes** pane, select **Yearly Income**.</span></span>

5.  <span data-ttu-id="9b4aa-127">속성 창에서 **DiscretizationMethod** 속성 값을 **Automatic** 으로 변경 하 고 **DiscretizationBucketCount** 속성의 값을로 변경 `5` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-127">In the Properties window, change the value for the **DiscretizationMethod** property to **Automatic** and change the value for the **DiscretizationBucketCount** property to `5`.</span></span>

     <span data-ttu-id="9b4aa-128">다음 그림에서는 **Yearly Income**의 수정된 속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-128">The following image shows the modified properties for **Yearly Income**.</span></span>

     <span data-ttu-id="9b4aa-129">![연간 소득에 대한 수정된 속성](../../2014/tutorials/media/l4-discretizationmethod-1.gif "연간 소득에 대한 수정된 속성")</span><span class="sxs-lookup"><span data-stu-id="9b4aa-129">![Modified properties for Yearly Income](../../2014/tutorials/media/l4-discretizationmethod-1.gif "Modified properties for Yearly Income")</span></span>

## <a name="grouping-attribute-hierarchy-members-in-the-employee-dimension"></a><span data-ttu-id="9b4aa-130">Employee 차원의 특성 계층 멤버 그룹화</span><span class="sxs-lookup"><span data-stu-id="9b4aa-130">Grouping Attribute Hierarchy Members in the Employee Dimension</span></span>

1.  <span data-ttu-id="9b4aa-131">Employee 차원에 대한 차원 디자이너로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-131">Switch to Dimension Designer for the Employee dimension.</span></span>

2.  <span data-ttu-id="9b4aa-132">**데이터 원본 뷰** 창에서 **Employee** 테이블을 마우스 오른쪽 단추로 클릭한 다음 **데이터 탐색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-132">In the **Data Source View** pane, right-click the **Employee** table, and then click **Explore Data**.</span></span>

     <span data-ttu-id="9b4aa-133">**SickLeaveHours** 열 및 **VacationHours** 열의 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-133">Notice the values for the **SickLeaveHours** column and the **VacationHours** column.</span></span>

3.  <span data-ttu-id="9b4aa-134">**Employee 테이블 탐색** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-134">Close the **Explore Employee Table** tab.</span></span>

4.  <span data-ttu-id="9b4aa-135">**특성** 창에서 **Sick Leave Hours**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-135">In the **Attributes** pane, select **Sick Leave Hours**.</span></span>

5.  <span data-ttu-id="9b4aa-136">속성 창에서 **DiscretizationMethod** 속성의 값을 **클러스터** 로 변경 하 고 **DiscretizationBucketCount** 속성의 값을로 변경 `5` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-136">In the Properties window, change the value for the **DiscretizationMethod** property to **Clusters** and change the value for the **DiscretizationBucketCount** property to `5`.</span></span>

6.  <span data-ttu-id="9b4aa-137">**특성** 창에서 **Vacation Hours**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-137">In the **Attributes** pane, select **Vacation Hours**.</span></span>

7.  <span data-ttu-id="9b4aa-138">속성 창에서 **DiscretizationMethod** 속성의 값을 **동일한 영역** 으로 변경 하 고 **DiscretizationBucketCount** 속성의 값을로 변경 `5` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-138">In the Properties window, change the value for the **DiscretizationMethod** property to **Equal Areas** and change the value for the **DiscretizationBucketCount** property to `5`.</span></span>

## <a name="browsing-the-modified-attribute-hierarchies"></a><span data-ttu-id="9b4aa-139">수정된 특성 계층 찾아보기</span><span class="sxs-lookup"><span data-stu-id="9b4aa-139">Browsing the Modified Attribute Hierarchies</span></span>

1.  <span data-ttu-id="9b4aa-140">**의** 빌드 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-140">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="9b4aa-141">배포가 성공적으로 완료되면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 대한 큐브 디자이너로 전환한 후 **브라우저** 탭에서 **다시 연결** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-141">When deployment has successfully completed, switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect** on the **Browser** tab.</span></span>

3.  <span data-ttu-id="9b4aa-142">Excel 아이콘을 클릭한 다음 **사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-142">Click the Excel icon, and then click **Enable**.</span></span>

4.  <span data-ttu-id="9b4aa-143">**Internet Sales-Sales Amount** 측정값을 피벗 테이블 필드 목록의 값 영역으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-143">Drag the **Internet Sales-Sales Amount** measure to the Values area of the PivotTable Field List.</span></span>

5.  <span data-ttu-id="9b4aa-144">필드 목록에서 **Product** 차원을 확장한 다음 **Product Model Lines** 사용자 계층을 필드 목록의 **행 레이블** 영역으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-144">In the field list, expand the **Product** dimension, and then drag the **Product Model Lines** user hierarchy to the **Row Labels** area of the field list.</span></span>

6.  <span data-ttu-id="9b4aa-145">필드 목록에서 **Customer** 차원을 확장하고 **Demographic** 표시 폴더를 확장한 다음 **Yearly Income** 특성 계층을 **열 레이블** 영역으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-145">Expand the **Customer** dimension in the field list, expand the **Demographic** display folder, and then drag the **Yearly Income** attribute hierarchy to the **Column Labels** area.</span></span>

     <span data-ttu-id="9b4aa-146">**Yearly Income** 특성 계층 멤버는 이제 연간 소득을 알 수 없는 고객에 대한 판매 버킷을 포함하여 6개의 버킷으로 그룹화됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-146">The members of the **Yearly Income** attribute hierarchy are now grouped into six buckets, including a bucket for sales to customers whose yearly income is unknown.</span></span> <span data-ttu-id="9b4aa-147">표시되지 않는 버킷도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-147">Not all buckets are displayed.</span></span>

7.  <span data-ttu-id="9b4aa-148">열 영역에서 **Yearly Income** 특성 계층을 제거하고 **값** 영역에서 **Internet Sales-Sales Amount** 측정값을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-148">Remove the **Yearly Income** attribute hierarchy from the columns area and remove the **Internet Sales-Sales Amount** measure from the **Values** area.</span></span>

8.  <span data-ttu-id="9b4aa-149">데이터 영역에 **Reseller Sales-Sales Amount** 측정값을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-149">Add the **Reseller Sales-Sales Amount** measure to the data area.</span></span>

9. <span data-ttu-id="9b4aa-150">필드 목록에서 **Employee** 차원과 **Organization**을 차례로 확장한 후 **Sick Leave Hours** 를 **열 레이블**로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-150">In the field list, expand the **Employee** dimension, expand **Organization**, then drag **Sick Leave Hours** to **Column Labels**.</span></span>

     <span data-ttu-id="9b4aa-151">모든 판매는 두 그룹 중 하나에 속하는 직원에 의해 이루어진 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-151">Notice that all sales are made by employees within one of two groups.</span></span> <span data-ttu-id="9b4aa-152">병가로 32-42시간을 사용한 직원이 병가로 20-31시간을 사용한 직원보다 훨씬 더 많은 판매량을 달성했습니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-152">Notice also that the employees with 32 - 42 sick leave hours made significantly more sales than employees with 20 - 31 sick leave hours.</span></span>

     <span data-ttu-id="9b4aa-153">다음 이미지에서는 직원 병가 시간별로 차원이 구분된 판매량을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-153">The following image shows sales dimensioned by employee sick leave hours.</span></span>

     <span data-ttu-id="9b4aa-154">![직원 병가 시간별로 차원을 구분한 판매량](../../2014/tutorials/media/l4-discretizationmethod-2.gif "직원 병가 시간별로 차원을 구분한 판매량")</span><span class="sxs-lookup"><span data-stu-id="9b4aa-154">![Sales dimensioned by employee sick leave hours](../../2014/tutorials/media/l4-discretizationmethod-2.gif "Sales dimensioned by employee sick leave hours")</span></span>

10. <span data-ttu-id="9b4aa-155">**Sick Leave Hours** 특성 계층을 **데이터** 창의 열 영역에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-155">Remove the **Sick Leave Hours** attribute hierarchy from the column area of the **Data** pane.</span></span>

11. <span data-ttu-id="9b4aa-156">**Vacation Hours** 를 **데이터** 창의 열 영역에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-156">Add **Vacation Hours** to the column area of the **Data** pane.</span></span>

     <span data-ttu-id="9b4aa-157">같은 영역 그룹화 방법이 사용된 두 그룹이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-157">Notice that two groups appear, based on the equal areas grouping method.</span></span> <span data-ttu-id="9b4aa-158">다른 3개의 그룹은 데이터 값이 없으므로 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-158">Three other groups are hidden because they contain no data values.</span></span>

## <a name="modifying-grouping-properties-and-reviewing-the-effect-of-the-changes"></a><span data-ttu-id="9b4aa-159">그룹화 속성 수정 및 변경 결과 검토</span><span class="sxs-lookup"><span data-stu-id="9b4aa-159">Modifying Grouping Properties and Reviewing the Effect of the Changes</span></span>

1.  <span data-ttu-id="9b4aa-160">**Employee** 차원에 대한 차원 디자이너로 전환한 다음 **특성** 창에서 **Vacation Hours** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-160">Switch to Dimension Designer for the **Employee** dimension, and then select **Vacation Hours** in the **Attributes** pane.</span></span>

2.  <span data-ttu-id="9b4aa-161">속성 창에서 **DiscretizationBucketCount** 속성 값을 **10**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-161">In the Properties window, change the value of the **DiscretizationBucketCount** property to **10.**</span></span>

3.  <span data-ttu-id="9b4aa-162">**의** 빌드 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-162">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

4.  <span data-ttu-id="9b4aa-163">배포가 성공적으로 완료되면 다시 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 대한 큐브 디자이너로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-163">When deployment has successfully completed, switch back to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>

5.  <span data-ttu-id="9b4aa-164">**브라우저** 탭에서 **다시 연결** 을 클릭하고 Excel 아이콘을 클릭한 다음 그룹화 방법의 변경 결과를 볼 수 있도록 피벗 테이블을 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-164">Click **Reconnect** on the **Browser** tab, click the Excel icon, and then reconstruct the PivotTable so that you can view the effect of the change to the grouping method:</span></span>

    1.  <span data-ttu-id="9b4aa-165">Reseller Sales-Sales Amount를 값으로 끌기</span><span class="sxs-lookup"><span data-stu-id="9b4aa-165">Drag Reseller Sales-Sales Amount to Values</span></span>

    2.  <span data-ttu-id="9b4aa-166">Employees Organization 폴더의 Vacation Hours를 열로 끌기</span><span class="sxs-lookup"><span data-stu-id="9b4aa-166">Drag Vacation Hours (in the Employees Organization folder) to Columns</span></span>

    3.  <span data-ttu-id="9b4aa-167">Product Model Lines를 행으로 끌기</span><span class="sxs-lookup"><span data-stu-id="9b4aa-167">Drag Product Model Lines to Rows</span></span>

     <span data-ttu-id="9b4aa-168">이제 제품에 대한 판매량 값이 있는 **Vacation Hours** 특성 멤버에는 3개의 그룹이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-168">Notice that there are now three groups of members of the **Vacation Hours** attribute that have sales values for products.</span></span> <span data-ttu-id="9b4aa-169">다른 7개의 그룹에는 판매량 데이터가 없는 멤버가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b4aa-169">(The other seven groups contain members with no sales data.)</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="9b4aa-170">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="9b4aa-170">Next Task in Lesson</span></span>
 [<span data-ttu-id="9b4aa-171">특성 계층 숨기기 및 비활성화</span><span class="sxs-lookup"><span data-stu-id="9b4aa-171">Hiding and Disabling Attribute Hierarchies</span></span>](lesson-4-4-hiding-and-disabling-attribute-hierarchies.md)

## <a name="see-also"></a><span data-ttu-id="9b4aa-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9b4aa-172">See Also</span></span>
 [<span data-ttu-id="9b4aa-173">특성 멤버 그룹화&#40;불연속화&#41;</span><span class="sxs-lookup"><span data-stu-id="9b4aa-173">Group Attribute Members &#40;Discretization&#41;</span></span>](multidimensional-models/attribute-properties-group-attribute-members.md)


