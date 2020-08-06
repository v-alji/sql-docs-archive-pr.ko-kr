---
title: SQL Server 에이전트에서 자동 관리 작업 예약 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- scheduling administrative tasks [SMO]
- SQL Server Agent [SMO]
- automatic administrative SMO tasks
ms.assetid: 900242ad-d6a2-48e9-8a1b-f0eea4413c16
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a7620935a257a4200999cce27ba901588839b16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659907"
---
# <a name="scheduling-automatic-administrative-tasks-in-sql-server-agent"></a><span data-ttu-id="3aedf-102">SQL Server 에이전트에서 자동 관리 태스크 예약</span><span class="sxs-lookup"><span data-stu-id="3aedf-102">Scheduling Automatic Administrative Tasks in SQL Server Agent</span></span>
  <span data-ttu-id="3aedf-103">SMO에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트는 다음 개체로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-103">In SMO, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is represented by the following objects:</span></span>  
  
-   <span data-ttu-id="3aedf-104"><xref:Microsoft.SqlServer.Management.Smo.Agent.JobServer> 개체에는 작업, 경고, 운영자의 세 가지 컬렉션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-104">The <xref:Microsoft.SqlServer.Management.Smo.Agent.JobServer> object has three collections of jobs, alerts and operators.</span></span>  
  
-   <span data-ttu-id="3aedf-105"><xref:Microsoft.SqlServer.Management.Smo.Agent.OperatorCollection> 개체는 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트로부터 자동으로 이벤트 알림을 받을 수 있는 호출기, 전자 메일 주소 및 net send 운영자 목록을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-105">The <xref:Microsoft.SqlServer.Management.Smo.Agent.OperatorCollection> object represents a list of pager, e-mail addresses and net send operators that can be notified of events automatically by the Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
-   <span data-ttu-id="3aedf-106"><xref:Microsoft.SqlServer.Management.Smo.Agent.AlertCollection> 개체는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 모니터링되는 시스템 이벤트나 성능 조건과 같은 상황 목록을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-106">The <xref:Microsoft.SqlServer.Management.Smo.Agent.AlertCollection> object represents a list of circumstances such as system events or performance conditions that are monitored by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="3aedf-107"><xref:Microsoft.SqlServer.Management.Smo.Agent.JobCollection> 개체는 약간 더 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-107">The <xref:Microsoft.SqlServer.Management.Smo.Agent.JobCollection> object is slightly more complex.</span></span> <span data-ttu-id="3aedf-108">이 개체는 지정된 일정에서 실행되는 다단계 태스크 목록을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-108">It represents a list of multi-step tasks that run at specified schedules.</span></span> <span data-ttu-id="3aedf-109">단계 및 일정 정보는 <xref:Microsoft.SqlServer.Management.Smo.Agent.JobStep> 및 <xref:Microsoft.SqlServer.Management.Smo.Agent.JobSchedule> 개체에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-109">The steps and schedule information are stored in the <xref:Microsoft.SqlServer.Management.Smo.Agent.JobStep> and <xref:Microsoft.SqlServer.Management.Smo.Agent.JobSchedule> objects.</span></span>  
  
 <span data-ttu-id="3aedf-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트 개체는 <xref:Microsoft.SqlServer.Management.Smo.Agent> 네임스페이스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-110">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent objects are in the <xref:Microsoft.SqlServer.Management.Smo.Agent> namespace.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3aedf-111">예</span><span class="sxs-lookup"><span data-stu-id="3aedf-111">Examples</span></span>  
 <span data-ttu-id="3aedf-112">제공된 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-112">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="3aedf-113">자세한 내용은 visual [studio .net에서 VISUAL BASIC SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 또는 [visual Studio .Net에서 VISUAL C&#35; smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3aedf-113">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
1.  <span data-ttu-id="3aedf-114">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트를 사용하는 프로그램에 대해 에이전트 네임스페이스를 한정하는 `Imports` 문을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-114">For programs that use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent, you must include the `Imports` statement to qualify the Agent namespace.</span></span> <span data-ttu-id="3aedf-115">다음과 같이 애플리케이션의 선언 앞에, 다른 `Imports` 문 끝에 구문을 삽입하십시오.</span><span class="sxs-lookup"><span data-stu-id="3aedf-115">Insert the statement after the other `Imports` statements, before any declarations in the application, such as:</span></span>  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Agent`  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-visual-basic"></a><span data-ttu-id="3aedf-116">Visual Basic에서 단계와 일정이 포함된 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="3aedf-116">Creating a Job with Steps and a Schedule in Visual Basic</span></span>  
 <span data-ttu-id="3aedf-117">이 코드 예제는 단계와 일정이 포함된 작업을 만든 다음 운영자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-117">This code example creates a job with steps and a schedule, and then informs an operator.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent1](SMO How to#SMO_VBAgent1)]  -->  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-visual-c"></a><span data-ttu-id="3aedf-118">Visual C#에서 단계와 일정이 포함된 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="3aedf-118">Creating a Job with Steps and a Schedule in Visual C#</span></span>  
 <span data-ttu-id="3aedf-119">이 코드 예제는 단계와 일정이 포함된 작업을 만든 다음 운영자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-119">This code example creates a job with steps and a schedule, and then informs an operator.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.  
            Server srv = new Server();  
  
            //Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.   
            Operator op = new Operator(srv.JobServer, "Test_Operator");  
  
            //Set the Net send address.   
            op.NetSendAddress = "Network1_PC";  
  
            //Create the operator on the instance of SQL Server Agent.   
            op.Create();  
  
            //Define a Job object variable by supplying the Agent and the name arguments in the constructor and setting properties.   
            Job jb = new Job(srv.JobServer, "Test_Job");  
  
            //Specify which operator to inform and the completion action.   
            jb.OperatorToNetSend = "Test_Operator";  
            jb.NetSendLevel = CompletionAction.Always;  
  
            //Create the job on the instance of SQL Server Agent.   
            jb.Create();  
  
            //Define a JobStep object variable by supplying the parent job and name arguments in the constructor.   
            JobStep jbstp = new JobStep(jb, "Test_Job_Step");  
            jbstp.Command = "Test_StoredProc";  
            jbstp.OnSuccessAction = StepCompletionAction.QuitWithSuccess;  
            jbstp.OnFailAction = StepCompletionAction.QuitWithFailure;  
  
            //Create the job step on the instance of SQL Agent.   
            jbstp.Create();  
  
            //Define a JobSchedule object variable by supplying the parent job and name arguments in the constructor.   
  
            JobSchedule jbsch = new JobSchedule(jb, "Test_Job_Schedule");  
  
            //Set properties to define the schedule frequency, and duration.   
            jbsch.FrequencyTypes = FrequencyTypes.Daily;  
            jbsch.FrequencySubDayTypes = FrequencySubDayTypes.Minute;  
            jbsch.FrequencySubDayInterval = 30;  
            TimeSpan ts1 = new TimeSpan(9, 0, 0);  
            jbsch.ActiveStartTimeOfDay = ts1;  
  
            TimeSpan ts2 = new TimeSpan(17, 0, 0);  
            jbsch.ActiveEndTimeOfDay = ts2;  
            jbsch.FrequencyInterval = 1;  
  
            System.DateTime d = new System.DateTime(2003, 1, 1);  
            jbsch.ActiveStartDate = d;  
  
            //Create the job schedule on the instance of SQL Agent.   
            jbsch.Create();  
        }  
```  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-powershell"></a><span data-ttu-id="3aedf-120">PowerShell에서 단계와 일정이 포함된 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="3aedf-120">Creating a Job with Steps and a Schedule in PowerShell</span></span>  
 <span data-ttu-id="3aedf-121">이 코드 예제는 단계와 일정이 포함된 작업을 만든 다음 운영자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-121">This code example creates a job with steps and a schedule, and then informs an operator.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.  
$op = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Operator -argumentlist $srv.JobServer, "Test_Operator"  
  
#Set the Net send address.  
$op.NetSendAddress = "Network1_PC"  
  
#Create the operator on the instance of SQL Agent.  
$op.Create()  
  
#Define a Job object variable by supplying the Agent and the name arguments in the constructor and setting properties.   
$jb = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Job -argumentlist $srv.JobServer, "Test_Job"   
  
#Specify which operator to inform and the completion action.   
$jb.OperatorToNetSend = "Test_Operator";   
$jb.NetSendLevel = [Microsoft.SqlServer.Management.SMO.Agent.CompletionAction]::Always  
  
#Create the job on the instance of SQL Server Agent.   
$jb.Create()  
  
#Define a JobStep object variable by supplying the parent job and name arguments in the constructor.   
$jbstp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.JobStep -argumentlist $jb, "Test_Job_Step"   
$jbstp.Command = "Test_StoredProc";   
$jbstp.OnSuccessAction = [Microsoft.SqlServer.Management.SMO.Agent.StepCompletionAction]::QuitWithSuccess;   
$jbstp.OnFailAction =[Microsoft.SqlServer.Management.SMO.Agent.StepCompletionAction]::QuitWithFailure;   
  
#Create the job step on the instance of SQL Agent.   
$jbstp.Create();   
  
#Define a JobSchedule object variable by supplying the parent job and name arguments in the constructor.   
$jbsch = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.JobSchedule -argumentlist $jb, "Test_Job_Schedule"   
  
#Set properties to define the schedule frequency, and duration.   
$jbsch.FrequencyTypes =  [Microsoft.SqlServer.Management.SMO.Agent.FrequencyTypes]::Daily  
  
$jbsch.FrequencySubDayTypes = [Microsoft.SqlServer.Management.SMO.Agent.FrequencySubDayTypes]::Minute  
$jbsch.FrequencySubDayInterval = 30  
$ts1 =  New-Object -TypeName TimeSpan -argumentlist 9, 0, 0  
$jbsch.ActiveStartTimeOfDay = $ts1  
$ts2 = New-Object -TypeName TimeSpan -argumentlist 17, 0, 0  
$jbsch.ActiveEndTimeOfDay = $ts2  
$jbsch.FrequencyInterval = 1  
$jbsch.ActiveStartDate = "01/01/2003"  
  
#Create the job schedule on the instance of SQL Agent.   
$jbsch.Create();  
```  
  
## <a name="creating-an-alert-in-visual-basic"></a><span data-ttu-id="3aedf-122">Visual Basic에서 경고 만들기</span><span class="sxs-lookup"><span data-stu-id="3aedf-122">Creating an Alert in Visual Basic</span></span>  
 <span data-ttu-id="3aedf-123">이 코드 예제는 성능 조건에 따라 트리거되는 경고를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-123">This code example creates an alert that is triggered by a performance condition.</span></span> <span data-ttu-id="3aedf-124">다음과 같은 특정 형식으로 조건을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-124">The condition must be provided in a specific format:</span></span>  
  
 <span data-ttu-id="3aedf-125">**ObjectName | CounterName | 인스턴스 | ComparisionOp | CompValue**</span><span class="sxs-lookup"><span data-stu-id="3aedf-125">**ObjectName|CounterName|Instance|ComparisionOp|CompValue**</span></span>  
  
 <span data-ttu-id="3aedf-126">경고 알림을 위해 운영자가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-126">An operator is required for the alert notification.</span></span> <span data-ttu-id="3aedf-127">`operator`가 Visual Basic 키워드이므로 <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> 형식을 대괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-127">The <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> type requires square parentheses because `operator` is a Visual Basic keyword.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent3](SMO How to#SMO_VBAgent3)]  -->  
  
## <a name="creating-an-alert-in-visual-c"></a><span data-ttu-id="3aedf-128">Visual C#에서 경고 만들기</span><span class="sxs-lookup"><span data-stu-id="3aedf-128">Creating an Alert in Visual C#</span></span>  
 <span data-ttu-id="3aedf-129">이 코드 예제는 성능 조건에 따라 트리거되는 경고를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-129">This code example creates an alert that is triggered by a performance condition.</span></span> <span data-ttu-id="3aedf-130">다음과 같은 특정 형식으로 조건을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-130">The condition must be provided in a specific format:</span></span>  
  
 <span data-ttu-id="3aedf-131">**ObjectName | CounterName | 인스턴스 | ComparisionOp | CompValue**</span><span class="sxs-lookup"><span data-stu-id="3aedf-131">**ObjectName|CounterName|Instance|ComparisionOp|CompValue**</span></span>  
  
 <span data-ttu-id="3aedf-132">경고 알림을 위해 운영자가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-132">An operator is required for the alert notification.</span></span> <span data-ttu-id="3aedf-133">`operator`가 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] 키워드이므로 <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> 형식을 대괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-133">The <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> type requires square parentheses because `operator` is a [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] keyword.</span></span>  
  
```csharp
{  
             //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
  
            //Define an Alert object variable by supplying the SQL Server Agent and the name arguments in the constructor.   
            Alert al = new Alert(srv.JobServer, "Test_Alert");  
  
            //Specify the performance condition string to define the alert.   
            al.PerformanceCondition = "SQLServer:General Statistics|User Connections||>|3";  
  
            //Create the alert on the SQL Agent.   
            al.Create();  
  
            //Define an Operator object variable by supplying the SQL Server Agent and the name arguments in the constructor.   
  
            Operator op = new Operator(srv.JobServer, "Test_Operator");  
            //Set the net send address.   
            op.NetSendAddress = "NetworkPC";  
            //Create the operator on the SQL Agent.   
            op.Create();  
            //Run the AddNotification method to specify the operator is notified when the alert is raised.   
            al.AddNotification("Test_Operator", NotifyMethods.NetSend);  
        }  
```  
  
## <a name="creating-an-alert-in-powershell"></a><span data-ttu-id="3aedf-134">PowerShell에서 경고 만들기</span><span class="sxs-lookup"><span data-stu-id="3aedf-134">Creating an Alert in PowerShell</span></span>  
 <span data-ttu-id="3aedf-135">이 코드 예제는 성능 조건에 따라 트리거되는 경고를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-135">This code example creates an alert that is triggered by a performance condition.</span></span> <span data-ttu-id="3aedf-136">다음과 같은 특정 형식으로 조건을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-136">The condition must be provided in a specific format:</span></span>  
  
 <span data-ttu-id="3aedf-137">**ObjectName | CounterName | 인스턴스 | ComparisionOp | CompValue**</span><span class="sxs-lookup"><span data-stu-id="3aedf-137">**ObjectName|CounterName|Instance|ComparisionOp|CompValue**</span></span>  
  
 <span data-ttu-id="3aedf-138">경고 알림을 위해 운영자가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-138">An operator is required for the alert notification.</span></span> <span data-ttu-id="3aedf-139">`operator`가 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] 키워드이므로 <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> 형식을 대괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-139">The <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> type requires square parentheses because `operator` is a [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] keyword.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define an Alert object variable by supplying the SQL Agent and the name arguments in the constructor.  
$al = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Alert -argumentlist $srv.JobServer, "Test_Alert"  
  
#Specify the performance condition string to define the alert.  
$al.PerformanceCondition = "SQLServer:General Statistics|User Connections||>|3"  
  
#Create the alert on the SQL Agent.  
$al.Create()  
  
#Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.  
$op = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Operator -argumentlist $srv.JobServer, "Test_Operator"  
  
#Set the Net send address.  
$op.NetSendAddress = "Network1_PC"  
  
#Create the operator on the instance of SQL Agent.  
$op.Create()  
  
#Run the AddNotification method to specify the operator is notified when the alert is raised.  
$ns = [Microsoft.SqlServer.Management.SMO.Agent.NotifyMethods]::NetSend  
$al.AddNotification("Test_Operator", $ns)  
  
#Drop the alert and the operator  
$al.Drop()  
$op.Drop()  
```  
  
## <a name="allowing-user-access-to-subsystem-by-using-a-proxy-account-in-visual-basic"></a><span data-ttu-id="3aedf-140">Visual Basic에서 프록시 계정을 사용하여 하위 시스템에 사용자 액세스 허용</span><span class="sxs-lookup"><span data-stu-id="3aedf-140">Allowing User Access to Subsystem by Using a Proxy Account in Visual Basic</span></span>  
 <span data-ttu-id="3aedf-141">이 코드 예제는 <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> 개체의 <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount> 메서드를 사용하여 지정된 하위 시스템에 사용자 액세스를 허용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-141">This code example shows how to allow a user access to a specified subsystem by using the <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount> object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent2](SMO How to#SMO_VBAgent2)]  -->  
  
## <a name="allowing-user-access-to-subsystem-by-using-a-proxy-account-in-visual-c"></a><span data-ttu-id="3aedf-142">Visual C#에서 프록시 계정을 사용하여 하위 시스템에 사용자 액세스 허용</span><span class="sxs-lookup"><span data-stu-id="3aedf-142">Allowing User Access to Subsystem by Using a Proxy Account in Visual C#</span></span>  
 <span data-ttu-id="3aedf-143">이 코드 예제는 <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> 개체의 <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount> 메서드를 사용하여 지정된 하위 시스템에 사용자 액세스를 허용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-143">This code example shows how to allow a user access to a specified subsystem by using the <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount> object.</span></span>  
  
```csharp
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Declare a JobServer object variable and reference the SQL Server Agent.   
JobServer js = default(JobServer);   
js = srv.JobServer;   
//Define a Credential object variable by supplying the parent server and name arguments in the constructor.   
Credential c = default(Credential);   
c = new Credential(srv, "Proxy_accnt");   
//Set the identity to a valid login represented by the vIdentity string variable.   
//The sub system will run under this login.   
c.Identity = vIdentity;   
//Create the credential on the instance of SQL Server.   
c.Create();   
//Define a ProxyAccount object variable by supplying the SQL Server Agent, the name, the credential, the description arguments in the constructor.   
ProxyAccount pa = default(ProxyAccount);   
pa = new ProxyAccount(js, "Test_proxy", "Proxy_accnt", true, "Proxy account for users to run job steps in command shell.");   
//Create the proxy account on the SQL Agent.   
pa.Create();   
//Add the login, represented by the vLogin string variable, to the proxy account.   
pa.AddLogin(vLogin);   
//Add the CmdExec subsytem to the proxy account.   
pa.AddSubSystem(AgentSubSystem.CmdExec);   
}   
//Now users logged on as vLogin can run CmdExec job steps with the specified credentials.   
```  
  
## <a name="see-also"></a><span data-ttu-id="3aedf-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3aedf-144">See Also</span></span>  
 <span data-ttu-id="3aedf-145">[SQL Server 에이전트](../../../ssms/agent/sql-server-agent.md) </span><span class="sxs-lookup"><span data-stu-id="3aedf-145">[SQL Server Agent](../../../ssms/agent/sql-server-agent.md) </span></span>  
 [<span data-ttu-id="3aedf-146">작업 구현</span><span class="sxs-lookup"><span data-stu-id="3aedf-146">Implement Jobs</span></span>](../../../ssms/agent/implement-jobs.md)  
