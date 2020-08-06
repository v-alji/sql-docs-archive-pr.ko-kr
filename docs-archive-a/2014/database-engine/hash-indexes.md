---
title: 해시 인덱스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f4bdc9c1-7922-4fac-8183-d11ec58fec4e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 05b8d1e3a5d92078cc2ec3fe7cd5b6d3fb5b47c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741228"
---
# <a name="hash-indexes"></a><span data-ttu-id="a5858-102">해시 인덱스</span><span class="sxs-lookup"><span data-stu-id="a5858-102">Hash Indexes</span></span>
  <span data-ttu-id="a5858-103">인덱스는 메모리 최적화 테이블의 진입점으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-103">Indexes are used as entry points for memory-optimized tables.</span></span> <span data-ttu-id="a5858-104">테이블의 행을 읽으려면 메모리에 있는 데이터를 찾을 인덱스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-104">Reading rows from a table requires an index to locate the data in memory.</span></span>  
  
 <span data-ttu-id="a5858-105">해시 인덱스는 나란히 있는 버킷의 컬렉션으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-105">A hash index consists of a collection of buckets organized in an array.</span></span> <span data-ttu-id="a5858-106">해시 함수는 인덱스 키를 해시 인덱스의 해당 버킷으로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-106">A hash function maps index keys to corresponding buckets in the hash index.</span></span> <span data-ttu-id="a5858-107">다음 그림에서는 해시 인덱스에 있는 세 개의 서로 다른 버킷에 매핑되는 세 개의 인덱스 키를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-107">The following figure shows three index keys that are mapped to three different buckets in the hash index.</span></span> <span data-ttu-id="a5858-108">이해를 돕기 위해 해시 함수 이름은 f(x)입니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-108">For illustration purposes the hash function name is f(x).</span></span>  
  
 <span data-ttu-id="a5858-109">![인덱스 키가 여러 버킷에 매핑되었습니다.](../../2014/database-engine/media/hekaton-tables-2.gif "인덱스 키가 여러 버킷에 매핑되었습니다.")</span><span class="sxs-lookup"><span data-stu-id="a5858-109">![Index keys mapped to different buckets.](../../2014/database-engine/media/hekaton-tables-2.gif "Index keys mapped to different buckets.")</span></span>  
  
 <span data-ttu-id="a5858-110">해시 인덱스에 사용되는 해시 함수의 특징은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-110">The hashing function used for hash indexes has the following characteristics:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="a5858-111">에는 모든 해시 인덱스에 사용되는 하나의 해시 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-111">has one hash function that is used for all hash indexes.</span></span>  
  
-   <span data-ttu-id="a5858-112">해시 함수는 결정적입니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-112">The hash function is deterministic.</span></span> <span data-ttu-id="a5858-113">동일한 인덱스 키가 항상 해시 인덱스의 동일한 버킷에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-113">The same index key is always mapped to the same bucket in the hash index.</span></span>  
  
-   <span data-ttu-id="a5858-114">여러 인덱스 키를 동일한 해시 버킷에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-114">Multiple index keys may be mapped to the same hash bucket.</span></span>  
  
-   <span data-ttu-id="a5858-115">해시 함수는 균형을 이룹니다. 즉, 해시 버킷에 대한 인덱스 키 값의 분포는 일반적으로 포아송 분포를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-115">The hash function is balanced, meaning that the distribution of index key values over hash buckets typically follows a Poisson distribution.</span></span>  
  
     <span data-ttu-id="a5858-116">포아송 분포는 균등한 분포가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-116">Poisson distribution is not an even distribution.</span></span> <span data-ttu-id="a5858-117">인덱스 키 값은 해시 버킷에 균등하게 분포되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-117">Index key values are not evenly distributed in the hash buckets.</span></span> <span data-ttu-id="a5858-118">예를 들어 *n* 개의 해시 버킷에 대한 *n* 개의 고유 인덱스 키의 포아송 분포는 버킷을 대략적으로 삼등분합니다. 삼등분된 버킷 부분에는 공백, 하나의 인덱스 키, 두 개의 인덱스 키가 각각 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-118">For example, a Poisson distribution of *n* distinct index keys over *n* hash buckets results in approximately one third empty buckets, one third of the buckets containing one index key, and the other third containing two index keys.</span></span> <span data-ttu-id="a5858-119">소수의 버킷에 세 개 이상의 키가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-119">A small number of buckets will contain more than two keys.</span></span>  
  
 <span data-ttu-id="a5858-120">두 개의 인덱스 키가 동일한 해시 버킷에 매핑되면 해시 충돌이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-120">If two index keys are mapped to the same hash bucket, there is a hash collision.</span></span> <span data-ttu-id="a5858-121">대부분의 해시 충돌은 읽기 작업의 성능에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-121">A large number of hash collisions can have a performance impact on read operations.</span></span>  
  
 <span data-ttu-id="a5858-122">메모리 내 해시 인덱스 구조는 메모리 포인터의 배열로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-122">The in-memory hash index structure consists of an array of memory pointers.</span></span> <span data-ttu-id="a5858-123">각 버킷은 이 배열의 오프셋에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-123">Each bucket maps to an offset in this array.</span></span> <span data-ttu-id="a5858-124">배열의 각 버킷은 해당 해시 버킷의 첫 번째 행을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-124">Each bucket in the array points to the first row in that hash bucket.</span></span> <span data-ttu-id="a5858-125">버킷의 각 행은 그 다음 행을 가리키기 때문에 다음 그림과 같이 각 해시 버킷에 대한 행 체인이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-125">Each row in the bucket points to the next row, thus resulting in a chain of rows for each hash bucket, as illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="a5858-126">![메모리 내 해시 인덱스 구조](../../2014/database-engine/media/hekaton-tables-3.gif "메모리 내 해시 인덱스 구조")</span><span class="sxs-lookup"><span data-stu-id="a5858-126">![The in-memory hash index structure.](../../2014/database-engine/media/hekaton-tables-3.gif "The in-memory hash index structure.")</span></span>  
  
 <span data-ttu-id="a5858-127">이 그림에는 행이 포함된 세 개의 버킷이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-127">The figure has three buckets with rows.</span></span> <span data-ttu-id="a5858-128">맨 위에서 두 번째 버킷에는 세 개의 빨간색 행이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-128">The second bucket from the top contains the three red rows.</span></span> <span data-ttu-id="a5858-129">네 번째 버킷에는 하나의 파란색 행이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-129">The fourth bucket contains the single blue row.</span></span> <span data-ttu-id="a5858-130">맨 아래 버킷에는 두 개의 녹색 행이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-130">The bottom bucket contains the two green rows.</span></span> <span data-ttu-id="a5858-131">이러한 행은 동일한 행의 서로 다른 버전일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5858-131">These could be different versions of the same row.</span></span>  
  
 <span data-ttu-id="a5858-132">메모리 최적화 테이블의 인덱스에 대한 자세한 내용은 [Guidelines for Using Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5858-132">For more information about indexes for memory-optimized tables, see [Guidelines for Using Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5858-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a5858-133">See Also</span></span>  
 [<span data-ttu-id="a5858-134">메모리 액세스에 최적화된 테이블의 인덱스</span><span class="sxs-lookup"><span data-stu-id="a5858-134">Indexes on Memory-Optimized Tables</span></span>](../../2014/database-engine/indexes-on-memory-optimized-tables.md)  
  
  
