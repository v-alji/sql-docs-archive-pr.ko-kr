---
title: 서버 속성(일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.general.f1
ms.assetid: 23537d52-4356-450f-a671-5921cef2431f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 66199e35c180790cba5120cb839be67e43052be6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742827"
---
# <a name="server-properties-general-page"></a><span data-ttu-id="3c3e5-102">서버 속성(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="3c3e5-102">Server Properties (General Page)</span></span>
  <span data-ttu-id="3c3e5-103">이 페이지를 사용하여 보고서 관리자에 사용된 제목을 보거나 수정하고, 내 보고서를 설정 또는 해제하고, 내 보고서의 보안에 대한 역할 정의를 선택하고 클라이언트 인쇄 컨트롤을 설정 또는 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-103">Use this page to view or modify the title used in Report Manager, enable or disable My Reports, select a role definition for My Reports security, and enable or disable the client print control.</span></span>  
  
 <span data-ttu-id="3c3e5-104">이 페이지를 열려면를 시작 하 고 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 보고서 서버 인스턴스에 연결한 다음 보고서 서버 이름을 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-104">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server instance, right-click the report server name, and then select **Properties**.</span></span>  
  
 <span data-ttu-id="3c3e5-105">서버 모드에 따라 설정할 수 있는 서버 속성이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-105">The server mode determines which server properties you can set.</span></span> <span data-ttu-id="3c3e5-106">SharePoint 통합 모드로 구성된 보고서 서버를 관리하는 경우 내 보고서를 활성화하거나 보고서 관리자에 대한 애플리케이션 제목을 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-106">If you are managing a report server that is configured for SharePoint integrated mode, you cannot enable My Reports or set the application title for Report Manager.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3c3e5-107">옵션</span><span class="sxs-lookup"><span data-stu-id="3c3e5-107">Options</span></span>  
 <span data-ttu-id="3c3e5-108">**이름**</span><span class="sxs-lookup"><span data-stu-id="3c3e5-108">**Name**</span></span>  
 <span data-ttu-id="3c3e5-109">보고서 관리자에 표시될 애플리케이션 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-109">Type an application name that appears in Report Manager.</span></span> <span data-ttu-id="3c3e5-110">기본적으로이 값은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 입니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-110">By default, this value is [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="3c3e5-111">지정한 이름은 보고서 관리자에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-111">The name that you specify appears only in Report Manager.</span></span>  
  
 <span data-ttu-id="3c3e5-112">**Version**</span><span class="sxs-lookup"><span data-stu-id="3c3e5-112">**Version**</span></span>  
 <span data-ttu-id="3c3e5-113">이 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-113">This property is read-only.</span></span> <span data-ttu-id="3c3e5-114">사용 중인의 버전을 지정 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3c3e5-114">Specifies the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] that you are using.</span></span>  
  
 <span data-ttu-id="3c3e5-115">**버전**</span><span class="sxs-lookup"><span data-stu-id="3c3e5-115">**Edition**</span></span>  
 <span data-ttu-id="3c3e5-116">이 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-116">This property is read-only.</span></span> <span data-ttu-id="3c3e5-117">현재 보고서 서버 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-117">Specifies the current report server instance.</span></span> <span data-ttu-id="3c3e5-118">일부 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서는 보고서 관리자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-118">Report Manager is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3c3e5-119">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-119">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="3c3e5-120">**인증 모드**</span><span class="sxs-lookup"><span data-stu-id="3c3e5-120">**Authentication Mode**</span></span>  
 <span data-ttu-id="3c3e5-121">이 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-121">This property is read-only.</span></span> <span data-ttu-id="3c3e5-122">보고서 서버 인스턴스에서 허용되는 인증 요청의 유형을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-122">It identifies the types of authentication requests accepted by the report server instance.</span></span> <span data-ttu-id="3c3e5-123">인증 모드를 변경하려면 RSReportServer.config 파일을 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-123">To change the authentication mode, you must edit the RSReportServer.config file.</span></span> <span data-ttu-id="3c3e5-124">자세한 내용은 [Authentication with the Report Server](../security/authentication-with-the-report-server.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-124">For more information, see [Authentication with the Report Server](../security/authentication-with-the-report-server.md).</span></span>  
  
 <span data-ttu-id="3c3e5-125">**URL**</span><span class="sxs-lookup"><span data-stu-id="3c3e5-125">**URL**</span></span>  
 <span data-ttu-id="3c3e5-126">이 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-126">This property is read-only.</span></span> <span data-ttu-id="3c3e5-127">보고서 서버 웹 서비스에 대한 URL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-127">Specifies the URL to the Report Server Web service.</span></span> <span data-ttu-id="3c3e5-128">이 값은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-128">This value is specified in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span> <span data-ttu-id="3c3e5-129">자세한 내용은 [URL 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-129">For more information, see [Configure a URL  &#40;SSRS Configuration Manager&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="3c3e5-130">**각 사용자에 대해 내 보고서 폴더 설정**</span><span class="sxs-lookup"><span data-stu-id="3c3e5-130">**Enable a My Reports folder for each user**</span></span>  
 <span data-ttu-id="3c3e5-131">사용자가 내 보고서를 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-131">Make My Reports available to users.</span></span> <span data-ttu-id="3c3e5-132">이 옵션은 기본 모드 보고서 서버에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-132">This option is only available for native mode report servers.</span></span>  
  
 <span data-ttu-id="3c3e5-133">**각 내 보고서 폴더에 적용할 역할을 선택하십시오.**</span><span class="sxs-lookup"><span data-stu-id="3c3e5-133">**Select the role to apply to each My Reports folder**</span></span>  
 <span data-ttu-id="3c3e5-134">내 보고서의 보안에 사용할 역할 정의를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-134">Specify a role definition to use for My Reports security.</span></span> <span data-ttu-id="3c3e5-135">역할 정의는 각 내 보고서 폴더에서 지원되는 태스크 집합을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-135">The role definition identifies the set of tasks that are supported in each My Reports folder.</span></span>  
  
 <span data-ttu-id="3c3e5-136">**ActiveX 클라이언트 인쇄 컨트롤에 대한 다운로드 설정**</span><span class="sxs-lookup"><span data-stu-id="3c3e5-136">**Enable download for the ActiveX client print control**</span></span>  
 <span data-ttu-id="3c3e5-137">`EnableClientPrinting` 보고서 서버 시스템 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-137">Sets the `EnableClientPrinting` report server system property.</span></span> <span data-ttu-id="3c3e5-138">클라이언트 인쇄를 설정하는 경우 로컬 관리자 권한을 가진 사용자는 HTML 보고서 인쇄를 위한 서명된 ActiveX 컨트롤을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-138">If you enable client printing, users who have local administrator permissions have the option of downloading a signed ActiveX control for printing HTML reports.</span></span> <span data-ttu-id="3c3e5-139">자세한 내용은 [Reporting Services에 대한 클라이언트 쪽 인쇄 기능 설정 및 해제](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c3e5-139">For more information, see [Enable and Disable Client-Side Printing for Reporting Services](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c3e5-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c3e5-140">See Also</span></span>  
 <span data-ttu-id="3c3e5-141">[보고서 서버 속성 &#40;Management Studio&#41;설정](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="3c3e5-141">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="3c3e5-142">[Management Studio에서 보고서 서버에 연결](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="3c3e5-142">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="3c3e5-143">[내 보고서 사용 및 사용 안 함](../report-server/enable-and-disable-my-reports.md) </span><span class="sxs-lookup"><span data-stu-id="3c3e5-143">[Enable and Disable My Reports](../report-server/enable-and-disable-my-reports.md) </span></span>  
 <span data-ttu-id="3c3e5-144">[Management Studio F1 도움말의 보고서 서버](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="3c3e5-144">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="3c3e5-145">내 보고서 보안 설정</span><span class="sxs-lookup"><span data-stu-id="3c3e5-145">Secure My Reports</span></span>](../security/secure-my-reports.md)  
  
  
