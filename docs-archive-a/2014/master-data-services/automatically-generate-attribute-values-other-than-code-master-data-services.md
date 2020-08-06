---
title: 코드 외의 특성 값 자동 생성(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b82f6f81-6e9c-4918-9ea9-4ab5f5d11b15
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8db6c89bdce2a11a5a54ed3a763a7bc41bd7f1be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659515"
---
# <a name="automatically-generate-attribute-values-other-than-code-master-data-services"></a><span data-ttu-id="f7894-102">코드 외의 특성 값 자동 생성(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f7894-102">Automatically Generate Attribute Values Other Than Code (Master Data Services)</span></span>
  <span data-ttu-id="f7894-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 비즈니스 규칙이 적용될 때마다 값으로 정수가 자동 할당되도록 하려면 엔터티의 특성 값에 대해 값을 자동으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], automatically generate values for an entity's attribute values when you want an integer to be automatically assigned as the value each time business rules are applied.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f7894-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="f7894-104">Prerequisites</span></span>  
 <span data-ttu-id="f7894-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="f7894-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="f7894-106">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="f7894-107">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-107">You must be a model administrator.</span></span> <span data-ttu-id="f7894-108">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7894-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="f7894-109">숫자 특성이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-109">A numeric attribute must exist.</span></span> <span data-ttu-id="f7894-110">자세한 내용은 [숫자 특성 만들기&#40;Master Data Services&#41;](../../2014/master-data-services/create-a-numeric-attribute-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7894-110">For more information, see [Create a Numeric Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-numeric-attribute-master-data-services.md).</span></span>  
  
### <a name="to-automatically-generate-an-attribute-value"></a><span data-ttu-id="f7894-111">특성 값을 자동으로 생성하려면</span><span class="sxs-lookup"><span data-stu-id="f7894-111">To automatically generate an attribute value</span></span>  
  
1.  <span data-ttu-id="f7894-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="f7894-113">메뉴 모음에서 **관리** 를 가리키고 **비즈니스 규칙**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-113">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="f7894-114">**비즈니스 규칙 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-114">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="f7894-115">**엔터티** 목록에서 엔터티를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-115">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="f7894-116">**멤버 유형** 목록에서 비즈니스 규칙을 적용할 멤버 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-116">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="f7894-117">**특성** 목록에서 기본값인 **모두**를 그대로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-117">From the **Attribute** list, leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="f7894-118">**비즈니스 규칙 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-118">Click **Add business rule**.</span></span>  
  
8.  <span data-ttu-id="f7894-119">**선택한 비즈니스 규칙 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-119">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="f7894-120">**구성 요소** 창에서 **동작** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-120">In the **Components** pane, expand the **Actions** node.</span></span>  
  
10. <span data-ttu-id="f7894-121">기본값 노드에서 **생성되는 값을 기본값으로 설정**을 클릭하고 **THEN** 창의 **동작** 레이블로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-121">In the Default Value node, click **defaults to a generated value** and drag it to the **THEN** pane's **Actions** label.</span></span>  
  
11. <span data-ttu-id="f7894-122">**특성** 창에서 생성할 값을 가진 특성을 클릭하고 이를 **동작 편집** 창의 **특성 선택** 레이블로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-122">In the **Attributes** pane, click the attribute with the value you want to generated and drag it to the **Edit Action** pane's **Select attribute** label.</span></span>  
  
12. <span data-ttu-id="f7894-123">**시작 값** 및 **증가값** 상자에 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-123">Type a value in the **Start with** and **Increment by** boxes.</span></span> <span data-ttu-id="f7894-124">멤버가 이미 있는 경우 가장 높은 기존 값을 기반으로 값이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-124">If members already exist, the value will be set based on the highest existing value.</span></span> <span data-ttu-id="f7894-125">예를 들어 가장 높은 기존 값이 299이고 **증가값**을 **1**로 설정하는 경우 다음 멤버의 값은 300으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-125">For example, if the highest existing value is 299 and you set **Increment by** to **1**, the next member's value will be set to 300.</span></span>  
  
13. <span data-ttu-id="f7894-126">**동작 편집** 창에서 **항목 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-126">In the **Edit Action** pane, click **Save item**.</span></span>  
  
14. <span data-ttu-id="f7894-127">**뒤로**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-127">Click **Back**.</span></span>  
  
15. <span data-ttu-id="f7894-128">필요에 따라 **비즈니스 규칙 유지 관리** 페이지에서 비즈니스 규칙을 포함하는 행에 대해 **이름**, **설명**또는 **알림** 열의 셀을 두 번 클릭하여 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-128">Optionally, on the **Business Rules Maintenance** page, for the row that contains your business rule, double-click a cell in the **Name**, **Description**, or **Notification** column to update the value.</span></span>  
  
16. <span data-ttu-id="f7894-129">**비즈니스 규칙 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-129">Click **Publish business rules**.</span></span>  
  
17. <span data-ttu-id="f7894-130">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-130">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="f7894-131">규칙의 상태가 **활성**으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7894-131">The rule's status changes to **Active**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f7894-132">다음 단계</span><span class="sxs-lookup"><span data-stu-id="f7894-132">Next Steps</span></span>  
  
-   [<span data-ttu-id="f7894-133">비즈니스 규칙에 대해 특정 멤버 유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f7894-133">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="f7894-134">비즈니스 규칙에 대해 버전 유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f7894-134">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="f7894-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7894-135">See Also</span></span>  
 <span data-ttu-id="f7894-136">[MDS(Master Data Services)&#41;&#40;자동 코드 만들기](../../2014/master-data-services/automatic-code-creation-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f7894-136">[Automatic Code Creation &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md) </span></span>  
 <span data-ttu-id="f7894-137">[비즈니스 규칙 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f7894-137">[Business Rules &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span></span>  
 [<span data-ttu-id="f7894-138">유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f7894-138">Validation &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-master-data-services.md)  
  
  
