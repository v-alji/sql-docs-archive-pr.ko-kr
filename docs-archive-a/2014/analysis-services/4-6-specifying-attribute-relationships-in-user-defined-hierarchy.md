---
title: 사용자 정의 계층의 특성 간 특성 관계 지정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 456c2a47-d395-45f9-9efa-89f3fa2ac621
author: minewiskan
ms.author: owend
ms.openlocfilehash: dc2fa03f72039aedd16c82b86ce0dd41b8f59702
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647354"
---
# <a name="specifying-attribute-relationships-between-attributes-in-a-user-defined-hierarchy"></a><span data-ttu-id="9696e-102">사용자 정의 계층의 특성 간 특성 관계 지정</span><span class="sxs-lookup"><span data-stu-id="9696e-102">Specifying Attribute Relationships Between Attributes in a User-Defined Hierarchy</span></span>
  <span data-ttu-id="9696e-103">이 자습서에서 이미 설명한 대로 특성 계층을 사용자 계층 안에 수준으로 구성하여 큐브 사용자를 위한 탐색 경로를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-103">As you have already learned in this tutorial, you can organize attribute hierarchies into levels within user hierarchies to provide navigation paths for users in a cube.</span></span> <span data-ttu-id="9696e-104">사용자 계층은 구/군/시, 시/도 및 국가와 같은 자연 계층을 나타내거나 직원 이름, 직책 및 부서 이름과 같은 탐색 경로를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-104">A user hierarchy can represent a natural hierarchy, such as city, state, and country, or can just represent a navigation path, such as employee name, title, and department name.</span></span> <span data-ttu-id="9696e-105">계층을 탐색하는 사용자에게는 이 두 가지 유형의 사용자 계층이 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-105">To the user navigating a hierarchy, these two types of user hierarchies are the same.</span></span>  
  
 <span data-ttu-id="9696e-106">자연 계층에서는 수준을 구성하는 특성 간의 특성 관계를 정의하면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 특정한 특성의 집계를 사용하여 관련 특성에서 결과를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-106">With a natural hierarchy, if you define attribute relationships between the attributes that make up the levels, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] can use an aggregation from one attribute to obtain the results from a related attribute.</span></span> <span data-ttu-id="9696e-107">특성 간에 정의된 관계가 없으면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 가 키 특성에서 키가 아닌 특성을 모두 집계합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-107">If there are no defined relationships between attributes, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] will aggregate all non-key attributes from the key attribute.</span></span> <span data-ttu-id="9696e-108">따라서 기본 데이터가 특성 관계를 지원하는 경우 특성 간의 특성 관계를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-108">Therefore, if the underlying data supports it, you should define attribute relationships between attributes.</span></span> <span data-ttu-id="9696e-109">특성 관계를 정의하면 차원, 파티션 및 쿼리 처리 성능이 개선됩니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-109">Defining attribute relationships improves dimension, partition, and query processing performance.</span></span> <span data-ttu-id="9696e-110">자세한 내용은 [특성 관계 정의](multidimensional-models/attribute-relationships-define.md) 및 [특성 관계](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9696e-110">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) and [Attribute Relationships](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
 <span data-ttu-id="9696e-111">특성 관계를 정의할 때 유동적 관계 또는 고정된 관계로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-111">When you define attribute relationships, you can specify that the relationship is either flexible or rigid.</span></span> <span data-ttu-id="9696e-112">고정된 관계로 정의할 경우 차원이 업데이트되면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 가 집계를 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-112">If you define a relationship as rigid, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] retains aggregations when the dimension is updated.</span></span> <span data-ttu-id="9696e-113">정의된 관계가 고정된 관계로 실제로 변경되면 차원이 전체적으로 처리되지 않을 경우 처리하는 동안 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-113">If a relationship that is defined as rigid actually changes, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] generates an error during processing unless the dimension is fully processed.</span></span> <span data-ttu-id="9696e-114">관계와 관계 속성을 적절히 지정하면 쿼리와 처리 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-114">Specifying the appropriate relationships and relationship properties increases query and processing performance.</span></span> <span data-ttu-id="9696e-115">자세한 내용은 [특성 관계 정의](multidimensional-models/attribute-relationships-define.md)및 [사용자 계층 속성](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9696e-115">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md), and [User Hierarchy Properties](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md).</span></span>  
  
 <span data-ttu-id="9696e-116">이 항목의 태스크에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트의 자연 사용자 계층에 있는 특성의 특성 관계를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-116">In the tasks in this topic, you define attribute relationships for the attributes in the natural user hierarchies in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project.</span></span> <span data-ttu-id="9696e-117">**Customer** 차원의 **Customer Geography**계층, **Sales Territory** 차원의 **Sales Territory** 계층, **Product** 차원의 **Product Model Lines** 계층 및 **Date** 차원의 **Fiscal Date** 와 **Calendar Date** 계층이 여기에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-117">These include the **Customer Geography** hierarchy in the **Custome**r dimension, the **Sales Territory** hierarchy in the **Sales Territory** dimension, the **Product Model** Lines hierarchy in the **Product** dimension, and the **Fiscal Date** and **Calendar Date** hierarchies in the **Date** dimension.</span></span> <span data-ttu-id="9696e-118">이러한 사용자 계층은 모두 자연 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-118">These user hierarchies are all natural hierarchies.</span></span>  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-customer-geography-hierarchy"></a><span data-ttu-id="9696e-119">Customer Geography 계층에 있는 특성의 특성 관계 정의</span><span class="sxs-lookup"><span data-stu-id="9696e-119">Defining Attribute Relationships for Attributes in the Customer Geography Hierarchy</span></span>  
  
1.  <span data-ttu-id="9696e-120">Customer 차원에 대한 차원 디자이너로 전환한 다음 **차원 구조** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-120">Switch to Dimension Designer for the Customer dimension, and then click the **Dimension Structure** tab.</span></span>  
  
     <span data-ttu-id="9696e-121">**계층** 창에서 **Customer Geography** 사용자 정의 계층의 수준을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-121">In the **Hierarchies** pane, notice the levels in the **Customer Geography** user-defined hierarchy.</span></span> <span data-ttu-id="9696e-122">수준 또는 특성 간의 관계가 정의되지 않았으므로 현재 이 계층은 사용자에 대한 드릴다운 경로에 불과합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-122">This hierarchy is currently just a drill-down path for users, as no relationship between levels or attributes have been defined.</span></span>  
  
2.  <span data-ttu-id="9696e-123">**특성 관계** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-123">Click the **Attribute Relationships** tab.</span></span>  
  
     <span data-ttu-id="9696e-124">**Geography** 테이블의 키가 아닌 특성을 **Geography** 테이블의 키 특성에 연결하는 4개의 특성 관계를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-124">Notice the four attribute relationships that link the non-key attributes from the **Geography** table to the key attribute from the **Geography** table.</span></span> <span data-ttu-id="9696e-125">**Geography** 특성은 **Full Name** 특성에 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-125">The **Geography** attribute is related to the **Full Name** attribute.</span></span> <span data-ttu-id="9696e-126">**Postal Code** 는 **Geography** 특성에 연결되고 **Geography** 특성은 **Full Name** 특성에 연결되므로 **Postal Code** 특성은 **Geography** 특성을 통해 **Full Name** 특성에 간접적으로 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-126">The **Postal Code** attribute is indirectly linked to the **Full Name** attribute through the **Geography** attribute, because the **Postal Code** is linked to the **Geography** attribute and the **Geography** attribute is linked to the **Full Name** attribute.</span></span> <span data-ttu-id="9696e-127">다음으로, **Geography** 특성을 사용하지 않도록 특성 관계를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-127">Next, we will change the attribute relationships so that they do not use the **Geography** attribute.</span></span>  
  
3.  <span data-ttu-id="9696e-128">다이어그램에서 **Full Name** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-128">In the diagram, right-click the **Full Name** attribute and then select **New Attribute Relationship**.</span></span>  
  
4.  <span data-ttu-id="9696e-129">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **Full Name**입니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-129">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Full Name**.</span></span> <span data-ttu-id="9696e-130">**관련 특성** 을 **Postal Code**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-130">Set the **Related Attribute** to **Postal Code**.</span></span> <span data-ttu-id="9696e-131">멤버 간의 관계는 시간이 지나면 변경될 수 있으므로 **관계 유형** 목록에서 관계 유형을 **유동** 으로 설정된 상태로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-131">In the **Relationship type** list, leave the relationship type set to **Flexible** because relationships between the members might change over time.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="9696e-132">관계가 중복되기 때문에 다이어그램에 경고 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-132">A warning icon appears in the diagram because the relationship is redundant.</span></span> <span data-ttu-id="9696e-133">관계 **전체 이름**  ->  **Geography** ->  **우편** 번호는 이미 존재 하며, 관계 **전체 이름**  ->  **우편**번호를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-133">The relationship **Full Name** -> **Geography**-> **Postal Code** already existed, and you just created the relationship **Full Name** -> **Postal Code**.</span></span> <span data-ttu-id="9696e-134">이제 관계 **지리** ->  **우편 번호가** 중복 되어 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-134">The relationship **Geography**-> **Postal Code** is now redundant, so we will remove it.</span></span>  
  
6.  <span data-ttu-id="9696e-135">**특성 관계** 창에서 **Geography**-> **Postal Code** 를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-135">In the **Attribute Relationships** pane, right-click **Geography**-> **Postal Code** and then click **Delete**.</span></span>  
  
7.  <span data-ttu-id="9696e-136">**개체 삭제** 대화 상자가 나타나면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-136">When the **Delete Objects** dialog box appears, click **OK**.</span></span>  
  
8.  <span data-ttu-id="9696e-137">다이어그램에서 **Postal Code** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-137">In the diagram, right-click the **Postal Code** attribute and then select **New Attribute Relationship**.</span></span>  
  
9. <span data-ttu-id="9696e-138">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **Postal Code**입니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-138">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Postal Code**.</span></span> <span data-ttu-id="9696e-139">**관련 특성** 을 **City**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-139">Set the **Related Attribute** to **City**.</span></span> <span data-ttu-id="9696e-140">**관계 유형** 목록에서 관계 유형을 **유동**으로 설정된 상태로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-140">In the **Relationship type** list, leave the relationship type set to **Flexible**.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="9696e-141">이제 관계 **지리** ->  **도시가** 중복 되어 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-141">The relationship **Geography**-> **City** is now redundant so we will delete it.</span></span>  
  
11. <span data-ttu-id="9696e-142">특성 관계 창에서 **Geography**City를 마우스 오른쪽 단추로 클릭 한 ->  **City** 다음 **삭제**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-142">In the Attribute Relationships pane, right-click **Geography**-> **City** and then click **Delete**.</span></span>  
  
12. <span data-ttu-id="9696e-143">**개체 삭제** 대화 상자가 나타나면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-143">When the **Delete Objects** dialog box appears, click **OK**.</span></span>  
  
13. <span data-ttu-id="9696e-144">다이어그램에서 **City** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-144">In the diagram, right-click the **City** attribute and then select **New Attribute Relationship**.</span></span>  
  
14. <span data-ttu-id="9696e-145">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **City**입니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-145">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **City**.</span></span> <span data-ttu-id="9696e-146">**관련 특성** 을 **State-Province**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-146">Set the **Related Attribute** to **State-Province**.</span></span> <span data-ttu-id="9696e-147">구/군/시와 시/도의 관계는 시간이 지나도 변경되지 않으므로 **관계 유형** 목록에서 관계 유형을 **고정** 으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-147">In the **Relationship type** list, set the relationship type to **Rigid** because the relationship between a city and a state will not change over time.</span></span>  
  
15. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
16. <span data-ttu-id="9696e-148">**Geography** 와 **State-Province** 사이의 화살표를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-148">Right-click the arrow between **Geography** and **State-Province** and then click **Delete**.</span></span>  
  
17. <span data-ttu-id="9696e-149">**개체 삭제** 대화 상자가 나타나면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-149">When the **Delete Objects** dialog box appears, click **OK**.</span></span>  
  
18. <span data-ttu-id="9696e-150">다이어그램에서 **State-Province** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-150">In the diagram, right-click the **State-Province** attribute and then select **New Attribute Relationship**.</span></span>  
  
19. <span data-ttu-id="9696e-151">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **State-Province**입니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-151">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **State-Province**.</span></span> <span data-ttu-id="9696e-152">**관련 특성** 을 **Country-Region**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-152">Set the **Related Attribute** to **Country-Region**.</span></span> <span data-ttu-id="9696e-153">시/도와 국가/지역의 관계는 시간이 지나도 변경되지 않으므로 **관계 유형** 목록에서 관계 유형을 **고정** 으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-153">In the **Relationship type** list, set the relationship type to **Rigid** because the relationship between a state-province and a country-region will not change over time.</span></span>  
  
20. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
21. <span data-ttu-id="9696e-154">특성 관계 창에서 **Geography** ->  **Country-region** 을 마우스 오른쪽 단추로 클릭 한 다음 **삭제**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-154">In the Attribute Relationships pane, right-click **Geography**-> **Country-Region** and then click **Delete**.</span></span>  
  
22. <span data-ttu-id="9696e-155">**개체 삭제** 대화 상자가 나타나면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-155">When the **Delete Objects** dialog box appears, click **OK**.</span></span>  
  
23. <span data-ttu-id="9696e-156">**차원 구조** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-156">Click the **Dimension Structure** tab.</span></span>  
  
     <span data-ttu-id="9696e-157">**Geography** 와 다른 특성 간 마지막 특성 관계를 삭제하면 해당 **Geography** 자체가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-157">Notice that when you delete the last attribute relationship between **Geography** and other attributes, that **Geography** itself is deleted.</span></span> <span data-ttu-id="9696e-158">특성이 더 이상 사용되지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-158">This is because the attribute is no longer used.</span></span>  
  
24. <span data-ttu-id="9696e-159">파일 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-159">On the File menu, click **Save All**.</span></span>  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-sales-territory-hierarchy"></a><span data-ttu-id="9696e-160">Sales Territory 계층에 있는 특성의 특성 관계 정의</span><span class="sxs-lookup"><span data-stu-id="9696e-160">Defining Attribute Relationships for Attributes in the Sales Territory Hierarchy</span></span>  
  
1.  <span data-ttu-id="9696e-161">**Sales Territory** 차원에 대한 차원 디자이너를 연 다음 **특성 관계** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-161">Open Dimension Designer for the **Sales Territory** dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="9696e-162">다이어그램에서 **Sales Territory Country** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-162">In the diagram, right-click the **Sales Territory Country** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="9696e-163">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **Sales Territory Country**입니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-163">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Sales Territory Country**.</span></span> <span data-ttu-id="9696e-164">**관련 특성** 을 **Sales Territory Group**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-164">Set the **Related Attribute** to **Sales Territory Group**.</span></span> <span data-ttu-id="9696e-165">**관계 유형** 목록에서 관계 유형을 **유동**으로 설정된 상태로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-165">In the **Relationship type** list, leave the relationship type set to **Flexible**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="9696e-166">이제**Sales Territory Group** 은 **Sales Territory Country**에 연결되고 **Sales Territory Country** 은 **Sales Territory Region**에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-166">**Sales Territory Group** is now linked to **Sales Territory Country**, and **Sales Territory Country** is now linked to **Sales Territory Region**.</span></span> <span data-ttu-id="9696e-167">한 국가의 지역 그룹화와 국가의 그룹화는 나중에 달라질 수 있으므로 이러한 각 관계의 **RelationshipType** 속성은 **유동** 으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-167">The **RelationshipType** property for each of these relationships is set to **Flexible** because the groupings of regions within a country might change over time and because the groupings of countries into groups might change over time.</span></span>  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-product-model-lines-hierarchy"></a><span data-ttu-id="9696e-168">Product Model Lines 계층에 있는 특성의 특성 관계 정의</span><span class="sxs-lookup"><span data-stu-id="9696e-168">Defining Attribute Relationships for Attributes in the Product Model Lines Hierarchy</span></span>  
  
1.  <span data-ttu-id="9696e-169">**Product** 차원에 대한 차원 디자이너를 연 다음 **특성 관계** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-169">Open Dimension Designer for the **Product** dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="9696e-170">다이어그램에서 **Model Name** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-170">In the diagram, right-click the **Model Name** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="9696e-171">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **Model Name**입니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-171">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Model Name**.</span></span> <span data-ttu-id="9696e-172">**관련 특성** 을 **Product Line**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-172">Set the **Related Attribute** to **Product Line**.</span></span> <span data-ttu-id="9696e-173">**관계 유형** 목록에서 관계 유형을 **유동**으로 설정된 상태로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-173">In the **Relationship type** list, leave the relationship type set to **Flexible**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-fiscal-date-hierarchy"></a><span data-ttu-id="9696e-174">Fiscal Date 계층에 있는 특성의 특성 관계 정의</span><span class="sxs-lookup"><span data-stu-id="9696e-174">Defining Attribute Relationships for Attributes in the Fiscal Date Hierarchy</span></span>  
  
1.  <span data-ttu-id="9696e-175">**Date** 차원에 대한 차원 디자이너로 전환한 다음 **특성 관계** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-175">Switch to Dimension Designer for the **Date** dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="9696e-176">다이어그램에서 **Month Name** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-176">In the diagram, right-click the **Month Name** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="9696e-177">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **Month Name**입니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-177">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Month Name**.</span></span> <span data-ttu-id="9696e-178">**관련 특성** 을 **Fiscal Quarter**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-178">Set the **Related Attribute** to **Fiscal Quarter**.</span></span> <span data-ttu-id="9696e-179">**관계 유형** 목록에서 관계 유형을 **고정**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-179">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="9696e-180">다이어그램에서 **Fiscal Quarter** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-180">In the diagram, right-click the **Fiscal Quarter** attribute and then select **New Attribute Relationship**.</span></span>  
  
6.  <span data-ttu-id="9696e-181">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **Fiscal Quarter**입니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-181">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Fiscal Quarter**.</span></span> <span data-ttu-id="9696e-182">**관련 특성** 을 **Fiscal Semester**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-182">Set the **Related Attribute** to **Fiscal Semester**.</span></span> <span data-ttu-id="9696e-183">**관계 유형** 목록에서 관계 유형을 **고정**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-183">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="9696e-184">다이어그램에서 **Fiscal Semester** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-184">In the diagram, right-click the **Fiscal Semester** attribute and then select **New Attribute Relationship**.</span></span>  
  
9. <span data-ttu-id="9696e-185">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **Fiscal Semester**입니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-185">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Fiscal Semester**.</span></span> <span data-ttu-id="9696e-186">**관련 특성** 을 **Fiscal Year**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-186">Set the **Related Attribute** to **Fiscal Year**.</span></span> <span data-ttu-id="9696e-187">**관계 유형** 목록에서 관계 유형을 **고정**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-187">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-calendar-date-hierarchy"></a><span data-ttu-id="9696e-188">Calendar Date 계층에 있는 특성의 특성 관계 정의</span><span class="sxs-lookup"><span data-stu-id="9696e-188">Defining Attribute Relationships for Attributes in the Calendar Date Hierarchy</span></span>  
  
1.  <span data-ttu-id="9696e-189">다이어그램에서 **Month Name** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-189">In the diagram, right-click the **Month Name** attribute and then select **New Attribute Relationship**.</span></span>  
  
2.  <span data-ttu-id="9696e-190">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **Month Name**입니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-190">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Month Name**.</span></span> <span data-ttu-id="9696e-191">**관련 특성** 을 **Calendar Quarter**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-191">Set the **Related Attribute** to **Calendar Quarter**.</span></span> <span data-ttu-id="9696e-192">**관계 유형** 목록에서 관계 유형을 **고정**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-192">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="9696e-193">다이어그램에서 **Calendar Quarter** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-193">In the diagram, right-click the **Calendar Quarter** attribute and then select **New Attribute Relationship**.</span></span>  
  
5.  <span data-ttu-id="9696e-194">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **Calendar Quarter**입니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-194">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Quarter**.</span></span> <span data-ttu-id="9696e-195">**관련 특성** 을 **Calendar Semester**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-195">Set the **Related Attribute** to **Calendar Semester**.</span></span> <span data-ttu-id="9696e-196">**관계 유형** 목록에서 관계 유형을 **고정**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-196">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="9696e-197">다이어그램에서 **Calendar Semester** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-197">In the diagram, right-click the **Calendar Semester** attribute and then select **New Attribute Relationship**.</span></span>  
  
8.  <span data-ttu-id="9696e-198">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **Calendar Semester**입니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-198">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Semester**.</span></span> <span data-ttu-id="9696e-199">**관련 특성** 을 **Calendar Year**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-199">Set the **Related Attribute** to **Calendar Year**.</span></span> <span data-ttu-id="9696e-200">**관계 유형** 목록에서 관계 유형을 **고정**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-200">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-geography-hierarchy"></a><span data-ttu-id="9696e-201">Geography 계층에 있는 특성의 특성 관계 정의</span><span class="sxs-lookup"><span data-stu-id="9696e-201">Defining Attribute Relationships for Attributes in the Geography Hierarchy</span></span>  
  
1.  <span data-ttu-id="9696e-202">Geography 차원에 대한 차원 디자이너를 연 다음 **특성 관계** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-202">Open Dimension Designer for the Geography dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="9696e-203">다이어그램에서 **Postal Code** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-203">In the diagram, right-click the **Postal Code** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="9696e-204">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **Postal Code**입니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-204">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Postal Code**.</span></span> <span data-ttu-id="9696e-205">**관련 특성** 을 **City**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-205">Set the **Related Attribute** to **City**.</span></span> <span data-ttu-id="9696e-206">**관계 유형** 목록에서 관계 유형을 **유동**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-206">In the **Relationship type** list, set the relationship type to **Flexible**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="9696e-207">다이어그램에서 **City** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-207">In the diagram, right-click the **City** attribute and then select **New Attribute Relationship**.</span></span>  
  
6.  <span data-ttu-id="9696e-208">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **City**입니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-208">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **City**.</span></span> <span data-ttu-id="9696e-209">**관련 특성** 을 **State-Province**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-209">Set the **Related Attribute** to **State-Province**.</span></span> <span data-ttu-id="9696e-210">**관계 유형** 목록에서 관계 유형을 **고정**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-210">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="9696e-211">다이어그램에서 **State-Province** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-211">In the diagram, right-click the **State-Province** attribute and then select **New Attribute Relationship**.</span></span>  
  
9. <span data-ttu-id="9696e-212">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **State-Province**입니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-212">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **State-Province**.</span></span> <span data-ttu-id="9696e-213">**관련 특성** 을 **Country-Region**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-213">Set the **Related Attribute** to **Country-Region**.</span></span> <span data-ttu-id="9696e-214">**관계 유형** 목록에서 관계 유형을 **고정**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-214">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="9696e-215">다이어그램에서 **Geography Key** 특성을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-215">In the diagram, right-click the **Geography Key** attribute and then select **Properties**.</span></span>  
  
12. <span data-ttu-id="9696e-216">**AttributeHierarchyOptimizedState** 속성을 **NotOptimized**로, **AttributeHierarchyOrdered** 속성을 **False**로, **AttributeHierarchyVisible** 속성을 **False**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-216">Set the **AttributeHierarchyOptimizedState** property to **NotOptimized**, set the **AttributeHierarchyOrdered** property to **False**, and set the **AttributeHierarchyVisible** property to **False**.</span></span>  
  
13. <span data-ttu-id="9696e-217">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-217">On the **File** menu, click **Save All**.</span></span>  
  
14. <span data-ttu-id="9696e-218">**의** 빌드 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9696e-218">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="9696e-219">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="9696e-219">Next Task in Lesson</span></span>  
 [<span data-ttu-id="9696e-220">알 수 없는 멤버 및 Null 처리 속성 정의</span><span class="sxs-lookup"><span data-stu-id="9696e-220">Defining the Unknown Member and Null Processing Properties</span></span>](lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="9696e-221">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9696e-221">See Also</span></span>  
 <span data-ttu-id="9696e-222">[특성 관계 정의](multidimensional-models/attribute-relationships-define.md) </span><span class="sxs-lookup"><span data-stu-id="9696e-222">[Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) </span></span>  
 [<span data-ttu-id="9696e-223">사용자 계층 속성</span><span class="sxs-lookup"><span data-stu-id="9696e-223">User Hierarchy Properties</span></span>](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)  
  
  
