---
title: '샘플: 서버 이벤트 용 WMI 공급자를 사용 하 여 SQL Server 에이전트 경고 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- SQL Server Agent [WMI]
- WMI Provider for Server Events, samples
- sample applications [WMI]
ms.assetid: d44811c7-cd46-4017-b284-c863ca088e8f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f23a3a8738435dc6a27a230f4521300a3ee2470f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733683"
---
# <a name="sample-creating-a-sql-server-agent-alert-by-using-the-wmi-provider-for-server-events"></a><span data-ttu-id="f7ba6-102">예제: 서버 이벤트용 WMI 공급자를 사용하여 SQL Server 에이전트 경고 만들기</span><span class="sxs-lookup"><span data-stu-id="f7ba6-102">Sample: Creating a SQL Server Agent Alert by Using the WMI Provider for Server Events</span></span>
  <span data-ttu-id="f7ba6-103">WMI 이벤트 공급자를 사용하는 일반적인 방법 중 하나는 특정 이벤트에 응답하는 SQL Server 에이전트 경고를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-103">One common way to use the WMI Event Provider is to create SQL Server Agent alerts that respond to specific events.</span></span> <span data-ttu-id="f7ba6-104">다음 예제에서는 XML 교착 상태 그래프 이벤트를 나중에 분석할 수 있도록 테이블에 저장하는 간단한 경고를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-104">The following sample presents a simple alert that saves XML deadlock graph events in a table for later analysis.</span></span> <span data-ttu-id="f7ba6-105">SQL Server 에이전트는 WQL 요청을 전송하고 WMI 이벤트를 수신하고 이벤트에 대한 응답으로 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-105">SQL Server Agent submits a WQL request, receives WMI events, and runs a job in response to the event.</span></span> <span data-ttu-id="f7ba6-106">알림 메시지 처리와 관련된 Service Broker 개체가 여러 개 있지만 WMI 이벤트 공급자가 이러한 개체의 생성 및 관리 세부 정보를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-106">Notice that, although several Service Broker objects are involved in processing the notification message, the WMI Event Provider handles the details of creating and managing these objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7ba6-107">예제</span><span class="sxs-lookup"><span data-stu-id="f7ba6-107">Example</span></span>  
 <span data-ttu-id="f7ba6-108">먼저 교착 상태 그래프 이벤트를 저장할 `AdventureWorks` 데이터베이스에 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-108">First, a table is created in the `AdventureWorks` database to hold the deadlock graph event.</span></span> <span data-ttu-id="f7ba6-109">테이블에는 두 개의 열이 포함 되어 있습니다. `AlertTime` 열은 경고가 실행 되는 시간을 보유 하 고 `DeadlockGraph` 열은 교착 상태 그래프가 포함 된 XML 문서를 보유 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-109">The table contains two columns: The `AlertTime` column holds the time that the alert runs, and the `DeadlockGraph` column holds the XML document that contains the deadlock graph.</span></span>  
  
 <span data-ttu-id="f7ba6-110">그런 다음 경고를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-110">Then, the alert is created.</span></span> <span data-ttu-id="f7ba6-111">스크립트에서는 경고에서 실행할 작업을 만들어 작업에 작업 단계를 추가하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 현재 인스턴스를 작업의 대상으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-111">The script first creates the job that the alert will run, adds a job step to the job, and targets the job to the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f7ba6-112">그런 후 스크립트에서는 경고를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-112">The script then creates the alert.</span></span>  
  
 <span data-ttu-id="f7ba6-113">작업 단계는 WMI 이벤트 인스턴스의 **TextData** 속성을 검색 하 고 해당 값을 **DeadlockEvents** 테이블의 **DeadlockGraph** 열에 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-113">The job step retrieves the **TextData** property of the WMI event instance and inserts that value into the **DeadlockGraph** column of the **DeadlockEvents** table.</span></span> <span data-ttu-id="f7ba6-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 문자열을 XML 형식으로 암시적으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-114">Notice that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implicitly converts the string into XML format.</span></span> <span data-ttu-id="f7ba6-115">작업 단계에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 하위 시스템을 사용하기 때문에 프록시가 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-115">Because the job step uses the [!INCLUDE[tsql](../../includes/tsql-md.md)] subsystem, the job step does not specify a proxy.</span></span>  
  
 <span data-ttu-id="f7ba6-116">경고는 교착 상태 그래프 추적 이벤트가 로깅될 때마다 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-116">The alert runs the job whenever a deadlock graph trace event would be logged.</span></span> <span data-ttu-id="f7ba6-117">WMI 경고에 대해 SQL Server 에이전트는 지정된 네임스페이스와 WQL 문을 사용하여 알림 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-117">For a WMI alert, SQL Server Agent creates a notification query using the namespace and WQL statement specified.</span></span> <span data-ttu-id="f7ba6-118">이 경고에 대해 SQL Server 에이전트는 로컬 컴퓨터에서 기본 인스턴스를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-118">For this alert, SQL Server Agent monitors the default instance on the local computer.</span></span> <span data-ttu-id="f7ba6-119">WQL 문은 기본 인스턴스에서 모든 `DEADLOCK_GRAPH` 이벤트를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-119">The WQL statement requests any `DEADLOCK_GRAPH` event in the default instance.</span></span> <span data-ttu-id="f7ba6-120">경고에서 모니터링하는 대상 인스턴스를 변경하려면 경고의 `MSSQLSERVER`에서 `@wmi_namespace`의 인스턴스 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-120">To change the instance that the alert monitors, substitute the instance name for `MSSQLSERVER` in the `@wmi_namespace` for the alert.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7ba6-121">WMI 이벤트를 수신 하는 SQL Server 에이전트은 [!INCLUDE[ssSB](../../includes/sssb-md.md)] **msdb** 및에서 사용 하도록 설정 해야 합니다 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f7ba6-121">For SQL Server Agent to receive WMI events, [!INCLUDE[ssSB](../../includes/sssb-md.md)] must be enabled in **msdb** and [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
IF OBJECT_ID('DeadlockEvents', 'U') IS NOT NULL  
BEGIN  
    DROP TABLE DeadlockEvents ;  
END ;  
GO  
  
CREATE TABLE DeadlockEvents  
    (AlertTime DATETIME, DeadlockGraph XML) ;  
GO  
-- Add a job for the alert to run.  
  
EXEC  msdb.dbo.sp_add_job @job_name=N'Capture Deadlock Graph',   
    @enabled=1,   
    @description=N'Job for responding to DEADLOCK_GRAPH events' ;  
GO  
  
-- Add a jobstep that inserts the current time and the deadlock graph into  
-- the DeadlockEvents table.  
  
EXEC msdb.dbo.sp_add_jobstep  
    @job_name = N'Capture Deadlock Graph',  
    @step_name=N'Insert graph into LogEvents',  
    @step_id=1,   
    @on_success_action=1,   
    @on_fail_action=2,   
    @subsystem=N'TSQL',   
    @command= N'INSERT INTO DeadlockEvents  
                (AlertTime, DeadlockGraph)  
                VALUES (getdate(), N''$(ESCAPE_SQUOTE(WMI(TextData)))'')',  
    @database_name=N'AdventureWorks' ;  
GO  
  
-- Set the job server for the job to the current instance of SQL Server.  
  
EXEC msdb.dbo.sp_add_jobserver @job_name = N'Capture Deadlock Graph' ;  
GO  
  
-- Add an alert that responds to all DEADLOCK_GRAPH events for  
-- the default instance. To monitor deadlocks for a different instance,  
-- change MSSQLSERVER to the name of the instance.  
  
EXEC msdb.dbo.sp_add_alert @name=N'Respond to DEADLOCK_GRAPH',   
@wmi_namespace=N'\\.\root\Microsoft\SqlServer\ServerEvents\MSSQLSERVER',   
    @wmi_query=N'SELECT * FROM DEADLOCK_GRAPH',   
    @job_name='Capture Deadlock Graph' ;  
GO  
```  
  
## <a name="testing-the-sample"></a><span data-ttu-id="f7ba6-122">예제 테스트</span><span class="sxs-lookup"><span data-stu-id="f7ba6-122">Testing the Sample</span></span>  
 <span data-ttu-id="f7ba6-123">작업이 실행되는 것을 확인하려면 교착 상태를 발생시켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-123">To see the job run, provoke a deadlock.</span></span> <span data-ttu-id="f7ba6-124">에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 두 개의 **SQL 쿼리** 탭을 열고 두 쿼리를 모두 동일한 인스턴스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-124">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open two **SQL Query** tabs and connect both queries to the same instance.</span></span> <span data-ttu-id="f7ba6-125">쿼리 탭 중 하나에서 다음 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-125">Run the following script in one of the query tabs.</span></span> <span data-ttu-id="f7ba6-126">이 스크립트는 하나의 결과 집합을 생성한 후 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-126">This script produces one result set and finishes.</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
BEGIN TRANSACTION ;  
GO  
  
SELECT TOP(1) Name FROM Production.Product WITH (XLOCK) ;  
GO  
```  
  
 <span data-ttu-id="f7ba6-127">두 번째 쿼리 탭에서 다음 스크립트를 실행 합니다. 이 스크립트는 하나의 결과 집합을 생성 한 다음 잠금을 획득 하기 위해 대기 하는 블록을 생성 `Production.Product` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-127">Run the following script in the second query tab. This script produces one result set and then blocks, waiting to acquire a lock on `Production.Product`.</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
BEGIN TRANSACTION ;  
GO  
  
SELECT TOP(1) Name FROM Production.Location WITH (XLOCK) ;  
GO  
  
SELECT TOP(1) Name FROM Production.Product WITH (XLOCK) ;  
GO  
```  
  
 <span data-ttu-id="f7ba6-128">첫 번째 쿼리 탭에서 다음 스크립트를 실행 합니다. 이 스크립트는 잠금을 획득 하려고 대기 하는를 차단 `Production.Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-128">Run the following script in the first query tab. This script blocks, waiting to acquire a lock on `Production.Location`.</span></span> <span data-ttu-id="f7ba6-129">지정된 제한 시간이 초과되면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 이 스크립트나 예제의 스크립트를 교착 상태로 처리한 후 트랜잭션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-129">After a short time-out, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will choose either this script or the script in the sample as the deadlock victim and end the transaction.</span></span>  
  
```  
SELECT TOP(1) Name FROM Production.Location WITH (XLOCK) ;  
GO  
```  
  
 <span data-ttu-id="f7ba6-130">교착 상태를 발생시킨 후 SQL Server 에이전트가 경고를 활성화하고 작업을 실행할 때까지 잠시 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-130">After provoking the deadlock, wait several moments for SQL Server Agent to activate the alert and run the job.</span></span> <span data-ttu-id="f7ba6-131">다음 스크립트를 실행하여 `DeadlockEvents` 테이블의 내용을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-131">Examine the contents of the `DeadlockEvents` table by running the following script:</span></span>  
  
```  
SELECT * FROM DeadlockEvents ;  
GO  
```  
  
 <span data-ttu-id="f7ba6-132">`DeadlockGraph` 열에는 교착 상태 그래프 이벤트의 모든 속성을 보여 주는 XML 문서가 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba6-132">The `DeadlockGraph` column should contain an XML document that shows all the properties of the deadlock graph event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7ba6-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7ba6-133">See Also</span></span>  
 [<span data-ttu-id="f7ba6-134">서버 이벤트용 WMI 공급자 개념</span><span class="sxs-lookup"><span data-stu-id="f7ba6-134">WMI Provider for Server Events Concepts</span></span>](wmi-provider-for-server-events-concepts.md)  
  
  
