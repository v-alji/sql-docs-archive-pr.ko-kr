---
title: 복제 유지 관리 작업 실행(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server replication]
ms.assetid: 0dc485a0-5a50-41eb-a29d-f2b2fb920174
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9dc27c65e96a9f956ffa6d3edf9c72ed52f721a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736256"
---
# <a name="run-replication-maintenance-jobs-sql-server-management-studio"></a><span data-ttu-id="71aef-102">복제 유지 관리 작업 실행(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="71aef-102">Run Replication Maintenance Jobs (SQL Server Management Studio)</span></span>
  <span data-ttu-id="71aef-103">복제는 다음 유지 관리 작업을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="71aef-103">Replication uses the following maintenance jobs:</span></span>  
  
-   <span data-ttu-id="71aef-104">**데이터 유효성 검사에 실패한 구독 다시 초기화**</span><span class="sxs-lookup"><span data-stu-id="71aef-104">**Reinitialize subscriptions having data validation failures**</span></span>
-   <span data-ttu-id="71aef-105">**에이전트 기록 정리: 배포**</span><span class="sxs-lookup"><span data-stu-id="71aef-105">**Agent history clean up: distribution**</span></span>
-   <span data-ttu-id="71aef-106">**배포에 대한 복제 모니터링 리프레셔**</span><span class="sxs-lookup"><span data-stu-id="71aef-106">**Replication monitoring refresher for distribution.**</span></span>
-   <span data-ttu-id="71aef-107">**복제 에이전트 점검**</span><span class="sxs-lookup"><span data-stu-id="71aef-107">**Replication agents checkup**</span></span>
-   <span data-ttu-id="71aef-108">**배포 기록 정리: 배포**</span><span class="sxs-lookup"><span data-stu-id="71aef-108">**Distribution clean up: distribution**</span></span>
-   <span data-ttu-id="71aef-109">**만료된 구독 정리**</span><span class="sxs-lookup"><span data-stu-id="71aef-109">**Expired subscription clean up**</span></span>  
  
 <span data-ttu-id="71aef-110">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]의 **작업** 폴더와 복제 모니터의 **에이전트** 탭에서 위와 같은 작업을 시작하고 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="71aef-110">Start and stop these jobs from the **Jobs** folder in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and from the **Agents** tab in Replication Monitor.</span></span> <span data-ttu-id="71aef-111">복제 모니터를 시작하는 방법은 [복제 모니터 시작](../monitor/start-the-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71aef-111">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span> <span data-ttu-id="71aef-112">동일한 폴더와 탭에서 사용 가능한 **작업 속성 - \<Job>** 대화 상자에서 각 작업의 속성을 보고 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="71aef-112">View and modify properties for each job in the **Job Properties - \<Job>** dialog box, which is available from the same folder and tab.</span></span>  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-management-studio"></a><span data-ttu-id="71aef-113">Management Studio에서 복제 유지 관리 작업을 시작하거나 중지하려면</span><span class="sxs-lookup"><span data-stu-id="71aef-113">To start or stop a replication maintenance job in Management Studio</span></span>  
  
1.  <span data-ttu-id="71aef-114">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]에서 배포자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="71aef-114">Connect to the Distributor in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="71aef-115">**SQL Server 에이전트** 폴더를 확장한 다음 **작업** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="71aef-115">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="71aef-116">작업을 마우스 오른쪽 단추로 클릭한 다음 **작업 시작** 또는 **작업 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71aef-116">Right-click a job, and then click **Start Job** or **Stop Job**.</span></span>  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-replication-monitor"></a><span data-ttu-id="71aef-117">복제 모니터에서 복제 유지 관리 작업을 시작하거나 중지하려면</span><span class="sxs-lookup"><span data-stu-id="71aef-117">To start or stop a replication maintenance job in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="71aef-118">복제 모니터에서 게시자 그룹을 확장한 다음 해당 게시자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="71aef-118">Expand a Publisher group in Replication Monitor, and then select a Publisher.</span></span>  
  
2.  <span data-ttu-id="71aef-119">**에이전트** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71aef-119">Click the **Agents** tab.</span></span>  
  
3.  <span data-ttu-id="71aef-120">표에서 작업을 마우스 오른쪽 단추로 클릭한 다음 **작업 시작** 또는 **작업 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71aef-120">Right-click a job in the grid, and then click **Start Job** or **Stop Job**.</span></span>  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-management-studio"></a><span data-ttu-id="71aef-121">Management Studio에서 복제 유지 관리 작업의 속성을 보고 수정하려면</span><span class="sxs-lookup"><span data-stu-id="71aef-121">To view and modify properties for a replication maintenance job in Management Studio</span></span>  
  
1.  <span data-ttu-id="71aef-122">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]에서 배포자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="71aef-122">Connect to the Distributor in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="71aef-123">**SQL Server 에이전트** 폴더를 확장한 다음 **작업** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="71aef-123">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="71aef-124">작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71aef-124">Right-click a job, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="71aef-125">**작업 속성 - \<Job>** 대화 상자에서 필요한 경우 속성을 수정한 다음, **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71aef-125">In the **Job Properties - \<Job>** dialog box, modify any properties if necessary, and then click **OK**.</span></span>  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-replication-monitor"></a><span data-ttu-id="71aef-126">복제 모니터에서 복제 유지 관리 작업의 속성을 보고 수정하려면</span><span class="sxs-lookup"><span data-stu-id="71aef-126">To view and modify properties for a replication maintenance job in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="71aef-127">복제 모니터에서 게시자 그룹을 확장한 다음 해당 게시자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="71aef-127">Expand a Publisher group in Replication Monitor, and then select a Publisher.</span></span>  
  
2.  <span data-ttu-id="71aef-128">**에이전트** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71aef-128">Click the **Agents** tab.</span></span>  
  
3.  <span data-ttu-id="71aef-129">표에서 작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71aef-129">Right-click a job in the grid, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="71aef-130">**작업 속성 - \<Job>** 대화 상자에서 필요한 경우 속성을 수정한 다음, **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71aef-130">In the **Job Properties - \<Job>** dialog box, modify any properties if necessary, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71aef-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71aef-131">See Also</span></span>  
 <span data-ttu-id="71aef-132">[복제 에이전트 시작 및 중지&#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="71aef-132">[Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="71aef-133">[복제 모니터를 사용하여 정보 보기 및 태스크 수행](../monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="71aef-133">[View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="71aef-134">복제 에이전트 관리</span><span class="sxs-lookup"><span data-stu-id="71aef-134">Replication Agent Administration</span></span>](../agents/replication-agent-administration.md)  
  
  
