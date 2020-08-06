---
title: 내 보고서 보안 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- denying My Reports folder access
- private folders [Reporting Services]
- user workspace [Reporting Services]
- security [Reporting Services], My Reports folder
- My Reports folder [Reporting Services]
ms.assetid: 3b23a382-13b8-4196-9a93-7fe62d03a63c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b0a832133852e05c54a80b73fad8a91426840467
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730083"
---
# <a name="secure-my-reports"></a><span data-ttu-id="d3a79-102">내 보고서 보안 설정</span><span class="sxs-lookup"><span data-stu-id="d3a79-102">Secure My Reports</span></span>
  <span data-ttu-id="d3a79-103">내 보고서 기능은 보고서 작업을 위한 사용자 관리 작업 영역을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-103">The My Reports feature provides a user-managed workspace for working with reports.</span></span> <span data-ttu-id="d3a79-104">원래 용도대로 사용하려면 내 보고서 폴더는 여러 사용자가 사용할 수 있는 다른 폴더보다 권한 제한이 적어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-104">In order to serve its intended purpose, the My Reports folder requires less restrictive permissions than other folders that are available for general use.</span></span> <span data-ttu-id="d3a79-105">다른 폴더의 보고서를 보고 실행할 수 있는 권한만 있는 사용자가 내 보고서 폴더와 자신이 소유한 내용을 관리하려면 확장된 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-105">Users who have permissions to only view and run reports in other folders might require an expanded set of permissions to manage their My Reports folders and content that they own.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="d3a79-106">는 이 용도에 맞는 특별한 역할 할당과 역할 정의를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-106">provides a specialized role assignment and role definition for this purpose.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3a79-107">내 보고서는 보고서 관리자에서만 사용할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="d3a79-107">My Reports is available only in Report Manager.</span></span> <span data-ttu-id="d3a79-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-108">It is not available in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
## <a name="role-assignment-for-my-reports"></a><span data-ttu-id="d3a79-109">내 보고서에 대한 역할 할당</span><span class="sxs-lookup"><span data-stu-id="d3a79-109">Role Assignment for My Reports</span></span>  
 <span data-ttu-id="d3a79-110">내 보고서에 대한 역할 할당에는 미리 설정된 요소가 있으며 내 보고서 폴더를 활성화하는 각 사용자에 대해 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-110">The role assignment for My Reports has preset elements and is automatically created for each user who activates a My Reports folder.</span></span> <span data-ttu-id="d3a79-111">보고서 서버가 자동으로 보안을 할당하도록 하면 관리자가 각각의 내 보고서 사용자에 대해 액세스할 수 있도록 설정하지 않아도 되므로 내 보고서를 광범위하게 사용하는 조직에 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-111">Having the report server automatically assign security is especially useful for organizations that use My Reports widely because administrators do not have to enable access for each My Reports user.</span></span>  
  
 <span data-ttu-id="d3a79-112">**내 보고서** 역할 할당은 다음과 같은 요소로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-112">A **My Reports** role assignment consists of the following elements:</span></span>  
  
-   <span data-ttu-id="d3a79-113">사용자 폴더 \My Reports 폴더에 있는 사용자의 내 보고서 폴더 \\ *\<username>* 입니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-113">The user's My Reports folder, which is located in Users Folders\\*\<username>* \My Reports folder.</span></span>  
  
-   <span data-ttu-id="d3a79-114">내 보고서 폴더 활성화 시 결정되는 사용자 계정.</span><span class="sxs-lookup"><span data-stu-id="d3a79-114">The user account, which is determined when the My Reports folder is activated.</span></span> <span data-ttu-id="d3a79-115">사용자가 보고서 관리자에서 내 보고서 폴더를 클릭하거나 보고서 디자이너에서 내 보고서 폴더에 보고서를 게시할 때 폴더가 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-115">A folder is activated when a user clicks a My Reports folder in Report Manager or when publishing a report to a My Reports folder from Report Designer.</span></span> <span data-ttu-id="d3a79-116">이 폴더는 사용자가 내 보고서 링크에 대한 속성을 요청할 때도 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-116">This folder is also activated when a user requests properties on the My Reports link.</span></span>  
  
-   <span data-ttu-id="d3a79-117">내 보고서에 대해 미리 정의된 역할 정의</span><span class="sxs-lookup"><span data-stu-id="d3a79-117">The predefined role definition for My Reports.</span></span>  
  
## <a name="role-definition-for-my-reports"></a><span data-ttu-id="d3a79-118">내 보고서에 대한 역할 정의</span><span class="sxs-lookup"><span data-stu-id="d3a79-118">Role Definition for My Reports</span></span>  
 <span data-ttu-id="d3a79-119">**내 보고서** 역할 정의에는 내 보고서 폴더의 내용 관리를 지원하는 태스크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-119">The **My Reports** role definition includes tasks that support content management of a My Reports folder.</span></span> <span data-ttu-id="d3a79-120">**내 보고서** 역할은 한 가지 용도의 역할로 생성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-120">The **My Reports** role is intended to be a single-purpose role.</span></span> <span data-ttu-id="d3a79-121">모든 항목 수준의 보안 정책으로 이 역할을 선택할 수는 있지만 다른 폴더 요구 사항에 맞게 수정하는 작업을 최소화하려면 그렇게 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-121">Although you can choose it for any item-level security policy, you should avoid doing so to minimize the chance that you will modify it to accommodate other folder requirements.</span></span> <span data-ttu-id="d3a79-122">내 보고서 기능에 대해 **내 보고서** 역할을 예약하면 여러 사용자에 대해 일관된 역할을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-122">Reserving the **My Reports** role for the My Reports feature can help you maintain a consistent experience for users.</span></span>  
  
 <span data-ttu-id="d3a79-123">기본적으로 보고서 서버 관리자만 **내 보고서** 역할을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-123">By default, only report server administrators modify the **My Reports** role.</span></span> <span data-ttu-id="d3a79-124">포함된 태스크를 변경하여 **내 보고서** 역할을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-124">You can customize the **My Reports** role by changing the tasks it contains.</span></span> <span data-ttu-id="d3a79-125">다른 역할로 대체할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-125">You can also substitute a different role.</span></span>  
  
## <a name="denying-access-to-my-reports"></a><span data-ttu-id="d3a79-126">내 보고서에 대한 액세스 거부</span><span class="sxs-lookup"><span data-stu-id="d3a79-126">Denying Access to My Reports</span></span>  
 <span data-ttu-id="d3a79-127">다음과 같은 방법으로 다른 사용자가 내 보고서에 액세스하지 못하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-127">You can prevent users from accessing My Reports by:</span></span>  
  
-   <span data-ttu-id="d3a79-128">사이트 설정 페이지에서 내 보고서 해제.</span><span class="sxs-lookup"><span data-stu-id="d3a79-128">Disabling My Reports on the Site Settings page.</span></span> <span data-ttu-id="d3a79-129">자세한 내용은 [내 보고서 설정 및 해제](../report-server/enable-and-disable-my-reports.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3a79-129">For more information, see [Enable and Disable My Reports](../report-server/enable-and-disable-my-reports.md).</span></span>  
  
-   <span data-ttu-id="d3a79-130">**내 보고서** 역할에서 모든 태스크 제거</span><span class="sxs-lookup"><span data-stu-id="d3a79-130">Removing all tasks from the **My Reports** role.</span></span>  
  
 <span data-ttu-id="d3a79-131">내 보고서를 해제하면 내 보고서 폴더에 대한 링크가 보고서 관리자에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-131">When you disable My Reports, the link to a My Reports folder is removed from Report Manager.</span></span> <span data-ttu-id="d3a79-132">내 보고서를 지원하는 기본 폴더 구조, 즉 사용자 폴더 폴더와 하위 폴더는 계속 사용할 수 있으며 사용자가 폴더 경로를 알고 있으면 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-132">The underlying folder structure that supports My Reports (that is, the Users Folders folder and subfolders) is still available and can be accessed if a user knows the folder path.</span></span> <span data-ttu-id="d3a79-133">**내 보고서** 역할에서 태스크를 제거하면 액세스할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3a79-133">Removing tasks from **My Reports** role ensures that access is prevented.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3a79-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d3a79-134">See Also</span></span>  
 <span data-ttu-id="d3a79-135">[보고서 및 리소스 보안](secure-reports-and-resources.md) </span><span class="sxs-lookup"><span data-stu-id="d3a79-135">[Secure Reports and Resources](secure-reports-and-resources.md) </span></span>  
 <span data-ttu-id="d3a79-136">[보안 폴더](secure-folders.md) </span><span class="sxs-lookup"><span data-stu-id="d3a79-136">[Secure Folders](secure-folders.md) </span></span>  
 [<span data-ttu-id="d3a79-137">기본 모드 보고서 서버에 대한 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="d3a79-137">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
