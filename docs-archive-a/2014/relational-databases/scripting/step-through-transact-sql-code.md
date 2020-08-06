---
title: Transact-SQL 코드 단계별 실행
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, debugging code
- Transact-SQL debugger, step over
- Transact-SQL debugger, step out
- Transact-SQL debugger, step into
ms.assetid: e09079b8-c4c9-42b4-821b-4ce81a98a086
author: rothja
ms.author: jroth
ms.openlocfilehash: 48cb307130c65729640864a26bdf1dfaf344b32b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653799"
---
# <a name="step-through-transact-sql-code"></a><span data-ttu-id="b68a2-102">Transact-SQL 코드 단계별 실행</span><span class="sxs-lookup"><span data-stu-id="b68a2-102">Step Through Transact-SQL Code</span></span>
  <span data-ttu-id="b68a2-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거를 사용하면 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리 편집기 창에서 실행되는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 문을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-103">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger enables you to control which [!INCLUDE[tsql](../../includes/tsql-md.md)] statements are run in a [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window.</span></span> <span data-ttu-id="b68a2-104">개별 문에서 디버거를 일시 중지한 다음 해당 지점에서의 코드 요소 상태를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-104">You can pause the debugger on individual statements and then view the state of the code elements at that point.</span></span>  
  
## <a name="breakpoints"></a><span data-ttu-id="b68a2-105">중단점</span><span class="sxs-lookup"><span data-stu-id="b68a2-105">Breakpoints</span></span>  
 <span data-ttu-id="b68a2-106">중단점은 디버거에게 특정 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 실행을 일시 중지하라는 신호를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-106">A breakpoint signals the debugger to pause execution on a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="b68a2-107">중단점에 대한 자세한 내용은 Transact-SQL 중단점 사용을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b68a2-107">For more information about breakpoints, see Using Transact-SQL Breakpoints.</span></span>  
  
## <a name="controlling-statement-execution"></a><span data-ttu-id="b68a2-108">문 실행 제어</span><span class="sxs-lookup"><span data-stu-id="b68a2-108">Controlling Statement Execution</span></span>  
 <span data-ttu-id="b68a2-109">[!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드의 현재 문에서 실행하기 위해 다음 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-109">In the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger, you can specify the following options for executing from the current statement in [!INCLUDE[tsql](../../includes/tsql-md.md)] code:</span></span>  
  
-   <span data-ttu-id="b68a2-110">다음 중단점까지 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-110">Run to the next breakpoint.</span></span>  
  
-   <span data-ttu-id="b68a2-111">다음 문을 한 단계씩 코드 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-111">Step into the next statement.</span></span>  
  
     <span data-ttu-id="b68a2-112">다음 문에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저, 함수 또는 트리거를 호출하면 디버거에서 모듈 코드가 포함된 새 쿼리 편집기 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-112">If the next statement invokes a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, function, or trigger, the debugger displays a new Query Editor window that contains the code of the module.</span></span> <span data-ttu-id="b68a2-113">창이 디버그 모드에 있으며 모듈의 첫 번째 문에서 실행이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-113">The window is in debug mode, and execution pauses on the first statement in the module.</span></span> <span data-ttu-id="b68a2-114">그리고 나서 중단점을 설정하거나 코드를 단계별로 실행하여 모듈 코드를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-114">You can then move through the module code, for example, by setting breakpoints or stepping through the code.</span></span>  
  
-   <span data-ttu-id="b68a2-115">다음 문을 프로시저 단위로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-115">Step over the next statement.</span></span>  
  
     <span data-ttu-id="b68a2-116">다음 문이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-116">The next statement is executed.</span></span> <span data-ttu-id="b68a2-117">그러나 문에서 저장 프로시저, 함수 또는 트리거를 호출하면 모듈 코드가 완료될 때까지 실행되고 결과가 호출 코드에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-117">However, if the statement invokes a stored procedure, function, or trigger, the module code runs until it finishes, and the results are returned to the calling code.</span></span> <span data-ttu-id="b68a2-118">저장 프로시저에 오류가 없으면 저장 프로시저를 프로시저 단위로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-118">If you are sure there are no errors in a stored procedure, you can step over it.</span></span> <span data-ttu-id="b68a2-119">저장 프로시저, 함수 또는 트리거를 호출한 후 문에서 실행이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-119">Execution pauses on the statement that follows the call to the stored procedure, function, or trigger.</span></span>  
  
-   <span data-ttu-id="b68a2-120">저장 프로시저, 함수 또는 트리거 프로시저를 나갑니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-120">Step out of a stored procedure, function, or trigger.</span></span>  
  
     <span data-ttu-id="b68a2-121">저장 프로시저, 함수 또는 트리거를 호출한 후 문에서 실행이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-121">Execution pauses on the statement that follows the call to the stored procedure, function, or trigger.</span></span>  
  
-   <span data-ttu-id="b68a2-122">현재 위치에서 포인터의 현재 위치로 실행하고 모든 중단점을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-122">Run from the current location to the current location of the pointer, and ignore all breakpoints.</span></span>  
  
 <span data-ttu-id="b68a2-123">다음 표에서는 문이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거에서 실행되는 방법을 제어하는 여러 방법을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-123">The following table lists the various ways in which you can control how statements execute in the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span>  
  
|<span data-ttu-id="b68a2-124">작업</span><span class="sxs-lookup"><span data-stu-id="b68a2-124">Action</span></span>|<span data-ttu-id="b68a2-125">절차</span><span class="sxs-lookup"><span data-stu-id="b68a2-125">Procedure</span></span>|  
|------------|---------------|  
|<span data-ttu-id="b68a2-126">현재 문부터 다음 중단점까지 모든 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-126">Run all statements from the current statement to the next breakpoint</span></span>|<span data-ttu-id="b68a2-127">**디버그** 메뉴에서 **계속**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-127">On the **Debug** menu, click **Continue**.</span></span><br /><br /> <span data-ttu-id="b68a2-128">**디버그** 도구 모음에서 **계속** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-128">On the **Debug** toolbar, click the **Continue** button.</span></span>|  
|<span data-ttu-id="b68a2-129">다음 문 또는 모듈을 한 단계씩 코드 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-129">Step into the next statement or module</span></span>|<span data-ttu-id="b68a2-130">**디버그** 메뉴에서 한 **단계씩 코드 실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-130">On the **Debug** menu, click **Step Into**.</span></span><br /><br /> <span data-ttu-id="b68a2-131">**디버그** 도구 모음에서 한 **단계씩 코드 실행** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-131">On the **Debug** toolbar, click the **Step Into** button.</span></span><br /><br /> <span data-ttu-id="b68a2-132">F11 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-132">Press F11.</span></span>|  
|<span data-ttu-id="b68a2-133">다음 문 또는 모듈을 프로시저 단위로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-133">Step over the next statement or module</span></span>|<span data-ttu-id="b68a2-134">**디버그** 메뉴에서 **프로시저 단위 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-134">On the **Debug** menu, click **Step Over**.</span></span><br /><br /> <span data-ttu-id="b68a2-135">**디버그** 도구 모음에서 **프로시저 단위 실행** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-135">On the **Debug** toolbar, click the **Step Over** button.</span></span><br /><br /> <span data-ttu-id="b68a2-136">F10 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-136">Press F10.</span></span>|  
|<span data-ttu-id="b68a2-137">모듈 프로시저를 나갑니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-137">Step out of a module</span></span>|<span data-ttu-id="b68a2-138">**디버그** 메뉴에서 **프로시저 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-138">On the **Debug** menu, click **Step Out**.</span></span><br /><br /> <span data-ttu-id="b68a2-139">**디버그** 도구 모음에서 **프로시저 아웃** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-139">On the **Debug** toolbar, click the **Step Out** button.</span></span><br /><br /> <span data-ttu-id="b68a2-140">Shift+F11을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-140">Press SHIFT+F11.</span></span>|  
|<span data-ttu-id="b68a2-141">현재 커서 위치까지 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-141">Run to the current cursor location</span></span>|<span data-ttu-id="b68a2-142">쿼리 편집기 창에서 마우스 오른쪽을 클릭한 다음 **커서까지 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-142">Right-click in the Query Editor window, and then click **Run To Cursor**.</span></span><br /><br /> <span data-ttu-id="b68a2-143">Ctrl+F10을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b68a2-143">Press CTRL+F10.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b68a2-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b68a2-144">See Also</span></span>  
 [<span data-ttu-id="b68a2-145">Transact-SQL 디버거 정보</span><span class="sxs-lookup"><span data-stu-id="b68a2-145">Transact-SQL Debugger Information</span></span>](transact-sql-debugger-information.md)  
  
  
