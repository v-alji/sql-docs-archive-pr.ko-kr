---
title: 부모-자식 계층의 부모 특성 속성 정의 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2d78fa73-a13b-4e12-bbd0-43e5307f760c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1dfa4340bdc161809cf3821e5cb1f0609399e1d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652418"
---
# <a name="defining-parent-attribute-properties-in-a-parent-child-hierarchy"></a><span data-ttu-id="0f116-102">부모-자식 계층의 부모 특성 속성 정의</span><span class="sxs-lookup"><span data-stu-id="0f116-102">Defining Parent Attribute Properties in a Parent-Child Hierarchy</span></span>
  <span data-ttu-id="0f116-103">부모-자식 계층은 두 개의 테이블 열을 기반으로 하는 차원의 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-103">A parent-child hierarchy is a hierarchy in a dimension that is based on two table columns.</span></span> <span data-ttu-id="0f116-104">이 두 열은 차원의 멤버 간 계층 관계를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-104">Together, these columns define the hierarchical relationships among the members of the dimension.</span></span> <span data-ttu-id="0f116-105">*멤버 키 열*이라는 첫 번째 열은 각 차원 멤버를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-105">The first column, called the *member key column*, identifies each dimension member.</span></span> <span data-ttu-id="0f116-106">*부모 열*이라는 다른 하나의 열은 각 차원 멤버의 부모를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-106">The other column, called the *parent column*, identifies the parent of each dimension member.</span></span> <span data-ttu-id="0f116-107">부모 특성의 **NamingTemplate** 속성은 부모-자식 계층의 각 수준 이름을 지정하고 **MembersWithData** 속성은 부모 멤버의 데이터 표시 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-107">The **NamingTemplate** property of a parent attribute determines the name of each level in the parent-child hierarchy, and the **MembersWithData** property determines whether data for parent members should be displayed.</span></span>

 <span data-ttu-id="0f116-108">자세한 내용은 [부모-자식 계층](multidimensional-models/parent-child-dimension.md), [부모-자식 계층의 특성](multidimensional-models/parent-child-dimension-attributes.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0f116-108">For more information, see [Parent-Child Hierarchy](multidimensional-models/parent-child-dimension.md), [Attributes in Parent-Child Hierarchies](multidimensional-models/parent-child-dimension-attributes.md)</span></span>

> [!NOTE]
>  <span data-ttu-id="0f116-109">차원 마법사를 사용하여 차원을 만들면 마법사에서 부모-자식 관계가 있는 테이블을 인식하고 자동으로 부모-자식 계층을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-109">When you use the Dimension Wizard to create a dimension, the wizard recognizes the tables that have parent-child relationships and automatically defines the parent-child hierarchy for you.</span></span>

 <span data-ttu-id="0f116-110">이 항목의 태스크에서는 **Employee** 차원에서 부모-자식 계층의 각 수준 이름을 정의하는 명명 템플릿을 만든 다음</span><span class="sxs-lookup"><span data-stu-id="0f116-110">In the tasks in this topic, you will create a naming template that defines the name for each level in the parent-child hierarchy in the **Employee** dimension.</span></span> <span data-ttu-id="0f116-111">모든 부모 데이터를 숨기도록 부모 특성을 구성하여 리프 수준 멤버의 판매량만 표시하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-111">You will then configure the parent attribute to hide all parent data, so that only the sales for leaf-level members are displayed.</span></span>

## <a name="browsing-the-employee-dimension"></a><span data-ttu-id="0f116-112">Employee 차원 찾아보기</span><span class="sxs-lookup"><span data-stu-id="0f116-112">Browsing the Employee Dimension</span></span>

1.  <span data-ttu-id="0f116-113">솔루션 탐색기의 **차원** 폴더에서 **Employee.dim** 을 두 번 클릭하여 Employee 차원에 대한 차원 디자이너를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-113">In Solution Explorer, double-click **Employee.dim** in the **Dimensions** folder to open Dimension Designer for the Employee dimension.</span></span>

2.  <span data-ttu-id="0f116-114">**브라우저** 탭을 클릭하여 **계층** 목록에서 **Employees** 가 선택되어 있는지 확인한 다음 **All Employees** 멤버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-114">Click the **Browser** tab, verify that **Employees** is selected in the **Hierarchy** list, and then expand the **All Employees** member.</span></span>

     <span data-ttu-id="0f116-115">**Ken J. Sánchez** 는 이 부모-자식 계층에서 최상위 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-115">Notice that **Ken J. Sánchez** is the top-level manager in this parent-child hierarchy.</span></span>

3.  <span data-ttu-id="0f116-116">**Ken J. Sánchez** 멤버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-116">Select the **Ken J. Sánchez** member.</span></span>

     <span data-ttu-id="0f116-117">이 멤버의 수준 이름은 **Level 02**입니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-117">Notice that the level name for this member is **Level 02**.</span></span> <span data-ttu-id="0f116-118">수준 이름은 **All Employees** 멤버 바로 위의 **현재 수준:** 다음에 나타납니다. 다음 태스크에서는 각 수준의 보다 설명적인 이름을 정의하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-118">(The level name appears after **Current level:** immediately above the **All Employees** member.) In the next task, you will define more descriptive names for each level.</span></span>

4.  <span data-ttu-id="0f116-119">**Ken J. Sánchez** 를 확장하여 이 관리자에게 보고하는 직원의 이름을 표시한 다음 **Brian S. Welcker** 를 선택하여 이 수준의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-119">Expand **Ken J. Sánchez** to view the names of the employees who report to this manager, and then select **Brian S. Welcker** to view the name of this level.</span></span>

     <span data-ttu-id="0f116-120">이 멤버의 수준 이름은 **Level 03**입니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-120">Notice that the level name for this member is **Level 03**.</span></span>

5.  <span data-ttu-id="0f116-121">솔루션 탐색기의 **큐브** 폴더에서 **Analysis Services Tutorial.cube** 를 두 번 클릭하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 대한 큐브 디자이너를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-121">In Solution Explorer, double-click **Analysis Services Tutorial.cube** in the **Cubes** folder to open Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>

6.  <span data-ttu-id="0f116-122">**브라우저** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-122">Click the **Browser** tab.</span></span>

7.  <span data-ttu-id="0f116-123">Excel 아이콘을 클릭한 다음 연결을 사용하도록 설정할지 묻는 메시지가 나타나면 **사용** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-123">Click the Excel icon, and then click **Enable** when prompted to enable connections.</span></span>

8.  <span data-ttu-id="0f116-124">피벗 테이블 필드 목록에서 **Reseller Sales**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-124">In the PivotTable Field List, expand **Reseller Sales**.</span></span> <span data-ttu-id="0f116-125">**Reseller Sales-Sales Amount** 를 값 영역으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-125">Drag **Reseller Sales-Sales Amount** to the Values area.</span></span>

9. <span data-ttu-id="0f116-126">피벗 테이블 필드 목록에서 **Employee**를 확장한 다음 **Employees** 계층을 **행** 영역으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-126">In the PivotTable Field List, expand **Employee**, and then drag the **Employees** hierarchy to the **Rows** area.</span></span>

     <span data-ttu-id="0f116-127">Employees 계층의 모든 멤버는 피벗 테이블 보고서의 A 열에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-127">All the members of the Employees hierarchy are added to column A of the PivotTable report.</span></span>

     <span data-ttu-id="0f116-128">다음 그림에서는 확장된 Employees 계층을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-128">The following image shows the Employees hierarchy expanded.</span></span>

10. <span data-ttu-id="0f116-129">![직원 계층을 보여 주는 피벗 테이블](../../2014/tutorials/media/l4-employee-1.gif "직원 계층을 보여 주는 피벗 테이블")</span><span class="sxs-lookup"><span data-stu-id="0f116-129">![PivotTable showing Employees hierarchy](../../2014/tutorials/media/l4-employee-1.gif "PivotTable showing Employees hierarchy")</span></span>

     <span data-ttu-id="0f116-130">Level 03의 각 관리자가 판매한 판매량도 Level 04에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-130">Notice that the sales made by each manager in Level 03 are also displayed in Level 04.</span></span> <span data-ttu-id="0f116-131">각 관리자도 다른 관리자의 직원이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-131">This is because each manager is also an employee of another manager.</span></span> <span data-ttu-id="0f116-132">다음 태스크에서는 이러한 판매량을 숨기는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-132">In the next task, you will hide these sale amounts.</span></span>

## <a name="modifying-parent-attribute-properties-in-the-employee-dimension"></a><span data-ttu-id="0f116-133">Employee 차원의 부모 특성 속성 수정</span><span class="sxs-lookup"><span data-stu-id="0f116-133">Modifying Parent Attribute Properties in the Employee Dimension</span></span>

1.  <span data-ttu-id="0f116-134">**Employee** 차원에 대한 차원 디자이너로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-134">Switch to Dimension Designer for the **Employee** dimension.</span></span>

2.  <span data-ttu-id="0f116-135">**차원 구조** 탭을 클릭한 다음 **특성** 창에서 **Employees** 특성 계층을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-135">Click the **Dimension Structure** tab, and then select the **Employees** attribute hierarchy in the **Attributes** pane.</span></span>

     <span data-ttu-id="0f116-136">이 특성의 고유 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-136">Notice the unique icon for this attribute.</span></span> <span data-ttu-id="0f116-137">이 아이콘은 해당 특성이 부모-자식 계층의 부모 키임을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-137">This icon signifies that the attribute is the parent key in a parent-child hierarchy.</span></span> <span data-ttu-id="0f116-138">또한 속성 창에서 해당 특성의 **Usage** 속성은 **Parent**로 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-138">Notice also, in the Properties window, that the **Usage** property for the attribute is defined as **Parent**.</span></span> <span data-ttu-id="0f116-139">이 속성은 차원이 디자인될 때 차원 마법사에 의해 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-139">This property was set by the Dimension Wizard when the dimension was designed.</span></span> <span data-ttu-id="0f116-140">마법사는 부모-자식 관계를 자동으로 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-140">The wizard automatically detected the parent-child relationship.</span></span>

3.  <span data-ttu-id="0f116-141">속성 창의**NamingTemplate**속성 셀에서 줄임표 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-141">In the Properties window, click the ellipsis button (**...**) in the **NamingTemplate** property cell.</span></span>

     <span data-ttu-id="0f116-142">**수준 명명 템플릿** 대화 상자에서 사용자가 큐브를 찾아볼 때 표시되는 부모-자식 계층의 수준 이름을 지정하는 수준 명명 템플릿을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-142">In the **Level Naming Template** dialog box, you define the level naming template that determines the level names in the parent-child hierarchy that are displayed to users as they browse cubes.</span></span>

4.  <span data-ttu-id="0f116-143">두 번째 행의 행에서 **\*** **이름** 열에 \*\*Employee Level \* \*\* 을 입력 한 다음 세 번째 행을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-143">In the second row, the **\*** row, type **Employee Level \*** in the **Name** column, and then click the third row.</span></span>

     <span data-ttu-id="0f116-144">**결과** 아래에서 순차적으로 증가하는 번호 다음에 나오는 각 수준의 이름이 "Employee Level"이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-144">Notice under **Result** that each level will now be named "Employee Level" followed by a sequentially increasing number.</span></span>

     <span data-ttu-id="0f116-145">다음 그림에서는 **수준 명명 템플릿** 대화 상자에서 변경 내용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-145">The following image shows the changes in the **Level Naming Template** dialog box.</span></span>

     <span data-ttu-id="0f116-146">![수준 명명 템플릿 대화 상자](../../2014/tutorials/media/l4-namingtemplate.gif "수준 명명 템플릿 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="0f116-146">![Level Naming Template dialog box](../../2014/tutorials/media/l4-namingtemplate.gif "Level Naming Template dialog box")</span></span>

5.  <span data-ttu-id="0f116-147">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-147">Click **OK**.</span></span>

6.  <span data-ttu-id="0f116-148">**Employees** 특성의 속성 창에 있는 **MembersWithData** 속성 셀에서 **NonLeafDataHidden** 을 선택하여 **Employees** 특성에 대해 이 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-148">In the Properties window for the **Employees** attribute, in the **MembersWithData** property cell, select **NonLeafDataHidden** to change this value for the **Employees** attribute.</span></span>

     <span data-ttu-id="0f116-149">이렇게 하면 부모-자식 계층의 리프 수준이 아닌 멤버와 관련된 데이터가 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-149">This will cause data that is related to non-leaf level members in the parent-child hierarchy to be hidden.</span></span>

## <a name="browsing-the-employee-dimension-with-the-modified-attributes"></a><span data-ttu-id="0f116-150">특성이 수정된 Employee 차원 찾아보기</span><span class="sxs-lookup"><span data-stu-id="0f116-150">Browsing the Employee Dimension with the Modified Attributes</span></span>

1.  <span data-ttu-id="0f116-151">**의** 빌드 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-151">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="0f116-152">배포가 성공적으로 완료되면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 대한 큐브 디자이너로 전환한 후 **브라우저** 탭의 도구 모음에서 **다시 연결** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-152">When deployment has successfully completed, switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect** on the toolbar of the **Browser** tab.</span></span>

3.  <span data-ttu-id="0f116-153">Excel 아이콘을 클릭한 다음 **사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-153">Click the Excel icon, and then click **Enable**.</span></span>

4.  <span data-ttu-id="0f116-154">**Reseller Sales-Sales Amount** 를 값 영역으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-154">Drag **Reseller Sales-Sales Amount** to the Values area.</span></span>

5.  <span data-ttu-id="0f116-155">**Employees** 계층을 행 레이블 영역으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-155">Drag the **Employees** hierarchy to the Row Labels area.</span></span>

     <span data-ttu-id="0f116-156">다음 이미지에서는 Employees 계층의 변경 내용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-156">The following image shows the changes that you made to the Employees hierarchy.</span></span> <span data-ttu-id="0f116-157">Stephen Y. Jiang은 더 이상 직원으로 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0f116-157">Notice that Stephen Y. Jiang no longer appears as an employee of himself.</span></span>

     <span data-ttu-id="0f116-158">![수정된 직원 계층](../../2014/tutorials/media/l4-employee-2.png "수정된 직원 계층")</span><span class="sxs-lookup"><span data-stu-id="0f116-158">![Modified Employees hierarchy](../../2014/tutorials/media/l4-employee-2.png "Modified Employees hierarchy")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="0f116-159">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="0f116-159">Next Task in Lesson</span></span>
 [<span data-ttu-id="0f116-160">자동으로 특성 멤버 그룹화</span><span class="sxs-lookup"><span data-stu-id="0f116-160">Automatically Grouping Attribute Members</span></span>](lesson-4-3-automatically-grouping-attribute-members.md)

## <a name="see-also"></a><span data-ttu-id="0f116-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0f116-161">See Also</span></span>
 <span data-ttu-id="0f116-162">부모-자식 계층의 [부모-자식 계층](multidimensional-models/parent-child-dimension.md) [특성](multidimensional-models/parent-child-dimension-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="0f116-162">[Parent-Child Hierarchy](multidimensional-models/parent-child-dimension.md) [Attributes in Parent-Child Hierarchies](multidimensional-models/parent-child-dimension-attributes.md)</span></span>


