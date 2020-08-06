---
title: 두 테이블 간에 관계 만들기 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.managereldb.f1
- sql12.asvs.bidtoolset.createrelatdb.f1
ms.assetid: 052d77b7-7922-408a-a200-786016ee4d15
author: minewiskan
ms.author: owend
ms.openlocfilehash: 33481b8d50be9ca632bcade932d51df86c1910a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649214"
---
# <a name="create-a-relationship-between-two-tables-ssas-tabular"></a><span data-ttu-id="89a5b-102">두 테이블 간에 관계 만들기(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="89a5b-102">Create a Relationship Between Two Tables (SSAS Tabular)</span></span>
  <span data-ttu-id="89a5b-103">데이터 원본의 테이블에 기존 관계가 없거나 새 테이블을 추가하는 경우 모델 디자이너의 도구를 사용하여 새 관계를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-103">If the tables in your data source do not have existing relationships, or if you add new tables, you can use the tools in the model designer to create new relationships.</span></span> <span data-ttu-id="89a5b-104">테이블 형식 모델에서 관계를 사용하는 방법에 대한 자세한 내용은 [관계&#40;SSAS 테이블 형식&#41;](relationships-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89a5b-104">For information about how relationships are used in tabular models, see [Relationships &#40;SSAS Tabular&#41;](relationships-ssas-tabular.md).</span></span>  
  
## <a name="create-a-relationship-between-two-tables"></a><span data-ttu-id="89a5b-105">두 테이블 간에 관계 만들기</span><span class="sxs-lookup"><span data-stu-id="89a5b-105">Create a relationship between two tables</span></span>  
  
#### <a name="to-create-a-relationship-between-two-tables-in-diagram-view-click-and-drag"></a><span data-ttu-id="89a5b-106">다이어그램 뷰에서 두 테이블 간의 관계를 만들려면(클릭하여 끌기)</span><span class="sxs-lookup"><span data-stu-id="89a5b-106">To create a relationship between two tables in Diagram View (Click and drag)</span></span>  
  
1.  <span data-ttu-id="89a5b-107">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 **모델** 메뉴를 클릭하고 **모델 뷰**를 클릭한 다음 **다이어그램 뷰**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-107">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, then click **Model View**, and then click **Diagram View**.</span></span>  
  
2.  <span data-ttu-id="89a5b-108">테이블 내의 열을 클릭한 채로 커서를 관련 조회 테이블의 관련 조회 열로 끌어다 놓으면</span><span class="sxs-lookup"><span data-stu-id="89a5b-108">Click (and hold) on a column within a table, then drag the cursor to a related lookup column in a related lookup table, and then release.</span></span> <span data-ttu-id="89a5b-109">관계가 올바른 순서로 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-109">The relationship will be created in the correct order automatically.</span></span>  
  
#### <a name="to-create-a-relationship-between-two-tables-in-diagram-view-right-click"></a><span data-ttu-id="89a5b-110">다이어그램 뷰에서 두 테이블 간의 관계를 만들려면(마우스 오른쪽 단추 클릭)</span><span class="sxs-lookup"><span data-stu-id="89a5b-110">To create a relationship between two tables in Diagram View (Right-click)</span></span>  
  
1.  <span data-ttu-id="89a5b-111">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 **모델** 메뉴를 클릭하고 **모델 뷰**를 클릭한 다음 **다이어그램 뷰**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-111">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, then click **Model View**, and then click **Diagram View**.</span></span>  
  
2.  <span data-ttu-id="89a5b-112">테이블 머리글 또는 열을 마우스 오른쪽 단추로 클릭하고 **관계 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-112">Right-click a table heading or column, and then click **Create Relationship**.</span></span>  
  
3.  <span data-ttu-id="89a5b-113">**관계 만들기** 대화 상자의 **테이블**에서 아래쪽 화살표를 클릭하고 드롭다운 목록에서 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-113">In the **Create Relationship** dialog box, click the down arrow for **Table**, and select a table from the dropdown list.</span></span>  
  
     <span data-ttu-id="89a5b-114">"일 대 다" 관계에서 이 테이블은 "다" 쪽에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-114">In a "one-to-many" relationship, this table should be on the "many" side.</span></span>  
  
4.  <span data-ttu-id="89a5b-115">**열**에서 **관련 조회 열**과 관련된 데이터가 들어 있는 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-115">For **Column**, select the column that contains the data that is related to **Related Lookup Column**.</span></span> <span data-ttu-id="89a5b-116">관계를 만들기 위해 열을 마우스 오른쪽 단추로 클릭하면 열이 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-116">The column is automatically selected if you right-clicked on a column to create the relationship.</span></span>  
  
5.  <span data-ttu-id="89a5b-117">**테이블**에서 방금 선택한 테이블과 관련된 데이터 열이 하나 이상 있는 테이블을 **관련 조회 테이블**에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-117">For **Related Lookup Table**, select a table that has at least one column of data that is related to the table you just selected for **Table**.</span></span>  
  
     <span data-ttu-id="89a5b-118">"일 대 다" 관계에서 이 테이블은 "일" 쪽에 있어야 하므로 선택한 열에 중복 값이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-118">In a "one-to-many" relationship, this table should be on the "one" side, meaning that the values in the selected column do not contain duplicates.</span></span> <span data-ttu-id="89a5b-119">잘못된 순서(다 대 일 대신 일 대 다)로 관계를 만들려고 하면 **관련 조회 열** 필드 옆에 아이콘이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-119">If you attempt to create the relationship in the wrong order (one-to-many instead of many-to-one), an icon will appear next to the **Related Lookup Column** field.</span></span> <span data-ttu-id="89a5b-120">순서를 반대로 하여 유효한 관계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-120">Reverse the order to create a valid relationship.</span></span>  
  
6.  <span data-ttu-id="89a5b-121">**열**에서 선택한 열의 값과 일치하는 고유 값이 있는 열을 **관련 조회 열**에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-121">For **Related Lookup Column**, select a column that has unique values that match the values in the column you selected for **Column**.</span></span>  
  
7.  <span data-ttu-id="89a5b-122">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-122">Click **Create**.</span></span>  
  
#### <a name="to-create-a-relationship-between-two-tables-in-data-view"></a><span data-ttu-id="89a5b-123">데이터 뷰에서 두 테이블 간의 관계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="89a5b-123">To create a relationship between two tables in Data View</span></span>  
  
1.  <span data-ttu-id="89a5b-124">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 **테이블** 메뉴를 클릭한 다음 **관계 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-124">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Table** menu, and then click **Create Relationships**.</span></span>  
  
2.  <span data-ttu-id="89a5b-125">**관계 만들기** 대화 상자의 **테이블**에서 아래쪽 화살표를 클릭하고 드롭다운 목록에서 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-125">In the **Create Relationship** dialog box, click the down arrow for **Table**, and select a table from the dropdown list.</span></span>  
  
     <span data-ttu-id="89a5b-126">"일 대 다" 관계에서 이 테이블은 "다" 쪽에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-126">In a "one-to-many" relationship, this table should be on the "many" side.</span></span>  
  
3.  <span data-ttu-id="89a5b-127">**열**에서 **관련 조회 열**과 관련된 데이터가 들어 있는 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-127">For **Column**, select the column that contains the data that is related to **Related Lookup Column**.</span></span>  
  
4.  <span data-ttu-id="89a5b-128">**테이블**에서 방금 선택한 테이블과 관련된 데이터 열이 하나 이상 있는 테이블을 **관련 조회 테이블**에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-128">For **Related Lookup Table**, select a table that has at least one column of data that is related to the table you just selected for **Table**.</span></span>  
  
     <span data-ttu-id="89a5b-129">"일 대 다" 관계에서 이 테이블은 "일" 쪽에 있어야 하므로 선택한 열에 중복 값이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-129">In a "one-to-many" relationship, this table should be on the "one" side, meaning that the values in the selected column do not contain duplicates.</span></span> <span data-ttu-id="89a5b-130">잘못된 순서(다 대 일 대신 일 대 다)로 관계를 만들려고 하면 **관련 조회 열** 필드 옆에 아이콘이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-130">If you attempt to create the relationship in the wrong order (one-to-many instead of many-to-one), an icon will appear next to the **Related Lookup Column** field.</span></span> <span data-ttu-id="89a5b-131">순서를 반대로 하여 유효한 관계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-131">Reverse the order to create a valid relationship.</span></span>  
  
5.  <span data-ttu-id="89a5b-132">**열**에서 선택한 열의 값과 일치하는 고유 값이 있는 열을 **관련 조회 열**에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-132">For **Related Lookup Column**, select a column that has unique values that match the values in the column you selected for **Column**.</span></span>  
  
6.  <span data-ttu-id="89a5b-133">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89a5b-133">Click **Create**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89a5b-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="89a5b-134">See Also</span></span>  
 <span data-ttu-id="89a5b-135">[SSAS 테이블 형식&#41;&#40;관계 삭제](delete-relationships-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="89a5b-135">[Delete Relationships &#40;SSAS Tabular&#41;](delete-relationships-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="89a5b-136">관계&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="89a5b-136">Relationships &#40;SSAS Tabular&#41;</span></span>](relationships-ssas-tabular.md)  
  
  
