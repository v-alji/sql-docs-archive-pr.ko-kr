---
title: 새 에이전트 프로필 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.newperfprofile.f1
helpviewer_keywords:
- New Agent Profile dialog box
ms.assetid: ebf59330-a421-45a5-9020-0484a96852bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1d7848e44585fd35a5b5a33cf431e15de96c9375
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736204"
---
# <a name="new-agent-profile"></a><span data-ttu-id="ec076-102">새 에이전트 프로필</span><span class="sxs-lookup"><span data-stu-id="ec076-102">New Agent Profile</span></span>
  <span data-ttu-id="ec076-103">**새 에이전트 프로필** 대화 상자를 사용하여 새 프로필을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec076-103">Use the **New Agent Profile** dialog box to create a new profile.</span></span> <span data-ttu-id="ec076-104">새 프로필은 항상 기존 프로필에 기반하지만 이를 애플리케이션 요구 사항에 맞게 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec076-104">New profiles are always based on existing profiles, but they can be modified to meet application requirements.</span></span> <span data-ttu-id="ec076-105">만든 프로필은 **에이전트 프로필** 대화 상자에서 기존 및 후속 에이전트 작업에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec076-105">After a profile has been created, it can be applied to existing and future agent jobs in the **Agent Profiles** dialog box.</span></span> <span data-ttu-id="ec076-106">에이전트 매개 변수 값은 \<**AgentProfileName> 속성\*\* 대화 상자에서 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec076-106">Agent parameter values can be edited in the \<**AgentProfileName> Properties\*\* dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ec076-107">옵션</span><span class="sxs-lookup"><span data-stu-id="ec076-107">Options</span></span>  
 <span data-ttu-id="ec076-108">**이름**</span><span class="sxs-lookup"><span data-stu-id="ec076-108">**Name**</span></span>  
 <span data-ttu-id="ec076-109">프로필의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ec076-109">Enter a name for the profile.</span></span>  
  
 <span data-ttu-id="ec076-110">**설명**</span><span class="sxs-lookup"><span data-stu-id="ec076-110">**Description**</span></span>  
 <span data-ttu-id="ec076-111">프로필에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ec076-111">Enter a description for the profile.</span></span>  
  
 <span data-ttu-id="ec076-112">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="ec076-112">**Parameter**</span></span>  
 <span data-ttu-id="ec076-113">프로필에 포함된 에이전트 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="ec076-113">The agent parameters included in the profile.</span></span> <span data-ttu-id="ec076-114">새 프로필의 기반으로 사용한 프로필이 반드시 각 매개 변수에 대해 값을 지정하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="ec076-114">The profile on which the new profile is based does not necessarily specify a value for each parameter.</span></span> <span data-ttu-id="ec076-115">지정한 에이전트에 유효한 모든 매개 변수를 보려면 **이 프로필에서 사용되는 매개 변수만 표시** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="ec076-115">To see all parameters that are valid for a given agent, clear the **Show only parameters used in this profile** check box.</span></span> <span data-ttu-id="ec076-116">각 매개 변수에 대한 설명은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ec076-116">For descriptions of each parameter, see:</span></span>  
  
-   [<span data-ttu-id="ec076-117">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="ec076-117">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
-   [<span data-ttu-id="ec076-118">복제 로그 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="ec076-118">Replication Log Reader Agent</span></span>](agents/replication-log-reader-agent.md)  
  
-   [<span data-ttu-id="ec076-119">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="ec076-119">Replication Distribution Agent</span></span>](agents/replication-distribution-agent.md)  
  
-   [<span data-ttu-id="ec076-120">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="ec076-120">Replication Merge Agent</span></span>](agents/replication-merge-agent.md)  
  
-   [<span data-ttu-id="ec076-121">Replication Queue Reader Agent</span><span class="sxs-lookup"><span data-stu-id="ec076-121">Replication Queue Reader Agent</span></span>](agents/replication-queue-reader-agent.md)  
  
 <span data-ttu-id="ec076-122">**기본값**</span><span class="sxs-lookup"><span data-stu-id="ec076-122">**Default Value**</span></span>  
 <span data-ttu-id="ec076-123">각 에이전트 매개 변수의 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="ec076-123">The default value for each agent parameter.</span></span>  
  
 <span data-ttu-id="ec076-124">**값**</span><span class="sxs-lookup"><span data-stu-id="ec076-124">**Value**</span></span>  
 <span data-ttu-id="ec076-125">새 프로필의 기반으로 사용한 프로필의 매개 변수에 대해 지정한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="ec076-125">The value specified for the parameter in the profile on which the new profile is based.</span></span> <span data-ttu-id="ec076-126">변경하려는 매개 변수 값으로 이 필드를 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="ec076-126">Edit this field for any parameter values you want to change.</span></span>  
  
 <span data-ttu-id="ec076-127">**이 프로필에서 사용되는 매개 변수만 표시**</span><span class="sxs-lookup"><span data-stu-id="ec076-127">**Show only parameters used in this profile**</span></span>  
 <span data-ttu-id="ec076-128">지정한 에이전트에 유효한 모든 매개 변수를 표시하려면 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="ec076-128">Clear to show all valid parameters for a given agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec076-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ec076-129">See Also</span></span>  
 <span data-ttu-id="ec076-130">[복제 에이전트 프로필 작업](agents/work-with-replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="ec076-130">[Work with Replication Agent Profiles](agents/work-with-replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="ec076-131">[복제 에이전트 개요](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="ec076-131">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="ec076-132">복제 에이전트 프로필</span><span class="sxs-lookup"><span data-stu-id="ec076-132">Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
  
