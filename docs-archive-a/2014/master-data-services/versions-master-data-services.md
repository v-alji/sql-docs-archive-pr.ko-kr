---
title: 버전(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- version flags [Master Data Services], about version flags
- versions [Master Data Services]
- version flags [Master Data Services]
- versions [Master Data Services], version flags
ms.assetid: 752ec96d-53d7-4160-8ed2-92e0324645f3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6f8b55a32cdf2a5aabad38ee3d0d4154c2ad6a6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646547"
---
# <a name="versions-master-data-services"></a><span data-ttu-id="0ec4a-102">버전(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0ec4a-102">Versions (Master Data Services)</span></span>
  <span data-ttu-id="0ec4a-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 모델 내에 여러 버전의 마스터 데이터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can create multiple versions of the master data within a model.</span></span> <span data-ttu-id="0ec4a-104">버전은 데이터 유효성을 검사하는 동안 잠그고 데이터 유효성 검사 이후에 커밋할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-104">Versions can be locked while you validate your data and committed after the data is validated.</span></span> <span data-ttu-id="0ec4a-105">커밋된 버전은 감사 가능한 변경 사항 레코드를 형성합니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-105">Committed versions form an auditable record of changes.</span></span> <span data-ttu-id="0ec4a-106">이러한 각 버전에는 모델의 모든 멤버, 특성 값, 계층 멤버, 계층 관계 및 컬렉션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-106">Each version you create contains all members, attribute values, hierarchy members, hierarchy relationships, and collections for the model.</span></span>  
  
## <a name="when-to-use-versions"></a><span data-ttu-id="0ec4a-107">버전을 사용하는 경우</span><span class="sxs-lookup"><span data-stu-id="0ec4a-107">When to Use Versions</span></span>  
 <span data-ttu-id="0ec4a-108">버전을 사용하여 수행할 수 있는 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-108">Use versions to:</span></span>  
  
-   <span data-ttu-id="0ec4a-109">시간이 지남에 따라 변경되는 마스터 데이터의 감사 가능한 레코드를 유지 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-109">Maintain an auditable record of your master data as it changes over time.</span></span>  
  
-   <span data-ttu-id="0ec4a-110">사용자가 변경하지 못하게 하여 모든 데이터가 비즈니스 규칙에 적합하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-110">Prevent users from making changes while you ensure all data validates successfully against business rules.</span></span>  
  
-   <span data-ttu-id="0ec4a-111">구독 시스템에서 사용할 모델을 잠글 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-111">Lock down a model for use by subscribing systems.</span></span>  
  
-   <span data-ttu-id="0ec4a-112">계층을 바로 구현하지 않고 여러 계층을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-112">Test different hierarchies without implementing them right away.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0ec4a-113">예를 들어 새 엔터티나 도메인 기반 특성을 만드는 경우와 같이 모델의 구조를 변경하면 변경 사항이 모든 버전에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-113">When you change the structure of your model, such as when you create a new entity or domain-based attribute, the change applies to all versions.</span></span> <span data-ttu-id="0ec4a-114">이전 버전의 모델을 보면 엔터티 또는 특성이 표시되지만 실제로 존재하는 데이터는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-114">If you view an earlier version of the model, the entity or attribute is displayed, but no data exists.</span></span>  
  
## <a name="version-flags"></a><span data-ttu-id="0ec4a-115">버전 플래그</span><span class="sxs-lookup"><span data-stu-id="0ec4a-115">Version Flags</span></span>  
 <span data-ttu-id="0ec4a-116">버전이 사용자 또는 구독 시스템에서 사용할 수 있도록 준비되면 버전을 식별할 플래그를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-116">When a version is ready for users or for a subscribing system, you can set a flag to identify the version.</span></span> <span data-ttu-id="0ec4a-117">이 플래그는 필요에 따라 버전 간에 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-117">You can move this flag from version to version as needed.</span></span> <span data-ttu-id="0ec4a-118">플래그는 사용자 및 구독 시스템이 사용할 모델 버전을 식별하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-118">Flags help users and subscribing systems identify which version of a model to use.</span></span>  
  
## <a name="workflow-for-version-management"></a><span data-ttu-id="0ec4a-119">버전 관리 워크플로</span><span class="sxs-lookup"><span data-stu-id="0ec4a-119">Workflow for Version Management</span></span>  
 <span data-ttu-id="0ec4a-120">버전 관리에 사용하는 워크플로는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-120">Use the following workflow for version management:</span></span>  
  
1.  <span data-ttu-id="0ec4a-121">초기 버전은 모델을 만들고 회사의 마스터 데이터로 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스를 채우면 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-121">An initial version is created automatically when you create a model and populate the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database with your company's master data.</span></span> <span data-ttu-id="0ec4a-122">사용 권한에 따라 사용자는 필요한 경우 이 버전을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-122">Based on permissions, users can make changes to this version as needed.</span></span>  
  
2.  <span data-ttu-id="0ec4a-123">모델의 버전을 커밋하려면 모델 관리자만 데이터를 업데이트할 수 있도록 버전을 잠급니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-123">When you want to commit a version of a model, lock the version so that only model administrators can update the data.</span></span> <span data-ttu-id="0ec4a-124">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-124">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span> <span data-ttu-id="0ec4a-125">알림이 구성된 경우 버전의 상태가 변경될 때마다 전자 메일 알림이 모델 관리자에게 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-125">If notifications are configured, an email notification is sent to model administrators each time the version's status changes.</span></span> <span data-ttu-id="0ec4a-126">자세한 내용은 [메일 알림 구성&#40;Master Data Services&#41;](../../2014/master-data-services/configure-email-notifications-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-126">For more information, see [Configure Email Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/configure-email-notifications-master-data-services.md).</span></span>  
  
3.  <span data-ttu-id="0ec4a-127">잠긴 버전의 데이터에 비즈니스 규칙을 적용하고 유효성 검사 문제를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-127">Apply business rules to the locked version's data and review any validation issues.</span></span> <span data-ttu-id="0ec4a-128">필요한 경우 누락된 정보를 채우거나 문제의 원인이 되는 트랜잭션을 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-128">If necessary, you can fill in missing information or revert the transaction that caused the issue.</span></span> <span data-ttu-id="0ec4a-129">또한 사용자가 변경할 수 있도록 버전의 잠금을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-129">You can also unlock the version for users to make changes.</span></span>  
  
4.  <span data-ttu-id="0ec4a-130">모든 데이터가 유효성 검사를 통과하면 버전을 커밋하고 구독 시스템에서 사용하도록 버전에 플래그를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-130">When all the data passes validation, commit the version and flag it for use by subscribing systems.</span></span> <span data-ttu-id="0ec4a-131">커밋된 버전에는 변경 내용을 적용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-131">Changes cannot be made to a committed version.</span></span>  
  
5.  <span data-ttu-id="0ec4a-132">커밋된 버전을 복사하고 모델의 새 버전으로 작업을 시작할 수 있음을 사용자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-132">Copy the committed version and notify users that they can begin working in a new version of the model.</span></span>  
  
## <a name="sequential-or-simultaneous-versions"></a><span data-ttu-id="0ec4a-133">순차 또는 동시 버전</span><span class="sxs-lookup"><span data-stu-id="0ec4a-133">Sequential or Simultaneous Versions</span></span>  
 <span data-ttu-id="0ec4a-134">모델의 순차 버전 또는 동시 버전을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-134">You can create sequential or simultaneous versions of your model.</span></span>  
  
-   <span data-ttu-id="0ec4a-135">**순차 버전.**</span><span class="sxs-lookup"><span data-stu-id="0ec4a-135">**Sequential versions.**</span></span> <span data-ttu-id="0ec4a-136">버전을 커밋할 때마다 새 복사본을 만들고 해당 버전에 다음 일련 번호를 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-136">Each time you commit a version, create a new copy and give the version the next sequential number.</span></span> <span data-ttu-id="0ec4a-137">예를 들어 모델의 **버전 7** 을 복사하여 복사본의 이름을 **버전 8**로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-137">For example, you can copy **Version 7** of your model and name the copy **Version 8**.</span></span>  
  
-   <span data-ttu-id="0ec4a-138">**동시 버전.**</span><span class="sxs-lookup"><span data-stu-id="0ec4a-138">**Simultaneous versions.**</span></span> <span data-ttu-id="0ec4a-139">둘 이상의 데이터 버전에서 동시에 작업하려는 경우 모델의 동시 버전을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-139">Create simultaneous versions of your model when you want to work on two or more versions of your data at once.</span></span> <span data-ttu-id="0ec4a-140">이는 정상적인 비즈니스 과정에 따른 조직 개편이나 합병 시 새 마스터 데이터를 기존 구조에 적합하게 만드는 방법을 확인하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-140">This is useful when your company has reorganizations or mergers that coincide with the normal course of business and you want to determine how the new master data might fit into your existing structures.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0ec4a-141">모든 버전을 복사할 수 있는지 아니면 커밋된 버전만 복사할 수 있는지는 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 의 설정에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-141">A setting in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] determines whether or not you can copy all versions or only those that are committed.</span></span> <span data-ttu-id="0ec4a-142">동시 버전을 만들려면 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 에서 모든 버전 복사를 허용하도록 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-142">To create simultaneous versions you must configure [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] to allow you to copy all versions.</span></span> <span data-ttu-id="0ec4a-143">이 설정은 시스템 설정 테이블에서도 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-143">This setting is also available in the System Settings table.</span></span> <span data-ttu-id="0ec4a-144">자세한 내용은 [시스템 설정&#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-144">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0ec4a-145">관련 작업</span><span class="sxs-lookup"><span data-stu-id="0ec4a-145">Related Tasks</span></span>  
  
|<span data-ttu-id="0ec4a-146">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="0ec4a-146">Task Description</span></span>|<span data-ttu-id="0ec4a-147">항목</span><span class="sxs-lookup"><span data-stu-id="0ec4a-147">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="0ec4a-148">기존 버전의 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-148">Change the name of an existing version.</span></span>|[<span data-ttu-id="0ec4a-149">버전 이름 변경&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0ec4a-149">Change a Version Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-version-name-master-data-services.md)|  
|<span data-ttu-id="0ec4a-150">관리자만 데이터를 편집할 수 있도록 버전을 잠급니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-150">Lock a version so only administrators can edit its data.</span></span>|[<span data-ttu-id="0ec4a-151">버전 잠금&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0ec4a-151">Lock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/lock-a-version-master-data-services.md)|  
|<span data-ttu-id="0ec4a-152">사용자가 데이터를 편집할 수 있도록 버전을 잠금 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-152">Unlock a version so users can edit its data.</span></span>|[<span data-ttu-id="0ec4a-153">버전 잠금 해제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0ec4a-153">Unlock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/unlock-a-version-master-data-services.md)|  
|<span data-ttu-id="0ec4a-154">모든 데이터의 유효성 검사를 마친 후 버전을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-154">Commit a version after all data is validated.</span></span>|[<span data-ttu-id="0ec4a-155">버전 커밋&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0ec4a-155">Commit a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/commit-a-version-master-data-services.md)|  
|<span data-ttu-id="0ec4a-156">버전을 표시하는 새 플래그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-156">Create a new flag to mark a version.</span></span>|[<span data-ttu-id="0ec4a-157">버전 플래그 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0ec4a-157">Create a Version Flag &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-version-flag-master-data-services.md)|  
|<span data-ttu-id="0ec4a-158">기존 버전 플래그의 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-158">Change the name of an existing version flag.</span></span>|[<span data-ttu-id="0ec4a-159">버전 플래그 이름 변경&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0ec4a-159">Change a Version Flag Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-version-flag-name-master-data-services.md)|  
|<span data-ttu-id="0ec4a-160">기존 플래그를 버전에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-160">Assign an existing flag to a version.</span></span>|[<span data-ttu-id="0ec4a-161">버전에 플래그 할당&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0ec4a-161">Assign a Flag to a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)|  
|<span data-ttu-id="0ec4a-162">기존 버전의 새 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-162">Create a new copy of an existing version</span></span>|[<span data-ttu-id="0ec4a-163">버전 복사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0ec4a-163">Copy a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/copy-a-version-master-data-services.md)|  
|<span data-ttu-id="0ec4a-164">기존 버전을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="0ec4a-164">Delete an existing version.</span></span>|[<span data-ttu-id="0ec4a-165">버전 삭제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0ec4a-165">Delete a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-version-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="0ec4a-166">관련 내용</span><span class="sxs-lookup"><span data-stu-id="0ec4a-166">Related Content</span></span>  
  
-   [<span data-ttu-id="0ec4a-167">트랜잭션 되돌리기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0ec4a-167">Reverse a Transaction &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/reverse-a-transaction-master-data-services.md)  
  
-   [<span data-ttu-id="0ec4a-168">알림&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0ec4a-168">Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/notifications-master-data-services.md)  
  
-   [<span data-ttu-id="0ec4a-169">비즈니스 규칙&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0ec4a-169">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
