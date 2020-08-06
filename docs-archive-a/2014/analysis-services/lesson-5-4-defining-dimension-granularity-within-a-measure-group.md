---
title: 측정값 그룹 내에서 차원 세분성 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4f079485-9eb4-405c-9a20-81258298b810
author: minewiskan
ms.author: owend
ms.openlocfilehash: dd1119da70631d66debdf79ecf8c911eedd06d44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649801"
---
# <a name="defining-dimension-granularity-within-a-measure-group"></a><span data-ttu-id="7b128-102">측정값 그룹의 차원 세분성 정의</span><span class="sxs-lookup"><span data-stu-id="7b128-102">Defining Dimension Granularity within a Measure Group</span></span>
  <span data-ttu-id="7b128-103">사용자는 다양한 목적에 맞게 팩트 데이터의 차원을 세밀하게 또는 구체적으로 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-103">Users will want to dimension fact data at different granularity or specificity for different purposes.</span></span> <span data-ttu-id="7b128-104">예를 들어 대리점이나 인터넷 판매의 판매 데이터는 매일 기록하고 판매 할당량 정보는 월별 또는 분기별로 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-104">For example, sales data for reseller or internet sales may be recorded for each day, whereas sales quota information may only exist at the month or quarter level.</span></span> <span data-ttu-id="7b128-105">이러한 시나리오에서 사용자는 서로 다른 팩트 테이블 각각에 대해 수준이 다양한 시간 차원을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-105">In these scenarios, users will want a time dimension with a different grain or level of detail for each of these different fact tables.</span></span> <span data-ttu-id="7b128-106">새 데이터베이스 차원을 이러한 다른 수준을 가진 시간 차원으로 정의할 수 있지만 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서는 더 쉬운 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-106">While you could define a new database dimension as a time dimension with this different grain, there is an easier way with [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="7b128-107">기본적으로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 측정값 그룹에 차원을 사용하면 해당 차원의 데이터 수준은 차원의 키 특성을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-107">By default in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], when a dimension is used within a measure group, the grain of the data within that dimension is based on the key attribute of the dimension.</span></span> <span data-ttu-id="7b128-108">예를 들어 시간 차원이 측정값 그룹 내에 포함되어 있고 시간 차원의 기본 수준이 매일이면 측정값 그룹에서 해당 차원의 기본 수준은 매일이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-108">For example, when a time dimension is included within a measure group and the default grain of the time dimension is daily, the default grain of that dimension within the measure group is daily.</span></span> <span data-ttu-id="7b128-109">이 자습서의 **Internet Sales** 및 **Reseller Sales** 측정값 그룹과 같은 많은 경우에 이 수준이 적절하게 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-109">Many times this is appropriate, such as for the **Internet Sales** and **Reseller Sales** measure groups in this tutorial.</span></span> <span data-ttu-id="7b128-110">그러나 차원이 Sales Quotas 또는 Budget 측정값 그룹과 같은 다른 종류의 측정값 그룹에 포함되어 있을 때는 일반적으로 월별 또는 분기별 수준이 보다 적절합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-110">However, when such a dimension is included in other types of measure groups, such as in a sales quota or budget measure group, a monthly or quarterly grain is generally more appropriate.</span></span>  
  
 <span data-ttu-id="7b128-111">큐브 차원에 기본 수준 이외의 수준을 지정하려면 큐브 디자이너의 **차원 용도** 탭에서 특정 측정값 그룹에 사용된 대로 큐브 차원 세분성 특성을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-111">To specify a grain for a cube dimension other than the default grain, you modify the granularity attribute for a cube dimension as used within a particular measure group on the **Dimension Usage** tab of Cube Designer.</span></span> <span data-ttu-id="7b128-112">특정 측정값 그룹 내 차원의 수준을 해당 차원의 키 특성이 아닌 특성으로 변경하면 측정값 그룹의 모든 다른 특성이 직접 또는 간접적으로 새 세분성 특성에 관련되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-112">When you change the grain of a dimension within a specific measure group to an attribute other than the key attribute for that dimension, you must guarantee that all other attributes in the measure group are directly or indirectly related to new granularity attribute.</span></span> <span data-ttu-id="7b128-113">다른 모든 특성과 측정값 그룹의 세분성 특성으로 지정된 특성 간 특성 관계를 지정하여 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-113">You do this by specifying attribute relationships between all other attributes and the attribute that is specified as the granularity attribute in the measure group.</span></span> <span data-ttu-id="7b128-114">이 경우에는 특성 관계를 이동하는 대신에 추가 특성 관계를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-114">In this case, you define additional attribute relationships rather than move attribute relationships.</span></span> <span data-ttu-id="7b128-115">세분성 특성으로 지정된 특성이 차원의 나머지 특성을 위해 측정값 그룹에서 사실상 키 특성이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-115">The attribute that is specified as the granularity attribute effectively becomes the key attribute within the measure group for the remaining attributes in the dimension.</span></span> <span data-ttu-id="7b128-116">특성 관계를 적절하게 지정하지 않으면 이 항목의 태스크에서 설명된 대로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서는 값을 제대로 집계할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-116">If you do not specify attribute relationships appropriately, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] will not be able to aggregate values correctly, as you will see in the tasks in this topic.</span></span>  
  
 <span data-ttu-id="7b128-117">자세한 내용은 [차원 관계](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), [일반 관계 및 일반 관계 속성 정의](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7b128-117">For more information, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), [Define a Regular Relationship and Regular Relationship Properties](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md).</span></span>  
  
 <span data-ttu-id="7b128-118">이 항목의 태스크에서는 Sales Quotas 측정값 그룹을 추가하고 이 측정값 그룹의 Date 차원 세분성이 월별이 되도록 정의한 다음</span><span class="sxs-lookup"><span data-stu-id="7b128-118">In the tasks in this topic, you add a Sales Quotas measure group and define the granularity of the Date dimension in this measure group to be monthly.</span></span> <span data-ttu-id="7b128-119">월 특성과 다른 차원 특성 간 특성 관계를 정의하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 값을 제대로 집계하도록 하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-119">You then define attribute relationships between the month attribute and other dimension attributes to ensure that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] aggregates values correctly.</span></span>  
  
## <a name="adding-tables-and-defining-the-sales-quotas-measure-group"></a><span data-ttu-id="7b128-120">테이블 추가 및 Sales Quotas 측정값 그룹 정의</span><span class="sxs-lookup"><span data-stu-id="7b128-120">Adding Tables and Defining the Sales Quotas Measure Group</span></span>  
  
1.  <span data-ttu-id="7b128-121">**Adventure Works DW 2012** 데이터 원본 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-121">Switch to the **Adventure Works DW 2012** data source view.</span></span>  
  
2.  <span data-ttu-id="7b128-122">**다이어그램 구성 도우미** 창에서 아무 곳 이나 마우스 오른쪽 단추로 클릭 하 고 **새 다이어그램**을 클릭 한 다음 다이어그램의 이름을로 지정한 다음 `Sales Quotas`</span><span class="sxs-lookup"><span data-stu-id="7b128-122">Right-click anywhere in the **Diagram Organizer** pane, click **New Diagram**, and then name the diagram `Sales Quotas`.</span></span>  
  
3.  <span data-ttu-id="7b128-123">**직원**, **영업 지역**및 `Date` 테이블을 **테이블** 창에서 **다이어그램** 창으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-123">Drag the **Employee**, **Sales Territory**, and `Date` tables from the **Tables** pane to the **Diagram** pane.</span></span>  
  
4.  <span data-ttu-id="7b128-124">**다이어그램** 창을 마우스 오른쪽 단추로 클릭하고 **테이블 추가/제거** 를 선택하여 **FactSalesQuota** 테이블을 **다이어그램**창에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-124">Add the **FactSalesQuota** table to the **Diagram** pane by right-clicking anywhere in the **Diagram** pane and selecting **Add/Remove Tables**.</span></span>  
  
     <span data-ttu-id="7b128-125">**SalesTerritory** 테이블은 **Employee** 테이블을 통해 **FactSalesQuota** 테이블에 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-125">Notice that the **SalesTerritory** table is linked to the **FactSalesQuota** table through the **Employee** table.</span></span>  
  
5.  <span data-ttu-id="7b128-126">**FactSalesQuota** 테이블의 열을 검토한 다음 이 테이블의 데이터를 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-126">Review the columns in the **FactSalesQuota** table and then explore the data in this table.</span></span>  
  
     <span data-ttu-id="7b128-127">이 테이블의 데이터 수준은 FactSalesQuota 테이블의 최하위 수준인 분기입니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-127">Notice that the grain of the data within this table is the calendar quarter, which is the lowest level of detail in the FactSalesQuota table.</span></span>  
  
6.  <span data-ttu-id="7b128-128">데이터 원본 뷰 디자이너에서 **FactSalesQuota** 테이블의 **FriendlyName** 속성을로 변경 합니다 `SalesQuotas` .</span><span class="sxs-lookup"><span data-stu-id="7b128-128">In Data Source View Designer, change the **FriendlyName** property of the **FactSalesQuota** table to `SalesQuotas`.</span></span>  
  
7.  <span data-ttu-id="7b128-129">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브로 전환한 다음 **큐브 구조** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-129">Switch to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Cube Structure** tab.</span></span>  
  
8.  <span data-ttu-id="7b128-130">**측정값** 창의 아무 곳 이나 마우스 오른쪽 단추로 클릭 하 고 **새 측정값 그룹**을 클릭 한 `SalesQuotas` 다음 **새 측정값 그룹** 대화 상자를 클릭 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-130">Right-click anywhere in the **Measures** pane, click **New Measure Group**, click `SalesQuotas` in the **New Measure Group** dialog box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="7b128-131">측정값 `Sales Quotas` 그룹이 **측정값** 창에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-131">The `Sales Quotas` measure group appears in the **Measures** pane.</span></span> <span data-ttu-id="7b128-132">**차원** 창에는 `Date` 데이터베이스 차원을 기반으로 새 큐브 차원도 정의 되어 있습니다 `Date` .</span><span class="sxs-lookup"><span data-stu-id="7b128-132">In the **Dimensions** pane, notice that a new `Date` cube dimension is also defined, based on the `Date` database dimension.</span></span> <span data-ttu-id="7b128-133">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서는 Sales Quotas 측정값 그룹의 기반이 되는 **FactSalesQuota** 팩트 테이블의 **DateKey** 열과 관련된 기존 시간 관련 큐브 차원을 인식하지 못하므로 새 시간 관련 큐브 차원이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-133">A new time-related cube dimension is defined because [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] does not know which of the existing time-related cube dimensions to relate to the **DateKey** column in the **FactSalesQuota** fact table that underlies the Sales Quotas measure group.</span></span> <span data-ttu-id="7b128-134">이 항목의 다른 태스크에서 이 큐브 차원을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-134">You will change this later in another task in this topic.</span></span>  
  
9. <span data-ttu-id="7b128-135">`Sales Quotas`측정값 그룹을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-135">Expand the `Sales Quotas` measure group.</span></span>  
  
10. <span data-ttu-id="7b128-136">**측정값** 창에서 **Sales Amount Quota**를 선택한 다음 속성 창에서 **FormatString** 속성 값을 **Currency** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-136">In the **Measures** pane, select **Sales Amount Quota**, and then set the value for the **FormatString** property to **Currency** in the Properties window.</span></span>  
  
11. <span data-ttu-id="7b128-137">**Sales 할당량 Count** 측정값을 선택한 다음 `#,#` 속성 창의 **FormatString** 속성 값으로을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-137">Select the **Sales Quotas Count** measure, and then type `#,#` as the value for the **FormatString** property in the Properties window.</span></span>  
  
12. <span data-ttu-id="7b128-138">측정값 그룹에서 **Calendar Quarter** 측정값을 삭제 `Sales Quotas` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-138">Delete the **Calendar Quarter** measure from the `Sales Quotas` measure group.</span></span>  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="7b128-139">에서는 Calendar Quarter 측정값의 기반이 되는 열을 측정값이 포함된 열로 감지합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-139">detected the column that underlies the Calendar Quarter measure as a column that contains measures.</span></span> <span data-ttu-id="7b128-140">그러나 이 열과 CalendarYear 열은 이 항목의 뒷부분에서 Sales Quotas 측정값 그룹을 Date 차원에 연결하는 데 사용할 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-140">However, this column and the CalendarYear column contain the values that you will use to link the Sales Quotas measure group to the Date dimension later in this topic.</span></span>  
  
13. <span data-ttu-id="7b128-141">**측정값** 창에서 측정값 그룹을 마우스 오른쪽 단추로 클릭 한 `Sales Quotas` 다음 **새 측정값**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-141">In the **Measures** pane, right-click the `Sales Quotas` measure group, and then click **New Measure**.</span></span>  
  
     <span data-ttu-id="7b128-142">**합계** 사용 유형을 사용하는 측정값에 사용 가능한 원본 열이 포함되어 있는 **새 측정값**대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-142">The **New Measure** dialog box opens, containing the available source columns for a measure with a usage type of **Sum**.</span></span>  
  
14. <span data-ttu-id="7b128-143">**새 측정값** 대화 상자의 **사용법** 목록에서 **고유 카운트** 를 선택 하 고 `SalesQuotas` **원본 테이블** 목록에서가 선택 되어 있는지 확인 한 다음 **원본 열** 목록에서 **EmployeeKey** 를 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-143">In the **New Measure** dialog box, select **Distinct count** in the **Usage** list, verify that `SalesQuotas` is selected in the **Source table** list, select **EmployeeKey** in the **Source column** list, and then click **OK**.</span></span>  
  
     <span data-ttu-id="7b128-144">**Sales Quotas 1**이라는 새 측정값 그룹에 측정값이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-144">Notice that the measure is created in a new measure group named **Sales Quotas 1**.</span></span> <span data-ttu-id="7b128-145">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 고유 카운트 측정값이 자체 측정값 그룹에 생성되므로 처리 성능을 극대화합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-145">Distinct count measures in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] are created in their own measure groups to maximize processing performance.</span></span>  
  
15. <span data-ttu-id="7b128-146">**Employee Key Distinct Count** 측정값의 **Name** 속성 값을로 변경 하 `Sales Person Count` 고 `#,#` **FormatString** 속성 값으로을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-146">Change the value for the **Name** property for the **Employee Key Distinct Count** measure to `Sales Person Count`, and then type `#,#` as the value for the **FormatString** property.</span></span>  
  
## <a name="browsing-the-measures-in-the-sales-quota-measure-group-by-date"></a><span data-ttu-id="7b128-147">Sales Quota 측정값 그룹에서 날짜별로 측정값 찾아보기</span><span class="sxs-lookup"><span data-stu-id="7b128-147">Browsing the Measures in the Sales Quota Measure Group by Date</span></span>  
  
1.  <span data-ttu-id="7b128-148">**빌드** 메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-148">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="7b128-149">배포가 성공적으로 완료되면 **Tutorial 큐브에 대한 큐브 디자이너에서** 브라우저 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 탭을 클릭한 다음 **다시 연결** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-149">When deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>  
  
3.  <span data-ttu-id="7b128-150">Excel 바로 가기를 클릭한 다음 **사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-150">Click the Excel shortcut, and then click **Enable**.</span></span>  
  
4.  <span data-ttu-id="7b128-151">피벗 테이블 필드 목록에서 `Sales Quotas` 측정값 그룹을 확장 한 다음 **Sales Amount Quota** 측정값을 값 영역으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-151">In the PivotTable Field List, expand the `Sales Quotas` measure group, and then drag the **Sales Amount Quota** measure to the Values area.</span></span>  
  
5.  <span data-ttu-id="7b128-152">**Sales Territory** 차원을 확장한 다음 **Sales Territories** 사용자 정의 계층을 행 레이블로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-152">Expand the **Sales Territory** dimension, and then drag the **Sales Territories** user-defined hierarchy to Row Labels.</span></span>  
  
     <span data-ttu-id="7b128-153">다음 이미지에서와 같이 Sales Territory 큐브 차원은 Fact Sales Quota 테이블에 직접 또는 간접적으로 관련되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-153">Notice that the Sales Territory cube dimension is not related, directly or indirectly, to the Fact Sales Quota table, as shown in the following image.</span></span>  
  
     <span data-ttu-id="7b128-154">![영업 지역 큐브 차원](../../2014/tutorials/media/l5-granularity-2.gif "Sales Territory 큐브 차원")</span><span class="sxs-lookup"><span data-stu-id="7b128-154">![Sales Territory cube dimension](../../2014/tutorials/media/l5-granularity-2.gif "Sales Territory cube dimension")</span></span>  
  
     <span data-ttu-id="7b128-155">이 항목의 다음과 같은 일련의 단계에서는 이 차원과 이 팩트 테이블 간 참조 차원 관계를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-155">In the next series of steps in this topic you will define a reference dimension relationship between this dimension and this fact table.</span></span>  
  
6.  <span data-ttu-id="7b128-156">**Sales Territories** 사용자 계층을 행 레이블 영역에서 열 레이블 영역으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-156">Move the **Sales Territories** user hierarchy from the Rows Labels area to the Column Labels area.</span></span>  
  
7.  <span data-ttu-id="7b128-157">피벗 테이블 필드 목록에서 **Sales Territories** 사용자 정의 계층을 선택한 다음 오른쪽의 아래쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-157">In the PivotTable Field list, select the **Sales Territories** user-defined hierarchy, and then click the down arrow to the right.</span></span>  
  
     <span data-ttu-id="7b128-158">![필드 목록의 Sales Territories 계층](../../2014/tutorials/media/l5-granularity-1a.png "필드 목록의 Sales Territories 계층")</span><span class="sxs-lookup"><span data-stu-id="7b128-158">![Sales Territories hierarchy in the field list](../../2014/tutorials/media/l5-granularity-1a.png "Sales Territories hierarchy in the field list")</span></span>  
  
8.  <span data-ttu-id="7b128-159">필터에서 모두 선택 확인란을 클릭하여 모든 선택 항목의 선택을 취소한 다음 **North America**만 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-159">In the filter, click the Select All checkbox to clear all the selections, and then choose just **North America**.</span></span>  
  
     <span data-ttu-id="7b128-160">![North America 선택을 위한 필터 창](../../2014/tutorials/media/l5-granularity-1b.png "North America 선택을 위한 필터 창")</span><span class="sxs-lookup"><span data-stu-id="7b128-160">![Filter pane for selecting North America](../../2014/tutorials/media/l5-granularity-1b.png "Filter pane for selecting North America")</span></span>  
  
9. <span data-ttu-id="7b128-161">피벗 테이블 필드 목록에서를 확장 `Date` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-161">In the PivotTable Field List, expand `Date`.</span></span>  
  
10. <span data-ttu-id="7b128-162">**Date.Fiscal Date** 사용자 계층을 행 레이블로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-162">Drag the **Date.Fiscal Date** user hierarchy to Row Labels</span></span>  
  
11. <span data-ttu-id="7b128-163">피벗 테이블에서 행 레이블 옆에 있는 아래쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-163">On the PivotTable, click the down arrow next to Row Labels.</span></span> <span data-ttu-id="7b128-164">**FY 2008**을 제외한 모든 연도를 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-164">Clear all of the years except for **FY 2008**.</span></span>  
  
     <span data-ttu-id="7b128-165">월 수준의 월 2007 년 7 월, **2007**, **2007**및 **2007 9** 월 멤버 대신 **월 수준의** **7 월** 멤버만 표시 되 고,이 경우에 **Month** 는 31 일이 아니라 해당 수준의 **7 월 2007 1** 일 멤버만 `Date` 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-165">Notice that only the **July 2007** member of the **Month** level appears, instead of the **July, 2007**, **August, 2007**, and **September, 2007** members of **Month** level, and that only the **July 1, 2007** member of the `Date` level appears, instead of all 31 days.</span></span> <span data-ttu-id="7b128-166">이 동작은 팩트 테이블의 데이터 수준이 분기이 고 차원의 수준이 매일 이기 때문에 발생 합니다 `Date` .</span><span class="sxs-lookup"><span data-stu-id="7b128-166">This behavior occurs because the grain of the data in the fact table is at the quarter level and the grain of the `Date` dimension is the daily level.</span></span> <span data-ttu-id="7b128-167">이 항목의 다음 태스크에서는 이 동작을 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-167">You will change this behavior in the next task in this topic.</span></span>  
  
     <span data-ttu-id="7b128-168">월 및 일 수준의 **Sales Amount Quota** 값도 분기 수준의 값과 같은 $13,733,000.00가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-168">Notice also that the **Sales Amount Quota** value for the month and day levels is the same value as for the quarter level, $13,733,000.00.</span></span> <span data-ttu-id="7b128-169">Sales Quotas 측정값 그룹의 데이터 최하위 수준이 분기 수준이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-169">This is because the lowest level of data in the Sales Quotas measure group is at the quarter level.</span></span> <span data-ttu-id="7b128-170">6단원에서는 이 동작을 변경하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-170">You will change this behavior in Lesson 6.</span></span>  
  
     <span data-ttu-id="7b128-171">다음 그림에서는 **Sales Amount Quota**의 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-171">The following image shows the values for **Sales Amount Quota**.</span></span>  
  
     <span data-ttu-id="7b128-172">![Sales Amount Quota 값](../../2014/tutorials/media/l5-granularity-3.png "Sales Amount Quota 값")</span><span class="sxs-lookup"><span data-stu-id="7b128-172">![Values for Sales Amount Quota](../../2014/tutorials/media/l5-granularity-3.png "Values for Sales Amount Quota")</span></span>  
  
## <a name="defining-dimension-usage-properties-for-the-sales-quotas-measure-group"></a><span data-ttu-id="7b128-173">Sales Quotas 측정값 그룹의 차원 용도 속성 정의</span><span class="sxs-lookup"><span data-stu-id="7b128-173">Defining Dimension Usage Properties for the Sales Quotas Measure Group</span></span>  
  
1.  <span data-ttu-id="7b128-174">**Employee** 차원에 대한 차원 디자이너를 열고 **데이터 원본 뷰** 창에서 **SalesTerritoryKey** 를 마우스 오른쪽 단추로 클릭한 다음 **열의 새 특성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-174">Open Dimension Designer for the **Employee** dimension, right-click **SalesTerritoryKey** in the **Data Source View** pane, and then click **New Attribute from Column**.</span></span>  
  
2.  <span data-ttu-id="7b128-175">**특성** 창에서 **SalesTerritoryKey**를 선택한 후 속성 창에서 **AttributeHierarchyVisible** 속성을 **False** 로, **AttributeHierarchyOptimizedState** 속성을 **NotOptimized**로, **AttributeHierarchyOrdered** 속성을 **False**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-175">In the **Attributes** pane, select **SalesTerritoryKey**, and then set the **AttributeHierarchyVisible** property to **False** in the Properties window, set the **AttributeHierarchyOptimizedState** property to **NotOptimized**, and set the **AttributeHierarchyOrdered** property to **False**.</span></span>  
  
     <span data-ttu-id="7b128-176">이 특성은 **Sales 지역** 차원을 `Sales Quotas` 및 **sales 할당량 1** 측정값 그룹에 참조 차원으로 연결 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-176">This attribute is required to link the **Sales Territory** dimension to the `Sales Quotas` and **Sales Quotas 1** measure groups as a referenced dimension.</span></span>  
  
3.  <span data-ttu-id="7b128-177">Tutorial 큐브에 대 한 큐브 디자이너에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **차원 용도** 탭을 클릭 한 다음 `Sales Quotas` 및 **Sales 할당량 1** 측정값 그룹 내의 차원 용도를 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-177">In Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, click the **Dimension Usage** tab, and then review the dimension usage within the `Sales Quotas` and **Sales Quotas 1** measure groups.</span></span>  
  
     <span data-ttu-id="7b128-178">**직원** 및 `Date` 큐브 차원은 일반 관계를 통해 **sales Quotasand sales 할당량 1** 측정값 그룹에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-178">Notice that the **Employee** and `Date` cube dimensions are linked to the **Sales Quotasand Sales Quotas 1** measure groups through regular relationships.</span></span> <span data-ttu-id="7b128-179">**Sales Territory** 큐브 차원은 이러한 측정값 그룹에 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-179">Notice also that the **Sales Territory** cube dimension is not linked to either of these measure groups.</span></span>  
  
4.  <span data-ttu-id="7b128-180">**Sales 영토** 차원과 측정값 그룹의 교집합에서 셀을 클릭 한 `Sales Quotas` 다음 찾아보기 단추 (**...**)를 클릭 합니다. **관계 정의** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-180">Click the cell at the intersection of the **Sales Territory** dimension and the `Sales Quotas` measure group and then click the browse button (**...**). The **Define Relationship** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="7b128-181">**관계 유형 선택** 목록에서 **참조**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-181">In the **Select relationship type** list, select **Referenced**.</span></span>  
  
6.  <span data-ttu-id="7b128-182">**중간 차원** 목록에서 **Employee**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-182">In the **Intermediate dimension** list, select **Employee**.</span></span>  
  
7.  <span data-ttu-id="7b128-183">**참조 차원 특성** 목록에서 **Sales Territory Region**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-183">In the **Reference dimension attribute** list, select **Sales Territory Region.**</span></span>  
  
8.  <span data-ttu-id="7b128-184">**중간 차원 특성** 목록에서 **Sales Territory Key**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-184">In the **Intermediate dimension attribute** list, select **Sales Territory Key**.</span></span> <span data-ttu-id="7b128-185">Sales Territory Region 특성의 키 열은 SalesTerritoryKey 열입니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-185">(The key column for the Sales Territory Region attribute is the SalesTerritoryKey column.)</span></span>  
  
9. <span data-ttu-id="7b128-186">**구체화** 확인란이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-186">Verify that the **Materialize** check box is selected.</span></span>  
  
10. <span data-ttu-id="7b128-187">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-187">Click **OK**.</span></span>  
  
11. <span data-ttu-id="7b128-188">**Sales 영토** 차원과 **sales 할당량 1** 측정값 그룹의 교집합에서 셀을 클릭 한 다음 찾아보기 단추 (**...**)를 클릭 합니다. **관계 정의** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-188">Click the cell at the intersection of the **Sales Territory** dimension and the **Sales Quotas 1** measure group and then click the browse button (**...**). The **Define Relationship** dialog box opens.</span></span>  
  
12. <span data-ttu-id="7b128-189">**관계 유형 선택** 목록에서 **참조**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-189">In the **Select relationship type** list, select **Referenced**.</span></span>  
  
13. <span data-ttu-id="7b128-190">**중간 차원** 목록에서 **Employee**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-190">In the **Intermediate dimension** list, select **Employee**.</span></span>  
  
14. <span data-ttu-id="7b128-191">**참조 차원 특성** 목록에서 **Sales Territory Region**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-191">In the **Reference dimension attribute** list, select **Sales Territory Region.**</span></span>  
  
15. <span data-ttu-id="7b128-192">**중간 차원 특성** 목록에서 **Sales Territory Key**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-192">In the **Intermediate dimension attribute** list, select **Sales Territory Key**.</span></span> <span data-ttu-id="7b128-193">Sales Territory Region 특성의 키 열은 SalesTerritoryKey 열입니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-193">(The key column for the Sales Territory Region attribute is the SalesTerritoryKey column.)</span></span>  
  
16. <span data-ttu-id="7b128-194">**구체화** 확인란이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-194">Verify that the **Materialize** check box is selected.</span></span>  
  
17. <span data-ttu-id="7b128-195">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-195">Click **OK**.</span></span>  
  
18. <span data-ttu-id="7b128-196">`Date`큐브 차원을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-196">Delete the `Date` cube dimension.</span></span>  
  
     <span data-ttu-id="7b128-197">4 개의 시간 관련 큐브 차원이 아니라 측정값 그룹의 **Order date** 큐브 차원을 차원에 `Sales Quotas` 대 한 기준으로 사용할 날짜로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-197">Instead of having four time-related cube dimensions, you will use the **Order Date** cube dimension in the `Sales Quotas` measure group as the date against which sales quotas will be dimensioned.</span></span> <span data-ttu-id="7b128-198">또한 이 큐브 차원을 큐브의 주 날짜 차원으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-198">You will also use this cube dimension as the primary date dimension in the cube.</span></span>  
  
19. <span data-ttu-id="7b128-199">**차원** 목록에서 **Order Date** 큐브 차원의 이름을으로 바꿉니다 `Date` .</span><span class="sxs-lookup"><span data-stu-id="7b128-199">In the **Dimensions** list, rename the **Order Date** cube dimension to `Date`.</span></span>  
  
     <span data-ttu-id="7b128-200">**Order Date** 큐브 차원의 이름을로 바꾸면 `Date` 사용자가 해당 역할을이 큐브의 주 날짜 차원으로 쉽게 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-200">Renaming the **Order Date** cube dimension to `Date` makes it easier for users to understand its role as the primary date dimension in this cube.</span></span>  
  
20. <span data-ttu-id="7b128-201">**...** `Sales Quotas` 측정값 그룹과 차원의 교집합에 있는 셀에서 찾아보기 단추 (...)를 클릭 합니다. `Date`</span><span class="sxs-lookup"><span data-stu-id="7b128-201">Click the browse button (**...**) in the cell at the intersection of the `Sales Quotas` measure group and the `Date` dimension.</span></span>  
  
21. <span data-ttu-id="7b128-202">**관계 정의** 대화 상자의 **관계 유형 선택** 목록에서 **일반** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-202">In the **Define Relationship** dialog box, select **Regular** in the **Select relationship type** list.</span></span>  
  
22. <span data-ttu-id="7b128-203">**세분성 특성** 목록에서 **Calendar Quarter**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-203">In the **Granularity attribute** list, select **Calendar Quarter**.</span></span>  
  
     <span data-ttu-id="7b128-204">세분성 특성으로 키가 아닌 특성을 선택했으므로 모든 다른 특성을 멤버 속성으로 지정하여 해당 특성이 직접 또는 간접적으로 세분성 특성에 관련되도록 해야 함을 알리는 경고가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-204">Notice that a warning appears to notify you that because you have selected a non-key attribute as the granularity attribute, you must make sure that all other attributes are directly or indirectly related to the granularity attribute by specifying them as member properties.</span></span>  
  
23. <span data-ttu-id="7b128-205">**관계 정의** 대화 상자의 **관계** 영역에서 Date 큐브 차원의 기반이 되는 테이블의 **CalendarYear** 및 **CalendarQuarter** 차원 열을 Sales Quota 측정값 그룹의 기반이 되는 테이블의 **CalendarYear** 및 **CalendarQuarter** 열에 연결한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-205">In the **Relationship** area of the **Define Relationship** dialog box, link the **CalendarYear** and **CalendarQuarter** dimension columns from the table that underlies the Date cube dimension to the **CalendarYear** and **CalendarQuarter** columns in the table that underlies the Sales Quota measure group, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7b128-206">Sales Quotas 측정값 그룹의 Date 큐브 차원에 대한 세분성 특성은 Calendar Quarter로 정의되지만 Internet Sales 및 Reseller Sales 측정값 그룹의 세분성 특성에는 Date 특성이 계속 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-206">The Calendar Quarter is defined as the granularity attribute for the Date cube dimension in the Sales Quotas measure group, but the Date attribute continues to be the granularity attribute for the Internet Sales and Reseller Sales measure groups.</span></span>  
  
24. <span data-ttu-id="7b128-207">**Sales Quotas 1** 측정값 그룹에 대해 이전 네 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-207">Repeat the previous four steps for the **Sales Quotas 1** measure group.</span></span>  
  
## <a name="defining-attribute-relationships-between-the-calendar-quarter-attribute-and-the-other-dimension-attributes-in-the-date-dimension"></a><span data-ttu-id="7b128-208">Date 차원의 Calendar Quarter 특성과 다른 차원 특성 간의 특성 관계 정의</span><span class="sxs-lookup"><span data-stu-id="7b128-208">Defining Attribute Relationships Between the Calendar Quarter Attribute and the Other Dimension Attributes in the Date Dimension</span></span>  
  
1.  <span data-ttu-id="7b128-209">차원에 대 한 **차원 디자이너** 로 전환한 `Date` 다음 **특성 관계** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-209">Switch to **Dimension Designer** for the `Date` dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
     <span data-ttu-id="7b128-210">Calendar **Year** 는 calendar **반기** 특성을 통해 calendar **Quarter** 에 연결 되지만 회계 달력 특성은 서로만 연결 됩니다. **Calendar Quarter** 특성에 연결 되지 않으므로 측정값 그룹에서 제대로 집계 되지 않습니다 `Sales Quotas` .</span><span class="sxs-lookup"><span data-stu-id="7b128-210">Notice that although **Calendar Year** is linked to **Calendar Quarter** through the **Calendar Semester** attribute, the fiscal calendar attributes are linked only to one another; they are not linked to the **Calendar Quarter** attribute and therefore will not aggregate correctly in the `Sales Quotas` measure group.</span></span>  
  
2.  <span data-ttu-id="7b128-211">다이어그램에서 **Calendar Quarter** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-211">In the diagram, right-click the **Calendar Quarter** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="7b128-212">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **Calendar Quarter**입니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-212">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Quarter**.</span></span> <span data-ttu-id="7b128-213">**관련 특성** 을 **Fiscal Quarter**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-213">Set the **Related Attribute** to **Fiscal Quarter**.</span></span>  
  
4.  <span data-ttu-id="7b128-214">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-214">Click **OK**.</span></span>  
  
     <span data-ttu-id="7b128-215">`Date`키가 아닌 특성이 세분성 특성으로 사용 될 경우 데이터가 집계 되지 않을 수 있는 하나 이상의 중복 특성 관계가 차원에 포함 되어 있음을 나타내는 경고 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-215">Notice that a warning message appears stating that the `Date` dimension contains one or more redundant attribute relationships that may prevent data from being aggregated when a non-key attribute is used as a granularity attribute.</span></span>  
  
5.  <span data-ttu-id="7b128-216">**Month Name** 특성과 **Fiscal Quarter** 특성 간의 특성 관계를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-216">Delete the attribute relationship between the **Month Name** attribute and the **Fiscal Quarter** attribute.</span></span>  
  
6.  <span data-ttu-id="7b128-217">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-217">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="browsing-the-measures-in-the-sales-quota-measure-group-by-date"></a><span data-ttu-id="7b128-218">Sales Quota 측정값 그룹에서 날짜별로 측정값 찾아보기</span><span class="sxs-lookup"><span data-stu-id="7b128-218">Browsing the Measures in the Sales Quota Measure Group by Date</span></span>  
  
1.  <span data-ttu-id="7b128-219">**빌드** 메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-219">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="7b128-220">배포가 성공적으로 완료되면 **Tutorial 큐브에 대한 큐브 디자이너에서** 브라우저 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 탭을 클릭한 다음 **다시 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-220">When deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect**.</span></span>  
  
3.  <span data-ttu-id="7b128-221">Excel 바로 가기를 클릭한 다음 **사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-221">Click the Excel shortcut, and then click **Enable**.</span></span>  
  
4.  <span data-ttu-id="7b128-222">**Sales Amount Quota** 측정값을 값 영역으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-222">Drag the **Sales Amount Quota** measure to the Values area.</span></span>  
  
5.  <span data-ttu-id="7b128-223">**Sales Territories** 사용자 계층을 열 레이블로 끌어온 다음 **North America**를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-223">Drag the **Sales Territories** user hierarchy to the Column Labels, and then filter on **North America**.</span></span>  
  
6.  <span data-ttu-id="7b128-224">**Date.FiscalDate** 사용자 계층을 행 레이블로 끌어간 다음 피벗 테이블에서 **행 레이블** 옆의 아래쪽 화살표를 클릭하고 **FY 2008**을 제외한 모든 확인란의 선택을 취소하여 2008 회계 연도만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-224">Drag the **Date.FiscalDate** user hierarchy to the Row Labels, and then click the down arrow next to **Row Labels** on the PivotTable, and clear all check boxes other than **FY 2008**, to display only fiscal year 2008.</span></span>  
  
7.  <span data-ttu-id="7b128-225">확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-225">Click OK.</span></span>  
  
8.  <span data-ttu-id="7b128-226">**FY 2008**, **H1 FY 2008**, **Q1 FY 2008**을 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-226">Expand **FY 2008**, expand **H1 FY 2008**, and then expand **Q1 FY 2008**.</span></span>  
  
     <span data-ttu-id="7b128-227">다음 그림에서는 Sales Quota 측정값 그룹의 차원이 올바르게 구분되어 있는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 대한 피벗 테이블을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-227">The following image shows a PivotTable for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, with the Sales Quota measure group dimensioned correctly.</span></span>  
  
     <span data-ttu-id="7b128-228">회계 분기 수준의 각 멤버 값이 분기 수준 값과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-228">Notice that each member of the fiscal quarter level has the same value as the quarter level.</span></span> <span data-ttu-id="7b128-229">**Q1 FY 2008** 을 예로 사용하면 **Q1 FY 2008** 의 할당량인 $9,180,000.00가 각 해당 멤버의 값이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-229">Using **Q1 FY 2008** as an example, the quota of $9,180,000.00 for **Q1 FY 2008** is also the value for each of its members.</span></span> <span data-ttu-id="7b128-230">이 동작은 팩트 테이블의 데이터 수준이 분기이고 Date 차원의 수준도 분기이기 때문에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-230">This behavior occurs because the grain of the data in the fact table is at the quarter level and the grain of the Date dimension is also at the quarter level.</span></span> <span data-ttu-id="7b128-231">6단원에서는 분기별 판매량을 각 월에 비례하게 할당하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7b128-231">In Lesson 6, you will learn how to allocate the quarterly amount proportionally to each month.</span></span>  
  
     <span data-ttu-id="7b128-232">![올바르게 차원이 지정된 Sales Quota 측정값 그룹](../../2014/tutorials/media/l5-granularity-7.gif "올바르게 차원이 지정된 Sales Quota 측정값 그룹")</span><span class="sxs-lookup"><span data-stu-id="7b128-232">![Sales Quota measure group dimensioned correctly](../../2014/tutorials/media/l5-granularity-7.gif "Sales Quota measure group dimensioned correctly")</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="7b128-233">다음 단원</span><span class="sxs-lookup"><span data-stu-id="7b128-233">Next Lesson</span></span>  
 [<span data-ttu-id="7b128-234">6단원: 계산 정의</span><span class="sxs-lookup"><span data-stu-id="7b128-234">Lesson 6: Defining Calculations</span></span>](lesson-6-defining-calculations.md)  
  
## <a name="see-also"></a><span data-ttu-id="7b128-235">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7b128-235">See Also</span></span>  
 <span data-ttu-id="7b128-236">[차원 관계](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span><span class="sxs-lookup"><span data-stu-id="7b128-236">[Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span></span>  
 <span data-ttu-id="7b128-237">[일반 관계 및 일반 관계 속성 정의](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md) </span><span class="sxs-lookup"><span data-stu-id="7b128-237">[Define a Regular Relationship and Regular Relationship Properties](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md) </span></span>  
 [<span data-ttu-id="7b128-238">데이터 원본 뷰 디자이너에서의 다이어그램 작업&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7b128-238">Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;</span></span>](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  
