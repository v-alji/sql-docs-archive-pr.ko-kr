---
title: SharePoint에서 보고서 서버 및 파워 뷰 통합 기능을 활성화 합니다. Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c7f64a54-c555-4d31-bf99-3abe57dc8626
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af5f544e959c039b0bdb85d63d0b94917254d78a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659850"
---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a><span data-ttu-id="0e3dc-102">SharePoint에서 보고서 서버 및 파워 뷰 통합 사이트 모음 기능 활성화</span><span class="sxs-lookup"><span data-stu-id="0e3dc-102">Activate the Report Server and Power View Integration Features in SharePoint</span></span>
  <span data-ttu-id="0e3dc-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] SharePoint 제품용 추가 기능을 설치 하면 일반적으로 사이트 모음 기능이 기본적으로 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-103">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] site collection features are usually activated by default after you install the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] Add-in for SharePoint products.</span></span> <span data-ttu-id="0e3dc-104">일부 경우에는 기능을 수동으로 활성화해야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-104">In some situations you will need to manually activate the features.</span></span>  
  
 <span data-ttu-id="0e3dc-105">SharePoint 제품의 설치 이후에 SharePoint 2010 제품용 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 추가 기능을 설치하면 보고서 서버 통합 기능 및 파워 뷰 통합 기능이 루트 사이트 모음에 대해서만 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-105">If you install the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in for SharePoint 2010 Products after the installation of the SharePoint product, then the Report Server integration feature and the Power View integration feature will only be activated for root site collections.</span></span> <span data-ttu-id="0e3dc-106">기타 사이트 모음의 경우 기능을 수동으로 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-106">For other site collections, you will need to manually activate the features.</span></span> <span data-ttu-id="0e3dc-107">예를 들어 **http://[내 서버 이름]/sites/[사이트 모음 이름]** 의 사이트 모음이 있는 경우 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 사이트 모음 기능을 수동으로 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-107">For example if you have a site collection of **http://[my server name]/sites/[site collection name]** you will need to manually activate the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] site collection features.</span></span>  
  
 <span data-ttu-id="0e3dc-108">루트 사이트 모음이 없으면 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 추가 기능이 다음과 유사한 메시지를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-108">When there is no root site collection, the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in will log a message similar to the following.</span></span>  
  
 <span data-ttu-id="0e3dc-109">"SharePoint 웹 응용 프로그램 80에는 루트 사이트 모음이 없습니다."</span><span class="sxs-lookup"><span data-stu-id="0e3dc-109">"SharePoint web app 80 does not have root site collection"</span></span>  
  
 <span data-ttu-id="0e3dc-110">"RS_SP_ # .log" 라는 추가 기능 설치 로그에서 메시지를 찾을 수 있습니다. 여기서 #는 증가 하는 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-110">The message will be found in the add-in installation log, named "RS_SP_#.log" where # is an incrementing number.</span></span> <span data-ttu-id="0e3dc-111">로그 파일은 현재 사용자 임시 폴더 (예: C:\Users \\ [사용자 이름] \appdata\local\temp)에서 찾을 수 있습니다. 추가 기능을 사용 하 여 로깅 옵션에 대 한 자세한 내용은 sharepoint [2010 및 sharepoint 2013&#41;&#40;Reporting Services 추가 기능 설치 또는 제거 ](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-111">The log file will be found in the current users Temp folder, for example C:\Users\\[user name]\AppData\Local\Temp. For more information on logging options with the add-in, see [Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).</span></span>  
  
 <span data-ttu-id="0e3dc-112">이 항목의 내용:</span><span class="sxs-lookup"><span data-stu-id="0e3dc-112">In this topic:</span></span>  
  
-   [<span data-ttu-id="0e3dc-113">보고서 서버 및 파워 뷰 통합 사이트 모음 기능을 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="0e3dc-113">To Activate the Report Server and Power View Integration Site Collection Features:</span></span>](#bkmk_features)  
  
-   [<span data-ttu-id="0e3dc-114">사이트 모음에서 Reporting Services 중앙 관리 사이트 모음 기능을 활성화 또는 비활성화하려면</span><span class="sxs-lookup"><span data-stu-id="0e3dc-114">To Activate or Deactivate Reporting Services Central Administration Site Collection Feature:</span></span>](#bkmk_centraladmin)  
  
##  <a name="to-activate-the-report-server-and-power-view-integration-site-collection-features"></a><a name="bkmk_features"></a><span data-ttu-id="0e3dc-115">보고서 서버 및 파워 뷰 통합 사이트 모음 기능을 활성화 하려면:</span><span class="sxs-lookup"><span data-stu-id="0e3dc-115">To Activate the Report Server and Power View Integration Site Collection Features:</span></span>  
  
1.  <span data-ttu-id="0e3dc-116">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능을 활성화하려는 사이트로 브라우저를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-116">Open your browser to the site where you want the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features active.</span></span>  
  
2.  <span data-ttu-id="0e3dc-117">**사이트 작업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-117">Click **Site Actions**.</span></span>  
  
3.  <span data-ttu-id="0e3dc-118">**사이트 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-118">Click **Site Settings**.</span></span>  
  
4.  <span data-ttu-id="0e3dc-119">사이트 모음 관리 그룹에서 **사이트 모음 기능** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-119">Click **Site Collection Features** in the Site Collection Administration Group.</span></span>  
  
5.  <span data-ttu-id="0e3dc-120">목록에서 **보고서 통합 기능** 이나 **파워 뷰 통합 기능** 을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-120">Find **Report Server Integration Feature** or **Power View Integration Feature** in the list.</span></span>  
  
6.  <span data-ttu-id="0e3dc-121">**활성화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-121">Click **Activate**.</span></span>  
  
 <span data-ttu-id="0e3dc-122">기능을 비활성화하려면 동일한 절차를 수행하고 **활성화** 대신 **비활성화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-122">To deactivate the features, you can use the same procedure, but click **Deactivate** rather than **Activate.**</span></span>  
  
##  <a name="to-activate-or-deactivate-reporting-services-central-administration-site-collection-feature"></a><a name="bkmk_centraladmin"></a><span data-ttu-id="0e3dc-123">Reporting Services 중앙 관리 사이트 모음 기능을 활성화 하거나 비활성화 하려면:</span><span class="sxs-lookup"><span data-stu-id="0e3dc-123">To Activate or Deactivate Reporting Services Central Administration Site Collection Feature:</span></span>  
  
1.  <span data-ttu-id="0e3dc-124">SharePoint 중앙 관리로 브라우저를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-124">Open your browser to SharePoint Central Administration.</span></span>  
  
2.  <span data-ttu-id="0e3dc-125">**사이트 작업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-125">Click **Site Actions**.</span></span>  
  
3.  <span data-ttu-id="0e3dc-126">**사이트 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-126">Click **Site Settings**.</span></span>  
  
4.  <span data-ttu-id="0e3dc-127">사이트 모음 관리 그룹에서 **사이트 모음 기능** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-127">Click **Site Collection Features** in the Site Collection Administration Group.</span></span>  
  
5.  <span data-ttu-id="0e3dc-128">목록에서 **보고서 서버 중앙 관리 기능** 을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-128">Find **Report Server Central Administration Feature** in the list.</span></span>  
  
6.  <span data-ttu-id="0e3dc-129">**활성화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-129">Click **Activate**.</span></span>  
  
 <span data-ttu-id="0e3dc-130">기능을 비활성화하려면 동일한 절차를 따르면서 **활성화** 대신 **비활성화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-130">To deactivate the feature, you can use the same procedure, but click **Deactivate** rather than **Activate.**</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0e3dc-131">다음 단계</span><span class="sxs-lookup"><span data-stu-id="0e3dc-131">Next Steps</span></span>  
 <span data-ttu-id="0e3dc-132">기능이 활성화된 후에는 계속해서 서버 통합을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e3dc-132">After the feature is activated, you can continue with server integration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e3dc-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e3dc-133">See Also</span></span>  
 [<span data-ttu-id="0e3dc-134">Sharepoint 2010 및 SharePoint 2013 &#40;Reporting Services 추가 기능을 설치 하거나 제거&#41;</span><span class="sxs-lookup"><span data-stu-id="0e3dc-134">Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
