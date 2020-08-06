---
title: 비즈니스 규칙 만들기 및 게시(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], creating
- creating business rules [Master Data Services]
ms.assetid: 6961d636-4d69-468e-81f7-8d0be6a4a039
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4dfca5613a1f328e02b3fd2c7337885a23889207
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659507"
---
# <a name="create-and-publish-a-business-rule-master-data-services"></a><span data-ttu-id="e7c47-102">비즈니스 규칙 만들기 및 게시(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e7c47-102">Create and Publish a Business Rule (Master Data Services)</span></span>
  <span data-ttu-id="e7c47-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 마스터 데이터의 정확성 유지를 위한 비즈니스 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a business rule to ensure the accuracy of your master data.</span></span> <span data-ttu-id="e7c47-104">규칙을 만든 후 게시해야 데이터에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-104">After you create a rule, you must publish it before you can apply it to data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e7c47-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="e7c47-105">Prerequisites</span></span>  
 <span data-ttu-id="e7c47-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="e7c47-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="e7c47-107">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="e7c47-108">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-108">You must be a model administrator.</span></span> <span data-ttu-id="e7c47-109">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e7c47-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-and-publish-a-business-rule"></a><span data-ttu-id="e7c47-110">비즈니스 규칙을 만들어 게시하려면</span><span class="sxs-lookup"><span data-stu-id="e7c47-110">To create and publish a business rule</span></span>  
  
1.  <span data-ttu-id="e7c47-111">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="e7c47-112">메뉴 모음에서 **관리** 를 가리키고 **비즈니스 규칙**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-112">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="e7c47-113">**비즈니스 규칙 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-113">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="e7c47-114">**엔터티** 목록에서 엔터티를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-114">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="e7c47-115">**멤버 유형** 목록에서 비즈니스 규칙을 적용할 멤버 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-115">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="e7c47-116">**특성** 목록에서 특성을 선택하거나 기본값인 **모두**를 그대로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-116">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="e7c47-117">**비즈니스 규칙 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-117">Click **Add business rule**.</span></span>  
  
8.  <span data-ttu-id="e7c47-118">**선택한 비즈니스 규칙 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-118">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="e7c47-119">**구성 요소** 창에서 **조건** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-119">In the **Components** pane, expand the **Conditions** node.</span></span>  
  
10. <span data-ttu-id="e7c47-120">조건을 클릭 하 고 **IF** 창의 **조건** 레이블로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-120">Click a condition and drag it to the **IF** pane's **Conditions** label.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="e7c47-121">마우스 오른쪽 단추를 클릭 하 고 **삭제**를 선택 하 여 비즈니스 규칙에서 항목을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-121">You can delete items from your business rule by right-clicking and choosing **Delete**.</span></span>  
  
11. <span data-ttu-id="e7c47-122">**특성** 창에서 특성을 클릭 하 고 **조건 편집** 창의 **특성 선택** 레이블로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-122">In the **Attributes** pane, click an attribute and drag it to the **Edit Condition** pane's **Select attribute** label.</span></span>  
  
12. <span data-ttu-id="e7c47-123">**조건 편집** 창에서 모든 필수 필드를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-123">In the **Edit Condition** pane, complete any required fields.</span></span>  
  
13. <span data-ttu-id="e7c47-124">**조건 편집** 창에서 **항목 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-124">In the **Edit Condition** pane, click **Save item**.</span></span>  
  
14. <span data-ttu-id="e7c47-125">**구성 요소** 창에서 **동작** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-125">In the **Components** pane, expand the **Actions** node.</span></span>  
  
15. <span data-ttu-id="e7c47-126">동작을 클릭하고 **THEN** 창의 **동작** 레이블로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-126">Click an action and drag it to the **THEN** pane's **Action** label.</span></span>  
  
16. <span data-ttu-id="e7c47-127">**특성** 창에서 특성을 클릭하고 **동작 편집** 창의 **특성 선택** 레이블로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-127">In the **Attributes** pane, click an attribute and drag it to the **Edit Action** pane's **Select attribute** label.</span></span>  
  
17. <span data-ttu-id="e7c47-128">**동작 편집** 창에서 모든 필수 필드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-128">In the **Edit Action** pane, complete any required fields.</span></span>  
  
18. <span data-ttu-id="e7c47-129">**동작 편집** 창에서 **항목 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-129">In the **Edit Action** pane, click **Save item**.</span></span>  
  
19. <span data-ttu-id="e7c47-130">필요에 따라 여러 조건을 규칙에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-130">Optionally, add multiple conditions to the rule.</span></span> <span data-ttu-id="e7c47-131">자세한 내용은 [비즈니스 규칙에 여러 조건 추가&#40;Master Data Services&#41;](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e7c47-131">For more information, see [Add Multiple Conditions to a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md).</span></span>  
  
20. <span data-ttu-id="e7c47-132">**뒤로**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-132">Click **Back**.</span></span>  
  
21. <span data-ttu-id="e7c47-133">필요에 따라 **비즈니스 규칙 유지 관리** 페이지에서 비즈니스 규칙을 포함하는 행에 대해 **이름**, **설명**또는 **알림** 열의 셀을 두 번 클릭하여 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-133">Optionally, on the **Business Rules Maintenance** page, for the row that contains your business rule, double-click a cell in the **Name**, **Description**, or **Notification** column to update the value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e7c47-134">유효성 검사 동작을 포함하는 규칙에 대해서만 알림이 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-134">Notifications are sent only for rules that include a validation action.</span></span>  
  
22. <span data-ttu-id="e7c47-135">**비즈니스 규칙 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-135">Click **Publish business rules**.</span></span>  
  
23. <span data-ttu-id="e7c47-136">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-136">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="e7c47-137">규칙의 상태가 **활성**으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-137">The rule's status changes to **Active**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e7c47-138">다음 단계</span><span class="sxs-lookup"><span data-stu-id="e7c47-138">Next Steps</span></span>  
  
-   <span data-ttu-id="e7c47-139">다음 절차 중 하나를 수행하여 비즈니스 규칙을 데이터에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c47-139">Apply business rules to data by following one of these procedures:</span></span>  
  
    -   [<span data-ttu-id="e7c47-140">비즈니스 규칙에 대해 특정 멤버 유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e7c47-140">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [<span data-ttu-id="e7c47-141">비즈니스 규칙에 대해 버전 유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e7c47-141">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="e7c47-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e7c47-142">See Also</span></span>  
 <span data-ttu-id="e7c47-143">[알림을 보내도록 비즈니스 규칙 구성 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="e7c47-143">[Configure Business Rules to Send Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md) </span></span>  
 <span data-ttu-id="e7c47-144">[비즈니스 규칙 이름 &#40;MDS(Master Data Services)&#41;변경](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="e7c47-144">[Change a Business Rule Name &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md) </span></span>  
 [<span data-ttu-id="e7c47-145">비즈니스 규칙에 여러 조건 추가&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e7c47-145">Add Multiple Conditions to a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)  
  
  
