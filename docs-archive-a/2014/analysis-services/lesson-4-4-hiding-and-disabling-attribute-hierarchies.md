---
title: 특성 계층 숨기기 및 해제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 095039c2-7104-414c-a9a6-327b03ce79df
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc043c68d2a83424a14707799fd90bf893abc12d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742632"
---
# <a name="hiding-and-disabling-attribute-hierarchies"></a><span data-ttu-id="c947b-102">특성 계층 숨기기 및 비활성화</span><span class="sxs-lookup"><span data-stu-id="c947b-102">Hiding and Disabling Attribute Hierarchies</span></span>
  <span data-ttu-id="c947b-103">기본적으로 특성 계층은 차원의 모든 특성에 대해 만들어지며 각 계층을 팩트 데이터 차원 지정에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-103">By default, an attribute hierarchy is created for every attribute in a dimension, and each hierarchy is available for dimensioning fact data.</span></span> <span data-ttu-id="c947b-104">이 계층은 계층의 모든 멤버를 포함하는 “All” 수준 및 세부 수준으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-104">This hierarchy consists of an "All" level and a detail level containing all members of the hierarchy.</span></span> <span data-ttu-id="c947b-105">이미 설명한 대로 특성을 사용자 정의 계층으로 구성하여 큐브에 탐색 경로를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-105">As you have already learned, you can organize attributes into user-defined hierarchies to provide navigation paths in a cube.</span></span> <span data-ttu-id="c947b-106">경우에 따라서는 일부 특성과 계층을 비활성화하거나 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-106">Under certain circumstances, you may want to disable or hide some attributes and their hierarchies.</span></span> <span data-ttu-id="c947b-107">예를 들어 주민 등록 번호, 급여, 생년월일 및 로그인 정보와 같은 일부 특성은 사용자가 큐브 정보의 차원을 지정하는 데 사용하는 특성이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-107">For example, certain attributes such as social security numbers or national identification numbers, pay rates, birth dates, and login information are not attributes by which users will dimension cube information.</span></span> <span data-ttu-id="c947b-108">일반적으로 이 정보는 특정 특성 멤버의 세부 사항으로만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-108">Instead, this information is generally only viewed as details of a particular attribute member.</span></span> <span data-ttu-id="c947b-109">이러한 특성 계층을 숨기고 특정 특성의 멤버 속성으로만 특성을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-109">You may want to hide these attribute hierarchies, leaving the attributes visible only as member properties of a specific attribute.</span></span> <span data-ttu-id="c947b-110">또한 고객 이름, 우편 번호 등의 다른 특성 멤버가 특성 계층을 통해 따로 표시되지 않고 사용자 계층을 통해 표시될 경우에만 이러한 특성 멤버를 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-110">You may also want to make members of other attributes, such as customer names or postal codes, visible only when they are viewed through a user hierarchy instead of independently through an attribute hierarchy.</span></span> <span data-ttu-id="c947b-111">그 이유 중 하나는 특성 계층에 있는 고유한 멤버의 개수 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-111">One reason to do so may be the sheer number of distinct members in the attribute hierarchy.</span></span> <span data-ttu-id="c947b-112">마지막으로 처리 성능을 향상시키기 위해 사용자가 탐색에 사용하지 않는 특성 계층을 비활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-112">Finally, to improve processing performance, you should disable attribute hierarchies that users will not use for browsing.</span></span>

 <span data-ttu-id="c947b-113">**AttributeHierarchyEnabled** 속성 값은 특성 계층을 만들지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-113">The value of the **AttributeHierarchyEnabled** property determines whether an attribute hierarchy is created.</span></span> <span data-ttu-id="c947b-114">이 속성을 **False**로 설정하면 특성 계층이 만들어지지 않으며 특성을 사용자 계층의 수준으로 사용할 수 없어 특성 계층이 멤버 속성으로만 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-114">If this property is set to **False**, the attribute hierarchy is not created and the attribute cannot be used as a level in a user hierarchy; the attribute hierarchy exists as a member property only.</span></span> <span data-ttu-id="c947b-115">그러나 비활성화된 특성 계층은 여전히 다른 특성의 멤버를 정렬하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-115">However, a disabled attribute hierarchy can still be used to order the members of another attribute.</span></span> <span data-ttu-id="c947b-116">**AttributeHierarchyEnabled** 속성 값을 **True**로 설정하면 **AttributeHierarchyVisible** 속성 값이 사용자 정의 계층에서의 사용에 관계없이 특성 계층을 표시할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-116">If the value of the **AttributeHierarchyEnabled** property is set to **True**, the value of the **AttributeHierarchyVisible** property determines whether the attribute hierarchy is visible independent of its use in a user-defined hierarchy.</span></span>

 <span data-ttu-id="c947b-117">특성 계층을 활성화하면 다음 3개의 추가 속성 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-117">When an attribute hierarchy is enabled, you may want to specify values for the following three additional properties:</span></span>

-   <span data-ttu-id="c947b-118">**IsAggregatable**</span><span class="sxs-lookup"><span data-stu-id="c947b-118">**IsAggregatable**</span></span>

     <span data-ttu-id="c947b-119">기본적으로 모든 특성 계층에 (All) 수준이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-119">By default, an (All) level is defined for all attribute hierarchies.</span></span> <span data-ttu-id="c947b-120">활성화된 특성 계층에 대해 (All) 수준을 비활성화하려면 이 속성의 값을 **False**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-120">To disable the (All) level for an enabled attribute hierarchy, set the value for this property to **False**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c947b-121">**IsAggregatable** 속성이 false로 설정된 특성은 사용자 정의 계층의 루트로만 사용할 수 있으며 기본 멤버가 지정되어 있어야 합니다. 그렇지 않은 경우 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 엔진이 기본 멤버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-121">An attribute that has its **IsAggregatable** property set to false can only be used as the root of a user-defined hierarchy and must have a default member specified (otherwise, one will be chosen for you by the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] engine).</span></span>

-   <span data-ttu-id="c947b-122">**AttributeHierarchyOrdered**</span><span class="sxs-lookup"><span data-stu-id="c947b-122">**AttributeHierarchyOrdered**</span></span>

     <span data-ttu-id="c947b-123">기본적으로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서는 처리하는 동안 활성화된 특성 계층의 멤버를 정렬한 다음 Name, Key 등 **OrderBy** 속성의 값에 따라 멤버를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-123">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] orders the members of enabled attribute hierarchies during processing, and then stores the members by the value of the **OrderBy** property, such as by Name or Key.</span></span> <span data-ttu-id="c947b-124">정렬이 중요하지 않은 경우에는 이 속성의 값을 **False**로 설정하여 처리 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-124">If you do not care about ordering, you can increase processing performance by setting the value of this property to **False**.</span></span>

-   <span data-ttu-id="c947b-125">**AttributeHierarchyOptimizedState**</span><span class="sxs-lookup"><span data-stu-id="c947b-125">**AttributeHierarchyOptimizedState**</span></span>

     <span data-ttu-id="c947b-126">기본적으로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서는 처리하는 동안 활성화된 각 특성 계층의 인덱스를 만들어 쿼리 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-126">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates an index for each enabled attribute hierarchy during processing, to improve query performance.</span></span> <span data-ttu-id="c947b-127">특성 계층을 찾아볼 수 없도록 하려면 이 속성의 값을 **NotOptimized**로 설정하여 처리 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-127">If you do not plan to use an attribute hierarchy for browsing, you can increase processing performance by setting the value of this property to **NotOptimized**.</span></span> <span data-ttu-id="c947b-128">그러나 숨겨진 계층을 차원의 키 특성으로 사용할 경우 특성 멤버의 인덱스를 만들어도 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-128">However, if you use a hidden hierarchy as the key attribute for the dimension, creating an index of the attribute members will still improve performance.</span></span>

 <span data-ttu-id="c947b-129">특성 계층을 비활성화하면 이러한 속성이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-129">These properties do not apply if an attribute hierarchy is disabled.</span></span>

 <span data-ttu-id="c947b-130">이 항목의 태스크에서는 찾아보는 데 사용하지 않을 Employee 차원의 주민 등록 번호 및 그 밖의 특성을 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-130">In the tasks in this topic, you will disable social security numbers and other attributes in the Employee dimension that will not be used for browsing.</span></span> <span data-ttu-id="c947b-131">그런 다음 고객 이름과 우편 번호 특성 계층을 Customer 차원에서 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-131">You will then hide the customer name and postal code attribute hierarchies in the Customer dimension.</span></span> <span data-ttu-id="c947b-132">이러한 계층에 특성 멤버가 많으면 사용자 계층과 관계없이 이러한 계층을 찾아보는 데에 시간이 상당히 많이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-132">The large number of attribute members in these hierarchies will make browsing these hierarchies very slow independent of a user hierarchy.</span></span>

## <a name="setting-attribute-hierarchy-properties-in-the-employee-dimension"></a><span data-ttu-id="c947b-133">Employee 차원의 특성 계층 속성 설정</span><span class="sxs-lookup"><span data-stu-id="c947b-133">Setting Attribute Hierarchy Properties in the Employee Dimension</span></span>

1.  <span data-ttu-id="c947b-134">Employee 차원에 대한 차원 디자이너로 전환한 다음 **브라우저** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-134">Switch to Dimension Designer for the Employee dimension, and then click the **Browser** tab.</span></span>

2.  <span data-ttu-id="c947b-135">**계층** 목록에 다음 특성 계층이 나타나는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-135">Verify that the following attribute hierarchies appear in the **Hierarchy** list:</span></span>

    -   <span data-ttu-id="c947b-136">**기본 비율**</span><span class="sxs-lookup"><span data-stu-id="c947b-136">**Base Rate**</span></span>

    -   <span data-ttu-id="c947b-137">**생년월일**</span><span class="sxs-lookup"><span data-stu-id="c947b-137">**Birth Date**</span></span>

    -   <span data-ttu-id="c947b-138">**로그인 ID**</span><span class="sxs-lookup"><span data-stu-id="c947b-138">**Login ID**</span></span>

    -   <span data-ttu-id="c947b-139">**관리자 SSN**</span><span class="sxs-lookup"><span data-stu-id="c947b-139">**Manager SSN**</span></span>

    -   <span data-ttu-id="c947b-140">**SSN**</span><span class="sxs-lookup"><span data-stu-id="c947b-140">**SSN**</span></span>

3.  <span data-ttu-id="c947b-141">**차원 구조** 탭으로 전환한 다음 **특성** 창에서 다음 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-141">Switch to the **Dimension Structure** tab, and then select the following attributes in the **Attributes** pane.</span></span> <span data-ttu-id="c947b-142">CTRL 키를 누른 채 각 측정값을 클릭하면 여러 측정값을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-142">You can select multiple measures by clicking each while holding down the CTRL key:</span></span>

    -   <span data-ttu-id="c947b-143">**기본 비율**</span><span class="sxs-lookup"><span data-stu-id="c947b-143">**Base Rate**</span></span>

    -   <span data-ttu-id="c947b-144">**생년월일**</span><span class="sxs-lookup"><span data-stu-id="c947b-144">**Birth Date**</span></span>

    -   <span data-ttu-id="c947b-145">**로그인 ID**</span><span class="sxs-lookup"><span data-stu-id="c947b-145">**Login ID**</span></span>

    -   <span data-ttu-id="c947b-146">**관리자 SSN**</span><span class="sxs-lookup"><span data-stu-id="c947b-146">**Manager SSN**</span></span>

    -   <span data-ttu-id="c947b-147">**SSN**</span><span class="sxs-lookup"><span data-stu-id="c947b-147">**SSN**</span></span>

4.  <span data-ttu-id="c947b-148">속성 창에서 선택한 특성에 대해 **AttributeHierarchyEnabled** 속성 값을 **False** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-148">In the Properties window, set the value of the **AttributeHierarchyEnabled** property to **False** for the selected attributes.</span></span>

     <span data-ttu-id="c947b-149">**특성** 창에서는 각 특성에 대한 아이콘이 변경되어 해당 특성이 활성화되지 않은 상태임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-149">Notice in the **Attributes** pane that the icon for each attribute has changed to indicate that the attribute is not enabled.</span></span>

     <span data-ttu-id="c947b-150">다음 이미지에서는 선택한 특성에 대해 False로 설정된 **AttributeHierarchyEnabled** 속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-150">The following image shows the **AttributeHierarchyEnabled** property set to False for the selected attributes.</span></span>

     <span data-ttu-id="c947b-151">![AttributeHierarchyEnabled 속성이 False로 설정됨](../../2014/tutorials/media/l4-hierarchyenabled-1.gif "AttributeHierarchyEnabled 속성이 False로 설정됨")</span><span class="sxs-lookup"><span data-stu-id="c947b-151">![AttributeHierarchyEnabled property set to False](../../2014/tutorials/media/l4-hierarchyenabled-1.gif "AttributeHierarchyEnabled property set to False")</span></span>

5.  <span data-ttu-id="c947b-152">**빌드** 메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-152">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

6.  <span data-ttu-id="c947b-153">처리가 성공적으로 완료되면 **브라우저** 탭으로 전환하고 **다시 연결**을 클릭한 다음 수정한 특성 계층을 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-153">When processing has successfully completed, switch to the **Browser** tab, click **Reconnect**, and then try to browse the modified attribute hierarchies.</span></span>

     <span data-ttu-id="c947b-154">수정한 특성의 멤버는 **계층** 목록의 특성 계층에서 찾아볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-154">Notice that the members of the modified attributes are not available for browsing as attribute hierarchies in the **Hierarchy** list.</span></span> <span data-ttu-id="c947b-155">비활성화된 특성 계층 하나를 사용자 계층의 수준으로 추가하려고 하면 특성 계층을 활성화해야 사용자 정의 계층에 포함할 수 있다고 알리는 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-155">If you try to add one of the disabled attribute hierarchies as a level in a user hierarchy, you will receive an error notifying you that the attribute hierarchy must be enabled to participate in a user-defined hierarchy.</span></span>

## <a name="setting-attribute-hierarchy-properties-in-the-customer-dimension"></a><span data-ttu-id="c947b-156">Customer 차원의 특성 계층 속성 설정</span><span class="sxs-lookup"><span data-stu-id="c947b-156">Setting Attribute Hierarchy Properties in the Customer Dimension</span></span>

1.  <span data-ttu-id="c947b-157">Customer 차원에 대한 차원 디자이너로 전환한 다음 **브라우저** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-157">Switch to Dimension Designer for the Customer dimension, and then click the **Browser** tab.</span></span>

2.  <span data-ttu-id="c947b-158">**계층** 목록에 다음 특성 계층이 나타나는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-158">Verify that the following attribute hierarchies appear in the **Hierarchy** list:</span></span>

    -   <span data-ttu-id="c947b-159">**전체 이름**</span><span class="sxs-lookup"><span data-stu-id="c947b-159">**Full Name**</span></span>

    -   <span data-ttu-id="c947b-160">**우편 번호**</span><span class="sxs-lookup"><span data-stu-id="c947b-160">**Postal Code**</span></span>

3.  <span data-ttu-id="c947b-161">**차원 구조** 탭으로 전환한 다음 Ctrl 키를 사용하여 한 번에 여러 특성을 선택할 수 있으므로 **특성** 창에서 다음 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-161">Switch to the **Dimension Structure** tab, and then select the following attributes in the **Attributes** pane by using the CTRL key to select multiple attributes at the same time:</span></span>

    -   <span data-ttu-id="c947b-162">**전체 이름**</span><span class="sxs-lookup"><span data-stu-id="c947b-162">**Full Name**</span></span>

    -   <span data-ttu-id="c947b-163">**우편 번호**</span><span class="sxs-lookup"><span data-stu-id="c947b-163">**Postal Code**</span></span>

4.  <span data-ttu-id="c947b-164">속성 창에서 선택한 특성에 대해 **AttributeHierarchyVisible** 속성 값을 **False** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-164">In the Properties window, set the value of the **AttributeHierarchyVisible** property to **False** for the selected attributes.</span></span>

     <span data-ttu-id="c947b-165">이러한 특성 계층의 멤버는 팩트 데이터 차원 지정에 사용되므로 이 특성 계층의 멤버를 정렬하고 최적화하면 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-165">Because the members of these attribute hierarchies will be used for dimensioning fact data, ordering and optimizing the members of these attribute hierarchies will improve performance.</span></span> <span data-ttu-id="c947b-166">따라서 이러한 특성의 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-166">Therefore, the properties of these attributes should not be changed.</span></span>

     <span data-ttu-id="c947b-167">다음 이미지에서는 False로 설정된 **AttributeHierarchyVisible** 속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-167">The following image shows the **AttributeHierarchyVisible** property set to False.</span></span>

     <span data-ttu-id="c947b-168">![AttributeHierarchyVisible 속성이 False로 설정됨](../../2014/tutorials/media/l4-hierarchyvisible-1.gif "AttributeHierarchyVisible 속성이 False로 설정됨")</span><span class="sxs-lookup"><span data-stu-id="c947b-168">![AttributeHierarchyVisible property set to False](../../2014/tutorials/media/l4-hierarchyvisible-1.gif "AttributeHierarchyVisible property set to False")</span></span>

5.  <span data-ttu-id="c947b-169">**특성** 창의 **우편 번호** 특성을 **계층 및 수준** 창에 있는 **고객 지리** 사용자 계층의 **구/군/시** 수준 바로 아래로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-169">Drag the **Postal Code** attribute from the **Attributes** pane into the **Customer Geography** user hierarchy in the **Hierarchies and Levels** pane, immediately under the **City** level.</span></span>

     <span data-ttu-id="c947b-170">숨겨진 특성도 사용자 계층의 수준이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-170">Notice that a hidden attribute can still become a level in a user hierarchy.</span></span>

6.  <span data-ttu-id="c947b-171">**빌드** 메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-171">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

7.  <span data-ttu-id="c947b-172">배포가 성공적으로 완료되면 Customer 차원의 **브라우저** 탭으로 전환한 다음 **다시 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-172">When deployment has successfully completed, switch to the **Browser** tab for the Customer dimension, and then click **Reconnect**.</span></span>

8.  <span data-ttu-id="c947b-173">**계층** 목록에서 수정한 특성 계층을 선택해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-173">Try to select either of the modified attribute hierarchies from the **Hierarchy** list.</span></span>

     <span data-ttu-id="c947b-174">수정한 특성 계층은 **계층** 목록에 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-174">Notice that neither of the modified attribute hierarchies appears in the **Hierarchy** list.</span></span>

9. <span data-ttu-id="c947b-175">**계층** 목록에서 **고객 지리**를 선택한 다음 브라우저 창에서 각 수준을 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-175">In the **Hierarchy** list, select **Customer Geography**, and then browse each level in the browser pane.</span></span>

     <span data-ttu-id="c947b-176">숨겨진 수준인 **우편 번호** 와 **전체 이름**이 사용자 정의 계층에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c947b-176">Notice that the hidden levels, **Postal Code** and **Full Name**, are visible in the user-defined hierarchy.</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="c947b-177">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="c947b-177">Next Task in Lesson</span></span>
 [<span data-ttu-id="c947b-178">보조 특성을 기준으로 특성 멤버 정렬</span><span class="sxs-lookup"><span data-stu-id="c947b-178">Sorting Attribute Members Based on a Secondary Attribute</span></span>](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md)


