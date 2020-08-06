---
title: 백업에서 트랜잭션 구독 초기화 (복제 Transact-sql 프로그래밍) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: d0637fc4-27cc-4046-98ea-dc86b7a3bd75
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1563d58f2d54f77680781e22a162112ade1658e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646875"
---
# <a name="initialize-a-transactional-subscription-from-a-backup-replication-transact-sql-programming"></a><span data-ttu-id="7a842-102">백업에서 트랜잭션 구독 초기화(복제 Transact-SQL 프로그래밍)</span><span class="sxs-lookup"><span data-stu-id="7a842-102">Initialize a Transactional Subscription from a Backup (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="7a842-103">일반적으로 트랜잭션 게시에 대한 구독은 스냅샷을 사용하여 초기화하지만 복제 저장 프로시저를 사용하여 백업에서 구독을 초기화할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-103">Although a subscription to a transactional publication is typically initialized with a snapshot, a subscription can be initialized from a backup using replication stored procedures.</span></span> <span data-ttu-id="7a842-104">자세한 내용은 [스냅샷 없이 트랜잭션 구독 초기화](initialize-a-transactional-subscription-without-a-snapshot.md)에서 수동으로 구독을 초기화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-104">For more information, see [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
### <a name="to-initialize-a-transactional-subscriber-from-a-backup"></a><span data-ttu-id="7a842-105">백업에서 트랜잭션 구독자를 초기화하려면</span><span class="sxs-lookup"><span data-stu-id="7a842-105">To initialize a transactional subscriber from a backup</span></span>  
  
1.  <span data-ttu-id="7a842-106">기존 게시의 경우 게시 데이터베이스의 게시자에서 [sp_helppublication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)을 실행하여 게시가 백업에서 초기화하는 기능을 지원하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-106">For an existing publication, ensure that the publication supports the ability to initialize from backup by executing [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="7a842-107">결과 집합에서 **allow_initialize_from_backup** 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-107">Note the value of **allow_initialize_from_backup** in the result set.</span></span>  
  
    -   <span data-ttu-id="7a842-108">값이 **1**이면 게시에서 이 기능을 지원하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-108">If the value is **1**, the publication supports this functionality.</span></span>  
  
    -   <span data-ttu-id="7a842-109">값이 **0**이면 게시 데이터베이스의 게시자에서 [sp_changepublication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-109">If the value is **0**, execute [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="7a842-110">\*\* \@ 속성\*\* 에 **allow_initialize_from_backup** 값을 지정 하 고 값에 값을 지정 `true` 합니다 \*\* \@ \*\*.</span><span class="sxs-lookup"><span data-stu-id="7a842-110">Specify a value of **allow_initialize_from_backup** for **\@property** and a value of `true` for **\@value**.</span></span>  
  
2.  <span data-ttu-id="7a842-111">새 게시의 경우 게시 데이터베이스의 게시자에서 [sp_addpublication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-111">For a new publication, execute [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="7a842-112">Allow_initialize_from_backup에 값을 `true` 지정 **allow_initialize_from_backup**합니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-112">Specify a value of `true` for **allow_initialize_from_backup**.</span></span> <span data-ttu-id="7a842-113">자세한 내용은 [게시 만들기](publish/create-a-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7a842-113">For more information, see [Create a Publication](publish/create-a-publication.md).</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="7a842-114">구독자 데이터가 누락되는 것을 방지하려면 **에서** sp_addpublication `@allow_initialize_from_backup = N'true'`을 사용할 때 항상 `@immediate_sync = N'true'`를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="7a842-114">To avoid missing subscriber data, when using **sp_addpublication** with `@allow_initialize_from_backup = N'true'`, always use `@immediate_sync = N'true'`.</span></span>  
  
3.  <span data-ttu-id="7a842-115">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) 문을 사용하여 게시 데이터베이스의 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-115">Create a backup of the publication database using the [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) statement.</span></span>  
  
4.  <span data-ttu-id="7a842-116">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) 문을 사용하여 구독자에서 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-116">Restore the backup on the Subscriber using the [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) statement.</span></span>  
  
5.  <span data-ttu-id="7a842-117">게시 데이터베이스의 게시자에서 [sp_addsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) 저장 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-117">At the Publisher on the publication database, execute the stored procedure [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span> <span data-ttu-id="7a842-118">다음 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-118">Specify the following parameters:</span></span>  
  
    -   <span data-ttu-id="7a842-119">\*\* \@ sync_type\*\* - **initialize with backup**값</span><span class="sxs-lookup"><span data-stu-id="7a842-119">**\@sync_type** - a value of **initialize with backup**.</span></span>  
  
    -   <span data-ttu-id="7a842-120">\*\* \@ backupdevicetype\*\* -백업 장치의 유형: **논리** (기본값), **디스크**또는 **테이프**입니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-120">**\@backupdevicetype** - the type of backup device: **logical** (default), **disk**, or **tape**.</span></span>  
  
    -   <span data-ttu-id="7a842-121">\*\* \@ backupdevicename\*\* 이름-복원에 사용할 논리적 또는 물리적 백업 장치입니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-121">**\@backupdevicename** - the logical or physical backup device to use for the restore.</span></span>  
  
         <span data-ttu-id="7a842-122">논리적 디바이스의 경우 **sp_addumpdevice** 를 사용하여 디바이스를 만들 때 지정한 백업 디바이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-122">For a logical device, specify the name of the backup device specified when **sp_addumpdevice** was used to create the device.</span></span>  
  
         <span data-ttu-id="7a842-123">물리적 디바이스의 경우 `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\BACKUP\Mybackup.dat'` 또는 `TAPE = '\\.\TAPE0'`과 같이 전체 경로와 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-123">For a physical device, specify a complete path and file name, such as `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\BACKUP\Mybackup.dat'` or `TAPE = '\\.\TAPE0'`.</span></span>  
  
    -   <span data-ttu-id="7a842-124">필드 \*\* \@ 암호\*\* -백업 세트를 만들 때 제공한 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-124">(Optional) **\@password** - a password that was provided when the backup set was created.</span></span>  
  
    -   <span data-ttu-id="7a842-125">필드 \*\* \@ mediapassword\*\* -미디어 세트를 포맷할 때 제공한 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-125">(Optional) **\@mediapassword** - a password that was provided when the media set was formatted.</span></span>  
  
    -   <span data-ttu-id="7a842-126">필드 \*\* \@ fileidhint\*\* -복원할 백업 세트에 대 한 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-126">(Optional) **\@fileidhint** - identifier for the backup set to be restored.</span></span> <span data-ttu-id="7a842-127">예를 들어 **1** 을 지정하면 백업 미디어의 첫 번째 백업 세트를 나타내고 **2** 를 지정하면 두 번째 백업 세트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-127">For example, specifying **1** indicates the first backup set on the backup medium and **2** indicates the second backup set.</span></span>  
  
    -   <span data-ttu-id="7a842-128">(테이프 장치에 대 한 선택 사항) \*\* \@ unload\*\* -복원이 완료 된 후 드라이브에서 테이프를 언로드해야 하는 경우 **1** (기본값) 값을 지정 하 고, 그렇지 않으면 **0** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-128">(Optional for tape devices) **\@unload** - specify a value of **1** (default) if the tape should be unloaded from the drive after the restore is complete and **0** if it should not be unloaded.</span></span>  
  
6.  <span data-ttu-id="7a842-129">(옵션) 끌어오기 구독의 경우 구독 데이터베이스의 구독자에서 [sp_addpullsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql) 및 [sp_addpullsubscription_agent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-129">(Optional) For a pull subscription, execute [sp_addpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql) and [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) at the Subscriber on the subscription database.</span></span> <span data-ttu-id="7a842-130">자세한 내용은 [끌어오기 구독 만들기](create-a-pull-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7a842-130">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
7.  <span data-ttu-id="7a842-131">(옵션) 배포 에이전트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="7a842-131">(Optional) Start the Distribution Agent.</span></span> <span data-ttu-id="7a842-132">자세한 내용은 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md) 또는 [Synchronize a Push Subscription](synchronize-a-push-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7a842-132">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md) or [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a842-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7a842-133">See Also</span></span>  
 <span data-ttu-id="7a842-134">[백업 및 복원으로 데이터베이스 복사](../databases/copy-databases-with-backup-and-restore.md) </span><span class="sxs-lookup"><span data-stu-id="7a842-134">[Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md) </span></span>  
 [<span data-ttu-id="7a842-135">SQL Server 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="7a842-135">Back Up and Restore of SQL Server Databases</span></span>](../backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  
