---
title: MSSQLSERVER_926 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 926 (Database Engine error)
ms.assetid: 57e01668-883b-4be4-84a8-a111caaf0486
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ae6796c9f4869d45223ab1283a68fc2bfe78aa11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650037"
---
# <a name="mssqlserver_926"></a><span data-ttu-id="31438-102">MSSQLSERVER_926</span><span class="sxs-lookup"><span data-stu-id="31438-102">MSSQLSERVER_926</span></span>
    
## <a name="details"></a><span data-ttu-id="31438-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="31438-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="31438-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="31438-104">Product Name</span></span>|<span data-ttu-id="31438-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="31438-105">SQL Server</span></span>|  
|<span data-ttu-id="31438-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="31438-106">Event ID</span></span>|<span data-ttu-id="31438-107">926</span><span class="sxs-lookup"><span data-stu-id="31438-107">926</span></span>|  
|<span data-ttu-id="31438-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="31438-108">Event Source</span></span>|<span data-ttu-id="31438-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="31438-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="31438-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="31438-110">Component</span></span>|<span data-ttu-id="31438-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="31438-111">SQLEngine</span></span>|  
|<span data-ttu-id="31438-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="31438-112">Symbolic Name</span></span>|<span data-ttu-id="31438-113">DB_SUSPECT</span><span class="sxs-lookup"><span data-stu-id="31438-113">DB_SUSPECT</span></span>|  
|<span data-ttu-id="31438-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="31438-114">Message Text</span></span>|<span data-ttu-id="31438-115">데이터베이스 '%.\*ls'을(를) 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31438-115">Database '%.\*ls' cannot be opened.</span></span> <span data-ttu-id="31438-116">복구에 의해 주의 대상으로 표시되었습니다.</span><span class="sxs-lookup"><span data-stu-id="31438-116">It has been marked SUSPECT by recovery.</span></span> <span data-ttu-id="31438-117">자세한 내용은 SQL Server 오류 로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="31438-117">See the SQL Server errorlog for more information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="31438-118">설명</span><span class="sxs-lookup"><span data-stu-id="31438-118">Explanation</span></span>  
 <span data-ttu-id="31438-119">데이터베이스를 일관성 있는 트랜잭션 상태가 되게 하는 복구 프로세스가 실패했으므로 데이터베이스가 주의 대상으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="31438-119">The database is marked as suspect because it failed the recovery process that brings a database to a consistent transactional state.</span></span> <span data-ttu-id="31438-120">이 문제는 다음 작업에서 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31438-120">This can occur during the following operations:</span></span>  
  
-   <span data-ttu-id="31438-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스 시작</span><span class="sxs-lookup"><span data-stu-id="31438-121">Starting up an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="31438-122">데이터베이스 연결</span><span class="sxs-lookup"><span data-stu-id="31438-122">Attaching a database.</span></span>  
  
-   <span data-ttu-id="31438-123">RESTORE 데이터베이스 또는 RESTORE LOG 프로시저 사용</span><span class="sxs-lookup"><span data-stu-id="31438-123">Using the RESTORE database or RESTORE LOG procedures.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="31438-124">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="31438-124">User Action</span></span>  
 <span data-ttu-id="31438-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]오류 로그를 검사하여 오류의 원인을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="31438-125">Inspect the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and determine the cause of the error.</span></span> <span data-ttu-id="31438-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 실패한 복구로 인해 다시 시작된 경우 복구 실패 원인을 보려면 이전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="31438-126">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been restarted since the failed recovery, look at previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error logs to see the reason why recovery failed.</span></span>  
  
 <span data-ttu-id="31438-127">지속적인 I/O 오류, 조각난 페이지 또는 다른 가능한 하드웨어 문제로 인해 복구가 실패한 경우 기본 하드웨어 문제를 해결하고 백업을 사용하여 데이터베이스를 복원하십시오.</span><span class="sxs-lookup"><span data-stu-id="31438-127">If the recovery failed because of a persistent I/O error, a torn page, or other possible hardware problem, resolve the underlying hardware problem and restore the database by using a backup.</span></span> <span data-ttu-id="31438-128">백업을 사용할 수 없는 경우 DBCC CHECKDB의 복구 옵션을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="31438-128">If no backups are available, consider the repair options of DBCC CHECKDB.</span></span>  
  
 <span data-ttu-id="31438-129">이 문제를 해결할 수 없으면 주 지원 공급자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="31438-129">If you are unable to resolve this problem, contact your primary support provider.</span></span> <span data-ttu-id="31438-130">검토에 사용할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그를 보관하십시오.</span><span class="sxs-lookup"><span data-stu-id="31438-130">Have the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log available for review.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31438-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="31438-131">See Also</span></span>  
 <span data-ttu-id="31438-132">[SQL Server 데이터베이스 백업 및 복원](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="31438-132">[Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="31438-133">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="31438-133">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="31438-134">[Transact-sql&#41;&#40;sys.sys데이터베이스](/sql/relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="31438-134">[sys.sysdatabases &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql) </span></span>  
 [<span data-ttu-id="31438-135">데이터베이스 분리 및 연결&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="31438-135">Database Detach and Attach &#40;SQL Server&#41;</span></span>](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
  
