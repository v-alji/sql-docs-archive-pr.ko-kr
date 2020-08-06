---
title: SharePoint 중앙 관리에서 보고서 서버 파일 동기화 기능 활성화 | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 03/06/2017
ms.openlocfilehash: 55feac69da85c7287ea56f4b8245350dd7e69565
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652661"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a><span data-ttu-id="6c361-102">SharePoint 중앙 관리에서 보고서 서버 파일 동기화 기능 활성화</span><span class="sxs-lookup"><span data-stu-id="6c361-102">Activate the Report Server File Sync Feature in SharePoint Central Administration</span></span>

<span data-ttu-id="6c361-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서 서버 파일 동기화 기능은 SharePoint 이벤트 처리기를 활용하여 보고서 서버 카탈로그를 문서 라이브러리의 항목과 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="6c361-103">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Report Server File Sync feature utilizes SharePoint event handlers to synchronize the report server catalog with items in document libraries.</span></span> <span data-ttu-id="6c361-104">이 기능은 사용자가 게시된 보고서 항목을 SharePoint 문서 라이브러리에 직접 자주 업로드하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c361-104">This feature is beneficial when users frequently upload published report items directly to SharePoint document libraries.</span></span> <span data-ttu-id="6c361-105">파일 동기화 기능이 활성화 되지 않은 경우 콘텐츠는 계속 동기화 되지만 자주 동기화 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c361-105">If the file Sync feature isn't activated, content will still be synchronized but not as frequently.</span></span>  
  
<span data-ttu-id="6c361-106">파일 동기화 기능은 SharePoint 제품용 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 추가 기능을 설치한 후 SharePoint 사이트 관리에서 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c361-106">The File Sync feature can be activated in SharePoint Site Administration after you install the [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] Add-in for SharePoint products.</span></span>  
  
<span data-ttu-id="6c361-107">이 기능은 사이트별로 수동으로 활성화하고 비활성화할 수 있으나 사이트 모음 수준에서는 이렇게 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c361-107">This feature can be manually activated and deactivated per site but not at the site collection level.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6c361-108">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="6c361-108">Prerequisites</span></span>  
 <span data-ttu-id="6c361-109">SharePoint용 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 추가 기능을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c361-109">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in for SharePoint must be installed.</span></span> <span data-ttu-id="6c361-110">추가 기능이 설치 되어 있지 않으면 파일 동기화 기능이 사이트 기능 목록에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c361-110">If the add-in isn't installed, the file sync feature won't be visible in the site feature list.</span></span>  
  
 <span data-ttu-id="6c361-111">설치를 확인하려면 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows **제어판**에서 설치된 애플리케이션 목록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6c361-111">To verify installation, view the list of installed applications in [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows **Control Panel**.</span></span> <span data-ttu-id="6c361-112">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 추가 기능이 설치되어 있으면 이 항목의 지침에 따라 보고서 서버 파일 동기화 기능을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="6c361-112">If the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in is installed, follow the instructions in this topic to activate the report server file sync feature.</span></span>  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a><span data-ttu-id="6c361-113">사이트에서 Reporting Services 파일 동기화 기능을 활성화 또는 비활성화하려면</span><span class="sxs-lookup"><span data-stu-id="6c361-113">To activate or deactivate the Reporting Services File Sync feature on a Site</span></span>  
  
1.  <span data-ttu-id="6c361-114">사이트의 기본 페이지에서 **사이트 작업** 메뉴를 클릭 하 고 **사이트 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c361-114">From the main page of your site, click the **Site Actions** menu and click **Site Settings**.</span></span>  
  
2.  <span data-ttu-id="6c361-115">**사이트 작업**에서 **사이트 기능 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c361-115">In the **Site Actions**, click **Manage Site Features**.</span></span>  
  
3.  <span data-ttu-id="6c361-116">목록에서 **보고서 서버 파일 동기화** 를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6c361-116">Find **Report Server File Sync** in the list.</span></span>  
  
4.  <span data-ttu-id="6c361-117">**활성화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c361-117">Click **Activate**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c361-118">보고서 서버 파일 동기화 기능을 비활성화하려면 동일한 절차를 따르면서 **비활성화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c361-118">To deactivate the Report Server file sync feature, you can use the same procedure but click **Deactivate**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c361-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6c361-119">See Also</span></span>  
 <span data-ttu-id="6c361-120">[보고서 파트 &#40;보고서 작성기 및 SSRS에 대 한 문제 해결&#41;](report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6c361-120">[Troubleshoot Report Parts &#40;Report Builder and SSRS&#41;](report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6c361-121">[SharePoint에서 보고서 서버 활성화 및 통합 기능 파워 뷰](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="6c361-121">[Activate the Report Server and Power View Integration Features in SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md) </span></span>  
 <span data-ttu-id="6c361-122">[Sharepoint 2010 및 SharePoint 2013 &#40;Reporting Services 추가 기능을 설치 하거나 제거&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="6c361-122">[Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="6c361-123">Sharepoint 2010 및 SharePoint 2013 &#40;Reporting Services 추가 기능을 설치 하거나 제거&#41;</span><span class="sxs-lookup"><span data-stu-id="6c361-123">Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
