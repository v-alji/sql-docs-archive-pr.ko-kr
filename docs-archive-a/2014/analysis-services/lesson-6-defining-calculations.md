---
title: '6 단원: 계산 정의 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e0a1e354-e879-4eb8-bb2b-6c3809e32cb6
author: minewiskan
ms.author: owend
ms.openlocfilehash: e0b3f7e925a11146204dc6c55e9ddd6820ecb802
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649775"
---
# <a name="lesson-6-defining-calculations"></a><span data-ttu-id="cd10e-102">6단원: 계산 정의</span><span class="sxs-lookup"><span data-stu-id="cd10e-102">Lesson 6: Defining Calculations</span></span>
  <span data-ttu-id="cd10e-103">이 단원에서는 MDX(Multidimensional Expressions) 식 또는 스크립트에 해당하는 계산을 정의하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-103">In this lesson, you learn to define calculations, which are Multidimensional Expressions (MDX) expressions or scripts.</span></span> <span data-ttu-id="cd10e-104">계산을 사용하면 계산 멤버와 명명된 집합을 정의하고 기타 스크립트 명령을 실행하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 큐브의 기능을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-104">Calculations enable you to define calculated members, named sets, and execute other script commands to extend the capabilities of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube.</span></span> <span data-ttu-id="cd10e-105">예를 들어 스크립트 명령을 실행하여 하위 큐브를 정의한 다음 하위 큐브의 셀에 계산을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-105">For example, you can run a script command to define a subcube and then assign a calculation to the cells in the subcube.</span></span>  
  
 <span data-ttu-id="cd10e-106">큐브 디자이너에서 새 계산을 정의하면 큐브 디자이너의 **계산** 탭에 있는 **스크립트 구성 도우미** 창에 해당 계산이 추가되며 **계산 식** 창의 계산 폼에 특정 계산 유형에 대한 필드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-106">When you define a new calculation in Cube Designer, the calculation is added to the **Script Organizer** pane of the **Calculations** tab of Cube Designer, and the fields for the particular calculation type are displayed in a calculations form in the **Calculation Expressions** pane.</span></span> <span data-ttu-id="cd10e-107">계산은 **스크립트 구성 도우미** 창에 나열된 순서대로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-107">Calculations are executed in the order in which they are listed in the **Script Organizer** pane.</span></span> <span data-ttu-id="cd10e-108">특정 계산을 마우스 오른쪽 단추로 클릭한 후 **위로 이동** 또는 **아래로 이동**을 선택하거나 특정 계산을 클릭한 후 **계산** 탭 도구 모음에 있는 **위로 이동** 또는 **아래로 이동** 아이콘을 사용하여 계산 순서를 다시 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-108">You can reorder the calculations by right-clicking on a particular calculation and then selecting **Move Up** or **Move Down**, or by clicking a particular calculation and then using the **Move Up** or **Move Down** icons on the toolbar of the **Calculations** tab.</span></span>  
  
 <span data-ttu-id="cd10e-109">**계산** 탭에서 새 계산을 추가하고 **계산 식** 창의 다음 보기 중 하나에서 기존 계산을 보거나 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-109">On the **Calculations** tab, you can add new calculations and view or edit existing calculations in the following views in the **Calculation Expressions** pane:</span></span>  
  
-   <span data-ttu-id="cd10e-110">폼 보기.</span><span class="sxs-lookup"><span data-stu-id="cd10e-110">Form view.</span></span> <span data-ttu-id="cd10e-111">이 보기는 단일 명령에 대한 식 및 속성을 그래픽 형식으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-111">This view shows the expressions and properties for a single command in a graphical format.</span></span> <span data-ttu-id="cd10e-112">MDX 스크립트를 편집하면 폼 보기가 식 상자로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-112">When you edit an MDX script, an expression box fills the Form view.</span></span>  
  
-   <span data-ttu-id="cd10e-113">스크립트 보기.</span><span class="sxs-lookup"><span data-stu-id="cd10e-113">Script view.</span></span> <span data-ttu-id="cd10e-114">이 보기에서는 모든 계산 스크립트가 코드 편집기에 표시되므로 계산 스크립트를 쉽게 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-114">This view displays all calculation scripts in a code editor, which lets you easily change the calculation scripts.</span></span> <span data-ttu-id="cd10e-115">**계산 식** 창이 스크립트 보기에 표시되면 **스크립트 구성 도우미** 가 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-115">When the **Calculation Expressions** pane is in Script view, the **Script Organizer** is hidden.</span></span> <span data-ttu-id="cd10e-116">스크립트 보기는 색 구분, 괄호 일치, 자동 완성 및 MDX 코드 영역을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-116">The Script view provides color coding, parenthesis matching, auto-complete, and MDX code regions.</span></span> <span data-ttu-id="cd10e-117">보다 쉬운 편집 작업을 위해 MDX 코드 영역을 확장하거나 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-117">You can expand or collapse the MDX code regions to make editing easier.</span></span>  
  
 <span data-ttu-id="cd10e-118">**계산 식** 창에서 이러한 보기 간 전환을 하려면 **계산** 탭 도구 모음에서 **폼 보기** 또는 **스크립트 보기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-118">To switch between these views in the **Calculation Expressions** pane, click **Form View** or **Script View** on the toolbar of the **Calculations** tab.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd10e-119">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 가 계산에서 구문 오류를 검색하면 스크립트 보기에서 오류를 수정할 때까지 폼 보기가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-119">If [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] detects a syntax error in any calculation, the Form view will not display until the error is corrected in the Script view.</span></span>  
  
 <span data-ttu-id="cd10e-120">비즈니스 인텔리전스 마법사를 사용하여 큐브에 특정 계산을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-120">You can also use the Business Intelligence Wizard to add certain calculations to a cube.</span></span> <span data-ttu-id="cd10e-121">예를 들어 이 마법사를 사용하여 큐브에 시간 인텔리전스를 추가할 수 있습니다. 즉, 월간 누계, 이동 평균 또는 기간별 누계와 같은 시간 관련 계산에 대한 계산 멤버를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-121">For example, you can use this wizard to add time intelligence to a cube, which means defining calculated members for time-related calculations such as period-to-date, moving averages, or period over period growth.</span></span> <span data-ttu-id="cd10e-122">자세한 내용은 [비즈니스 인텔리전스 마법사를 사용하여 시간 인텔리전스 계산 정의](multidimensional-models/define-time-intelligence-calculations-using-the-business-intelligence-wizard.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd10e-122">For more information, see [Define Time Intelligence Calculations using the Business Intelligence Wizard](multidimensional-models/define-time-intelligence-calculations-using-the-business-intelligence-wizard.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cd10e-123">**계산** 탭에서 계산 스크립트는 CALCULATE 명령으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-123">On the **Calculations** tab, the calculation script starts with the CALCULATE command.</span></span> <span data-ttu-id="cd10e-124">CALCULATE 명령은 큐브의 셀 집계를 제어하므로 큐브 셀의 집계 방식을 수동으로 지정하려는 경우에만 이 명령을 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-124">The CALCULATE command controls the aggregation of the cells in the cube and you should edit this command only if you intend to manually specify how the cube cells should be aggregated.</span></span>  
  
 <span data-ttu-id="cd10e-125">자세한 내용은 [계산](multidimensional-models-olap-logical-cube-objects/calculations.md)및 [다차원 모델의 계산](multidimensional-models/calculations-in-multidimensional-models.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd10e-125">For more information, see [Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md), and [Calculations in Multidimensional Models](multidimensional-models/calculations-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd10e-126">이 자습서의 모든 단원에 대한 완료된 프로젝트를 온라인으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-126">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="cd10e-127">이전 단원에서 완료된 프로젝트를 시작 지점으로 사용하여 어떠한 단원으로든 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-127">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="cd10e-128">이 자습서와 함께 제공되는 샘플 프로젝트를 다운로드하려면[여기를 클릭](https://go.microsoft.com/fwlink/?LinkID=221866) 하십시오.</span><span class="sxs-lookup"><span data-stu-id="cd10e-128">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="cd10e-129">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-129">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="cd10e-130">계산 멤버 정의</span><span class="sxs-lookup"><span data-stu-id="cd10e-130">Defining Calculated Members</span></span>](lesson-6-1-defining-calculated-members.md)  
 <span data-ttu-id="cd10e-131">이 태스크에서는 계산 멤버의 정의 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-131">In this task, you learn to define calculated members.</span></span>  
  
 [<span data-ttu-id="cd10e-132">명명된 집합 정의</span><span class="sxs-lookup"><span data-stu-id="cd10e-132">Defining Named Sets</span></span>](lesson-6-2-defining-named-sets.md)  
 <span data-ttu-id="cd10e-133">이 태스크에서는 명명된 집합의 정의 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="cd10e-133">In this task, you learn to define named sets.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="cd10e-134">다음 단원</span><span class="sxs-lookup"><span data-stu-id="cd10e-134">Next Lesson</span></span>  
 [<span data-ttu-id="cd10e-135">7단원: KPI&#40;핵심 성과 지표&#41; 정의</span><span class="sxs-lookup"><span data-stu-id="cd10e-135">Lesson 7: Defining Key Performance Indicators &#40;KPIs&#41;</span></span>](lesson-7-defining-key-performance-indicators-kpis.md)  
  
## <a name="see-also"></a><span data-ttu-id="cd10e-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd10e-136">See Also</span></span>  
 <span data-ttu-id="cd10e-137">[Analysis Services 자습서 시나리오](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="cd10e-137">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="cd10e-138">[&#40;의 다차원 모델링은 놀이 Works 자습서&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="cd10e-138">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 <span data-ttu-id="cd10e-139">[명명 된 집합 만들기](multidimensional-models/create-named-sets.md) </span><span class="sxs-lookup"><span data-stu-id="cd10e-139">[Create Named Sets](multidimensional-models/create-named-sets.md) </span></span>  
 [<span data-ttu-id="cd10e-140">계산 멤버 만들기</span><span class="sxs-lookup"><span data-stu-id="cd10e-140">Create Calculated Members</span></span>](multidimensional-models/create-calculated-members.md)  
  
  
