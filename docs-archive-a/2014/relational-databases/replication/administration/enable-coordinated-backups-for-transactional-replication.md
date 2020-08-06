---
title: 트랜잭션 복제에 대해 통합 백업 사용 (복제 Transact-sql 프로그래밍) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- transactional replication, backup and restore
- sp_replicationdboption
- sync with backup [SQL Server replication]
- coordinated backups [SQL Server replication]
- backups [SQL Server replication], transactional replication
ms.assetid: 73a914ba-8b2d-4f4d-ac1b-db9bac676a30
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 77405cd968fa917c3ccc799eb7d168782443eee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741884"
---
# <a name="enable-coordinated-backups-for-transactional-replication-replication-transact-sql-programming"></a><span data-ttu-id="d8311-102">트랜잭션 복제에 대해 통합 백업 사용(복제 Transact-SQL 프로그래밍)</span><span class="sxs-lookup"><span data-stu-id="d8311-102">Enable Coordinated Backups for Transactional Replication (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="d8311-103">트랜잭션 복제에 데이터베이스를 사용할 경우 모든 트랜잭션을 배포 데이터베이스에 배달하기 전에 반드시 백업하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8311-103">When enabling a database for transactional replication, you can specify that all transactions must be backed up before being delivered to the distribution database.</span></span> <span data-ttu-id="d8311-104">배포자에 전파된 트랜잭션이 백업될 때까지 게시 데이터베이스의 트랜잭션 로그가 잘리지 않도록 배포 데이터베이스에 통합 백업을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8311-104">You can also enable coordinated backup on the distribution database so that the transaction log for the publication database is not truncated until transactions that have been propagated to the Distributor have been backed up.</span></span> <span data-ttu-id="d8311-105">자세한 내용은 [스냅샷 및 트랜잭션 복제의 백업 및 복원을 위한 전략](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d8311-105">For more information, see [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).</span></span>  
  
### <a name="to-enable-coordinated-backups-for-a-database-published-with-transactional-replication"></a><span data-ttu-id="d8311-106">트랜잭션 복제를 사용하여 게시된 데이터베이스에 대해 통합 백업을 사용하도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="d8311-106">To enable coordinated backups for a database published with transactional replication</span></span>  
  
1.  <span data-ttu-id="d8311-107">게시자에서 [DATABASEPROPERTYEX&#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) 함수를 사용하여 게시 데이터베이스의 **IsSyncWithBackup** 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d8311-107">At the Publisher, use the [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) function to return the **IsSyncWithBackup** property of the publication database.</span></span> <span data-ttu-id="d8311-108">해당 함수에서 **1**을 반환하면 게시된 데이터베이스에 대해 통합 백업이 이미 사용되고 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d8311-108">If the function returns **1**, coordinated backups are already enabled for the published database.</span></span>  
  
2.  <span data-ttu-id="d8311-109">1단계의 해당 함수에서 **0**을 반환하면 게시 데이터베이스의 게시자에서 [sp_replicationdboption&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d8311-109">If the function in step 1 returns **0**, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="d8311-110">**\@optname**에 **sync with backup** 값을 지정하고 **\@value**에 **true** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8311-110">Specify a value of **sync with backup** for **\@optname**, and **true** for **\@value**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d8311-111">**sync with backup** 옵션을 **false**로 변경하면 로그 판독기 에이전트가 실행된 후 또는 한 번의 간격이 지난 후(로그 판독기 에이전트가 계속 실행되는 경우) 게시 데이터베이스의 잘린 부분이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8311-111">If you change the **sync with backup** option to **false**, the truncation point of the publication database will be updated after the Log Reader Agent runs, or after an interval if the Log Reader Agent is running continuously.</span></span> <span data-ttu-id="d8311-112">최대 간격은 기본값이 30초인 **MessageInterval** 에이전트 매개 변수로 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8311-112">The maximum interval is controlled by the **-MessageInterval** agent parameter (which has a default of 30 seconds).</span></span>  
  
### <a name="to-enable-coordinated-backups-for-a-distribution-database"></a><span data-ttu-id="d8311-113">배포 데이터베이스에 통합 백업을 사용하도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="d8311-113">To enable coordinated backups for a distribution database</span></span>  
  
1.  <span data-ttu-id="d8311-114">배포자에서 [DATABASEPROPERTYEX&#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) 함수를 사용하여 배포 데이터베이스의 **IsSyncWithBackup** 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d8311-114">At the Distributor, use the [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) function to return the **IsSyncWithBackup** property of the distribution database.</span></span> <span data-ttu-id="d8311-115">해당 함수에서 **1**을 반환하면 배포 데이터베이스에 대해 통합 백업이 이미 사용되고 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d8311-115">If the function returns **1**, coordinated backups are already enabled for the distribution database.</span></span>  
  
2.  <span data-ttu-id="d8311-116">1단계의 해당 함수에서 **0**을 반환하면 배포 데이터베이스의 배포자에서 [sp_replicationdboption&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d8311-116">If the function in step 1 returns **0**, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) at the Distributor on the distribution database.</span></span> <span data-ttu-id="d8311-117">\*\* \@ Optname\*\* 에 **sync with backup** 값을 지정 하 고 \*\* \@ 값\*\*으로 **true** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8311-117">Specify a value of **sync with backup** for **\@optname** and **true** for **\@value**.</span></span>  
  
### <a name="to-disable-coordinated-backups"></a><span data-ttu-id="d8311-118">통합 백업을 사용하지 않도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="d8311-118">To disable coordinated backups</span></span>  
  
1.  <span data-ttu-id="d8311-119">게시 데이터베이스의 게시자 또는 배포 데이터베이스의 배포자에서 [sp_replicationdboption&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d8311-119">At either the Publisher on the publication database or at the Distributor on the distribution database, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql).</span></span> <span data-ttu-id="d8311-120">**\@optname**에 **sync with backup** 값을 지정하고 **\@value**에 **false** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8311-120">Specify a value of **sync with backup** for **\@optname** and **false** for **\@value**.</span></span>  
  
  
