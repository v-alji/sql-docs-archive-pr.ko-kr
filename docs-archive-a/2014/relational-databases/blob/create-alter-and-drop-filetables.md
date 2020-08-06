---
title: FileTable 만들기, 변경 및 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], altering
- FileTables [SQL Server], dropping
- FileTables [SQL Server], creating
ms.assetid: 47d69e37-8778-4630-809b-2261b5c41c2c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3a10e6333f6dd38a850a832b82a7cb7a0e0bf698
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647065"
---
# <a name="create-alter-and-drop-filetables"></a><span data-ttu-id="d7ddf-102">FileTable 만들기, 변경 및 삭제</span><span class="sxs-lookup"><span data-stu-id="d7ddf-102">Create, Alter, and Drop FileTables</span></span>
  <span data-ttu-id="d7ddf-103">새 FileTable을 만들거나 기존 FileTable을 변경 또는 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-103">Describes how to create a new FileTable, or alter or drop an existing FileTable.</span></span>  
  
##  <a name="creating-a-filetable"></a><a name="BasicsCreate"></a> <span data-ttu-id="d7ddf-104">FileTable 만들기</span><span class="sxs-lookup"><span data-stu-id="d7ddf-104">Creating a FileTable</span></span>  
 <span data-ttu-id="d7ddf-105">FileTable은 미리 정의된 고정 스키마가 있는 특수한 사용자 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-105">A FileTable is a specialized user table that has a pre-defined and fixed schema.</span></span> <span data-ttu-id="d7ddf-106">이 스키마는 FILESTREAM 데이터, 파일/디렉터리 정보 및 파일 특성을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-106">This schema stores FILESTREAM data, file and directory information, and file attributes.</span></span> <span data-ttu-id="d7ddf-107">FileTable 스키마에 대한 자세한 내용은 [FileTable Schema](filetable-schema.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-107">For information about the FileTable schema, see [FileTable Schema](filetable-schema.md).</span></span>  
  
 <span data-ttu-id="d7ddf-108">Transact-SQL 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 새 FileTable을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-108">You can create a new FileTable by using Transact-SQL or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="d7ddf-109">FileTable에는 고정 스키마가 있으므로 열 목록을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-109">Since a FileTable has a fixed schema, you do not have to specify a list of columns.</span></span> <span data-ttu-id="d7ddf-110">FileTable을 만드는 간단한 구문에서 다음을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-110">The simple syntax for creating a FileTable lets you specify:</span></span>  
  
-   <span data-ttu-id="d7ddf-111">디렉터리 이름.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-111">A directory name.</span></span> <span data-ttu-id="d7ddf-112">FileTable 폴더 계층 구조에서 이 테이블 수준 디렉터리는 데이터베이스 수준에서 지정된 데이터베이스 디렉터리의 자식이 되고 테이블에 저장된 파일 또는 디렉터리의 부모가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-112">In the FileTable folder hierarchy, this table-level directory becomes the child of the database directory specified at the database level, and the parent of the files or directories stored in the table.</span></span>  
  
-   <span data-ttu-id="d7ddf-113">FileTable의 **Name** 열에 있는 파일 이름에 사용할 데이터 정렬의 이름</span><span class="sxs-lookup"><span data-stu-id="d7ddf-113">The name of the collation to be used for file names in the **Name** column of the FileTable.</span></span>  
  
-   <span data-ttu-id="d7ddf-114">자동으로 만들어지는 UNIQUE 제약 조건 및 세 가지 기본 키에 사용할 이름</span><span class="sxs-lookup"><span data-stu-id="d7ddf-114">The names to be used for the 3 primary key and unique constraints that are automatically created.</span></span>  
  
###  <a name="how-to-create-a-filetable"></a><a name="HowToCreate"></a> <span data-ttu-id="d7ddf-115">방법: FileTable 만들기</span><span class="sxs-lookup"><span data-stu-id="d7ddf-115">How To: Create a FileTable</span></span>  
 <span data-ttu-id="d7ddf-116">**Transact-SQL을 사용하여 FileTable 만들기**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-116">**Create a FileTable by Using Transact-SQL**</span></span>  
 <span data-ttu-id="d7ddf-117">**AS FileTable** 옵션이 포함된 [CREATE TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) 문을 호출하여 FileTable을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-117">Create a FileTable by calling the [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) statement with the **AS FileTable** option.</span></span> <span data-ttu-id="d7ddf-118">FileTable에는 고정 스키마가 있으므로 열 목록을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-118">Since a FileTable has a fixed schema, you do not have to specify a list of columns.</span></span> <span data-ttu-id="d7ddf-119">새 FileTable에 대해 다음 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-119">You can specify the following settings for the new FileTable:</span></span>  
  
1.  <span data-ttu-id="d7ddf-120">**FILETABLE_DIRECTORY**.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-120">**FILETABLE_DIRECTORY**.</span></span> <span data-ttu-id="d7ddf-121">FileTable에 저장된 모든 파일 및 디렉터리에 대한 루트 디렉터리 역할을 하는 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-121">Specifies the directory that serves as the root directory for all the files and directories stored in the FileTable.</span></span> <span data-ttu-id="d7ddf-122">이 이름은 데이터베이스의 모든 FileTable 디렉터리 이름 중에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-122">This name should be unique among all the FileTable directory names in the database.</span></span> <span data-ttu-id="d7ddf-123">고유성 비교는 현재 데이터 정렬 설정과 관계없이 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-123">Comparison for uniqueness is case-insensitive, regardless of the current collation settings.</span></span>  
  
    -   <span data-ttu-id="d7ddf-124">이 값의 데이터 형식은 **nvarchar(255)** 이며 **Latin1_General_CI_AS_KS_WS**의 고정된 데이터 정렬을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-124">This value has a data type of **nvarchar(255)** and uses a fixed collation of **Latin1_General_CI_AS_KS_WS**.</span></span>  
  
    -   <span data-ttu-id="d7ddf-125">제공하는 디렉터리 이름은 올바른 디렉터리 이름에 대한 파일 시스템 요구 사항을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-125">The directory name that you provide must comply with the requirements of the file system for a valid directory name.</span></span>  
  
    -   <span data-ttu-id="d7ddf-126">이 이름은 데이터베이스의 모든 FileTable 디렉터리 이름 중에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-126">This name should be unique among all the FileTable directory names in the database.</span></span> <span data-ttu-id="d7ddf-127">고유성 비교는 현재 데이터 정렬 설정과 관계없이 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-127">Comparison for uniqueness is case-insensitive, regardless of the current collation settings.</span></span>  
  
    -   <span data-ttu-id="d7ddf-128">FileTable 만들 때 디렉터리 이름을 제공하지 않은 경우 FileTable의 이름이 디렉터리 이름으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-128">If you do not provide a directory name when you create the FileTable, then the name of the FileTable itself is used as the directory name.</span></span>  
  
2.  <span data-ttu-id="d7ddf-129">**FILETABLE_COLLATE_FILENAME**.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-129">**FILETABLE_COLLATE_FILENAME**.</span></span> <span data-ttu-id="d7ddf-130">FileTable의 **Name** 열에 적용할 데이터 정렬의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-130">Specifies the name of the collation to be applied to the **Name** column in the FileTable.</span></span>  
  
    1.  <span data-ttu-id="d7ddf-131">지정한 데이터 정렬은 Windows 파일 이름 의미 체계를 따르도록 **대/소문자를 구분하지 않아야** 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-131">The specified collation must be **case-insensitive** to comply with Windows file naming semantics.</span></span>  
  
    2.  <span data-ttu-id="d7ddf-132">**FILETABLE_COLLATE_FILENAME**값을 제공하지 않거나 **database_default**를 지정한 경우 열은 현재 데이터베이스의 데이터 정렬을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-132">If you do not provide a value for **FILETABLE_COLLATE_FILENAME**, or you specify **database_default**, the column inherits the collation of the current database.</span></span> <span data-ttu-id="d7ddf-133">현재 데이터베이스 데이터 정렬이 대/소문자를 구분하면 오류가 발생하고 **CREATE TABLE** 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-133">If the current database collation is case-sensitive, an error is raised and the **CREATE TABLE** operation fails.</span></span>  
  
3.  <span data-ttu-id="d7ddf-134">자동으로 만들어지는 UNIQUE 제약 조건 및 세 가지 기본 키에 사용할 이름도 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-134">You can also specify the names to be used for the 3 primary key and unique constraints that are automatically created.</span></span> <span data-ttu-id="d7ddf-135">이름을 입력하지 않으면 시스템이 이 항목의 뒷부분에 나와 있는 이름을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-135">If you do not provide names, then the system generates names as described later in this topic.</span></span>  
  
    -   <span data-ttu-id="d7ddf-136">**FILETABLE_PRIMARY_KEY_CONSTRAINT_NAME**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-136">**FILETABLE_PRIMARY_KEY_CONSTRAINT_NAME**</span></span>  
  
    -   <span data-ttu-id="d7ddf-137">**FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-137">**FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME**</span></span>  
  
    -   <span data-ttu-id="d7ddf-138">**FILETABLE_FULLPATH_UNIQUE_CONSTRAINT_NAME**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-138">**FILETABLE_FULLPATH_UNIQUE_CONSTRAINT_NAME**</span></span>  
  
 <span data-ttu-id="d7ddf-139">**예**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-139">**Examples**</span></span>  
  
 <span data-ttu-id="d7ddf-140">다음 예제에서는 새 FileTable을 만들고 **FILETABLE_DIRECTORY** 및 **FILETABLE_COLLATE_FILENAME**둘 다에 대해 사용자 정의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-140">The following example creates a new FileTable and specifies user-defined values for both **FILETABLE_DIRECTORY** and **FILETABLE_COLLATE_FILENAME**.</span></span>  
  
```sql  
CREATE TABLE DocumentStore AS FileTable  
    WITH (   
          FileTable_Directory = 'DocumentTable',  
          FileTable_Collate_Filename = database_default  
         );  
GO  
```  
  
 <span data-ttu-id="d7ddf-141">또한 다음 예에서는 새로운 Filetable을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-141">The following example also creates a new FileTable.</span></span> <span data-ttu-id="d7ddf-142">사용자 정의 값이 지원되지 않기 때문에 **FILETABLE_DIRECTORY** 값은 FileTable 값이 되고, **FILETABLE_COLLATE_FILENAME** 값은 database_default가 되며, 기본 키 및 UNIQUE 제약 조건에는 시스템에서 생성한 이름이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-142">Since user-defined values are not specified, the value of **FILETABLE_DIRECTORY** becomes the name of the FileTable, the value of **FILETABLE_COLLATE_FILENAME** becomes database_default, and the primary key and unique contraints receive system-generated names.</span></span>  
  
```sql  
CREATE TABLE DocumentStore AS FileTable;  
GO  
```  
  
 <span data-ttu-id="d7ddf-143">**SQL Server Management Studio를 사용하여 FileTable 만들기**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-143">**Create a FileTable by Using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="d7ddf-144">개체 탐색기에서 선택한 데이터베이스의 개체를 확장하고 **테이블** 폴더에서 마우스 오른쪽 단추를 클릭한 다음 **새 FileTable**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-144">In Object Explorer, expand the objects under the selected database, then right-click on the **Tables** folder, and then select **New FileTable**.</span></span>  
  
 <span data-ttu-id="d7ddf-145">이 옵션은 Transact-SQL 스크립트 템플릿이 포함된 새 스크립트 창을 엽니다. 이 템플릿을 사용자 지정하여 FileTable을 만드는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-145">This option opens a new script window which contains a Transact-SQL script template that you can customize and run to create a FileTable.</span></span> <span data-ttu-id="d7ddf-146">**쿼리** 메뉴에서 **템플릿 매개 변수 값 지정** 옵션을 사용하여 스크립트를 쉽게 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-146">Use the **Specify Values for Template Parameters** option on the **Query** menu to customize the script easily.</span></span>  
  
###  <a name="requirements-and-restrictions-for-creating-a-filetable"></a><a name="ReqCreate"></a> <span data-ttu-id="d7ddf-147">FileTable 만들기에 대한 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="d7ddf-147">Requirements and Restrictions for Creating a FileTable</span></span>  
  
-   <span data-ttu-id="d7ddf-148">기존 테이블을 변경하여 FileTable로 변환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-148">You cannot alter an existing table to convert it into a FileTable.</span></span>  
  
-   <span data-ttu-id="d7ddf-149">데이터베이스 수준에서 이전에 지정된 디렉터리에 null이 아닌 값이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-149">The parent directory previously specified at the database level must have a non-null value.</span></span> <span data-ttu-id="d7ddf-150">데이터베이스 수준 디렉터리를 지정하는 방법에 대한 자세한 내용은 [FileTable의 필수 구성 요소를 사용하도록 설정](enable-the-prerequisites-for-filetable.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-150">For information about specifying the database-level directory, see [Enable the Prerequisites for FileTable](enable-the-prerequisites-for-filetable.md).</span></span>  
  
-   <span data-ttu-id="d7ddf-151">FileTable에는 FILESTREAM 열이 포함되어 있으므로 FileTable에는 유효한 FILESTREAM 파일 그룹이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-151">A FileTable requires a valid FILESTREAM filegroup, since a FileTable contains a FILESTREAM column.</span></span> <span data-ttu-id="d7ddf-152">필요에 따라 **CREATE TABLE** 명령의 일부로 유효한 FILESTREAM 파일 그룹을 지정하여 FileTable을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-152">You can optionally specify a valid FILESTREAM filegroup as part of the **CREATE TABLE** command for creating a FileTable.</span></span> <span data-ttu-id="d7ddf-153">파일 그룹을 지정하지 않으면 FileTable에는 데이터베이스의 기본 FILESTREAM 파일 그룹이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-153">If you do not specify a filegroup, then the FileTable uses the default FILESTREAM filegroup for the database.</span></span> <span data-ttu-id="d7ddf-154">데이터베이스에 FILESTREAM 파일 그룹이 없으면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-154">If the database does not have a FILESTREAM filegroup, then an error is raised.</span></span>  
  
-   <span data-ttu-id="d7ddf-155">**CREATE TABLE...AS FILETABLE** 문의 일부로 테이블 제약 조건을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-155">You cannot create a table constraint as part of a **CREATE TABLE...AS FILETABLE** statement.</span></span> <span data-ttu-id="d7ddf-156">그러나 **ALTER TABLE** 문을 사용하여 나중에 제약 조건을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-156">However you can add the constraint later by using an **ALTER TABLE** statement.</span></span>  
  
-   <span data-ttu-id="d7ddf-157">**tempdb** 데이터베이스나 다른 시스템 데이터베이스에는 FileTable을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-157">You cannot create a FileTable in the **tempdb** database or in any of the other system databases.</span></span>  
  
-   <span data-ttu-id="d7ddf-158">FileTable을 임시 테이블로 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-158">You cannot create a FileTable as a temporary table.</span></span>  
  
##  <a name="altering-a-filetable"></a><a name="BasicsAlter"></a> <span data-ttu-id="d7ddf-159">FileTable 변경</span><span class="sxs-lookup"><span data-stu-id="d7ddf-159">Altering a FileTable</span></span>  
 <span data-ttu-id="d7ddf-160">FileTable에는 미리 정의된 고정 스키마가 있으므로 해당 열을 추가하거나 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-160">Since a FileTable has a pre-defined and fixed schema, you cannot add or change its columns.</span></span> <span data-ttu-id="d7ddf-161">그러나 FileTable에 사용자 지정 인덱스, 트리거, 제약 조건 및 다른 옵션을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-161">However, you can add custom indexes, triggers, constraints, and other options to a FileTable.</span></span>  
  
 <span data-ttu-id="d7ddf-162">시스템 정의 제약 조건을 포함하여 ALTER TABLE 문을 사용하여 FileTable 네임스페이스를 사용하거나 사용하지 않도록 설정하는 방법은 [FileTable 관리](manage-filetables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-162">For information about using the ALTER TABLE statement to enable or disable the FileTable namespace, including the system-defined constraints, see [Manage FileTables](manage-filetables.md).</span></span>  
  
###  <a name="how-to-change-the-directory-for-a-filetable"></a><a name="HowToChange"></a> <span data-ttu-id="d7ddf-163">방법: FileTable의 디렉터리 변경</span><span class="sxs-lookup"><span data-stu-id="d7ddf-163">How To: Change the Directory for a FileTable</span></span>  
 <span data-ttu-id="d7ddf-164">**Transact-SQL을 사용하여 FileTable의 디렉터리 변경**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-164">**Change the Directory for a FileTable by Using Transact-SQL**</span></span>  
 <span data-ttu-id="d7ddf-165">ALTER TABLE 문을 호출하고 **FILETABLE_DIRECTORY** SET 옵션에 유효한 새 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-165">Call the ALTER TABLE statement and provide a valid new value for the **FILETABLE_DIRECTORY** SET option.</span></span>  
  
 <span data-ttu-id="d7ddf-166">**예제**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-166">**Example**</span></span>  
  
```sql  
ALTER TABLE filetable_name  
    SET ( FILETABLE_DIRECTORY = N'directory_name' );  
GO  
```  
  
 <span data-ttu-id="d7ddf-167">**SQL Server Management Studio를 사용하여 FileTable의 디렉터리 변경**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-167">**Change the Directory for a FileTable by Using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="d7ddf-168">개체 탐색기에서 FileTable을 마우스 오른쪽 단추로 클릭하고 **속성** 을 선택하여 **테이블 속성** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-168">In Object Explorer, right-click on the FileTable and select **Properties** to open the **Table Properties** dialog box.</span></span> <span data-ttu-id="d7ddf-169">**FileTable** 페이지에서 **FileTable 디렉터리 이름**의 새 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-169">On the **FileTable** page, enter a new value for **FileTable directory name**.</span></span>  
  
###  <a name="requirements-and-restrictions-for-altering-a-filetable"></a><a name="ReqAlter"></a> <span data-ttu-id="d7ddf-170">FileTable 변경에 대한 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="d7ddf-170">Requirements and Restrictions for Altering a FileTable</span></span>  
  
-   <span data-ttu-id="d7ddf-171">**FILETABLE_COLLATE_FILENAME**값은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-171">You cannot alter the value of **FILETABLE_COLLATE_FILENAME**.</span></span>  
  
-   <span data-ttu-id="d7ddf-172">FileTable의 시스템 정의 열은 변경, 삭제하거나 사용하지 않도록 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-172">You cannot change, drop, or disable the system-defined columns of a FileTable.</span></span>  
  
-   <span data-ttu-id="d7ddf-173">FileTable에 새 사용자 열, 계산 열 또는 지속형 계산 열을 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-173">You cannot add new user columns, computed columns, or persisted computed columns to a FileTable.</span></span>  
  
##  <a name="dropping-a-filetable"></a><a name="BasicsDrop"></a> <span data-ttu-id="d7ddf-174">FileTable 삭제</span><span class="sxs-lookup"><span data-stu-id="d7ddf-174">Dropping a FileTable</span></span>  
 <span data-ttu-id="d7ddf-175">[DROP TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) 문의 일반 구문을 사용하여 FileTable을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-175">You can drop a FileTable by using the ordinary syntax for the [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="d7ddf-176">Filetable를 삭제하면 다음 개체도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-176">When you drop a FileTable, the following objects are also dropped:</span></span>  
  
-   <span data-ttu-id="d7ddf-177">FileTable의 모든 열과 테이블에 연결된 모든 개체(예: 인덱스, 제약 조건 및 트리거)도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-177">All the columns of the FileTable and all the objects associated with the table, such as indexes, constraints, and triggers, are also dropped.</span></span>  
  
-   <span data-ttu-id="d7ddf-178">포함된 FileTable 디렉터리 및 하위 디렉터리가 데이터베이스의 FILESTREAM 파일 및 디렉터리 계층 구조에서 사라집니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-178">The FileTable directory and the sub-directories that it contained disappear from the FILESTREAM file and directory hierarchy of the database.</span></span>  
  
 <span data-ttu-id="d7ddf-179">FileTable의 파일 네임스페이스에 열려 있는 파일 핸들이 있는 경우 DROP TABLE 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-179">The DROP TABLE command fails if there are open file handles in the FileTable's file namespace.</span></span> <span data-ttu-id="d7ddf-180">열려 있는 핸들을 닫는 방법에 대한 자세한 내용은 [FileTable 관리](manage-filetables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-180">For information about closing open handles, see [Manage FileTables](manage-filetables.md).</span></span>  
  
##  <a name="other-database-objects-are-created-when-you-create-a-filetable"></a><a name="BasicsOtherObjects"></a> <span data-ttu-id="d7ddf-181">FileTable을 만들 때 생성되는 다른 데이터베이스 개체</span><span class="sxs-lookup"><span data-stu-id="d7ddf-181">Other Database Objects Are Created When You Create a FileTable</span></span>  
 <span data-ttu-id="d7ddf-182">새 FileTable을 만들면 일부 시스템 정의 인덱스 및 제약 조건도 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-182">When you create a new FileTable, some system-defined indexes and constraints are also created.</span></span> <span data-ttu-id="d7ddf-183">이러한 개체는 변경하거나 삭제할 수 없으며, FileTable 자체가 삭제된 경우에만 사라집니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-183">You cannot alter or drop these objects; they disappear only when the FileTable itself is dropped.</span></span> <span data-ttu-id="d7ddf-184">이러한 개체의 목록을 보려면 카탈로그 뷰 [sys.filetable_system_defined_objects&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql)를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-184">To see the list of these objects, query the catalog view [sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql).</span></span>  
  
```sql  
--View all objects for all filetables, unsorted  
SELECT * FROM sys.filetable_system_defined_objects;  
GO  
  
--View sorted list with friendly names  
SELECT OBJECT_NAME(parent_object_id) AS 'FileTable', OBJECT_NAME(object_id) AS 'System-defined Object'  
    FROM sys.filetable_system_defined_objects  
    ORDER BY FileTable, 'System-defined Object';  
GO  
```  
  
 <span data-ttu-id="d7ddf-185">**새 FileTable을 만들 때 생성되는 인덱스**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-185">**Indexes that are created when you create a new FileTable**</span></span>  
 <span data-ttu-id="d7ddf-186">새 FileTable을 만들면 다음과 같은 시스템 정의 인덱스도 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-186">When you create a new FileTable, the following system-defined indexes are also created:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d7ddf-187">**열**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-187">**Columns**</span></span>|<span data-ttu-id="d7ddf-188">**인덱스 유형**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-188">**Index type**</span></span>|  
|<span data-ttu-id="d7ddf-189">[path_locator] ASC</span><span class="sxs-lookup"><span data-stu-id="d7ddf-189">[path_locator] ASC</span></span>|<span data-ttu-id="d7ddf-190">기본 키, 비클러스터형</span><span class="sxs-lookup"><span data-stu-id="d7ddf-190">Primary Key, nonclustered</span></span>|  
|<span data-ttu-id="d7ddf-191">[parent_path_locator] ASC,</span><span class="sxs-lookup"><span data-stu-id="d7ddf-191">[parent_path_locator] ASC,</span></span><br /><br /> <span data-ttu-id="d7ddf-192">[name] ASC</span><span class="sxs-lookup"><span data-stu-id="d7ddf-192">[name] ASC</span></span>|<span data-ttu-id="d7ddf-193">고유, 비클러스터형</span><span class="sxs-lookup"><span data-stu-id="d7ddf-193">Unique, nonclustered</span></span>|  
|<span data-ttu-id="d7ddf-194">[stream_id] ASC</span><span class="sxs-lookup"><span data-stu-id="d7ddf-194">[stream_id] ASC</span></span>|<span data-ttu-id="d7ddf-195">고유, 비클러스터형</span><span class="sxs-lookup"><span data-stu-id="d7ddf-195">Unique, nonclustered</span></span>|  
  
 <span data-ttu-id="d7ddf-196">**새 FileTable을 만들 때 생성되는 제약 조건**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-196">**Constraints that are created when you create a new FileTable**</span></span>  
 <span data-ttu-id="d7ddf-197">새 FileTable을 만들면 다음과 같은 시스템 정의 제약 조건도 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-197">When you create a new FileTable, the following system-defined constraints are also created:</span></span>  
  
|<span data-ttu-id="d7ddf-198">제약 조건</span><span class="sxs-lookup"><span data-stu-id="d7ddf-198">Constraints</span></span>|<span data-ttu-id="d7ddf-199">적용</span><span class="sxs-lookup"><span data-stu-id="d7ddf-199">Enforces</span></span>|  
|-----------------|--------------|  
|<span data-ttu-id="d7ddf-200">다음 열에 대한 기본 제약 조건:</span><span class="sxs-lookup"><span data-stu-id="d7ddf-200">Default constraints on the following columns:</span></span><br /><br /> <span data-ttu-id="d7ddf-201">**creation_time**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-201">**creation_time**</span></span> <br /> <span data-ttu-id="d7ddf-202">**is_archive**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-202">**is_archive**</span></span> <br /> <span data-ttu-id="d7ddf-203">**is_directory**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-203">**is_directory**</span></span> <br /> <span data-ttu-id="d7ddf-204">**is_hidden**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-204">**is_hidden**</span></span> <br /> <span data-ttu-id="d7ddf-205">**is_offline**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-205">**is_offline**</span></span> <br /> <span data-ttu-id="d7ddf-206">**is_readonly**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-206">**is_readonly**</span></span> <br /> <span data-ttu-id="d7ddf-207">**is_system**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-207">**is_system**</span></span> <br /> <span data-ttu-id="d7ddf-208">**is_temporary**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-208">**is_temporary**</span></span> <br /> <span data-ttu-id="d7ddf-209">**last_access_time**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-209">**last_access_time**</span></span> <br /> <span data-ttu-id="d7ddf-210">**last_write_time**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-210">**last_write_time**</span></span> <br /> <span data-ttu-id="d7ddf-211">**path_locator**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-211">**path_locator**</span></span> <br /> <span data-ttu-id="d7ddf-212">**stream_id**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-212">**stream_id**</span></span>|<span data-ttu-id="d7ddf-213">시스템 정의 기본 제약 조건이 지정된 열에 기본값을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-213">The system-defined default constraints enforce default values for the specified columns.</span></span>|  
|<span data-ttu-id="d7ddf-214">CHECK 제약 조건</span><span class="sxs-lookup"><span data-stu-id="d7ddf-214">Check constraints</span></span>|<span data-ttu-id="d7ddf-215">시스템 정의 CHECK 제약 조건이 다음 요구 사항을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-215">The system-defined check constraints enforce the following requirements:</span></span><br /><br /> <span data-ttu-id="d7ddf-216">유효한 파일 이름</span><span class="sxs-lookup"><span data-stu-id="d7ddf-216">Valid filenames.</span></span><br /><br /> <span data-ttu-id="d7ddf-217">유효한 파일 특성</span><span class="sxs-lookup"><span data-stu-id="d7ddf-217">Valid file attributes.</span></span><br /><br /> <span data-ttu-id="d7ddf-218">부모 개체는 디렉터리여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-218">Parent object must be a directory.</span></span><br /><br /> <span data-ttu-id="d7ddf-219">파일 조작 중에는 네임스페이스 계층 구조가 잠깁니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-219">Namespace hierarchy is locked during file manipulation.</span></span>|  
  
 <span data-ttu-id="d7ddf-220">**시스템 정의 제약 조건에 대한 명명 규칙**</span><span class="sxs-lookup"><span data-stu-id="d7ddf-220">**Naming convention for the system-defined constraints**</span></span>  
 <span data-ttu-id="d7ddf-221">위에서 설명한 시스템 정의 제약 조건은 **\<constraintType>_\<tablename>[\_\<columnname>]\_\<uniquifier>** 형식으로 명명되며 여기서</span><span class="sxs-lookup"><span data-stu-id="d7ddf-221">The system-defined constraints described above are named in the format **\<constraintType>_\<tablename>[\_\<columnname>]\_\<uniquifier>** where:</span></span>  
  
-   <span data-ttu-id="d7ddf-222">*<constraint_type>* 은 CK(확인 제약 조건), DF(기본 제약 조건), FK(외래 키), PK(기본 키) 또는 UQ(고유 제약 조건)입니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-222">*<constraint_type>* is CK (check constraint), DF (default constraint), FK (foreign key), PK (primary key), or UQ (unique constraint).</span></span>  
  
-   <span data-ttu-id="d7ddf-223">*\<uniquifier>* 는 이름을 고유하게 만드는 시스템 생성 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-223">*\<uniquifier>* is a system-generated string to make the name unique.</span></span> <span data-ttu-id="d7ddf-224">이 문자열은 FileTable 이름 및 고유 식별자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ddf-224">This string may contain the FileTable name and a unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7ddf-225">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d7ddf-225">See Also</span></span>  
 [<span data-ttu-id="d7ddf-226">FileTable 관리</span><span class="sxs-lookup"><span data-stu-id="d7ddf-226">Manage FileTables</span></span>](manage-filetables.md)  
  
  
