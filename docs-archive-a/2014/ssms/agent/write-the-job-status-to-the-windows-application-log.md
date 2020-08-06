---
title: Windows 애플리케이션 로그에 작업 상태 쓰기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- status information [SQL Server], jobs
- SQL Server Agent jobs, status
- writing job status to log
- jobs [SQL Server Agent], status
- logs [SQL Server], jobs
ms.assetid: 3b813702-8f61-40ec-bf3b-ce9deb7e68be
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67bdd7948d1722e49976d5e48b571c684431cd1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734883"
---
# <a name="write-the-job-status-to-the-windows-application-log"></a><span data-ttu-id="93d2e-102">Windows 애플리케이션 로그에 작업 상태 쓰기</span><span class="sxs-lookup"><span data-stu-id="93d2e-102">Write the Job Status to the Windows Application Log</span></span>
  <span data-ttu-id="93d2e-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , 또는 SQL Server 관리 개체를 사용 하 여 Windows 응용 프로그램 이벤트 로그에 작업 상태를 쓰도록에서 에이전트를 구성 하는 방법에 대해 설명 합니다 [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="93d2e-103">This topic describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to write job status to the Windows application event log by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="93d2e-104">작업 응답은 데이터베이스 관리자에게 작업 완료 시점과 작업 실행 간격을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="93d2e-104">Job responses ensure that database administrators know when jobs complete and how frequently they run.</span></span> <span data-ttu-id="93d2e-105">일반적인 작업 응답은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="93d2e-105">Typical job responses include:</span></span>  
  
-   <span data-ttu-id="93d2e-106">전자 메일, 전자 호출 또는 **net send** 메시지 등으로 운영자에게 알림</span><span class="sxs-lookup"><span data-stu-id="93d2e-106">Notifying the operator by using e-mail, electronic paging, or a **net send** message.</span></span> <span data-ttu-id="93d2e-107">운영자가 추가 작업 동작을 실행해야 할 경우 이 작업 응답 중 하나를 사용.</span><span class="sxs-lookup"><span data-stu-id="93d2e-107">Use one of these job responses if the operator must perform a follow-up action.</span></span> <span data-ttu-id="93d2e-108">예를 들어 백업 작업이 성공적으로 완료될 경우 운영자는 백업 테이프를 빼낸 다음 안전한 곳에 저장하도록 알림을 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93d2e-108">For example, if a backup job completes successfully, the operator must be notified to remove the backup tape and store it in a safe location.</span></span>  
  
-   <span data-ttu-id="93d2e-109">이벤트 메시지를 Windows 애플리케이션 로그에 씀</span><span class="sxs-lookup"><span data-stu-id="93d2e-109">Writing an event message to the Windows application log.</span></span> <span data-ttu-id="93d2e-110">이 응답은 실패한 작업에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93d2e-110">You can use this response only for failed jobs.</span></span>  
  
-   <span data-ttu-id="93d2e-111">작업을 자동 삭제함</span><span class="sxs-lookup"><span data-stu-id="93d2e-111">Automatically deleting the job.</span></span> <span data-ttu-id="93d2e-112">이 작업을 반환할 필요가 없을 경우에는 이 작업 응답을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="93d2e-112">Use this job response if you are certain that you do not need to rerun this job.</span></span>  
  
 <span data-ttu-id="93d2e-113">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="93d2e-113">**In This Topic**</span></span>  
  
-   <span data-ttu-id="93d2e-114">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="93d2e-114">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="93d2e-115">보안</span><span class="sxs-lookup"><span data-stu-id="93d2e-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="93d2e-116">**Windows 애플리케이션 로그에 작업 상태를 쓰려면:**</span><span class="sxs-lookup"><span data-stu-id="93d2e-116">**To write the job status to the Windows application log, using:**</span></span>  
  
     [<span data-ttu-id="93d2e-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="93d2e-117">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="93d2e-118">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="93d2e-118">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="93d2e-119">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="93d2e-119">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="93d2e-120">보안</span><span class="sxs-lookup"><span data-stu-id="93d2e-120">Security</span></span>  
 <span data-ttu-id="93d2e-121">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93d2e-121">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="93d2e-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="93d2e-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-write-job-status-to-the-windows-application-log"></a><span data-ttu-id="93d2e-123">Windows 애플리케이션 로그에 작업 상태를 쓰려면</span><span class="sxs-lookup"><span data-stu-id="93d2e-123">To write job status to the Windows application log</span></span>  
  
1.  <span data-ttu-id="93d2e-124">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="93d2e-124">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="93d2e-125">**SQL Server 에이전트**, **작업**을 차례로 확장하고 편집할 작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93d2e-125">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to edit, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="93d2e-126">**알림** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="93d2e-126">Select the **Notifications** page.</span></span>  
  
4.  <span data-ttu-id="93d2e-127">**Windows 애플리케이션 이벤트 로그에 쓰기**를 선택하고 다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="93d2e-127">Check **Write to Windows application event log**, and choose one of the following:</span></span>  
  
    -   <span data-ttu-id="93d2e-128">작업이 성공적으로 완료되었을 때 작업 상태를 기록하려면**작업 성공 시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93d2e-128">Click**When the job succeeds**to log the job status when the job completes successfully.</span></span>  
  
    -   <span data-ttu-id="93d2e-129">작업이 성공적으로 완료되었을 때 작업 상태를 기록하려면**작업 실패 시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93d2e-129">Click**When the job fails**to log the job status when the job completes unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="93d2e-130">작업이 성공적으로 완료되었을 때 작업 상태를 기록하려면**작업 완료 시** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93d2e-130">Click**When the job completes** to log the job status regardless of completion status.</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="93d2e-131">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="93d2e-131">Using SQL Server Management Objects</span></span>  

### <a name="to-write-job-status-to-the-windows-application-log"></a><span data-ttu-id="93d2e-132">Windows 애플리케이션 로그에 작업 상태를 쓰려면</span><span class="sxs-lookup"><span data-stu-id="93d2e-132">To write job status to the Windows application log</span></span>
  
 <span data-ttu-id="93d2e-133">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `EventLogLevel` 클래스의 `Job` 속성을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="93d2e-133">Call the `EventLogLevel` property of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
  
 <span data-ttu-id="93d2e-134">다음 코드 예에서는 작업 실행이 끝날 때 운영 체제 이벤트 로그 항목을 생성하도록 작업을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="93d2e-134">The following code example sets the job to generate an operating system event log entry when the job execution finishes.</span></span>  
  
```powershell
$srv = new-object Microsoft.SqlServer.Management.Smo.Server("(local)")  
$jb = new-object Microsoft.SqlServer.Management.Smo.Agent.Job($srv.JobServer, "Test Job")  
$jb.EventLogLevel = [Microsoft.SqlServer.Management.Smo.Agent.CompletionAction]::Always  
```  
