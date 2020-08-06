---
title: 사용자 및 경고 관리자에게 사용 권한 부여 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 166808e1-ada7-48d2-bda8-8f7c017fb3aa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5bf7f030871287379ce9fb32a1789b95cff0fc0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660348"
---
# <a name="grant-permissions-to-users-and-alerting-administrators"></a><span data-ttu-id="539aa-102">사용자 및 경고 담당자에게 권한 부여</span><span class="sxs-lookup"><span data-stu-id="539aa-102">Grant Permissions to Users and Alerting Administrators</span></span>
  <span data-ttu-id="539aa-103">사용자 및 경고 담당자는 SharePoint 권한을 부여 받아야 경로를 만들고, 편집하고, 삭제하고 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-103">Before users and alerting administrators can create, edit, delete, and view data alerts they must be granted SharePoint permissions.</span></span> <span data-ttu-id="539aa-104">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 데이터 알림 기능을 사용하는 데에는 특별한 권한이 필요 없이 기본 제공 SharePoint 권한을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-104">There are no special permissions to use with the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] data alerting feature, you use the built-in SharePoint permissions.</span></span>  
  
 <span data-ttu-id="539aa-105">**정보 근로자** - 경고 만들기 및 항목 보기 SharePoint 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-105">**Information workers**-Permissions must include the Create Alert and View Items SharePoint permissions.</span></span> <span data-ttu-id="539aa-106">디자인, 참가, 읽기, 보기만 등의 기본 제공 SharePoint 권한 수준은 경고 만들기 및 항목 보기 SharePoint 권한을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-106">The built-in SharePoint permission levels named Design, Contribute, Read, and View Only include the Create Alert and View Items SharePoint permissions.</span></span> <span data-ttu-id="539aa-107">알림을 만들고 편집하며 실행하고 보는 사용자를 지원하는 데 필요한 권한이 있으면 사용자 지정 권한 수준을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-107">You can also create a custom permission level with the permissions required to support users that create, edit, run, and view data alerts.</span></span>  
  
 <span data-ttu-id="539aa-108">**경고 담당자** - 경고 관리 SharePoint 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-108">**Alerting administrators**-Permissions must include the Manage Alert SharePoint permission.</span></span> <span data-ttu-id="539aa-109">기본적으로 팀 사이트 사이트 템플릿을 사용하여 만든 사이트에 대해서는 모든 권한 수준만 이 권한을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-109">By default only the Full Control permission level includes this permission for sites created with the Team Site site template.</span></span> <span data-ttu-id="539aa-110">다른 사이트 템플릿을 사용하는 경우 기본 SharePoint 그룹의 다른 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-110">If you use other site templates, you will see different lists of default SharePoint groups.</span></span> <span data-ttu-id="539aa-111">기본 제공 권한 수준 중 하나에 경고 관리 권한을 추가할 수 있습니다. 또는 데이터 경고를 보고 삭제하는 경고 담당자를 지원하는 데 필요한 권한이 있으면 사용자 지정 권한 수준을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-111">You can add the Manage Alert permission to one of the built-in permission levels or create a custom permission level with the permission required to support alerting administrators that view and delete data alerts.</span></span>  
  
 <span data-ttu-id="539aa-112">SharePoint 권한에 대한 자세한 내용은 [사용자 권한 및 권한 수준(SharePoint Server 2010)](https://technet.microsoft.com/library/cc721640.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="539aa-112">To learn more about SharePoint permissions, see [User permissions and permission levels (SharePoint Server 2010)](https://technet.microsoft.com/library/cc721640.aspx).</span></span>  
  
### <a name="to-grant-permissions"></a><span data-ttu-id="539aa-113">사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="539aa-113">To grant permissions</span></span>  
  
1.  <span data-ttu-id="539aa-114">사용 권한을 부여할 SharePoint 사이트로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-114">Go to the SharePoint site to which you want to grant permissions.</span></span>  
  
2.  <span data-ttu-id="539aa-115">도구 모음에서 **사이트 작업** 을 클릭한 후 **사이트 사용 권한**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-115">On the toolbar, click **Site Actions** and then click **Site Permissions**.</span></span>  
  
     <span data-ttu-id="539aa-116">이 옵션이 나타나지 않으면 다른 사람에게 권한을 부여할 권한이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-116">If you do not see this option, you do not sufficient permission to grant permissions to others.</span></span>  
  
3.  <span data-ttu-id="539aa-117">**권한 부여**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-117">Click **Grant Permissions**.</span></span>  
  
4.  <span data-ttu-id="539aa-118">**사용자/그룹**에서 권한을 부여할 대상의 사용자 이름, 그룹 이름 또는 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-118">In **Users/Groups**, type the user names, group names, or e-mail addresses you want grant permission to.</span></span>  
  
5.  <span data-ttu-id="539aa-119">**SharePoint 그룹에 사용자 추가** 또는 **사용자에게 사용 권한 직접 부여** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-119">Select the **Add users to a SharePoint group** or **Grant users permission directly** option.</span></span> <span data-ttu-id="539aa-120">**SharePoint 그룹에 사용자 추가** 를 선택했는지, 아니면 **사용자에게 사용 권한 직접 부여** 를 선택했는지에 따라 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-120">Depending on whether you selected **Add users to a SharePoint group** or **Grant users permissions directly** do one of the following:</span></span>  
  
    -   <span data-ttu-id="539aa-121">**SharePoint 그룹에 사용자 추가**를 선택한 경우 드롭다운 목록에서 권한 수준을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-121">If you selected **Add users to a SharePoint group**, select a permission level in the drop-down list.</span></span>  
  
    -   <span data-ttu-id="539aa-122">**사용자에게 사용 권한 직접 부여**를 선택한 경우 권한 수준을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="539aa-122">If you selected **Grant users permissions directly**, select a permission level.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="539aa-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="539aa-123">See Also</span></span>  
 <span data-ttu-id="539aa-124">[Sharepoint 사이트의 보고서 서버 항목에 대 한 사용 권한은 SharePoint 통합 모드에서 Reporting Services &#40;설정&#41;](security/set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="539aa-124">[Set Permissions for Report Server Items on a SharePoint Site &#40;Reporting Services in SharePoint Integrated Mode&#41;](security/set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span></span>  
 [<span data-ttu-id="539aa-125">Reporting Services 데이터 경고</span><span class="sxs-lookup"><span data-stu-id="539aa-125">Reporting Services Data Alerts</span></span>](../ssms/agent/alerts.md)  
  
  
