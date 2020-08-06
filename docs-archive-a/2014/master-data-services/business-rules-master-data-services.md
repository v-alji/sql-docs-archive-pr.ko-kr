---
title: 비즈니스 규칙(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], about business rules
- business rules [Master Data Services]
ms.assetid: a9f9e41a-2461-4845-b947-58b3a205543f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 00ac4b7d8970978ef111d56e5a809ada36362583
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661232"
---
# <a name="business-rules-master-data-services"></a><span data-ttu-id="1748d-102">비즈니스 규칙(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1748d-102">Business Rules (Master Data Services)</span></span>
  <span data-ttu-id="1748d-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 비즈니스 규칙은 마스터 데이터의 품질과 정확성을 유지하는 데 사용되는 규칙입니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a business rule is a rule that you use to ensure the quality and accuracy of your master data.</span></span> <span data-ttu-id="1748d-104">비즈니스 규칙을 사용하여 자동으로 데이터를 업데이트하거나, 전자 메일을 보내거나, 비즈니스 프로세스 또는 워크플로를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-104">You can use a business rule to automatically update data, to send email, or to start a business process or workflow.</span></span>  
  
## <a name="create-and-publish-business-rules"></a><span data-ttu-id="1748d-105">비즈니스 규칙 만들기 및 게시</span><span class="sxs-lookup"><span data-stu-id="1748d-105">Create and Publish Business Rules</span></span>  
 <span data-ttu-id="1748d-106">비즈니스 규칙은 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 만드는 `If/Then` 문입니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-106">Business rules are `If/Then` statements that you create in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span> <span data-ttu-id="1748d-107">특성 값이 지정한 조건을 충족하는 경우 동작이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-107">If an attribute value meets a specified condition, then an action is taken.</span></span> <span data-ttu-id="1748d-108">가능한 동작에는 기본값 설정이나 값 변경이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-108">Possible actions include setting a default value or changing a value.</span></span> <span data-ttu-id="1748d-109">이러한 동작을 전자 메일 알림과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-109">These actions can be combined with sending an email notification.</span></span>  
  
 <span data-ttu-id="1748d-110">비즈니스 규칙은 특성 값이 변경될 때(예: Color 특성 값 변경 시 동작 수행)나 특정 특성 값(예: Color=Blue일 경우 동작 수행)을 기반으로 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-110">Business rules can be based on specific attribute values (for example, take action if Color=Blue), or when attribute values change (for example, take action if the value of the Color attribute changes).</span></span> <span data-ttu-id="1748d-111">비특정 변경 사항 추적에 대한 자세한 내용은 [변경 내용 추적&#40;Master Data Services&#41;](change-tracking-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1748d-111">For more information about tracking non-specific changes, see [Change Tracking &#40;Master Data Services&#41;](change-tracking-master-data-services.md).</span></span>  
  
 <span data-ttu-id="1748d-112">비즈니스 규칙을 사용하려면 먼저 규칙을 만들어 게시한 다음 게시된 규칙을 데이터에 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-112">To use business rules you must first create and publish your rules, then apply the published rules to data.</span></span> <span data-ttu-id="1748d-113">버전의 유효성을 검사하여 데이터의 하위 집합 또는 버전의 모든 데이터에 규칙을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-113">You can apply rules to subsets of data or to all data for a version by validating the version.</span></span> <span data-ttu-id="1748d-114">모든 특성이 비즈니스 규칙 유효성 검사를 통과해야 버전이 커밋될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-114">A version cannot be committed until all attributes pass business rule validation.</span></span>  
  
 <span data-ttu-id="1748d-115">사용자가 비즈니스 규칙 유효성 검사에 통과하지 않은 특성 값을 추가하는 경우에도 해당 값이 저장될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-115">If a user attempts to add an attribute value that doesn't pass business rule validation, the value can still be saved.</span></span> <span data-ttu-id="1748d-116">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에 표시된 유효성 검사 문제를 검토 및 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-116">You can review and correct validation issues, which are displayed in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
 <span data-ttu-id="1748d-117">모델 배포 패키지를 만들 때 비즈니스 규칙을 포함하려면 버전의 데이터를 패키지에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-117">When you create a model deployment package, if you want to include business rules you must include data from the version in the package.</span></span>  
  
 <span data-ttu-id="1748d-118">**OR** 연산자를 사용하는 비즈니스 규칙을 만드는 경우 개별적으로 평가할 수 있는 각 조건 문에 대해 개별 규칙을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-118">If you create a business rule that uses the **OR** operator, you should create a separate rule for each conditional statement that can be evaluated independently.</span></span> <span data-ttu-id="1748d-119">그런 다음 필요에 따라 규칙을 제외시키면 유연성이 향상되고 더 쉽게 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-119">You can then exclude rules as needed, providing more flexibility and easier troubleshooting.</span></span>  
  
## <a name="how-business-rules-are-applied"></a><span data-ttu-id="1748d-120">비즈니스 규칙을 적용하는 방법</span><span class="sxs-lookup"><span data-stu-id="1748d-120">How Business Rules Are Applied</span></span>  
 <span data-ttu-id="1748d-121">규칙을 실행할 우선 순위를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-121">You can set priority order for rules to run in.</span></span> <span data-ttu-id="1748d-122">그러나 우선 순위를 고려하기 전에 비즈니스 규칙은 규칙에서 수행하는 동작 유형에 따라 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-122">However, before priority is taken into account, business rules are applied based on the type of action the rule takes.</span></span> <span data-ttu-id="1748d-123">순서는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-123">The order is as follows:</span></span>  
  
1.  <span data-ttu-id="1748d-124">**기본값**</span><span class="sxs-lookup"><span data-stu-id="1748d-124">**Default Value**</span></span>  
  
2.  <span data-ttu-id="1748d-125">**값 변경**</span><span class="sxs-lookup"><span data-stu-id="1748d-125">**Change Value**</span></span>  
  
3.  <span data-ttu-id="1748d-126">**유효성 검사**</span><span class="sxs-lookup"><span data-stu-id="1748d-126">**Validation**</span></span>  
  
4.  <span data-ttu-id="1748d-127">**외부 동작**</span><span class="sxs-lookup"><span data-stu-id="1748d-127">**External Action**</span></span>  
  
 <span data-ttu-id="1748d-128">이 그룹 내에서 동작은 우선 순위가 낮은 것부터 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-128">Within these groups, actions are applied in priority order, from lowest to highest.</span></span> <span data-ttu-id="1748d-129">따라서 예를 들면 네 개의 개별 규칙에 **기본값** 동작이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-129">So for example, four separate rules might have **Default Value** actions.</span></span> <span data-ttu-id="1748d-130">먼저 발생하는 **기본값** 동작은 웹 UI에 지정된 우선 순위에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-130">The **Default Value** action that occurs first depends on the priority order specified in the web UI.</span></span>  
  
 <span data-ttu-id="1748d-131">규칙을 적용하는 방법에 대한 기타 중요한 참고 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-131">Other important notes about applying rules:</span></span>  
  
-   <span data-ttu-id="1748d-132">비즈니스 규칙이 제외되거나 **활성**상태로 게시되지 않는 경우에도 해당 규칙은 여전히 사용할 수 있지만 비즈니스 규칙 적용 시에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-132">If a business rule is excluded or is not published with a status of **Active**, the rule is still available but is not included when business rules are applied.</span></span>  
  
-   <span data-ttu-id="1748d-133">비즈니스 규칙은 모든 리프 멤버나 통합 멤버 중 하나의 특성 값에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-133">Business rules apply to the attribute values for all leaf or all consolidated members, not both.</span></span>  
  
-   <span data-ttu-id="1748d-134">비즈니스 규칙은 **열림** 또는 **잠금**상태인 모델 버전에 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-134">Business rules can be applied to any version of a model that is **Open** or **Locked**.</span></span>  
  
-   <span data-ttu-id="1748d-135">비즈니스 규칙을 적용할 때 데이터에 대해 변경된 내용은 트랜잭션으로 기록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-135">Changes made to data when business rules are applied are not logged as transactions.</span></span>  
  
-   <span data-ttu-id="1748d-136">비즈니스 규칙은 **워크플로 시작** 동작을 두 개 이상 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-136">A business rule cannot contain more than one **start workflow** action.</span></span>  
  
## <a name="system-settings"></a><span data-ttu-id="1748d-137">시스템 설정</span><span class="sxs-lookup"><span data-stu-id="1748d-137">System Settings</span></span>  
 <span data-ttu-id="1748d-138">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 에는 비즈니스 규칙에 영향을 주는 두 가지 설정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-138">There are two settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] that affect business rules.</span></span> <span data-ttu-id="1748d-139">이러한 설정은 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 에서 조정하거나 시스템 설정 테이블에서 직접 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-139">You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or directly in the System Settings table.</span></span> <span data-ttu-id="1748d-140">자세한 내용은 [시스템 설정&#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1748d-140">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="1748d-141">관련 작업</span><span class="sxs-lookup"><span data-stu-id="1748d-141">Related Tasks</span></span>  
  
|<span data-ttu-id="1748d-142">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="1748d-142">Task Description</span></span>|<span data-ttu-id="1748d-143">항목</span><span class="sxs-lookup"><span data-stu-id="1748d-143">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="1748d-144">새 비즈니스 규칙을 만들어 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-144">Create and publish a new business rule.</span></span>|[<span data-ttu-id="1748d-145">비즈니스 규칙 만들기 및 게시&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1748d-145">Create and Publish a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)|  
|<span data-ttu-id="1748d-146">비즈니스 규칙에 여러 조건을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-146">Add multiple conditions to a business rule.</span></span>|[<span data-ttu-id="1748d-147">비즈니스 규칙에 여러 조건 추가&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1748d-147">Add Multiple Conditions to a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)|  
|<span data-ttu-id="1748d-148">특성에 값이 필요한 비즈니스 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-148">Create a business rule to require that attributes have values.</span></span>|[<span data-ttu-id="1748d-149">특성 값 요구&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1748d-149">Require Attribute Values &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/require-attribute-values-master-data-services.md)|  
|<span data-ttu-id="1748d-150">특성 값 변경 사항을 기반으로 동작을 수행하는 비즈니스 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-150">Create a business rule to take an action based on changes to attribute values.</span></span>|[<span data-ttu-id="1748d-151">특성 값 변경 기반 동작 시작&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1748d-151">Initiate Actions Based on Attribute Value Changes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
|<span data-ttu-id="1748d-152">기존 비즈니스 규칙의 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-152">Change the name of an existing business rule.</span></span>|[<span data-ttu-id="1748d-153">비즈니스 규칙 이름 변경&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1748d-153">Change a Business Rule Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)|  
|<span data-ttu-id="1748d-154">비즈니스 규칙이 적용될 때 알림을 보내도록 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-154">Configure [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to send notifications when business rules are applied.</span></span>|[<span data-ttu-id="1748d-155">알림을 보내도록 비즈니스 규칙 구성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1748d-155">Configure Business Rules to Send Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)|  
|<span data-ttu-id="1748d-156">특정 멤버에 비즈니스 규칙을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-156">Apply business rules to specific members.</span></span>|[<span data-ttu-id="1748d-157">비즈니스 규칙에 대해 특정 멤버 유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1748d-157">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|<span data-ttu-id="1748d-158">비즈니스 규칙을 사용하지 않도록 제외합니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-158">Exclude a business rule so it is not used.</span></span>|[<span data-ttu-id="1748d-159">비즈니스 규칙 제외&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1748d-159">Exclude a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/exclude-a-business-rule-master-data-services.md)|  
|<span data-ttu-id="1748d-160">기존 비즈니스 규칙을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="1748d-160">Delete an existing business rule.</span></span>|[<span data-ttu-id="1748d-161">비즈니스 규칙 삭제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1748d-161">Delete a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-business-rule-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="1748d-162">관련 내용</span><span class="sxs-lookup"><span data-stu-id="1748d-162">Related Content</span></span>  
  
-   [<span data-ttu-id="1748d-163">MDS(Master Data Services) 개요</span><span class="sxs-lookup"><span data-stu-id="1748d-163">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)  
  
-   [<span data-ttu-id="1748d-164">버전&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1748d-164">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
-   [<span data-ttu-id="1748d-165">유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1748d-165">Validation &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-master-data-services.md)  
  
-   [<span data-ttu-id="1748d-166">변경 내용 추적&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1748d-166">Change Tracking &#40;Master Data Services&#41;</span></span>](change-tracking-master-data-services.md)  
  
  
