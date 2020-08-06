---
title: 보고서 서버 구성 및 관리(SSRS 기본 모드) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, components
- deploying [Reporting Services], component options
- report servers [Reporting Services], component options
- configuration options [Reporting Services]
- administering Reporting Services
- components [Reporting Services], configuring
- configuring servers [Reporting Services]
ms.assetid: cfec012b-56f1-4346-9814-247acf22351c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5164fd2f9170cb092a45394f64f06d7622253f2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652594"
---
# <a name="configure-and-administer-a-report-server-ssrs-native-mode"></a><span data-ttu-id="50c3b-102">보고서 서버 구성 및 관리(SSRS 기본 모드)</span><span class="sxs-lookup"><span data-stu-id="50c3b-102">Configure and Administer a Report Server (SSRS Native Mode)</span></span>
  <span data-ttu-id="50c3b-103">이 항목에서는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 구성하는 데 사용할 수 있는 방식을 요약하여 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="50c3b-103">This topic summarizes the approaches that you can use to configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="50c3b-104">또한 여기에는 특정 구성 요소, 기능 또는 서버 기능의 구성 방법을 설명하는 항목의 목록도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50c3b-104">It also includes a list of topics that explain how to configure specific components, features, or server capabilities.</span></span> <span data-ttu-id="50c3b-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 구성하기 위해 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50c3b-105">To configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can:</span></span>  
  
-   <span data-ttu-id="50c3b-106">Reporting Services 구성 관리자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50c3b-106">Use the Reporting Services Configuration Manager.</span></span> <span data-ttu-id="50c3b-107">이 섹션에서 대부분의 항목은 이 도구를 통해 특정 기능을 구성하는 방법에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="50c3b-107">Many of the topics in this section contain information about how to configure specific features through this tool.</span></span>  
  
-   <span data-ttu-id="50c3b-108">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 사용하여 서버 속성 사용자 지정, 내 보고서 활성화, 추적 로그 활성화 및 사이트 전체 기본값 설정을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50c3b-108">Use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to customize server properties, enable My Reports, enable trace logs, and set site-wide defaults.</span></span> <span data-ttu-id="50c3b-109">사이트 설정에 대한 자세한 내용은 Management Studio의 [Reporting Services 보고서 서버&#40;기본 모드&#41;](reporting-services-report-server-native-mode.md) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50c3b-109">For more information about site settings, see [Reporting Services Report Server &#40;Native Mode&#41;](reporting-services-report-server-native-mode.md) for Management Studio.</span></span> <span data-ttu-id="50c3b-110">서버 속성을 프로그래밍 방식으로 설정하는 스크립트를 만들고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50c3b-110">Note that you can create and run script that sets server properties programmatically.</span></span> <span data-ttu-id="50c3b-111">자세한 내용은 [배포 및 관리 태스크 스크립팅](../tools/script-deployment-and-administrative-tasks.md) 및 [보고서 서버 시스템 속성](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50c3b-111">For more information, see [Script Deployment and Administrative Tasks](../tools/script-deployment-and-administrative-tasks.md) and [Report Server System Properties](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md).</span></span>  
  
-   <span data-ttu-id="50c3b-112">보고서 관리자를 사용하여 보고서 서버에 액세스하는 사용 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50c3b-112">Use Report Manager to grant permissions to access the report server.</span></span> <span data-ttu-id="50c3b-113">사용 권한은 각 사용자 또는 그룹 계정에 대해 정의하는 역할 할당을 통해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="50c3b-113">Permissions are conveyed through role assignments that you define for each user or group account.</span></span> <span data-ttu-id="50c3b-114">자세한 내용은 [역할 및 사용 권한&#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50c3b-114">For more information, see [Roles and Permissions &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md).</span></span>  
  
-   <span data-ttu-id="50c3b-115">필요에 따라 구성 파일을 수정하여 애플리케이션 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50c3b-115">Optionally, modify configuration files to change application settings.</span></span> <span data-ttu-id="50c3b-116">각 파일에 대한 자세한 내용과 해당 파일의 수정 지침은 [Reporting Services Configuration Files](reporting-services-configuration-files.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="50c3b-116">For more information about each file and guidelines for modifying them, see [Reporting Services Configuration Files](reporting-services-configuration-files.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="50c3b-117">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="50c3b-117">In This Section</span></span>  
 [<span data-ttu-id="50c3b-118">보고서 서버 URL 구성&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="50c3b-118">Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
 <span data-ttu-id="50c3b-119">보고서 서버 및 보고서 관리자에 액세스하는 데 사용하는 URL을 정의하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="50c3b-119">Describes how to define the URLs used to access the report server and Report Manager.</span></span>  
  
 [<span data-ttu-id="50c3b-120">보고서 서버 서비스 계정 구성&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="50c3b-120">Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
 <span data-ttu-id="50c3b-121">서비스 계정 및 암호를 수정하는 방법에 대한 권장 사항과 단계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="50c3b-121">Provides recommendations and steps on how to modify service account and password.</span></span>  
  
 [<span data-ttu-id="50c3b-122">보고서 서버 데이터베이스 만들기&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="50c3b-122">Create a Report Server Database  &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
 <span data-ttu-id="50c3b-123">서버 메타데이터 및 개체를 저장하는 데 필요한 보고서 서버 데이터베이스를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="50c3b-123">Describes how to create a report server database, required for storing server metadata and objects.</span></span>  
  
 [<span data-ttu-id="50c3b-124">보고서 서버 데이터베이스 연결 구성&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="50c3b-124">Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
 <span data-ttu-id="50c3b-125">보고서 서버에서 보고서 서버 데이터베이스에 연결하는 데 사용하는 연결 문자열을 수정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="50c3b-125">Describes how to modify the connection string used by the report server to connect to the report server database.</span></span>  
  
 [<span data-ttu-id="50c3b-126">SSRS Configuration Manager &#40;전자 메일 배달에 대 한 보고서 서버 구성&#41;</span><span class="sxs-lookup"><span data-stu-id="50c3b-126">Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 <span data-ttu-id="50c3b-127">전자 메일 보고서 배포를 지원하도록 보고서 서버를 구성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="50c3b-127">Describes how to configure a report server to support e-mail report distribution.</span></span>  
  
 [<span data-ttu-id="50c3b-128">무인 실행 계정 구성&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="50c3b-128">Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
 <span data-ttu-id="50c3b-129">보고서를 무인 모드로 처리하는 데 필요한 사용자 계정을 구성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="50c3b-129">Describes how to configure a user account to process reports in unattended mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c3b-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50c3b-130">See Also</span></span>  
 <span data-ttu-id="50c3b-131">[보고서 작성기 액세스 구성](configure-report-builder-access.md) </span><span class="sxs-lookup"><span data-stu-id="50c3b-131">[Configure Report Builder Access](configure-report-builder-access.md) </span></span>  
 <span data-ttu-id="50c3b-132">[Reporting Services 구성 파일](reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="50c3b-132">[Reporting Services Configuration Files](reporting-services-configuration-files.md) </span></span>  
 <span data-ttu-id="50c3b-133">[Reporting Services 구성 관리자&#40;기본 모드&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="50c3b-133">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="50c3b-134">[Reporting Services 보안 및 보호](../security/reporting-services-security-and-protection.md) </span><span class="sxs-lookup"><span data-stu-id="50c3b-134">[Reporting Services Security and Protection](../security/reporting-services-security-and-protection.md) </span></span>  
 [<span data-ttu-id="50c3b-135">Reporting Services 보고서 서버&#40;기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="50c3b-135">Reporting Services Report Server &#40;Native Mode&#41;</span></span>](reporting-services-report-server-native-mode.md)  
  
  
