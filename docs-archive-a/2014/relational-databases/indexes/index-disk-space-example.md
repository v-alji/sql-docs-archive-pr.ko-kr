---
title: 인덱스 디스크 공간 예 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- online index disk space
- disk space [SQL Server], indexes
- index disk space [SQL Server]
- space [SQL Server], indexes
- indexes [SQL Server], disk space requirements
- offline index disk space [SQL Server]
ms.assetid: e5c71f55-0be3-4c93-97e9-7b3455c8f581
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e4a30c6ce986095496a11c41f3102d095e8c632b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650974"
---
# <a name="index-disk-space-example"></a><span data-ttu-id="b0963-102">인덱스 디스크 공간 예</span><span class="sxs-lookup"><span data-stu-id="b0963-102">Index Disk Space Example</span></span>
  <span data-ttu-id="b0963-103">인덱스를 생성하거나, 다시 작성하거나, 삭제할 때마다 해당 파일 및 파일 그룹에서 이전(원본) 및 새(대상) 구조 모두에 대한 디스크 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-103">Whenever an index is created, rebuilt, or dropped, disk space for both the old (source) and new (target) structures is required in their appropriate files and filegroups.</span></span> <span data-ttu-id="b0963-104">기존 구조는 인덱스 생성 트랜잭션이 커밋된 후 할당 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-104">The old structure is not deallocated until the index creation transaction commits.</span></span> <span data-ttu-id="b0963-105">또한 분류 작업을 위한 임시 디스크 공간도 추가로 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-105">Additional temporary disk space for sorting operations may also be needed.</span></span> <span data-ttu-id="b0963-106">자세한 내용은 [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b0963-106">For more information, see [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md).</span></span>  
  
 <span data-ttu-id="b0963-107">다음 예에서는 클러스터형 인덱스를 만들기 위한 디스크 공간 요구 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-107">In this example, disk space requirements to create a clustered index are determined.</span></span>  
  
 <span data-ttu-id="b0963-108">클러스터형 인덱스를 만들기 전에 다음과 같은 조건이 참인 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-108">Assume the following conditions are true before creating the clustered index:</span></span>  
  
-   <span data-ttu-id="b0963-109">기존 테이블(힙)에 행이 백만 개 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-109">The existing table (heap) contains 1 million rows.</span></span> <span data-ttu-id="b0963-110">각 행의 길이는 200바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-110">Each row is 200 bytes long.</span></span>  
  
-   <span data-ttu-id="b0963-111">비클러스터형 인덱스 A에 행이 백만 개 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-111">Nonclustered index A contains 1 million rows.</span></span> <span data-ttu-id="b0963-112">각 행의 길이는 50바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-112">Each row is 50 bytes long.</span></span>  
  
-   <span data-ttu-id="b0963-113">비클러스터형 인덱스 B에 행이 백만 개 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-113">Nonclustered index B contains 1 million rows.</span></span> <span data-ttu-id="b0963-114">각 행의 길이는 80바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-114">Each row is 80 bytes long.</span></span>  
  
-   <span data-ttu-id="b0963-115">index create memory 옵션이 2MB로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-115">The index create memory option is set to 2 MB.</span></span>  
  
-   <span data-ttu-id="b0963-116">모든 기존 및 새 인덱스의 채우기 비율 값은 80입니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-116">A fill factor value of 80 is used for all existing and new indexes.</span></span> <span data-ttu-id="b0963-117">즉, 페이지의 80%가 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-117">This means the pages are 80 percent full.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b0963-118">클러스터형 인덱스를 만들 경우 행 표시기를 새 클러스터형 인덱스 키로 대체하기 위해 두 개의 비클러스터형 인덱스를 다시 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-118">As a result of creating a clustered index, the two nonclustered indexes must be rebuilt to replace the row indicator with the new clustered index key.</span></span>  
  
## <a name="disk-space-calculations-for-an-offline-index-operation"></a><span data-ttu-id="b0963-119">오프라인 인덱스 작업의 디스크 공간 계산</span><span class="sxs-lookup"><span data-stu-id="b0963-119">Disk Space Calculations for an Offline Index Operation</span></span>  
 <span data-ttu-id="b0963-120">아래의 단계에서는 인덱스 작업 동안 사용할 임시 디스크 공간과 새 인덱스를 저장하기 위한 영구 디스크 공간을 모두 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-120">In the following steps, both temporary disk space to be used during the index operation and permanent disk space to store the new indexes are calculated.</span></span> <span data-ttu-id="b0963-121">결과를 반올림하고 인덱스 리프 수준의 크기만 고려하는 등 대략적으로 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-121">The calculations shown are approximate; results are rounded up and consider only the size of index leaf level.</span></span> <span data-ttu-id="b0963-122">대략적으로 계산한 경우에는 이를 나타내기 위해 물결표(~)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-122">The tilde (~) is used to indicate approximate calculations.</span></span>  
  
1.  <span data-ttu-id="b0963-123">원본 구조의 크기를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-123">Determine the size of the source structures.</span></span>  
  
     <span data-ttu-id="b0963-124">힙: 1백만 \* 200바이트 = 200MB</span><span class="sxs-lookup"><span data-stu-id="b0963-124">Heap: 1 million \* 200 bytes ~ 200 MB</span></span>  
  
     <span data-ttu-id="b0963-125">비클러스터형 인덱스 A: 1백만 \* 50바이트/80% = 63MB</span><span class="sxs-lookup"><span data-stu-id="b0963-125">Nonclustered index A: 1 million \* 50 bytes / 80% ~ 63 MB</span></span>  
  
     <span data-ttu-id="b0963-126">비클러스터형 인덱스 B: 1백만 \* 80바이트/80% = 100MB</span><span class="sxs-lookup"><span data-stu-id="b0963-126">Nonclustered index B: 1 million \* 80 bytes / 80% ~ 100 MB</span></span>  
  
     <span data-ttu-id="b0963-127">기존 구조의 전체 크기: 363MB</span><span class="sxs-lookup"><span data-stu-id="b0963-127">Total size of existing structures: 363 MB</span></span>  
  
2.  <span data-ttu-id="b0963-128">대상 인덱스 구조의 크기를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-128">Determine the size of the target index structures.</span></span> <span data-ttu-id="b0963-129">새 클러스터형 키 길이가 uniqueifier를 포함하여 24바이트인 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-129">Assume that the new clustered key is 24 bytes long including a uniqueifier.</span></span> <span data-ttu-id="b0963-130">비클러스터형 인덱스 모두의 행 표시기(8바이트 길이)가 이 클러스터형 키로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-130">The row indicator (8 bytes long) in both nonclustered indexes will be replaced by this clustered key.</span></span>  
  
     <span data-ttu-id="b0963-131">클러스터형 인덱스: 1백만 \* 200바이트/80% = 250MB</span><span class="sxs-lookup"><span data-stu-id="b0963-131">Clustered index: 1 million \* 200 bytes / 80% ~ 250 MB</span></span>  
  
     <span data-ttu-id="b0963-132">비클러스터형 인덱스 A: 1백만 \* (50 – 8 + 24)바이트/80% = 83MB</span><span class="sxs-lookup"><span data-stu-id="b0963-132">Nonclustered index A: 1 million \* (50 - 8 + 24) bytes / 80% ~ 83 MB</span></span>  
  
     <span data-ttu-id="b0963-133">비클러스터형 인덱스 B: 1백만 \* (80 – 8 + 24)바이트/80% = 120MB</span><span class="sxs-lookup"><span data-stu-id="b0963-133">Nonclustered index B: 1 million \* (80 - 8 + 24) bytes / 80% ~ 120 MB</span></span>  
  
     <span data-ttu-id="b0963-134">새 구조의 전체 크기: 453MB</span><span class="sxs-lookup"><span data-stu-id="b0963-134">Total size of new structures: 453 MB</span></span>  
  
     <span data-ttu-id="b0963-135">인덱스 작업 동안 원본 구조와 대상 구조를 모두 지원하는 데 필요한 전체 디스크 공간은 816MB(363+453)입니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-135">Total disk space required to support both the source and target structures for the duration of the index operation is 816 MB (363 + 453).</span></span> <span data-ttu-id="b0963-136">인덱스 작업이 커밋되면 원본 구조에 현재 할당된 공간은 할당 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-136">The space currently allocated to the source structures will be deallocated after the index operation is committed.</span></span>  
  
3.  <span data-ttu-id="b0963-137">정렬을 위한 추가 임시 디스크 공간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-137">Determine additional temporary disk space for sorting.</span></span>  
  
     <span data-ttu-id="b0963-138">SORT_IN_TEMPDB를 ON으로 설정하여 **tempdb** 에서 정렬하고 SORT_IN_TEMPDB를 OFF로 설정하여 대상 위치에서 정렬하기 위한 공간 요구 사항이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-138">Space requirements are shown for sorting in **tempdb** (with SORT_IN_TEMPDB set to ON) and sorting in the target location (with SORT_IN_TEMPDB set to OFF).</span></span>  
  
    1.  <span data-ttu-id="b0963-139">SORT_IN_TEMPDB을 ON으로 설정한 경우 **tempdb** 에 가장 큰 인덱스(1백만\*200바이트~200MB)를 보관할 만큼 충분한 디스크 공간이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-139">When SORT_IN_TEMPDB is set to ON, **tempdb** must have sufficient disk space to hold the largest index (1 million \* 200 bytes ~ 200 MB).</span></span> <span data-ttu-id="b0963-140">정렬 작업에서는 채우기 비율을 고려하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-140">Fill factor is not considered in the sorting operation.</span></span>  
  
         <span data-ttu-id="b0963-141">**tempdb** 위치의 추가 디스크 공간은 [index create memory 서버 구성 옵션 구성](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) 값 = 2MB와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-141">Additional disk space (in the **tempdb** location) equal to the [Configure the index create memory Server Configuration Option](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) value = 2 MB.</span></span>  
  
         <span data-ttu-id="b0963-142">SORT_IN_TEMPDB를 ON으로 설정한 경우의 전체 임시 디스크 공간 크기~202MB.</span><span class="sxs-lookup"><span data-stu-id="b0963-142">Total size of temporary disk space with SORT_IN_TEMPDB set to ON ~ 202 MB.</span></span>  
  
    2.  <span data-ttu-id="b0963-143">SORT_IN_TEMPDB를 OFF(기본값)로 설정한 경우 2단계에서 이미 새 인덱스용으로 간주한 250MB의 디스크 공간을 정렬에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-143">When SORT_IN_TEMPDB is set to OFF (default), the 250 MB of disk space already considered for the new index in step 2 is used for sorting.</span></span>  
  
         <span data-ttu-id="b0963-144">대상 위치의 추가 디스크 공간은 [index create memory 서버 구성 옵션 구성](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) 값 = 2MB와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-144">Additional disk space (in the target location) equal to the [Configure the index create memory Server Configuration Option](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) value = 2 MB.</span></span>  
  
         <span data-ttu-id="b0963-145">SORT_IN_TEMPDB를 OFF로 설정한 경우의 전체 임시 디스크 공간 크기~2MB.</span><span class="sxs-lookup"><span data-stu-id="b0963-145">Total size of temporary disk space with SORT_IN_TEMPDB set to OFF = 2 MB.</span></span>  
  
 <span data-ttu-id="b0963-146">**tempdb**를 사용하는 경우 클러스터형 및 비클러스터형 인덱스를 만드는 데 총 1018MB(816+202)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-146">Using **tempdb**, a total of 1018 MB (816 + 202) would be needed to create the clustered and nonclustered indexes.</span></span> <span data-ttu-id="b0963-147">**tempdb** 를 사용하면 인덱스를 만드는 데 사용되는 임시 디스크 공간이 늘어나지만 **tempdb** 가 사용자 데이터베이스와 다른 디스크 집합에 있을 때 인덱스를 만드는 데 필요한 시간이 줄어들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-147">Although using **tempdb** increases the amount of temporary disk space used to create an index, it may reduce the time that is required to create an index when **tempdb** is on a different set of disks than the user database.</span></span> <span data-ttu-id="b0963-148">**tempdb**사용에 대한 자세한 내용은 [인덱스에 대한 SORT_IN_TEMPDB 옵션](indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b0963-148">For more information about using **tempdb**, see [SORT_IN_TEMPDB Option For Indexes](indexes.md).</span></span>  
  
 <span data-ttu-id="b0963-149">**tempdb**를 사용하지 않는 경우 클러스터형 및 비클러스터형 인덱스를 만드는 데 총 818MB(816+2)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-149">Without using **tempdb**, a total of 818 MB (816+ 2) would be needed to create the clustered and nonclustered indexes.</span></span>  
  
## <a name="disk-space-calculations-for-an-online-clustered-index-operation"></a><span data-ttu-id="b0963-150">온라인 클러스터형 인덱스 작업의 디스크 공간 계산</span><span class="sxs-lookup"><span data-stu-id="b0963-150">Disk Space Calculations for an Online Clustered Index Operation</span></span>  
 <span data-ttu-id="b0963-151">온라인으로 클러스터형 인덱스를 만들거나, 삭제하거나 또는 다시 작성할 때는 임시 매핑 인덱스를 작성하고 관리하는 데 추가로 디스크 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-151">When you create, drop, or rebuild a clustered index online, additional disk space is required to build and maintain a temporary mapping index.</span></span> <span data-ttu-id="b0963-152">이 임시 매핑 인덱스는 테이블의 각 행에 대해 하나의 레코드를 포함하고 있으며 해당 내용은 이전 및 새 책갈피 열의 합집합입니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-152">This temporary mapping index contains one record for each row in the table, and its contents are the union of the old and new bookmark columns.</span></span>  
  
 <span data-ttu-id="b0963-153">온라인 클러스터형 인덱스 작업에 필요한 디스크 공간을 계산하려면 오프라인 인덱스 작업에 대한 단계를 따르고 그 결과를 아래에 나와 있는 단계의 결과에 추가하십시오.</span><span class="sxs-lookup"><span data-stu-id="b0963-153">To calculate the disk space needed for an online clustered index operation, follow the steps shown for an offline index operation and add those results to the results of the following step.</span></span>  
  
-   <span data-ttu-id="b0963-154">임시 매핑 인덱스에 대한 공간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-154">Determine space for the temporary mapping index.</span></span>  
  
     <span data-ttu-id="b0963-155">이 예에서 이전 책갈피는 힙 (8 바이트)의 행 ID (RID)이 고 새 책갈피는 클러스터링 키 (를 포함 하는 24 바이트 `uniqueifier` )입니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-155">In this example, the old bookmark is the row ID (RID) of the heap (8 bytes) and the new bookmark is the clustering key (24 bytes including a `uniqueifier`).</span></span> <span data-ttu-id="b0963-156">이전 책갈피와 새 책갈피 사이에 겹치는 열은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-156">There are no overlapping columns between the old and new bookmarks.</span></span>  
  
     <span data-ttu-id="b0963-157">임시 매핑 인덱스 크기 = 1백만\*(8바이트+24바이트)/80%~40MB</span><span class="sxs-lookup"><span data-stu-id="b0963-157">Temporary mapping index size = 1 million \* (8 bytes + 24 bytes) / 80% ~ 40 MB.</span></span>  
  
     <span data-ttu-id="b0963-158">SORT_IN_TEMPDB를 OFF로 설정한 경우에는 대상 위치에서 필요한 디스크 공간에, SORT_IN_TEMPDB를 ON으로 설정한 경우에는 **tempdb** 에 이 디스크 공간을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-158">This disk space must be added to the required disk space in the target location if SORT_IN_TEMPDB is set to OFF, or to **tempdb** if SORT_IN_TEMPDB is set to ON.</span></span>  
  
 <span data-ttu-id="b0963-159">자세한 내용은 [인덱스 DDL 작업의 디스크 공간 요구 사항](disk-space-requirements-for-index-ddl-operations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b0963-159">For more information about the temporary mapping index, see [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md).</span></span>  
  
## <a name="disk-space-summary"></a><span data-ttu-id="b0963-160">디스크 공간 요약</span><span class="sxs-lookup"><span data-stu-id="b0963-160">Disk Space Summary</span></span>  
 <span data-ttu-id="b0963-161">다음 표는 디스크 공간 계산 결과를 요약한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-161">The following table summarizes the results of the disk space calculations.</span></span>  
  
|<span data-ttu-id="b0963-162">인덱스 작업</span><span class="sxs-lookup"><span data-stu-id="b0963-162">Index operation</span></span>|<span data-ttu-id="b0963-163">다음 구조의 위치에 대한 디스크 공간 요구 사항</span><span class="sxs-lookup"><span data-stu-id="b0963-163">Disk space requirements for the locations of the following structures</span></span>|  
|---------------------|---------------------------------------------------------------------------|  
|<span data-ttu-id="b0963-164">SORT_IN_TEMPDB = ON인 경우 오프라인 인덱스 작업</span><span class="sxs-lookup"><span data-stu-id="b0963-164">Offline index operation with SORT_IN_TEMPDB = ON</span></span>|<span data-ttu-id="b0963-165">작업 중 전체 공간: 1018 m b:</span><span class="sxs-lookup"><span data-stu-id="b0963-165">Total space during the operation: 1018 MB:</span></span><br /><br /> <span data-ttu-id="b0963-166">-기존 테이블 및 인덱스: 363MB\*</span><span class="sxs-lookup"><span data-stu-id="b0963-166">-Existing table and indexes: 363 MB\*</span></span><br /><br /> -<br />                    <span data-ttu-id="b0963-167">**tempdb**: 202MB\*</span><span class="sxs-lookup"><span data-stu-id="b0963-167">**tempdb**: 202 MB\*</span></span><br /><br /> <span data-ttu-id="b0963-168">-새 인덱스: 453MB</span><span class="sxs-lookup"><span data-stu-id="b0963-168">-New indexes: 453 MB</span></span><br /><br /> <span data-ttu-id="b0963-169">작업 후 필요한 전체 공간: 453MB</span><span class="sxs-lookup"><span data-stu-id="b0963-169">Total space required after the operation: 453 MB</span></span>|  
|<span data-ttu-id="b0963-170">SORT_IN_TEMPDB = OFF인 경우 오프라인 인덱스 작업</span><span class="sxs-lookup"><span data-stu-id="b0963-170">Offline index operation with SORT_IN_TEMPDB = OFF</span></span>|<span data-ttu-id="b0963-171">작업 중 전체 공간: 816 m b:</span><span class="sxs-lookup"><span data-stu-id="b0963-171">Total space during the operation: 816 MB:</span></span><br /><br /> <span data-ttu-id="b0963-172">-기존 테이블 및 인덱스: 363MB\*</span><span class="sxs-lookup"><span data-stu-id="b0963-172">-Existing table and indexes: 363 MB\*</span></span><br /><br /> <span data-ttu-id="b0963-173">-새 인덱스: 453MB</span><span class="sxs-lookup"><span data-stu-id="b0963-173">-New indexes: 453 MB</span></span><br /><br /> <span data-ttu-id="b0963-174">작업 후 필요한 전체 공간: 453MB</span><span class="sxs-lookup"><span data-stu-id="b0963-174">Total space required after the operation: 453 MB</span></span>|  
|<span data-ttu-id="b0963-175">SORT_IN_TEMPDB = ON인 경우 온라인 인덱스 작업</span><span class="sxs-lookup"><span data-stu-id="b0963-175">Online index operation with SORT_IN_TEMPDB = ON</span></span>|<span data-ttu-id="b0963-176">작업 중 전체 공간: 1058 m b:</span><span class="sxs-lookup"><span data-stu-id="b0963-176">Total space during the operation: 1058 MB:</span></span><br /><br /> <span data-ttu-id="b0963-177">-기존 테이블 및 인덱스: 363MB\*</span><span class="sxs-lookup"><span data-stu-id="b0963-177">-Existing table and indexes: 363 MB\*</span></span><br /><br /> <span data-ttu-id="b0963-178">-**tempdb** (매핑 인덱스 포함): 242 m b \*</span><span class="sxs-lookup"><span data-stu-id="b0963-178">-**tempdb** (includes mapping index): 242 MB\*</span></span><br /><br /> <span data-ttu-id="b0963-179">-새 인덱스: 453MB</span><span class="sxs-lookup"><span data-stu-id="b0963-179">-New indexes: 453 MB</span></span><br /><br /> <span data-ttu-id="b0963-180">작업 후 필요한 전체 공간: 453MB</span><span class="sxs-lookup"><span data-stu-id="b0963-180">Total space required after the operation: 453 MB</span></span>|  
|<span data-ttu-id="b0963-181">SORT_IN_TEMPDB = OFF인 경우 온라인 인덱스 작업</span><span class="sxs-lookup"><span data-stu-id="b0963-181">Online index operation with SORT_IN_TEMPDB = OFF</span></span>|<span data-ttu-id="b0963-182">작업 중 전체 공간: 856 m b:</span><span class="sxs-lookup"><span data-stu-id="b0963-182">Total space during the operation: 856 MB:</span></span><br /><br /> <span data-ttu-id="b0963-183">-기존 테이블 및 인덱스: 363MB\*</span><span class="sxs-lookup"><span data-stu-id="b0963-183">-Existing table and indexes: 363 MB\*</span></span><br /><br /> <span data-ttu-id="b0963-184">-임시 매핑 인덱스: 40MB\*</span><span class="sxs-lookup"><span data-stu-id="b0963-184">-Temporary mapping index: 40 MB\*</span></span><br /><br /> <span data-ttu-id="b0963-185">-새 인덱스: 453MB</span><span class="sxs-lookup"><span data-stu-id="b0963-185">-New indexes: 453 MB</span></span><br /><br /> <span data-ttu-id="b0963-186">작업 후 필요한 전체 공간: 453MB</span><span class="sxs-lookup"><span data-stu-id="b0963-186">Total space required after the operation: 453 MB</span></span>|  
  
 <span data-ttu-id="b0963-187">\*이 공간은 인덱스 작업이 커밋된 후 할당 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-187">\*This space is deallocated after the index operation is committed.</span></span>  
  
 <span data-ttu-id="b0963-188">이 예에서는 동시 사용자 업데이트 및 삭제 작업으로 인해 만들어진 버전 레코드용으로 **tempdb** 에서 추가로 필요한 임시 디스크 공간을 고려하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="b0963-188">This example does not consider any additional temporary disk space required in **tempdb** for version records created by concurrent user update and delete operations.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="b0963-189">관련 내용</span><span class="sxs-lookup"><span data-stu-id="b0963-189">Related Content</span></span>  
 [<span data-ttu-id="b0963-190">인덱스 DDL 작업의 디스크 공간 요구 사항</span><span class="sxs-lookup"><span data-stu-id="b0963-190">Disk Space Requirements for Index DDL Operations</span></span>](disk-space-requirements-for-index-ddl-operations.md)  
  
 [<span data-ttu-id="b0963-191">인덱스 작업에 필요한 트랜잭션 로그 디스크 공간</span><span class="sxs-lookup"><span data-stu-id="b0963-191">Transaction Log Disk Space for Index Operations</span></span>](transaction-log-disk-space-for-index-operations.md)  
  
  
