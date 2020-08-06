---
title: 업그레이드 문제 Reporting Services (업그레이드 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], upgrade issues
- Reporting Services, upgrades
- upgrading Reporting Services
- report servers [Reporting Services], upgrade issues
ms.assetid: d9663f25-98d7-4508-ae3c-55a7277211bd
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 569afe735d68a724c0b4cc61ad2b7767088c2b30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660859"
---
# <a name="reporting-services-upgrade-issues-upgrade-advisor"></a><span data-ttu-id="8aeb4-102">Reporting Services 업그레이드 문제(업그레이드 관리자)</span><span class="sxs-lookup"><span data-stu-id="8aeb4-102">Reporting Services Upgrade Issues (Upgrade Advisor)</span></span>
  <span data-ttu-id="8aeb4-103">다음 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 로의 업그레이드에 영향을 줄 수 있는 문제에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8aeb4-103">The following topics describe the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] issues that might affect your upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="8aeb4-104">이러한 변화가 환경에 미치는 영향을 완화하기 위해 취할 수 있는 조치에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8aeb4-104">The topics describe actions that you can take to mitigate the effect of these changes on your environment.</span></span>  
  
 <span data-ttu-id="8aeb4-105">업그레이드 관리자는 보고서 서버 설치를 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="8aeb4-105">Upgrade Advisor analyzes a report server installation.</span></span> <span data-ttu-id="8aeb4-106">보고서 디자이너가 컴퓨터에 설치된 유일한 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 요소인 경우와 같이 클라이언트 구성 요소만 설치된 경우에는 문제가 보고되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8aeb4-106">If only client components are installed (for example, if Report Designer is the only [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] component installed on the computer), no issues will be reported.</span></span>  
  
 <span data-ttu-id="8aeb4-107">설치를 구성한 방법에 따라 업그레이드 관리자가 보고하지 않는 추가적인 문제가 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aeb4-107">Depending on how you configured your installation, you may encounter additional issues that are not reported by Upgrade Advisor.</span></span> <span data-ttu-id="8aeb4-108">이러한 문제는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 업그레이드를 방해하지 않지만 업그레이드가 완료된 후 보고서와 애플리케이션이 실행되는 방법에는 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aeb4-108">These issues do not prevent a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] upgrade from succeeding, but they may affect how reports and applications run after an upgrade is finished.</span></span> <span data-ttu-id="8aeb4-109">이러한 문제에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 "Reporting Services의 이전 버전과의 호환성"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8aeb4-109">To learn about these issues, see "Reporting Services Backward Compatibility" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="8aeb4-110">설치 프로그램을 사용하여 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치를 업그레이드할 수 없는 경우에는 새 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스를 설치하고 기존 설치를 새 인스턴스로 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aeb4-110">If you cannot use Setup to upgrade a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation, you can install a new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance and migrate your existing installation to the new instance.</span></span> <span data-ttu-id="8aeb4-111">자세한 내용은 온라인 설명서의 "업그레이드 및 마이그레이션 Reporting Services"을 참조 하십시오 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [Reporting Services 업그레이드 및 마이그레이션](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8aeb4-111">For more information, see "Upgrade and Migrate Reporting Services" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online, [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).</span></span>  
  
 <span data-ttu-id="8aeb4-112">다음 항목에서는 업그레이드 관리자가 보고하는 알려진 문제에 대해 설명하고 업그레이드를 성공적으로 수행하기 위해 기존 설치를 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8aeb4-112">The following topics describe known issues that are reported by Upgrade Advisor, and explain how you can modify your existing installation to allow an upgrade to occur.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8aeb4-113">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스를 분석하려면 보고서 서버에 업그레이드 관리자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8aeb4-113">Upgrade Advisor must be installed on the report server to analyze an instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="8aeb4-114">는 원격 분석을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8aeb4-114">does not support remote analysis.</span></span>  
>   
>  <span data-ttu-id="8aeb4-115">자세한 내용은 [업그레이드 관리자 설치](../../../2014/sql-server/install/installing-upgrade-advisor.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8aeb4-115">For more information, see [Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8aeb4-116">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="8aeb4-116">In This Section</span></span>  
  
-   [<span data-ttu-id="8aeb4-117">보고서 서버 웹 사이트의 클라이언트 인증서 &#40;업그레이드 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="8aeb4-117">Client certificates on the report server web site &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/client-certificates-on-the-report-server-web-site-upgrade-advisor.md)  
  
-   [<span data-ttu-id="8aeb4-118">보고서 서버 &#40;업그레이드 관리자에서 사용자 지정 확장 프로그램이 검색 되었습니다&#41;</span><span class="sxs-lookup"><span data-stu-id="8aeb4-118">Custom extensions were detected on the report server &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/custom-extensions-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [<span data-ttu-id="8aeb4-119">보고서 서버 &#40;업그레이드 관리자에서 사용자 지정 보고서 항목이 검색 되었습니다&#41;</span><span class="sxs-lookup"><span data-stu-id="8aeb4-119">Custom report items were detected on the report server &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/custom-report-items-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [<span data-ttu-id="8aeb4-120">업그레이드 관리자 &#40;IIS 이전 버전과의 호환성 구성 요소가 검색 되지 않았습니다&#41;</span><span class="sxs-lookup"><span data-stu-id="8aeb4-120">IIS backward compatibility components were not detected &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/iis-backward-compatibility-components-were-not-detected-upgrade-advisor.md)  
  
-   [<span data-ttu-id="8aeb4-121">업그레이드 관리자 &#40;IP 주소 제한이 검색 되었습니다&#41;</span><span class="sxs-lookup"><span data-stu-id="8aeb4-121">IP address restriction detected &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/ip-address-restriction-detected-upgrade-advisor.md)  
  
-   [<span data-ttu-id="8aeb4-122">보고서 서버 사이트 &#40;업그레이드 관리자에서 ISAPI 필터를 검색 했습니다&#41;</span><span class="sxs-lookup"><span data-stu-id="8aeb4-122">ISAPI filters detected on the report server site &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/isapi-filters-detected-on-the-report-server-site-upgrade-advisor.md)  
  
-   [<span data-ttu-id="8aeb4-123">업그레이드 관리자 &#40;보고서 서버 컴퓨터에서 사용 되지 않는 확장이 검색 되었습니다&#41;</span><span class="sxs-lookup"><span data-stu-id="8aeb4-123">Obsolete extensions were detected on the report server computer &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor.md)  
  
-   [<span data-ttu-id="8aeb4-124">업그레이드 관리자 &#40;보고서 서버 데이터베이스가 구성 되어 있지 않습니다&#41;</span><span class="sxs-lookup"><span data-stu-id="8aeb4-124">Report server database is not configured &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/report-server-database-is-not-configured-upgrade-advisor.md)  
  
-   [<span data-ttu-id="8aeb4-125">SQL Server 2005 보고서 서버 웹 서비스 그룹이 업그레이드 관리자 &#40;검색 되었습니다&#41;</span><span class="sxs-lookup"><span data-stu-id="8aeb4-125">SQL Server 2005 Report Server Web Service group detected &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/sql-server-2005-report-server-web-service-group-detected-upgrade-advisor.md)  
  
-   [<span data-ttu-id="8aeb4-126">업그레이드 관리자 &#40;가상 디렉터리가 지정 되지 않았습니다&#41;</span><span class="sxs-lookup"><span data-stu-id="8aeb4-126">Virtual directories are unspecified &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/virtual-directories-are-unspecified-upgrade-advisor.md)  
  
-   [<span data-ttu-id="8aeb4-127">가상 디렉터리에 업그레이드 관리자 &#40;지원 되지 않는 인증 방법이 있습니다&#41;</span><span class="sxs-lookup"><span data-stu-id="8aeb4-127">Virtual directory has unsupported authentication method &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/virtual-directory-has-unsupported-authentication-method-upgrade-advisor.md)  
  
-   [<span data-ttu-id="8aeb4-128">SQL Server Standard 및 Enterprise &#40;업그레이드 관리자의 CPU 및 메모리 제한에 대 한 변경&#41;</span><span class="sxs-lookup"><span data-stu-id="8aeb4-128">Changes to CPU and memory limits for SQL Server Standard and Enterprise &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/cpu-memory-limits-changes-sql-server-standard-enterprise-upgrade-advisor.md)  
  
-   [<span data-ttu-id="8aeb4-129">SharePoint 팜 &#40;업그레이드 관리자에 필요한 도메인 계정&#41;</span><span class="sxs-lookup"><span data-stu-id="8aeb4-129">Domain accounts required for SharePoint farm &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/domain-accounts-required-for-sharepoint-farm-upgrade-advisor.md)  
  
-   [<span data-ttu-id="8aeb4-130">보고서 서버 &#40;업그레이드 관리자에 게 직접 탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="8aeb4-130">Direct Browsing to Report Server &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/direct-browsing-to-report-server-upgrade-advisor.md)  
  
-   [<span data-ttu-id="8aeb4-131">Microsoft SharePoint 2007은 업그레이드 관리자 &#40;설치 됩니다&#41;</span><span class="sxs-lookup"><span data-stu-id="8aeb4-131">Microsoft SharePoint 2007 is Installed &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/microsoft-sharepoint-2007-is-installed-upgrade-advisor.md)  
  
-   [<span data-ttu-id="8aeb4-132">Microsoft SQL Server Reporting Services SharePoint 공유 서비스가 &#40;업그레이드 관리자와 함께 설치 됩니다&#41;</span><span class="sxs-lookup"><span data-stu-id="8aeb4-132">Microsoft SQL Server Reporting Services SharePoint Shared Service is Installed Side by Side &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/sql-server-reporting-services-sharepoint-shared-service-side-by-side-upgrade-advisor.md)  
  
-   [<span data-ttu-id="8aeb4-133">업그레이드 관리자 &#40;데이터베이스 엔진 서버 데이터 정렬이 호환 되지 않습니다&#41;</span><span class="sxs-lookup"><span data-stu-id="8aeb4-133">Incompatible Database Engine Server Collation &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/incompatible-database-engine-server-collation-upgrade-advisor.md)  
  
-   [<span data-ttu-id="8aeb4-134">기타 Reporting Services 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="8aeb4-134">Other Reporting Services Upgrade Issues</span></span>](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md)  
  
  
