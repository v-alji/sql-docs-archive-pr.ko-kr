---
title: 에이전트 프로필(단일 에이전트) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.perfprofileagentname.f1
helpviewer_keywords:
- Agent Profile dialog box
ms.assetid: 22713555-c496-4ce1-8ec7-4ae75cfadca8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7def9a6fef4e7e66076ee18552705c6071dab134
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648958"
---
# <a name="agent-profiles-single-agent"></a><span data-ttu-id="4aae8-102">에이전트 프로필(단일 에이전트)</span><span class="sxs-lookup"><span data-stu-id="4aae8-102">Agent Profiles (single agent)</span></span>
  <span data-ttu-id="4aae8-103">**에이전트 프로필** 대화 상자를 사용하여 에이전트 프로필을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aae8-103">Use the **Agent Profiles** dialog box to manage profiles for an agent.</span></span> <span data-ttu-id="4aae8-104">에이전트 프로필을 사용하면 각 에이전트의 런타임 매개 변수를 편리하게 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aae8-104">Agent profiles provide a convenient way to manage the runtime parameters for each agent.</span></span> <span data-ttu-id="4aae8-105">각 에이전트에는 기본 프로필이 있으며 미리 정의된 프로필이 추가된 에이전트도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aae8-105">Each agent has a default profile, and some agents have additional predefined profiles.</span></span> <span data-ttu-id="4aae8-106">예를 들어 병합 에이전트에는 느린 대역폭 연결을 위한 "느린 연결" 프로필이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aae8-106">For example, the Merge Agent has a "slow link" profile designed for low bandwidth connections.</span></span> <span data-ttu-id="4aae8-107">대부분의 애플리케이션은 미리 정의된 프로필만으로 충분하지만 사용자 정의 프로필을 만들어 에이전트 동작을 사용자 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aae8-107">Predefined profiles are sufficient for most applications, but you can also create user-defined profiles, allowing you to customize agent behavior.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4aae8-108">옵션</span><span class="sxs-lookup"><span data-stu-id="4aae8-108">Options</span></span>  
 <span data-ttu-id="4aae8-109">**새 에이전트에 대한 기본값**</span><span class="sxs-lookup"><span data-stu-id="4aae8-109">**Default for New**</span></span>  
 <span data-ttu-id="4aae8-110">지정한 유형의 에이전트에 대해 작업을 만들 때 사용할 프로필을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4aae8-110">Select the profile that will be used when jobs are created for an agent of a given type.</span></span> <span data-ttu-id="4aae8-111">예를 들어 병합 게시에 대한 구독을 여러 개 만들 경우 각 구독의 병합 에이전트 작업은 선택한 프로필을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4aae8-111">For example, if you create a number of subscriptions to a merge publication, the Merge Agent job for each subscription will use the profile selected.</span></span> <span data-ttu-id="4aae8-112">기존 작업의 프로필을 변경하려면 프로필을 선택하고 **기존 에이전트 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4aae8-112">If you want to change the profile for existing jobs, select a profile, and then click **Change Existing Agents**.</span></span>  
  
 <span data-ttu-id="4aae8-113">**이름**</span><span class="sxs-lookup"><span data-stu-id="4aae8-113">**Name**</span></span>  
 <span data-ttu-id="4aae8-114">프로필의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="4aae8-114">The name of the profile.</span></span>  
  
 <span data-ttu-id="4aae8-115">**형식**</span><span class="sxs-lookup"><span data-stu-id="4aae8-115">**Type**</span></span>  
 <span data-ttu-id="4aae8-116">프로필 유형: **사용자** (사용자 정의 프로필) 또는 **시스템** (미리 정의된 프로필)입니다.</span><span class="sxs-lookup"><span data-stu-id="4aae8-116">The type of profile: **User** (user-defined) or **System** (predefined).</span></span>  
  
 <span data-ttu-id="4aae8-117">**속성 (...)**</span><span class="sxs-lookup"><span data-stu-id="4aae8-117">**Properties (...)**</span></span>  
 <span data-ttu-id="4aae8-118">에이전트 프로필의 각 매개 변수에 사용된 값을 보려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4aae8-118">Click to view the values used for each parameter in the agent profile.</span></span>  
  
 <span data-ttu-id="4aae8-119">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="4aae8-119">**New**</span></span>  
 <span data-ttu-id="4aae8-120">새 프로필을 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4aae8-120">Click to create a new profile.</span></span>  
  
 <span data-ttu-id="4aae8-121">**Delete**</span><span class="sxs-lookup"><span data-stu-id="4aae8-121">**Delete**</span></span>  
 <span data-ttu-id="4aae8-122">사용자 정의 프로필을 선택하고 **삭제** 를 클릭하여 해당 프로필을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="4aae8-122">Select a user-defined profile, and then click **Delete** to delete that profile.</span></span> <span data-ttu-id="4aae8-123">미리 정의된 프로필은 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4aae8-123">Predefined profiles cannot be deleted.</span></span>  
  
 <span data-ttu-id="4aae8-124">**기존 에이전트 변경**</span><span class="sxs-lookup"><span data-stu-id="4aae8-124">**Change Existing Agents**</span></span>  
 <span data-ttu-id="4aae8-125">프로필을 선택하고 **기존 에이전트 변경** 을 클릭하여 지정한 유형의 에이전트에 대한 모든 기존 작업에서 선택한 프로필을 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4aae8-125">Select a profile, and then click **Change Existing Agents** to specify that all existing jobs for an agent of a given type should use the selected profile.</span></span> <span data-ttu-id="4aae8-126">예를 들어 병합 게시에 대한 구독을 여러 개 만들었는데, 프로필을 변경하여 이러한 각 구독에 대한 병합 에이전트 작업에서 **느린 연결 에이전트 프로필**을 사용하도록 지정하려면 해당 프로필을 선택하고 **기존 에이전트 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4aae8-126">For example, if you have created a number of subscriptions to a merge publication, and you want to change the profile to specify that the Merge Agent job for each of these subscriptions should use the **Slow link agent profile**, select that profile, and then click **Change Existing Agents**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aae8-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4aae8-127">See Also</span></span>  
 <span data-ttu-id="4aae8-128">[복제 에이전트 프로필 작업](agents/work-with-replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="4aae8-128">[Work with Replication Agent Profiles](agents/work-with-replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="4aae8-129">[복제 에이전트 개요](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="4aae8-129">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="4aae8-130">복제 에이전트 프로필</span><span class="sxs-lookup"><span data-stu-id="4aae8-130">Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
  
