---
title: 사용자 정의 계층 추가 또는 삭제 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], adding
- removing hierarchies
- adding hierarchies
- deleting hierarchies
- hierarchies [Analysis Services], removing
ms.assetid: 953818b4-9543-4c01-bb20-1d45ec6dfb91
author: minewiskan
ms.author: owend
ms.openlocfilehash: d20404a1d93d57221eb830366392eb90600f26c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652389"
---
# <a name="add-or-delete-a-user-defined-hierarchy"></a><span data-ttu-id="26bfd-102">사용자 정의 계층 추가 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="26bfd-102">Add or Delete a User-Defined Hierarchy</span></span>
  <span data-ttu-id="26bfd-103">**의 차원 디자이너에 있는** 차원 구조 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]탭의 차원에서 사용자 정의 계층을 추가하거나 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26bfd-103">You add a user-defined hierarchy to or remove a user-defined hierarchy from a dimension on the **Dimension Structure** tab in Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="26bfd-104">사용자 정의 계층을 추가하는 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서 계층이 인스턴스화되고 해당 차원이 처리되어야만 사용자가 계층을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26bfd-104">When you add a user-defined hierarchy, it is not available to users until it is instantiated in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and the dimension is processed.</span></span> <span data-ttu-id="26bfd-105">자세한 내용은 [SSAS&#41;&#40;다차원 모델 데이터베이스](multidimensional-model-databases-ssas.md) 및 [다차원 모델 개체 처리](processing-a-multidimensional-model-analysis-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="26bfd-105">For more information, see [Multidimensional Model Databases &#40;SSAS&#41;](multidimensional-model-databases-ssas.md) and [Multidimensional Model Object Processing](processing-a-multidimensional-model-analysis-services.md).</span></span>  
  
### <a name="to-add-a-user-defined-hierarchy-to-a-dimension"></a><span data-ttu-id="26bfd-106">차원에 사용자 정의 계층을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="26bfd-106">To add a user-defined hierarchy to a dimension</span></span>  
  
1.  <span data-ttu-id="26bfd-107">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 해당 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트를 연 다음 작업할 차원을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="26bfd-107">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the appropriate [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, and then open the dimension with which you want to work.</span></span>  
  
     <span data-ttu-id="26bfd-108">차원은 차원 디자이너의 **차원 구조** 탭에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="26bfd-108">The dimension opens in Dimension Designer on the **Dimension Structure** tab.</span></span>  
  
2.  <span data-ttu-id="26bfd-109">**특성** 창에서 사용자 정의 계층에 사용할 특성을 **계층** 창으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="26bfd-109">From the **Attributes** pane, drag an attribute that you want to use in the user-defined hierarchy to the **Hierarchies** pane.</span></span>  
  
3.  <span data-ttu-id="26bfd-110">사용자 정의 계층에서 수준을 형성할 추가 특성을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="26bfd-110">Drag additional attributes to form levels in the user-defined hierarchy.</span></span>  
  
     <span data-ttu-id="26bfd-111">계층에서 특성이 나열되는 순서는 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="26bfd-111">The order in which attributes are listed in the hierarchy is important.</span></span> <span data-ttu-id="26bfd-112">예를 들어 시간 계층의 연도는 계층 목록에서 일보다 상위에 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26bfd-112">For example, in a time hierarchy, years should appear higher in the hierarchy list than days.</span></span>  
  
4.  <span data-ttu-id="26bfd-113">필요에 따라 사용자 정의 계층에서 수준을 올바른 위치로 끌어 수준을 다시 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="26bfd-113">Optionally, rearrange the levels in the user-defined hierarchy by dragging them to the correct positions.</span></span>  
  
5.  <span data-ttu-id="26bfd-114">필요에 따라 사용자 정의 계층이나 해당 수준의 속성을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="26bfd-114">Optionally, modify properties of the user-defined hierarchy or its levels.</span></span>  
  
     <span data-ttu-id="26bfd-115">예를 들어 일반적으로 사용자 정의 계층의 이름을 지정하고 해당 수준의 이름을 하나 이상 바꾸며 All 수준의 사용자 지정 이름을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26bfd-115">For example, you might want to specify a name for the user-defined hierarchy, rename one or more of its levels, and define a custom name for the All level.</span></span> <span data-ttu-id="26bfd-116">자세한 내용은 [사용자 계층 속성](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)및 [수준 속성 &#91;Paved Over&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="26bfd-116">For more information, see [User Hierarchy Properties](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md), and [Level Properties &#91;Paved Over&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="26bfd-117">기본적으로 사용자 정의 계층은 단순히 사용자가 정보를 보기 위해 드릴다운할 수 있는 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="26bfd-117">By default, a user-defined hierarchy is just a path that enables users to drill down for information.</span></span> <span data-ttu-id="26bfd-118">그러나 수준 간에 관계가 있으면 수준 간의 특성 관계를 구성하여 쿼리 성능을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26bfd-118">However, if relationships exist between levels, you can increase query performance by configuring attribute relationships between levels.</span></span> <span data-ttu-id="26bfd-119">자세한 내용은 [특성 관계](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md) 및 [특성 관계 정의](attribute-relationships-define.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26bfd-119">For more information, see [Attribute Relationships](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md) and [Define Attribute Relationships](attribute-relationships-define.md).</span></span>  
  
### <a name="to-remove-a-user-defined-hierarchy-from-a-dimension"></a><span data-ttu-id="26bfd-120">차원에서 사용자 정의 계층을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="26bfd-120">To remove a user-defined hierarchy from a dimension</span></span>  
  
-   <span data-ttu-id="26bfd-121">**차원 구조** 탭의 **계층** 창에서 제거할 사용자 정의 계층을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26bfd-121">On the **Dimension Structure** tab, click the user-defined hierarchy that you want to remove in the **Hierarchies** pane.</span></span> <span data-ttu-id="26bfd-122">도구 모음에서 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26bfd-122">On the toolbar, click **Delete**.</span></span>  
  
     - <span data-ttu-id="26bfd-123">또는</span><span class="sxs-lookup"><span data-stu-id="26bfd-123">or -</span></span>  
  
-   <span data-ttu-id="26bfd-124">**계층** 창에서 제거할 사용자 정의 계층을 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26bfd-124">Right-click the user-defined hierarchy that you want to remove in the **Hierarchies** pane and then click **Delete**.</span></span>  
  
     - <span data-ttu-id="26bfd-125">또는</span><span class="sxs-lookup"><span data-stu-id="26bfd-125">or -</span></span>  
  
-   <span data-ttu-id="26bfd-126">사용자 정의 계층을 디자인 화면 밖으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="26bfd-126">Drag the user-defined hierarchy off of the design surface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26bfd-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="26bfd-127">See Also</span></span>  
 <span data-ttu-id="26bfd-128">[사용자 계층](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="26bfd-128">[User Hierarchies](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md) </span></span>  
 [<span data-ttu-id="26bfd-129">사용자 정의 계층 만들기</span><span class="sxs-lookup"><span data-stu-id="26bfd-129">Create User-Defined Hierarchies</span></span>](user-defined-hierarchies-create.md)  
  
  
