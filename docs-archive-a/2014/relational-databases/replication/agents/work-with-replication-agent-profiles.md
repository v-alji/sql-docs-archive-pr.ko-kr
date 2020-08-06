---
title: 복제 에이전트 프로필 작업 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], agents and profiles
- replication agent profiles [SQL Server]
- agents [SQL Server replication], profiles
- profiles [SQL Server], replication agents
ms.assetid: 9c290a88-4e9f-4a7e-aab5-4442137a9918
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fc20451edfb1096fca7e468effb14df78b51f758
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646940"
---
# <a name="work-with-replication-agent-profiles"></a><span data-ttu-id="1d806-102">복제 에이전트 프로필 작업</span><span class="sxs-lookup"><span data-stu-id="1d806-102">Work with Replication Agent Profiles</span></span>
  <span data-ttu-id="1d806-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 복제 에이전트 프로필로 작업하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-103">This topic describes how to work with Replication Agent Profiles in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="1d806-104">각 복제 에이전트의 동작은 에이전트 프로필을 통해 설정할 수 있는 매개 변수 집합으로 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-104">The behavior of each replication agent is controlled by a set of parameters that can be set through agent profiles.</span></span> <span data-ttu-id="1d806-105">각 에이전트에는 기본 프로필이 있으며 일부 에이전트에는 미리 정의된 프로필이 추가되어 있습니다. 이러한 프로필은 에이전트에 대해 한 번에 하나만 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-105">Each agent has a default profile, and some have additional predefined profiles; at a given time, only one profile is active for an agent.</span></span>  
  
 <span data-ttu-id="1d806-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="1d806-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1d806-107">**다음을 사용하여 복제 에이전트 프로필로 작업하려면**</span><span class="sxs-lookup"><span data-stu-id="1d806-107">**To work with Replication Agent Profiles, using:**</span></span>  
  
     [<span data-ttu-id="1d806-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1d806-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
    -   <span data-ttu-id="1d806-109">에이전트 프로필 대화 상자에 액세스</span><span class="sxs-lookup"><span data-stu-id="1d806-109">Access the Agent Profiles dialog box</span></span>  
  
    -   <span data-ttu-id="1d806-110">에이전트에 대해 프로필 지정</span><span class="sxs-lookup"><span data-stu-id="1d806-110">Specify a profile for an agent</span></span>  
  
    -   <span data-ttu-id="1d806-111">프로필 만들기</span><span class="sxs-lookup"><span data-stu-id="1d806-111">Create a profile</span></span>  
  
    -   <span data-ttu-id="1d806-112">프로필 수정</span><span class="sxs-lookup"><span data-stu-id="1d806-112">Modify a profile</span></span>  
  
    -   <span data-ttu-id="1d806-113">프로필 삭제</span><span class="sxs-lookup"><span data-stu-id="1d806-113">Delete a profile</span></span>  
  
     [<span data-ttu-id="1d806-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1d806-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
    -   <span data-ttu-id="1d806-115">프로필 만들기</span><span class="sxs-lookup"><span data-stu-id="1d806-115">Create a profile</span></span>  
  
    -   <span data-ttu-id="1d806-116">프로필 수정</span><span class="sxs-lookup"><span data-stu-id="1d806-116">Modify a profile</span></span>  
  
    -   <span data-ttu-id="1d806-117">프로필 삭제</span><span class="sxs-lookup"><span data-stu-id="1d806-117">Delete a profile</span></span>  
  
    -   <span data-ttu-id="1d806-118">동기화 중 에이전트 프로필 사용</span><span class="sxs-lookup"><span data-stu-id="1d806-118">Use agent profiles during synchronization</span></span>  
  
    -   <span data-ttu-id="1d806-119">Transact-SQL 예</span><span class="sxs-lookup"><span data-stu-id="1d806-119">Transact-SQL example</span></span>  
  
     [<span data-ttu-id="1d806-120">RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="1d806-120">Replication Management Objects</span></span>](#RMOProcedure)  
  
    -   <span data-ttu-id="1d806-121">프로필 만들기</span><span class="sxs-lookup"><span data-stu-id="1d806-121">Create a profile</span></span>  
  
    -   <span data-ttu-id="1d806-122">프로필 수정</span><span class="sxs-lookup"><span data-stu-id="1d806-122">Modify a profile</span></span>  
  
    -   <span data-ttu-id="1d806-123">프로필 삭제</span><span class="sxs-lookup"><span data-stu-id="1d806-123">Delete a profile</span></span>  
  
-   <span data-ttu-id="1d806-124">**후속 작업:**  [에이전트 매개 변수 변경 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="1d806-124">**Follow Up:**  [After Changing Agent Parameters](#FollowUp)</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1d806-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="1d806-125">Using SQL Server Management Studio</span></span>  
  
###  <a name="to-access-the-agent-profiles-dialog-box-from-sql-server-management-studio"></a><a name="Access_SSMS"></a> <span data-ttu-id="1d806-126">SQL Server Management Studio에서 에이전트 프로필 대화 상자에 액세스하려면</span><span class="sxs-lookup"><span data-stu-id="1d806-126">To access the Agent Profiles dialog box from SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="1d806-127">**배포자 속성 - \<Distributor>** 대화 상자의 **일반** 페이지에서 **프로필 기본값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-127">On the **General** page of the **Distributor Properties - \<Distributor>** dialog box, click **Profile Defaults**.</span></span>  
  
#### <a name="to-access-the-agent-profiles-dialog-box-from-replication-monitor"></a><span data-ttu-id="1d806-128">복제 모니터에서 에이전트 프로필 대화 상자에 액세스하려면</span><span class="sxs-lookup"><span data-stu-id="1d806-128">To access the Agent Profiles dialog box from Replication Monitor</span></span>  
  
-   <span data-ttu-id="1d806-129">모든 에이전트에 대한 대화 상자를 열려면 게시자를 마우스 오른쪽 단추로 클릭한 다음 **에이전트 프로필**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-129">To open the dialog box for all agents, right-click a Publisher, and then click **Agent Profiles**.</span></span>  
  
-   <span data-ttu-id="1d806-130">단일 에이전트에 대한 대화 상자를 열려면 다음을 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="1d806-130">To open the dialog box for a single agent:</span></span>  
  
    1.  <span data-ttu-id="1d806-131">복제 모니터에서 왼쪽 창의 게시자 그룹을 확장하고 해당 게시자를 확장한 다음 해당 게시를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-131">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
    2.  <span data-ttu-id="1d806-132">배포 에이전트 및 병합 에이전트 프로필의 경우 **모든 구독** 탭에서 구독을 마우스 오른쪽 단추로 클릭한 다음 **에이전트 프로필**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-132">For Distribution Agent and Merge Agent profiles, right-click a subscription on the **All Subscriptions** tab, and then click **Agent Profile**.</span></span> <span data-ttu-id="1d806-133">다른 에이전트의 경우 **에이전트** 탭에서 에이전트를 마우스 오른쪽 단추로 클릭하고 **에이전트 프로필**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-133">For other agents, right-click the agent on the **Agents** tab, and then click **Agent Profile**.</span></span>  
  
###  <a name="to-specify-a-profile-for-an-agent"></a><a name="Specify_SSMS"></a> <span data-ttu-id="1d806-134">에이전트에 대해 프로필을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="1d806-134">To specify a profile for an agent</span></span>  
  
1.  <span data-ttu-id="1d806-135">**에이전트 프로필** 대화 상자에 둘 이상의 에이전트에 대한 프로필이 표시되면 에이전트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-135">If the **Agent Profiles** dialog box displays profiles for more than one agent, select an agent.</span></span>  
  
2.  <span data-ttu-id="1d806-136">**에이전트 프로필** 표의 **새 에이전트에 대한 기본값** 열에서 프로필을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-136">Select a profile in the **Default for new** column of the **Agent profiles** grid.</span></span> <span data-ttu-id="1d806-137">기본적으로 프로필은 새 게시 및 구독에 대한 에이전트에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-137">By default, the profile is only applied to agents for new publications and subscriptions.</span></span>  
  
3.  <span data-ttu-id="1d806-138">기존 게시 또는 구독에 대해 선택한 유형의 모든 에이전트에서 이 프로필을 사용하려면 **기존 에이전트 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-138">To specify that all agents of the selected type for existing publications or subscriptions should use this profile, click **Change existing agents**.</span></span>  
  
###  <a name="to-view-and-edit-the-parameters-associated-with-a-profile"></a><a name="Modify_SSMS"></a> <span data-ttu-id="1d806-139">프로필과 연결된 매개 변수를 보고 편집하려면</span><span class="sxs-lookup"><span data-stu-id="1d806-139">To view and edit the parameters associated with a profile</span></span>  
  
1.  <span data-ttu-id="1d806-140">**에이전트 프로필** 대화 상자에 둘 이상의 에이전트에 대한 프로필이 표시되면 에이전트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-140">If the **Agent Profiles** dialog box displays profiles for more than one agent, select an agent.</span></span>  
  
2.  <span data-ttu-id="1d806-141">프로필 옆에 있는 속성 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-141">Click the properties button (**...**) next to a profile.</span></span>  
  
3.  <span data-ttu-id="1d806-142">**\<ProfileName> 프로필 속성** 대화 상자에서 매개 변수 및 값을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-142">View the parameters and values in the **\<ProfileName> Profile Properties** dialog box.</span></span>  
  
    -   <span data-ttu-id="1d806-143">사용자 정의 프로필의 매개 변수는 편집할 수 있지만 미리 정의된 시스템 프로필의 매개 변수는 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-143">Parameters in user-defined profiles can be edited; parameters in predefined system profiles cannot.</span></span>  
  
    -   <span data-ttu-id="1d806-144">에이전트에 대한 모든 매개 변수를 보려면 **이 프로필에서 사용되는 매개 변수만 표시** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-144">To view all parameters for an agent, clear the **Show only parameters used in this profile** check box.</span></span> <span data-ttu-id="1d806-145">에이전트 매개 변수에 대한 자세한 내용은 이 항목 끝에 있는 링크를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1d806-145">For information about agent parameters, see the links at the end of this topic.</span></span>  
  
4.  <span data-ttu-id="1d806-146">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-146">Click **Close**.</span></span>  
  
###  <a name="to-create-a-user-defined-profile"></a><a name="Create_SSMS"></a> <span data-ttu-id="1d806-147">사용자 정의 프로필을 만들려면</span><span class="sxs-lookup"><span data-stu-id="1d806-147">To create a user-defined profile</span></span>  
  
1.  <span data-ttu-id="1d806-148">**에이전트 프로필** 대화 상자에 둘 이상의 에이전트에 대한 프로필이 표시되면 에이전트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-148">If the **Agent Profiles** dialog box displays profiles for more than one agent, select an agent.</span></span>  
  
2.  <span data-ttu-id="1d806-149">**새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-149">Click **New**.</span></span>  
  
3.  <span data-ttu-id="1d806-150">**새 에이전트 프로필** 초기화 대화 상자에서 새 프로필의 기반으로 사용할 기존 프로필을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-150">In the **New Agent Profile** initialization dialog box, select an existing profile on which to base the new profile.</span></span>  
  
4.  <span data-ttu-id="1d806-151">**새 에이전트 프로필** 대화 상자에서 **이름** 및 **설명** 입력란에 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-151">In the **New Agent Profile** dialog box, enter values in the **Name** and **Description** text boxes.</span></span>  
  
5.  <span data-ttu-id="1d806-152">매개 변수를 수정하여 프로필을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-152">Modify parameters to tailor the profile.</span></span> <span data-ttu-id="1d806-153">에이전트에 대한 모든 매개 변수를 보려면 **이 프로필에서 사용되는 매개 변수만 표시** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-153">To view all parameters for an agent, clear the **Show only parameters used in this profile** check box.</span></span> <span data-ttu-id="1d806-154">에이전트 매개 변수에 대한 자세한 내용은 이 항목 끝에 있는 링크를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1d806-154">For information about agent parameters, see the links at the end of this topic.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
###  <a name="to-delete-a-user-defined-profile"></a><a name="Delete_SSMS"></a> <span data-ttu-id="1d806-155">사용자 정의 프로필을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="1d806-155">To delete a user-defined profile</span></span>  
  
1.  <span data-ttu-id="1d806-156">**에이전트 프로필** 대화 상자에 둘 이상의 에이전트에 대한 프로필이 표시되면 에이전트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-156">If the **Agent Profiles** dialog box displays profiles for more than one agent, select an agent.</span></span>  
  
2.  <span data-ttu-id="1d806-157">프로필이 하나 이상의 에이전트와 연결되어 있으면 해당 에이전트의 프로필을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-157">If a profile is associated with one or more agents, change the profile for those agents:</span></span>  
  
    1.  <span data-ttu-id="1d806-158">**에이전트 프로필** 표에서 다른 프로필을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-158">Select a different profile in the **Agent profiles** grid.</span></span>  
  
    2.  <span data-ttu-id="1d806-159">**기존 에이전트 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-159">Click **Change existing agents**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="1d806-160">이렇게 하면 삭제할 프로필을 사용하는 에이전트 외에 기존 게시 또는 구독에 대해 선택한 유형의 모든 에이전트에 대한 프로필까지 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-160">This will change the profile for all agents of the selected type for existing publications or subscriptions, not only the ones using the profile you want to delete.</span></span>  
  
3.  <span data-ttu-id="1d806-161">삭제할 프로필을 선택한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-161">Select the profile you want to delete, and then click **Delete**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1d806-162">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="1d806-162">Using Transact-SQL</span></span>  
  
###  <a name="to-create-a-new-agent-profile"></a><a name="Create_tsql"></a> <span data-ttu-id="1d806-163">새 에이전트 프로필을 만들려면</span><span class="sxs-lookup"><span data-stu-id="1d806-163">To create a new agent profile</span></span>  
  
1.  <span data-ttu-id="1d806-164">배포자에서 [sp_add_agent_profile&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-164">At the Distributor, execute [sp_add_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql).</span></span> <span data-ttu-id="1d806-165">을 지정 하 **@name** 고에 값으로 **1** 을 지정 **@profile_type** 하 고에 다음 값 중 하나를 지정 합니다 **@agent_type** .</span><span class="sxs-lookup"><span data-stu-id="1d806-165">Specify **@name**, a value of **1** for **@profile_type**, and one of the following values for **@agent_type**:</span></span>  
  
    -   <span data-ttu-id="1d806-166">**\@profile_type** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-166">**1** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span></span>  
  
    -   <span data-ttu-id="1d806-167">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-167">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span></span>  
  
    -   <span data-ttu-id="1d806-168">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-168">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span></span>  
  
    -   <span data-ttu-id="1d806-169">**4** - [Replication Merge Agent](replication-merge-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-169">**4** - [Replication Merge Agent](replication-merge-agent.md)</span></span>  
  
    -   <span data-ttu-id="1d806-170">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-170">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span></span>  
  
     <span data-ttu-id="1d806-171">이 프로필이 해당 유형의 복제 에이전트에 대한 새 기본 프로필이 될 경우 **@profile_type** 에 값 **@default**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-171">If this profile will become the new default profile for its type of replication agent, specify a value of **1** for **@default**.</span></span> <span data-ttu-id="1d806-172">새 프로필의 식별자는 output 매개 변수를 사용 하 여 반환 됩니다 **@profile_id** .</span><span class="sxs-lookup"><span data-stu-id="1d806-172">The identifier for the new profile is returned using the **@profile_id** output parameter.</span></span> <span data-ttu-id="1d806-173">이 출력 매개 변수는 지정된 에이전트 유형의 기본 프로필을 기반으로 한 프로필 매개 변수 집합을 사용하여 새 프로필을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-173">This creates a new profile with a set of profile parameters based on the default profile for the given agent type.</span></span>  
  
2.  <span data-ttu-id="1d806-174">새 프로필이 만들어진 후 기본 매개 변수를 추가, 제거 또는 수정하여 프로필을 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-174">After the new profile has been created, add, remove, or modify the default parameters to customize the profile.</span></span>  
  
###  <a name="to-modify-an-existing-agent-profile"></a><a name="Modify_tsql"></a> <span data-ttu-id="1d806-175">기존 에이전트 프로필을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="1d806-175">To modify an existing agent profile</span></span>  
  
1.  <span data-ttu-id="1d806-176">배포자에서 [sp_help_agent_profile&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-176">At the Distributor, execute [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql).</span></span> <span data-ttu-id="1d806-177">에 다음 값 중 하나를 지정 합니다 **@agent_type** .</span><span class="sxs-lookup"><span data-stu-id="1d806-177">Specify one of the following values for **@agent_type**:</span></span>  
  
    -   <span data-ttu-id="1d806-178">**\@profile_type** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-178">**1** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span></span>  
  
    -   <span data-ttu-id="1d806-179">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-179">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span></span>  
  
    -   <span data-ttu-id="1d806-180">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-180">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span></span>  
  
    -   <span data-ttu-id="1d806-181">**4** - [Replication Merge Agent](replication-merge-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-181">**4** - [Replication Merge Agent](replication-merge-agent.md)</span></span>  
  
    -   <span data-ttu-id="1d806-182">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-182">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span></span>  
  
     <span data-ttu-id="1d806-183">이렇게 하면 지정된 에이전트 유형에 대해 모든 이벤트가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-183">This returns all profiles for the specified type of agent.</span></span> <span data-ttu-id="1d806-184">변경할 프로필의 결과 집합에 있는 **profile_id** 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-184">Note the value of **profile_id** in the result set for the profile to change.</span></span>  
  
2.  <span data-ttu-id="1d806-185">배포자에서 [sp_help_agent_parameter&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-185">At the Distributor, execute [sp_help_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql).</span></span> <span data-ttu-id="1d806-186">에 대해 1 단계에서 가져온 프로필 식별자를 지정 **@profile_id** 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-186">Specify the profile identifier from step 1 for **@profile_id**.</span></span> <span data-ttu-id="1d806-187">그러면 해당 프로필의 모든 매개 변수가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-187">This returns all parameters for the profile.</span></span> <span data-ttu-id="1d806-188">프로필에서 수정하거나 제거할 매개 변수의 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-188">Note the name of any parameters to modify or remove from the profile.</span></span>  
  
3.  <span data-ttu-id="1d806-189">프로필의 매개 변수 값을 변경하려면 [sp_change_agent_profile&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-189">To change the value of a parameter in a profile, execute [sp_change_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql).</span></span> <span data-ttu-id="1d806-190">에 1 단계에서 가져온 프로필 식별자를 지정 하 **@profile_id** 고,에 변경할 매개 변수의 이름을 지정 하 **@property** 고, 매개 변수의 새 값을 지정 **@value** 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-190">Specify the profile identifier from step 1 for **@profile_id**, the name of the parameter to change for **@property**, and a new value for the parameter for **@value**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1d806-191">기존 에이전트 프로필은 에이전트의 기본 프로필이 되도록 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-191">You cannot change an existing agent profile to become the default profile for an agent.</span></span> <span data-ttu-id="1d806-192">대신 이전 절차에서와 같이 새 프로필을 기본 프로필로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-192">You must instead create a new profile as the default profile, as shown in the previous procedure.</span></span>  
  
4.  <span data-ttu-id="1d806-193">프로필에서 매개 변수를 제거하려면 [sp_drop_agent_parameter&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-193">To remove a parameter from a profile, execute [sp_drop_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql).</span></span> <span data-ttu-id="1d806-194">에 1 단계에서 가져온 프로필 식별자를 지정 하 **@profile_id** 고에 제거할 매개 변수의 이름을 지정 **@parameter_name** 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-194">Specify the profile identifier from step 1 for **@profile_id** and the name of the parameter to remove for **@parameter_name**.</span></span>  
  
5.  <span data-ttu-id="1d806-195">프로필에 새 매개 변수를 추가하려면 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-195">To add a new parameter to a profile, you must do the following:</span></span>  
  
    -   <span data-ttu-id="1d806-196">배포자에서 [MSagentparameterlist&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msagentparameterlist-transact-sql) 테이블을 쿼리하여 각 에이전트 유형에 설정할 수 있는 프로필 매개 변수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-196">Query the [MSagentparameterlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msagentparameterlist-transact-sql) table at the Distributor to determine which profile parameters can be set for each agent type.</span></span>  
  
    -   <span data-ttu-id="1d806-197">배포자에서 [sp_add_agent_parameter&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-197">At the Distributor, execute [sp_add_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql).</span></span> <span data-ttu-id="1d806-198">에 1 단계에서 가져온 프로필 식별자를 지정 하 **@profile_id** 고,에 추가할 유효한 매개 변수의 이름을 지정 하 **@parameter_name** 고, 매개 변수의 값을 지정 합니다 **@parameter_value** .</span><span class="sxs-lookup"><span data-stu-id="1d806-198">Specify the profile identifier from step 1 for **@profile_id**, the name of a valid parameter to add for **@parameter_name**, and the value of the parameter for **@parameter_value**.</span></span>  
  
###  <a name="to-delete-an-agent-profile"></a><a name="Delete_tsql"></a> <span data-ttu-id="1d806-199">에이전트 프로필을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="1d806-199">To delete an agent profile</span></span>  
  
1.  <span data-ttu-id="1d806-200">배포자에서 [sp_help_agent_profile&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-200">At the Distributor, execute [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql).</span></span> <span data-ttu-id="1d806-201">에 다음 값 중 하나를 지정 합니다 **@agent_type** .</span><span class="sxs-lookup"><span data-stu-id="1d806-201">Specify one of the following values for **@agent_type**:</span></span>  
  
    -   <span data-ttu-id="1d806-202">**\@profile_type** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-202">**1** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span></span>  
  
    -   <span data-ttu-id="1d806-203">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-203">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span></span>  
  
    -   <span data-ttu-id="1d806-204">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-204">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span></span>  
  
    -   <span data-ttu-id="1d806-205">**4** - [Replication Merge Agent](replication-merge-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-205">**4** - [Replication Merge Agent](replication-merge-agent.md)</span></span>  
  
    -   <span data-ttu-id="1d806-206">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-206">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span></span>  
  
     <span data-ttu-id="1d806-207">이렇게 하면 지정된 에이전트 유형에 대해 모든 이벤트가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-207">This returns all profiles for the specified type of agent.</span></span> <span data-ttu-id="1d806-208">제거할 프로필의 결과 집합에 있는 **profile_id** 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-208">Note the value of **profile_id** in the result set for the profile to remove.</span></span>  
  
2.  <span data-ttu-id="1d806-209">배포자에서 [sp_drop_agent_profile&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-209">At the Distributor, execute [sp_drop_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql).</span></span> <span data-ttu-id="1d806-210">에 대해 1 단계에서 가져온 프로필 식별자를 지정 **@profile_id** 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-210">Specify the profile identifier from step 1 for **@profile_id**.</span></span>  
  
###  <a name="to-use-agent-profiles-during-synchronization"></a><a name="Synch_tsql"></a> <span data-ttu-id="1d806-211">동기화 중 에이전트 프로필을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="1d806-211">To use agent profiles during synchronization</span></span>  
  
1.  <span data-ttu-id="1d806-212">배포자에서 [sp_help_agent_profile&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-212">At the Distributor, execute [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql).</span></span> <span data-ttu-id="1d806-213">에 다음 값 중 하나를 지정 합니다 **@agent_type** .</span><span class="sxs-lookup"><span data-stu-id="1d806-213">Specify one of the following values for **@agent_type**:</span></span>  
  
    -   <span data-ttu-id="1d806-214">**\@profile_type** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-214">**1** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span></span>  
  
    -   <span data-ttu-id="1d806-215">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-215">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span></span>  
  
    -   <span data-ttu-id="1d806-216">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-216">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span></span>  
  
    -   <span data-ttu-id="1d806-217">**4** - [Replication Merge Agent](replication-merge-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-217">**4** - [Replication Merge Agent](replication-merge-agent.md)</span></span>  
  
    -   <span data-ttu-id="1d806-218">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="1d806-218">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span></span>  
  
     <span data-ttu-id="1d806-219">이렇게 하면 지정된 에이전트 유형에 대해 모든 이벤트가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-219">This returns all profiles for the specified type of agent.</span></span> <span data-ttu-id="1d806-220">`profile_name`사용할 프로필의 결과 집합에서 값을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-220">Note the value of `profile_name` in the result set for the profile to use.</span></span>  
  
2.  <span data-ttu-id="1d806-221">에이전트가 에이전트 작업에서 시작 되는 경우 에이전트를 시작 하는 작업 단계를 편집 하 여 `profile_name` **-ProfileName** 명령줄 매개 변수 뒤에 1 단계에서 얻은 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-221">If the agent is started from an agent job, edit the job step that starts the agent to specify the value of `profile_name` obtained in step 1 after the **-ProfileName** command-line parameter.</span></span> <span data-ttu-id="1d806-222">자세한 내용은 [복제 에이전트의 명령 프롬프트 매개 변수 보기 및 수정&#40;SQL Server Management Studio&#41;](view-and-modify-replication-agent-command-prompt-parameters.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1d806-222">For more information, see [View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;](view-and-modify-replication-agent-command-prompt-parameters.md).</span></span>  
  
3.  <span data-ttu-id="1d806-223">명령 프롬프트에서 에이전트를 시작할 때 `profile_name` **-ProfileName** 명령줄 매개 변수 뒤에 1 단계에서 얻은 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-223">When starting the agent from the command prompt, specify the value of `profile_name` obtained in step 1 after the **-ProfileName** command-line parameter.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="1d806-224">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1d806-224">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="1d806-225">이 예제에서는 **custom_merge**라는 병합 에이전트의 사용자 지정 프로필을 만들고, **-UploadReadChangesPerBatch** 매개 변수의 값을 변경하고, 새 **-ExchangeType** 매개 변수를 추가하고, 만들어진 프로필에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-225">This example creates a custom profile for the Merge Agent named **custom_merge**, changes the value of the **-UploadReadChangesPerBatch** parameter, adds a new **-ExchangeType** parameter, and returns information on the profile that is created.</span></span>  
  
 [!code-sql[HowTo#sp_addagentprofileparam](../../../snippets/tsql/SQL15/replication/howto/tsql/createperfparammerge.sql#sp_addagentprofileparam)]  
  
##  <a name="using-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="1d806-226">RMO 사용</span><span class="sxs-lookup"><span data-stu-id="1d806-226">Using RMO</span></span>  
  
###  <a name="to-create-a-new-agent-profile"></a><a name="Create_RMO"></a> <span data-ttu-id="1d806-227">새 에이전트 프로필을 만들려면</span><span class="sxs-lookup"><span data-stu-id="1d806-227">To create a new agent profile</span></span>  
  
1.  <span data-ttu-id="1d806-228"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스의 인스턴스를 사용하여 배포자에 대한 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-228">Create a connection to the Distributor by using an instance of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="1d806-229"><xref:Microsoft.SqlServer.Replication.AgentProfile> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-229">Create an instance of the <xref:Microsoft.SqlServer.Replication.AgentProfile> class.</span></span>  
  
3.  <span data-ttu-id="1d806-230">개체의 다음 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-230">Set the following properties on the object:</span></span>  
  
    -   <span data-ttu-id="1d806-231"><xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> - 프로필의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-231"><xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> - the name for the profile.</span></span>  
  
    -   <span data-ttu-id="1d806-232"><xref:Microsoft.SqlServer.Replication.AgentProfile.AgentType%2A> - 프로필을 만들 복제 에이전트의 유형을 지정하는 <xref:Microsoft.SqlServer.Replication.AgentType> 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-232"><xref:Microsoft.SqlServer.Replication.AgentProfile.AgentType%2A> - an <xref:Microsoft.SqlServer.Replication.AgentType> value that specifies the type of replication agent for which the profile is being created.</span></span>  
  
    -   <span data-ttu-id="1d806-233"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - 1단계에서 만든 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 입니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-233"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> created in step 1.</span></span>  
  
    -   <span data-ttu-id="1d806-234"><xref:Microsoft.SqlServer.Replication.AgentProfile.Description%2A> (옵션) - 프로필에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-234">(Optional) <xref:Microsoft.SqlServer.Replication.AgentProfile.Description%2A> - a description of the profile.</span></span>  
  
    -   <span data-ttu-id="1d806-235"><xref:Microsoft.SqlServer.Replication.AgentProfile.Default%2A>(옵션) - 이 <xref:Microsoft.SqlServer.Replication.AgentType>의 모든 새 에이전트 작업에서 기본적으로 이 프로필이 사용되는 경우 이 속성을 `true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-235">(Optional) <xref:Microsoft.SqlServer.Replication.AgentProfile.Default%2A> - set this property to `true` if all new agent jobs for this <xref:Microsoft.SqlServer.Replication.AgentType> will use this profile by default.</span></span>  
  
4.  <span data-ttu-id="1d806-236"><xref:Microsoft.SqlServer.Replication.AgentProfile.Create%2A> 메서드를 호출하여 서버에 프로필을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-236">Call the <xref:Microsoft.SqlServer.Replication.AgentProfile.Create%2A> method to create the profile on the server.</span></span>  
  
5.  <span data-ttu-id="1d806-237">서버에 프로필이 있으면 복제 에이전트 매개 변수의 값을 추가, 제거 또는 변경하여 프로필을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-237">Once the profile exists on the server, you can customize it by adding, removing, or changing the values of replication agent parameters.</span></span>  
  
6.  <span data-ttu-id="1d806-238">기존 복제 에이전트 작업에 프로필을 할당하려면 <xref:Microsoft.SqlServer.Replication.AgentProfile.AssignToAgent%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-238">To assign the profile to an existing replication agent job, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.AssignToAgent%2A> method.</span></span> <span data-ttu-id="1d806-239">*distributionDBName* 에 대한 배포 데이터베이스 이름 및 *agentID*에 대한 작업 ID를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-239">Pass the name of the distribution database for *distributionDBName* and the ID of the job for *agentID*.</span></span>  
  
###  <a name="to-modify-an-existing-agent-profile"></a><a name="Modify_RMO"></a> <span data-ttu-id="1d806-240">기존 에이전트 프로필을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="1d806-240">To modify an existing agent profile</span></span>  
  
1.  <span data-ttu-id="1d806-241"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스의 인스턴스를 사용하여 배포자에 대한 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-241">Create a connection to the Distributor by using an instance of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="1d806-242"><xref:Microsoft.SqlServer.Replication.ReplicationServer> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-242">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span> <span data-ttu-id="1d806-243">1단계에서 만든 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-243">Pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object created in step 1.</span></span>  
  
3.  <span data-ttu-id="1d806-244"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-244">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="1d806-245">이 메서드가 `false`를 반환하는 경우 배포자가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-245">If this method returns `false`, verify that the Distributor exists.</span></span>  
  
4.  <span data-ttu-id="1d806-246"><xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumAgentProfiles%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-246">Call the <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumAgentProfiles%2A> method.</span></span> <span data-ttu-id="1d806-247"><xref:Microsoft.SqlServer.Replication.AgentType> 값을 전달하여 반환되는 프로필의 범위를 특정 유형의 복제 에이전트로 좁힙니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-247">Pass an <xref:Microsoft.SqlServer.Replication.AgentType> value to narrow down the returned profiles to a specific type of replication agent.</span></span>  
  
5.  <span data-ttu-id="1d806-248">반환된 <xref:Microsoft.SqlServer.Replication.AgentProfile> 에서 원하는 <xref:System.Collections.ArrayList>개체를 가져옵니다. 이때 개체의 <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> 속성은 프로필 이름과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-248">Get the desired <xref:Microsoft.SqlServer.Replication.AgentProfile> object from the returned <xref:System.Collections.ArrayList>, where the <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> property of the object matches the profile name.</span></span>  
  
6.  <span data-ttu-id="1d806-249"><xref:Microsoft.SqlServer.Replication.AgentProfile> 의 다음 메서드 중 하나를 호출하여 프로필을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-249">Call one of the following methods of <xref:Microsoft.SqlServer.Replication.AgentProfile> to change the profile:</span></span>  
  
    -   <span data-ttu-id="1d806-250"><xref:Microsoft.SqlServer.Replication.AgentProfile.AddParameter%2A> - 프로필에 지원되는 매개 변수를 추가합니다. 여기서 *name* 은 복제 에이전트 매개 변수의 이름이고 *value* 는 지정된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-250"><xref:Microsoft.SqlServer.Replication.AgentProfile.AddParameter%2A> - adds a supported parameter to the profile, where *name* is the name of the replication agent parameter and *value* is the specified value.</span></span> <span data-ttu-id="1d806-251">지정된 에이전트 유형에 대해 지원되는 모든 에이전트 매개 변수를 열거하려면 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-251">To enumerate all supported agent parameters for a given agent type, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> method.</span></span> <span data-ttu-id="1d806-252">이 메서드는 지원되는 모든 매개 변수를 나타내는 <xref:System.Collections.ArrayList> 개체의 <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-252">This method returns an <xref:System.Collections.ArrayList> of <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> objects that represent all supported parameters.</span></span>  
  
    -   <span data-ttu-id="1d806-253"><xref:Microsoft.SqlServer.Replication.AgentProfile.RemoveParameter%2A> - 프로필에서 기존 매개 변수를 제거합니다. 여기서 *name* 은 복제 에이전트 매개 변수의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-253"><xref:Microsoft.SqlServer.Replication.AgentProfile.RemoveParameter%2A> - removes an existing parameter from the profile, where *name* is the name of the replication agent parameter.</span></span> <span data-ttu-id="1d806-254">프로필에 대해 정의된 현재의 모든 에이전트 매개 변수를 열거하려면 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-254">To enumerate all current agent parameters defined for the profile, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> method.</span></span> <span data-ttu-id="1d806-255">이 메서드는 이 프로필의 기존 매개 변수를 나타내는 <xref:System.Collections.ArrayList> 개체의 <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-255">This method returns an <xref:System.Collections.ArrayList> of <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> objects that represent the existing parameter for this profile.</span></span>  
  
    -   <span data-ttu-id="1d806-256"><xref:Microsoft.SqlServer.Replication.AgentProfile.ChangeParameter%2A> - 프로필의 기존 매개 변수 설정을 변경합니다. 여기서 *name* 은 에이전트 매개 변수의 이름이고 *newValue* 는 매개 변수를 변경할 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-256"><xref:Microsoft.SqlServer.Replication.AgentProfile.ChangeParameter%2A> - changes the setting of an existing parameter in the profile, where *name* is the name of the agent parameter and *newValue* is the value to which the parameter is being changed.</span></span> <span data-ttu-id="1d806-257">프로필에 대해 정의된 현재의 모든 에이전트 매개 변수를 열거하려면 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-257">To enumerate all current agent parameters defined for the profile, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> method.</span></span> <span data-ttu-id="1d806-258">이 메서드는 이 프로필의 기존 매개 변수를 나타내는 <xref:System.Collections.ArrayList> 개체의 <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-258">This method returns an <xref:System.Collections.ArrayList> of <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> objects that represent the existing parameter for this profile.</span></span> <span data-ttu-id="1d806-259">지원되는 모든 에이전트 매개 변수 설정을 열거하려면 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-259">To enumerate all supported agent parameter settings, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> method.</span></span> <span data-ttu-id="1d806-260">이 메서드는 모든 매개 변수에 대해 지원되는 값을 나타내는 <xref:System.Collections.ArrayList> 개체의 <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-260">This method returns an <xref:System.Collections.ArrayList> of <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> objects that represent the supported values for all parameters.</span></span>  
  
###  <a name="to-delete-an-agent-profile"></a><a name="Delete_RMO"></a> <span data-ttu-id="1d806-261">에이전트 프로필을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="1d806-261">To delete an agent profile</span></span>  
  
1.  <span data-ttu-id="1d806-262"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스의 인스턴스를 사용하여 배포자에 대한 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-262">Create a connection to the Distributor by using an instance of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="1d806-263"><xref:Microsoft.SqlServer.Replication.AgentProfile> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-263">Create an instance of the <xref:Microsoft.SqlServer.Replication.AgentProfile> class.</span></span> <span data-ttu-id="1d806-264"><xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> 에 프로필 이름을 설정하고 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 에 1단계에서 만든 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-264">Set the name of the profile for <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> and the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="1d806-265"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-265">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="1d806-266">이 메서드가 `false`를 반환하는 경우 지정한 이름이 올바르지 않거나 해당 프로필이 서버에 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-266">If this method returns `false`, either the specified name was incorrect or the profile does not exist on the server.</span></span>  
  
4.  <span data-ttu-id="1d806-267"><xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A> 속성이 고객 프로필을 나타내는 <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.User>로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-267">Verify that the <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A> property is set to <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.User>, which indicates a customer profile.</span></span> <span data-ttu-id="1d806-268"><xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.System> 의 값이 <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A>인 프로필은 제거하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-268">You should not remove a profile that has a value of <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.System> for <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A>.</span></span>  
  
5.  <span data-ttu-id="1d806-269"><xref:Microsoft.SqlServer.Replication.AgentProfile.Remove%2A> 메서드를 호출하여 이 개체가 나타내는 사용자 정의 프로필을 서버에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-269">Call the <xref:Microsoft.SqlServer.Replication.AgentProfile.Remove%2A> method to remove the user-defined profile represented by this object from the server.</span></span>  
  
##  <a name="follow-up-after-changing-agent-parameters"></a><a name="FollowUp"></a> <span data-ttu-id="1d806-270">후속 작업: 에이전트 매개 변수 변경 후</span><span class="sxs-lookup"><span data-stu-id="1d806-270">Follow Up: After Changing Agent Parameters</span></span>  
 <span data-ttu-id="1d806-271">에이전트 매개 변수에 대한 변경 사항은 다음에 에이전트가 시작될 때 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-271">Agent parameter changes take effect the next time the agent is started.</span></span> <span data-ttu-id="1d806-272">에이전트가 연속적으로 실행되는 경우에는 에이전트를 중단했다가 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d806-272">If the agent runs continuously, you must stop and restart the agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d806-273">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1d806-273">See Also</span></span>  
 <span data-ttu-id="1d806-274">[복제 에이전트 프로필](replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="1d806-274">[Replication Agent Profiles](replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="1d806-275">[Replication Snapshot Agent](replication-snapshot-agent.md) </span><span class="sxs-lookup"><span data-stu-id="1d806-275">[Replication Snapshot Agent](replication-snapshot-agent.md) </span></span>  
 <span data-ttu-id="1d806-276">[Replication Log Reader Agent](replication-log-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="1d806-276">[Replication Log Reader Agent](replication-log-reader-agent.md) </span></span>  
 <span data-ttu-id="1d806-277">[Replication Distribution Agent](replication-distribution-agent.md) </span><span class="sxs-lookup"><span data-stu-id="1d806-277">[Replication Distribution Agent](replication-distribution-agent.md) </span></span>  
 <span data-ttu-id="1d806-278">[Replication Merge Agent](replication-merge-agent.md) </span><span class="sxs-lookup"><span data-stu-id="1d806-278">[Replication Merge Agent](replication-merge-agent.md) </span></span>  
 [<span data-ttu-id="1d806-279">Replication Queue Reader Agent</span><span class="sxs-lookup"><span data-stu-id="1d806-279">Replication Queue Reader Agent</span></span>](replication-queue-reader-agent.md)  
  
  
