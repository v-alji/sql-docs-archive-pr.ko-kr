---
title: Sharepoint 사이트의 보고서 서버 항목에 대 한 사용 권한 설정 (SharePoint 통합 모드의 Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], SharePoint integrated mode
- SharePoint integration [Reporting Services], permissions
ms.assetid: 2467c657-a3bf-4ec3-a88c-8877df19823d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f38497843ca99342f13952153d7fed957564e006
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730079"
---
# <a name="set-permissions-for-report-server-items-on-a-sharepoint-site-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="7bbb8-102">SharePoint 사이트의 보고서 서버 항목에 대한 사용 권한 설정(SharePoint 통합 모드의 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="7bbb8-102">Set Permissions for Report Server Items on a SharePoint Site (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="7bbb8-103">기본 보안 설정으로 필요한 액세스 수준을 얻을 수 없는 경우 새 사용 권한 수준을 만들어 특정 보고서 서버 항목이나 작업에 대한 액세스 권한을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-103">If default security settings do not provide the level of access that you require, you can create new permission levels to provide access to specific report server items or operations.</span></span> <span data-ttu-id="7bbb8-104">사용자 지정 보안 설정은 특정 보고서에 대한 액세스를 제한하려는 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-104">Custom security settings can be useful if you want to restrict access to a particular report.</span></span>  
  
 <span data-ttu-id="7bbb8-105">사용 권한 수준 및 그룹을 만들려면 사이트 소유자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-105">You must be a site owner to create permission levels and groups.</span></span> <span data-ttu-id="7bbb8-106">사용 권한 수준은 사이트 전체에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-106">Permission levels are used globally throughout a site.</span></span> <span data-ttu-id="7bbb8-107">새 사용 권한 수준을 만들면 다른 사이트 소유자도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-107">If you create a new permission level, it will be available to other site owners.</span></span>  
  
 <span data-ttu-id="7bbb8-108">대부분의 사용 권한은 부모 사이트로부터 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-108">Most permissions are inherited from a parent site.</span></span> <span data-ttu-id="7bbb8-109">특정 라이브러리나 항목에 대해 사용 권한을 할당하면 사용 권한 상속이 해제되고 사이트 계층의 해당 분기에 대해 사용 권한을 관리해야 하는 추가 오버헤드가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-109">If you assign permissions on a specific library or item, you break permission inheritance and incur additional overhead in how manage permissions for that branch of your site hierarchy.</span></span>  
  
 <span data-ttu-id="7bbb8-110">보고서 정의 파일(.rdl), 모델 파일(.smdl) 및 공유 데이터 원본 파일(.rsds)에 대해 사용 권한을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-110">You can set permissions on report definition (.rdl), model (.smdl), and shared data source (.rsds) files.</span></span> <span data-ttu-id="7bbb8-111">동일한 항목에 대해 상속된 사용 권한과 관리되는 사용 권한을 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-111">You cannot combine inherited and managed permissions on the same item.</span></span> <span data-ttu-id="7bbb8-112">직접 사용 권한을 관리하도록 선택하면 상속된 사용 권한은 현재 항목에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-112">If you choose to manage permissions directly, inherited permissions will have no effect on the current item.</span></span> <span data-ttu-id="7bbb8-113">나중에 사용 권한 상속을 재개하려면 **동작** 메뉴에서 **사용 권한 상속** 을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-113">If you want to resume permission inheritance later, you can select **Inherit Permissions** on the **Actions** menu.</span></span>  
  
 <span data-ttu-id="7bbb8-114">모델의 엔터티와 큐브 뷰에 대해 사용 권한을 설정하려면 모델에 대한 모든 권한 수준의 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-114">To set permissions on entities and perspectives in a model, you must have Full Control level of permission for the model.</span></span> <span data-ttu-id="7bbb8-115">모든 권한에는 사이트 소유자 및 모든 권한 수준의 사용 권한이 있는 기타 SharePoint 그룹에 부여되는 사이트 수준의 사용 권한인 "사용 권한 관리"가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-115">Full Control includes "Manage Permissions", which is a site level permission that is granted to site owners and other SharePoint groups who have Full Control level of permission.</span></span> <span data-ttu-id="7bbb8-116">특정 사용자에게 모델 항목 보안을 설정할 수 있도록 권한을 부여하려는 경우 사용 권한 상속을 해제하고 사용자나 그룹에 모델 파일에 대한 승격된 사용 권한(예: 모든 권한)을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-116">If you want to offer specific users the ability to set model item security, you must break permission inheritance and grant elevated permissions (such as Full Control) to the user or group on the model file.</span></span> <span data-ttu-id="7bbb8-117">라이브러리의 항목(예: 파일)에 대한 "모든 권한"을 부여하면 사용 권한의 범위는 해당 항목이고 동일한 라이브러리 내에서 부모 또는 다른 항목으로 확장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-117">When you grant Full Control on an item such as a file in the library, the permissions are scoped to that item and do not extend to the parent or to other items within the same library.</span></span> <span data-ttu-id="7bbb8-118">모델에 대한 "사용 권한 관리" 권한이 부여된 사용자는 SharePoint 사이트나 모델 디자이너를 통해 모델 항목 보안을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-118">After the user has Manage Permissions permission on the model, he or she can use set model item security via the SharePoint site or Model Designer.</span></span>  
  
### <a name="to-set-permissions-on-an-individual-report-model-or-data-source"></a><span data-ttu-id="7bbb8-119">개별 보고서, 모델 또는 데이터 원본에 대한 사용 권한을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="7bbb8-119">To set permissions on an individual report, model, or data source</span></span>  
  
1.  <span data-ttu-id="7bbb8-120">라이브러리가 열려 있지 않으면 빠른 실행에서 해당 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-120">If the library is not already open, click its name on the Quick Launch.</span></span> <span data-ttu-id="7bbb8-121">라이브러리 이름이 나타나지 않으면 **모든 사이트 콘텐츠 보기**를 클릭한 다음 라이브러리 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-121">If the name of your library does not appear, click **View All Site Content**, and then click the name of your library.</span></span>  
  
2.  <span data-ttu-id="7bbb8-122">보고서, 보고서 모델 또는 공유 데이터 원본 파일을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-122">Point to the report, report model, or shared data source file.</span></span>  
  
3.  <span data-ttu-id="7bbb8-123">아래쪽 화살표를 클릭하고 메뉴에서 **사용 권한 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-123">Click the down arrow, and on the menu, click **Manage Permissions**.</span></span>  
  
4.  <span data-ttu-id="7bbb8-124">**동작** 메뉴에서 **사용 권한 편집**을 클릭한 다음 **확인** 을 클릭하여 동작을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-124">On the **Actions** menu, click **Edit Permissions**, and then click **OK** to confirm the action.</span></span>  
  
5.  <span data-ttu-id="7bbb8-125">아직 파일을 사용할 권한이 없는 사용자나 그룹에 사용 권한을 부여하려면 **새로 만들기**, **사용자 추가**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-125">To give permissions to a user or group that does not yet have permissions to use the file, click **New**, and then click **Add Users**.</span></span>  
  
6.  <span data-ttu-id="7bbb8-126">기존 사용자 또는 그룹의 사용 권한을 제거하거나 수정하려면 사용자나 그룹 옆의 확인란을 클릭하고 **동작**을 클릭한 다음 **사용자의 사용 권한 제거** 또는 **사용자의 사용 권한 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-126">To remove or modify permissions for an existing user or group, click the check box next to the user or group, click **Actions**, and then click **Remove User Permissions** or **Edit User Permissions**.</span></span>  
  
### <a name="to-set-permissions-that-enable-model-item-security"></a><span data-ttu-id="7bbb8-127">모델 항목 보안을 설정하는 사용 권한을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="7bbb8-127">To set permissions that enable model item security</span></span>  
  
1.  <span data-ttu-id="7bbb8-128">사이트에 대한 "사용 권한 관리" 권한이 있는 계정을 사용하여 SharePoint 사이트에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-128">Log in to the SharePoint site using an account that has Manage Permissions permission on the site.</span></span>  
  
2.  <span data-ttu-id="7bbb8-129">모델이 포함된 라이브러리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-129">Open the library that contains the model.</span></span>  
  
3.  <span data-ttu-id="7bbb8-130">모델을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-130">Point to the model.</span></span>  
  
4.  <span data-ttu-id="7bbb8-131">모델 옆의 아래쪽 화살표를 클릭하고 **사용 권한 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-131">Click the down arrow next to the model, and click **Manage Permissions**.</span></span>  
  
5.  <span data-ttu-id="7bbb8-132">**동작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-132">Click **Actions**.</span></span>  
  
6.  <span data-ttu-id="7bbb8-133">**사용 권한 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-133">Click **Edit Permissions**.</span></span> <span data-ttu-id="7bbb8-134">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-134">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="7bbb8-135">**새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-135">Click **New**.</span></span>  
  
8.  <span data-ttu-id="7bbb8-136">**사용자 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-136">Click **Add Users**.</span></span>  
  
9. <span data-ttu-id="7bbb8-137">사용자/그룹에 사용자 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-137">In Users/Groups, enter the user account.</span></span>  
  
10. <span data-ttu-id="7bbb8-138">**사용자에게 사용 권한 직접 부여**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-138">Select **Give users permission directly**.</span></span>  
  
11. <span data-ttu-id="7bbb8-139">**모든 권한**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-139">Click **Full Control**.</span></span>  
  
12. <span data-ttu-id="7bbb8-140">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-140">Click **OK**.</span></span> <span data-ttu-id="7bbb8-141">특정 모델에 대한 사용 권한 관리 권한이 있는 사용자는 모델을 열어 모델 내에서 사용 권한을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-141">Once a user has the ability to manage permissions for a specific model, he or she can open the model to edit permissions within the model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bbb8-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7bbb8-142">See Also</span></span>  
 <span data-ttu-id="7bbb8-143">[보고서 서버 항목에 대해 Windows SharePoint Services의 기본 제공 보안 사용](use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md) </span><span class="sxs-lookup"><span data-stu-id="7bbb8-143">[Use Built-in Security in Windows SharePoint Services for Report Server Items](use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md) </span></span>  
 <span data-ttu-id="7bbb8-144">[SharePoint 웹 애플리케이션에서 보고서 서버 작업에 대한 사용 권한 설정](set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md) </span><span class="sxs-lookup"><span data-stu-id="7bbb8-144">[Set Permissions for Report Server Operations in a SharePoint Web Application](set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md) </span></span>  
 <span data-ttu-id="7bbb8-145">[Reporting Services의 역할 및 태스크와 SharePoint 그룹 및 사용 권한 비교](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="7bbb8-145">[Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md) </span></span>  
 <span data-ttu-id="7bbb8-146">[보고서 서버 항목에 대한 SharePoint 사이트 및 목록 사용 권한 참조](sharepoint-site-and-list-permission-reference-for-report-server-items.md) </span><span class="sxs-lookup"><span data-stu-id="7bbb8-146">[SharePoint Site and List Permission Reference for Report Server Items](sharepoint-site-and-list-permission-reference-for-report-server-items.md) </span></span>  
 [<span data-ttu-id="7bbb8-147">SharePoint 사이트의 보고서 서버 항목에 대한 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="7bbb8-147">Granting Permissions on Report Server Items on a SharePoint Site</span></span>](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
  
  
