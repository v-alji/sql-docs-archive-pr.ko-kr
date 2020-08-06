---
title: 데이터 압축 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- page compression [Database Engine]
- indexes [SQL Server], compressed
- compressed indexes [SQL Server]
- storage compression [Database Engine]
- tables [SQL Server], compressed
- storage [SQL Server], compressed
- compression [SQL Server]
- row compression [Database Engine]
- compression [SQL Server], about compressed tables and indexes
- data compression [Database Engine]
- compressed tables [SQL Server]
ms.assetid: 5f33e686-e115-4687-bd39-a00c48646513
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 48c4b11963d8e05ff7787ce9200329daf2e899ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659475"
---
# <a name="data-compression"></a><span data-ttu-id="ca84a-102">Data Compression</span><span class="sxs-lookup"><span data-stu-id="ca84a-102">Data Compression</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="ca84a-103">는 rowstore 테이블 및 인덱스를 위해 행 및 페이지 압축을 지원하며 columnstore 테이블 및 인덱스를 위해 columnstore 및 columnstore 보관 압축을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-103">supports row and page compression for rowstore tables and indexes, and supports columnstore and columnstore archival compression for columnstore tables and indexes.</span></span>  
  
 <span data-ttu-id="ca84a-104">rowstore 테이블 및 인덱스의 경우 데이터베이스 크기를 줄이려면 데이터 압축 기능을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="ca84a-104">For rowstore tables and indexes, use the data compression feature to help reduce the size of the database.</span></span> <span data-ttu-id="ca84a-105">데이터를 압축하면 공간을 절약할 수 있을 뿐만 아니라 데이터가 보다 적은 수의 페이지에 저장되어 쿼리가 디스크에서 읽어야 하는 페이지가 적어지므로 I/O가 많은 작업의 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-105">In addition to saving space, data compression can help improve performance of I/O intensive workloads because the data is stored in fewer pages and queries need to read fewer pages from disk.</span></span> <span data-ttu-id="ca84a-106">그러나 데이터를 애플리케이션과 교환하는 동안 데이터를 압축하고 압축 해제하기 위해 데이터베이스 서버에 추가 CPU 리소스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-106">However, extra CPU resources are required on the database server to compress and decompress the data, while data is exchanged with the application.</span></span> <span data-ttu-id="ca84a-107">다음 데이터베이스 개체에 대해 행 및 페이지 압축을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-107">You can configure row and page compression on the following database objects:</span></span>  
  
-   <span data-ttu-id="ca84a-108">힙으로 저장되는 전체 테이블</span><span class="sxs-lookup"><span data-stu-id="ca84a-108">A whole table that is stored as a heap.</span></span>  
  
-   <span data-ttu-id="ca84a-109">클러스터형 인덱스로 저장되는 전체 테이블</span><span class="sxs-lookup"><span data-stu-id="ca84a-109">A whole table that is stored as a clustered index.</span></span>  
  
-   <span data-ttu-id="ca84a-110">전체 비클러스터형 인덱스</span><span class="sxs-lookup"><span data-stu-id="ca84a-110">A whole nonclustered index.</span></span>  
  
-   <span data-ttu-id="ca84a-111">전체 인덱싱된 뷰</span><span class="sxs-lookup"><span data-stu-id="ca84a-111">A whole indexed view.</span></span>  
  
-   <span data-ttu-id="ca84a-112">분할된 테이블과 인덱스의 경우 파티션별로 압축 옵션을 구성할 수 있고 개체의 다양한 파티션에 동일한 압축 설정을 구성할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-112">For partitioned tables and indexes, you can configure the compression option for each partition, and the various partitions of an object do not have to have the same compression setting.</span></span>  
  
 <span data-ttu-id="ca84a-113">columnstore 테이블 및 인덱스의 경우 모든 columnstore 테이블 및 인덱스는 항상 columnstore 압축을 사용하며 이것은 사용자가 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-113">For columnstore tables and indexes, all columnstore tables and indexes always use columnstore compression and this is not user configurable.</span></span> <span data-ttu-id="ca84a-114">데이터를 저장하고 검색할 추가 시간과 CPU 리소스가 있는 상황에서 데이터 크기를 더 줄이려면 columnstore 보관 압축을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="ca84a-114">Use columnstore archival compression to further reduce the data size for situations when you can afford extra time and CPU resources to store and retrieve the data.</span></span>  <span data-ttu-id="ca84a-115">다음 데이터베이스 개체에 대해 columnstore 보관 압축을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-115">You can configure columnstore archival compression on the following database objects:</span></span>  
  
-   <span data-ttu-id="ca84a-116">전체 columnstore 테이블 또는 전체 클러스터형 columnstore 인덱스</span><span class="sxs-lookup"><span data-stu-id="ca84a-116">A whole columnstore table or a whole clustered columnstore index.</span></span>  <span data-ttu-id="ca84a-117">columnstore 테이블은 클러스터형 columnstore 인덱스로 저장되므로 둘 다 같은 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-117">Since a columnstore table is stored as a clustered columnstore index, both approaches have the same results.</span></span>  
  
-   <span data-ttu-id="ca84a-118">전체 비클러스터형 columnstore 인덱스</span><span class="sxs-lookup"><span data-stu-id="ca84a-118">A whole nonclustered columnstore index.</span></span>  
  
-   <span data-ttu-id="ca84a-119">분할된 columnstore 테이블과 columnstore 인덱스의 경우 파티션별로 보관 압축 옵션을 구성할 수 있고 다양한 파티션에 동일한 보관 압축 설정을 구성할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-119">For partitioned columnstore tables and columnstore indexes, you can configure the archival compression option for each partition, and the various partitions do not have to have the same archival compression setting.</span></span>  
  
## <a name="considerations-for-when-you-use-row-and-page-compression"></a><span data-ttu-id="ca84a-120">행 및 페이지 압축 시 고려 사항</span><span class="sxs-lookup"><span data-stu-id="ca84a-120">Considerations for When You Use Row and Page Compression</span></span>  
 <span data-ttu-id="ca84a-121">행 및 페이지 압축을 사용할 때 다음 사항을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-121">When you use row and page compression, be aware the following considerations:</span></span>  
  
-   <span data-ttu-id="ca84a-122">데이터 압축의 세부 사항은 서비스 팩이나 후속 릴리스에서 예고 없이 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-122">The details of data compression are subject to change without notice in service packs or subsequent releases.</span></span>  
  
-   <span data-ttu-id="ca84a-123">일부 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서는 압축을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-123">Compression is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ca84a-124">자세한 내용은 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca84a-124">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="ca84a-125">시스템 테이블에는 압축을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-125">Compression is not available for system tables.</span></span>  
  
-   <span data-ttu-id="ca84a-126">압축하면 한 페이지에 더 많은 행을 저장할 수 있지만 테이블 또는 인덱스의 최대 행 크기는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-126">Compression can allow more rows to be stored on a page, but does not change the maximum row size of a table or index.</span></span>  
  
-   <span data-ttu-id="ca84a-127">최대 행 크기와 압축 오버헤드를 더한 값이 최대 행 크기 8060바이트를 초과하는 테이블에서는 압축을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-127">A table cannot be enabled for compression when the maximum row size plus the compression overhead exceeds the maximum row size of 8060 bytes.</span></span> <span data-ttu-id="ca84a-128">예를 들어, c1 및 c2 열이 있는 테이블은 `char(8000)` `char(53)` 추가 압축 오버 헤드로 인해 압축할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-128">For example, a table that has the columns c1`char(8000)` and c2`char(53)` cannot be compressed because of the additional compression overhead.</span></span> <span data-ttu-id="ca84a-129">vardecimal 스토리지 형식이 사용되는 경우 해당 형식을 사용하면 행 크기 검사가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-129">When the vardecimal storage format is used, the row-size check is performed when the format is enabled.</span></span> <span data-ttu-id="ca84a-130">행 및 페이지 압축의 경우 개체가 처음 압축될 때 행 크기 검사가 수행된 다음 각 행을 삽입하거나 수정할 때 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-130">For row and page compression, the row-size check is performed when the object is initially compressed, and then checked as each row is inserted or modified.</span></span> <span data-ttu-id="ca84a-131">압축에는 다음 두 가지 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-131">Compression enforces the following two rules:</span></span>  
  
    -   <span data-ttu-id="ca84a-132">고정 길이 형식으로의 업데이트가 항상 성공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-132">An update to a fixed-length type must always succeed.</span></span>  
  
    -   <span data-ttu-id="ca84a-133">데이터 압축 비활성화에 항상 성공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-133">Disabling data compression must always succeed.</span></span> <span data-ttu-id="ca84a-134">압축된 행이 8060바이트 미만으로 페이지에 맞더라도 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 압축하지 않을 경우 행에 맞지 않는 업데이트 내용을 적용할 수 없도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-134">Even if the compressed row fits on the page, which means that it is less than 8060 bytes; [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prevents updates that would not fit on the row when it is uncompressed.</span></span>  
  
-   <span data-ttu-id="ca84a-135">파티션 목록을 지정하는 경우 개별 파티션에 대한 압축 유형을 ROW, PAGE 또는 NONE으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-135">When a list of partitions is specified, the compression type can be set to ROW, PAGE, or NONE on individual partitions.</span></span> <span data-ttu-id="ca84a-136">파티션 목록을 지정하지 않은 경우에는 모든 파티션이 문에 지정된 데이터 압축 속성을 사용하여 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-136">If the list of partitions is not specified, all partitions are set with the data compression property that is specified in the statement.</span></span> <span data-ttu-id="ca84a-137">테이블이나 인덱스를 만들 때 달리 지정하지 않는 한 데이터 압축이 NONE으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-137">When a table or index is created, data compression is set to NONE unless otherwise specified.</span></span> <span data-ttu-id="ca84a-138">테이블을 수정할 경우에는 달리 지정하지 않는 한 기존 압축이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-138">When a table is modified, the existing compression is preserved unless otherwise specified.</span></span>  
  
-   <span data-ttu-id="ca84a-139">범위를 벗어난 파티션 목록을 지정하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-139">If you specify a list of partitions or a partition that is out of range, an error will be generated.</span></span>  
  
-   <span data-ttu-id="ca84a-140">비클러스터형 인덱스는 테이블의 압축 속성을 상속하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-140">Nonclustered indexes do not inherit the compression property of the table.</span></span> <span data-ttu-id="ca84a-141">인덱스를 압축하려면 인덱스의 압축 속성을 명시적으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-141">To compress indexes, you must explicitly set the compression property of the indexes.</span></span> <span data-ttu-id="ca84a-142">기본적으로 인덱스를 만들 때 인덱스의 압축 설정은 NONE으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-142">By default, the compression setting for indexes will set to NONE when the index is created.</span></span>  
  
-   <span data-ttu-id="ca84a-143">힙에 클러스터형 인덱스를 만드는 경우 이 클러스터형 인덱스는 다른 압축 상태를 지정하지 않는 한 힙의 압축 상태를 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-143">When a clustered index is created on a heap, the clustered index inherits the compression state of the heap unless an alternative compression state is specified.</span></span>  
  
-   <span data-ttu-id="ca84a-144">힙이 페이지 수준 압축을 사용하도록 구성된 경우 페이지는 다음과 같은 방식으로만 페이지 수준 압축을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-144">When a heap is configured for page-level compression, pages receive page-level compression only in the following ways:</span></span>  
  
    -   <span data-ttu-id="ca84a-145">대량 최적화가 사용하도록 설정된 상태로 데이터를 대량으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-145">Data is bulk imported with bulk optimizations enabled.</span></span>  
  
    -   <span data-ttu-id="ca84a-146">INSERT INTO ... WITH (TABLOCK) 구문 및 테이블에 비클러스터형 인덱스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-146">Data is inserted using INSERT INTO ... WITH (TABLOCK) syntax and the table does not have a nonclustered index.</span></span>  
  
    -   <span data-ttu-id="ca84a-147">ALTER TABLE ... REBUILD 문을 PAGE 압축 옵션과 함께 실행하여 테이블을 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-147">A table is rebuilt by executing the ALTER TABLE ... REBUILD statement with the PAGE compression option.</span></span>  
  
-   <span data-ttu-id="ca84a-148">DML 작업의 일부로 힙에 할당된 새 페이지에서는 힙이 다시 작성될 때까지 PAGE 압축을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-148">New pages allocated in a heap as part of DML operations will not use PAGE compression until the heap is rebuilt.</span></span> <span data-ttu-id="ca84a-149">압축을 제거하고 다시 적용하거나, 클러스터형 인덱스를 만들거나 제거하여 힙을 다시 작성하십시오.</span><span class="sxs-lookup"><span data-stu-id="ca84a-149">Rebuild the heap by removing and reapplying compression, or by creating and removing a clustered index.</span></span>  
  
-   <span data-ttu-id="ca84a-150">힙의 압축 설정을 변경하는 경우 힙의 새 행 위치에 대한 포인터를 포함하도록 테이블의 모든 비클러스터형 인덱스를 다시 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-150">Changing the compression setting of a heap requires all nonclustered indexes on the table to be rebuilt so that they have pointers to the new row locations in the heap.</span></span>  
  
-   <span data-ttu-id="ca84a-151">온라인이나 오프라인으로 ROW 또는 PAGE 압축을 사용하거나 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-151">You can enable or disable ROW or PAGE compression online or offline.</span></span> <span data-ttu-id="ca84a-152">힙에서 압축을 사용하도록 설정하는 것은 온라인 작업의 경우 단일 스레드입니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-152">Enabling compression on a heap is single threaded for an online operation.</span></span>  
  
-   <span data-ttu-id="ca84a-153">행 또는 페이지 압축을 사용하거나 사용하지 않도록 설정하기 위한 디스크 공간 요구 사항은 인덱스를 만들거나 다시 작성하는 경우와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-153">The disk space requirements for enabling or disabling row or page compression are the same as for creating or rebuilding an index.</span></span> <span data-ttu-id="ca84a-154">분할된 데이터의 경우 한 번에 하나의 파티션에 대해 압축을 사용하거나 사용하지 않도록 설정하여 필요한 공간을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-154">For partitioned data, you can reduce the space that is required by enabling or disabling compression for one partition at a time.</span></span>  
  
-   <span data-ttu-id="ca84a-155">분할된 테이블에서 파티션의 압축 상태를 확인하려면 sys.partitions 카탈로그 뷰의 data_compression 열을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-155">To determine the compression state of partitions in a partitioned table, query the data_compression column of the sys.partitions catalog view.</span></span>  
  
-   <span data-ttu-id="ca84a-156">인덱스를 압축하는 경우 리프 수준 페이지는 행 압축과 페이지 압축을 모두 사용하여 압축될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-156">When you are compressing indexes, leaf-level pages can be compressed with both row and page compression.</span></span> <span data-ttu-id="ca84a-157">리프 수준이 아닌 페이지는 페이지 압축을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-157">Non-leaf-level pages do not receive page compression.</span></span>  
  
-   <span data-ttu-id="ca84a-158">큰 값 데이터 형식은 해당 크기 때문에 일반 행 데이터와 별도로 특수 용도 페이지에 저장되기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-158">Because of their size, large-value data types are sometimes stored separately from the normal row data on special purpose pages.</span></span> <span data-ttu-id="ca84a-159">별도로 저장되는 데이터에는 데이터 압축을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-159">Data compression is not available for the data that is stored separately.</span></span>  
  
-   <span data-ttu-id="ca84a-160">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 에서 vardecimal 스토리지 형식을 구현한 테이블을 업그레이드해도 해당 설정은 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-160">Tables which implemented the vardecimal storage format in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] will retain that setting when upgraded.</span></span> <span data-ttu-id="ca84a-161">vardecimal 스토리지 형식의 테이블에 행 압축을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-161">You can apply row compression to a table that has the vardecimal storage format.</span></span> <span data-ttu-id="ca84a-162">그러나 행 압축이 vardecimal 스토리지 형식의 상위 집합이므로 vardecimal 스토리지 형식을 유지할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-162">However, because row compression is a superset of the vardecimal storage format, there is no reason to retain the vardecimal storage format.</span></span> <span data-ttu-id="ca84a-163">vardecimal 스토리지 형식과 행 압축을 함께 사용해도 10진수 값이 추가로 압축되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-163">Decimal values gain no additional compression when you combine the vardecimal storage format with row compression.</span></span> <span data-ttu-id="ca84a-164">vardecimal 스토리지 형식의 테이블에 페이지 압축을 적용할 수 있지만 vardecimal 스토리지 형식 열이 추가로 압축되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-164">You can apply page compression to a table that has the vardecimal storage format; however, the vardecimal storage format columns probably will not achieve additional compression.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="ca84a-165">에서는 vardecimal 스토리지 형식을 지원하지만 행 수준 압축으로 동일한 결과를 얻을 수 있으므로 vardecimal 스토리지 형식은 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-165">supports the vardecimal storage format; however, because row-level compression achieves the same goals, the vardecimal storage format is deprecated.</span></span> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="using-columnstore-and-columnstore-archive-compression"></a><span data-ttu-id="ca84a-166">Columnstore 및 Columnstore 보관 압축 사용</span><span class="sxs-lookup"><span data-stu-id="ca84a-166">Using Columnstore and Columnstore Archive Compression</span></span>  
  
||  
|-|  
|<span data-ttu-id="ca84a-167">**적용 대상**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] ~ [현재 버전](https://go.microsoft.com/fwlink/p/?LinkId=299658)).</span><span class="sxs-lookup"><span data-stu-id="ca84a-167">**Applies to**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] through [current version](https://go.microsoft.com/fwlink/p/?LinkId=299658)).</span></span>|  
  
### <a name="basics"></a><span data-ttu-id="ca84a-168">기본 사항</span><span class="sxs-lookup"><span data-stu-id="ca84a-168">Basics</span></span>  
 <span data-ttu-id="ca84a-169">Columnstore 테이블 및 인덱스는 항상 columnstore 압축으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-169">Columnstore tables and indexes are always stored with columnstore compression.</span></span> <span data-ttu-id="ca84a-170">보관 압축이라고 하는 추가 압축을 구성하여 columnstore 데이터 크기를 더 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-170">You can further reduce the size of columnstore data by configuring an additional compression called archival compression.</span></span>  <span data-ttu-id="ca84a-171">보관 압축을 수행하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 데이터에 대해 Microsoft XPRESS 압축 알고리즘을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-171">To perform archival compression, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs the Microsoft XPRESS compression algorithm on the data.</span></span> <span data-ttu-id="ca84a-172">다음 데이터 압축 유형을 사용하여 보관 압축을 추가하거나 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-172">Add or remove archival compression by using the following data compression types:</span></span>  
  
-   <span data-ttu-id="ca84a-173">보관 압축으로 columnstore 데이터를 압축하려면 `COLUMNSTORE_ARCHIVE` 데이터 압축을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="ca84a-173">Use `COLUMNSTORE_ARCHIVE` data compression to compress columnstore data with archival compression.</span></span>  
  
-   <span data-ttu-id="ca84a-174">보관 압축을 풀려면 **COLUMNSTORE** 데이터 압축을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="ca84a-174">Use **COLUMNSTORE** data compression to decompress archival compression.</span></span> <span data-ttu-id="ca84a-175">결과 데이터는 columnstore 압축으로 계속해서 압축됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-175">This resulting data will continue to be compressed with columnstore compression.</span></span>  
  
 <span data-ttu-id="ca84a-176">보관 압축을 추가하려면 REBUILD 옵션 및 DATA COMPRESSION = COLUMNSTORE와 함께 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) 또는 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) 를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="ca84a-176">To add archival compression, use [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) or [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) with the REBUILD option and DATA COMPRESSION = COLUMNSTORE.</span></span>  
  
 <span data-ttu-id="ca84a-177">예제:</span><span class="sxs-lookup"><span data-stu-id="ca84a-177">Examples:</span></span>  
  
```  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  COLUMNSTORE_ARCHIVE) ;  
  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (DATA_COMPRESSION =  COLUMNSTORE_ARCHIVE) ;  
  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (DATA_COMPRESSION =  COLUMNSTORE_ARCHIVE ON PARTITIONS (2,4)) ;  
  
```  
  
 <span data-ttu-id="ca84a-178">보관 압축을 제거하고 데이터를 columnst또는e 압축으로 복원하려면 REBUILD 옵션 및 DATA COMPRESSION = COLUMNSTORE와 함께 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) 또는 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) 를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="ca84a-178">To remove archival compression and restore the data to columnstore compression, use [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) or [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) with the REBUILD option and DATA COMPRESSION = COLUMNSTORE.</span></span>  
  
 <span data-ttu-id="ca84a-179">예제:</span><span class="sxs-lookup"><span data-stu-id="ca84a-179">Examples:</span></span>  
  
```  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  COLUMNSTORE) ;  
  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (DATA_COMPRESSION =  COLUMNSTORE) ;  
  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (DATA_COMPRESSION =  COLUMNSTORE ON PARTITIONS (2,4) ) ;  
  
```  
  
 <span data-ttu-id="ca84a-180">다음 예에서는 데이터 압축을 일부 파티션의 경우 columnstore로 설정하고 다른 파티션의 경우 columnstore 보관으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-180">This next example sets the data compression to columnstore on some partitions, and to columnstore archival on other partitions.</span></span>  
  
```  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (  
    DATA_COMPRESSION =  COLUMNSTORE ON PARTITIONS (4,5),  
    DATA COMPRESSION = COLUMNSTORE_ARCHIVE ON PARTITIONS (1,2,3)  
) ;  
```  
  
### <a name="performance"></a><span data-ttu-id="ca84a-181">성능</span><span class="sxs-lookup"><span data-stu-id="ca84a-181">Performance</span></span>  
 <span data-ttu-id="ca84a-182">보관 압축으로 columnstore 인덱스를 압축하면 보관 압축을 사용하지 않는 columnstore 인덱스보다 인덱스가 느리게 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-182">Compressing columnstore indexes with archival compression will cause the index to perform slower than columnstore indexes that do not have the archival compression.</span></span>  <span data-ttu-id="ca84a-183">데이터를 압축하고 검색할 추가 시간과 CPU 리소스가 있는 상황에서만 보관 압축을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="ca84a-183">Use archival compression only when you can afford to use extra time and CPU resources to compress and retrieve the data.</span></span>  
  
 <span data-ttu-id="ca84a-184">성능 저하의 이점은 자주 액세스하지 않는 데이터에 대해 유용한 스토리지 용량 감소입니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-184">The benefit of slower performance is reduced storage which is useful for data that is not frequently accessed.</span></span> <span data-ttu-id="ca84a-185">예를 들어, 월별 데이터에 대해 파티션이 있고 대부분의 작업이 가장 최근 월에 대한 작업인 경우 스토리지 요구 사항을 줄이기 위해 이전 월을 보관할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-185">For example, if you have a partition for each month of data, and most of your activity is for the most recent months, you could archive older months to reduce the storage requirements.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="ca84a-186">메타데이터</span><span class="sxs-lookup"><span data-stu-id="ca84a-186">Metadata</span></span>  
 <span data-ttu-id="ca84a-187">다음 시스템 뷰에는 클러스터형 인덱스의 데이터 압축 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-187">The following system views contain information about data compression for clustered indexes:</span></span>  
  
-   <span data-ttu-id="ca84a-188">[&#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) - `type` 및 열에는 `type_desc` 클러스터형 columnstore 및 비클러스터형 columnstore가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-188">[sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) - The `type` and `type_desc` columns include CLUSTERED COLUMNSTORE and NONCLUSTERED COLUMNSTORE.</span></span>  
  
-   <span data-ttu-id="ca84a-189">[&#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql) - `data_compression` 및 열에는 `data_compression_desc` COLUMNSTORE 및 COLUMNSTORE_ARCHIVE가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-189">[sys.partitions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql) - The `data_compression` and `data_compression_desc` columns include COLUMNSTORE and COLUMNSTORE_ARCHIVE.</span></span>  
  
 <span data-ttu-id="ca84a-190">[sp_estimate_data_compression_savings&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) 프로시저는 columnstore 인덱스에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-190">The procedure [sp_estimate_data_compression_savings &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) does not apply to columnstore indexes.</span></span>  
  
## <a name="how-compression-affects-partitioned-tables-and-indexes"></a><span data-ttu-id="ca84a-191">압축이 분할된 테이블 및 인덱스에 주는 영향</span><span class="sxs-lookup"><span data-stu-id="ca84a-191">How Compression Affects Partitioned Tables and Indexes</span></span>  
 <span data-ttu-id="ca84a-192">분할된 테이블 및 인덱스에서 데이터 압축을 사용할 때는 다음 사항을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-192">When you use data compression with partitioned tables and indexes, be aware of the following considerations:</span></span>  
  
-   <span data-ttu-id="ca84a-193">ALTER PARTITION 문을 사용하여 파티션을 분할할 경우 두 파티션이 모두 원래 파티션의 데이터 압축 특성을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-193">When partitions are split by using the ALTER PARTITION statement, both partitions inherit the data compression attribute of the original partition.</span></span>  
  
-   <span data-ttu-id="ca84a-194">두 파티션을 병합할 경우 결과 파티션이 대상 파티션의 데이터 압축 특성을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-194">When two partitions are merged, the resultant partition inherits the data compression attribute of the destination partition.</span></span>  
  
-   <span data-ttu-id="ca84a-195">파티션을 전환하려면 파티션의 데이터 압축 속성이 테이블의 압축 속성과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-195">To switch a partition, the data compression property of the partition must match the compression property of the table.</span></span>  
  
-   <span data-ttu-id="ca84a-196">분할된 테이블 또는 인덱스의 압축을 수정하는 데에는 다음과 같은 두 가지 구문 변형을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-196">There are two syntax variations that you can use to modify the compression of a partitioned table or index:</span></span>  
  
    -   <span data-ttu-id="ca84a-197">다음 구문에서는 참조된 파티션만 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-197">The following syntax rebuilds only the referenced partition:</span></span>  
  
        ```  
        ALTER TABLE <table_name>   
        REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  <option>)  
        ```  
  
    -   <span data-ttu-id="ca84a-198">다음 구문에서는 참조되지 않는 파티션의 기존 압축 설정을 사용하여 전체 테이블을 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-198">The following syntax rebuilds the whole table by using the existing compression setting for any partitions that are not referenced:</span></span>  
  
        ```  
        ALTER TABLE <table_name>   
        REBUILD PARTITION = ALL   
        WITH (DATA_COMPRESSION = PAGE ON PARTITIONS(<range>),  
        ... )  
        ```  
  
     <span data-ttu-id="ca84a-199">분할된 인덱스에서는 같은 원칙에 따라 ALTER INDEX를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-199">Partitioned indexes follow the same principle using ALTER INDEX.</span></span>  
  
-   <span data-ttu-id="ca84a-200">클러스터형 인덱스를 삭제한 경우 파티션 구성표를 수정하지 않으면 해당 힙 파티션에서 데이터 압축 설정이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-200">When a clustered index is dropped, the corresponding heap partitions retain their data compression setting unless the partitioning scheme is modified.</span></span> <span data-ttu-id="ca84a-201">파티션 구성표를 변경하는 경우 모든 파티션이 압축되지 않은 상태로 다시 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-201">If the partitioning scheme is changed, all partitions are rebuilt to an uncompressed state.</span></span> <span data-ttu-id="ca84a-202">클러스터형 인덱스를 삭제하고 파티션 구성표를 변경하려면 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-202">To drop a clustered index and change the partitioning scheme requires the following steps:</span></span>  
  
     1. <span data-ttu-id="ca84a-203">클러스터형 인덱스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-203">Drop the clustered index.</span></span>  
  
     2. <span data-ttu-id="ca84a-204">압축 옵션을 지정하는 ALTER TABLE ... REBUILD ... 옵션을 사용하여 테이블을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-204">Modify the table by using the ALTER TABLE ... REBUILD ... option that specifies the compression option.</span></span>  
  
     <span data-ttu-id="ca84a-205">클러스터형 인덱스를 OFFLINE으로 삭제하면 클러스터형 인덱스의 상위 수준만 제거되므로 작업이 상당히 빠르게 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-205">To drop a clustered index OFFLINE is a very fast operation, because only the upper levels of clustered indexes are removed.</span></span> <span data-ttu-id="ca84a-206">클러스터형 인덱스를 ONLINE으로 삭제하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 1단계와 2단계에서 한 번씩, 총 두 번에 걸쳐 힙을 다시 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-206">When a clustered index is dropped ONLINE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must rebuild the heap two times, once for step 1 and once for step 2.</span></span>  
  
## <a name="how-compression-affects-replication"></a><span data-ttu-id="ca84a-207">압축이 복제에 주는 영향</span><span class="sxs-lookup"><span data-stu-id="ca84a-207">How Compression Affects Replication</span></span>  
 <span data-ttu-id="ca84a-208">데이터 압축과 복제를 함께 사용할 때는 다음 사항을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-208">When you are using data compression with replication, be aware of the following considerations:</span></span>  
  
-   <span data-ttu-id="ca84a-209">스냅샷 에이전트에서 초기 스키마 스크립트를 생성할 때 새 스키마는 테이블과 해당 인덱스 모두에 대해 동일한 압축 설정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-209">When the Snapshot Agent generates the initial schema script, the new schema will use the same compression settings for both the table and its indexes.</span></span> <span data-ttu-id="ca84a-210">압축을 인덱스에 사용하지 않고 테이블에만 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-210">Compression cannot be enabled on just the table and not the index.</span></span>  
  
-   <span data-ttu-id="ca84a-211">트랜잭션 복제의 경우 아티클 스키마 옵션에 따라 스크립팅할 종속 개체 및 속성이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-211">For transactional replication the article schema option determines what dependent objects and properties have to be scripted.</span></span> <span data-ttu-id="ca84a-212">자세한 내용은 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca84a-212">For more information, see [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span>  
  
     <span data-ttu-id="ca84a-213">배포 에이전트에서는 스크립트를 적용할 때 하위 구독자를 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-213">The Distribution Agent does not check for down-level Subscribers when it applies scripts.</span></span> <span data-ttu-id="ca84a-214">압축 복제를 선택하는 경우 하위 구독자에서 테이블을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-214">If the replication of compression is selected, creating the table on down-level Subscribers will fail.</span></span> <span data-ttu-id="ca84a-215">혼합 토폴로지의 경우 압축 복제를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="ca84a-215">In the case of a mixed topology, do not enable the replication of compression.</span></span>  
  
-   <span data-ttu-id="ca84a-216">병합 복제의 경우 게시 호환성 수준이 스키마 옵션을 재정의하며 스크립팅될 스키마 개체를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-216">For merge replication, publication compatibility level overrides the schema options and determines the schema objects that will be scripted.</span></span>  
  
     <span data-ttu-id="ca84a-217">혼합 토폴로지의 경우 새 압축 옵션을 지원할 필요가 없으면 게시 호환성 수준을 하위 구독자 버전으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-217">In the case of a mixed topology, if it is not required to support the new compression options, the publication compatibility level should be set to the down-level Subscriber version.</span></span> <span data-ttu-id="ca84a-218">새 압축 옵션이 필요하면 테이블을 만든 후 구독자에서 테이블을 압축합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-218">If it is required, compress tables on the Subscriber after they have been created.</span></span>  
  
 <span data-ttu-id="ca84a-219">다음 표에서는 복제하는 동안 압축을 제어하는 복제 설정을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-219">The following table shows replication settings that control compression during replication.</span></span>  
  
|<span data-ttu-id="ca84a-220">사용자 의도</span><span class="sxs-lookup"><span data-stu-id="ca84a-220">User intent</span></span>|<span data-ttu-id="ca84a-221">테이블 또는 인덱스에 대한 파티션 구성표 복제</span><span class="sxs-lookup"><span data-stu-id="ca84a-221">Replicate partition scheme for a table or index</span></span>|<span data-ttu-id="ca84a-222">압축 설정 복제</span><span class="sxs-lookup"><span data-stu-id="ca84a-222">Replicate compression settings</span></span>|<span data-ttu-id="ca84a-223">스크립팅 동작</span><span class="sxs-lookup"><span data-stu-id="ca84a-223">Scripting behavior</span></span>|  
|-----------------|-----------------------------------------------------|------------------------------------|------------------------|  
|<span data-ttu-id="ca84a-224">파티션 구성표를 복제하고 파티션의 구독자에서 압축 사용</span><span class="sxs-lookup"><span data-stu-id="ca84a-224">To replicate the partition scheme and enable compression on the Subscriber on the partition.</span></span>|<span data-ttu-id="ca84a-225">True</span><span class="sxs-lookup"><span data-stu-id="ca84a-225">True</span></span>|<span data-ttu-id="ca84a-226">True</span><span class="sxs-lookup"><span data-stu-id="ca84a-226">True</span></span>|<span data-ttu-id="ca84a-227">파티션 구성표와 압축 설정을 모두 스크립팅합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-227">Scripts both the partition scheme and the compression settings.</span></span>|  
|<span data-ttu-id="ca84a-228">파티션 구성표를 복제하지만 구독자에서 데이터를 압축하지 않음</span><span class="sxs-lookup"><span data-stu-id="ca84a-228">To replicate the partition scheme but not compress the data on the Subscriber.</span></span>|<span data-ttu-id="ca84a-229">True</span><span class="sxs-lookup"><span data-stu-id="ca84a-229">True</span></span>|<span data-ttu-id="ca84a-230">False</span><span class="sxs-lookup"><span data-stu-id="ca84a-230">False</span></span>|<span data-ttu-id="ca84a-231">파티션 구성표를 스크립팅하지만 파티션의 압축 설정은 스크립팅하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-231">Scripts out the partition scheme but not the compression settings for the partition.</span></span>|  
|<span data-ttu-id="ca84a-232">파티션 구성표를 복제하지 않고 구독자에서 데이터를 압축하지 않음</span><span class="sxs-lookup"><span data-stu-id="ca84a-232">To not replicate the partition scheme and not compress the data on the Subscriber.</span></span>|<span data-ttu-id="ca84a-233">False</span><span class="sxs-lookup"><span data-stu-id="ca84a-233">False</span></span>|<span data-ttu-id="ca84a-234">False</span><span class="sxs-lookup"><span data-stu-id="ca84a-234">False</span></span>|<span data-ttu-id="ca84a-235">파티션이나 압축 설정을 스크립팅하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-235">Does not script partition or compression settings.</span></span>|  
|<span data-ttu-id="ca84a-236">게시자에서 모든 파티션이 압축된 경우 구독자에서 테이블을 압축하지만 파티션 구성표를 복제하지 않음</span><span class="sxs-lookup"><span data-stu-id="ca84a-236">To compress the table on the Subscriber if all the partitions are compressed on the Publisher, but not replicate the partition scheme.</span></span>|<span data-ttu-id="ca84a-237">False</span><span class="sxs-lookup"><span data-stu-id="ca84a-237">False</span></span>|<span data-ttu-id="ca84a-238">True</span><span class="sxs-lookup"><span data-stu-id="ca84a-238">True</span></span>|<span data-ttu-id="ca84a-239">모든 파티션에서 압축을 사용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-239">Checks if all the partitions are enabled for compression.</span></span><br /><br /> <span data-ttu-id="ca84a-240">테이블 수준에서 압축을 스크립팅합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-240">Scripts out compression at the table level.</span></span>|  
  
## <a name="how-compression-affects-other-sql-server-components"></a><span data-ttu-id="ca84a-241">압축이 다른 SQL Server 구성 요소에 주는 영향</span><span class="sxs-lookup"><span data-stu-id="ca84a-241">How Compression Affects Other SQL Server Components</span></span>  
 <span data-ttu-id="ca84a-242">압축은 스토리지 엔진에서 발생하므로 데이터는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 다른 구성 요소 대부분에 압축되지 않은 상태로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-242">Compression occurs in the storage engine and the data is presented to most of the other components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in an uncompressed state.</span></span> <span data-ttu-id="ca84a-243">따라서 압축이 다른 구성 요소에 주는 영향은 다음으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-243">This limits the effects of compression on the other components to the following:</span></span>  
  
-   <span data-ttu-id="ca84a-244">대량 가져오기 및 내보내기 작업</span><span class="sxs-lookup"><span data-stu-id="ca84a-244">Bulk import and export operations</span></span>  
  
     <span data-ttu-id="ca84a-245">데이터를 내보낼 때는 네이티브 형식으로 내보내더라도 데이터가 압축되지 않는 행 형식으로 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-245">When data is exported, even in native format, the data is output in the uncompressed row format.</span></span> <span data-ttu-id="ca84a-246">따라서 내보낸 데이터 파일의 크기가 원본 데이터보다 훨씬 커질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-246">This can cause the size of exported data file to be significantly larger than the source data.</span></span>  
  
     <span data-ttu-id="ca84a-247">데이터를 가져올 때는 대상 테이블이 압축을 사용하도록 설정된 경우 스토리지 엔진에서 데이터를 압축된 행 형식으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-247">When data is imported, if the target table has been enabled for compression, the data is converted by the storage engine into compressed row format.</span></span> <span data-ttu-id="ca84a-248">이로 인해 데이터를 압축되지 않은 테이블로 가져올 때보다 CPU 사용량이 증가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-248">This can cause increased CPU usage compared to when data is imported into an uncompressed table.</span></span>  
  
     <span data-ttu-id="ca84a-249">페이지 압축을 사용하여 힙으로 데이터를 대량으로 가져오는 경우 대량 가져오기 작업에서는 데이터를 삽입할 때 페이지 압축을 사용하여 데이터를 압축하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-249">When data is bulk imported into a heap with page compression, the bulk import operation will try to compress the data with page compression when the data is inserted.</span></span>  
  
-   <span data-ttu-id="ca84a-250">백업 및 복원에는 압축이 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-250">Compression does not affect backup and restore.</span></span>  
  
-   <span data-ttu-id="ca84a-251">로그 전달에는 압축이 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-251">Compression does not affect log shipping.</span></span>  
  
-   <span data-ttu-id="ca84a-252">스파스 열에서는 데이터 압축이 호환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-252">Data compression is incompatible with sparse columns.</span></span> <span data-ttu-id="ca84a-253">따라서 스파스 열이 포함된 테이블은 압축할 수 없으며 스파스 열을 압축된 테이블에 추가할 수도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-253">Therefore, tables containing sparse columns cannot be compressed nor can sparse columns be added to a compressed table.</span></span>  
  
-   <span data-ttu-id="ca84a-254">데이터는 서로 다른 페이지 수 및 페이지당 행 수를 사용하여 저장되므로 압축을 사용하도록 설정하면 쿼리 계획이 변경될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca84a-254">Enabling compression can cause query plans to change because the data is stored using a different number of pages and number of rows per page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca84a-255">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ca84a-255">See Also</span></span>  
 <span data-ttu-id="ca84a-256">[행 압축 구현](row-compression-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="ca84a-256">[Row Compression Implementation](row-compression-implementation.md) </span></span>  
 <span data-ttu-id="ca84a-257">[페이지 압축 구현](page-compression-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="ca84a-257">[Page Compression Implementation](page-compression-implementation.md) </span></span>  
 <span data-ttu-id="ca84a-258">[유니코드 압축 구현](unicode-compression-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="ca84a-258">[Unicode Compression Implementation](unicode-compression-implementation.md) </span></span>  
 <span data-ttu-id="ca84a-259">[CREATE PARTITION SCHEME&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-scheme-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca84a-259">[CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-scheme-transact-sql) </span></span>  
 <span data-ttu-id="ca84a-260">[CREATE PARTITION FUNCTION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca84a-260">[CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-function-transact-sql) </span></span>  
 <span data-ttu-id="ca84a-261">[CREATE TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca84a-261">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="ca84a-262">[ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca84a-262">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 <span data-ttu-id="ca84a-263">[CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca84a-263">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 [<span data-ttu-id="ca84a-264">ALTER INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ca84a-264">ALTER INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
  
