---
title: FileTable 관리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], security
- FileTables [SQL Server], managing access
ms.assetid: 93af982c-b4fe-4be0-8268-11f86dae27e1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a15a914c243f1fafd3b913d98113e984bf533086
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731727"
---
# <a name="manage-filetables"></a><span data-ttu-id="aa189-102">FileTable 관리</span><span class="sxs-lookup"><span data-stu-id="aa189-102">Manage FileTables</span></span>
  <span data-ttu-id="aa189-103">FileTable을 관리하는 데 사용되는 일반적인 관리 태스크에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-103">Describes common administrative tasks for managing FileTables.</span></span>  
  
##  <a name="how-to-get-a-list-of-filetables-and-related-objects"></a><a name="HowToEnumerate"></a> <span data-ttu-id="aa189-104">방법: FileTable 및 관련 개체 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="aa189-104">How To: Get a List of FileTables and Related Objects</span></span>  
 <span data-ttu-id="aa189-105">FileTable 목록을 가져오려면 다음 카탈로그 뷰 중 하나를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-105">To get a list of FileTables, query one of the following catalog views:</span></span>  
  
-   [<span data-ttu-id="aa189-106">sys.filetables&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="aa189-106">sys.filetables &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-filetables-transact-sql)  
  
-   <span data-ttu-id="aa189-107">[sys.tables&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)(**is_filetable** 열의 값 확인)</span><span class="sxs-lookup"><span data-stu-id="aa189-107">[sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql) (Check the value of the **is_filetable** column.)</span></span>  
  
```sql  
SELECT * FROM sys.filetables;  
GO  
  
SELECT * FROM sys.tables WHERE is_filetable = 1;  
GO  
```  
  
 <span data-ttu-id="aa189-108">연결된 FileTable을 만들 때 생성된 시스템 정의 개체 목록을 가져오려면 카탈로그 뷰 [sys.filetable_system_defined_objects&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql)를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-108">To get a list of the system-defined objects that were created when the associated FileTables were created, query the catalog view [sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql).</span></span>  
  
```sql  
SELECT object_id, OBJECT_NAME(object_id) AS 'Object Name'  
    FROM sys.filetable_system_defined_objects  
    WHERE object_id = filetable_object_id;  
GO  
```  
  
##  <a name="disabling-and-re-enabling-non-transactional-access-at-the-database-level"></a><a name="BasicsDisabling"></a> <span data-ttu-id="aa189-109">데이터베이스 수준에서 비트랜잭션 액세스 사용 해제 및 다시 설정</span><span class="sxs-lookup"><span data-stu-id="aa189-109">Disabling and Re-enabling Non-Transactional Access at the Database Level</span></span>  
 <span data-ttu-id="aa189-110">특정 관리 태스크에 필요한 단독 액세스 권한을 획득하려면 비트랜잭션 액세스를 일시적으로 사용하지 않도록 설정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-110">To acquire the exclusive access that is required for certain administrative tasks, you may have to disable non-transactional access temporarily.</span></span>  
  
 <span data-ttu-id="aa189-111">**비트랜잭션 액세스 수준을 변경할 경우 ALTER DATABASE 문의 동작**</span><span class="sxs-lookup"><span data-stu-id="aa189-111">**Behavior of the ALTER DATABASE statement when changing the level of non-transactional access**</span></span>  
  
-   <span data-ttu-id="aa189-112">비트랜잭션 액세스를 READ_ONLY 또는 OFF로 설정하면 ALTER DATABASE 명령은 요청한 작업과 충돌하는 열려 있는 파일 핸들이 있는 동안에는 사용자에게 제어를 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-112">When you set non-transactional access to READ_ONLY or OFF, the ALTER DATABASE command does not return control to the user as long as there are open file handles that conflict with the requested operation.</span></span> <span data-ttu-id="aa189-113">이 작업과 충돌하는 파일 핸들에는 다음과 같은 것이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-113">The file handles that conflict with this operation include the following:</span></span>  
  
    -   <span data-ttu-id="aa189-114">액세스를 **NONE**으로 설정하는 경우 모든 열려 있는 파일 핸들</span><span class="sxs-lookup"><span data-stu-id="aa189-114">When you are setting access to **NONE**, all open file handles.</span></span>  
  
    -   <span data-ttu-id="aa189-115">액세스를 **READ_ONLY**로 설정하는 경우 쓰기 액세스를 위해 열린 모든 파일 핸들</span><span class="sxs-lookup"><span data-stu-id="aa189-115">When you are setting access to **READ_ONLY**, all file handles opened for write access.</span></span>  
  
     <span data-ttu-id="aa189-116">열려 있는 파일 핸들을 중지하는 방법은 이 항목의 [FileTable과 연결된 열려 있는 파일 핸들 중지](#BasicsKilling) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa189-116">For information about killing open file handles, see [Killing Open File Handles Associated with a FileTable](#BasicsKilling) in this topic.</span></span>  
  
     <span data-ttu-id="aa189-117">ALTER DATABASE 명령이 취소되거나 시간 초과로 종료된 경우에는 트랜잭션 액세스 수준이 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-117">If the ALTER DATABASE command is canceled or ends with a timeout, then the level of transactional access is not changed.</span></span>  
  
-   <span data-ttu-id="aa189-118">WITH \<termination> 절(ROLLBACK AFTER integer [ SECONDS ] | ROLLBACK IMMEDIATE | NO_WAIT)이 포함된 ALTER DATABASE 문을 호출하면 열려 있는 모든 비트랜잭션 파일 핸들이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-118">If you call the ALTER DATABASE statement with a WITH \<termination> clause (ROLLBACK AFTER integer [ SECONDS ] | ROLLBACK IMMEDIATE | NO_WAIT), then all open non-transactional file handles are killed.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="aa189-119">열려 있는 파일 핸들을 중지하면 저장하지 않은 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-119">Killing open file handles may cause users to lose unsaved data.</span></span> <span data-ttu-id="aa189-120">이 동작은 파일 시스템 자체의 동작과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-120">This behavior is consistent with the behavior of the file system itself.</span></span>  
  
 <span data-ttu-id="aa189-121">**비트랜잭션 액세스를 사용하지 않도록 설정할 경우의 효과**</span><span class="sxs-lookup"><span data-stu-id="aa189-121">**Effects of disabling non-transactional access**</span></span>  
  
 <span data-ttu-id="aa189-122">데이터베이스 수준에서 비트랜잭션 액세스 수준을 변경하면 데이터베이스 수준 디렉터리에 다음과 같은 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-122">Changing the level of non-transactional access at the database level has the following effects on the FileTable directories under the database-level directory:</span></span>  
  
-   <span data-ttu-id="aa189-123">액세스를 **NONE**으로 설정한 경우 모든 FileTable 디렉터리와 내용이 더 이상 액세스할 수 없거나 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-123">When you set access to **NONE**, then all the FileTable directories and their contents are no longer accessible or visible.</span></span>  
  
-   <span data-ttu-id="aa189-124">액세스를 **READ_ONLY**로 설정한 경우 모든 FileTable 디렉터리와 내용도 읽기 전용이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-124">When you set access to **READ_ONLY**, then all the FileTable directories and their contents are also read-only.</span></span>  
  
 <span data-ttu-id="aa189-125">인스턴스 수준에서 FILESTREAM을 사용하지 않도록 설정하면 해당 인스턴스의 데이터베이스 수준 디렉터리와 이 디렉터리 아래의 FileTable 디렉터리에 다음과 같은 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-125">Disabling FILESTREAM at the instance level has the following effects on the database-level directories on that instance, and the FileTable directories under them:</span></span>  
  
-   <span data-ttu-id="aa189-126">인스턴스 수준에서 FILESTREAM을 사용하지 않도록 설정한 경우 인스턴스에 대한 데이터베이스 수준 디렉터리가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-126">None of the database-level directories on the instance are visible if FILESTREAM is disabled at the instance level.</span></span>  
  
###  <a name="how-to-disable-and-re-enable-non-transactional-access-at-the-database-level"></a><a name="HowToDisable"></a> <span data-ttu-id="aa189-127">방법: 데이터베이스 수준에서 비트랜잭션 액세스 사용 해제 및 다시 설정</span><span class="sxs-lookup"><span data-stu-id="aa189-127">How To: Disable and Re-enable Non-Transactional Access at the Database Level</span></span>  
 <span data-ttu-id="aa189-128">자세한 내용은 [ALTER DATABASE SET 옵션&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa189-128">For more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
 <span data-ttu-id="aa189-129">**전체 비트랜잭션 액세스를 사용하지 않도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="aa189-129">**To disable full non-transactional access**</span></span>  
 <span data-ttu-id="aa189-130">**ALTER DATABASE** 문을 호출하고 **NON_TRANSACTED_ACCESS** 값을 **READ_ONLY** 또는 **OFF**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-130">Call the **ALTER DATABASE** statement and SET the value of **NON_TRANSACTED_ACCESS** to **READ_ONLY** or **OFF**.</span></span>  
  
```sql  
-- Disable write access.  
ALTER DATABASE database_name  
    SET FILESTREAM ( NON_TRANSACTED_ACCESS = READ_ONLY );  
GO  
  
-- Disable non-transactional access.  
ALTER DATABASE database_name  
    SET FILESTREAM ( NON_TRANSACTED_ACCESS = OFF );  
GO  
```  
  
 <span data-ttu-id="aa189-131">**전체 비트랜잭션 액세스를 다시 사용하도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="aa189-131">**To re-enable full non-transactional access**</span></span>  
 <span data-ttu-id="aa189-132">**ALTER DATABASE** 문을 호출하고 **NON_TRANSACTED_ACCESS** 값을 **FULL**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-132">Call the **ALTER DATABASE** statement and SET the value of **NON_TRANSACTED_ACCESS** to **FULL**.</span></span>  
  
```sql  
ALTER DATABASE database_name  
    SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL );  
GO  
```  
  
###  <a name="how-to-ensure-the-visibility-of-the-filetables-in-a-database"></a><a name="visible"></a> <span data-ttu-id="aa189-133">방법: 데이터베이스에서 FileTable의 가시성 보장</span><span class="sxs-lookup"><span data-stu-id="aa189-133">How to: Ensure the Visibility of the FileTables in a Database</span></span>  
 <span data-ttu-id="aa189-134">다음 조건에 모두 해당하는 경우 데이터베이스 수준 디렉터리와 이 디렉터리 아래의 FileTable 디렉터리가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-134">A database-level directory and the FileTable directories under it are visible when all of these conditions are true:</span></span>  
  
1.  <span data-ttu-id="aa189-135">인스턴스 수준에서 FILESTREAM을 사용하도록 설정한 경우</span><span class="sxs-lookup"><span data-stu-id="aa189-135">FILESTREAM is enabled at the instance level.</span></span>  
  
2.  <span data-ttu-id="aa189-136">데이터베이스 수준에서 비트랜잭션 액세스를 사용하도록 설정한 경우</span><span class="sxs-lookup"><span data-stu-id="aa189-136">Non-transactional access is enabled at the database level.</span></span>  
  
3.  <span data-ttu-id="aa189-137">데이터베이스 수준에서 유효한 디렉터리를 지정한 경우</span><span class="sxs-lookup"><span data-stu-id="aa189-137">A valid directory has been specified at the database level.</span></span>  
  
##  <a name="disabling-and-re-enabling-the-filetable-namespace-at-the-table-level"></a><a name="BasicsEnabling"></a> <span data-ttu-id="aa189-138">테이블 수준에서 FileTable 네임스페이스 사용 해제 및 다시 설정</span><span class="sxs-lookup"><span data-stu-id="aa189-138">Disabling and Re-enabling the FileTable Namespace at the Table Level</span></span>  
 <span data-ttu-id="aa189-139">FileTable 네임스페이스를 사용하지 않도록 설정하면 FileTable과 함께 만들어진 모든 시스템 정의 제약 조건 및 트리거도 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-139">Disabling the FileTable namespace disables all the system-defined constraints and triggers that were created with the FileTable.</span></span> <span data-ttu-id="aa189-140">이는 FileTable 의미 체계를 적용해야 하는 부담 없이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 작업을 사용하여 FileTable을 대규모로 다시 구성해야 하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-140">This is useful in cases where a FileTable has to be reorganized on a large scale by using [!INCLUDE[tsql](../../includes/tsql-md.md)] operations without incurring the expense of enforcing FileTable semantics.</span></span> <span data-ttu-id="aa189-141">하지만 이러한 작업으로 인해 FileTable이 일관성 없는 상태가 되고 FILETABLE 네임스페이스를 다시 사용하도록 설정하는 작업을 수행하지 못하게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-141">However these operations can leave the FileTable in an inconsistent state, and can prevent the re-enabling of the FileTable namespace.</span></span>  
  
 <span data-ttu-id="aa189-142">FileTable 네임스페이스를 사용하지 않도록 설정하면 다음과 같은 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-142">Disabling a FileTable namespace has the following results:</span></span>  
  
-   <span data-ttu-id="aa189-143">FileTable 열과 데이터는 테이블에서 실제로 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-143">FileTable columns and data are not physically dropped from the table.</span></span>  
  
-   <span data-ttu-id="aa189-144">FileTable 디렉터리와 이 디렉터리에 포함된 파일 및 디렉터리가 파일 시스템에서 사라지고 파일 I/O 액세스 기능에 대해 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-144">The FileTable directory and the files and directories that it contains disappear from the file system and are not available for file i/o access.</span></span>  
  
-   <span data-ttu-id="aa189-145">시스템 정의 FileTable 열은 삭제하거나 다시 만들 수 없지만 DML 작업 시 일반 열과 동일하게 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-145">System-defined FileTable columns cannot be dropped and recreated; otherwise, however, they behave like ordinary columns for DML operations.</span></span>  
  
-   <span data-ttu-id="aa189-146">열려 있는 파일 핸들이 있으면 FileTable 제약 조건을 사용하지 않도록 설정할 수 없습니다. 그렇게 하려면 테이블에 대한 스키마 잠금이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-146">Open file handles prevent the FileTable constraints from being disabled, since this operation requires a schema lock on the table.</span></span>  
  
-   <span data-ttu-id="aa189-147">FileTable 네임스페이스를 사용하지 않도록 설정하면 시스템 정의 제약 조건 및 트리거를 포함한 모든 FileTable 의미 체계의 적용이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-147">Enforcement of all the FileTable semantics, including system-defined constraints and triggers, stops after the FileTable namespace is disabled.</span></span>  
  
 <span data-ttu-id="aa189-148">FileTable 네임스페이스를 다시 사용하도록 설정하면 다음과 같은 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-148">Re-enabling a FileTable namespace has the following results:</span></span>  
  
-   <span data-ttu-id="aa189-149">FileTable의 일관성이 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-149">The FileTable is checked for consistency.</span></span> <span data-ttu-id="aa189-150">불일치가 발견되면 오류가 발생하고 FileTable이 사용되지 않는 상태로 유지되고, 그렇지 않으면 FileTable이 다시 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-150">If inconsistencies are found, then an error is raised and the FileTable remains disabled; otherwise, the FileTable is re-enabled.</span></span>  
  
-   <span data-ttu-id="aa189-151">시스템 정의 제약 조건 및 트리거를 포함하여 FileTable 의미 체계의 적용이 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-151">The enforcement of FileTable semantics, including system-defined constraints and triggers, is restored.</span></span>  
  
-   <span data-ttu-id="aa189-152">FileTable 디렉터리와 이 디렉터리에 포함된 파일 및 디렉터리가 파일 시스템에 표시되고 파일 I/O 액세스 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-152">The FileTable directory and the files and directories that it contains become visible in the file system and become available for file i/o access.</span></span>  
  
###  <a name="how-to-disable-and-re-enable-the-filetable-namespace-at-the-table-level"></a><a name="HowToEnableNS"></a> <span data-ttu-id="aa189-153">방법: 테이블 수준에서 FileTable 네임스페이스 사용 해제 및 다시 설정</span><span class="sxs-lookup"><span data-stu-id="aa189-153">How To: Disable and Re-enable the FileTable Namespace at the Table Level</span></span>  
 <span data-ttu-id="aa189-154">**{ ENABLE | DISABLE } FILETABLE_NAMESPACE** 옵션을 사용하여 ALTER TABLE 문을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-154">Call the ALTER TABLE statement with the **{ ENABLE | DISABLE } FILETABLE_NAMESPACE** option.</span></span>  
  
 <span data-ttu-id="aa189-155">**FileTable 네임스페이스를 사용하지 않도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="aa189-155">**To disable the FileTable namespace**</span></span>  
 ```sql  
ALTER TABLE filetable_name  
    DISABLE FILETABLE_NAMESPACE;  
GO  
```  
  
 <span data-ttu-id="aa189-156">**FileTable 네임스페이스를 다시 사용하도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="aa189-156">**To re-enable the FileTable namespace**</span></span>  
 ```sql  
ALTER TABLE filetable_name  
    ENABLE FILETABLE_NAMESPACE;  
GO  
```  
  
##  <a name="killing-open-file-handles-associated-with-a-filetable"></a><a name="BasicsKilling"></a> <span data-ttu-id="aa189-157">FileTable과 연결된 열려 있는 파일 핸들 중지</span><span class="sxs-lookup"><span data-stu-id="aa189-157">Killing Open File Handles Associated with a FileTable</span></span>  
 <span data-ttu-id="aa189-158">FileTable에 저장된 파일에 대해 열려 있는 핸들이 있으면 특정 관리 태스크에 필요한 단독 액세스가 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-158">Open handles to the files stored in a FileTable can prevent the exclusive access that is required for certain administrative tasks.</span></span> <span data-ttu-id="aa189-159">긴급 태스크를 수행할 수 있도록 하려면 하나 이상의 FileTable과 연결된 열려 있는 파일 핸들을 중지해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-159">To enable urgent tasks, you may have to kill open file handles associated with one or more FileTables.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="aa189-160">열려 있는 파일 핸들을 중지하면 저장하지 않은 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-160">Killing open file handles may cause users to lose unsaved data.</span></span> <span data-ttu-id="aa189-161">이 동작은 파일 시스템 자체의 동작과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-161">This behavior is consistent with the behavior of the file system itself.</span></span>  
  
###  <a name="how-to-get-a-list-of-open-file-handles-associated-with-a-filetable"></a><a name="HowToListOpen"></a> <span data-ttu-id="aa189-162">방법: FileTable과 연결된 열려 있는 파일 핸들 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="aa189-162">How To: Get a List of Open File Handles Associated with a FileTable</span></span>  
 <span data-ttu-id="aa189-163">카탈로그 뷰 [sys.dm_filestream_non_transacted_handles&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql)를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-163">Query the catalog view [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql).</span></span>  
  
```sql  
SELECT * FROM sys.dm_filestream_non_transacted_handles;  
GO  
```  
  
###  <a name="how-to-kill-open-file-handles-associated-with-a-filetable"></a><a name="HowToKill"></a> <span data-ttu-id="aa189-164">방법: FileTable과 연결된 열려 있는 파일 핸들 중지</span><span class="sxs-lookup"><span data-stu-id="aa189-164">How To: Kill Open File Handles Associated with a FileTable</span></span>  
 <span data-ttu-id="aa189-165">적절한 인수로 저장 프로시저 [sp_kill_filestream_non_transacted_handles&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles)를 호출하여 데이터베이스 또는 FileTable에 열려 있는 모든 파일 핸들을 중지하거나 특정 핸들을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-165">Call the stored procedure [sp_kill_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles) with the appropriate arguments to kill all open file handles in the database or in the FileTable, or to kill a specific handle.</span></span>  
  
```  
USE database_name;  
  
-- Kill all open handles in all the filetables in the database.  
EXEC sp_kill_filestream_non_transacted_handles;  
GO  
  
-- Kill all open handles in a single filetable.  
EXEC sp_kill_filestream_non_transacted_handles @table_name = 'filetable_name';  
GO  
  
-- Kill a single handle.  
EXEC sp_kill_filestream_non_transacted_handles @handle_id = integer_handle_id;  
GO  
```  
  
###  <a name="how-to-identify-the-locks-held-by-filetables"></a><a name="HowToIdentifyLocks"></a> <span data-ttu-id="aa189-166">방법: FileTable이 보유한 잠금 식별</span><span class="sxs-lookup"><span data-stu-id="aa189-166">How to: Identify the Locks Held by FileTables</span></span>  
 <span data-ttu-id="aa189-167">FileTable이 보유한 대부분의 잠금은 애플리케이션에서 연 파일에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-167">Most locks taken by FileTables correspond to files opened by applications.</span></span>  
  
 <span data-ttu-id="aa189-168">**열려 있는 파일과 연결된 잠금을 식별하려면**</span><span class="sxs-lookup"><span data-stu-id="aa189-168">**To identify open files and the associated locks**</span></span>  
 <span data-ttu-id="aa189-169">동적 관리 뷰 [sys.dm_tran_locks&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql)의 **request_owner_id** 필드와 [sys.dm_filestream_non_transacted_handles&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql)의 **fcb_id** 필드를 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-169">Join the **request_owner_id** field in the dynamic management view [sys.dm_tran_locks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql) with the **fcb_id** field in [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql).</span></span> <span data-ttu-id="aa189-170">잠금이 열려 있는 하나의 열려 있는 파일 핸들에 해당하지 않는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-170">In some cases, the lock does not correspond to a single open file handle.</span></span>  
  
```sql  
SELECT opened_file_name  
    FROM sys.dm_filestream_non_transacted_handles  
    WHERE fcb_id IN  
        ( SELECT request_owner_id FROM sys.dm_tran_locks );  
GO  
```  
  
##  <a name="filetable-security"></a><a name="BasicsSecurity"></a> <span data-ttu-id="aa189-171">FileTable 보안</span><span class="sxs-lookup"><span data-stu-id="aa189-171">FileTable Security</span></span>  
 <span data-ttu-id="aa189-172">FileTable에 저장되는 파일과 디렉터리에는 SQL Server 보안만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-172">The files and directories stored in FileTables are secured by SQL Server security only.</span></span> <span data-ttu-id="aa189-173">테이블 및 열 기반 보안은 파일 시스템 액세스와 [!INCLUDE[tsql](../../includes/tsql-md.md)] 액세스에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-173">Table and column-based security is enforced for file system access as well as [!INCLUDE[tsql](../../includes/tsql-md.md)] access.</span></span> <span data-ttu-id="aa189-174">Windows 파일 시스템 보안 API 및 ACL 설정은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-174">Windows file system security APIs and ACL settings are not supported.</span></span>  
  
 <span data-ttu-id="aa189-175">파일 데이터는 FileTable에 FILESTREAM 열로 저장되므로 FILESTREAM 파일 그룹과 컨테이너에 적용 가능한 보안 및 액세스 권한이 FileTable에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-175">The security and access permissions that are applicable to FILESTREAM filegroups and containers also apply to FileTables, since the file data is stored as a FILESTREAM column in the FileTable.</span></span>  
  
 <span data-ttu-id="aa189-176">**FileTable 보안 및 Transact-SQL 액세스**</span><span class="sxs-lookup"><span data-stu-id="aa189-176">**FileTable Security and Transact-SQL Access**</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="aa189-177">액세스는 FileTable의 데이터에 대해 다른 테이블과 동일한 방식으로 보호됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-177">access to data in FileTables is secured in the same way as any other table.</span></span> <span data-ttu-id="aa189-178">데이터를 액세스하거나 변경하는 모든 작업에 대해 적절한 테이블 및 열 수준 보안 검사가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-178">Appropriate table and column-level security checks are done for every operation that accesses or changes the data.</span></span>  
  
 <span data-ttu-id="aa189-179">**FileTable 보안 및 파일 시스템 액세스**</span><span class="sxs-lookup"><span data-stu-id="aa189-179">**FileTable Security and File System Access**</span></span>  
 <span data-ttu-id="aa189-180">파일 시스템 API를 통해 FileTable에 저장된 파일 또는 디렉터리에 대한 핸들을 열려면 FileTable의 전체 행에 대한 적절한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 권한(테이블 수준 권한)이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-180">File system APIs require appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permissions on the entire row in the FileTable (that is, table-level permission) to open a handle to a file or directory stored in the FileTable.</span></span> <span data-ttu-id="aa189-181">사용자에게 FileTable의 모든 열에 대한 적절한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 권한이 없으면 파일 시스템 액세스가 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-181">If the user does not have the appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permission on any column in the FileTable, then file system access is denied.</span></span>  
  
##  <a name="backup-and-filetables"></a><a name="OtherBackup"></a> <span data-ttu-id="aa189-182">백업과 FileTable</span><span class="sxs-lookup"><span data-stu-id="aa189-182">Backup and FileTables</span></span>  
 <span data-ttu-id="aa189-183">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 사용하여 FileTable을 백업하면 FILESTREAM 데이터가 데이터베이스에 구조화된 데이터와 함께 백업됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-183">When you use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to back up a FileTable, the FILESTREAM data is backed up with the structured data in the database.</span></span> <span data-ttu-id="aa189-184">FILESTREAM 데이터를 관계형 데이터와 함께 백업하지 않으려면 부분 백업을 사용하여 FILESTREAM 파일 그룹을 제외할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-184">If you do not want to back up FILESTREAM data with relational data, you can use a partial backup to exclude FILESTREAM filegroups.</span></span>  
  
 <span data-ttu-id="aa189-185">**FileTable 백업의 트랜잭션 일관성**</span><span class="sxs-lookup"><span data-stu-id="aa189-185">**Transactional Consistency of FileTable Backups**</span></span>  
  
 <span data-ttu-id="aa189-186">백업, 로그 백업 및 트랜잭션 복제를 비롯한 많은 관리 도구와 작업에서는 트랜잭션 로그를 읽음으로써 트랜잭션 차원에서 일관된 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-186">Many administrative tools and operations, (including backup, log backup, and transactional replication) read transactionally consistent data by reading the transaction logs.</span></span> <span data-ttu-id="aa189-187">이때 트랜잭션의 일부로 업데이트된 FILESTREAM 데이터를 읽게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-187">At this time, they read any FILESTREAM data updated as part of a transaction.</span></span> <span data-ttu-id="aa189-188">데이터베이스 수준에서 비트랜잭션 액세스가 사용하도록 설정되지 않은 경우 이러한 도구 및 작업은 전체 트랜잭션에 일관되게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-188">When non-transactional access is not enabled at the database level, these tools and operations work with full transactional consistency.</span></span>  
  
 <span data-ttu-id="aa189-189">그러나 전체 비트랜잭션 액세스가 사용하도록 설정되어 있으면 FileTable에는 도구 또는 프로세스가 트랜잭션 로그에서 읽고 있는 트랜잭션보다 더 최근에 비트랜잭션 업데이트를 통해 업데이트된 데이터가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-189">However, when full non-transactional access is enabled, then a FileTable could contain data that was updated more recently (through a non-transactional update) than the transaction that the tool or process is reading from the transaction log.</span></span> <span data-ttu-id="aa189-190">즉, 특정 트랜잭션에 대한 "지정 시간" 복원 작업에 해당 트랜잭션보다 최신 상태인 FILESTREAM 데이터가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-190">This means that a "point in time" restore operation to a specific transaction may contain FILESTREAM data that is more recent than that transaction.</span></span> <span data-ttu-id="aa189-191">이는 FileTable에 대한 비트랜잭션 업데이트가 허용될 때의 예상 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-191">This is the expected behavior when non-transactional updates are allowed on FileTables.</span></span>  
  
##  <a name="sql-server-profiler-and-filetables"></a><a name="Monitor"></a> <span data-ttu-id="aa189-192">SQL Server Profiler와 FileTable</span><span class="sxs-lookup"><span data-stu-id="aa189-192">SQL Server Profiler and FileTables</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="aa189-193">Profiler는 FileTable에 저장되는 파일에 대한 추적 출력에서 Windows 파일 열기 및 파일 닫기 작업을 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-193">Profiler can capture the Windows File Open and File Close operations in trace output for files that are stored in a FileTable.</span></span>  
  
##  <a name="auditing-and-filetables"></a><a name="OtherAuditing"></a> <span data-ttu-id="aa189-194">감사와 FileTable</span><span class="sxs-lookup"><span data-stu-id="aa189-194">Auditing and FileTables</span></span>  
 <span data-ttu-id="aa189-195">다른 테이블과 마찬가지로 FileTable을 감사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-195">FileTable can be audited just like any other table.</span></span> <span data-ttu-id="aa189-196">그러나 Win32 액세스 패턴은 집합 기반 작업이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-196">Howerver, Win32 access patterns are not set based operations.</span></span> <span data-ttu-id="aa189-197">파일 시스템의 단일 동작은 여러 개의 Transact-SQL DML 작업으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-197">A single action in the file system translates into multiple Transact-SQL DML operations.</span></span> <span data-ttu-id="aa189-198">예를 들어 Microsoft Word에서 파일을 여는 동작은 여러 개의 열기/닫기/만들기/이름 바꾸기/삭제 작업과 해당하는 Transact-SQL DML 작업으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-198">For example, opening a file in Microsoft Word translates into multiple open/close/create/rename/delete operations and corresponding Transact-SQL DML activities.</span></span> <span data-ttu-id="aa189-199">이로 인해 파일 시스템 동작 간의 레코드와 해당하는 Transact-SQL DML 감사 레코드 간의 상관 관계를 파악하기가 어려운 복잡한 감사 레코드가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-199">This results in verbose audit records where it is hard to correlate records between file system actions and corresponding Transact-SQL DML audit records.</span></span>  
  
##  <a name="dbcc-and-filetables"></a><a name="OtherDBCC"></a> <span data-ttu-id="aa189-200">DBCC와 FileTable</span><span class="sxs-lookup"><span data-stu-id="aa189-200">DBCC and FileTables</span></span>  
 <span data-ttu-id="aa189-201">DBCC CHECKCONSTRAINTS를 사용하여 시스템 정의 제약 조건을 비롯한 FileTable의 제약 조건을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa189-201">You can use DBCC CHECKCONSTRAINTS to validate the constraints on a FileTable including system-defined constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa189-202">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aa189-202">See Also</span></span>  
 <span data-ttu-id="aa189-203">[FileTable과 기타 SQL Server 기능 간 호환성](filetable-compatibility-with-other-sql-server-features.md) </span><span class="sxs-lookup"><span data-stu-id="aa189-203">[FileTable Compatibility with Other SQL Server Features](filetable-compatibility-with-other-sql-server-features.md) </span></span>  
 [<span data-ttu-id="aa189-204">FileTable DDL, 함수, 저장 프로시저 및 뷰</span><span class="sxs-lookup"><span data-stu-id="aa189-204">FileTable DDL, Functions, Stored Procedures, and Views</span></span>](../views/views.md)  
  
  
