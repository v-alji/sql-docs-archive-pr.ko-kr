---
title: 데이터베이스 미러링 및 전체 텍스트 카탈로그(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- full-text catalogs [SQL Server], database mirroring
- catalogs [SQL Server], database mirroring
ms.assetid: e34072ae-fe8a-462d-bb03-02fa0987f793
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 39929f4bed6edbd1e8ec5c1b72dbe8f7aefeec68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648568"
---
# <a name="database-mirroring-and-full-text-catalogs-sql-server"></a><span data-ttu-id="2595e-102">데이터베이스 미러링 및 전체 텍스트 카탈로그(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2595e-102">Database Mirroring and Full-Text Catalogs (SQL Server)</span></span>
  <span data-ttu-id="2595e-103">전체 텍스트 카탈로그가 있는 데이터베이스를 미러링하려면 일반적인 백업을 사용하여 주 데이터베이스의 전체 데이터베이스 백업을 만든 다음 백업을 복원하여 데이터베이스를 미러 서버로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="2595e-103">To mirror a database that has a full-text catalog, use backup as usual to create a full database backup of the principal database, and then restore the backup to copy the database to the mirror server.</span></span> <span data-ttu-id="2595e-104">자세한 내용은 [미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2595e-104">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
## <a name="full-text-catalog-and-indexes-before-failover"></a><span data-ttu-id="2595e-105">장애 조치(Failover) 이전의 전체 텍스트 카탈로그 및 인덱스</span><span class="sxs-lookup"><span data-stu-id="2595e-105">Full-Text Catalog and Indexes Before Failover</span></span>  
 <span data-ttu-id="2595e-106">새로 생성된 미러 데이터베이스에서 전체 텍스트 카탈로그는 데이터베이스가 백업될 때와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="2595e-106">In a newly created mirror database, the full-text catalog is the same as when the database was backed up.</span></span> <span data-ttu-id="2595e-107">데이터베이스 미러링이 시작된 후 CREATE FULLTEXT CATALOG, ALTER FULLTEXT CATALOG, DROP FULLTEXT CATALOG 등과 같은 DDL 문으로 적용된 모든 카탈로그 수준 변경 내용은 기록되고 미러 서버로 전송되어 미러 데이터베이스에서 재생됩니다.</span><span class="sxs-lookup"><span data-stu-id="2595e-107">After database mirroring starts, any catalog-level changes that were made by DDL statements (CREATE FULLTEXT CATALOG, ALTER FULLTEXT CATALOG, DROP FULLTEXT CATALOG) are logged and sent to the mirror server to be replayed on the mirror database.</span></span> <span data-ttu-id="2595e-108">그러나 인덱스 수준 변경 내용은 주 서버에 기록되지 않으므로 미러 데이터베이스에서 재현되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2595e-108">However, index-level changes are not reproduced on the mirror database because it is not logged on to the principal server.</span></span> <span data-ttu-id="2595e-109">따라서 미러 데이터베이스의 전체 텍스트 카탈로그 내용은 주 데이터베이스의 전체 텍스트 카탈로그 내용이 변경됨에 따라 동기화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2595e-109">Therefore, as the contents of the full-text catalog change on the principal database, the contents of the full-text catalog on the mirror database are unsynchronized.</span></span>  
  
## <a name="full-text-indexes-after-failover"></a><span data-ttu-id="2595e-110">장애 조치 이후의 전체 텍스트 인덱스</span><span class="sxs-lookup"><span data-stu-id="2595e-110">Full-Text Indexes After Failover</span></span>  
 <span data-ttu-id="2595e-111">장애 조치 이후 새로운 주 서버에서 또는 다음 상황에서 전체 텍스트 인덱스의 전체 탐색이 필요하거나 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2595e-111">After a failover, a full crawl of a full-text index on the new principal server might be required or useful in the following situations:</span></span>  
  
-   <span data-ttu-id="2595e-112">변경 추적이 전체 텍스트 인덱스에서 해제되어 있으면 다음 문을 사용하여 해당 인덱스에서 전체 탐색을 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2595e-112">If change-tracking is turned OFF on a full text index, you must start a full crawl on that index by using the following statement:</span></span>  
  
     <span data-ttu-id="2595e-113">ALTER FULLTEXT INDEX ON *table_name* START FULL POPULATION</span><span class="sxs-lookup"><span data-stu-id="2595e-113">ALTER FULLTEXT INDEX ON *table_name* START FULL POPULATION</span></span>  
  
-   <span data-ttu-id="2595e-114">전체 텍스트 인덱스가 변경 내용을 자동으로 추적하도록 구성되어 있으면 전체 텍스트 인덱스가 자동으로 동기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="2595e-114">If a full-text index is configured for automatic change tracking, the full-text index is automatically synchronized.</span></span> <span data-ttu-id="2595e-115">그러나 동기화로 인해 전체 텍스트 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2595e-115">However, synchronization slows full-text performance somewhat.</span></span> <span data-ttu-id="2595e-116">성능이 너무 저하될 경우에는 다음과 같이 변경 내용 추적을 해제하여 전체 탐색을 수행한 후 자동 추적을 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2595e-116">If performance is too slow, you can cause a full crawl by setting change tracking off and then resetting it to automatic:</span></span>  
  
    -   <span data-ttu-id="2595e-117">변경 내용 추적을 해제하려면</span><span class="sxs-lookup"><span data-stu-id="2595e-117">To set change tracking off:</span></span>  
  
         <span data-ttu-id="2595e-118">ALTER FULLTEXT INDEX ON *table_name* SET CHANGE_TRACKING OFF</span><span class="sxs-lookup"><span data-stu-id="2595e-118">ALTER FULLTEXT INDEX ON *table_name* SET CHANGE_TRACKING OFF</span></span>  
  
    -   <span data-ttu-id="2595e-119">변경 내용 자동 추적을 자동으로 설정하려면</span><span class="sxs-lookup"><span data-stu-id="2595e-119">To set on automatic change tracking to automatic:</span></span>  
  
         <span data-ttu-id="2595e-120">ALTER FULLTEXT INDEX ON *table_name* SET CHANGE_TRACKING AUTO</span><span class="sxs-lookup"><span data-stu-id="2595e-120">ALTER FULLTEXT INDEX ON *table_name* SET CHANGE_TRACKING AUTO</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2595e-121">자동 변경 추적이 설정되어 있는지 확인하려면 [OBJECTPROPERTYEX](/sql/t-sql/functions/objectproperty-transact-sql) 함수를 사용하여 테이블의 **TableFullTextBackgroundUpdateIndexOn** 속성을 쿼리하세요.</span><span class="sxs-lookup"><span data-stu-id="2595e-121">To see whether auto change tracking is on, you can use the [OBJECTPROPERTYEX](/sql/t-sql/functions/objectproperty-transact-sql) function to query the **TableFullTextBackgroundUpdateIndexOn** property of the table.</span></span>  
  
 <span data-ttu-id="2595e-122">자세한 내용은 [ALTER FULLTEXT INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2595e-122">For more information, see [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2595e-123">장애 조치 이후의 탐색 시작은 복원 이후의 탐색 시작과 동일하게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="2595e-123">Starting a crawl after failover works the same as starting a crawl after a restore.</span></span>  
  
## <a name="after-forcing-service"></a><span data-ttu-id="2595e-124">서비스 강제 이후</span><span class="sxs-lookup"><span data-stu-id="2595e-124">After Forcing Service</span></span>  
 <span data-ttu-id="2595e-125">미러 서버에 대해 서비스를 강제(데이터 손실 가능)한 후 전체 탐색을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2595e-125">After service is forced to the mirror server (with possible data loss), start a full crawl.</span></span> <span data-ttu-id="2595e-126">전체 탐색을 시작할 때 사용할 방법은 전체 텍스트 인덱스의 변경 내용 추적 여부에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2595e-126">The method to use for starting a full crawl depends on whether the full-text index is change tracked.</span></span> <span data-ttu-id="2595e-127">자세한 내용은 이 항목의 앞부분에 나오는 "장애 조치 이후의 전체 텍스트 인덱스"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2595e-127">For more information, see "Full-Text Indexes After Failover," earlier in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2595e-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2595e-128">See Also</span></span>  
 <span data-ttu-id="2595e-129">[ALTER FULLTEXT INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2595e-129">[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) </span></span>  
 <span data-ttu-id="2595e-130">[CREATE FULLTEXT INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2595e-130">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span></span>  
 <span data-ttu-id="2595e-131">[DROP FULLTEXT INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2595e-131">[DROP FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-index-transact-sql) </span></span>  
 <span data-ttu-id="2595e-132">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2595e-132">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="2595e-133">전체 텍스트 카탈로그와 인덱스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="2595e-133">Back Up and Restore Full-Text Catalogs and Indexes</span></span>](../../relational-databases/indexes/indexes.md)  
  
  
