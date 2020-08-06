---
title: 작업 전송 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.f1
helpviewer_keywords:
- Transfer Jobs task [Integration Services]
ms.assetid: 1bf33885-9c5b-47e4-a549-f5920b66a1de
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d692934d5f7c8c1449b123ee8b9caf1d8bb34744
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638928"
---
# <a name="transfer-jobs-task"></a><span data-ttu-id="acb6d-102">작업 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="acb6d-102">Transfer Jobs Task</span></span>
  <span data-ttu-id="acb6d-103">작업 전송 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 사이에서 하나 이상의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트 작업을 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-103">The Transfer Jobs task transfers one or more [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="acb6d-104">작업 전송 태스크는 모든 작업 또는 지정된 작업만 전송하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-104">The Transfer Jobs task can be configured to transfer all jobs, or only specified jobs.</span></span> <span data-ttu-id="acb6d-105">또한 전송된 작업을 대상에서 활성화할지 여부를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-105">You can also indicate whether the transferred jobs are enabled at the destination.</span></span>  
  
 <span data-ttu-id="acb6d-106">전송할 작업이 대상에 이미 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-106">The jobs to be transferred may already exist on the destination.</span></span> <span data-ttu-id="acb6d-107">기존 태스크가 있을 경우 처리할 수 있는 방식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-107">The Transfer Jobs task can be configured to handle existing jobs in the following ways:</span></span>  
  
-   <span data-ttu-id="acb6d-108">기존 작업을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-108">Overwrite existing jobs.</span></span>  
  
-   <span data-ttu-id="acb6d-109">중복 작업이 있으면 전송이 실패하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-109">Fail the task when duplicate jobs exist.</span></span>  
  
-   <span data-ttu-id="acb6d-110">중복 작업을 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-110">Skip duplicate jobs.</span></span>  
  
 <span data-ttu-id="acb6d-111">작업 전송 태스크는 실행 시 하나 또는 두 개의 SMO 연결 관리자를 사용하여 원본과 대상을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-111">At run time, the Transfer Jobs task connects to the source and destination servers by using one or two SMO connection managers.</span></span> <span data-ttu-id="acb6d-112">SMO 연결 관리자는 작업 전송 태스크와 별도로 구성된 후 작업 전송 태스크에서 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-112">The SMO connection manager is configured separately from the Transfer Jobs task, and then is referenced in the Transfer Jobs task.</span></span> <span data-ttu-id="acb6d-113">SMO 연결 관리자는 액세스할 서버 및 서버 액세스 시 사용할 인증 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-113">The SMO connection manager specifies the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="acb6d-114">자세한 내용은 [SMO Connection Manager](../connection-manager/smo-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="acb6d-114">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
## <a name="transferring-jobs-between-instances-of-sql-server"></a><span data-ttu-id="acb6d-115">SQL Server 인스턴스 간 작업 전송</span><span class="sxs-lookup"><span data-stu-id="acb6d-115">Transferring Jobs Between Instances of SQL Server</span></span>  
 <span data-ttu-id="acb6d-116">작업 전송 태스크의 원본 및 대상으로는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-116">The Transfer Jobs task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span> <span data-ttu-id="acb6d-117">원본 또는 대상으로 사용하는 버전에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-117">There are no restrictions on which version to use as a source or destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="acb6d-118">이벤트</span><span class="sxs-lookup"><span data-stu-id="acb6d-118">Events</span></span>  
 <span data-ttu-id="acb6d-119">작업 전송 태스크는 전송된 작업 수를 보고하는 정보 이벤트와 작업을 덮어씀을 알리는 경고 이벤트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-119">The Transfer Jobs task raises an information event that reports the number of jobs transferred and a warning event when a job is overwritten.</span></span> <span data-ttu-id="acb6d-120">태스크는 작업 전송의 진행률을 보고하지 않으며 0% 및 100%(완료)만 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-120">The task does not report incremental progress of the job transfer; it reports only 0% and 100% completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="acb6d-121">실행 값</span><span class="sxs-lookup"><span data-stu-id="acb6d-121">Execution Value</span></span>  
 <span data-ttu-id="acb6d-122">태스크의 `ExecutionValue` 속성에 정의된 실행 값은 전송된 작업 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-122">The execution value, defined in the `ExecutionValue` property of the task, returns the number of jobs that are transferred.</span></span> <span data-ttu-id="acb6d-123">사용자 정의 변수를 작업 전송 태스크의 `ExecValueVariable` 속성에 할당하여 작업 전송에 대한 정보를 패키지에 있는 다른 개체에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-123">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Jobs task, information about the job transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="acb6d-124">자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md) 및 [패키지에서 변수 사용](../use-variables-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="acb6d-124">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="acb6d-125">로그 항목</span><span class="sxs-lookup"><span data-stu-id="acb6d-125">Log Entries</span></span>  
 <span data-ttu-id="acb6d-126">작업 전송 태스크는 다음과 같은 사용자 지정 로그 항목을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-126">The Transfer Jobs task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="acb6d-127">TransferJobsTaskStarTransferringObjects - 이 로그 항목은 전송이 시작되었음을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-127">TransferJobsTaskStarTransferringObjects   This log entry reports that the transfer has started.</span></span> <span data-ttu-id="acb6d-128">로그 항목에 시작 시간이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-128">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="acb6d-129">TransferJobsTaskFinishedTransferringObjects - 이 로그 항목은 전송이 완료되었음을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-129">TransferJobsTaskFinishedTransferringObjects    This log entry reports that the transfer has finished.</span></span> <span data-ttu-id="acb6d-130">로그 항목에 종료 시간이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-130">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="acb6d-131">이외에 `OnInformation` 이벤트의 로그 항목은 전송된 작업 수를 보고하며 `OnWarning` 이벤트의 로그 항목은 덮어쓴 각 대상 작업에 대해 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-131">In addition, a log entry for the `OnInformation` event reports the number of jobs that were transferred and a log entry for the `OnWarning` event is written for each job on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="acb6d-132">보안 및 사용 권한</span><span class="sxs-lookup"><span data-stu-id="acb6d-132">Security and Permissions</span></span>  
 <span data-ttu-id="acb6d-133">작업을 전송하려면 사용자는 sysadmin 고정 서버 역할의 멤버이거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 원본 및 대상 인스턴스 모두에 있는 msdb 데이터베이스의 고정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-133">To transfer jobs, the user must be a member of the sysadmin fixed server role or one of the fixed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles on the msdb database on the both the source and destination instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="configuration-of-the-transfer-jobs-task"></a><span data-ttu-id="acb6d-134">작업 전송 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="acb6d-134">Configuration of the Transfer Jobs Task</span></span>  
 <span data-ttu-id="acb6d-135">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acb6d-135">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="acb6d-136">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="acb6d-136">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="acb6d-137">작업 전송 태스크 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="acb6d-137">Transfer Jobs Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="acb6d-138">작업 전송 태스크 편집기&#40;작업 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="acb6d-138">Transfer Jobs Task Editor &#40;Jobs Page&#41;</span></span>](../transfer-jobs-task-editor-jobs-page.md)  
  
-   [<span data-ttu-id="acb6d-139">식 페이지</span><span class="sxs-lookup"><span data-stu-id="acb6d-139">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="acb6d-140">이러한 속성을 프로그래밍 방식으로 설정하는 방법은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="acb6d-140">For information about programmatically setting these properties, click the of the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferJobsTask.TransferJobsTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="acb6d-141">관련 작업</span><span class="sxs-lookup"><span data-stu-id="acb6d-141">Related Tasks</span></span>  
 <span data-ttu-id="acb6d-142">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="acb6d-142">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="acb6d-143">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="acb6d-143">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="acb6d-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="acb6d-144">See Also</span></span>  
 <span data-ttu-id="acb6d-145">[Integration Services 태스크](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="acb6d-145">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="acb6d-146">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="acb6d-146">Control Flow</span></span>](control-flow.md)  
  
  
