---
title: 데이터베이스의 크기 늘리기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], size
- increasing database size
- database size [SQL Server], increasing
- size [SQL Server], databases
ms.assetid: 14f4206d-3afa-4ba9-9849-23e81d63306d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 71dcb00b3f5525f7059fc54911baed929f763008
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742188"
---
# <a name="increase-the-size-of-a-database"></a><span data-ttu-id="82335-102">데이터베이스의 크기 늘리기</span><span class="sxs-lookup"><span data-stu-id="82335-102">Increase the Size of a Database</span></span>
  <span data-ttu-id="82335-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]의 데이터베이스 크기를 늘리는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="82335-103">This topic describes how to increase the size of a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="82335-104">기존 데이터 또는 로그 파일의 크기를 늘리거나 데이터베이스에 새 파일을 추가하여 데이터베이스를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82335-104">The database is expanded by either increasing the size of an existing data or log file or by adding a new file to the database.</span></span>  
  
 <span data-ttu-id="82335-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="82335-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="82335-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="82335-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="82335-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="82335-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="82335-108">보안</span><span class="sxs-lookup"><span data-stu-id="82335-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="82335-109">**데이터베이스의 크기를 늘리려면:**</span><span class="sxs-lookup"><span data-stu-id="82335-109">**To increase the size of a database, using:**</span></span>  
  
     [<span data-ttu-id="82335-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="82335-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="82335-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="82335-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="82335-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="82335-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="82335-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="82335-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="82335-114">BACKUP 문이 실행 중인 동안에는 파일을 추가 또는 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82335-114">You cannot add or remove a file while a BACKUP statement is running.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="82335-115">보안</span><span class="sxs-lookup"><span data-stu-id="82335-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="82335-116">권한</span><span class="sxs-lookup"><span data-stu-id="82335-116">Permissions</span></span>  
 <span data-ttu-id="82335-117">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="82335-117">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="82335-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="82335-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-increase-the-size-of-a-database"></a><span data-ttu-id="82335-119">데이터베이스의 크기를 늘리려면</span><span class="sxs-lookup"><span data-stu-id="82335-119">To increase the size of a database</span></span>  
  
1.  <span data-ttu-id="82335-120">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="82335-120">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="82335-121">**데이터베이스**를 확장하고 크기를 늘릴 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82335-121">Expand **Databases**, right-click the database to increase, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="82335-122">**데이터베이스 속성**에서 **파일** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82335-122">In **Database Properties**, select the **Files** page.</span></span>  
  
4.  <span data-ttu-id="82335-123">기존 파일의 크기를 늘리려면 파일의 **처음 크기(MB)** 열의 값을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="82335-123">To increase the size of an existing file, increase the value in the **Initial Size (MB)** column for the file.</span></span> <span data-ttu-id="82335-124">데이터베이스 크기는 최소 1MB 단위로 늘려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82335-124">You must increase the size of the database by at least 1 megabyte.</span></span>  
  
5.  <span data-ttu-id="82335-125">새 파일을 추가하여 데이터베이스 크기를 늘리려면 **추가** 를 클릭한 다음 새 파일에 대한 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="82335-125">To increase the size of the database by adding a new file, click **Add** and then enter the values for the new file.</span></span> <span data-ttu-id="82335-126">자세한 내용은 [데이터베이스에 데이터 또는 로그 파일 추가](add-data-or-log-files-to-a-database.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82335-126">For more information, see [Add Data or Log Files to a Database](add-data-or-log-files-to-a-database.md).</span></span>  
  
6.  <span data-ttu-id="82335-127">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82335-127">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="82335-128">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="82335-128">Using Transact-SQL</span></span>  
  
#### <a name="to-increase-the-size-of-a-database"></a><span data-ttu-id="82335-129">데이터베이스의 크기를 늘리려면</span><span class="sxs-lookup"><span data-stu-id="82335-129">To increase the size of a database</span></span>  
  
1.  <span data-ttu-id="82335-130">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="82335-130">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="82335-131">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82335-131">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="82335-132">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82335-132">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="82335-133">다음 예에서는 `test1dat3`파일의 크기를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="82335-133">This example increases the size of the file `test1dat3`.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase5](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase5)]  
  
 <span data-ttu-id="82335-134">더 많은 예제를 보려면 [ALTER DATABASE 파일 및 파일 그룹 옵션&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82335-134">For more examples, see [ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82335-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82335-135">See Also</span></span>  
 <span data-ttu-id="82335-136">[데이터베이스에 데이터 또는 로그 파일 추가](add-data-or-log-files-to-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="82335-136">[Add Data or Log Files to a Database](add-data-or-log-files-to-a-database.md) </span></span>  
 [<span data-ttu-id="82335-137">데이터베이스 축소</span><span class="sxs-lookup"><span data-stu-id="82335-137">Shrink a Database</span></span>](shrink-a-database.md)  
  
  
