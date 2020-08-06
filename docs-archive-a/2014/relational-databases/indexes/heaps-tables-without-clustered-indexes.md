---
title: 힙(클러스터형 인덱스가 없는 테이블) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- heaps
ms.assetid: df5c4dfb-d372-4d0f-859a-a2d2533ee0d7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2a39bac2e0352f2adc7749e980d5cc91044f8ab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660570"
---
# <a name="heaps-tables-without-clustered-indexes"></a><span data-ttu-id="73156-102">힙(클러스터형 인덱스가 없는 테이블)</span><span class="sxs-lookup"><span data-stu-id="73156-102">Heaps (Tables without Clustered Indexes)</span></span>
  <span data-ttu-id="73156-103">힙이란 클러스터형 인덱스가 없는 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="73156-103">A heap is a table without a clustered index.</span></span> <span data-ttu-id="73156-104">힙으로 저장된 테이블에서 하나 이상의 비클러스터형 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73156-104">One or more nonclustered indexes can be created on tables stored as a heap.</span></span> <span data-ttu-id="73156-105">데이터는 순서를 지정하지 않고 힙에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="73156-105">Data is stored in the heap without specifying an order.</span></span> <span data-ttu-id="73156-106">일반적으로 데이터는 처음에 행이 테이블에 삽입되는 순서대로 저장되지만 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 힙 안의 데이터를 이동하여 행을 효율적으로 저장할 수 있습니다. 따라서 데이터 순서는 예측할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="73156-106">Usually data is initially stored in the order in which is the rows are inserted into the table, but the [!INCLUDE[ssDE](../../includes/ssde-md.md)] can move data around in the heap to store the rows efficiently; so the data order cannot be predicted.</span></span> <span data-ttu-id="73156-107">힙에서 반환되는 행의 순서를 지정하려면 `ORDER BY` 절을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73156-107">To guarantee the order of rows returned from a heap, you must use the `ORDER BY` clause.</span></span> <span data-ttu-id="73156-108">행의 스토리지 순서를 지정하려면 테이블에서 클러스터형 인덱스를 만들어 테이블이 힙이 되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="73156-108">To specify the order for storage of the rows, create a clustered index on the table, so that the table is not a heap.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73156-109">클러스터형 인덱스를 만들지 않고 테이블을 힙으로 두면 좋은 몇 가지 이유가 있지만, 힙을 효율적으로 사용하려면 고급 기술이 요구됩니다.</span><span class="sxs-lookup"><span data-stu-id="73156-109">There are sometimes good reasons to leave a table as a heap instead of creating a clustered index, but using heaps effectively is an advanced skill.</span></span> <span data-ttu-id="73156-110">힙을 테이블로 두어야 할 이유가 없는 한 대부분의 테이블에는 신중하게 선택된 클러스터형 인덱스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73156-110">Most tables should have a carefully chosen clustered index unless a good reason exists for leaving the table as a heap.</span></span>  
  
## <a name="when-to-use-a-heap"></a><span data-ttu-id="73156-111">힙을 사용하는 경우</span><span class="sxs-lookup"><span data-stu-id="73156-111">When to Use a Heap</span></span>  
 <span data-ttu-id="73156-112">테이블이 힙이고 비클러스터형 인덱스가 없는 경우 행을 찾으려면 전체 테이블을 검사(테이블 검색)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73156-112">If a table is a heap and does not have any nonclustered indexes, then the entire table must be examined (a table scan) to find any row.</span></span> <span data-ttu-id="73156-113">회사의 12개 지사 목록과 같이 테이블이 작은 경우에는 이렇게 하는 것이 문제가 되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73156-113">This can be acceptable when the table is tiny, such as a list of the 12 regional offices of a company.</span></span>  
  
 <span data-ttu-id="73156-114">테이블을 힙으로 저장하면 파일 번호, 데이터 페이지 번호 및 페이지의 슬롯으로 구성된 RID(행 식별자)에 대한 참조로 개별 행이 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="73156-114">When a table is stored as a heap, individual rows are identified by reference to a row identifier (RID) consisting of the file number, data page number, and slot on the page.</span></span> <span data-ttu-id="73156-115">행 ID는 작고 효율적인 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="73156-115">The row id is a small and efficient structure.</span></span> <span data-ttu-id="73156-116">데이터 설계자는 비클러스터형 인덱스를 통해 항상 데이터에 액세스하고 RID가 클러스터형 인덱스 키보다 작은 경우에 힙을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73156-116">Sometimes data architects use heaps when data is always accessed through nonclustered indexes and the RID is smaller than a clustered index key.</span></span>  
  
## <a name="when-not-to-use-a-heap"></a><span data-ttu-id="73156-117">힙을 사용하지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="73156-117">When Not to Use a Heap</span></span>  
 <span data-ttu-id="73156-118">데이터가 주로 정렬된 순서대로 반환되는 경우에는 힙을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73156-118">Do not use a heap when the data is frequently returned in a sorted order.</span></span> <span data-ttu-id="73156-119">정렬 열에 대해 클러스터형 인덱스를 사용하면 정렬 작업이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73156-119">A clustered index on the sorting column could avoid the sorting operation.</span></span>  
  
 <span data-ttu-id="73156-120">데이터를 자주 그룹화하는 경우 힙을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73156-120">Do not use a heap when the data is frequently grouped together.</span></span> <span data-ttu-id="73156-121">데이터를 그룹화하기 전에 데이터를 정렬해야 하며, 정렬 열에 대해 클러스터형 인덱스를 사용하면 정렬 작업이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73156-121">Data must be sorted before it is grouped, and a clustered index on the sorting column could avoid the sorting operation.</span></span>  
  
 <span data-ttu-id="73156-122">테이블에서 데이터 범위를 자주 쿼리하는 경우 힙을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73156-122">Do not use a heap when ranges of data are frequently queried from the table.</span></span>  <span data-ttu-id="73156-123">범위 열에 대해 클러스터형 인덱스를 사용하면 전체 힙을 정렬할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="73156-123">A clustered index on the range column will avoid sorting the entire heap.</span></span>  
  
 <span data-ttu-id="73156-124">비클러스터형 인덱스가 없고 테이블이 큰 경우 힙을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73156-124">Do not use a heap when there are no nonclustered indexes and the table is large.</span></span> <span data-ttu-id="73156-125">힙에서 행을 찾으려면 힙의 모든 행을 읽어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73156-125">In a heap, all rows of the heap must be read to find any row.</span></span>  
  
## <a name="managing-heaps"></a><span data-ttu-id="73156-126">힙 관리</span><span class="sxs-lookup"><span data-stu-id="73156-126">Managing Heaps</span></span>  
 <span data-ttu-id="73156-127">힙을 만들려면 클러스터형 인덱스가 없는 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="73156-127">To create a heap, create a table without a clustered index.</span></span> <span data-ttu-id="73156-128">테이블에 이미 클러스터형 인덱스가 포함되어 있는 경우 클러스터형 인덱스를 삭제하여 테이블을 힙에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73156-128">If a table already has a clustered index, drop the clustered index to return the table to a heap.</span></span>  
  
 <span data-ttu-id="73156-129">힙을 제거하려면 힙에 클러스터형 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="73156-129">To remove a heap, create a clustered index on the heap.</span></span>  
  
 <span data-ttu-id="73156-130">힙을 다시 작성하여 불필요하게 사용된 공간을 복구하려면 힙에 클러스터형 인덱스를 만든 다음 해당 클러스터형 인덱스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="73156-130">To rebuild a heap to reclaim wasted space, create a clustered index on the heap, and then drop that clustered index.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="73156-131">클러스터형 인덱스를 만들거나 삭제하면 전체 테이블을 다시 쓸 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="73156-131">Creating or dropping clustered indexes requires rewriting the entire table.</span></span> <span data-ttu-id="73156-132">테이블에 비클러스터형 인덱스가 포함되어 있는 경우 클러스터형 인덱스가 변경될 때마다 모든 비클러스터형 인덱스를 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73156-132">If the table has nonclustered indexes, all the nonclustered indexes must all be recreated whenever the clustered index is changed.</span></span> <span data-ttu-id="73156-133">따라서 힙을 클러스터형 인덱스 구조로 변경하거나 클러스터형 인덱스를 힙으로 변경하면 tempdb에서 데이터를 다시 정렬하는 데 많은 디스크 공간이 필요하고 많은 시간이 소요될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73156-133">Therefore, changing from a heap to a clustered index structure or back can take a lot of time and require disk space for reordering data in tempdb.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="73156-134">관련 내용</span><span class="sxs-lookup"><span data-stu-id="73156-134">Related Content</span></span>  
 [<span data-ttu-id="73156-135">CREATE INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="73156-135">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
 [<span data-ttu-id="73156-136">DROP INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="73156-136">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
 [<span data-ttu-id="73156-137">클러스터형 및 비클러스터형 인덱스 소개</span><span class="sxs-lookup"><span data-stu-id="73156-137">Clustered and Nonclustered Indexes Described</span></span>](clustered-and-nonclustered-indexes-described.md)  
  
  
