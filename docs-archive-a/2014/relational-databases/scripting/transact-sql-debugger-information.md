---
title: Transact-SQL 디버거 정보
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, Locals Window
- Transact-SQL debugger, Watch Window
- Transact-SQL debugger, Threads Window
- Transact-SQL debugger, Call Stack Window
- Transact-SQL debugger, QuickWatch
- Transact-SQL debugger, viewing information
ms.assetid: b99819cc-f388-41a1-b304-36e78ce24147
author: rothja
ms.author: jroth
ms.openlocfilehash: c51ed39f0ed5f4ffb3e1a0c0dcb307f82d10bb10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741756"
---
# <a name="transact-sql-debugger-information"></a><span data-ttu-id="7d2e3-102">Transact-SQL 디버거 정보</span><span class="sxs-lookup"><span data-stu-id="7d2e3-102">Transact-SQL Debugger Information</span></span>
  <span data-ttu-id="7d2e3-103">디버거가 특정 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 실행을 일시 중지할 때마다 여러 디버거 창을 사용하여 현재 실행 상태를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-103">Every time that the debugger pauses execution on a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, you can use the various debugger windows to view the current execution state.</span></span>  
  
## <a name="debugger-windows"></a><span data-ttu-id="7d2e3-104">디버거 창</span><span class="sxs-lookup"><span data-stu-id="7d2e3-104">Debugger Windows</span></span>  
 <span data-ttu-id="7d2e3-105">디버거 모드에서 디버거가 주 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 창 아래쪽에 두 개의 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-105">In debugger mode, the debugger opens two windows at the bottom of the main [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] window.</span></span> <span data-ttu-id="7d2e3-106">디버거는 이 두 창에 해당 정보를 모두 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-106">The debugger displays all its information in these two windows.</span></span> <span data-ttu-id="7d2e3-107">각 디버거 창에는 창에 표시되는 정보 집합을 제어하기 위해 선택할 수 있는 탭이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-107">Each of the debugger windows has tabs that you can select to control which set of information is displayed in the window.</span></span> <span data-ttu-id="7d2e3-108">왼쪽 디버거 창에는 **지역**, **조사식1**, **조사식2**, **조사식3**및 **조사식4** 탭이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-108">The left debugger window contains the **Locals**, **Watch1**, **Watch2**, **Watch3**, and **Watch4** tabs.</span></span> <span data-ttu-id="7d2e3-109">오른쪽 디버거 창에는 **호출 스택**, **스레드**, **중단점**, **명령 창**및 **출력** 탭이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-109">The right debugger window contains the **Call Stack**, **Threads**, **Breakpoints**, **Command Window**, and **Output** tabs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7d2e3-110">앞의 설명은 디버거 창의 기본 위치에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-110">The previous descriptions apply to the default locations of the debugger windows.</span></span> <span data-ttu-id="7d2e3-111">탭을 끌어 창 사이를 이동하거나 탭의 도킹을 해제하여 원하는 위치에 배치할 수 있는 새 창을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-111">You can drag a tab to move it from one window to another, or you can undock a tab to create a new window that you can put wherever you want.</span></span>  
  
 <span data-ttu-id="7d2e3-112">이러한 탭 또는 창의 일부는 기본적으로 활성화되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-112">By default, not all of these tabs or windows are active.</span></span> <span data-ttu-id="7d2e3-113">다음 방법 중 하나를 수행하여 특정 창을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-113">You can open a particular window by using either of the following ways:</span></span>  
  
-   <span data-ttu-id="7d2e3-114">**디버그** 메뉴에서 **창**을 클릭한 다음 원하는 창을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-114">On the **Debug** menu, click **Windows**, and then select the window you want.</span></span>  
  
-   <span data-ttu-id="7d2e3-115">**디버그** 도구 모음에서 **중단점**을 클릭한 다음 원하는 창을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-115">On the **Debug** toolbar, click **Breakpoints**, and then select the window you want.</span></span>  
  
## <a name="transact-sql-expressions"></a><span data-ttu-id="7d2e3-116">Transact-SQL 식</span><span class="sxs-lookup"><span data-stu-id="7d2e3-116">Transact-SQL Expressions</span></span>  
 <span data-ttu-id="7d2e3-117">식은 변수 또는 매개 변수와 같은 단일 스칼라 값으로 계산되는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 절입니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-117">Expressions are [!INCLUDE[tsql](../../includes/tsql-md.md)] clauses that evaluate to a single, scalar value, such as variables or parameters.</span></span> <span data-ttu-id="7d2e3-118">왼쪽 디버거 창에서는 식에 현재 할당된 데이터 값을 최대 5개의 탭 또는 창인 **로컬, 조사식1**, **조사식2**, **조사식3**및 **조사식4**에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-118">The left debugger window can display the data values that are currently assigned to expressions in up to five tabs or windows: **Locals, Watch1**, **Watch2**, **Watch3**, and **Watch4**.</span></span>  
  
 <span data-ttu-id="7d2e3-119">**지역** 창에는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거의 현재 범위에 있는 지역 변수에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-119">The **Locals** window displays information about the local variables in the current scope of the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span> <span data-ttu-id="7d2e3-120">**지역** 창에 나열된 식 집합은 디버거가 코드의 서로 다른 부분에서 실행할 때 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-120">The set of expressions that are listed in the **Locals** window changes as the debugger runs through the different parts of the code.</span></span>  
  
 <span data-ttu-id="7d2e3-121">**간략한 조사식** 및 네 개의 **조사식** 창에 있는 식은 변수의 식별자만 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-121">The expressions in the **QuickWatch** and the four **Watch** windows are not limited to just listing the identifier of a variable.</span></span> <span data-ttu-id="7d2e3-122">변수에 숫자를 추가하는 등 단일 값으로 계산되는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 식 또는 단일 값으로 계산되는 SELECT 문을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-122">You can specify a [!INCLUDE[tsql](../../includes/tsql-md.md)] expression that evaluates to a single value, such as adding a number to a variable, or a SELECT statement that evaluates to a single value.</span></span> <span data-ttu-id="7d2e3-123">다음은 이러한 템플릿의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-123">Examples include:</span></span>  
  
-   <span data-ttu-id="7d2e3-124">@IntegerCounter와 같은 변수 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-124">The name of a variable, such as @IntegerCounter.</span></span>  
  
-   <span data-ttu-id="7d2e3-125">@IntegerCounter + 1 등의 변수에 대한 산술 연산입니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-125">An arithmetic operation on a variable, such as @IntegerCounter + 1.</span></span>  
  
-   <span data-ttu-id="7d2e3-126">@FirstName + @LastName과 같은 두 문자 변수에 대한 문자열 연산입니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-126">A string operation on two character variables, such as @FirstName + @LastName.</span></span>  
  
-   <span data-ttu-id="7d2e3-127">SELECT CharCol FROM MyTable WHERE PrimaryKey = 1 등의 단일 값을 반환하는 SELECT 문입니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-127">A SELECT statement that returns a single value, such as SELECT CharCol FROM MyTable WHERE PrimaryKey = 1.</span></span>  
  
 <span data-ttu-id="7d2e3-128">**간략한 조사식** 창을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] 식 값을 본 다음 해당 식을 **조사식** 창에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-128">You can use the **QuickWatch** window to view the value of a [!INCLUDE[tsql](../../includes/tsql-md.md)] expression, and then save that expression to a **Watch** window.</span></span> <span data-ttu-id="7d2e3-129">**간략한 조사식**에서 식을 선택하려면 **식** 상자에서 식 이름을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-129">To select an expression in **QuickWatch**, either select or enter the name of the expression in the **Expression** box.</span></span>  
  
 <span data-ttu-id="7d2e3-130">4개의 **조사식** 창에는 선택한 변수 및 식에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-130">The four **Watch** windows display information about variables and expressions that you have selected.</span></span> <span data-ttu-id="7d2e3-131">**조사식** 창에 나열된 식 집합은 목록에서 식을 추가하거나 삭제할 때까지 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-131">The set of expressions that are listed in the **Watch** windows does not change until you either add or delete expressions from the list.</span></span>  
  
 <span data-ttu-id="7d2e3-132">**조사식** 창에 식을 추가하려면 **간략한 조사식** 대화 상자에서 **조사식 추가** 를 선택하거나 **조사식** 창에서 빈 행의 **이름** 열에 식 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-132">To add an expression to a **Watch** window, you can either select **Add Watch** in the **QuickWatch** dialog box, or enter the name of the expression in the **Name** column of an empty row in a **Watch** window.</span></span>  
  
 <span data-ttu-id="7d2e3-133">행을 마우스 오른쪽 단추로 클릭한 다음 **값 편집**을 선택하여 **지역**, **조사식** 또는 **간략한 조사식**창에서 변수에 대한 데이터 값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-133">You can set the data values for variables in the **Locals**, **Watch**, or **QuickWatch** windows by right-clicking the row and then selecting **Edit Value**.</span></span> <span data-ttu-id="7d2e3-134">**지역** 창, **조사식** 창 및 **간략한 조사식** 대화 상자의 **값** 열은 모두 텍스트, XML 및 HTML 데이터 시각화 도우미를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-134">The **Value** columns in the **Locals** window, **Watch** window, and **QuickWatch** dialog box all support text, XML, and HTML data visualizers.</span></span> <span data-ttu-id="7d2e3-135">시각화 도우미는 **값** 열의 오른쪽 끝에 있는 돋보기 모양의 데이터 팁으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-135">The visualizers are represented by a magnifying glass data tip on the right side end of the **Values** column.</span></span> <span data-ttu-id="7d2e3-136">시각화 도우미를 사용하면 브라우저 창에서 XML 파일을 보는 경우와 같이 데이터 형식과 일치하는 표시 형식으로 텍스트, XML 또는 HTML 데이터 값을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-136">You can use the visualizers to view text, XML, or HTML data values in displays that match the data types, for example, viewing XML files in a browser window.</span></span>  
  
 <span data-ttu-id="7d2e3-137">디버그 모드에서 마우스 포인터를 식별자 위로 이동하면 식 이름 및 식의 현재 값이 포함된 **요약 정보** 팝업 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-137">In debug mode, when you move the mouse pointer over an identifier, a **Quick Info** pop up is displayed with the name of the expression and its current value.</span></span> <span data-ttu-id="7d2e3-138">자세한 내용은 [요약 정보&#40;IntelliSense&#41;](quick-info-intellisense.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-138">For more information, see [Quick Info &#40;IntelliSense&#41;](quick-info-intellisense.md).</span></span>  
  
## <a name="breakpoints"></a><span data-ttu-id="7d2e3-139">중단점</span><span class="sxs-lookup"><span data-stu-id="7d2e3-139">Breakpoints</span></span>  
 <span data-ttu-id="7d2e3-140">**중단점** 창을 사용하여 현재 설정된 중단점을 보고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-140">You can use the **Breakpoints** window to view and manage the currently set breakpoints.</span></span> <span data-ttu-id="7d2e3-141">자세한 내용은 [Transact-SQL 코드 단계별 실행](step-through-transact-sql-code.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-141">For more information, see [Step Through Transact-SQL Code](step-through-transact-sql-code.md).</span></span>  
  
## <a name="call-stacks"></a><span data-ttu-id="7d2e3-142">호출 스택</span><span class="sxs-lookup"><span data-stu-id="7d2e3-142">Call Stacks</span></span>  
 <span data-ttu-id="7d2e3-143">**호출 스택** 창에는 현재 실행 위치와 원래 쿼리 편집기 창에서 전달된 실행이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 모듈(함수, 저장 프로시저 또는 트리거)을 통해 현재 실행 위치에 도달하는 방법에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-143">The **Call Stack** window displays the current execution location, and information about how execution passed from the original editor window through any [!INCLUDE[tsql](../../includes/tsql-md.md)] modules (functions, stored procedures, or triggers) to reach the current execution location.</span></span> <span data-ttu-id="7d2e3-144">**호출 스택** 창의 각 행은 스택 프레임이라고 하며 다음 항목 중 하나를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-144">Each row in the **Call Stack** window is called a stack frame and represents any one of the following items:</span></span>  
  
-   <span data-ttu-id="7d2e3-145">현재 실행 위치</span><span class="sxs-lookup"><span data-stu-id="7d2e3-145">The current execution location.</span></span>  
  
-   <span data-ttu-id="7d2e3-146">한 모듈에서 다른 모듈로의 호출</span><span class="sxs-lookup"><span data-stu-id="7d2e3-146">A call from one module to another.</span></span>  
  
-   <span data-ttu-id="7d2e3-147">편집기 창에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 모듈로의 호출</span><span class="sxs-lookup"><span data-stu-id="7d2e3-147">A call from an editor window to a [!INCLUDE[tsql](../../includes/tsql-md.md)] module.</span></span>  
  
 <span data-ttu-id="7d2e3-148">스택 순서는 모듈이 호출되는 순서와 반대입니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-148">The order of the stack is the reverse of that in which the modules were called.</span></span> <span data-ttu-id="7d2e3-149">현재 실행 위치는 스택의 맨 위이며 원래 호출 위치는 맨 아래입니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-149">The current execution location is at the top of the stack and the original call at the bottom.</span></span> <span data-ttu-id="7d2e3-150">스택 프레임의 왼쪽 여백에 있는 노란색 화살표는 디버거가 실행을 일시 중지한 프레임을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-150">A yellow arrow on the left margin of the stack frame identifies the frame in which the debugger paused execution.</span></span>  
  
 <span data-ttu-id="7d2e3-151">**이름** 열은 다음 정보를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-151">The **Name** column records the following information:</span></span>  
  
-   <span data-ttu-id="7d2e3-152">다음 수준까지 호출한 코드 줄을 포함하는 원본 모듈</span><span class="sxs-lookup"><span data-stu-id="7d2e3-152">The source module that contains the line of code that called down to the next level.</span></span>  
  
-   <span data-ttu-id="7d2e3-153">스택의 다음 모듈을 호출한 코드 줄</span><span class="sxs-lookup"><span data-stu-id="7d2e3-153">The line of code that called the next module on the stack.</span></span>  
  
-   <span data-ttu-id="7d2e3-154">매개 변수를 가져온 저장 프로시저 또는 함수까지 호출한 경우 모든 매개 변수의 이름, 데이터 형식 및 값도 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-154">If the call went to a stored procedure or function that took parameters, the names, data types, and values of all the parameters are also listed.</span></span>  
  
 <span data-ttu-id="7d2e3-155">**지역**, **조사식**및 **간략한 조사식** 창의 식은 현재 스택 프레임에 대해 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-155">The expressions in the **Locals**, **Watch**, and **QuickWatch** windows are evaluated for the current stack frame.</span></span> <span data-ttu-id="7d2e3-156">기본적으로 현재 스택 프레임은 디버거가 실행을 일시 중지한 스택의 맨 위 프레임입니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-156">By default, the current stack frame is the top frame in the stack, where the debugger paused execution.</span></span> <span data-ttu-id="7d2e3-157">다른 스택 프레임을 현재 프레임으로 지정한 경우 **지역**, **조사식**및 **간략한 조사식** 창의 식은 새 스택 프레임에 대해 다시 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-157">When you specify another stack frame as the current frame, the expressions in the **Locals**, **Watch**, and **QuickWatch** windows are reevaluated for the new stack frame.</span></span> <span data-ttu-id="7d2e3-158">프레임을 두 번 클릭하거나 프레임을 클릭하고 **프레임으로 전환**을 선택하여 현재 스택 프레임을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-158">You can change the current stack frame by either by double-clicking a frame or clicking a frame and selecting **Switch To Frame**.</span></span> <span data-ttu-id="7d2e3-159">이 경우 **지역**, **조사식**및 **간략한 조사식** 창의 식은 새 프레임에 대해 다시 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-159">At that point, the expressions in the **Locals**, **Watch**, and **QuickWatch** windows are reevaluated for the new frame.</span></span> <span data-ttu-id="7d2e3-160">현재 스택 프레임이 스택의 맨 위 프레임이 아닌 경우 스택 프레임 왼쪽 여백에 있는 녹색 화살표가 현재 스택 프레임을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-160">Whenever the current stack frame is not the top frame in the stack, a green arrow on the left margin of the stack frame identifies the current stack frame.</span></span>  
  
 <span data-ttu-id="7d2e3-161">스택 프레임을 마우스 오른쪽 단추로 클릭하고 **원본 코드로 이동**을 선택하면 해당 프레임에 대한 코드가 쿼리 편집기 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-161">When you right-click a stack frame and select **Go To Source Code**, the code for that frame is displayed in a Query Editor window.</span></span> <span data-ttu-id="7d2e3-162">그러나 해당 프레임이 현재 프레임으로 생성되지 않고 **지역**, **조사식**및 **간략한 조사식** 창의 내용이 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-162">However, that frame is not made the current frame, and the contents of the **Locals**, **Watch**, and **QuickWatch** windows are not changed.</span></span>  
  
## <a name="system-information-and-transact-sql-results"></a><span data-ttu-id="7d2e3-163">시스템 정보 및 Transact-SQL 결과</span><span class="sxs-lookup"><span data-stu-id="7d2e3-163">System Information and Transact-SQL Results</span></span>  
 <span data-ttu-id="7d2e3-164">디버거는 **출력** 창에 해당 상태 및 이벤트 메시지를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-164">The debugger lists its status and event messages in the **Output** window.</span></span> <span data-ttu-id="7d2e3-165">여기에는 디버거에서 다른 프로세스에 연결하는 경우 또는 디버거 스레드가 종료되는 경우와 같은 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-165">This includes information such as when the debugger attaches to other processes or when debugger threads end.</span></span>  
  
 <span data-ttu-id="7d2e3-166">디버그 모드에서는 **결과** 및 **메시지** 탭이 쿼리 편집기에 계속 활성화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-166">While in debug mode, the **Results** and **Messages** tabs are still active in the Query Editor.</span></span> <span data-ttu-id="7d2e3-167">**결과** 탭은 디버깅 세션 동안 실행되는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문의 결과 집합을 계속 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-167">The **Results** tab continues to display the result sets from the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are executed during a debugging session.</span></span> <span data-ttu-id="7d2e3-168">**메시지** 탭은 *xx* 개 행 적용됨, PRINT 및 RAISERROR 문의 출력과 같은 시스템 메시지를 계속 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2e3-168">The **Messages** tab continues to display system messages, such as *xx* Rows Affected and the output of PRINT and RAISERROR statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d2e3-169">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7d2e3-169">See Also</span></span>  
 <span data-ttu-id="7d2e3-170">[지역 창](transact-sql-debugger-locals-window.md) </span><span class="sxs-lookup"><span data-stu-id="7d2e3-170">[Locals Window](transact-sql-debugger-locals-window.md) </span></span>  
 <span data-ttu-id="7d2e3-171">[조사식 창](transact-sql-debugger-watch-window.md) </span><span class="sxs-lookup"><span data-stu-id="7d2e3-171">[Watch Window](transact-sql-debugger-watch-window.md) </span></span>  
 <span data-ttu-id="7d2e3-172">[간략한 조사식 대화 상자](transact-sql-debugger-quickwatch-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="7d2e3-172">[QuickWatch Dialog Box](transact-sql-debugger-quickwatch-dialog-box.md) </span></span>  
 <span data-ttu-id="7d2e3-173">[중단점 창](transact-sql-debugger-breakpoints-window.md) </span><span class="sxs-lookup"><span data-stu-id="7d2e3-173">[Breakpoints Window](transact-sql-debugger-breakpoints-window.md) </span></span>  
 <span data-ttu-id="7d2e3-174">[호출 스택 창](transact-sql-debugger-call-stack-window.md) </span><span class="sxs-lookup"><span data-stu-id="7d2e3-174">[Call Stack Window](transact-sql-debugger-call-stack-window.md) </span></span>  
 <span data-ttu-id="7d2e3-175">[스레드 창](transact-sql-debugger-threads-window.md) </span><span class="sxs-lookup"><span data-stu-id="7d2e3-175">[Threads Window](transact-sql-debugger-threads-window.md) </span></span>  
 <span data-ttu-id="7d2e3-176">[출력 창](transact-sql-debugger-output-window.md) </span><span class="sxs-lookup"><span data-stu-id="7d2e3-176">[Output Window](transact-sql-debugger-output-window.md) </span></span>  
 [<span data-ttu-id="7d2e3-177">Transact-SQL 디버거</span><span class="sxs-lookup"><span data-stu-id="7d2e3-177">Transact-SQL Debugger</span></span>](transact-sql-debugger.md)  
  
  
