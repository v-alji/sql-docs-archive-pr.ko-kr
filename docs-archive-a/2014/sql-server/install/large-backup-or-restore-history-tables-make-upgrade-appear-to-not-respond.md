---
title: 대량 백업 또는 복원 기록 테이블이 있으면 업그레이드가 응답 하지 않는 것 처럼 보일 수 있습니다. | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- backup history tables
- history tables
ms.assetid: f88d86ec-324b-4518-b6d7-1af7e7265812
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 918c20f58c00c535d8ed41d887e9671f5e821a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646819"
---
# <a name="large-backup-or-restore-history-tables-make-upgrade-appear-to-not-respond"></a><span data-ttu-id="dfb26-102">큰 백업 또는 복원 기록 테이블이 있으면 업그레이드가 응답하지 않는 것으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="dfb26-102">Large backup or restore history tables make upgrade appear to not respond</span></span>
  <span data-ttu-id="dfb26-103">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서 경우 일부 백업 및 복원 기록 테이블에 새 열이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb26-103">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], new columns were added to some of the backup and restore history tables.</span></span> <span data-ttu-id="dfb26-104">이러한 테이블을 업그레이드하려면 새 열을 추가하도록 이러한 테이블을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb26-104">Upgrading these tables requires altering them to add the new columns.</span></span> <span data-ttu-id="dfb26-105">이러한 테이블 중 하나 이상에 많은 수의 행이 포함되어 있으면 해당 테이블에 열을 추가하는 ALTER TABLE 문에서 업그레이드가 오랫동안 지체됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb26-105">If one or more of these tables contains a large number of rows, the upgrade will stall for a substantial amount of time on the ALTER TABLE statement that adds columns to that table.</span></span>  
  
## <a name="component"></a><span data-ttu-id="dfb26-106">구성 요소</span><span class="sxs-lookup"><span data-stu-id="dfb26-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="dfb26-107">Description</span><span class="sxs-lookup"><span data-stu-id="dfb26-107">Description</span></span>  
 <span data-ttu-id="dfb26-108">다음 백업 또는 복원 기록 테이블에 많은 수의 행이 포함 되어 있으면 업그레이드가 응답 하지 않는 것 처럼 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb26-108">Upgrade can appear to stop responding if any of the following backup or restore history tables contains a large number of rows:</span></span>  
  
-   <span data-ttu-id="dfb26-109">**backupfile**</span><span class="sxs-lookup"><span data-stu-id="dfb26-109">**backupfile**</span></span>  
  
-   <span data-ttu-id="dfb26-110">**backupmediafamily**</span><span class="sxs-lookup"><span data-stu-id="dfb26-110">**backupmediafamily**</span></span>  
  
-   <span data-ttu-id="dfb26-111">**backupmediaset**</span><span class="sxs-lookup"><span data-stu-id="dfb26-111">**backupmediaset**</span></span>  
  
-   <span data-ttu-id="dfb26-112">**backupset**</span><span class="sxs-lookup"><span data-stu-id="dfb26-112">**backupset**</span></span>  
  
-   <span data-ttu-id="dfb26-113">**restorefile**</span><span class="sxs-lookup"><span data-stu-id="dfb26-113">**restorefile**</span></span>  
  
-   <span data-ttu-id="dfb26-114">**restorefilegroup**</span><span class="sxs-lookup"><span data-stu-id="dfb26-114">**restorefilegroup**</span></span>  
  
-   <span data-ttu-id="dfb26-115">**restorehistory**</span><span class="sxs-lookup"><span data-stu-id="dfb26-115">**restorehistory**</span></span>  
  
 <span data-ttu-id="dfb26-116">이러한 테이블 중 10,000개 이상의 행이 포함된 테이블이 있으면 업그레이드 관리자는 규칙 위반 오류를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb26-116">If any of these tables has 10,000 or more rows, Upgrade Advisor reports a noncompliance failure.</span></span> <span data-ttu-id="dfb26-117">이때 업그레이드 관리자는 허용된 행 수를 초과한 테이블을 보고하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb26-117">It does not report which table exceeds the allowed number of rows.</span></span> <span data-ttu-id="dfb26-118">이러한 오류는 10,000개의 행을 초과하는 행이 처음 발견되는 대로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb26-118">The first table that exceeds 10,000 rows causes the failure.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="dfb26-119">수정 동작</span><span class="sxs-lookup"><span data-stu-id="dfb26-119">Corrective Action</span></span>  
 <span data-ttu-id="dfb26-120">10,000개의 행을 초과하는 행이 있으면 데이터베이스를 업그레이드하기 전에 행 수를 10,000개 미만으로 줄이는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb26-120">Before you upgrade a database, if any of these tables exceeds 10,000 rows, we recommend that you reduce the number to less than 10,000.</span></span> <span data-ttu-id="dfb26-121">이러한 모든 테이블의 행을 줄이려면 **sp_delete_backuphistory** 저장 프로시저를 실행 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb26-121">To reduce rows in all of these tables, you can run the **sp_delete_backuphistory** stored procedure.</span></span> <span data-ttu-id="dfb26-122">이 프로시저는 모든 백업 및 복원 기록 테이블에서 지정한 날짜보다 오래된 백업 세트의 항목을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb26-122">This procedure deletes the entries in all of the backup and restore history tables for backup sets older than a specified date.</span></span> <span data-ttu-id="dfb26-123">자세한 내용은 [sp_delete_backuphistory&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dfb26-123">For more information, see [sp_delete_backuphistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dfb26-124">백업 및 복원 기록 테이블에 10,000개 이상의 행이 있는 데이터베이스를 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb26-124">You can upgrade a database whose backup and restore history tables are larger than 10,000 rows.</span></span> <span data-ttu-id="dfb26-125">그러나 큰 테이블이 변경되는 동안에는 업그레이드가 중지된 것처럼 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb26-125">But the upgrade may appear to stall while large tables are being altered.</span></span> <span data-ttu-id="dfb26-126">테이블이 클수록 업그레이드를 완료하는 데 걸리는 시간도 길어집니다.</span><span class="sxs-lookup"><span data-stu-id="dfb26-126">The larger the tables, the longer that Setup takes to complete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfb26-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dfb26-127">See Also</span></span>  
 <span data-ttu-id="dfb26-128">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="dfb26-128">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="dfb26-129">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="dfb26-129">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
