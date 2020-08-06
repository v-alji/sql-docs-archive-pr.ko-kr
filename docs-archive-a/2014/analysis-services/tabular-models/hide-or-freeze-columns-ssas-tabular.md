---
title: 열 숨기기 또는 고정 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.hideunhidecolumnsdb.f1
ms.assetid: 5407aee5-6a07-4559-a2ba-2ca00a242f02
author: minewiskan
ms.author: owend
ms.openlocfilehash: 71398eecbc342b4e3f9c2445fef3023132266dac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728835"
---
# <a name="hide-or-freeze-columns-ssas-tabular"></a><span data-ttu-id="906f8-102">열 숨기기 또는 고정(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="906f8-102">Hide or Freeze Columns (SSAS Tabular)</span></span>
  <span data-ttu-id="906f8-103">모델 디자이너에서 테이블에 표시하지 않으려는 열이 있는 경우 해당 열을 임시로 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-103">In the model designer, if there are columns that you don't want to display in a table, you can temporarily hide them.</span></span> <span data-ttu-id="906f8-104">열을 숨기면 새 열을 추가하거나 관련 데이터 열만 사용하여 작업하기 위해 화면에서 공간을 확보할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-104">Hiding a column gives you more room on the screen to add new columns or to work with only relevant columns of data.</span></span> <span data-ttu-id="906f8-105">모델 디자이너의 **열** 메뉴 및 각 열 머리글을 마우스 오른쪽 단추로 클릭했을 때 열리는 메뉴를 사용하여 열을 숨기거나 숨겨진 열을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-105">You can hide and unhide columns from the **Column** menu in the model designer, and from the right-click menu available from each column header.</span></span> <span data-ttu-id="906f8-106">모델의 다른 영역으로 스크롤할 때 모델의 특정 영역이 계속 표시되도록 하려면 해당 영역의 열을 고정하여 잠글 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-106">To keep an area of a model visible while you scroll to another area of the model, you can lock specific columns in one area by freezing them.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="906f8-107">열을 숨기는 기능은 데이터 보안의 목적보다는 모델 디자이너 또는 보고서에 표시되는 열의 목록을 단순화하고 간소화하기 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-107">The ability to hide columns is not intended to be used for data security, only to simplify and shorten the list of columns visible in the model designer or reports.</span></span> <span data-ttu-id="906f8-108">데이터 보안을 위해서는 보안 역할을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-108">To secure data, you can define security roles.</span></span> <span data-ttu-id="906f8-109">역할을 통해 특정 개체에 대해서만 메타데이터와 데이터를 볼 수 있도록 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-109">Roles can limit viewable metadata and data to only those objects defined in the role.</span></span> <span data-ttu-id="906f8-110">자세한 내용은 [역할&#40;SSAS 테이블 형식&#41;](roles-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="906f8-110">For more information, see [Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="906f8-111">열을 숨길 때 모델 디자이너 또는 보고서에서 작업할 동안에만 열을 숨기는 방법도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-111">When you hide a column, you have the option to hide the column while you are working in the model designer or in reports.</span></span> <span data-ttu-id="906f8-112">모든 열을 숨기면 모델 디자이너에서 전체 테이블이 공백으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-112">If you hide all columns, the entire table appears blank in the model designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="906f8-113">숨겨야 하는 열이 많은 경우 열을 숨기거나 숨김을 해제하는 대신 큐브 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-113">If you have many columns to hide, you can create a perspective instead of hiding and unhiding columns.</span></span> <span data-ttu-id="906f8-114">큐브 뷰는 관련 데이터의 하위 집합을 보다 쉽게 사용할 수 있는 사용자 지정 데이터 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-114">A perspective is a custom view of the data that makes it easier to work with subset of related data.</span></span> <span data-ttu-id="906f8-115">자세한 내용은 [큐브 뷰 만들기 및 관리&#40;SSAS 테이블 형식&#41;](perspectives-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="906f8-115">For more information, see [Create and Manage Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md)</span></span>  
  
### <a name="to-hide-an-individual-column"></a><span data-ttu-id="906f8-116">개별 열을 숨기려면</span><span class="sxs-lookup"><span data-stu-id="906f8-116">To hide an individual column</span></span>  
  
1.  <span data-ttu-id="906f8-117">모델 디자이너에서 숨기려는 열이 포함된 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-117">In the model designer, select the table that contains the column that you want to hide.</span></span>  
  
2.  <span data-ttu-id="906f8-118">열을 마우스 오른쪽 단추로 클릭하고 **열 숨기기**를 클릭한 다음 **디자이너 및 보고서에서**, **보고서에서**또는 **디자이너에서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-118">Right-click the column, then click **Hide Columns**, and then click **From Designer and Reports**, **From Reports**, or **From Designer**.</span></span>  
  
### <a name="to-hide-multiple-columns"></a><span data-ttu-id="906f8-119">여러 열을 숨기려면</span><span class="sxs-lookup"><span data-stu-id="906f8-119">To hide multiple columns</span></span>  
  
1.  <span data-ttu-id="906f8-120">모델 디자이너에서 숨기려는 열이 포함된 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-120">In the model designer, select the table that contains the columns that you want to hide.</span></span>  
  
2.  <span data-ttu-id="906f8-121">**열** 메뉴에서 **숨기기 및 숨기기 취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-121">Click on the **Columns** menu, and then click **Hide and Unhide**.</span></span>  
  
3.  <span data-ttu-id="906f8-122">**열 숨기기 및 숨기기 취소** 대화 상자에서 숨기려는 각 열을 찾은 다음 **디자이너** 및 **보고서**중 하나 또는 둘 다 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-122">In the **Hide and Unhide Columns** dialog box, locate each column that you want to hide, and then deselect one or both of **In Designer** and **In Reports**.</span></span>  
  
4.  <span data-ttu-id="906f8-123">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-123">Click **OK**.</span></span>  
  
### <a name="to-freeze-columns"></a><span data-ttu-id="906f8-124">열을 고정하려면</span><span class="sxs-lookup"><span data-stu-id="906f8-124">To freeze columns</span></span>  
  
1.  <span data-ttu-id="906f8-125">모델 디자이너에서 고정할 열이 포함된 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-125">In the model designer, select the table that contains the columns that you want to freeze.</span></span>  
  
2.  <span data-ttu-id="906f8-126">고정할 열을 하나 이상 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-126">Select one or more columns to freeze.</span></span>  
  
3.  <span data-ttu-id="906f8-127">**열** 메뉴에서 **고정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-127">Click on the **Columns** menu, and then click **Freeze**..</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="906f8-128">열이 고정되면 디자이너에서 테이블의 왼쪽(또는 앞)으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-128">When a column(s) is frozen, it is moved to left (or front) of the table in the designer.</span></span> <span data-ttu-id="906f8-129">나중에 열의 고정을 취소해도 다시 원래 위치로 이동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="906f8-129">Unfreezing the column does not move it back to its original location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="906f8-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="906f8-130">See Also</span></span>  
 <span data-ttu-id="906f8-131">[SSAS 테이블 형식&#41;&#40;테이블 및 열](tables-and-columns-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="906f8-131">[Tables and Columns &#40;SSAS Tabular&#41;](tables-and-columns-ssas-tabular.md) </span></span>  
 <span data-ttu-id="906f8-132">[SSAS 테이블 형식&#41;&#40;큐브 뷰](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="906f8-132">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="906f8-133">역할&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="906f8-133">Roles &#40;SSAS Tabular&#41;</span></span>](roles-ssas-tabular.md)  
  
  
