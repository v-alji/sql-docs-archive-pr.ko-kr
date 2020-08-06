---
title: 보고서 관리자 URL (SSRS 기본 모드) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.rsconfigtool.reportmanagervirtualdirectory.f1
ms.assetid: 45768952-23a6-45a5-b541-e7bf192b4a78
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ec43c91bb2d24bb96cc6541d93311ce6dd234ed4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652555"
---
# <a name="report-manager-url-ssrs-native-mode"></a><span data-ttu-id="7d2d8-102">보고서 관리자 URL(SSRS 기본 모드)</span><span class="sxs-lookup"><span data-stu-id="7d2d8-102">Report Manager URL (SSRS Native Mode)</span></span>
  <span data-ttu-id="7d2d8-103">보고서 관리자 URL 페이지를 사용하여 보고서 관리자에 액세스하는 데 사용되는 URL을 구성하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2d8-103">Use the Report Manager URL page to configure or modify the URL used to access Report Manager.</span></span> <span data-ttu-id="7d2d8-104">기본적으로 보고서 관리자 URL은 보고서 서버 웹 서비스 URL의 접두사, IP 주소 및 포트를 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2d8-104">By default, the Report Manager URL inherits the prefix, IP address, and port of the Report Server Web service URL.</span></span> <span data-ttu-id="7d2d8-105">보고서 관리자가 동일한 보고서 서버 서비스 내에서 실행되는 웹 서비스에 대한 프런트 엔드 액세스를 제공하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="7d2d8-105">This is because Report Manager provides front-end access to the Web service that runs within the same Report Server service.</span></span> <span data-ttu-id="7d2d8-106">서비스 애플리케이션을 격리하고 보고서 관리자를 사용하여 다른 컴퓨터의 보고서 서버 웹 서비스에 액세스하는 경우 보고서 관리자가 다른 인스턴스를 가리키도록 RSReportServer.config 파일을 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2d8-106">If you are isolating the service applications and using Report Manager to access a Report Server Web service on a different computer, you must edit RSReportServer.config file to point Report Manager to a different instance.</span></span> <span data-ttu-id="7d2d8-107">원격 보고서 서버에 대 한 보고서 관리자 연결을 구성 하는 방법에 대 한 자세한 내용은 [Reporting Services 구성 관리자 &#40;기본 모드&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7d2d8-107">For more information about configuring a Report Manager connection to a remote report server, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="7d2d8-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="7d2d8-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="7d2d8-109">SharePoint 통합 모드로 실행되도록 보고서 서버를 구성하는 경우에는 보고서 관리자 URL을 만들지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="7d2d8-109">If you are configuring the report server to run in SharePoint integrated mode, do not create a Report Manager URL.</span></span> <span data-ttu-id="7d2d8-110">SharePoint 통합 모드에서 실행되는 보고서 서버에서는 보고서 관리자가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2d8-110">Report Manager is not supported on a report server that runs in SharePoint integrated mode.</span></span> <span data-ttu-id="7d2d8-111">보고서 관리자에 대한 URL이 이미 있는 경우 SharePoint 통합 모드에서 실행되도록 보고서 서버를 구성한 후에는 이 URL을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2d8-111">If a URL already exists for Report Manager, it will become unavailable after you configure the report server to run in SharePoint integrated mode.</span></span>  
  
 <span data-ttu-id="7d2d8-112">이 페이지를 열려면 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자를 시작하고 탐색 창에서 **보고서 관리자 URL** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2d8-112">To open this page, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and click **Report Manager URL** in the navigation pane.</span></span> <span data-ttu-id="7d2d8-113">Configuration Manager를 시작 하는 방법에 대 한 자세한 내용은 [Reporting Services 구성 관리자 &#40;기본 모드&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7d2d8-113">For more information about how to start the Configuration Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7d2d8-114">보고서 관리자가 활성화되어 있지 않으면 이 페이지에서 옵션을 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2d8-114">If Report Manager is not enabled, you cannot set options on this page.</span></span> <span data-ttu-id="7d2d8-115">보고서 관리자 사용에 대 한 자세한 내용은 [Reporting Services 구성 관리자 &#40;기본 모드&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7d2d8-115">For more information about enabling Report Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7d2d8-116">옵션</span><span class="sxs-lookup"><span data-stu-id="7d2d8-116">Options</span></span>  
 <span data-ttu-id="7d2d8-117">**가상 디렉터리**</span><span class="sxs-lookup"><span data-stu-id="7d2d8-117">**Virtual Directory**</span></span>  
 <span data-ttu-id="7d2d8-118">보고서 관리자의 가상 디렉터리 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2d8-118">Specifies the virtual directory name for Report Manager.</span></span> <span data-ttu-id="7d2d8-119">같은 컴퓨터의 각 보고서 관리자 인스턴스에 대해 가상 디렉터리 이름은 하나만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d2d8-119">You can only have one virtual directory name for each Report Manager instance on the same computer.</span></span>  
  
 <span data-ttu-id="7d2d8-120">**URL**</span><span class="sxs-lookup"><span data-stu-id="7d2d8-120">**URLs**</span></span>  
 <span data-ttu-id="7d2d8-121">현재 보고서 관리자 인스턴스에 정의된 URL을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2d8-121">Displays the URL defined for the current Report Manager instance.</span></span>  
  
 <span data-ttu-id="7d2d8-122">**고급**</span><span class="sxs-lookup"><span data-stu-id="7d2d8-122">**Advanced**</span></span>  
 <span data-ttu-id="7d2d8-123">현재 보고서 관리자 인스턴스에 대해 다른 URL을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7d2d8-123">Add an additional URL for the current Report Manager instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d2d8-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7d2d8-124">See Also</span></span>  
 <span data-ttu-id="7d2d8-125">[SSRS Configuration Manager &#40;URL 구성&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="7d2d8-125">[Configure a URL  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="7d2d8-126">[구성 파일의 Url &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="7d2d8-126">[URLs in Configuration Files  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="7d2d8-127">보고서 서버 URL 구성&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="7d2d8-127">Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
