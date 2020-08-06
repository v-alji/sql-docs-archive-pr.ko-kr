---
title: FileTable의 필수 구성 요소를 사용하도록 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], prerequisites
ms.assetid: 6286468c-9dc9-4eda-9961-071d2a36ebd6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5d5d2c5dab7909ec5403911d482823f488cdd809
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638855"
---
# <a name="enable-the-prerequisites-for-filetable"></a><span data-ttu-id="01991-102">FileTable의 필수 구성 요소를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="01991-102">Enable the Prerequisites for FileTable</span></span>
  <span data-ttu-id="01991-103">FileTable을 만들고 사용하기 위한 필수 구성 요소를 사용하도록 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-103">Describes how to enable the prerequisites for creating and using FileTables.</span></span>  
  
##  <a name="enabling-the-prerequisites-for-filetable"></a><a name="EnablePrereq"></a> <span data-ttu-id="01991-104">FileTable의 필수 구성 요소를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="01991-104">Enabling the Prerequisites for FileTable</span></span>  
 <span data-ttu-id="01991-105">FileTable을 만들고 사용하기 위한 필수 구성 요소를 사용하도록 설정하려면 다음 항목을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-105">To enable the prerequisites for creating and using FileTables, enable the following items:</span></span>  
  
-   <span data-ttu-id="01991-106">**인스턴스 수준:**</span><span class="sxs-lookup"><span data-stu-id="01991-106">**At the instance level:**</span></span>  
  
    -   [<span data-ttu-id="01991-107">인스턴스 수준에서 FILESTREAM을 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="01991-107">Enabling FILESTREAM at the Instance Level</span></span>](#BasicsFilestream)  
  
-   <span data-ttu-id="01991-108">**데이터베이스 수준:**</span><span class="sxs-lookup"><span data-stu-id="01991-108">**At the database level:**</span></span>  
  
    -   [<span data-ttu-id="01991-109">데이터베이스 수준에서 FILESTREAM 파일 그룹 제공</span><span class="sxs-lookup"><span data-stu-id="01991-109">Providing a FILESTREAM Filegroup at the Database Level</span></span>](#filegroup)  
  
    -   [<span data-ttu-id="01991-110">데이터베이스 수준에서 비트랜잭션 액세스를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="01991-110">Enabling Non-Transactional Access at the Database Level</span></span>](#BasicsNTAccess)  
  
    -   [<span data-ttu-id="01991-111">데이터베이스 수준에서 FileTable의 디렉터리 지정</span><span class="sxs-lookup"><span data-stu-id="01991-111">Specifying a Directory for FileTables at the Database Level</span></span>](#BasicsDirectory)  
  
##  <a name="enabling-filestream-at-the-instance-level"></a><a name="BasicsFilestream"></a> <span data-ttu-id="01991-112">인스턴스 수준에서 FILESTREAM을 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="01991-112">Enabling FILESTREAM at the Instance Level</span></span>  
 <span data-ttu-id="01991-113">FileTable은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 FILESTREAM 기능을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-113">FileTables extend the capabilities of the FILESTREAM feature of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="01991-114">따라서 FileTable을 만들고 사용하려면 먼저 Windows 수준과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 파일 I/O 액세스를 위해 FILESTREAM을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-114">Therefore you have to enable FILESTREAM for file I/O access at the Windows level and on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you can create and use FileTables.</span></span>  
  
###  <a name="how-to-enable-filestream-at-the-instance-level"></a><a name="HowToFilestream"></a> <span data-ttu-id="01991-115">방법: 인스턴스 수준에서 FILESTREAM 사용</span><span class="sxs-lookup"><span data-stu-id="01991-115">How To: Enable FILESTREAM at the Instance Level</span></span>  
 <span data-ttu-id="01991-116">FILESTREAM을 사용하도록 설정하는 방법은 [FILESTREAM 사용 및 구성](enable-and-configure-filestream.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01991-116">For information about how to enable FILESTREAM, see [Enable and Configure FILESTREAM](enable-and-configure-filestream.md).</span></span>  
  
 <span data-ttu-id="01991-117">`sp_configure`를 호출하여 인스턴스 수준에서 FILESTREAM을 사용하도록 설정하려면 filestream_access_level 옵션을 2로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-117">When you call `sp_configure` to enable FILESTREAM at the instance level, you have to set the filestream_access_level option to 2.</span></span> <span data-ttu-id="01991-118">자세한 내용은 [FILESTREAM 액세스 수준 서버 구성 옵션](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01991-118">For more information, see [filestream access level Server Configuration Option](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md).</span></span>  
  
###  <a name="how-to-allow-filestream-through-the-firewall"></a><a name="firewall"></a> <span data-ttu-id="01991-119">방법: 방화벽을 통해 FILESTREAM 허용</span><span class="sxs-lookup"><span data-stu-id="01991-119">How To: Allow FILESTREAM through the Firewall</span></span>  
 <span data-ttu-id="01991-120">방화벽을 통해 FILESTREAM을 허용하는 방법은 [Configure a Firewall for FILESTREAM Access](configure-a-firewall-for-filestream-access.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01991-120">For information about how to allow FILESTREAM through the firewall, see [Configure a Firewall for FILESTREAM Access](configure-a-firewall-for-filestream-access.md).</span></span>  
  
##  <a name="providing-a-filestream-filegroup-at-the-database-level"></a><a name="filegroup"></a> <span data-ttu-id="01991-121">데이터베이스 수준에서 FILESTREAM 파일 그룹 제공</span><span class="sxs-lookup"><span data-stu-id="01991-121">Providing a FILESTREAM Filegroup at the Database Level</span></span>  
 <span data-ttu-id="01991-122">데이터베이스에서 FileTables를 만들려면 데이터베이스에 FILESTREAM 파일 그룹이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-122">Before you can create FileTables in a database, the database must have a FILESTREAM filegroup.</span></span> <span data-ttu-id="01991-123">이 필수 구성 요소에 대한 자세한 내용은 [FILESTREAM 사용 데이터베이스 만들기](create-a-filestream-enabled-database.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01991-123">For more information about this prerequisite, see [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md).</span></span>  
  
##  <a name="enabling-non-transactional-access-at-the-database-level"></a><a name="BasicsNTAccess"></a> <span data-ttu-id="01991-124">데이터베이스 수준에서 비트랜잭션 액세스를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="01991-124">Enabling Non-Transactional Access at the Database Level</span></span>  
 <span data-ttu-id="01991-125">FileTable을 사용하면 Windows 애플리케이션에서 트랜잭션 없이도 FILESTREAM 데이터에 대한 Windows 파일 핸들을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01991-125">FileTables let Windows applications obtain a Windows file handle to FILESTREAM data without requiring a transaction.</span></span> <span data-ttu-id="01991-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 저장된 파일에 대해 이 비트랜잭션 액세스를 허용하려면 FileTable을 포함할 각 데이터베이스의 데이터베이스 수준에서 원하는 비트랜잭션 액세스 수준을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-126">To allow this non-transactional access to files stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you have to specify the desired level of non-transactional access at the database level for each database that will contain FileTables.</span></span>  
  
###  <a name="how-to-check-whether-non-transactional-access-is-enabled-on-databases"></a><a name="HowToCheckAccess"></a> <span data-ttu-id="01991-127">방법: 데이터베이스에 비트랜잭션 액세스가 사용하도록 설정되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="01991-127">How To: Check Whether Non-Transactional Access Is Enabled on Databases</span></span>  
 <span data-ttu-id="01991-128">카탈로그 뷰 [sys.database_filestream_options&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql)를 쿼리하고 **non_transacted_access** 및 **non_transacted_access_desc** 열을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-128">Query the catalog view [sys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql) and check the **non_transacted_access** and **non_transacted_access_desc** columns.</span></span>  
  
```sql  
SELECT DB_NAME(database_id), non_transacted_access, non_transacted_access_desc  
    FROM sys.database_filestream_options;  
GO  
```  
  
###  <a name="how-to-enable-non-transactional-access-at-the-database-level"></a><a name="HowToNTAccess"></a> <span data-ttu-id="01991-129">방법: 데이터베이스 수준에서 비트랜잭션 액세스를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="01991-129">How To: Enable Non-Transactional Access at the Database Level</span></span>  
 <span data-ttu-id="01991-130">사용 가능한 비트랜잭션 액세스 수준은 FULL, READ_ONLY 및 OFF입니다.</span><span class="sxs-lookup"><span data-stu-id="01991-130">The available levels of non-transactional access are FULL, READ_ONLY, and OFF.</span></span>  
  
 <span data-ttu-id="01991-131">**Transact-SQL을 사용하여 비트랜잭션 액세스 수준 지정**</span><span class="sxs-lookup"><span data-stu-id="01991-131">**Specify the level of non-transactional access by using Transact-SQL**</span></span>  
 -   <span data-ttu-id="01991-132">**새 데이터베이스를 만들 경우** **NON_TRANSACTED_ACCESS** FILESTREAM 옵션을 사용하여 [CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) 문을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-132">When you **create a new database**, call the [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) statement with the **NON_TRANSACTED_ACCESS** FILESTREAM option.</span></span>  
  
    ```sql  
    CREATE DATABASE database_name  
        WITH FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' )  
    ```  
  
-   <span data-ttu-id="01991-133">**기존 데이터베이스를 변경할 경우** **NON_TRANSACTED_ACCESS** FILESTREAM 옵션을 사용하여 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) 문을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-133">When you **alter an existing database**, call the [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) statement with the **NON_TRANSACTED_ACCESS** FILESTREAM option.</span></span>  
  
    ```sql  
    ALTER DATABASE database_name  
        SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' )  
    ```  
  
 <span data-ttu-id="01991-134">**SQL Server Management Studio를 사용하여 비트랜잭션 액세스 수준 지정**</span><span class="sxs-lookup"><span data-stu-id="01991-134">**Specify the level of non-transactional access by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="01991-135">**데이터베이스 속성** 대화 상자의 **옵션** 페이지에 있는 **FILESTREAM 비트랜잭션 액세스** 필드에서 비트랜잭션 액세스 수준을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01991-135">You can specify the level of non-transactional access in the **FILESTREAM Non-transacted Access** field of the **Options** page of the **Database Properties** dialog box.</span></span> <span data-ttu-id="01991-136">이 대화 상자에 대한 자세한 내용은 [데이터베이스 속성&#40;옵션 페이지&#41;](../databases/database-properties-options-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01991-136">For more information about this dialog box, see [Database Properties &#40;Options Page&#41;](../databases/database-properties-options-page.md).</span></span>  
  
##  <a name="specifying-a-directory-for-filetables-at-the-database-level"></a><a name="BasicsDirectory"></a> <span data-ttu-id="01991-137">데이터베이스 수준에서 FileTable의 디렉터리 지정</span><span class="sxs-lookup"><span data-stu-id="01991-137">Specifying a Directory for FileTables at the Database Level</span></span>  
 <span data-ttu-id="01991-138">데이터베이스 수준에서 파일에 대한 비트랜잭션 액세스를 사용하도록 설정할 경우 필요에 따라 **DIRECTORY_NAME** 옵션을 사용하여 디렉터리 이름도 함께 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01991-138">When you enable non-transactional access to files at the database level, you can optionally provide a directory name at the same time by using the **DIRECTORY_NAME** option.</span></span> <span data-ttu-id="01991-139">비트랜잭션 액세스를 사용하도록 설정할 때 디렉터리 이름을 제공하지 않은 경우 나중에 해당 이름을 제공해야 데이터베이스에 FileTable을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01991-139">If you do not provide a directory name when you enable non-transactional access, then you have to provide it later before you can create FileTables in the database.</span></span>  
  
 <span data-ttu-id="01991-140">FileTable 폴더 계층 구조에서 이 데이터베이스 수준 디렉터리는 인스턴스 수준에서 FILESTREAM에 대해 지정된 공유 이름의 자식이 되고 데이터베이스에 만들어진 FileTable의 부모가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01991-140">In the FileTable folder hierarchy, this database-level directory becomes the child of the share name specified for FILESTREAM at the instance level, and the parent of the FileTables created in the database.</span></span> <span data-ttu-id="01991-141">자세한 내용은 [Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01991-141">For more information, see [Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md).</span></span>  
  
###  <a name="how-to-specify-a-directory-for-filetables-at-the-database-level"></a><a name="HowToDirectory"></a> <span data-ttu-id="01991-142">방법: 데이터베이스 수준에서 FileTable의 디렉터리 지정</span><span class="sxs-lookup"><span data-stu-id="01991-142">How To: Specify a Directory for FileTables at the Database Level</span></span>  
 <span data-ttu-id="01991-143">지정한 이름은 데이터베이스 수준 디렉터리의 인스턴스 전체에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-143">The name that you specify must be unique across the instance for database-level directories.</span></span>  
  
 <span data-ttu-id="01991-144">**Transact-SQL을 사용하여 FileTable의 디렉터리 지정**</span><span class="sxs-lookup"><span data-stu-id="01991-144">**Specify a directory for FileTables by using Transact-SQL**</span></span>  
 -   <span data-ttu-id="01991-145">**새 데이터베이스를 만들 경우** **DIRECTORY_NAME** FILESTREAM 옵션을 사용하여 [CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) 문을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-145">When you **create a new database**, call the [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) statement with the **DIRECTORY_NAME** FILESTREAM option.</span></span>  
  
    ```sql  
    CREATE DATABASE database_name  
        WITH FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   <span data-ttu-id="01991-146">**기존 데이터베이스를 변경할 경우** **DIRECTORY_NAME** FILESTREAM 옵션을 사용하여 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) 문을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-146">When you **alter an existing database**, call the [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) statement with the **DIRECTORY_NAME** FILESTREAM option.</span></span> <span data-ttu-id="01991-147">이러한 옵션을 사용하여 디렉터리 이름을 변경할 경우 데이터베이스가 단독으로 잠겨 있고 열려 있는 파일 핸들이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-147">When you use these options to change the directory name, the database must be exclusively locked, with no open file handles.</span></span>  
  
    ```sql  
    ALTER DATABASE database_name  
        SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   <span data-ttu-id="01991-148">**데이터베이스를 연결할 경우** **FOR ATTACH** 옵션 및 **DIRECTORY_NAME** FILESTREAM 옵션을 사용하여 [CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) 문을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-148">When you **attach a database**, call the [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) statement with the **FOR ATTACH** option and with the **DIRECTORY_NAME** FILESTREAM option.</span></span>  
  
    ```sql  
    CREATE DATABASE database_name  
        FOR ATTACH WITH FILESTREAM ( DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   <span data-ttu-id="01991-149">**데이터베이스를 복원할 경우** **DIRECTORY_NAME** FILESTREAM 옵션을 사용하여 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) 문을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-149">When you **restore a database**, call the [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) statement with the **DIRECTORY_NAME** FILESTREAM option.</span></span>  
  
    ```sql  
    RESTORE DATABASE database_name  
        WITH FILESTREAM ( DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
 <span data-ttu-id="01991-150">**SQL Server Management Studio를 사용하여 FileTable의 디렉터리 지정**</span><span class="sxs-lookup"><span data-stu-id="01991-150">**Specify a directory for FileTables by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="01991-151">**데이터베이스 속성** 대화 상자의 **옵션** 페이지에 있는 **FILESTREAM 디렉터리 이름** 필드에서 디렉터리 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01991-151">You can specify a directory name in the **FILESTREAM Directory Name** field of the **Options** page of the **Database Properties** dialog box.</span></span> <span data-ttu-id="01991-152">이 대화 상자에 대한 자세한 내용은 [데이터베이스 속성&#40;옵션 페이지&#41;](../databases/database-properties-options-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01991-152">For more information about this dialog box, see [Database Properties &#40;Options Page&#41;](../databases/database-properties-options-page.md).</span></span>  
  
###  <a name="how-to-view-existing-directory-names-for-the-instance"></a><a name="viewnames"></a> <span data-ttu-id="01991-153">방법: 인스턴스에 대한 기존 디렉터리 이름 보기</span><span class="sxs-lookup"><span data-stu-id="01991-153">How to: View Existing Directory Names for the Instance</span></span>  
 <span data-ttu-id="01991-154">인스턴스의 기존 디렉터리 이름 목록을 보려면 카탈로그 뷰 [sys.database_filestream_options&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql)를 쿼리하고 **filestream_database_directory_name** 열을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-154">To view the list of existing directory names for the instance, query the catalog view [sys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql) and check the **filestream_database_directory_name** column.</span></span>  
  
```sql  
SELECT DB_NAME ( database_id ), directory_name  
    FROM sys.database_filestream_options;  
GO  
```  
  
###  <a name="requirements-and-restrictions-for-the-database-level-directory"></a><a name="ReqDirectory"></a> <span data-ttu-id="01991-155">데이터베이스 수준 디렉터리에 대한 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="01991-155">Requirements and Restrictions for the Database-Level Directory</span></span>  
  
-   <span data-ttu-id="01991-156">**CREATE DATABASE** 또는 **ALTER DATABASE** 를 호출할 때 옵션으로 **DIRECTORY_NAME**을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01991-156">Setting the **DIRECTORY_NAME** is optional when you call **CREATE DATABASE** or **ALTER DATABASE**.</span></span> <span data-ttu-id="01991-157">**DIRECTORY_NAME**의 값을 지정하지 않으면 디렉터리 이름은 null로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="01991-157">If you do not specify a value for **DIRECTORY_NAME**, then the directory name remains null.</span></span> <span data-ttu-id="01991-158">그러나 데이터베이스 수준에서 **DIRECTORY_NAME** 의 값을 지정하기 전까지는 데이터베이스에 FileTable을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="01991-158">However you cannot create FileTables in the database until you specify a value for **DIRECTORY_NAME** at the database level.</span></span>  
  
-   <span data-ttu-id="01991-159">제공하는 디렉터리 이름은 올바른 디렉터리 이름에 대한 파일 시스템 요구 사항을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-159">The directory name that you provide must comply with the requirements of the file system for a valid directory name.</span></span>  
  
-   <span data-ttu-id="01991-160">데이터베이스에 FileTable이 포함되어 있으면 **DIRECTORY_NAME** 을 다시 null 값으로 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="01991-160">When the database contains FileTables, you cannot set the **DIRECTORY_NAME** back to a null value.</span></span>  
  
-   <span data-ttu-id="01991-161">데이터베이스를 연결하거나 복원할 때 대상 인스턴스에 이미 있는 **DIRECTORY_NAME** 값이 새 데이터베이스에 있으면 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-161">When you attach or restore a database, the operation fails if the new database has a value for **DIRECTORY_NAME** that already exists in the target instance.</span></span> <span data-ttu-id="01991-162">**CREATE DATABASE FOR ATTACH** 또는 **RESTORE DATABASE** 를 호출할 때 **DIRECTORY_NAME**에 고유한 값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01991-162">Specify a unique value for **DIRECTORY_NAME** when you call **CREATE DATABASE FOR ATTACH** or **RESTORE DATABASE**.</span></span>  
  
-   <span data-ttu-id="01991-163">기존 데이터베이스를 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드할 경우 **DIRECTORY_NAME** 값은 null입니다.</span><span class="sxs-lookup"><span data-stu-id="01991-163">When you upgrade an existing database to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the value of **DIRECTORY_NAME** is null.</span></span>  
  
-   <span data-ttu-id="01991-164">데이터베이스 수준에서 비트랜잭션 액세스를 사용하거나 사용하지 않도록 설정할 때 디렉터리 이름이 지정되었는지 여부나 디렉터리 이름이 고유한지 여부는 확인되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01991-164">When you enable or disable non-transactional access at the database level, the operation does not check whether the directory name has been specified or whether it is unique.</span></span>  
  
-   <span data-ttu-id="01991-165">FileTable에 대해 사용하도록 설정된 데이터베이스를 삭제하면 해당 데이터베이스에 있는 데이터베이스 수준 디렉터리와 모든 디렉터리 구조가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="01991-165">When you drop a database that was enabled for FileTables, the database-level directory and all the directory stuctures of all the FileTables under it are removed.</span></span>  
  
  
