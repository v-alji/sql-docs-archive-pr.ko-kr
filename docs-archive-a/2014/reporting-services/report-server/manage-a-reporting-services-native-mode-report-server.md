---
title: Reporting Services 기본 모드 보고서 서버 관리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Configuration tool
- configuration options [Reporting Services]
- report servers [Reporting Services], configuring
ms.assetid: 6ca03a09-d6a8-4c93-ba12-1c99dcbfb618
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0d44a9329074a20c04f878c055674ea563b297f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652574"
---
# <a name="manage-a-reporting-services-native-mode-report-server"></a><span data-ttu-id="15caf-102">Reporting Services 기본 모드 보고서 서버 관리</span><span class="sxs-lookup"><span data-stu-id="15caf-102">Manage a Reporting Services Native Mode Report Server</span></span>
  <span data-ttu-id="15caf-103">이 섹션에서는 Reporting Services 구성 관리자를 사용하여 기본 모드 보고서 서버 인스턴스를 구성하는 절차를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="15caf-103">This section contains procedures for configuring a native mode report server instance using the Reporting Services Configuration Manager.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15caf-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="15caf-104">In This Section</span></span>  
 <span data-ttu-id="15caf-105">이 섹션의 항목은 필요한 지침을 쉽게 찾을 수 있도록 범주로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15caf-105">The topics in this section are organized into categories so that you can more easily find the instructions you want.</span></span> <span data-ttu-id="15caf-106">첫 번째 섹션에는 기본 모드 보고서 서버의 기본 구성 태스크에 대한 항목,</span><span class="sxs-lookup"><span data-stu-id="15caf-106">The first section contains topics for basic configuration tasks for a native mode report server.</span></span> <span data-ttu-id="15caf-107">두 번째 섹션에는 고급 구성 항목이 포함되어 있고</span><span class="sxs-lookup"><span data-stu-id="15caf-107">The second section contains advanced configuration topics.</span></span> <span data-ttu-id="15caf-108">세 번째 섹션에는 SharePoint 통합 모드에서 실행되도록 보고서 서버를 구성하는 방법에 대한 항목이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15caf-108">The third section contains topics for configuring a report server to run in SharePoint integrated mode.</span></span>  
  
### <a name="basic-configuration"></a><span data-ttu-id="15caf-109">기본 구성</span><span class="sxs-lookup"><span data-stu-id="15caf-109">Basic Configuration</span></span>  
 [<span data-ttu-id="15caf-110">Reporting Services 구성 관리자&#40;기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="15caf-110">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
 <span data-ttu-id="15caf-111">Reporting Services 구성 도구를 시작하는 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15caf-111">Provides steps for starting the Reporting Services Configuration tool.</span></span>  
  
 [<span data-ttu-id="15caf-112">서비스 계정 구성&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="15caf-112">Configure a Service Account &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)  
 <span data-ttu-id="15caf-113">보고서 서버 서비스에 대한 계정 및 암호 정보를 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15caf-113">Explains how to specify account and password information for the Report Server service.</span></span>  
  
 [<span data-ttu-id="15caf-114">보고서 서버의 SPN&#40;서비스 사용자 이름&#41; 등록</span><span class="sxs-lookup"><span data-stu-id="15caf-114">Register a Service Principal Name &#40;SPN&#41; for a Report Server</span></span>](register-a-service-principal-name-spn-for-a-report-server.md)  
 <span data-ttu-id="15caf-115">Kerberos 인증을 사용하는 네트워크에서 도메인 사용자 계정으로 실행되는 보고서 서버의 SPN을 수동으로 등록하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15caf-115">Explains how to manually register an SPN for a report server that runs under a domain user account on a network that uses Kerberos authentication.</span></span>  
  
 [<span data-ttu-id="15caf-116">URL 구성&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="15caf-116">Configure a URL  &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-a-url-ssrs-configuration-manager.md)  
 <span data-ttu-id="15caf-117">보고서 서버 웹 서비스 및 보고서 관리자에 액세스하는 데 사용되는 하나 이상의 URL을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15caf-117">Explains how to establish one or more URLs used to access the Report Server Web service and Report Manager.</span></span>  
  
 [<span data-ttu-id="15caf-118">기본 모드 보고서 서버 데이터베이스 만들기&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="15caf-118">Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)  
 <span data-ttu-id="15caf-119">보고서 서버 데이터베이스를 만드는 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15caf-119">Provides steps for creating a report server database.</span></span> <span data-ttu-id="15caf-120">이 단계는 Reporting Services 설치를 배포하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="15caf-120">This step is required for deploying a Reporting Services installation.</span></span>  
  
### <a name="advanced-or-optional-configuration"></a><span data-ttu-id="15caf-121">고급 또는 선택 사항 구성</span><span class="sxs-lookup"><span data-stu-id="15caf-121">Advanced or Optional Configuration</span></span>  
 [<span data-ttu-id="15caf-122">기본 모드 보고서 서버 확장 배포 구성&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="15caf-122">Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
 <span data-ttu-id="15caf-123">여러 보고서 서버에서 보고서 서버 데이터베이스를 공유하도록 구성하는 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15caf-123">Provides steps for configuring multiple report servers to share a report server database.</span></span>  
  
 [<span data-ttu-id="15caf-124">SSRS Configuration Manager &#40;전자 메일 배달에 대 한 보고서 서버 구성&#41;</span><span class="sxs-lookup"><span data-stu-id="15caf-124">Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 <span data-ttu-id="15caf-125">전자 메일 배포를 위한 보고서 서버를 구성하는 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15caf-125">Provides steps for configuring a report server for e-mail distribution.</span></span>  
  
 [<span data-ttu-id="15caf-126">보고서 서버 액세스를 위한 방화벽 구성</span><span class="sxs-lookup"><span data-stu-id="15caf-126">Configure a Firewall for Report Server Access</span></span>](configure-a-firewall-for-report-server-access.md)  
 <span data-ttu-id="15caf-127">보고서 서버의 인바운드 요청과 아웃바운드 응답에 사용되는 포트를 여는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15caf-127">Explains how to open ports used for inbound requests and outbound responses from a report server.</span></span>  
  
 [<span data-ttu-id="15caf-128">로컬 관리에 대해 기본 모드 보고서 서버 구성&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="15caf-128">Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;</span></span>](configure-a-native-mode-report-server-for-local-administration-ssrs.md)  
 <span data-ttu-id="15caf-129">http://localhost를 사용하여 보고서 서버 또는 보고서 관리자에 연결할 때 필요한 추가 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15caf-129">Describes additional steps required to connect to Report Manager or a report server using http://localhost.</span></span>  
  
 [<span data-ttu-id="15caf-130">원격 관리를 위한 보고서 서버 구성</span><span class="sxs-lookup"><span data-stu-id="15caf-130">Configure a Report Server for Remote Administration</span></span>](configure-a-report-server-for-remote-administration.md)  
 <span data-ttu-id="15caf-131">다른 컴퓨터에서 연결하여 구성할 수 있도록 원격 보고서 서버 인스턴스를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15caf-131">Explains how to configure a remote report server instance so that you can connect to and configure it from a different computer.</span></span>  
  
 [<span data-ttu-id="15caf-132">Reporting Services 기능 설정 또는 해제</span><span class="sxs-lookup"><span data-stu-id="15caf-132">Turn Reporting Services Features On or Off</span></span>](turn-reporting-services-features-on-or-off.md)  
 <span data-ttu-id="15caf-133">Reporting Services 설치에서 사용하지 않는 기능을 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15caf-133">Explains how to remove unused features in a Reporting Services installation.</span></span>  
  
 [<span data-ttu-id="15caf-134">원격 오류 활성화&#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="15caf-134">Enable Remote Errors &#40;Reporting Services&#41;</span></span>](enable-remote-errors-reporting-services.md)  
 <span data-ttu-id="15caf-135">원격 서버에서 발생하는 오류 조건에 대한 추가 정보를 반환하도록 보고서 서버에 대한 서버 속성을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15caf-135">Explains how to set server properties on a report server to return additional information about error conditions that occur on remote servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15caf-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15caf-136">See Also</span></span>  
 <span data-ttu-id="15caf-137">[보고서 서버 구성 및 관리&#40;SSRS 기본 모드&#41;](configure-and-administer-a-report-server-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="15caf-137">[Configure and Administer a Report Server &#40;SSRS Native Mode&#41;](configure-and-administer-a-report-server-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="15caf-138">보고서 서버의 구성 및 관리&#40;Reporting Services SharePoint 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="15caf-138">Configuration and Administration of a Report Server &#40;Reporting Services SharePoint Mode&#41;</span></span>](../configure-administer-report-server-reporting-services-sharepoint-mode.md)  
  
  
