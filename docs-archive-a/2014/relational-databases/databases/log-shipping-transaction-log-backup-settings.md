---
title: 로그 전달 트랜잭션 로그 백업 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.settings.tlogback.f1
ms.assetid: 9a6e6c16-7f71-412b-bba6-7bffac001277
author: stevestein
ms.author: sstein
ms.openlocfilehash: b5420f3032cd2477d23028a2e27c1ce89c4e0525
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742183"
---
# <a name="log-shipping-transaction-log-backup-settings"></a><span data-ttu-id="39cc9-102">로그 전달 트랜잭션 로그 백업 설정</span><span class="sxs-lookup"><span data-stu-id="39cc9-102">Log Shipping Transaction Log Backup Settings</span></span>
  <span data-ttu-id="39cc9-103">이 대화 상자를 사용하여 로그 전달 구성에 대한 트랜잭션 로그 백업 설정을 구성하고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-103">Use this dialog box to configure and modify the transaction log backup settings for a log shipping configuration.</span></span>  
  
 <span data-ttu-id="39cc9-104">로그 전달 개념에 대한 설명은 [로그 전달 정보&#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39cc9-104">For an explanation of log shipping concepts, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="39cc9-105">옵션</span><span class="sxs-lookup"><span data-stu-id="39cc9-105">Options</span></span>  
 <span data-ttu-id="39cc9-106">**백업 폴더의 네트워크 경로**</span><span class="sxs-lookup"><span data-stu-id="39cc9-106">**Network path to the backup folder**</span></span>  
 <span data-ttu-id="39cc9-107">이 상자에 백업 폴더의 네트워크 공유를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-107">Type the network share to your backup folder in this box.</span></span> <span data-ttu-id="39cc9-108">트랜잭션 로그 백업을 저장하는 로컬 폴더를 공유해야 로그 전달 복사 작업을 통해 해당 파일을 보조 서버에 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-108">The local folder where your transaction log backups are saved must be shared so that the log shipping copy jobs can copy these files to the secondary server.</span></span> <span data-ttu-id="39cc9-109">보조 서버 인스턴스에서 복사 작업을 실행하는 데 사용할 프록시 계정에 이 네트워크 공유를 읽을 수 있는 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-109">You must grant read permissions on this network share to the proxy account under which the copy job will run at the secondary server instance.</span></span> <span data-ttu-id="39cc9-110">기본적으로 이 계정은 보조 서버 인스턴스의 SQLServerAgent 서비스 계정이지만 관리자가 다른 프록시 계정을 선택하여 작업에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-110">By default, this is the SQLServerAgent service account of the secondary server instance, but an administrator can choose another proxy account for the job.</span></span>  
  
 <span data-ttu-id="39cc9-111">**백업 폴더가 주 서버에 있는 경우 폴더의 로컬 경로를 입력하십시오.**</span><span class="sxs-lookup"><span data-stu-id="39cc9-111">**If the backup folder is located on the primary server, type the local path to the folder**</span></span>  
 <span data-ttu-id="39cc9-112">백업 폴더가 주 서버에 있는 경우 백업 폴더의 로컬 드라이브 문자와 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-112">Type the local drive letter and path to the backup folder if the backup folder is located on the primary server.</span></span> <span data-ttu-id="39cc9-113">백업 폴더가 주 서버에 없는 경우에는 이 상자를 비워 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-113">If the backup folder is not located on the primary server, you can leave this blank.</span></span>  
  
 <span data-ttu-id="39cc9-114">여기에서 로컬 경로를 지정하면 BACKUP 명령에서 이 경로를 사용하여 트랜잭션 로그 백업을 만듭니다. 그러나 로컬 경로를 지정하지 않으면 BACKUP 명령에서 **백업 폴더의 네트워크 경로** 상자에 지정된 네트워크 경로를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-114">If you specify a local path here, the BACKUP command will use this path to create the transaction log backups; otherwise, if no local path is specified, the BACKUP command will use the network path specified in the **Network path to the backup folder** box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39cc9-115">주 서버의 로컬 시스템 계정에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정이 실행되고 있으면 주 서버에 백업 폴더를 만들고 여기에서 이 폴더의 로컬 경로를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-115">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account is running under the local system account on the primary server, you must create the backup folder on the primary server and specify the local path to that folder here.</span></span> <span data-ttu-id="39cc9-116">주 서버 인스턴스의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정에는 이 폴더에 대한 읽기 및 쓰기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account of the primary server instance must have Read and Write permissions on this folder.</span></span>  
  
 <span data-ttu-id="39cc9-117">**다음보다 오래된 파일 삭제**</span><span class="sxs-lookup"><span data-stu-id="39cc9-117">**Delete files older than**</span></span>  
 <span data-ttu-id="39cc9-118">트랜잭션 로그 백업을 삭제하기 전에 백업 디렉터리에 보관하는 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-118">Specify the length of time you want transaction log backups to remain in your backup directory before being deleted.</span></span>  
  
 <span data-ttu-id="39cc9-119">**다음 기간 내에 백업이 발생하지 않으면 경고**</span><span class="sxs-lookup"><span data-stu-id="39cc9-119">**Alert if no backup occurs within**</span></span>  
 <span data-ttu-id="39cc9-120">트랜잭션 로그 백업이 수행되지 않았다는 경고를 발생시키기 전까지 로그 전달에서 기다리는 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-120">Specify the amount of time you want log shipping to wait before raising an alert that no transaction log backups have occurred.</span></span>  
  
 <span data-ttu-id="39cc9-121">**작업 이름**</span><span class="sxs-lookup"><span data-stu-id="39cc9-121">**Job name**</span></span>  
 <span data-ttu-id="39cc9-122">로그 전달에 사용할 트랜잭션 로그 백업을 만드는 데 사용되는 SQL Server 에이전트 작업의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-122">Displays the name of the SQL Server Agent job that is used to create the transaction log backups for log shipping.</span></span> <span data-ttu-id="39cc9-123">처음 작업을 만들 때 상자에 이름을 입력하여 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-123">When first creating the job, you can modify the name by typing in the box.</span></span>  
  
 <span data-ttu-id="39cc9-124">**일정**</span><span class="sxs-lookup"><span data-stu-id="39cc9-124">**Schedule**</span></span>  
 <span data-ttu-id="39cc9-125">주 데이터베이스의 트랜잭션 로그를 백업하기 위한 현재 일정을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-125">Displays the current schedule for backing up the transaction logs of the primary database.</span></span> <span data-ttu-id="39cc9-126">백업 작업이 생성되기 전에는 **일정...** 을 클릭하여 이 일정을 수정할 수 있고 작업이 생성된 후에는 **작업 편집...** 을 클릭하여 이 일정을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-126">Before the backup job has been created, You can modify this schedule by clicking **Schedule...**. After the job has been created, you can modify this schedule by clicking **Edit Job...**.</span></span>  
  
### <a name="backup-job"></a><span data-ttu-id="39cc9-127">백업 작업</span><span class="sxs-lookup"><span data-stu-id="39cc9-127">Backup Job</span></span>  
 <span data-ttu-id="39cc9-128">**일정...**</span><span class="sxs-lookup"><span data-stu-id="39cc9-128">**Schedule...**</span></span>  
 <span data-ttu-id="39cc9-129">SQL Server 에이전트 작업을 만들 때 생성되는 일정을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-129">Modify the schedule that is created when the SQL Server Agent job is created.</span></span>  
  
 <span data-ttu-id="39cc9-130">**작업 편집...**</span><span class="sxs-lookup"><span data-stu-id="39cc9-130">**Edit Job...**</span></span>  
 <span data-ttu-id="39cc9-131">주 데이터베이스에 대해 트랜잭션 로그 백업을 수행하는 작업의 SQL Server 에이전트 작업 매개 변수를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-131">Modify the SQL Server Agent job parameters for the job that performs transaction log backups on the primary database.</span></span>  
  
 <span data-ttu-id="39cc9-132">**이 작업 비활성화**</span><span class="sxs-lookup"><span data-stu-id="39cc9-132">**Disable this job**</span></span>  
 <span data-ttu-id="39cc9-133">트랜잭션 로그 백업을 만들지 않도록 SQL Server 에이전트 작업을 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-133">Disable the SQL Server Agent job from creating transaction log backups.</span></span>  
  
### <a name="compression"></a><span data-ttu-id="39cc9-134">압축</span><span class="sxs-lookup"><span data-stu-id="39cc9-134">Compression</span></span>  
 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="39cc9-135">(이상 버전)에서는 [백업 압축](../backup-restore/backup-compression-sql-server.md)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-135">(or a later version) supports [backup compression](../backup-restore/backup-compression-sql-server.md).</span></span>  
  
 <span data-ttu-id="39cc9-136">**백업 압축 설정**</span><span class="sxs-lookup"><span data-stu-id="39cc9-136">**Set backup compression**</span></span>  
 <span data-ttu-id="39cc9-137">[!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] 이상 버전에서 이 로그 전달 구성의 로그 백업에 대해 다음 백업 압축 값 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-137">In [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (or a later version), select one the following backup compression values for the log backups of this log shipping configuration:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="39cc9-138">**기본 서버 설정 사용**</span><span class="sxs-lookup"><span data-stu-id="39cc9-138">**Use the default server setting**</span></span>|<span data-ttu-id="39cc9-139">서버 수준 기본값을 사용하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-139">Click to use the server-level default.</span></span><br /><br /> <span data-ttu-id="39cc9-140">이 기본값은 **백업 압축 기본값** 서버 구성 옵션으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-140">This default is set by the **backup compression default** server-configuration option.</span></span> <span data-ttu-id="39cc9-141">이 옵션의 현재 설정을 확인하는 방법에 대한 자세한 내용은 [백업 압축 기본값 서버 구성 옵션 보기 또는 구성](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39cc9-141">For information about how to view the current setting of this option, see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>|  
|<span data-ttu-id="39cc9-142">**백업 압축**</span><span class="sxs-lookup"><span data-stu-id="39cc9-142">**Compress backup**</span></span>|<span data-ttu-id="39cc9-143">서버 수준 기본값에 관계없이 백업을 압축하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-143">Click to compress the backup, regardless of the server-level default.</span></span><br /><br /> <span data-ttu-id="39cc9-144">**\*\* 중요 \*\*** 기본적으로 압축하면 CPU 사용량이 크게 늘어나고 압축 프로세스로 사용되는 추가 CPU는 동시 작업에 악영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-144">**\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations.</span></span> <span data-ttu-id="39cc9-145">따라서 CPU 사용량이 [리소스 관리자](../resource-governor/resource-governor.md)에 의해 제한되는 세션에서 우선 순위가 낮은 압축 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-145">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by the [Resource Governor](../resource-governor/resource-governor.md).</span></span> <span data-ttu-id="39cc9-146">자세한 내용은 이 항목 뒷부분의 [Resource GovernoR을 사용하여 백업 압축을 통해 CPU 사용량 제한&#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)에 의해 제한되는 세션에서 우선 순위가 낮은 압축 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-146">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>|  
|<span data-ttu-id="39cc9-147">**백업 압축 안 함**</span><span class="sxs-lookup"><span data-stu-id="39cc9-147">**Do not compress backup**</span></span>|<span data-ttu-id="39cc9-148">서버 수준 기본값에 관계없이 압축되지 않은 백업을 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39cc9-148">Click to create an uncompressed backup, regardless of the server-level default.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39cc9-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="39cc9-149">See Also</span></span>  
 <span data-ttu-id="39cc9-150">[SQL Server 에이전트 작업을 만들고 관리하도록 사용자 구성](../../ssms/agent/configure-a-user-to-create-and-manage-sql-server-agent-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="39cc9-150">[Configure a User to Create and Manage SQL Server Agent Jobs](../../ssms/agent/configure-a-user-to-create-and-manage-sql-server-agent-jobs.md) </span></span>  
 [<span data-ttu-id="39cc9-151">로그 전달 정보&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="39cc9-151">About Log Shipping &#40;SQL Server&#41;</span></span>](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
