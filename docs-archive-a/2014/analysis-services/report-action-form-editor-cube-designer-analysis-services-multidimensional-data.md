---
title: 보고서 동작 폼 편집기 (동작 탭, 큐브 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionexpression.reportaction.f1
ms.assetid: cebfdd07-e376-46d6-86ef-b6f816a2f360
author: minewiskan
ms.author: owend
ms.openlocfilehash: a6e417f666ec5e6827763257eff19294e21543b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652387"
---
# <a name="report-action-form-editor-actions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="5b3af-102">보고서 동작 폼 편집기(동작 탭, 큐브 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="5b3af-102">Report Action Form Editor (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="5b3af-103">큐브 디자이너의 **작업** 탭에 있는 **보고 동작 폼 편집기** 창을 사용하여 **작업 구성 도우미** 창에서 선택한 보고 작업을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-103">Use the **Report Action Form Editor** pane on the **Actions** tab in Cube Designer to modify the report action selected in the **Action Organizer** pane.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5b3af-104">옵션</span><span class="sxs-lookup"><span data-stu-id="5b3af-104">Options</span></span>  
 <span data-ttu-id="5b3af-105">**이름**</span><span class="sxs-lookup"><span data-stu-id="5b3af-105">**Name**</span></span>  
 <span data-ttu-id="5b3af-106">동작의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-106">Type the name of the action.</span></span>  
  
 <span data-ttu-id="5b3af-107">**동작 대상**</span><span class="sxs-lookup"><span data-stu-id="5b3af-107">**Action Target**</span></span>  
 <span data-ttu-id="5b3af-108">**대상 유형** 및 **대상 개체** 옵션을 보려면 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-108">Expand to view the **Target type** and **Target object** options.</span></span>  
  
 <span data-ttu-id="5b3af-109">**대상 유형**</span><span class="sxs-lookup"><span data-stu-id="5b3af-109">**Target type**</span></span>  
 <span data-ttu-id="5b3af-110">동작을 연결할 개체의 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-110">Select the type of object to which the action is to be associated.</span></span> <span data-ttu-id="5b3af-111">서버는 지정한 유형의 개체에 해당되는 동작만 클라이언트에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-111">The server returns to the client only those actions that apply to the object of the specified type.</span></span> <span data-ttu-id="5b3af-112">**조건** 을 만족하고 다음 표에 지정된 개체를 선택한 경우에만 클라이언트에서 이러한 동작을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-112">The action is available to the client if the **Condition** is met and if the objects specified in the following table are selected.</span></span>  
  
|<span data-ttu-id="5b3af-113">값</span><span class="sxs-lookup"><span data-stu-id="5b3af-113">Value</span></span>|<span data-ttu-id="5b3af-114">선택한 개체</span><span class="sxs-lookup"><span data-stu-id="5b3af-114">Selected Object</span></span>|  
|-----------|---------------------|  
|<span data-ttu-id="5b3af-115">특성 멤버</span><span class="sxs-lookup"><span data-stu-id="5b3af-115">Attribute members</span></span>|<span data-ttu-id="5b3af-116">**대상 개체**의 특성에 기반한 수준에서 멤버가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-116">A member is selected from a level based on the attribute in **Target object**.</span></span><br /><br /> <span data-ttu-id="5b3af-117">참고: 선택한 특성을 사용하는 다른 사용자 계층은 보고 동작을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-117">Note: Other user hierarchies that use the selected attribute inherit the report action.</span></span>|  
|<span data-ttu-id="5b3af-118">셀</span><span class="sxs-lookup"><span data-stu-id="5b3af-118">Cells</span></span>|<span data-ttu-id="5b3af-119">**대상 개체** 의 명명된 집합이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-119">The named set in **Target object** is selected.</span></span> <span data-ttu-id="5b3af-120">큐브의 모든 셀을 선택하려면 **셀 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-120">Select **All cells** to select all of the cells in the cube.</span></span>|  
|<span data-ttu-id="5b3af-121">큐브</span><span class="sxs-lookup"><span data-stu-id="5b3af-121">Cube</span></span>|<span data-ttu-id="5b3af-122">**대상 개체** 의 큐브가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-122">The cube in **Target object** is selected.</span></span> <span data-ttu-id="5b3af-123">현재 큐브를 사용하려면 CURRENTCUBE를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-123">Select CURRENTCUBE to use the current cube.</span></span><br /><br /> <span data-ttu-id="5b3af-124">참고: CURRENTCUBE를 사용하면 큐브의 이름을 바꾸거나 동작을 다른 큐브로 복사하는 경우 이식성이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-124">Note: Using CURRENTCUBE provides additional portability in cases where the cube may be renamed or the action copied to other cubes.</span></span> <span data-ttu-id="5b3af-125">CURRENTCUBE를 사용하여 현재 큐브를 나타내는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-125">It is recommended that you use CURRENTCUBE to represent the current cube.</span></span>|  
|<span data-ttu-id="5b3af-126">차원 멤버</span><span class="sxs-lookup"><span data-stu-id="5b3af-126">Dimension members</span></span>|<span data-ttu-id="5b3af-127">**대상 개체** 의 차원 멤버가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-127">A member of the dimension in **Target object** is selected.</span></span>|  
|<span data-ttu-id="5b3af-128">계층</span><span class="sxs-lookup"><span data-stu-id="5b3af-128">Hierarchy</span></span>|<span data-ttu-id="5b3af-129">**대상 개체** 의 계층이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-129">The hierarchy in **Target object** is selected.</span></span>|  
|<span data-ttu-id="5b3af-130">계층 멤버</span><span class="sxs-lookup"><span data-stu-id="5b3af-130">Hierarchy members</span></span>|<span data-ttu-id="5b3af-131">**대상 개체** 의 계층 내에 있는 멤버가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-131">A member within the hierarchy in **Target object** is selected.</span></span>|  
|<span data-ttu-id="5b3af-132">Level</span><span class="sxs-lookup"><span data-stu-id="5b3af-132">Level</span></span>|<span data-ttu-id="5b3af-133">**대상 개체** 의 수준이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-133">The level in **Target object** is selected.</span></span>|  
|<span data-ttu-id="5b3af-134">수준 멤버</span><span class="sxs-lookup"><span data-stu-id="5b3af-134">Level members</span></span>|<span data-ttu-id="5b3af-135">**대상 개체** 의 수준 내에 있는 멤버가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-135">A member within the level in **Target object** is selected.</span></span>|  
  
 <span data-ttu-id="5b3af-136">**대상 개체**</span><span class="sxs-lookup"><span data-stu-id="5b3af-136">**Target object**</span></span>  
 <span data-ttu-id="5b3af-137">동작을 연결할 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-137">Select the object to which the action is to be associated.</span></span> <span data-ttu-id="5b3af-138">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스는 선택한 개체에 적용 되는 동작만 클라이언트에 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-138">The [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance returns to the client only those actions that apply to the selected object.</span></span> <span data-ttu-id="5b3af-139">사용 가능한 개체 목록은 **대상 유형**에서 선택한 항목에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-139">The list of available objects is constrained by the choice of **Target type**.</span></span>  
  
 <span data-ttu-id="5b3af-140">**조건(옵션)**</span><span class="sxs-lookup"><span data-stu-id="5b3af-140">**Condition (Optional)**</span></span>  
 <span data-ttu-id="5b3af-141">선택적 조건을 기술하는 MDX(Multidimensional Expression) 식을 입력합니다. 이 옵션은 **대상 개체**와 함께 사용되어 동작의 가용성을 추가로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-141">Enter the Multidimensional Expressions (MDX) expression that describes an optional condition, used in conjunction with **Target object**, which further restricts when the action is available.</span></span> <span data-ttu-id="5b3af-142">식은 부울 값을 반환해야 합니다. True인 경우 동작을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-142">The expression must return a Boolean value that, if true, indicates the action is available.</span></span>  
  
 <span data-ttu-id="5b3af-143">**계산 도구** 창에서 선택한 요소를 이 옵션으로 끌어서 놓으면 선택한 요소의 MDX 구문을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-143">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="5b3af-144">**보고서 서버**</span><span class="sxs-lookup"><span data-stu-id="5b3af-144">**Report Server**</span></span>  
 <span data-ttu-id="5b3af-145">**서버 이름**, **서버 경로**및 **보고서 형식** 옵션을 보려면 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-145">Expand to view the **Server name**, **Server path**, and **Report format** options.</span></span>  
  
 <span data-ttu-id="5b3af-146">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="5b3af-146">**Server name**</span></span>  
 <span data-ttu-id="5b3af-147">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 동작에서 보고서를 실행 하는 인스턴스의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-147">Type the name of the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] instance on which the action runs the report.</span></span>  
  
 <span data-ttu-id="5b3af-148">**서버 경로**</span><span class="sxs-lookup"><span data-stu-id="5b3af-148">**Server path**</span></span>  
 <span data-ttu-id="5b3af-149">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 인스턴스의 보고서 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-149">Type the path to the report on the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] instance.</span></span> <span data-ttu-id="5b3af-150">예를 들어 **Sales/YearlySalesByCategory**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-150">For example, type **Sales/YearlySalesByCategory**.</span></span>  
  
 <span data-ttu-id="5b3af-151">**보고서 형식**</span><span class="sxs-lookup"><span data-stu-id="5b3af-151">**Report format**</span></span>  
 <span data-ttu-id="5b3af-152">보고서를 반환할 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-152">Select the format in which the report is returned.</span></span> <span data-ttu-id="5b3af-153">다음 표에서는 사용 가능한 형식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-153">The following table describes the available formats.</span></span>  
  
|<span data-ttu-id="5b3af-154">값</span><span class="sxs-lookup"><span data-stu-id="5b3af-154">Value</span></span>|<span data-ttu-id="5b3af-155">Description</span><span class="sxs-lookup"><span data-stu-id="5b3af-155">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5b3af-156">HTML5</span><span class="sxs-lookup"><span data-stu-id="5b3af-156">HTML5</span></span>|<span data-ttu-id="5b3af-157">보고서는 HTML 5.0 호환 형식으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-157">Report is returned in an HTML 5.0-compliant format.</span></span>|  
|<span data-ttu-id="5b3af-158">HTML3</span><span class="sxs-lookup"><span data-stu-id="5b3af-158">HTML3</span></span>|<span data-ttu-id="5b3af-159">보고서는 HTML 3.2 호환 형식으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-159">Report is returned in an HTML 3.2-compliant format.</span></span>|  
|<span data-ttu-id="5b3af-160">Excel</span><span class="sxs-lookup"><span data-stu-id="5b3af-160">Excel</span></span>|<span data-ttu-id="5b3af-161">보고서는 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 통합 문서(.xls) 파일로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-161">Report is returned as a [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel workbook (.xls) file.</span></span>|  
|<span data-ttu-id="5b3af-162">PDF</span><span class="sxs-lookup"><span data-stu-id="5b3af-162">PDF</span></span>|<span data-ttu-id="5b3af-163">보고서는 Adobe Portable Document Format(.pdf) 파일로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-163">Report is returned as an Adobe Portable Document Format (.pdf) file.</span></span>|  
  
 <span data-ttu-id="5b3af-164">**매개 변수(옵션)**</span><span class="sxs-lookup"><span data-stu-id="5b3af-164">**Parameters (Optional)**</span></span>  
 <span data-ttu-id="5b3af-165">**보고서**에서 지정한 보고서에 대해 제공할 수 있는 보고서 매개 변수 표를 보려면 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-165">Expand to view a grid in which report parameters can be supplied for the report specified in **Report**.</span></span> <span data-ttu-id="5b3af-166">표에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-166">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="5b3af-167">열</span><span class="sxs-lookup"><span data-stu-id="5b3af-167">Column</span></span>|<span data-ttu-id="5b3af-168">Description</span><span class="sxs-lookup"><span data-stu-id="5b3af-168">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5b3af-169">**매개 변수 이름**</span><span class="sxs-lookup"><span data-stu-id="5b3af-169">**Parameter Name**</span></span>|<span data-ttu-id="5b3af-170">보고서로 전달할 보고서 매개 변수의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-170">Type the name of the report parameter to be passed to the report.</span></span>|  
|<span data-ttu-id="5b3af-171">**매개 변수 값**</span><span class="sxs-lookup"><span data-stu-id="5b3af-171">**Parameter Value**</span></span>|<span data-ttu-id="5b3af-172">보고서로 전달할 보고서 매개 변수의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-172">Type the value of the report parameter to be passed to the report.</span></span><br /><br /> <span data-ttu-id="5b3af-173">줄임표 단추 (**...**)를 클릭하여 **MDX 작성기** 대화 상자를 표시하고 보고서 매개 변수의 값을 제공하는 MDX 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-173">Click the ellipsis button (**...**) to display the **MDX Builder** dialog box and create an MDX expression that provides the value of the report parameter.</span></span> <span data-ttu-id="5b3af-174">**MDX 작성기** 대화 상자에 대한 자세한 내용은 [MDX 작성기&#40;Analysis Services - 다차원 데이터&#41;](mdx-builder-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5b3af-174">For more information about the **MDX Builder** dialog box, see [MDX Builder &#40;Analysis Services - Multidimensional Data&#41;](mdx-builder-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="5b3af-175">매개 변수를 MDX 식에 설정하면 동작을 실행할 때 해당 식을 평가하고, 매개 변수를 MDX 식에 설정하지 않으면 해당 식을 수정하지 않고 보고서에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-175">If the parameter is set to an MDX expression, then the expression is evaluated when the action is run, otherwise it is passed to the report without modification.</span></span>|  
  
 <span data-ttu-id="5b3af-176">**추가 속성**</span><span class="sxs-lookup"><span data-stu-id="5b3af-176">**Additional Properties**</span></span>  
 <span data-ttu-id="5b3af-177">확장하면 **호출**, **애플리케이션**, **설명**, **캡션**및 **MDX 캡션** 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-177">Expand to view the **Invocation**, **Application**, **Description**, **Caption**, and **Caption Is MDX** options.</span></span>  
  
 <span data-ttu-id="5b3af-178">**호출**</span><span class="sxs-lookup"><span data-stu-id="5b3af-178">**Invocation**</span></span>  
 <span data-ttu-id="5b3af-179">동작 실행 시기를 나타내는 설정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-179">Select the setting that indicates when the action should be carried out.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b3af-180">이 옵션은 클라이언트 애플리케이션에 동작 실행 시기에 대한 권장 사항만 제공할 뿐 직접 작업 호출을 제어하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-180">This option only provides a recommendation to a client application as to when to execute an action, and does not directly control the invocation of the action.</span></span>  
  
 <span data-ttu-id="5b3af-181">다음 표에서는 사용 가능한 설정에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-181">The following table describes the available settings.</span></span>  
  
|<span data-ttu-id="5b3af-182">값</span><span class="sxs-lookup"><span data-stu-id="5b3af-182">Value</span></span>|<span data-ttu-id="5b3af-183">Description</span><span class="sxs-lookup"><span data-stu-id="5b3af-183">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5b3af-184">Batch</span><span class="sxs-lookup"><span data-stu-id="5b3af-184">Batch</span></span>|<span data-ttu-id="5b3af-185">작업은 일괄 처리 작업이 나 태스크의 일부로 실행 해야 합니다 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5b3af-185">The action should run as part of a batch operation or a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] task.</span></span>|  
|<span data-ttu-id="5b3af-186">대화형</span><span class="sxs-lookup"><span data-stu-id="5b3af-186">Interactive</span></span>|<span data-ttu-id="5b3af-187">사용자가 작업을 호출할 때 동작이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-187">The action runs when the user invokes the action.</span></span>|  
|<span data-ttu-id="5b3af-188">열 때</span><span class="sxs-lookup"><span data-stu-id="5b3af-188">On Open</span></span>|<span data-ttu-id="5b3af-189">큐브를 처음으로 열 때 동작이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-189">The action runs when the cube is first opened.</span></span>|  
  
 <span data-ttu-id="5b3af-190">**애플리케이션**</span><span class="sxs-lookup"><span data-stu-id="5b3af-190">**Application**</span></span>  
 <span data-ttu-id="5b3af-191">**동작 식**에서 반환한 문자열을 해석할 수 있는 애플리케이션의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-191">Type the name of the application that can interpret the string returned by **Action expression**.</span></span>  
  
 <span data-ttu-id="5b3af-192">이 옵션을 사용하여 이 동작을 가장 많이 사용하는 클라이언트 애플리케이션을 식별하고 팝업 메뉴에서 해당 작업 옆에 적절한 아이콘을 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-192">You can also use this option to identify which client application most commonly uses this action, as well as to display appropriate icons next to the action in a pop-up menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b3af-193">이 옵션은 클라이언트 애플리케이션에 동작을 실행해야 하는 클라이언트 애플리케이션에 대한 권장 사항만 제공할 뿐 직접 작업에 대한 액세스를 제어하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-193">This option only provides a recommendation to a client application as to what client application should execute an action, and does not directly control access to the action.</span></span> <span data-ttu-id="5b3af-194">클라이언트 애플리케이션은 다른 클라이언트 애플리케이션에 연결된 모든 동작을 숨겨야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-194">Client applications should hide any actions that are associated with other client applications.</span></span>  
  
 <span data-ttu-id="5b3af-195">**설명**</span><span class="sxs-lookup"><span data-stu-id="5b3af-195">**Description**</span></span>  
 <span data-ttu-id="5b3af-196">동작에 대한 선택적 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-196">Type the optional description of the action.</span></span>  
  
 <span data-ttu-id="5b3af-197">**캡션**</span><span class="sxs-lookup"><span data-stu-id="5b3af-197">**Caption**</span></span>  
 <span data-ttu-id="5b3af-198">**MDX 캡션** 이 **False**로 설정된 경우 클라이언트 애플리케이션에서 동작에 대해 표시할 캡션을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-198">Type the caption to be displayed for the action in the client application if **Caption Is MDX** is set to **False**.</span></span>  
  
 <span data-ttu-id="5b3af-199">**MDX 캡션** 이 **True**로 설정된 경우 캡션 문자열을 반환하는 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-199">Type the MDX expression that returns a string for the caption if **Caption Is MDX** is set to **True**.</span></span>  
  
 <span data-ttu-id="5b3af-200">**MDX 캡션**</span><span class="sxs-lookup"><span data-stu-id="5b3af-200">**Caption is MDX**</span></span>  
 <span data-ttu-id="5b3af-201">클라이언트 애플리케이션에서 동작에 대해 표시할 캡션을 나타내는 리터럴 문자열이 **캡션** 에 포함되어 있음을 나타내려면 **False** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-201">Select **False** to indicate that **Caption** contains a literal string representing a caption to be displayed for the action in the client application.</span></span>  
  
 <span data-ttu-id="5b3af-202">클라이언트 애플리케이션에서 동작에 대해 표시할 캡션을 나타내는 문자열을 반환하는 MDX 식이 **캡션** 에 포함되어 있음을 나타내려면 **True** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-202">Select **True** to indicate that **Caption** contains an MDX expression that returns a string representing a caption to be displayed for the action in the client application.</span></span> <span data-ttu-id="5b3af-203">클라이언트 애플리케이션으로 동작을 반환하기 전에 MDX 식을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3af-203">The MDX expression must be resolved before the action is returned to the client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b3af-204">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5b3af-204">See Also</span></span>  
 <span data-ttu-id="5b3af-205">[큐브 디자이너 Analysis Services&#41; &#40;&#40;작업은 다차원 데이터&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5b3af-205">[Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="5b3af-206">[도구 모음 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5b3af-206">[Toolbar &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="5b3af-207">[동작 구성 도우미 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5b3af-207">[Action Organizer &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="5b3af-208">[계산 도구 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5b3af-208">[Calculation Tools &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="5b3af-209">[작업 폼 편집기 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5b3af-209">[Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="5b3af-210">드릴스루 동작 폼 편집기 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="5b3af-210">Drillthrough Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  
