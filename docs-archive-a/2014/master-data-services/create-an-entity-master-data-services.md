---
title: 엔터티 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], creating
- creating entities [Master Data Services]
ms.assetid: d9a6a51e-7b53-4785-a118-3baeb7ca2d48
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7cefdedd07ee248f12b3b17337878934a2b1aa84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660655"
---
# <a name="create-an-entity-master-data-services"></a><span data-ttu-id="733f4-102">엔터티 만들기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="733f4-102">Create an Entity (Master Data Services)</span></span>
  <span data-ttu-id="733f4-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 멤버와 해당 특성을 포함할 엔터티를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create an entity to contain members and their attributes.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="733f4-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="733f4-104">Prerequisites</span></span>  
 <span data-ttu-id="733f4-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="733f4-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="733f4-106">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="733f4-107">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-107">You must be a model administrator.</span></span> <span data-ttu-id="733f4-108">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="733f4-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="733f4-109">모델이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-109">A model must exist.</span></span> <span data-ttu-id="733f4-110">자세한 내용은 [모델 만들기&#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="733f4-110">For more information, see [Create a Model &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md).</span></span>  
  
### <a name="to-create-an-entity"></a><span data-ttu-id="733f4-111">엔터티를 만들려면</span><span class="sxs-lookup"><span data-stu-id="733f4-111">To create an entity</span></span>  
  
1.  <span data-ttu-id="733f4-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="733f4-113">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **엔터티**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="733f4-114">**엔터티 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="733f4-115">**엔터티 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-115">Click **Add entity**.</span></span>  
  
5.  <span data-ttu-id="733f4-116">**엔터티 이름** 상자에 엔터티의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-116">In the **Entity name** box, type the name of the entity.</span></span>  
  
6.  <span data-ttu-id="733f4-117">준비 테이블 **이름** 상자에 준비 테이블의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-117">In the **Name for staging tables** box, type a name for the staging table.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="733f4-118">모델 이름을 준비 테이블의 일부로 사용합니다(예: *Modelname_Entityname*).</span><span class="sxs-lookup"><span data-stu-id="733f4-118">Use the model name as part of the staging table name, for example *Modelname_Entityname*.</span></span> <span data-ttu-id="733f4-119">그러면 데이터베이스에서 테이블을 더 쉽게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-119">This makes the tables easier to find in the database.</span></span> <span data-ttu-id="733f4-120">준비 테이블에 대 한 자세한 내용은 [데이터 가져오기 &#40;MDS(Master Data Services)&#41;](overview-importing-data-from-tables-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="733f4-120">For more information about the staging tables, see [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).</span></span>  
  
7.  <span data-ttu-id="733f4-121">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-121">Optional.</span></span> <span data-ttu-id="733f4-122">**코드 값 자동으로 만들기** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-122">Select the **Create Code values automatically** check box.</span></span> <span data-ttu-id="733f4-123">자세한 내용은 [MDS(Master Data Services)&#41;&#40;자동 코드 만들기 ](../../2014/master-data-services/automatic-code-creation-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="733f4-123">For more information, see [Automatic Code Creation &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md).</span></span>  
  
8.  <span data-ttu-id="733f4-124">**명시적 계층 및 컬렉션 사용** 목록에서 다음 옵션 중 하나를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-124">From the **Enable explicit hierarchies and collections** list, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="733f4-125">**아니요**.</span><span class="sxs-lookup"><span data-stu-id="733f4-125">**No**.</span></span> <span data-ttu-id="733f4-126">명시적 계층 및 컬렉션에 대해 엔터티를 사용할 필요가 없으면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-126">Select this option if you do not need to enable the entity for explicit hierarchies and collections.</span></span> <span data-ttu-id="733f4-127">필요할 경우 나중에 이 옵션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-127">You can change this later if needed.</span></span>  
  
    -   <span data-ttu-id="733f4-128">**예**.</span><span class="sxs-lookup"><span data-stu-id="733f4-128">**Yes**.</span></span> <span data-ttu-id="733f4-129">명시적 계층 및 컬렉션에 대해 엔터티를 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-129">Select this option when you want to enable the entity for explicit hierarchies and collections.</span></span> <span data-ttu-id="733f4-130">**명시적 계층 이름** 상자에 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-130">In the **Explicit hierarchy name** box, type a name.</span></span> <span data-ttu-id="733f4-131">필요에 따라 **필수 계층 (모든 리프 멤버 포함)** 을 선택 하 여 명시적 계층을 필수 계층으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-131">Optionally, select **Mandatory hierarchy (all leaf members are included** to make the explicit hierarchy a mandatory hierarchy.</span></span>  
  
9. <span data-ttu-id="733f4-132">**엔터티 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="733f4-132">Click **Save entity**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="733f4-133">다음 단계</span><span class="sxs-lookup"><span data-stu-id="733f4-133">Next Steps</span></span>  
  
-   [<span data-ttu-id="733f4-134">텍스트 특성 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="733f4-134">Create a Text Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)  
  
-   [<span data-ttu-id="733f4-135">도메인 기반 특성 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="733f4-135">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
-   [<span data-ttu-id="733f4-136">파일 특성 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="733f4-136">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="733f4-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="733f4-137">See Also</span></span>  
 <span data-ttu-id="733f4-138">[엔터티 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/entities-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="733f4-138">[Entities &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md) </span></span>  
 <span data-ttu-id="733f4-139">[명시적 계층 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="733f4-139">[Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span></span>  
 <span data-ttu-id="733f4-140">[엔터티 이름 &#40;MDS(Master Data Services)&#41;변경](edit-an-entity-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="733f4-140">[Change an Entity Name &#40;Master Data Services&#41;](edit-an-entity-master-data-services.md) </span></span>  
 [<span data-ttu-id="733f4-141">엔터티 삭제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="733f4-141">Delete an Entity &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-entity-master-data-services.md)  
  
  
