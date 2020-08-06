---
title: SQL Server 2014의 SQL Server Reporting Services에 대 한 동작 변경 내용 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- rows [Reporting Services], heights
- leading blanks
- installing Reporting Services, behavior changes with release
- cryptography [Reporting Services]
- Setup [Reporting Services], behavior changes with release
- DefaultValueQueryBased property
- encryption [Reporting Services]
- decryption [Reporting Services]
- blank characters [SQL Server]
- initializing installations [Reporting Services]
- behavior changes [Reporting Services]
ms.assetid: 2a767f0f-84f2-4099-8784-1e37790f858e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 966447192c492a907f0b506ae21befd513b2fcfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648336"
---
# <a name="behavior-changes-to-sql-server-reporting-services--in-sql-server-2014"></a><span data-ttu-id="fb393-102">SQL Server 2014에서 SQL Server Reporting Services의 동작 변경 내용</span><span class="sxs-lookup"><span data-stu-id="fb393-102">Behavior Changes to SQL Server Reporting Services  in SQL Server 2014</span></span>
  <span data-ttu-id="fb393-103">이 항목에서는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]의 동작 변경 내용에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-103">This topic describes behavior changes in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="fb393-104">동작 변경 내용은 이전 버전의 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 와 비교해서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 기능이 작동하고 상호 작용하는 방법에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-104">Behavior changes affect how features work or interact in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] as compared to previous versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="fb393-105">이 항목의 내용:</span><span class="sxs-lookup"><span data-stu-id="fb393-105">In this topic:</span></span>  
  
-   [<span data-ttu-id="fb393-106">SQL Server 2014 Reporting Services 동작 변경</span><span class="sxs-lookup"><span data-stu-id="fb393-106">SQL Server 2014 Reporting Services Behavior Changes</span></span>](#bkmk_sql14)  
  
-   [<span data-ttu-id="fb393-107">SQL Server 2012 Reporting Services 동작 변경 내용</span><span class="sxs-lookup"><span data-stu-id="fb393-107">SQL Server 2012 Reporting Services Behavior Changes</span></span>](#bkmk_rc0)  
  
-   [<span data-ttu-id="fb393-108">SQL Server 2008 R2 Reporting Services의 동작 변경 내용</span><span class="sxs-lookup"><span data-stu-id="fb393-108">SQL Server 2008 R2 Reporting Services Behavior Changes</span></span>](#bkmk_kj)  
  
##  <a name="sssql14-reporting-services-behavior-changes"></a><a name="bkmk_sql14"></a><span data-ttu-id="fb393-109">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]Reporting Services 동작 변경 내용</span><span class="sxs-lookup"><span data-stu-id="fb393-109">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services Behavior Changes</span></span>  
 <span data-ttu-id="fb393-110">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 에서 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]기능에는 동작 변경 내용이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-110">There are no [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] behavior changes in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>  
  
##  <a name="sssql11-reporting-services-behavior-changes"></a><a name="bkmk_rc0"></a><span data-ttu-id="fb393-111">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]Reporting Services 동작 변경 내용</span><span class="sxs-lookup"><span data-stu-id="fb393-111">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services Behavior Changes</span></span>  
 <span data-ttu-id="fb393-112">이 섹션에서는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 모드의 동작 변경 내용에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-112">This section describes behavior changes to [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>  
  
### <a name="view-items-permission-will-not-download-shared-datasets-sharepoint-mode"></a><span data-ttu-id="fb393-113">항목 보기 권한으로 공유 데이터 세트 다운로드 불가(SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="fb393-113">View Items permission will not download Shared Datasets (SharePoint Mode)</span></span>  
 <span data-ttu-id="fb393-114">**새 동작:** SharePoint "항목 보기" 권한이 있는 사용자는 더 이상 Reporting Services 공유 데이터 집합의 콘텐츠를 다운로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-114">**New Behavior:** Users with the SharePoint permission of "View Items" can no longer download the contents of Reporting Services shared datasets.</span></span> <span data-ttu-id="fb393-115">이 동작 변경은 이제 보고서, 데이터 원본 및 모델에 대 한 "항목 보기" 권한과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-115">This behavior change is now consistent with the "View Items" permissions for reports, data sources, and models.</span></span> <span data-ttu-id="fb393-116">"항목 보기" 권한이 있는 사용자는 보고서, 데이터 원본 및 모델을 보고 실행할 수 있지만 해당 콘텐츠를 다운로드할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-116">Users with "View Items" permission can view and execute reports, data sources, and models but they cannot download their content.</span></span>  
  
 <span data-ttu-id="fb393-117">**이전 동작:** "항목 보기" SharePoint 권한이 있는 사용자는 공유 데이터 집합 Reporting Services의 콘텐츠를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-117">**Previous Behavior:** Users with the "View Items" SharePoint permission could download the contents of Reporting Services shared datasets.</span></span>  
  
 <span data-ttu-id="fb393-118">SharePoint 권한 수준에 대한 자세한 내용은 [사용자 권한 및 사용 권한 수준](https://technet.microsoft.com/library/cc721640.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb393-118">For more information on SharePoint permission levels, see [User permissions and permission levels](https://technet.microsoft.com/library/cc721640.aspx)</span></span>  
  
### <a name="report-server-trace-logs-are-in-a-new-location-for-sharepoint-mode-sharepoint-mode"></a><span data-ttu-id="fb393-119">SharePoint 모드에서 보고서 서버 추적 로그가 새 위치에 있음(SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="fb393-119">Report Server trace logs are in a new location for SharePoint mode (SharePoint Mode)</span></span>  
 <span data-ttu-id="fb393-120">**새 동작:** SharePoint 모드로 설치 된 보고서 서버의 경우 보고서 서버 추적 로그 는%Programfiles%\Common Files\Microsoft Shared\Web Server Extensions\14\Web Services\reportserver\logfiles 아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-120">**New behavior:** For a report server installed in SharePoint mode, the report server trace logs will be under %Programfiles%\Common Files\Microsoft Shared\Web Server Extensions\14\Web Services\ReportServer\LogFiles.</span></span>  
  
 <span data-ttu-id="fb393-121">**이전 동작:** 보고서 서버 추적 로그는 다음과 유사한 경로 아래에 있습니다 .%Programfilesdir%\Microsoft SQL Server \\<RS_instance> \Reporting Services\LogFiles</span><span class="sxs-lookup"><span data-stu-id="fb393-121">**Previous Behavior:** Report Server trace logs were found under a path similar to the following:  %Programfilesdir%\Microsoft SQL Server\\<RS_instance>\Reporting Services\LogFiles</span></span>  
  
### <a name="getserverconfiginfo-soap-api-is-no-longer-supported-sharepoint-mode"></a><span data-ttu-id="fb393-122">GetServerConfigInfo SOAP API가 더 이상 지원되지 않음(SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="fb393-122">GetServerConfigInfo SOAP API is no longer supported (SharePoint Mode)</span></span>  
 <span data-ttu-id="fb393-123">**새 동작**: PowerShell Cmdlet "get-sprsserviceapplicationservers"를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-123">**New behavior**: Use PowerShell cmdlet "Get-SPRSServiceApplicationServers"</span></span>  
  
 <span data-ttu-id="fb393-124">**이전 동작:** 고객은 끝점에서 직접 통신 하 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 고 GetReportServerConfigInfo ()를 호출 하는 SOAP 클라이언트 코드를 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-124">**Previous Behavior:** Customers could develop SOAP client code to communicate directly with the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] end point, and call GetReportServerConfigInfo().</span></span>  
  
### <a name="report-server-configuration-and-management-tools"></a><span data-ttu-id="fb393-125">보고서 서버 구성 및 관리 도구</span><span class="sxs-lookup"><span data-stu-id="fb393-125">Report Server Configuration and Management Tools</span></span>  
  
#### <a name="configuration-manager-is-not-used-for-sharepoint-mode"></a><span data-ttu-id="fb393-126">구성 관리자가 SharePoint 모드에서 사용되지 않음</span><span class="sxs-lookup"><span data-stu-id="fb393-126">Configuration Manager is not used for SharePoint Mode</span></span>  
 <span data-ttu-id="fb393-127">**새 동작:**[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 구성 관리자가 더 이상 SharePoint 모드 보고서 서버를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-127">**New behavior:** The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager no longer supports SharePoint Mode report servers.</span></span> <span data-ttu-id="fb393-128">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 모드 구성을 이제 SharePoint 중앙 관리를 사용하여 완료할 수 있으므로 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 구성 관리자가 더 이상 SharePoint 모드를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-128">Configuration of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode can now be completed by using SharePoint Central administration and therefore [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager no longer supports SharePoint mode.</span></span> <span data-ttu-id="fb393-129">구성 관리자는 이제 기본 모드 보고서 서버에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-129">Configuration Manager is now only used for Native mode report servers.</span></span>  
  
#### <a name="you-cannot-change-the-server-from-one-mode-to-another"></a><span data-ttu-id="fb393-130">서버를 한 모드에서 다른 모드로 변경할 수 없음</span><span class="sxs-lookup"><span data-stu-id="fb393-130">You cannot change the server from one mode to another</span></span>  
 <span data-ttu-id="fb393-131">**새 동작:** 서버 모드를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-131">**New behavior:** You cannot change server modes.</span></span> <span data-ttu-id="fb393-132">보고서 서버를 기본 모드로 설치하는 경우 이것을 SharePoint 모드로 변경하거나 다시 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-132">If you install a report server as Native mode you cannot change or re-configure it to be SharePoint mode.</span></span> <span data-ttu-id="fb393-133">SharePoint 모드로 설치하는 경우 보고서 서버를 기본 모드로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-133">If you install in SharePoint mode, you can change the report server to native mode.</span></span>  
  
 <span data-ttu-id="fb393-134">**이전 동작:** 고객이 SharePoint 모드로 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서 서버를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-134">**Previous Behavior:** Customer installs a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server in SharePoint mode.</span></span> <span data-ttu-id="fb393-135">고객이 보고서 서버를 기본 모드로 전환하려는 경우 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 구성 관리자를 열어 새 기본 모드 데이터베이스를 만들거나 기존 기본 모드 데이터베이스에 연결하여 기본 모드로 전환할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-135">If the customer wants to switch the report server to Native mode, they could open the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] configuration manager to switch to Native mode by either creating a new or connecting to an existing Native mode database.</span></span> <span data-ttu-id="fb393-136">또한 고객은 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 구성 관리자를 사용하여 SharePoint 모드에서 기본 모드로 전환할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-136">The customer could also use [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager to switch from SharePoint mode to Native mode.</span></span>  
  
##  <a name="sql-server-2008-r2-reporting-services-behavior-changes"></a><a name="bkmk_kj"></a><span data-ttu-id="fb393-137">SQL Server 2008 R2 Reporting Services 동작 변경 내용</span><span class="sxs-lookup"><span data-stu-id="fb393-137">SQL Server 2008 R2 Reporting Services Behavior Changes</span></span>  
 <span data-ttu-id="fb393-138">이 섹션에서는의 동작 변경 내용에 대해 설명 합니다 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fb393-138">This section describes behavior changes in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb393-139">SQL Server 2008 R2는 SQL Server 2008의 부 버전 업그레이드이므로 SQL Server 2008 섹션의 내용도 검토하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-139">Because SQL Server 2008 R2 is a minor version upgrade of SQL Server 2008, we recommend that you also review the content in the SQL Server 2008 section.</span></span>  
  
### <a name="secureconnectionlevel-property-in-the-reporting-services-wmi-provider-library"></a><span data-ttu-id="fb393-140">Reporting Services WMI 공급자 라이브러리의 SecureConnectionLevel 속성</span><span class="sxs-lookup"><span data-stu-id="fb393-140">SecureConnectionLevel Property in the Reporting Services WMI Provider Library</span></span>  
 <span data-ttu-id="fb393-141">의 WMI 공급자 라이브러리에서 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] **secureconnectionlevel** 속성은 모든 웹 서비스 메서드에 ssl `0` (Secure Socket Layer)이 필요 하지 않음을 나타내는,,, 및 값을 사용 하 여 `1` `2` `3` `0` `3` 모든 웹 서비스 메서드에 ssl이 필요 함을 나타내고 `1` 및는 ssl이 `2` 필요한 웹 서비스 메서드의 하위 집합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-141">In the WMI provider library for [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], the **SecureConnectionLevel** property allows values of `0`,`1`,`2`,`3`, with `0` indicating that Secure Socket Layer (SSL) is not required for any of the Web service methods, `3` indicating that SSL is required for all the Web service methods, and `1` and `2` indicate subsets of Web service methods that require SSL.</span></span> <span data-ttu-id="fb393-142">에서 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 이러한 값은 두 가지 의미를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-142">In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], these values will have only two possible meanings:</span></span>  
  
-   <span data-ttu-id="fb393-143">`0`은 웹 서비스에 메서드에 SSL이 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-143">`0` indicates SSL is not required for any of the Web service methods.</span></span>  
  
-   <span data-ttu-id="fb393-144">양의 정수는 모든 웹 서비스에 메서드에 SSL이 필요함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-144">A positive integer indicates SSL is required for all the Web service methods.</span></span>  
  
 <span data-ttu-id="fb393-145">이 변경 내용은 보고서 서버에서 웹 서비스 호출에 응답하는 방식을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="fb393-145">This change affects how the report server responds to Web service calls.</span></span> <span data-ttu-id="fb393-146">예를 들어는 <xref:ReportService2005.ReportingService2005.ListSecureMethods%2A> 이제 **secureconnectionlevel** 이 0으로 설정 된 경우 아무것도 반환 하지 않으며 <xref:ReportService2005.ReportingService2005> **secureconnectionlevel** 이, 또는로 설정 된 경우에는 모든 메서드를 반환 합니다 `1` `2` `3` .</span><span class="sxs-lookup"><span data-stu-id="fb393-146">For example, <xref:ReportService2005.ReportingService2005.ListSecureMethods%2A> now returns nothing if **SecureConnectionLevel** is set to 0 and all the methods in <xref:ReportService2005.ReportingService2005> if **SecureConnectionLevel** is set to `1`, `2`, or `3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb393-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fb393-147">See Also</span></span>  
 <span data-ttu-id="fb393-148">[새로운 기능 &#40;Reporting Services&#41;](what-s-new-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="fb393-148">[What's New &#40;Reporting Services&#41;](what-s-new-reporting-services.md) </span></span>  
 <span data-ttu-id="fb393-149">[SQL Server 2014의 SQL Server Reporting Services에서 사용 되지 않는 기능](deprecated-features-in-sql-server-reporting-services-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fb393-149">[Deprecated Features in SQL Server Reporting Services in SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md) </span></span>  
 <span data-ttu-id="fb393-150">[SQL Server 2014의 SQL Server Reporting Services에 대해 지원 되지 않는 기능](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fb393-150">[Discontinued Functionality to SQL Server Reporting Services in SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md) </span></span>  
 [<span data-ttu-id="fb393-151">SQL Server 2014에서 SQL Server Reporting Services의 주요 변경 내용</span><span class="sxs-lookup"><span data-stu-id="fb393-151">Breaking Changes in SQL Server Reporting Services in SQL Server 2014</span></span>](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)  
  
  
