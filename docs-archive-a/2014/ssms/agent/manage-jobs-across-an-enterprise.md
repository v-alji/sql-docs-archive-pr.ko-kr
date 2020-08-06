---
title: 기업 내 작업 관리 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiserver job management [SQL Server]
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
- target servers [SQL Server], job changes
ms.assetid: 4fe7f6c6-f89b-4430-979c-4994a5dcf7a6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 385435302b2e987c86afb17eaebf90e91bc93e56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649346"
---
# <a name="manage-jobs-across-an-enterprise"></a><span data-ttu-id="e3746-102">기업 내 작업 관리</span><span class="sxs-lookup"><span data-stu-id="e3746-102">Manage Jobs Across an Enterprise</span></span>
  <span data-ttu-id="e3746-103">외부에서 다중 서버 작업 정의를 변경 하는 경우에는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 대상 서버에서 업데이트 된 작업을 다시 다운로드할 수 있도록 변경 내용을 다운로드 목록에 게시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3746-103">If you make changes to multiserver job definitions outside [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you must post the changes to the download list so that target servers can download the updated job again.</span></span> <span data-ttu-id="e3746-104">대상 서버가 최근의 작업 정의를 갖도록 하려면 다중 서버 작업을 업데이트한 후 다음과 같이 INSERT 명령을 게시하십시오.</span><span class="sxs-lookup"><span data-stu-id="e3746-104">To ensure that target servers have current job definitions, post an INSERT instruction after you update the multiserver job, as follows:</span></span>  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 <span data-ttu-id="e3746-105">다중 서버 작업이 수정되었음을 대상 서버에 알리려면 다음 프로시저 중 하나를 사용한 후 앞의 명령을 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3746-105">To notify target servers that a multiserver job has been modified, you must invoke the preceding command after using any of the following procedures:</span></span>  
  
-   [<span data-ttu-id="e3746-106">sp_add_jobstep(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e3746-106">sp_add_jobstep (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [<span data-ttu-id="e3746-107">sp_update_jobstep(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e3746-107">sp_update_jobstep (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)  
  
-   [<span data-ttu-id="e3746-108">sp_delete_jobstep(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e3746-108">sp_delete_jobstep (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql)  
  
-   [<span data-ttu-id="e3746-109">sp_attach_schedule&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e3746-109">sp_attach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [<span data-ttu-id="e3746-110">Transact-sql&#41;sp_detach_schedule &#40;</span><span class="sxs-lookup"><span data-stu-id="e3746-110">sp_detach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql)  
  
    > [!NOTE]  
    >  <span data-ttu-id="e3746-111">저장 프로시저에서는 요청된 변경 내용을 다운로드 목록에 자동 게시하기 때문에 **sp_update_job** 이나 **sp_delete_job** 을 호출한 다음에 **sp_post_msx_operation**을 호출하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3746-111">It is not necessary to call **sp_post_msx_operation** after you call **sp_update_job** or **sp_delete_job**, because these stored procedures post the required changes to the download list automatically.</span></span>  
  
 <span data-ttu-id="e3746-112">다음은 기업 전체에 걸쳐 업무 관리에 사용하는 공통 태스크입니다.</span><span class="sxs-lookup"><span data-stu-id="e3746-112">The following are common tasks for managing jobs across an enterprise:</span></span>  
  
 <span data-ttu-id="e3746-113">**대상 서버의 상태를 점검하려면**</span><span class="sxs-lookup"><span data-stu-id="e3746-113">**To check the status of a target server**</span></span>  
  
-   [<span data-ttu-id="e3746-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e3746-114">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql)  
  
-   [<span data-ttu-id="e3746-115">SMO(SQL Server 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="e3746-115">SQL Server Management Objects (SMO)</span></span>](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 <span data-ttu-id="e3746-116">**작업의 대상 서버를 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="e3746-116">**To change the target servers for a job**</span></span>  
  
-   [<span data-ttu-id="e3746-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e3746-117">SQL Server Management Studio</span></span>](modify-the-target-servers-for-a-job.md)  
  
-   [<span data-ttu-id="e3746-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e3746-118">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  
-   [<span data-ttu-id="e3746-119">SMO(SQL Server 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="e3746-119">SQL Server Management Objects (SMO)</span></span>](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 <span data-ttu-id="e3746-120">**대상 서버의 위치를 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="e3746-120">**To change the location of a target server**</span></span>  
  
-   [<span data-ttu-id="e3746-121">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e3746-121">SQL Server Management Studio</span></span>](../sql-server-management-studio-ssms.md)  
  
-   [<span data-ttu-id="e3746-122">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e3746-122">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)  
  
-   [<span data-ttu-id="e3746-123">SMO(SQL Server 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="e3746-123">SQL Server Management Objects (SMO)</span></span>](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 <span data-ttu-id="e3746-124">**대상 서버 클럭을 동기화하려면**</span><span class="sxs-lookup"><span data-stu-id="e3746-124">**To synchronize target server clocks**</span></span>  
  
-   [<span data-ttu-id="e3746-125">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e3746-125">SQL Server Management Studio</span></span>](synchronize-target-server-clocks-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="e3746-126">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e3746-126">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql)  
  
 <span data-ttu-id="e3746-127">**대상 서버가 마스터 서버를 폴링하도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="e3746-127">**To force a target server to poll the master server**</span></span>  
  
-   [<span data-ttu-id="e3746-128">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e3746-128">SQL Server Management Studio</span></span>](force-a-target-server-to-poll-the-master-server.md)  
  
-   [<span data-ttu-id="e3746-129">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e3746-129">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="e3746-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3746-130">See Also</span></span>  
 [<span data-ttu-id="e3746-131">이벤트 관리</span><span class="sxs-lookup"><span data-stu-id="e3746-131">Manage Events</span></span>](manage-events.md)  
  
  
