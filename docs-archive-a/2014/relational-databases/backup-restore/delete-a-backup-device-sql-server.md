---
title: 백업 디바이스 삭제(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- database backups [SQL Server], deleting devices
- backup devices [SQL Server], deleting
- deleting backup devices
- removing backup devices
- backing up databases [SQL Server], backup devices
ms.assetid: 7be62480-ed6a-4262-a071-1feba73b1c02
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e8734e587a8ecde315fb17120511455a59e38901
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650134"
---
# <a name="delete-a-backup-device-sql-server"></a><span data-ttu-id="15f03-102">백업 디바이스 삭제(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="15f03-102">Delete a Backup Device (SQL Server)</span></span>
  <span data-ttu-id="15f03-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 백업 디바이스를 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15f03-103">This topic describes how to delete a backup device in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="15f03-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="15f03-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="15f03-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="15f03-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="15f03-106">보안</span><span class="sxs-lookup"><span data-stu-id="15f03-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="15f03-107">**다음을 사용하여 백업 디바이스를 삭제합니다.**</span><span class="sxs-lookup"><span data-stu-id="15f03-107">**To delete a backup device, using:**</span></span>  
  
     [<span data-ttu-id="15f03-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="15f03-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="15f03-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="15f03-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="15f03-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="15f03-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="15f03-111">보안</span><span class="sxs-lookup"><span data-stu-id="15f03-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="15f03-112">권한</span><span class="sxs-lookup"><span data-stu-id="15f03-112">Permissions</span></span>  
 <span data-ttu-id="15f03-113">**diskadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="15f03-113">Requires membership in the **diskadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="15f03-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="15f03-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-backup-device"></a><span data-ttu-id="15f03-115">백업 디바이스를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="15f03-115">To delete a backup device</span></span>  
  
1.  <span data-ttu-id="15f03-116">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 다음 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="15f03-116">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="15f03-117">**서버 개체**를 확장한 다음 **백업 디바이스**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="15f03-117">Expand **Server Objects**, and then expand **Backup Devices**.</span></span>  
  
3.  <span data-ttu-id="15f03-118">원하는 디바이스를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15f03-118">Right-click the device you want, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="15f03-119">**개체 삭제** 대화 상자에서 올바른 디바이스 이름이 **개체 이름** 열에 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="15f03-119">In the **Delete Object** dialog box, verify that the correct device name appears in the **Object Name** column.</span></span>  
  
5.  <span data-ttu-id="15f03-120">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15f03-120">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="15f03-121">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="15f03-121">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-backup-device"></a><span data-ttu-id="15f03-122">백업 디바이스를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="15f03-122">To delete a backup device</span></span>  
  
1.  <span data-ttu-id="15f03-123">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="15f03-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="15f03-124">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15f03-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="15f03-125">다음 예를 복사하여 쿼리에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="15f03-125">Copy and paste the following example into the query.</span></span> <span data-ttu-id="15f03-126">이 예에서는 [sp_dropdevice](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) 를 사용하여 백업 디바이스를 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15f03-126">This example shows how to use [sp_dropdevice](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) to delete a backup device.</span></span> <span data-ttu-id="15f03-127">`mybackupdisk` 백업 디바이스와 실제 이름 `c:\backup\backup1.bak`를 만들려면 첫 번째 예를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="15f03-127">Execute the first example to create the `mybackupdisk` backup device and the physical name `c:\backup\backup1.bak`.</span></span> <span data-ttu-id="15f03-128">`mybackupdisk` 백업 디바이스를 삭제하려면 `sp_dropdevice`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="15f03-128">Execute `sp_dropdevice` to delete the `mybackupdisk` backup device.</span></span> <span data-ttu-id="15f03-129">`delfile` 매개 변수는 물리적 이름을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="15f03-129">The `delfile` parameter deletes the physical name.</span></span>  
  
```sql  
--Define a backup device and physical name.   
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'disk', 'mybackupdisk', 'c:\backup\backup1.bak' ;  
GO  
--Delete the backup device and the physical name.  
USE AdventureWorks2012 ;  
GO  
EXEC sp_dropdevice ' mybackupdisk ', 'delfile' ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="15f03-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15f03-130">See Also</span></span>  
 <span data-ttu-id="15f03-131">[논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="15f03-131">[View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md) </span></span>  
 <span data-ttu-id="15f03-132">[sys.backup_devices&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="15f03-132">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span></span>  
 <span data-ttu-id="15f03-133">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="15f03-133">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="15f03-134">[백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="15f03-134">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="15f03-135">sp_addumpdevice&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="15f03-135">sp_addumpdevice &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)  
  
  
