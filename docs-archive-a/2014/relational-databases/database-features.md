---
title: 데이터베이스 기능 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 04518abb-8581-47c8-a601-ee9136c3c0eb
author: rothja
ms.author: jroth
ms.openlocfilehash: 56b9f9ba9cc6e11ea82b822ae10b31710c8617b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652158"
---
# <a name="database-features"></a><span data-ttu-id="b13e1-102">데이터베이스 기능</span><span class="sxs-lookup"><span data-stu-id="b13e1-102">Database Features</span></span>
  <span data-ttu-id="b13e1-103">이 섹션에서는 데이터베이스, 데이터베이스 개체, 데이터 형식, 그리고 데이터 작업 및 관리에 사용되는 메커니즘과 관련된 기능 및 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="b13e1-103">This section contains the features and tasks associated with databases, database objects, data types, and the mechanisms used to work with or manage data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b13e1-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="b13e1-104">In This Section</span></span>  
  
|||
|--|--|
|[<span data-ttu-id="b13e1-105">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="b13e1-105">Databases</span></span>](databases/databases.md)|[<span data-ttu-id="b13e1-106">SQL Server 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="b13e1-106">Back Up and Restore of SQL Server Databases</span></span>](backup-restore/back-up-and-restore-of-sql-server-databases.md)|  
|[<span data-ttu-id="b13e1-107">테이블</span><span class="sxs-lookup"><span data-stu-id="b13e1-107">Tables</span></span>](tables/tables.md)|[<span data-ttu-id="b13e1-108">시퀀스 번호</span><span class="sxs-lookup"><span data-stu-id="b13e1-108">Sequence Numbers</span></span>](sequence-numbers/sequence-numbers.md)|[<span data-ttu-id="b13e1-109">데이터 대량 가져오기 및 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b13e1-109">Bulk Import and Export of Data &#40;SQL Server&#41;</span></span>](import-export/bulk-import-and-export-of-data-sql-server.md)|  
|[<span data-ttu-id="b13e1-110">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="b13e1-110">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](in-memory-oltp/in-memory-oltp-in-memory-optimization.md)|[<span data-ttu-id="b13e1-111">DDL 트리거</span><span class="sxs-lookup"><span data-stu-id="b13e1-111">DDL Triggers</span></span>](triggers/ddl-triggers.md)|[<span data-ttu-id="b13e1-112">Data Compression</span><span class="sxs-lookup"><span data-stu-id="b13e1-112">Data Compression</span></span>](data-compression/data-compression.md)|  
|[<span data-ttu-id="b13e1-113">인덱스</span><span class="sxs-lookup"><span data-stu-id="b13e1-113">Indexes</span></span>](indexes/indexes.md)|[<span data-ttu-id="b13e1-114">DML 트리거</span><span class="sxs-lookup"><span data-stu-id="b13e1-114">DML Triggers</span></span>](triggers/dml-triggers.md)|[<span data-ttu-id="b13e1-115">Transact-SQL의 OLE 자동화 개체</span><span class="sxs-lookup"><span data-stu-id="b13e1-115">OLE Automation Objects in Transact-SQL</span></span>](stored-procedures/ole-automation-objects-in-transact-sql.md)|  
|[<span data-ttu-id="b13e1-116">Partitioned Tables and Indexes</span><span class="sxs-lookup"><span data-stu-id="b13e1-116">Partitioned Tables and Indexes</span></span>](partitions/partitioned-tables-and-indexes.md)|[<span data-ttu-id="b13e1-117">동의어&#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="b13e1-117">Synonyms &#40;Database Engine&#41;</span></span>](synonyms/synonyms-database-engine.md)|[<span data-ttu-id="b13e1-118">이벤트 알림</span><span class="sxs-lookup"><span data-stu-id="b13e1-118">Event Notifications</span></span>](service-broker/event-notifications.md)|  
|[<span data-ttu-id="b13e1-119">뷰</span><span class="sxs-lookup"><span data-stu-id="b13e1-119">Views</span></span>](views/views.md)|[<span data-ttu-id="b13e1-120">XML 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b13e1-120">XML Data &#40;SQL Server&#41;</span></span>](xml/xml-data-sql-server.md)|[<span data-ttu-id="b13e1-121">성능 모니터링 및 튜닝</span><span class="sxs-lookup"><span data-stu-id="b13e1-121">Monitor and Tune for Performance</span></span>](performance/monitor-and-tune-for-performance.md)|  
|[<span data-ttu-id="b13e1-122">저장 프로시저&#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="b13e1-122">Stored Procedures &#40;Database Engine&#41;</span></span>](stored-procedures/stored-procedures-database-engine.md)|[<span data-ttu-id="b13e1-123">공간 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b13e1-123">Spatial Data &#40;SQL Server&#41;</span></span>](spatial/spatial-data-sql-server.md)||  
|[<span data-ttu-id="b13e1-124">검색 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b13e1-124">Search &#40;SQL Server&#41;</span></span>](../database-engine/search-sql-server.md)|[<span data-ttu-id="b13e1-125">Blob&#40;Binary Large Object&#41; 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b13e1-125">Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;</span></span>](blob/binary-large-object-blob-data-sql-server.md)||  
|[<span data-ttu-id="b13e1-126">사용자 정의 함수</span><span class="sxs-lookup"><span data-stu-id="b13e1-126">User-Defined Functions</span></span>](user-defined-functions/user-defined-functions.md)|[<span data-ttu-id="b13e1-127">데이터 계층 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="b13e1-127">Data-tier Applications</span></span>](data-tier-applications/data-tier-applications.md)||  
|[<span data-ttu-id="b13e1-128">통계</span><span class="sxs-lookup"><span data-stu-id="b13e1-128">Statistics</span></span>](statistics/statistics.md)|[<span data-ttu-id="b13e1-129">트랜잭션 로그&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b13e1-129">The Transaction Log &#40;SQL Server&#41;</span></span>](logs/the-transaction-log-sql-server.md)||  
|[<span data-ttu-id="b13e1-130">계획 지침</span><span class="sxs-lookup"><span data-stu-id="b13e1-130">Plan Guides</span></span>](performance/plan-guides.md)|[<span data-ttu-id="b13e1-131">데이터베이스 검사점&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b13e1-131">Database Checkpoints &#40;SQL Server&#41;</span></span>](logs/database-checkpoints-sql-server.md)||  
  
  
