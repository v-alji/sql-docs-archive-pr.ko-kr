---
title: 관계 삭제 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d40e3f05-54e8-4c4b-807a-0b06f446079b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c63324918eb6919ce0abd65b5ee0765f9d7243b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728844"
---
# <a name="delete-relationships-ssas-tabular"></a><span data-ttu-id="b8e52-102">관계 삭제(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="b8e52-102">Delete Relationships (SSAS Tabular)</span></span>
  <span data-ttu-id="b8e52-103">다이어그램 뷰의 모델 디자이너나 관계 관리 대화 상자를 사용하여 기존 관계를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8e52-103">You can delete existing relationships by using the model designer in Diagram View or by using the Manage Relationships dialog box.</span></span> <span data-ttu-id="b8e52-104">테이블 형식 모델에서 관계를 사용하는 방법에 대한 자세한 내용은 [관계&#40;SSAS 테이블 형식&#41;](relationships-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b8e52-104">For information about how relationships are used in tabular models, see [Relationships &#40;SSAS Tabular&#41;](relationships-ssas-tabular.md).</span></span>  
  
## <a name="considerations-for-deleting-relationships"></a><span data-ttu-id="b8e52-105">관계 삭제 시 고려 사항</span><span class="sxs-lookup"><span data-stu-id="b8e52-105">Considerations for Deleting Relationships</span></span>  
 <span data-ttu-id="b8e52-106">관계를 삭제할지 여부를 결정할 때 다음 사항에 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="b8e52-106">Keep the following issues in mind when deciding whether to delete a relationship:</span></span>  
  
-   <span data-ttu-id="b8e52-107">관계 삭제를 실행 취소할 방법이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8e52-107">There is no way to undo the deletion of a relationship.</span></span> <span data-ttu-id="b8e52-108">관계를 다시 만들 수 있지만 이 동작을 수행하려면 모델의 수식을 완전히 다시 계산해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8e52-108">You can re-create the relationship, but this action requires a complete recalculation of formulas in the model.</span></span> <span data-ttu-id="b8e52-109">따라서 관계를 삭제하기 전에 먼저 해당 관계가 수식에 사용되는지 항상 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="b8e52-109">Therefore, always check first before deleting a relationship that is used in formulas.</span></span>  
  
-   <span data-ttu-id="b8e52-110">두 테이블 사이의 관계를 삭제하면 해당 테이블을 참조하는 수식에서 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8e52-110">Deleting a relationship between two tables can cause errors in formulas that reference these tables.</span></span>  
  
-   <span data-ttu-id="b8e52-111">DAX(Data Analysis Expression) RELATED 함수는 테이블 간의 관계를 사용하여 다른 테이블에서 관련 값을 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="b8e52-111">The Data Analysis Expression (DAX) RELATED function uses the relationships between tables to look up related values in another table.</span></span> <span data-ttu-id="b8e52-112">관계가 삭제된 이후에는 다른 결과가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8e52-112">It will return different results after the relationship is deleted.</span></span> <span data-ttu-id="b8e52-113">RELATED(DAX) 함수에 대한 자세한 내용은 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b8e52-113">For more information, see the RELATED Function (DAX).</span></span>  
  
-   <span data-ttu-id="b8e52-114">피벗 테이블 및 수식 결과가 변경되는 것 이외에도 관계를 만들거나 삭제하면 통합 문서가 다시 계산되므로 다소 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8e52-114">In addition to changing PivotTable and formula results, both the creation and deletion of relationships will cause the workbook to be recalculated, which can take some time.</span></span>  
  
## <a name="delete-relationships"></a><span data-ttu-id="b8e52-115">관계 삭제</span><span class="sxs-lookup"><span data-stu-id="b8e52-115">Delete Relationships</span></span>  
  
#### <a name="to-delete-a-relationship-by-using-diagram-view"></a><span data-ttu-id="b8e52-116">다이어그램 뷰를 사용하여 관계를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="b8e52-116">To delete a relationship by using Diagram View</span></span>  
  
1.  <span data-ttu-id="b8e52-117">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 **모델** 메뉴를 클릭하고 **모델 뷰**를 가리킨 다음 **다이어그램 뷰**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8e52-117">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Model** menu, then point to **Model View**, and then click **Diagram View**.</span></span>  
  
2.  <span data-ttu-id="b8e52-118">두 테이블 간의 관계 선을 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8e52-118">Right-click a relationship line between two tables, and then click **Delete**.</span></span>  
  
#### <a name="to-delete-a-relationship-by-using-the-manage-relationships-dialog-box"></a><span data-ttu-id="b8e52-119">관계 관리 대화 상자를 사용하여 관계를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="b8e52-119">To delete a relationship by using the Manage Relationships dialog box</span></span>  
  
1.  <span data-ttu-id="b8e52-120">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 **테이블** 메뉴를 클릭한 다음 **관계 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8e52-120">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Table** menu, and then click **Manage Relationships**.</span></span>  
  
2.  <span data-ttu-id="b8e52-121">**관계 관리** 대화 상자의 목록에서 관계를 하나 이상 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b8e52-121">In the **Manage Relationships** dialog box, select one or more relationships from the list.</span></span>  
  
     <span data-ttu-id="b8e52-122">관계를 여러 개 선택하려면 Ctrl 키를 누른 채 각 관계를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8e52-122">To select multiple relationships, hold down CTRL while you click each relationship.</span></span>  
  
3.  <span data-ttu-id="b8e52-123">**관계 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8e52-123">Click **Delete Relationship**.</span></span>  
  
4.  <span data-ttu-id="b8e52-124">**관계 관리** 대화 상자에서 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8e52-124">In the **Manage Relationships** dialog box, click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e52-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8e52-125">See Also</span></span>  
 <span data-ttu-id="b8e52-126">[SSAS 테이블 형식&#41;&#40;관계](relationships-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="b8e52-126">[Relationships &#40;SSAS Tabular&#41;](relationships-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="b8e52-127">두 테이블 간에 관계 만들기&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="b8e52-127">Create a Relationship Between Two Tables &#40;SSAS Tabular&#41;</span></span>](create-a-relationship-between-two-tables-ssas-tabular.md)  
  
  
