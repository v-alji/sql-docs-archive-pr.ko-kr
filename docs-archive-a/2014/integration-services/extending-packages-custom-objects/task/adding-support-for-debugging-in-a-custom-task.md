---
title: 사용자 지정 태스크에 디버깅 지원 추가 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BreakpointManager class
- breakpoints [Integration Services]
- custom tasks [Integration Services], debugging
- IDTSSuspend interface
- IDTSBreakpointSite interface
- SSIS custom tasks, debugging
- debugging [Integration Services], custom tasks
ms.assetid: 7f06e49b-0b60-4e81-97da-d32dc248264a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fcc1d0c18cd559b547eadb9c1fa77e8f143389d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652224"
---
# <a name="adding-support-for-debugging-in-a-custom-task"></a><span data-ttu-id="112cb-102">사용자 지정 태스크에 디버깅 지원 추가</span><span class="sxs-lookup"><span data-stu-id="112cb-102">Adding Support for Debugging in a Custom Task</span></span>
  <span data-ttu-id="112cb-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 런타임 엔진에서는 중단점을 사용하여 실행 중 패키지, 태스크 및 기타 유형의 컨테이너를 일시 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-103">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] run-time engine enables packages, tasks, and other types of containers to be suspended during execution by using breakpoints.</span></span> <span data-ttu-id="112cb-104">중단점을 사용하면 애플리케이션이나 태스크가 올바르게 실행되지 못하도록 하는 오류를 검토하고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-104">The use of breakpoints lets you review and correct errors that prevent your application or tasks from running correctly.</span></span> <span data-ttu-id="112cb-105">중단점 아키텍처를 통해 클라이언트는 태스크 처리가 일시 중지된 동안 정의된 실행 지점에서 패키지에 있는 개체의 런타임 값을 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-105">The breakpoint architecture enables the client to evaluate the run-time value of objects in the package at defined points of execution while task processing is suspended.</span></span>  
  
 <span data-ttu-id="112cb-106">사용자 지정 태스크 개발자는 이 아키텍처를 기반으로 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> 인터페이스와 해당 부모 인터페이스인 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend>를 사용하여 사용자 지정 중단점 대상을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-106">Custom task developers can use this architecture to create custom breakpoint targets by using the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> interface, and its parent interface, <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend>.</span></span> <span data-ttu-id="112cb-107"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> 인터페이스는 사용자 지정 중단점 위치 또는 대상을 만들고 관리하기 위한 태스크와 런타임 엔진 간의 상호 작용을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-107">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> interface defines the interaction between the run-time engine and the task for creating and managing custom breakpoint sites or targets.</span></span> <span data-ttu-id="112cb-108"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> 인터페이스는 런타임 엔진에서 실행을 일시 중지하거나 다시 시작하도록 태스크에 알리기 위해 호출하는 메서드 및 속성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-108">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> interface provides methods and properties that are called by the run-time engine to notify the task to suspend or resume its execution.</span></span>  
  
 <span data-ttu-id="112cb-109">중단점 위치 또는 대상은 태스크 실행 중 처리를 일시 중지할 수 있는 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-109">A breakpoint site or target is a point in the execution of the task where processing can be suspended.</span></span> <span data-ttu-id="112cb-110">**중단점 설정** 대화 상자의 사용 가능한 중단점 위치 중에서 사용자가 원하는 중단점 위치를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-110">Users select from available breakpoint sites in the **Set Breakpoints** dialog box.</span></span> <span data-ttu-id="112cb-111">예를 들어 Foreach 루프 컨테이너에서는 기본 중단점 옵션 외에도 "루프의 모든 반복 시작에서 중단" 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-111">For example, in addition to the default breakpoint options, the Foreach Loop Container offers the "Break at the beginning of every iteration of the loop" option.</span></span>  
  
 <span data-ttu-id="112cb-112">태스크는 실행 중 중단점 대상에 도달하면 중단점 대상을 평가하여 해당 중단점이 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-112">When a task reaches a breakpoint target during execution, it evaluates the breakpoint target to determine whether a breakpoint is enabled.</span></span> <span data-ttu-id="112cb-113">중단점이 설정되어 있으면 사용자가 해당 중단점에서 실행을 중지하기를 원한다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-113">This indicates that the user wants execution to stop at that breakpoint.</span></span> <span data-ttu-id="112cb-114">중단점이 설정된 경우 태스크에서는 런타임 엔진에 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-114">If the breakpoint is enabled, the task raises the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> event to the run-time engine.</span></span> <span data-ttu-id="112cb-115">런타임 엔진은 패키지에서 현재 실행 중인 각 태스크의 `Suspend` 메서드를 호출하여 이벤트에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-115">The run-time engine responds to the event by calling the `Suspend` method of each task that is currently running in the package.</span></span> <span data-ttu-id="112cb-116">런타임에서 일시 중지된 태스크의 `ResumeExecution` 메서드를 호출하면 태스크 실행이 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-116">Execution of the task resumes when the runtime calls the `ResumeExecution` method of the suspended task.</span></span>  
  
 <span data-ttu-id="112cb-117">중단점을 사용하지 않는 태스크도 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> 및 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> 인터페이스를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-117">Tasks that do not use breakpoints should still implement the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> and <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> interfaces.</span></span> <span data-ttu-id="112cb-118">이러한 인터페이스를 구현하면 패키지의 다른 개체가 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> 이벤트를 발생시킬 때 태스크가 올바르게 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-118">This ensures that the task is suspended correctly when other objects in the package raise <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> events.</span></span>  
  
## <a name="idtsbreakpointsite-interface-and-breakpointmanager"></a><span data-ttu-id="112cb-119">IDTSBreakpointSite 인터페이스 및 BreakpointManager</span><span class="sxs-lookup"><span data-stu-id="112cb-119">IDTSBreakpointSite Interface and BreakpointManager</span></span>  
 <span data-ttu-id="112cb-120">태스크에서는 정수 ID와 문자열 설명을 매개 변수로 제공하는 <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager.CreateBreakpointTarget%2A>의 <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager> 메서드를 호출하여 중단점 대상을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-120">Tasks create breakpoint targets by calling the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager.CreateBreakpointTarget%2A> method of the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager>, providing an integer ID and string description as parameters.</span></span> <span data-ttu-id="112cb-121">태스크는 코드에서 중단점 대상이 들어 있는 지점에 도달하면 <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager.IsBreakpointTargetEnabled%2A> 메서드로 중단점 대상을 평가하여 해당 중단점이 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-121">When the task reaches the point in its code that contains a breakpoint target, it evaluates the breakpoint target by using the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager.IsBreakpointTargetEnabled%2A> method to determine whether that breakpoint is enabled.</span></span> <span data-ttu-id="112cb-122">`true`인 경우 태스크에서는 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> 이벤트를 발생시켜 런타임 엔진에 이를 알립니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-122">If `true`, the task notifies the run-time engine by raising the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> event.</span></span>  
  
 <span data-ttu-id="112cb-123"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> 인터페이스는 태스크를 만들 때 런타임 엔진에서 호출하는 단일 메서드 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite.AcceptBreakpointManager%2A>를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-123">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> interface defines a single method, <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite.AcceptBreakpointManager%2A>, which is called by the run-time engine during task creation.</span></span> <span data-ttu-id="112cb-124">이 메서드는 매개 변수로 <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager> 개체를 제공하며, 이 개체는 태스크에서 중단점을 만들고 관리하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-124">This method provides as a parameter the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager> object, which is then used by the task to create and manage its breakpoints.</span></span> <span data-ttu-id="112cb-125">태스크에서는 <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager>를 `Validate` 및 `Execute` 메서드 실행 중에 사용할 수 있도록 로컬로 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-125">Tasks should store the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager> locally for use during the `Validate` and `Execute` methods.</span></span>  
  
 <span data-ttu-id="112cb-126">다음 예제 코드에서는 <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager>를 사용하여 중단점 대상을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-126">The following sample code demonstrates how to create a breakpoint target by using the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager>.</span></span> <span data-ttu-id="112cb-127">이 예제에서는 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> 메서드를 호출하여 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-127">The sample calls the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> method to raise the event.</span></span>  
  
```csharp  
public void AcceptBreakpointManager( BreakpointManager breakPointManager )  
{  
   //   Store the breakpoint manager locally.  
   this.bpm  = breakPointManager;  
}  
public override DTSExecResult Execute( Connections connections,  
  Variables variables, IDTSComponentEvents events,  
  IDTSLogging log, DtsTransaction txn)  
{  
   //   Create a breakpoint.  
   this.bpm.CreateBreakPointTarget( 1 , "A sample breakpoint target." );  
...  
   if( this.bpm.IsBreakpointTargetEnabled( 1 ) == true )  
      events.OnBreakpointHit( this.bpm.GetBreakpointTarget( 1 ) );  
}  
```  
  
```vb  
Public Sub AcceptBreakpointManager(ByVal breakPointManager As BreakpointManager)  
  
   ' Store the breakpoint manager locally.  
   Me.bpm  = breakPointManager  
  
End Sub  
  
Public Overrides Function Execute(ByVal connections As Connections, _  
  ByVal variables As Variables, ByVal events As IDTSComponentEvents, _  
  ByVal log As IDTSLogging, ByVal txn As DtsTransaction) As DTSExecResult  
  
   ' Create a breakpoint.  
   Me.bpm.CreateBreakPointTarget(1 , "A sample breakpoint target.")  
  
   If Me.bpm.IsBreakpointTargetEnabled(1) = True Then  
      events.OnBreakpointHit(Me.bpm.GetBreakpointTarget(1))  
   End If  
  
End Function  
```  
  
## <a name="idtssuspend-interface"></a><span data-ttu-id="112cb-128">IDTSSuspend 인터페이스</span><span class="sxs-lookup"><span data-stu-id="112cb-128">IDTSSuspend Interface</span></span>  
 <span data-ttu-id="112cb-129"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> 인터페이스는 런타임 엔진에서 태스크 실행을 일시 중지하거나 다시 시작할 때 호출하는 메서드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-129">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> interface defines the methods that are called by the run-time engine when it pauses or resumes execution of a task.</span></span> <span data-ttu-id="112cb-130"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> 인터페이스는 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> 인터페이스에 의해 구현되며 이 인터페이스의 `Suspend` 및 `ResumeExecution` 메서드는 대개 사용자 지정 태스크에 의해 재정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-130">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> interface is implemented by the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> interface, and its `Suspend` and `ResumeExecution` methods are usually overridden by the custom task.</span></span> <span data-ttu-id="112cb-131">런타임 엔진은 태스크에서 `OnBreakpointHit` 이벤트를 받으면 실행 중인 각 태스크의 `Suspend` 메서드를 호출하여 태스크를 일시 중지하라고 알립니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-131">When the run-time engine receives an `OnBreakpointHit` event from a task, it calls the `Suspend` method of each running task, notifying the tasks to pause.</span></span> <span data-ttu-id="112cb-132">클라이언트가 실행을 다시 시작하면 런타임 엔진에서는 일시 중지된 태스크의 `ResumeExecution` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-132">When the client resumes execution, the run-time engine calls the `ResumeExecution` method of the tasks that are suspended.</span></span>  
  
 <span data-ttu-id="112cb-133">태스크 실행을 일시 중지하고 다시 시작하려면 태스크의 실행 스레드를 일시 중지하고 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-133">Suspending and resuming task execution involves pausing and resuming the task's execution thread.</span></span> <span data-ttu-id="112cb-134">관리 코드에서는 .NET Framework의 `ManualResetEvent` 네임스페이스에 있는 `System.Threading` 클래스를 사용하여 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-134">In managed code, you do this using the `ManualResetEvent` class in `System.Threading` namespace of the .NET Framework.</span></span>  
  
 <span data-ttu-id="112cb-135">다음 코드 예제에서는 태스크 실행을 일시 중지하고 다시 시작하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-135">The following code sample demonstrates suspension and resumption of task execution.</span></span> <span data-ttu-id="112cb-136">`Execute` 메서드는 앞의 코드 예제에서 변경되었으며, 중단점이 발생하면 실행 스레드가 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="112cb-136">Notice that the `Execute` method has changed from the previous code sample, and the execution thread is paused when firing the breakpoint.</span></span>  
  
```csharp  
private ManualResetEvent m_suspended = new ManualResetEvent( true );  
private ManualResetEvent m_canExecute = new ManualResetEvent( true );  
private int   m_suspendRequired = 0;  
private int   m_debugMode = 0;  
  
public override DTSExecResult Execute( Connections connections, Variables variables, IDTSComponentEvents events, IDTSLogging log, DtsTransaction txn)  
{  
   // While a task is not executing, it is suspended.    
   // Now that we are executing,  
   // change to not suspended.  
   ChangeEvent(m_suspended, false);  
  
   // Check for a suspend before doing any work,   
   // in case the suspend and execute calls  
   // were initiated at virtually the same time.  
   CheckAndSuspend();  
   CheckAndFireBreakpoint( componentEvents, 1);  
}  
private void CheckAndSuspend()  
{  
   // Loop until we can execute.    
   // The loop is required rather than a simple If  
   // because there is a time between the return from WaitOne and the  
   // reset that we might receive another Suspend call.    
   // Suspend() will see that we are suspended  
   // and return.  So we need to rewait.  
   while (!m_canExecute.WaitOne(0, false))  
   {  
      ChangeEvent(m_suspended, true);  
      m_canExecute.WaitOne();  
      ChangeEvent(m_suspended, false);  
   }  
}  
private void CheckAndFireBreakpoint(IDTSComponentEvents events, int breakpointID)  
{  
   // If the breakpoint is enabled, fire it.  
   if (m_debugMode != 0 &&    this.bpm.IsBreakpointTargetEnabled(breakpointID))  
   {  
      //   Enter a suspend mode before firing the breakpoint.    
      //   Firing the breakpoint will cause the runtime   
      //   to call Suspend on this task.    
      //   Because we are blocked on the breakpoint,   
      //   we are suspended.  
      ChangeEvent(m_suspended, true);  
      events.OnBreakpointHit(this.bpm.GetBreakpointTarget(breakpointID));  
      ChangeEvent(m_suspended, false);  
   }  
   // Check for a suspension for two reasons:   
   //   1. If we are at a point where we could fire a breakpoint,   
   //      we are at a valid suspend point.  Even if we didn't hit a  
   //      breakpoint, the runtime may have called suspend,   
   //      so check for it.       
   //   2. Between the return from OnBreakpointHit   
   //      and the reset of the event, it is possible to have  
   //      received a suspend call from which we returned because   
   //      we were already suspended.  We need to be sure it is okay  
   //      to continue executing now.  
   CheckAndSuspend();  
}  
static void ChangeEvent(ManualResetEvent e, bool shouldSet)  
{  
   bool succeeded;  
   if (shouldSet)  
      succeeded = e.Set();  
   else  
      succeeded = e.Reset();  
  
   if (!succeeded)  
      throw new Exception("Synchronization object failed.");  
  
}  
public bool SuspendRequired  
{  
   get   {return m_suspendRequired != 0;}  
   set  
   {  
      // This lock is also taken by Suspend().    
      // Because it is possible for the package to be  
      // suspended and resumed in quick succession,   
      // this property might be set before  
      // the actual Suspend() call.    
      // Without the lock, the Suspend() might reset the canExecute  
      // event after we set it to abort the suspension.  
      lock (this)  
      {  
         Interlocked.Exchange(ref m_suspendRequired, value ? 1 : 0);  
         if (!value)  
            ResumeExecution();  
      }  
   }  
}  
public void ResumeExecution()  
{  
   ChangeEvent( m_canExecute,true );  
}  
public void Suspend()  
{  
   // This lock is also taken by the set SuspendRequired method.    
   // It prevents this call from overriding an   
   // aborted suspension.  See comments in set SuspendRequired.  
   lock (this)  
   {  
      // If a Suspend is required, do it.  
      if (m_suspendRequired != 0)  
         ChangeEvent(m_canExecute, false);  
   }  
   // We can't return from Suspend until the task is "suspended".  
   // This can happen one of two ways:   
   // the m_suspended event occurs, indicating that the execute thread  
   // has suspended, or the canExecute flag is set,   
   // indicating that a suspend is no longer required.  
   WaitHandle [] suspendOperationComplete = {m_suspended, m_canExecute};  
   WaitHandle.WaitAny(suspendOperationComplete);  
}  
```  
  
```vb  
Private m_suspended As ManualResetEvent = New ManualResetEvent(True)  
Private m_canExecute As ManualResetEvent = New ManualResetEvent(True)  
Private m_suspendRequired As Integer = 0  
Private m_debugMode As Integer = 0  
  
Public Overrides Function Execute(ByVal connections As Connections, _  
ByVal variables As Variables, ByVal events As IDTSComponentEvents, _  
ByVal log As IDTSLogging, ByVal txn As DtsTransaction) As DTSExecResult  
  
   ' While a task is not executing it is suspended.    
   ' Now that we are executing,  
   ' change to not suspended.  
   ChangeEvent(m_suspended, False)  
  
   ' Check for a suspend before doing any work,   
   ' in case the suspend and execute calls  
   ' were initiated at virtually the same time.  
   CheckAndSuspend()  
   CheckAndFireBreakpoint(componentEvents, 1)  
  
End Function  
  
Private Sub CheckAndSuspend()  
  
   ' Loop until we can execute.    
   ' The loop is required rather than a simple if  
   ' because there is a time between the return from WaitOne and the  
   ' reset that we might receive another Suspend call.    
   ' Suspend() will see that we are suspended  
   ' and return.  So we need to rewait.  
   Do While Not m_canExecute.WaitOne(0, False)  
              ChangeEvent(m_suspended, True)  
              m_canExecute.WaitOne()  
              ChangeEvent(m_suspended, False)  
   Loop  
  
End Sub  
  
Private Sub CheckAndFireBreakpoint(ByVal events As IDTSComponentEvents, _  
ByVal breakpointID As Integer)  
  
   ' If the breakpoint is enabled, fire it.  
   If m_debugMode <> 0 AndAlso Me.bpm.IsBreakpointTargetEnabled(breakpointID) Then  
              '   Enter a suspend mode before firing the breakpoint.    
              '   Firing the breakpoint will cause the runtime   
              '   to call Suspend on this task.    
              '   Because we are blocked on the breakpoint,   
              '   we are suspended.  
              ChangeEvent(m_suspended, True)  
              events.OnBreakpointHit(Me.bpm.GetBreakpointTarget(breakpointID))  
              ChangeEvent(m_suspended, False)  
   End If  
  
   ' Check for a suspension for two reasons:   
   '   1. If we are at a point where we could fire a breakpoint,   
   '         we are at a valid suspend point.  Even if we didn't hit a  
   '         breakpoint, the runtime may have called suspend,   
   '         so check for it.     
   '   2. Between the return from OnBreakpointHit   
   '         and the reset of the event, it is possible to have  
   '         received a suspend call from which we returned because   
   '         we were already suspended.  We need to be sure it is okay  
   '         to continue executing now.  
   CheckAndSuspend()  
  
End Sub  
  
Shared Sub ChangeEvent(ByVal e As ManualResetEvent, ByVal shouldSet As Boolean)  
  
   Dim succeeded As Boolean  
   If shouldSet Then  
              succeeded = e.Set()  
   Else  
              succeeded = e.Reset()  
   End If  
  
   If (Not succeeded) Then  
              Throw New Exception("Synchronization object failed.")  
   End If  
  
End Sub  
  
Public Property SuspendRequired() As Boolean  
   Get  
               Return m_suspendRequired <> 0  
  End Get  
  Set  
    ' This lock is also taken by Suspend().    
     '   Because it is possible for the package to be  
     '   suspended and resumed in quick succession,   
     '   this property might be set before  
     '   the actual Suspend() call.    
     '   Without the lock, the Suspend() might reset the canExecute  
     '   event after we set it to abort the suspension.  
              SyncLock Me  
                         Interlocked.Exchange(m_suspendRequired,IIf(Value, 1, 0))  
                         If (Not Value) Then  
                                    ResumeExecution()  
                         End If  
              End SyncLock  
   End Set  
End Property  
  
Public Sub ResumeExecution()  
   ChangeEvent(m_canExecute,True)  
End Sub  
  
Public Sub Suspend()  
  
   ' This lock is also taken by the set SuspendRequired method.    
   ' It prevents this call from overriding an   
   ' aborted suspension.  See comments in set SuspendRequired.  
   SyncLock Me  
   ' If a Suspend is required, do it.  
              If m_suspendRequired <> 0 Then  
                         ChangeEvent(m_canExecute, False)  
              End If  
   End SyncLock  
   ' We can't return from Suspend until the task is "suspended".  
   ' This can happen one of two ways:   
   ' the m_suspended event occurs, indicating that the execute thread  
   ' has suspended, or the canExecute flag is set,   
   ' indicating that a suspend is no longer required.  
   Dim suspendOperationComplete As WaitHandle() = {m_suspended, m_canExecute}  
   WaitHandle.WaitAny(suspendOperationComplete)  
  
End Sub  
```  
  
<span data-ttu-id="112cb-137">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="112cb-137">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="112cb-138">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="112cb-138">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="112cb-139">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="112cb-139">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="112cb-140">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="112cb-140">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="112cb-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112cb-141">See Also</span></span>  
 [<span data-ttu-id="112cb-142">제어 흐름 디버깅</span><span class="sxs-lookup"><span data-stu-id="112cb-142">Debugging Control Flow</span></span>](../../troubleshooting/debugging-control-flow.md)  
  
  
