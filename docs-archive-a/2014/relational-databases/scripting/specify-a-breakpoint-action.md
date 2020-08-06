---
title: 중단점 동작 지정
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint action
- Transact-SQL debugger, breakpoint when hit action
ms.assetid: f97f0097-6f51-40c1-b2e0-294a93ce1e1b
author: rothja
ms.author: jroth
ms.openlocfilehash: 57b3c445e738752400e716538e038349e04e7bd2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651620"
---
# <a name="specify-a-breakpoint-action"></a><span data-ttu-id="64df3-102">중단점 동작 지정</span><span class="sxs-lookup"><span data-stu-id="64df3-102">Specify a Breakpoint Action</span></span>
  <span data-ttu-id="64df3-103">중단점 **적중될 때** 동작은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거가 중단점에 대해 수행하는 사용자 지정 태스크를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-103">A breakpoint **When Hit** action specifies a custom task that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger performs for a breakpoint.</span></span> <span data-ttu-id="64df3-104">지정한 적중 횟수에 도달하고 지정한 중단 조건을 만족하면 디버거는 해당 중단점에 대해 지정된 동작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-104">If the specified hit count is reached and any specified breakpoint condition is satisfied, the debugger performs the action specified for the breakpoint.</span></span>  
  
##  <a name="action-considerations"></a><a name="BKMK_ActionConsiderations"></a> <span data-ttu-id="64df3-105">동작 고려 사항</span><span class="sxs-lookup"><span data-stu-id="64df3-105">Action Considerations</span></span>  
 <span data-ttu-id="64df3-106">중단점의 기본 동작은 적중 횟수와 중단점 조건을 모두 만족하면 실행을 중단하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-106">The default action for a breakpoint is to break execution when both the hit count and breakpoint condition have been satisfied.</span></span> <span data-ttu-id="64df3-107">**디버거에서** 적중될 때 [!INCLUDE[tsql](../../includes/tsql-md.md)] 동작은 주로 출력 메시지를 지정하여 대신 디버거 **출력** 창에 정보를 출력하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-107">The primary use of a **When Hit** action in the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger is to instead print information to the debugger **Output** window by specifying a print message.</span></span>  
  
 <span data-ttu-id="64df3-108">출력 메시지는 디버깅 중인 **의 정보가 포함된 식을 포함하는 텍스트 문자열로** 메시지 표시 [!INCLUDE[tsql](../../includes/tsql-md.md)] 옵션에 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-108">A print message is specified in the **Print a Message** option, and is specified as a text string that includes expressions containing information from the [!INCLUDE[tsql](../../includes/tsql-md.md)] being debugged.</span></span> <span data-ttu-id="64df3-109">식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-109">Expressions include:</span></span>  
  
-   <span data-ttu-id="64df3-110">중괄호({})에 포함된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 식.</span><span class="sxs-lookup"><span data-stu-id="64df3-110">A [!INCLUDE[tsql](../../includes/tsql-md.md)] expression contained in curly braces ({}).</span></span> <span data-ttu-id="64df3-111">식은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 변수, 매개 변수 및 기본 제공 함수를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-111">The expressions can include [!INCLUDE[tsql](../../includes/tsql-md.md)] variables, parameters, and built-in functions.</span></span> <span data-ttu-id="64df3-112">예제에는 {@MyVariable}, {@NameParameter}, {@@SPID} 또는 {SERVERPROPERTY('ProcessID')}가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-112">Examples include {@MyVariable}, {@NameParameter}, {@@SPID}, or {SERVERPROPERTY('ProcessID')}.</span></span>  
  
-   <span data-ttu-id="64df3-113">다음 키워드 중 하나:</span><span class="sxs-lookup"><span data-stu-id="64df3-113">One of the following keywords:</span></span>  
  
    1.  <span data-ttu-id="64df3-114">$ADDRESS는 중단점이 설정된 저장 프로시저 또는 사용자 정의 함수의 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-114">$ADDRESS returns the name of the stored procedure or user-defined function where the breakpoint is set.</span></span> <span data-ttu-id="64df3-115">중단점이 편집기 창에 설정되어 있으면 $ADDRESS는 편집 중인 스크립트 파일의 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-115">If the breakpoint is set in the editor window, $ADDRESS returns the name of the script file being edited.</span></span> <span data-ttu-id="64df3-116">[!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거에서 $ADDRESS와 $FUNCTION은 동일한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-116">$ADDRESS and $FUNCTION return the same information in the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span>  
  
    2.  <span data-ttu-id="64df3-117">$CALLER는 저장 프로시저 또는 함수를 호출한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드 단위의 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-117">$CALLER returns the name of the unit of [!INCLUDE[tsql](../../includes/tsql-md.md)] code that called a stored procedure or function.</span></span> <span data-ttu-id="64df3-118">중단점이 편집기 창에 있으면 $CALLER 반환 \<No caller available> 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-118">If the breakpoint is in the editor window, $CALLER returns \<No caller available>.</span></span> <span data-ttu-id="64df3-119">중단점이 편집기 창의 코드에서 호출되는 저장 프로시저 또는 사용자 정의 함수에 있으면 $CALLER는 편집 중인 파일의 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-119">If the breakpoint is in a stored procedure or user-defined function called from the code in the editor window, $CALLER returns the name of the file being edited.</span></span> <span data-ttu-id="64df3-120">중단점이 다른 저장 프로시저 또는 함수에서 호출되는 저장 프로시저 또는 사용자 정의 함수에 있으면 $CALLER는 호출하는 프로시저 또는 함수의 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-120">If the breakpoint is in a stored procedure or user-defined function called from another stored procedure or function, $CALLER returns the name of the calling procedure or function.</span></span>  
  
    3.  <span data-ttu-id="64df3-121">$CALLSTACK은 체인에서 현재 저장 프로시저 또는 사용자 정의 함수를 호출한 함수 호출 스택을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-121">$CALLSTACK returns the call stack of functions in the chain that called the current stored procedure or user-defined function.</span></span> <span data-ttu-id="64df3-122">중단점이 편집기 창에 있으면 $CALLSTACK은 편집 중인 스크립트 파일의 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-122">If the breakpoint is in the editor window, $CALLSTACK returns the name of the script file being edited.</span></span>  
  
    4.  <span data-ttu-id="64df3-123">$FUNCTION은 중단점이 설정된 저장 프로시저 또는 사용자 정의 함수의 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-123">$FUNCTION returns the name of the stored procedure or user-defined function where the breakpoint is set.</span></span> <span data-ttu-id="64df3-124">중단점이 편집기 창에 설정되어 있으면 $FUNCTION은 편집 중인 스크립트 파일의 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-124">If the breakpoint is set in the editor window, $FUNCTION returns the name of the script file being edited.</span></span>  
  
    5.  <span data-ttu-id="64df3-125">$PID 및 $PNAME은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 이 실행되고 있는 데이터베이스 엔진 인스턴스를 실행하는 운영 체제 프로세스의 ID 및 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-125">$PID and $PNAME return the ID and name of the operating system process running the instance of the Database Engine where the [!INCLUDE[tsql](../../includes/tsql-md.md)] is running.</span></span> <span data-ttu-id="64df3-126">$PID는 SERVERPROPERTY('ProcessID')와 동일한 ID를 반환합니다. 다른 점은 $PID는 16진수 값이고 SERVERPROPERTY('ProcessID')는 10진수 값이라는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-126">$PID returns the same ID as SERVERPROPERTY('ProcessID'), except that $PID is a hexadecimal value while SERVERPROPERTY('ProcessID') is a decimal value.</span></span>  
  
    6.  <span data-ttu-id="64df3-127">$TID 및 $TNAME은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리를 실행하는 운영 체제 스레드의 ID 및 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-127">$TID and $TNAME return the ID and name of the operating system thread running the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch.</span></span> <span data-ttu-id="64df3-128">이 스레드는 데이터베이스 엔진 인스턴스를 실행하는 프로세스에 연결되어 있는 스레드입니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-128">The thread is one associated with the process running the instance of the Database Engine.</span></span> <span data-ttu-id="64df3-129">$TID는 SELECT kpid FROM sys.sysprocesses WHERE spid = @@SPID와 동일한 값을 반환합니다. 다른 점은 $TID는 16진수 값이고 kpid는 10진수 값이라는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-129">$TID returns the same value as SELECT kpid FROM sys.sysprocesses WHERE spid = @@SPID, except that $TID is a hexadecimal value while kpid is a decimal value.</span></span>  
  
-   <span data-ttu-id="64df3-130">백슬래시(\\) 문자를 이스케이프 문자로 사용하여 \\{, \\}, \\\\등의 중괄호 및 백슬래시를 메시지에 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-130">You can also use the backslash character (\\) as an escape character to allow curly braces and backslashes in the message: \\{, \\}, and \\\\.</span></span>  
  
#### <a name="to-specify-a-when-hit-action"></a><span data-ttu-id="64df3-131">적중될 때 동작을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="64df3-131">To Specify a When Hit Action</span></span>  
  
1.  <span data-ttu-id="64df3-132">편집기 창에서 중단점 문자 모양을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **적중될 때** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-132">In the editor window, right-click the breakpoint glyph, and then click **When Hit** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="64df3-133">또는</span><span class="sxs-lookup"><span data-stu-id="64df3-133">-or-</span></span>  
  
     <span data-ttu-id="64df3-134">**중단점** 창에서 중단점 문자 모양을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **적중될 때** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-134">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **When hit** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="64df3-135">**중단점이 적중될 때** 대화 상자에서 원하는 동작을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-135">In the **When Breakpoint Is Hit** dialog box, select the behavior you want:</span></span>  
  
    1.  <span data-ttu-id="64df3-136">중단점이 적중될 때 디버거 출력 창에 메시지를 출력하려면 **메시지 표시** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-136">Select **Print a Message** to print a message in the debugger Output window when the breakpoint is hit.</span></span>  
  
    2.  <span data-ttu-id="64df3-137">**매크로 실행** 옵션은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거에서 사용할 수 없으므로 회색으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-137">The **Run a Macro** option is not available from the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger, and is greyed out.</span></span>  
  
    3.  <span data-ttu-id="64df3-138">중단점이 실행을 일시 중지하지 않도록 하려면 **계속 실행** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-138">Select **Continue execution** if you do not want the breakpoint to pause execution.</span></span> <span data-ttu-id="64df3-139">이 옵션은 **메시지 표시** 옵션을 선택한 경우에만 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-139">This option is active only if you have selected the **Print a Message** option.</span></span>  
  
3.  <span data-ttu-id="64df3-140">**확인** 을 클릭하여 변경 내용을 구현하거나 **취소** 를 클릭하여 변경 내용을 적용하지 않고 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="64df3-140">Click **OK** to implement the changes, or **Cancel** to exit without applying the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64df3-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="64df3-141">See Also</span></span>  
 <span data-ttu-id="64df3-142">[중단점 조건 지정](specify-a-breakpoint-condition.md) </span><span class="sxs-lookup"><span data-stu-id="64df3-142">[Specify a Breakpoint Condition](specify-a-breakpoint-condition.md) </span></span>  
 [<span data-ttu-id="64df3-143">적중 횟수 지정</span><span class="sxs-lookup"><span data-stu-id="64df3-143">Specify a Hit Count</span></span>](specify-a-hit-count.md)  
