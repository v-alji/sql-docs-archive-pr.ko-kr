---
title: 단일 사용자 모드로 SQL Server 시작 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- starting SQL Server, single-user mode
- single-user mode [SQL Server]
ms.assetid: 72eb4fc1-7af4-4ec6-9e02-11a69e02748e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b2600524da45f9a81f155432397cee2e7e876274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646627"
---
# <a name="start-sql-server-in-single-user-mode"></a><span data-ttu-id="b4121-102">단일 사용자 모드로 SQL Server 시작</span><span class="sxs-lookup"><span data-stu-id="b4121-102">Start SQL Server in Single-User Mode</span></span>
  <span data-ttu-id="b4121-103">특정 상황에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시작 옵션 -m **을 사용하여**의 인스턴스를 단일 사용자 모드로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-103">Under certain circumstances, you may have to start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode by using the **startup option -m.**</span></span> <span data-ttu-id="b4121-104">예를 들어 서버 구성 옵션을 변경하거나 손상된 master 데이터베이스 또는 다른 시스템 데이터베이스를 복구하려고 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-104">For example, you may want to change server configuration options or recover a damaged master database or other system database.</span></span> <span data-ttu-id="b4121-105">두 가지 동작 모두 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 단일 사용자 모드로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-105">Both actions require starting an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode.</span></span>  
  
 <span data-ttu-id="b4121-106">단일 사용자 모드로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 시작하면 컴퓨터에서 로컬 Administrators 그룹의 모든 멤버가 sysadmin 고정 서버 역할의 멤버로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-106">Starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode enables any member of the computer's local Administrators group to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a member of the sysadmin fixed server role.</span></span> <span data-ttu-id="b4121-107">자세한 내용은 [시스템 관리자가 잠겨 있는 경우 SQL Server에 연결](connect-to-sql-server-when-system-administrators-are-locked-out.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b4121-107">For more information, see [Connect to SQL Server When System Administrators Are Locked Out](connect-to-sql-server-when-system-administrators-are-locked-out.md).</span></span>  
  
 <span data-ttu-id="b4121-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 단일 사용자 모드로 시작할 경우 다음에 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4121-108">When you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, note the following:</span></span>  
  
-   <span data-ttu-id="b4121-109">사용자 한 명만 서버에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-109">Only one user can connect to the server.</span></span>  
  
-   <span data-ttu-id="b4121-110">CHECKPOINT 프로세스는 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-110">The CHECKPOINT process is not executed.</span></span> <span data-ttu-id="b4121-111">기본적으로 서버 시작 시 자동 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-111">By default, it is executed automatically at startup.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4121-112">단일 사용자 모드로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결하기 전에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스를 중단하십시오. 그렇지 않으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스에서 해당 연결을 사용하므로 연결이 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-112">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service before connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode; otherwise, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service uses the connection, thereby blocking it.</span></span>  
  
 <span data-ttu-id="b4121-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 단일 사용자 모드로 시작할 경우 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-113">When you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] can connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b4121-114">개체 탐색기의 일부 작업에는 둘 이상의 연결이 필요하므로 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에서 개체 탐색기가 실패할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-114">Object Explorer in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] might fail because it requires more than one connection for some operations.</span></span> <span data-ttu-id="b4121-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 단일 사용자 모드로 관리하려면 [!INCLUDE[tsql](../../includes/tsql-md.md)] 의 쿼리 편집기를 통해서만 연결하여 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]문을 실행하거나 [sqlcmd 유틸리티](../../tools/sqlcmd-utility.md)를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="b4121-115">To manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements by connecting only through the Query Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], or use the [sqlcmd utility](../../tools/sqlcmd-utility.md).</span></span>  
  
 <span data-ttu-id="b4121-116">**Sqlcmd** 또는와 함께 **-m** 옵션을 사용 하는 경우 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 지정 된 클라이언트 응용 프로그램에 대 한 연결을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-116">When you use the **-m** option with **sqlcmd** or [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can limit the connections to a specified client application.</span></span> <span data-ttu-id="b4121-117">예를 들어 **-m "sqlcmd"** 는 연결 수를 단일 연결로 제한 하며 해당 연결은 자신을 **sqlcmd** 클라이언트 프로그램으로 식별 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-117">For example, **-m"sqlcmd"** limits connections to a single connection and that connection must identify itself as the **sqlcmd** client program.</span></span> <span data-ttu-id="b4121-118">단일 사용자 모드에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 시작하며 알 수 없는 클라이언트 애플리케이션에서 사용 가능한 유일한 연결을 사용할 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-118">Use this option when you are starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode and an unknown client application is taking the only available connection.</span></span> <span data-ttu-id="b4121-119">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 쿼리 편집기를 통해 연결하려면 **-m"Microsoft SQL Server Management Studio - 쿼리"** 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-119">To connect through the Query Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], use **-m"Microsoft SQL Server Management Studio - Query"**.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b4121-120">이 옵션을 보안 용도로는 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="b4121-120">Do not use this option as a security feature.</span></span> <span data-ttu-id="b4121-121">클라이언트 애플리케이션에서 클라이언트 애플리케이션 이름을 제공하므로 연결 문자열의 일부로 잘못된 이름을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-121">The client application provides the client application name, and can provide a false name as part of the connection string.</span></span>  
  
## <a name="note-for-clustered-installations"></a><span data-ttu-id="b4121-122">클러스터형 설치에 대한 참고 사항</span><span class="sxs-lookup"><span data-stu-id="b4121-122">Note for Clustered installations</span></span>  
 <span data-ttu-id="b4121-123">클러스터 환경에 설치된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 단일 사용자 모드로 시작되면 클러스터 리소스 dll이 사용 가능한 모든 연결을 사용하므로 서버에 대한 다른 연결은 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-123">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation in a clustered environment, when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started in single user mode, the cluster resource dll uses up the available connection thereby blocking any other connections to the server.</span></span> <span data-ttu-id="b4121-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 이 상태이고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 리소스가 그룹에 영향을 주도록 구성되어 있는 경우 온라인으로 이 리소스를 가져오려고 하면 SQL 리소스가 다른 노드로 장애 조치(failover)될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-124">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is in this state, if you try to bring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent resource online, it may fail over the SQL resource to a different node if the resource is configured to affect the group.</span></span>  
  
 <span data-ttu-id="b4121-125">이 문제를 해결하려면 다음 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-125">To get around the problem use the following procedure:</span></span>  
  
1.  <span data-ttu-id="b4121-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 고급 속성에서 –m 시작 매개 변수를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-126">Remove the -m startup parameter from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] advanced Properties.</span></span>  
  
2.  <span data-ttu-id="b4121-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 리소스를 오프라인 상태로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-127">Take the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource offline.</span></span>  
  
3.  <span data-ttu-id="b4121-128">이 그룹의 현재 소유자 노드에서 명령 프롬프트를 열고</span><span class="sxs-lookup"><span data-stu-id="b4121-128">From the current owner node of this group, issue the following command from the command prompt:</span></span>  
    <span data-ttu-id="b4121-129">net start MSSQLSERVER /m 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-129">net start MSSQLSERVER /m.</span></span>  
  
4.  <span data-ttu-id="b4121-130">클러스터 관리자 또는 장애 조치(failover) 클러스터 관리 콘솔에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 리소스가 여전히 오프라인 상태인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-130">Verify from the cluster administrator or failover cluster management console that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource is still offline.</span></span>  
  
5.  <span data-ttu-id="b4121-131">이제 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결합니다. SQLCMD -E -S\<servername>.</span><span class="sxs-lookup"><span data-stu-id="b4121-131">Connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] now using the following command and do the necessary operation: SQLCMD -E -S\<servername>.</span></span>  
  
6.  <span data-ttu-id="b4121-132">작업이 완료되면 명령 프롬프트를 닫고 클러스터 관리자를 통해 SQL 및 기타 리소스를 다시 온라인 상태로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b4121-132">Once the operation is complete, close the command prompt and bring back the SQL and other resources online through cluster administrator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4121-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4121-133">See Also</span></span>  
 <span data-ttu-id="b4121-134">[SQL Server 에이전트 서비스 시작, 중지 또는 일시 중지](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md) </span><span class="sxs-lookup"><span data-stu-id="b4121-134">[Start, Stop, or Pause the SQL Server Agent Service](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md) </span></span>  
 <span data-ttu-id="b4121-135">[데이터베이스 관리자를 위한 진단 연결](diagnostic-connection-for-database-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="b4121-135">[Diagnostic Connection for Database Administrators](diagnostic-connection-for-database-administrators.md) </span></span>  
 <span data-ttu-id="b4121-136">[sqlcmd 유틸리티](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="b4121-136">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 <span data-ttu-id="b4121-137">[CHECKPOINT&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b4121-137">[CHECKPOINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql) </span></span>  
 <span data-ttu-id="b4121-138">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b4121-138">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="b4121-139">데이터베이스 엔진 서비스 시작 옵션</span><span class="sxs-lookup"><span data-stu-id="b4121-139">Database Engine Service Startup Options</span></span>](database-engine-service-startup-options.md)  
  
  
