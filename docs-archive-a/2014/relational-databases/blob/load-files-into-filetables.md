---
title: FileTable로 파일 로드 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], migrating files
- FileTables [SQL Server], bulk loading
- FileTables [SQL Server], loading files
ms.assetid: dc842a10-0586-4b0f-9775-5ca0ecc761d9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 43ea31523da2dfa8b387f68ce4f7c7f07868dd6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740059"
---
# <a name="load-files-into-filetables"></a><span data-ttu-id="6b3ba-102">FileTable로 파일 로드</span><span class="sxs-lookup"><span data-stu-id="6b3ba-102">Load Files into FileTables</span></span>
  <span data-ttu-id="6b3ba-103">파일을 FileTable로 로드 또는 마이그레이션하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-103">Describes how to load or migrate files into FileTables.</span></span>  
  
##  <a name="loading-or-migrating-files-into-a-filetable"></a><a name="BasicsLoadNew"></a> <span data-ttu-id="6b3ba-104">FileTable로 파일 로드 또는 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="6b3ba-104">Loading or Migrating Files into a FileTable</span></span>  
 <span data-ttu-id="6b3ba-105">FileTable로 파일을 로드하거나 마이그레이션하기 위해 선택하는 방법은 파일이 현재 저장된 위치에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-105">The method that you choose for loading or migrating files into a FileTable depends on where the files are currently stored.</span></span>  
  
|<span data-ttu-id="6b3ba-106">파일의 현재 위치</span><span class="sxs-lookup"><span data-stu-id="6b3ba-106">Current location of files</span></span>|<span data-ttu-id="6b3ba-107">마이그레이션 옵션</span><span class="sxs-lookup"><span data-stu-id="6b3ba-107">Options for migration</span></span>|  
|-------------------------------|---------------------------|  
|<span data-ttu-id="6b3ba-108">파일이 현재 파일 시스템에 저장되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-108">Files are currently stored in the file system.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6b3ba-109">에서 파일에 대해 알지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-109">has no knowledge of the files.</span></span>|<span data-ttu-id="6b3ba-110">FileTable은 Windows 파일 시스템에 폴더로 나타나므로 파일을 이동하거나 복사하는 데 사용할 수 있는 방법으로 파일을 새 FileTable로 쉽게 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-110">Since a FileTable appears as a folder in the Windows file system, you can easily load files into a new FileTable by using any of the available methods for moving or copying files.</span></span> <span data-ttu-id="6b3ba-111">이러한 방법에는 Windows 탐색기, 명령줄 옵션(xcopy, robocopy 등), 사용자 지정 스크립트나 애플리케이션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-111">These methods include Windows Explorer, command line options including xcopy and robocopy, and custom scripts or applications.</span></span><br /><br /> <span data-ttu-id="6b3ba-112">기존 폴더를 FileTable로 변환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-112">You cannot convert an existing folder to a FileTable.</span></span>|  
|<span data-ttu-id="6b3ba-113">파일이 현재 파일 시스템에 저장되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-113">Files are currently stored in the file system.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6b3ba-114">에 파일에 대한 포인터가 포함된 메타데이터의 테이블이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-114">contains a table of metadata that contains pointers to the files.</span></span>|<span data-ttu-id="6b3ba-115">첫 번째 단계는 위에서 설명한 방법 중 하나를 사용하여 파일을 이동하거나 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-115">The first step is to move or copy the files by using one of the methods mentioned above.</span></span><br /><br /> <span data-ttu-id="6b3ba-116">두 번째 단계는 파일의 새 위치를 가리키도록 기존 메타데이터 테이블을 업데이트하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-116">The second step is to update the existing table of metadata to point to the new location of the files.</span></span><br /><br /> <span data-ttu-id="6b3ba-117">자세한 내용은 이 항목의 [예: 파일 시스템에서 FileTable로 파일 마이그레이션](#HowToMigrateFiles) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-117">For more information, see [Example: Migrating Files from the File System into a FileTable](#HowToMigrateFiles) in this topic.</span></span>|  
  
###  <a name="how-to-load-files-into-a-filetable"></a><a name="HowToLoadNew"></a> <span data-ttu-id="6b3ba-118">방법: FileTable로 파일 로드</span><span class="sxs-lookup"><span data-stu-id="6b3ba-118">How To: Load Files into a FileTable</span></span>  
 <span data-ttu-id="6b3ba-119">다음과 같은 방법으로 파일을 FileTable로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-119">The methods that you can use to load files into a FileTable include the following:</span></span>  
  
-   <span data-ttu-id="6b3ba-120">Windows 탐색기에서 원본 폴더의 파일을 새 FileTable 폴더로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-120">Drag and drop files from the source folders to the new FileTable folder in Windows Explorer.</span></span>  
  
-   <span data-ttu-id="6b3ba-121">명령 프롬프트나 배치 파일 또는 스크립트에서 MOVE, COPY, XCOPY 또는 ROBOCOPY 등의 명령줄 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-121">Use command line options such as MOVE, COPY, XCOPY, or ROBOCOPY from the command prompt or in a batch file or script.</span></span>  
  
-   <span data-ttu-id="6b3ba-122">**System.IO** 네임스페이스의 메서드를 사용하여 파일을 이동하거나 복사하는 사용자 지정 애플리케이션을 C# 또는 Visual Basic.NET으로 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-122">Write a custom application in C# or Visual Basic.NET that uses methods from the **System.IO** namespace to move or copy the files.</span></span>  
  
###  <a name="example-migrating-files-from-the-file-system-into-a-filetable"></a><a name="HowToMigrateFiles"></a> <span data-ttu-id="6b3ba-123">예제: 파일 시스템에서 FileTable로 파일 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="6b3ba-123">Example: Migrating Files from the File System into a FileTable</span></span>  
 <span data-ttu-id="6b3ba-124">이 시나리오에서는 파일이 파일 시스템에 저장되어 있고 파일에 대한 포인터가 포함된 메타데이터의 테이블이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-124">In this scenario, your files are stored in the file system, and you have a table of metadata in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that contains pointers to the files.</span></span> <span data-ttu-id="6b3ba-125">파일을 FileTable로 이동한 다음 메타데이터에 있는 각 파일의 원래 UNC 경로를 FileTable UNC 경로로 바꾸려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-125">You want to move the files into a FileTable, and then replace the original UNC path for each file in the metadata with the FileTable UNC path.</span></span> <span data-ttu-id="6b3ba-126">[GetPathLocator&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql) 함수를 사용하면 이 목표를 쉽게 달성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-126">The [GetPathLocator &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql) function helps you to achieve this goal.</span></span>  
  
 <span data-ttu-id="6b3ba-127">이 예에서는 `PhotoMetadata` 사진에 대 한 데이터를 포함 하는 기존 데이터베이스 테이블이 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-127">For this example, assume that there is an existing database table, `PhotoMetadata`, which contains data about photographs.</span></span> <span data-ttu-id="6b3ba-128">이 테이블에는 .jpg 파일의 실제 UNC 경로가 포함되어 있는 `varchar`(512) 형식의 `UNCPath` 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-128">This table has a column `UNCPath` of type `varchar`(512) which contains the actual UNC path to a .jpg file.</span></span>  
  
 <span data-ttu-id="6b3ba-129">파일 시스템의 이미지 파일을 FileTable로 마이그레이션하려면 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-129">To migrate the image files from the file system into a FileTable, you have to do the following:</span></span>  
  
1.  <span data-ttu-id="6b3ba-130">파일을 저장할 새 FileTable을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-130">Create a new FileTable to hold the files.</span></span> <span data-ttu-id="6b3ba-131">이 예에서는 테이블 이름으로 `dbo.PhotoTable`을 사용하지만 테이블을 만드는 코드는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-131">This example uses the table name, `dbo.PhotoTable`, but does not show the code to create the table.</span></span>  
  
2.  <span data-ttu-id="6b3ba-132">xcopy 또는 유사한 도구를 사용하여 .jpg 파일과 해당 디렉터리 구조를 FileTable의 루트 디렉터리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-132">Use xcopy or a similar tool to copy the .jpg files, with their directory structure, into the root directory of the FileTable.</span></span>  
  
3.  <span data-ttu-id="6b3ba-133">다음과 유사한 코드를 사용하여 `PhotoMetadata` 테이블의 메타데이터를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-133">Fix the metadata in the `PhotoMetadata` table, by using code similar to the following:</span></span>  
  
```sql  
--  Add a path locator column to the PhotoMetadata table.  
ALTER TABLE PhotoMetadata ADD pathlocator hierarchyid;  
  
-- Get the root path of the Photo directory on the File Server.  
DECLARE @UNCPathRoot varchar(100) = '\\RemoteShare\Photographs';  
  
-- Get the root path of the FileTable.  
DECLARE @FileTableRoot varchar(1000);  
SELECT @FileTableRoot = FileTableRootPath('dbo.PhotoTable');  
  
-- Update the PhotoMetadata table.  
  
-- Replace the File Server UNC path with the FileTable path.  
UPDATE PhotoMetadata  
    SET UNCPath = REPLACE(UNCPath, @UNCPathRoot, @FileTableRoot);  
  
-- Update the pathlocator column to contain the pathlocator IDs from the FileTable.  
UPDATE PhotoMetadata  
    SET pathlocator = GetPathLocator(UNCPath);  
```  
  
##  <a name="bulk-loading-files-into-a-filetable"></a><a name="BasicsBulkLoad"></a> <span data-ttu-id="6b3ba-134">FileTable로 파일 대량 로드</span><span class="sxs-lookup"><span data-stu-id="6b3ba-134">Bulk Loading Files into a FileTable</span></span>  
 <span data-ttu-id="6b3ba-135">FileTable은 다음과 같은 경우 대량 작업에서 일반 테이블처럼 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-135">A FileTable behaves like a normal table for bulk operations, with the following qualifications.</span></span>  
  
 <span data-ttu-id="6b3ba-136">FileTable에 파일 및 디렉터리 네임스페이스의 무결성이 유지되도록 하는 시스템 정의 제약 조건이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-136">A FileTable has system-defined constraints which ensure that the integrity of the file and directory namespace is maintained.</span></span> <span data-ttu-id="6b3ba-137">FileTable로 대량 로드되는 데이터에 대해 이러한 제약 조건을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-137">These constraints have to be verified on the data bulk loaded into the FileTable.</span></span> <span data-ttu-id="6b3ba-138">일부 대량 삽입 작업에서는 테이블 제약 조건이 무시될 수 있으므로 다음 요구 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-138">Since some bulk insert operations allow table constraints to be ignored, the following requirements are enforced.</span></span>  
  
-   <span data-ttu-id="6b3ba-139">제약 조건이 적용되는 대량 로드 작업은 FileTable에 대해 다른 테이블의 경우와 동일하게 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-139">Bulk loading operations that enforce constraints can be run against a FileTable as against any other table.</span></span> <span data-ttu-id="6b3ba-140">이 범주에는 다음 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-140">This category includes the following operations:</span></span>  
  
    -   <span data-ttu-id="6b3ba-141">CHECK_CONSTRAINTS 절을 사용하는 bcp</span><span class="sxs-lookup"><span data-stu-id="6b3ba-141">bcp with CHECK_CONSTRAINTS clause.</span></span>  
  
    -   <span data-ttu-id="6b3ba-142">CHECK_CONSTRAINTS 절을 사용하는 BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="6b3ba-142">BULK INSERT with CHECK_CONSTRAINTS clause.</span></span>  
  
    -   <span data-ttu-id="6b3ba-143">INSERT INTO ... IGNORE_CONSTRAINTS 절을 사용하지 않는 SELECT \* FROM OPENROWSET(BULK ...)</span><span class="sxs-lookup"><span data-stu-id="6b3ba-143">INSERT INTO ... SELECT \* FROM OPENROWSET(BULK ...) without IGNORE_CONSTRAINTS clause.</span></span>  
  
-   <span data-ttu-id="6b3ba-144">FileTable 시스템 정의 제약 조건을 해제하지 않은 경우 제약 조건을 적용하지 않은 대량 로드 작업은 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-144">Bulk loading operations that do not enforce constraints fail unless the FileTable system-defined constraints have been disabled.</span></span> <span data-ttu-id="6b3ba-145">이 범주에는 다음 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-145">This category includes the following operations:</span></span>  
  
    -   <span data-ttu-id="6b3ba-146">CHECK_CONSTRAINTS 절을 사용하지 않는 bcp</span><span class="sxs-lookup"><span data-stu-id="6b3ba-146">bcp without CHECK_CONSTRAINTS clause.</span></span>  
  
    -   <span data-ttu-id="6b3ba-147">CHECK_CONSTRAINTS 절을 사용하지 않는 BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="6b3ba-147">BULK INSERT without CHECK_CONSTRAINTS clause.</span></span>  
  
    -   <span data-ttu-id="6b3ba-148">INSERT INTO ... IGNORE_CONSTRAINTS 절을 사용하는 SELECT \* FROM OPENROWSET(BULK ...)</span><span class="sxs-lookup"><span data-stu-id="6b3ba-148">INSERT INTO ... SELECT \* FROM OPENROWSET(BULK ...) with IGNORE_CONSTRAINTS clause.</span></span>  
  
###  <a name="how-to-bulk-load-files-into-a-filetable"></a><a name="HowToBulkLoad"></a> <span data-ttu-id="6b3ba-149">방법: FileTable로 파일 대량 로드</span><span class="sxs-lookup"><span data-stu-id="6b3ba-149">How To: Bulk Load Files into a FileTable</span></span>  
 <span data-ttu-id="6b3ba-150">다음과 같은 다양한 방법을 사용하여 파일을 FileTable로 대량 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-150">You can use various methods to bulk load files into a FileTable:</span></span>  
  
-   <span data-ttu-id="6b3ba-151">**bcp**</span><span class="sxs-lookup"><span data-stu-id="6b3ba-151">**bcp**</span></span>  
  
    -   <span data-ttu-id="6b3ba-152">**CHECK_CONSTRAINTS** 절을 사용하여 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-152">Call with the **CHECK_CONSTRAINTS** clause.</span></span>  
  
    -   <span data-ttu-id="6b3ba-153">FileTable 네임스페이스를 사용하지 않도록 설정하고, **CHECK_CONSTRAINTS** 절을 사용하지 않고 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-153">Disable the FileTable namespace and call without the **CHECK_CONSTRAINTS** clause.</span></span> <span data-ttu-id="6b3ba-154">그런 다음 FileTable 네임스페이스를 다시 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-154">Then re-enable the FileTable namespace.</span></span>  
  
-   <span data-ttu-id="6b3ba-155">**BULK INSERT**</span><span class="sxs-lookup"><span data-stu-id="6b3ba-155">**BULK INSERT**</span></span>  
  
    -   <span data-ttu-id="6b3ba-156">**CHECK_CONSTRAINTS** 절을 사용하여 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-156">Call with the **CHECK_CONSTRAINTS** clause.</span></span>  
  
    -   <span data-ttu-id="6b3ba-157">FileTable 네임스페이스를 사용하지 않도록 설정하고, **CHECK_CONSTRAINTS** 절을 사용하지 않고 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-157">Disable the FileTable namespace and call without the **CHECK_CONSTRAINTS** clause.</span></span> <span data-ttu-id="6b3ba-158">그런 다음 FileTable 네임스페이스를 다시 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-158">Then re-enable the FileTable namespace.</span></span>  
  
-   <span data-ttu-id="6b3ba-159">**INSERT INTO ... SELECT \* FROM OPENROWSET(BULK ...)**</span><span class="sxs-lookup"><span data-stu-id="6b3ba-159">**INSERT INTO ... SELECT \* FROM OPENROWSET(BULK ...)**</span></span>  
  
    -   <span data-ttu-id="6b3ba-160">**IGNORE_CONSTRAINTS** 절을 사용하여 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-160">Call with the **IGNORE_CONSTRAINTS** clause.</span></span>  
  
    -   <span data-ttu-id="6b3ba-161">FileTable 네임스페이스를 사용하지 않도록 설정하고, **IGNORE_CONSTRAINTS** 절을 사용하지 않고 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-161">Disable the FileTable namespace and call without the **IGNORE_CONSTRAINTS** clause.</span></span> <span data-ttu-id="6b3ba-162">그런 다음 FileTable 네임스페이스를 다시 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-162">Then re-enable the FileTable namespace.</span></span>  
  
 <span data-ttu-id="6b3ba-163">FileTable 제약 조건을 해제하는 방법은 [FileTables 관리](manage-filetables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-163">For information about disabling the FileTable constraints, see [Manage FileTables](manage-filetables.md).</span></span>  
  
###  <a name="how-to-disable-filetable-constraints-for-bulk-loading"></a><a name="disabling"></a> <span data-ttu-id="6b3ba-164">방법: 대량 로드에 대한 FileTable 제약 조건 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="6b3ba-164">How To: Disable FileTable Constraints for Bulk Loading</span></span>  
 <span data-ttu-id="6b3ba-165">시스템 정의 제약 조건을 적용하는 오버헤드 없이 파일을 FileTable로 대량 로드하려면 제약 조건을 일시적으로 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-165">To bulk load files into a FileTable without the overhead of enforcing the system-defined constraints, you can temporarily disable the constraints.</span></span> <span data-ttu-id="6b3ba-166">자세한 내용은 [FileTables 관리](manage-filetables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b3ba-166">For more information, see [Manage FileTables](manage-filetables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b3ba-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6b3ba-167">See Also</span></span>  
 <span data-ttu-id="6b3ba-168">[Transact-SQL을 사용하여 FileTable에 액세스](access-filetables-with-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="6b3ba-168">[Access FileTables with Transact-SQL](access-filetables-with-transact-sql.md) </span></span>  
 [<span data-ttu-id="6b3ba-169">파일 입/출력 API를 사용하여 FileTable 액세스</span><span class="sxs-lookup"><span data-stu-id="6b3ba-169">Access FileTables with File Input-Output APIs</span></span>](access-filetables-with-file-input-output-apis.md)  
  
  
