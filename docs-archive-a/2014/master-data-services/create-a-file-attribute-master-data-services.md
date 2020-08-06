---
title: 파일 특성 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating file attributes [Master Data Services]
- attributes [Master Data Services], creating file attributes
ms.assetid: d224886b-2ef1-4658-8b01-2213cc4b8df6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f4f6e2f10a830d089d1d217f7cf54d0b8557add9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647729"
---
# <a name="create-a-file-attribute-master-data-services"></a><span data-ttu-id="d5701-102">파일 특성 만들기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d5701-102">Create a File Attribute (Master Data Services)</span></span>
  <span data-ttu-id="d5701-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 특성 값을 파일로 채우려면 파일 특성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a file attribute to populate attribute values with files.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d5701-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="d5701-104">Prerequisites</span></span>  
 <span data-ttu-id="d5701-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="d5701-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d5701-106">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="d5701-107">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-107">You must be a model administrator.</span></span> <span data-ttu-id="d5701-108">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d5701-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="d5701-109">해당 특성을 만들 엔터티가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-109">An entity must exist to create the attribute for.</span></span> <span data-ttu-id="d5701-110">자세한 내용은 [&#41;MDS(Master Data Services) 엔터티 &#40;만들기 ](../../2014/master-data-services/create-an-entity-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d5701-110">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-file-attribute"></a><span data-ttu-id="d5701-111">파일 특성을 만들려면</span><span class="sxs-lookup"><span data-stu-id="d5701-111">To create a file attribute</span></span>  
  
1.  <span data-ttu-id="d5701-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="d5701-113">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **엔터티**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="d5701-114">**엔터티 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="d5701-115">해당 특성을 만들려는 엔터티의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-115">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="d5701-116">**선택한 엔터티 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-116">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="d5701-117">**엔터티 편집** 페이지에서</span><span class="sxs-lookup"><span data-stu-id="d5701-117">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="d5701-118">리프 멤버에 대한 특성일 경우 **리프 멤버 특성** 창에서 **리프 특성 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-118">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="d5701-119">통합 멤버에 대한 특성일 경우 **통합 멤버 특성** 창에서 **통합 특성 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-119">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="d5701-120">컬렉션에 대한 특성일 경우 **컬렉션 특성** 창에서 **컬렉션 특성 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-120">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="d5701-121">**특성 추가** 페이지에서 **파일** 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-121">On the **Add Attribute** page, select the **File** option.</span></span>  
  
8.  <span data-ttu-id="d5701-122">**이름** 상자에 특성의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-122">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="d5701-123">특성 이름으로 사용 하지 않아야 하는 단어의 목록을 보려면 [예약어 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/reserved-words-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d5701-123">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="d5701-124">**탐색기** 표에 표시할 특성 열의 너비를 **표시 픽셀 폭** 상자에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-124">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="d5701-125">**파일 확장명** 목록에서 사용자가 업로드할 수 있는 파일 형식을 하나 이상 선택 하거나 기본값 (\*. \* )을 그대로 사용 하 여 모든 파일 형식을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-125">From the **File extension** list, select one or more file types that a user can upload, or leave the default (\*.\*) to allow all file types.</span></span>  
  
11. <span data-ttu-id="d5701-126">또는 특성 그룹의 변경 내용을 추적하려면 **변경 내용 추적 설정** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-126">Optionally, select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="d5701-127">자세한 내용은 [변경 내용 추적 그룹에 특성 추가&#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5701-127">For more information, see [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).</span></span>  
  
12. <span data-ttu-id="d5701-128">**특성 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-128">Click **Save attribute**.</span></span>  
  
13. <span data-ttu-id="d5701-129">**엔터티 유지 관리** 페이지에서 **엔터티 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d5701-129">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5701-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d5701-130">See Also</span></span>  
 <span data-ttu-id="d5701-131">[특성 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d5701-131">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="d5701-132">[특성 이름을 MDS(Master Data Services) &#40;변경&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d5701-132">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 <span data-ttu-id="d5701-133">[도메인 기반 특성 &#40;MDS(Master Data Services)를 만듭니다&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d5701-133">[Create a Domain-Based Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="d5701-134">텍스트 특성 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d5701-134">Create a Text Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)  
  
  
