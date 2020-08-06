---
title: 다차원 모델의 큐브 뷰 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- default members
- hiding objects from perspective
- renaming perspectives
- attributes [Analysis Services], default members
- removing perspectives
- perspectives [Analysis Services]
- names [Analysis Services], perspectives
- cubes [Analysis Services], perspectives
- deleting perspectives
ms.assetid: 5a3d6577-6833-4c24-820c-b65bb856157b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2d4be87ddbd691710b361d8b07d225bce37659fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648647"
---
# <a name="perspectives-in-multidimensional-models"></a><span data-ttu-id="922e4-102">다차원 모델의 큐브 뷰</span><span class="sxs-lookup"><span data-stu-id="922e4-102">Perspectives in Multidimensional Models</span></span>
  <span data-ttu-id="922e4-103">큐브 뷰는 특정 애플리케이션이나 사용자 그룹을 위해 생성된 큐브 하위 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-103">A perspective is a subset of a cube created for a particular application or group of users.</span></span> <span data-ttu-id="922e4-104">큐브 자체가 기본 큐브 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-104">The cube itself is the default perspective.</span></span> <span data-ttu-id="922e4-105">큐브 뷰는 큐브로 클라이언트에게 노출됩니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-105">A perspective is exposed to a client as a cube.</span></span> <span data-ttu-id="922e4-106">큐브 뷰는 사용자에게 다른 큐브와 같게 보입니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-106">When a user views a perspective, it appears like another cube.</span></span> <span data-ttu-id="922e4-107">큐브 뷰에서 쓰기 저장을 통해 큐브 데이터를 변경하면 원본 큐브에 변경 내용이 반영됩니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-107">Any changes made to cube data through writeback in the perspective are to the original cube.</span></span> <span data-ttu-id="922e4-108">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 뷰에 대한 자세한 내용은 [큐브 뷰](../multidimensional-models-olap-logical-cube-objects/perspectives.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="922e4-108">For more information about the views in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], see [Perspectives](../multidimensional-models-olap-logical-cube-objects/perspectives.md).</span></span>  
  
 <span data-ttu-id="922e4-109">큐브 디자이너의 **큐브 뷰** 탭을 사용하여 큐브에 큐브 뷰를 만들거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-109">Use the **Perspectives** tab in Cube Designer to create or modify perspectives in a cube.</span></span> <span data-ttu-id="922e4-110">**큐브 뷰** 탭의 첫 번째 열은 큐브의 모든 개체가 나열된 **큐브 개체** 열입니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-110">The first column of the **Perspectives** tab is the **Cube Objects** column, which lists all the objects in the cube.</span></span> <span data-ttu-id="922e4-111">이 열은 큐브의 기본 큐브 뷰에 해당되며, 큐브 자체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-111">This corresponds to the default perspective for the cube, which is the cube itself.</span></span>  
  
## <a name="creating-or-deleting-perspectives"></a><span data-ttu-id="922e4-112">큐브 뷰 만들기 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="922e4-112">Creating or Deleting Perspectives</span></span>  
 <span data-ttu-id="922e4-113">**큐브** 메뉴의 **새 큐브 뷰** 를 클릭하여 **큐브 뷰** 탭에 큐브 뷰를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-113">You can add a perspective to the **Perspectives** tab by clicking **New Perspective** on the **Cube** menu.</span></span> <span data-ttu-id="922e4-114">도구 모음의 **새 큐브 뷰** 단추를 클릭하거나 창의 아무 곳이나 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **새 큐브 뷰** 를 클릭해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-114">You can also click the **New Perspective** button on the toolbar, or right-click anywhere in the pane and click **New Perspective** on the shortcut menu.</span></span> <span data-ttu-id="922e4-115">큐브에 큐브 뷰를 얼마든지 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-115">You can add any number of perspectives to a cube.</span></span>  
  
 <span data-ttu-id="922e4-116">큐브 뷰를 제거하려면 먼저 삭제할 큐브 뷰에 해당하는 열에서 아무 셀이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-116">To remove a perspective, first click any cell in the column for the perspective that you want to delete.</span></span> <span data-ttu-id="922e4-117">그런 다음 **큐브** 메뉴에서 **큐브 뷰 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-117">Then, on the **Cube** menu, click **Delete Perspective**.</span></span> <span data-ttu-id="922e4-118">도구 모음에서 **큐브 뷰 삭제** 단추를 클릭하거나 삭제할 큐브 뷰에서 아무 셀이나 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **큐브 뷰 삭제** 를 클릭해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-118">You can also click the **Delete Perspective** button on the toolbar, or right-click any cell in the perspective you want to delete, and then click **Delete Perspective** on the shortcut menu.</span></span>  
  
## <a name="renaming-perspectives"></a><span data-ttu-id="922e4-119">큐브 뷰 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="922e4-119">Renaming Perspectives</span></span>  
 <span data-ttu-id="922e4-120">각 큐브 뷰의 첫 번째 행에 큐브 뷰의 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-120">The first row of each perspective shows its name.</span></span> <span data-ttu-id="922e4-121">큐브 뷰를 만들면 처음에는 이름이 Perspective입니다. Perspective라는 큐브 뷰가 이미 있는 경우에는 1부터 시작하는 서수가 뒤에 붙습니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-121">When you create a perspective, the name is initially Perspective (followed by an ordinal number, starting with 1, if there is already a perspective called Perspective).</span></span> <span data-ttu-id="922e4-122">이름을 클릭하고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-122">You can click the name to edit it.</span></span>  
  
## <a name="hiding-objects-from-a-perspective"></a><span data-ttu-id="922e4-123">큐브 뷰에서 개체 숨기기</span><span class="sxs-lookup"><span data-stu-id="922e4-123">Hiding Objects from a Perspective</span></span>  
 <span data-ttu-id="922e4-124">큐브 뷰에서 개체를 숨기려면 큐브 뷰 열에서 해당 개체에 대한 행에 있는 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-124">To hide an object from a perspective, clear the check box in the row that corresponds to the object in the column for the perspective.</span></span> <span data-ttu-id="922e4-125">큐브 뷰에서 숨길 수 있는 큐브 개체는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-125">The cube objects that can be hidden from a perspective are:</span></span>  
  
-   <span data-ttu-id="922e4-126">측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="922e4-126">Measure groups</span></span>  
  
-   <span data-ttu-id="922e4-127">측정값</span><span class="sxs-lookup"><span data-stu-id="922e4-127">Measures</span></span>  
  
-   <span data-ttu-id="922e4-128">차원</span><span class="sxs-lookup"><span data-stu-id="922e4-128">Dimensions</span></span>  
  
-   <span data-ttu-id="922e4-129">계층 구조</span><span class="sxs-lookup"><span data-stu-id="922e4-129">Hierarchies</span></span>  
  
-   <span data-ttu-id="922e4-130">명명된 집합</span><span class="sxs-lookup"><span data-stu-id="922e4-130">Named sets</span></span>  
  
-   <span data-ttu-id="922e4-131">KPI</span><span class="sxs-lookup"><span data-stu-id="922e4-131">KPIs</span></span>  
  
-   <span data-ttu-id="922e4-132">동작</span><span class="sxs-lookup"><span data-stu-id="922e4-132">Actions</span></span>  
  
-   <span data-ttu-id="922e4-133">계산 멤버</span><span class="sxs-lookup"><span data-stu-id="922e4-133">Calculated members</span></span>  
  
 <span data-ttu-id="922e4-134">개체를 표시하려면**큐브 개체**에서 해당 개체 유형에 대한 범주( **측정값 그룹**, **차원**, **KPI**, **계산**또는 **동작**)를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-134">To view any object, expand the category (**Measure Groups**, **Dimensions**, **KPIs**, **Calculations**, or **Actions**) for any object type under **Cube Objects**.</span></span> <span data-ttu-id="922e4-135">차원의 계층이나 특성을 표시하려면 먼저 차원을 확장한 다음 **계층** 또는 **특성** 행을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-135">To view hierarchies or attributes in a dimension, first expand a dimension, and then expand the **Hierarchies** or **Attributes** row.</span></span> <span data-ttu-id="922e4-136">측정값 그룹의 측정값을 표시하려면 측정값 그룹을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="922e4-136">To view measures in a measure group, expand the measure group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="922e4-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="922e4-137">See Also</span></span>  
 [<span data-ttu-id="922e4-138">다차원 모델의 큐브</span><span class="sxs-lookup"><span data-stu-id="922e4-138">Cubes in Multidimensional Models</span></span>](cubes-in-multidimensional-models.md)  
  
  
