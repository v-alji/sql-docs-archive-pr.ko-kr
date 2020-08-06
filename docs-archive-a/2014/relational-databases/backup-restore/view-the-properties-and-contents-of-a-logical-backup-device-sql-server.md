---
title: 논리적 백업 디바이스의 속성 및 내용 보기(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- displaying backup content
- viewing backup content
- database backups [SQL Server], viewing content
- backing up databases [SQL Server], viewing content
- backing up databases [SQL Server], properties
- displaying backup properties
- backup devices [SQL Server], viewing information
- viewing backup properties
- database backups [SQL Server], properties
ms.assetid: 3a309074-e816-454d-b6c3-fcfdde0cbf74
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f2bdf41e3dbda079e3627ff7a7c1c3c78103b728
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734164"
---
# <a name="view-the-properties-and-contents-of-a-logical-backup-device-sql-server"></a><span data-ttu-id="6e21f-102">논리적 백업 디바이스의 속성 및 내용 보기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6e21f-102">View the Properties and Contents of a Logical Backup Device (SQL Server)</span></span>
  <span data-ttu-id="6e21f-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 논리적 백업 디바이스의 속성과 내용을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6e21f-103">This topic describes how to view the properties and contents of a logical backup device in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="6e21f-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="6e21f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6e21f-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="6e21f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6e21f-106">보안</span><span class="sxs-lookup"><span data-stu-id="6e21f-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6e21f-107">**논리적 백업 디바이스의 속성과 내용을 보려면:**</span><span class="sxs-lookup"><span data-stu-id="6e21f-107">**To view the properties and contents of a logical backup device, using:**</span></span>  
  
     [<span data-ttu-id="6e21f-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6e21f-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6e21f-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6e21f-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6e21f-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="6e21f-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6e21f-111">보안</span><span class="sxs-lookup"><span data-stu-id="6e21f-111">Security</span></span>  
 <span data-ttu-id="6e21f-112">보안에 대한 자세한 내용은 [RESTORE LABELONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e21f-112">For information about security, see [RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6e21f-113">권한</span><span class="sxs-lookup"><span data-stu-id="6e21f-113">Permissions</span></span>  
 <span data-ttu-id="6e21f-114">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상 버전에서 백업 세트나 백업 디바이스에 대한 정보를 얻으려면 CREATE DATABASE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6e21f-114">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission.</span></span> <span data-ttu-id="6e21f-115">자세한 내용은 [GRANT 데이터베이스 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e21f-115">For more information, see [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6e21f-116">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="6e21f-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-properties-and-contents-of-a-logical-backup-device"></a><span data-ttu-id="6e21f-117">논리적 백업 디바이스의 속성과 내용을 보려면</span><span class="sxs-lookup"><span data-stu-id="6e21f-117">To view the properties and contents of a logical backup device</span></span>  
  
1.  <span data-ttu-id="6e21f-118">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 후 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6e21f-118">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="6e21f-119">**서버 개체**를 확장한 다음 **백업 디바이스**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6e21f-119">Expand **Server Objects**, and expand **Backup Devices**.</span></span>  
  
3.  <span data-ttu-id="6e21f-120">디바이스를 클릭하고 **속성**을 마우스 오른쪽 단추로 클릭하면 **백업 디바이스** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="6e21f-120">Click the device and right-click **Properties**, which opens the **Backup Device** dialog box.</span></span>  
  
4.  <span data-ttu-id="6e21f-121">**일반** 페이지에 디바이스 이름과 대상이 표시됩니다. 대상은 테이프 디바이스이거나 파일 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="6e21f-121">The **General** page displays the device name and destination, which is either a tape device or file path.</span></span>  
  
5.  <span data-ttu-id="6e21f-122">**페이지 선택** 페이지에서 **미디어 내용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e21f-122">In the **Select a Page** pane, click **Media Contents**.</span></span>  
  
6.  <span data-ttu-id="6e21f-123">다음과 같은 속성 패널에 오른쪽 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e21f-123">The right-hand pane displays in the following properties panels:</span></span>  
  
    -   <span data-ttu-id="6e21f-124">**미디어**</span><span class="sxs-lookup"><span data-stu-id="6e21f-124">**Media**</span></span>  
  
         <span data-ttu-id="6e21f-125">미디어 시퀀스 번호, 패밀리 시퀀스 번호, 미러 ID(있는 경우) 등의 미디어 시퀀스 정보 및 미디어를 만든 날짜와 시간</span><span class="sxs-lookup"><span data-stu-id="6e21f-125">Media sequence information (the media sequence number, the family sequence number, and the mirror identifier, if any) and the media creation date and time.</span></span>  
  
    -   <span data-ttu-id="6e21f-126">**미디어 세트**</span><span class="sxs-lookup"><span data-stu-id="6e21f-126">**Media set**</span></span>  
  
         <span data-ttu-id="6e21f-127">미디어 세트 정보: 미디어 세트 이름과 설명(있는 경우) 및 미디어 세트에 있는 패밀리 수</span><span class="sxs-lookup"><span data-stu-id="6e21f-127">Media set information: the media set name and description, if any, and the number of families in the media set.</span></span>  
  
7.  <span data-ttu-id="6e21f-128">**백업 세트** 표에는 미디어 세트 내용에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e21f-128">The **Backup sets** grid displays information about the contents of the media set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e21f-129">자세한 내용은 [미디어 내용 페이지](backup-device-media-contents-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e21f-129">For more information, see [Media Contents Page](backup-device-media-contents-page.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6e21f-130">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="6e21f-130">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-properties-and-contents-of-a-logical-backup-device"></a><span data-ttu-id="6e21f-131">논리적 백업 디바이스의 속성과 내용을 보려면</span><span class="sxs-lookup"><span data-stu-id="6e21f-131">To view the properties and contents of a logical backup device</span></span>  
  
1.  <span data-ttu-id="6e21f-132">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6e21f-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6e21f-133">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e21f-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6e21f-134">[RESTORE LABELONLY](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e21f-134">Use the [RESTORE LABELONLY](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) statement.</span></span> <span data-ttu-id="6e21f-135">이 예에서는 `AdvWrks2008R2Backup` 논리적 백업 디바이스에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6e21f-135">This example returns information about the `AdvWrks2008R2Backup` logical backup device.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
RESTORE LABELONLY  
   FROM AdvWrks2008R2Backup ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e21f-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e21f-136">See Also</span></span>  
 <span data-ttu-id="6e21f-137">[backupfilegroup&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6e21f-137">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span></span>  
 <span data-ttu-id="6e21f-138">[backupfile&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6e21f-138">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span></span>  
 <span data-ttu-id="6e21f-139">[backupset&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6e21f-139">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="6e21f-140">[backupmediaset&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6e21f-140">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span></span>  
 <span data-ttu-id="6e21f-141">[backupmediafamily&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6e21f-141">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span></span>  
 <span data-ttu-id="6e21f-142">[sp_addumpdevice&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6e21f-142">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 [<span data-ttu-id="6e21f-143">백업 디바이스&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6e21f-143">Backup Devices &#40;SQL Server&#41;</span></span>](backup-devices-sql-server.md)  
  
  
