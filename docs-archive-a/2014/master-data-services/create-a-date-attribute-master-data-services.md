---
title: 날짜 특성 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating date attributes [Master Data Services]
- attributes [Master Data Services], creating date attributes
ms.assetid: 22a8f1a3-b4f2-4cfa-8495-7daad5ce9d12
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 93797b90ff03c6a2b60ce8e015897a46a7448aad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638890"
---
# <a name="create-a-date-attribute-master-data-services"></a><span data-ttu-id="45344-102">날짜 특성 만들기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="45344-102">Create a Date Attribute (Master Data Services)</span></span>
  <span data-ttu-id="45344-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 사용자가 날짜를 특성 값으로 입력할 수 있게 하려면 날짜 특성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45344-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a date attribute when you want users to enter a date as an attribute value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="45344-104">이 특성을 DateTime이라고 하지만 시간 값이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="45344-104">The attribute is called DateTime, but time values are not supported.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="45344-105">전제 조건</span><span class="sxs-lookup"><span data-stu-id="45344-105">Prerequisites</span></span>  
 <span data-ttu-id="45344-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="45344-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="45344-107">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="45344-108">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-108">You must be a model administrator.</span></span> <span data-ttu-id="45344-109">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45344-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="45344-110">해당 특성을 만들 엔터티가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-110">You must have an entity to create the attribute for.</span></span> <span data-ttu-id="45344-111">자세한 내용은 [&#41;MDS(Master Data Services) 엔터티 &#40;만들기 ](../../2014/master-data-services/create-an-entity-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45344-111">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-date-attribute"></a><span data-ttu-id="45344-112">날짜 특성을 만들려면</span><span class="sxs-lookup"><span data-stu-id="45344-112">To create a date attribute</span></span>  
  
1.  <span data-ttu-id="45344-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="45344-114">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **엔터티**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-114">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="45344-115">**엔터티 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-115">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="45344-116">해당 특성을 만들려는 엔터티의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-116">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="45344-117">**선택한 엔터티 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-117">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="45344-118">**엔터티 편집** 페이지에서</span><span class="sxs-lookup"><span data-stu-id="45344-118">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="45344-119">리프 멤버에 대한 특성일 경우 **리프 멤버 특성** 창에서 **리프 특성 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-119">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="45344-120">통합 멤버에 대한 특성일 경우 **통합 멤버 특성** 창에서 **통합 특성 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-120">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="45344-121">컬렉션에 대한 특성일 경우 **컬렉션 특성** 창에서 **컬렉션 특성 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-121">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="45344-122">**특성 추가** 페이지에서 **자유 형식** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-122">On the **Add Attribute** page, select the **Free-form** option.</span></span>  
  
8.  <span data-ttu-id="45344-123">**이름** 상자에 특성의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-123">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="45344-124">특성 이름으로 사용 하지 않아야 하는 단어의 목록을 보려면 [예약어 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/reserved-words-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45344-124">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="45344-125">**탐색기** 표에 표시할 특성 열의 너비를 **표시 픽셀 폭** 상자에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-125">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="45344-126">**데이터 형식** 목록에서 **DateTime**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-126">From the **Data type** list, select **DateTime**.</span></span>  
  
11. <span data-ttu-id="45344-127">**입력 마스크** 목록에서 날짜 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-127">From the **Input mask** list, select a format for dates.</span></span>  
  
12. <span data-ttu-id="45344-128">또는 특성 그룹의 변경 내용을 추적하려면 **변경 내용 추적 설정** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-128">Optionally, select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="45344-129">자세한 내용은 [변경 내용 추적 그룹에 특성 추가&#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45344-129">For more information, see [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).</span></span>  
  
13. <span data-ttu-id="45344-130">**특성 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-130">Click **Save attribute**.</span></span>  
  
14. <span data-ttu-id="45344-131">**엔터티 유지 관리** 페이지에서 **엔터티 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-131">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="to-display-the-time-portion-of-a-datetime-value"></a><span data-ttu-id="45344-132">날짜/시간 값의 시간 부분을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="45344-132">To display the time portion of a datetime value</span></span>  
 <span data-ttu-id="45344-133">사용자 인터페이스에서 날짜/시간 값의 시간 부분을 표시하도록 하려면 특성에 대한 적절한 입력 마스크를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-133">To have the user interface display the time portion of a datetime value, you must select an appropriate input mask for the attribute.</span></span> <span data-ttu-id="45344-134">이를 수행하는 Datetime 특성의 기본 제공 마스크가 없는 경우 시간을 표시할 수 있도록 하는 새 마스크를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45344-134">None of the built-in masks for Datetime attributes do this, but you can add a new mask that will allow you to display time.</span></span> <span data-ttu-id="45344-135">이렇게 하려면 기본 제공 마스크가 저장되는 MDS 데이터베이스의 mdm.tblList 테이블에 행을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-135">To do so, add a row in the mdm.tblList table of the MDS database, where the built-in masks are stored.</span></span> <span data-ttu-id="45344-136">행의 값은 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45344-136">The row should have the following values:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="45344-137">ListCode</span><span class="sxs-lookup"><span data-stu-id="45344-137">ListCode</span></span>|<span data-ttu-id="45344-138">lstInputMask</span><span class="sxs-lookup"><span data-stu-id="45344-138">lstInputMask</span></span>|  
|<span data-ttu-id="45344-139">ListName</span><span class="sxs-lookup"><span data-stu-id="45344-139">ListName</span></span>|<span data-ttu-id="45344-140">입력 마스크</span><span class="sxs-lookup"><span data-stu-id="45344-140">Input Mask</span></span>|  
|<span data-ttu-id="45344-141">Seq</span><span class="sxs-lookup"><span data-stu-id="45344-141">Seq</span></span>|<span data-ttu-id="45344-142">19</span><span class="sxs-lookup"><span data-stu-id="45344-142">19</span></span>|  
|<span data-ttu-id="45344-143">List Option</span><span class="sxs-lookup"><span data-stu-id="45344-143">List Option</span></span>|<span data-ttu-id="45344-144">dd/MM/yyyy hh:mm:ss tt</span><span class="sxs-lookup"><span data-stu-id="45344-144">dd/MM/yyyy hh:mm:ss tt</span></span>|  
|<span data-ttu-id="45344-145">Option ID</span><span class="sxs-lookup"><span data-stu-id="45344-145">Option ID</span></span>|<span data-ttu-id="45344-146">19</span><span class="sxs-lookup"><span data-stu-id="45344-146">19</span></span>|  
|<span data-ttu-id="45344-147">IsVisible</span><span class="sxs-lookup"><span data-stu-id="45344-147">IsVisible</span></span>|<span data-ttu-id="45344-148">1</span><span class="sxs-lookup"><span data-stu-id="45344-148">1</span></span>|  
|<span data-ttu-id="45344-149">Group_ID</span><span class="sxs-lookup"><span data-stu-id="45344-149">Group_ID</span></span>|<span data-ttu-id="45344-150">3</span><span class="sxs-lookup"><span data-stu-id="45344-150">3</span></span>|  
  
 <span data-ttu-id="45344-151">mdm.tblList 표에 위 값이 있는 행을 입력하면 입력 마스크 목록 상자에서 "dd/MM/yyyy hh:mm:ss tt" 마스크를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45344-151">After you enter a row with the above values in the mdm.tblList table, the "dd/MM/yyyy hh:mm:ss tt" mask will be available in the Input mask list box.</span></span> <span data-ttu-id="45344-152">그러면 해당 엔터티를 선택하여 MDS 탐색기에서 엔터티의 datetime 특성 열에 날짜 및 시간을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45344-152">You can then select that mask to display the date and time in a datetime attribute column of an entity in the MDS Explorer.</span></span>  
  
 <span data-ttu-id="45344-153">입력 마스크는 사용자 지정 .NET DateTime 형식 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="45344-153">The Input Mask is a custom .NET DateTime format string.</span></span> <span data-ttu-id="45344-154">자세한 내용은 [사용자 지정 날짜 및 시간 형식 문자열](https://msdn.microsoft.com/library/8kb3ddd4\(v=vs.110\).aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45344-154">For more information, see [Custom Date and Time Format Strings](https://msdn.microsoft.com/library/8kb3ddd4\(v=vs.110\).aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45344-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45344-155">See Also</span></span>  
 <span data-ttu-id="45344-156">[특성 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="45344-156">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="45344-157">[특성 이름을 MDS(Master Data Services) &#40;변경&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="45344-157">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 <span data-ttu-id="45344-158">[도메인 기반 특성 &#40;MDS(Master Data Services)를 만듭니다&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="45344-158">[Create a Domain-Based Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="45344-159">파일 특성 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="45344-159">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
