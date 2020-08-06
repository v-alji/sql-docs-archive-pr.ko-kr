---
title: 에이전트 프로필 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.perfprofiles.f1
helpviewer_keywords:
- Agent Profiles dialog box
ms.assetid: 0422e99c-e688-419b-bb4c-c7bebeef1d8d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7584670088da1ac7a9c81f1f8f0cbdce8b040c7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648957"
---
# <a name="agent-profiles"></a><span data-ttu-id="01f48-102">에이전트 프로필</span><span class="sxs-lookup"><span data-stu-id="01f48-102">Agent Profiles</span></span>
  <span data-ttu-id="01f48-103">**에이전트 프로필** 대화 상자를 사용하여 에이전트 프로필을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01f48-103">Use the **Agent Profiles** dialog box to manage agent profiles.</span></span> <span data-ttu-id="01f48-104">에이전트 프로필을 사용하면 각 에이전트의 런타임 매개 변수를 편리하게 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01f48-104">Agent profiles provide a convenient way to manage the runtime parameters for each agent.</span></span> <span data-ttu-id="01f48-105">각 에이전트에는 기본 프로필이 있으며 미리 정의된 프로필이 추가된 에이전트도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01f48-105">Each agent has a default profile, and some agents have additional predefined profiles.</span></span> <span data-ttu-id="01f48-106">예를 들어 병합 에이전트에는 느린 대역폭 연결을 위한 "느린 연결" 프로필이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01f48-106">For example, the Merge Agent has a "slow link" profile designed for low bandwidth connections.</span></span> <span data-ttu-id="01f48-107">대부분의 애플리케이션은 미리 정의된 프로필만으로 충분하지만 사용자 정의 프로필을 만들어 에이전트 동작을 사용자 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01f48-107">Predefined profiles are sufficient for most applications, but you can also create user-defined profiles, allowing you to customize agent behavior.</span></span>  
  
## <a name="options"></a><span data-ttu-id="01f48-108">옵션</span><span class="sxs-lookup"><span data-stu-id="01f48-108">Options</span></span>  
 <span data-ttu-id="01f48-109">**페이지 선택**</span><span class="sxs-lookup"><span data-stu-id="01f48-109">**Select a page**</span></span>  
 <span data-ttu-id="01f48-110">왼쪽 창에서 에이전트를 선택하면 오른쪽 창에 해당 에이전트의 프로필이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="01f48-110">Select an agent in the left pane, and the profiles for the agent are displayed in the right pane.</span></span>  
  
 <span data-ttu-id="01f48-111">**새 에이전트에 대한 기본값**</span><span class="sxs-lookup"><span data-stu-id="01f48-111">**Default for New**</span></span>  
 <span data-ttu-id="01f48-112">지정한 유형의 에이전트에 대해 작업을 만들 때 사용할 프로필을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="01f48-112">Select the profile that will be used when jobs are created for an agent of a given type.</span></span> <span data-ttu-id="01f48-113">예를 들어 병합 게시에 대한 구독을 여러 개 만들 경우 각 구독의 병합 에이전트 작업은 선택한 프로필을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="01f48-113">For example, if you create a number of subscriptions to a merge publication, the Merge Agent job for each subscription will use the profile selected.</span></span> <span data-ttu-id="01f48-114">기존 작업의 프로필을 변경하려면 프로필을 선택하고 **기존 에이전트 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="01f48-114">If you want to change the profile for existing jobs, select a profile, and then click **Change Existing Agents**.</span></span>  
  
 <span data-ttu-id="01f48-115">**이름**</span><span class="sxs-lookup"><span data-stu-id="01f48-115">**Name**</span></span>  
 <span data-ttu-id="01f48-116">프로필의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="01f48-116">The name of the profile.</span></span>  
  
 <span data-ttu-id="01f48-117">**형식**</span><span class="sxs-lookup"><span data-stu-id="01f48-117">**Type**</span></span>  
 <span data-ttu-id="01f48-118">프로필 유형: **사용자** (사용자 정의 프로필) 또는 **시스템** (미리 정의된 프로필)입니다.</span><span class="sxs-lookup"><span data-stu-id="01f48-118">The type of profile: **User** (user-defined) or **System** (predefined).</span></span>  
  
 <span data-ttu-id="01f48-119">**속성 (...)**</span><span class="sxs-lookup"><span data-stu-id="01f48-119">**Properties (...)**</span></span>  
 <span data-ttu-id="01f48-120">에이전트 프로필의 각 매개 변수에 사용된 값을 보려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="01f48-120">Click to view the values used for each parameter in the agent profile.</span></span>  
  
 <span data-ttu-id="01f48-121">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="01f48-121">**New**</span></span>  
 <span data-ttu-id="01f48-122">새 프로필을 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="01f48-122">Click to create a new profile.</span></span>  
  
 <span data-ttu-id="01f48-123">**Delete**</span><span class="sxs-lookup"><span data-stu-id="01f48-123">**Delete**</span></span>  
 <span data-ttu-id="01f48-124">사용자 정의 프로필을 선택하고 **삭제** 를 클릭하여 해당 프로필을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="01f48-124">Select a user-defined profile, and then click **Delete** to delete that profile.</span></span> <span data-ttu-id="01f48-125">미리 정의된 프로필은 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="01f48-125">Predefined profiles cannot be deleted.</span></span>  
  
 <span data-ttu-id="01f48-126">**기존 에이전트 변경**</span><span class="sxs-lookup"><span data-stu-id="01f48-126">**Change Existing Agents**</span></span>  
 <span data-ttu-id="01f48-127">프로필을 선택하고 **기존 에이전트 변경** 을 클릭하여 지정한 유형의 에이전트에 대한 모든 기존 작업에서 선택한 프로필을 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="01f48-127">Select a profile, and then click **Change Existing Agents** to specify that all existing jobs for an agent of a given type should use the selected profile.</span></span> <span data-ttu-id="01f48-128">예를 들어 병합 게시에 대한 구독을 여러 개 만들었는데, 프로필을 변경하여 이러한 각 구독에 대한 병합 에이전트 작업에서 **느린 연결 에이전트 프로필**을 사용하도록 지정하려면 해당 프로필을 선택하고 **기존 에이전트 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="01f48-128">For example, if you have created a number of subscriptions to a merge publication, and you want to change the profile to specify that the Merge Agent job for each of these subscriptions should use the **Slow link agent profile**, select that profile, and then click **Change Existing Agents**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f48-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="01f48-129">See Also</span></span>  
 <span data-ttu-id="01f48-130">[복제 에이전트 프로필 작업](agents/work-with-replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="01f48-130">[Work with Replication Agent Profiles](agents/work-with-replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="01f48-131">[복제 에이전트 개요](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="01f48-131">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="01f48-132">복제 에이전트 프로필</span><span class="sxs-lookup"><span data-stu-id="01f48-132">Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
  
