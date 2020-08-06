---
title: MSSQLSERVER_605 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 605 (Database Engine error)
ms.assetid: d8d3a22e-1ff8-48a4-891f-4c8619437e24
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e196fba84af492b25e798629d3e808b1bf22857e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653879"
---
# <a name="mssqlserver_605"></a><span data-ttu-id="8ecf2-102">MSSQLSERVER_605</span><span class="sxs-lookup"><span data-stu-id="8ecf2-102">MSSQLSERVER_605</span></span>
    
## <a name="details"></a><span data-ttu-id="8ecf2-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="8ecf2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8ecf2-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="8ecf2-104">Product Name</span></span>|<span data-ttu-id="8ecf2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8ecf2-105">SQL Server</span></span>|  
|<span data-ttu-id="8ecf2-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="8ecf2-106">Event ID</span></span>|<span data-ttu-id="8ecf2-107">605</span><span class="sxs-lookup"><span data-stu-id="8ecf2-107">605</span></span>|  
|<span data-ttu-id="8ecf2-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="8ecf2-108">Event Source</span></span>|<span data-ttu-id="8ecf2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8ecf2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8ecf2-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="8ecf2-110">Component</span></span>|<span data-ttu-id="8ecf2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8ecf2-111">SQLEngine</span></span>|  
|<span data-ttu-id="8ecf2-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="8ecf2-112">Symbolic Name</span></span>|<span data-ttu-id="8ecf2-113">WRONGPAGE</span><span class="sxs-lookup"><span data-stu-id="8ecf2-113">WRONGPAGE</span></span>|  
|<span data-ttu-id="8ecf2-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="8ecf2-114">Message Text</span></span>|<span data-ttu-id="8ecf2-115">데이터베이스 %d에서 논리 페이지 %S_PGID을(를) 인출하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-115">Attempt to fetch logical page %S_PGID in database %d failed.</span></span> <span data-ttu-id="8ecf2-116">이 페이지는 할당 단위 %I64d이(가) 아닌 %I64d에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-116">It belongs to allocation unit %I64d not to %I64d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8ecf2-117">설명</span><span class="sxs-lookup"><span data-stu-id="8ecf2-117">Explanation</span></span>  
 <span data-ttu-id="8ecf2-118">이 오류는 일반적으로 지정한 데이터베이스의 페이지 또는 할당이 손상되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-118">This error generally signifies page or allocation corruption in the specified database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="8ecf2-119">는 페이지 링크를 따라가거나 IAM(Index Allocation Map)을 사용하여 테이블에 속하는 페이지를 읽을 때 손상을 감지합니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-119">detects corruption when reading pages belonging to a table either by following the page linkages or by using the Index Allocation Map (IAM).</span></span> <span data-ttu-id="8ecf2-120">테이블에 할당된 모든 페이지는 해당 테이블과 연결된 할당 단위 중 하나에 속해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-120">All pages allocated to a table must belong to one of the allocation units associated with the table.</span></span> <span data-ttu-id="8ecf2-121">페이지 머리글에 포함된 할당 단위 ID가 테이블에 연결된 할당 단위 ID와 일치하지 않으면 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-121">If the allocation unit ID contained in the page header does not match an allocation unit ID associated with the table, this exception is raised.</span></span> <span data-ttu-id="8ecf2-122">오류 메시지에 나열된 첫 번째 할당 단위 ID는 페이지 머리글에 있는 ID이고 두 번째 할당 단위 값은 테이블과 연결된 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-122">The first allocation unit ID listed in the error message is the ID present in the page header, and the second allocation unit value is the ID associated with the table.</span></span>  
  
 <span data-ttu-id="8ecf2-123">**데이터 손상 오류**</span><span class="sxs-lookup"><span data-stu-id="8ecf2-123">**Data Corruption Errors**</span></span>  
  
 <span data-ttu-id="8ecf2-124">심각도 수준 21은 잠재적 데이터 손상을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-124">A severity level of 21 indicates potential data corruption.</span></span> <span data-ttu-id="8ecf2-125">가능한 원인은 손상된 페이지 체인, 손상된 IAM 또는 해당 개체에 대한 [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) 카탈로그 뷰의 잘못된 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-125">Possible causes are a damaged page chain, a corrupt IAM, or an invalid entry in the [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) catalog view for that object.</span></span> <span data-ttu-id="8ecf2-126">이러한 오류는 하드웨어 또는 디스크 디바이스 드라이버 오류로 인해 발생하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-126">These errors are often caused by hardware or disk device driver failure.</span></span>  
  
 <span data-ttu-id="8ecf2-127">**일시적 오류**</span><span class="sxs-lookup"><span data-stu-id="8ecf2-127">**Transient Errors**</span></span>  
  
 <span data-ttu-id="8ecf2-128">심각도 수준 12는 잠재적인 일시적 오류를 나타냅니다. 이 오류는 캐시에서 발생하며 디스크에 있는 데이터 손상을 나타내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-128">A severity level of 12 indicates a potential transient error; that is, it occurs in the cache and does not indicate damage to data on disk.</span></span> <span data-ttu-id="8ecf2-129">일시적 605 오류는 다음과 같은 조건에서 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-129">Transient 605 errors can be caused by the following conditions:</span></span>  
  
-   <span data-ttu-id="8ecf2-130">운영 체제에서 I/O 작업이 완료되었다고 너무 빨리 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 알리는 경우. 실제 데이터 손상이 없는 경우에도 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-130">The operating system prematurely notifies [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that an I/O operation has completed; the error message is displayed even though no actual data corruption exists.</span></span>  
  
 <span data-ttu-id="8ecf2-131">최적화 프로그램 힌트 NOLOCK을 사용하여 쿼리를 실행하거나 트랜잭션 격리 수준을 READ UNCOMMITTED로 설정하는 경우.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-131">Running a query with the Optimizer hint NOLOCK or setting the transaction isolation level to READ UNCOMMITTED.</span></span> <span data-ttu-id="8ecf2-132">NOLOCK 또는 READ UNCOMMITTED를 사용하는 쿼리에서 다른 사용자가 이동하거나 변경 중인 데이터를 읽으려고 하면 605 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-132">When a query that is using NOLOCK or READ UNCOMMITTED tries to read data that is being moved or changed by another user, a 605 error occurs.</span></span> <span data-ttu-id="8ecf2-133">일시적 605 오류인지 확인하려면 나중에 쿼리를 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-133">To verify that it is a transient 605 error, rerun the query later.</span></span> <span data-ttu-id="8ecf2-134">자세한 내용은 이 KB 문서 [235880](https://support.microsoft.com/kb/235880/en-us): "SQL Server에서 최적화 프로그램 힌트 NOLOCK를 사용하여 쿼리를 실행하거나 트랜잭션 격리 수준을 READ UNCOMMITTED로 설정하면 "오류 605" 오류 메시지가 나타난다"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-134">For more information, see this KB article [235880](https://support.microsoft.com/kb/235880/en-us): "You receive an "Error 605" error message when you run a query with the optimizer hint NOLOCK or you set the transaction isolation level to READ UNCOMMITTED in SQL Server."</span></span>  
  
 <span data-ttu-id="8ecf2-135">일반적으로 데이터에 액세스하는 동안 오류가 발생했는데 후속 DBCC CHECKDB 작업이 오류 없이 완료되면 일시적 605 오류일 가능성이 큽니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-135">In general, if the error occurs during data access but subsequent DBCC CHECKDB operations complete without error, the 605 error was probably transient.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8ecf2-136">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="8ecf2-136">User Action</span></span>  
 <span data-ttu-id="8ecf2-137">605 오류가 일시적 오류가 아니면 문제가 심각하며 다음 태스크를 수행하여 문제를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-137">If the 605 error is not transient, the problem is severe and must be corrected by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="8ecf2-138">다음 쿼리를 실행하여 메시지에 지정된 할당 단위와 연결된 테이블을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-138">Identify the tables associated with the allocation units specified in the message by running the following query.</span></span> <span data-ttu-id="8ecf2-139">`allocation_unit_id`를 오류 메시지에 지정된 할당 단위로 바꾸십시오.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-139">Replace `allocation_unit_id` with the allocation units specified in the error message.</span></span>  
  
     <span data-ttu-id="8ecf2-140">USE`database_name`;</span><span class="sxs-lookup"><span data-stu-id="8ecf2-140">USE`database_name`;</span></span>  
  
     <span data-ttu-id="8ecf2-141">이동</span><span class="sxs-lookup"><span data-stu-id="8ecf2-141">GO</span></span>  
  
     <span data-ttu-id="8ecf2-142">SELECT au.allocation_unit_id, OBJECT_NAME(p.object_id) AS table_name, fg.name AS filegroup_name,</span><span class="sxs-lookup"><span data-stu-id="8ecf2-142">SELECT au.allocation_unit_id, OBJECT_NAME(p.object_id) AS table_name, fg.name AS filegroup_name,</span></span>  
  
     <span data-ttu-id="8ecf2-143">au.type_desc AS allocation_type, au.data_pages, partition_number</span><span class="sxs-lookup"><span data-stu-id="8ecf2-143">au.type_desc AS allocation_type, au.data_pages, partition_number</span></span>  
  
     <span data-ttu-id="8ecf2-144">FROM sys.allocation_units AS au</span><span class="sxs-lookup"><span data-stu-id="8ecf2-144">FROM sys.allocation_units AS au</span></span>  
  
     <span data-ttu-id="8ecf2-145">JOIN sys.partitions AS p ON au.container_id = p.partition_id</span><span class="sxs-lookup"><span data-stu-id="8ecf2-145">JOIN sys.partitions AS p ON au.container_id = p.partition_id</span></span>  
  
     <span data-ttu-id="8ecf2-146">JOIN sys.filegroups AS fg ON fg.data_space_id = au.data_space_id</span><span class="sxs-lookup"><span data-stu-id="8ecf2-146">JOIN sys.filegroups AS fg ON fg.data_space_id = au.data_space_id</span></span>  
  
     <span data-ttu-id="8ecf2-147">WHERE au.allocation_unit_id = `allocation_unit_id` OR au.allocation_unit_id = `allocation_unit_id`</span><span class="sxs-lookup"><span data-stu-id="8ecf2-147">WHERE au.allocation_unit_id = `allocation_unit_id` OR au.allocation_unit_id = `allocation_unit_id`</span></span>  
  
     <span data-ttu-id="8ecf2-148">ORDER BY au.allocation_unit_id;</span><span class="sxs-lookup"><span data-stu-id="8ecf2-148">ORDER BY au.allocation_unit_id;</span></span>  
  
     <span data-ttu-id="8ecf2-149">이동</span><span class="sxs-lookup"><span data-stu-id="8ecf2-149">GO</span></span>  
  
2.  <span data-ttu-id="8ecf2-150">오류 메시지에 지정된 두 번째 할당 단위 ID와 연결된 테이블에 대해 REPAIR 절 없이 DBCC CHECKTABLE을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-150">Execute DBCC CHECKTABLE without a REPAIR clause on the table associated with the second allocation unit ID specified in the error message.</span></span>  
  
3.  <span data-ttu-id="8ecf2-151">가능한 한 즉시 REPAIR 절 없이 DBCC CHECKDB를 실행하여 전체 데이터베이스의 전체 손상 범위를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-151">Execute DBCC CHECKDB without a REPAIR clause as soon as possible to determine the full extent of the corruption in the entire database.</span></span>  
  
4.  <span data-ttu-id="8ecf2-152">오류 로그에서 자주 605 오류와 함께 나타나는 다른 오류를 확인하고 Windows 이벤트 로그에서 시스템 또는 하드웨어 관련 문제를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-152">Check the error log for other errors that often accompany a 605 error and examine the Windows Event Log for any system or hardware related issues.</span></span> <span data-ttu-id="8ecf2-153">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-153">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="8ecf2-154">하드웨어 관련 문제가 아니면 다음 태스크 중 하나를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-154">If the problem is not hardware related, perform one of the following tasks:</span></span>  
  
1.  <span data-ttu-id="8ecf2-155">정상적인 백업을 사용하여 데이터베이스를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-155">Restore the database from a known clean backup.</span></span> <span data-ttu-id="8ecf2-156">페이지 복원 백업 기능을 사용하여 손상된 페이지만 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-156">You can leverage the page restore backup feature to restore just the damaged pages.</span></span>  
  
2.  <span data-ttu-id="8ecf2-157">3단계에서 수행한 DBCC CHECKDB 작업에서 권장하는 REPAIR 절을 사용하여 DBCC CHECKDB를 실행하고 손상을 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-157">Run DBCC CHECKDB with the REPAIR clause recommended by the DBCC CHECKDB operation performed in step 3 to repair the corruption.</span></span> <span data-ttu-id="8ecf2-158">REPAIR 절 중 하나를 사용하여 DBCC CHECKDB를 실행해도 문제가 해결되지 않으면 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-158">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span> <span data-ttu-id="8ecf2-159">DBCC CHECKDB의 출력을 검토할 수 있도록 제공하십시오.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-159">Have the output from DBCC CHECKDB available for review.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="8ecf2-160">REPAIR 절을 사용할 경우 DBCC CHECKDB가 데이터에 미치는 영향을 확인하려면 이 문을 실행하기 전에 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="8ecf2-160">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ecf2-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ecf2-161">See Also</span></span>  
 [<span data-ttu-id="8ecf2-162">DBCC CHECKTABLE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8ecf2-162">DBCC CHECKTABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql)  
  
  
