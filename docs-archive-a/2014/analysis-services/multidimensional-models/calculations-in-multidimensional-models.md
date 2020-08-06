---
title: 다차원 모델의 계산 | Microsoft Docs
ms.custom: ''
ms.date: 12/10/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculations [Analysis Services], creating
- deleting calculations
- calculations [Analysis Services], scripts
- Cube Designer
- modifying scripts
- removing calculations
- calculations [Analysis Services], deleting
- scripts [Analysis Services], calculations
- cubes [Analysis Services], calculations
- solve orders [Analysis Services]
ms.assetid: c21b3459-9bef-45a2-aba5-c992eba5b66e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 64a9733c4fd198a9906e28c437f7ba4fb10dd39a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737156"
---
# <a name="calculations-in-multidimensional-models"></a><span data-ttu-id="becc3-102">다차원 모델의 계산</span><span class="sxs-lookup"><span data-stu-id="becc3-102">Calculations in Multidimensional Models</span></span>
  <span data-ttu-id="becc3-103">큐브 디자이너의 **계산** 탭을 사용하여 계산 멤버, 명명된 집합 및 기타 MDX(Multidimensional Expression) 계산을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-103">Use the **Calculations** tab of Cube Designer to create calculated members, named sets, and other Multidimensional Expressions (MDX) calculations.</span></span>  
  
 <span data-ttu-id="becc3-104">**계산** 탭에는 다음과 같은 세 개의 창이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-104">The **Calculations** tab has the following three panes:</span></span>  
  
-   <span data-ttu-id="becc3-105">**스크립트 구성 도우미** 창 - 큐브의 계산이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-105">The **Script Organizer** pane lists the calculations in a cube.</span></span> <span data-ttu-id="becc3-106">이 창을 사용하여 계산을 만들고 구성하고 선택하여 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-106">Use this pane to create, organize, and select calculations for editing.</span></span>  
  
-   <span data-ttu-id="becc3-107">**계산 도구** 창 - 계산을 만들 때 사용할 수 있는 메타데이터, 함수 및 템플릿을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-107">The **Calculation Tools** pane provides metadata, functions, and templates with which to create calculations.</span></span>  
  
-   <span data-ttu-id="becc3-108">계산 식 창 - 폼 보기와 스크립트 보기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-108">The Calculation Expressions pane supports a form view and a script view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="becc3-109">MDX 스크립팅에 대 한 자세한 내용은 [Microsoft SQL Server 2005의 Mdx 스크립팅 소개](https://go.microsoft.com/fwlink/?LinkId=81892)를 참조 하 고, Microsoft TechNet 웹 사이트의 [SQL Server 2005-Analysis Services](https://go.microsoft.com/fwlink/?LinkId=80853) 페이지에서 추가 리소스 섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="becc3-109">For more information about MDX scripting, see [Introduction to MDX Scripting in Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892), and see the Additional Resources section on the [SQL Server 2005 - Analysis Services](https://go.microsoft.com/fwlink/?LinkId=80853) page on the Microsoft TechNet Web site.</span></span> <span data-ttu-id="becc3-110">큐브 디자인과 관련된 성능 문제에 대한 자세한 내용은 [SQL Server 2005 Analysis Services 성능 가이드(SQL Server 2005 Analysis Services Performance Guide)](https://download.microsoft.com/download/8/5/e/85eea4fa-b3bb-4426-97d0-7f7151b2011c/ssas2005perfguide.doc)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="becc3-110">For more information about performance issues related to cube design, see the [SQL Server 2005 Analysis Services Performance Guide](https://download.microsoft.com/download/8/5/e/85eea4fa-b3bb-4426-97d0-7f7151b2011c/ssas2005perfguide.doc).</span></span>  
  
## <a name="creating-a-new-calculation"></a><span data-ttu-id="becc3-111">새 계산 만들기</span><span class="sxs-lookup"><span data-stu-id="becc3-111">Creating a New Calculation</span></span>  
 <span data-ttu-id="becc3-112">새 계산을 만들려면 큐브 디자이너의 **계산** 탭에서 **큐브** 메뉴를 선택하고 만들려는 계산 유형에 따라 **새 계산 멤버**, **새 명명된 집합**또는 **새 스크립트 명령**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-112">To create a new calculation, on the **Calculations** tab of Cube Designer, on the **Cube** menu, click either **New Calculated Member**, **New Named Set**, or **New Script Command**, depending on the type of calculation you want to create.</span></span> <span data-ttu-id="becc3-113">도구 모음에서 해당 단추를 클릭하거나 **스크립트 구성 도우미** 창에서 아무데나 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 명령 중 하나를 클릭할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-113">You can also click any of the corresponding buttons on the toolbar, or right-click anywhere in the **Script Organizer** pane and then click one of the commands on the shortcut menu.</span></span> <span data-ttu-id="becc3-114">이렇게 하면 **스크립트 구성 도우미** 창에 새 계산이 추가되고 계산 식 창의 계산 폼에 계산에 대한 필드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-114">This action adds a new calculation to the **Script Organizer** pane and displays fields for it in the calculations form in the Calculations Expressions pane.</span></span> <span data-ttu-id="becc3-115">새 스크립트를 만드는 경우에는 계산 식 창에 스크립트 보기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-115">If you create a new script, this action opens the Script view in the Calculation Expressions pane.</span></span> <span data-ttu-id="becc3-116">세 가지 유형의 계산을 작성하는 방법은 [계산 멤버 만들기](create-calculated-members.md), [명명된 집합 만들기](create-named-sets.md)및 [할당 및 기타 스크립트 명령 정의](define-assignments-and-other-script-commands.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="becc3-116">For more information about building the three types of calculations, see [Create Calculated Members](create-calculated-members.md), [Create Named Sets](create-named-sets.md), and [Define Assignments and Other Script Commands](define-assignments-and-other-script-commands.md).</span></span>  
  
## <a name="editing-scripts"></a><span data-ttu-id="becc3-117">스크립트 편집</span><span class="sxs-lookup"><span data-stu-id="becc3-117">Editing Scripts</span></span>  
 <span data-ttu-id="becc3-118">**계산** 탭의 계산 식 창에서 스크립트를 편집 합니다. 계산 식 창에는 스크립트 보기와 폼 보기의 두 가지 뷰가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-118">Edit scripts in the Calculation Expressions pane of the **Calculations** tab. The Calculation Expressions pane has two views, Script view and Form view.</span></span> <span data-ttu-id="becc3-119">폼 보기에는 단일 명령에 대한 식과 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-119">The Form view shows the expressions and properties for a single command.</span></span> <span data-ttu-id="becc3-120">MDX 스크립트를 편집할 때는 식 상자가 전체 폼 보기를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-120">When you edit an MDX script, an expression box fills the entire Form view.</span></span>  
  
 <span data-ttu-id="becc3-121">스크립트 보기에는 스크립트를 편집할 수 있는 코드 편집기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-121">The Script view provides a code editor in which to edit the scripts.</span></span> <span data-ttu-id="becc3-122">계산 식 창이 스크립트 보기 상태에 있는 경우에는 **스크립트 구성 도우미** 창이 사라집니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-122">While the Calculation Expressions pane is in Script view, the **Script Organizer** pane is hidden.</span></span> <span data-ttu-id="becc3-123">스크립트 보기는 색 구분, 괄호 일치, 자동 완성 및 MDX 코드 영역을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-123">The Script view provides color coding, parenthesis matching, auto-complete, and MDX code regions.</span></span> <span data-ttu-id="becc3-124">편집하기 쉽도록 MDX 코드 영역을 축소하거나 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-124">The MDX code regions can be collapsed or expanded to facilitate editing.</span></span>  
  
 <span data-ttu-id="becc3-125">**큐브** 메뉴에서 **계산 표시 위치**를 가리킨 다음 **스크립트** 또는 **폼**을 클릭하여 폼 보기와 스크립트 보기 간에 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-125">You can switch between the Form view and the Script view by clicking the **Cube** menu, pointing to **Show Calculations in**, and then clicking **Script** or **Form**.</span></span> <span data-ttu-id="becc3-126">도구 모음에서 **폼 보기** 또는 **스크립트 보기** 를 클릭하여 전환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-126">You can also click either **Form view** or **Script view** on the toolbar.</span></span>  
  
## <a name="changing-solve-order"></a><span data-ttu-id="becc3-127">계산 순서 변경</span><span class="sxs-lookup"><span data-stu-id="becc3-127">Changing Solve Order</span></span>  
 <span data-ttu-id="becc3-128">계산은 **스크립트 구성 도우미** 창에 나열된 순서로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-128">Calculations are solved in the order listed in the **Script Organizer** pane.</span></span> <span data-ttu-id="becc3-129">계산을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **위로 이동** 또는 **아래로 이동** 을 클릭하여 계산 순서를 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-129">You can reorder the calculations by right-clicking any calculation and then clicking **Move Up** or **Move Down** on the shortcut menu.</span></span> <span data-ttu-id="becc3-130">계산을 클릭한 다음 도구 모음에서 **위로 이동** 또는 **아래로 이동** 단추를 클릭할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-130">You can also click a calculation and then click the **Move Up** or **Move Down** button on the toolbar.</span></span>  
  
 <span data-ttu-id="becc3-131">계산 셀과 계산 멤버에 대한 계산 순서를 수동으로 다시 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-131">You can override this order manually for calculated cells and calculated members.</span></span> <span data-ttu-id="becc3-132">패스 순서 및 계산 순서에 대한 자세한 내용은 [패스 순서 및 계산 순서 이해&#40;MDX&#41;](mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="becc3-132">For more information about pass order and solve order, see [Understanding Pass Order and Solve Order &#40;MDX&#41;](mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md).</span></span>  
  
## <a name="deleting-a-calculation"></a><span data-ttu-id="becc3-133">계산 삭제</span><span class="sxs-lookup"><span data-stu-id="becc3-133">Deleting a Calculation</span></span>  
 <span data-ttu-id="becc3-134">기존 계산을 삭제하려면 **스크립트 구성 도우미** 창의 **계산** 탭에서 삭제할 계산을 선택하고 **편집** 메뉴에서 **삭제** 를 클릭하거나 도구 모음에서 **삭제** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-134">To delete an existing calculation, on the **Calculations** tab, in the **Script Organizer** pane, select the calculation to be deleted, and then click **Delete** on the **Edit** menu or click the **Delete** icon on the toolbar.</span></span> <span data-ttu-id="becc3-135">**스크립트 구성 도우미** 창에서 계산을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **삭제** 를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="becc3-135">You can also right-click the calculation in the **Script Organizer** pane and select **Delete** from the short-cut menu.</span></span>  
  
  
