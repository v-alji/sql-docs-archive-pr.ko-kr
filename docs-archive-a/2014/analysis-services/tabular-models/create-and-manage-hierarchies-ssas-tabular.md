---
title: 계층 만들기 및 관리 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8dd30cd0-a831-4d25-b577-648d7f3c7fa6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0bab3e09aadb4e0c857b9c1da3111e03e90f777e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649209"
---
# <a name="create-and-manage-hierarchies-ssas-tabular"></a><span data-ttu-id="e78d6-102">계층 만들기 및 관리(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="e78d6-102">Create and Manage Hierarchies (SSAS Tabular)</span></span>
  <span data-ttu-id="e78d6-103">모델 디자이너(다이어그램 뷰)에서 계층을 만들고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-103">Hierarchies can be created and managed in the model designer, in Diagram View.</span></span> <span data-ttu-id="e78d6-104">모델 디자이너(다이어그램 뷰)를 보려면 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 **모델** 메뉴를 클릭하고 **모델 뷰**를 가리킨 다음 **다이어그램 뷰**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-104">To view the model designer in Diagram View, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Model** menu, then point to **Model View**, and then click **Diagram View**.</span></span>  
  
 <span data-ttu-id="e78d6-105">이 항목에는 다음 태스크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-105">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="e78d6-106">계층 만들기</span><span class="sxs-lookup"><span data-stu-id="e78d6-106">Create a Hierarchy</span></span>](#bkmk_create)  
  
-   [<span data-ttu-id="e78d6-107">계층 편집</span><span class="sxs-lookup"><span data-stu-id="e78d6-107">Edit a Hierarchy</span></span>](#bkmk_edit)  
  
-   [<span data-ttu-id="e78d6-108">계층 삭제</span><span class="sxs-lookup"><span data-stu-id="e78d6-108">Delete a Hierarchy</span></span>](#bkmk_delete)  
  
##  <a name="create-a-hierarchy"></a><a name="bkmk_create"></a> <span data-ttu-id="e78d6-109">계층 만들기</span><span class="sxs-lookup"><span data-stu-id="e78d6-109">Create a Hierarchy</span></span>  
 <span data-ttu-id="e78d6-110">열 및 테이블의 상황에 맞는 메뉴를 사용하여 계층을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-110">You can create a hierarchy by using the columns and table context menu.</span></span> <span data-ttu-id="e78d6-111">계층을 만들면 새 부모 수준이 자식 수준으로 선택한 열과 함께 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-111">When you create a hierarchy, a new parent level displays with selected columns as child levels.</span></span>  
  
#### <a name="to-create-a-hierarchy-from-the-context-menu"></a><span data-ttu-id="e78d6-112">상황에 맞는 메뉴에서 계층을 만들려면</span><span class="sxs-lookup"><span data-stu-id="e78d6-112">To create a hierarchy from the context menu</span></span>  
  
1.  <span data-ttu-id="e78d6-113">모델 디자이너(다이어그램 뷰)의 테이블 창에서 열을 마우스 오른쪽 단추로 클릭한 다음 **계층 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-113">In the model designer (Diagram View), in a table window, right-click on a column, and then click **Create Hierarchy**.</span></span>  
  
     <span data-ttu-id="e78d6-114">여러 열을 선택하려면 각 열을 클릭한 다음 마우스 오른쪽 단추를 클릭하여 상황에 맞는 메뉴를 열고 **계층 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-114">To select multiple columns, click each column, then right-click to open the context menu, and then click **Create Hierarchy**.</span></span>  
  
     <span data-ttu-id="e78d6-115">부모 계층 수준이 테이블 창의 맨 아래에 만들어지고 선택한 열이 계층 아래에 자식 수준으로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-115">A parent hierarchy level is created at the bottom of the table window and the selected columns are copied under the hierarchy as child levels.</span></span>  
  
2.  <span data-ttu-id="e78d6-116">계층의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-116">Type a name for the hierarchy.</span></span>  
  
 <span data-ttu-id="e78d6-117">열을 복사 하는 계층의 부모 수준으로 추가 열을 끌어 놓을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-117">You can drag additional columns into your hierarchy's parent level, which copies the columns.</span></span> <span data-ttu-id="e78d6-118">끈 열을 계층에서 해당 열을 표시하려는 위치의 자식 수준에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-118">Drop the child level to place it where you want it to appear in the hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e78d6-119">하나 이상의 열과 함께 측정값을 여러 개 선택하거나 여러 테이블의 열을 선택할 경우 계층 만들기 명령이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-119">The Create Hierarchy command is disabled in the context menu if you multi-select a measure along with one or more columns or you select columns from multiple tables.</span></span>  
  
##  <a name="edit-a-hierarchy"></a><a name="bkmk_edit"></a><span data-ttu-id="e78d6-120">계층 편집</span><span class="sxs-lookup"><span data-stu-id="e78d6-120">Edit a Hierarchy</span></span>  
 <span data-ttu-id="e78d6-121">계층 이름 바꾸기, 자식 수준 이름 바꾸기, 자식 수준 순서 변경, 다른 열을 자식 수준으로 추가, 계층에서 자식 수준 제거, 자식 수준의 원본 이름(열 이름) 표시, 계층 부모 수준과 이름이 동일한 자식 수준 숨기기 등의 편집 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-121">You can rename a hierarchy, rename a child level, change the order of the child levels, add additional columns as child levels, remove a child level from a hierarchy, show the source name of a child level (the column name), and hide a child level if it has the same name as the hierarchy parent level.</span></span>  
  
#### <a name="to-change-the-name-of-a-hierarchy-or-child-level"></a><span data-ttu-id="e78d6-122">계층 또는 자식 수준의 이름을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="e78d6-122">To change the name of a hierarchy or child level</span></span>  
  
1.  <span data-ttu-id="e78d6-123">계층 부모 수준 또는 자식 수준을 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-123">Right-click the hierarchy parent level or a child level, and the click **Rename**.</span></span>  
  
2.  <span data-ttu-id="e78d6-124">새 이름을 입력하거나 기존 이름을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-124">Type a new name or edit the existing name.</span></span>  
  
#### <a name="to-change-the-order-of-a-child-level-in-a-hierarchy"></a><span data-ttu-id="e78d6-125">계층의 자식 수준 순서를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="e78d6-125">To change the order of a child level in a hierarchy</span></span>  
  
-   <span data-ttu-id="e78d6-126">자식 수준을 클릭하여 계층의 새 위치로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-126">Click and drag a child level into a new position in the hierarchy.</span></span>  
  
-   <span data-ttu-id="e78d6-127">또는 계층의 자식 수준을 마우스 오른쪽 단추로 클릭하고, 위로 이동을 클릭하여 목록의 위쪽 수준으로 이동하거나 아래로 이동을 클릭하여 목록의 아래쪽 수준으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-127">Or, right-click a child level of the hierarchy, and then click Move Up to move the level up in the list, or click Move Down to move the level down in the list.</span></span>  
  
-   <span data-ttu-id="e78d6-128">또는 자식 수준을 클릭하여 선택한 다음 Alt + 위쪽 화살표를 클릭하여 목록에서 상위 수준으로 이동하거나, Alt + 아래쪽 화살표를 클릭하여 하위 수준으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-128">Or, click a child level to select it, and then press Alt + Up Arrow to move the level up, or press Alt+Down Arrow to move the level down in the list.</span></span>  
  
#### <a name="to-add-another-child-level-to-a-hierarchy"></a><span data-ttu-id="e78d6-129">계층에 다른 자식 수준을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="e78d6-129">To add another child level to a hierarchy</span></span>  
  
-   <span data-ttu-id="e78d6-130">열을 클릭하고 부모 수준으로 끌거나 계층의 특정 위치로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-130">Click and drag a column onto the parent level or into a specific location of the hierarchy.</span></span> <span data-ttu-id="e78d6-131">그러면 해당 열이 계층의 자식 수준으로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-131">The column is copied as a child level of the hierarchy.</span></span>  
  
-   <span data-ttu-id="e78d6-132">또는 열을 마우스 오른쪽 단추로 클릭하고 **계층에 추가**를 가리킨 다음 계층을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-132">Or, right-click a column, point to **Add to Hierarchy**, and then click the hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e78d6-133">보고서에서 숨겨진 열을 계층에 자식 수준으로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-133">You can add a hidden column (a column that is hidden from reports) as a child level to the hierarchy.</span></span> <span data-ttu-id="e78d6-134">자식 수준은 숨겨지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-134">The child level is not hidden.</span></span>  
  
#### <a name="to-remove-a-child-level-from-a-hierarchy"></a><span data-ttu-id="e78d6-135">계층에서 자식 수준을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="e78d6-135">To remove a child level from a hierarchy</span></span>  
  
-   <span data-ttu-id="e78d6-136">자식 수준을 마우스 오른쪽 단추로 클릭하고 **계층에서 제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-136">Right-click a child level, and then click **Remove from Hierarchy**.</span></span>  
  
-   <span data-ttu-id="e78d6-137">또는 계층의 자식 수준을 클릭하고 **Delete**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-137">Or, click a child level, and then press **Delete**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e78d6-138">계층 자식 수준의 이름을 바꿀 경우 해당 자식 수준은 더 이상 자식 수준을 복사하는 데 사용된 열과 동일한 이름을 공유하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-138">If you rename a hierarchy child level, it no longer shares the same name as the column that it is copied from.</span></span> <span data-ttu-id="e78d6-139">**원본 열 이름 표시** 명령을 사용하여 복사해 온 원본 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-139">Use the **Show Source Name** command to see which column it was copied from.</span></span>  
  
#### <a name="to-show-a-source-name"></a><span data-ttu-id="e78d6-140">원본 이름을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="e78d6-140">To show a source name</span></span>  
  
-   <span data-ttu-id="e78d6-141">계층 자식 수준을 마우스 오른쪽 단추로 클릭하고 **원본 이름 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-141">Right-click a hierarchy child level, and then click **Show Source Name**.</span></span> <span data-ttu-id="e78d6-142">복사해 온 원본 열의 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-142">The name of the column that it was copied from appears.</span></span>  
  
##  <a name="delete-a-hierarchy"></a><a name="bkmk_delete"></a><span data-ttu-id="e78d6-143">계층 삭제</span><span class="sxs-lookup"><span data-stu-id="e78d6-143">Delete a Hierarchy</span></span>  
  
#### <a name="to-delete-a-hierarchy-and-remove-its-child-levels"></a><span data-ttu-id="e78d6-144">계층을 삭제하고 자식 수준을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="e78d6-144">To delete a hierarchy and remove its child levels</span></span>  
  
-   <span data-ttu-id="e78d6-145">부모 계층 수준을 마우스 오른쪽 단추로 클릭하고 계층 삭제를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-145">Right-click the parent hierarchy level, and then click Delete Hierarchy.</span></span>  
  
-   <span data-ttu-id="e78d6-146">또는 부모 계층 수준을 클릭하고 Delete 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-146">Or, click the parent hierarchy level, and then press Delete.</span></span> <span data-ttu-id="e78d6-147">이 경우 모든 자식 수준도 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="e78d6-147">This also removes all the child levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e78d6-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e78d6-148">See Also</span></span>  
 <span data-ttu-id="e78d6-149">[테이블 형식 모델 디자이너 &#40;SSAS 테이블 형식&#41;](../tabular-model-designer-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="e78d6-149">[Tabular Model Designer &#40;SSAS Tabular&#41;](../tabular-model-designer-ssas-tabular.md) </span></span>  
 <span data-ttu-id="e78d6-150">[계층 &#40;SSAS 테이블 형식&#41;](hierarchies-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="e78d6-150">[Hierarchies &#40;SSAS Tabular&#41;](hierarchies-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="e78d6-151">측정값&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="e78d6-151">Measures &#40;SSAS Tabular&#41;</span></span>](measures-ssas-tabular.md)  
  
  
