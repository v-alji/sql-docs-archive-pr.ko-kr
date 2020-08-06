---
title: 확장 이벤트에 PowerShell 공급자 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- PowerShell [SQL Server], xevent
- extended events [SQL Server], PowerShell
- PowerShell [SQL Server], extended events
ms.assetid: 0b10016f-a479-4444-a484-46cb4677cf64
author: rothja
ms.author: jroth
ms.openlocfilehash: a9efbd389545dcde8285a38b06f41580fb65de6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652117"
---
# <a name="use-the-powershell-provider-for-extended-events"></a><span data-ttu-id="e8db8-102">확장 이벤트에 PowerShell 공급자 사용</span><span class="sxs-lookup"><span data-stu-id="e8db8-102">Use the PowerShell Provider for Extended Events</span></span>
  <span data-ttu-id="e8db8-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 공급자를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 확장 이벤트를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-103">You can manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Extended Events by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider.</span></span> <span data-ttu-id="e8db8-104">XEvent 하위 폴더는 SQLSERVER 드라이브 아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-104">The XEvent subfolder is available under the SQLSERVER drive.</span></span> <span data-ttu-id="e8db8-105">다음 방법 중 하나를 사용하여 이 폴더에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-105">You can access the folder by using either of the following methods:</span></span>  
  
-   <span data-ttu-id="e8db8-106">명령 프롬프트에서 `sqlps`를 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-106">At a command prompt, type `sqlps`, and then press ENTER.</span></span> <span data-ttu-id="e8db8-107">`cd xevent`를 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-107">Type `cd xevent`, and then press ENTER.</span></span> <span data-ttu-id="e8db8-108">여기에서 **cd** 와 `dir` 명령 (또는 **Set-Location** 및 **Get-childitem** cmdlet)을 사용 하 여 서버 이름 및 인스턴스 이름으로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-108">From there, you can use the **cd** and `dir` commands (or **Set-Location** and **Get-Childitem** cmdlets) to navigate to the server name and instance name.</span></span>  
  
-   <span data-ttu-id="e8db8-109">개체 탐색기에서 인스턴스 이름, **관리**를 차례로 확장하고 **확장 이벤트**를 마우스 오른쪽 단추로 클릭한 다음 **PowerShell 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-109">In Object Explorer, expand the instance name, expand **Management**, right-click **Extended Events**, and then click **Start PowerShell**.</span></span> <span data-ttu-id="e8db8-110">이렇게 하면 다음 경로의 PowerShell이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-110">This starts PowerShell in the following path:</span></span>  
  
     <span data-ttu-id="e8db8-111">PS SQLSERVER: \ XEvent \\ *ServerName* \\ *InstanceName*></span><span class="sxs-lookup"><span data-stu-id="e8db8-111">PS SQLSERVER:\XEvent\\*ServerName*\\*InstanceName*></span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e8db8-112">**확장 이벤트**아래의 모든 노드에서 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-112">You can start PowerShell from any node under **Extended Events**.</span></span> <span data-ttu-id="e8db8-113">예를 들어 **세션**을 마우스 오른쪽 단추로 클릭한 다음 **PowerShell 시작**을 클릭하면</span><span class="sxs-lookup"><span data-stu-id="e8db8-113">For example, you can right-click **Sessions**, and then click **Start PowerShell**.</span></span> <span data-ttu-id="e8db8-114">한 수준 아래인 세션 폴더에서 PowerShell이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-114">This starts PowerShell one level deeper, at the Sessions folder.</span></span>  
  
 <span data-ttu-id="e8db8-115">XEvent 폴더 트리를 탐색하여 기존 확장 이벤트 세션 및 관련된 이벤트, 대상 및 조건자를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-115">You can browse the XEvent folder tree to view existing Extended Events sessions and their associated events, targets and predicates.</span></span> <span data-ttu-id="e8db8-116">예를 들어 PS SQLSERVER: \ XEvent \\ *ServerName* \\ *InstanceName*> 경로에서를 입력 하는 경우 `cd sessions` enter 키를 누르고를 입력 한 `dir` 다음 enter 키를 누르면 해당 인스턴스에 저장 된 세션 목록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-116">For example, from the PS SQLSERVER:\XEvent\\*ServerName*\\*InstanceName*> path, if you type `cd sessions`, press ENTER, type `dir`, and then press ENTER, you can see the list of sessions that are stored on that instance.</span></span> <span data-ttu-id="e8db8-117">세션이 실행 중인지 여부(실행 중인 경우 실행 시간) 및 인스턴스가 시작될 때 세션이 시작되도록 구성되어 있는지 여부도 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-117">You can also view whether the session is running (and if this is the case, for how long), and whether the session is configured to start when the instance starts.</span></span>  
  
 <span data-ttu-id="e8db8-118">세션과 연결된 이벤트, 이벤트의 조건자 및 대상을 보려면 디렉터리를 세션 이름으로 변경한 다음 이벤트나 대상 폴더를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-118">To view the events, their predictates, and the targets that are associated with a session, you can change directories to the session name, and then view either the events or targets folder.</span></span> <span data-ttu-id="e8db8-119">예를 들어, 기본 시스템 상태 세션과 연결 된 이벤트 및 해당 조건자를 보려면 PS SQLSERVER: \ XEvent \\ *ServerName* \\ *InstanceName*\sessions> path에서 enter 키를 입력 하 `cd system_health\events,` `dir` 고를 입력 한 다음 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-119">For example, to view the events and their predicates that are associated with the default system health session, from the PS SQLSERVER:\XEvent\\*ServerName*\\*InstanceName*\Sessions> path, type `cd system_health\events,` press ENTER, type `dir`, and then press ENTER.</span></span>  
  
 <span data-ttu-id="e8db8-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 공급자는 확장 이벤트 세션을 생성, 변경 및 관리하는 데 사용할 수 있는 강력한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-120">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider is a powerful tool that you can use to create, alter, and manage Extended Events sessions.</span></span> <span data-ttu-id="e8db8-121">다음 섹션에서는 확장 이벤트에 PowerShell 스크립트를 사용하는 몇 가지 기본적인 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-121">The following section provides some basic examples of using PowerShell scripts with Extended Events.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e8db8-122">예</span><span class="sxs-lookup"><span data-stu-id="e8db8-122">Examples</span></span>  
 <span data-ttu-id="e8db8-123">다음 예에서 다음 사항에 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="e8db8-123">In the following examples, note the following:</span></span>  
  
-   <span data-ttu-id="e8db8-124">스크립트는 PS SQLSERVER:> 프롬프트에서 실행 해야 합니다 \\ (명령 프롬프트에서를 입력 하 여 사용 가능 `sqlps` ).</span><span class="sxs-lookup"><span data-stu-id="e8db8-124">The scripts must be run from the PS SQLSERVER:\\> prompt (available by typing `sqlps` at a command prompt).</span></span>  
  
-   <span data-ttu-id="e8db8-125">스크립트가 기본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-125">The scripts use the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="e8db8-126">스크립트를 .ps1 확장명으로 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-126">The scripts must be saved with a .ps1 extension.</span></span>  
  
-   <span data-ttu-id="e8db8-127">PowerShell 실행 정책에서 스크립트 실행을 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-127">The PowerShell execution policy must allow the script to run.</span></span> <span data-ttu-id="e8db8-128">실행 정책을 설정하려면 **Set-Executionpolicy** cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-128">To set the execution policy, use the **Set-Executionpolicy** cmdlet.</span></span> <span data-ttu-id="e8db8-129">자세한 내용을 확인하려면 `get-help set-executionpolicy -detailed`를 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-129">(For more information, type `get-help set-executionpolicy -detailed`, and then press ENTER.)</span></span>  
  
 <span data-ttu-id="e8db8-130">다음 스크립트는 'TestSession'이라는 새 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-130">The following script creates a new session that is named 'TestSession'.</span></span>  
  
```powershell
#Script for creating a session.  
cd XEvent  
$h = hostname  
cd $h  
  
#Use the default instance.  
$store = dir | where {$_.DisplayName -ieq 'default'}  
$session = New-Object Microsoft.SqlServer.Management.XEvent.Session -ArgumentList $store, "TestSession"  
$event = $session.AddEvent("sqlserver.file_written")  
$event.AddAction("package0.callstack")  
$session.Create()  
```  
  
 <span data-ttu-id="e8db8-131">다음 스크립트는 앞의 예에서 만든 세션에 링 버퍼 대상을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-131">The following script adds the ring buffer target to the session that was created in the previous example.</span></span> <span data-ttu-id="e8db8-132">이 예에서는 `Alter` 메서드를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-132">(This example shows the use of the `Alter` method.</span></span> <span data-ttu-id="e8db8-133">세션을 처음 만들 때 대상을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-133">Be aware that you can add the target when you first create the session.)</span></span>  
  
```powershell
#Script to alter a session.  
cd XEvent  
$h = hostname  
cd $h  
cd DEFAULT\Sessions  
  
#Used to find the specified session.  
$session = dir | where {$_.Name -eq 'TestSession'}  
  
#Add the ring buffer target and call the Alter method.  
$session.AddTarget("package0.ring_buffer")  
$session.Alter()  
```  
  
 <span data-ttu-id="e8db8-134">다음 스크립트는 조건자 식을 사용하는 새 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-134">The following script creates a new session that uses a predicate expression.</span></span> <span data-ttu-id="e8db8-135">이 경우 세션에서 sqlserver.file_written 이벤트를 통해 c:\temp.log 파일이 기록되는 시점에 대한 정보를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-135">In this case, the session collects information for when the c:\temp.log file is written to (through the sqlserver.file_written event).</span></span>  
  
```powershell
#Script for creating a session.  
cd XEvent  
$h = hostname  
cd $h  
  
#Use the default instance.  
$store = dir | where {$_.DisplayName -ieq 'default'}  
$session = New-Object Microsoft.SqlServer.Management.XEvent.Session -ArgumentList $store, "TestSession2"  
$event = $session.AddEvent("sqlserver.file_written")  
  
#Construct a predicate "equal_i_unicode_string(path, N'c:\temp.log')".  
$column = $store.SqlServerPackage.EventInfoSet["file_written"].DataEventColumnInfoSet["path"]  
$operand = new-object Microsoft.SqlServer.Management.XEvent.PredOperand -argumentlist $column  
$value = new-object Microsoft.SqlServer.Management.XEvent.PredValue -argumentlist "c:\temp.log"  
$compare = $store.Package0Package.PredCompareInfoSet["equal_i_unicode_string"]  
$predicate = new-object Microsoft.SqlServer.Management.XEvent.PredFunctionExpr -ArgumentList $compare, $operand, $value  
$event.SetPredicate($predicate)  
$session.Create()  
```  
  
## <a name="security"></a><span data-ttu-id="e8db8-136">보안</span><span class="sxs-lookup"><span data-stu-id="e8db8-136">Security</span></span>  
 <span data-ttu-id="e8db8-137">확장 이벤트 세션을 생성, 변경 또는 삭제하려면 ALTER ANY EVENT SESSION 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db8-137">To create, alter, or drop an Extended Events session, you must have the ALTER ANY EVENT SESSION permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8db8-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e8db8-138">See Also</span></span>  
 <span data-ttu-id="e8db8-139">[SQL Server PowerShell](../../powershell/sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="e8db8-139">[SQL Server PowerShell](../../powershell/sql-server-powershell.md) </span></span>  
 <span data-ttu-id="e8db8-140">[System_health 세션 사용](use-the-ssms-xe-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="e8db8-140">[Use the system_health Session](use-the-ssms-xe-profiler.md) </span></span>  
 [<span data-ttu-id="e8db8-141">확장 이벤트 도구</span><span class="sxs-lookup"><span data-stu-id="e8db8-141">Extended Events Tools</span></span>](extended-events-tools.md)  
