---
title: 백업 세트의 데이터 및 로그 파일 보기(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- database backups [SQL Server], viewing backup sets
- viewing backup set information
- backup sets [SQL Server], viewing files in
- displaying backup set information
- transaction log backups [SQL Server], viewing backup sets
- backing up [SQL Server], viewing backup sets
ms.assetid: abb6420c-f809-426e-aeb4-d0a74989cf39
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7dbcb14a658b49aba6f5f2ebe3425a2ab5759efa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734176"
---
# <a name="view-the-data-and-log-files-in-a-backup-set-sql-server"></a><span data-ttu-id="030dd-102">백업 세트의 데이터와 로그 파일 보기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="030dd-102">View the Data and Log Files in a Backup Set (SQL Server)</span></span>
  <span data-ttu-id="030dd-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 백업 집합의 데이터 및 로그 파일을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="030dd-103">This topic describes how to view the data and log files in a backup set in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="030dd-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="030dd-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="030dd-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="030dd-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="030dd-106">보안</span><span class="sxs-lookup"><span data-stu-id="030dd-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="030dd-107">**다음을 사용하여 백업 세트의 데이터와 로그 파일을 봅니다.**</span><span class="sxs-lookup"><span data-stu-id="030dd-107">**To view the data and log files in a backup set, using:**</span></span>  
  
     [<span data-ttu-id="030dd-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="030dd-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="030dd-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="030dd-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="030dd-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="030dd-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="030dd-111">보안</span><span class="sxs-lookup"><span data-stu-id="030dd-111">Security</span></span>  
 <span data-ttu-id="030dd-112">보안에 대한 자세한 내용은 [RESTORE FILELISTONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="030dd-112">For information about security, see [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="030dd-113">권한</span><span class="sxs-lookup"><span data-stu-id="030dd-113">Permissions</span></span>  
 <span data-ttu-id="030dd-114">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상 버전에서 백업 세트나 백업 디바이스에 대한 정보를 얻으려면 CREATE DATABASE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="030dd-114">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission.</span></span> <span data-ttu-id="030dd-115">자세한 내용은 [GRANT 데이터베이스 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="030dd-115">For more information, see [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="030dd-116">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="030dd-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-data-and-log-files-in-a-backup-set"></a><span data-ttu-id="030dd-117">백업 세트의 데이터와 로그 파일을 보려면</span><span class="sxs-lookup"><span data-stu-id="030dd-117">To view the data and log files in a backup set</span></span>  
  
1.  <span data-ttu-id="030dd-118">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 후 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="030dd-118">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="030dd-119">**데이터베이스**를 확장하고 해당 데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스** 를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="030dd-119">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="030dd-120">데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭하면 **데이터베이스 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="030dd-120">Right-click the database, and then click **Properties**, which opens the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="030dd-121">**페이지 선택** 창에서 **파일**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="030dd-121">In the **Select a Page** pane, click **Files**.</span></span>  
  
5.  <span data-ttu-id="030dd-122">**데이터베이스 파일** 표 형태에서 데이터 및 로그 파일의 목록과 그 속성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="030dd-122">Look in the **Database files** grid for a list of the data and log files and their properties.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="030dd-123">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="030dd-123">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-data-and-log-files-in-a-backup-set"></a><span data-ttu-id="030dd-124">백업 세트의 데이터와 로그 파일을 보려면</span><span class="sxs-lookup"><span data-stu-id="030dd-124">To view the data and log files in a backup set</span></span>  
  
1.  <span data-ttu-id="030dd-125">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="030dd-125">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="030dd-126">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="030dd-126">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="030dd-127">[RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="030dd-127">Use the [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) statement.</span></span> <span data-ttu-id="030dd-128">이 예에서는`FILE=2`백업 디바이스의 두 번째 백업 세트( `AdventureWorksBackups` )에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="030dd-128">This example returns information about the second backup set (`FILE=2`) on the `AdventureWorksBackups` backup device.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
RESTORE FILELISTONLY FROM AdventureWorksBackups   
   WITH FILE=2;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="030dd-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="030dd-129">See Also</span></span>  
 <span data-ttu-id="030dd-130">[backupfilegroup&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="030dd-130">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span></span>  
 <span data-ttu-id="030dd-131">[backupfile&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="030dd-131">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span></span>  
 <span data-ttu-id="030dd-132">[backupset&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="030dd-132">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="030dd-133">[backupmediaset&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="030dd-133">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span></span>  
 <span data-ttu-id="030dd-134">[backupmediafamily&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="030dd-134">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span></span>  
 [<span data-ttu-id="030dd-135">백업 디바이스&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="030dd-135">Backup Devices &#40;SQL Server&#41;</span></span>](backup-devices-sql-server.md)  
  
  
