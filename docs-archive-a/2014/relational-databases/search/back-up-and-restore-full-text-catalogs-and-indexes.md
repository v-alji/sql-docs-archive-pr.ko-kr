---
title: 전체 텍스트 카탈로그와 인덱스 백업 및 복원 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes [SQL Server], backing up
- full-text search [SQL Server], back up and restore
- recovery [full-text search]
- backups [SQL Server], full-text indexes
- full-text indexes [SQL Server], restoring
- restore operations [full-text search]
ms.assetid: 6a4080d9-e43f-4b7b-a1da-bebf654c1194
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6c0df49c03325da375427c6566799f374fcc9dd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659912"
---
# <a name="back-up-and-restore-full-text-catalogs-and-indexes"></a><span data-ttu-id="70a83-102">전체 텍스트 카탈로그와 인덱스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="70a83-102">Back Up and Restore Full-Text Catalogs and Indexes</span></span>
  <span data-ttu-id="70a83-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 만든 전체 텍스트 인덱스를 백업 및 복원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="70a83-103">This topic explains how to back up and restore full-text indexes created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="70a83-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 전체 텍스트 카탈로그는 논리적인 개념이며 파일 그룹에 상주하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="70a83-104">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the full-text catalog is a logical concept and does not reside in a filegroup.</span></span> <span data-ttu-id="70a83-105">따라서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 전체 텍스트 카탈로그를 백업하려면 카탈로그에 속한 전체 텍스트 인덱스가 포함된 모든 파일 그룹을 식별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70a83-105">Therefore, to back up a full-text catalog in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must identify every filegroup that contains a full-text index that belongs to the catalog.</span></span> <span data-ttu-id="70a83-106">그런 다음 해당 파일 그룹을 하나씩 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70a83-106">Then you must back up those filegroups, one by one.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="70a83-107">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 데이터베이스를 업그레이드할 때 전체 텍스트 카탈로그를 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70a83-107">It is possible to import full-text catalogs when upgrading a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] database.</span></span> <span data-ttu-id="70a83-108">가져온 각 전체 텍스트 카탈로그는 고유한 파일 그룹에 있는 데이터베이스 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="70a83-108">Each imported full-text catalog is a database file in its own filegroup.</span></span> <span data-ttu-id="70a83-109">가져온 카탈로그를 백업하려면 해당 파일 그룹을 백업하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="70a83-109">To back up an imported catalog, simply back up its filegroup.</span></span> <span data-ttu-id="70a83-110">자세한 내용은 [온라인 설명서의](https://go.microsoft.com/fwlink/?LinkID=121052)전체 텍스트 카탈로그 백업 및 복원 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70a83-110">For more information, see [Backing Up and Restoring Full-Text Catalogs](https://go.microsoft.com/fwlink/?LinkID=121052), in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Books Online.</span></span>  
  
##  <a name="backing-up-the-full-text-indexes-of-a-full-text-catalog"></a><a name="backingup"></a> <span data-ttu-id="70a83-111">전체 텍스트 카탈로그의 전체 텍스트 인덱스 백업</span><span class="sxs-lookup"><span data-stu-id="70a83-111">Backing Up the Full-Text Indexes of a Full-Text Catalog</span></span>  
  
###  <a name="finding-the-full-text-indexes-of-a-full-text-catalog"></a><a name="Find_FTIs_of_a_Catalog"></a> <span data-ttu-id="70a83-112">전체 텍스트 카탈로그에서 전체 텍스트 인덱스 찾기</span><span class="sxs-lookup"><span data-stu-id="70a83-112">Finding the Full-Text Indexes of a Full-Text Catalog</span></span>  
 <span data-ttu-id="70a83-113">[sys.fulltext_indexes](/sql/t-sql/queries/select-transact-sql) 및 [sys.fulltext_catalogs](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql) 카탈로그 뷰에서 열을 선택하는 다음과 같은 [SELECT](/sql/relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql) 문을 사용하여 전체 텍스트 인덱스의 속성을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70a83-113">You can retrieve the properties of the full-text indexes by using the following [SELECT](/sql/t-sql/queries/select-transact-sql) statement, which selects columns from the [sys.fulltext_indexes](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql) and [sys.fulltext_catalogs](/sql/relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql) catalog views.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @TableID int;  
SET @TableID = (SELECT OBJECT_ID('AdventureWorks2012.Production.Product'));  
SELECT object_name(@TableID), i.is_enabled, i.change_tracking_state,   
   i.has_crawl_completed, i.crawl_type, c.name as fulltext_catalog_name   
   FROM sys.fulltext_indexes i, sys.fulltext_catalogs c   
   WHERE i.fulltext_catalog_id = c.fulltext_catalog_id;  
GO  
```  
  

  
###  <a name="finding-the-filegroup-or-file-that-contains-a-full-text-index"></a><a name="Find_FG_of_FTI"></a> <span data-ttu-id="70a83-114">전체 텍스트 인덱스를 포함하는 파일 그룹 또는 파일 찾기</span><span class="sxs-lookup"><span data-stu-id="70a83-114">Finding the Filegroup or File That Contains a Full-Text Index</span></span>  
 <span data-ttu-id="70a83-115">전체 텍스트 인덱스가 생성되면 다음 위치 중 하나로 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="70a83-115">When a full-text index is created, it is placed in one of the following locations:</span></span>  
  
-   <span data-ttu-id="70a83-116">사용자가 지정한 파일 그룹</span><span class="sxs-lookup"><span data-stu-id="70a83-116">A user-specified filegroup.</span></span>  
  
-   <span data-ttu-id="70a83-117">분할되지 않은 테이블의 경우 기본 테이블 또는 뷰와 동일한 파일 그룹</span><span class="sxs-lookup"><span data-stu-id="70a83-117">The same filegroup as base table or view, for a nonpartitioned table.</span></span>  
  
-   <span data-ttu-id="70a83-118">분할된 테이블의 경우 기본 파일 그룹</span><span class="sxs-lookup"><span data-stu-id="70a83-118">The primary filegroup, for a partitioned table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70a83-119">전체 텍스트 인덱스 만들기에 대한 정보는 [전체 텍스트 인덱스 만들기 및 관리](create-and-manage-full-text-indexes.md) 및 [CREATE FULLTEXT INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70a83-119">For information about creating a full-text index, see [Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md) and [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="70a83-120">테이블 또는 뷰에서 전체 텍스트 인덱스의 파일 그룹을 찾으려면 다음 쿼리를 사용합니다. 여기서 *object_name* 은 테이블 또는 뷰의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="70a83-120">To find the filegroup of full-text index on a table or view, use the following query, where *object_name* is the name of the table or view:</span></span>  
  
```  
SELECT name FROM sys.filegroups f, sys.fulltext_indexes i   
   WHERE f.data_space_id = i.data_space_id   
      and i.object_id = object_id('object_name');  
GO  
  
```  
  

  
###  <a name="backing-up-the-filegroups-that-contain-full-text-indexes"></a><a name="Back_up_FTIs_of_FTC"></a> <span data-ttu-id="70a83-121">전체 텍스트 인덱스가 포함된 파일 그룹 백업</span><span class="sxs-lookup"><span data-stu-id="70a83-121">Backing Up the Filegroups That Contain Full-Text Indexes</span></span>  
 <span data-ttu-id="70a83-122">전체 텍스트 카탈로그의 인덱스를 포함하는 파일 그룹을 찾은 후에는 각 파일 그룹을 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70a83-122">After you find the filegroups that contain the indexes of a full-text catalog, you need back up each of the filegroups.</span></span> <span data-ttu-id="70a83-123">백업 프로세스 중에는 전체 텍스트 카탈로그를 삭제하거나 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70a83-123">During the backup process, full-text catalogs may not be dropped or added.</span></span>  
  
 <span data-ttu-id="70a83-124">파일 그룹의 첫 번째 백업은 전체 파일 백업이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70a83-124">The first backup of a filegroup must be a full file backup.</span></span> <span data-ttu-id="70a83-125">파일 그룹의 전체 파일 백업을 만들면 전체 파일 백업에 기반을 둔 일련의 차등 파일 백업을 하나 이상 만들어 파일 그룹의 변경 내용만 백업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70a83-125">After you have created a full file backup for a filegroup, you could back up only the changes in a filegroup by creating a series of one or more differential file backups that are based on the full file backup.</span></span>  
  
 <span data-ttu-id="70a83-126">**파일과 파일 그룹을 백업하려면**</span><span class="sxs-lookup"><span data-stu-id="70a83-126">**To back up files and filegroups**</span></span>  
  
-   [<span data-ttu-id="70a83-127">파일 및 파일 그룹 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70a83-127">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="70a83-128">BACKUP&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="70a83-128">BACKUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-transact-sql)  
  

  
##  <a name="restoring-a-full-text-index"></a><a name="Restore_FTI"></a> <span data-ttu-id="70a83-129">전체 텍스트 인덱스 복원</span><span class="sxs-lookup"><span data-stu-id="70a83-129">Restoring a Full-Text Index</span></span>  
 <span data-ttu-id="70a83-130">백업된 파일 그룹을 복원하면 전체 텍스트 인덱스 파일과 파일 그룹에 있는 다른 파일들까지 모두 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="70a83-130">Restoring a backed-up filegroup restores the full-text index files, as well as the other files in the filegroup.</span></span> <span data-ttu-id="70a83-131">기본적으로 파일 그룹은 파일 그룹이 백업된 디스크 위치에 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="70a83-131">By default, the filegroup is restored to the disk location on which the filegroup was backed up.</span></span>  
  
 <span data-ttu-id="70a83-132">전체 텍스트 인덱싱된 테이블이 온라인 상태이고 백업을 만들 때 채우기가 실행 중이었으면 복원 후 채우기가 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="70a83-132">If a full-text indexed table was online and a population was running when the backup was created, the population is resumed after the restore.</span></span>  
  
 <span data-ttu-id="70a83-133">**파일 그룹을 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="70a83-133">**To restore a filegroup**</span></span>  
  
-   [<span data-ttu-id="70a83-134">파일 및 파일 그룹 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70a83-134">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="70a83-135">기존 파일에서 파일 및 파일 그룹 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70a83-135">Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [<span data-ttu-id="70a83-136">새 위치로 파일 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70a83-136">Restore Files to a New Location &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="70a83-137">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="70a83-137">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  

  
## <a name="see-also"></a><span data-ttu-id="70a83-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="70a83-138">See Also</span></span>  
 <span data-ttu-id="70a83-139">[서버 인스턴스의 전체 텍스트 검색 관리 및 모니터링](manage-and-monitor-full-text-search-for-a-server-instance.md) </span><span class="sxs-lookup"><span data-stu-id="70a83-139">[Manage and Monitor Full-Text Search for a Server Instance](manage-and-monitor-full-text-search-for-a-server-instance.md) </span></span>  
 [<span data-ttu-id="70a83-140">전체 텍스트 검색 업그레이드</span><span class="sxs-lookup"><span data-stu-id="70a83-140">Upgrade Full-Text Search</span></span>](upgrade-full-text-search.md)  
  
  
