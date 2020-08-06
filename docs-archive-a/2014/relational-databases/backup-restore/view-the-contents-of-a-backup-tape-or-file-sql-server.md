---
title: 백업 테이프 또는 파일의 내용 보기(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], tapes
- displaying backup content
- viewing backup content
- tape backup devices, viewing contents
- database backups [SQL Server], viewing content
- backing up databases [SQL Server], viewing content
ms.assetid: cd6674a2-ca55-4b5a-a971-878ba001821e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 044519b64d41fbbdfc9302ce24369ab282727f67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734179"
---
# <a name="view-the-contents-of-a-backup-tape-or-file-sql-server"></a><span data-ttu-id="c5594-102">백업 테이프 또는 파일의 내용 보기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c5594-102">View the Contents of a Backup Tape or File (SQL Server)</span></span>
  <span data-ttu-id="c5594-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 백업 테이프 또는 파일의 내용을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-103">This topic describes how to view the content of a backup tape or file in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c5594-104">테이프 백업 디바이스에 대한 지원은 나중 버전의 SQL Server에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-104">Support for tape backup devices will be removed in a future version of SQL Server.</span></span> <span data-ttu-id="c5594-105">새 개발 작업에서는 이 기능을 사용하지 않도록 하고, 현재 이 기능을 사용하는 애플리케이션은 수정하세요.</span><span class="sxs-lookup"><span data-stu-id="c5594-105">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="c5594-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="c5594-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c5594-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="c5594-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c5594-108">보안</span><span class="sxs-lookup"><span data-stu-id="c5594-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c5594-109">**다음을 사용하여 백업 테이프 또는 파일의 내용을 봅니다.**</span><span class="sxs-lookup"><span data-stu-id="c5594-109">**To view the content of a backup tape or file, using:**</span></span>  
  
     [<span data-ttu-id="c5594-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c5594-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c5594-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c5594-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c5594-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c5594-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c5594-113">보안</span><span class="sxs-lookup"><span data-stu-id="c5594-113">Security</span></span>  
 <span data-ttu-id="c5594-114">보안에 대한 자세한 내용은 [RESTORE HEADERONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c5594-114">For information about security, see [RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c5594-115">권한</span><span class="sxs-lookup"><span data-stu-id="c5594-115">Permissions</span></span>  
 <span data-ttu-id="c5594-116">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상 버전에서 백업 세트나 백업 디바이스에 대한 정보를 얻으려면 CREATE DATABASE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-116">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission.</span></span> <span data-ttu-id="c5594-117">자세한 내용은 [GRANT 데이터베이스 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c5594-117">For more information, see [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c5594-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="c5594-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-content-of-a-backup-tape-or-file"></a><span data-ttu-id="c5594-119">백업 테이프 또는 파일의 내용을 보려면</span><span class="sxs-lookup"><span data-stu-id="c5594-119">To view the content of a backup tape or file</span></span>  
  
1.  <span data-ttu-id="c5594-120">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 후 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-120">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="c5594-121">**데이터베이스**를 확장하고 해당 데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스** 를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-121">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="c5594-122">백업하려는 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음 **백업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-122">Right-click the database you want to backup, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="c5594-123">**데이터베이스 백업** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-123">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="c5594-124">**일반** 페이지의 **대상** 섹션에서 **디스크** 또는 **테이프**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-124">In the **Destination** section of the **General** page, click either **Disk** or **Tape**.</span></span> <span data-ttu-id="c5594-125">**백업할 위치** 목록 상자에서 디스크 파일 또는 테이프를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-125">In the **Back up to** list box, look for the disk file or tape you want.</span></span>  
  
     <span data-ttu-id="c5594-126">목록 상자에 디스크 파일 또는 테이프가 표시되지 않으면 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-126">If the disk file or tape is not displayed in the list-box, click **Add**.</span></span> <span data-ttu-id="c5594-127">파일 이름 또는 테이프 드라이브를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-127">Select a file name or tape drive.</span></span> <span data-ttu-id="c5594-128">**확인** 을 클릭하여 **백업할 위치**목록 상자에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-128">To add it to the **Back up to** list-box, click **OK**.</span></span>  
  
5.  <span data-ttu-id="c5594-129">**백업할 위치** 목록 상자에서 보려는 디스크 또는 테이프 드라이브의 경로를 선택한 다음 **내용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-129">In the **Back up to** list-box, select the path of the disk or tape drive you want to view, and click **Contents**.</span></span> <span data-ttu-id="c5594-130">**디바이스 내용** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-130">This opens the **Device Contents** dialog box.</span></span>  
  
6.  <span data-ttu-id="c5594-131">선택한 테이프 또는 파일의 미디어 세트 및 백업 세트에 대한 정보가 오른쪽 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-131">The right-hand pane displays information about the media set and backup sets on the selected tape or file.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c5594-132">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="c5594-132">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-content-of-a-backup-tape-or-file"></a><span data-ttu-id="c5594-133">백업 테이프 또는 파일의 내용을 보려면</span><span class="sxs-lookup"><span data-stu-id="c5594-133">To view the content of a backup tape or file</span></span>  
  
1.  <span data-ttu-id="c5594-134">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c5594-135">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c5594-136">[RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-136">Use the [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) statement.</span></span> <span data-ttu-id="c5594-137">이 예에서는 `AdventureWorks2012-FullBackup.bak`라는 파일에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c5594-137">This example returns information about the file named `AdventureWorks2012-FullBackup.bak`.</span></span>  
  
```sql  
USE AdventureWorks2012;  
RESTORE HEADERONLY   
FROM DISK = N'C:\AdventureWorks2012-FullBackup.bak' ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5594-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c5594-138">See Also</span></span>  
 <span data-ttu-id="c5594-139">[backupfilegroup&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c5594-139">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span></span>  
 <span data-ttu-id="c5594-140">[backupfile&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c5594-140">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span></span>  
 <span data-ttu-id="c5594-141">[backupset&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c5594-141">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="c5594-142">[backupmediaset&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c5594-142">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span></span>  
 <span data-ttu-id="c5594-143">[backupmediafamily&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c5594-143">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span></span>  
 <span data-ttu-id="c5594-144">[백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c5594-144">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 <span data-ttu-id="c5594-145">[디스크 파일에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c5594-145">[Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span></span>  
 [<span data-ttu-id="c5594-146">테이프 드라이브에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c5594-146">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
  
