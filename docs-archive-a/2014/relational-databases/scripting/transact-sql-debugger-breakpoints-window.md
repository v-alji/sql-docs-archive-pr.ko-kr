---
title: 중단점 창
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Breakpoints Window [Transact-SQL]
ms.assetid: bad88d10-fdd5-4d3d-b5ea-a4f063847485
author: rothja
ms.author: jroth
ms.openlocfilehash: 077d501e581ed5baaac45cc6bbbb34e0040730e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653790"
---
# <a name="breakpoints-window"></a><span data-ttu-id="a017a-102">중단점 창</span><span class="sxs-lookup"><span data-stu-id="a017a-102">Breakpoints Window</span></span>
  <span data-ttu-id="a017a-103">**중단점** 창에서는 현재 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기에 설정된 모든 중단점을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-103">The **Breakpoints** window lists all the breakpoints that are set in the current [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="a017a-104">중단점을 관리하려면 **중단점** 창의 도구 모음을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-104">To manage the breakpoints, use the toolbar in the **Breakpoints** window.</span></span> <span data-ttu-id="a017a-105">여기서 중단점은 디버깅 데이터를 볼 수 있도록 디버그 모드에서 실행을 일시 중지하는 코드의 특정 위치를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-105">Breakpoints are locations in the code where execution pauses in debug mode so that you can view debugging data.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="a017a-106">작업 목록</span><span class="sxs-lookup"><span data-stu-id="a017a-106">Task List</span></span>  
 <span data-ttu-id="a017a-107">**중단점 창에 액세스하려면**</span><span class="sxs-lookup"><span data-stu-id="a017a-107">**To access the Breakpoints window**</span></span>  
  
-   <span data-ttu-id="a017a-108">**디버그** 메뉴에서 **창**을 클릭한 다음 **중단점**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-108">On the **Debug** menu, click **Windows**, and then click **Breakpoints**.</span></span>  
  
## <a name="breakpoints-window-columns"></a><span data-ttu-id="a017a-109">중단점 창 열</span><span class="sxs-lookup"><span data-stu-id="a017a-109">Breakpoints Window Columns</span></span>  
 <span data-ttu-id="a017a-110">기본적으로 **중단점** 창에는 다음과 같은 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-110">By default, the **Breakpoints** window lists the following columns.</span></span>  
  
 <span data-ttu-id="a017a-111">**이름**</span><span class="sxs-lookup"><span data-stu-id="a017a-111">**Name**</span></span>  
 <span data-ttu-id="a017a-112">중단점의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-112">Displays the name of the breakpoint.</span></span> <span data-ttu-id="a017a-113">중단점 이름은 디버거에서 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-113">Breakpoint names are provided by the debugger.</span></span> <span data-ttu-id="a017a-114">이 이름에는 중단점을 포함하는 데이터베이스 엔진 쿼리 편집기 창의 이름과 중단점이 설정된 쿼리 편집기의 줄 번호가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-114">This name includes the name of Database Engine Query Editor window that contains the breakpoint, and the line number in the Query Editor on which the breakpoint is set.</span></span>  
  
 <span data-ttu-id="a017a-115">**Condition**</span><span class="sxs-lookup"><span data-stu-id="a017a-115">**Condition**</span></span>  
 <span data-ttu-id="a017a-116">**(조건 없음)** 을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-116">Displays **(no condition)**.</span></span> <span data-ttu-id="a017a-117">[!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거는 중단점 조건 설정을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-117">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support setting breakpoint conditions.</span></span>  
  
 <span data-ttu-id="a017a-118">**적중 횟수**</span><span class="sxs-lookup"><span data-stu-id="a017a-118">**Hit Count**</span></span>  
 <span data-ttu-id="a017a-119">**항상 중단**을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-119">Displays**breaks always**.</span></span>  
  
 <span data-ttu-id="a017a-120">**열** 목록에서 다음 열을 선택하여 해당 열을 추가하거나 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-120">You can add and remove the following columns by selecting them on the **Columns** list.</span></span>  
  
 <span data-ttu-id="a017a-121">**Filter**</span><span class="sxs-lookup"><span data-stu-id="a017a-121">**Filter**</span></span>  
 <span data-ttu-id="a017a-122">**(없음)** 을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-122">Displays **(none)**.</span></span> <span data-ttu-id="a017a-123">[!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거는 중단점 필터 설정을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-123">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support setting breakpoint filters.</span></span>  
  
 <span data-ttu-id="a017a-124">**적중될 때**</span><span class="sxs-lookup"><span data-stu-id="a017a-124">**When Hit**</span></span>  
 <span data-ttu-id="a017a-125">**중단**을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-125">Displays **Break**.</span></span>  
  
 <span data-ttu-id="a017a-126">**언어**</span><span class="sxs-lookup"><span data-stu-id="a017a-126">**Language**</span></span>  
 <span data-ttu-id="a017a-127">**의 경우** Transact-SQL [!INCLUDE[tsql](../../includes/tsql-md.md)]을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-127">Displays **Transact-SQL** for [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a017a-128">**Function**</span><span class="sxs-lookup"><span data-stu-id="a017a-128">**Function**</span></span>  
 <span data-ttu-id="a017a-129">중단점이 설정된 줄의 번호를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-129">Displays the number of the line on which the breakpoint is set.</span></span>  
  
 <span data-ttu-id="a017a-130">**최근에 사용한 파일**</span><span class="sxs-lookup"><span data-stu-id="a017a-130">**File**</span></span>  
 <span data-ttu-id="a017a-131">중단점을 포함하는 원본 파일 이름과 중단점이 설정된 줄의 번호를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-131">Displays the name of the source file that contains the breakpoint, and the number of the line on which the breakpoint is set.</span></span>  
  
 <span data-ttu-id="a017a-132">**주소**</span><span class="sxs-lookup"><span data-stu-id="a017a-132">**Address**</span></span>  
 <span data-ttu-id="a017a-133">[!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거는 이 기능을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-133">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support this feature.</span></span>  
  
 <span data-ttu-id="a017a-134">**처리**</span><span class="sxs-lookup"><span data-stu-id="a017a-134">**Process**</span></span>  
 <span data-ttu-id="a017a-135">**[SQL]** 을 표시하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 프로세스임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-135">Displays **[SQL]** to indicate that this is a [!INCLUDE[ssDE](../../includes/ssde-md.md)] process.</span></span> <span data-ttu-id="a017a-136">코드를 실행하는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스 이름 뒤에 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-136">This is followed by the name of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in which the code executes.</span></span>  
  
## <a name="breakpoints-window-toolbar"></a><span data-ttu-id="a017a-137">중단점 창 도구 모음</span><span class="sxs-lookup"><span data-stu-id="a017a-137">Breakpoints Window Toolbar</span></span>  
 <span data-ttu-id="a017a-138">현재 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기 창에 활성 상태의 중단점이 있으면 중단점을 관리하는 데 사용할 수 있는 도구 모음이 **중단점** 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-138">When the current [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window has active breakpoints, the **Breakpoints** window displays a toolbar that can be used to manage the breakpoints.</span></span>  
  
 <span data-ttu-id="a017a-139">**Delete**</span><span class="sxs-lookup"><span data-stu-id="a017a-139">**Delete**</span></span>  
 <span data-ttu-id="a017a-140">선택한 중단점을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-140">Deletes the selected breakpoint.</span></span>  
  
 <span data-ttu-id="a017a-141">**모든 중단점 삭제**</span><span class="sxs-lookup"><span data-stu-id="a017a-141">**Delete All Breakpoints**</span></span>  
 <span data-ttu-id="a017a-142">**중단점** 창에 표시된 모든 중단점을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-142">Deletes all breakpoints that are displayed in the **Breakpoints** window.</span></span>  
  
 <span data-ttu-id="a017a-143">**모든 중단점 해제**</span><span class="sxs-lookup"><span data-stu-id="a017a-143">**Disable All Breakpoints**</span></span>  
 <span data-ttu-id="a017a-144">더 이상 코드 실행을 중지하지 않도록 모든 중단점을 해제하지만 중단점은 그대로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-144">Disables all breakpoints so that they no longer stop code execution; however, the breakpoints remain.</span></span> <span data-ttu-id="a017a-145">모든 중단점을 해제하면 **모든 중단점 설정**단추로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-145">When all the breakpoints are disabled, this button becomes **Enable All Breakpoints**.</span></span>  
  
 <span data-ttu-id="a017a-146">**모든 중단점 설정**</span><span class="sxs-lookup"><span data-stu-id="a017a-146">**Enable All Breakpoints**</span></span>  
 <span data-ttu-id="a017a-147">코드 실행을 중지하도록 모든 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-147">Enables all breakpoints so that they stop code execution.</span></span> <span data-ttu-id="a017a-148">모든 중단점이 설정되면 **모든 중단점 해제**단추로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-148">When all breakpoints are enabled, this button becomes **Disable All Breakpoints**.</span></span>  
  
 <span data-ttu-id="a017a-149">**소스 코드로 이동**</span><span class="sxs-lookup"><span data-stu-id="a017a-149">**Go To Source Code**</span></span>  
 <span data-ttu-id="a017a-150">쿼리 편집기에서 선택한 중단점을 포함하는 줄에 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-150">Positions the cursor on the line in the Query Editor that contains the selected breakpoint.</span></span>  
  
 <span data-ttu-id="a017a-151">**열**</span><span class="sxs-lookup"><span data-stu-id="a017a-151">**Columns**</span></span>  
 <span data-ttu-id="a017a-152">**중단점** 창에 표시할 수 있는 모든 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-152">Lists all the columns that can be displayed in the **Breakpoints** window.</span></span> <span data-ttu-id="a017a-153">확인란은 표시된 열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-153">A check box indicates the columns that are displayed.</span></span> <span data-ttu-id="a017a-154">**중단점** 창에서 열을 추가하거나 제거하려면 목록에서 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a017a-154">To add or remove a column in the **Breakpoints** window, select the column on the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a017a-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a017a-155">See Also</span></span>  
 [<span data-ttu-id="a017a-156">Transact-SQL 디버거</span><span class="sxs-lookup"><span data-stu-id="a017a-156">Transact-SQL Debugger</span></span>](transact-sql-debugger.md)  
