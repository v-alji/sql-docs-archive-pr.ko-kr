---
title: 데이터베이스 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], creating
- database creation [SQL Server], SQL Server Management Studio
- creating databases
ms.assetid: 4c4beea2-6cbc-4352-9db6-49ea8130bb64
author: stevestein
ms.author: sstein
ms.openlocfilehash: fe42e394482e3abf4d87c00c6e79ee84db6ba278
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650114"
---
# <a name="create-a-database"></a><span data-ttu-id="bd750-102">데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="bd750-102">Create a Database</span></span>
  <span data-ttu-id="bd750-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 데이터베이스를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-103">This topic describes how to create a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="bd750-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="bd750-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="bd750-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="bd750-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="bd750-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="bd750-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="bd750-107">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="bd750-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="bd750-108">권장 사항</span><span class="sxs-lookup"><span data-stu-id="bd750-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="bd750-109">보안</span><span class="sxs-lookup"><span data-stu-id="bd750-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="bd750-110">**데이터베이스를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="bd750-110">**To create a database, using:**</span></span>  
  
     [<span data-ttu-id="bd750-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bd750-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="bd750-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bd750-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bd750-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="bd750-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="bd750-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="bd750-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="bd750-115">하나의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스당 최대 32,767개의 데이터베이스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-115">A maximum of 32,767 databases can be specified on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="bd750-116">필수 조건</span><span class="sxs-lookup"><span data-stu-id="bd750-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="bd750-117">CREATE DATABASE 문은 기본 트랜잭션 관리 모드인 자동 커밋 모드에서 실행해야 하며 명시적 또는 암시적 트랜잭션에서는 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-117">The CREATE DATABASE statement must run in autocommit mode (the default transaction management mode) and is not allowed in an explicit or implicit transaction.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="bd750-118">권장 사항</span><span class="sxs-lookup"><span data-stu-id="bd750-118">Recommendations</span></span>  
  
-   <span data-ttu-id="bd750-119">사용자 데이터베이스를 생성, 수정 또는 삭제할 때마다 [master](master-database.md) 데이터베이스를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-119">The [master](master-database.md) database should be backed up whenever a user database is created, modified, or dropped.</span></span>  
  
-   <span data-ttu-id="bd750-120">데이터베이스를 만들 때는 데이터베이스에서 예상되는 최대 데이터 크기를 고려하여 데이터 파일을 가능한 한 크게 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-120">When you create a database, make the data files as large as possible based on the maximum amount of data you expect in the database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bd750-121">보안</span><span class="sxs-lookup"><span data-stu-id="bd750-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bd750-122">권한</span><span class="sxs-lookup"><span data-stu-id="bd750-122">Permissions</span></span>  
 <span data-ttu-id="bd750-123">master 데이터베이스의 CREATE DATABASE 권한이 있거나 CREATE ANY DATABASE 또는 ALTER ANY DATABASE 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-123">Requires CREATE DATABASE permission in the master database, or requires CREATE ANY DATABASE, or ALTER ANY DATABASE permission.</span></span>  
  
 <span data-ttu-id="bd750-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 디스크 사용을 제어하기 위해 일반적으로 데이터베이스를 만들 수 있는 사용 권한은 일부 로그인 계정으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-124">To maintain control over disk use on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], permission to create databases is typically limited to a few login accounts.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bd750-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="bd750-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-database"></a><span data-ttu-id="bd750-126">데이터베이스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="bd750-126">To create a database</span></span>  
  
1.  <span data-ttu-id="bd750-127">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-127">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="bd750-128">**데이터베이스**를 마우스 오른쪽 단추로 클릭한 다음 **새 데이터베이스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-128">Right-click **Databases**, and then click **New Database**.</span></span>  
  
3.  <span data-ttu-id="bd750-129">**새 데이터베이스**에 데이터베이스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-129">In **New Database**, enter a database name.</span></span>  
  
4.  <span data-ttu-id="bd750-130">모든 기본값을 사용하여 데이터베이스를 만들려면 **확인**을 클릭합니다. 그렇지 않으면 다음 옵션 단계로 계속 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-130">To create the database by accepting all default values, click **OK**; otherwise, continue with the following optional steps.</span></span>  
  
5.  <span data-ttu-id="bd750-131">소유자 이름을 변경하려면 ( **…** )을 클릭하여 다른 소유자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-131">To change the owner name, click (**...**) to select another owner.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bd750-132">**부터 모든 사용자 데이터베이스에서 전체 텍스트를 사용할 수 있기 때문에** 전체 텍스트 인덱싱 사용 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]옵션이 항상 선택되어 있고 흐리게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-132">The **Use full-text indexing** option is always checked and dimmed because, beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], all user databases are full-text enabled.</span></span>  
  
6.  <span data-ttu-id="bd750-133">주 데이터 및 트랜잭션 로그 파일의 기본값을 변경하려면 **데이터베이스 파일** 표에서 해당 셀을 클릭하고 새 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-133">To change the default values of the primary data and transaction log files, in the **Database files** grid, click the appropriate cell and enter the new value.</span></span> <span data-ttu-id="bd750-134">자세한 내용은 [데이터베이스에 데이터 또는 로그 파일 추가](add-data-or-log-files-to-a-database.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd750-134">For more information, see [Add Data or Log Files to a Database](add-data-or-log-files-to-a-database.md).</span></span>  
  
7.  <span data-ttu-id="bd750-135">데이터베이스의 데이터 정렬을 변경하려면 **옵션** 페이지를 선택한 다음 목록에서 데이터 정렬을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-135">To change the collation of the database, select the **Options** page, and then select a collation from the list.</span></span>  
  
8.  <span data-ttu-id="bd750-136">복구 모델을 변경하려면 **옵션** 페이지를 선택하고 목록에서 복구 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-136">To change the recovery model, select the **Options** page and select a recovery model from the list.</span></span>  
  
9. <span data-ttu-id="bd750-137">데이터베이스 옵션을 변경하려면 **옵션** 페이지를 선택한 다음 데이터베이스 옵션을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-137">To change database options, select the **Options** page, and then modify the database options.</span></span> <span data-ttu-id="bd750-138">각 옵션에 대한 자세한 내용은 [ALTER DATABASE SET 옵션&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd750-138">For a description of each option, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
10. <span data-ttu-id="bd750-139">새 파일 그룹을 추가하려면 **파일 그룹** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-139">To add a new filegroup, click the **Filegroups** page.</span></span> <span data-ttu-id="bd750-140">**추가** 를 클릭한 다음 파일 그룹의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-140">Click **Add** and then enter the values for the filegroup.</span></span>  
  
11. <span data-ttu-id="bd750-141">데이터베이스에 확장 속성을 추가하려면 **확장 속성** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-141">To add an extended property to the database, select the **Extended Properties** page.</span></span>  
  
    1.  <span data-ttu-id="bd750-142">**이름** 열에 확장 속성의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-142">In the **Name** column, enter a name for the extended property.</span></span>  
  
    2.  <span data-ttu-id="bd750-143">**값** 열에 확장 속성 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-143">In the **Value** column, enter the extended property text.</span></span> <span data-ttu-id="bd750-144">예를 들어 데이터베이스에 대해 설명하는 하나 이상의 문을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-144">For example, enter one or more statements that describe the database.</span></span>  
  
12. <span data-ttu-id="bd750-145">데이터베이스를 만들려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-145">To create the database, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="bd750-146">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="bd750-146">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-database"></a><span data-ttu-id="bd750-147">데이터베이스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="bd750-147">To create a database</span></span>  
  
1.  <span data-ttu-id="bd750-148">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-148">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bd750-149">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bd750-150">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-150">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="bd750-151">다음 예에서는 `Sales`데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-151">This example creates the database `Sales`.</span></span> <span data-ttu-id="bd750-152">PRIMARY 키워드를 사용하지 않았으므로 첫 번째 파일(`Sales`_`dat`)이 주 파일이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-152">Because the keyword PRIMARY is not used, the first file (`Sales`_`dat`) becomes the primary file.</span></span> <span data-ttu-id="bd750-153">`Sales`\_`dat` 파일의 SIZE 매개 변수에 MB 또는 KB를 지정하지 않았으므로 기본값 MB를 사용하여 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-153">Because neither MB nor KB is specified in the SIZE parameter for the `Sales`\_`dat` file, it uses MB and is allocated in megabytes.</span></span> <span data-ttu-id="bd750-154">사용자 데이터베이스를 생성, 수정 또는 삭제할 때마다 `Sales`\_`log` 파일은 `MB` 매개 변수에 명시적으로 `SIZE` 접미사를 지정했으므로 메가바이트(MB)로 공간이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd750-154">The `Sales`\_`log` file is allocated in megabytes because the `MB` suffix is explicitly stated in the `SIZE` parameter.</span></span>  
  
```sql  
USE master ;  
GO  
CREATE DATABASE Sales  
ON   
( NAME = Sales_dat,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\saledat.mdf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 )  
LOG ON  
( NAME = Sales_log,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\salelog.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 25MB,  
    FILEGROWTH = 5MB ) ;  
GO  
```  
  
 <span data-ttu-id="bd750-155">추가 예제를 보려면 [CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd750-155">For more examples, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd750-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bd750-156">See Also</span></span>  
 <span data-ttu-id="bd750-157">[Database Files and Filegroups](database-files-and-filegroups.md) </span><span class="sxs-lookup"><span data-stu-id="bd750-157">[Database Files and Filegroups](database-files-and-filegroups.md) </span></span>  
 <span data-ttu-id="bd750-158">[데이터베이스 분리 및 연결&#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bd750-158">[Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span></span>  
 <span data-ttu-id="bd750-159">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bd750-159">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="bd750-160">데이터베이스에 데이터 또는 로그 파일 추가</span><span class="sxs-lookup"><span data-stu-id="bd750-160">Add Data or Log Files to a Database</span></span>](add-data-or-log-files-to-a-database.md)  
  
  
