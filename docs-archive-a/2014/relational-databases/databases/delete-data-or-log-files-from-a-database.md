---
title: 데이터베이스에서 데이터 또는 로그 파일 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], files
- deleting files
- removing files
- removing data
- data deletions [SQL Server]
- file deletion [SQL Server]
- deleting data
ms.assetid: 0db4018c-ce2c-4ba1-bb29-1e4f3791c925
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6f7bd170e085e9bc94b00446545850e905efaa34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742196"
---
# <a name="delete-data-or-log-files-from-a-database"></a><span data-ttu-id="a7e0d-102">데이터베이스에서 데이터 또는 로그 파일 삭제</span><span class="sxs-lookup"><span data-stu-id="a7e0d-102">Delete Data or Log Files from a Database</span></span>
  <span data-ttu-id="a7e0d-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]의 데이터 또는 로그 파일을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e0d-103">This topic describes how to delete data or log files in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a7e0d-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="a7e0d-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="a7e0d-105">필수 조건</span><span class="sxs-lookup"><span data-stu-id="a7e0d-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="a7e0d-106">빈 파일만 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7e0d-106">A file must be empty before it can be deleted.</span></span> <span data-ttu-id="a7e0d-107">자세한 내용은 [파일 축소](shrink-a-file.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a7e0d-107">For more information, see [Shrink a File](shrink-a-file.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a7e0d-108">보안</span><span class="sxs-lookup"><span data-stu-id="a7e0d-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a7e0d-109">권한</span><span class="sxs-lookup"><span data-stu-id="a7e0d-109">Permissions</span></span>  
 <span data-ttu-id="a7e0d-110">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e0d-110">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a7e0d-111">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="a7e0d-111">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-data-or-log-files-from-a-database"></a><span data-ttu-id="a7e0d-112">데이터베이스에서 데이터 또는 로그 파일을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="a7e0d-112">To delete data or log files from a database</span></span>  
  
1.  <span data-ttu-id="a7e0d-113">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e0d-113">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="a7e0d-114">**데이터베이스**를 확장하고 파일을 삭제할 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e0d-114">Expand **Databases**, right-click the database from which to delete the file, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a7e0d-115">**파일** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e0d-115">Select the **Files** page.</span></span>  
  
4.  <span data-ttu-id="a7e0d-116">**데이터베이스 파일** 표에서 삭제할 파일을 선택하고 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e0d-116">In the **Database files** grid, select the file to delete and then click **Remove**.</span></span>  
  
5.  <span data-ttu-id="a7e0d-117">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e0d-117">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a7e0d-118">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="a7e0d-118">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-data-or-log-files-from-a-database"></a><span data-ttu-id="a7e0d-119">데이터베이스에서 데이터 또는 로그 파일을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="a7e0d-119">To delete data or log files from a database</span></span>  
  
1.  <span data-ttu-id="a7e0d-120">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e0d-120">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a7e0d-121">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e0d-121">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a7e0d-122">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e0d-122">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="a7e0d-123">다음 예에서는 `test1dat4`파일을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e0d-123">This example removes the file `test1dat4`.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase4](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase4)]  
  
 <span data-ttu-id="a7e0d-124">더 많은 예제를 보려면 [ALTER DATABASE 파일 및 파일 그룹 옵션&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a7e0d-124">For more examples, see [ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e0d-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a7e0d-125">See Also</span></span>  
 <span data-ttu-id="a7e0d-126">[데이터베이스 축소](shrink-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="a7e0d-126">[Shrink a Database](shrink-a-database.md) </span></span>  
 [<span data-ttu-id="a7e0d-127">데이터베이스에 데이터 또는 로그 파일 추가</span><span class="sxs-lookup"><span data-stu-id="a7e0d-127">Add Data or Log Files to a Database</span></span>](add-data-or-log-files-to-a-database.md)  
  
  
