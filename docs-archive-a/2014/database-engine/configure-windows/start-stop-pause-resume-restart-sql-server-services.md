---
title: 데이터베이스 엔진, SQL Server 에이전트 또는 SQL Server Browser 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, start and stop services
- stopping SQL Server Agent
- parameters [SQL Server], startup options
- SQL Server, startup options
- Database Engine [SQL Server], starting and stopping services
- pausing SQL Server
- PowerShell [SQL Server], starting and stopping services
- single-user mode [SQL Server], starting in
- SQL Server Management Studio [SQL Server], starting or stopping services
- stopping SQL Server Browser service
- starting SQL Server Agent
- default instances [SQL Server], starting and stopping
- SQL Server Agent, starting and stopping
- command prompt [SQL Server], starting and stopping SQL Server services
- continuing SQL Server
- starting SQL Server Database Engine
- net stop commands [SQL Server]
- command prompt [SQL Server], SQL Browser service
- Configuration Manager, start and stop services
- resuming SQL Server
- startup options [SQL Server]
- named instances [SQL Server], starting and stopping
- net start commands [SQL Server]
- SQL Server, starting and stopping
- stopping SQL Server
- starting SQL Server Browser service
- SQL Server Database Engine setting startup options
- administering SQL Server, starting and stopping services
- Management Studio [SQL Server], starting or stopping services
ms.assetid: 32660a02-e5a1-411a-9e57-7066ca459df6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f4b102c8fd81923d7386c8e556896e715311a07e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738697"
---
# <a name="start-stop-pause-resume-restart-the-database-engine-sql-server-agent-or-sql-server-browser-service"></a><span data-ttu-id="a9119-102">데이터베이스 엔진, SQL Server 에이전트 또는 SQL Server Browser 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작</span><span class="sxs-lookup"><span data-stu-id="a9119-102">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>
  <span data-ttu-id="a9119-103">이 항목에서는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , 명령 프롬프트에서 **net** 명령, 또는 PowerShell을 사용 하 여, 에이전트 또는 Browser 서비스를 시작, 중지, 일시 중지, 재개 또는 다시 시작 하는 방법에 대해 설명 합니다 [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a9119-103">This topic describes how to start, stop, pause, resume, or restart the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], **net** commands from a command prompt, [!INCLUDE[tsql](../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
-   <span data-ttu-id="a9119-104">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="a9119-104">**Before you begin:**</span></span>  
  
    -   [<span data-ttu-id="a9119-105">SQL Server Database Engine, SQL Server 에이전트 및 SQL Server Browser 서비스 정의</span><span class="sxs-lookup"><span data-stu-id="a9119-105">What are these services?</span></span>](#Services)  
  
    -   [<span data-ttu-id="a9119-106">추가 정보</span><span class="sxs-lookup"><span data-stu-id="a9119-106">Additional Information</span></span>](#MoreInformation)  
  
    -   [<span data-ttu-id="a9119-107">보안</span><span class="sxs-lookup"><span data-stu-id="a9119-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a9119-108">**사용 지침**</span><span class="sxs-lookup"><span data-stu-id="a9119-108">**Instructions using:**</span></span>  
  
    -   [<span data-ttu-id="a9119-109">SQL Server 구성 관리자</span><span class="sxs-lookup"><span data-stu-id="a9119-109">SQL Server Configuration Manager</span></span>](#SSCMProcedure)  
  
    -   [<span data-ttu-id="a9119-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a9119-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
    -   [<span data-ttu-id="a9119-111">명령 프롬프트 창의 net 명령</span><span class="sxs-lookup"><span data-stu-id="a9119-111">net Commands from a Command Prompt window</span></span>](#CommandPrompt)  
  
    -   [<span data-ttu-id="a9119-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a9119-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
    -   [<span data-ttu-id="a9119-113">PowerShell</span><span class="sxs-lookup"><span data-stu-id="a9119-113">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a9119-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="a9119-114">Before You Begin</span></span>  
  
###  <a name="what-is-the-ssdenoversion-service-the-ssnoversion-agent-service-and-the-ssnoversion-browser-service"></a><a name="Services"></a><span data-ttu-id="a9119-115">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 서비스, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스 정의</span><span class="sxs-lookup"><span data-stu-id="a9119-115">What is the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service, and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service?</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a9119-116">구성 요소는 Windows 서비스로 실행되는 실행 가능한 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-116">components are executable programs that run as a Windows service.</span></span> <span data-ttu-id="a9119-117">Windows 서비스로 실행되는 프로그램은 컴퓨터 화면에 작업을 표시하지 않고도 작업을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-117">Programs that run as a Windows service can continue to operate without displaying any activity on the computer screen.</span></span>  
  
 <span data-ttu-id="a9119-118">**[!INCLUDE[ssDE](../../includes/ssde-md.md)]출력소**</span><span class="sxs-lookup"><span data-stu-id="a9119-118">**[!INCLUDE[ssDE](../../includes/ssde-md.md)] service**</span></span>  
 <span data-ttu-id="a9119-119">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]인 실행 가능한 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-119">The executable process that is the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="a9119-120">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 컴퓨터당 하나로 제한되는 기본 인스턴스이거나 [!INCLUDE[ssDE](../../includes/ssde-md.md)]의 명명된 여러 인스턴스 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-120">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] can be the default instance (limit one per computer), or can be one of many named instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="a9119-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 컴퓨터에 설치된 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-121">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to determine which instances of [!INCLUDE[ssDE](../../includes/ssde-md.md)] are installed on the computer.</span></span> <span data-ttu-id="a9119-122">기본 인스턴스 (설치 하는 경우)는 \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER)\*\* 로 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-122">The default instance (if you install it) is listed as **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER)**.</span></span> <span data-ttu-id="a9119-123">명명 된 인스턴스 (설치 하는 경우)는 \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (<instance_name>)\*\* 으로 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-123">Named instances (if you install them) are listed as **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (<instance_name>)**.</span></span> <span data-ttu-id="a9119-124">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] express는 \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLEXPRESS)\*\* 로 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-124">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express is installed as **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLEXPRESS)**.</span></span>  
  
 <span data-ttu-id="a9119-125">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트 서비스**</span><span class="sxs-lookup"><span data-stu-id="a9119-125">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service**</span></span>  
 <span data-ttu-id="a9119-126">작업 및 경고라고 하는 예약된 관리 태스크를 실행하는 Windows 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-126">A Windows service that executes scheduled administrative tasks, which are called jobs and alerts.</span></span> <span data-ttu-id="a9119-127">자세한 내용은 [SQL Server Agent](../../ssms/agent/sql-server-agent.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9119-127">For more information, see [SQL Server Agent](../../ssms/agent/sql-server-agent.md).</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a9119-128">에이전트는 일부 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-128">Agent is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a9119-129">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a9119-129">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="a9119-130">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Browser 서비스**</span><span class="sxs-lookup"><span data-stu-id="a9119-130">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service**</span></span>  
 <span data-ttu-id="a9119-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 리소스에 대해 들어오는 요청을 수신하고 컴퓨터에 설치된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 정보를 제공하는 Windows 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-131">A Windows service that listens for incoming requests for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources and provides clients information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span> <span data-ttu-id="a9119-132">컴퓨터에 설치된 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스의 단일 인스턴스가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-132">A single instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service is used for all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installed on the computer.</span></span>  
  
###  <a name="additional-information"></a><a name="MoreInformation"></a><span data-ttu-id="a9119-133">추가 정보</span><span class="sxs-lookup"><span data-stu-id="a9119-133">Additional Information</span></span>  
  
-   <span data-ttu-id="a9119-134">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 서비스를 일시 중지하면 새 사용자는 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결할 수 없지만 이미 연결되어 있는 사용자는 연결이 끊어질 때까지 계속해서 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-134">Pausing the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service prevents new users from connecting to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], but users who are already connected can continue to work until their connections are broken.</span></span> <span data-ttu-id="a9119-135">사용자가 작업을 완료할 때까지 기다렸다가 서비스를 중지하려면 일시 중지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-135">Use pause when you want to wait for users to complete work before you stop the service.</span></span> <span data-ttu-id="a9119-136">이렇게 하면 사용자가 진행 중인 트랜잭션을 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-136">This enables them to complete transactions that are in progress.</span></span> <span data-ttu-id="a9119-137">재개를 사용하면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 새 연결을 다시 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-137">Resume allows the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to accept new connections again.</span></span> <span data-ttu-id="a9119-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스는 일시 중지하거나 재개할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-138">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service cannot be paused or resumed.</span></span>  
  
-   <span data-ttu-id="a9119-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자와 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서는 다음 아이콘을 사용하여 서비스의 현재 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-139">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] display the current status of services by using the following icons.</span></span>  
  
     <span data-ttu-id="a9119-140">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager**</span><span class="sxs-lookup"><span data-stu-id="a9119-140">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager**</span></span>  
  
    -   <span data-ttu-id="a9119-141">서비스 이름 옆에 녹색 화살표가 있는 아이콘이 표시되면 서비스가 시작된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-141">A green arrow on the icon next to the service name indicates that the service is started.</span></span>  
  
    -   <span data-ttu-id="a9119-142">서비스 이름 옆에 빨간색 사각형이 있는 아이콘이 표시되면 서비스가 중지된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-142">A red square on the icon next to the service name indicates that the service is stopped.</span></span>  
  
    -   <span data-ttu-id="a9119-143">서비스 이름 옆에 두 개의 파란색 세로 선이 있는 아이콘이 표시되면 서비스가 일시 중지된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-143">Two vertical blue lines on the icon next to the service name indicates that the service is paused.</span></span>  
  
    -   <span data-ttu-id="a9119-144">[!INCLUDE[ssDE](../../includes/ssde-md.md)]을 다시 시작하면 서비스가 중지되었음을 나타내는 빨간색 사각형이 표시되었다가 서비스가 성공적으로 시작되었음을 나타내는 녹색 화살표가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-144">When restarting the [!INCLUDE[ssDE](../../includes/ssde-md.md)], a red square will indicate that the service stopped, and then a green arrow will indicate that he service started successfully.</span></span>  
  
     **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
    -   <span data-ttu-id="a9119-145">서비스 이름 옆의 녹색 원 아이콘에 흰색 화살표가 표시되면 서비스가 시작된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-145">A white arrow on a green circle icon next to the service name indicates that the service is started.</span></span>  
  
    -   <span data-ttu-id="a9119-146">서비스 이름 옆에 흰색 사각형이 있는 빨간색 원 아이콘이 표시되면 서비스가 중지된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-146">A white square on a red circle icon next to the service name indicates that the service is stopped.</span></span>  
  
    -   <span data-ttu-id="a9119-147">서비스 이름 옆에 두 개의 흰색 세로 선이 있는 파란색 원 아이콘이 표시되면 서비스가 일시 중지된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-147">Two vertical white lines on a blue circle icon next to the service name indicates that the service is paused.</span></span>  
  
-   <span data-ttu-id="a9119-148">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하는 경우 가능한 옵션만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-148">When using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], only options that are possible will be available.</span></span> <span data-ttu-id="a9119-149">예를 들어 서비스가 이미 시작된 경우 **시작** 은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-149">For example, if the service is already started, **Start** will be unavailable.</span></span>  
  
-   <span data-ttu-id="a9119-150">클러스터에서 실행 중인 경우 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 서비스는 클러스터 관리자를 사용하면 가장 완벽하게 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-150">When running on a cluster, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service is best managed by using Cluster Administrator.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a9119-151">보안</span><span class="sxs-lookup"><span data-stu-id="a9119-151">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a9119-152">권한</span><span class="sxs-lookup"><span data-stu-id="a9119-152">Permissions</span></span>  
 <span data-ttu-id="a9119-153">기본적으로 로컬 Administrators 그룹의 멤버만 서비스를 시작, 중지, 일시 중지, 재개 또는 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-153">By default, only members of the local administrators group can start, stop, pause, resume or restart a service.</span></span> <span data-ttu-id="a9119-154">관리자가 아닌 사용자에게 서비스 관리 권한을 부여하려면 [Windows Server 2003에서 사용자에게 서비스 관리 권한을 부여하는 방법](https://support.microsoft.com/kb/325349)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9119-154">To grant non-administrators the ability to manage services, see [How to grant users rights to manage services in Windows Server 2003](https://support.microsoft.com/kb/325349).</span></span> <span data-ttu-id="a9119-155">이 프로세스는 다른 Windows 버전에서도 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-155">(The process is similar on other versions of Windows.)</span></span>  
  
 <span data-ttu-id="a9119-156">[!INCLUDE[ssDE](../../includes/ssde-md.md)]명령을 사용 하 여을 중지 [!INCLUDE[tsql](../../includes/tsql-md.md)] `SHUTDOWN` 하려면 **sysadmin** 또는 **serveradmin** 고정 서버 역할의 멤버 여야 하며 양도할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-156">Stopping the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by using the [!INCLUDE[tsql](../../includes/tsql-md.md)]`SHUTDOWN` command requires membership in the **sysadmin** or **serveradmin** fixed server roles, and is not transferable.</span></span>  
  
##  <a name="using-ssnoversion-configuration-manager"></a><a name="SSCMProcedure"></a><span data-ttu-id="a9119-157">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="a9119-157">Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager</span></span>  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-ssdenoversion"></a><span data-ttu-id="a9119-158">다음 인스턴스를 시작, 중지, 일시 중지, 재개 또는 다시 시작하기: [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9119-158">To start, stop, pause, resume, or restart the an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="a9119-159">**시작** 메뉴에서 **모든 프로그램**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-159">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="a9119-160">**사용자 계정 컨트롤** 대화 상자가 나타나면 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-160">If the **User Account Control** dialog box appears, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="a9119-161">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자의 왼쪽 창에서 **SQL Server 서비스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-161">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the left pane, click **SQL Server Services**.</span></span>  
  
4.  <span data-ttu-id="a9119-162">결과 창에서 **SQL Server(MSSQLServer)** 또는 명명된 인스턴스를 마우스 오른쪽 단추로 클릭하고 **시작**, **중지**, **일시 중지**, **재개**또는 **다시 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-162">In the results pane, right-click **SQL Server (MSSQLServer)** or a named instance, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.</span></span>  
  
5.  <span data-ttu-id="a9119-163">**확인** 을 클릭하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-163">Click **OK** to close [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a9119-164">시작 옵션을 사용하여 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스를 시작하려면 [서버 시작 옵션 구성&#40;SQL Server 구성 관리자&#41;](scm-services-configure-server-startup-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9119-164">To start an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with startup options, see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](scm-services-configure-server-startup-options.md).</span></span>  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-ssnoversion-browser-or-an-instance-of-the-ssnoversion-agent"></a><span data-ttu-id="a9119-165">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 인스턴스를 시작, 중지, 일시 중지, 재개 또는 다시 시작하려면</span><span class="sxs-lookup"><span data-stu-id="a9119-165">To start, stop, pause, resume, or restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser or an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent</span></span>  
  
1.  <span data-ttu-id="a9119-166">**시작** 메뉴에서 **모든 프로그램**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-166">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="a9119-167">**사용자 계정 컨트롤** 대화 상자가 나타나면 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-167">If the **User Account Control** dialog box appears, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="a9119-168">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자의 왼쪽 창에서 **SQL Server 서비스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-168">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the left pane, click **SQL Server Services**.</span></span>  
  
4.  <span data-ttu-id="a9119-169">결과 창에서 명명 된 인스턴스에 대 한 \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 브라우저**또는 \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 (MSSQLServer)** 또는 \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 (<instance_name>)\*\* 를 마우스 오른쪽 단추로 클릭 한 다음 **시작**, **중지**, **일시 중지**, **재개**또는 **다시 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-169">In the results pane, right-click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser**, or **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent (MSSQLServer)** or **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent (<instance_name>)** for a named instance, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.</span></span>  
  
5.  <span data-ttu-id="a9119-170">**확인** 을 클릭하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-170">Click **OK** to close [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a9119-171">에이전트는 일시 중지할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-171">Agent cannot be paused.</span></span>  
  
##  <a name="using-ssnoversion-management-studio"></a><a name="SSMSProcedure"></a><span data-ttu-id="a9119-172">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="a9119-172">Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio</span></span>  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-ssdenoversion"></a><span data-ttu-id="a9119-173">다음 인스턴스를 시작, 중지, 일시 중지, 재개 또는 다시 시작하기: [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9119-173">To start, stop, pause, resume, or restart the an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="a9119-174">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결하고 시작할 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스를 마우스 오른쪽 단추로 클릭한 다음 **시작**, **중지**, **일시 중지**, **재개**또는 **다시 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-174">In Object Explorer, connect to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], right-click the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] you want to start, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.</span></span>  
  
     <span data-ttu-id="a9119-175">또는 등록된 서버에서 시작할 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스를 마우스 오른쪽 단추로 클릭하고 **서비스 제어**를 가리킨 다음 **시작**, **중지**, **일시 중지**, **재개**또는 **다시 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-175">Or, in Registered Servers, right-click the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] you want to start, point to **Service Control**, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.</span></span>  
  
2.  <span data-ttu-id="a9119-176">**사용자 계정 컨트롤** 대화 상자가 나타나면 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-176">If the **User Account Control** dialog box appears, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="a9119-177">작업을 수행할지 묻는 메시지가 표시되면 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-177">When prompted if you want to perform the action, click **Yes**.</span></span>  
  
#### <a name="to-start-stop-or-restart-the-an-instance-of-the-ssnoversion-agent"></a><span data-ttu-id="a9119-178">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 인스턴스를 시작, 중지 또는 다시 시작하려면</span><span class="sxs-lookup"><span data-stu-id="a9119-178">To start, stop, or restart the an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent</span></span>  
  
1.  <span data-ttu-id="a9119-179">개체 탐색기에서 인스턴스에 연결 하 고 [!INCLUDE[ssDE](../../includes/ssde-md.md)] \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트\*\*를 마우스 오른쪽 단추로 클릭 한 다음 **시작**, **중지**또는 **다시 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-179">In Object Explorer, connect to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], right-click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent**, and then click **Start**, **Stop**, or **Restart**.</span></span>  
  
2.  <span data-ttu-id="a9119-180">**사용자 계정 컨트롤** 대화 상자가 나타나면 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-180">If the **User Account Control** dialog box appears, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="a9119-181">작업을 수행할지 묻는 메시지가 표시되면 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-181">When prompted if you want to perform the action, click **Yes**.</span></span>  
  
##  <a name="from-the-command-prompt-window-using-net-commands"></a><a name="CommandPrompt"></a> <span data-ttu-id="a9119-182">명령 프롬프트 창에서 net 명령 사용</span><span class="sxs-lookup"><span data-stu-id="a9119-182">From the Command Prompt Window using net Commands</span></span>  
 <span data-ttu-id="a9119-183">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows **net** 명령을 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 시작, 중지 또는 일시 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-183">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services can be started, stopped, or paused by using [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows **net** commands.</span></span>  
  
###  <a name="to-start-the-default-instance-of-the-ssde"></a><a name="dbDefault"></a> <span data-ttu-id="a9119-184">다음 기본 인스턴스 시작하기: [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9119-184">To start the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span></span>  
  
-   <span data-ttu-id="a9119-185">명령 프롬프트에서 다음 명령 중 하나를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-185">From a command prompt, enter one of the following commands:</span></span>  
  
     <span data-ttu-id="a9119-186">**net start "SQL Server (MSSQLSERVER)"**</span><span class="sxs-lookup"><span data-stu-id="a9119-186">**net start "SQL Server (MSSQLSERVER)"**</span></span>  
  
     <span data-ttu-id="a9119-187">또는</span><span class="sxs-lookup"><span data-stu-id="a9119-187">-or-</span></span>  
  
     <span data-ttu-id="a9119-188">**net start MSSQLSERVER**</span><span class="sxs-lookup"><span data-stu-id="a9119-188">**net start MSSQLSERVER**</span></span>  
  
###  <a name="to-start-a-named-instance-of-the-ssde"></a><a name="dbNamed"></a> <span data-ttu-id="a9119-189">다음 명명된 인스턴스 시작하기: [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9119-189">To start a named instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span></span>  
  
-   <span data-ttu-id="a9119-190">명령 프롬프트에서 다음 명령 중 하나를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-190">From a command prompt, enter one of the following commands.</span></span> <span data-ttu-id="a9119-191">*\<instancename>* 을 관리할 인스턴스 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-191">Replace *\<instancename>* with the name of the instance you want to manage.</span></span>  
  
     <span data-ttu-id="a9119-192">**net start “SQL Server (** *instancename* **)”**</span><span class="sxs-lookup"><span data-stu-id="a9119-192">**net start "SQL Server (** *instancename* **)"**</span></span>  
  
     <span data-ttu-id="a9119-193">또는</span><span class="sxs-lookup"><span data-stu-id="a9119-193">-or-</span></span>  
  
     <span data-ttu-id="a9119-194">**net start MSSQL$** *instancename*</span><span class="sxs-lookup"><span data-stu-id="a9119-194">**net start MSSQL$** *instancename*</span></span>  
  
###  <a name="to-start-the-ssde-with-startup-options"></a><a name="dbStartup"></a> <span data-ttu-id="a9119-195">시작 옵션으로 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 을 시작하려면</span><span class="sxs-lookup"><span data-stu-id="a9119-195">To start the [!INCLUDE[ssDE](../../includes/ssde-md.md)] with startup options</span></span>  
  
-   <span data-ttu-id="a9119-196">**net start "SQL Server (MSSQLSERVER)"** 문 끝에 공백으로 구분된 시작 옵션을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-196">Add startup options to the end of the **net start "SQL Server (MSSQLSERVER)"** statement, separated by a space.</span></span> <span data-ttu-id="a9119-197">**net start**를 사용하여 시작하는 경우에는 시작 옵션에 하이픈(-) 대신 슬래시(/)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-197">When started using **net start**, startup options use a slash (/) instead of a hyphen (-).</span></span>  
  
     <span data-ttu-id="a9119-198">**net start "SQL Server (MSSQLSERVER)" /f /m**</span><span class="sxs-lookup"><span data-stu-id="a9119-198">**net start "SQL Server (MSSQLSERVER)" /f /m**</span></span>  
  
     <span data-ttu-id="a9119-199">또는</span><span class="sxs-lookup"><span data-stu-id="a9119-199">-or-</span></span>  
  
     <span data-ttu-id="a9119-200">**net start MSSQLSERVER /f /m**</span><span class="sxs-lookup"><span data-stu-id="a9119-200">**net start MSSQLSERVER /f /m**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a9119-201">시작 옵션에 대한 자세한 내용은 [데이터베이스 엔진 서비스 시작 옵션](database-engine-service-startup-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9119-201">For more information about startup options, see [Database Engine Service Startup Options](database-engine-service-startup-options.md).</span></span>  
  
###  <a name="to-start-the-ssnoversion-agent-on-the-default-instance-of-ssnoversion"></a><a name="agDefault"></a> <span data-ttu-id="a9119-202">시작 옵션으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 기본 인스턴스에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9119-202">To start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent on the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="a9119-203">명령 프롬프트에서 다음 명령 중 하나를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-203">From a command prompt, enter one of the following commands:</span></span>  
  
     <span data-ttu-id="a9119-204">**net start "SQL Server Agent (MSSQLSERVER)"**</span><span class="sxs-lookup"><span data-stu-id="a9119-204">**net start "SQL Server Agent (MSSQLSERVER)"**</span></span>  
  
     <span data-ttu-id="a9119-205">또는</span><span class="sxs-lookup"><span data-stu-id="a9119-205">-or-</span></span>  
  
     <span data-ttu-id="a9119-206">**net start SQLSERVERAGENT**</span><span class="sxs-lookup"><span data-stu-id="a9119-206">**net start SQLSERVERAGENT**</span></span>  
  
###  <a name="to-start-the-ssnoversion-agent-on-a-named-instance-of-ssnoversion"></a><a name="agNamed"></a> <span data-ttu-id="a9119-207">시작 옵션으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 명명된 인스턴스에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9119-207">To start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent on a named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="a9119-208">명령 프롬프트에서 다음 명령 중 하나를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-208">From a command prompt, enter one of the following commands.</span></span> <span data-ttu-id="a9119-209">*instancename* 을 관리할 인스턴스 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-209">Replace *instancename* with the name of the instance you want to manage.</span></span>  
  
     <span data-ttu-id="a9119-210">**net start "SQL Server Agent(** *instancename* **)"**</span><span class="sxs-lookup"><span data-stu-id="a9119-210">**net start "SQL Server Agent(** *instancename* **)"**</span></span>  
  
     <span data-ttu-id="a9119-211">또는</span><span class="sxs-lookup"><span data-stu-id="a9119-211">-or-</span></span>  
  
     <span data-ttu-id="a9119-212">**net start SQLAgent$** *instancename*</span><span class="sxs-lookup"><span data-stu-id="a9119-212">**net start SQLAgent$** *instancename*</span></span>  
  
 <span data-ttu-id="a9119-213">문제 해결을 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 세부 정보 표시 모드로 실행하는 방법은 [sqlagent90 애플리케이션](../../tools/sqlagent90-application.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9119-213">For information about how to run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in verbose mode for troubleshooting, see [sqlagent90 Application](../../tools/sqlagent90-application.md).</span></span>  
  
###  <a name="to-start-the-ssnoversion-browser"></a><a name="Browser"></a><span data-ttu-id="a9119-214">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="a9119-214">To start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser</span></span>  
  
-   <span data-ttu-id="a9119-215">명령 프롬프트에서 다음 명령 중 하나를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-215">From a command prompt, enter one of the following commands:</span></span>  
  
     <span data-ttu-id="a9119-216">**net start "SQL Server Browser"**</span><span class="sxs-lookup"><span data-stu-id="a9119-216">**net start "SQL Server Browser"**</span></span>  
  
     <span data-ttu-id="a9119-217">또는</span><span class="sxs-lookup"><span data-stu-id="a9119-217">-or-</span></span>  
  
     <span data-ttu-id="a9119-218">**net start SQLBrowser**</span><span class="sxs-lookup"><span data-stu-id="a9119-218">**net start SQLBrowser**</span></span>  
  
###  <a name="to-pause-or-stop-services-from-the-command-prompt-window"></a><a name="pauseStop"></a> <span data-ttu-id="a9119-219">명령 프롬프트 창에서 서비스를 일시 중지하거나 중지하려면</span><span class="sxs-lookup"><span data-stu-id="a9119-219">To pause or stop services from the Command Prompt window</span></span>  
  
-   <span data-ttu-id="a9119-220">서비스를 일시 중지하거나 중지하려면 다음과 같은 방법으로 명령을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-220">To pause or stop services modify the commands in the following ways.</span></span>  
  
    -   <span data-ttu-id="a9119-221">서비스를 일시 중지하려면 **net start** 를 **net pause**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-221">To pause a service, replace **net start** with **net pause**.</span></span>  
  
    -   <span data-ttu-id="a9119-222">서비스를 중지하려면 **net start** 를 **net stop**으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-222">To stop a service, replace **net start** with use **net stop**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a9119-223">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="a9119-223">Using Transact-SQL</span></span>  
 <span data-ttu-id="a9119-224">`SHUTDOWN` 문을 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)]을 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-224">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] can be stopped by using the `SHUTDOWN` statement.</span></span>  
  
#### <a name="to-stop-the-ssde-using-tsql"></a><span data-ttu-id="a9119-225">다음을 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 을 중지하기: [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9119-225">To stop the [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
-   <span data-ttu-id="a9119-226">현재 실행 중인 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문 및 저장 프로시저가 완료될 때까지 기다린 다음 [!INCLUDE[ssDE](../../includes/ssde-md.md)]을 중지하려면 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-226">To wait for currently running [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and stored procedures to finish, and then stop the [!INCLUDE[ssDE](../../includes/ssde-md.md)], execute the following statement.</span></span>  
  
    ```sql  
    SHUTDOWN;   
    ```  
  
-   <span data-ttu-id="a9119-227">[!INCLUDE[ssDE](../../includes/ssde-md.md)]을 즉시 중지하려면 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-227">To stop the [!INCLUDE[ssDE](../../includes/ssde-md.md)] immediately, execute the following statement.</span></span>  
  
    ```sql  
    SHUTDOWN WITH NOWAIT;   
    ```  
  
 <span data-ttu-id="a9119-228">문에 대 한 자세한 내용은 `SHUTDOWN` [SHUTDOWN &#40;transact-sql&#41;](/sql/t-sql/language-elements/shutdown-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a9119-228">For more information about the `SHUTDOWN` statement, see [SHUTDOWN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/shutdown-transact-sql).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="a9119-229">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="a9119-229">Using PowerShell</span></span>  
  
#### <a name="to-start-and-stop-ssde-services"></a><span data-ttu-id="a9119-230">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 서비스를 시작 및 중지하려면</span><span class="sxs-lookup"><span data-stu-id="a9119-230">To start and stop [!INCLUDE[ssDE](../../includes/ssde-md.md)] services</span></span>  
  
1.  <span data-ttu-id="a9119-231">명령 프롬프트 창에서 다음 명령을 실행하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-231">In a Command Prompt window, start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell by executing the following command.</span></span>  
  
    ```ms-dos  
    sqlps  
    ```  
  
2.  <span data-ttu-id="a9119-232">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 명령 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-232">At a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell command prompt, by executing the following command.</span></span> <span data-ttu-id="a9119-233">`computername` 을 사용 중인 컴퓨터의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-233">Replace `computername` with the name of your computer.</span></span>  
  
    ```powershell  
    # Get a reference to the ManagedComputer class.  
    CD SQLSERVER:\SQL\computername  
    $Wmi = (Get-Item .).ManagedComputer
    ```  
  
3.  <span data-ttu-id="a9119-234">중지하거나 시작할 서비스를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-234">Identify the service that you want to stop or start.</span></span> <span data-ttu-id="a9119-235">다음 줄 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-235">Pick one of the following lines.</span></span> <span data-ttu-id="a9119-236">`instancename` 을 명명된 인스턴스의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-236">Replace `instancename` with the name of the named instance.</span></span>  
  
    -   <span data-ttu-id="a9119-237">[!INCLUDE[ssDE](../../includes/ssde-md.md)]의 기본 인스턴스에 대한 참조를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="a9119-237">To get a reference to the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQLSERVER']  
        ```  
  
    -   <span data-ttu-id="a9119-238">[!INCLUDE[ssDE](../../includes/ssde-md.md)]의 명명된 인스턴스에 대한 참조를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="a9119-238">To get a reference to a named instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQL$instancename']  
        ```  
  
    -   <span data-ttu-id="a9119-239">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 기본 인스턴스에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에이전트 서비스에 대한 참조를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="a9119-239">To get a reference to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service on the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLSERVERAGENT']  
        ```  
  
    -   <span data-ttu-id="a9119-240">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 명명된 인스턴스에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에이전트 서비스에 대한 참조를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="a9119-240">To get a reference to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service on a named instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLAGENT$instancename']  
        ```  
  
    -   <span data-ttu-id="a9119-241">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스에 대한 참조를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="a9119-241">To get a reference to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLBROWSER']  
        ```  
  
4.  <span data-ttu-id="a9119-242">예를 완료하여 선택한 서비스를 시작한 다음 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="a9119-242">Complete the example to start and then stop the selected service.</span></span>  
  
    ```powershell  
    # Display the state of the service.  
    $DfltInstance  
    # Start the service.  
    $DfltInstance.Start();  
    # Wait until the service has time to start.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    # Stop the service.  
    $DfltInstance.Stop();  
    # Wait until the service has time to stop.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a9119-243">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a9119-243">See Also</span></span>  
 <span data-ttu-id="a9119-244">[최소 구성으로 SQL Server 시작](start-sql-server-with-minimal-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="a9119-244">[Start SQL Server with Minimal Configuration](start-sql-server-with-minimal-configuration.md) </span></span>  
 [<span data-ttu-id="a9119-245">SQL Server 2014 버전에서 지원하는 기능</span><span class="sxs-lookup"><span data-stu-id="a9119-245">Features Supported by the Editions of SQL Server 2014</span></span>](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
