---
title: 서버 폴링 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- target servers [SQL Server], polling interval
- polling master servers [SQL Server]
- server polling [SQL Server]
- master servers [SQL Server], polling
- polling interval [SQL Server]
ms.assetid: 96f5fd43-3edd-4418-9dd0-4d34e618890e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6370e53083d2cf818e8c8b09752d49e092755a46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652533"
---
# <a name="poll-servers"></a><span data-ttu-id="6c68f-102">서버 폴링</span><span class="sxs-lookup"><span data-stu-id="6c68f-102">Poll Servers</span></span>
  <span data-ttu-id="6c68f-103">다중 서버 관리가 구현될 때 대상 서버는 정기적으로 마스터 서버에 연결하여 실행된 작업에 대한 정보를 업로드하고 새 작업을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="6c68f-103">When multiserver administration is implemented, target servers periodically contact the master server to upload information on jobs that have been executed, and download new jobs.</span></span> <span data-ttu-id="6c68f-104">마스터 서버에 연결하는 프로세스를 *서버 폴링* 이라고 하며 서버 폴링은 정기적인 *폴링 간격*마다 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6c68f-104">The process of contacting the master server is called *server polling,* which takes place at regular *polling intervals.*</span></span>  
  
## <a name="polling-intervals"></a><span data-ttu-id="6c68f-105">폴링 간격</span><span class="sxs-lookup"><span data-stu-id="6c68f-105">Polling Intervals</span></span>  
 <span data-ttu-id="6c68f-106">폴링 간격(기본적으로 1분)은 대상 서버가 명령을 다운로드하고 작업 실행 결과를 업로드하기 위해 마스터 서버에 연결하는 시간 간격을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="6c68f-106">The polling interval (one minute by default) controls how frequently the target server connects to the master server to download instructions and upload the results of job execution.</span></span>  
  
 <span data-ttu-id="6c68f-107">대상 서버가 마스터 서버를 폴링할 때는 **msdb** 데이터베이스의 **sysdownloadlist** 테이블에서 대상 서버에 할당된 작업을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="6c68f-107">When a target server polls the master server, it reads the operations assigned to the target server from the **sysdownloadlist** table in the **msdb** database.</span></span> <span data-ttu-id="6c68f-108">이 작업에서는 다중 서버 작업 및 대상 서버의 다양한 작업 항목을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="6c68f-108">These operations control multiserver jobs and various aspects of the behavior of a target server.</span></span> <span data-ttu-id="6c68f-109">작업 삭제, 작업 삽입, 작업 시작, 대상 서버의 폴링 간격 업데이트 등이 이러한 작업의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="6c68f-109">Examples of operations include deleting a job, inserting a job, starting a job, and updating the polling interval of a target server.</span></span>  
  
 <span data-ttu-id="6c68f-110">작업은 다음 방법 중 하나로 **sysdownloadlist** 테이블에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c68f-110">Operations are posted to the **sysdownloadlist** table in either of the following ways:</span></span>  
  
-   <span data-ttu-id="6c68f-111">명시적으로 **sp_post_msx_operation** 저장 프로시저를 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="6c68f-111">Explicitly by using the **sp_post_msx_operation** stored procedure.</span></span>  
  
-   <span data-ttu-id="6c68f-112">암시적으로 다른 작업 저장 프로시저를 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="6c68f-112">Implicitly by using other job stored procedures.</span></span>  
  
 <span data-ttu-id="6c68f-113">작업 저장 프로시저를 사용하여 다중 서버 작업 일정 또는 작업 단계를 수정하거나 SQL-DMO(SQL Distributed Management Objects)를 사용하여 다중 서버 작업을 제어하는 경우 다중 서버 작업의 단계 또는 일정을 수정한 후 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6c68f-113">If you use job stored procedures to modify multiserver job schedules or job steps, or SQL Distributed Management Objects (SQL-DMO) to control multiserver jobs, issue the following command after modifying a multiserver job's steps or schedules:</span></span>  
  
```  
EXECUTE msdb.dbo.sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 <span data-ttu-id="6c68f-114">이 명령을 실행하면 대상 서버가 현재 작업 정의와 동기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c68f-114">Issue this command keeps the target servers synchronized with the current job definition.</span></span>  
  
 <span data-ttu-id="6c68f-115">다음의 경우에는 작업을 명시적으로 게시하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c68f-115">You do not have to post operations explicitly if you use the following:</span></span>  
  
-   <span data-ttu-id="6c68f-116">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 다중 서버 작업을 제어하는 경우</span><span class="sxs-lookup"><span data-stu-id="6c68f-116">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to control multiserver jobs.</span></span>  
  
-   <span data-ttu-id="6c68f-117">작업 저장 프로시저를 사용하여 작업 일정이나 작업 단계를 수정하지 않을 경우</span><span class="sxs-lookup"><span data-stu-id="6c68f-117">Job stored procedures that do not modify job schedules or job steps.</span></span>  
  
 <span data-ttu-id="6c68f-118">**대상 서버가 마스터 서버를 폴링하도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="6c68f-118">**To force a target server to poll the master server**</span></span>  
  
-   [<span data-ttu-id="6c68f-119">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6c68f-119">SQL Server Management Studio</span></span>](force-a-target-server-to-poll-the-master-server.md)  
  
-   [<span data-ttu-id="6c68f-120">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6c68f-120">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="6c68f-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6c68f-121">See Also</span></span>  
 [<span data-ttu-id="6c68f-122">이벤트 관리</span><span class="sxs-lookup"><span data-stu-id="6c68f-122">Manage Events</span></span>](manage-events.md)  
  
  
