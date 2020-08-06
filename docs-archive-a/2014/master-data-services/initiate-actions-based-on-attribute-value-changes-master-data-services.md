---
title: 특성 값 변경 기반 동작 시작(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], tracking attribute changes
- change tracking groups [Master Data Services], initiating actions
ms.assetid: 5e4402ce-31db-4774-a2a1-552335f87693
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 50931b9f9c4bd5d08596d485ba695143b9c6594e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729552"
---
# <a name="initiate-actions-based-on-attribute-value-changes-master-data-services"></a><span data-ttu-id="6790f-102">특성 값 변경 기반 동작 시작(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="6790f-102">Initiate Actions Based on Attribute Value Changes (Master Data Services)</span></span>
  <span data-ttu-id="6790f-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 특성 값 변경을 기반으로 동작을 시작하는 비즈니스 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a business rule to initiate actions based on changes to attribute values.</span></span> <span data-ttu-id="6790f-104">예를 들어, 특정 특성 값이 변경될 때 값을 변경하거나 알림을 보내거나 외부 워크플로를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-104">For example, when a specific attribute value changes, you may want to change a value, send a notification, or start an external workflow.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6790f-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="6790f-105">Prerequisites</span></span>  
 <span data-ttu-id="6790f-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="6790f-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="6790f-107">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="6790f-108">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-108">You must be a model administrator.</span></span> <span data-ttu-id="6790f-109">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6790f-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="6790f-110">특성이 변경 내용 추적 그룹 안에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-110">Your attributes must be in a change tracking group.</span></span> <span data-ttu-id="6790f-111">자세한 내용은 [변경 내용 추적 그룹에 특성 추가&#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6790f-111">See [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) for more information.</span></span>  
  
### <a name="to-create-a-business-rule-to-initiate-actions-based-on-attribute-value-changes"></a><span data-ttu-id="6790f-112">특성 값 변경을 기반으로 하는 동작을 시작하는 비즈니스 규칙을 만들려면</span><span class="sxs-lookup"><span data-stu-id="6790f-112">To create a business rule to initiate actions based on attribute value changes</span></span>  
  
1.  <span data-ttu-id="6790f-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="6790f-114">메뉴 모음에서 **관리** 를 가리키고 **비즈니스 규칙**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-114">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="6790f-115">**비즈니스 규칙 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-115">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="6790f-116">**엔터티** 목록에서 엔터티를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-116">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="6790f-117">**멤버 유형** 목록에서 비즈니스 규칙을 적용할 멤버 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-117">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="6790f-118">**특성** 목록에서 특성을 선택하거나 기본값인 **모두**를 그대로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-118">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="6790f-119">**비즈니스 규칙 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-119">Click **Add business rule**.</span></span>  
  
8.  <span data-ttu-id="6790f-120">**선택한 비즈니스 규칙 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-120">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="6790f-121">**구성 요소** 창에서 **조건** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-121">In the **Components** pane, expand the **Conditions** node.</span></span>  
  
10. <span data-ttu-id="6790f-122">**값 비교** 노드 아래에서 **이(가) 변경된 경우** 를 **IF** 창의 **조건** 레이블로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-122">Under the **Value comparison** node, drag **has changed** to the **IF** pane's **Conditions** label.</span></span>  
  
11. <span data-ttu-id="6790f-123">**특성** 창에서 특성을 클릭 하 고 **조건 편집** 창의 **특성 선택** 레이블로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-123">In the **Attributes** pane, click an attribute and drag it to the **Edit Condition** pane's **Select attribute** label.</span></span> <span data-ttu-id="6790f-124">이 특성은 규칙에 아무 영향도 주지 않으므로 사용할 수 있는 모든 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-124">This attribute has no effect on the rule, so select any available attribute.</span></span>  
  
12. <span data-ttu-id="6790f-125">**조건 편집** 창의 **변경 내용 추적 그룹** 상자에서 필수 구성 요소의 일부로 할당한 변경 내용 추적 그룹의 번호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-125">In the **Edit Condition** pane, in the **Change tracking group** box, type the number of the change tracking group that you assigned as part of the prerequisites.</span></span>  
  
13. <span data-ttu-id="6790f-126">**조건 편집** 창에서 **항목 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-126">In the **Edit Condition** pane, click **Save item**.</span></span>  
  
14. <span data-ttu-id="6790f-127">**구성 요소** 창에서 **동작** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-127">In the **Components** pane, expand the **Actions** node.</span></span>  
  
15. <span data-ttu-id="6790f-128">동작을 클릭하고 **THEN** 창의 **동작** 레이블로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-128">Click an action and drag it to the **THEN** pane's **Action** label.</span></span>  
  
16. <span data-ttu-id="6790f-129">**특성** 창에서 특성을 클릭하고 **동작 편집** 창의 **특성 선택** 레이블로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-129">In the **Attributes** pane, click an attribute and drag it to the **Edit Action** pane's **Select attribute** label.</span></span>  
  
17. <span data-ttu-id="6790f-130">**동작 편집** 창에서 모든 필수 필드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-130">In the **Edit Action** pane, complete any required fields.</span></span>  
  
18. <span data-ttu-id="6790f-131">**동작 편집** 창에서 **항목 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-131">In the **Edit Action** pane, click **Save item**.</span></span>  
  
19. <span data-ttu-id="6790f-132">**뒤로**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-132">Click **Back**.</span></span>  
  
20. <span data-ttu-id="6790f-133">필요에 따라 **비즈니스 규칙 유지 관리** 페이지에서 비즈니스 규칙을 포함하는 행에 대해 **이름**, **설명**또는 **알림** 열의 셀을 두 번 클릭하여 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-133">Optionally, on the **Business Rules Maintenance** page, for the row that contains your business rule, double-click a cell in the **Name**, **Description**, or **Notification** column to update the value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6790f-134">유효성 검사 동작을 포함하는 규칙에 대해서만 알림이 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-134">Notifications are sent only for rules that include a validation action.</span></span>  
  
21. <span data-ttu-id="6790f-135">**비즈니스 규칙 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-135">Click **Publish business rules**.</span></span>  
  
22. <span data-ttu-id="6790f-136">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-136">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="6790f-137">규칙의 상태가 **활성**으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-137">The rule's status changes to **Active**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6790f-138">다음 단계</span><span class="sxs-lookup"><span data-stu-id="6790f-138">Next Steps</span></span>  
  
-   <span data-ttu-id="6790f-139">다음 절차 중 하나를 수행하여 비즈니스 규칙을 데이터에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="6790f-139">Apply business rules to data by following one of these procedures:</span></span>  
  
    -   [<span data-ttu-id="6790f-140">비즈니스 규칙에 대해 특정 멤버 유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6790f-140">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [<span data-ttu-id="6790f-141">비즈니스 규칙에 대해 버전 유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6790f-141">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="6790f-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6790f-142">See Also</span></span>  
 <span data-ttu-id="6790f-143">[특성을 변경 내용 추적 그룹 &#40;MDS(Master Data Services)에 추가&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="6790f-143">[Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) </span></span>  
 [<span data-ttu-id="6790f-144">비즈니스 규칙&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6790f-144">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
