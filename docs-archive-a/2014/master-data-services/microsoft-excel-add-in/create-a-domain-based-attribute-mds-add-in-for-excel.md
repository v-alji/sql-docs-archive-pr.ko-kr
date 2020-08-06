---
title: 도메인 기반 특성 만들기(Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 7b3e30dc-8f41-4a5d-8009-ae5a4426a64b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bda0c7f63ad380aaea5d980d2e729822ec9a3d22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638883"
---
# <a name="create-a-domain-based-attribute-mds-add-in-for-excel"></a><span data-ttu-id="9dd0f-102">도메인 기반 특성 만들기(Excel용 MDS 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="9dd0f-102">Create a Domain-based Attribute (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="9dd0f-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서 관리자는 열에 있는 값을 특정 값 집합으로 제약하려는 경우 도메인 기반 특성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], administrators can create a domain-based attribute when they want to constrain the values in a column to a specific set of values.</span></span>  
  
 <span data-ttu-id="9dd0f-104">워크시트에 이미 있는 값이나 기존 엔터티에서 가져온 값으로 제약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-104">The values can already be in the worksheet or they can come from an existing entity.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9dd0f-105"> 목록에서 값을 선택하는 대신 제약된 열에 값을 입력하면 값이 게시될 때 **$InputStatus$** 열에 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-105">If users type a value in the constrained column, rather than selecting from the list, errors are displayed in the **$InputStatus$** column when they publish.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9dd0f-106">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="9dd0f-106">Prerequisites</span></span>  
 <span data-ttu-id="9dd0f-107">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="9dd0f-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="9dd0f-108">**시스템 관리** 와 **탐색기** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-108">You must have permission to access the **System Administration** and **Explorer** functional areas.</span></span>  
  
-   <span data-ttu-id="9dd0f-109">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-109">You must be a model administrator.</span></span> <span data-ttu-id="9dd0f-110">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](../administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-110">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="9dd0f-111">모델과 엔터티가 이미 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-111">The model and entity must already exist.</span></span>  
  
### <a name="to-perform-this-procedure"></a><span data-ttu-id="9dd0f-112">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="9dd0f-112">To perform this procedure:</span></span>  
  
1.  <span data-ttu-id="9dd0f-113">Excel에서 제약할 열(특성)이 포함된 엔터티를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-113">In Excel, load the entity that contains the column (attribute) you want to constrain.</span></span> <span data-ttu-id="9dd0f-114">자세한 내용은 [MDS에서 Excel로 데이터 로드](export-data-to-excel-from-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-114">For more information, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
2.  <span data-ttu-id="9dd0f-115">제약할 열에서 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-115">Click any cell in the column you want to constrain.</span></span>  
  
3.  <span data-ttu-id="9dd0f-116">**모델 작성** 그룹에서 **특성 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-116">In the **Build Model** group, click **Attribute Properties**.</span></span>  
  
4.  <span data-ttu-id="9dd0f-117">**특성 속성** 대화 상자의 **특성 유형** 목록에서 **제약된 목록(도메인 기반)** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-117">In the **Attribute Properties** dialog box, in the **Attribute type** list, choose **Constrained list (domain-based)**.</span></span>  
  
5.  <span data-ttu-id="9dd0f-118">**특성을 채울 값** 목록에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-118">In the **Populate the attribute with values from** list:</span></span>  
  
    -   <span data-ttu-id="9dd0f-119">워크시트의 값을 사용하려면 **선택한 열**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-119">To use values from the worksheet, choose **the selected column**.</span></span> <span data-ttu-id="9dd0f-120">선택한 열의 값을 사용하여 새 엔터티와 새 준비 테이블이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-120">A new entity and new staging table will be created with the values from the selected column.</span></span>  
  
    -   <span data-ttu-id="9dd0f-121">기존 엔터티의 값을 사용하려면 엔터티 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-121">To use values from an existing entity, choose the name of the entity.</span></span>  
  
6.  <span data-ttu-id="9dd0f-122">이전 단계에서 **선택한 열을** 을 선택한 경우 **새 엔터티 이름** 상자에 새 엔터티의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-122">If you chose **the selected column** in the previous step, in the **New entity name** box, type a name for the new entity.</span></span> <span data-ttu-id="9dd0f-123">이 이름은 열(특성) 이름과 같을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-123">This can be the same as the column (attribute) name.</span></span>  
  
7.  <span data-ttu-id="9dd0f-124">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-124">Click **OK**.</span></span> <span data-ttu-id="9dd0f-125">이제 열의 각 셀에 사용자가 값을 선택할 수 있는 목록이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-125">Each cell in the column now has a list of values for users to choose from.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9dd0f-126">다음 단계</span><span class="sxs-lookup"><span data-stu-id="9dd0f-126">Next Steps</span></span>  
  
-   <span data-ttu-id="9dd0f-127">제약된 목록에 값을 추가하거나 목록에서 값을 삭제하려면 특성의 기반이 되는 엔터티를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-127">To add and delete values in the constrained list, load the entity that the attribute is based on.</span></span> <span data-ttu-id="9dd0f-128">엔터티를 로드 하는 방법에 대 한 자세한 내용은 [MDS에서 Excel로 데이터 로드](export-data-to-excel-from-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9dd0f-128">For more information on loading entities, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd0f-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9dd0f-129">See Also</span></span>  
 <span data-ttu-id="9dd0f-130">[도메인 기반 특성 &#40;MDS(Master Data Services)&#41;](../domain-based-attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="9dd0f-130">[Domain-Based Attributes &#40;Master Data Services&#41;](../domain-based-attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="9dd0f-131">[엔터티 &#40;Excel용 MDS 추가 기능를 만듭니다&#41;](create-an-entity-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="9dd0f-131">[Create an Entity &#40;MDS Add-in for Excel&#41;](create-an-entity-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="9dd0f-132">모델 작성&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="9dd0f-132">Building a Model &#40;MDS Add-in for Excel&#41;</span></span>](building-a-model-mds-add-in-for-excel.md)  
  
  
