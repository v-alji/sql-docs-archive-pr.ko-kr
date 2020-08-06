---
title: 새 정책 만들기 또는 정책 열기 대화 상자, 일반 페이지 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.newgroup.f1
- sql12.swb.dmf.policy.f1
- sql12.swb.dmf.policy.filter.f1
ms.assetid: c00bebd0-d04b-4c64-840e-8b7a2c603436
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4b67cb8faf18001b841824b806e7befc0683d457
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649015"
---
# <a name="create-new-policy-or-open-policy-dialog-box-general-page"></a><span data-ttu-id="b5fec-102">새 정책 만들기 또는 정책 열기 대화 상자, 일반 페이지</span><span class="sxs-lookup"><span data-stu-id="b5fec-102">Create New Policy or Open Policy Dialog Box, General Page</span></span>
  <span data-ttu-id="b5fec-103">이 대화 상자를 사용하여 새 정책 기반 관리 정책을 만들거나 기존 정책을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-103">Use this dialog box to create a new Policy-Based Management policy or modify an existing policy.</span></span> <span data-ttu-id="b5fec-104">**적용 대상** 및 **서버 제한** 영역을 필터로 사용하여 정책을 사용 가능한 모든 대상의 하위 집합으로 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-104">Use the **Against targets** and **Server restriction** areas as a filter to limit policies to a subset of all possible targets.</span></span> <span data-ttu-id="b5fec-105">조건을 대상 필터로 사용하려면 조건이 물리적 패싯에 대해 정의되어야 하며 함수를 포함하지 않아야 하고 Like 연산자를 포함하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-105">For conditions to be used as target filters, they must be defined on a physical facet, must not contain functions, and must not contain the LIKE operator.</span></span> <span data-ttu-id="b5fec-106">시스템에서 정책에 대한 개체 집합을 계산할 때 기본적으로 시스템 개체가 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-106">When the system computes the object set for a policy, by default the system objects are excluded.</span></span>  <span data-ttu-id="b5fec-107">예를 들어, 정책의 개체 집합이 모든 테이블을 참조할 경우 시스템 테이블에 정책이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-107">For example, if the object set of the policy refers to all tables, the policy will not apply to system tables.</span></span> <span data-ttu-id="b5fec-108">사용자가 시스템 개체에 대해 정책을 평가하려면 개체 집합에 시스템 개체를 명시적으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-108">If users want to evaluate a policy against system objects, they can explicitly add system objects to the object set.</span></span> <span data-ttu-id="b5fec-109">그러나 모든 정책이 **일정 검사** 평가 모드에 대해 지원되더라도 성능상의 이유로 임의 개체 집합의 모든 정책이 **변경 내용 검사** 평가 모드에 대해 지원되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-109">However, though all policies are supported for **check on schedule** evaluation mode, for performance reason, not all policies with arbitrary object sets are supported for **check on change** evaluation mode.</span></span> <span data-ttu-id="b5fec-110">자세한 내용은 [https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx](https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5fec-110">For more information, see [https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx](https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx)</span></span>  
  
## <a name="options"></a><span data-ttu-id="b5fec-111">옵션</span><span class="sxs-lookup"><span data-stu-id="b5fec-111">Options</span></span>  
 <span data-ttu-id="b5fec-112">**이름**</span><span class="sxs-lookup"><span data-stu-id="b5fec-112">**Name**</span></span>  
 <span data-ttu-id="b5fec-113">새 정책의 경우 새 정책 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-113">For a new policy, type the new policy name.</span></span> <span data-ttu-id="b5fec-114">기존 정책의 경우 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-114">For an existing policy, the name is displayed.</span></span>  
  
 <span data-ttu-id="b5fec-115">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="b5fec-115">**Enabled**</span></span>  
 <span data-ttu-id="b5fec-116">정책을 설정하려면 **사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-116">Select the **Enabled** check box to enable the policy.</span></span> <span data-ttu-id="b5fec-117">정책을 해제하려면 **사용** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-117">Clear the **Enabled** check box to disable the policy.</span></span> <span data-ttu-id="b5fec-118">**사용** 상자는 정책 자동화에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-118">The **Enabled** box applies to policy automation.</span></span> <span data-ttu-id="b5fec-119">이 상자는 정책의 자동화 시스템을 만들거나 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-119">It creates or removes the automation system for the policy.</span></span> <span data-ttu-id="b5fec-120">Automation은 다음과 같은 메커니즘을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-120">Automation uses the following mechanisms:</span></span>  
  
 <span data-ttu-id="b5fec-121">**변경 시: 방지**</span><span class="sxs-lookup"><span data-stu-id="b5fec-121">**On change: prevent**</span></span>  
 <span data-ttu-id="b5fec-122">데이터베이스 트리거에서 정책 준수를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-122">A database trigger enforces compliance.</span></span>  
  
 <span data-ttu-id="b5fec-123">**변경 시: 로그만**</span><span class="sxs-lookup"><span data-stu-id="b5fec-123">**On change: log only**</span></span>  
 <span data-ttu-id="b5fec-124">알림 서비스 이벤트가 정책 준수를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-124">A notification services event checks for compliance.</span></span>  
  
 <span data-ttu-id="b5fec-125">**예약 시**</span><span class="sxs-lookup"><span data-stu-id="b5fec-125">**On schedule**</span></span>  
 <span data-ttu-id="b5fec-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업이 생성되어 일정에 따른 정책 준수를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-126">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job is created to check for compliance on a schedule.</span></span>  
  
 <span data-ttu-id="b5fec-127">**요청 시** 평가 모드를 사용하여 실행되는 정책은 이 확인란을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-127">Policies that are run using **On demand** evaluation mode do not use this check box.</span></span>  
  
 <span data-ttu-id="b5fec-128">**조건 확인**</span><span class="sxs-lookup"><span data-stu-id="b5fec-128">**Check condition**</span></span>  
 <span data-ttu-id="b5fec-129">이 정책이 사용하는 정책 기반 관리 조건을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-129">Select the Policy-Based Management condition that this policy uses.</span></span> <span data-ttu-id="b5fec-130">관련 정책 기반 관리 패싯에 대한 서버의 모든 조건이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-130">All conditions on the server for the associated Policy-Based Management facet are listed.</span></span> <span data-ttu-id="b5fec-131">새 조건을 만들려면 **새 조건** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-131">Click **New condition** to create a new condition.</span></span> <span data-ttu-id="b5fec-132">조건을 수정하려면 줄임표 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-132">Click the ellipsis (**...**) button to modify the condition.</span></span>  
  
 <span data-ttu-id="b5fec-133">**적용 대상**</span><span class="sxs-lookup"><span data-stu-id="b5fec-133">**Against targets**</span></span>  
 <span data-ttu-id="b5fec-134">이 패싯에서 필터 식을 완성하는 데 사용할 수 있는 대상 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-134">Select the target types that are available for this facet to complete a filter expression.</span></span>  
  
 <span data-ttu-id="b5fec-135">**평가 모드**</span><span class="sxs-lookup"><span data-stu-id="b5fec-135">**Evaluation Mode**</span></span>  
 <span data-ttu-id="b5fec-136">정책의 평가 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-136">Select the evaluation mode for the policy.</span></span> <span data-ttu-id="b5fec-137">일부 정책은 검사되지만 적용될 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-137">Some policies can be checked but not enforced.</span></span> <span data-ttu-id="b5fec-138">평가 모드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-138">The evaluation modes are as follows:</span></span>  
  
 <span data-ttu-id="b5fec-139">**요청 시**</span><span class="sxs-lookup"><span data-stu-id="b5fec-139">**On demand**</span></span>  
 <span data-ttu-id="b5fec-140">정책은 **평가** 대화 상자에서 실행할 때만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-140">Policy will only be run when you run it from the **Evaluate** dialog box.</span></span>  
  
 <span data-ttu-id="b5fec-141">**예약 시**</span><span class="sxs-lookup"><span data-stu-id="b5fec-141">**On schedule**</span></span>  
 <span data-ttu-id="b5fec-142">주기적으로 정책을 평가하고 정책을 준수하지 않는 정책에 대한 로그 항목을 기록하고 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-142">Periodically evaluates the policy, records a log entry for policies that have out-of-compliance, and creates a report.</span></span> <span data-ttu-id="b5fec-143">**일정** 상자를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-143">Enables the **Schedule** box.</span></span>  
  
 <span data-ttu-id="b5fec-144">**변경 시: 로그만**</span><span class="sxs-lookup"><span data-stu-id="b5fec-144">**On change: log only**</span></span>  
 <span data-ttu-id="b5fec-145">변경을 시도하면 이 옵션은 정책을 준수하지 않는 변경을 방지하지 않지만 정책 위반을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-145">When changes are tried, this option does not prevent out-of-compliance changes, but logs policy violations.</span></span>  
  
 <span data-ttu-id="b5fec-146">**변경 시: 방지**</span><span class="sxs-lookup"><span data-stu-id="b5fec-146">**On change: prevent**</span></span>  
 <span data-ttu-id="b5fec-147">변경을 시도하면 이 옵션은 정책을 위반하는 변경을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-147">When changes are tried, this option prevents changes that would violate the policy.</span></span>  
  
 <span data-ttu-id="b5fec-148">**일정**</span><span class="sxs-lookup"><span data-stu-id="b5fec-148">**Schedule**</span></span>  
 <span data-ttu-id="b5fec-149">**예약 시** 평가 모드를 선택하면 이 옵션이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-149">This option appears when **On schedule** evaluation mode is selected.</span></span> <span data-ttu-id="b5fec-150">일정 이름을 입력하고 **선택** 을 클릭하여 목록에서 일정을 선택하거나 **새로 만들기** 를 클릭하여 새 일정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-150">Type the name of the schedule, click **Pick** to select a schedule from a list, or click **New** to create a new schedule.</span></span> <span data-ttu-id="b5fec-151">일정 영역을 설정하려면 **예약 시** 를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-151">To enable the schedule area, **On schedule** must be selected.</span></span>  
  
 <span data-ttu-id="b5fec-152">**서버 제한**</span><span class="sxs-lookup"><span data-stu-id="b5fec-152">**Server restriction**</span></span>  
 <span data-ttu-id="b5fec-153">이 정책에 적합한 서버 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-153">Select the types of servers that are appropriate for this policy.</span></span> <span data-ttu-id="b5fec-154">**없음** 을 선택하거나, 가능한 서버를 필터링하는 조건을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fec-154">Options are **None** or select a condition that filters the possible servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5fec-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5fec-155">See Also</span></span>  
 [<span data-ttu-id="b5fec-156">정책 기반 관리를 사용하여 서버 관리</span><span class="sxs-lookup"><span data-stu-id="b5fec-156">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
