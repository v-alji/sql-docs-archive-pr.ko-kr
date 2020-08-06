---
title: MSSQL_ENG003165 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG003165 error
ms.assetid: 707d33dd-644e-4cc9-ac51-dddd49031530
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1702588ba6ac1beeb33b87a7afc7fc330271559
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638689"
---
# <a name="mssql_eng003165"></a><span data-ttu-id="d413a-102">MSSQL_ENG003165</span><span class="sxs-lookup"><span data-stu-id="d413a-102">MSSQL_ENG003165</span></span>
    
## <a name="message-details"></a><span data-ttu-id="d413a-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="d413a-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d413a-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="d413a-104">Product Name</span></span>|<span data-ttu-id="d413a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d413a-105">SQL Server</span></span>|  
|<span data-ttu-id="d413a-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="d413a-106">Event ID</span></span>|<span data-ttu-id="d413a-107">3165</span><span class="sxs-lookup"><span data-stu-id="d413a-107">3165</span></span>|  
|<span data-ttu-id="d413a-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="d413a-108">Event Source</span></span>|<span data-ttu-id="d413a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d413a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d413a-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="d413a-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="d413a-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="d413a-111">Symbolic Name</span></span>||  
|<span data-ttu-id="d413a-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="d413a-112">Message Text</span></span>|<span data-ttu-id="d413a-113">데이터베이스 '%ls'이(가) 복원되었지만 복제가 복원/제거되는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="d413a-113">Database '%ls' was restored; however, an error was encountered while replication was being restored/removed.</span></span> <span data-ttu-id="d413a-114">데이터베이스가 오프라인 상태로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d413a-114">The database has been left offline.</span></span> <span data-ttu-id="d413a-115">SQL Server 온라인 설명서의 MSSQL_ENG003165 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d413a-115">See the topic MSSQL_ENG003165 in SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d413a-116">설명</span><span class="sxs-lookup"><span data-stu-id="d413a-116">Explanation</span></span>  
 <span data-ttu-id="d413a-117">이 오류는 복제된 데이터베이스의 백업을 복원하는 동안 문제가 발생하는 경우 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d413a-117">This error is raised if a problem occurs restoring a backup of a replicated database:</span></span>  
  
-   <span data-ttu-id="d413a-118">백업을 수행한 데이터베이스와 서버로 해당 백업을 복원하는 경우 이 오류는 복제 설정을 제대로 복원하지 못했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d413a-118">If the backup is being restored to the same database and server on which it was taken, the error indicates that replication settings could not be restored properly.</span></span>  
  
-   <span data-ttu-id="d413a-119">백업을 다른 데이터베이스나 서버로 복원하는 경우 이 오류는 복제 설정을 제대로 제거하지 못했음을 나타냅니다. 데이터베이스나 서버가 다른 경우에는 기본적으로 복제 설정이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="d413a-119">If the backup is being restored to a different database or server, the error indicates that replication settings could not be removed properly (by default, replication settings are removed if the database or server is different).</span></span>  
  
 <span data-ttu-id="d413a-120">이 오류의 원인은 복원된 데이터베이스와 복제 메타데이터 **msdb**, **master**또는 배포 데이터베이스가 포함된 하나 이상의 시스템 데이터베이스의 상태가 일치하지 않기 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d413a-120">The error is probably the result of a mismatch between the state of the restored database and one or more system databases that contain replication metadata: **msdb**, **master**, or the distribution database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d413a-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="d413a-121">User Action</span></span>  
 <span data-ttu-id="d413a-122">이 문제를 해결하려면:</span><span class="sxs-lookup"><span data-stu-id="d413a-122">To resolve this issue:</span></span>  
  
1.  <span data-ttu-id="d413a-123">예를 들면 `ALTER DATABASE AdventureWorks SET ONLINE`과 같이 ALTER DATABASE를 실행하여 데이터베이스를 온라인 상태로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d413a-123">Execute ALTER DATABASE to bring the database online; for example: `ALTER DATABASE AdventureWorks SET ONLINE`.</span></span> <span data-ttu-id="d413a-124">자세한 내용은 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d413a-124">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span> <span data-ttu-id="d413a-125">복제 설정을 유지하려면 2단계로 이동하고,</span><span class="sxs-lookup"><span data-stu-id="d413a-125">If you want to preserve replication settings, go to step 2.</span></span> <span data-ttu-id="d413a-126">그렇지 않은 경우에는 3단계로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="d413a-126">If not, go to step 3.</span></span>  
  
2.  <span data-ttu-id="d413a-127">[sp_restoredbreplication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-restoredbreplication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d413a-127">Execute [sp_restoredbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-restoredbreplication-transact-sql).</span></span> <span data-ttu-id="d413a-128">이 저장 프로시저가 성공적으로 실행되면 복원이 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="d413a-128">If this stored procedure executes successfully, the restore is complete.</span></span> <span data-ttu-id="d413a-129">성공적으로 실행되지 않으면 3단계로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="d413a-129">If it does not execute successfully, go to step 3.</span></span>  
  
3.  <span data-ttu-id="d413a-130">[sp_removedbreplication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)을 실행하여 모든 복제 설정을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="d413a-130">Execute [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to remove all replication settings.</span></span>  
  
     <span data-ttu-id="d413a-131">필요한 경우 복제를 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d413a-131">Reconfigure replication if necessary.</span></span> <span data-ttu-id="d413a-132">복제 토폴로지를 권장 사항대로 스크립팅한 경우에는 스크립트를 사용하여 토폴로지를 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d413a-132">If you have scripted the replication topology as recommended, use scripts to reconfigure the topology.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d413a-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d413a-133">See Also</span></span>  
 <span data-ttu-id="d413a-134">[SQL Server 데이터베이스 백업 및 복원](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="d413a-134">[Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="d413a-135">[복제된 데이터베이스 백업 및 복원](administration/back-up-and-restore-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="d413a-135">[Back Up and Restore Replicated Databases](administration/back-up-and-restore-replicated-databases.md) </span></span>  
 [<span data-ttu-id="d413a-136">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="d413a-136">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
