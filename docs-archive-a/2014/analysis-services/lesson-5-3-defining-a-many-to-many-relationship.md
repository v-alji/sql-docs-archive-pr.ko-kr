---
title: 다 대 다 관계 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7bebb174-148c-4cbb-a285-2f6d536a16d5
author: minewiskan
ms.author: owend
ms.openlocfilehash: fb4e18831ae23b8cf1f0702b357672f7520478a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731071"
---
# <a name="defining-a-many-to-many-relationship"></a><span data-ttu-id="23696-102">다 대 다 관계 정의</span><span class="sxs-lookup"><span data-stu-id="23696-102">Defining a Many-to-Many Relationship</span></span>
  <span data-ttu-id="23696-103">차원을 정의할 경우 일반적으로 각 팩트는 하나의 차원 멤버에만 조인되지만 단일 차원 멤버는 여러 팩트와 연결될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23696-103">When you define a dimension, typically each fact joins to one and only one dimension member, whereas a single dimension member can be associated with many different facts.</span></span> <span data-ttu-id="23696-104">예를 들어 각 고객은 여러 개의 주문을 가질 수 있지만 각 주문은 단일 컴퓨터에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-104">For example, each customer can have many orders but each order belongs to a single customer.</span></span> <span data-ttu-id="23696-105">관계형 데이터베이스 용어에서이 *관계를 일 대 다 관계*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-105">In relational database terminology, this is referred to as a *one-to-many relationship*.</span></span> <span data-ttu-id="23696-106">그러나 단일 팩트가 여러 차원 멤버에 조인될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23696-106">However, sometimes a single fact can join to multiple dimension members.</span></span> <span data-ttu-id="23696-107">관계형 데이터베이스 용어에서 이 관계를 *다 대 다 관계*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-107">In relational database terminology, this is referred to as a *many-to-many relationship*.</span></span> <span data-ttu-id="23696-108">예를 들어 고객이 구매하는 데는 여러 이유가 있고 구매 이유는 여러 구매와 연결될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23696-108">For example, a customer may have multiple reasons for making a purchase, and a purchase reason can be associated with multiple purchases.</span></span> <span data-ttu-id="23696-109">조인 테이블을 사용하여 각 구매와 관련된 판매 이유를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-109">A join table is used to define the sales reasons that relate to each purchase.</span></span> <span data-ttu-id="23696-110">그러므로 이러한 관계에서 생성된 Sales Reason 차원에는 단일 판매 트랜잭션과 관련된 여러 멤버가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="23696-110">A Sales Reason dimension constructed from such relationships would then have multiple members that relate to a single sales transaction.</span></span> <span data-ttu-id="23696-111">다 대 다 차원은 차원 모델을 표준 별모양 스키마 이상으로 확장하고 차원이 팩트 테이블에 직접 관련되지 않는 경우 복잡한 분석을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-111">Many-to-many dimensions expand the dimensional model beyond the classic star schema and support complex analytics when dimensions are not directly related to a fact table.</span></span>

 <span data-ttu-id="23696-112">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서는 차원 테이블에 조인할 중간 팩트 테이블을 지정하여 차원과 측정값 그룹의 다 대 다 관계를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-112">In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], you define a many-to-many relationship between a dimension and a measure group by specifying an intermediate fact table that is joined to the dimension table.</span></span> <span data-ttu-id="23696-113">이에 따라 중간 팩트 테이블은 팩트 테이블이 조인되는 중간 차원 테이블에 조인됩니다.</span><span class="sxs-lookup"><span data-stu-id="23696-113">An intermediate fact table is joined, in turn, to an intermediate dimension table to which the fact table is joined.</span></span> <span data-ttu-id="23696-114">중간 팩트 테이블과 관계의 차원 테이블 및 중간 차원 모두 간의 다 대 다 관계는 주 차원 멤버와 관계에 의해 지정된 측정값 그룹의 측정값 간에 다 대 다 관계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="23696-114">The many-to-many relationships between the intermediate fact table and both the dimension tables in the relationship and the intermediate dimension creates the many-to-many relationships between members of the primary dimension and measures in the measure group that is specified by the relationship.</span></span> <span data-ttu-id="23696-115">중간 측정값 그룹을 통해 차원 및 측정값 그룹 간에 다 대 다 관계를 정의하려면 중간 측정값 그룹이 하나 이상의 차원을 원래의 측정값 그룹과 공유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-115">In order to define a many-to-many relationship between a dimension and a measure group through an intermediate measure group, the intermediate measure group must share one or more dimensions with the original measure group.</span></span>

 <span data-ttu-id="23696-116">다 대 다 차원이 사용되면 값의 합계가 고유하게 계산됩니다. 이는 All 멤버에 대해 값이 두 번 이상 집계되지 않는다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-116">With a many-to-many dimension, values are distinct summed, which means that they do not aggregate more than once to the All member.</span></span>

> [!NOTE]
>  <span data-ttu-id="23696-117">다 대 다 차원 관계를 지원 하려면 데이터 원본 뷰에서 관련 된 모든 테이블 간에 기본 키-외래 키 관계를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-117">In order to support a many-to-many dimension relationship, a primary key-foreign key relationship must be defined in the data source view between all the tables that are involved.</span></span> <span data-ttu-id="23696-118">정의하지 않으면 큐브 디자이너의 **차원 용도** 탭에서 관계를 설정할 때 올바른 중간 측정값 그룹을 선택할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23696-118">Otherwise, you will not be able to select the correct intermediate measure group when you establish the relationship in the **Dimension Usage** tab of Cube Designer.</span></span>

 <span data-ttu-id="23696-119">자세한 내용은 [차원 관계](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)와 [다 대 다 관계 및 다 대 다 관계 속성 정의](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23696-119">For more information, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), and [Define a Many-to-Many Relationship and Many-to-Many Relationship Properties](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md).</span></span>

 <span data-ttu-id="23696-120">이 항목의 태스크에서는 Sales Reasons 차원과 Sales Reasons 측정값 그룹을 정의하고 Sales Reasons 측정값 그룹을 통해 Sales Reasons 차원과 Internet Sales 측정값 그룹 간에 다 대 다 관계를 정의하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-120">In the tasks in this topic, you define the Sales Reasons dimension and the Sales Reasons measure group, and you define a many-to-many relationship between the Sales Reasons dimension and the Internet Sales measure group through the Sales Reasons measure group.</span></span>

## <a name="adding-required-tables-to-the-data-source-view"></a><span data-ttu-id="23696-121">데이터 원본 뷰에 필수 테이블 추가</span><span class="sxs-lookup"><span data-stu-id="23696-121">Adding Required Tables to the Data Source View</span></span>

1.  <span data-ttu-id="23696-122">**Adventure Works DW 2012** 데이터 원본 뷰에 대한 데이터 원본 뷰 디자이너를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="23696-122">Open Data Source View Designer for the **Adventure Works DW 2012** data source view.</span></span>

2.  <span data-ttu-id="23696-123">**다이어그램 구성 도우미** 창에서 아무 곳 이나 마우스 오른쪽 단추로 클릭 하 고 **새 다이어그램**을 클릭 한 다음 `Internet Sales Order Reasons` 새 다이어그램의 이름으로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-123">Right-click anywhere in the **Diagram Organizer** pane, click **New Diagram**, and specify `Internet Sales Order Reasons` as the name for this new diagram.</span></span>

3.  <span data-ttu-id="23696-124">**테이블** 창에서 **InternetSales** 테이블을 **다이어그램** 창으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="23696-124">Drag the **InternetSales** table to the **Diagram** pane from the **Tables** pane.</span></span>

4.  <span data-ttu-id="23696-125">**다이어그램** 창을 마우스 오른쪽 단추로 클릭한 다음 **테이블 추가/제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-125">Right-click anywhere in the **Diagram** pane, and then click **Add/Remove Tables**.</span></span>

5.  <span data-ttu-id="23696-126">**테이블 추가/제거** 대화 상자에서 **DimSalesReason** 테이블과 **FactInternetSalesReason** 테이블을 **포함된 개체** 목록에 추가한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-126">In the **Add/Remove Tables** dialog box, add the **DimSalesReason** table and the **FactInternetSalesReason** table to the **Included objects** list, and then click **OK**.</span></span>

     <span data-ttu-id="23696-127">관련 된 테이블 간의 기본 키-외래 키 관계가 기본 관계형 데이터베이스에 정의 되어 있으므로 해당 관계가 자동으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23696-127">Notice that the primary key-foreign key relationships between the tables that are involved are established automatically because those relationships are defined in the underlying relational database.</span></span> <span data-ttu-id="23696-128">이러한 관계가 기본 관계형 데이터베이스에 정의되어 있지 않으면 해당 관계를 데이터 원본 뷰에서 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-128">If these relationships were not defined in the underlying relational database, you would have to define them in the data source view.</span></span>

6.  <span data-ttu-id="23696-129">**서식** 메뉴에서 **자동 레이아웃**을 가리킨 다음 **다이어그램**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-129">On the **Format** menu, point to **Auto Layout**, and then click **Diagram**.</span></span>

7.  <span data-ttu-id="23696-130">속성 창에서 **Dimsalesreason** 테이블의 **friendlyname** 속성을로 변경 하 `SalesReason` 고 **FactInternetSalesReason** 테이블의 **friendlyname** 속성을로 변경 합니다 `InternetSalesReason` .</span><span class="sxs-lookup"><span data-stu-id="23696-130">In the Properties window, change the **FriendlyName** property of the **DimSalesReason** table to `SalesReason`, and then change the **FriendlyName** property of the **FactInternetSalesReason** table to `InternetSalesReason`.</span></span>

8.  <span data-ttu-id="23696-131">**테이블** 창에서 **InternetSalesReason(dbo.FactInternetSalesReason)** 을 확장하고 **SalesOrderNumber**를 클릭한 다음 속성 창에서 이 데이터 열의 **DataType** 속성을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-131">In the **Tables** pane, expand **InternetSalesReason (dbo.FactInternetSalesReason)**, click **SalesOrderNumber**, and then review the **DataType** property for this data column in the Properties window.</span></span>

     <span data-ttu-id="23696-132">**SalesOrderNumber** 열의 데이터 형식은 문자열 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="23696-132">Notice that the data type for the **SalesOrderNumber** column is a string data type.</span></span>

9. <span data-ttu-id="23696-133">테이블의 다른 열에 대 한 데이터 형식을 검토 `InternetSalesReason` 합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-133">Review the data types for the other columns in the `InternetSalesReason` table.</span></span>

     <span data-ttu-id="23696-134">이 테이블의 다른 두 개의 열에 대한 데이터 형식은 숫자 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="23696-134">Notice that the data types for the other two columns in this table are numeric data types.</span></span>

10. <span data-ttu-id="23696-135">**테이블** 창에서 **InternetSalesReason(dbo.FactInternetSalesReason)** 을 마우스 오른쪽 단추로 클릭한 다음 **데이터 탐색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-135">In the **Tables** pane, right-click **InternetSalesReason (dbo.FactInternetSalesReason)**, and then click **Explore Data**.</span></span>

     <span data-ttu-id="23696-136">다음 이미지에서와 같이 각 주문에서 각 줄 번호의 키 값은 해당 줄 항목의 구매에 대한 판매 이유를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-136">Notice that, for each line number within each order, a key value identifies the sales reason for the purchase of that line item, as shown in the following image.</span></span>

     <span data-ttu-id="23696-137">![구매에 대한 판매 이유를 식별하기 위한 키 값](../../2014/tutorials/media/l5-many-to-many-1.gif "구매에 대한 판매 이유를 식별하기 위한 키 값")</span><span class="sxs-lookup"><span data-stu-id="23696-137">![Key value to identify sales reason for purchases](../../2014/tutorials/media/l5-many-to-many-1.gif "Key value to identify sales reason for purchases")</span></span>

## <a name="defining-the-intermediate-measure-group"></a><span data-ttu-id="23696-138">중간 측정값 그룹 정의</span><span class="sxs-lookup"><span data-stu-id="23696-138">Defining the Intermediate Measure Group</span></span>

1.  <span data-ttu-id="23696-139">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 대한 큐브 디자이너로 전환한 다음 **큐브 구조** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-139">Switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Cube Structure** tab.</span></span>

2.  <span data-ttu-id="23696-140">**측정값** 창을 마우스 오른쪽 단추로 클릭한 다음 **새 측정값 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-140">Right-click anywhere in the **Measures** pane, and then click **New Measure Group**.</span></span> <span data-ttu-id="23696-141">자세한 내용은 [다차원 모델의 측정값 및 측정값 그룹 만들기](multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23696-141">For more information, see [Create Measures and Measure Groups in Multidimensional Models](multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md).</span></span>

3.  <span data-ttu-id="23696-142">**새 측정값 그룹** 대화 상자의 `InternetSalesReason` **데이터 원본 뷰에서 테이블 선택** 목록에서를 선택한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-142">In the **New Measure Group** dialog box, select `InternetSalesReason` in the **Select a table from the data source view** list, and then click **OK**.</span></span>

     <span data-ttu-id="23696-143">이제 **Internet Sales Reason** 측정값 그룹이 **측정값** 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="23696-143">Notice that the **Internet Sales Reason** measure group now appears in the **Measures** pane.</span></span>

4.  <span data-ttu-id="23696-144">**Internet Sales Reason** 측정값 그룹을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-144">Expand the **Internet Sales Reason** measure group.</span></span>

     <span data-ttu-id="23696-145">이 새 측정값 그룹에는 단일 측정값 **Internet Sales Reason Count** 만 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23696-145">Notice that only a single measure is defined for this new measure group, the **Internet Sales Reason Count** measure.</span></span>

5.  <span data-ttu-id="23696-146">**Internet Sales Reason Count** 를 선택하고 속성 창에서 이 측정값의 속성을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-146">Select **Internet Sales Reason Count** and review the properties of this measure in the Properties window.</span></span>

     <span data-ttu-id="23696-147">이 측정값의 **AggregateFunction** 속성은 **Sum** 이 아니라 **Count**로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="23696-147">Notice that the **AggregateFunction** property for this measure is defined as **Count** instead of **Sum**.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]<span data-ttu-id="23696-148">기본 데이터 형식이 문자열 데이터 형식 이므로 **Count** 를 선택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="23696-148">chose **Count** because the underlying data type is a string data type.</span></span> <span data-ttu-id="23696-149">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서는 기본 팩트 테이블의 다른 두 열을 실제 측정값이 아니라 숫자 키로 검색하므로 해당 열은 측정값으로 선택되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23696-149">The other two columns in the underlying fact table were not selected as measures because [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] detected them as numeric keys instead of as actual measures.</span></span> <span data-ttu-id="23696-150">자세한 내용은 [반가산적 동작 정의](multidimensional-models/define-semiadditive-behavior.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23696-150">For more information, see [Define Semiadditive Behavior](multidimensional-models/define-semiadditive-behavior.md).</span></span>

6.  <span data-ttu-id="23696-151">속성 창에서 **Internet Sales Reason Count** 측정값의 **Visible** 속성을 **False**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-151">In the Properties window, change the **Visible** property of the **Internet Sales Reason Count** measure to **False**.</span></span>

     <span data-ttu-id="23696-152">이 측정값은 Internet Sales 측정값 그룹 다음에 정의할 Sales Reason 차원을 조인하는 데만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="23696-152">This measure will only be used to join the Sales Reason dimension that you will define next to the Internet Sales measure group.</span></span> <span data-ttu-id="23696-153">사용자가 이 측정값을 직접 찾아보지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23696-153">Users will not browse this measure directly.</span></span>

     <span data-ttu-id="23696-154">다음 그림에서는 **Internet Sales Reason Count** 측정값의 속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="23696-154">The following image shows the properties for the **Internet Sales Reason Count** measure.</span></span>

     <span data-ttu-id="23696-155">![Internet Sales Reason Count 측정값 속성](../../2014/tutorials/media/l5-many-to-many-2.gif "Internet Sales Reason Count 측정값 속성")</span><span class="sxs-lookup"><span data-stu-id="23696-155">![Properties for Internet Sales Reason Count measure](../../2014/tutorials/media/l5-many-to-many-2.gif "Properties for Internet Sales Reason Count measure")</span></span>

## <a name="defining-the-many-to-many-dimension"></a><span data-ttu-id="23696-156">다 대 다 차원 정의</span><span class="sxs-lookup"><span data-stu-id="23696-156">Defining the Many-to-Many Dimension</span></span>

1.  <span data-ttu-id="23696-157">솔루션 탐색기에서 **차원**을 마우스 오른쪽 단추로 클릭한 다음 **새 차원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-157">In Solution Explorer, right-click **Dimensions**, and then click **New Dimension**.</span></span>

2.  <span data-ttu-id="23696-158">**차원 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-158">On the **Welcome to the Dimension Wizard** page, click **Next**.</span></span>

3.  <span data-ttu-id="23696-159">**생성 방법 선택** 페이지에서 **기존 테이블 사용** 옵션이 선택되어 있는지 확인하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-159">On the **Select Creation Method** page, verify that the **Use an existing table** option is selected, and then click **Next**.</span></span>

4.  <span data-ttu-id="23696-160">**원본 정보 지정** 페이지에서 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012 데이터 원본 뷰가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-160">On the **Specify Source Information** page, verify that the [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012 data source view is selected.</span></span>

5.  <span data-ttu-id="23696-161">**주 테이블** 목록에서을 선택 `SalesReason` 합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-161">In the **Main table** list, select `SalesReason`.</span></span>

6.  <span data-ttu-id="23696-162">**키 열** 목록에 **SalesReasonKey** 가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-162">In the **Key columns** list, verify that **SalesReasonKey** is listed.</span></span>

7.  <span data-ttu-id="23696-163">**이름 열** 목록에서 **SalesReasonName**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-163">In the **Name column** list, select **SalesReasonName**.</span></span>

8.  <span data-ttu-id="23696-164">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-164">Click **Next**.</span></span>

9. <span data-ttu-id="23696-165">**차원 특성 선택** 페이지에서 키 특성인 **Sales Reason Key** 특성이 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="23696-165">On the **Select Dimension Attributes** page, the **Sales Reason Key** attribute is automatically selected because it is the key attribute.</span></span> <span data-ttu-id="23696-166">**Sales Reason Reason Type** 특성 옆에 있는 확인란을 선택 하 고 이름을로 변경한 `Sales Reason Type` 후 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-166">Select the check box beside the **Sales Reason Reason Type** attribute, change its name to `Sales Reason Type`, and then click **Next**.</span></span>

10. <span data-ttu-id="23696-167">**마법사 완료** 페이지에서 **마침** 을 클릭하여 Sales Reason 차원을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="23696-167">On the **Completing the Wizard** page, click **Finish** to create the Sales Reason dimension.</span></span>

11. <span data-ttu-id="23696-168">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-168">On the **File** menu, click **Save All**.</span></span>

12. <span data-ttu-id="23696-169">**Sales reason** 차원에 대 한 차원 디자이너의 **특성** 창에서 **sales reason Key**를 선택한 다음 속성 창의 **이름** 속성을로 변경 합니다.`Sales Reason.`</span><span class="sxs-lookup"><span data-stu-id="23696-169">In the **Attributes** pane of the Dimension Designer for the **Sales Reason** dimension, select **Sales Reason Key**, and then change the **Name** property in the Properties window to `Sales Reason.`</span></span>

13. <span data-ttu-id="23696-170">차원 디자이너의 **계층** 창에서 **Sales Reasons** `Sales Reason Type` 수준 및 **sales Reason** 수준을 해당 순서로 포함 하는 sales Reason 사용자 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="23696-170">In the **Hierarchies** pane of the Dimension Designer, create a **Sales Reasons** user hierarchy that contains the `Sales Reason Type` level and the **Sales Reason** level, in that order.</span></span>

14. <span data-ttu-id="23696-171">속성 창에서 `All Sales Reasons` Sales 이유가 계층의 **AllMemberName** 속성에 대 한 값으로를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-171">In the Properties window, define `All Sales Reasons` as the value for the **AllMemberName** property of the Sales Reasons hierarchy.</span></span>

15. <span data-ttu-id="23696-172">`All Sales Reasons`Sales Reason 차원의 **AttributeAllMemberName** 속성에 대 한 값으로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-172">Define `All Sales Reasons` as the value for **AttributeAllMemberName** property of the Sales Reason dimension.</span></span>

16. <span data-ttu-id="23696-173">새로 만들어진 차원을 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 큐브 차원으로 추가하려면 **큐브 디자이너**로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-173">To add the newly created dimension to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube as a cube dimension, switch to **Cube Designer**.</span></span> <span data-ttu-id="23696-174">**큐브 구조** 탭에서 **차원** 창을 마우스 오른쪽 단추로 클릭하고 **큐브 차원 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-174">On the **Cube Structure** tab, right-click in the **Dimensions** pane and select **Add Cube Dimension**.</span></span>

17. <span data-ttu-id="23696-175">**큐브 차원 추가** 대화 상자에서 **Sales Reason** 을 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-175">In the **Add Cube Dimension** dialog box, select **Sales Reason** and then click **OK**.</span></span>

18. <span data-ttu-id="23696-176">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-176">On the **File** menu, click **Save All**.</span></span>

## <a name="defining-the-many-to-many-relationship"></a><span data-ttu-id="23696-177">다 대 다 관계 정의</span><span class="sxs-lookup"><span data-stu-id="23696-177">Defining the Many to Many Relationship</span></span>

1.  <span data-ttu-id="23696-178">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 대한 큐브 디자이너로 전환한 다음 **차원 용도** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-178">Switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Dimension Usage** tab.</span></span>

     <span data-ttu-id="23696-179">**Sales Reason** 차원은 **Internet Sales Reason** 측정값 그룹과 일반 관계가 정의되어 있지만 **Internet Sales** 또는 **Reseller Sales** 측정값 그룹과는 관계가 정의되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23696-179">Notice that the **Sales Reason** dimension has a regular relationship defined with the **Internet Sales Reason** measure group, but has no relationship defined with the **Internet Sales** or **Reseller Sales** measure groups.</span></span> <span data-ttu-id="23696-180">또한 **Internet Sales Order Details** 차원은 **Internet Sales** 측정값 그룹과 **Fact Relationship** 관계가 정의되어 있는 **Internet Sales Reason** 차원과 일반 관계가 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23696-180">Notice also that the **Internet Sales Order Details** dimension has a regular relationship defined with the **Internet Sales Reason** dimension, which in turn has a **Fact Relationship** with the **Internet Sales** measure group.</span></span> <span data-ttu-id="23696-181">이 차원이 없거나 **Internet Sales Reason** 및 **Internet Sales** 측정값 그룹과 관계가 정의된 다른 차원이 없을 경우 다 대 다 관계를 정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23696-181">If this dimension was not present (or another dimension with a relationship with both the **Internet Sales Reason** and the **Internet Sales** measure group were not present), you would not be able to define the many-to-many relationship.</span></span>

2.  <span data-ttu-id="23696-182">**Internet Sales** 측정값 그룹과 **Sales Reason** 차원의 교집합에 있는 셀을 클릭한 다음 찾아보기 단추(**...**)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-182">Click the cell at the intersection of the **Internet Sales** measure group and the **Sales Reason** dimension and then click the browse button (**...**).</span></span>

3.  <span data-ttu-id="23696-183">**관계 정의** 대화 상자의 **관계 유형 선택** 목록에서 **다 대 다** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-183">In the **Define Relationship** dialog box, select **Many-to-Many** in the **Select relationship type** list.</span></span>

     <span data-ttu-id="23696-184">Sales Reason 차원을 Internet Sales 측정값 그룹에 연결하는 중간 측정값 그룹을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-184">You have to define the intermediate measure group that connects the Sales Reason dimension to the Internet Sales measure group.</span></span>

4.  <span data-ttu-id="23696-185">**중간 측정값 그룹** 목록에서 **Internet Sales Reason**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-185">In the **Intermediate measure group** list, select **Internet Sales Reason**.</span></span>

     <span data-ttu-id="23696-186">다음 그림에서는 **관계 정의** 대화 상자의 변경 내용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="23696-186">The following image shows the changes in the **Define Relationship** dialog box.</span></span>

     <span data-ttu-id="23696-187">![관계 정의 대화 상자](../../2014/tutorials/media/l5-many-to-many-3.gif "관계 정의 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="23696-187">![Define Relationship dialog box](../../2014/tutorials/media/l5-many-to-many-3.gif "Define Relationship dialog box")</span></span>

5.  <span data-ttu-id="23696-188">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-188">Click **OK**.</span></span>

     <span data-ttu-id="23696-189">Sales Reason 차원과 Internet Sales 측정값 그룹 간의 관계를 나타내는 다 대 다 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="23696-189">Notice the many-to-many icon that represents the relationship between the Sales Reason dimension and the Internet Sales measure group.</span></span>

## <a name="browsing-the-cube-and-the-many-to-many-dimension"></a><span data-ttu-id="23696-190">큐브 및 다 대 다 차원 찾아보기</span><span class="sxs-lookup"><span data-stu-id="23696-190">Browsing the Cube and the Many-to-Many Dimension</span></span>

1.  <span data-ttu-id="23696-191">**빌드** 메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-191">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="23696-192">배포가 성공적으로 완료되면 **Tutorial 큐브에 대한 큐브 디자이너에서** 브라우저 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 탭으로 전환한 다음 **다시 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-192">When deployment has successfully completed, switch to the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect**.</span></span>

3.  <span data-ttu-id="23696-193">데이터 창의 데이터 영역에 **Internet Sales-Sales Amount** 측정값을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-193">Add the **Internet Sales-Sales Amount** measure to the data area of the data pane.</span></span>

4.  <span data-ttu-id="23696-194">**Sales Reason** 차원의 **Sales Reasons** 사용자 정의 계층을 데이터 창의 행 영역에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-194">Add the **Sales Reasons** user-defined hierarchy from the **Sales Reason** dimension to the row area of the data pane.</span></span>

5.  <span data-ttu-id="23696-195">메타데이터 창에서 **Customer**, **Location**, **Customer Geography**, **Members**, **All Customers**, **Australia**를 차례로 확장하고 **Queensland**를 마우스 오른쪽 단추로 클릭한 다음 **필터에 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23696-195">In the metadata pane, expand **Customer**, expand **Location**, expand **Customer Geography**, expand **Members**, expand **All Customers**, expand **Australia**, right-click **Queensland**, and then click **Add to Filter**.</span></span>

6.  <span data-ttu-id="23696-196">수준의 각 멤버를 확장 `Sales Reason Type` 하 여 Queensland의 고객이 인터넷을 통해 제품을 구매 하는 데 제공한 각 이유와 관련 된 달러 값을 검토 합니다 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="23696-196">Expand each member of the `Sales Reason Type` level to review the dollar values that are associated with each reason a customer in Queensland gave for their purchase of an [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] product over the Internet.</span></span>

     <span data-ttu-id="23696-197">각 판매 이유와 연결된 합계가 총 판매량보다 크며</span><span class="sxs-lookup"><span data-stu-id="23696-197">Notice that the totals that are associated with each sales reason add up to more than the total sales.</span></span> <span data-ttu-id="23696-198">이는 일부 고객이 여러 구매 이유를 언급했기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="23696-198">This is because some customers cited multiple reasons for their purchase.</span></span>

     <span data-ttu-id="23696-199">다음 그림에서는 큐브 디자이너의 **필터** 창과 **데이터** 창을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="23696-199">The following image shows the **Filter** pane and **Data** pane of Cube Designer.</span></span>

     <span data-ttu-id="23696-200">![큐브 디자이너의 필터 창과 데이터 창](../../2014/tutorials/media/l5-many-to-many-5.gif "큐브 디자이너의 필터 창과 데이터 창")</span><span class="sxs-lookup"><span data-stu-id="23696-200">![Filter and Data panes of Cube Designer](../../2014/tutorials/media/l5-many-to-many-5.gif "Filter and Data panes of Cube Designer")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="23696-201">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="23696-201">Next Task in Lesson</span></span>
 [<span data-ttu-id="23696-202">측정값 그룹의 차원 세분성 정의</span><span class="sxs-lookup"><span data-stu-id="23696-202">Defining Dimension Granularity within a Measure Group</span></span>](lesson-5-4-defining-dimension-granularity-within-a-measure-group.md)

## <a name="see-also"></a><span data-ttu-id="23696-203">참고 항목</span><span class="sxs-lookup"><span data-stu-id="23696-203">See Also</span></span>
 <span data-ttu-id="23696-204">[데이터 원본 뷰 디자이너에서 다이어그램 사용 &#40;Analysis Services&#41;](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md) [차원 관계](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) [는 다 대 다 관계 및 다 대 다 관계 속성을 정의 합니다](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md) .</span><span class="sxs-lookup"><span data-stu-id="23696-204">[Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md) [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) [Define a Many-to-Many Relationship and Many-to-Many Relationship Properties](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md)</span></span>


