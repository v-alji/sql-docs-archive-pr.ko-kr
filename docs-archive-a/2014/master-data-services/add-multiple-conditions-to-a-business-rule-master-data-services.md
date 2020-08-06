---
title: 비즈니스 규칙에 여러 조건 추가(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], multiple conditions
ms.assetid: 5f0f6958-6cf2-444b-bdcd-05b887637a0b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c62b8dfa4f459958d12bd384b85aa74bef382b21
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652891"
---
# <a name="add-multiple-conditions-to-a-business-rule-master-data-services"></a><span data-ttu-id="d6999-102">비즈니스 규칙에 여러 조건 추가(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d6999-102">Add Multiple Conditions to a Business Rule (Master Data Services)</span></span>
  <span data-ttu-id="d6999-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 더 복잡한 규칙을 원할 경우 여러 **AND** 또는 **OR** 조건을 비즈니스 규칙에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], add multiple **AND** or **OR** conditions to a business rule when you want a more complex rule.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6999-104">**OR** 연산자를 사용하는 비즈니스 규칙을 만드는 경우 개별적으로 평가할 수 있는 각 조건 문에 대해 개별 규칙을 만드는 것을 고려해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="d6999-104">If you create a business rule that uses the **OR** operator, consider creating a separate rule for each conditional statement that can be evaluated independently.</span></span> <span data-ttu-id="d6999-105">그런 다음 필요에 따라 규칙을 제외시키면 유연성이 향상되고 더 쉽게 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-105">You can then exclude rules as needed, providing more flexibility and easier troubleshooting.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d6999-106">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="d6999-106">Prerequisites</span></span>  
 <span data-ttu-id="d6999-107">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="d6999-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d6999-108">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="d6999-109">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-109">You must be a model administrator.</span></span> <span data-ttu-id="d6999-110">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d6999-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="d6999-111">비즈니스 규칙이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-111">A business rule must exist.</span></span> <span data-ttu-id="d6999-112">자세한 내용은 [비즈니스 규칙 만들기 및 게시&#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6999-112">For more information, see [Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).</span></span>  
  
### <a name="to-add-multiple-conditions-to-a-business-rule"></a><span data-ttu-id="d6999-113">여러 조건을 비즈니스 규칙에 추가하려면</span><span class="sxs-lookup"><span data-stu-id="d6999-113">To add multiple conditions to a business rule</span></span>  
  
1.  <span data-ttu-id="d6999-114">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="d6999-115">메뉴 모음에서 **관리** 를 가리키고 **비즈니스 규칙**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-115">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="d6999-116">**비즈니스 규칙 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-116">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="d6999-117">**엔터티** 목록에서 엔터티를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-117">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="d6999-118">**멤버 유형** 목록에서 멤버 유형을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-118">From the **Member Type** list, select a type of member.</span></span>  
  
6.  <span data-ttu-id="d6999-119">**특성** 목록에서 특성을 선택하거나 기본값인 **모두**를 그대로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-119">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="d6999-120">편집할 비즈니스 규칙 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-120">Click the row for the business rule you want to edit.</span></span>  
  
8.  <span data-ttu-id="d6999-121">**선택한 비즈니스 규칙 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-121">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="d6999-122">**구성 요소** 창에서 **논리 연산자** 노드를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-122">In the **Components** pane, expand the **Logical Operators** node.</span></span>  
  
10. <span data-ttu-id="d6999-123">**And** 또는 **or** 를 클릭 하 고 **IF** 창의 **및** 레이블로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-123">Click **AND** or **OR** and drag it to the **IF** pane's **AND** label.</span></span>  
  
11. <span data-ttu-id="d6999-124">**구성 요소** 창에서 **조건** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-124">In the **Components** pane, expand the **Conditions** node.</span></span>  
  
12. <span data-ttu-id="d6999-125">조건을 클릭 하 고 **IF** 창으로 끌어 10 단계에서 **and** 또는 **or** 레이블로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-125">Click a condition and drag it to **IF** pane, to the **AND** or **OR** label from step 10.</span></span>  
  
13. <span data-ttu-id="d6999-126">**특성** 창에서 특성을 클릭 하 고 **조건 편집** 창의 **특성 선택** 레이블로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-126">In the **Attributes** pane, click an attribute and drag it to the **Edit Condition** pane's **Select attribute** label.</span></span>  
  
14. <span data-ttu-id="d6999-127">**조건 편집** 창에서 모든 필수 필드를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-127">In the **Edit Condition** pane, complete any required fields.</span></span>  
  
15. <span data-ttu-id="d6999-128">**조건 편집** 창에서 **항목 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-128">In the **Edit Condition** pane, click **Save item**.</span></span>  
  
16. <span data-ttu-id="d6999-129">필요에 따라 추가 조건을 추가 하려면 **구성 요소** 창에서 **and** 또는 **or** 를 **IF** 창에서 임의의 **and** 또는 **or** 로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-129">Optionally, to add more conditions, from the **Components** pane, drag **AND** or **OR** to any **AND** or **OR** in the **IF** pane.</span></span> <span data-ttu-id="d6999-130">그런 다음 13-15단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-130">Then follow steps 13-15.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="d6999-131">조건을 삭제 하려면 조건 이름을 클릭 하 고 **조건 편집** 창에서 **항목 삭제**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6999-131">To delete a condition, click the name of the condition and in the **Edit Condition** pane, click **Delete item**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6999-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d6999-132">See Also</span></span>  
 <span data-ttu-id="d6999-133">[비즈니스 규칙 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d6999-133">[Business Rules &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span></span>  
 <span data-ttu-id="d6999-134">[비즈니스 규칙 이름 &#40;MDS(Master Data Services)&#41;변경](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d6999-134">[Change a Business Rule Name &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md) </span></span>  
 [<span data-ttu-id="d6999-135">알림을 보내도록 비즈니스 규칙 구성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d6999-135">Configure Business Rules to Send Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
