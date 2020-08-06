---
title: 테이블 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.tableproperties.storage.f1
- sql12.SWB.SELECTCOLUMNS.F1
- sql12.swb.tableproperties.filetable.f1
- sql12.swb.tableproperties.general.f1
- sql12.swb.tableproperties.changetracking.f1
ms.assetid: ad8a2fd4-f092-4c0f-be85-54ce8b9d725a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 037e56649d3473e3fe09b9533bcc96b4729870d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651564"
---
# <a name="table-properties"></a><span data-ttu-id="fc11d-102">테이블 속성</span><span class="sxs-lookup"><span data-stu-id="fc11d-102">Table Properties</span></span>
  <span data-ttu-id="fc11d-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 테이블 속성 편집 대화 상자에 표시된 테이블 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-103">This topic describes the table properties that are displayed in the Table Properties dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="fc11d-104">이러한 속성을 표시하는 방법은 [테이블 정의 보기](view-the-table-definition.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc11d-104">For more information about how to display these properties, see [View the Table Definition](view-the-table-definition.md).</span></span>  
  
 <span data-ttu-id="fc11d-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="fc11d-105">**In This Topic**</span></span>  
  
1.  [<span data-ttu-id="fc11d-106">일반 페이지</span><span class="sxs-lookup"><span data-stu-id="fc11d-106">General Page</span></span>](#GeneralPage)  
  
2.  [<span data-ttu-id="fc11d-107">변경 내용 추적 페이지</span><span class="sxs-lookup"><span data-stu-id="fc11d-107">Change Tracking Page</span></span>](#ChangeTracking)  
  
3.  [<span data-ttu-id="fc11d-108">파일 테이블 페이지</span><span class="sxs-lookup"><span data-stu-id="fc11d-108">File Table Page</span></span>](#FileTable)  
  
4.  [<span data-ttu-id="fc11d-109"> 페이지</span><span class="sxs-lookup"><span data-stu-id="fc11d-109">Storage Page</span></span>](#Storage)  
  
##  <a name="general-page"></a><a name="GeneralPage"></a> <span data-ttu-id="fc11d-110">일반 페이지</span><span class="sxs-lookup"><span data-stu-id="fc11d-110">General Page</span></span>  
 <span data-ttu-id="fc11d-111">**Database**</span><span class="sxs-lookup"><span data-stu-id="fc11d-111">**Database**</span></span>  
 <span data-ttu-id="fc11d-112">이 테이블이 포함된 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-112">The name of the database containing this table.</span></span>  
  
 <span data-ttu-id="fc11d-113">**Server**</span><span class="sxs-lookup"><span data-stu-id="fc11d-113">**Server**</span></span>  
 <span data-ttu-id="fc11d-114">현재 서버 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-114">The name of the current server instance.</span></span>  
  
 <span data-ttu-id="fc11d-115">**사용자**</span><span class="sxs-lookup"><span data-stu-id="fc11d-115">**User**</span></span>  
 <span data-ttu-id="fc11d-116">이 연결을 사용하는 사용자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-116">The name of the user of this connection.</span></span>  
  
 <span data-ttu-id="fc11d-117">**만든 날짜**</span><span class="sxs-lookup"><span data-stu-id="fc11d-117">**Created Date**</span></span>  
 <span data-ttu-id="fc11d-118">테이블을 만든 날짜와 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-118">The date and time that the table was created.</span></span>  
  
 <span data-ttu-id="fc11d-119">**이름**</span><span class="sxs-lookup"><span data-stu-id="fc11d-119">**Name**</span></span>  
 <span data-ttu-id="fc11d-120">테이블의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-120">The name of the table.</span></span>  
  
 <span data-ttu-id="fc11d-121">**스키마**</span><span class="sxs-lookup"><span data-stu-id="fc11d-121">**Schema**</span></span>  
 <span data-ttu-id="fc11d-122">테이블을 소유하고 있는 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-122">The schema that owns the table.</span></span>  
  
 <span data-ttu-id="fc11d-123">**시스템 개체**</span><span class="sxs-lookup"><span data-stu-id="fc11d-123">**System object**</span></span>  
 <span data-ttu-id="fc11d-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 내부 정보를 보관하는 데 사용하는 시스템 테이블을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-124">Indicates this table is a system table, used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to contain internal information.</span></span> <span data-ttu-id="fc11d-125">시스템 테이블은 사용자가 직접 변경하거나 참조해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-125">Users should not directly change or reference system tables.</span></span>  
  
 <span data-ttu-id="fc11d-126">**ANSI NULL**</span><span class="sxs-lookup"><span data-stu-id="fc11d-126">**ANSI NULLs**</span></span>  
 <span data-ttu-id="fc11d-127">ANSI NULL 옵션이 ON으로 설정된 상태에서 개체가 만들어졌는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-127">Indicates if the object was created with the ANSI NULLs option set to ON.</span></span> <span data-ttu-id="fc11d-128">자세한 내용은 [SET ANSI_NULLS&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc11d-128">For more information, see [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql)</span></span>  
  
 <span data-ttu-id="fc11d-129">**따옴표 붙은 식별자**</span><span class="sxs-lookup"><span data-stu-id="fc11d-129">**Quoted identifier**</span></span>  
 <span data-ttu-id="fc11d-130">따옴표 붙은 식별자 옵션이 ON으로 설정된 상태에서 개체가 만들어졌는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-130">Indicates if the object was created with the quoted identifier option set to ON.</span></span> <span data-ttu-id="fc11d-131">자세한 내용은 [SET QUOTED_IDENTIFIER&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc11d-131">For more information, see [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)</span></span>  
  
 <span data-ttu-id="fc11d-132">**잠금 에스컬레이션**</span><span class="sxs-lookup"><span data-stu-id="fc11d-132">**Lock Escalation**</span></span>  
 <span data-ttu-id="fc11d-133">테이블의 잠금 에스컬레이션 세분성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-133">Indicates the lock escalation granularity of the table.</span></span> <span data-ttu-id="fc11d-134">데이터베이스 엔진에서의 잠금에 대한 자세한 내용은 [SQL Server 트랜잭션 잠금 및 행 버전 관리 지침](https://msdn.microsoft.com/library/jj856598.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc11d-134">For more information about locking in the Database Engine, see [SQL Server Transaction Locking and Row Versioning Guide](https://msdn.microsoft.com/library/jj856598.aspx).</span></span> <span data-ttu-id="fc11d-135">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-135">Possible values are:</span></span>  
  
 <span data-ttu-id="fc11d-136">AUTO</span><span class="sxs-lookup"><span data-stu-id="fc11d-136">AUTO</span></span>  
 <span data-ttu-id="fc11d-137">이 옵션을 선택하면 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 에서 테이블 스키마에 적절한 잠금 에스컬레이션 세분성을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-137">This option allows the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] to select the lock escalation granularity that is appropriate for the table schema.</span></span>  
  
-   <span data-ttu-id="fc11d-138">테이블이 분할된 경우에는 잠금이 HOBT(힙 또는 B-트리) 세분성으로 에스컬레이션됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-138">If the table is partitioned, lock escalation will be allowed to the heap or B-tree (HoBT) granularity.</span></span> <span data-ttu-id="fc11d-139">잠금이 HoBT 수준으로 에스컬레이션된 후에는 나중에 잠금이 TABLE 세분성으로 에스컬레이션되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-139">After the lock is escalated to the HoBT level, the lock will not be escalated later to TABLE granularity.</span></span>  
  
-   <span data-ttu-id="fc11d-140">테이블이 분할되지 않은 경우에는 잠금이 TABLE 세분성으로 에스컬레이션됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-140">If the table is not partitioned, the lock escalation will be done to the TABLE granularity.</span></span>  
  
 <span data-ttu-id="fc11d-141">TABLE</span><span class="sxs-lookup"><span data-stu-id="fc11d-141">TABLE</span></span>  
 <span data-ttu-id="fc11d-142">테이블이 분할되었는지 여부에 관계없이 잠금 에스컬레이션이 테이블 수준 세분성에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-142">Lock escalation will be done at table-level granularity regardless of whether the table is partitioned or not partitioned.</span></span> <span data-ttu-id="fc11d-143">기본값은 TABLE입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-143">TABLE is the default value.</span></span>  
  
 <span data-ttu-id="fc11d-144">DISABLE</span><span class="sxs-lookup"><span data-stu-id="fc11d-144">DISABLE</span></span>  
 <span data-ttu-id="fc11d-145">대부분의 경우 잠금 에스컬레이션이 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-145">Prevents lock escalation in most cases.</span></span> <span data-ttu-id="fc11d-146">테이블 수준 잠금은 부분적으로 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-146">Table-level locks are not completely disallowed.</span></span> <span data-ttu-id="fc11d-147">예를 들어 직렬화 가능 격리 수준에서 클러스터형 인덱스가 없는 테이블을 검색하면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 테이블 잠금을 사용하여 데이터 무결성을 보호해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-147">For example, when you are scanning a table that has no clustered index under the serializable isolation level, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] must take a table lock to protect data integrity.</span></span>  
  
 <span data-ttu-id="fc11d-148">**테이블 복제 여부**</span><span class="sxs-lookup"><span data-stu-id="fc11d-148">**Table is replicated**</span></span>  
 <span data-ttu-id="fc11d-149">테이블이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제를 사용하여 다른 데이터베이스에 복제된 경우를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-149">Indicates when the table is replicated to another database using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="fc11d-150">가능한 값은 `True` 또는 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-150">Possible values are `True` or `False`.</span></span>  
  
##  <a name="change-tracking-page"></a><a name="ChangeTracking"></a><span data-ttu-id="fc11d-151">변경 내용 추적 페이지</span><span class="sxs-lookup"><span data-stu-id="fc11d-151">Change Tracking Page</span></span>  
 <span data-ttu-id="fc11d-152">**변경 내용 추적**</span><span class="sxs-lookup"><span data-stu-id="fc11d-152">**Change Tracking**</span></span>  
 <span data-ttu-id="fc11d-153">테이블에 대해 변경 내용 추적이 설정되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-153">Indicates whether change tracking is enabled for the table.</span></span> <span data-ttu-id="fc11d-154">기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-154">The default value is `False`.</span></span>  
  
 <span data-ttu-id="fc11d-155">이 옵션은 데이터베이스에 대해 변경 내용 추적이 설정된 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-155">This option is available only when change tracking is enabled for the database.</span></span>  
  
 <span data-ttu-id="fc11d-156">변경 내용 추적을 설정하려면 테이블에 기본 키가 있어야 하고, 해당 테이블을 수정할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-156">To enable change tracking, the table must have a primary key, and you must have permission to modify the table.</span></span> <span data-ttu-id="fc11d-157">[ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)을 사용하여 변경 내용 추적을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-157">You can configure change tracking by using [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
 <span data-ttu-id="fc11d-158">**추적 열 업데이트됨**</span><span class="sxs-lookup"><span data-stu-id="fc11d-158">**Track Columns Updated**</span></span>  
 <span data-ttu-id="fc11d-159">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 에서 업데이트된 열을 추적하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-159">Indicates whether the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] tracks which columns were updated.</span></span>  
  
 <span data-ttu-id="fc11d-160">변경 내용 추적에 대한 자세한 내용은 [변경 내용 추적 정보&#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc11d-160">For more information about Change Tracking, see [About Change Tracking &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md).</span></span>  
  
##  <a name="filetable-page"></a><a name="FileTable"></a> <span data-ttu-id="fc11d-161">FileTable 페이지</span><span class="sxs-lookup"><span data-stu-id="fc11d-161">FileTable Page</span></span>  
 <span data-ttu-id="fc11d-162">FileTable과 관련된 테이블의 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-162">Displays properties of the table related to FileTables.</span></span> <span data-ttu-id="fc11d-163">자세한 내용은 [FileTables&#40;SQL Server&#41;](../blob/filetables-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc11d-163">For more information, see [FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md).</span></span>  
  
 <span data-ttu-id="fc11d-164">**FileTable 이름 열 데이터 정렬**</span><span class="sxs-lookup"><span data-stu-id="fc11d-164">**FileTable name column collation**</span></span>  
 <span data-ttu-id="fc11d-165">FileTable의 **Name** 열에 적용되는 데이터 정렬입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-165">The collation that is applied to the **Name** column in a FileTable.</span></span> <span data-ttu-id="fc11d-166">**Name** 열에는 파일 및 디렉터리 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-166">The **Name** column contains file and directory names.</span></span>  
  
 <span data-ttu-id="fc11d-167">**FileTable 디렉터리 이름**</span><span class="sxs-lookup"><span data-stu-id="fc11d-167">**FileTable directory name**</span></span>  
 <span data-ttu-id="fc11d-168">FileTable의 루트 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-168">The root folder for the FileTable.</span></span>  
  
 <span data-ttu-id="fc11d-169">**FileTable 네임스페이스 사용**</span><span class="sxs-lookup"><span data-stu-id="fc11d-169">**FileTable namespace enabled**</span></span>  
 <span data-ttu-id="fc11d-170">`True` 값은 해당 테이블이 FileTable임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-170">When `True`, this value indicates that the table is a FileTable.</span></span> <span data-ttu-id="fc11d-171">이 값을 `False`로 변경하면 FileTable이 일반적인 사용자 테이블로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-171">If you change this value to `False`, you are changing the FileTable to an ordinary user table.</span></span> <span data-ttu-id="fc11d-172">나중에 테이블을 다시 FileTable로 변경할 경우 테이블이 FileTable 일관성 검사를 통과해야 변환이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-172">If you later want to change the table back to a FileTable, the table will have to pass a FileTable consistency check before the conversion succeeds.</span></span>  
  
##  <a name="storage-page"></a><a name="Storage"></a><span data-ttu-id="fc11d-173">저장소 페이지</span><span class="sxs-lookup"><span data-stu-id="fc11d-173">Storage Page</span></span>  
 <span data-ttu-id="fc11d-174">선택한 테이블의 스토리지 관련 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-174">Displays the storage related properties of the selected table.</span></span>  
  
### <a name="compression"></a><span data-ttu-id="fc11d-175">압축</span><span class="sxs-lookup"><span data-stu-id="fc11d-175">Compression</span></span>  
 <span data-ttu-id="fc11d-176">**압축 유형**</span><span class="sxs-lookup"><span data-stu-id="fc11d-176">**Compression type**</span></span>  
 <span data-ttu-id="fc11d-177">테이블의 압축 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-177">The compression type of the table.</span></span> <span data-ttu-id="fc11d-178">이 속성은 분할되지 않은 테이블에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-178">This property is only available for tables that are not partitioned.</span></span> <span data-ttu-id="fc11d-179">자세한 내용은 [Data Compression](../data-compression/data-compression.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc11d-179">For more information, see [Data Compression](../data-compression/data-compression.md).</span></span>  
  
 <span data-ttu-id="fc11d-180">**페이지 압축을 사용하는 파티션**</span><span class="sxs-lookup"><span data-stu-id="fc11d-180">**Partitions using page compression**</span></span>  
 <span data-ttu-id="fc11d-181">페이지 압축을 사용하는 파티션 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-181">The partition numbers that are using page compression.</span></span> <span data-ttu-id="fc11d-182">이 속성은 분할된 테이블에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-182">This property is only available for partitioned tables.</span></span>  
  
 <span data-ttu-id="fc11d-183">**압축되지 않은 파티션**</span><span class="sxs-lookup"><span data-stu-id="fc11d-183">**Partitions not compressed**</span></span>  
 <span data-ttu-id="fc11d-184">압축되지 않은 파티션 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-184">The partition numbers that are not compressed.</span></span> <span data-ttu-id="fc11d-185">이 속성은 분할된 테이블에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-185">This property is only available for partitioned tables.</span></span>  
  
 <span data-ttu-id="fc11d-186">**행 압축을 사용하는 파티션**</span><span class="sxs-lookup"><span data-stu-id="fc11d-186">**Partitions using row compression**</span></span>  
 <span data-ttu-id="fc11d-187">행 압축을 사용하는 파티션 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-187">The partition numbers that are using row compression.</span></span> <span data-ttu-id="fc11d-188">이 속성은 분할된 테이블에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-188">This property is only available for partitioned tables.</span></span>  
  
### <a name="filegroup"></a><span data-ttu-id="fc11d-189">파일 그룹</span><span class="sxs-lookup"><span data-stu-id="fc11d-189">Filegroup</span></span>  
 <span data-ttu-id="fc11d-190">**텍스트 파일 그룹**</span><span class="sxs-lookup"><span data-stu-id="fc11d-190">**Text filegroup**</span></span>  
 <span data-ttu-id="fc11d-191">테이블의 텍스트 데이터가 들어 있는 파일 그룹의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-191">The name of the filegroup that contains the text data for the table.</span></span>  
  
 <span data-ttu-id="fc11d-192">**파일 그룹**</span><span class="sxs-lookup"><span data-stu-id="fc11d-192">**Filegroup**</span></span>  
 <span data-ttu-id="fc11d-193">테이블이 있는 파일 그룹의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-193">The name of the filegroup that contains the table.</span></span>  
  
 <span data-ttu-id="fc11d-194">**테이블 분할 여부**</span><span class="sxs-lookup"><span data-stu-id="fc11d-194">**Table is partitioned**</span></span>  
 <span data-ttu-id="fc11d-195">가능한 값은 `True` 및 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-195">Possible values are `True` and `False`.</span></span>  
  
 <span data-ttu-id="fc11d-196">**Filestream 파일 그룹**</span><span class="sxs-lookup"><span data-stu-id="fc11d-196">**Filestream filegroup**</span></span>  
 <span data-ttu-id="fc11d-197">테이블에 FILESTREAM 특성이 있는 `varbinary(max)` 열이 있을 경우 FILESTREAM 데이터 파일 그룹의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-197">Specify the name of the FILESTREAM data filegroup if the table has a `varbinary(max)` column that has the FILESTREAM attribute.</span></span> <span data-ttu-id="fc11d-198">기본값은 기본 FILESTREAM 데이터 파일 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-198">The default value is the default FILESTREAM data filegroup.</span></span>  
  
 <span data-ttu-id="fc11d-199">테이블에 FILESTREAM 데이터가 없는 경우 이 필드가 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-199">If the table does not contain FILESTREAM data, the field is blank.</span></span>  
  
### <a name="general"></a><span data-ttu-id="fc11d-200">일반</span><span class="sxs-lookup"><span data-stu-id="fc11d-200">General</span></span>  
 <span data-ttu-id="fc11d-201">**VarDecimal 스토리지 형식을 사용합니다.**</span><span class="sxs-lookup"><span data-stu-id="fc11d-201">**Vardecimal storage format is enabled**</span></span>  
 <span data-ttu-id="fc11d-202">`True`인 경우이 읽기 전용 값은 `decimal` 및 `numeric` 데이터 형식이 vardecimal 저장소 형식을 사용 하 여 저장 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-202">When `True`, this read-only value indicates that `decimal` and `numeric` data types are stored by using the vardecimal storage format.</span></span> <span data-ttu-id="fc11d-203">이 옵션을 변경 하려면 `vardecimal storage format` [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql)의 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-203">To change this option, use the `vardecimal storage format` option of [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql).</span></span> <span data-ttu-id="fc11d-204">VarDecimal 스토리지 형식은 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-204">Vardecimal storage format is deprecated.</span></span> <span data-ttu-id="fc11d-205">대신 ROW 압축을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="fc11d-205">Use ROW compression instead.</span></span>  
  
 <span data-ttu-id="fc11d-206">**인덱스 공간**</span><span class="sxs-lookup"><span data-stu-id="fc11d-206">**Index space**</span></span>  
 <span data-ttu-id="fc11d-207">테이블의 인덱스가 차지하는 공간의 크기(MB)입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-207">The amount of space in megabytes that the indexes occupy in the table.</span></span> <span data-ttu-id="fc11d-208">이 값에 테이블에 대한 XML 인덱스 공간 사용량은 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-208">This value does not include XML index space usage for the table.</span></span> <span data-ttu-id="fc11d-209">XML 인덱스가 해당 테이블에 속할 경우 [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) 를 대신 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="fc11d-209">If XML indexes belong to the table, use [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) instead.</span></span>  
  
 <span data-ttu-id="fc11d-210">**행 개수**</span><span class="sxs-lookup"><span data-stu-id="fc11d-210">**Row count**</span></span>  
 <span data-ttu-id="fc11d-211">표의 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-211">The number of rows in the table.</span></span>  
  
 <span data-ttu-id="fc11d-212">**데이터 공간**</span><span class="sxs-lookup"><span data-stu-id="fc11d-212">**Data space**</span></span>  
 <span data-ttu-id="fc11d-213">테이블의 데이터가 차지하는 공간의 크기(MB)입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-213">The amount of space in megabytes that the data occupies in the table.</span></span>  
  
### <a name="partitioning"></a><span data-ttu-id="fc11d-214">분할</span><span class="sxs-lookup"><span data-stu-id="fc11d-214">Partitioning</span></span>  
 <span data-ttu-id="fc11d-215">이 섹션은 테이블이 분할된 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-215">This section is only available if the table is partitioned.</span></span> <span data-ttu-id="fc11d-216">자세한 내용은 [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc11d-216">For more information, see [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).</span></span>  
  
 <span data-ttu-id="fc11d-217">**파티션 열**</span><span class="sxs-lookup"><span data-stu-id="fc11d-217">**Partition column**</span></span>  
 <span data-ttu-id="fc11d-218">테이블이 분할된 열의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-218">The name of the column on which the table is partitioned.</span></span>  
  
 <span data-ttu-id="fc11d-219">**파티션 구성표**</span><span class="sxs-lookup"><span data-stu-id="fc11d-219">**Partition scheme**</span></span>  
 <span data-ttu-id="fc11d-220">테이블이 분할된 경우에 표시되는 파티션 구성표의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-220">Name of the partition scheme if the table is partitioned.</span></span> <span data-ttu-id="fc11d-221">테이블이 분할되지 않은 경우 이 필드가 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-221">If the table is not partitioned, the field is blank.</span></span>  
  
 <span data-ttu-id="fc11d-222">**파티션 수**</span><span class="sxs-lookup"><span data-stu-id="fc11d-222">**Number of partitions**</span></span>  
 <span data-ttu-id="fc11d-223">테이블에 있는 파티션의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-223">The number of partitions in the table.</span></span>  
  
 <span data-ttu-id="fc11d-224">**FILESTREAM 파티션 구성표**</span><span class="sxs-lookup"><span data-stu-id="fc11d-224">**FILESTREAM partition scheme**</span></span>  
 <span data-ttu-id="fc11d-225">테이블이 분할된 경우에 표시되는 FILESTREAM 파티션 구성표의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-225">The name of the FILESTREAM partition scheme if the table is partitioned.</span></span> <span data-ttu-id="fc11d-226">테이블이 분할되지 않은 경우 이 필드가 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-226">If the table is not partitioned, the field is blank.</span></span>  
  
 <span data-ttu-id="fc11d-227">FILESTREAM 파티션 구성표는 **파티션 구성표** 옵션에서 지정한 구성표와 대칭이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc11d-227">The FILESTREAM partition scheme must be symmetric to the scheme that is specified in the **Partition scheme** option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc11d-228">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc11d-228">See Also</span></span>  
 <span data-ttu-id="fc11d-229">[테이블 정의 보기](view-the-table-definition.md) </span><span class="sxs-lookup"><span data-stu-id="fc11d-229">[View the Table Definition](view-the-table-definition.md) </span></span>  
 [<span data-ttu-id="fc11d-230">열 수정&#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="fc11d-230">Modify Columns &#40;Database Engine&#41;</span></span>](../tables/modify-columns-database-engine.md)  
  
  
