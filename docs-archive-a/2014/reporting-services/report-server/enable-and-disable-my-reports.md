---
title: 내 보고서 사용 및 사용 안 함 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- deactivated My Reports folder
- folders [Reporting Services], My Reports
- activated My Reports folder
- My Reports folder [Reporting Services]
- disabling My Reports folder
ms.assetid: 16c76e82-9fd4-417c-9ed3-a7d5bcd1dba2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ef9b48744365b981d11b0e5ae20dc654f2d131d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652578"
---
# <a name="enable-and-disable-my-reports"></a><span data-ttu-id="4488a-102">내 보고서 설정 및 해제</span><span class="sxs-lookup"><span data-stu-id="4488a-102">Enable and Disable My Reports</span></span>
  <span data-ttu-id="4488a-103">내 보고서 기능은 보고서 서버 데이터베이스에 프라이빗 스토리지를 할당하여 해당 사용자가 소유한 보고서를 프라이빗 폴더에 저장할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-103">The My Reports feature allocates personal storage in the report server database so that users can save reports that they own in a private folder.</span></span> <span data-ttu-id="4488a-104">보고서 서버 관리자는 이 기능을 설정 또는 해제하거나 이 작업 영역으로 수행할 수 있는 작업을 제어하는 보안 설정을 수정하여 이 기능의 작동 방식을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-104">As a report server administrator, you can enable or disable this feature or change how the feature works by modifying the security settings that control what users can do with this workspace.</span></span>  
  
 <span data-ttu-id="4488a-105">기본적으로 내 보고서 기능은 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-105">The My Reports feature is disabled by default.</span></span> <span data-ttu-id="4488a-106">모든 사용자에 대해 이 기능을 설정 또는 해제할 수 있지만 특정 사용자 그룹만 이 기능을 사용하도록 설정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-106">You can either enable or disable the feature for all users, but you cannot enable it for a subset of users.</span></span> <span data-ttu-id="4488a-107">대부분의 사용자와 조직에서는 이 기능을 유용하게 사용할 수 있습니다. 이 도움말 항목에 설명되어 있는 장단점을 잘 살펴보고 이 기능이 해당 조직에 적합한지를 판단해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="4488a-107">Most users and organizations find this feature valuable; study the advantages and disadvantages presented later in this topic to determine whether it is a good fit for your organization.</span></span>  
  
## <a name="how-to-enable-and-disable-my-reports"></a><span data-ttu-id="4488a-108">내 보고서를 설정 또는 해제하는 방법</span><span class="sxs-lookup"><span data-stu-id="4488a-108">How to Enable and Disable My Reports</span></span>  
 <span data-ttu-id="4488a-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 내 보고서를 설정하려면 보고서 서버 인스턴스에 연결하고 **서버 속성** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-109">To enable My Reports by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the report server instance and open the **Server Properties** page.</span></span> <span data-ttu-id="4488a-110">그런 다음 **일반** 탭에서 **각 사용자에 대해 내 보고서 폴더 설정** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-110">Then on the **General** tab, select the **Enable a My Reports folder for each user** option.</span></span>  
  
 <span data-ttu-id="4488a-111">내 보고서에 사용되는 역할 정의에 따라 내 보고서 작업 영역에서 지원되는 동작이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-111">The role definition used for My Reports determines what actions are supported in the My Reports workspace.</span></span> <span data-ttu-id="4488a-112">예를 들어 내 보고서 역할에서 "링크된 보고서 만들기"가 제외된 경우에 사용자는 내 보고서 폴더에서 링크된 보고서를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-112">For example, if the My Reports role excludes "Create linked reports," users cannot create linked reports in the My Reports folders.</span></span> <span data-ttu-id="4488a-113">자세한 내용은 [내 보고서 보안 설정](../security/secure-my-reports.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4488a-113">For more information, see [Secure My Reports](../security/secure-my-reports.md).</span></span>  
  
 <span data-ttu-id="4488a-114">내 보고서를 비활성화하려면 **각 사용자에 대해 내 보고서 폴더 설정**의 선택을 취소하십시오.</span><span class="sxs-lookup"><span data-stu-id="4488a-114">To deactivate My Reports, clear **Enable a My Reports folder for each user**.</span></span> <span data-ttu-id="4488a-115">내 보고서를 비활성화하면 사용자가 내 보고서 폴더에 대해 볼 수 있는 표시가 모두 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-115">Deactivating My Reports removes for users all visible indications of the My Reports folder.</span></span> <span data-ttu-id="4488a-116">실제 스토리지를 제공하는 폴더 즉, 사용자 폴더의 하위 폴더는 이 기능을 해제한 후 수동으로 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-116">The folders that provide actual storage (that is, the subfolders in Users Folders) must be deleted manually once the feature is disabled.</span></span>  
  
### <a name="when-my-reports-is-activated"></a><span data-ttu-id="4488a-117">내 보고서가 활성화된 경우</span><span class="sxs-lookup"><span data-stu-id="4488a-117">When My Reports Is Activated</span></span>  
 <span data-ttu-id="4488a-118">이 기능을 활성화하면 사용자는 루트 폴더인 홈 아래에 있는 내 보고서 폴더를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-118">Once the feature is activated, users see a My Reports folder located under the root folder, Home.</span></span> <span data-ttu-id="4488a-119">보고서 서버 관리자는 내 보고서 폴더는 물론 각 사용자의 하위 폴더가 있는 "사용자 폴더" 폴더도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-119">In addition to a My Reports folder, report server administrators also see a Users Folders folder that contains the subfolder for each user.</span></span>  
  
 <span data-ttu-id="4488a-120">이 기능이 활성화되어 있을 때는 사용자 폴더 및 그 하위 폴더를 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-120">While the feature is activated, Users Folders and its subfolders cannot be deleted.</span></span> <span data-ttu-id="4488a-121">그리고 "내 보고서"라는 이름은 루트 노드(홈) 아래에 생성된 폴더에 대한 이름으로 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-121">Furthermore, the name "My Reports" becomes a reserved name for folders created under the root node (Home).</span></span>  
  
 <span data-ttu-id="4488a-122">내 보고서를 비활성화했다가 활성화하는 경우 "사용자 폴더" 폴더가 새로 생성됩니다(없는 경우).</span><span class="sxs-lookup"><span data-stu-id="4488a-122">If you activate My Reports after it has been deactivated, the report server creates a new Users Folders folder if one does not already exist.</span></span> <span data-ttu-id="4488a-123">사용자 폴더가 있으면 사용자가 해당 내 보고서 폴더에 로그온할 때 새 하위 폴더가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-123">If Users Folders exists, the report server adds new subfolders as users log on to their My Reports folders.</span></span>  
  
### <a name="when-my-reports-is-deactivated"></a><span data-ttu-id="4488a-124">내 보고서가 비활성화된 경우</span><span class="sxs-lookup"><span data-stu-id="4488a-124">When My Reports Is Deactivated</span></span>  
 <span data-ttu-id="4488a-125">이 기능이 비활성화되면 "내 보고서"라는 이름이 더 이상 예약되지 않습니다. 사용자는 홈 폴더 아래에 내 보고서라는 개인 폴더를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-125">Once the feature is deactivated, the name "My Reports" is no longer reserved; users can create a personal folder named My Reports under the Home folder.</span></span> <span data-ttu-id="4488a-126">또한 내 보고서를 사용자별 내 보고서 하위 폴더로 리디렉션하는 기능은 더 이상 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-126">In addition, redirection from My Reports to user-specific My Reports subfolders is no longer performed.</span></span> <span data-ttu-id="4488a-127">마지막으로 URL 주소에 사용자별 내 보고서 폴더를 포함하는 보고서 링크는 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-127">Lastly, any report links that include a user-specific My Reports folder in the URL address will no longer work.</span></span>  
  
## <a name="choosing-to-use-my-reports"></a><span data-ttu-id="4488a-128">내 보고서를 사용하도록 선택</span><span class="sxs-lookup"><span data-stu-id="4488a-128">Choosing to Use My Reports</span></span>  
 <span data-ttu-id="4488a-129">전용 서버 리소스를 통해 사용자 작업 영역을 지원할지 여부에 따라 내 보고서 사용 여부가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-129">Deciding whether to use My Reports depends on whether you want to dedicate server resources to support a user workspace.</span></span> <span data-ttu-id="4488a-130">내 보고서는 사용자가 작업에 필요한 정보 리소스를 제어할 수 있도록 하는 강력한 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-130">My Reports is a powerful feature that allows users to have control over information resources that help them do their jobs.</span></span> <span data-ttu-id="4488a-131">특별한 용도로 만들어진 보고서 작업도 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-131">It also provides a way for users to work with reports that are not intended for general use.</span></span> <span data-ttu-id="4488a-132">내 보고서를 사용하는 가장 중요한 이유 중 하나는 보고서를 작성하고 검토해야 하는 사용자를 단위별로 안전하게 관리할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-132">One of the most compelling reasons to use My Reports is that it provides secure, manageable support for the segment of users who need to author and review reports.</span></span> <span data-ttu-id="4488a-133">이 기능이 없으면 각 상황에 따라 여러 사용자에 대한 폴더 및 보안 정책을 직접 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-133">Without this feature, you may find yourself creating folders and security policies for various users on an ad hoc basis.</span></span> <span data-ttu-id="4488a-134">따라서 사용자 및 사용자 요구의 변화에 따라 폴더 및 정책 수가 계속 늘어나 시간이 지날수록 관리하기 어려워집니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-134">As users and user needs change, this approach results in ever-increasing numbers of folders and policies that are difficult to maintain over time.</span></span>  
  
 <span data-ttu-id="4488a-135">내 보고서를 활성화하는 경우 내 보고서 링크를 클릭하는 도메인 계정으로 모든 사용자를 위한 내 보고서 폴더가 생성됩니다. 사용자가 원하지 않더라도 내 보고서 폴더는 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-135">Note that if you do activate My Reports, the report server creates a My Reports folder for every user with a domain account who clicks the My Reports link, even if the user does not want or need a My Reports folder.</span></span> <span data-ttu-id="4488a-136">사용되고 있는 폴더를 확인할 체계적인 방식은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-136">There is no systematic way to determine which folders are being used.</span></span> <span data-ttu-id="4488a-137">폴더에 포함된 내용이 있는지 확인하려면 폴더를 직접 살펴봐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4488a-137">You must review the folders manually to see whether they contain anything.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4488a-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4488a-138">See Also</span></span>  
 <span data-ttu-id="4488a-139">[내 보고서 보안 설정](../security/secure-my-reports.md) </span><span class="sxs-lookup"><span data-stu-id="4488a-139">[Secure My Reports](../security/secure-my-reports.md) </span></span>  
 [<span data-ttu-id="4488a-140">보고서 서버 콘텐츠 관리&#40;SSRS 기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="4488a-140">Report Server Content Management &#40;SSRS Native Mode&#41;</span></span>](report-server-content-management-ssrs-native-mode.md)  
  
  
