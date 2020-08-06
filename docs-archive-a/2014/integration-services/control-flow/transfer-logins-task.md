---
title: 로그인 전송 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferloginstask.f1
helpviewer_keywords:
- Transfer Logins task [Integration Services]
ms.assetid: 1df60fd6-c019-405d-8155-c330dbac2cc1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d42d39b6cc7c2f350e3e3adc774be23934981369
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638926"
---
# <a name="transfer-logins-task"></a><span data-ttu-id="88c24-102">로그인 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="88c24-102">Transfer Logins Task</span></span>
  <span data-ttu-id="88c24-103">로그인 전송 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스 사이에서 하나 이상의 로그인을 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-103">The Transfer Logins task transfers one or more logins between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="transfer-logins-between-instances-of-sql-server"></a><span data-ttu-id="88c24-104">SQL Server 인스턴스 간 로그인 전송</span><span class="sxs-lookup"><span data-stu-id="88c24-104">Transfer Logins Between Instances of SQL Server</span></span>  
 <span data-ttu-id="88c24-105">로그인 전송 태스크의 원본 및 대상으로는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-105">The Transfer Logins task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="88c24-106">이벤트</span><span class="sxs-lookup"><span data-stu-id="88c24-106">Events</span></span>  
 <span data-ttu-id="88c24-107">로그인 전송 태스크는 전송된 로그인 수를 보고하는 정보 이벤트와 로그인을 덮어씀을 알리는 경고 이벤트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-107">The task raises an information event that reports the number of logins transferred and a warning event when a login is overwritten.</span></span>  
  
 <span data-ttu-id="88c24-108">태스크는 로그인 전송의 진행률을 보고하지 않으며 0% 및 100 %(완료)만 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-108">The Transfer Logins task does not report incremental progress of the login transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="88c24-109">실행 값</span><span class="sxs-lookup"><span data-stu-id="88c24-109">Execution Value</span></span>  
 <span data-ttu-id="88c24-110">태스크의 `ExecutionValue` 속성에 정의된 실행 값은 전송된 로그인 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-110">The execution value, defined in the `ExecutionValue` property of the task, returns the number of logins transferred.</span></span> <span data-ttu-id="88c24-111">사용자 정의 변수를 로그인 전송 태스크의 `ExecValueVariable` 속성에 할당하여 로그인 전송에 대한 정보를 패키지에 있는 다른 개체에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-111">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Logins task, information about the login transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="88c24-112">자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md) 및 [패키지에서 변수 사용](../use-variables-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88c24-112">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="88c24-113">로그 항목</span><span class="sxs-lookup"><span data-stu-id="88c24-113">Log Entries</span></span>  
 <span data-ttu-id="88c24-114">로그인 전송 태스크는 다음과 같은 사용자 지정 로그 항목을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-114">The Transfer Logins task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="88c24-115">TransferLoginsTaskStarTransferringObjects - 이 로그 항목은 전송이 시작되었음을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-115">TransferLoginsTaskStarTransferringObjects    This log entry reports the transfer has started.</span></span> <span data-ttu-id="88c24-116">로그 항목에 시작 시간이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-116">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="88c24-117">TransferLoginsTaskFinishedTransferringObjects - 이 로그 항목은 전송이 완료되었음을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-117">TransferLoginsTaskFinishedTransferringObjects   This log entry reports the transfer has completed.</span></span> <span data-ttu-id="88c24-118">로그 항목에 종료 시간이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-118">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="88c24-119">이외에 `OnInformation` 이벤트의 로그 항목은 전송된 로그인 수를 보고하며 `OnWarning` 이벤트의 로그 항목은 덮어쓴 각 대상 로그인에 대해 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-119">In addition, a log entry for the `OnInformation` event reports the number of logins that were transferred, and a log entry for the `OnWarning` event is written for each login on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="88c24-120">보안 및 사용 권한</span><span class="sxs-lookup"><span data-stu-id="88c24-120">Security and Permissions</span></span>  
 <span data-ttu-id="88c24-121">원본 서버에서 로그인을 찾고 대상 서버에서 로그인을 만들려면 사용자는 두 서버 모두에서 sysadmin 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-121">To browse logins on the source server and to create logins on the destination server, the user must be a member of the sysadmin server role on both servers.</span></span>  
  
## <a name="configuration-of-the-transfer-logins-task"></a><span data-ttu-id="88c24-122">로그인 전송 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="88c24-122">Configuration of the Transfer Logins Task</span></span>  
 <span data-ttu-id="88c24-123">로그인 전송 태스크를 모든 로그인을 전송하거나, 지정된 로그인만 전송하거나, 지정된 데이터베이스에 액세스할 수 있는 모든 로그인만을 전송하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-123">The Transfer Logins task can be configured to transfer all logins, only specified logins, or all logins that have access to specified databases only.</span></span> <span data-ttu-id="88c24-124">sa 로그인은 전송할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-124">The sa login cannot be transferred.</span></span> <span data-ttu-id="88c24-125">sa 로그인의 이름을 바꿀 수 있지만 이름을 바꾼 sa 로그인도 전송할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-125">The sa login may be renamed; however, the renamed sa login cannot be transferred either.</span></span>  
  
 <span data-ttu-id="88c24-126">또한 이 태스크가 로그인과 연결된 SID(보안 ID)를 복사할지 여부도 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-126">You can also indicate whether the task copies the security identifiers (SIDs) associated with the logins.</span></span> <span data-ttu-id="88c24-127">로그인 전송 태스크를 데이터베이스 전송 태스크와 연결하여 사용하는 경우 SID를 대상에 복사해야 합니다. 그렇지 않으면 전송된 로그인은 대상 데이터베이스에서 인식되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-127">If the Transfer Logins task is used in conjunction with the Transfer Database task the SIDs must be copied to the destination; otherwise, the transferred logins are not recognized by the destination database.</span></span>  
  
 <span data-ttu-id="88c24-128">대상으로 전송된 로그인은 비활성화되고 임의의 암호가 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-128">At the destination, the transferred logins are disabled and assigned random passwords.</span></span> <span data-ttu-id="88c24-129">대상 서버에 있는 sysadmin 역할의 멤버가 암호를 변경하고 로그인을 활성화해야 로그인을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-129">A member of the sysadmin role on the destination server must change the passwords and enable the logins before the logins can be used.</span></span>  
  
 <span data-ttu-id="88c24-130">전송할 로그인이 이미 대상에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-130">The logins to be transferred may already exist on the destination.</span></span> <span data-ttu-id="88c24-131">기존 로그인이 있을 경우 다음과 같이 처리하도록 로그인 전송 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-131">The Transfer Logins task can be configured to handle existing logins in the following ways:</span></span>  
  
-   <span data-ttu-id="88c24-132">기존 로그인을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-132">Overwrite existing logins.</span></span>  
  
-   <span data-ttu-id="88c24-133">중복 로그인이 있으면 전송이 실패하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-133">Fail the task when duplicate logins exist.</span></span>  
  
-   <span data-ttu-id="88c24-134">중복 로그인을 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-134">Skip duplicate logins.</span></span>  
  
 <span data-ttu-id="88c24-135">로그인 전송 태스크는 실행 시 하나 또는 두 개의 SMO 연결 관리자를 사용하여 원본과 대상을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-135">At run time, the Transfer Logins task connects to the source and destination servers by using two SMO connection managers.</span></span> <span data-ttu-id="88c24-136">SMO 연결 관리자는 로그인 전송 태스크와 별도로 구성된 후 로그인 전송 태스크에서 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-136">The SMO connection managers are configured separately from the Transfer Logins task, and then referenced in the Transfer Logins task.</span></span> <span data-ttu-id="88c24-137">SMO 연결 관리자는 액세스할 서버 및 사용할 인증 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-137">The SMO connection managers specify the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="88c24-138">자세한 내용은 [SMO Connection Manager](../connection-manager/smo-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88c24-138">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
 <span data-ttu-id="88c24-139">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88c24-139">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="88c24-140">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="88c24-140">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="88c24-141">로그인 전송 태스크 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="88c24-141">Transfer Logins Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="88c24-142">로그인 전송 태스크 편집기&#40;로그인 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="88c24-142">Transfer Logins Task Editor &#40;Logins Page&#41;</span></span>](../transfer-logins-task-editor-logins-page.md)  
  
-   [<span data-ttu-id="88c24-143">식 페이지</span><span class="sxs-lookup"><span data-stu-id="88c24-143">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="88c24-144">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="88c24-144">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="88c24-145">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="88c24-145">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-transfer-logins-task"></a><span data-ttu-id="88c24-146">로그인 전송 태스크의 프로그래밍 방식 구성</span><span class="sxs-lookup"><span data-stu-id="88c24-146">Programmatic Configuration of the Transfer Logins Task</span></span>  
 <span data-ttu-id="88c24-147">이러한 속성을 프로그래밍 방식으로 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="88c24-147">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferLoginsTask.TransferLoginsTask>  
  
  
