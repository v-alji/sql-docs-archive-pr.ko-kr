---
title: 테이블과 저장 프로시저의 네이티브 컴파일 | Microsoft 문서
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 5880fbd9-a23e-464a-8b44-09750eeb2dad
author: rothja
ms.author: jroth
ms.openlocfilehash: 32c5b04610d894e06278fbeecdaf3bbebe850d60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652116"
---
# <a name="native-compilation-of-tables-and-stored-procedures"></a><span data-ttu-id="60077-102">테이블과 저장 프로시저의 네이티브 컴파일</span><span class="sxs-lookup"><span data-stu-id="60077-102">Native Compilation of Tables and Stored Procedures</span></span>
  <span data-ttu-id="60077-103">메모리 내 OLTP에서는 네이티브 컴파일이라는 개념이 도입됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-103">In-Memory OLTP introduces the concept of native compilation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="60077-104">는 메모리 최적화 테이블에 액세스하는 저장 프로시저를 고유하게 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60077-104">can natively compile stored procedures that access memory-optimized tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="60077-105">는 기본적으로 메모리 최적화 테이블을 컴파일할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60077-105">is also able to natively compile memory-optimized tables.</span></span> <span data-ttu-id="60077-106">네이티브 컴파일을 사용하면 기존의 해석된 [!INCLUDE[tsql](../../includes/tsql-md.md)]보다 빠르게 데이터에 액세스할 수 있으며 더 효율적으로 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60077-106">Native compilation allows faster data access and more efficient query execution than interpreted (traditional) [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="60077-107">테이블과 저장 프로시저의 네이티브 컴파일은 DLL을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="60077-107">Native compilation of tables and stored procedures produce DLLs.</span></span>  
  
 <span data-ttu-id="60077-108">메모리 액세스에 최적화된 테이블 형식의 네이티브 컴파일도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-108">Native compilation of memory optimized table types is also supported.</span></span> <span data-ttu-id="60077-109">자세한 내용은 [Memory-Optimized Table Variables](../../database-engine/memory-optimized-table-variables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60077-109">For more information, see [Memory-Optimized Table Variables](../../database-engine/memory-optimized-table-variables.md).</span></span>  
  
 <span data-ttu-id="60077-110">네이티브 컴파일은 추가로 컴파일하거나 해석할 필요 없이 프로세서 명령으로 구성된 네이티브 코드로 프로그래밍 구문을 변환하는 프로세스를 말합니다.</span><span class="sxs-lookup"><span data-stu-id="60077-110">Native compilation refers to the process of converting programming constructs to native code, consisting of processor instructions without the need for further compilation or interpretation.</span></span>  
  
 <span data-ttu-id="60077-111">메모리 내 OLTP에서는 메모리 최적화 테이블이 생성되고 고유하게 컴파일된 저장 프로시저가 로드될 때 네이티브 DLL로 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-111">In-Memory OLTP compiles memory-optimized tables when they are created, and natively compiled stored procedures when they are loaded to native DLLs.</span></span> <span data-ttu-id="60077-112">또한 데이터베이스나 서버를 다시 시작한 후에도 DLL이 다시 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-112">In addition, the DLLs are recompiled after a database or server restart.</span></span> <span data-ttu-id="60077-113">DLL을 다시 만드는 데 필요한 정보는 데이터베이스 메타데이터에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-113">The information necessary to recreate the DLLs is stored in the database metadata.</span></span> <span data-ttu-id="60077-114">DLL은 데이터베이스와 연결되어 있지만 데이터베이스의 일부는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="60077-114">The DLLs are not part of the database, though they are associated with the database.</span></span> <span data-ttu-id="60077-115">예를 들어, DLL은 데이터베이스 백업에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="60077-115">For example, the DLLs are not included in database backups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60077-116">메모리 액세스에 최적화된 테이블은 서버 재시작 중 다시 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-116">Memory-optimized tables are recompiled during a server restart.</span></span> <span data-ttu-id="60077-117">데이터베이스 복구 속도를 높이기 위해 고유하게 컴파일된 저장 프로시저는 서버 재시작 중 다시 컴파일되지 않고 첫 번째 실행 시에 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-117">To speed up database recovery, natively compiled stored procedures are not recompiled during a server restart, they are compiled at the time of first execution.</span></span> <span data-ttu-id="60077-118">이렇게 지연되는 컴파일의 결과로, 고유하게 컴파일된 저장 프로시저는 첫 번째 실행 후 [sys.dm_os_loaded_modules&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-loaded-modules-transact-sql)를 호출할 때만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="60077-118">As a result of this deferred compilation, natively compiled stored procedures only appear when calling [sys.dm_os_loaded_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-loaded-modules-transact-sql) after first execution.</span></span>  
  
## <a name="maintenance-of-in-memory-oltp-dlls"></a><span data-ttu-id="60077-119">메모리 내 OLTP DLL의 유지 관리</span><span class="sxs-lookup"><span data-stu-id="60077-119">Maintenance of In-Memory OLTP DLLs</span></span>  
 <span data-ttu-id="60077-120">다음 쿼리에서는 서버의 메모리에 현재 로드된 모든 테이블 및 저장 프로시저 DLL을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="60077-120">The following query shows all table and stored procedure DLLs currently loaded in memory on the server:</span></span>  
  
```sql  
SELECT name, description FROM sys.dm_os_loaded_modules  
where description = 'XTP Native DLL'  
```  
  
 <span data-ttu-id="60077-121">데이터베이스 관리자는 네이티브 컴파일에서 생성된 파일을 유지 관리할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="60077-121">Database administrators do not need to maintain files that are generated by a native compilation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="60077-122">에서는 생성된 파일 중에서 더 이상 필요 없는 파일을 자동으로 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="60077-122">automatically removes generated files that are no longer needed.</span></span> <span data-ttu-id="60077-123">예를 들어, 테이블과 저장 프로시저가 삭제되거나 데이터베이스가 삭제되면 생성된 파일이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-123">For example, generated files will be deleted when a table and stored procedure is deleted, or if a database is dropped.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60077-124">컴파일이 실패하거나 중단된 경우 생성된 일부 파일이 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="60077-124">If compilation fails or is interrupted, some generated files are not removed.</span></span> <span data-ttu-id="60077-125">이러한 파일은 지원 가능성을 위해 의도적으로 남겨지며 데이터베이스를 삭제하면 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-125">These files are intentionally left behind for supportability and are removed when the database is dropped.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60077-126">데이터베이스를 시작하는 중에 SQL Server가 데이터베이스 복구에 필요한 모든 테이블에 대한 DLL을 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="60077-126">During database startup, SQL Server compiles DLLs for all tables needed for database recovery.</span></span> <span data-ttu-id="60077-127">데이터베이스를 다시 시작하기 직전에 테이블이 삭제된 경우, 파일의 체크포인트나 트랜잭션 로그에 테이블의 잔해가 남아있을 수 있으므로 데이터베이스를 시작하는 중에 테이블에 대한 DLL이 다시 컴파일될 가능성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60077-127">If a table was dropped just prior to a database restart there can still be remnants of the table in the checkpoint files or the transaction log so the DLL for the table might be recompiled during database startup.</span></span> <span data-ttu-id="60077-128">다시 시작한 후에 일반 정리 프로세스에 의해 DLL이 언로드되고 파일이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-128">After restart the DLL will be unloaded and the files will be removed by the normal cleanup process.</span></span>  
  
## <a name="native-compilation-of-tables"></a><span data-ttu-id="60077-129">테이블의 네이티브 컴파일</span><span class="sxs-lookup"><span data-stu-id="60077-129">Native Compilation of Tables</span></span>  
 <span data-ttu-id="60077-130">ph x="1" /&gt; 문을 사용하여 메모리 최적화 테이블을 만들면 데이터베이스 메타데이터에 테이블 정보가 기록되고 메모리에 테이블 및 인덱스 구조가 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-130">Creating a memory-optimized table using the `CREATE TABLE` statement results in the table information being written to the database metadata and the table and index structures created in memory.</span></span> <span data-ttu-id="60077-131">또한 테이블이 DLL로 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-131">The table will also be compiled to a DLL.</span></span>  
  
 <span data-ttu-id="60077-132">다음 예제 스크립트에서는 데이터베이스와 메모리 최적화 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="60077-132">Consider the following sample script, which creates a database and a memory-optimized table:</span></span>  
  
```sql  
use master  
go  
create database db1  
go  
alter database db1 add filegroup db1_mod contains memory_optimized_data  
go  
-- adapt filename as needed  
alter database db1 add file (name='db1_mod', filename='c:\data\db1_mod') to filegroup db1_mod  
go  
use db1  
go  
create table dbo.t1  
   (c1 int not null primary key nonclustered,  
    c2 INT)  
with (memory_optimized=on)  
go  
-- retrieve the path of the DLL for table t1  
select name, description FROM sys.dm_os_loaded_modules  
where name like '%xtp_t_' + cast(db_id() as varchar(10)) + '_' + cast(object_id('dbo.t1') as varchar(10)) + '.dll'  
go  
```  
  
 <span data-ttu-id="60077-133">테이블을 만들면 테이블 DLL이 만들어지고 DLL이 메모리에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-133">Creating the table also creates the table DLL and loads the DLL in memory.</span></span> <span data-ttu-id="60077-134">CREATE TABLE 문 바로 뒤의 DMV 쿼리가 테이블 DLL의 경로를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="60077-134">The DMV query immediately after the CREATE TABLE statement retrieves the path of the table DLL.</span></span>  
  
 <span data-ttu-id="60077-135">테이블 DLL은 테이블의 인덱스 구조와 행 형식을 이해합니다.</span><span class="sxs-lookup"><span data-stu-id="60077-135">The table DLL understands the index structures and row format of the table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="60077-136">에서는 인덱스 순회, 행 검색뿐 아니라 행 내용 저장에도 DLL을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="60077-136">uses the DLL for traversing indexes, retrieving rows, as well as storing the contents of the rows.</span></span>  
  
## <a name="native-compilation-of-stored-procedures"></a><span data-ttu-id="60077-137">저장 프로시저의 네이티브 컴파일</span><span class="sxs-lookup"><span data-stu-id="60077-137">Native Compilation of Stored Procedures</span></span>  
 <span data-ttu-id="60077-138">NATIVE_COMPILATION으로 표시된 저장 프로시저는 고유하게 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-138">Stored procedures that are marked with NATIVE_COMPILATION are natively compiled.</span></span> <span data-ttu-id="60077-139">성능에 중요한 영향을 미치는 비즈니스 논리를 효율적으로 실행하기 위해 프로시저의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 모두 네이티브 코드로 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-139">This means the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the procedure are all compiled to native code for efficient execution of performance-critical business logic.</span></span>  
  
 <span data-ttu-id="60077-140">고유하게 컴파일된 저장 프로시저에 대한 자세한 내용은 [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60077-140">For more information about natively compiled stored procedures, see [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md).</span></span>  
  
 <span data-ttu-id="60077-141">다음 예제 저장 프로시저에서는 이전 예제의 테이블 t1에 행을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="60077-141">Consider the following sample stored procedure, which inserts rows in the table t1 from the previous example:</span></span>  
  
```sql  
create procedure dbo.native_sp  
with native_compilation, schemabinding, execute as owner  
as  
begin atomic  
with (transaction isolation level=snapshot, language=N'us_english')  
  
  declare @i int = 1000000  
  while @i > 0  
  begin  
    insert dbo.t1 values (@i, @i+1)  
    set @i -= 1  
  end  
  
end  
go  
exec dbo.native_sp  
go  
-- reset  
delete from dbo.t1  
go  
```  
  
 <span data-ttu-id="60077-142">native_sp에 대한 DLL은 t1에 대한 DLL 및 메모리 내 OLTP 스토리지 엔진과 직접 상호 작용하여 행을 최대한 빠르게 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60077-142">The DLL for native_sp can interact directly with the DLL for t1, as well as the In-Memory OLTP storage engine, to insert the rows as fast as possible.</span></span>  
  
 <span data-ttu-id="60077-143">메모리 내 OLTP 컴파일러는 쿼리 최적화 프로그램을 이용하여 저장 프로시저의 각 쿼리에 대한 효율적인 실행 계획을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="60077-143">The In-Memory OLTP compiler leverages the query optimizer to create an efficient execution plan for each of the queries in the stored procedure.</span></span> <span data-ttu-id="60077-144">테이블의 데이터가 변경되면 고유하게 컴파일된 저장 프로시저는 자동으로 다시 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-144">Note that natively compiled stored procedures are not automatically recompiled if the data in the table changes.</span></span> <span data-ttu-id="60077-145">메모리 내 OLTP를 사용한 통계 및 저장 프로시저 유지 관리에 대한 자세한 내용은 [메모리 액세스에 최적화된 테이블에 대한 통계](memory-optimized-tables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60077-145">For more information on maintaining statistics and stored procedures with In-Memory OLTP see [Statistics for Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
## <a name="security-considerations-for-native-compilation"></a><span data-ttu-id="60077-146">네이티브 컴파일에 대한 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="60077-146">Security Considerations for Native Compilation</span></span>  
 <span data-ttu-id="60077-147">테이블 및 저장 프로시저의 네이티브 컴파일에서는 메모리 내 OLTP 컴파일러를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="60077-147">Native compilation of tables and stored procedures uses the In-Memory OLTP compiler.</span></span> <span data-ttu-id="60077-148">이 컴파일러는 디스크에 기록되고 메모리에 로드되는 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="60077-148">This compiler produces files that are written to disk and loaded into memory.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="60077-149">는 다음과 같은 메커니즘을 사용하여 이러한 파일에 대한 액세스를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="60077-149">uses the following mechanisms to limit access to these files.</span></span>  
  
### <a name="native-compiler"></a><span data-ttu-id="60077-150">기본 컴파일러</span><span class="sxs-lookup"><span data-stu-id="60077-150">Native Compiler</span></span>  
 <span data-ttu-id="60077-151">컴파일러 실행 파일과 네이티브 컴파일에 필요한 이진 파일 및 헤더 파일은 MSSQL\Binn\Xtp 폴더 아래에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 일부로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-151">The compiler executable, as well as binaries and header files required for native compilation are installed as part of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance under the folder MSSQL\Binn\Xtp.</span></span> <span data-ttu-id="60077-152">따라서 기본 인스턴스가 c:\program files 아래에 설치 되는 경우 컴파일러 파일은 c:\program files \MSSQL12.에 설치 됩니다. \\ [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] MSSQLSERVER\MSSQL\Binn\Xtp.</span><span class="sxs-lookup"><span data-stu-id="60077-152">So, if the default instance is installed under C:\Program Files, the compiler files are installed in C:\Program Files\\[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\Binn\Xtp.</span></span>  
  
 <span data-ttu-id="60077-153">컴파일러에 대한 액세스를 제한하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 ACL(액세스 제어 목록)을 사용하여 이진 파일에 대한 액세스를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="60077-153">To limit access to the compiler, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses access control lists (ACLs) to restrict access to binary files.</span></span> <span data-ttu-id="60077-154">모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이진 파일은 ACL을 통해 수정이나 변조로부터 보호됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-154">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] binaries are protected against modification or tampering through ACLs.</span></span> <span data-ttu-id="60077-155">기본 컴파일러의 ACL은 컴파일러의 사용도 제한합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정 및 시스템 관리자에게만 기본 컴파일러 파일에 대한 읽기 및 실행 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60077-155">The native compiler's ACLs also limit use of the compiler; only the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and system administrators have read and execute permissions for native compiler files.</span></span>  
  
### <a name="files-generated-by-a-native-compilation"></a><span data-ttu-id="60077-156">네이티브 컴파일에서 생성된 파일</span><span class="sxs-lookup"><span data-stu-id="60077-156">Files Generated by a Native Compilation</span></span>  
 <span data-ttu-id="60077-157">테이블이나 저장 프로시저가 컴파일될 때 생성되는 파일에는 DDL과 .c, .obj, .xml 및 .pdb 확장명을 사용하는 파일을 비롯한 중간 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60077-157">The files produced when a table or stored procedure is compiled include the DLL and intermediate files including files with the following extensions: .c, .obj, .xml, and .pdb.</span></span> <span data-ttu-id="60077-158">생성된 파일은 기본 데이터 폴더의 하위 폴더에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-158">The generated files are saved in a subfolder of the default data folder.</span></span> <span data-ttu-id="60077-159">하위 폴더를 Xtp라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="60077-159">The subfolder is called Xtp.</span></span> <span data-ttu-id="60077-160">기본 데이터 폴더를 사용 하 여 기본 인스턴스를 설치 하는 경우 생성 된 파일은 C:\Program files \\ [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12.에 배치 됩니다. MSSQLSERVER\MSSQL\DATA\Xtp.</span><span class="sxs-lookup"><span data-stu-id="60077-160">When installing the default instance with the default data folder, the generated files are placed in C:\Program Files\\[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\DATA\Xtp.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="60077-161">는 생성된 DDL의 변조를 다음 세 가지 방법으로 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="60077-161">prevents tampering with the generated DLLs in three ways:</span></span>  
  
-   <span data-ttu-id="60077-162">테이블이나 저장 프로시저가 DLL로 컴파일될 때 이 DLL은 즉시 메모리에 로드되고 sqlserver.exe 프로세스에 링크됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-162">When a table or stored procedure is compiled to a DLL, this DLL is immediately loaded into memory and linked to the sqlserver.exe process.</span></span> <span data-ttu-id="60077-163">DLL은 프로세스에 링크되어 있는 동안 수정될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="60077-163">A DLL cannot be modified while it is linked to a process.</span></span>  
  
-   <span data-ttu-id="60077-164">데이터베이스가 다시 시작될 때 모든 테이블 및 저장 프로시저는 데이터베이스 메타데이터에 따라 다시 컴파일됩니다(제거되고 다시 만들어짐).</span><span class="sxs-lookup"><span data-stu-id="60077-164">When a database is restarted, all tables and stored procedures are recompiled (removed and recreated) based on the database metadata.</span></span> <span data-ttu-id="60077-165">이에 따라 악성 에이전트가 생성된 파일에서 변경한 모든 내용이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="60077-165">This will remove any changes made to a generated file by a malicious agent.</span></span>  
  
-   <span data-ttu-id="60077-166">생성된 파일은 사용자 데이터의 일부로 간주되며 ACL을 통해 데이터베이스 파일과 동일한 보안 제한이 적용됩니다. 즉, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정 및 시스템 관리자만 생성된 파일에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60077-166">The generated files are considered part of user data, and have the same security restrictions, via ACLs, as database files: only the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and system administrators can access these files.</span></span>  
  
 <span data-ttu-id="60077-167">생성된 파일을 관리하는 데는 사용자 개입이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="60077-167">No user interaction is needed to manage these files.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="60077-168">는 필요에 따라 이러한 파일을 만들고 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="60077-168">will create and remove the files as necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60077-169">참고 항목</span><span class="sxs-lookup"><span data-stu-id="60077-169">See Also</span></span>  
 <span data-ttu-id="60077-170">[메모리 액세스에 최적화 된 테이블](memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="60077-170">[Memory-Optimized Tables](memory-optimized-tables.md) </span></span>  
 [<span data-ttu-id="60077-171">고유하게 컴파일된 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="60077-171">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
