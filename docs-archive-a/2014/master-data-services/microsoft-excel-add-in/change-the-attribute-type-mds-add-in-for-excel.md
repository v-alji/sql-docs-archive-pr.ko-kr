---
title: 특성 유형 변경(Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9d3001d9-8d0f-4e4a-8e04-4f666bf0df69
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a55ca53fcf6923957e2196840aea2fb5914e1746
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730800"
---
# <a name="change-the-attribute-type-mds-add-in-for-excel"></a><span data-ttu-id="8db57-102">특성 유형 변경(Excel용 MDS 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="8db57-102">Change the Attribute Type (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="8db57-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서 관리자는 허용되는 문자 개수 또는 데이터 형식이 잘못된 경우 특성 유형을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], administrators can change the attribute type when the data type or number of allowed characters is incorrect.</span></span>  
  
 <span data-ttu-id="8db57-104">제한된 목록(도메인 기반 특성)을 만들도록 특성 유형을 변경하려는 경우 [도메인 기반 특성 만들기&#40;Excel용 MDS 추가 기능&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8db57-104">If you want to change the attribute type to create a constrained list (domain-based attribute), see [Create a Domain-based Attribute &#40;MDS Add-in for Excel&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8db57-105">**이름** 또는 **코드** 열의 유형이나 길이는 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-105">You cannot update the type or length of the **Name** or **Code** columns.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8db57-106">필수 조건</span><span class="sxs-lookup"><span data-stu-id="8db57-106">Prerequisites</span></span>  
 <span data-ttu-id="8db57-107">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="8db57-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="8db57-108">**시스템 관리** 와 **탐색기** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-108">You must have permission to access the **System Administration** and **Explorer** functional areas.</span></span>  
  
-   <span data-ttu-id="8db57-109">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-109">You must be a model administrator.</span></span> <span data-ttu-id="8db57-110">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](../administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8db57-110">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="8db57-111">기존 모델, 엔터티 및 특성이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-111">There must be an existing model, entity, and attribute.</span></span>  
  
### <a name="to-change-the-attribute-type"></a><span data-ttu-id="8db57-112">특성 유형을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="8db57-112">To change the attribute type</span></span>  
  
1.  <span data-ttu-id="8db57-113">Excel에서 변경하려는 열(특성)이 포함된 엔터티를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-113">In Excel, load the entity that contains the column (attribute) you want to change.</span></span> <span data-ttu-id="8db57-114">자세한 내용은 [MDS에서 Excel로 데이터 로드](export-data-to-excel-from-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8db57-114">For more information, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
2.  <span data-ttu-id="8db57-115">변경할 열에서 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-115">Click any cell in the column you want to change.</span></span>  
  
3.  <span data-ttu-id="8db57-116">**모델 작성** 그룹에서 **특성 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-116">In the **Build Model** group, click **Attribute Properties**.</span></span>  
  
4.  <span data-ttu-id="8db57-117">**특성 속성** 대화 상자에서 필요에 따라 설정을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-117">In the **Attribute Properties** dialog box, update settings as needed.</span></span>  
  
5.  <span data-ttu-id="8db57-118">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-118">Click **OK**.</span></span>  
  
## <a name="what-happens-when-you-change-the-attribute-type"></a><span data-ttu-id="8db57-119">특성 유형을 변경하면 어떻게 됩니까?</span><span class="sxs-lookup"><span data-stu-id="8db57-119">What happens when you change the attribute type?</span></span>  
 <span data-ttu-id="8db57-120">특성에 종속성이 존재하여, 그러한 속성이 MDS 비즈니스 규칙에 의해 참조되거나 특성이 구독 뷰에 포함될 경우, 사용자가 특성의 데이터 형식을 변경하면, MDS에서 다음 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-120">If there is any dependency on the attribute, such as the attribute is referenced by any MDS business rule or the attribute is included in a subscription view, and you change the data type of an attribute, MDS will:</span></span>  
  
-   <span data-ttu-id="8db57-121">특성의 데이터 형식을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-121">Change the data type of the attribute.</span></span>  
  
-   <span data-ttu-id="8db57-122">값을 포함 하지 않는 "_old" 라는 접미사를 사용 하 여 특성의 복사본을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-122">Generate a copy of the attribute with the suffix "_old" that does not contain any value.</span></span> <span data-ttu-id="8db57-123">이를 **사용 되지 않는** 특성 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-123">This is called a **deprecated** attribute.</span></span>  
  
 <span data-ttu-id="8db57-124">하지만 원래 특성의 모든 기존 종속성은 변경된 특성이 아닌 더 이상 사용되지 않는 특성을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-124">However, all the existing dependencies on the original attribute will point to the deprecated attribute, and not to the changed one.</span></span>  
  
 <span data-ttu-id="8db57-125">즉,</span><span class="sxs-lookup"><span data-stu-id="8db57-125">This implies that:</span></span>  
  
-   <span data-ttu-id="8db57-126">특성의 새로운 데이터 형식에 따라 논리가 동일하지 않을 수 있기 때문에 변경된 특성을 가리키도록 비즈니스 규칙을 새로 고쳐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-126">You must refresh the business rules to point to the changed attribute because the logic may not be the same given the new data type of the attribute.</span></span> <span data-ttu-id="8db57-127">영향을 받는 각 규칙을 편집하고, 더 이상 사용되지 않는 특성(_old)에서 참조를 제거하고 업데이트된 특성을 가리키도록 식을 재작업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-127">You will have to edit each affected rule, and then rework the expressions to point to remove references from the deprecated attribute (_old) to point to the updated attribute.</span></span>  
  
-   <span data-ttu-id="8db57-128">통합 관리 선택 항목에서 구독 뷰를 열고, 뷰 행을 선택 하 고, 연필 아이콘을 클릭 하 여 편집용으로 연 다음, **디스크 저장** 아이콘을 클릭 하 여 뷰 정의를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-128">You must open any subscription views under the Integration Management selection, select the view row, open it for editing by clicking the pencil icon, and then click the **Save disk** icon to refresh the view definition.</span></span> <span data-ttu-id="8db57-129">뷰 구문을 재생성하는 데 다른 변경 사항은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-129">No other change is needed to regenerate the view syntax.</span></span>  
  
-   <span data-ttu-id="8db57-130">특성이 포함된 준비 테이블에는 더 이상 사용되지 않는 특성 열이 테이블에 추가됩니다. 즉, 준비 코드에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-130">Staging tables that include the attribute will have a deprecated attribute column added to them, which means that your staging code will be affected.</span></span> <span data-ttu-id="8db57-131">더 이상 사용되지 않는 특성을 없애기 위해서는 비즈니스 규칙 및 구독 뷰를 업데이트한 후 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-131">To get rid of the deprecated attribute, you can delete it after you have updated the business rules and subscription views.</span></span>  
  
 <span data-ttu-id="8db57-132">**더 이상 사용되지 않는 특성 삭제**</span><span class="sxs-lookup"><span data-stu-id="8db57-132">**Deleting the deprecated attribute**</span></span>  
  
 <span data-ttu-id="8db57-133">더 이상 사용되지 않는 특성을 삭제하려면 먼저 앞에서 설명한 것처럼 비즈니스 규칙을 수정하고 구독 뷰를 다시 생성하여 특성에 대한 모든 참조를 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-133">Before you delete any deprecated attribute, you must remove any references to the attribute such as fixing the business rules and regenerating subscription views as described earlier.</span></span> <span data-ttu-id="8db57-134">그렇지 않으면 더 이상 사용되지 않는 특성을 삭제하려고 시도할 때 시스템 관리 웹 페이지에서 개체에서 참조되기 때문에 특성을 삭제할 수 없다는 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-134">Otherwise, you will get an error in the System Administration web page when you attempt to delete the deprecated attribute stating that the attribute cannot be deleted because it is referenced by an object.</span></span>  
  
 <span data-ttu-id="8db57-135">특성을 삭제 하려면 [&#40;MDS(Master Data Services) 특성 삭제](../delete-an-attribute-master-data-services.md) 를 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="8db57-135">To delete an attribute, see [Delete an Attribute &#40;Master Data Services&#41;](../delete-an-attribute-master-data-services.md)</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="8db57-136">기존 데이터 및 관련 항목이 포함된 MDS 특성의 데이터 형식을 변경하는 것은 번거로운 일일 수 있습니다. 특히 엔터티에 종속된 비즈니스 규칙 또는 구독 뷰가 선언되었다면 더욱 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-136">It is cumbersome to change data types for MDS attributes that have existing data and related entities, especially if there is a business rule or subscription view declared which depends on the entity.</span></span> <span data-ttu-id="8db57-137">가장 좋은 방법은 필요한 값을 저장하기에 충분히 유연한 데이터 형식으로 시작하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-137">The best practice is to start with a data type that is flexible enough to hold the necessary values.</span></span> <span data-ttu-id="8db57-138">예를 들어 문자열을 작은 크기로 시작할 수 있지만 시간이 지남에 따라 길이를 늘려야 할 수 있으므로, 최악의 시나리오를 고려하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8db57-138">For example, strings may start small, but may need to be lengthened over time, so consider the worst case scenarios.</span></span> <span data-ttu-id="8db57-139">텍스트 문자열 길이가 너무 길면 부담이 될 수 있으므로(예를 들어 GUI 텍스트 상자가 너무 넓으면 화면에 맞게 표시하기 어려울 수 있음), 너무 긴 문자열 길이는 피하십시오.</span><span class="sxs-lookup"><span data-stu-id="8db57-139">Extra text string length can be burdensome (for example, wide GUI text boxes are hard to fit on the screen), so avoid too long string length.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8db57-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8db57-140">See Also</span></span>  
 <span data-ttu-id="8db57-141">[특성 &#40;MDS(Master Data Services)&#41;](../attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="8db57-141">[Attributes &#40;Master Data Services&#41;](../attributes-master-data-services.md) </span></span>  
 [<span data-ttu-id="8db57-142">모델 작성&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="8db57-142">Building a Model &#40;MDS Add-in for Excel&#41;</span></span>](building-a-model-mds-add-in-for-excel.md)  
  
  
