---
title: 유지 관리 계획 만들기(유지 관리 계획 디자인 화면) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Maintenance Plan Design Surface
ms.assetid: 2ef803ee-a9f8-454a-ad63-fedcbe6838d1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 77e347720824198ba7d6abaddedd7a581ace98a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653356"
---
# <a name="create-a-maintenance-plan-maintenance-plan-design-surface"></a><span data-ttu-id="0276e-102">유지 관리 계획 만들기(유지 관리 계획 디자인 화면)</span><span class="sxs-lookup"><span data-stu-id="0276e-102">Create a Maintenance Plan (Maintenance Plan Design Surface)</span></span>
  <span data-ttu-id="0276e-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 유지 관리 디자인 화면을 사용하여 단일 서버 또는 다중 서버 유지 관리 계획을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-103">This topic describes how to create a single server or multiserver maintenance plan using the Maintenance Plan Design Surface in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="0276e-104">기본 유지 관리 계획을 만들 때는 **유지 관리 계획 마법사** 가 적합한 반면 디자인 화면을 사용하여 계획을 만들면 워크플로의 향상된 기능을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-104">While the **Maintenance Plan Wizard** is best for creating basic maintenance plans, creating a plan using the design surface allows you to utilize enhanced workflow.</span></span>  
  
 <span data-ttu-id="0276e-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="0276e-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0276e-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="0276e-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0276e-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="0276e-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0276e-108">보안</span><span class="sxs-lookup"><span data-stu-id="0276e-108">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="0276e-109">유지 관리 계획 디자인 화면을 사용하여 유지 관리 계획 만들기</span><span class="sxs-lookup"><span data-stu-id="0276e-109">Creating a maintenance plan using the Maintenance Plan Design Surface</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0276e-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="0276e-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0276e-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="0276e-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="0276e-112">다중 서버 유지 관리 계획을 만들려면 하나의 마스터 서버 및 하나 이상의 대상 서버가 있는 다중 서버 환경을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-112">To create a multiserver maintenance plan, a multiserver environment containing one master server and one or more target servers must be configured.</span></span> <span data-ttu-id="0276e-113">다중 서버 유지 관리 계획은 마스터 서버에서 만들고 유지 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-113">Multiserver maintenance plans must be created and maintained on the master server.</span></span> <span data-ttu-id="0276e-114">이러한 계획을 대상 서버에서 볼 수 있지만 유지 관리할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-114">These plans can be viewed, but not maintained, on target servers.</span></span>  
  
-   <span data-ttu-id="0276e-115">**db_ssisadmin** 및 **dc_admin** 역할의 멤버는 해당 권한을 **sysadmin**으로 승격할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-115">Members of the **db_ssisadmin** and **dc_admin** roles may be able to elevate their privileges to **sysadmin**.</span></span> <span data-ttu-id="0276e-116">이러한 권한 승격이 발생할 수 있는 것은 이러한 역할이 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 수정할 수 있고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 **에이전트의** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보안 컨텍스트를 사용하여 이러한 패키지를 실행할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-116">This elevation of privilege can occur because these roles can modify [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages; these packages can be executed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the **sysadmin** security context of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="0276e-117">유지 관리 계획, 데이터 컬렉션 집합 및 기타 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 실행할 때 이러한 권한 상승이 발생하지 않도록 하려면 패키지를 실행하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업이 제한된 권한을 갖는 프록시 계정을 사용하도록 구성하거나 **db_ssisadmin** 및 **dc_admin** 역할에 **sysadmin** 멤버만 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-117">To guard against this elevation of privilege when running maintenance plans, data collection sets, and other [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs that run packages to use a proxy account with limited privileges or only add **sysadmin** members to the **db_ssisadmin** and **dc_admin** roles.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0276e-118">보안</span><span class="sxs-lookup"><span data-stu-id="0276e-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0276e-119">권한</span><span class="sxs-lookup"><span data-stu-id="0276e-119">Permissions</span></span>  
 <span data-ttu-id="0276e-120">유지 관리 계획을 만들거나 관리하려면 **sysadmin** 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-120">To create or manage maintenance plans, you must be a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="0276e-121">개체 탐색기에 **sysadmin** 고정 서버 역할의 멤버인 사용자에 대한 **유지 관리 계획** 노드만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-121">Object Explorer only displays the **Maintenance Plans** node for users who are members of the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-maintenance-plan-design-surface"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0276e-122">유지 관리 계획 디자인 화면 사용</span><span class="sxs-lookup"><span data-stu-id="0276e-122">Using Maintenance Plan Design Surface</span></span>  
  
#### <a name="to-create-a-maintenance-plan"></a><span data-ttu-id="0276e-123">유지 관리 계획을 만들려면</span><span class="sxs-lookup"><span data-stu-id="0276e-123">To create a maintenance plan</span></span>  
  
1.  <span data-ttu-id="0276e-124">개체 탐색기에서 더하기 기호를 클릭하여 유지 관리 계획을 만들 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-124">In Object Explorer, click the plus sign to expand the server where you want to create a maintenance plan.</span></span>  
  
2.  <span data-ttu-id="0276e-125">더하기 기호를 클릭하여 **관리** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-125">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="0276e-126">**유지 관리 계획** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 유지 관리 계획**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-126">Right-click the **Maintenance Plans** folder and select **New Maintenance Plan**.</span></span>  
  
4.  <span data-ttu-id="0276e-127">**새 유지 관리 계획** 대화 상자의 **이름** 상자에 계획의 이름을 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-127">In the **New Maintenance Plan** dialog box, in the **Name** box, type a name for the plan and click **OK**.</span></span> <span data-ttu-id="0276e-128">이렇게 하면 주 그리드에서 만든 **Subplan_1** 하위 계획이 있는 _maintenance_plan_name_ **[Design]** 화면과 도구 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-128">This opens the  Toolbox and the _maintenance_plan_name_ **[Design]** surface with the **Subplan_1** subplan created in the main grid.</span></span>  
  
     <span data-ttu-id="0276e-129">다음 옵션은 디자인 화면의 헤더에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-129">The following options are available in the design space's header.</span></span>  
  
     <span data-ttu-id="0276e-130">**하위 계획 추가**</span><span class="sxs-lookup"><span data-stu-id="0276e-130">**Add Subplan**</span></span>  
     <span data-ttu-id="0276e-131">구성할 수 있는 하위 계획을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-131">Adds a subplan that you can configure.</span></span>  
  
     <span data-ttu-id="0276e-132">**하위 계획 속성**</span><span class="sxs-lookup"><span data-stu-id="0276e-132">**Subplan Properties**</span></span>  
     <span data-ttu-id="0276e-133">주 표에서 선택한 하위 계획에 대해 **하위 계획 속성** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-133">Displays the **Subplan Properties** dialog box for the selected subplan in the main grid.</span></span> <span data-ttu-id="0276e-134">또는 표에서 하위 계획을 두 번 클릭하여 **하위 계획 속성** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-134">Alternately, double-click a subplan in the grid to display the **Subplan Properties** dialog box.</span></span> <span data-ttu-id="0276e-135">이 대화 상자에 대한 자세한 내용은 아래를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0276e-135">See below for more information on this dialog box.</span></span>  
  
     <span data-ttu-id="0276e-136">**선택한 하위 계획 삭제**</span><span class="sxs-lookup"><span data-stu-id="0276e-136">**Delete Selected Subplan**</span></span>  
     <span data-ttu-id="0276e-137">선택한 하위 계획을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-137">Deletes the selected subplan.</span></span>  
  
     <span data-ttu-id="0276e-138">**하위 계획 일정**</span><span class="sxs-lookup"><span data-stu-id="0276e-138">**Subplan Schedule**</span></span>  
     <span data-ttu-id="0276e-139">선택한 하위 계획에 대해 **새 작업 일정** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-139">Displays the **New Job Schedule** dialog box for the selected subplan.</span></span>  
  
     <span data-ttu-id="0276e-140">**일정 제거**</span><span class="sxs-lookup"><span data-stu-id="0276e-140">**Remove Schedule**</span></span>  
     <span data-ttu-id="0276e-141">선택한 하위 계획에서 일정을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-141">Removes a schedule from the selected subplan.</span></span>  
  
     <span data-ttu-id="0276e-142">**연결 관리**</span><span class="sxs-lookup"><span data-stu-id="0276e-142">**Manage Connections**</span></span>  
     <span data-ttu-id="0276e-143">**연결 관리** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-143">Displays the **Manage Connections** dialog box.</span></span> <span data-ttu-id="0276e-144">유지 관리 계획에 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 연결을 추가하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-144">Used to add additional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance connections to the maintenance plan.</span></span> <span data-ttu-id="0276e-145">이 대화 상자에 대한 자세한 내용은 아래를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0276e-145">See below for more information on this dialog box.</span></span>  
  
     <span data-ttu-id="0276e-146">**보고 및 로깅**</span><span class="sxs-lookup"><span data-stu-id="0276e-146">**Reporting and Logging**</span></span>  
     <span data-ttu-id="0276e-147">**보고 및 로깅** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-147">Displays the **Reporting and Logging** dialog box.</span></span> <span data-ttu-id="0276e-148">이 대화 상자에 대한 자세한 내용은 아래를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0276e-148">See below for more information on this dialog box.</span></span>  
  
     <span data-ttu-id="0276e-149">**서버**</span><span class="sxs-lookup"><span data-stu-id="0276e-149">**Servers**</span></span>  
     <span data-ttu-id="0276e-150">하위 계획 태스크를 실행할 서버를 선택하는 데 사용되는 **서버** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-150">Display the **Servers** dialog box, which is used to select the servers where the subplan tasks will be run.</span></span> <span data-ttu-id="0276e-151">이 옵션은 다중 서버 환경의 마스터 서버에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-151">This option is enabled only on master servers in multiserver environments.</span></span> <span data-ttu-id="0276e-152">자세한 내용은 [다중 서버 환경 만들기](../../ssms/agent/create-a-multiserver-environment.md) 및 [유지 관리 계획&#40;Servers&#41;](maintenance-plan-servers.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0276e-152">For more information, see [Create a Multiserver Environment](../../ssms/agent/create-a-multiserver-environment.md) and [Maintenance Plan &#40;Servers&#41;](maintenance-plan-servers.md).</span></span>  
  
     <span data-ttu-id="0276e-153">**이름**</span><span class="sxs-lookup"><span data-stu-id="0276e-153">**Name**</span></span>  
     <span data-ttu-id="0276e-154">유지 관리 계획 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-154">Display the maintenance plan name.</span></span> <span data-ttu-id="0276e-155">새 유지 관리 계획의 경우 유지 관리 계획 디자이너가 열리기 전에 나타나는 대화 상자에서 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-155">For new maintenance plans, the name is specified in a dialog box before the maintenance plan designer opens.</span></span> <span data-ttu-id="0276e-156">유지 관리 계획의 이름을 바꾸려면 개체 탐색기에서 해당 계획을 마우스 오른쪽 단추로 클릭한 다음 **이름 바꾸기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-156">To rename a maintenance plan, right-click the plan in Object Explorer, and then click **Rename**.</span></span>  
  
     <span data-ttu-id="0276e-157">**설명**</span><span class="sxs-lookup"><span data-stu-id="0276e-157">**Description**</span></span>  
     <span data-ttu-id="0276e-158">유지 관리 계획에 대한 설명을 확인하거나 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-158">View or specify a description for the maintenance plan.</span></span> <span data-ttu-id="0276e-159">설명의 최대 길이는 512자입니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-159">The maximum length for a description is 512 characters.</span></span>  
  
     <span data-ttu-id="0276e-160">**디자이너 화면**</span><span class="sxs-lookup"><span data-stu-id="0276e-160">**Designer Surface**</span></span>  
     <span data-ttu-id="0276e-161">유지 관리 계획을 디자인 및 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-161">Design and maintain maintenance plans.</span></span> <span data-ttu-id="0276e-162">디자이너 화면을 사용하여 계획에 유지 관리 태스크를 추가하거나 제거하고, 작업 간의 선행 링크를 지정하며 작업 분기와 병렬 처리를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-162">Use the designer surface to add maintenance tasks to a plan, remove tasks from a plan, specify precedence links between the tasks, and indicate task branching and parallelism.</span></span>  
  
     <span data-ttu-id="0276e-163">두 태스크 간의 선행 링크는 작업 간의 관계를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-163">A precedence link between two tasks establishes a relationship between the tasks.</span></span> <span data-ttu-id="0276e-164">두 번째 태스크( *종속 태스크*)는 첫 번째 태스크( *선행 태스크*)의 실행 결과가 지정한 조건과 일치하는 경우에만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-164">The second task (the *dependent task*) executes only if the execution result of the first task (the *precedent task*) matches specified criteria.</span></span> <span data-ttu-id="0276e-165">대개 지정되는 실행 결과는 **성공**, **실패**또는 **완료**입니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-165">Typically the execution result specified is **Success**, **Failure**, or **Completion**.</span></span> <span data-ttu-id="0276e-166">자세한 내용은 아래의 **8** 단계를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0276e-166">For more information, see step **8** below.</span></span>  
  
5.  <span data-ttu-id="0276e-167">디자인 화면의 헤더에서 **Subplan_1** 을 두 번 클릭하고 **하위 계획 속성** 대화 상자에 하위 계획의 이름 및 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-167">In the design space's header, double-click **Subplan_1** and enter a name and description for the subplan in the **Subplan Properties** dialog box.</span></span>  
  
     <span data-ttu-id="0276e-168">다음 옵션은 **하위 계획 속성** 대화 상자에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-168">The following options are available in the **Subplan Properties** dialog box.</span></span>  
  
     <span data-ttu-id="0276e-169">**이름**</span><span class="sxs-lookup"><span data-stu-id="0276e-169">**Name**</span></span>  
     <span data-ttu-id="0276e-170">하위 계획의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-170">The name of the subplan.</span></span>  
  
     <span data-ttu-id="0276e-171">**설명**</span><span class="sxs-lookup"><span data-stu-id="0276e-171">**Description**</span></span>  
     <span data-ttu-id="0276e-172">하위 계획에 대한 간단한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-172">A brief description of the subplan.</span></span>  
  
     <span data-ttu-id="0276e-173">**일정**</span><span class="sxs-lookup"><span data-stu-id="0276e-173">**Schedule**</span></span>  
     <span data-ttu-id="0276e-174">하위 계획이 어떤 일정에 따라 실행될지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-174">Indicates on what schedule the subplan will be run.</span></span> <span data-ttu-id="0276e-175">**하위 계획 일정** 을 클릭하여 **새 작업 일정** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-175">Click **Subplan Schedule** to open the **New Job Schedule** dialog box.</span></span> <span data-ttu-id="0276e-176">**일정 제거** 를 클릭하여 하위 계획에서 일정을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-176">Click **Remove Schedule** to delete the schedule from the subplan.</span></span>  
  
     <span data-ttu-id="0276e-177">**다음 계정으로 실행** 목록</span><span class="sxs-lookup"><span data-stu-id="0276e-177">**Run as** list</span></span>  
     <span data-ttu-id="0276e-178">이 하위 태스크를 실행하는 데 사용할 계정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-178">Select the account to use to run this subtask.</span></span>  
  
6.  <span data-ttu-id="0276e-179">**하위 계획 일정** 을 클릭하여 **새 작업 일정** 대화 상자에 일정 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-179">Click **Subplan Schedule** to enter schedule details in the **New Job Schedule** dialog box.</span></span>  
  
7.  <span data-ttu-id="0276e-180">하위 계획을 작성하려면 **도구 상자** 에서 계획 디자인 화면으로 태스크 흐름 요소를 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-180">To build the subplan, drag and drop task flow elements from the **Toolbox** to the plan design surface.</span></span> <span data-ttu-id="0276e-181">태스크를 두 번 클릭하여 대화 상자를 연 후 작업 옵션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-181">Double-click tasks to open dialog boxes to configure the task options.</span></span>  
  
     <span data-ttu-id="0276e-182">다음 유지 관리 계획 태스크는 **도구 상자**에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-182">The following maintenance plan tasks are available in the **Toolbox**:</span></span>  
  
    -   <span data-ttu-id="0276e-183">**데이터베이스 백업 태스크**</span><span class="sxs-lookup"><span data-stu-id="0276e-183">**Back up Database Task**</span></span>  
  
    -   <span data-ttu-id="0276e-184">**데이터베이스 무결성 검사 태스크**</span><span class="sxs-lookup"><span data-stu-id="0276e-184">**Check Database Integrity Task**</span></span>  
  
    -   <span data-ttu-id="0276e-185">**SQL Server 에이전트 작업 실행 태스크**</span><span class="sxs-lookup"><span data-stu-id="0276e-185">**Execute SQL Server Agent Job Task**</span></span>  
  
    -   <span data-ttu-id="0276e-186">**T-SQL 문 실행 태스크**</span><span class="sxs-lookup"><span data-stu-id="0276e-186">**Execute T-SQL Statement Task**</span></span>  
  
    -   <span data-ttu-id="0276e-187">**기록 정리 태스크**</span><span class="sxs-lookup"><span data-stu-id="0276e-187">**History Cleanup Task**</span></span>  
  
    -   <span data-ttu-id="0276e-188">**유지 관리 정리 태스크**</span><span class="sxs-lookup"><span data-stu-id="0276e-188">**Maintenance Cleanup Task**</span></span>  
  
    -   <span data-ttu-id="0276e-189">**운영자에게 알림 태스크**</span><span class="sxs-lookup"><span data-stu-id="0276e-189">**Notify Operator Task**</span></span>  
  
    -   <span data-ttu-id="0276e-190">**인덱스 다시 작성 태스크**</span><span class="sxs-lookup"><span data-stu-id="0276e-190">**Rebuild Index Task**</span></span>  
  
    -   <span data-ttu-id="0276e-191">**인덱스 다시 구성 태스크**</span><span class="sxs-lookup"><span data-stu-id="0276e-191">**Reorganize Index Task**</span></span>  
  
    -   <span data-ttu-id="0276e-192">**데이터베이스 축소 태스크**</span><span class="sxs-lookup"><span data-stu-id="0276e-192">**Shrink Database Task**</span></span>  
  
    -   <span data-ttu-id="0276e-193">**통계 업데이트 태스크**</span><span class="sxs-lookup"><span data-stu-id="0276e-193">**Update Statistics Task**</span></span>  
  
     <span data-ttu-id="0276e-194">**도구 상자**에 태스크를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="0276e-194">To add tasks to the **Toolbox**:</span></span>  
  
    1.  <span data-ttu-id="0276e-195">**도구** 메뉴에서 **도구 상자 항목 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-195">On the **Tools** menu, click **Choose Toolbox Items**.</span></span>  
  
    2.  <span data-ttu-id="0276e-196">**도구 상자**에 표시할 도구를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-196">Select the tools you want to appear in the **Toolbox**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="0276e-197">**도구 상자** 에 유지 관리 계획 태스크를 추가하면 이 태스크를 **유지 관리 계획 마법사**에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-197">Adding maintenance plan tasks to the **Toolbox** also makes them available in the **Maintenance Plan Wizard**.</span></span> <span data-ttu-id="0276e-198">위의 개별 태스크에 대한 자세한 내용은 [유지 관리 계획 마법사 시작](use-the-maintenance-plan-wizard.md#SSMSProcedure) 에서 **유지 관리 계획 마법사 사용**을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0276e-198">For more information on the individual tasks above, see [Using Maintenance Plan Wizard](use-the-maintenance-plan-wizard.md#SSMSProcedure) under **Start the Maintenance Plan Wizard**.</span></span>  
  
8.  <span data-ttu-id="0276e-199">태스크 간의 워크플로를 정의하려면:</span><span class="sxs-lookup"><span data-stu-id="0276e-199">To define a workflow between tasks:</span></span>  
  
    1.  <span data-ttu-id="0276e-200">선행 태스크를 마우스 오른쪽 단추로 클릭하고 **선행 제약 조건 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-200">Right-click the precedent task and select **Add Precedence Constraint**.</span></span>  
  
    2.  <span data-ttu-id="0276e-201">**제어 흐름** 대화 상자의 **대상** 목록에서 종속 태스크를 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-201">In the **Control Flow** dialog box, in the **To** list, select the dependent task and click **OK**.</span></span>  
  
    3.  <span data-ttu-id="0276e-202">두 태스크 사이의 커넥터를 두 번 클릭하여 **선행 제약 조건 편집기** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-202">Double click the connector between the two tasks to open the **Precedence Constraint Editor** dialog box.</span></span>  
  
         <span data-ttu-id="0276e-203">다음 옵션은 **선행 제약 조건 편집기** 대화 상자에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-203">The following options are available in the **Precedence Constraint Editor** dialog box.</span></span>  
  
         <span data-ttu-id="0276e-204">**제약 조건 옵션**</span><span class="sxs-lookup"><span data-stu-id="0276e-204">**Constraint option**</span></span>  
         <span data-ttu-id="0276e-205">두 태스크 사이에서 제약 조건이 작동하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-205">Defines how a constraint works between two tasks.</span></span>  
  
         <span data-ttu-id="0276e-206">**평가 작업**  목록</span><span class="sxs-lookup"><span data-stu-id="0276e-206">**Evaluation operation**  list</span></span>  
         <span data-ttu-id="0276e-207">선행 제약 조건에서 사용하는 평가 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-207">Specify the evaluation operation that the precedence constraint uses.</span></span> <span data-ttu-id="0276e-208">사용할 수 있는 작업에는 **제약 조건**, **식**, **식 및 제약 조건**, **식 또는 제약 조건**이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-208">The operations are: **Constraint**, **Expression**, **Expression and Constraint**, and **Expression or Constraint**.</span></span>  
  
         <span data-ttu-id="0276e-209">**값** 목록</span><span class="sxs-lookup"><span data-stu-id="0276e-209">**Value** list</span></span>  
         <span data-ttu-id="0276e-210">제약 조건 값을 지정합니다. **성공**, **실패** 또는 **완료**와 같은 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-210">Specify the constraint value: **Success**, **Failure**, or **Completion**.</span></span> <span data-ttu-id="0276e-211">기본값은**성공** 입니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-211">**Success** is the default.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="0276e-212">선행 제약 조건 줄은 **성공**인 경우 녹색, **실패**인 경우 빨간색, **완료**인 경우 파란색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-212">The precedence constraint line is green for **Success**, red for **Failure**, and blue for **Completion**.</span></span>  
  
         <span data-ttu-id="0276e-213">**식**</span><span class="sxs-lookup"><span data-stu-id="0276e-213">**Expression**</span></span>  
         <span data-ttu-id="0276e-214">**식**, **식 및 제약 조건**또는 **식 또는 제약 조건**작업을 사용하는 경우 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-214">If using the operations **Expression**, **Expression and Constraint**, or **Expression or Constraint**, type an expression.</span></span> <span data-ttu-id="0276e-215">식은 부울로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-215">The expression must evaluate to a Boolean.</span></span>  
  
         <span data-ttu-id="0276e-216">**Test**</span><span class="sxs-lookup"><span data-stu-id="0276e-216">**Test**</span></span>  
         <span data-ttu-id="0276e-217">식의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-217">Validate the expression.</span></span>  
  
         <span data-ttu-id="0276e-218">**여러 제약 조건**</span><span class="sxs-lookup"><span data-stu-id="0276e-218">**Multiple constraints**</span></span>  
         <span data-ttu-id="0276e-219">여러 제약 조건이 제한된 태스크의 실행을 제어하기 위해 어떤 방식으로 상호 운영되는지 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-219">Define how multiple constraints interoperate to control the execution of the constrained task.</span></span>  
  
         <span data-ttu-id="0276e-220">**논리적 AND**</span><span class="sxs-lookup"><span data-stu-id="0276e-220">**Logical AND**</span></span>  
         <span data-ttu-id="0276e-221">동일한 실행 파일의 여러 선행 제약 조건을 함께 평가하도록 지정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-221">Select to specify that multiple precedence constraints on the same executable must be evaluated together.</span></span> <span data-ttu-id="0276e-222">모든 제약 조건이 True여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-222">All constraints must evaluate to True.</span></span> <span data-ttu-id="0276e-223">이 옵션이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-223">This option is the default.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="0276e-224">이 유형의 선행 제약 조건은 녹색, 빨간색 또는 파란색 실선으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-224">This type of precedence constraint appears as a solid green, red, or blue line.</span></span>  
  
         <span data-ttu-id="0276e-225">**논리적 OR**</span><span class="sxs-lookup"><span data-stu-id="0276e-225">**Logical OR**</span></span>  
         <span data-ttu-id="0276e-226">동일한 실행 파일의 여러 선행 제약 조건을 함께 평가하도록 지정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-226">Select to specify that multiple precedence constraints on the same executable must be evaluated together.</span></span> <span data-ttu-id="0276e-227">적어도 하나의 제약 조건이 True여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-227">At least one constraint must evaluate to True.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="0276e-228">이 유형의 선행 제약 조건은 녹색, 빨간색 또는 파란색 점선으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-228">This type of precedence constraint appears as a dotted green, red, or blue line.</span></span>  
  
9. <span data-ttu-id="0276e-229">다른 일정에서 실행되는 태스크를 포함하는 다른 하위 계획을 추가하려면 도구 모음에서 **하위 계획 추가** 를 클릭하여 **하위 계획 속성** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-229">To add another subplan that contains tasks run on a different schedule, click **Add Subplan** on the toolbar to open the **Subplan Properties** dialog box.</span></span>  
  
10. <span data-ttu-id="0276e-230">다른 서버에 연결을 추가하려면:</span><span class="sxs-lookup"><span data-stu-id="0276e-230">To add connections to different servers:</span></span>  
  
    1.  <span data-ttu-id="0276e-231">디자인 화면의 도구 모음에서 **연결 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-231">In the design space's toolbar, click **Manage Connections**.</span></span>  
  
    2.  <span data-ttu-id="0276e-232">**연결 관리** 대화 상자에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-232">In the **Manage Connections** dialog box, click **Add**.</span></span>  
  
    3.  <span data-ttu-id="0276e-233">**연결 속성** 대화 상자의 **연결 이름** 상자에 만들려는 연결의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-233">In the **Connection Properties** dialog box, in the **Connection name** box, enter the name of the connection you are creating.</span></span>  
  
    4.  <span data-ttu-id="0276e-234">**SQL Server 데이터에 연결하려면 다음을 지정하세요.** 의 **서버 이름 선택 또는 입력** 상자에 사용하려는 SQL Server의 이름을 입력하거나 줄임표 **(...)** 를 클릭하여 **SQL Server** 대화 상자에서 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-234">Under **Specify the following to connect to SQL Server data**, in the **Select or enter a server name** box, either enter the name of the SQL server you want to use or click the ellipsis **(...)** and select a server in the **SQL Server** dialog box.</span></span> <span data-ttu-id="0276e-235">**SQL Server** 대화 상자에서 서버를 선택하는 경우 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-235">If you select a server from the **SQL Server** dialog box, click **OK**.</span></span>  
  
    5.  <span data-ttu-id="0276e-236">**서버 로그온 정보 입력**에서 **Windows NT 통합 보안 사용** 또는 **특정 사용자 이름 및 암호 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-236">Under **Enter information to log on to the server**, select either **Use Windows NT Integrated security** or **Use a specific user name and password**.</span></span> <span data-ttu-id="0276e-237">특정 사용자 이름 및 암호를 사용하도록 선택한 경우 **사용자 이름** 및 **암호** 상자에 각각 해당 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-237">If you elect to use a specific user name and password, enter that information in the **User name** and **Password** boxes, respectively.</span></span>  
  
    6.  <span data-ttu-id="0276e-238">**연결 속성** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-238">In the **Connection Properties** dialog box, click **OK**.</span></span>  
  
    7.  <span data-ttu-id="0276e-239">**연결 관리** 대화 상자에서 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-239">In the **Manage Connections** dialog box, click **Close**.</span></span>  
  
11. <span data-ttu-id="0276e-240">보고 옵션을 지정하려면:</span><span class="sxs-lookup"><span data-stu-id="0276e-240">To specify reporting options:</span></span>  
  
    1.  <span data-ttu-id="0276e-241">디자인 화면의 도구 모음에서 **보고 및 로깅**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-241">In the design space's toolbar, click **Reporting and Logging**.</span></span>  
  
    2.  <span data-ttu-id="0276e-242">**보고 및 로깅** 대화 상자의 **보고**에서 **텍스트 파일 보고서 생성** 또는 **전자 메일 받는 사람에게 보고서 보내기** 중 하나를 선택하거나 둘 다 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-242">In the **Reporting and Logging** dialog box, under **Reporting**, select **Generate a text file report** or **Send report to an email recipient** or both.</span></span>  
  
        1.  <span data-ttu-id="0276e-243">**텍스트 파일 보고서 생성**을 선택하는 경우 **새 파일 만들기** 또는 **파일에 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-243">If you select **Generate a text file report**, select either **Create a new file** or **Append to file**.</span></span>  
  
        2.  <span data-ttu-id="0276e-244">위에서 선택한 내용에 따라 **폴더** 또는 **파일 이름** 상자에 정보를 입력하여 새 파일이나 추가할 파일의 이름과 전체 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-244">Depending on the selection above, enter the name and full path of the new file or file to be appended by entering the information in the **Folder** or **File name** boxes.</span></span> <span data-ttu-id="0276e-245">또는 줄임표 **(...)** 를 클릭 하 고 **폴더 찾기-**_server_name_ 또는 **데이터베이스 파일 찾기-**_server_name_ 대화 상자에서 폴더나 파일 이름의 경로를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-245">Alternately, click on the ellipsis **(...)** and select the path to the folder or file name from the **Locate Folder -**_server_name_ or **Locate Database Files -**_server_name_ dialog boxes.</span></span>  
  
        3.  <span data-ttu-id="0276e-246">**전자 메일 받는 사람에게 보고서 보내기**를 선택하는 경우 **에이전트 운영자** 목록에서 전자 메일로 보낼 보고서의 받는 사람을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-246">If you select **Send report to an email recipient**, on the **Agent operator** list, select the recipient of the emailed report.</span></span>  
  
            > [!NOTE]  
            >  <span data-ttu-id="0276e-247">SQL Server 에이전트에서 메일을 보내려면 데이터베이스 메일을 사용하도록 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-247">SQL Server Agent must be configured to use Database Mail in order to send mail.</span></span> <span data-ttu-id="0276e-248">자세한 내용은 [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0276e-248">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)</span></span>  
  
    3.  <span data-ttu-id="0276e-249">보다 자세한 정보를 저장하려면 **로깅**에서 **확장 정보 기록**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-249">To save more detailed information, under **Logging**, select **Log extended information**.</span></span>  
  
    4.  <span data-ttu-id="0276e-250">유지 관리 계획 결과 정보를 다른 서버에 쓰려면 **원격 서버에 기록** 을 선택하고 **연결** 목록에서 서버 연결을 선택하거나 **새로 만들기** 를 클릭하고 **연결 속성** 대화 상자에 연결 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-250">To write maintenance plan results information to another server, select **Log to remote server** and either select a server connection from the **Connection** list or click **New** and enter the connection information in the **Connection Properties** dialog box.</span></span>  
  
    5.  <span data-ttu-id="0276e-251">**보고 및 로깅** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-251">In the **Reporting and Logging** dialog box, click **OK**.</span></span>  
  
12. <span data-ttu-id="0276e-252">로그 파일 뷰어에서 이 결과를 보려면 **개체 탐색기**에서 **유지 관리 계획** 폴더 또는 특정 유지 관리 계획을 마우스 오른쪽 단추로 클릭하고 **기록 보기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-252">To view the results in the log file viewer, in **Object Explorer**, right-click either the **Maintenance Plans** folder or the specific maintenance plan and select **View History**.</span></span>  
  
     <span data-ttu-id="0276e-253">**로그 파일 뷰어-**_server_name_ 대화 상자에서 다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-253">The following options are available on the **Log File Viewer -**_server_name_ dialog box.</span></span>  
  
     <span data-ttu-id="0276e-254">**로그 로드**</span><span class="sxs-lookup"><span data-stu-id="0276e-254">**Load Log**</span></span>  
     <span data-ttu-id="0276e-255">로드할 로그 파일을 지정할 수 있는 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-255">Open a dialog box where you can specify a log file to load.</span></span>  
  
     <span data-ttu-id="0276e-256">**내보내기**</span><span class="sxs-lookup"><span data-stu-id="0276e-256">**Export**</span></span>  
     <span data-ttu-id="0276e-257">**로그 파일 요약** 표에 표시된 정보를 텍스트 파일로 내보낼 수 있는 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-257">Open a dialog box that lets you export the information that is shown in the **Log file summary** grid to a text file.</span></span>  
  
     <span data-ttu-id="0276e-258">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="0276e-258">**Refresh**</span></span>  
     <span data-ttu-id="0276e-259">선택한 로그의 뷰를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-259">Refresh the view of the selected logs.</span></span> <span data-ttu-id="0276e-260">**새로 고침** 단추를 누르면 필터 설정을 적용하는 동안 대상 서버에서 선택한 로그를 다시 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-260">The **Refresh** button rereads the selected logs from the target server while applying any filter settings.</span></span>  
  
     <span data-ttu-id="0276e-261">**Filter**</span><span class="sxs-lookup"><span data-stu-id="0276e-261">**Filter**</span></span>  
     <span data-ttu-id="0276e-262">**연결**, **날짜**또는 기타 **일반** 필터 조건과 같이 로그 파일 필터링에 사용되는 설정을 지정할 수 있는 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-262">Open a dialog box that lets you specify settings that are used to filter the log file, such as **Connection**, **Date**, or other **General** filter criteria.</span></span>  
  
     <span data-ttu-id="0276e-263">**검색**</span><span class="sxs-lookup"><span data-stu-id="0276e-263">**Search**</span></span>  
     <span data-ttu-id="0276e-264">로그 파일에서 특정 텍스트를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-264">Search the log file for specific text.</span></span> <span data-ttu-id="0276e-265">와일드카드 문자를 사용한 검색은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-265">Searching with wildcard characters is not supported.</span></span>  
  
     <span data-ttu-id="0276e-266">**중지**</span><span class="sxs-lookup"><span data-stu-id="0276e-266">**Stop**</span></span>  
     <span data-ttu-id="0276e-267">로그 파일 항목의 로드를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-267">Stops loading the log file entries.</span></span> <span data-ttu-id="0276e-268">예를 들어 원격 또는 오프라인 로그 파일을 로드하는 데 시간이 오래 걸리며 최근 항목만 보려는 경우 이 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-268">For example, you can use this option if a remote or offline log file takes a long time to load, and you only want to view the most recent entries.</span></span>  
  
     <span data-ttu-id="0276e-269">**로그 파일 요약**</span><span class="sxs-lookup"><span data-stu-id="0276e-269">**Log file summary**</span></span>  
     <span data-ttu-id="0276e-270">이 정보 창에는 로그 파일 필터링에 대한 요약이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-270">This information panel displays a summary of the log file filtering.</span></span> <span data-ttu-id="0276e-271">파일을 필터링하지 않은 경우 **적용된 필터 없음**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-271">If the file is not filtered, you will see the following text, **No filter applied**.</span></span> <span data-ttu-id="0276e-272">로그에 필터를 적용한 경우에는 **로그 항목 필터링 조건:** \<filter criteria>라는 텍스트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-272">If a filter is applied to the log, you will see the following text, **Filter log entries where:** \<filter criteria>.</span></span>  
  
     <span data-ttu-id="0276e-273">**Date**</span><span class="sxs-lookup"><span data-stu-id="0276e-273">**Date**</span></span>  
     <span data-ttu-id="0276e-274">이벤트의 날짜를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-274">Displays the date of the event.</span></span>  
  
     <span data-ttu-id="0276e-275">**원본**</span><span class="sxs-lookup"><span data-stu-id="0276e-275">**Source**</span></span>  
     <span data-ttu-id="0276e-276">서비스의 이름(예: MSSQLSERVER)과 같이 이벤트가 생성된 원본 기능을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-276">Displays the source feature from which the event is created, such as the name of the service (MSSQLSERVER, for example).</span></span> <span data-ttu-id="0276e-277">이 열은 일부 로그 유형의 경우에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-277">This does not appear for all log types.</span></span>  
  
     <span data-ttu-id="0276e-278">**메시지**</span><span class="sxs-lookup"><span data-stu-id="0276e-278">**Message**</span></span>  
     <span data-ttu-id="0276e-279">이벤트와 관련된 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-279">Displays any messages associated with the event.</span></span>  
  
     <span data-ttu-id="0276e-280">**로그 유형**</span><span class="sxs-lookup"><span data-stu-id="0276e-280">**Log Type**</span></span>  
     <span data-ttu-id="0276e-281">이벤트가 속한 로그의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-281">Displays the type of log to which the event belongs.</span></span> <span data-ttu-id="0276e-282">선택한 모든 로그가 로그 파일 요약 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-282">All selected logs appear in the log file summary window.</span></span>  
  
     <span data-ttu-id="0276e-283">**로그 원본**</span><span class="sxs-lookup"><span data-stu-id="0276e-283">**Log Source**</span></span>  
     <span data-ttu-id="0276e-284">이벤트가 캡처되는 원본 로그에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-284">Displays a description of the source log in which the event is captured.</span></span>  
  
     <span data-ttu-id="0276e-285">**선택한 행 정보**</span><span class="sxs-lookup"><span data-stu-id="0276e-285">**Selected row details**</span></span>  
     <span data-ttu-id="0276e-286">선택한 이벤트 행에 대한 추가 정보를 페이지 아래쪽에 표시하려면 해당 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-286">Select a row to display additional details about the selected event row at the bottom of the page.</span></span> <span data-ttu-id="0276e-287">열을 표의 새 위치로 끌어서 다시 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-287">The columns can be reordered by dragging them to new locations in the grid.</span></span> <span data-ttu-id="0276e-288">표 머리글의 열 구분선을 왼쪽이나 오른쪽으로 끌어 열의 크기를 조정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-288">The columns can be resized by dragging the column separator bars in the grid header to the left or right.</span></span> <span data-ttu-id="0276e-289">열 내용에 맞게 열 너비를 자동 조정하려면 표 머리글의 열 구분선을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-289">Double-click the column separator bars in the grid header to automatically size the column to the content width.</span></span>  
  
     <span data-ttu-id="0276e-290">**인스턴스**</span><span class="sxs-lookup"><span data-stu-id="0276e-290">**Instance**</span></span>  
     <span data-ttu-id="0276e-291">이벤트가 발생한 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-291">The name of the instance on which the event occurred.</span></span> <span data-ttu-id="0276e-292">이 이름은 *컴퓨터 이름*\\*인스턴스 이름*으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0276e-292">This is displayed as *computer name*\\*instance name*.</span></span>  
  
  
