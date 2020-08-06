---
title: 호출 스택 창
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Call Stack Window [Transact-SQL]
ms.assetid: ddb0b19c-87cd-4883-bcb8-ec09ffb30369
author: rothja
ms.author: jroth
ms.openlocfilehash: b4b72e484ade696be81ebac8ea4eed9be295edf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659921"
---
# <a name="call-stack-window"></a><span data-ttu-id="3196b-102">호출 스택 창</span><span class="sxs-lookup"><span data-stu-id="3196b-102">Call Stack Window</span></span>
  <span data-ttu-id="3196b-103">**호출 스택** 창에는 호출 스택의 모듈, 모듈에 전달되는 매개 변수의 값 및 데이터 형식이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-103">The **Call Stack** window displays the modules on the call stack, and the data types and values of any parameters that are passed to the modules.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="3196b-104">모듈은 저장 프로시저, 함수 및 트리거를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-104">modules include stored procedures, functions, and triggers.</span></span> <span data-ttu-id="3196b-105">호출 스택을 표시하려면 디버그 모드여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-105">To display the call stack, you must be in debug mode.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="3196b-106">작업 목록</span><span class="sxs-lookup"><span data-stu-id="3196b-106">Task List</span></span>  
 <span data-ttu-id="3196b-107">**호출 스택 창에 액세스하려면**</span><span class="sxs-lookup"><span data-stu-id="3196b-107">**To access the Call Stack window**</span></span>  
  
-   <span data-ttu-id="3196b-108">**디버그** 메뉴에서 **창**을 선택한 다음 **호출 스택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-108">On the **Debug** menu, click **Windows**, and then click **Call Stack**.</span></span>  
  
 <span data-ttu-id="3196b-109">**현재 호출 스택 프레임을 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="3196b-109">**To change the current Call Stack frame**</span></span>  
  
 <span data-ttu-id="3196b-110">다음 절차 중 하나를 사용하여 스택 프레임을 현재 프레임으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-110">You can use either of the following procedures to make a stack frame the current frame:</span></span>  
  
-   <span data-ttu-id="3196b-111">스택 프레임을 마우스 오른쪽 단추로 클릭하고 **프레임으로 전환**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-111">Right-click the stack frame, and then click **Switch To Frame**.</span></span>  
  
-   <span data-ttu-id="3196b-112">스택 프레임을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-112">Double-click the stack frame.</span></span>  
  
 <span data-ttu-id="3196b-113">**현재 프레임이 아닌 프레임 원본을 보려면**</span><span class="sxs-lookup"><span data-stu-id="3196b-113">**To view the source of a frame other than the current frame**</span></span>  
  
-   <span data-ttu-id="3196b-114">스택 프레임을 마우스 오른쪽 단추로 클릭한 다음 **소스 코드로 이동**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-114">Right-click the stack frame, and then click **Go To Source Code**.</span></span>  
  
## <a name="stack-frames"></a><span data-ttu-id="3196b-115">스택 프레임</span><span class="sxs-lookup"><span data-stu-id="3196b-115">Stack Frames</span></span>  
 <span data-ttu-id="3196b-116">**호출 스택** 창의 각 행은 스택 프레임이라고 하며 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 파일에서의 모듈 호출 또는 모듈 사이의 호출을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-116">Each row in the **Call Stack** window is called a stack frame and represents either a call from a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file to a module or a call from one module to another.</span></span> <span data-ttu-id="3196b-117">화면의 맨 아래 스택 프레임은 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기 창에서 스택으로 처음 호출을 수행한 줄을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-117">The bottom stack frame in the display indicates the line in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window that made the first call into the stack.</span></span> <span data-ttu-id="3196b-118">맨 위 행은 디버거가 실행을 일시 중지한 행을 나타내며 창의 왼쪽 여백에 노란 화살표로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-118">The top row indicates the line on which the debugger paused execution, and is identified by a yellow arrow in the left margin of the window.</span></span> <span data-ttu-id="3196b-119">각 중간 행은 모듈과 다음으로 높은 스택 프레임을 호출한 원본 코드의 줄 번호를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-119">Each intermediate row indicates the module and the line number of the source code that called the next higher stack frame.</span></span>  
  
 <span data-ttu-id="3196b-120">**지역**, **조사식**및 **간략한 조사식** 창의 모든 식은 현재 스택 프레임을 기준으로 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-120">All expressions in the **Locals**, **Watch**, and **QuickWatch** windows are evaluated based on the current stack frame.</span></span> <span data-ttu-id="3196b-121">현재 프레임에 대한 코드는 쿼리 편집기 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-121">The Query Editor window displays the code for the current frame.</span></span> <span data-ttu-id="3196b-122">기본적으로 현재 스택 프레임은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거가 실행을 일시 중지한 프레임입니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-122">By default, the current stack frame is the frame in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger paused execution.</span></span> <span data-ttu-id="3196b-123">현재 스택 프레임에서 다른 프레임으로 변경하면 **지역**, **조사식**및 **간략한 조사식** 창의 식은 새 프레임의 컨텍스트에서 다시 평가되고 새 프레임의 원본 코드가 쿼리 편집기 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-123">When you change the current stack frame to another frame, the expressions in the **Locals**, **Watch**, and **QuickWatch** windows are reevaluated in the context of the new frame, and the source code of the new frame is displayed in the Query Editor window.</span></span>  
  
## <a name="columns"></a><span data-ttu-id="3196b-124">열</span><span class="sxs-lookup"><span data-stu-id="3196b-124">Columns</span></span>  
 <span data-ttu-id="3196b-125">**이름**</span><span class="sxs-lookup"><span data-stu-id="3196b-125">**Name**</span></span>  
 <span data-ttu-id="3196b-126">호출 스택의 모듈에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-126">Displays information about a module on the call stack.</span></span>  
  
 <span data-ttu-id="3196b-127">호출 스택의 맨 아래 행에서 **이름** 에는 쿼리 편집기 원본 창과 스택으로 처음 호출을 수행한 줄 번호가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-127">For the bottom row in the call stack, **Name** lists the Query Editor source window and line number of the first call into the stack.</span></span> <span data-ttu-id="3196b-128">다른 행에서 **이름** 형식은 **Module(Instance.Database)(ParmList) LineNumber**입니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-128">For the other rows, **Name** has the format **Module(Instance.Database)(ParmList) LineNumber**.</span></span>  
  
 <span data-ttu-id="3196b-129">**모듈**</span><span class="sxs-lookup"><span data-stu-id="3196b-129">**Module**</span></span>  
 <span data-ttu-id="3196b-130">해당 저장 프로시저 또는 함수의 이름이나 다음 프레임으로 호출되는 저장 프로시저의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-130">Is the name of the stored procedure, function, or stored procedure that called to the next frame.</span></span>  
  
 <span data-ttu-id="3196b-131">**Instance.Database**</span><span class="sxs-lookup"><span data-stu-id="3196b-131">**Instance.Database**</span></span>  
 <span data-ttu-id="3196b-132">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스 및 모듈을 포함하는 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-132">Is the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and the database that is holding the module.</span></span>  
  
 <span data-ttu-id="3196b-133">**ParmList**</span><span class="sxs-lookup"><span data-stu-id="3196b-133">**ParmList**</span></span>  
 <span data-ttu-id="3196b-134">모듈 호출 중에 전달되는 각 매개 변수의 데이터 형식, 이름 및 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-134">Indicates the data type, name, and value for each parameter that is passed in during the call to the module.</span></span>  
  
 <span data-ttu-id="3196b-135">**LineNumber**</span><span class="sxs-lookup"><span data-stu-id="3196b-135">**LineNumber**</span></span>  
 <span data-ttu-id="3196b-136">맨 위 행을 제외한 모든 행에서 **LineNumber** 는 모듈에서 프레임으로 호출된 줄을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-136">For all rows except the top row, **LineNumber** indicates which line in the module called to the frame.</span></span> <span data-ttu-id="3196b-137">맨 위 행에서 **LineNumber** 는 현재 디버거의 포커스가 있는 줄을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-137">For the top row, **LineNumber** indicates the line on which the debugger is currently focused.</span></span>  
  
 <span data-ttu-id="3196b-138">**언어**</span><span class="sxs-lookup"><span data-stu-id="3196b-138">**Language**</span></span>  
 <span data-ttu-id="3196b-139">**의 경우** Transact-SQL [!INCLUDE[tsql](../../includes/tsql-md.md)]을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3196b-139">Displays **Transact-SQL** for [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3196b-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3196b-140">See Also</span></span>  
 <span data-ttu-id="3196b-141">[Transact-sql 디버거](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="3196b-141">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="3196b-142">[Transact-sql 디버거 정보](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="3196b-142">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 [<span data-ttu-id="3196b-143">Transact-SQL 코드 단계별 실행</span><span class="sxs-lookup"><span data-stu-id="3196b-143">Step Through Transact-SQL Code</span></span>](step-through-transact-sql-code.md)  
