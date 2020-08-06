---
title: 기업 내 관리 자동화 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enterprise automatic administration [SQL Server]
- multiserver administration [SQL Server]
- SQL Server Agent jobs, multiserver administration
- jobs [SQL Server Agent], multiserver administration
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- master servers [SQL Server]
- multiple instances of SQL Server
- target servers [SQL Server]
ms.assetid: 44d8365b-42bd-4955-b5b2-74a8a9f4a75f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8df3e34c2c70c81f9710ade0d6855446b930fb50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652547"
---
# <a name="automated-administration-across-an-enterprise"></a><span data-ttu-id="7f051-102">기업 내 관리 자동화</span><span class="sxs-lookup"><span data-stu-id="7f051-102">Automated Administration Across an Enterprise</span></span>
  <span data-ttu-id="7f051-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 여러 인스턴스에 대한 관리 자동화를 *다중 서버 관리*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-103">Automating administration across multiple instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is called *multiserver administration*.</span></span> <span data-ttu-id="7f051-104">다중 서버 관리를 사용하여 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-104">Use multiserver administration to do the following:</span></span>  
  
-   <span data-ttu-id="7f051-105">두 대 이상의 서버 관리</span><span class="sxs-lookup"><span data-stu-id="7f051-105">Manage two or more servers.</span></span>  
  
-   <span data-ttu-id="7f051-106">데이터 웨어하우징을 위해 엔터프라이즈 서버 간의 정보 흐름 예약</span><span class="sxs-lookup"><span data-stu-id="7f051-106">Schedule information flows between enterprise servers for data warehousing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7f051-107">[!INCLUDE[msCoName](../../includes/msconame-md.md)]는 총 소유 비용을 줄이고자 하는 지속적인 노력의 일환으로 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에서 정책 기반 관리라고 하는 서버 관리 방법과 구성 서버 및 서버 그룹을 사용하는 다중 서버 쿼리라고 하는 두 가지 기능을 새로 도입했습니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-107">As part of [!INCLUDE[msCoName](../../includes/msconame-md.md)] ongoing efforts to reduce the total cost of ownership, [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] introduced two features:  a method of managing servers that is called Policy-Based Management, and multiserver queries that use configuration servers and server groups.</span></span> <span data-ttu-id="7f051-108">이러한 기능을 이 항목에서 설명하는 일부 기능 대신 또는 일부 기능과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-108">These features can be used with, or instead of, some of the features that are described in this topic.</span></span> <span data-ttu-id="7f051-109">자세한 내용은 [정책 기반 관리를 사용 하 여 서버 관리](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) 및 [중앙 관리 서버를 사용 하 여 여러 서버 관리](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7f051-109">For more information, see [Administer Servers by Using Policy-Based Management](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) and [Administer Multiple Servers Using Central Management Servers](../../relational-databases/administer-multiple-servers-using-central-management-servers.md).</span></span>  
  
 <span data-ttu-id="7f051-110">다중 서버 관리를 이용하려면 마스터 서버와 대상 서버가 적어도 하나씩 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-110">To take advantage of multiserver administration, you must have at least one master server and at least one target server.</span></span> <span data-ttu-id="7f051-111">마스터 서버는 대상 서버에 작업을 배포하거나 대상 서버에서 이벤트를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-111">A master server distributes jobs to, and receives events from, target servers.</span></span> <span data-ttu-id="7f051-112">또한 마스터 서버에서는 대상 서버에서 실행되는 작업에 대한 작업 정의의 중앙 복사본을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-112">A master server also stores the central copy of job definitions for jobs that are run on target servers.</span></span> <span data-ttu-id="7f051-113">대상 서버는 주기적으로 마스터 서버에 연결되어 작업 일정을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-113">Target servers connect periodically to the master server to update their schedule of jobs.</span></span> <span data-ttu-id="7f051-114">새 작업이 마스터 서버에 있는 경우 대상 서버는 작업을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-114">If a new job exists on the master server, the target server downloads the job.</span></span> <span data-ttu-id="7f051-115">대상 서버는 작업을 완료한 후에 마스터 서버에 다시 연결하여 작업 상태를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-115">After the target server completes the job, it reconnects to the master server and reports the status of the job.</span></span>  
  
 <span data-ttu-id="7f051-116">다음 그림은 마스터 서버와 대상 서버 간의 관계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-116">The following illustration shows the relationship between master and target servers:</span></span>  
  
 <span data-ttu-id="7f051-117">![다중 서버 관리 구성](../../database-engine/media/multisvr.gif "다중 서버 관리 구성")</span><span class="sxs-lookup"><span data-stu-id="7f051-117">![Multiserver administration configuration](../../database-engine/media/multisvr.gif "Multiserver administration configuration")</span></span>  
  
 <span data-ttu-id="7f051-118">대기업에서 부서 서버를 관리하는 경우 다음을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-118">If you administer departmental servers across a large corporation, you can define the following:</span></span>  
  
-   <span data-ttu-id="7f051-119">작업 단계를 사용하는 하나의 백업 작업</span><span class="sxs-lookup"><span data-stu-id="7f051-119">One backup job with job steps.</span></span>  
  
-   <span data-ttu-id="7f051-120">백업 실패 시 알릴 운영자</span><span class="sxs-lookup"><span data-stu-id="7f051-120">Operators to notify in case of backup failure.</span></span>  
  
-   <span data-ttu-id="7f051-121">백업 작업의 실행 일정</span><span class="sxs-lookup"><span data-stu-id="7f051-121">An execution schedule for the backup job.</span></span>  
  
 <span data-ttu-id="7f051-122">마스터 서버에 이 백업 작업을 한 번 쓴 다음 각 부서 서버를 대상 서버로 참여시킵니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-122">Write this backup job one time on the master server and then enlist each departmental server as a target server.</span></span> <span data-ttu-id="7f051-123">모든 부서 서버는 참여할 때부터 동일한 백업 작업을 실행하지만 작업은 한 번만 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-123">From the time of their enlistment, all the departmental servers run the same backup job, yet you defined the job only once.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7f051-124">다중 서버 관리 기능은 sysadmin 역할의 멤버를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-124">Multiserver administration features are intended for members of the sysadmin role.</span></span> <span data-ttu-id="7f051-125">그러나 대상 서버에서 sysadmin 역할의 멤버는 마스터 서버에 의해 대상 서버에서 실행된 작업을 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-125">However, a member of the sysadmin role on the target server cannot edit the operations that are performed on the target server by the master server.</span></span> <span data-ttu-id="7f051-126">이 보안 조치는 작업 단계가 실수로 삭제되는 것과 대상 서버에서 작업이 중단되는 것을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-126">This security measure prevents job steps from being accidentally deleted and operations on the target server from being interrupted.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7f051-127">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="7f051-127">In This Section</span></span>  
 [<span data-ttu-id="7f051-128">다중 서버 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="7f051-128">Create a Multiserver Environment</span></span>](create-a-multiserver-environment.md)  
 <span data-ttu-id="7f051-129">마스터 서버와 대상 서버를 만들고 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-129">Contains information about how to create and manage master and target servers.</span></span>  
  
 [<span data-ttu-id="7f051-130">다중 서버 환경에 적합한 SQL Server 에이전트 서비스 계정 선택</span><span class="sxs-lookup"><span data-stu-id="7f051-130">Choose the Right SQL Server Agent Service Account for Multiserver Environments</span></span>](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)  
 <span data-ttu-id="7f051-131">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트 서비스에 관리자가 아닌 Windows 계정이나 로컬 시스템 계정을 사용할 경우 다중 서버 환경에 미치는 영향에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-131">Contains information about how using nonadministrative Windows accounts or the Local System account for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service can affect multiserver environments.</span></span>  
  
 [<span data-ttu-id="7f051-132">대상 서버의 암호화 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="7f051-132">Set Encryption Options on Target Servers</span></span>](set-encryption-options-on-target-servers.md)  
 <span data-ttu-id="7f051-133">대상 서버에서 MsxEncryptChannelOptions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트 레지스트리 하위 키를 설정하는 방법에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-133">Contains information about setting the MsxEncryptChannelOptions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent registry subkey on target servers.</span></span>  
  
 [<span data-ttu-id="7f051-134">기업 내 작업 관리</span><span class="sxs-lookup"><span data-stu-id="7f051-134">Manage Jobs Across an Enterprise</span></span>](manage-jobs-across-an-enterprise.md)  
 <span data-ttu-id="7f051-135">작업 상태를 확인하고, 작업의 대상 서버를 변경하고, 대상 서버 클럭을 동기화하고, 현재 작업 상태에 대해 마스터 서버를 폴링하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-135">Contains information about checking job status, changing target servers for jobs, synchronizing target server clocks, and polling master servers for their current job status.</span></span>  
  
 [<span data-ttu-id="7f051-136">프록시를 사용하는 다중 서버 작업 문제 해결</span><span class="sxs-lookup"><span data-stu-id="7f051-136">Troubleshoot Multiserver Jobs That Use Proxies</span></span>](troubleshoot-multiserver-jobs-that-use-proxies.md)  
 <span data-ttu-id="7f051-137">실패한 프록시 사용 다중 서버 작업의 문제 해결 방법에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-137">Contains information about troubleshooting multiserver jobs that use proxies which fail.</span></span>  
  
 [<span data-ttu-id="7f051-138">서버 폴링</span><span class="sxs-lookup"><span data-stu-id="7f051-138">Poll Servers</span></span>](poll-servers.md)  
 <span data-ttu-id="7f051-139">암시적이고 명시적으로 대상 서버에서 마스터 서버를 폴링하여 작업 정보를 동기화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-139">Contains information about how to implicitly and explicitly make target servers poll master servers to synchronize jobs information.</span></span>  
  
 [<span data-ttu-id="7f051-140">이벤트 관리</span><span class="sxs-lookup"><span data-stu-id="7f051-140">Manage Events</span></span>](manage-events.md)  
 <span data-ttu-id="7f051-141">대상 서버에서 마스터 서버로 이벤트를 전달하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-141">Contains information about event forwarding from target servers to master servers.</span></span>  
  
 [<span data-ttu-id="7f051-142">기업 내의 자동화된 관리 튜닝</span><span class="sxs-lookup"><span data-stu-id="7f051-142">Tune Automated Administration Across an Enterprise</span></span>](tune-automated-administration-across-an-enterprise.md)  
 <span data-ttu-id="7f051-143">다중 서버 환경에서 자동화된 관리를 통해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 자체 튜닝 기능을 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7f051-143">Contains information about how automated administration in a multiserver environment takes advantage of the self-tuning features of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f051-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7f051-144">See Also</span></span>  
 <span data-ttu-id="7f051-145">[SQL Server 데이터베이스 엔진의 이전 버전과의 호환성](../../database-engine/sql-server-database-engine-backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="7f051-145">[SQL Server Database Engine Backward Compatibility](../../database-engine/sql-server-database-engine-backward-compatibility.md) </span></span>  
 <span data-ttu-id="7f051-146">[서버 등록](../register-servers/register-servers.md) </span><span class="sxs-lookup"><span data-stu-id="7f051-146">[Register Servers](../register-servers/register-servers.md) </span></span>  
 <span data-ttu-id="7f051-147">[Transact-sql&#41;sp_add_targetservergroup &#40;](/sql/relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7f051-147">[sp_add_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql) </span></span>  
 <span data-ttu-id="7f051-148">[Transact-sql&#41;sp_delete_targetserver &#40;](/sql/relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7f051-148">[sp_delete_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql) </span></span>  
 <span data-ttu-id="7f051-149">[Transact-sql&#41;sp_delete_targetservergroup &#40;](/sql/relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7f051-149">[sp_delete_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql) </span></span>  
 <span data-ttu-id="7f051-150">[Transact-sql&#41;sp_help_downloadlist &#40;](/sql/relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7f051-150">[sp_help_downloadlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql) </span></span>  
 <span data-ttu-id="7f051-151">[Transact-sql&#41;sp_help_jobserver &#40;](/sql/relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7f051-151">[sp_help_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql) </span></span>  
 <span data-ttu-id="7f051-152">[Transact-sql&#41;sp_help_targetservergroup &#40;](/sql/relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7f051-152">[sp_help_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql) </span></span>  
 <span data-ttu-id="7f051-153">[Transact-sql&#41;sp_resync_targetserver &#40;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7f051-153">[sp_resync_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql) </span></span>  
 <span data-ttu-id="7f051-154">[Transact-sql&#41;sp_update_targetservergroup &#40;](/sql/relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7f051-154">[sp_update_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql) </span></span>  
 <span data-ttu-id="7f051-155">[dbo.sysjobservers &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobservers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7f051-155">[dbo.sysjobservers &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobservers-transact-sql) </span></span>  
 <span data-ttu-id="7f051-156">[Transact-sql&#41;&#40;로그인sys.sys](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7f051-156">[sys.syslogins &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql) </span></span>  
 [<span data-ttu-id="7f051-157">dbo.systargetservers &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="7f051-157">dbo.systargetservers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/dbo-systargetservers-transact-sql)  
  
  
