---
title: 개체 탐색기 세부 정보 창 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.summary.report.f1
- sql12.swb.summary.general.f1
helpviewer_keywords:
- object search [SQL Server], Object Explorer
- Object Explorer
- object search [SQL Server]
- searching objects [SQL Server]
ms.assetid: b963e3c2-dc9e-4d38-bd28-2e00fe9e0e47
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0ec856ce01930683cf20683a418a658a5b877729
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741535"
---
# <a name="object-explorer-details-pane"></a><span data-ttu-id="f668c-102">개체 탐색기 세부 정보 창</span><span class="sxs-lookup"><span data-stu-id="f668c-102">Object Explorer Details Pane</span></span>
  <span data-ttu-id="f668c-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 구성 요소인 개체 탐색기 정보는 서버의 모든 개체를 테이블 형식으로 표시하고 이러한 개체를 관리하기 위한 사용자 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-103">Object Explorer Details, a component of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], provides a tabular view of all the objects in the server and presents a user interface to manage them.</span></span> <span data-ttu-id="f668c-104">개체 탐색기의 기능은 서버의 유형에 따라 조금씩 다르지만 일반적으로 데이터베이스를 위한 개발 기능과 모든 서버 유형을 위한 관리 기능을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-104">The capabilities of Object Explorer vary slightly depending on the type of server, but generally include the development features for databases and management features for all server types.</span></span>  
  
 <span data-ttu-id="f668c-105">개체 탐색기 정보 창은 기본적으로 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-105">The Object Explorer Details pane is visible in the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] by default.</span></span> <span data-ttu-id="f668c-106">개체 탐색기가 표시되지 않으면 **보기** 메뉴에서 **개체 탐색기 정보** 를 클릭하거나 **F7**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-106">If you cannot see Object Explorer, on the **View** menu, click **Object Explorer Details** or press **F7**.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]<span data-ttu-id="f668c-107">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 가 시작될 때 사용되는 Microsoft Windows 국가 및 언어 옵션의 날짜 형식에 따라 날짜를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-107">presents dates formatted with the Microsoft Windows Regional and Language Options in effect when [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] was started.</span></span> <span data-ttu-id="f668c-108">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 다시 시작하면 새 설정이 반영됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-108">Restart [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to reflect newer settings.</span></span>  
  
## <a name="object-explorer-details"></a><span data-ttu-id="f668c-109">개체 탐색기 정보</span><span class="sxs-lookup"><span data-stu-id="f668c-109">Object Explorer Details</span></span>  
 <span data-ttu-id="f668c-110">개체 탐색기 정보를 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 폴더 및 개체를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-110">Object Explorer Details can be used to navigate through folders and objects on your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="f668c-111">32비트 운영 체제에서는 개체 탐색기가 64,000개의 개체만 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-111">On 32-bit operating systems, Object Explorer can only display 64,000 objects.</span></span> <span data-ttu-id="f668c-112">추가 개체에 액세스하려면 아이콘을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-112">An icon must be selected to access additional objects.</span></span>  
  
 <span data-ttu-id="f668c-113">개체 탐색기 정보에는 다음 표에 설명된 아이콘이 있는 도구 모음이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-113">Object Explorer Details includes a toolbar which contains the icons described in the following table.</span></span> <span data-ttu-id="f668c-114">아이콘은 해당되는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-114">Icons are only available when appropriate.</span></span>  
  
|<span data-ttu-id="f668c-115">아이콘</span><span class="sxs-lookup"><span data-stu-id="f668c-115">Icon</span></span>|<span data-ttu-id="f668c-116">작업</span><span class="sxs-lookup"><span data-stu-id="f668c-116">Action</span></span>|  
|----------|------------|  
|<span data-ttu-id="f668c-117">**뒤로**</span><span class="sxs-lookup"><span data-stu-id="f668c-117">**Back**</span></span>|<span data-ttu-id="f668c-118">개체 탐색기 정보에 표시된 이전 항목으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-118">Moves to the previous items displayed in Object Explorer Details.</span></span> <span data-ttu-id="f668c-119">이전 화면이 검색 작업으로 인한 결과 화면인 경우 검색을 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-119">Re-runs a search when the previous display is the result of a search operation.</span></span>|  
|<span data-ttu-id="f668c-120">**앞으로**</span><span class="sxs-lookup"><span data-stu-id="f668c-120">**Forward**</span></span>|<span data-ttu-id="f668c-121">**뒤로** 작업을 선택한 후 다음 화면으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-121">Moves to the next screen after a **Back** operation is selected.</span></span>|  
|<span data-ttu-id="f668c-122">**위로**</span><span class="sxs-lookup"><span data-stu-id="f668c-122">**Up**</span></span>|<span data-ttu-id="f668c-123">부모 개체 또는 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-123">Moves to the parent object or folder.</span></span>|  
|<span data-ttu-id="f668c-124">**동기화**</span><span class="sxs-lookup"><span data-stu-id="f668c-124">**Synchronize**</span></span>|<span data-ttu-id="f668c-125">개체 탐색기의 포커스를 개체 탐색기 정보에서 선택한 개체로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-125">Sets the focus of Object Explorer to the selected object in Object Explorer Details.</span></span>|  
|<span data-ttu-id="f668c-126">**Filter**</span><span class="sxs-lookup"><span data-stu-id="f668c-126">**Filter**</span></span>|<span data-ttu-id="f668c-127">사용 가능한 경우 구성 가능한 개체 하위 집합을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-127">When available, shows a configurable subset of objects.</span></span>|  
|<span data-ttu-id="f668c-128">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="f668c-128">**Refresh**</span></span>|<span data-ttu-id="f668c-129">개체 탐색기 정보의 화면 표시를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-129">Refreshes the display in Object Explorer Details.</span></span>|  
|<span data-ttu-id="f668c-130">**검색**</span><span class="sxs-lookup"><span data-stu-id="f668c-130">**Search**</span></span>|<span data-ttu-id="f668c-131">특정 데이터베이스 개체를 찾기 위한 검색 단어를 입력할 영역을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-131">Provides an area to enter a search term for certain database objects.</span></span>|  
  
### <a name="column-header-selections"></a><span data-ttu-id="f668c-132">열 머리글 선택</span><span class="sxs-lookup"><span data-stu-id="f668c-132">Column Header Selections</span></span>  
 <span data-ttu-id="f668c-133">개체 탐색기 정보에는 선택할 수 있는 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-133">Object Explorer Details has selectable columns.</span></span> <span data-ttu-id="f668c-134">열 머리글을 마우스 오른쪽 단추로 클릭하고 표시할 항목을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-134">You can right-click in any column header and check the items that you want to display.</span></span> <span data-ttu-id="f668c-135">선택한 항목은 다른 개체를 탐색할 때도 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-135">Your selections will be persisted across the different objects you navigate through.</span></span> <span data-ttu-id="f668c-136">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 닫고 다시 시작해도 각 사용자가 선택한 설정이 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-136">Selections for each user are retained when you leave and restart [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="f668c-137">데이터베이스와 같은 일부 개체 유형에 대한 열을 모두 표시하면 큰 개체 집합에 대한 표시 렌더링이 약간 느려질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-137">Showing all columns for some object types (such as Databases) might slow the display rendering slightly for large sets of objects.</span></span>  
  
### <a name="sorting"></a><span data-ttu-id="f668c-138">정렬</span><span class="sxs-lookup"><span data-stu-id="f668c-138">Sorting</span></span>  
 <span data-ttu-id="f668c-139">열 머리글을 한 번 클릭하면 해당 열을 기준으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-139">Clicking one time on a column header will sort by that column.</span></span> <span data-ttu-id="f668c-140">동일한 머리글을 다시 클릭하면 해당 열을 기준으로 역순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-140">Clicking again on the same header reverse-sorts by that column.</span></span> <span data-ttu-id="f668c-141">각 사용자가 선택한 정렬 설정은 다른 개체 및 폴더에서도 그대로 유지되며 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 다시 시작해도 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-141">Sort selections are maintained for each user across objects and folders, and on [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] restart.</span></span>  
  
### <a name="filtering"></a><span data-ttu-id="f668c-142">Filtering</span><span class="sxs-lookup"><span data-stu-id="f668c-142">Filtering</span></span>  
 <span data-ttu-id="f668c-143">개체 탐색기 정보에 표시되는 특정 개체 목록은 개체 탐색기 정보 도구 모음의 **필터** 아이콘을 사용하여 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-143">Certain lists of objects displayed in Object Explorer Detail can be filtered using the **Filter** icon on the Object Explorer Details toolbar.</span></span> <span data-ttu-id="f668c-144">필터링이 가능하면 아이콘이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-144">The icon will be enabled when filtering is possible.</span></span>  
  
### <a name="details-pane"></a><span data-ttu-id="f668c-145">정보 창</span><span class="sxs-lookup"><span data-stu-id="f668c-145">Details Pane</span></span>  
 <span data-ttu-id="f668c-146">개체 탐색기 정보의 맨 아래 영역에는 선택한 개체에 대한 특정 정보가 표시되는 패널이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-146">The very bottom area of Object Explorer Details contains a panel that displays certain details of the selected object.</span></span> <span data-ttu-id="f668c-147">여러 개체를 선택한 경우 개체 수만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-147">Multiple object selections show only the count of the objects.</span></span> <span data-ttu-id="f668c-148">패널에서 항목을 선택하고 **복사** 아이콘을 클릭하면 표시된 텍스트가 클립보드에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-148">When items are selected in the panel, click the **Copy** icon to copy the displayed text to the clipboard.</span></span>  
  
 <span data-ttu-id="f668c-149">아래쪽 화살표 키를 누르면 목록에서 다음 항목이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-149">The down arrow key moves the selection to the next item in the list.</span></span> <span data-ttu-id="f668c-150">위쪽 화살표 키를 누르면 목록에서 이전 항목이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-150">The up arrow key moves the selection to the previous item in the list.</span></span> <span data-ttu-id="f668c-151">화살표 키를 누르고 있으면 항목 간 이동 속도가 빨라집니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-151">Holding the arrow key down will speed through the items.</span></span> <span data-ttu-id="f668c-152">속성 목록의 맨 아래 또는 맨 위 항목에서 선택이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-152">The selection stops at the bottom or top of the property list.</span></span>  
  
 <span data-ttu-id="f668c-153">속성 이름의 첫 번째 문자를 입력하면 해당 문자로 시작하는 다음 속성이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-153">Typing the first character of a property name moves the selection to the next property that begins with that character.</span></span>  
  
 <span data-ttu-id="f668c-154">속성이 여러 열에 정렬되어 있는 경우 왼쪽 화살표 및 오른쪽 화살표 키를 사용하여 인접 열로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-154">When properties are arranged in multiple columns, use the left arrow and right arrow keys to move to adjacent columns.</span></span>  
  
 <span data-ttu-id="f668c-155">속성 값을 클립보드로 복사하려면 다음과 같은 키보드 키 조합을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-155">To copy property values to the clipboard, use the following keyboard key combinations:</span></span>  
  
-   <span data-ttu-id="f668c-156">Ctrl+C는 속성 값을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-156">Ctrl+C copies the property value.</span></span>  
  
-   <span data-ttu-id="f668c-157">Ctrl+Shift+C는 탭 구분 기호를 사용하여 속성 이름과 속성 값을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-157">Ctrl+Shift+C copies the property name and the property value with a tab delimiter.</span></span>  
  
 <span data-ttu-id="f668c-158">개체 탐색기 정보 속성 창에서 오른쪽 클릭 메뉴를 사용하여 모든 속성 또는 모든 속성과 이름을 클립보드로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-158">Use the right-click menu in the Object Explorer Details property pane to copy all properties or all properties and names to the clipboard.</span></span>  
  
 <span data-ttu-id="f668c-159">필드 너비가 좁아서 속성 값을 완전히 표시할 수 없을 때 속성 값을 표시하려면 마우스 커서를 값 위에 놓거나 속성 값에 UI 포커스를 설정하여 전체 속성 값이 들어 있는 도구 설명을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-159">To display a property value when the field width does not completely display a property value, hover the mouse cursor over the value or set UI focus on the property value to activate a tool tip with the entire property value.</span></span> <span data-ttu-id="f668c-160">긴 속성 값에 포커스가 있으면 내게 필요한 옵션 화면 판독기가 전체 속성 값을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-160">Accessibility screen readers will report the full property value when the user focuses on the long property value.</span></span>  
  
 <span data-ttu-id="f668c-161">속성 창의 속성 수가 콘텐츠 영역에 표시될 수 있는 수보다 많으면 속성 창의 오른쪽에 스크롤 막대가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-161">If the number of properties in the property pane exceeds that which will fit in the content area, a scroll bar will appear on the right side of the property pane.</span></span> <span data-ttu-id="f668c-162">스크롤 막대를 사용하여 콘텐츠 영역의 속성 값 뷰를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-162">Use the scroll bar to adjust the view of property values in the content area.</span></span>  
  
### <a name="multiple-object-selection"></a><span data-ttu-id="f668c-163">여러 개체 선택</span><span class="sxs-lookup"><span data-stu-id="f668c-163">Multiple Object Selection</span></span>  
 <span data-ttu-id="f668c-164">개체 탐색기 정보에서는 여러 개체를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-164">Object Explorer Details supports multiple object selection.</span></span> <span data-ttu-id="f668c-165">예를 들어 개체 탐색기에서 테이블을 선택하는 경우 개체 탐색기 정보 창에서 **Ctrl** 키를 누른 채 여러 테이블을 선택하고 마우스 오른쪽 단추를 클릭한 다음 **삭제** 또는 **테이블 스크립팅** 을 선택하여 선택한 모든 테이블에 대해 동시에 동작을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-165">For example, if you select Tables in Object Explorer, then in the Object Explorer Details window if you hold down the **Ctrl** key, you can select several tables, right-click them, and then select **Delete** or **Script Table AS** to act on all the selected tables immediately.</span></span> <span data-ttu-id="f668c-166">표준 복사 명령은 표시된 텍스트를 클립보드에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-166">The standard copy commands will copy the displayed text to the clipboard.</span></span>  
  
## <a name="sql-server-object-search"></a><span data-ttu-id="f668c-167">SQL Server 개체 검색</span><span class="sxs-lookup"><span data-stu-id="f668c-167">SQL Server Object Search</span></span>  
 <span data-ttu-id="f668c-168">와일드카드</span><span class="sxs-lookup"><span data-stu-id="f668c-168">Wildcards</span></span>  
  
-   <span data-ttu-id="f668c-169">표준 와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-169">Standard wildcard characters are supported.</span></span> <span data-ttu-id="f668c-170">예를 들어 **dm_os%counters** 를 검색하면 dm_os_memory_cache_counters와 dm_os_performance_counters가 모두 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-170">For example, searching for **dm_os%counters** returns both dm_os_memory_cache_counters and dm_os_performance_counters.</span></span> <span data-ttu-id="f668c-171">자세한 내용은 [와일드 카드를 사용 하 여 텍스트 검색](../../relational-databases/scripting/search-text-with-wildcards.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f668c-171">For more information, see [Search Text with Wildcards](../../relational-databases/scripting/search-text-with-wildcards.md).</span></span>  
  
 <span data-ttu-id="f668c-172">검색 범위</span><span class="sxs-lookup"><span data-stu-id="f668c-172">Search Scope</span></span>  
  
-   <span data-ttu-id="f668c-173">각 검색의 범위는 개체 탐색기 트리의 현재 포커스로 한정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-173">Each search is scoped to the current focus in the Object Explorer tree.</span></span> <span data-ttu-id="f668c-174">예를 들어 데이터베이스에 개체 탐색기 포커스가 있는 경우 **dm_os%counters** 를 검색하면 해당 데이터베이스에서 dm_os_memory_cache_counters와 dm_os_performance_counters가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-174">For example, if the Object Explorer focus is on a database, search for **dm_os%counters** returns dm_os_memory_cache_counters and dm_os_performance_counters in that database.</span></span> <span data-ttu-id="f668c-175">데이터베이스 노드에 개체 탐색기 포커스가 있는 경우 모든 데이터베이스가 검색되어 동적 뷰의 여러 인스턴스가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-175">If the Object Explorer focus is on the Databases node, all databases are searched and multiple instances of the dynamic views are returned.</span></span>  
  
 <span data-ttu-id="f668c-176">큰 집합</span><span class="sxs-lookup"><span data-stu-id="f668c-176">Large Sets</span></span>  
  
-   <span data-ttu-id="f668c-177">큰 개체 집합을 검색하면 시간이 많이 걸리고 서버 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f668c-177">Searching large object sets can take a long time and slow server performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f668c-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f668c-178">See Also</span></span>  
 [<span data-ttu-id="f668c-179">개체 탐색기</span><span class="sxs-lookup"><span data-stu-id="f668c-179">Object Explorer</span></span>](object-explorer.md)  
  
  
