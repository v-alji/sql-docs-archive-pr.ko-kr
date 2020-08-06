---
title: 역할 만들기, 삭제 또는 수정(Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- deleting roles
- removing roles
- roles [Reporting Services], definitions
- modifying roles
- roles [Reporting Services], deleting
- roles [Reporting Services], modifying
ms.assetid: 3d1d56e6-a283-44a7-8417-36cb4d2c74d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 543bddda88e41af39d3200df4728716d46b3ae8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736016"
---
# <a name="create-delete-or-modify-a-role-management-studio"></a><span data-ttu-id="ef98e-102">역할 만들기, 삭제 또는 수정(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="ef98e-102">Create, Delete, or Modify a Role (Management Studio)</span></span>
  <span data-ttu-id="ef98e-103">Reporting Services에서는 보고서 서버에 대한 액세스 수준을 정의한 미리 정의된 역할을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-103">Reporting Services provides predefined roles that define a level of access to a report server.</span></span> <span data-ttu-id="ef98e-104">보고서 서버에 액세스해야 하는 사용자나 그룹은 수행할 수 있는 태스크를 설명하는 역할을 통해 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-104">Each user or group who requires access to report server does so through a role that describes the tasks that can be performed.</span></span> <span data-ttu-id="ef98e-105">역할은 보고서 서버 전체에 대해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-105">Roles are defined for the report server as a whole.</span></span> <span data-ttu-id="ef98e-106">보고서 서버의 특정 부분에 대한 역할 정의를 다르게 하거나 환경에 따라 다르게 역할을 사용하도록 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-106">You cannot vary a role definition for specific parts of the report server, or specify that a role be used differently depending on the circumstances.</span></span>  
  
 <span data-ttu-id="ef98e-107">역할을 생성, 수정 또는 삭제하려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-107">To create, modify, or delete roles, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="ef98e-108">사용되지 않은 역할만 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-108">You can only delete roles that are not used.</span></span>  
  
 <span data-ttu-id="ef98e-109">만든 역할에 사용자나 그룹을 할당하려면 보고서 관리자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-109">To assign users and groups to the roles that you create, use Report Manager.</span></span> <span data-ttu-id="ef98e-110">자세한 내용은 [사용자에 게 보고서 서버에 대 한 액세스 권한 부여 &#40;보고서 관리자&#41;](grant-user-access-to-a-report-server.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef98e-110">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ef98e-111">보고서 서버가 SharePoint 통합 모드용으로 구성되고 보고서 서버가 통합된 SharePoint 사이트에 연결된 경우 보고서 서버 내용 및 작업에 대한 액세스를 제어하는 사용 권한 수준을 보고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-111">If the report server is configured for SharePoint integrated mode, and you connected to the SharePoint site that the report server is integrated with, you can view and modify the permission levels that control access to report server content and operations.</span></span>  
  
### <a name="to-create-a-role-definition"></a><span data-ttu-id="ef98e-112">역할 정의를 만들려면</span><span class="sxs-lookup"><span data-stu-id="ef98e-112">To create a role definition</span></span>  
  
1.  <span data-ttu-id="ef98e-113">개체 탐색기에서 보고서 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-113">In Object Explorer, expand a report server node.</span></span>  
  
2.  <span data-ttu-id="ef98e-114">보안 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-114">Expand the Security folder.</span></span>  
  
3.  <span data-ttu-id="ef98e-115">항목 수준의 역할 정의를 만드는 경우 **역할**을 마우스 오른쪽 단추로 클릭하고 **새 역할**을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-115">If you are creating an item-level role definition, right-click **Roles**, and point to **New Role**.</span></span>  
  
     <span data-ttu-id="ef98e-116">또는 시스템 수준의 역할 정의를 만드는 경우 **시스템 역할**을 마우스 오른쪽 단추로 클릭하고 **새 시스템 역할**을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-116">Or, if you are creating a system-level role definition, right-click **System Roles**, and point to **New System Role**.</span></span>  
  
4.  <span data-ttu-id="ef98e-117">역할의 고유 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-117">Type a unique name for the role.</span></span> <span data-ttu-id="ef98e-118">이름은 한 글자 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-118">A name must contain at least one character.</span></span> <span data-ttu-id="ef98e-119">공백 및 특정 기호도 포함할 수 있지만 ; ?</span><span class="sxs-lookup"><span data-stu-id="ef98e-119">It can also include spaces and certain symbols, but not the characters ; ?</span></span> <span data-ttu-id="ef98e-120">: \@ & = +, $/\* \< > | "또는/입니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-120">: \@ & = + , $ / \* \< > | " or /.</span></span>  
  
5.  <span data-ttu-id="ef98e-121">설명을 입력합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="ef98e-121">Optionally type a description.</span></span> <span data-ttu-id="ef98e-122">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에서 이 설명은 이 페이지에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-122">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] this description is visible only on this page.</span></span> <span data-ttu-id="ef98e-123">보고자 관리자를 통해 이 항목을 보는 사용자는 해당 도구에서 이 설명을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-123">Users who view this item through Report Manager can see this description in that tool.</span></span>  
  
6.  <span data-ttu-id="ef98e-124">이 역할의 멤버가 수행할 수 있는 태스크를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-124">Select the tasks that members of this role can perform.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-or-modify-a-role-definition"></a><span data-ttu-id="ef98e-125">역할 정의를 삭제하거나 수정하려면</span><span class="sxs-lookup"><span data-stu-id="ef98e-125">To delete or modify a role definition</span></span>  
  
1.  <span data-ttu-id="ef98e-126">개체 탐색기에서 보고서 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-126">In Object Explorer, expand a report server node.</span></span>  
  
2.  <span data-ttu-id="ef98e-127">보안 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-127">Expand the Security folder.</span></span>  
  
3.  <span data-ttu-id="ef98e-128">항목 수준의 역할 정의를 삭제하거나 수정하려면 역할 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-128">To delete or modify an item-level role definition, expand the Roles folder.</span></span> <span data-ttu-id="ef98e-129">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-129">Perform one of the following:</span></span>  
  
    1.  <span data-ttu-id="ef98e-130">역할 정의를 삭제하려면 항목을 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-130">To delete a role definition, right-click the item and click **Delete**.</span></span> <span data-ttu-id="ef98e-131">**개체 삭제** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-131">The **Delete Object** dialog box is displayed.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    2.  <span data-ttu-id="ef98e-132">역할 정의를 수정하려면 항목을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-132">To modify a role definition, right-click the item and click **Properties**.</span></span> <span data-ttu-id="ef98e-133">**사용자 역할 속성** 대화 상자의 일반 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-133">The General page of the **User Role Properties** dialog box is displayed.</span></span>  
  
         <span data-ttu-id="ef98e-134">이 역할의 멤버가 수행할 수 있는 태스크를 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-134">Select the tasks that members of this role can perform, and click **OK**.</span></span>  
  
4.  <span data-ttu-id="ef98e-135">시스템 수준의 역할 정의를 삭제하거나 수정하려면 **시스템 역할** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-135">To delete or modify a system-level role definition, expand the **System Roles** folder.</span></span> <span data-ttu-id="ef98e-136">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-136">Perform one of the following:</span></span>  
  
    1.  <span data-ttu-id="ef98e-137">시스템 역할 정의를 삭제하려면 항목을 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-137">To delete a system role definition, right-click the item and click **Delete**.</span></span> <span data-ttu-id="ef98e-138">**개체 삭제** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-138">The **Delete Object** dialog box is displayed.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    2.  <span data-ttu-id="ef98e-139">시스템 역할 정의를 수정하려면 항목을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-139">To modify a system role definition, right-click the item and click **Properties**.</span></span> <span data-ttu-id="ef98e-140">**시스템 역할 속성** 대화 상자의 일반 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-140">The General page of the **System Role Properties** dialog box is displayed.</span></span>  
  
         <span data-ttu-id="ef98e-141">이 역할의 멤버가 수행할 수 있는 태스크를 선택하고 **확인** 을 클릭하여 변경 내용을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="ef98e-141">Select the tasks that members of this role can perform, and click **OK** to apply the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef98e-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef98e-142">See Also</span></span>  
 <span data-ttu-id="ef98e-143">[Management Studio에서 보고서 서버에 연결](../tools/connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ef98e-143">[Connect to a Report Server in Management Studio](../tools/connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="ef98e-144">(create-and-manage-role-assignments.md)</span><span class="sxs-lookup"><span data-stu-id="ef98e-144">(create-and-manage-role-assignments.md)</span></span>   
 [<span data-ttu-id="ef98e-145">SQL Server Management Studio의 Reporting Services&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ef98e-145">Reporting Services in SQL Server Management Studio &#40;SSRS&#41;</span></span>](../tools/reporting-services-in-sql-server-management-studio-ssrs.md)  
  
  
