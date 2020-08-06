---
title: 데이터베이스 상태 | Microsoft 문서
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASESTATES.F1
helpviewer_keywords:
- emergency database state [SQL Server]
- verifying database states
- viewing database states
- displaying database states
- database states [SQL Server]
- current database state
- offline database state [SQL Server]
- suspect database state
- recovery pending database state [SQL Server]
- states [SQL Server], databases
- online database state
- states [SQL Server]
- restoring database state [SQL Server]
ms.assetid: b7f1f111-ca73-4a89-b567-a98d64d6ecb3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0aec4e5fb367f5fe9bf8fca5ed056269930cf2db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742207"
---
# <a name="database-states"></a><span data-ttu-id="9de7b-102">데이터베이스 상태</span><span class="sxs-lookup"><span data-stu-id="9de7b-102">Database States</span></span>
  <span data-ttu-id="9de7b-103">데이터베이스는 항상 하나의 특정한 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-103">A database is always in one specific state.</span></span> <span data-ttu-id="9de7b-104">예를 들어 ONLINE, OFFLINE 또는 SUSPECT 상태일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-104">For example, these states include ONLINE, OFFLINE, or SUSPECT.</span></span> <span data-ttu-id="9de7b-105">데이터베이스의 현재 상태를 확인하려면 **sys.databases** 카탈로그 뷰의 [state_desc](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 열이나 **DATABASEPROPERTYEX** 함수의 [Status](/sql/t-sql/functions/databasepropertyex-transact-sql) 속성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-105">To verify the current state of a database, select the **state_desc** column in the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view or the **Status** property in the [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) function.</span></span>  
  
## <a name="database-state-definitions"></a><span data-ttu-id="9de7b-106">데이터베이스 상태 정의</span><span class="sxs-lookup"><span data-stu-id="9de7b-106">Database State Definitions</span></span>  
 <span data-ttu-id="9de7b-107">다음 표에서는 데이터베이스 상태를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-107">The following table defines the database states.</span></span>  
  
|<span data-ttu-id="9de7b-108">시스템 상태</span><span class="sxs-lookup"><span data-stu-id="9de7b-108">State</span></span>|<span data-ttu-id="9de7b-109">정의</span><span class="sxs-lookup"><span data-stu-id="9de7b-109">Definition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="9de7b-110">ONLINE</span><span class="sxs-lookup"><span data-stu-id="9de7b-110">ONLINE</span></span>|<span data-ttu-id="9de7b-111">데이터베이스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-111">Database is available for access.</span></span> <span data-ttu-id="9de7b-112">복구의 실행 취소 단계가 완료되지 않은 경우에도 주 파일 그룹은 온라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-112">The primary filegroup is online, although the undo phase of recovery may not have been completed.</span></span>|  
|<span data-ttu-id="9de7b-113">OFFLINE</span><span class="sxs-lookup"><span data-stu-id="9de7b-113">OFFLINE</span></span>|<span data-ttu-id="9de7b-114">데이터베이스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-114">Database is unavailable.</span></span> <span data-ttu-id="9de7b-115">명시적 사용자 동작으로 인해 데이터베이스가 오프라인 상태가 되어 추가 사용자 동작이 수행될 때까지 오프라인 상태로 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-115">A database becomes offline by explicit user action and remains offline until additional user action is taken.</span></span> <span data-ttu-id="9de7b-116">예를 들어 파일을 새 디스크로 이동하기 위해 데이터베이스를 오프라인으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-116">For example, the database may be taken offline in order to move a file to a new disk.</span></span> <span data-ttu-id="9de7b-117">이러한 경우 이동이 완료되면 데이터베이스가 온라인 상태로 돌아옵니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-117">The database is then brought back online after the move has been completed.</span></span>|  
|<span data-ttu-id="9de7b-118">RESTORING</span><span class="sxs-lookup"><span data-stu-id="9de7b-118">RESTORING</span></span>|<span data-ttu-id="9de7b-119">주 파일 그룹에서 하나 이상의 파일을 복원하고 있거나 하나 이상의 보조 파일이 오프라인 상태에서 복원되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-119">One or more files of the primary filegroup are being restored, or one or more secondary files are being restored offline.</span></span> <span data-ttu-id="9de7b-120">데이터베이스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-120">The database is unavailable.</span></span>|  
|<span data-ttu-id="9de7b-121">RECOVERING</span><span class="sxs-lookup"><span data-stu-id="9de7b-121">RECOVERING</span></span>|<span data-ttu-id="9de7b-122">데이터베이스가 복구되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-122">Database is being recovered.</span></span> <span data-ttu-id="9de7b-123">복구 중 과정은 일시적 상태입니다. 복구가 성공하면 데이터베이스는 자동으로 온라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-123">The recovering process is a transient state; the database will automatically become online if the recovery succeeds.</span></span> <span data-ttu-id="9de7b-124">복구가 실패하면 데이터베이스는 주의 대상 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-124">If the recovery fails, the database will become suspect.</span></span> <span data-ttu-id="9de7b-125">데이터베이스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-125">The database is unavailable.</span></span>|  
|<span data-ttu-id="9de7b-126">RECOVERY PENDING</span><span class="sxs-lookup"><span data-stu-id="9de7b-126">RECOVERY PENDING</span></span>|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="9de7b-127">에서 복구 중 리소스 관련 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-127">has encountered a resource-related error during recovery.</span></span> <span data-ttu-id="9de7b-128">데이터베이스가 손상되지는 않았지만 파일이 누락되었거나 시스템 리소스 제한으로 인해 데이터베이스를 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-128">The database is not damaged, but files may be missing or system resource limitations may be preventing it from starting.</span></span> <span data-ttu-id="9de7b-129">데이터베이스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-129">The database is unavailable.</span></span> <span data-ttu-id="9de7b-130">오류를 해결하고 복구 프로세스를 완료하기 위한 사용자의 추가적인 동작이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-130">Additional action by the user is required to resolve the error and let the recovery process be completed.</span></span>|  
|<span data-ttu-id="9de7b-131">SUSPECT</span><span class="sxs-lookup"><span data-stu-id="9de7b-131">SUSPECT</span></span>|<span data-ttu-id="9de7b-132">주 파일 그룹이 주의 대상이거나 손상되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-132">At least the primary filegroup is suspect and may be damaged.</span></span> <span data-ttu-id="9de7b-133">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]를 시작하는 동안에는 데이터베이스를 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-133">The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9de7b-134">데이터베이스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-134">The database is unavailable.</span></span> <span data-ttu-id="9de7b-135">문제를 해결하기 위한 사용자의 추가적인 동작이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-135">Additional action by the user is required to resolve the problem.</span></span>|  
|<span data-ttu-id="9de7b-136">EMERGENCY</span><span class="sxs-lookup"><span data-stu-id="9de7b-136">EMERGENCY</span></span>|<span data-ttu-id="9de7b-137">사용자가 데이터베이스를 변경하고 응급 상태로 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-137">User has changed the database and set the status to EMERGENCY.</span></span> <span data-ttu-id="9de7b-138">데이터베이스가 단일 사용자 모드에 있고 복구 또는 복원되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-138">The database is in single-user mode and may be repaired or restored.</span></span> <span data-ttu-id="9de7b-139">데이터베이스가 READ_ONLY로 표시되고 로깅이 비활성화되며 **sysadmin** 고정 서버 역할의 멤버로 액세스가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-139">The database is marked READ_ONLY, logging is disabled, and access is limited to members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="9de7b-140">EMERGENCY는 주로 문제 해결을 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-140">EMERGENCY is primarily used for troubleshooting purposes.</span></span> <span data-ttu-id="9de7b-141">예를 들어 주의 대상으로 표시된 데이터베이스를 응급 상태로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-141">For example, a database marked as suspect can be set to the EMERGENCY state.</span></span> <span data-ttu-id="9de7b-142">이렇게 하면 시스템 관리자가 데이터베이스에 읽기 전용으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-142">This could permit the system administrator read-only access to the database.</span></span> <span data-ttu-id="9de7b-143">**sysadmin** 고정 서버 역할의 멤버만 데이터베이스를 응급 상태로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9de7b-143">Only members of the **sysadmin** fixed server role can set a database to the EMERGENCY state.</span></span>|  
  
## <a name="related-content"></a><span data-ttu-id="9de7b-144">관련 내용</span><span class="sxs-lookup"><span data-stu-id="9de7b-144">Related Content</span></span>  
 [<span data-ttu-id="9de7b-145">ALTER DATABASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9de7b-145">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
 [<span data-ttu-id="9de7b-146">미러링 상태&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9de7b-146">Mirroring States &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
 [<span data-ttu-id="9de7b-147">파일 상태</span><span class="sxs-lookup"><span data-stu-id="9de7b-147">File States</span></span>](file-states.md)  
  
  
