---
title: 기록 정리 태스크(유지 관리 계획) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.historycleanup.f1
helpviewer_keywords:
- History Cleanup Task dialog box
ms.assetid: 66bb6c39-958c-4053-a27f-b1118d2567f5
ms.reviewer: ''
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 03ff35b14fc13d2b4446b15501114489b52c421e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653350"
---
# <a name="history-cleanup-task-maintenance-plan"></a><span data-ttu-id="708dd-102">기록 정리 태스크(유지 관리 계획)</span><span class="sxs-lookup"><span data-stu-id="708dd-102">History Cleanup Task (Maintenance Plan)</span></span>

  <span data-ttu-id="708dd-103">**기록 정리 태스크** 대화 상자를 사용하여 msdb 데이터베이스의 테이블에서 오래된 기록 정보를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-103">Use the **History Cleanup Task** dialog to discard old historical information from tables in the msdb database.</span></span> <span data-ttu-id="708dd-104">이 태스크는 백업 및 복원 기록, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 기록 및 유지 관리 계획 기록의 삭제를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-104">This task supports deleting backup and restore history, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Job history, and maintenance plan history.</span></span>  
  
 <span data-ttu-id="708dd-105">이 문은 **sp_purge_jobhistory** 문과 **sp_delete_backuphistory** 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-105">This statement uses the **sp_purge_jobhistory** and **sp_delete_backuphistory** statements.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="708dd-106">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="708dd-106">UI element list</span></span>  
 <span data-ttu-id="708dd-107">**연결**</span><span class="sxs-lookup"><span data-stu-id="708dd-107">**Connection**</span></span>  
 <span data-ttu-id="708dd-108">이 태스크를 수행할 때 사용할 서버 연결을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-108">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="708dd-109">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="708dd-109">**New**</span></span>  
 <span data-ttu-id="708dd-110">이 태스크를 수행할 때 사용할 새 서버 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-110">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="708dd-111">**새 연결** 대화 상자는 뒷부분에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-111">The **New Connection** dialog box is described later in this topic.</span></span>  
  
 <span data-ttu-id="708dd-112">**백업 및 복원 기록**</span><span class="sxs-lookup"><span data-stu-id="708dd-112">**Backup and restore history**</span></span>  
 <span data-ttu-id="708dd-113">최근 백업을 만들었을 당시의 기록을 보존하면 데이터베이스를 복원하려고 할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 복구 계획을 만드는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-113">Retaining records of when recent backups were created can help [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] create a recovery plan when you want to restore a database.</span></span> <span data-ttu-id="708dd-114">보존 기간은 적어도 전체 데이터베이스 백업 빈도만큼 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-114">The retention period should be at least the frequency of full database back ups.</span></span>  
  
 <span data-ttu-id="708dd-115">**SQL Server 에이전트 작업 기록**</span><span class="sxs-lookup"><span data-stu-id="708dd-115">**SQL Server Agent Job history**</span></span>  
 <span data-ttu-id="708dd-116">이 기록을 사용하면 실패한 작업의 문제를 해결하거나 데이터베이스 동작의 발생 이유를 확인하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-116">This history can help you troubleshoot failed jobs, or determine why database actions occurred.</span></span>  
  
 <span data-ttu-id="708dd-117">**유지 관리 계획 기록**</span><span class="sxs-lookup"><span data-stu-id="708dd-117">**Maintenance plan history**</span></span>  
 <span data-ttu-id="708dd-118">이 기록을 사용하면 실패한 유지 관리 계획 동작의 문제를 해결하거나 데이터베이스 작업의 발생 이유를 확인하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-118">This history can help you troubleshoot failed maintenance plan jobs, or determine why database actions occurred.</span></span>  
  
 <span data-ttu-id="708dd-119">**다음보다 오래된 기록 데이터 제거**</span><span class="sxs-lookup"><span data-stu-id="708dd-119">**Remove historical data older than**</span></span>  
 <span data-ttu-id="708dd-120">삭제할 항목의 보존 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-120">Specify age of items that you want to delete.</span></span>  
  
 <span data-ttu-id="708dd-121">**T-SQL 보기**</span><span class="sxs-lookup"><span data-stu-id="708dd-121">**View T-SQL**</span></span>  
 <span data-ttu-id="708dd-122">선택한 옵션을 기반으로 서버에 대해 수행한 이 태스크의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-122">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="708dd-123">영향을 받은 개체 수가 많은 경우에는 표시하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-123">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="708dd-124">새 연결 대화 상자</span><span class="sxs-lookup"><span data-stu-id="708dd-124">New Connection Dialog Box</span></span>  
 <span data-ttu-id="708dd-125">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="708dd-125">**Connection name**</span></span>  
 <span data-ttu-id="708dd-126">새 연결의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-126">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="708dd-127">**서버 이름 선택 또는 입력**</span><span class="sxs-lookup"><span data-stu-id="708dd-127">**Select or enter a server name**</span></span>  
 <span data-ttu-id="708dd-128">이 태스크를 수행할 때 연결할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-128">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="708dd-129">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="708dd-129">**Refresh**</span></span>  
 <span data-ttu-id="708dd-130">사용할 수 있는 서버 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-130">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="708dd-131">**서버 로그온 정보 입력**</span><span class="sxs-lookup"><span data-stu-id="708dd-131">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="708dd-132">서버에 대한 인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-132">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="708dd-133">**Windows NT 통합 보안 사용**</span><span class="sxs-lookup"><span data-stu-id="708dd-133">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="708dd-134">Microsoft Windows 인증을 사용하여 SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-134">Connect to an instance of the SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] with Microsoft Windows Authentication.</span></span>  
  
 <span data-ttu-id="708dd-135">**특정 사용자 이름 및 암호 사용**</span><span class="sxs-lookup"><span data-stu-id="708dd-135">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="708dd-136">SQL Server 인증을 사용하여 SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-136">Connect to an instance of the SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] using SQL Server Authentication.</span></span> <span data-ttu-id="708dd-137">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-137">This option is not available.</span></span>  
  
 <span data-ttu-id="708dd-138">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="708dd-138">**User name**</span></span>  
 <span data-ttu-id="708dd-139">인증 시 사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-139">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="708dd-140">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-140">This option is not available.</span></span>  
  
 <span data-ttu-id="708dd-141">**암호**</span><span class="sxs-lookup"><span data-stu-id="708dd-141">**Password**</span></span>  
 <span data-ttu-id="708dd-142">인증 시 사용할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-142">Provide a password to use when authenticating.</span></span> <span data-ttu-id="708dd-143">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="708dd-143">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="708dd-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="708dd-144">See Also</span></span>  
 <span data-ttu-id="708dd-145">[sp_purge_jobhistory&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="708dd-145">[sp_purge_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql) </span></span>  
 [<span data-ttu-id="708dd-146">sp_delete_backuphistory&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="708dd-146">sp_delete_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)  
  
  
