---
title: 작업 전송 태스크 편집기 (작업 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.jobs.f1
helpviewer_keywords:
- Transfer Jobs Task Editor
ms.assetid: e72b1dc7-8cda-4ee6-abb5-d438370f04df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d2d506da6997965e40d66521f7dccb8218e165fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661719"
---
# <a name="transfer-jobs-task-editor-jobs-page"></a><span data-ttu-id="92ca7-102">작업 전송 태스크 편집기(작업 페이지)</span><span class="sxs-lookup"><span data-stu-id="92ca7-102">Transfer Jobs Task Editor (Jobs Page)</span></span>
  <span data-ttu-id="92ca7-103">**작업 전송 태스크 편집기** 대화 상자의 **작업** 페이지를 사용하여 하나 이상의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 작업을 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 한 인스턴스에서 다른 인스턴스로 복사하기 위한 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-103">Use the **Jobs** page of the **Transfer Jobs Task Editor** dialog box to specify properties for copying one or more [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another.</span></span> <span data-ttu-id="92ca7-104">작업 전송 태스크에 대한 자세한 내용은 [Transfer Jobs Task](control-flow/transfer-jobs-task.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="92ca7-104">For more information about the Transfer Jobs task, see [Transfer Jobs Task](control-flow/transfer-jobs-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="92ca7-105">원본 서버의 작업에 액세스하려면 사용자가 적어도 서버에서 **SQLAgentUserRole** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-105">To access jobs on the source server, users must be a member of at least the **SQLAgentUserRole** fixed database role on the server.</span></span> <span data-ttu-id="92ca7-106">대상 서버에 작업을 만들려면 사용자가 **sysadmin** 고정 서버 역할의 멤버이거나 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 고정 데이터베이스 역할 중 하나여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-106">To successfully create jobs on the destination server, the user must be a member of the **sysadmin** fixed server role or one of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent fixed database roles.</span></span> <span data-ttu-id="92ca7-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 고정 데이터베이스 역할 및 해당 권한에 대한 자세한 내용은 [SQL Server 에이전트 고정 데이터베이스 역할](../ssms/agent/sql-server-agent-fixed-database-roles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92ca7-107">For more information about [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent fixed database roles and their permissions, see [SQL Server Agent Fixed Database Roles](../ssms/agent/sql-server-agent-fixed-database-roles.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="92ca7-108">옵션</span><span class="sxs-lookup"><span data-stu-id="92ca7-108">Options</span></span>  
 <span data-ttu-id="92ca7-109">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="92ca7-109">**SourceConnection**</span></span>  
 <span data-ttu-id="92ca7-110">목록에서 SMO 연결 관리자를 선택하거나, **\<New connection...>** 을 클릭하여 원본 서버에 대한 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-110">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="92ca7-111">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="92ca7-111">**DestinationConnection**</span></span>  
 <span data-ttu-id="92ca7-112">목록에서 SMO 연결 관리자를 선택하거나, **\<New connection...>** 을 클릭하여 대상 서버에 대한 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-112">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="92ca7-113">**TransferAllJobs**</span><span class="sxs-lookup"><span data-stu-id="92ca7-113">**TransferAllJobs**</span></span>  
 <span data-ttu-id="92ca7-114">원본 서버에서 대상 서버로 모든 SQL Server 에이전트 작업을 복사할지, 아니면 지정한 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 작업만 복사할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-114">Select whether the task should copy all or only the specified [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs from the source to the destination server.</span></span>  
  
 <span data-ttu-id="92ca7-115">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-115">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="92ca7-116">값</span><span class="sxs-lookup"><span data-stu-id="92ca7-116">Value</span></span>|<span data-ttu-id="92ca7-117">Description</span><span class="sxs-lookup"><span data-stu-id="92ca7-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="92ca7-118">**True**</span><span class="sxs-lookup"><span data-stu-id="92ca7-118">**True**</span></span>|<span data-ttu-id="92ca7-119">모든 작업을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-119">Copy all jobs.</span></span>|  
|<span data-ttu-id="92ca7-120">**False**</span><span class="sxs-lookup"><span data-stu-id="92ca7-120">**False**</span></span>|<span data-ttu-id="92ca7-121">지정한 작업만 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-121">Copy only the specified jobs.</span></span>|  
  
 <span data-ttu-id="92ca7-122">**JobsList**</span><span class="sxs-lookup"><span data-stu-id="92ca7-122">**JobsList**</span></span>  
 <span data-ttu-id="92ca7-123">복사할 작업을 선택하려면 찾아보기 단추 **(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-123">Click the browse button **(...)** to select the jobs to copy.</span></span> <span data-ttu-id="92ca7-124">하나 이상의 작업을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-124">At least one job must be selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="92ca7-125">복사할 작업을 선택하기 전에 **SourceConnection** 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-125">Specify the **SourceConnection** before selecting jobs to copy.</span></span>  
  
 <span data-ttu-id="92ca7-126">**TransferAllJobs** 를 **True** 로 설정하면 **JobsList**옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-126">The **JobsList** option is unavailable when **TransferAllJobs** is set to **True**.</span></span>  
  
 <span data-ttu-id="92ca7-127">**IfObjectExists**</span><span class="sxs-lookup"><span data-stu-id="92ca7-127">**IfObjectExists**</span></span>  
 <span data-ttu-id="92ca7-128">태스크에서 대상 서버에 이미 있는 작업과 이름이 동일한 작업을 처리하는 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-128">Select how the task should handle jobs of the same name that already exist on the destination server.</span></span>  
  
 <span data-ttu-id="92ca7-129">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-129">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="92ca7-130">값</span><span class="sxs-lookup"><span data-stu-id="92ca7-130">Value</span></span>|<span data-ttu-id="92ca7-131">Description</span><span class="sxs-lookup"><span data-stu-id="92ca7-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="92ca7-132">**FailTask**</span><span class="sxs-lookup"><span data-stu-id="92ca7-132">**FailTask**</span></span>|<span data-ttu-id="92ca7-133">대상 서버에 이름이 동일한 작업이 이미 있는 경우 태스크가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-133">Task fails if jobs of the same name already exist on the destination server.</span></span>|  
|<span data-ttu-id="92ca7-134">**Overwrite**</span><span class="sxs-lookup"><span data-stu-id="92ca7-134">**Overwrite**</span></span>|<span data-ttu-id="92ca7-135">대상 서버에 이름이 동일한 태스크가 있는 경우 이를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-135">Task overwrites jobs of the same name on the destination server.</span></span>|  
|<span data-ttu-id="92ca7-136">**skip**</span><span class="sxs-lookup"><span data-stu-id="92ca7-136">**Skip**</span></span>|<span data-ttu-id="92ca7-137">대상 서버에 이름이 동일한 태스크가 있는 경우 이를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-137">Task skips jobs of the same name that exist on the destination server.</span></span>|  
  
 <span data-ttu-id="92ca7-138">**EnableJobsAtDestination**</span><span class="sxs-lookup"><span data-stu-id="92ca7-138">**EnableJobsAtDestination**</span></span>  
 <span data-ttu-id="92ca7-139">대상 서버로 복사한 작업을 활성화할지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-139">Select whether the jobs copied to the destination server should be enabled.</span></span>  
  
 <span data-ttu-id="92ca7-140">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-140">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="92ca7-141">값</span><span class="sxs-lookup"><span data-stu-id="92ca7-141">Value</span></span>|<span data-ttu-id="92ca7-142">Description</span><span class="sxs-lookup"><span data-stu-id="92ca7-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="92ca7-143">**True**</span><span class="sxs-lookup"><span data-stu-id="92ca7-143">**True**</span></span>|<span data-ttu-id="92ca7-144">대상 서버에서 작업을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-144">Enable jobs on destination server.</span></span>|  
|<span data-ttu-id="92ca7-145">**False**</span><span class="sxs-lookup"><span data-stu-id="92ca7-145">**False**</span></span>|<span data-ttu-id="92ca7-146">대상 서버에서 작업을 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="92ca7-146">Disable jobs on destination server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92ca7-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="92ca7-147">See Also</span></span>  
 <span data-ttu-id="92ca7-148">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="92ca7-148">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="92ca7-149">[Integration Services 태스크](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="92ca7-149">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="92ca7-150">[작업 전송 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="92ca7-150">[Transfer Jobs Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="92ca7-151">[식 페이지](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="92ca7-151">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="92ca7-152">SMO 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="92ca7-152">SMO Connection Manager</span></span>](connection-manager/smo-connection-manager.md)  
  
  
