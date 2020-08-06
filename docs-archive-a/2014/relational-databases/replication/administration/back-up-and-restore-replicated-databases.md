---
title: 복제된 데이터베이스 백업 및 복원 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- backups [SQL Server replication]
- administering replication, restoring
- backing up replicated databases
- backups [SQL Server replication], about backups
- restoring replicated databases [SQL Server replication]
- recovery [SQL Server replication], about recovery
- restoring databases [SQL Server], replicated databases
- backing up databases [SQL Server], replicated databases
- restoring [SQL Server replication], about restoring
- recovery [SQL Server replication]
- replication [SQL Server], administering
- distribution databases [SQL Server replication], backing up
- restoring [SQL Server replication]
- administering replication, backing up
ms.assetid: 04588807-21e7-4bbe-9727-b72f692cffa7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e91505bacf67f7f4628bd1b3f6b2cc78a6bc4c3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651657"
---
# <a name="back-up-and-restore-replicated-databases"></a><span data-ttu-id="e8d84-102">복제된 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="e8d84-102">Back Up and Restore Replicated Databases</span></span>
  <span data-ttu-id="e8d84-103">복제된 데이터베이스의 경우 데이터를 백업 및 복원할 때 특별히 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d84-103">Replicated databases require special attention with regards to backing up and restoring data.</span></span> <span data-ttu-id="e8d84-104">이 항목에서는 각 복제 유형의 백업 및 복원 전략에 대한 기초 정보와 추가 정보 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d84-104">This topic provides introductory information and links to further information on backup and restore strategies for each type of replication.</span></span>  
  
 <span data-ttu-id="e8d84-105">복제에서는 복제된 데이터베이스를 백업이 생성된 서버 및 데이터베이스로 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8d84-105">Replication supports restoring replicated databases to the same server and database from which the backup was created.</span></span> <span data-ttu-id="e8d84-106">복제된 데이터베이스의 백업을 다른 서버 또는 데이터베이스로 복원할 경우 복제 설정은 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8d84-106">If you restore a backup of a replicated database to another server or database, replication settings cannot be preserved.</span></span> <span data-ttu-id="e8d84-107">이 경우 백업 복원 후 모든 게시 및 구독을 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d84-107">In this case, you must recreate all publications and subscriptions after backups are restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8d84-108">로그 전달을 사용하는 경우 복제된 데이터베이스를 대기 서버로 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8d84-108">It is possible to restore a replicated database to a standby server if log shipping is being used.</span></span> <span data-ttu-id="e8d84-109">자세한 내용은 [로그 전달 및 복제&#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8d84-109">For more information, see [Log Shipping and Replication &#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="e8d84-110">복제된 데이터베이스와 관련 시스템 데이터베이스를 정기적으로 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d84-110">Replicated databases and their associated system databases should be backed up regularly.</span></span> <span data-ttu-id="e8d84-111">다음 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d84-111">Back up the following databases:</span></span>  
  
-   <span data-ttu-id="e8d84-112">게시자의 게시 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="e8d84-112">The publication database at the Publisher</span></span>  
  
-   <span data-ttu-id="e8d84-113">배포자의 배포 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="e8d84-113">The distribution database at the Distributor</span></span>  
  
-   <span data-ttu-id="e8d84-114">구독자의 구독 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="e8d84-114">The subscription database at each Subscriber</span></span>  
  
-   <span data-ttu-id="e8d84-115">게시자, 배포자 및 모든 구독자의 **master** 및 **msdb** 시스템 데이터베이스.</span><span class="sxs-lookup"><span data-stu-id="e8d84-115">The **master** and **msdb** system databases at the Publisher, Distributor and all Subscribers.</span></span> <span data-ttu-id="e8d84-116">이러한 데이터베이스는 각각 그리고 관련 복제 데이터베이스와 동시에 백업되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d84-116">These databases should be backed up at the same time as each other and the relevant replication database.</span></span> <span data-ttu-id="e8d84-117">예를 들어 게시 데이터베이스를 백업할 때 게시자의 **master** 및 **msdb** 데이터베이스를 동시에 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d84-117">For example, back up the **master** and **msdb** databases at the Publisher at the same time you back up the publication database.</span></span> <span data-ttu-id="e8d84-118">게시 데이터베이스를 복원한 경우 **master** 및 **msdb** 데이터베이스의 복제 구성 및 설정이 게시 데이터베이스와 일치하는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="e8d84-118">If the publication database is restored, ensure that the **master** and **msdb** database are consistent with the publication database in terms of replication configuration and settings.</span></span>  
  
 <span data-ttu-id="e8d84-119">정기적인 로그 백업을 수행할 경우 모든 복제 관련 변경 내용은 로그 백업에 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8d84-119">If you perform regular log backups, any replication-related changes should be captured in the log backups.</span></span> <span data-ttu-id="e8d84-120">로그 백업을 수행하지 않는 경우 복제와 관련된 설정이 변경될 때마다 백업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d84-120">If you do not perform log backups, a backup should be performed whenever a setting relevant to replication is changed.</span></span> <span data-ttu-id="e8d84-121">자세한 내용은 [Common Actions Requiring an Updated Backup](common-actions-requiring-an-updated-backup.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8d84-121">For more information, see [Common Actions Requiring an Updated Backup](common-actions-requiring-an-updated-backup.md).</span></span>  
  
## <a name="backup-and-restore-strategies"></a><span data-ttu-id="e8d84-122">백업 및 복원 전략</span><span class="sxs-lookup"><span data-stu-id="e8d84-122">Backup and Restore Strategies</span></span>  
 <span data-ttu-id="e8d84-123">복제 토폴로지의 각 노드를 백업하고 복원하는 전략은 사용하는 복제 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e8d84-123">The strategies for backing up and restoring each node in a replication topology differ according to the type of replication used.</span></span> <span data-ttu-id="e8d84-124">각 복제 유형의 백업 및 복원 전략에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e8d84-124">For information on backup and restore strategies for each type of replication, see the following topics:</span></span>  
  
-   [<span data-ttu-id="e8d84-125">스냅샷 및 트랜잭션 복제의 백업 및 복원을 위한 전략</span><span class="sxs-lookup"><span data-stu-id="e8d84-125">Strategies for Backing Up and Restoring Snapshot and Transactional Replication</span></span>](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)  
  
-   [<span data-ttu-id="e8d84-126">병합 복제 백업 및 복원 전략</span><span class="sxs-lookup"><span data-stu-id="e8d84-126">Strategies for Backing Up and Restoring Merge Replication</span></span>](strategies-for-backing-up-and-restoring-merge-replication.md)  
  
 <span data-ttu-id="e8d84-127">어떤 복구 전략을 사용하는지에 관계없이 항상 현재 복제 설정 스크립트를 안전한 위치에 보관해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d84-127">As part of any recovery strategy, always keep a current script of your replication settings in a safe location.</span></span> <span data-ttu-id="e8d84-128">서버에 오류가 발생하거나 테스트 환경을 설정해야 할 때는 서버 이름 참조를 변경하여 스크립트를 수정하고 이를 사용하여 복제 설정을 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8d84-128">In the event of server failure or the need to set up a test environment, you can modify the script by changing server name references, and it can be used to help recreate your replication settings.</span></span> <span data-ttu-id="e8d84-129">현재 복제 설정을 스크립팅할 뿐만 아니라 복제의 활성화 및 비활성화도 스크립팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d84-129">In addition to scripting your current replication settings, you should script the enabling and disabling of replication.</span></span> <span data-ttu-id="e8d84-130">복제 개체 스크립팅에 대한 자세한 내용은 [Scripting Replication](../scripting-replication.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e8d84-130">For information about scripting replication objects, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d84-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e8d84-131">See Also</span></span>  
 <span data-ttu-id="e8d84-132">[SQL Server 데이터베이스 백업 및 복원](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="e8d84-132">[Back Up and Restore of SQL Server Databases](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="e8d84-133">Best Practices for Replication Administration</span><span class="sxs-lookup"><span data-stu-id="e8d84-133">Best Practices for Replication Administration</span></span>](best-practices-for-replication-administration.md)  
  
  
