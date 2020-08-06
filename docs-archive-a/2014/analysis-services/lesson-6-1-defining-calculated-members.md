---
title: 계산 멤버 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 07f13e1c-0b20-4f9e-ad62-c438983f2785
author: minewiskan
ms.author: owend
ms.openlocfilehash: f2a054356613ebf3d4cf825c1fa4c238a5362ec3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649782"
---
# <a name="defining-calculated-members"></a><span data-ttu-id="4b489-102">계산 멤버 정의</span><span class="sxs-lookup"><span data-stu-id="4b489-102">Defining Calculated Members</span></span>
  <span data-ttu-id="4b489-103">계산 멤버는 큐브 데이터, 산술 연산자, 숫자 및 함수 조합을 기반으로 정의되는 차원 또는 측정값 그룹의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-103">Calculated members are members of a dimension or a measure group that are defined based on a combination of cube data, arithmetic operators, numbers, and functions.</span></span> <span data-ttu-id="4b489-104">예를 들어 큐브에 있는 두 개의 물리적 측정값 합계를 계산하는 계산 멤버를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-104">For example, you can create a calculated member that calculates the sum of two physical measures in the cube.</span></span> <span data-ttu-id="4b489-105">계산 멤버 정의는 큐브에 저장되지만 해당 값은 쿼리 시간에 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-105">Calculated member definitions are stored in cubes, but their values are calculated at query time.</span></span>  
  
 <span data-ttu-id="4b489-106">계산 멤버를 만들려면 큐브 디자이너의 **계산 탭** 에 있는 **새 계산 멤버** 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-106">To create a calculated member, use the **New Calculated Member** command on the **Calculations** tab of Cube Designer.</span></span> <span data-ttu-id="4b489-107">측정값 차원을 비롯하여 모든 차원 내에서 계산 멤버를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-107">You can create a calculated member within any dimension, including the measures dimension.</span></span> <span data-ttu-id="4b489-108">또한 **계산 속성** 대화 상자에서 표시 폴더 안에 계산 멤버를 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-108">You can also place a calculated member within a display folder in the **Calculation Properties** dialog box.</span></span> <span data-ttu-id="4b489-109">자세한 내용은 [계산](multidimensional-models-olap-logical-cube-objects/calculations.md), [다차원 모델의 계산](multidimensional-models/calculations-in-multidimensional-models.md)및 [계산 멤버 만들기](multidimensional-models/create-calculated-members.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4b489-109">For more information, see [Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md), [Calculations in Multidimensional Models](multidimensional-models/calculations-in-multidimensional-models.md), and [Create Calculated Members](multidimensional-models/create-calculated-members.md).</span></span>  
  
 <span data-ttu-id="4b489-110">이 항목의 태스크에서는 사용자들이 인터넷 판매, 대리점 판매 및 모든 판매에 대해 매출이익률과 매출 비율을 확인할 수 있는 계산 측정값을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-110">In the tasks in this topic, you define calculated measures to let users view the gross profit margin percentage and sales ratios for Internet sales, reseller sales, and for all sales.</span></span>  
  
## <a name="defining-calculations-to-aggregate-physical-measures"></a><span data-ttu-id="4b489-111">물리적 측정값을 집계하는 계산 정의</span><span class="sxs-lookup"><span data-stu-id="4b489-111">Defining Calculations to Aggregate Physical Measures</span></span>  
  
1.  <span data-ttu-id="4b489-112">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 대한 큐브 디자이너를 열고 **계산** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-112">Open Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Calculations** tab.</span></span>  
  
     <span data-ttu-id="4b489-113">**계산 식** 창 및 **스크립트 구성 도우미** 창에는 기본 CALCULATE 명령이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-113">Notice the default CALCULATE command in the **Calculation Expressions** pane and in the **Script Organizer** pane.</span></span> <span data-ttu-id="4b489-114">이 명령은 큐브의 측정값을 AggregateFunction 속성으로 지정된 값에 따라 집계하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-114">This command specifies that the measures in the cube should be aggregated according to the value that is specified by their AggregateFunction properties.</span></span> <span data-ttu-id="4b489-115">측정값은 일반적으로 합산되지만 약간 다른 방식으로 계산되거나 집계될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-115">Measure values are generally summed, but may also be counted or aggregated in some other manner.</span></span>  
  
     <span data-ttu-id="4b489-116">다음 그림에서는 큐브 디자이너의 **계산** 탭을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-116">The following image shows the **Calculations** tab of Cube Designer.</span></span>  
  
     <span data-ttu-id="4b489-117">![큐브 디자이너의 계산 탭](../../2014/tutorials/media/l6-calculatedmembers-1.gif "큐브 디자이너의 계산 탭")</span><span class="sxs-lookup"><span data-stu-id="4b489-117">![Calculations tab of Cube Designer](../../2014/tutorials/media/l6-calculatedmembers-1.gif "Calculations tab of Cube Designer")</span></span>  
  
2.  <span data-ttu-id="4b489-118">**계산** 탭의 도구 모음에서 **새 계산 멤버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-118">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
     <span data-ttu-id="4b489-119">이 새 계산 멤버의 속성을 정의할 수 있는 새 양식이 **계산 식** 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-119">A new form appears in the **Calculation Expressions** pane within which you define the properties of this new calculated member.</span></span> <span data-ttu-id="4b489-120">새 멤버는 **스크립트 구성 도우미** 창에도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-120">The new member also appears in the **Script Organizer** pane.</span></span>  
  
     <span data-ttu-id="4b489-121">다음 그림에서는 **새 계산 멤버** 를 클릭할 때 **계산 식**창에 나타나는 양식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-121">The following image shows the form that appears in the **Calculation Expressions** pane when you click **New Calculated Member**.</span></span>  
  
     <span data-ttu-id="4b489-122">![계산 식 창 양식](../../2014/tutorials/media/l6-calculatedmembers-02.gif "계산 식 창 양식")</span><span class="sxs-lookup"><span data-stu-id="4b489-122">![Calculation Expressions pane form](../../2014/tutorials/media/l6-calculatedmembers-02.gif "Calculation Expressions pane form")</span></span>  
  
3.  <span data-ttu-id="4b489-123">**이름** 상자에서 계산 측정값의 이름을로 변경 `[Total Sales Amount]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-123">In the **Name** box, change the name of the calculated measure to `[Total Sales Amount]`.</span></span>  
  
     <span data-ttu-id="4b489-124">계산 멤버의 이름에 공백이 들어 있으면 계산 멤버 이름을 대괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-124">If the name of a calculated member contains a space, the calculated member name must be enclosed in square brackets.</span></span>  
  
     <span data-ttu-id="4b489-125">기본적으로 **부모 계층** 목록의 **Measures** 차원에 새 계산 멤버가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-125">Notice in the **Parent hierarchy** list that, by default, a new calculated member is created in the **Measures** dimension.</span></span> <span data-ttu-id="4b489-126">측정값 차원의 계산 멤버를 계산 측정값이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-126">A calculated member in the Measures dimension is also frequently called a calculated measure.</span></span>  
  
4.  <span data-ttu-id="4b489-127">**계산** 탭의 **계산 도구** 창에 있는 **메타데이터** 탭에서 **Measures** 를 확장한 후 **Internet Sales** 를 확장하여 **Internet Sales** 측정값 그룹에 대한 메타데이터를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-127">On the **Metadata** tab in the **Calculation Tools** pane of the **Calculations** tab, expand **Measures** and then expand **Internet Sales** to view the metadata for the **Internet Sales** measure group.</span></span>  
  
     <span data-ttu-id="4b489-128">**계산 도구** 창의 메타데이터 요소를 **식** 상자로 끌어온 다음 연산자 및 기타 요소를 추가하여 MDX(Multidimensional Expressions) 식을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-128">You can drag metadata elements from the **Calculation Tools** pane into the **Expression** box and then add operators and other elements to create Multidimensional Expressions (MDX) expressions.</span></span> <span data-ttu-id="4b489-129">또는 **식** 상자에 직접 MDX 식을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-129">Alternatively, you can type the MDX expression directly into the **Expression** box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b489-130">**계산 도구** 창에 메타데이터가 표시되지 않으면 도구 모음에서 **다시 연결** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-130">If you cannot view any metadata in the **Calculation Tools** pane, click **Reconnect** on the toolbar.</span></span> <span data-ttu-id="4b489-131">이 옵션을 사용할 수 없으면 큐브를 처리하거나 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 시작해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-131">If this does not work, you may have to process the cube or start the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="4b489-132">**계산 도구** 창의 **메타데이터** 탭에서 **계산 식** 창의 **식** 상자로 **Internet Sales-Sales Amount** 를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-132">Drag **Internet Sales-Sales Amount** from the **Metadata** tab in the **Calculation Tools** pane into the **Expression** box in the **Calculation Expressions** pane.</span></span>  
  
6.  <span data-ttu-id="4b489-133">**식** 상자에서`+`[Measures].[Internet Sales-Sales Amount] **뒤에 더하기 기호(**)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-133">In the **Expression** box, type a plus sign (`+`) after **[Measures].[Internet Sales-Sales Amount]**.</span></span>  
  
7.  <span data-ttu-id="4b489-134">**계산 도구** 창의 **메타데이터** 탭에서 **Reseller Sales**를 확장한 후 **계산 식** 창의 **식** 상자에서 더하기 기호(+) 뒤로 **Reseller Sales-Sales Amount** 를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-134">On the **Metadata** tab in the **Calculation Tools** pane, expand **Reseller Sales**, and then drag **Reseller Sales-Sales Amount** into the **Expression** box in the **Calculation Expressions** pane after the plus sign (+).</span></span>  
  
8.  <span data-ttu-id="4b489-135">**형식 문자열** 목록에서 **"Currency"를 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="4b489-135">In the **Format string** list, select **"Currency".**</span></span>  
  
9. <span data-ttu-id="4b489-136">**비어 있지 않은 동작** 목록에서 **Internet Sales-Sales Amount** 및 **Reseller Sales-Sales Amount**에 대한 확인란을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-136">In the **Non-empty behavior** list, select the check boxes for **Internet Sales-Sales Amount** and **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="4b489-137">**비어 있지 않은 동작** 목록에서 지정한 측정값은 MDX의 NON EMPTY 쿼리를 해결하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-137">The measures you specify in the **Non-empty behavior** list are used to resolve NON EMPTY queries in MDX.</span></span> <span data-ttu-id="4b489-138">**비어 있지 않은 동작** 목록에 하나 이상의 측정값을 지정하면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 지정된 모든 측정값이 비어 있는 경우 계산 멤버를 비어 있는 것으로 취급합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-138">When you specify one or more measures in the **Non-empty behavior** list, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] treats the calculated member as empty if all the specified measures are empty.</span></span> <span data-ttu-id="4b489-139">**비어 있지 않은 동작** 속성을 비워 두면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 계산 멤버 자체를 계산하여 멤버가 비어 있는지 여부를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-139">If the **Non-empty behavior** property is blank, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] must evaluate the calculated member itself to determine whether the member is empty.</span></span>  
  
     <span data-ttu-id="4b489-140">다음 그림에서는 이전 단계에서 지정한 설정으로 채워진 **계산 식** 창을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-140">The following image shows the **Calculation Expressions** pane populated with the settings that you specified in the previous steps.</span></span>  
  
     <span data-ttu-id="4b489-141">![채워진 계산 식 창](../../2014/tutorials/media/l6-calculatedmembers-03.gif "채워진 계산 식 창")</span><span class="sxs-lookup"><span data-stu-id="4b489-141">![Populated Calculation Expressions pane](../../2014/tutorials/media/l6-calculatedmembers-03.gif "Populated Calculation Expressions pane")</span></span>  
  
10. <span data-ttu-id="4b489-142">**계산** 탭의 도구 모음에서 **스크립트 보기**를 클릭한 후 **계산 식** 창에서 계산 스크립트를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-142">On the toolbar of the **Calculations** tab, click **Script View**, and then review the calculation script in the **Calculation Expressions** pane.</span></span>  
  
     <span data-ttu-id="4b489-143">새 계산은 초기 CALCULATE 식에 추가되며 개별 계산은 세미콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-143">Notice that the new calculation is added to the initial CALCULATE expression; each individual calculation is separated by a semicolon.</span></span> <span data-ttu-id="4b489-144">또한 계산 스크립트 맨 앞에 설명이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-144">Notice also that a comment appears at the beginning of the calculation script.</span></span> <span data-ttu-id="4b489-145">계산 스크립트 내에 계산 그룹에 대한 설명을 추가하면 사용자 자신 및 다른 개발자가 복잡한 계산 스크립트를 이해하는 데 도움을 주므로 바람직합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-145">Adding comments within the calculation script for groups of calculations is a good practice, to help you and other developers understand complex calculation scripts.</span></span>  
  
11. <span data-ttu-id="4b489-146">계산 스크립트에서 **Calculate;** 명령 뒤, 새로 추가한 계산 스크립트 앞에 새 줄을 추가한 후 다음 텍스트를 별도의 줄로 스크립트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-146">Add a new line in the calculation script after the **Calculate;** command and before the newly added calculation script, and then add the following text to the script on its own line:</span></span>  
  
    ```  
    /* Calculations to aggregate Internet Sales and Reseller Sales measures */  
    ```  
  
     <span data-ttu-id="4b489-147">다음 그림에서는 자습서의 이 부분에서 **계산 식** 창에 표시되어야 하는 계산 스크립트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-147">The following image shows the calculation scripts as they should appear in the **Calculation Expressions** pane at this point in the tutorial.</span></span>  
  
     <span data-ttu-id="4b489-148">![계산 식 창의 스크립트](../../2014/tutorials/media/l6-calculatedmembers-04.gif "계산 식 창의 스크립트")</span><span class="sxs-lookup"><span data-stu-id="4b489-148">![Scripts in Calculation Expressions pane](../../2014/tutorials/media/l6-calculatedmembers-04.gif "Scripts in Calculation Expressions pane")</span></span>  
  
12. <span data-ttu-id="4b489-149">**계산** 탭의 도구 모음에서 **폼 보기**를 클릭 하 `[Total Sales Amount]` 고 **스크립트 구성 도우미** 창에서가 선택 되어 있는지 확인 한 다음 **새 계산 멤버**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-149">On the toolbar of the **Calculations** tab, click **Form View**, verify that `[Total Sales Amount]` is selected in the **Script Organizer** pane, and then click **New Calculated Member**.</span></span>  
  
13. <span data-ttu-id="4b489-150">이 새 계산 멤버의 이름을로 변경 하 `[Total Product Cost]` 고 **식** 상자에 다음 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-150">Change the name of this new calculated member to `[Total Product Cost]`, and then create the following expression in the **Expression** box:</span></span>  
  
    ```  
    [Measures].[Internet Sales-Total Product Cost] + [Measures].[Reseller Sales-Total Product Cost]  
    ```  
  
14. <span data-ttu-id="4b489-151">**형식 문자열** 목록에서 **"Currency"** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-151">In the **Format string** list, select **"Currency"**.</span></span>  
  
15. <span data-ttu-id="4b489-152">**비어 있지 않은 동작** 목록에서 **Internet Sales-Total Product Cost** 및 **Reseller Sales-Total Product Cost**에 대한 확인란을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-152">In the **Non-empty behavior** list, select the check boxes for **Internet Sales-Total Product Cost** and **Reseller Sales-Total Product Cost**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="4b489-153">이제 두 개의 계산 멤버가 정의되었으며 이 멤버는 **스크립트 구성 도우미** 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-153">You have now defined two calculated members, both of which are visible in the **Script Organizer** pane.</span></span> <span data-ttu-id="4b489-154">이러한 계산 멤버는 계산 스크립트에서 이후 정의하는 다른 계산에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-154">These calculated members can be used by other calculations that you define later in the calculation script.</span></span> <span data-ttu-id="4b489-155">**스크립트 구성 도우미** 창에서 계산 멤버를 선택하여 계산 멤버의 정의를 확인할 수 있습니다. 계산 멤버의 정의는 폼 보기의 **계산 식** 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-155">You can view the definition of any calculated member by selecting the calculated member in the **Script Organizer** pane; the definition of the calculated member will appear in the **Calculation Expressions** pane in the Form view.</span></span> <span data-ttu-id="4b489-156">새로 정의한 계산 멤버는 해당 개체를 배포한 후에만 **계산 도구** 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-156">Newly defined calculated members will not appear in the **Calculation Tools** pane until these objects have been deployed.</span></span> <span data-ttu-id="4b489-157">계산을 위한 추가 처리는 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-157">Calculations do not require processing.</span></span>  
  
## <a name="defining-gross-profit-margin-calculations"></a><span data-ttu-id="4b489-158">매출이익률 계산 정의</span><span class="sxs-lookup"><span data-stu-id="4b489-158">Defining Gross Profit Margin Calculations</span></span>  
  
1.  <span data-ttu-id="4b489-159">`[Total Product Cost]` **스크립트 구성 도우미** 창에서가 선택 되어 있는지 확인 한 다음 **계산** 탭의 도구 모음에서 **새 계산 멤버** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-159">Verify that `[Total Product Cost]` is selected in the **Script Organizer** pane, and then click **New Calculated Member** on the toolbar of the **Calculations** tab.</span></span>  
  
2.  <span data-ttu-id="4b489-160">**이름** 상자에서이 새 계산 측정값의 이름을로 변경 `[Internet GPM]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-160">In the **Name** box, change the name of this new calculated measure to `[Internet GPM]`.</span></span>  
  
3.  <span data-ttu-id="4b489-161">**식** 상자에서 다음 MDX 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-161">In the **Expression** box, create the following MDX expression:</span></span>  
  
    ```  
    ([Measures].[Internet Sales-Sales Amount] -   
    [Measures].[Internet Sales-Total Product Cost]) /  
    [Measures].[Internet Sales-Sales Amount]  
    ```  
  
4.  <span data-ttu-id="4b489-162">**형식 문자열** 목록에서 **"Percent"** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-162">In the **Format string** list, select **"Percent"**.</span></span>  
  
5.  <span data-ttu-id="4b489-163">**비어 있지 않은 동작** 목록에서 **Internet Sales-Sales Amount**에 대한 확인란을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-163">In the **Non-empty behavior** list, select the check box for **Internet Sales-Sales Amount**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="4b489-164">**계산** 탭의 도구 모음에서 **새 계산 멤버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-164">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
7.  <span data-ttu-id="4b489-165">**이름** 상자에서이 새 계산 측정값의 이름을로 변경 `[Reseller GPM]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-165">In the **Name** box, change the name of this new calculated measure to `[Reseller GPM]`.</span></span>  
  
8.  <span data-ttu-id="4b489-166">**식** 상자에서 다음 MDX 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-166">In the **Expression** box, create the following MDX expression:</span></span>  
  
    ```  
    ([Measures].[Reseller Sales-Sales Amount] -   
    [Measures].[Reseller Sales-Total Product Cost]) /  
    [Measures].[Reseller Sales-Sales Amount]  
    ```  
  
9. <span data-ttu-id="4b489-167">**형식 문자열** 목록에서 **"Percent"** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-167">In the **Format string** list, select **"Percent"**.</span></span>  
  
10. <span data-ttu-id="4b489-168">**비어 있지 않은 동작** 목록에서 **Reseller Sales-Sales Amount**에 대한 확인란을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-168">In the **Non-empty behavior** list, select the check box for **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="4b489-169">**계산** 탭의 도구 모음에서 **새 계산 멤버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-169">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
12. <span data-ttu-id="4b489-170">**이름** 상자에서이 계산 측정값의 이름을로 변경 `[Total GPM]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-170">In the **Name** box, change the name of this calculated measure to `[Total GPM]`.</span></span>  
  
13. <span data-ttu-id="4b489-171">**식** 상자에서 다음 MDX 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-171">In the **Expression** box, create the following MDX expression:</span></span>  
  
    ```  
    ([Measures].[Total Sales Amount] -   
    [Measures].[Total Product Cost]) /  
    [Measures].[Total Sales Amount]  
    ```  
  
     <span data-ttu-id="4b489-172">이 계산 멤버는 다른 계산 멤버를 참조하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-172">Notice that this calculated member is referencing other calculated members.</span></span> <span data-ttu-id="4b489-173">이 계산 멤버는 자신이 참조하는 계산 멤버 다음에 계산되므로 유효한 계산 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-173">Because this calculated member will be calculated after the calculated members that it references, this is a valid calculated member.</span></span>  
  
14. <span data-ttu-id="4b489-174">**형식 문자열** 목록에서 **"Percent"** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-174">In the **Format string** list, select **"Percent"**.</span></span>  
  
15. <span data-ttu-id="4b489-175">**비어 있지 않은 동작** 목록에서 **Internet Sales-Sales Amount** 및 **Reseller Sales-Sales Amount**에 대한 확인란을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-175">In the **Non-empty behavior** list, select the check boxes for **Internet Sales-Sales Amount** and **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="4b489-176">**계산** 탭의 도구 모음에서 **스크립트 보기** 를 클릭하고 계산 스크립트에 방금 추가한 3개의 계산을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-176">On the toolbar of the **Calculations** tab, click **Script View** and review the three calculations you just added to the calculation script.</span></span>  
  
17. <span data-ttu-id="4b489-177">계산 스크립트에서 계산 바로 앞에 새 줄을 추가한 `[Internet GPM]` 후 다음 텍스트를 별도의 줄로 스크립트에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-177">Add a new line in the calculation script immediately before the `[Internet GPM]` calculation, and then add the following text to the script on its own line:</span></span>  
  
    ```  
    /* Calculations to calculate gross profit margin */  
    ```  
  
     <span data-ttu-id="4b489-178">다음 그림에서는 3개의 새 계산을 포함하는 **식** 창을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-178">The following image shows the **Expressions** pane with the three new calculations.</span></span>  
  
     <span data-ttu-id="4b489-179">![계산 식 창의 새 계산](../../2014/tutorials/media/l6-calculatedmembers-05.gif "계산 식 창의 새 계산")</span><span class="sxs-lookup"><span data-stu-id="4b489-179">![New calculations in Calculation Expressions pane](../../2014/tutorials/media/l6-calculatedmembers-05.gif "New calculations in Calculation Expressions pane")</span></span>  
  
## <a name="defining-the-percent-of-total-calculations"></a><span data-ttu-id="4b489-180">총 계산의 백분율 정의</span><span class="sxs-lookup"><span data-stu-id="4b489-180">Defining the Percent of Total Calculations</span></span>  
  
1.  <span data-ttu-id="4b489-181">**계산** 탭의 도구 모음에서 **폼 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-181">On the toolbar of the **Calculations** tab, click **Form View**.</span></span>  
  
2.  <span data-ttu-id="4b489-182">**스크립트 구성 도우미** 창에서를 선택한 `[Total GPM]` 다음 **계산** 탭의 도구 모음에서 **새 계산 멤버** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-182">In the **Script Organizer** pane, select `[Total GPM]`, and then click **New Calculated Member** on the toolbar of the **Calculations** tab.</span></span>  
  
     <span data-ttu-id="4b489-183">**새 계산 멤버** 를 클릭하기 전에 **스크립트 구성 도우미** 창에서 최종 계산 멤버를 클릭하면 새 계산 멤버가 스크립트 끝에 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-183">Clicking the final calculated member in the **Script Organizer** pane before you click **New Calculated Member** guarantees that the new calculated member will be entered at the end of the script.</span></span> <span data-ttu-id="4b489-184">스크립트는 **스크립트 구성 도우미** 창에 나타난 순서대로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-184">Scripts execute in the order that they appear in the **Script Organizer** pane.</span></span>  
  
3.  <span data-ttu-id="4b489-185">이 새 계산 멤버의 이름을로 변경 `[Internet Sales Ratio to All Products]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-185">Change the name of this new calculated member to `[Internet Sales Ratio to All Products]`.</span></span>  
  
4.  <span data-ttu-id="4b489-186">**식** 입력란에 다음 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-186">Type the following expression in the **Expression** box:</span></span>  
  
    ```  
    Case  
        When IsEmpty( [Measures].[Internet Sales-Sales Amount] )   
        Then 0  
        Else ( [Product].[Product Categories].CurrentMember,  
               [Measures].[Internet Sales-Sales Amount]) /  
             ( [Product].[Product Categories].[(All)].[All],   
               [Measures].[Internet Sales-Sales Amount] )  
        End  
    ```  
  
     <span data-ttu-id="4b489-187">이 MDX 식은 각 제품의 총 인터넷 판매에 영향을 미치는 요인을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-187">This MDX expression calculates the contribution to total Internet sales of each product.</span></span> <span data-ttu-id="4b489-188">Case 문을 IS EMPTY 함수와 함께 사용하면 제품 판매가 없을 때 0으로 나누기 오류가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-188">The Case statement together with the IS EMPTY function ensures that a divide by zero error does not occur when a product has no sales.</span></span>  
  
5.  <span data-ttu-id="4b489-189">**형식 문자열** 목록에서 **"Percent"** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-189">In the **Format string** list, select **"Percent"**.</span></span>  
  
6.  <span data-ttu-id="4b489-190">**비어 있지 않은 동작** 목록에서 **Internet Sales-Sales Amount**에 대한 확인란을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-190">In the **Non-empty behavior** list, select the check box for **Internet Sales-Sales Amount**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="4b489-191">**계산** 탭의 도구 모음에서 **새 계산 멤버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-191">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
8.  <span data-ttu-id="4b489-192">이 계산 멤버의 이름을로 변경 `[Reseller Sales Ratio to All Products]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-192">Change the name of this calculated member to `[Reseller Sales Ratio to All Products]`.</span></span>  
  
9. <span data-ttu-id="4b489-193">**식** 입력란에 다음 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-193">Type the following expression in the **Expression** box:</span></span>  
  
    ```  
    Case  
        When IsEmpty( [Measures].[Reseller Sales-Sales Amount] )   
        Then 0  
        Else ( [Product].[Product Categories].CurrentMember,  
               [Measures].[Reseller Sales-Sales Amount]) /  
             ( [Product].[Product Categories].[(All)].[All],   
               [Measures].[Reseller Sales-Sales Amount] )  
        End  
    ```  
  
10. <span data-ttu-id="4b489-194">**형식 문자열** 목록에서 **"Percent"** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-194">In the **Format string** list, select **"Percent"**.</span></span>  
  
11. <span data-ttu-id="4b489-195">**비어 있지 않은 동작** 목록에서 **Reseller Sales-Sales Amount**에 대한 확인란을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-195">In the **Non-empty behavior** list, select the check box for **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="4b489-196">**계산** 탭의 도구 모음에서 **새 계산 멤버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-196">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
13. <span data-ttu-id="4b489-197">이 계산 멤버의 이름을로 변경 `[Total Sales Ratio to All Products]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-197">Change the name of this calculated member to `[Total Sales Ratio to All Products]`.</span></span>  
  
14. <span data-ttu-id="4b489-198">**식** 입력란에 다음 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-198">Type the following expression in the **Expression** box:</span></span>  
  
    ```  
    Case  
        When IsEmpty( [Measures].[Total Sales Amount] )   
        Then 0  
        Else ( [Product].[Product Categories].CurrentMember,  
               [Measures].[Total Sales Amount]) /  
             ( [Product].[Product Categories].[(All)].[All],   
               [Measures].[Total Sales Amount] )  
        End  
    ```  
  
15. <span data-ttu-id="4b489-199">**형식 문자열** 목록에서 **"Percent"** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-199">In the **Format string** list, select **"Percent"**.</span></span>  
  
16. <span data-ttu-id="4b489-200">**비어 있지 않은 동작** 목록에서 **Internet Sales-Sales Amount** 및 **Reseller Sales-Sales Amount**에 대한 확인란을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-200">In the **Non-empty behavior** list, select the check boxes for **Internet Sales-Sales Amount** and **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
17. <span data-ttu-id="4b489-201">**계산** 탭의 도구 모음에서 **스크립트 보기**를 클릭하고 계산 스크립트에 방금 추가한 3개의 계산을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-201">On the toolbar of the **Calculations** tab, click **Script View**, and then review the three calculations that you just added to the calculation script.</span></span>  
  
18. <span data-ttu-id="4b489-202">계산 스크립트에서 계산 바로 앞에 새 줄을 추가한 `[Internet Sales Ratio to All Products]` 후 다음 텍스트를 별도의 줄로 스크립트에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-202">Add a new line in the calculation script immediately before the `[Internet Sales Ratio to All Products]` calculation, and then add the following text to the script on its own line:</span></span>  
  
    ```  
    /* Calculations to calculate percentage of product to total product sales */  
    ```  
  
     <span data-ttu-id="4b489-203">이제 총 8개의 계산 멤버가 정의되었으며 이 멤버는 폼 보기에서 **스크립트 구성 도우미** 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-203">You have now defined a total of eight calculated members, which are visible in the **Script Organizer** pane when you are in Form view.</span></span>  
  
## <a name="browsing-the-new-calculated-members"></a><span data-ttu-id="4b489-204">새 계산 멤버 검색</span><span class="sxs-lookup"><span data-stu-id="4b489-204">Browsing the New Calculated Members</span></span>  
  
1.  <span data-ttu-id="4b489-205">**의** 빌드 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-205">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="4b489-206">배포가 성공적으로 완료되면 **브라우저** 탭으로 전환한 다음 **다시 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-206">When deployment has successfully completed, switch to the **Browser** tab, click **Reconnect**.</span></span>  
  
3.  <span data-ttu-id="4b489-207">Excel 아이콘을 클릭한 다음 **사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-207">Click the Excel icon, and then click **Enable**.</span></span>  
  
4.  <span data-ttu-id="4b489-208">**피벗 테이블 필드 목록** 창에서 **값** 폴더를 확장하여 측정값 차원의 새 계산 멤버를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-208">In the **PivotTable Field List** pane, expand **Values** folder to view the new calculated members in the Measures dimension.</span></span>  
  
5.  <span data-ttu-id="4b489-209">**Total Sales Amount** 를 값 영역으로 끌어간 다음 결과를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-209">Drag the **Total Sales Amount** to the Values area, and then review the results.</span></span>  
  
     <span data-ttu-id="4b489-210">**Internet Sales** 및 **Reseller Sales** 측정값 그룹의 **Internet Sales-Sales Amount** 및 **Reseller Sales-Sales Amount** 측정값을 값 영역으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-210">Drag **Internet Sales-Sales Amount** and **Reseller Sales-Sales Amount** measures from the **Internet Sales** and **Reseller Sales** measure groups to the Values area.</span></span>  
  
     <span data-ttu-id="4b489-211">**Total Sales Amount** 측정값은 **Internet Sales-Sales Amount** 측정값과 **Reseller Sales-Sales Amount** 측정값을 합한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-211">Notice that the **Total Sales Amount** measure is the sum of the **Internet Sales-Sales Amount** measure and the **Reseller Sales-Sales Amount** measure.</span></span>  
  
6.  <span data-ttu-id="4b489-212">**보고서 필터** 영역의 필터 영역에 **Product Categories** 사용자 정의 계층을 추가한 후 **Mountain Bikes**를 기준으로 데이터를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-212">Add the **Product Categories** user-defined hierarchy to the filter area of the **Report Filter** area, and then filter the data by **Mountain Bikes**.</span></span>  
  
     <span data-ttu-id="4b489-213">**Mountain Bikes** 의 **Internet Sales-Sales Amount** 및 **Reseller Sales-Sales Amount** 측정값을 기반으로 제품 판매의 **Mountain Bikes** 범주에 대한 **Total Sales Amount**측정값이 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-213">Notice that the **Total Sales Amount** measure is calculated for the **Mountain Bikes** category of product sales based on the **Internet Sales-Sales Amount** and the **Reseller Sales-Sales Amount** measures for **Mountain Bikes**.</span></span>  
  
7.  <span data-ttu-id="4b489-214">행 레이블 영역에 **Date.Calendar Date** 사용자 정의 계층을 추가한 후 결과를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-214">Add the **Date.Calendar Date** user-defined hierarchy to the Row labels area, and then review the results.</span></span>  
  
     <span data-ttu-id="4b489-215">**Mountain Bikes** 의 **Internet Sales-Sales Amount** 및 **Reseller Sales-Sales Amount** 측정값을 기반으로 제품 판매의 **Mountain Bikes** 범주에 대한 **Total Sales Amount**측정값이 연도별로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-215">Notice that the **Total Sales Amount** measure for each calendar year is calculated for the **Mountain Bikes** category of product sales based on the **Internet Sales-Sales Amount** and the **Reseller Sales-Sales Amount** measures for **Mountain Bikes**.</span></span>  
  
8.  <span data-ttu-id="4b489-216">값 영역에 **Total GPM**, **Internet GPM**및 **Reseller GPM** 측정값을 추가한 후 결과를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-216">Add the **Total GPM**, **Internet GPM**, and **Reseller GPM** measures to the Values area, and then review the results.</span></span>  
  
     <span data-ttu-id="4b489-217">다음 그림에 표시된 것처럼 대리점 판매의 매출이익률은 인터넷 판매의 매출이익률보다 훨씬 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-217">Notice that the gross profit margin for reseller sales is significantly lower than for sales over the Internet, as shown in the following image.</span></span>  
  
     <span data-ttu-id="4b489-218">![대리점 판매를 보여 주는 데이터 창](../../2014/tutorials/media/l6-calculatedmembers-7b.gif "대리점 판매를 보여 주는 데이터 창")</span><span class="sxs-lookup"><span data-stu-id="4b489-218">![Data pane showing reseller sales](../../2014/tutorials/media/l6-calculatedmembers-7b.gif "Data pane showing reseller sales")</span></span>  
  
9. <span data-ttu-id="4b489-219">값 영역에 **Total Sales Ratio to All Products**, **Internet Sales Ratio to All Products**및 **Reseller Sales Ratio to All Products** 측정값을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-219">Add the **Total Sales Ratio to All Products**, **Internet Sales Ratio to All Products**, and **Reseller Sales Ratio to All Products** measures to the Values area.</span></span>  
  
     <span data-ttu-id="4b489-220">모든 제품 대비 산악 자전거 매출 비율은 인터넷 판매에서는 시간에 따라 증가하지만 대리점 판매의 경우는 감소합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-220">Notice that the ratio of the sales of mountain bikes to all products has increased over time for Internet sales, but is decreasing over time for reseller sales.</span></span> <span data-ttu-id="4b489-221">또한 모든 제품 대비 산악 자전거 매출 비율은 인터넷 판매의 경우보다 대리점 판매량이 더 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-221">Notice also that the ratio of the sale of mountain bikes to all products is lower from sales through resellers than it is for sales over the Internet.</span></span>  
  
10. <span data-ttu-id="4b489-222">필터를 **Mountain Bikes** 에서 **Bikes**로 변경한 후 결과를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-222">Change the filter from **Mountain Bikes** to **Bikes**, and review the results.</span></span>  
  
     <span data-ttu-id="4b489-223">여행용 자전거와 도로용 자전거는 밑지고 판매되는 경우가 많으므로 대리점을 통해 판매된 모든 자전거의 매출이익률은 적자입니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-223">Notice that the gross profit margin for all bikes sold through resellers is negative, because touring bikes and road bikes are being sold at a loss.</span></span>  
  
11. <span data-ttu-id="4b489-224">필터를 **Accessories**로 변경한 후 결과를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-224">Change the filter to **Accessories**, and then review the results.</span></span>  
  
     <span data-ttu-id="4b489-225">부속품 판매는 시간에 따라 증가하지만 이러한 판매는 총 판매의 일부에 지나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-225">Notice that the sale of accessories is increasing over time, but that these sales make up only a small fraction of total sales.</span></span> <span data-ttu-id="4b489-226">또한 부속품 판매의 매출이익률은 자전거 판매 매출이익률보다 높습니다.</span><span class="sxs-lookup"><span data-stu-id="4b489-226">Notice also that the gross profit margin for sales of accessories is higher than for bikes.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="4b489-227">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="4b489-227">Next Task in Lesson</span></span>  
 [<span data-ttu-id="4b489-228">명명된 집합 정의</span><span class="sxs-lookup"><span data-stu-id="4b489-228">Defining Named Sets</span></span>](lesson-6-2-defining-named-sets.md)  
  
## <a name="see-also"></a><span data-ttu-id="4b489-229">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b489-229">See Also</span></span>  
 <span data-ttu-id="4b489-230">[계산](multidimensional-models-olap-logical-cube-objects/calculations.md) </span><span class="sxs-lookup"><span data-stu-id="4b489-230">[Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md) </span></span>  
 <span data-ttu-id="4b489-231">[다차원 모델의 계산](multidimensional-models/calculations-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="4b489-231">[Calculations in Multidimensional Models](multidimensional-models/calculations-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="4b489-232">계산 멤버 만들기</span><span class="sxs-lookup"><span data-stu-id="4b489-232">Create Calculated Members</span></span>](multidimensional-models/create-calculated-members.md)  
  
  
