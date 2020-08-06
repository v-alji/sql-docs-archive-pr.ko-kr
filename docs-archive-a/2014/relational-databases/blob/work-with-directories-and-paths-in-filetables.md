---
title: FileTable에서 디렉터리 및 경로 작업 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], directories
ms.assetid: f1e45900-bea0-4f6f-924e-c11e1f98ab62
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4641159e894b764cbee4d7f02085f3ceb8e6d87d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728351"
---
# <a name="work-with-directories-and-paths-in-filetables"></a><span data-ttu-id="5b303-102">FileTable에서 디렉터리 및 경로 작업</span><span class="sxs-lookup"><span data-stu-id="5b303-102">Work with Directories and Paths in FileTables</span></span>
  <span data-ttu-id="5b303-103">파일이 FileTable에 저장되는 디렉터리 구조에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-103">Describes the directory structure in which the files are stored in FileTables.</span></span>  
  
##  <a name="how-to-work-with-directories-and-paths-in-filetables"></a><a name="HowToDirectories"></a> <span data-ttu-id="5b303-104">방법: FileTable에서 디렉터리 및 경로 작업</span><span class="sxs-lookup"><span data-stu-id="5b303-104">How To: Work with Directories and Paths in FileTables</span></span>  
 <span data-ttu-id="5b303-105">다음 세 개의 함수를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 FileTable 디렉터리 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-105">You can use the following 3 functions to work with FileTable directories in [!INCLUDE[tsql](../../includes/tsql-md.md)]:</span></span>  
  
|<span data-ttu-id="5b303-106">원하는 결과</span><span class="sxs-lookup"><span data-stu-id="5b303-106">To get this result</span></span>|<span data-ttu-id="5b303-107">사용할 함수</span><span class="sxs-lookup"><span data-stu-id="5b303-107">Use this function</span></span>|  
|------------------------|-----------------------|  
|<span data-ttu-id="5b303-108">특정 FileTable 또는 현재 데이터베이스에 대한 루트 수준 UNC 경로를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-108">Get the root-level UNC path for a specific FileTable or for the current database.</span></span>|[<span data-ttu-id="5b303-109">FileTableRootPath&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5b303-109">FileTableRootPath &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/filetablerootpath-transact-sql)|  
|<span data-ttu-id="5b303-110">FileTable의 파일이나 디렉터리에 대한 절대 또는 상대 UNC 경로를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-110">Get an absolute or relative UNC path for a file or directory in a FileTable.</span></span>|[<span data-ttu-id="5b303-111">GetFileNamespacePath&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5b303-111">GetFileNamespacePath &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql)|  
|<span data-ttu-id="5b303-112">경로를 제공하여 FileTable의 지정된 파일 또는 디렉터리에 대한 경로 로케이터 ID 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-112">Get the path locator ID value for the specified file or directory in a FileTable, by providing the path.</span></span>|[<span data-ttu-id="5b303-113">GetPathLocator&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5b303-113">GetPathLocator &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/getpathlocator-transact-sql)|  
  
##  <a name="how-to-use-relative-paths-for-portable-code"></a><a name="BestPracticeRelativePaths"></a> <span data-ttu-id="5b303-114">방법: 이식 가능한 코드에 상대 경로 사용</span><span class="sxs-lookup"><span data-stu-id="5b303-114">How to: Use Relative Paths for Portable Code</span></span>  
 <span data-ttu-id="5b303-115">코드와 애플리케이션을 현재 컴퓨터 및 데이터베이스 외에서도 사용할 수 있도록 하려면 코드를 작성할 때 절대 파일 경로를 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-115">To keep code and applications independent of the current computer and database, avoid writing code that relies on absolute file paths.</span></span> <span data-ttu-id="5b303-116">대신 다음 예와 같이 [FileTableRootPath&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filetablerootpath-transact-sql) 및 [GetFileNamespacePath&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql)함수를 함께 사용하여 런타임에 파일의 전체 경로를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-116">Instead, get the complete path for a file at run time by using the [FileTableRootPath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filetablerootpath-transact-sql) and [GetFileNamespacePath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql)) functions together, as shown in the following example.</span></span> <span data-ttu-id="5b303-117">기본적으로 `GetFileNamespacePath` 함수는 데이터베이스의 루트 경로 아래에 있는 파일의 상대 경로를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-117">By default, the `GetFileNamespacePath` function returns the relative path of the file under the root path for the database.</span></span>  
  
```sql  
USE database_name;  
DECLARE @root nvarchar(100);  
DECLARE @fullpath nvarchar(1000);  
  
SELECT @root = FileTableRootPath();  
SELECT @fullpath = @root + file_stream.GetFileNamespacePath()  
    FROM filetable_name  
    WHERE name = N'document_name';  
  
PRINT @fullpath;  
GO  
```  
  
##  <a name="important-restrictions"></a><a name="restrictions"></a> <span data-ttu-id="5b303-118">중요 제한 사항</span><span class="sxs-lookup"><span data-stu-id="5b303-118">Important restrictions</span></span>  
  
###  <a name="nesting-level"></a><a name="nesting"></a> <span data-ttu-id="5b303-119">중첩 수준</span><span class="sxs-lookup"><span data-stu-id="5b303-119">Nesting level</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5b303-120">15개 수준을 초과하는 하위 디렉터리를 FileTable 디렉터리에 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-120">You cannot store more than 15 levels of subdirectories in the FileTable directory.</span></span> <span data-ttu-id="5b303-121">15개 수준의 하위 디렉터리를 저장할 경우 최하위 수준에는 파일이 포함될 수 없습니다. 최하위 수준에 파일이 있으면 수준이 초과됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-121">When you store 15 levels of subdirectories, then the lowest level cannot contain files, since these files would represent an additional level.</span></span>  
  
###  <a name="length-of-full-path-name"></a><a name="fqnlength"></a> <span data-ttu-id="5b303-122">전체 경로 이름의 길이</span><span class="sxs-lookup"><span data-stu-id="5b303-122">Length of full path name</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5b303-123">NTFS 파일 시스템은 Windows 셸 및 대부분의 Windows API의 260자 제한보다 긴 경로 이름을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-123">The NTFS file system supports path names that are much longer than the 260-character limit of the Windows shell and most Windows APIs.</span></span> <span data-ttu-id="5b303-124">따라서 전체 경로 이름이 260자를 초과할 수 있기 때문에 Windows 탐색기 또는 다른 많은 Windows 애플리케이션으로 보거나 열 수 없는 Transact-SQL을 사용하여 FileTable의 파일 계층에 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-124">Therefore it is possible to create files in the file hierarchy of a FileTable by using Transact-SQL that you cannot view or open with Windows Explorer or many other Windows applications, because the full path name exceeds 260 characters.</span></span> <span data-ttu-id="5b303-125">그러나 Transact-SQL을 사용해서도 이러한 파일에 계속 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-125">However you can continue to access these files by using Transact-SQL.</span></span>  
  
##  <a name="the-full-path-to-an-item-stored-in-a-filetable"></a><a name="fullpath"></a> <span data-ttu-id="5b303-126">FileTable에 저장된 항목의 전체 경로</span><span class="sxs-lookup"><span data-stu-id="5b303-126">The full path to an item stored in a FileTable</span></span>  
 <span data-ttu-id="5b303-127">FileTable에 저장된 파일 또는 디렉터리의 전체 경로는 다음 요소로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-127">The full path to a file or directory stored in a FileTable begins with the following elements:</span></span>  
  
1.  <span data-ttu-id="5b303-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 수준에서 파일 I/O 액세스를 위해 설정된 공유</span><span class="sxs-lookup"><span data-stu-id="5b303-128">The share enabled for FILESTREAM file I/O access at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance level.</span></span>  
  
2.  <span data-ttu-id="5b303-129">데이터베이스 수준에서 지정된 **DIRECTORY_NAME**</span><span class="sxs-lookup"><span data-stu-id="5b303-129">The **DIRECTORY_NAME** specified at the database level.</span></span>  
  
3.  <span data-ttu-id="5b303-130">FileTable 수준에서 지정된 **FILETABLE_DIRECTORY**</span><span class="sxs-lookup"><span data-stu-id="5b303-130">The **FILETABLE_DIRECTORY** specified at the FileTable level.</span></span>  
  
 <span data-ttu-id="5b303-131">결과 계층 구조는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-131">The resulting hierarchy looks like this:</span></span>  
  
 `\\<machine>\<instance-level FILESTREAM share>\<database-level directory>\<FileTable directory>\`  
  
 <span data-ttu-id="5b303-132">이 디렉터리 계층 구조는 FileTable 파일 네임스페이스의 루트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-132">This directory hierarchy forms the root of the FileTable's file namespace.</span></span> <span data-ttu-id="5b303-133">이 디렉터리 계층 구조 아래에 FileTable에 대한 FILESTREAM 데이터가 파일 및 하위 디렉터리로 저장되며, 이 하위 디렉터리도 파일과 하위 디렉터리를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-133">Under this directory hierarchy, the FILESTREAM data for the FileTable is stored as files, and as subdirectories which can also contain files and subdirectories.</span></span>  
  
 <span data-ttu-id="5b303-134">인스턴스 수준 FILESTREAM 공유에 만들어지는 디렉터리 계층 구조는 가상 디렉터리 계층 구조라는 것을 유념해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-134">It is important to keep in mind that the directory hierarchy created under the instance-level FILESTREAM share is a virtual directory hierarchy.</span></span> <span data-ttu-id="5b303-135">이 계층 구조는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 저장되며 NTFS 파일 시스템에는 물리적으로 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-135">This hierarchy is stored in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database and is not represented physically in the NTFS file system.</span></span> <span data-ttu-id="5b303-136">이 FILESTREAM 공유 및 여기에 포함된 FileTable에서 파일 및 디렉터리에 액세스하는 모든 작업은 파일 시스템에 포함된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소에서 가로채어 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-136">All operations that access files and directories under the FILESTREAM share and in the FileTables that it contains are intercepted and handled by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component embedded in the file system.</span></span>  
  
##  <a name="the-semantics-of-the-root-directories-at-the-instance-database-and-filetable-levels"></a><a name="roots"></a> <span data-ttu-id="5b303-137">인스턴스, 데이터베이스 및 FileTable 수준에서 루트 디렉터리의 의미 체계</span><span class="sxs-lookup"><span data-stu-id="5b303-137">The semantics of the root directories at the instance, database, and FileTable levels</span></span>  
 <span data-ttu-id="5b303-138">이 디렉터리 계층 구조는 다음과 같은 의미 체계를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-138">This directory hierarchy observes the following semantics:</span></span>  
  
-   <span data-ttu-id="5b303-139">인스턴스 수준 FILESTREAM 공유는 관리자에 의해 구성되어 서버 속성으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-139">The instance-level FILESTREAM share is configured by an administrator and stored as a property of the server.</span></span> <span data-ttu-id="5b303-140">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 이 공유의 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-140">You can rename this share by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="5b303-141">이름 바꾸기 작업을 적용하려면 서버를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-141">A renaming operation does not take effect until the server is restarted.</span></span>  
  
-   <span data-ttu-id="5b303-142">새 데이터베이스를 만들 때 데이터베이스 수준 **DIRECTORY_NAME** 은 기본적으로 null입니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-142">The database-level **DIRECTORY_NAME** is null by default when you create a new database.</span></span> <span data-ttu-id="5b303-143">관리자는 **ALTER DATABASE** 문을 사용하여 이 이름을 설정하거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-143">An administrator can set or change this name by using the **ALTER DATABASE** statement.</span></span> <span data-ttu-id="5b303-144">이름은 해당 인스턴스에서 고유해야 하며 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-144">The name must be unique (in a case-insensitive comparison) in that instance.</span></span>  
  
-   <span data-ttu-id="5b303-145">일반적으로 FileTable을 만들 때 **FILETABLE_DIRECTORY** 이름을 **CREATE TABLE** 문의 일부로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-145">You typically provide the **FILETABLE_DIRECTORY** name as part of the **CREATE TABLE** statement when you create a FileTable.</span></span> <span data-ttu-id="5b303-146">**ALTER TABLE** 명령을 사용하여 이 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-146">You can change this name by using the **ALTER TABLE** command.</span></span>  
  
-   <span data-ttu-id="5b303-147">파일 I/O 작업을 통해 이 루트 디렉터리의 이름을 바꿀 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-147">You cannot rename these root directories through file I/O operations.</span></span>  
  
-   <span data-ttu-id="5b303-148">이러한 루트 디렉터리는 단독 파일 핸들로 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-148">You cannot open these root directories with exclusive file handles.</span></span>  
  
##  <a name="the-is_directory-column-in-the-filetable-schema"></a><a name="is_directory"></a> <span data-ttu-id="5b303-149">FileTable 스키마의 is_directory 열</span><span class="sxs-lookup"><span data-stu-id="5b303-149">The is_directory column in the FileTable schema</span></span>  
 <span data-ttu-id="5b303-150">다음 표에서는 **is_directory** 열과 FileTable의 FILESTREAM 데이터가 포함된 **file_stream** 열 간의 상호 작용에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-150">The following table describes the interaction between the **is_directory** column and the **file_stream** column that contains the FILESTREAM data in a FileTable.</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="5b303-151">*is_directory* **value**</span><span class="sxs-lookup"><span data-stu-id="5b303-151">*is_directory* **value**</span></span>|<span data-ttu-id="5b303-152">*file_stream* **value**</span><span class="sxs-lookup"><span data-stu-id="5b303-152">*file_stream* **value**</span></span>|<span data-ttu-id="5b303-153">**동작**</span><span class="sxs-lookup"><span data-stu-id="5b303-153">**Behavior**</span></span>|  
|<span data-ttu-id="5b303-154">FALSE</span><span class="sxs-lookup"><span data-stu-id="5b303-154">FALSE</span></span>|<span data-ttu-id="5b303-155">NULL</span><span class="sxs-lookup"><span data-stu-id="5b303-155">NULL</span></span>|<span data-ttu-id="5b303-156">이는 시스템 정의 제약 조건에 의해 catch되는 잘못된 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-156">This is an invalid combination that will be caught by a system-defined constraint.</span></span>|  
|<span data-ttu-id="5b303-157">FALSE</span><span class="sxs-lookup"><span data-stu-id="5b303-157">FALSE</span></span>|\<value>|<span data-ttu-id="5b303-158">항목은 파일을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-158">The item represents a file.</span></span>|  
|<span data-ttu-id="5b303-159">TRUE</span><span class="sxs-lookup"><span data-stu-id="5b303-159">TRUE</span></span>|<span data-ttu-id="5b303-160">NULL</span><span class="sxs-lookup"><span data-stu-id="5b303-160">NULL</span></span>|<span data-ttu-id="5b303-161">항목은 디렉터리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-161">The item represents a directory.</span></span>|  
|<span data-ttu-id="5b303-162">TRUE</span><span class="sxs-lookup"><span data-stu-id="5b303-162">TRUE</span></span>|\<value>|<span data-ttu-id="5b303-163">이는 시스템 정의 제약 조건에 의해 catch되는 잘못된 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-163">This is an invalid combination that will be caught by a system-defined constraint.</span></span>|  
  
##  <a name="using-virtual-network-names-vnns-with-alwayson-availability-groups"></a><a name="alwayson"></a> <span data-ttu-id="5b303-164">AlwaysOn 가용성 그룹에 VNN(가상 네트워크 이름) 사용</span><span class="sxs-lookup"><span data-stu-id="5b303-164">Using Virtual Network Names (VNNs) with AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="5b303-165">FILESTREAM 또는 FileTable 데이터가 포함된 데이터베이스가 AlwaysOn 가용성 그룹에 속하는 경우</span><span class="sxs-lookup"><span data-stu-id="5b303-165">When the database that contains FILESTREAM or FileTable data belongs to an AlwaysOn availability group:</span></span>  
  
-   <span data-ttu-id="5b303-166">FILESTREAM 및 FileTable 함수가 컴퓨터 이름 대신 VNN(가상 네트워크 이름)을 사용하거나 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-166">The FILESTREAM and FileTable functions accept or return virtual network names (VNNs) instead of computer names.</span></span> <span data-ttu-id="5b303-167">이러한 함수에 대한 자세한 내용은 [Filestream 및 FileTable 함수&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5b303-167">For more information about these functions, see [Filestream and FileTable Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql).</span></span>  
  
-   <span data-ttu-id="5b303-168">파일 시스템 API를 통한 FILESTREAM 또는 FileTable 데이터에 대한 모든 액세스에는 컴퓨터 이름 대신 VNN이 사용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b303-168">All access to FILESTREAM or FileTable data through the file system APIs should use VNNs instead of computer names.</span></span> <span data-ttu-id="5b303-169">자세한 내용은 [AlwaysOn 가용성 그룹의 FILESTREAM 및 FileTable&#40;SQL Server&#41;](../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5b303-169">For more information, see [FILESTREAM and FileTable with AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b303-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5b303-170">See Also</span></span>  
 <span data-ttu-id="5b303-171">[FileTable의 필수 구성 요소를 사용하도록 설정](enable-the-prerequisites-for-filetable.md) </span><span class="sxs-lookup"><span data-stu-id="5b303-171">[Enable the Prerequisites for FileTable](enable-the-prerequisites-for-filetable.md) </span></span>  
 <span data-ttu-id="5b303-172">[FileTable 만들기, 변경 및 삭제](create-alter-and-drop-filetables.md) </span><span class="sxs-lookup"><span data-stu-id="5b303-172">[Create, Alter, and Drop FileTables](create-alter-and-drop-filetables.md) </span></span>  
 <span data-ttu-id="5b303-173">[Transact-SQL을 사용하여 FileTable에 액세스](access-filetables-with-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="5b303-173">[Access FileTables with Transact-SQL](access-filetables-with-transact-sql.md) </span></span>  
 [<span data-ttu-id="5b303-174">파일 입/출력 API를 사용하여 FileTable 액세스</span><span class="sxs-lookup"><span data-stu-id="5b303-174">Access FileTables with File Input-Output APIs</span></span>](access-filetables-with-file-input-output-apis.md)  
  
  
