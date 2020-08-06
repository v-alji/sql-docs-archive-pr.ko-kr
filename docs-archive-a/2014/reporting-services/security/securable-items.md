---
title: 보안 개체 항목 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- securable items [Reporting Services]
- roles [Reporting Services], securable items
- security [Reporting Services], securable items listed
- role-based security [Reporting Services], securable items
ms.assetid: 27f58d4c-5c7b-4947-af5b-0f1fa60faf5f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f2f9fa5108831cb6c469710a71439bf3cfb6194a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653732"
---
# <a name="securable-items"></a><span data-ttu-id="fbee6-102">보안 개체 항목</span><span class="sxs-lookup"><span data-stu-id="fbee6-102">Securable Items</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="fbee6-103">에서는 역할 기반 보안을 사용하여 보고서 서버에 저장되어 있는 항목에 대한 액세스를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-103">uses role-based security to control access to items that are stored on a report server.</span></span> <span data-ttu-id="fbee6-104">사용자에게 보고서 서버 액세스 권한을 부여할 때는 일반적으로 다음과 같이 역할 할당 쌍을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-104">When you grant a user access to a report server, you typically do so by creating a pair of role assignments:</span></span>  
  
-   <span data-ttu-id="fbee6-105">사이트 수준에서 만들기</span><span class="sxs-lookup"><span data-stu-id="fbee6-105">At the site level</span></span>  
  
-   <span data-ttu-id="fbee6-106">보고서 서버 폴더 계층의 루트 노드인 홈에서 만들기</span><span class="sxs-lookup"><span data-stu-id="fbee6-106">On Home, which is the root node of the report server folder hierarchy</span></span>  
  
 <span data-ttu-id="fbee6-107">보안은 보고서 서버 폴더 계층에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-107">Security is inherited within the report server folder hierarchy.</span></span> <span data-ttu-id="fbee6-108">사이트 수준 또는 홈 폴더에서 역할 할당을 만들면 보고서 서버의 모든 항목 및 작업으로 확장되는 사용 권한 상속이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-108">Creating role assignments at the site level and on the Home folder sets permission inheritance that extends to all items and operations on a report server.</span></span>  
  
 <span data-ttu-id="fbee6-109">개별 항목에 대해 보안을 정의하여 사용 권한 상속을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-109">You can override permission inheritance by defining security for individual items.</span></span> <span data-ttu-id="fbee6-110">개별적으로 보안을 설정할 수 있는 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-110">Items that you can secure individually include:</span></span>  
  
-   <span data-ttu-id="fbee6-111">폴더</span><span class="sxs-lookup"><span data-stu-id="fbee6-111">Folders</span></span>  
  
-   <span data-ttu-id="fbee6-112">보고서</span><span class="sxs-lookup"><span data-stu-id="fbee6-112">Reports</span></span>  
  
-   <span data-ttu-id="fbee6-113">보고서 모델</span><span class="sxs-lookup"><span data-stu-id="fbee6-113">Report models</span></span>  
  
-   <span data-ttu-id="fbee6-114">리소스</span><span class="sxs-lookup"><span data-stu-id="fbee6-114">Resources</span></span>  
  
-   <span data-ttu-id="fbee6-115">공유 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="fbee6-115">Shared data sources</span></span>  
  
-   <span data-ttu-id="fbee6-116">공유 데이터 세트</span><span class="sxs-lookup"><span data-stu-id="fbee6-116">Shared datasets</span></span>  
  
 <span data-ttu-id="fbee6-117">일정 및 구독과 같은 기타 생성자는 보안이 명시적으로 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-117">Other constructs, such as schedules and subscriptions, are not explicitly secured.</span></span> <span data-ttu-id="fbee6-118">일정과 구독은 보고서의 보안 내에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-118">Schedules and subscriptions operate within the security of a report.</span></span>  
  
## <a name="item-descriptions"></a><span data-ttu-id="fbee6-119">항목 설명</span><span class="sxs-lookup"><span data-stu-id="fbee6-119">Item Descriptions</span></span>  
 <span data-ttu-id="fbee6-120">다음 표에서는 보안 개체 항목을 표시하고 각각의 특징에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-120">The following table lists securable items and describes their characteristics.</span></span>  
  
|<span data-ttu-id="fbee6-121">항목</span><span class="sxs-lookup"><span data-stu-id="fbee6-121">Item</span></span>|<span data-ttu-id="fbee6-122">특징</span><span class="sxs-lookup"><span data-stu-id="fbee6-122">Characteristics</span></span>|  
|----------|---------------------|  
|<span data-ttu-id="fbee6-123">폴더</span><span class="sxs-lookup"><span data-stu-id="fbee6-123">Folders</span></span>|<span data-ttu-id="fbee6-124">폴더 보안은 폴더 자체 및 폴더에 포함된 항목에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-124">Folder security applies to the folder itself and the items it contains.</span></span> <span data-ttu-id="fbee6-125">홈 폴더는 폴더 계층의 루트 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-125">The Home folder is the root node of the folder hierarchy.</span></span> <span data-ttu-id="fbee6-126">이 폴더에 대해 설정한 보안은 폴더 계층의 모든 종속 폴더, 보고서, 리소스 및 공유 데이터 원본에 대한 초기 보안 설정이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-126">Security that you set for this folder establishes the initial security settings for all subordinate folders, reports, resources, and shared data sources in the folder hierarchy.</span></span> <span data-ttu-id="fbee6-127">자세한 내용은 [폴더 보안](secure-folders.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbee6-127">For more information, see [Secure Folders](secure-folders.md).</span></span><br /><br /> <span data-ttu-id="fbee6-128">내 보고서는 전용 역할을 기반으로 암시된 역할 할당을 통해 보안되는 특수한 용도의 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-128">My Reports is a special-purpose folder that is secured through an implied role assignment based on a dedicated role.</span></span> <span data-ttu-id="fbee6-129">자세한 내용은 [내 보고서 보안 설정](secure-my-reports.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbee6-129">For more information, see [Secure My Reports](secure-my-reports.md).</span></span>|  
|<span data-ttu-id="fbee6-130">보고서</span><span class="sxs-lookup"><span data-stu-id="fbee6-130">Reports</span></span>|<span data-ttu-id="fbee6-131">보고서 및 링크된 보고서는 해당 보고서의 속성 변경 등 사용자가 수행할 수 있는 동작의 범위를 제어하여 보안을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-131">Reports and linked reports can be secured to control the range of actions that users can perform, such as changing the properties of a given report.</span></span><br /><br /> <span data-ttu-id="fbee6-132">보고서 기록은 기록을 포함하는 보고서를 통해 보안 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-132">Report history is secured through the report that contains the history.</span></span> <span data-ttu-id="fbee6-133">보고서 기록 내에서는 스냅샷을 개별적으로 보안 유지할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-133">You cannot secure individual snapshots within report history.</span></span><br /><br /> <span data-ttu-id="fbee6-134">보고서 보안에 대한 자세한 내용은 [보고서 및 리소스 보안](secure-reports-and-resources.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbee6-134">For more information about report security, see [Secure Reports and Resources](secure-reports-and-resources.md).</span></span>|  
|<span data-ttu-id="fbee6-135">보고서 모델</span><span class="sxs-lookup"><span data-stu-id="fbee6-135">Report models</span></span>|<span data-ttu-id="fbee6-136">보고서 모델의 전체 또는 일부에 대해 역할 할당을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-136">You can specify role assignment on all or part of a report model.</span></span> <span data-ttu-id="fbee6-137">보고서 모델은 광범위할 수 있으므로 기밀 데이터로 매핑되는 모델 항목의 보안을 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-137">Because report models can be quite extensive, you might want to secure the model items that map to confidential data.</span></span>|  
|<span data-ttu-id="fbee6-138">리소스</span><span class="sxs-lookup"><span data-stu-id="fbee6-138">Resources</span></span>|<span data-ttu-id="fbee6-139">리소스는 리소스 자체 및 해당 속성에 대한 액세스를 제어하도록 보안을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-139">Resources can be secured to control access to the resource itself and its properties.</span></span><br /><br /> <span data-ttu-id="fbee6-140">독립 실행형 리소스만 개별 항목으로 보안을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-140">Only stand-alone resources can be secured as separate items.</span></span> <span data-ttu-id="fbee6-141">보고서에 포함된 리소스는 해당 보고서와 별도로 보안을 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-141">Resources that are embedded within a report cannot be secured separately from that report.</span></span><br /><br /> <span data-ttu-id="fbee6-142">리소스 보안에 대한 자세한 내용은 [보고서 및 리소스 보안](secure-reports-and-resources.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbee6-142">For more information about resource security, see [Secure Reports and Resources](secure-reports-and-resources.md).</span></span>|  
|<span data-ttu-id="fbee6-143">공유 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="fbee6-143">Shared data sources</span></span>|<span data-ttu-id="fbee6-144">공유 데이터 원본의 보안을 설정하여 항목과 해당 속성 페이지에 대한 액세스를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-144">Shared data sources can be secured to limit access to the item and its property pages.</span></span> <span data-ttu-id="fbee6-145">자세한 내용은 [공유 데이터 원본 항목 보안 설정](secure-shared-data-source-items.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbee6-145">For more information, see [Secure Shared Data Source Items](secure-shared-data-source-items.md).</span></span>|  
|<span data-ttu-id="fbee6-146">공유 데이터 세트</span><span class="sxs-lookup"><span data-stu-id="fbee6-146">Shared datasets</span></span>|<span data-ttu-id="fbee6-147">공유 데이터 세트는 해당 공유 데이터 세트의 정의 보기 또는 변경, 속성 변경 등 사용자가 수행할 수 있는 동작의 범위를 제어하여 보안을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbee6-147">Shared datasets can be secured to control the range of actions that users can perform, such as viewing or changing the definition, or changing the properties of a given shared dataset.</span></span><br /><br /> <span data-ttu-id="fbee6-148">자세한 내용은 [공유 데이터 세트 항목 보안 설정](secure-shared-dataset-items.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbee6-148">For more information, see [Secure Shared Dataset Items](secure-shared-dataset-items.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbee6-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fbee6-149">See Also</span></span>  
 <span data-ttu-id="fbee6-150">[기본 모드 보고서 서버에 대한 사용 권한 부여](granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="fbee6-150">[Granting Permissions on a Native Mode Report Server](granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="fbee6-151">[역할 만들기, 삭제 또는 수정&#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md) </span><span class="sxs-lookup"><span data-stu-id="fbee6-151">[Create, Delete, or Modify a Role &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md) </span></span>  
 <span data-ttu-id="fbee6-152">[사용자에게 보고서 서버에 대한 액세스 권한 부여&#40;보고서 관리자&#41;](grant-user-access-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="fbee6-152">[Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) </span></span>  
 [<span data-ttu-id="fbee6-153">역할 할당 수정 또는 삭제&#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="fbee6-153">Modify or Delete a Role Assignment &#40;Report Manager&#41;</span></span>](role-assignments-modify-or-delete.md)  
  
  
