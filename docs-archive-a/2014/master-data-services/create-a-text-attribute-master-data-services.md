---
title: 텍스트 특성 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], creating text attributes
- creating text attributes [Master Data Services]
ms.assetid: cd8b57de-364d-42a3-9273-c1c6b992bb40
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c0f44e0e6c6e3df49b6a3746648ee46a23a7a3ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661704"
---
# <a name="create-a-text-attribute-master-data-services"></a><span data-ttu-id="c38af-102">텍스트 특성 만들기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="c38af-102">Create a Text Attribute (Master Data Services)</span></span>
  <span data-ttu-id="c38af-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 사용자가 텍스트 문자열을 특성 값으로 입력할 수 있도록 하려면 텍스트 특성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a text attribute when you want users to enter a text string as an attribute value.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c38af-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c38af-104">Prerequisites</span></span>  
 <span data-ttu-id="c38af-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="c38af-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="c38af-106">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="c38af-107">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-107">You must be a model administrator.</span></span> <span data-ttu-id="c38af-108">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c38af-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="c38af-109">해당 특성을 만들 엔터티가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-109">An entity must exist to create the attribute for.</span></span> <span data-ttu-id="c38af-110">자세한 내용은 [&#41;MDS(Master Data Services) 엔터티 &#40;만들기 ](../../2014/master-data-services/create-an-entity-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c38af-110">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-text-attribute"></a><span data-ttu-id="c38af-111">텍스트 특성을 만들려면</span><span class="sxs-lookup"><span data-stu-id="c38af-111">To create a text attribute</span></span>  
  
1.  <span data-ttu-id="c38af-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="c38af-113">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **엔터티**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="c38af-114">**엔터티 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="c38af-115">해당 특성을 만들려는 엔터티의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-115">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="c38af-116">**선택한 엔터티 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-116">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="c38af-117">**엔터티 편집** 페이지에서</span><span class="sxs-lookup"><span data-stu-id="c38af-117">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="c38af-118">리프 멤버에 대한 특성일 경우 **리프 멤버 특성** 창에서 **리프 특성 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-118">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="c38af-119">통합 멤버에 대한 특성일 경우 **통합 멤버 특성** 창에서 **통합 특성 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-119">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="c38af-120">컬렉션에 대한 특성일 경우 **컬렉션 특성** 창에서 **컬렉션 특성 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-120">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="c38af-121">**특성 추가** 페이지에서 **자유 형식** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-121">On the **Add Attribute** page, select the **Free-form** option.</span></span>  
  
8.  <span data-ttu-id="c38af-122">**이름** 상자에 특성의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-122">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="c38af-123">특성 이름으로 사용 하지 않아야 하는 단어의 목록을 보려면 [예약어 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/reserved-words-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c38af-123">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="c38af-124">**탐색기** 표에 표시할 특성 열의 너비를 **표시 픽셀 폭** 상자에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-124">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="c38af-125">**데이터 형식** 목록에서 **텍스트**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-125">From the **Data type** list, select **Text**.</span></span>  
  
11. <span data-ttu-id="c38af-126">**길이** 상자에 허용되는 최대 문자 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-126">In the **Length** box, type the maximum number of characters allowed.</span></span>  
  
12. <span data-ttu-id="c38af-127">또는 특성 그룹의 변경 내용을 추적하려면 **변경 내용 추적 설정** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-127">Optionally, select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="c38af-128">자세한 내용은 [변경 내용 추적 그룹에 특성 추가&#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c38af-128">For more information, see [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).</span></span>  
  
13. <span data-ttu-id="c38af-129">**특성 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-129">Click **Save attribute**.</span></span>  
  
14. <span data-ttu-id="c38af-130">**엔터티 유지 관리** 페이지에서 **엔터티 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c38af-130">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c38af-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c38af-131">See Also</span></span>  
 <span data-ttu-id="c38af-132">[특성 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="c38af-132">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="c38af-133">[특성 이름을 MDS(Master Data Services) &#40;변경&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="c38af-133">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 <span data-ttu-id="c38af-134">[도메인 기반 특성 &#40;MDS(Master Data Services)를 만듭니다&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="c38af-134">[Create a Domain-Based Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="c38af-135">파일 특성 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c38af-135">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
