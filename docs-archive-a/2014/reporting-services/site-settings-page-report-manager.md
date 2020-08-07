---
title: 사이트 설정 페이지 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4d67a01c-eae4-49ba-a6e8-8e983c0248f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 75805a4e30293195b23cd5b75f1de3a01a1e76d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731395"
---
# <a name="site-settings-page-report-manager"></a><span data-ttu-id="1005e-102">사이트 설정 페이지(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="1005e-102">Site Settings Page (Report Manager)</span></span>
  <span data-ttu-id="1005e-103">사이트 설정 페이지를 사용하여 애플리케이션 제목을 변경하고 보고서 기록 제한 및 보고서 처리 시간 제한 값에 대한 서버 차원 기본값을 설정하고 시스템 수준 역할 할당을 관리하고 공유 일정을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-103">Use the Site Settings page to change the application title, set server-wide defaults for report history limits and report processing timeout values, manage system-level role assignments, and manage shared schedules.</span></span> <span data-ttu-id="1005e-104">이 페이지를 보려면 내용 관리자 및 시스템 관리자 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-104">You must have Content Manager and System Administrator permissions to view this page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1005e-105">일부 SQL Server 버전에서 보고서 기록, 보고서 실행 및 공유 일정 기능은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-105">The following features are not available in every edition of SQL Server: report history, report execution, and shared schedules.</span></span> <span data-ttu-id="1005e-106">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1005e-106">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="1005e-107">탐색</span><span class="sxs-lookup"><span data-stu-id="1005e-107">Navigation</span></span>  
 <span data-ttu-id="1005e-108">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="1005e-108">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-site-settings-page"></a><span data-ttu-id="1005e-109">사이트 설정 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="1005e-109">To open the Site Settings page</span></span>  
  
1.  <span data-ttu-id="1005e-110">보고서 관리자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-110">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="1005e-111">페이지의 맨 위에서 **사이트 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-111">At the top of the page, click **Site Settings**.</span></span> <span data-ttu-id="1005e-112">사이트의 일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-112">This opens the General Properties page of the site.</span></span>  
  
     <span data-ttu-id="1005e-113">**참고:** 메뉴에 **사이트 설정** 옵션이 표시 되지 않는 경우 필요한 권한이 없는 것입니다. 자세한 내용은 [로컬 관리를 위한 기본 모드 보고서 서버 구성 &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)의 "사이트 설정" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1005e-113">**Note:** If you do not see the **Site Settings** option in the menu, you do not have the required permissions, For more information see the "site settings" section of [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1005e-114">옵션</span><span class="sxs-lookup"><span data-stu-id="1005e-114">Options</span></span>  
 <span data-ttu-id="1005e-115">**이름**</span><span class="sxs-lookup"><span data-stu-id="1005e-115">**Name**</span></span>  
 <span data-ttu-id="1005e-116">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 보고서 관리자의 이 인스턴스에 사용할 제목을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-116">Specify the title to use for this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Report Manager.</span></span> <span data-ttu-id="1005e-117">기본적으로 제목은 " [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] "입니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-117">By default, the title is "[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]".</span></span>  
  
 <span data-ttu-id="1005e-118">**보고서 기록의 기본 설정 선택**</span><span class="sxs-lookup"><span data-stu-id="1005e-118">**Select the default settings for report history**</span></span>  
 <span data-ttu-id="1005e-119">보관할 보고서 기록 복사본 수로 기본값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-119">Select a default value for the number of copies of report history to retain.</span></span> <span data-ttu-id="1005e-120">이 기본값은 보고서 기록 제한을 설정하는 초기 설정이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-120">The default value provides an initial setting that establishes report history limits.</span></span> <span data-ttu-id="1005e-121">보고서 수준에서 이 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-121">You can vary these settings at the report level.</span></span> <span data-ttu-id="1005e-122">자세한 내용은 [스냅샷 옵션 속성 페이지&#40;보고서 관리자&#41;](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1005e-122">For more information, see [Snapshot Options Properties Page &#40;Report Manager&#41;](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="1005e-123">나중에 보고서 기록을 제한하면 기존 보고서 기록이 지정한 제한을 초과하는 경우 보고서 서버에서 기존 보고서 기록을 새 제한으로 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-123">If you limit report history later, when the existing report history exceeds the limit you specify, the report server reduces the existing report history to the new limit.</span></span> <span data-ttu-id="1005e-124">가장 오래된 보고서 스냅샷이 먼저 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-124">The oldest report snapshots are deleted first.</span></span> <span data-ttu-id="1005e-125">보고서 기록이 비어 있거나 제한보다 적은 경우 새 보고서 스냅샷이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-125">If report history is empty or below the limit, new report snapshots are added.</span></span> <span data-ttu-id="1005e-126">한도에 이르면 새 보고서 스냅샷이 추가될 때 가장 오래된 스냅샷이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-126">When the limit is reached, the oldest snapshot is deleted when a new report snapshot is added.</span></span>  
  
 <span data-ttu-id="1005e-127">**보고서 실행 제한 시간**</span><span class="sxs-lookup"><span data-stu-id="1005e-127">**Report Execution Timeout**</span></span>  
 <span data-ttu-id="1005e-128">보고서 처리를 일정 시간(초)으로 제한할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-128">Specify whether report processing times out after a certain number of seconds.</span></span>  
  
 <span data-ttu-id="1005e-129">이 값은 보고서 서버의 보고서 처리에 적용되며,</span><span class="sxs-lookup"><span data-stu-id="1005e-129">This value applies to report processing on a report server.</span></span> <span data-ttu-id="1005e-130">사용자의 보고서에 데이터를 제공하는 데이터베이스 서버의 데이터 처리에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-130">It does not affect data processing on the database server that provides the data for your report.</span></span>  
  
 <span data-ttu-id="1005e-131">보고서 처리 시간은 보고서를 선택한 후 보고서가 열리는 데 걸리는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-131">The report processing timer clock begins when the report is selected and ends when the report opens.</span></span> <span data-ttu-id="1005e-132">이 값을 설정할 때는 데이터 처리와 보고서 처리가 모두 완료될 수 있는 시간으로 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="1005e-132">When you set this value, specify enough time to complete both data processing and report processing.</span></span>  
  
 <span data-ttu-id="1005e-133">**사용자 지정 보고서 작성기 시작 URL**</span><span class="sxs-lookup"><span data-stu-id="1005e-133">**Custom Report Builder launch URL**</span></span>  
 <span data-ttu-id="1005e-134">보고서 서버에서 기본 보고서 작성기 URL을 사용하지 않는 경우에는 사용자 지정 URL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-134">Specify a custom URL when the report server does not use the default Report Builder URL.</span></span> <span data-ttu-id="1005e-135">이 설정은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-135">This setting is optional.</span></span> <span data-ttu-id="1005e-136">값을 지정하지 않으면 기본 URL이 사용되어 보고서 작성기가 ClickOnce 애플리케이션으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-136">If you do not specify a value, the default URL will be used, which launches Report Builder as a ClickOnce application.</span></span> <span data-ttu-id="1005e-137">기본 URL은 다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-137">The default URL is one of the following:</span></span>  
  
 <span data-ttu-id="1005e-138">**기본 모드 보고서 서버:** 기본 모드 설치에서 기본 URL은 http:// \<*computername*> /reportserver/reportbuilder/ReportBuilder_3_0_0_0. 응용 프로그램의 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-138">**Native mode report server:** In a native mode installation, the default URL will take the form of http://\<*computername*>/reportserver/ReportBuilder/ReportBuilder_3_0_0_0.application.</span></span>  
  
 <span data-ttu-id="1005e-139">SharePoint 통합 모드: 기본 URL은 http:// \<*SharePoint_site*> /_vti_bin/reportbuilder/ReportBuilder_3_0_0_0. "의 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-139">SharePoint integrated mode: The default URL will take the form of http://\<*SharePoint_site*>/_vti_bin/ReportBuilder/ReportBuilder_3_0_0_0.application."</span></span>  
  
 <span data-ttu-id="1005e-140">**적용**</span><span class="sxs-lookup"><span data-stu-id="1005e-140">**Apply**</span></span>  
 <span data-ttu-id="1005e-141">변경 내용을 보고서 서버에 저장하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-141">Click to save your changes to the report server.</span></span>  
  
 <span data-ttu-id="1005e-142">**보안**</span><span class="sxs-lookup"><span data-stu-id="1005e-142">**Security**</span></span>  
 <span data-ttu-id="1005e-143">사용자 및 그룹 계정을 미리 정의된 시스템 역할에 할당할 수 있는 시스템 역할 할당 페이지를 열려면 이 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-143">Click this link to open the System Role Assignments page, on which you can assign user and group accounts to predefined system roles.</span></span>  
  
 <span data-ttu-id="1005e-144">**일정**</span><span class="sxs-lookup"><span data-stu-id="1005e-144">**Schedules**</span></span>  
 <span data-ttu-id="1005e-145">사용자가 자신의 보고서 및 구독용으로 선택 가능한 공유 일정을 미리 정의할 수 있는 일정 페이지를 열려면 이 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1005e-145">Click this link to open the Schedules page, on which you can predefine shared schedules that users can select for their reports and subscriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1005e-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1005e-146">See Also</span></span>  
 <span data-ttu-id="1005e-147">[보고서 관리자&#40;SSRS 기본 모드&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="1005e-147">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="1005e-148">[기본 모드 보고서 서버에 대한 사용 권한 부여](security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="1005e-148">[Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="1005e-149">[미리 정의 된 역할](security/role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="1005e-149">[Predefined Roles](security/role-definitions-predefined-roles.md) </span></span>  
 [<span data-ttu-id="1005e-150">보고서 관리자 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="1005e-150">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
