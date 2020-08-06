---
title: 대량 가져오기의 최소 로깅을 위한 필수 조건 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- minimal logging [SQL Server]
- logged bulk copy [SQL Server]
- logs [SQL Server], minimal logging
- minimally logged operations [SQL Server]
- bulk importing [SQL Server], minimal logging
ms.assetid: bd1dac6b-6ef8-4735-ad4e-67bb42dc4f66
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4711e25dcfcc99e14894e47166638673c61a6831
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741044"
---
# <a name="prerequisites-for-minimal-logging-in-bulk-import"></a><span data-ttu-id="63abd-102">Prerequisites for Minimal Logging in Bulk Import</span><span class="sxs-lookup"><span data-stu-id="63abd-102">Prerequisites for Minimal Logging in Bulk Import</span></span>
  <span data-ttu-id="63abd-103">전체 복구 모델을 사용하는 데이터베이스의 경우 대량 가져오기로 수행되는 모든 행 삽입 작업이 트랜잭션 로그에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-103">For a database under the full recovery model, all row-insert operations that are performed by bulk import are fully logged in the transaction log.</span></span> <span data-ttu-id="63abd-104">전체 복구 모델을 사용할 경우 많은 양의 데이터를 가져오면 트랜잭션 로그가 빨리 채워질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-104">Large data imports can cause the transaction log to fill rapidly if the full recovery model is used.</span></span> <span data-ttu-id="63abd-105">이와 달리 단순 복구 모델 또는 대량 로그 복구 모델에서 대량 가져오기 작업의 로깅을 최소화하면 대량 가져오기 작업에 의해 로그 공간이 채워질 가능성이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-105">In contrast, under the simple recovery model or bulk-logged recovery model, minimal logging of bulk-import operations reduces the possibility that a bulk-import operation will fill the log space.</span></span> <span data-ttu-id="63abd-106">또한 최소 로깅은 전체 로깅보다 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-106">Minimal logging is also more efficient than full logging.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63abd-107">대량 로그 복구 모델은 대규모의 대량 작업 중에 전체 복구 모델을 임시로 대체하기 위해 고안된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-107">The bulk-logged recovery model is designed to temporarily replace the full recovery model during large bulk operations.</span></span>  
  
## <a name="table-requirements-for-minimally-logging-bulk-import-operations"></a><span data-ttu-id="63abd-108">대량 가져오기 작업의 최소 로깅을 위한 테이블 요구 사항</span><span class="sxs-lookup"><span data-stu-id="63abd-108">Table Requirements for Minimally Logging Bulk-Import Operations</span></span>  
 <span data-ttu-id="63abd-109">최소 로깅에서 대상 테이블은 다음 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-109">Minimal logging requires that the target table meets the following conditions:</span></span>  
  
-   <span data-ttu-id="63abd-110">테이블이 복제되고 있지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-110">The table is not being replicated.</span></span>  
  
-   <span data-ttu-id="63abd-111">테이블 잠금이 지정되어야 합니다(TABLOCK 사용).</span><span class="sxs-lookup"><span data-stu-id="63abd-111">Table locking is specified (using TABLOCK).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63abd-112">대량 가져오기 작업을 최소 로깅으로 수행하는 동안 데이터 삽입은 트랜잭션 로그에 기록되지 않지만 새 익스텐트를 테이블에 할당할 때마다 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 익스텐트 할당을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-112">Although data insertions are not logged in the transaction log during a minimally logged bulk-import operation, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] still logs extent allocations each time a new extent is allocated to the table.</span></span>  
  
-   <span data-ttu-id="63abd-113">메모리 최적화 테이블이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-113">Table is not a memory-optimized table.</span></span>  
  
 <span data-ttu-id="63abd-114">테이블에 대한 최소 로깅의 발생 여부는 다음과 같이 테이블의 인덱싱 여부에 따라 달라지고, 테이블이 인덱싱되는 경우 테이블이 비어 있는지 여부에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-114">Whether minimal logging can occur for a table also depends on whether the table is indexed and, if so, whether the table is empty:</span></span>  
  
-   <span data-ttu-id="63abd-115">테이블에 인덱스가 없는 경우 데이터 페이지가 최소 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-115">If the table has no indexes, data pages are minimally logged.</span></span>  
  
-   <span data-ttu-id="63abd-116">테이블에 클러스터형 인덱스는 없지만 하나 이상의 비클러스터형 인덱스가 있는 경우 데이터 페이지는 항상 최소 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-116">If the table has no clustered index but has one or more nonclustered indexes, data pages are always minimally logged.</span></span> <span data-ttu-id="63abd-117">그러나 인덱스 페이지 로깅 방법은 다음과 같이 테이블이 비어 있는지 여부에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-117">How index pages are logged, however, depends on whether the table is empty:</span></span>  
  
    -   <span data-ttu-id="63abd-118">테이블이 비어 있는 경우 인덱스 페이지가 최소 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-118">If the table is empty, index pages are minimally logged.</span></span>  
  
    -   <span data-ttu-id="63abd-119">테이블이 비어 있지 않은 경우 인덱스 페이지가 모두 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-119">If table is non-empty, index pages are fully logged.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="63abd-120">빈 테이블로 시작하여 데이터 대량 가져오기를 다중 일괄 처리로 수행하는 경우 첫 번째 일괄 처리에서는 인덱스 및 데이터 페이지가 최소 로깅되지만 두 번째 일괄 처리부터는 데이터 페이지만 최소 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-120">If you start with an empty table and bulk import the data in multiple batches, both index and data pages are minimally logged for the first batch, but beginning with the second batch, only data pages are minimally logged.</span></span>  
  
-   <span data-ttu-id="63abd-121">테이블에 클러스터형 인덱스가 있고 비어 있는 경우 데이터 및 인덱스 페이지가 모두 최소 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-121">If the table has a clustered index and is empty, both data and index pages are minimally logged.</span></span> <span data-ttu-id="63abd-122">이와 달리 테이블에 클러스터형 인덱스가 있고 비어 있지 않은 경우 데이터 페이지와 인덱스 페이지는 복구 모델에 관계없이 모두 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-122">In contrast, if a table has a clustered index and is non-empty, data pages and index pages are both fully logged regardless of the recovery model.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63abd-123">빈 테이블로 시작하여 데이터 대량 가져오기를 일괄 처리로 수행하는 경우 첫 번째 일괄 처리에서는 인덱스 및 데이터 페이지가 최소 로깅되지만 두 번째 일괄 처리부터는 데이터 페이지만 대량으로 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-123">If you start with an empty table and bulk import the data in batches, both index and data pages are minimally logged for the first batch, but from the second batch onwards, only data pages are bulk logged.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63abd-124">트랜잭션 복제를 사용하는 경우 대량 로그 복구 모델에서도 BULK INSERT 작업이 모두 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="63abd-124">When transactional replication is enabled, BULK INSERT operations are fully logged even under the Bulk Logged recovery model.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="63abd-125">관련 작업</span><span class="sxs-lookup"><span data-stu-id="63abd-125">Related Tasks</span></span>  
  
-   [<span data-ttu-id="63abd-126">데이터베이스 복구 모델 보기 또는 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="63abd-126">View or Change the Recovery Model of a Database &#40;SQL Server&#41;</span></span>](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="63abd-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63abd-127">See Also</span></span>  
 <span data-ttu-id="63abd-128">[복구 모델&#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63abd-128">[Recovery Models &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md) </span></span>  
 <span data-ttu-id="63abd-129">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="63abd-129">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="63abd-130">[BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="63abd-130">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="63abd-131">[OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="63abd-131">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="63abd-132">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="63abd-132">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="63abd-133">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="63abd-133">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="63abd-134">[테이블 힌트&#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table) </span><span class="sxs-lookup"><span data-stu-id="63abd-134">[Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table) </span></span>  
 [<span data-ttu-id="63abd-135">INSERT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="63abd-135">INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/insert-transact-sql)  
  
  
