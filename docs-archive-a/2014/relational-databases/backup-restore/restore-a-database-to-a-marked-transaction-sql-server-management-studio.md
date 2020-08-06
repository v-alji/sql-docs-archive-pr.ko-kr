---
title: 데이터베이스를 표시된 트랜잭션으로 복원(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoretlog.markedtransaction.f1
helpviewer_keywords:
- database restores [SQL Server], marked transactions
- restoring databases [SQL Server], marked transactions
- marked transactions [SQL Server], restoring
ms.assetid: 8f0ea144-1819-4832-905f-e5d0f49b066b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8de9ef5bed389f020f14e60ccd99f39698e7110f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653464"
---
# <a name="restore-a-database-to-a-marked-transaction-sql-server-management-studio"></a><span data-ttu-id="afc6f-102">데이터베이스를 표시된 트랜잭션으로 복원(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="afc6f-102">Restore a Database to a Marked Transaction (SQL Server Management Studio)</span></span>
  <span data-ttu-id="afc6f-103">데이터베이스가 복원 상태인 경우 **트랜잭션 로그 복원** 대화 상자를 사용하여 사용 가능한 로그 백업에서 데이터베이스를 표시된 트랜잭션으로 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afc6f-103">When a database is in the restoring state, you can use the **Restore Transaction Log** dialog box to restore the database to a marked transaction in the available log backups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="afc6f-104">자세한 내용은 [표시된 트랜잭션을 사용하여 관련 데이터베이스를 일관되게 복구&#40;전체 복구 모델&#41;](use-marked-transactions-to-recover-related-databases-consistently.md) 및 [표시된 트랜잭션을 포함하는 관련 데이터베이스 복구](recovery-of-related-databases-that-contain-marked-transaction.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="afc6f-104">For more information, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md) and [Recovery of Related  Databases That Contain Marked Transaction](recovery-of-related-databases-that-contain-marked-transaction.md).</span></span>  
  
### <a name="to-restore-a-marked-transaction"></a><span data-ttu-id="afc6f-105">표시된 트랜잭션을 복원하려면</span><span class="sxs-lookup"><span data-stu-id="afc6f-105">To restore a marked transaction</span></span>  
  
1.  <span data-ttu-id="afc6f-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 후 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="afc6f-106">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="afc6f-107">**데이터베이스**를 확장하고 해당 데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스** 를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="afc6f-107">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="afc6f-108">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음 **복원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="afc6f-108">Right-click the database, point to **Tasks**, and then click **Restore**.</span></span>  
  
4.  <span data-ttu-id="afc6f-109">**트랜잭션 로그**를 클릭하여 **트랜잭션 로그 복원** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="afc6f-109">Click **Transaction Log**, which opens the **Restore Transaction Log** dialog box.</span></span>  
  
5.  <span data-ttu-id="afc6f-110">**일반** 페이지의 **복원 위치** 섹션에서 **표시된 트랜잭션**을 선택하여 **표시된 트랜잭션 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="afc6f-110">On the **General** page, in the **Restore To** section, select **Marked transaction**, which opens the **Select Marked Transaction** dialog box.</span></span> <span data-ttu-id="afc6f-111">이 대화 상자는 선택된 트랜잭션 로그 백업에서 사용할 수 있는 표시된 트랜잭션을 표로 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="afc6f-111">This dialog box displays a grid listing the marked transactions available in the selected transaction log backups.</span></span>  
  
     <span data-ttu-id="afc6f-112">기본적으로 표시된 트랜잭션 이전까지만 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="afc6f-112">By default, the restore is up to, but excluding, the marked transaction.</span></span> <span data-ttu-id="afc6f-113">표시된 트랜잭션도 복원하려면 **표시된 트랜잭션 포함**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="afc6f-113">To restore the marked transaction also, select **Include marked transaction**.</span></span>  
  
     <span data-ttu-id="afc6f-114">다음 표에서는 표의 열 머리글을 나열하고 해당 값을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="afc6f-114">The following table lists the column headers of the grid and describes their values.</span></span>  
  
    |<span data-ttu-id="afc6f-115">헤더</span><span class="sxs-lookup"><span data-stu-id="afc6f-115">Header</span></span>|<span data-ttu-id="afc6f-116">값</span><span class="sxs-lookup"><span data-stu-id="afc6f-116">Value</span></span>|  
    |------------|-----------|  
    |\<blank>|<span data-ttu-id="afc6f-117">표시 선택을 위한 확인란을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="afc6f-117">Displays a checkbox for selecting the mark.</span></span>|  
    |<span data-ttu-id="afc6f-118">**트랜잭션 표시**</span><span class="sxs-lookup"><span data-stu-id="afc6f-118">**Transaction Mark**</span></span>|<span data-ttu-id="afc6f-119">트랜잭션이 커밋될 때 사용자가 지정한 표시된 트랜잭션의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="afc6f-119">Name of the marked transaction specified by the user when the transaction was committed.</span></span>|  
    |<span data-ttu-id="afc6f-120">**Date**</span><span class="sxs-lookup"><span data-stu-id="afc6f-120">**Date**</span></span>|<span data-ttu-id="afc6f-121">트랜잭션이 커밋된 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="afc6f-121">Date and time of the transaction when it was committed.</span></span> <span data-ttu-id="afc6f-122">트랜잭션 날짜 및 시간은 클라이언트 컴퓨터의 날짜 및 시간이 아닌 **msdbgmarkhistory** 테이블에 기록된 날짜 및 시간으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="afc6f-122">Transaction date and time are displayed as recorded in the **msdbgmarkhistory** table, not in the client computer's date and time.</span></span>|  
    |<span data-ttu-id="afc6f-123">**설명**</span><span class="sxs-lookup"><span data-stu-id="afc6f-123">**Description**</span></span>|<span data-ttu-id="afc6f-124">트랜잭션이 커밋될 때 사용자가 지정한 표시된 트랜잭션에 대한 설명입니다(있는 경우).</span><span class="sxs-lookup"><span data-stu-id="afc6f-124">Description of marked transaction specified by the user when the transaction was committed (if any).</span></span>|  
    |<span data-ttu-id="afc6f-125">**LSN**</span><span class="sxs-lookup"><span data-stu-id="afc6f-125">**LSN**</span></span>|<span data-ttu-id="afc6f-126">표시된 트랜잭션의 로그 시퀀스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="afc6f-126">Log sequence number of the marked transaction.</span></span>|  
    |<span data-ttu-id="afc6f-127">**Database**</span><span class="sxs-lookup"><span data-stu-id="afc6f-127">**Database**</span></span>|<span data-ttu-id="afc6f-128">표시된 트랜잭션이 커밋된 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="afc6f-128">Name of the database where the marked transaction was committed.</span></span>|  
    |<span data-ttu-id="afc6f-129">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="afc6f-129">**User Name**</span></span>|<span data-ttu-id="afc6f-130">표시된 트랜잭션을 커밋한 데이터베이스 사용자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="afc6f-130">Name of the database user who committed the marked transaction.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="afc6f-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="afc6f-131">See Also</span></span>  
 <span data-ttu-id="afc6f-132">[데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="afc6f-132">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 [<span data-ttu-id="afc6f-133">트랜잭션 로그 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="afc6f-133">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
  
