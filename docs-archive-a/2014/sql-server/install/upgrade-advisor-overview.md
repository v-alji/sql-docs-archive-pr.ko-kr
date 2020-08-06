---
title: 업그레이드 관리자 개요 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Report Viewer
- SQL Server Upgrade Advisor, components
- tools [Upgrade Advisor]
- Upgrade Advisor [SQL Server], components
- components [Upgrade Advisor]
- Upgrade Advisor Analysis Wizard
- limitations [Upgrade Advisor]
- analyzing system [Upgrade Advisor]
- analyzing system [Upgrade Advisor], about analysis
ms.assetid: f5c56f63-4478-40af-abb9-642f58a0026c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 6d787f41eba97314986ec77df4cfcff580ae9915
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650413"
---
# <a name="upgrade-advisor-overview"></a><span data-ttu-id="c82c7-102">업그레이드 관리자 개요</span><span class="sxs-lookup"><span data-stu-id="c82c7-102">Upgrade Advisor Overview</span></span>
  <span data-ttu-id="c82c7-103">업그레이드 관리자는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 및 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 구성 요소를 분석하고 분석 결과에 대한 정보가 포함된 보고서를 볼 수 있는 중앙 콘솔을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-103">Upgrade Advisor provides a central console to analyze [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], and [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] components, and to view reports that contain information about the results of the analysis.</span></span>  
  
## <a name="how-upgrade-advisor-works"></a><span data-ttu-id="c82c7-104">업그레이드 관리자 작동 방식</span><span class="sxs-lookup"><span data-stu-id="c82c7-104">How Upgrade Advisor Works</span></span>  
 <span data-ttu-id="c82c7-105">업그레이드 관리자를 실행하면 업그레이드 관리자 시작 페이지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-105">When you run Upgrade Advisor, the Upgrade Advisor start page appears.</span></span> <span data-ttu-id="c82c7-106">업그레이드 관리자 시작 페이지에서 다음을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-106">The Upgrade Advisor start page is the launching point for the following:</span></span>  
  
-   <span data-ttu-id="c82c7-107">업그레이드 관리자 분석 마법사</span><span class="sxs-lookup"><span data-stu-id="c82c7-107">Upgrade Advisor Analysis Wizard</span></span>  
  
-   <span data-ttu-id="c82c7-108">업그레이드 관리자 보고서 뷰어</span><span class="sxs-lookup"><span data-stu-id="c82c7-108">Upgrade Advisor Report Viewer</span></span>  
  
-   <span data-ttu-id="c82c7-109">업그레이드 관리자 도움말</span><span class="sxs-lookup"><span data-stu-id="c82c7-109">Upgrade Advisor Help</span></span>  
  
 <span data-ttu-id="c82c7-110">처음 업그레이드 관리자를 사용할 때 업그레이드 관리자 분석 마법사를 실행하여 서버를 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-110">The first time that you use Upgrade Advisor, run the Upgrade Advisor Analysis Wizard to analyze a server.</span></span> <span data-ttu-id="c82c7-111">마법사가 분석을 완료 하면 마법사에서 **보고서 시작** 을 클릭 하거나 업그레이드 관리자 시작 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-111">When the wizard completes the analysis, click **Launch Report** from the wizard or return to the Upgrade Advisor start page.</span></span> <span data-ttu-id="c82c7-112">그런 다음 업그레이드 관리자 보고서 뷰어를 실행하여 보고서를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-112">From there, run the Upgrade Advisor Report Viewer to view the report.</span></span> <span data-ttu-id="c82c7-113">보고서는 알려진 문제를 해결하는 데 도움이 되는 정보에 대한 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-113">The report provides links to information that will help you resolve known issues.</span></span>  
  
## <a name="upgrade-advisor-analysis-wizard"></a><span data-ttu-id="c82c7-114">업그레이드 관리자 분석 마법사</span><span class="sxs-lookup"><span data-stu-id="c82c7-114">Upgrade Advisor Analysis Wizard</span></span>  
 <span data-ttu-id="c82c7-115">분석을 수행 하려면 업그레이드 관리자 시작 페이지에서 **업그레이드 관리자 분석 마법사 시작** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-115">To perform an analysis, click **Launch Upgrade Advisor Analysis Wizard** on the Upgrade Advisor start page.</span></span> <span data-ttu-id="c82c7-116">업그레이드 관리자 분석 마법사는 컴퓨터, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소 및 분석할 추적 파일에 대한 정보를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-116">The Upgrade Advisor Analysis Wizard gathers information about the computer, instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components, and trace files that you want to analyze.</span></span> <span data-ttu-id="c82c7-117">모든 정보가 수집되고 확인되고 나면 업그레이드 관리자 분석 마법사는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소를 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-117">After all the information has been gathered and confirmed, the Upgrade Advisor Analysis Wizard analyzes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c82c7-118">업그레이드 관리자 분석 마법사를 실행할 때마다 별도의 보고서가 생성되고 선택한 구성 요소에 대한 기존 보고서는 덮어쓰여지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-118">Each time you run the Upgrade Advisor Analysis Wizard, a separate report is generated, and existing reports for the selected components are not overwritten.</span></span> <span data-ttu-id="c82c7-119">그러나 보고서 뷰어에는 가장 최근의 다섯 개 보고서만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-119">However, the report viewer displays only the five latest reports.</span></span>  
  
 <span data-ttu-id="c82c7-120">업그레이드 관리자 분석 마법사는 분석 작업을 마치면 분석에 포함된 각 구성 요소에 대해 XML 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-120">When the Upgrade Advisor Analysis Wizard finishes its analysis, it creates an XML file for each component that you have included in the analysis.</span></span> <span data-ttu-id="c82c7-121">XML 파일에는 각 구성 요소에서 발견된 항목 및 문제가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-121">The XML files contain the items and issues discovered in each component.</span></span>  
  
### <a name="what-upgrade-advisor-analyzes"></a><span data-ttu-id="c82c7-122">업그레이드 관리자의 분석 대상</span><span class="sxs-lookup"><span data-stu-id="c82c7-122">What Upgrade Advisor Analyzes</span></span>  
 <span data-ttu-id="c82c7-123">각 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소에 대해 업그레이드 관리자의 컨텍스트에서 전용 분석기가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-123">A dedicated analyzer runs in the context of Upgrade Advisor for each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component.</span></span> <span data-ttu-id="c82c7-124">각 분석기의 출력은 해당 구성 요소에 대한 XML 보고서입니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-124">The output of each analyzer is an XML report for that component.</span></span>  
  
 <span data-ttu-id="c82c7-125">업그레이드 관리자는 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-125">Upgrade Advisor queries the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components:</span></span>  
  
-   <span data-ttu-id="c82c7-126">복제, [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에이전트, 전체 텍스트 검색 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client가 포함된 데이터베이스 서버([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]이라고도 함)</span><span class="sxs-lookup"><span data-stu-id="c82c7-126">Database Server (also referred to as the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online), which includes Replication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, Full-Text Search, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="c82c7-127">분석 중에 각 분석기는 로그 파일을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-127">During analysis, each analyzer creates a log file.</span></span> <span data-ttu-id="c82c7-128">이러한 로그 파일을 사용하여 분석 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-128">You can use these log files to troubleshoot the analysis.</span></span> <span data-ttu-id="c82c7-129">예를 들어 업그레이드 관리자의 실행 속도가 느린 경우 로그 파일을 통해 속도 지연의 원인을 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-129">For example, if Upgrade Advisor is running slowly, you can view the log files to determine the cause of the delay.</span></span>  
  
### <a name="upgrade-advisor-limitations"></a><span data-ttu-id="c82c7-130">업그레이드 관리자 제한 사항</span><span class="sxs-lookup"><span data-stu-id="c82c7-130">Upgrade Advisor Limitations</span></span>  
 <span data-ttu-id="c82c7-131">업그레이드 관리자는 업그레이드에 영향을 미칠 수 있는 문제를 모두 검색하지는 못합니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-131">Upgrade Advisor cannot detect every issue that might affect an upgrade.</span></span> <span data-ttu-id="c82c7-132">예를 들어 최종 사용자 데스크톱에서 실행되는 클라이언트 애플리케이션에 SQL 코드를 삽입한 경우 업그레이드 관리자는 이 애플리케이션을 분석할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-132">For example, if you have embedded SQL code in a client application that runs on end-user desktops, it will not be possible for Upgrade Advisor to analyze the applications.</span></span> <span data-ttu-id="c82c7-133">이러한 항목에 대해서도 문제를 고려하여 각자 설치 기반의 필요에 따라 정보를 업그레이드, 마이그레이션 또는 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-133">For these items, you still must consider the issues and upgrade, migrate, or modify the information as required in your installation.</span></span>  
  
 <span data-ttu-id="c82c7-134">업그레이드 관리자는 암호화된 저장 프로시저, 확장 저장 프로시저의 코드, 그리고 [!INCLUDE[tsql](../../includes/tsql-md.md)] 이외의 다른 언어로 된 소스 코드를 분석하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-134">Upgrade Advisor does not analyze encrypted stored procedures, code in extended stored procedures, and source code in languages other than [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
## <a name="upgrade-advisor-report-viewer"></a><span data-ttu-id="c82c7-135">업그레이드 관리자 보고서 뷰어</span><span class="sxs-lookup"><span data-stu-id="c82c7-135">Upgrade Advisor Report Viewer</span></span>  
 <span data-ttu-id="c82c7-136">업그레이드 관리자 보고서를 보려면 업그레이드 관리자 시작 페이지에서 **업그레이드 관리자 보고서 뷰어 시작** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-136">To view an Upgrade Advisor report, click **Launch Upgrade Advisor Report Viewer** on the Upgrade Advisor start page.</span></span> <span data-ttu-id="c82c7-137">업그레이드 관리자 보고서 뷰어를 시작하면 기본 디렉터리의 보고서가 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-137">When the Upgrade Advisor Report Viewer starts, the reports in the default directory are loaded.</span></span> <span data-ttu-id="c82c7-138">업그레이드 관리자 보고서 뷰어가 기본 디렉터리에서 보고서를 찾지 못한 경우 보고서는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-138">Reports are not displayed if the Upgrade Advisor Report Viewer does not find any reports in the default directory.</span></span> <span data-ttu-id="c82c7-139">기본 디렉터리에 보고서가 없는 경우에는 업그레이드 관리자 분석 마법사를 실행하여 보고서를 작성하거나 다른 서버 또는 하위 디렉터리에서 기존 보고서를 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-139">If there are no reports in the default directory, you can either run the Upgrade Advisor Analysis Wizard to create a report or load an existing report from another server or from a subdirectory.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="c82c7-140">업그레이드 관리자는 기존 보고서를 덮어쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-140">Upgrade Advisor does not overwrite existing reports.</span></span> <span data-ttu-id="c82c7-141">그러나 보고서 뷰어에는 가장 최근의 다섯 개 보고서만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-141">However, the report viewer displays only the five latest reports.</span></span> <span data-ttu-id="c82c7-142">이전 보고서를 보려면 **보고서** 드롭다운 목록 상자에서 보고서를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-142">To view an earlier report, select the report from the **Report** drop-down list box.</span></span> <span data-ttu-id="c82c7-143">타임스탬프는 보고서가 생성된 날짜와 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-143">The timestamp indicates the date and time the report was generated.</span></span>  
  
 <span data-ttu-id="c82c7-144">업그레이드 관리자 분석 마법사를 통해 작성된 XML 파일이 업그레이드 관리자 보고서 뷰어에 로드되면 각 구성 요소에 대한 보고서가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-144">When XML files from the Upgrade Advisor Analysis Wizard are loaded into the Upgrade Advisor Report Viewer, a report for each component is displayed.</span></span> <span data-ttu-id="c82c7-145">이 보고서에는 처리해야 할 모든 알려진 문제가 포함됩니다(검색 가능한 문제와 검색 불가능한 문제 모두).</span><span class="sxs-lookup"><span data-stu-id="c82c7-145">The report contains all the known issues, both detectable and undetectable, that you need to address.</span></span> <span data-ttu-id="c82c7-146">각 문제에는 중요도를 나타내는 아이콘, 문제를 처리해야 하는 시기를 알려 주는 레이블, 그리고 간단한 설명이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-146">For each issue there is an icon indicating importance, a label informing you when the issue must be fixed, and a short description.</span></span> <span data-ttu-id="c82c7-147">문제를 확장하면 보다 자세한 설명, 문제 세부 정보로 연결되는 링크, 도움말 파일로 연결되는 링크가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-147">When you expand an issue, you will see a longer description, a link to issue details, and a link to the Help file.</span></span> <span data-ttu-id="c82c7-148">각 문제에 대한 정보는 문제 해결을 위해 필요한 정보를 충분히 제공하도록 고안되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-148">The information for each issue is designed to provide enough information for you to fix the issue.</span></span>  
  
 <span data-ttu-id="c82c7-149">대부분의 구성 요소에는 검색되지 않는 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-149">Most components have issues that cannot be detected.</span></span> <span data-ttu-id="c82c7-150">이러한 문제를 보려면 해당 구성 요소에 대 한 **기타 업그레이드 문제** 항목을 확장 한 다음 링크를 클릭 하 여 설명서의 문제에 대 한 추가 정보를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c82c7-150">To view these issues, expand the **Other Upgrade Issues** item for the component, and then click the link to view additional information about the issues in the documentation.</span></span> <span data-ttu-id="c82c7-151">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이전 버전과의 호환성 문제에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c82c7-151">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backward compatibility issues, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c82c7-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c82c7-152">See Also</span></span>  
 [<span data-ttu-id="c82c7-153">업그레이드 관리자 작업</span><span class="sxs-lookup"><span data-stu-id="c82c7-153">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
