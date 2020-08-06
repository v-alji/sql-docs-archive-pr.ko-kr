---
title: master 저장 프로시저 전송 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfermasterspstask.f1
helpviewer_keywords:
- Transfer Master Stored Procedures task [Integration Services]
ms.assetid: 81702560-48a3-46d1-a469-e41304c7af8e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1915a3129eeb6e14c4315c37f2c6c2bf5b0d5412
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741160"
---
# <a name="transfer-master-stored-procedures-task"></a><span data-ttu-id="2d1eb-102">Master 저장 프로시저 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="2d1eb-102">Transfer Master Stored Procedures Task</span></span>
  <span data-ttu-id="2d1eb-103">master 저장 프로시저 전송 태스크는 **인스턴스의** master [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]데이터베이스 간에 하나 이상의 사용자 정의 저장 프로시저를 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-103">The Transfer Master Stored Procedures task transfers one or more user-defined stored procedures between **master** databases on instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2d1eb-104">**master** 데이터베이스에서 저장 프로시저를 전송하려면 프로시저 소유자가 dbo여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-104">To transfer a stored procedure from the **master** database, the owner of the procedure must be dbo.</span></span>  
  
 <span data-ttu-id="2d1eb-105">모든 저장 프로시저를 전송하거나 지정된 저장 프로시저만을 전송하도록 Master 저장 프로시저 전송 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-105">The Transfer Master Stored Procedures task can be configured to transfer all stored procedures or only specified stored procedures.</span></span> <span data-ttu-id="2d1eb-106">이 태스크는 시스템 저장 프로시저를 복사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-106">This task does not copy system stored procedures.</span></span>  
  
 <span data-ttu-id="2d1eb-107">전송될 Master 저장 프로시저가 대상에 이미 존재할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-107">The master stored procedures to be transferred may already exist on the destination.</span></span> <span data-ttu-id="2d1eb-108">다음 방식으로 기존의 저장 프로시저를 처리하도록 Master 저장 프로시저 전송 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-108">The Transfer Master Stored Procedures task can be configured to handle existing stored procedures in the following ways:</span></span>  
  
-   <span data-ttu-id="2d1eb-109">기존의 저장 프로시저를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-109">Overwrite existing stored procedures.</span></span>  
  
-   <span data-ttu-id="2d1eb-110">중복 저장 프로시저가 있는 경우 태스크가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-110">Fail the task when duplicate stored procedures exist.</span></span>  
  
-   <span data-ttu-id="2d1eb-111">중복 저장 프로시저를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-111">Skip duplicate stored procedures.</span></span>  
  
 <span data-ttu-id="2d1eb-112">Master 저장 프로시저 전송 태스크는 런타임에 두 개의 SMO 연결 관리자를 사용해 원본 서버와 대상 서버로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-112">At run time, the Transfer Master Stored Procedures task connects to the source and destination servers by using two SMO connection managers.</span></span> <span data-ttu-id="2d1eb-113">SMO 연결 관리자는 Master 저장 프로시저 전송 태스크와 별도로 구성되며 Master 저장 프로시저 전송 태스크에서 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-113">The SMO connection managers are configured separately from the Transfer Master Stored Procedures task, and then referenced in the Transfer Master Stored Procedures task.</span></span> <span data-ttu-id="2d1eb-114">SMO 연결 관리자는 액세스할 서버 및 사용할 인증 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-114">The SMO connection managers specify the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="2d1eb-115">자세한 내용은 [SMO Connection Manager](../connection-manager/smo-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-115">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
## <a name="transferring-stored-procedures-between-instances-of-sql-server"></a><span data-ttu-id="2d1eb-116">SQL Server 인스턴스 간 저장 프로시저 전송</span><span class="sxs-lookup"><span data-stu-id="2d1eb-116">Transferring Stored Procedures Between Instances of SQL Server</span></span>  
 <span data-ttu-id="2d1eb-117">Master 저장 프로시저 전송 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 원본 및 대상을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-117">The Transfer Master Stored Procedures task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="2d1eb-118">이벤트</span><span class="sxs-lookup"><span data-stu-id="2d1eb-118">Events</span></span>  
 <span data-ttu-id="2d1eb-119">Master 저장 프로시저 전송 태스크는 전송된 저장 프로시저의 수를 보고하는 정보 이벤트 및 저장 프로시저를 덮어쓰는 경우 경고 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-119">The task raises an information event that reports the number of stored procedures transferred and a warning event when a stored procedure is overwritten.</span></span>  
  
 <span data-ttu-id="2d1eb-120">Master 저장 프로시저 전송 태스크는 로그인 전송의 진행 상황은 보고하지 않으며 0% 및 100% 완료만 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-120">The Transfer Master Stored Procedures task does not report incremental progress of the login transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="2d1eb-121">실행 값</span><span class="sxs-lookup"><span data-stu-id="2d1eb-121">Execution Value</span></span>  
 <span data-ttu-id="2d1eb-122">태스크의 `ExecutionValue` 속성에 정의된 실행 값은 전송된 저장 프로시저의 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-122">The execution value, defined in the `ExecutionValue` property of the task, returns the number of stored procedures transferred.</span></span> <span data-ttu-id="2d1eb-123">Master 저장 프로시저 전송 태스크의 `ExecValueVariable` 속성에 사용자 정의 변수를 할당하면 패키지 내의 다른 개체에서 저장 프로시저 전송에 대한 정보를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-123">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Master Stored Procedures task, information about the stored procedure transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="2d1eb-124">자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md) 및 [패키지에서 변수 사용](../use-variables-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-124">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="2d1eb-125">로그 항목</span><span class="sxs-lookup"><span data-stu-id="2d1eb-125">Log Entries</span></span>  
 <span data-ttu-id="2d1eb-126">Master 저장 프로시저 전송 태스크는 다음 사용자 지정 로그 항목을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-126">The Transfer Master Stored Procedures task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="2d1eb-127">TransferStoredProceduresTaskStartTransferringObjects  이 로그 항목은 전송이 시작되었음을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-127">TransferStoredProceduresTaskStartTransferringObjects  This log entry reports that the transfer has started.</span></span> <span data-ttu-id="2d1eb-128">로그 항목에 시작 시간이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-128">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="2d1eb-129">TransferSStoredProceduresTaskFinishedTransferringObjects  이 로그 항목은 전송이 완료되었음을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-129">TransferSStoredProceduresTaskFinishedTransferringObjects  This log entry reports that the transfer has finished.</span></span> <span data-ttu-id="2d1eb-130">로그 항목에 종료 시간이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-130">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="2d1eb-131">또한 `OnInformation` 이벤트 로그 항목은 전송된 저장 프로시저의 수를 보고하며 대상의 저장 프로시저를 덮어쓸 때마다 `OnWarning` 이벤트 로그 항목이 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-131">In addition, a log entry for the `OnInformation` event reports the number of stored procedures that were transferred, and a log entry for the `OnWarning` event is written for each stored procedure on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="2d1eb-132">보안 및 사용 권한</span><span class="sxs-lookup"><span data-stu-id="2d1eb-132">Security and Permissions</span></span>  
 <span data-ttu-id="2d1eb-133">사용자는 원본에서 **master** 데이터베이스의 저장 프로시저 목록을 볼 수 있는 권한이 있어야 하며 sysadmin 서버 역할의 멤버이거나 대상 서버의 **master** 데이터베이스에서 저장 프로시저를 만들 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-133">The user must have permission to view the list of stored procedure in the **master** database on the source, and must be a member of the sysadmin server role or have permission to created stored procedures in the **master** database on the destination server.</span></span>  
  
## <a name="configuration-of-the-transfer-master-stored-procedures-task"></a><span data-ttu-id="2d1eb-134">Master 저장 프로시저 전송 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="2d1eb-134">Configuration of the Transfer Master Stored Procedures Task</span></span>  
 <span data-ttu-id="2d1eb-135">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-135">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="2d1eb-136">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-136">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="2d1eb-137">master 저장 프로시저 전송 태스크 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="2d1eb-137">Transfer Master Stored Procedures Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="2d1eb-138">master 저장 프로시저 전송 태스크 편집기&#40저장 프로시저 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="2d1eb-138">Transfer Master Stored Procedures Task Editor &#40;Stored Procedures Page&#41;</span></span>](../transfer-master-stored-procedures-task-editor-stored-procedures-page.md)  
  
-   [<span data-ttu-id="2d1eb-139">식 페이지</span><span class="sxs-lookup"><span data-stu-id="2d1eb-139">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="2d1eb-140">이러한 속성을 프로그래밍 방식으로 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-140">For information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferStoredProceduresTask.TransferStoredProceduresTask>  
  
### <a name="configuring-the-transfer-master-stored-procedures-task-programmatically"></a><span data-ttu-id="2d1eb-141">태스크 프로그래밍 방식으로 Master 저장 프로시저 전송 구성</span><span class="sxs-lookup"><span data-stu-id="2d1eb-141">Configuring the Transfer Master Stored Procedures Task Programmatically</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="2d1eb-142">관련 작업</span><span class="sxs-lookup"><span data-stu-id="2d1eb-142">Related Tasks</span></span>  
 <span data-ttu-id="2d1eb-143">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="2d1eb-143">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="2d1eb-144">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="2d1eb-144">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="2d1eb-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d1eb-145">See Also</span></span>  
 <span data-ttu-id="2d1eb-146">[SQL Server 개체 전송 태스크](transfer-sql-server-objects-task.md) </span><span class="sxs-lookup"><span data-stu-id="2d1eb-146">[Transfer SQL Server Objects Task](transfer-sql-server-objects-task.md) </span></span>  
 <span data-ttu-id="2d1eb-147">[Integration Services 태스크](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="2d1eb-147">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="2d1eb-148">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="2d1eb-148">Control Flow</span></span>](control-flow.md)  
  
  
