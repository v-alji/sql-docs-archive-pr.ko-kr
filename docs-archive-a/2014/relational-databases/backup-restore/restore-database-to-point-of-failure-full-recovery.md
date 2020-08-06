---
title: 전체 복구 모델에서 오류 지점으로 데이터베이스 복원 (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- point of failure [SQL Server]
- restoring databases [SQL Server], point of failure
- database restores [SQL Server], point of failure
ms.assetid: 04106e18-bbf7-4a5e-a2e1-3d65319814d5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 95b73660ebb44f4daffe6eaefd873699cfbbd8ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650121"
---
# <a name="restore-a-database-to-the-point-of-failure-under-the-full-recovery-model-transact-sql"></a><span data-ttu-id="bff15-102">전체 복구 모델에서 특정 오류 지점으로 데이터베이스 복원(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="bff15-102">Restore a Database to the Point of Failure Under the Full Recovery Model (Transact-SQL)</span></span>
  <span data-ttu-id="bff15-103">이 항목에서는 실패한 지점으로 복원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bff15-103">This topic explains how to restore to the point of failure.</span></span> <span data-ttu-id="bff15-104">이 항목은 전체 복구 모델 또는 대량 로그 복구 모델을 사용하는 데이터베이스에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="bff15-104">The topic is relevant only for databases that are using the full or bulk-logged recovery models.</span></span>  
  
### <a name="to-restore-to-the-point-of-failure"></a><span data-ttu-id="bff15-105">실패한 지점으로 복원하려면</span><span class="sxs-lookup"><span data-stu-id="bff15-105">To restore to the point of failure</span></span>  
  
1.  <span data-ttu-id="bff15-106">다음의 기본 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 문을 실행하여 비상 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="bff15-106">Back up the tail of the log by running the following basic [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement:</span></span>  
  
    ```  
    BACKUP LOG <database_name> TO <backup_device>   
       WITH NORECOVERY, NO_TRUNCATE;  
    ```  
  
2.  <span data-ttu-id="bff15-107">다음의 기본 [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) 문을 실행하여 전체 데이터베이스 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="bff15-107">Restore a full database backup by running the following basic [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) statement:</span></span>  
  
    ```  
    RESTORE DATABASE <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
3.  <span data-ttu-id="bff15-108">필요에 따라 다음의 기본 RESTORE DATABASE 문을 실행하여 차등 데이터베이스 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="bff15-108">Optionally, restore a differential database backup by running the following basic RESTORE DATABASE statement:</span></span>  
  
    ```  
    RESTORE DATABASE <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
4.  <span data-ttu-id="bff15-109">RESTORE LOG 문에 WITH NORECOVERY를 지정하여 1단계에서 만든 비상 로그 백업을 포함하는 각 트랜잭션 로그를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="bff15-109">Apply each transaction log, including the tail-log backup you created in step 1, by specifying WITH NORECOVERY in the RESTORE LOG statement:</span></span>  
  
    ```  
    RESTORE LOG <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
5.  <span data-ttu-id="bff15-110">다음의 RESTORE DATABASE 문을 실행하여 데이터베이스를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="bff15-110">Recover the database by running the following RESTORE DATABASE statement:</span></span>  
  
    ```  
    RESTORE DATABASE <database_name>   
       WITH RECOVERY;  
    ```  
  
## <a name="example"></a><span data-ttu-id="bff15-111">예제</span><span class="sxs-lookup"><span data-stu-id="bff15-111">Example</span></span>  
 <span data-ttu-id="bff15-112">예를 실행하려면 우선 다음 준비를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bff15-112">Before you can run the example, you must complete the following preparations:</span></span>  
  
1.  <span data-ttu-id="bff15-113">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스의 기본 복구 모델은 단순 복구 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="bff15-113">The default recovery model of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database is the simple recovery model.</span></span> <span data-ttu-id="bff15-114">이 복구 모델에서는 실패한 지점에 대한 복원을 지원하지 않으므로 다음의 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ALTER DATABASE [문을 실행하여 전체 복구 모델을 사용하도록](/sql/t-sql/statements/alter-database-transact-sql) 를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bff15-114">Because this recovery model does not support restoring to the point of a failure, set [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] to use the full recovery model by running the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement:</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
    ```  
  
2.  <span data-ttu-id="bff15-115">다음 BACKUP 문을 사용하여 데이터베이스의 전체 데이터베이스 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bff15-115">Create a full database back of the database by using the following BACKUP statement:</span></span>  
  
    ```  
    BACKUP DATABASE AdventureWorks2012 TO DISK = 'C:\AdventureWorks2012_Data.bck';  
    ```  
  
3.  <span data-ttu-id="bff15-116">일상적인 로그 백업 생성:</span><span class="sxs-lookup"><span data-stu-id="bff15-116">Create a routine log backup:</span></span>  
  
    ```  
    BACKUP LOG AdventureWorks2012 TO DISK = 'C:\AdventureWorks2012_Log.bck';  
    ```  
  
 <span data-ttu-id="bff15-117">다음 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스의 비상 로그 백업을 만든 후 이전에 만들어진 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="bff15-117">The following example restores the backups that are created previously, after creating a tail-log backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="bff15-118">이 단계에서는 로그 디스크에 액세스할 수 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="bff15-118">(This step assumes that the log disk can be accessed.)</span></span>  
  
 <span data-ttu-id="bff15-119">우선 이 예에서는 활성 로그를 캡처하는 데이터베이스의 비상 로그 백업을 만들고 데이터베이스를 복원 중인 상태로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="bff15-119">First, the example creates a tail-log backup of the database that captures the active log and leaves the database in the Restoring state.</span></span> <span data-ttu-id="bff15-120">그런 다음 데이터베이스 백업을 복원하고 이전에 만든 일상적인 로그 백업을 적용한 후 비상 로그 백업을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="bff15-120">Then, the example restores the database backup, applies the routine log backup created previously, and applies the tail-log backup.</span></span> <span data-ttu-id="bff15-121">끝으로 별도의 단계로 데이터베이스를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="bff15-121">Finally, the example recovers the database in a separate step.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bff15-122">기본 동작은 최종 백업을 복원하는 문의 일부로 데이터베이스를 복구하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bff15-122">The default behavior is to recover a database as part of the statement that restores the final backup.</span></span>  
  
```  
/* Example of restoring a to the point of failure */  
-- Step 1: Create a tail-log backup by using WITH NORECOVERY.  
BACKUP LOG AdventureWorks2012  
   TO DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 2: Restore the full database backup.  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'C:\AdventureWorks2012_Data.bck'  
   WITH NORECOVERY;  
GO  
-- Step 3: Restore the first transaction log backup.  
RESTORE LOG AdventureWorks2012  
   FROM DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 4: Restore the tail-log backup.  
RESTORE LOG AdventureWorks2012  
   FROM  DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 5: Recover the database.  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="bff15-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bff15-123">See Also</span></span>  
 <span data-ttu-id="bff15-124">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bff15-124">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 [<span data-ttu-id="bff15-125">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bff15-125">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
