---
title: 특성 값 요구(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], requiring attribute values
- attributes [Master Data Services], requiring values
ms.assetid: a360ef13-0c34-43b8-a87e-2f5d8732d30e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 42b412fc42138c5e186c6c7ad42373f20e35f3cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648417"
---
# <a name="require-attribute-values-master-data-services"></a><span data-ttu-id="879a9-102">특성 값 요구(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="879a9-102">Require Attribute Values (Master Data Services)</span></span>
  <span data-ttu-id="879a9-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 마스터 데이터를 완전한 상태로 유지하려면 특성 값을 요구합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], require attribute values when you want to ensure your master data is complete.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="879a9-104">도메인 기반 특성 값이 없는 멤버는 이러한 관계를 기반으로 하는 파생 계층에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-104">Members that are missing domain-based attribute values are not displayed in derived hierarchies that are based on those relationships.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="879a9-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="879a9-105">Prerequisites</span></span>  
 <span data-ttu-id="879a9-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="879a9-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="879a9-107">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="879a9-108">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-108">You must be a model administrator.</span></span> <span data-ttu-id="879a9-109">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="879a9-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-require-attribute-values"></a><span data-ttu-id="879a9-110">특성 값 요청</span><span class="sxs-lookup"><span data-stu-id="879a9-110">To require attribute values</span></span>  
  
1.  <span data-ttu-id="879a9-111">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="879a9-112">메뉴 모음에서 **관리** 를 가리키고 **비즈니스 규칙**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-112">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="879a9-113">**비즈니스 규칙 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-113">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="879a9-114">**엔터티** 목록에서 엔터티를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-114">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="879a9-115">**멤버 유형** 목록에서 비즈니스 규칙을 적용할 멤버 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-115">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="879a9-116">**특성** 목록에서 특성을 선택하거나 기본값인 **모두**를 그대로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-116">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="879a9-117">**비즈니스 규칙 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-117">Click **Add business rule**.</span></span>  
  
8.  <span data-ttu-id="879a9-118">**선택한 비즈니스 규칙 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-118">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="879a9-119">**구성 요소** 창에서 **동작** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-119">In the **Components** pane, expand the **Actions** node.</span></span>  
  
10. <span data-ttu-id="879a9-120">**필수를** 클릭 하 고 **THEN** 창의 **동작** 레이블로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-120">Click **is required** and drag it to the **THEN** pane's **Action** label.</span></span>  
  
11. <span data-ttu-id="879a9-121">**특성** 창에서 특성을 클릭하고 **동작 편집** 창의 **특성 선택** 레이블로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-121">In the **Attributes** pane, click an attribute and drag it to the **Edit Action** pane's **Select attribute** label.</span></span>  
  
12. <span data-ttu-id="879a9-122">**동작 편집** 창에서 **항목 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-122">In the **Edit Action** pane, click **Save item**.</span></span>  
  
13. <span data-ttu-id="879a9-123">**뒤로**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-123">Click **Back**.</span></span>  
  
14. <span data-ttu-id="879a9-124">필요에 따라 **비즈니스 규칙 유지 관리** 페이지에서 비즈니스 규칙을 포함하는 행에 대해 **이름**, **설명**또는 **알림** 열의 셀을 두 번 클릭하여 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-124">Optionally, on the **Business Rules Maintenance** page, for the row that contains your business rule, double-click a cell in the **Name**, **Description**, or **Notification** column to update the value.</span></span>  
  
15. <span data-ttu-id="879a9-125">**비즈니스 규칙 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-125">Click **Publish business rules**.</span></span>  
  
16. <span data-ttu-id="879a9-126">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-126">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="879a9-127">규칙의 상태가 **활성**으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-127">The rule's status changes to **Active**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="879a9-128">다음 단계</span><span class="sxs-lookup"><span data-stu-id="879a9-128">Next Steps</span></span>  
  
-   <span data-ttu-id="879a9-129">다음 절차 중 하나를 수행하여 비즈니스 규칙을 데이터에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="879a9-129">Apply business rules to data by following one of these procedures:</span></span>  
  
    -   [<span data-ttu-id="879a9-130">비즈니스 규칙에 대해 특정 멤버 유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="879a9-130">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [<span data-ttu-id="879a9-131">비즈니스 규칙에 대해 버전 유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="879a9-131">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="879a9-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="879a9-132">See Also</span></span>  
 <span data-ttu-id="879a9-133">[비즈니스 규칙 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="879a9-133">[Business Rules &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span></span>  
 [<span data-ttu-id="879a9-134">파생 계층&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="879a9-134">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
