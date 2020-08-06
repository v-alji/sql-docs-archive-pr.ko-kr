---
title: 오류 메시지 전송 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.f1
helpviewer_keywords:
- Transfer Error Messages task [Integration Services]
ms.assetid: da702289-035a-4d14-bd74-04461fbfee1b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 952acc28a79fef7e7351c97400e05bc7ba5b9243
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638929"
---
# <a name="transfer-error-messages-task"></a><span data-ttu-id="c874f-102">오류 메시지 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="c874f-102">Transfer Error Messages Task</span></span>
  <span data-ttu-id="c874f-103">오류 메시지 전송 태스크에서는 하나 이상의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자 정의 오류 메시지를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스 간에 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-103">The Transfer Error Messages task transfers one or more [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user-defined error messages between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c874f-104">사용자 정의 메시지는 50000보다 크거나 같은 식별자를 가진 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-104">User-defined messages are messages with an identifier that is equal to or greater than 50000.</span></span> <span data-ttu-id="c874f-105">50000보다 작은 식별자를 가진 메시지는 시스템 오류 메시지이며 오류 메시지 전송 태스크를 사용하여 전송할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-105">Messages with an identifier less than 50000 are system error messages, and cannot be transferred by using the Transfer Error Messages task.</span></span>  
  
 <span data-ttu-id="c874f-106">모든 오류 메시지를 전송하거나 지정한 오류 메시지만 전송하도록 오류 메시지 전송 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-106">The Transfer Error Messages task can be configured to transfer all error messages, or only the specified error messages.</span></span> <span data-ttu-id="c874f-107">사용자 정의 오류 메시지는 여러 다른 언어로 제공될 수 있으며 지정된 언어로만 메시지를 전송하도록 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-107">User-defined error messages may be available in a number of different languages and the task can be configured to transfer only messages in selected languages.</span></span> <span data-ttu-id="c874f-108">다른 언어 버전의 메시지를 대상 서버로 전송하려면 해당 서버에 1033 코드 페이지를 사용하는 us_english 버전의 메시지가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-108">A us_english version of the message that uses code page 1033 must exist on the destination server before you can transfer other language versions of the message to that server.</span></span>  
  
 <span data-ttu-id="c874f-109">master 데이터베이스의 sysmessages 테이블에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용하는 시스템 및 사용자 정의된 모든 오류 메시지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-109">The sysmessages table in the master database contains all the error messages-both system and user-defined-that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses.</span></span>  
  
 <span data-ttu-id="c874f-110">전송할 사용자 정의 메시지가 이미 대상에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-110">The user-defined messages to be transferred may already exist on the destination.</span></span> <span data-ttu-id="c874f-111">식별자 및 언어가 동일한 경우 오류 메시지는 중복 오류 메시지로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-111">An error message is defined as a duplicate error message if the identifier and the language are the same.</span></span> <span data-ttu-id="c874f-112">다음 방식으로 기존 오류 메시지를 처리하도록 오류 메시지 전송 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-112">The Transfer Error Messages task can be configured to handle existing error messages in the following ways:</span></span>  
  
-   <span data-ttu-id="c874f-113">기존 오류 메시지를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-113">Overwrite existing error messages.</span></span>  
  
-   <span data-ttu-id="c874f-114">중복 메시지가 있는 경우 태스크가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-114">Fail the task when duplicate messages exist.</span></span>  
  
-   <span data-ttu-id="c874f-115">중복 오류 메시지를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-115">Skip duplicate error messages.</span></span>  
  
 <span data-ttu-id="c874f-116">오류 메시지 전송 태스크는 런타임에 한 개 또는 두 개의 SMO 연결 관리자를 사용하여 원본 및 대상 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-116">At run time, the Transfer Error Messages task connects to the source and destination servers by using one or two SMO connection managers.</span></span> <span data-ttu-id="c874f-117">SMO 연결 관리자는 오류 메시지 전송 태스크와 별도로 구성된 후 오류 메시지 전송 태스크에서 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-117">The SMO connection manager is configured separately from the Transfer Error Messages task, and then is referenced in the Transfer Error Messages task.</span></span> <span data-ttu-id="c874f-118">SMO 연결 관리자는 액세스할 서버 및 서버 액세스 시 사용할 인증 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-118">The SMO connection manager specifies the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="c874f-119">자세한 내용은 [SMO Connection Manager](../connection-manager/smo-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c874f-119">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
 <span data-ttu-id="c874f-120">오류 메시지 전송 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 원본 및 대상을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-120">The Transfer Error Messages task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span> <span data-ttu-id="c874f-121">원본 또는 대상으로 사용하는 버전에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-121">There are no restrictions on which version to use as a source or destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="c874f-122">이벤트</span><span class="sxs-lookup"><span data-stu-id="c874f-122">Events</span></span>  
 <span data-ttu-id="c874f-123">이 태스크는 전송된 오류 메시지의 수를 보고하는 정보 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-123">The task raises an information event that reports the number of error messages that have been transferred.</span></span>  
  
 <span data-ttu-id="c874f-124">오류 메시지 전송 태스크는 오류 메시지를 전송하는 진행 과정은 보고하지 않으며 0% 및 100% 완료만 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-124">The Transfer Error Messages task does not report incremental progress of the error message transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="c874f-125">실행 값</span><span class="sxs-lookup"><span data-stu-id="c874f-125">Execution Value</span></span>  
 <span data-ttu-id="c874f-126">전송된 오류 메시지의 개수는 태스크의 `ExecutionValue` 속성에 정의된 실행 값으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-126">The execution value, defined in the `ExecutionValue` property of the task, returns the number of error messages that have been transferred.</span></span> <span data-ttu-id="c874f-127">오류 메시지 전송 태스크의 `ExecValueVariable` 속성에 사용자 정의 변수를 할당하면 패키지 내의 다른 개체에서 오류 메시지 전송에 대한 정보를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-127">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Error Message task, information about the error message transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="c874f-128">자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md) 및 [패키지에서 변수 사용](../use-variables-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c874f-128">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="c874f-129">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c874f-129">Log Entries</span></span>  
 <span data-ttu-id="c874f-130">오류 메시지 전송 태스크에는 다음 사용자 지정 로그 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-130">The Transfer Error Messages task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="c874f-131">TransferErrorMessagesTaskStartTransferringObjects    이 로그 항목에서는 전송이 시작되었음을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-131">TransferErrorMessagesTaskStartTransferringObjects    This log entry reports that the transfer has started.</span></span> <span data-ttu-id="c874f-132">로그 항목에 시작 시간이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-132">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="c874f-133">TransferErrorMessagesTaskFinishedTransferringObjects   이 로그 항목에서는 전송이 완료되었음을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-133">TransferErrorMessagesTaskFinishedTransferringObjects   This log entry reports that the transfer has finished.</span></span> <span data-ttu-id="c874f-134">로그 항목에 종료 시간이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-134">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="c874f-135">이외에 `OnInformation` 이벤트의 로그 항목은 전송된 오류 메시지 수를 보고하며 `OnWarning event`의 로그 항목은 덮어쓴 대상에 대한 각 오류 메시지에 대해 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-135">In addition, a log entry for the `OnInformation` event reports the number of error messages that were transferred, and a log entry for the `OnWarning event` is written for each error message on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="c874f-136">보안 및 사용 권한</span><span class="sxs-lookup"><span data-stu-id="c874f-136">Security and Permissions</span></span>  
 <span data-ttu-id="c874f-137">새 오류 메시지를 만들려면 패키지를 실행하는 사용자가 대상 서버의 sysadmin 또는 serveradmin 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-137">To create new error messages, the user that runs the package must be a member of the sysadmin or serveradmin server role on the destination server.</span></span>  
  
## <a name="configuration-of-the-transfer-error-messages-task"></a><span data-ttu-id="c874f-138">오류 메시지 전송 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="c874f-138">Configuration of the Transfer Error Messages Task</span></span>  
 <span data-ttu-id="c874f-139">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c874f-139">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="c874f-140">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="c874f-140">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c874f-141">오류 메시지 전송 태스크 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="c874f-141">Transfer Error Messages Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="c874f-142">오류 메시지 전송 태스크 편집기&#40;메시지 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="c874f-142">Transfer Error Messages Task Editor &#40;Messages Page&#41;</span></span>](../transfer-error-messages-task-editor-messages-page.md)  
  
-   [<span data-ttu-id="c874f-143">식 페이지</span><span class="sxs-lookup"><span data-stu-id="c874f-143">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="c874f-144">이러한 속성을 프로그래밍 방식으로 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="c874f-144">For information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferErrorMessagesTask.TransferErrorMessagesTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="c874f-145">관련 작업</span><span class="sxs-lookup"><span data-stu-id="c874f-145">Related Tasks</span></span>  
 <span data-ttu-id="c874f-146">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="c874f-146">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="c874f-147">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="c874f-147">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="c874f-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c874f-148">See Also</span></span>  
 <span data-ttu-id="c874f-149">[Integration Services 태스크](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="c874f-149">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="c874f-150">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="c874f-150">Control Flow</span></span>](control-flow.md)  
  
  
