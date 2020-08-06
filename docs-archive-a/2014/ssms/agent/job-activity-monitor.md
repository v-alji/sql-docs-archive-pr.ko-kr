---
title: 작업 활동 모니터 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.ACTIVITYMON.F1
- sql12.ag.jobactivitymonitor.alljobs.f1
ms.assetid: 11f2182c-5f71-46f8-8d2b-74f0fc48f2d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6f89d5448f0885c85229c2808ee6f85bf6fa071
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731355"
---
# <a name="job-activity-monitor"></a><span data-ttu-id="5581b-102">작업 활동 모니터</span><span class="sxs-lookup"><span data-stu-id="5581b-102">Job Activity Monitor</span></span>
  <span data-ttu-id="5581b-103">이 페이지를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업의 현재 활동을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-103">Use this page to view the current activity of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span> <span data-ttu-id="5581b-104">**필터** 를 클릭하여 표시되는 작업의 수를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-104">Click **Filter** to limit the jobs displayed.</span></span> <span data-ttu-id="5581b-105">**에이전트 작업 활동** 표는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-105">The **Agent Job Activity** grid is read-only.</span></span> <span data-ttu-id="5581b-106">표를 정렬하려면 열 머리글을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-106">Click on the column headers to sort the grid.</span></span> <span data-ttu-id="5581b-107">작업을 수정하려면 작업을 두 번 클릭하여 **작업 속성** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-107">To modify a job, double-click the job to open the **Job Properties** dialog box.</span></span> <span data-ttu-id="5581b-108">표에서 작업을 마우스 오른쪽 단추로 클릭하여 모든 작업 단계의 실행을 시작하거나, 특정 작업 단계에서 시작하거나, 작업을 활성화 또는 비활성화하거나, 작업을 새로 고치거나, 작업을 삭제하거나, 작업 기록이나 작업 속성을 확인하는 등의 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-108">Right-click a job in the grid to start it running all job steps, start at a particular job step, disable or enable the job, refresh the job, delete the job, view the history of the job, or view the properties of the job.</span></span> <span data-ttu-id="5581b-109">현재 정보로 표를 업데이트하려면 **새로 고침** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-109">Click **Refresh** to update the grid with current information.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5581b-110">옵션</span><span class="sxs-lookup"><span data-stu-id="5581b-110">Options</span></span>  
 <span data-ttu-id="5581b-111">**이름**</span><span class="sxs-lookup"><span data-stu-id="5581b-111">**Name**</span></span>  
 <span data-ttu-id="5581b-112">작업의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-112">Name of the job.</span></span>  
  
 <span data-ttu-id="5581b-113">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="5581b-113">**Enabled**</span></span>  
 <span data-ttu-id="5581b-114">작업을 사용할지(**예**) 또는 사용하지 않을지(**아니요**)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-114">Whether the job is enabled (**yes**) or not enabled (**no**).</span></span>  
  
 <span data-ttu-id="5581b-115">**상태** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="5581b-115">**Status** <sup>1</sup></span></span>  
 <span data-ttu-id="5581b-116">작업의 현재 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-116">Current status of the job.</span></span>  
  
 <span data-ttu-id="5581b-117">**마지막 실행 결과**</span><span class="sxs-lookup"><span data-stu-id="5581b-117">**Last Run Outcome**</span></span>  
 <span data-ttu-id="5581b-118">마지막으로 실행했을 때의 작업 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-118">Job status when last run.</span></span>  
  
 <span data-ttu-id="5581b-119">**마지막 실행**</span><span class="sxs-lookup"><span data-stu-id="5581b-119">**Last Run**</span></span>  
 <span data-ttu-id="5581b-120">서버의 로컬 날짜 및 시간을 사용하여 마지막으로 작업을 실행한 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-120">Date and time job was last run using the local date and time of the server.</span></span>  
  
 <span data-ttu-id="5581b-121">**다음 실행** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="5581b-121">**Next Run** <sup>1</sup></span></span>  
 <span data-ttu-id="5581b-122">서버의 로컬 날짜 및 시간을 사용하여 다음에 작업을 실행하기로 예약한 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-122">Date and time the job is next scheduled to run using the local date and time of the server.</span></span>  
  
 <span data-ttu-id="5581b-123">**범주**</span><span class="sxs-lookup"><span data-stu-id="5581b-123">**Category**</span></span>  
 <span data-ttu-id="5581b-124">작업에 지정된 작업 범주입니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-124">The job category assigned to the job.</span></span>  
  
 <span data-ttu-id="5581b-125">**실행할**</span><span class="sxs-lookup"><span data-stu-id="5581b-125">**Runnable**</span></span>  
 <span data-ttu-id="5581b-126">작업을 실행할 수 있으면**예** 이고 작업을 실행할 수 없으면 **아니요** 입니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-126">**Yes** if the job can be run; **No** if the job cannot be run.</span></span> <span data-ttu-id="5581b-127">단계나 대상 서버가 없는 경우 작업을 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-127">A job is not runnable if it has no steps or if it has no target server.</span></span>  
  
 <span data-ttu-id="5581b-128">**예약**</span><span class="sxs-lookup"><span data-stu-id="5581b-128">**Scheduled**</span></span>  
 <span data-ttu-id="5581b-129">작업이 작업 일정에 할당되어 있으면**예** 이고, 그렇지 않으면 **아니요** 입니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-129">**Yes** if the job is assigned to a job schedule; **No** if the job has no schedule.</span></span>  
  
 <span data-ttu-id="5581b-130"><sup>1</sup> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Sysadmin 고정 서버 역할과 서버 관리자 그룹의 멤버만이 열의 값을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-130"><sup>1</sup>Only members of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin fixed server role and the server administrators group can see values in this column.</span></span> <span data-ttu-id="5581b-131">SQLAgentOperatorRole 역할의 멤버는 이 열의 값을 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-131">Members of the SQLAgentOperatorRole role cannot see values in this column.</span></span>  
  
#### <a name="to-open-the-job-activity-monitor"></a><span data-ttu-id="5581b-132">작업 활동 모니터를 열려면</span><span class="sxs-lookup"><span data-stu-id="5581b-132">To open the Job Activity Monitor</span></span>  
  
-   <span data-ttu-id="5581b-133">**개체 탐색기**에서 해당 서버를 확장하고 **SQL Server 에이전트**를 확장한 다음 **작업 활동 모니터**를 마우스 오른쪽 단추로 클릭하고 **작업 활동 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5581b-133">In **Object Explorer**, expand your server, expand **SQL Server Agent**, right-click **Job Activity Monitor**, and then click **View Job Activity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5581b-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5581b-134">See Also</span></span>  
 [<span data-ttu-id="5581b-135">작업 활동 모니터링</span><span class="sxs-lookup"><span data-stu-id="5581b-135">Monitor Job Activity</span></span>](monitor-job-activity.md)  
  
  
