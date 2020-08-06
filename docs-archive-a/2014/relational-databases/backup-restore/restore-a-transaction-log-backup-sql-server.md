---
title: 트랜잭션 로그 백업 복원(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoretlog.options.f1
- sql12.swb.restoretlog.general.f1
helpviewer_keywords:
- restore log
- backing up transaction logs [SQL Server], restoring
- transaction log backups [SQL Server], restoring
- restoring transaction logs [SQL Server], restoring backups
- transaction log restores [SQL Server], SQL Server Management Studio
ms.assetid: 1de2b888-78a6-4fb2-a647-ba4bf097caf3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 68fe4bbc199d6555bd490d25f92491100b8bbfcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653458"
---
# <a name="restore-a-transaction-log-backup-sql-server"></a><span data-ttu-id="39e39-102">트랜잭션 로그 백업 복원(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="39e39-102">Restore a Transaction Log Backup (SQL Server)</span></span>
  <span data-ttu-id="39e39-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 트랜잭션 로그 백업을 복원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-103">This topic describes how to restore a transaction log backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="39e39-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="39e39-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="39e39-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="39e39-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="39e39-106">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="39e39-106">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="39e39-107">보안</span><span class="sxs-lookup"><span data-stu-id="39e39-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="39e39-108">**트랜잭션 로그 백업을 복원하려면:**</span><span class="sxs-lookup"><span data-stu-id="39e39-108">**To restore a transaction log backup, using:**</span></span>  
  
     [<span data-ttu-id="39e39-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="39e39-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="39e39-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="39e39-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="39e39-111">관련 작업</span><span class="sxs-lookup"><span data-stu-id="39e39-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="39e39-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="39e39-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="39e39-113">필수 조건</span><span class="sxs-lookup"><span data-stu-id="39e39-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="39e39-114">백업은 만든 순서대로 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-114">Backups must be restored in the order in which they were created.</span></span> <span data-ttu-id="39e39-115">특정 트랜잭션 로그 백업을 복원하려면 먼저 커밋되지 않은 트랜잭션을 롤백하지 않고, 즉 WITH NORECOVERY로 다음과 같은 이전 백업을 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-115">Before you can restore a particular transaction log backup, you must first restore the following previous backups without rolling back uncommitted transactions, that is WITH NORECOVERY:</span></span>  
  
    -   <span data-ttu-id="39e39-116">특정 트랜잭션 로그 백업 이전에 수행된 전체 데이터베이스 백업 및 마지막 차등 백업(있는 경우)</span><span class="sxs-lookup"><span data-stu-id="39e39-116">The full database backup and the last differential backup, if any, taken before the particular transaction log backup.</span></span> <span data-ttu-id="39e39-117">가장 최근의 전체 또는 차등 데이터베이스 백업이 생성되기 전에 데이터베이스에 전체 복구 모델이나 대량 로그 복구 모델이 사용되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-117">Before the most recent full or differential database backup was created, the database must have been using the full recovery model or bulk-logged recovery model.</span></span>  
  
    -   <span data-ttu-id="39e39-118">전체 데이터베이스 백업이나 차등 백업 이후(복원하는 경우), 특정 트랜잭션 로그 백업 이전에 수행된 전체 트랜잭션 로그 백업</span><span class="sxs-lookup"><span data-stu-id="39e39-118">All transaction log backups taken after the full database backup or the differential backup (if you restore one) and before the particular transaction log backup.</span></span> <span data-ttu-id="39e39-119">로그 백업이 로그 체인에 따라 간격 없이 생성된 순서대로 적용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-119">Log backups must be applied in the sequence in which they were created, without any gaps in the log chain.</span></span>  
  
         <span data-ttu-id="39e39-120">트랜잭션 로그 백업에 대한 자세한 내용은 [트랜잭션 로그 백업&#40;SQL Server&#41;](transaction-log-backups-sql-server.md) 및 [트랜잭션 로그 백업 적용&#40;SQL Server&#41;](apply-transaction-log-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39e39-120">For more information about transaction log backups, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) and [Apply Transaction Log Backups &#40;SQL Server&#41;](apply-transaction-log-backups-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="39e39-121">보안</span><span class="sxs-lookup"><span data-stu-id="39e39-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="39e39-122">권한</span><span class="sxs-lookup"><span data-stu-id="39e39-122">Permissions</span></span>  
 <span data-ttu-id="39e39-123">멤버 자격 정보를 서버에서 항상 사용할 수 있는 역할에 RESTORE 권한이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-123">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="39e39-124">고정 데이터베이스 역할의 멤버 자격은 데이터베이스가 액세스 가능한 상태이며 손상되지 않은 경우에만 확인할 수 있는데, RESTORE 실행 시 데이터베이스가 항상 이러한 상태인 것은 아니므로 **db_owner** 고정 데이터베이스 역할의 멤버에게는 RESTORE 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-124">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="39e39-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="39e39-125">Using SQL Server Management Studio</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="39e39-126">일반적인 복원 프로세스는 데이터 백업 및 차등 백업과 함께 **데이터베이스 복원** 대화 상자에서 로그 백업을 선택하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-126">The normal process of a restore is to select the log backups in the **Restore Database** dialog box along with the data and differential backups.</span></span>  
  
#### <a name="to-restore-a-transaction-log-backup"></a><span data-ttu-id="39e39-127">트랜잭션 로그 백업을 복원하려면</span><span class="sxs-lookup"><span data-stu-id="39e39-127">To restore a transaction log backup</span></span>  
  
1.  <span data-ttu-id="39e39-128">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 후 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-128">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="39e39-129">**데이터베이스**를 확장하고 해당 데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스** 를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-129">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="39e39-130">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**, **복원**을 차례로 가리킨 다음 **트랜잭션 로그**를 클릭하여 **트랜잭션 로그 복원** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-130">Right-click the database, point to **Tasks**, point to **Restore**, and then click **Transaction Log**, which opens the **Restore Transaction Log** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="39e39-131">**트랜잭션 로그** 가 회색으로 표시되어 있는 경우에는 먼저 전체 또는 차등 백업을 복원해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-131">If **Transaction Log** is grayed out, you may need to restore a full or differential backup first.</span></span> <span data-ttu-id="39e39-132">**데이터베이스 백업** 대화 상자를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="39e39-132">Use the **Database** backup dialog box.</span></span>  
  
4.  <span data-ttu-id="39e39-133">**일반** 페이지의 **데이터베이스** 목록 상자에서 데이터베이스의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-133">On the **General** page, in the **Database** list box, select the name of a database.</span></span> <span data-ttu-id="39e39-134">복원 중인 상태의 데이터베이스만 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-134">Only databases in the restoring state are listed.</span></span>  
  
5.  <span data-ttu-id="39e39-135">복원할 백업 세트의 원본 및 위치를 지정하려면 다음 옵션 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-135">To specify the source and location of the backup sets to restore, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="39e39-136">**데이터베이스의 이전 백업 원본**</span><span class="sxs-lookup"><span data-stu-id="39e39-136">**From previous backups of database**</span></span>  
  
         <span data-ttu-id="39e39-137">복원할 데이터베이스를 드롭다운 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-137">Select the database to restore from the drop-down list.</span></span> <span data-ttu-id="39e39-138">목록에는 **msdb** 백업 기록에 따라 백업된 데이터베이스만 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-138">The list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    -   <span data-ttu-id="39e39-139">**파일 또는 테이프 원본**</span><span class="sxs-lookup"><span data-stu-id="39e39-139">**From file or tape**</span></span>  
  
         <span data-ttu-id="39e39-140">찾아보기( **...** ) 단추를 클릭하여 **백업 디바이스 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-140">Click the browse (**...**) button to open the **Select backup devices** dialog box.</span></span> <span data-ttu-id="39e39-141">**백업 미디어 유형** 상자에서 나열된 디바이스 유형 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-141">In the **Backup media type** box, select one of the listed device types.</span></span> <span data-ttu-id="39e39-142">**백업 미디어** 상자에 대해 하나 이상의 디바이스를 선택하려면 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-142">To select one or more devices for the **Backup media** box, click **Add**.</span></span>  
  
         <span data-ttu-id="39e39-143">원하는 디바이스를 **백업 미디어** 목록 상자에 추가한 후 **확인** 을 클릭하여 **일반** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-143">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
6.  <span data-ttu-id="39e39-144">**복원할 트랜잭션 로그 백업 선택** 표에서 복원할 백업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-144">In the **Select the transaction log backups to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="39e39-145">이 표에는 선택한 데이터베이스에 사용할 수 있는 트랜잭션 로그 백업이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-145">This grid lists the transaction log backups available for the selected database.</span></span> <span data-ttu-id="39e39-146">로그 백업은 **첫 번째 LSN** 이 데이터베이스의 **마지막 LSN** 보다 큰 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-146">A log backup is available only if its **First LSN** greater than the **Last LSN** of the database.</span></span> <span data-ttu-id="39e39-147">로그 백업은 포함된 LSN(로그 시퀀스 번호) 순서로 나열되며 이 순서로 복원되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-147">Log backups are listed in the order of the log sequence numbers (LSN) they contain, and they must be restored in this order.</span></span>  
  
     <span data-ttu-id="39e39-148">다음 표에서는 표의 열 머리글을 나열하고 해당 값을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-148">The following table lists the column headers of the grid and describes their values.</span></span>  
  
    |<span data-ttu-id="39e39-149">헤더</span><span class="sxs-lookup"><span data-stu-id="39e39-149">Header</span></span>|<span data-ttu-id="39e39-150">값</span><span class="sxs-lookup"><span data-stu-id="39e39-150">Value</span></span>|  
    |------------|-----------|  
    |<span data-ttu-id="39e39-151">**복원**</span><span class="sxs-lookup"><span data-stu-id="39e39-151">**Restore**</span></span>|<span data-ttu-id="39e39-152">선택된 확인란은 복원될 백업 세트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-152">Selected check boxes indicate the backup sets to be restored.</span></span>|  
    |<span data-ttu-id="39e39-153">**이름**</span><span class="sxs-lookup"><span data-stu-id="39e39-153">**Name**</span></span>|<span data-ttu-id="39e39-154">백업 세트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-154">Name of the backup set.</span></span>|  
    |<span data-ttu-id="39e39-155">**구성 요소**</span><span class="sxs-lookup"><span data-stu-id="39e39-155">**Component**</span></span>|<span data-ttu-id="39e39-156">백업된 구성 요소입니다. **데이터베이스**, **파일** 또는 \<blank>(트랜잭션 로그의 경우)가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-156">Backed-up component: **Database**, **File**, or \<blank> (for transaction logs).</span></span>|  
    |<span data-ttu-id="39e39-157">**Database**</span><span class="sxs-lookup"><span data-stu-id="39e39-157">**Database**</span></span>|<span data-ttu-id="39e39-158">백업 작업과 연관된 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-158">Name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="39e39-159">**Start Date**</span><span class="sxs-lookup"><span data-stu-id="39e39-159">**Start Date**</span></span>|<span data-ttu-id="39e39-160">클라이언트의 국가별 설정으로 표시되는 백업 작업 시작 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-160">Date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="39e39-161">**완료 날짜**</span><span class="sxs-lookup"><span data-stu-id="39e39-161">**Finish Date**</span></span>|<span data-ttu-id="39e39-162">클라이언트의 국가별 설정으로 표시되는 백업 작업 완료 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-162">Date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="39e39-163">**첫 번째 LSN**</span><span class="sxs-lookup"><span data-stu-id="39e39-163">**First LSN**</span></span>|<span data-ttu-id="39e39-164">백업 세트에 있는 첫 번째 트랜잭션의 로그 시퀀스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-164">Log sequence number of the first transaction in the backup set.</span></span> <span data-ttu-id="39e39-165">파일 백업의 경우 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-165">Blank for file backups.</span></span>|  
    |<span data-ttu-id="39e39-166">**마지막 LSN**</span><span class="sxs-lookup"><span data-stu-id="39e39-166">**Last LSN**</span></span>|<span data-ttu-id="39e39-167">백업 세트에 있는 마지막 트랜잭션의 로그 시퀀스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-167">Log sequence number of the last transaction in the backup set.</span></span> <span data-ttu-id="39e39-168">파일 백업의 경우 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-168">Blank for file backups.</span></span>|  
    |<span data-ttu-id="39e39-169">**검사점 LSN**</span><span class="sxs-lookup"><span data-stu-id="39e39-169">**Checkpoint LSN**</span></span>|<span data-ttu-id="39e39-170">백업 생성 시 가장 최근 검사점의 로그 시퀀스 번호</span><span class="sxs-lookup"><span data-stu-id="39e39-170">Log sequence number of the most recent checkpoint at the time the backup was created.</span></span>|  
    |<span data-ttu-id="39e39-171">**전체 LSN**</span><span class="sxs-lookup"><span data-stu-id="39e39-171">**Full LSN**</span></span>|<span data-ttu-id="39e39-172">가장 최근 전체 데이터베이스 백업의 로그 시퀀스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-172">Log sequence number of the most recent full database backup.</span></span>|  
    |<span data-ttu-id="39e39-173">**Server**</span><span class="sxs-lookup"><span data-stu-id="39e39-173">**Server**</span></span>|<span data-ttu-id="39e39-174">백업 작업을 수행한 데이터베이스 엔진 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-174">Name of the Database Engine instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="39e39-175">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="39e39-175">**User Name**</span></span>|<span data-ttu-id="39e39-176">백업 작업을 수행한 사용자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-176">Name of the user who performed the backup operation.</span></span>|  
    |<span data-ttu-id="39e39-177">**크기**</span><span class="sxs-lookup"><span data-stu-id="39e39-177">**Size**</span></span>|<span data-ttu-id="39e39-178">백업 세트의 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-178">Size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="39e39-179">**위치**</span><span class="sxs-lookup"><span data-stu-id="39e39-179">**Position**</span></span>|<span data-ttu-id="39e39-180">볼륨에 있는 백업 세트의 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-180">Position of the backup set in the volume.</span></span>|  
    |<span data-ttu-id="39e39-181">**만료**</span><span class="sxs-lookup"><span data-stu-id="39e39-181">**Expiration**</span></span>|<span data-ttu-id="39e39-182">백업 세트가 만료되는 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-182">Date and time the backup set expires.</span></span>|  
  
7.  <span data-ttu-id="39e39-183">다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-183">Select one of the following:</span></span>  
  
    -   <span data-ttu-id="39e39-184">**지정 시간**</span><span class="sxs-lookup"><span data-stu-id="39e39-184">**Point in time**</span></span>  
  
         <span data-ttu-id="39e39-185">기본값(**가장 최근**)을 유지하거나 찾아보기 단추를 클릭하여 표시된 **특정 시점 복원** 대화 상자에서 특정 날짜 및 시간을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-185">Either retain the default (**Most recent possible**) or select a specific date and time by clicking the browse button, which opens the **Point in Time Restore** dialog box.</span></span>  
  
    -   <span data-ttu-id="39e39-186">**표시된 트랜잭션**</span><span class="sxs-lookup"><span data-stu-id="39e39-186">**Marked transaction**</span></span>  
  
         <span data-ttu-id="39e39-187">데이터베이스를 이전에 표시된 트랜잭션으로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-187">Restore the database to a previously marked transaction.</span></span> <span data-ttu-id="39e39-188">이 옵션을 선택하면 **표시된 트랜잭션** 대화 상자가 시작됩니다. 이 대화 상자에는 선택한 트랜잭션 로그 백업에 사용할 수 있는 표시된 트랜잭션이 나열된 표가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-188">Selecting this option launches the **Select Marked Transaction** dialog box, which displays a grid listing the marked transactions available in the selected transaction log backups.</span></span>  
  
         <span data-ttu-id="39e39-189">기본적으로 표시된 트랜잭션 이전까지만 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-189">By default, the restore is up to, but excluding, the marked transaction.</span></span> <span data-ttu-id="39e39-190">표시된 트랜잭션도 복원하려면 **표시된 트랜잭션 포함**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-190">To restore the marked transaction also, select **Include marked transaction**.</span></span>  
  
         <span data-ttu-id="39e39-191">다음 표에서는 표의 열 머리글을 나열하고 해당 값을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-191">The following table lists the column headers of the grid and describes their values.</span></span>  
  
        |<span data-ttu-id="39e39-192">헤더</span><span class="sxs-lookup"><span data-stu-id="39e39-192">Header</span></span>|<span data-ttu-id="39e39-193">값</span><span class="sxs-lookup"><span data-stu-id="39e39-193">Value</span></span>|  
        |------------|-----------|  
        |\<blank>|<span data-ttu-id="39e39-194">표시 선택을 위한 확인란을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-194">Displays a checkbox for selecting the mark.</span></span>|  
        |<span data-ttu-id="39e39-195">**트랜잭션 표시**</span><span class="sxs-lookup"><span data-stu-id="39e39-195">**Transaction Mark**</span></span>|<span data-ttu-id="39e39-196">트랜잭션이 커밋될 때 사용자가 지정한 표시된 트랜잭션의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-196">Name of the marked transaction specified by the user when the transaction was committed.</span></span>|  
        |<span data-ttu-id="39e39-197">**Date**</span><span class="sxs-lookup"><span data-stu-id="39e39-197">**Date**</span></span>|<span data-ttu-id="39e39-198">트랜잭션이 커밋된 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-198">Date and time of the transaction when it was committed.</span></span> <span data-ttu-id="39e39-199">트랜잭션 날짜 및 시간은 클라이언트 컴퓨터의 날짜 및 시간이 아닌 **msdbgmarkhistory** 테이블에 기록된 날짜 및 시간으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-199">Transaction date and time are displayed as recorded in the **msdbgmarkhistory** table, not in the client computer's date and time.</span></span>|  
        |<span data-ttu-id="39e39-200">**설명**</span><span class="sxs-lookup"><span data-stu-id="39e39-200">**Description**</span></span>|<span data-ttu-id="39e39-201">트랜잭션이 커밋될 때 사용자가 지정한 표시된 트랜잭션에 대한 설명입니다(있는 경우).</span><span class="sxs-lookup"><span data-stu-id="39e39-201">Description of marked transaction specified by the user when the transaction was committed (if any).</span></span>|  
        |<span data-ttu-id="39e39-202">**LSN**</span><span class="sxs-lookup"><span data-stu-id="39e39-202">**LSN**</span></span>|<span data-ttu-id="39e39-203">표시된 트랜잭션의 로그 시퀀스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-203">Log sequence number of the marked transaction.</span></span>|  
        |<span data-ttu-id="39e39-204">**Database**</span><span class="sxs-lookup"><span data-stu-id="39e39-204">**Database**</span></span>|<span data-ttu-id="39e39-205">표시된 트랜잭션이 커밋된 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-205">Name of the database where the marked transaction was committed.</span></span>|  
        |<span data-ttu-id="39e39-206">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="39e39-206">**User Name**</span></span>|<span data-ttu-id="39e39-207">표시된 트랜잭션을 커밋한 데이터베이스 사용자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-207">Name of the database user who committed the marked transaction.</span></span>|  
  
8.  <span data-ttu-id="39e39-208">고급 옵션을 보거나 선택하려면 **페이지 선택** 창에서 **옵션** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-208">To view or select the advanced options, click **Options** in the **Select a page** pane.</span></span>  
  
9. <span data-ttu-id="39e39-209">**복원 옵션** 섹션에서 선택 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-209">In the **Restore options** section, the choices are:</span></span>  
  
    -   <span data-ttu-id="39e39-210">**복제 설정 유지(WITH KEEP_REPLICATION)**</span><span class="sxs-lookup"><span data-stu-id="39e39-210">**Preserve the replication settings (WITH KEEP_REPLICATION)**</span></span>  
  
         <span data-ttu-id="39e39-211">게시된 데이터베이스를 해당 데이터베이스가 생성된 서버 이외의 다른 서버로 복원할 경우 복제 설정을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-211">Preserves the replication settings when restoring a published database to a server other than the server where the database was created.</span></span>  
  
         <span data-ttu-id="39e39-212">이 옵션은 옵션을 사용 하 여 백업을 복원 하는 것과 같은 **커밋되지 않은 트랜잭션을 롤백하여 데이터베이스를 사용할 수 있는 상태로 유지** 합니다. 옵션 (뒷부분에서 설명)과 함께 사용할 수 있습니다. `RECOVERY`</span><span class="sxs-lookup"><span data-stu-id="39e39-212">This option is available only with the **Leave the database ready for use by rolling back the uncommitted transactions...** option (described later), which is equivalent to restoring a backup with the `RECOVERY` option.</span></span>  
  
         <span data-ttu-id="39e39-213">이 옵션을 선택 하는 것은 문에서 옵션을 사용 하는 것과 같습니다 `KEEP_REPLICATION` [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` .</span><span class="sxs-lookup"><span data-stu-id="39e39-213">Checking this option is equivalent to using the `KEEP_REPLICATION` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
    -   <span data-ttu-id="39e39-214">**각 백업 복원 전에 확인**</span><span class="sxs-lookup"><span data-stu-id="39e39-214">**Prompt before restoring each backup**</span></span>  
  
         <span data-ttu-id="39e39-215">첫 번째 복원 후 각 백업 세트를 복원하기 전에 이 옵션은 복원 시퀀스를 계속할지 여부를 묻는 **복원 계속** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-215">Before restoring each backup set (after the first), this option brings up the **Continue with Restore** dialog box, which asks you to indicate whether you want to continue the restore sequence.</span></span> <span data-ttu-id="39e39-216">이 대화 상자는 다음 미디어 세트(사용 가능한 경우)의 이름, 백업 세트 이름 및 백업 세트 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-216">This dialog displays the name of the next media set (if available), the backup set name, and backup set description.</span></span>  
  
         <span data-ttu-id="39e39-217">이 옵션은 다양한 미디어 세트의 테이프를 바꿔야 할 때 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-217">This option is particularly useful when you must swap tapes for different media sets.</span></span> <span data-ttu-id="39e39-218">예를 들어 서버에 한 개의 테이프 디바이스만 있을 때 이 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-218">For example, you can use it when the server has only one tape device.</span></span> <span data-ttu-id="39e39-219">**확인**을 클릭하기 전에 진행할 준비가 될 때까지 기다리세요.</span><span class="sxs-lookup"><span data-stu-id="39e39-219">Wait until you are ready to proceed before clicking **OK**.</span></span>  
  
         <span data-ttu-id="39e39-220">**아니요** 를 클릭하면 데이터베이스를 복원 중인 상태로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-220">Clicking **No** leaves the database in the restoring state.</span></span> <span data-ttu-id="39e39-221">사용자 편의를 위해 완료된 마지막 복원 다음에 복원 시퀀스를 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-221">At your convenience, you can continue the restore sequence after the last restore that completed.</span></span> <span data-ttu-id="39e39-222">다음 백업이 데이터 백업 또는 차등 백업인 경우 **데이터베이스 복원** 태스크를 다시 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="39e39-222">If the next backup is a data or differential backup, use the **Restore Database** task again.</span></span> <span data-ttu-id="39e39-223">다음 백업이 로그 백업인 경우 **트랜잭션 로그 복원** 태스크를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-223">If the next backup is a log backup, use the **Restore Transaction Log** task.</span></span>  
  
    -   <span data-ttu-id="39e39-224">**복원된 데이터베이스에 대한 액세스 제한(WITH RESTRICTED_USER)**</span><span class="sxs-lookup"><span data-stu-id="39e39-224">**Restrict access to the restored database (WITH RESTRICTED_USER)**</span></span>  
  
         <span data-ttu-id="39e39-225">**db_owner**, **dbcreator**또는 **sysadmin**의 멤버만 복원된 데이터베이스를 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-225">Makes the restored database available only to the members of **db_owner**, **dbcreator**, or **sysadmin**.</span></span>  
  
         <span data-ttu-id="39e39-226">이 옵션을 선택 하는 것은 문에서 옵션을 사용 하는 것과 같습니다 `RESTRICTED_USER` [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` .</span><span class="sxs-lookup"><span data-stu-id="39e39-226">Checking this option is synonymous to using the `RESTRICTED_USER` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
10. <span data-ttu-id="39e39-227">**복구 상태** 옵션에서 복원 작업 이후의 데이터베이스 상태를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-227">For the **Recovery state** options, specify the state of the database after the restore operation.</span></span>  
  
    -   <span data-ttu-id="39e39-228">**커밋되지 않은 트랜잭션을 롤백하여 데이터베이스를 사용할 수 있는 상태로 유지합니다. 추가 트랜잭션 로그를 복원할 수 없습니다. (RESTORE WITH RECOVERY)**</span><span class="sxs-lookup"><span data-stu-id="39e39-228">**Leave the database ready for use by rolling back uncommitted transactions. Additional transaction logs cannot be restored. (RESTORE WITH RECOVERY)**</span></span>  
  
         <span data-ttu-id="39e39-229">데이터베이스를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-229">Recovers the database.</span></span> <span data-ttu-id="39e39-230">이 옵션은 `RECOVERY` 문의 옵션과 동일 [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` 합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-230">This option is equivalent to the `RECOVERY` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
         <span data-ttu-id="39e39-231">복원할 로그 파일이 없는 경우에만 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-231">Choose this option only if you have no log files you want to restore.</span></span>  
  
    -   <span data-ttu-id="39e39-232">**데이터베이스를 비작동 상태로 유지하고 커밋되지 않은 트랜잭션을 롤백하지 않습니다. 추가 트랜잭션 로그를 복원할 수 (RESTORE WITH NORECOVERY)**</span><span class="sxs-lookup"><span data-stu-id="39e39-232">**Leave the database non-operational, and do not roll back uncommitted transactions. Additional transaction logs can be restored. (RESTORE WITH NORECOVERY)**</span></span>  
  
         <span data-ttu-id="39e39-233">데이터베이스를 복원되지 않은 `RESTORING` 상태로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-233">Leaves the database unrecovered, in the `RESTORING` state.</span></span> <span data-ttu-id="39e39-234">이 옵션은 문에서 옵션을 사용 하는 것과 같습니다 `NORECOVERY` [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` .</span><span class="sxs-lookup"><span data-stu-id="39e39-234">This option is equivalent to using the `NORECOVERY` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
         <span data-ttu-id="39e39-235">이 옵션을 선택하면 **복제 설정 유지** 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-235">When you choose this option, the **Preserve replication settings** option is unavailable.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="39e39-236">미러 또는 보조 데이터베이스의 경우 항상 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-236">For a mirror or secondary database, always select this option.</span></span>  
  
    -   <span data-ttu-id="39e39-237">**데이터베이스를 읽기 전용 모드로 유지합니다. 커밋되지 않은 트랜잭션 실행을 취소하지만 복구 결과를 되돌릴 수 있도록 실행 취소 동작을 파일에 (RESTORE WITH STANDBY)**</span><span class="sxs-lookup"><span data-stu-id="39e39-237">**Leave the database in read-only mode. Undo uncommitted transactions, but save the undo actions in a file so that recovery effects can be reversed. (RESTORE WITH STANDBY)**</span></span>  
  
         <span data-ttu-id="39e39-238">데이터베이스를 대기 모드로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-238">Leaves the database in a standby state.</span></span> <span data-ttu-id="39e39-239">이 옵션은 문에서 옵션을 사용 하는 것과 같습니다 `STANDBY` [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` .</span><span class="sxs-lookup"><span data-stu-id="39e39-239">This option is equivalent to using the `STANDBY` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
         <span data-ttu-id="39e39-240">이 옵션을 선택하려면 대기 파일을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-240">Choosing this option requires that you specify a standby file.</span></span>  
  
11. <span data-ttu-id="39e39-241">필요에 따라 **대기 파일** 입력란에 대기 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-241">Optionally, specify a standby file name in the **Standby file** text box.</span></span> <span data-ttu-id="39e39-242">데이터베이스를 읽기 전용 모드로 유지하는 경우 이 옵션이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-242">This option is required if you leave the database in read-only mode.</span></span> <span data-ttu-id="39e39-243">대기 파일을 찾아보거나 입력란에 해당 경로 이름을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-243">You can browse for the standby file or type its pathname in the text box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="39e39-244">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="39e39-244">Using Transact-SQL</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="39e39-245">모호하지 않도록 항상 모든 RESTORE 문에 명시적으로 WITH NORECOVERY 또는 WITH RECOVERY를 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-245">We recommend that you always explicitly specify either WITH NORECOVERY or WITH RECOVERY in every RESTORE statement to eliminate ambiguity.</span></span> <span data-ttu-id="39e39-246">이는 스크립트 작성 시 특히 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-246">This is particularly important when writing scripts.</span></span>  
  
#### <a name="to-restore-a-transaction-log-backup"></a><span data-ttu-id="39e39-247">트랜잭션 로그 백업을 복원하려면</span><span class="sxs-lookup"><span data-stu-id="39e39-247">To restore a transaction log backup</span></span>  
  
1.  <span data-ttu-id="39e39-248">RESTORE LOG 문을 실행하여 트랜잭션 로그 백업을 적용합니다. 이때 다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-248">Execute the RESTORE LOG statement to apply the transaction log backup, specifying:</span></span>  
  
    -   <span data-ttu-id="39e39-249">트랜잭션 로그가 적용될 데이터베이스의 이름</span><span class="sxs-lookup"><span data-stu-id="39e39-249">The name of the database to which the transaction log will be applied.</span></span>  
  
    -   <span data-ttu-id="39e39-250">트랜잭션 로그 백업이 복원될 백업 디바이스</span><span class="sxs-lookup"><span data-stu-id="39e39-250">The backup device where the transaction log backup will be restored from.</span></span>  
  
    -   <span data-ttu-id="39e39-251">NORECOVERY 절</span><span class="sxs-lookup"><span data-stu-id="39e39-251">The NORECOVERY clause.</span></span>  
  
     <span data-ttu-id="39e39-252">이 문의 기본 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-252">The basic syntax for this statement is as follows:</span></span>  
  
     <span data-ttu-id="39e39-253">RESTORE LOG *database_name* FROM <backup_device> WITH NORECOVERY.</span><span class="sxs-lookup"><span data-stu-id="39e39-253">RESTORE LOG *database_name* FROM <backup_device> WITH NORECOVERY.</span></span>  
  
     <span data-ttu-id="39e39-254">여기서 *database_name*은 데이터베이스의 이름이고 &lt;backup_device&gt;는 복원 중인 로그 백업이 포함된 디바이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-254">Where *database_name* is the name of database and <backup_device>is the name of the device that contains the log backup being restored.</span></span>  
  
2.  <span data-ttu-id="39e39-255">적용해야 할 각 트랜잭션 로그 백업에 대해 1단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-255">Repeat step 1 for each transaction log backup you have to apply.</span></span>  
  
3.  <span data-ttu-id="39e39-256">복원 시퀀스의 마지막 백업을 복원한 후 데이터베이스를 복구하려면 다음 문 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-256">After restoring the last backup in your restore sequence, to recover the database use one of the following statements:</span></span>  
  
    -   <span data-ttu-id="39e39-257">데이터베이스를 마지막 RESTORE LOG 문의 일부로 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-257">Recover the database as part of the last RESTORE LOG statement:</span></span>  
  
        ```  
        RESTORE LOG <database_name> FROM <backup_device> WITH RECOVERY;  
        GO  
        ```  
  
    -   <span data-ttu-id="39e39-258">별도의 RESTORE DATABASE 문을 사용하여 데이터베이스를 복구할 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-258">Wait to recover the database by using a separate RESTORE DATABASE statement:</span></span>  
  
        ```  
        RESTORE LOG <database_name> FROM <backup_device> WITH NORECOVERY;   
        RESTORE DATABASE <database_name> WITH RECOVERY;  
        GO  
        ```  
  
         <span data-ttu-id="39e39-259">데이터베이스를 복구할 때까지 기다리면 필요한 모든 로그 백업을 복원했는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-259">Waiting to recover the database gives you the opportunity to verify that you have restored all of the necessary log backups.</span></span> <span data-ttu-id="39e39-260">이 방법은 지정 시간 복원을 수행할 때 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-260">This approach is often advisable when you are performing a point-in-time restore.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="39e39-261">미러 데이터베이스를 만드는 경우 복구 단계를 생략하세요.</span><span class="sxs-lookup"><span data-stu-id="39e39-261">If you are creating a mirror database, omit the recovery step.</span></span> <span data-ttu-id="39e39-262">미러 데이터베이스는 RESTORING 상태로 유지되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-262">A mirror database must remain in the RESTORING state.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="39e39-263">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="39e39-263">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="39e39-264">기본적으로 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스는 단순 복구 모델을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-264">By default, the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database uses the simple recovery model.</span></span> <span data-ttu-id="39e39-265">다음 예에서는 전체 복구 모델을 사용하도록 데이터베이스를 다음과 같이 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-265">The following examples require modifying the database to use the full recovery model, as follows:</span></span>  
  
```sql  
ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
```  
  
#### <a name="a-applying-a-single-transaction-log-backup"></a><span data-ttu-id="39e39-266">A.</span><span class="sxs-lookup"><span data-stu-id="39e39-266">A.</span></span> <span data-ttu-id="39e39-267">단일 트랜잭션 로그 백업 적용</span><span class="sxs-lookup"><span data-stu-id="39e39-267">Applying a single transaction log backup</span></span>  
 <span data-ttu-id="39e39-268">다음 예에서는 먼저 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 이라는 백업 디바이스에 상주하는 전체 데이터베이스 백업을 사용하여 `AdventureWorks2012_1`데이터베이스를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-268">The following example starts by restoring the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database by using a full database backup that resides on a backup device named `AdventureWorks2012_1`.</span></span> <span data-ttu-id="39e39-269">그런 다음 `AdventureWorks2012_log`라는 백업 디바이스에 상주하는 첫 번째 트랜잭션 로그 백업을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-269">The example then applies the first transaction log backup that resides on a backup device named `AdventureWorks2012_log`.</span></span> <span data-ttu-id="39e39-270">마지막으로 데이터베이스를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-270">Finally, the example recovers the database.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012  
   FROM AdventureWorks2012_1  
   WITH NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 1,  
   WITH NORECOVERY;  
GO  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY;  
GO  
```  
  
#### <a name="b-applying-multiple-transaction-log-backups"></a><span data-ttu-id="39e39-271">B.</span><span class="sxs-lookup"><span data-stu-id="39e39-271">B.</span></span> <span data-ttu-id="39e39-272">여러 트랜잭션 로그 백업 적용</span><span class="sxs-lookup"><span data-stu-id="39e39-272">Applying multiple transaction log backups</span></span>  
 <span data-ttu-id="39e39-273">다음 예에서는 먼저 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 이라는 백업 디바이스에 상주하는 전체 데이터베이스 백업을 사용하여 `AdventureWorks2012_1`데이터베이스를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-273">The following example starts by restoring the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database by using a full database backup that resides on a backup device named `AdventureWorks2012_1`.</span></span> <span data-ttu-id="39e39-274">그런 다음 `AdventureWorks2012_log`라는 백업 디바이스에 상주하는 처음 3개의 트랜잭션 로그 백업을 하나씩 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-274">The example then applies, one by one, the first three transaction log backups that reside on a backup device named `AdventureWorks2012_log`.</span></span> <span data-ttu-id="39e39-275">마지막으로 데이터베이스를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="39e39-275">Finally, the example recovers the database.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012  
   FROM AdventureWorks2012_1  
   WITH NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 1,  
   NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 2,  
   WITH NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 3,  
   WITH NORECOVERY;  
GO  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="39e39-276">관련 작업</span><span class="sxs-lookup"><span data-stu-id="39e39-276">Related Tasks</span></span>  
  
-   [<span data-ttu-id="39e39-277">트랜잭션 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="39e39-277">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="39e39-278">데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="39e39-278">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="39e39-279">전체 복구 모델에서 특정 오류 지점으로 데이터베이스 복원&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="39e39-279">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="39e39-280">SQL Server 데이터베이스를 지정 시간으로 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="39e39-280">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   [<span data-ttu-id="39e39-281">데이터베이스를 표시된 트랜잭션으로 복원&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="39e39-281">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="39e39-282">참고 항목</span><span class="sxs-lookup"><span data-stu-id="39e39-282">See Also</span></span>  
 <span data-ttu-id="39e39-283">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="39e39-283">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="39e39-284">트랜잭션 로그 백업 적용&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="39e39-284">Apply Transaction Log Backups &#40;SQL Server&#41;</span></span>](apply-transaction-log-backups-sql-server.md)  
  
  
