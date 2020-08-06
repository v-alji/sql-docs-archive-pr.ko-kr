---
title: 팩트 관계 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4b49a078-6848-4286-bc71-cf4862d29064
author: minewiskan
ms.author: owend
ms.openlocfilehash: 26f8068301c424d5aea9f54e882ceb8a4dc72806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660726"
---
# <a name="defining-a-fact-relationship"></a><span data-ttu-id="3a26b-102">팩트 관계 정의</span><span class="sxs-lookup"><span data-stu-id="3a26b-102">Defining a Fact Relationship</span></span>
  <span data-ttu-id="3a26b-103">사용자는 팩트 테이블에 있는 데이터 항목별로 측정값 차원을 구분하거나 특정 판매 팩트에 관련된 송장 번호나 구매 주문 번호와 같은 특정 추가 관련 정보를 팩트 테이블에서 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-103">Users sometimes want to be able to dimension measures by data items that are in the fact table or to query the fact table for specific additional related information, such as invoice numbers or purchase order numbers related to specific sales facts.</span></span> <span data-ttu-id="3a26b-104">이러한 팩트 테이블 항목을 기반으로 차원을 정의할 경우 이 차원을 *팩트 차원*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-104">When you define a dimension based on such a fact table item, the dimension is called a *fact dimension*.</span></span> <span data-ttu-id="3a26b-105">팩트 차원은 중복 제거 차원이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-105">Fact dimensions are also known as degenerate dimensions.</span></span> <span data-ttu-id="3a26b-106">팩트 차원은 특정 송장 번호에 관련된 모든 행과 같은 관련 팩트 테이블 행을 함께 그룹화하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-106">Fact dimensions are useful for grouping together related fact table rows, such as all the rows that are related to a particular invoice number.</span></span> <span data-ttu-id="3a26b-107">이 정보를 관계형 데이터베이스에 있는 별도의 차원 테이블에 넣을 수 있는데도 정보에 대한 별도의 차원 테이블을 만들면 차원 테이블이 팩트 테이블과 같은 속도로 커지고 중복 데이터가 발생하며 과도하게 복잡해지기 때문에 좋지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-107">Although you can put this information in a separate dimension table in the relational database, creating a separate dimension table for the information provides no benefit because the dimension table would grow at the same rate as the fact table, and would just create duplicate data and unnecessary complexity.</span></span>

 <span data-ttu-id="3a26b-108">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 쿼리 성능 향상을 위해 팩트 차원 데이터를 MOLAP 차원 구조로 복제할지 또는 쿼리 성능을 향상시키는 대신 스토리지 공간을 절약하기 위해 팩트 차원을 ROLAP 차원으로 정의할지 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-108">Within [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], you can determine whether to duplicate the fact dimension data in a MOLAP dimension structure for increased query performance, or whether to define the fact dimension as a ROLAP dimension to save storage space at the expense of query performance.</span></span> <span data-ttu-id="3a26b-109">MOLAP 스토리지 모드를 사용하여 차원을 저장하면 모든 차원 멤버는 측정값 그룹의 파티션에 저장될 뿐만 아니라 고도로 압축된 MOLAP 구조로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-109">When you store a dimension with the MOLAP storage mode, all the dimension members are stored in the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in a highly compressed MOLAP structure, in addition to being stored in the measure group's partitions.</span></span> <span data-ttu-id="3a26b-110">ROLAP 저장소 모드를 사용 하 여 차원을 저장 하면 차원 정의만 MOLAP 구조로 저장 되 고 차원 멤버 자체는 쿼리 시 기본 관계형 팩트 테이블에서 쿼리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-110">When you store a dimension with the ROLAP storage mode, only the dimension definition is stored in the MOLAP structure-the dimension members themselves are queried from the underlying relational fact table at query time.</span></span> <span data-ttu-id="3a26b-111">팩트 차원의 쿼리 빈도, 표준 쿼리에서 반환된 행 수, 쿼리 성능 및 처리 비용에 따라 적절한 스토리지 모드를 결정하십시오.</span><span class="sxs-lookup"><span data-stu-id="3a26b-111">You decide the appropriate storage mode based on how frequently the fact dimension is queried, the number of rows returned by a typical query, the performance of the query, and the processing cost.</span></span> <span data-ttu-id="3a26b-112">차원을 ROLAP으로 정의한다고 해서 해당 차원을 사용하는 모든 큐브도 ROLAP 스토리지 모드를 사용하여 저장해야 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-112">Defining a dimension as ROLAP does not require that all cubes that use the dimension also be stored with the ROLAP storage mode.</span></span> <span data-ttu-id="3a26b-113">각 차원에 대한 스토리지 모드는 독립적으로 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-113">The storage mode for each dimension can be configured independently.</span></span>

 <span data-ttu-id="3a26b-114">팩트 차원을 정의하면 팩트 차원과 측정값 그룹의 관계를 팩트 관계로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-114">When you define a fact dimension, you can define the relationship between the fact dimension and the measure group as a fact relationship.</span></span> <span data-ttu-id="3a26b-115">팩트 관계에 적용되는 제약 조건은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-115">The following constraints apply to fact relationships:</span></span>

-   <span data-ttu-id="3a26b-116">세분성 특성이 차원에 대한 키 열이어야 하며 이에 따라 차원과 팩트 테이블의 팩트 간 일 대 일 관계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-116">The granularity attribute must be the key column for the dimension, which creates a one-to-one relationship between the dimension and the facts in the fact table.</span></span>

-   <span data-ttu-id="3a26b-117">차원은 하나의 측정값 그룹에 대한 팩트 관계만 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-117">A dimension can have a fact relationship with only a single measure group.</span></span>

> [!NOTE]
>  <span data-ttu-id="3a26b-118">매번 팩트 관계에서 참조하는 측정값 그룹을 업데이트한 후에는 팩트 차원을 증분 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-118">Fact dimensions must be incrementally updated after every update to the measure group that the fact relationship references.</span></span>

 <span data-ttu-id="3a26b-119">자세한 내용은 [차원 관계](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)와 [팩트 관계 및 팩트 관계 속성 정의](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a26b-119">For more information, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), and [Define a Fact Relationship and Fact Relationship Properties](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md).</span></span>

 <span data-ttu-id="3a26b-120">이 항목의 태스크에서는 **FactInternetSales** 팩트 테이블의 **CustomerPONumber** 열을 기반으로 새 큐브 차원을 추가한 다음</span><span class="sxs-lookup"><span data-stu-id="3a26b-120">In the tasks in this topic, you add a new cube dimension based on the **CustomerPONumber** column in the **FactInternetSales** fact table.</span></span> <span data-ttu-id="3a26b-121">이 새로운 큐브 차원과 **Internet Sales** 측정값 그룹 간 관계를 팩트 관계로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-121">You then define the relationship between this new cube dimension and the **Internet Sales** measure group as a fact relationship.</span></span>

## <a name="defining-the-internet-sales-orders-fact-dimension"></a><span data-ttu-id="3a26b-122">Internet Sales Orders 팩트 차원 정의</span><span class="sxs-lookup"><span data-stu-id="3a26b-122">Defining the Internet Sales Orders Fact Dimension</span></span>

1.  <span data-ttu-id="3a26b-123">솔루션 탐색기에서 **차원**을 마우스 오른쪽 단추로 클릭한 다음 **새 차원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-123">In Solution Explorer, right-click **Dimensions**, and then click **New Dimension**.</span></span>

2.  <span data-ttu-id="3a26b-124">**차원 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-124">On the **Welcome to the Dimension Wizard** page, click **Next**.</span></span>

3.  <span data-ttu-id="3a26b-125">**생성 방법 선택** 페이지에서 **기존 테이블 사용** 옵션이 선택되어 있는지 확인하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-125">On the **Select Creation Method** page, verify that the **Use an existing table** option is selected, and then click **Next**.</span></span>

4.  <span data-ttu-id="3a26b-126">**원본 정보 지정** 페이지에서 **Adventure Works DW 2012** 데이터 원본 뷰가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-126">On the **Specify Source Information** page, verify that the **Adventure Works DW 2012** data source view is selected.</span></span>

5.  <span data-ttu-id="3a26b-127">**주 테이블** 목록에서 **InternetSales**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-127">In the **Main table** list, select **InternetSales**.</span></span>

6.  <span data-ttu-id="3a26b-128">**키 열** 목록에 **SalesOrderNumber** 와 **SalesOrderLineNumber** 가 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-128">In the **Key columns** list, verify that **SalesOrderNumber** and **SalesOrderLineNumber** are listed.</span></span>

7.  <span data-ttu-id="3a26b-129">**이름 열** 목록에서 **SalesOrderLineNumber**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-129">In the **Name column** list, select **SalesOrderLineNumber**.</span></span>

8.  <span data-ttu-id="3a26b-130">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-130">Click **Next**.</span></span>

9. <span data-ttu-id="3a26b-131">**관련 테이블 선택** 페이지에서 모든 테이블 옆 확인란의 선택을 취소한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-131">On the **Select Related Tables** page, clear the check boxes beside all of the tables, and then click **Next**.</span></span>

10. <span data-ttu-id="3a26b-132">**차원 특성 선택** 페이지에서 헤더의 확인란을 두 번 클릭하여 모든 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-132">On the **Select Dimension Attributes** page, click the check box in the header twice to clear all of the check boxes.</span></span> <span data-ttu-id="3a26b-133">**Sales Order Number** 특성은 키 특성이므로 선택된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-133">The **Sales Order Number** attribute will remain selected because it is the key attribute.</span></span>

11. <span data-ttu-id="3a26b-134">**Customer PO Number** 특성을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-134">Select the **Customer PO Number** attribute, and then click **Next**.</span></span>

12. <span data-ttu-id="3a26b-135">**마법사 완료** 페이지에서 이름을 **Internet Sales Order Details** 로 바꾼 후 **마침** 을 클릭하여 마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-135">On the **Completing the Wizard** page, change the name to **Internet Sales Order Details** and then click **Finish** to complete the wizard.</span></span>

13. <span data-ttu-id="3a26b-136">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-136">On the **File** menu, click **Save All**.</span></span>

14. <span data-ttu-id="3a26b-137">**Internet Sales Order Details** 차원에 대 한 차원 디자이너의 **특성** 창에서 **Sales order Number**를 선택한 후 속성 창의 **이름** 속성을로 변경 합니다.`Item Description.`</span><span class="sxs-lookup"><span data-stu-id="3a26b-137">In the **Attributes** pane of the Dimension Designer for the **Internet Sales Order Details** dimension, select **Sales Order Number**, and then change the **Name** property in the Properties window to `Item Description.`</span></span>

15. <span data-ttu-id="3a26b-138">**NameColumn** 속성 셀에서 찾아보기 단추 **(...)** 를 클릭 합니다. **이름 열** 대화 상자의 **원본 테이블** 목록에서 **Product** 를 선택 하 고 **원본 열**에 **EnglishProductName** 를 선택한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-138">In the **NameColumn** property cell, click the browse button **(...)**. In the **Name Column** dialog box, select **Product** from the **Source table** list, select **EnglishProductName** for the **Source column**, and then click **OK**.</span></span>

16. <span data-ttu-id="3a26b-139">**데이터 원본 뷰** 창에서 **InternetSales** 테이블의 **SalesOrderNumber** 열을 **특성** 창으로 끌어다 놓아 **Sales Order Number** 특성을 차원에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-139">Add the **Sales Order Number** attribute to the dimension by dragging the **SalesOrderNumber** column from the **InternetSales** table in the **Data Source View** pane to the **Attributes** pane.</span></span>

17. <span data-ttu-id="3a26b-140">새 **Sales Order Number** 특성의 **Name** 속성을로 변경 하 `Order Number` 고 **OrderBy** 속성을 **Key**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-140">Change the **Name** property of the new **Sales Order Number** attribute to `Order Number`, and change the **OrderBy** property to **Key**.</span></span>

18. <span data-ttu-id="3a26b-141">**계층** 창에서 및 항목 설명 수준을 순서 대로 포함 하는 **Internet Sales Orders** 사용자 계층을 만듭니다 `Order Number` **Item Description** .</span><span class="sxs-lookup"><span data-stu-id="3a26b-141">In the **Hierarchies** pane, create an **Internet Sales Orders** user hierarchy that contains the `Order Number` and **Item Description** levels, in that order.</span></span>

19. <span data-ttu-id="3a26b-142">**특성** 창에서 **Internet Sales Order Details**를 선택한 다음 속성 창에서 **StorageMode** 속성 값을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-142">In the **Attributes** pane, select **Internet Sales Order Details**, and then review the value for the **StorageMode** property in the Properties window.</span></span>

     <span data-ttu-id="3a26b-143">기본적으로 이 차원은 MOLAP 차원으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-143">Notice that, by default, this dimension is stored as a MOLAP dimension.</span></span> <span data-ttu-id="3a26b-144">스토리지 모드를 ROLAP으로 변경하면 처리 시간과 스토리지 공간이 절약되지만 쿼리 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-144">Although changing the storage mode to ROLAP will save processing time and storage space, it occurs at the expense of query performance.</span></span> <span data-ttu-id="3a26b-145">이 자습서에서는 스토리지 모드로 MOLAP을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-145">For the purposes of this tutorial, you will use MOLAP as the storage mode.</span></span>

20. <span data-ttu-id="3a26b-146">새로 만들어진 차원을 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 큐브 차원으로 추가하려면 **큐브 디자이너**로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-146">To add the newly created dimension to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube as a cube dimension, switch to **Cube Designer**.</span></span> <span data-ttu-id="3a26b-147">**큐브 구조** 탭에서 **차원** 창을 마우스 오른쪽 단추로 클릭하고 **큐브 차원 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-147">On the **Cube Structure** tab, right-click in the **Dimensions** pane and select **Add Cube Dimension**.</span></span>

21. <span data-ttu-id="3a26b-148">**큐브 차원 추가**대화 상자에서 **Internet Sales Order Details** 를 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-148">In the **Add Cube Dimension**.dialog box, select **Internet Sales Order Details** and then click **OK**.</span></span>

## <a name="defining-a-fact-relationship-for-the-fact-dimension"></a><span data-ttu-id="3a26b-149">팩트 차원의 팩트 관계 정의</span><span class="sxs-lookup"><span data-stu-id="3a26b-149">Defining a Fact Relationship for the Fact Dimension</span></span>

1.  <span data-ttu-id="3a26b-150">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 대한 큐브 디자이너에서 **차원 용도** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-150">In the Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, click the **Dimension Usage** tab.</span></span>

     <span data-ttu-id="3a26b-151">**Internet Sales Order Details** 큐브 차원은 고유 아이콘에 표시된 대로 자동으로 팩트 관계를 갖도록 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-151">Notice that the **Internet Sales Order Details** cube dimension is automatically configured as having a fact relationship, as shown by the unique icon.</span></span>

2.  <span data-ttu-id="3a26b-152">**Internet sales** 측정값 그룹과 **Internet sales Order Details** 차원의 교집합에서 **Item Description** 셀의 찾아보기 단추 (**...**)를 클릭 하 여 팩트 관계 속성을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-152">Click the browse button (**...**) in the **Item Description** cell, at the intersection of the **Internet Sales** measure group and the **Internet Sales Order Details** dimension, to review the fact relationship properties.</span></span>

     <span data-ttu-id="3a26b-153">**관계 정의** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-153">The **Define Relationship** dialog box opens.</span></span> <span data-ttu-id="3a26b-154">어떤 속성도 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-154">Notice that you cannot configure any of the properties.</span></span>

     <span data-ttu-id="3a26b-155">다음 그림에서는 **관계 정의** 대화 상자의 팩트 관계 속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-155">The following image shows the fact relationship properties in the **Define Relationship** dialog box.</span></span>

     <span data-ttu-id="3a26b-156">![관계 정의 대화 상자](../../2014/tutorials/media/l5-factrelationship-2.gif "관계 정의 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="3a26b-156">![Define Relationship dialog box](../../2014/tutorials/media/l5-factrelationship-2.gif "Define Relationship dialog box")</span></span>

3.  <span data-ttu-id="3a26b-157">**취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-157">Click **Cancel**.</span></span>

## <a name="browsing-the-cube-by-using-the-fact-dimension"></a><span data-ttu-id="3a26b-158">팩트 차원을 사용하여 큐브 찾아보기</span><span class="sxs-lookup"><span data-stu-id="3a26b-158">Browsing the Cube by Using the Fact Dimension</span></span>

1.  <span data-ttu-id="3a26b-159">**빌드** 메뉴에서 **Analysis Services Tutorial 배포** 를 클릭하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스의 변경 내용을 배포하고 데이터베이스를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-159">On the **Build** menu, click **Deploy Analysis Services Tutorial** to deploy the changes to the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and process the database.</span></span>

2.  <span data-ttu-id="3a26b-160">배포가 성공적으로 완료된 후 **Tutorial 큐브에 대한 큐브 디자이너에서** 브라우저 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 탭을 클릭한 다음 **다시 연결** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-160">After deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>

3.  <span data-ttu-id="3a26b-161">데이터 창에서 모든 측정값과 계층을 제거한 다음 **Internet Sales-Sales Amount** 측정값을 데이터 창의 데이터 영역에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-161">Clear all measures and hierarchies from the data pane, and then add the **Internet Sales-Sales Amount** measure to the data area of the data pane.</span></span>

4.  <span data-ttu-id="3a26b-162">메타데이터 창에서 **Customer**, **Location**, **Customer Geography**, **Members**, **All Customers**, **Australia**, **Queensland**, **Brisbane**, **4000**을 차례로 확장하고 **Adam Powell**를 마우스 오른쪽 단추로 클릭한 다음 **필터에 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-162">In the metadata pane, expand **Customer**, expand **Location**, expand **Customer Geography**, expand **Members**, expand **All Customers**, expand **Australia**, expand **Queensland**, expand **Brisbane**, expand **4000**, right-click **Adam Powell**, and then click **Add to Filter**.</span></span>

     <span data-ttu-id="3a26b-163">단일 고객에게 반환되는 판매 주문을 제한하도록 필터링하면 해당 쿼리 성능이 크게 저하되지 않고도 대용량 팩트 테이블에서 기본 정보로 드릴다운할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-163">Filtering to limit the sales orders returned to a single customer lets the user drill down to the underlying detail in a large fact table without suffering a significant loss in query performance.</span></span>

5.  <span data-ttu-id="3a26b-164">**Internet Sales Order Details** 차원의 **Internet Sales Orders** 사용자 정의 계층을 데이터 창의 행 영역에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-164">Add the **Internet Sales Orders** user-defined hierarchy from the **Internet Sales Order Details** dimension to the row area of the data pane.</span></span>

     <span data-ttu-id="3a26b-165">판매 주문 번호와 Adam Powell의 해당 인터넷 판매량이 데이터 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-165">Notice that the sales order numbers and the corresponding Internet sales amounts for Adam Powell appear in the data pane.</span></span>

     <span data-ttu-id="3a26b-166">다음 이미지에서는 이전 단계의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3a26b-166">The following image shows the result of the previous steps.</span></span>

     <span data-ttu-id="3a26b-167">![Internet Sales-Sales Amount 차원 지정](../../2014/tutorials/media/l5-factrelationship-3.gif "Internet Sales-Sales Amount 차원 지정")</span><span class="sxs-lookup"><span data-stu-id="3a26b-167">![Dimensioning of Internet Sales-Sales Amount](../../2014/tutorials/media/l5-factrelationship-3.gif "Dimensioning of Internet Sales-Sales Amount")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="3a26b-168">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="3a26b-168">Next Task in Lesson</span></span>
 [<span data-ttu-id="3a26b-169">다 대 다 관계 정의</span><span class="sxs-lookup"><span data-stu-id="3a26b-169">Defining a Many-to-Many Relationship</span></span>](lesson-5-3-defining-a-many-to-many-relationship.md)

## <a name="see-also"></a><span data-ttu-id="3a26b-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a26b-170">See Also</span></span>
 <span data-ttu-id="3a26b-171">[차원 관계](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) [는 팩트 관계 및 팩트 관계 속성을 정의 합니다](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md) .</span><span class="sxs-lookup"><span data-stu-id="3a26b-171">[Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) [Define a Fact Relationship and Fact Relationship Properties](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)</span></span>


