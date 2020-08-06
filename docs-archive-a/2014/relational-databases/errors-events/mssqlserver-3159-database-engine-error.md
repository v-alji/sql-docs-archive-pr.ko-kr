---
title: MSSQLSERVER_3159 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3159 (Database Engine error)
ms.assetid: c93c1003-0e3a-40aa-9873-44a0f5b8b57e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b469842b2aab15980c72ea01e46270c55ef29e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651022"
---
# <a name="mssqlserver_3159"></a><span data-ttu-id="1b511-102">MSSQLSERVER_3159</span><span class="sxs-lookup"><span data-stu-id="1b511-102">MSSQLSERVER_3159</span></span>
    
## <a name="details"></a><span data-ttu-id="1b511-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="1b511-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1b511-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="1b511-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="1b511-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="1b511-105">Event ID</span></span>|<span data-ttu-id="1b511-106">3159</span><span class="sxs-lookup"><span data-stu-id="1b511-106">3159</span></span>|  
|<span data-ttu-id="1b511-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="1b511-107">Event Source</span></span>|<span data-ttu-id="1b511-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1b511-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1b511-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="1b511-109">Component</span></span>|<span data-ttu-id="1b511-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1b511-110">SQLEngine</span></span>|  
|<span data-ttu-id="1b511-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="1b511-111">Symbolic Name</span></span>|<span data-ttu-id="1b511-112">LDDB_LOGNOTBACKEDUP</span><span class="sxs-lookup"><span data-stu-id="1b511-112">LDDB_LOGNOTBACKEDUP</span></span>|  
|<span data-ttu-id="1b511-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="1b511-113">Message Text</span></span>|<span data-ttu-id="1b511-114">데이터베이스 "%ls"의 비상 로그 백업이 수행되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="1b511-114">The tail of the log for the database "%ls" has not been backed up.</span></span> <span data-ttu-id="1b511-115">로그에 포함된 작업이 손실되지 않도록 하려면 BACKUP LOG WITH NORECOVERY를 사용하여 로그를 백업하십시오.</span><span class="sxs-lookup"><span data-stu-id="1b511-115">Use BACKUP LOG WITH NORECOVERY to back up the log if it contains work that you do not want to lose.</span></span> <span data-ttu-id="1b511-116">로그 내용을 덮어쓰려면 RESTORE 문에 WITH REPLACE나 WITH STOPAT 절을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="1b511-116">Use the WITH REPLACE or WITH STOPAT clause of the RESTORE statement to just overwrite the contents of the log.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1b511-117">설명</span><span class="sxs-lookup"><span data-stu-id="1b511-117">Explanation</span></span>  
 <span data-ttu-id="1b511-118">대부분의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 전체 또는 대량 로그 복구 모델을 사용할 경우 아직 백업되지 않은 로그 레코드를 캡처하기 위해 비상 로그 백업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b511-118">In most cases, under the full or bulk-logged recovery models, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requires that you back up the tail of the log to capture the log records that have not yet been backed up.</span></span> <span data-ttu-id="1b511-119">복원 작업 바로 전에 수행한 비상 로그의 로그 백업을 비상 로그 백업이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b511-119">A log backup taken of the tail of the log just before a restore operation is called a tail-log backup.</span></span>  
  
 <span data-ttu-id="1b511-120">데이터베이스를 실패 지점으로 복구할 때는 비상 로그 백업이 복구 계획의 마지막 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="1b511-120">When you are recovering a database to the point of a failure, the tail-log backup is the last backup of interest in the recovery plan.</span></span> <span data-ttu-id="1b511-121">비상 로그를 백업할 수 없으면 실패 전에 생성된 마지막 백업의 끝으로만 데이터베이스를 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b511-121">If you cannot back up the tail of the log, you can recover a database only to the end of the last backup that was created before the failure.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="1b511-122">에서는 일반적으로 데이터베이스를 복원하기 전에 비상 로그 백업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b511-122">usually requires that you take a tail-log backup before you start to restore a database.</span></span> <span data-ttu-id="1b511-123">비상 로그 백업은 작업 손실을 방지하고 로그 체인을 그대로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="1b511-123">The tail-log backup prevents work loss and keeps the log chain intact.</span></span> <span data-ttu-id="1b511-124">그러나 모든 복원 시나리오에서 비상 로그 백업이 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1b511-124">However, not all restore scenarios require a tail-log backup.</span></span> <span data-ttu-id="1b511-125">복구 지점이 이전 로그 백업에 포함된 경우 또는 데이터베이스를 이동 또는 대체(덮어쓰기)하는 중이고 가장 최근 백업 이후의 시점으로 이를 복원할 필요가 없는 경우에는 비상 로그 백업이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b511-125">You do not have to have a tail-log backup if the recovery point is included in an earlier log backup, or if you are moving or replacing (overwriting) the database and do not need to restore it to a point of time after the most recent backup.</span></span> <span data-ttu-id="1b511-126">또한 로그 파일이 손상되었고 비상 로그 백업을 만들 수 없으면 비상 로그 백업을 사용하지 않고 데이터베이스를 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b511-126">Also, if the log files are damaged and a tail-log backup cannot be created, you must restore the database without using a tail-log backup.</span></span> <span data-ttu-id="1b511-127">최신 로그 백업 이후 커밋된 모든 트랜잭션은 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b511-127">Any transactions committed after the latest log backup are lost.</span></span> <span data-ttu-id="1b511-128">자세한 내용은 이 항목의 뒷부분에 나오는 "비상 로그 백업을 사용하지 않고 복원"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1b511-128">For more information, see "Restoring Without Using a Tail-Log Backup," later in this topic.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="1b511-129">REPLACE는 신중한 검토 후에만 사용해야 하며 되도록 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b511-129">REPLACE should be used rarely, and only after careful consideration.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1b511-130">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="1b511-130">User Action</span></span>  
 <span data-ttu-id="1b511-131">비상 로그 백업을 수행하고 복원 작업을 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="1b511-131">Take a tail-log backup, and retry the restore operation.</span></span>  
  
 <span data-ttu-id="1b511-132">비상 로그를 백업할 수 없으면 RESTORE 문에 WITH STOPAT 또는 WITH REPLACE를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b511-132">If you cannot back up the tail of the log, use WITH STOPAT or WITH REPLACE in your RESTORE statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b511-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1b511-133">See Also</span></span>  
 <span data-ttu-id="1b511-134">[SQL Server 데이터베이스를 지정 시간으로 복원&#40;전체 복구 모델&#41;](../backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="1b511-134">[Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](../backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span></span>  
 <span data-ttu-id="1b511-135">[데이터베이스가 손상 된 경우 트랜잭션 로그를 백업 &#40;SQL Server&#41;](../backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1b511-135">[Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;](../backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md) </span></span>  
 <span data-ttu-id="1b511-136">[트랜잭션 로그 백업&#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1b511-136">[Back Up a Transaction Log &#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="1b511-137">비상 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1b511-137">Tail-Log Backups &#40;SQL Server&#41;</span></span>](../backup-restore/tail-log-backups-sql-server.md)  
  
  
