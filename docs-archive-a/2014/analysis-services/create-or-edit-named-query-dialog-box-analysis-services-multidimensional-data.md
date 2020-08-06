---
title: 명명 된 쿼리 만들기 또는 편집 대화 상자 (다차원 데이터 Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.createnamedquery.f1
helpviewer_keywords:
- Create Named Query dialog box
ms.assetid: 8e192ad6-a0b1-4e21-bb3f-087c93e62941
author: minewiskan
ms.author: owend
ms.openlocfilehash: cb255a44d2dde18e8d5e20343c7c5396f2e867d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649275"
---
# <a name="create-or-edit-named-query-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="812af-102">명명된 쿼리 만들기 또는 편집 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="812af-102">Create or Edit Named Query Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="812af-103">**의** 명명된 쿼리 만들기/편집 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 대화 상자를 사용하여 **데이터 원본 뷰 디자이너**에서 명명된 쿼리를 생성 또는 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="812af-103">Use the **Create/Edit Named Query** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create or edit a named query in **Data Source View Designer**.</span></span> <span data-ttu-id="812af-104">명명된 쿼리를 다른 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체의 기반으로 사용할 수 있는 테이블로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="812af-104">A named query can be treated as a table, on which you can base other [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects.</span></span> <span data-ttu-id="812af-105">다음을 수행하여 **명명된 쿼리 만들기/편집** 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="812af-105">You can display the **Create/Edit Named Query** dialog box by:</span></span>  
  
-   <span data-ttu-id="812af-106">**데이터 원본 뷰 디자이너** 의 **도구 모음** 창에 있는 **새 명명된 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-106">Clicking **New Named Query** on the **Toolbar** pane of **Data Source View Designer**.</span></span>  
  
-   <span data-ttu-id="812af-107">**데이터 원본 뷰 디자이너** 의 **다이어그램** 창을 마우스 오른쪽 단추로 클릭한 다음 **새 명명된 쿼리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-107">Right-clicking the **Diagram** pane of **Data Source View Designer** and selecting **New Named Query**.</span></span>  
  
-   <span data-ttu-id="812af-108">**데이터 원본 뷰 디자이너** 의 **다이어그램** 또는 **테이블** 창에서 명명된 쿼리의 이름을 마우스 오른쪽 단추로 클릭한 다음 **명명된 쿼리 편집**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-108">Right-clicking the name of a named query in the **Diagram** or **Tables** pane of **Data Source View Designer** and selecting **Edit Named Query**.</span></span>  
  
 <span data-ttu-id="812af-109">기본 공급자에 유효한 쿼리 명령을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-109">The query entered must be a valid query command for the underlying provider.</span></span> <span data-ttu-id="812af-110">쿼리는 유효성 검사에 사용할 기본 공급자와 함께 준비되며 반환된 열을 식별하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-110">The query is prepared with the underlying provider for validation, and to identify the columns returned.</span></span> <span data-ttu-id="812af-111">대화 상자는 다음 두 가지 뷰를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-111">The dialog box can present two views:</span></span>  
  
-   <span data-ttu-id="812af-112">VDT(Visual Database Tools) 쿼리 작성기</span><span class="sxs-lookup"><span data-stu-id="812af-112">Visual Database Tools (VDT) Query Builder</span></span>  
  
     <span data-ttu-id="812af-113">VDT 쿼리 작성기 뷰에서는 모든 사용자를 위해 SQL 쿼리를 시각적으로 생성하고 테스트할 수 있는 사용자 인터페이스 도구 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-113">For all users, the VDT Query Builder view provides a set of user interface tools for visually constructing and testing a SQL query.</span></span>  
  
-   <span data-ttu-id="812af-114">일반 쿼리 작성기</span><span class="sxs-lookup"><span data-stu-id="812af-114">Generic Query Builder</span></span>  
  
     <span data-ttu-id="812af-115">일반 쿼리 작성기 뷰에서는 고급 사용자를 위해 SQL 쿼리를 생성하고 테스트할 수 있는 보다 단순하고 직접적인 사용자 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-115">For advanced users, the Generic Query Builder view provides a simpler, more direct user interface for constructing and testing a SQL query.</span></span>  
  
## <a name="options"></a><span data-ttu-id="812af-116">옵션</span><span class="sxs-lookup"><span data-stu-id="812af-116">Options</span></span>  
 <span data-ttu-id="812af-117">**이름**</span><span class="sxs-lookup"><span data-stu-id="812af-117">**Name**</span></span>  
 <span data-ttu-id="812af-118">쿼리의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-118">Type the name of the query.</span></span>  
  
 <span data-ttu-id="812af-119">**설명**</span><span class="sxs-lookup"><span data-stu-id="812af-119">**Description**</span></span>  
 <span data-ttu-id="812af-120">쿼리에 대한 선택적 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-120">Type the optional description of the query.</span></span>  
  
 <span data-ttu-id="812af-121">**데이터 원본**</span><span class="sxs-lookup"><span data-stu-id="812af-121">**Data Source**</span></span>  
 <span data-ttu-id="812af-122">쿼리의 데이터 원본을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-122">Specifies the data source for the query.</span></span>  
  
 <span data-ttu-id="812af-123">**쿼리 정의**</span><span class="sxs-lookup"><span data-stu-id="812af-123">**Query definition**</span></span>  
 <span data-ttu-id="812af-124">쿼리 정의에서는 선택한 뷰에 따라 쿼리를 정의하고 테스트할 수 있는 도구 모음 및 창을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-124">The query definition provides a toolbar and panes in which to define and test the query, depending on the selected view.</span></span>  
  
 <span data-ttu-id="812af-125">**도구 모음**</span><span class="sxs-lookup"><span data-stu-id="812af-125">**Toolbar**</span></span>  
 <span data-ttu-id="812af-126">도구 모음을 사용하여 데이터 세트를 관리하고, 표시할 창을 선택하고, 다양한 쿼리 함수를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="812af-126">Use the toolbar to manage datasets, select panes to display, and control various query functions.</span></span>  
  
|<span data-ttu-id="812af-127">값</span><span class="sxs-lookup"><span data-stu-id="812af-127">Value</span></span>|<span data-ttu-id="812af-128">Description</span><span class="sxs-lookup"><span data-stu-id="812af-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="812af-129">**일반 쿼리 작성기로 전환**</span><span class="sxs-lookup"><span data-stu-id="812af-129">**Switch to Generic Query Builder**</span></span>|<span data-ttu-id="812af-130">일반 쿼리 작성기 뷰에 사용할 수 있는 옵션만 표시하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-130">Select to display only the options available to the Generic Query Builder view.</span></span> <span data-ttu-id="812af-131">다음 옵션만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-131">Only the following options are displayed:</span></span><br /><span data-ttu-id="812af-132">**SQL 창**</span><span class="sxs-lookup"><span data-stu-id="812af-132">**SQL pane**</span></span><br /><span data-ttu-id="812af-133">**결과 창**</span><span class="sxs-lookup"><span data-stu-id="812af-133">**Result pane**</span></span><br /><span data-ttu-id="812af-134">**도구 모음**( **VDT 쿼리 작성기로 전환** 및 **실행**</span><span class="sxs-lookup"><span data-stu-id="812af-134">**Toolbar**, containing only **Switch to VDT Query Builder** and **Run**</span></span><br /><br /> <br /><br /> <span data-ttu-id="812af-135">참고: 이 옵션은 **VDT 쿼리 작성기로 전환** 을 선택할 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-135">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="812af-136">**VDT 쿼리 작성기로 전환**</span><span class="sxs-lookup"><span data-stu-id="812af-136">**Switch to VDT Query Builder**</span></span>|<span data-ttu-id="812af-137">이 옵션을 선택하면 VDT(Visual Database Tools) 쿼리 작성기 뷰에 사용할 수 있는 모든 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-137">Select to display all of the options available to the Visual Database Tools (VDT) Query Builder view.</span></span><br /><br /> <span data-ttu-id="812af-138">참고: 이 옵션은 **일반 쿼리 작성기로 전환** 을 선택할 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-138">Note: This option is displayed only if **Switch to Generic Query Builder** is selected.</span></span>|  
|<span data-ttu-id="812af-139">**다이어그램 창 표시/숨기기**</span><span class="sxs-lookup"><span data-stu-id="812af-139">**Show/Hide Diagram Pane**</span></span>|<span data-ttu-id="812af-140">**다이어그램 창을**표시 하거나 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="812af-140">Shows or hides the **Diagram pane**.</span></span><br /><br /> <span data-ttu-id="812af-141">**참고** 이 옵션은 **VDT 쿼리 작성기로 전환** 을 선택한 경우에만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-141">**Note** This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="812af-142">**표 형태 창 표시/숨기기**</span><span class="sxs-lookup"><span data-stu-id="812af-142">**Show/Hide Grid Pane**</span></span>|<span data-ttu-id="812af-143">**표 형태 창을**표시 하거나 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="812af-143">Shows or hides the **Grid pane**.</span></span><br /><br /> <span data-ttu-id="812af-144">참고: 이 옵션은 **VDT 쿼리 작성기로 전환** 을 선택할 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-144">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="812af-145">**SQL 창 표시/숨기기**</span><span class="sxs-lookup"><span data-stu-id="812af-145">**Show/Hide SQL Pane**</span></span>|<span data-ttu-id="812af-146">**SQL 창**을 표시하거나 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="812af-146">Shows or hides the **SQL pane**.</span></span><br /><br /> <span data-ttu-id="812af-147">참고: 이 옵션은 **VDT 쿼리 작성기로 전환** 을 선택할 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-147">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="812af-148">**결과 창 표시/숨기기**</span><span class="sxs-lookup"><span data-stu-id="812af-148">**Show/Hide Result Pane**</span></span>|<span data-ttu-id="812af-149">**결과 창**을 표시하거나 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="812af-149">Shows or hides the **Result pane**.</span></span><br /><br /> <span data-ttu-id="812af-150">참고: 이 옵션은 **VDT 쿼리 작성기로 전환** 을 선택할 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-150">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="812af-151">**Run**</span><span class="sxs-lookup"><span data-stu-id="812af-151">**Run**</span></span>|<span data-ttu-id="812af-152">쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-152">Runs the query.</span></span> <span data-ttu-id="812af-153">결과는 **결과 창**에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-153">Results are displayed in the **Result pane**.</span></span>|  
|<span data-ttu-id="812af-154">**SQL 검증**</span><span class="sxs-lookup"><span data-stu-id="812af-154">**Verify SQL**</span></span>|<span data-ttu-id="812af-155">쿼리에서 SQL 문을 검증합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-155">Verifies the SQL statement in the query.</span></span><br /><br /> <span data-ttu-id="812af-156">참고: 이 옵션은 **VDT 쿼리 작성기로 전환** 을 선택할 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-156">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="812af-157">**오름차순 정렬**</span><span class="sxs-lookup"><span data-stu-id="812af-157">**Sort Ascending**</span></span>|<span data-ttu-id="812af-158">**표 형태 창**에서 선택한 열의 출력 행을 오름차순으로 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-158">Sorts output rows on the selected column in the **Grid pane**, in ascending order.</span></span><br /><br /> <span data-ttu-id="812af-159">참고: 이 옵션은 **VDT 쿼리 작성기로 전환** 을 선택할 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-159">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="812af-160">**내림차순 정렬**</span><span class="sxs-lookup"><span data-stu-id="812af-160">**Sort Descending**</span></span>|<span data-ttu-id="812af-161">**표 형태 창**에서 선택한 열의 출력 행을 내림차순으로 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-161">Sorts output rows on the selected column in the **Grid pane**, in descending order.</span></span><br /><br /> <span data-ttu-id="812af-162">참고: 이 옵션은 **VDT 쿼리 작성기로 전환** 을 선택할 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-162">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="812af-163">**필터 제거**</span><span class="sxs-lookup"><span data-stu-id="812af-163">**Remove Filter**</span></span>|<span data-ttu-id="812af-164">해당 사항이 있을 경우 **표 형태 창**에서 선택한 행의 정렬 조건을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-164">Removes sort criteria, if applicable, for the selected row in the **Grid pane**.</span></span><br /><br /> <span data-ttu-id="812af-165">참고: 이 옵션은 **VDT 쿼리 작성기로 전환** 을 선택할 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-165">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="812af-166">**Group By 사용**</span><span class="sxs-lookup"><span data-stu-id="812af-166">**Use Group By**</span></span>|<span data-ttu-id="812af-167">쿼리에 그룹화 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-167">Adds grouping functionality to the query.</span></span><br /><br /> <span data-ttu-id="812af-168">참고: 이 옵션은 **VDT 쿼리 작성기로 전환** 을 선택할 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-168">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="812af-169">**테이블 추가**</span><span class="sxs-lookup"><span data-stu-id="812af-169">**Add Table**</span></span>|<span data-ttu-id="812af-170">새 테이블 또는 뷰를 쿼리에 추가할 수 있는 **테이블 추가** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-170">Displays the **Add Table** dialog box to add a new table or view to the query.</span></span> <span data-ttu-id="812af-171">**테이블 추가** 대화 상자에 대한 자세한 내용은 [테이블 추가 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](add-table-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="812af-171">For more information about the **Add Table** dialog box, see [Add Table Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](add-table-dialog-box-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="812af-172">참고: 이 옵션은 **VDT 쿼리 작성기로 전환** 을 선택할 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-172">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
  
 <span data-ttu-id="812af-173">**다이어그램 창**</span><span class="sxs-lookup"><span data-stu-id="812af-173">**Diagram pane**</span></span>  
 <span data-ttu-id="812af-174">쿼리에서 참조하는 개체를 다이어그램으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-174">Displays the objects referenced by the query as a diagram.</span></span> <span data-ttu-id="812af-175">다이어그램은 쿼리에 포함된 테이블과 이러한 테이블의 조인 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="812af-175">The diagram shows the tables included in the query, and how they are joined.</span></span> <span data-ttu-id="812af-176">쿼리 출력에 열을 추가하거나 제거하려면 테이블에서 해당 열의 옆에 있는 확인란을 선택하거나 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-176">Select or clear the check box next to a column in a table to add or remove it from the query output.</span></span>  
  
 <span data-ttu-id="812af-177">쿼리에 테이블을 추가하면 대화 상자에서 테이블의 키를 기반으로 테이블 간의 조인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="812af-177">When you add tables to the query, the dialog box creates joins between tables based on the keys in the table.</span></span> <span data-ttu-id="812af-178">조인을 추가하려면 한 테이블의 필드를 다른 테이블의 필드로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="812af-178">To add a join, drag a field from one table onto a field in another table.</span></span> <span data-ttu-id="812af-179">조인을 관리하려면 해당 연결을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-179">To manage a join, right-click the join.</span></span>  
  
 <span data-ttu-id="812af-180">**다이어그램 창** 을 마우스 오른쪽 단추로 클릭하여 테이블을 추가 또는 제거하고, 모든 테이블을 선택하고, 창을 표시하거나 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="812af-180">Right-click the **Diagram pane** to add or remove tables, select all the tables, and show or hide panes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="812af-181">**다이어그램 창**, **표 형태 창**및 **SQL 창** 의 내용이 동기화되므로 하나의 창에서 변경된 내용은 나머지 두 창에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-181">The contents of the **Diagram pane**, **Grid pane**, and **SQL pane** are synchronized, so that changes in one pane are reflected in the other two panes.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="812af-182">대화 상자에서는 쿼리 유형을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="812af-182">Changing query types is not supported by the dialog box.</span></span>  
  
 <span data-ttu-id="812af-183">**표 형태 창**</span><span class="sxs-lookup"><span data-stu-id="812af-183">**Grid pane**</span></span>  
 <span data-ttu-id="812af-184">쿼리에서 참조하는 개체를 표에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-184">Displays the objects referenced by the query in a grid.</span></span> <span data-ttu-id="812af-185">이 창을 사용하여 쿼리에 열을 추가하거나 제거하고 각 열의 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="812af-185">You can use this pane to add and remove columns to the query and change the settings for each column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="812af-186">**다이어그램 창**, **표 형태 창**및 **SQL 창** 의 내용이 동기화되므로 하나의 창에서 변경된 내용은 나머지 두 창에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-186">The contents of the **Diagram pane**, **Grid pane**, and **SQL pane** are synchronized, so that changes in one pane are reflected in the other two panes.</span></span>  
  
 <span data-ttu-id="812af-187">**SQL 창**</span><span class="sxs-lookup"><span data-stu-id="812af-187">**SQL pane**</span></span>  
 <span data-ttu-id="812af-188">쿼리를 SQL 문으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-188">Displays the query as a SQL statement.</span></span> <span data-ttu-id="812af-189">쿼리용 SQL 문을 변경하려면 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-189">Type to change the SQL statement for the query.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="812af-190">**다이어그램 창**, **표 형태 창**및 **SQL 창** 의 내용이 동기화되므로 하나의 창에서 변경된 내용은 나머지 두 창에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="812af-190">The contents of the **Diagram pane**, **Grid pane**, and **SQL pane** are synchronized, so that changes in one pane are reflected in the other two panes.</span></span>  
  
 <span data-ttu-id="812af-191">**결과 창**</span><span class="sxs-lookup"><span data-stu-id="812af-191">**Result pane**</span></span>  
 <span data-ttu-id="812af-192">**도구 모음** 창에서 **실행** 을 클릭하면 쿼리 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="812af-192">Displays the results of the query when you click **Run** on the **Toolbar** pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="812af-193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="812af-193">See Also</span></span>  
 <span data-ttu-id="812af-194">[Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="812af-194">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="812af-195">데이터 원본 뷰에서 명명된 쿼리 정의&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="812af-195">Define Named Queries in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-named-queries-in-a-data-source-view-analysis-services.md)  
  
  
