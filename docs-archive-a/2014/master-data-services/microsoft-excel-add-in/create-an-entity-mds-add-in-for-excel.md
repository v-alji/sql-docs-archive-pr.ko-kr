---
title: 엔터티 만들기(Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: d354abb3-88fe-4b40-a374-f6256b84ffae
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 87ad67f7347da87c67afc11590df6775af4cf3d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638881"
---
# <a name="create-an-entity-mds-add-in-for-excel"></a><span data-ttu-id="cbc1c-102">엔터티 만들기(Excel용 MDS 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="cbc1c-102">Create an Entity (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="cbc1c-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서 관리자는 새 엔터티를 만들어 데이터를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], administrators can create new entities to store data.</span></span> <span data-ttu-id="cbc1c-104">엔터티를 만들 때 엔터티에 저장할 데이터의 샘플을 로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-104">When you create an entity you should load at least a sampling of the data you want to store.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cbc1c-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="cbc1c-105">Prerequisites</span></span>  
 <span data-ttu-id="cbc1c-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="cbc1c-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="cbc1c-107">**시스템 관리** 와 **탐색기** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-107">You must have permission to access the **System Administration** and **Explorer** functional areas.</span></span>  
  
-   <span data-ttu-id="cbc1c-108">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-108">You must be a model administrator.</span></span> <span data-ttu-id="cbc1c-109">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](../administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-109">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="cbc1c-110">만든 엔터티를 포함할 기존 모델이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-110">You must have an existing model to create the entity in.</span></span> <span data-ttu-id="cbc1c-111">자세한 내용은 [모델 만들기&#40;Master Data Services&#41;](../create-a-model-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-111">For more information, see [Create a Model &#40;Master Data Services&#41;](../create-a-model-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="cbc1c-112">데이터가 다음 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-112">Ensure that your data meets the following requirements:</span></span>  
  
    -   <span data-ttu-id="cbc1c-113">데이터에 머리글 행이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-113">The data should have a header row.</span></span>  
  
    -   <span data-ttu-id="cbc1c-114">**이름** 및 **코드** 열을 포함하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-114">It is helpful to have **Name** and **Code** columns.</span></span> <span data-ttu-id="cbc1c-115">**코드** 는 각 행의 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-115">**Code** is a unique identifier for each row.</span></span>  
  
    -   <span data-ttu-id="cbc1c-116">머리글 행 외에도 데이터 행이 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-116">You should have at least one row of data other than the header.</span></span> <span data-ttu-id="cbc1c-117">모든 열에 값이 포함되어 있을 필요는 없지만 엔터티에 포함할 데이터를 잘 나타내는 데이터가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-117">All columns do not need values, but the data should be representative of the data that will be in the entity.</span></span>  
  
    -   <span data-ttu-id="cbc1c-118">고유 식별자(MDS에서는 **코드**라고 함)가 포함된 열이 있는 경우 값이 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-118">If you have a column that contains a unique identifier (known in MDS as **Code**), ensure that the values are unique.</span></span> <span data-ttu-id="cbc1c-119">식별자가 포함된 열이 없으면 엔터티를 만들 때 자동으로 생성되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-119">If no column contains identifiers, you can have them generated automatically when you create the entity.</span></span>  
  
    -   <span data-ttu-id="cbc1c-120">수식이 포함된 셀이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-120">Ensure that no cells contain formulas.</span></span>  
  
    -   <span data-ttu-id="cbc1c-121">시간 값이 포함된 셀이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-121">Ensure that no cells contain time values.</span></span> <span data-ttu-id="cbc1c-122">MDS에서 날짜 값은 저장할 수 있지만 시간 값은 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-122">Date values can be saved in MDS but time values cannot.</span></span>  
  
### <a name="to-create-an-entity-and-load-data"></a><span data-ttu-id="cbc1c-123">엔터티를 만들고 데이터를 로드하려면</span><span class="sxs-lookup"><span data-stu-id="cbc1c-123">To create an entity and load data</span></span>  
  
1.  <span data-ttu-id="cbc1c-124">로드할 데이터가 들어 있는 Excel 워크시트를 열거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-124">Open or create an Excel worksheet that contains data you want to load.</span></span>  
  
2.  <span data-ttu-id="cbc1c-125">새 엔터티에 로드할 셀을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-125">Select the cells you want to load into the new entity.</span></span>  
  
3.  <span data-ttu-id="cbc1c-126">**마스터 데이터** 탭의 **모델 작성** 그룹에서 **엔터티 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-126">On the **Master Data** tab, in the **Build Model** group, click **Create Entity**.</span></span>  
  
4.  <span data-ttu-id="cbc1c-127">MDS 저장소에 연결할지 묻는 메시지가 표시되면 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-127">If you are prompted to connect to an MDS repository, connect.</span></span>  
  
5.  <span data-ttu-id="cbc1c-128">**엔터티 만들기** 대화 상자에서 기본 범위를 그대로 적용하거나 로드할 데이터에 맞게 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-128">In the **Create Entity** dialog box, leave the default range or change it to apply to the data you want to load.</span></span>  
  
6.  <span data-ttu-id="cbc1c-129">**내 데이터에 머리글 표시** 확인란의 선택을 취소하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-129">Do not clear the **My data has headers** check box.</span></span>  
  
7.  <span data-ttu-id="cbc1c-130">**모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-130">From the **Model** list, select a model.</span></span>  
  
8.  <span data-ttu-id="cbc1c-131">**버전** 목록에서 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-131">From the **Version** list, select a version.</span></span>  
  
9. <span data-ttu-id="cbc1c-132">**새 엔터티 이름** 상자에 엔터티의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-132">In the **New entity name** box, type a name for the entity.</span></span>  
  
10. <span data-ttu-id="cbc1c-133">**코드** 목록에서 고유 식별자가 포함된 열을 선택하거나 코드가 자동으로 생성되도록 둡니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-133">From the **Code** list, select the column that contains unique identifiers or have codes generated automatically.</span></span>  
  
11. <span data-ttu-id="cbc1c-134">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-134">Optional.</span></span> <span data-ttu-id="cbc1c-135">**이름** 목록에서 각 멤버의 이름이 포함된 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-135">From the **Name** list, select a column that contains names for each member.</span></span>  
  
12. <span data-ttu-id="cbc1c-136">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-136">Click **OK**.</span></span> <span data-ttu-id="cbc1c-137">엔터티가 만들어지면 새 머리글 행이 표시되고 셀이 강조 표시되며 엔터티 이름과 일치하도록 시트 이름이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-137">When the entity has been created successfully, a new header row is displayed, the cells are highlighted, and the sheet name is updated to match the entity name.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="cbc1c-138">다음 단계</span><span class="sxs-lookup"><span data-stu-id="cbc1c-138">Next Steps</span></span>  
  
-   <span data-ttu-id="cbc1c-139">발생한 오류를 보려면 **게시 및 유효성 검사** 그룹에서 **상태 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-139">To view errors that occurred, in the **Publish and Validate** group, click **Show Status**.</span></span> <span data-ttu-id="cbc1c-140">ValidationStatus 및 InputStatus 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-140">ValidationStatus and InputStatus columns are displayed.</span></span> <span data-ttu-id="cbc1c-141">자세한 내용은 [데이터 유효성 검사&#40;Excel용 MDS 추가 기능&#41;](validating-data-mds-add-in-for-excel.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-141">For more information, see [Validating Data &#40;MDS Add-in for Excel&#41;](validating-data-mds-add-in-for-excel.md).</span></span>  
  
-   <span data-ttu-id="cbc1c-142">예상한 데이터 형식으로 특성이 만들어졌는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc1c-142">Confirm that the attributes were created as the data type you expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbc1c-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cbc1c-143">See Also</span></span>  
 [<span data-ttu-id="cbc1c-144">도메인 기반 특성 만들기&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="cbc1c-144">Create a Domain-based Attribute &#40;MDS Add-in for Excel&#41;</span></span>](create-a-domain-based-attribute-mds-add-in-for-excel.md)  
  
  
