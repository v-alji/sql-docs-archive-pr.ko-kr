---
title: 데이터베이스에 데이터 또는 로그 파일 추가 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], files
- adding data files
- adding files
- adding log files
- file additions [SQL Server], steps
- files [SQL Server], adding
- data additions [SQL Server]
ms.assetid: 8ead516a-1334-4f40-84b2-509d0a8ffa45
author: stevestein
ms.author: sstein
ms.openlocfilehash: f72e00f9dab422652237b4b85579c544d0cda9fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742239"
---
# <a name="add-data-or-log-files-to-a-database"></a><span data-ttu-id="00960-102">데이터베이스에 데이터 또는 로그 파일 추가</span><span class="sxs-lookup"><span data-stu-id="00960-102">Add Data or Log Files to a Database</span></span>
  <span data-ttu-id="00960-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]의 데이터베이스에 데이터 또는 로그 파일을 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-103">This topic describes how to add data or log files to a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="00960-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="00960-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="00960-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="00960-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="00960-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="00960-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="00960-107">보안</span><span class="sxs-lookup"><span data-stu-id="00960-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="00960-108">**데이터베이스에 데이터 또는 로그 파일을 추가하려면:**</span><span class="sxs-lookup"><span data-stu-id="00960-108">**To add data or log files to a database, using:**</span></span>  
  
     [<span data-ttu-id="00960-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="00960-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="00960-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="00960-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="00960-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="00960-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="00960-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="00960-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="00960-113">BACKUP 문이 실행 중인 동안에는 파일을 추가 또는 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="00960-113">You cannot add or remove a file while a BACKUP statement is running.</span></span>  
  
-   <span data-ttu-id="00960-114">각 데이터베이스에 최대 32,767개의 파일과 32,767개의 파일 그룹을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00960-114">A maximum of 32,767 files and 32,767 filegroups can be specified for each database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="00960-115">보안</span><span class="sxs-lookup"><span data-stu-id="00960-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="00960-116">권한</span><span class="sxs-lookup"><span data-stu-id="00960-116">Permissions</span></span>  
 <span data-ttu-id="00960-117">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-117">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="00960-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="00960-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-add-data-or-log-files-to-a-database"></a><span data-ttu-id="00960-119">데이터베이스에 데이터 또는 로그 파일을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="00960-119">To add data or log files to a database</span></span>  
  
1.  <span data-ttu-id="00960-120">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-120">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="00960-121">**데이터베이스**를 확장하고 파일을 추가할 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-121">Expand **Databases**, right-click the database from which to add the files, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="00960-122">**데이터베이스 속성** 대화 상자에서 **파일** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-122">In the **Database Properties** dialog box, select the **Files** page.</span></span>  
  
4.  <span data-ttu-id="00960-123">데이터 또는 트랜잭션 로그 파일을 추가하려면 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-123">To add a data or transaction log file, click **Add**.</span></span>  
  
5.  <span data-ttu-id="00960-124">**데이터베이스 파일** 표에서 파일의 논리적 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-124">In the **Database files** grid, enter a logical name for the file.</span></span> <span data-ttu-id="00960-125">파일 이름은 데이터베이스 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-125">The file name must be unique within the database.</span></span>  
  
6.  <span data-ttu-id="00960-126">데이터 또는 로그 중에서 원하는 파일 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-126">Select the file type, data or log.</span></span>  
  
7.  <span data-ttu-id="00960-127">데이터 파일을 선택한 경우 파일을 포함할 파일 그룹을 목록에서 선택하거나 **\<new filegroup>** 을 선택하여 새 파일 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="00960-127">For a data file, select the filegroup in which the file should be included from the list, or select **\<new filegroup>** to create a new filegroup.</span></span> <span data-ttu-id="00960-128">트랜잭션 로그는 파일 그룹에 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="00960-128">Transaction logs cannot be put in filegroups.</span></span>  
  
8.  <span data-ttu-id="00960-129">파일의 처음 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-129">Specify the initial size of the file.</span></span> <span data-ttu-id="00960-130">데이터베이스에서 예상되는 최대 데이터 양을 고려하여 데이터 파일의 크기를 최대한 크게 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-130">Make the data file as large as possible, based on the maximum amount of data you expect in the database.</span></span>  
  
9. <span data-ttu-id="00960-131">파일 증가 방법을 지정하려면 **자동 증가** 열에서 ( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-131">To specify how the file should grow, click (**...**) in the **Autogrowth** column.</span></span> <span data-ttu-id="00960-132">다음 옵션 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-132">Select from the following options:</span></span>  
  
    1.  <span data-ttu-id="00960-133">현재 선택한 파일이 데이터 공간이 추가로 필요할 때마다 증가되도록 하려면 **자동 증가 사용** 확인란을 선택하고 다음 옵션 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-133">To allow for the currently selected file to grow as more data space is required, select the **Enable Autogrowth** check box and then select from the following options:</span></span>  
  
    2.  <span data-ttu-id="00960-134">파일이 고정된 증가분만큼 증가하도록 지정하려면 **MB 단위로** 를 선택하고 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-134">To specify that the file should grow by fixed increments, select **In Megabytes** and specify a value.</span></span>  
  
    3.  <span data-ttu-id="00960-135">파일이 현재 파일 크기의 비율에 따라 증가하도록 지정하려면 **백분율 단위로** 를 선택하고 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-135">To specify that the file should grow by a percentage of the current file size, select **In Percent** and specify a value.</span></span>  
  
10. <span data-ttu-id="00960-136">최대 파일 크기를 제한하려면 다음 옵션 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-136">To specify the maximum file size limit, select from the following options:</span></span>  
  
    1.  <span data-ttu-id="00960-137">파일이 증가할 수 있는 최대 크기를 지정하려면 **제한된 파일 증가(MB)** 를 선택하고 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-137">To specify the maximum size the file should be able to grow to, select **Restricted File Growth (MB)** and specify a value.</span></span>  
  
    2.  <span data-ttu-id="00960-138">파일이 필요에 따라 무제한 증가하도록 하려면 **파일 무제한 증가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-138">To allow for the file to grow as much as needed, select **Unrestricted File Growth**.</span></span>  
  
    3.  <span data-ttu-id="00960-139">파일이 증가되지 않도록 하려면 **자동 증가 사용** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-139">To prevent the file from growing, clear the **Enable Autogrowth** check box.</span></span> <span data-ttu-id="00960-140">**처음 크기(MB)** 열에 지정된 값에 도달하면 파일 크기가 더 이상 증가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00960-140">The size of the file will not grow beyond the value specified in the **Initial Size (MB)** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="00960-141">데이터베이스 최대 크기는 사용 가능한 디스크 공간 크기에 따라 결정되며 라이선스 제한은 사용 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 버전에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="00960-141">The maximum database size is determined by the amount of disk space available and the licensing limits determined by the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you are using.</span></span>  
  
11. <span data-ttu-id="00960-142">파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-142">Specify the path for the file location.</span></span> <span data-ttu-id="00960-143">지정한 경로가 있어야 파일을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00960-143">The specified path must exist before adding the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="00960-144">기본적으로 데이터와 트랜잭션 로그는 단일 디스크 시스템에 맞게 동일한 드라이브와 경로에 배치되지만 프로덕션 환경에서는 적절하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00960-144">By default, the data and transaction logs are put on the same drive and path to accommodate single-disk systems, but may not be optimal for production environments.</span></span> <span data-ttu-id="00960-145">자세한 내용은 [Database Files and Filegroups](database-files-and-filegroups.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00960-145">For more information, see [Database Files and Filegroups](database-files-and-filegroups.md).</span></span>  
  
12. <span data-ttu-id="00960-146">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-146">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="00960-147">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="00960-147">Using Transact-SQL</span></span>  
  
#### <a name="to-add-data-or-log-files-to-a-database"></a><span data-ttu-id="00960-148">데이터베이스에 데이터 또는 로그 파일을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="00960-148">To add data or log files to a database</span></span>  
  
1.  <span data-ttu-id="00960-149">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-149">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="00960-150">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-150">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="00960-151">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-151">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="00960-152">이 예에서는 데이터베이스에 두 개의 파일이 포함된 파일 그룹을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-152">The example adds a filegroup with two files to a database.</span></span> <span data-ttu-id="00960-153">이 예에서는 `Test1FG1` 데이터베이스에 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 파일 그룹을 만들고 이 파일 그룹에 두 개의 5MB 파일을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="00960-153">The example creates the filegroup `Test1FG1` in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database and adds two 5-MB files to the filegroup.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase2](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase2)]  
  
 <span data-ttu-id="00960-154">더 많은 예제를 보려면 [ALTER DATABASE 파일 및 파일 그룹 옵션&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00960-154">For more examples, see [ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00960-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="00960-155">See Also</span></span>  
 <span data-ttu-id="00960-156">[Database Files and Filegroups](database-files-and-filegroups.md) </span><span class="sxs-lookup"><span data-stu-id="00960-156">[Database Files and Filegroups](database-files-and-filegroups.md) </span></span>  
 <span data-ttu-id="00960-157">[데이터베이스에서 데이터 또는 로그 파일 삭제](delete-data-or-log-files-from-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="00960-157">[Delete Data or Log Files from a Database](delete-data-or-log-files-from-a-database.md) </span></span>  
 [<span data-ttu-id="00960-158">데이터베이스의 크기 늘리기</span><span class="sxs-lookup"><span data-stu-id="00960-158">Increase the Size of a Database</span></span>](increase-the-size-of-a-database.md)  
  
  
