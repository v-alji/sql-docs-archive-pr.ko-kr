---
title: 주 로그 전달 서버와 보조 로그 전달 서버 간 역할 변경(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], role changes
- secondary data files [SQL Server], roles changed between
- primary databases [SQL Server]
- initial role changes [SQL Server]
- log shipping [SQL Server], failover
- failover [SQL Server], log shipping
ms.assetid: 2d7cc40a-47e8-4419-9b2b-7c69f700e806
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 52ddb89bfd18eef4cd2140bc67cf93d1800138f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734423"
---
# <a name="change-roles-between-primary-and-secondary-log-shipping-servers-sql-server"></a><span data-ttu-id="9f215-102">주 로그 전달 서버와 보조 로그 전달 서버 간 역할 변경(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9f215-102">Change Roles Between Primary and Secondary Log Shipping Servers (SQL Server)</span></span>
  <span data-ttu-id="9f215-103">보조 서버로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그 전달 구성에 대해 장애 조치(Failover)를 수행한 후에 주 데이터베이스로 작동하도록 보조 데이터베이스를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-103">After you have failed over a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log shipping configuration to a secondary server, you can configure your secondary database to act as the primary database.</span></span> <span data-ttu-id="9f215-104">그러면 필요할 때 주 데이터베이스와 보조 데이터베이스를 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-104">Then, you will be able to swap primary and secondary databases as needed.</span></span>  
  
## <a name="performing-the-initial-role-change"></a><span data-ttu-id="9f215-105">초기 역할 변경 수행</span><span class="sxs-lookup"><span data-stu-id="9f215-105">Performing the Initial Role Change</span></span>  
 <span data-ttu-id="9f215-106">처음으로 보조 데이터베이스로 장애 조치(Failover)를 하고 이 데이터베이스를 새로운 주 데이터베이스로 만들 때 일련의 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-106">The first time you want to fail over to the secondary database and make it your new primary database, there is a series of steps you must take.</span></span> <span data-ttu-id="9f215-107">이러한 초기 단계를 수행한 후에는 주 데이터베이스와 보조 데이터베이스의 역할을 쉽게 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-107">After you have followed these initial steps, you will be able to swap roles between the primary database and the secondary database easily.</span></span>  
  
1.  <span data-ttu-id="9f215-108">수동으로 주 데이터베이스에서 보조 데이터베이스로 장애 조치(Failover)를 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-108">Manually fail over from the primary database to a secondary database.</span></span> <span data-ttu-id="9f215-109">NORECOVERY를 사용하여 주 서버의 활성 트랜잭션 로그를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-109">Be sure to back up the active transaction log on your primary server with NORECOVERY.</span></span> <span data-ttu-id="9f215-110">자세한 내용은 [로그 전달 보조 데이터베이스로 장애 조치(failover)&#40;SQL Server&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9f215-110">For more information, see [Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="9f215-111">원래 주 서버에서 로그 전달 백업 작업을 비활성화하고 원래 보조 서버에서 복사 및 복원 작업을 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-111">Disable the log shipping backup job on the original primary server, and the copy and restore jobs on the original secondary server.</span></span>  
  
3.  <span data-ttu-id="9f215-112">새로운 주 데이터베이스로 만들 보조 데이터베이스에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 로그 전달을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-112">On your secondary database (the database you want to be the new primary), configure log shipping using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="9f215-113">자세한 내용은 [로그 전달 구성&#40;SQL Server&#41;](configure-log-shipping-sql-server.md)에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-113">For more information, see [Configure Log Shipping &#40;SQL Server&#41;](configure-log-shipping-sql-server.md).</span></span> <span data-ttu-id="9f215-114">다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-114">Include the following steps:</span></span>  
  
    1.  <span data-ttu-id="9f215-115">원래의 주 서버용으로 만든 공유와 같은 공유를 백업 생성에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-115">Use the same share for creating backups that you created for the original primary server.</span></span>  
  
    2.  <span data-ttu-id="9f215-116">보조 데이터베이스를 추가할 때 **보조 데이터베이스 설정** 대화 상자에서 **보조 데이터베이스** 상자에 원래의 주 데이터베이스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-116">When adding the secondary database, in the **Secondary Database Settings** dialog box, enter the name of the original primary database in the **Secondary database** box.</span></span>  
  
    3.  <span data-ttu-id="9f215-117">**보조 데이터베이스 설정** 대화 상자에서 **아니요, 보조 데이터베이스가 초기화되었습니다.** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-117">In the **Secondary Database Settings** dialog box, select **No, the secondary database is initialized**.</span></span>  
  
4.  <span data-ttu-id="9f215-118">이전 로그 전달 구성에서 로그 전달 모니터링을 사용하도록 설정한 경우에는 새 로그 전달 구성을 모니터링하도록 로그 전달 모니터링을 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-118">If log shipping monitoring was enabled on your former log shipping configuration, reconfigure log shipping monitoring to monitor the new log shipping configuration.</span></span>  <span data-ttu-id="9f215-119">*database_name* 을 사용자 데이터베이스 이름으로 바꾸어 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-119">Execute the following commands, replacing *database_name* with the name of your database:</span></span>  
  
    1.  <span data-ttu-id="9f215-120">**새 주 서버에서 다음을 수행합니다.**</span><span class="sxs-lookup"><span data-stu-id="9f215-120">**On the new primary server**</span></span>  
  
         <span data-ttu-id="9f215-121">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-121">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
        ```  
        -- Statement to execute on the new primary server  
        USE msdb  
        GO  
        EXEC master.dbo.sp_change_log_shipping_secondary_database @secondary_database = N'database_name', @threshold_alert_enabled = 0;  
        GO  
        ```  
  
    2.  <span data-ttu-id="9f215-122">**새 보조 서버에서 다음을 수행합니다.**</span><span class="sxs-lookup"><span data-stu-id="9f215-122">**On the new secondary server**</span></span>  
  
         <span data-ttu-id="9f215-123">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-123">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
        ```  
        -- Statement to execute on the new secondary server  
        USE msdb  
        GO  
        EXEC master.dbo.sp_change_log_shipping_primary_database @database=N'database_name', @threshold_alert_enabled = 0;  
        GO  
        ```  
  
## <a name="swapping-roles"></a><span data-ttu-id="9f215-124">역할 바꾸기</span><span class="sxs-lookup"><span data-stu-id="9f215-124">Swapping Roles</span></span>  
 <span data-ttu-id="9f215-125">초기 역할 변경을 위해 위의 단계를 완료한 후에 이 섹션의 단계에 따라 주 데이터베이스와 보조 데이터베이스의 역할을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-125">After you have completed the steps above for the initial role change, you can change roles between the primary database and the secondary database by following the steps in this section.</span></span> <span data-ttu-id="9f215-126">역할을 변경하려면 아래의 일반적인 단계를 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="9f215-126">To perform a role change, follow these general steps:</span></span>  
  
1.  <span data-ttu-id="9f215-127">보조 데이터베이스를 온라인 상태로 만들고 NORECOVERY를 사용하여 주 서버의 트랜잭션 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-127">Bring the secondary database online, backing up the transaction log on the primary server with NORECOVERY.</span></span>  
  
2.  <span data-ttu-id="9f215-128">원래 주 서버에서 로그 전달 백업 작업을 비활성화하고 원래 보조 서버에서 복사 및 복원 작업을 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-128">Disable the log shipping backup job on the original primary server, and the copy and restore jobs on the original secondary server.</span></span>  
  
3.  <span data-ttu-id="9f215-129">보조 서버(새로운 주 서버)의 로그 전달 백업 작업을 활성화하고 주 서버(새로운 보조 서버)의 복사 및 복원 작업을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-129">Enable the log shipping backup job on the secondary server (the new primary server), and the copy and restore jobs on the primary server (the new secondary server).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9f215-130">보조 데이터베이스를 주 데이터베이스로 변경하는 경우 사용자와 애플리케이션에 일관된 환경을 제공하려면 로그인, 작업 등 데이터베이스의 일부 또는 모든 메타데이터를 새로운 주 서버 인스턴스에서 다시 만들어야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f215-130">When you change a secondary database to the primary database, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins and jobs, on the new primary server instance.</span></span> <span data-ttu-id="9f215-131">자세한 내용은 [다른 서버 인스턴스에서 데이터베이스를 사용할 수 있도록 할 때 메타데이터 관리&#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9f215-131">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="9f215-132">관련 작업</span><span class="sxs-lookup"><span data-stu-id="9f215-132">Related Tasks</span></span>  
  
-   [<span data-ttu-id="9f215-133">로그 전달 보조 데이터베이스로 장애 조치(failover)&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9f215-133">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [<span data-ttu-id="9f215-134">역할 전환 후 로그인 및 작업 관리&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9f215-134">Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;</span></span>](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="9f215-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9f215-135">See Also</span></span>  
 [<span data-ttu-id="9f215-136">로그 전달 테이블 및 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="9f215-136">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
