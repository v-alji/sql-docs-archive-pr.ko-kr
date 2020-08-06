---
title: 로그 전달 보조 데이터베이스로 장애 조치(SQL Server) | Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- primary databases [SQL Server]
- secondary data files [SQL Server], manual fail over
- log shipping [SQL Server], failover
- failover [SQL Server], log shipping
ms.assetid: edfe5d59-4287-49c1-96c9-dd56212027bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 164e2809e4eff5a14ef54124df7c7ca9077793ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734419"
---
# <a name="fail-over-to-a-log-shipping-secondary-sql-server"></a><span data-ttu-id="08c18-102">로그 전달 보조 데이터베이스로 장애 조치(Failover)(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="08c18-102">Fail Over to a Log Shipping Secondary (SQL Server)</span></span>
  <span data-ttu-id="08c18-103">로그 전달 보조 데이터베이스로 장애 조치(Failover)는 주 서버 인스턴스에서 오류가 발생하거나 유지 관리가 필요한 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="08c18-103">Failing over to a log shipping secondary is useful if the primary server instance fails or requires maintenance.</span></span>  
  
## <a name="preparing-for-a-controlled-failover"></a><span data-ttu-id="08c18-104">제어된 장애 조치(Failover) 준비</span><span class="sxs-lookup"><span data-stu-id="08c18-104">Preparing for a Controlled Failover</span></span>  
 <span data-ttu-id="08c18-105">일반적으로 주 데이터베이스는 가장 최근의 백업 작업 이후 계속 업데이트되므로 주 데이터베이스와 보조 데이터베이스는 동기화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="08c18-105">Typically, the primary and secondary databases are unsynchronized, because the primary database continues to be updated after its latest backup job.</span></span> <span data-ttu-id="08c18-106">경우에 따라 최근 트랜잭션 로그 백업이 보조 서버 인스턴스로 복사되지 않았거나 복사된 일부 로그 백업이 보조 데이터베이스에 아직 적용되지 않았을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08c18-106">Also, in some cases, recent transaction log backups have not been copied to the secondary server instances, or some copied log backups might still not have been applied to the secondary database.</span></span> <span data-ttu-id="08c18-107">가능한 경우 먼저 모든 보조 데이터베이스를 주 데이터베이스와 동기화하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="08c18-107">We recommend that you begin by synchronizing all of the secondary databases with the primary database, if possible.</span></span>  
  
 <span data-ttu-id="08c18-108">로그 전달 작업에 대한 자세한 내용은 [로그 전달 정보&#40;SQL Server&#41;](about-log-shipping-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="08c18-108">For information about log shipping jobs, see [About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md).</span></span>  
  
## <a name="failing-over"></a><span data-ttu-id="08c18-109">장애 조치(Failover)</span><span class="sxs-lookup"><span data-stu-id="08c18-109">Failing Over</span></span>  
 <span data-ttu-id="08c18-110">보조 데이터베이스로 장애 조치(Failover)하려면</span><span class="sxs-lookup"><span data-stu-id="08c18-110">To fail over to a secondary database:</span></span>  
  
1.  <span data-ttu-id="08c18-111">백업 공유에서 복사되지 않은 백업 파일을 각 보조 서버의 복사 대상 폴더로 모두 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="08c18-111">Copy any uncopied backup files from the backup share to the copy destination folder of each secondary server.</span></span>  
  
2.  <span data-ttu-id="08c18-112">적용되지 않은 트랜잭션 로그 백업을 각 보조 데이터베이스에 순서대로 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="08c18-112">Apply any unapplied transaction log backups in sequence to each secondary database.</span></span> <span data-ttu-id="08c18-113">자세한 내용은 [트랜잭션 로그 백업 적용&#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="08c18-113">For more information, see [Apply Transaction Log Backups &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="08c18-114">주 데이터베이스에 액세스할 수 있으면 활성 트랜잭션 로그를 백업하여 이 로그 백업을 보조 데이터베이스에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="08c18-114">If the primary database is accessible, back up the active transaction log and apply the log backup to the secondary databases.</span></span>  
  
     <span data-ttu-id="08c18-115">원래 주 서버 인스턴스가 손상되지 않은 경우 WITH NORECOVERY를 사용하여 주 데이터베이스의 트랜잭션 비상 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="08c18-115">If the original primary server instance is not damaged, back up the tail of the transaction log of the primary database using WITH NORECOVERY.</span></span> <span data-ttu-id="08c18-116">이렇게 하면 데이터베이스가 복원 상태로 남아 있으므로 사용자가 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08c18-116">This leaves the database in the restoring state and therefore unavailable to users.</span></span> <span data-ttu-id="08c18-117">그러므로 대체 주 데이터베이스에서 트랜잭션 로그 백업을 적용하여 이 데이터베이스를 롤포워드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08c18-117">Eventually you will be able to roll this database forward by applying transaction log backups from the replacement primary database.</span></span>  
  
     <span data-ttu-id="08c18-118">자세한 내용은 [트랜잭션 로그 백업&#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="08c18-118">For more information, see [Transaction Log Backups &#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md).</span></span>  
  
4.  <span data-ttu-id="08c18-119">보조 서버가 동기화된 후 해당 보조 데이터베이스를 복구하고 해당 서버 인스턴스로 리디렉션하여 원하는 데이터베이스로 장애 조치(Failover)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08c18-119">After the secondary servers are synchronized, you can fail over to whichever one you prefer by recovering its secondary database and redirecting clients to that server instance.</span></span> <span data-ttu-id="08c18-120">복구하면 데이터베이스가 일관성 있는 온라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="08c18-120">Recovering puts the database into a consistent state and brings it online.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="08c18-121">보조 데이터베이스를 사용하는 경우 메타데이터가 원래 주 데이터베이스의 메타데이터와 일치하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08c18-121">When you make a secondary database available, you should ensure that its metadata is consistent with the metadata of the original primary database.</span></span> <span data-ttu-id="08c18-122">자세한 내용은 [다른 서버 인스턴스에서 데이터베이스를 사용할 수 있도록 할 때 메타데이터 관리&#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="08c18-122">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
5.  <span data-ttu-id="08c18-123">보조 데이터베이스를 복구한 후에는 다른 보조 데이터베이스에 대해 주 데이터베이스의 역할을 하도록 다시 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08c18-123">After you have recovered a secondary database, you can reconfigure it to act as a primary database for other secondary databases.</span></span>  
  
     <span data-ttu-id="08c18-124">다른 보조 데이터베이스를 사용하는 경우 [로그 전달 구성&#40;SQL Server&#41;](configure-log-shipping-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="08c18-124">If no other secondary database is available, see [Configure Log Shipping &#40;SQL Server&#41;](configure-log-shipping-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="08c18-125">관련 작업</span><span class="sxs-lookup"><span data-stu-id="08c18-125">Related Tasks</span></span>  
  
-   [<span data-ttu-id="08c18-126">주 로그 전달 서버와 보조 로그 전달 서버 간 역할 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="08c18-126">Change Roles Between Primary and Secondary Log Shipping Servers &#40;SQL Server&#41;</span></span>](change-roles-between-primary-and-secondary-log-shipping-servers-sql-server.md)  
  
-   [<span data-ttu-id="08c18-127">역할 전환 후 로그인 및 작업 관리&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="08c18-127">Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;</span></span>](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="08c18-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08c18-128">See Also</span></span>  
 <span data-ttu-id="08c18-129">[로그 전달 테이블 및 저장 프로시저](log-shipping-tables-and-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="08c18-129">[Log Shipping Tables and Stored Procedures](log-shipping-tables-and-stored-procedures.md) </span></span>  
 <span data-ttu-id="08c18-130">[로그 전달 정보&#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="08c18-130">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="08c18-131">비상 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="08c18-131">Tail-Log Backups &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/tail-log-backups-sql-server.md)  
  
  
