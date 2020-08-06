---
title: 업그레이드 관리자 실행 (사용자 인터페이스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Report Viewer
- Upgrade Advisor [SQL Server], running
- launching Upgrade Advisor
- Upgrade Advisor Analysis Wizard
- starting Upgrade Advisor
- SQL Server Upgrade Advisor, running
ms.assetid: 7f47c9b3-88d3-43d6-837e-f157b49a55ac
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a5e47ef2b8183823dff884e114adc420e371adf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660853"
---
# <a name="running-upgrade-advisor-user-interface"></a><span data-ttu-id="0147f-102">업그레이드 관리자 실행(사용자 인터페이스)</span><span class="sxs-lookup"><span data-stu-id="0147f-102">Running Upgrade Advisor (User Interface)</span></span>
  <span data-ttu-id="0147f-103">업그레이드를 계획하는 동안 업그레이드 관리자를 실행하여 로컬 또는 원격 구성 요소를 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0147f-103">You can run Upgrade Advisor to analyze local or remote components during upgrade planning.</span></span> <span data-ttu-id="0147f-104">업그레이드 관리자는 분석되는 각 구성 요소와 인스턴스에 대한 보고서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="0147f-104">Upgrade Advisor produces a report for each component and instance that is analyzed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0147f-105">업그레이드 관리자는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 원격 인스턴스를 분석하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0147f-105">Upgrade Advisor does not analyze remote instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="0147f-106">[!INCLUDE[ssRS](../../includes/ssrs.md)] 인스턴스를 분석하려면 [!INCLUDE[ssRS](../../includes/ssrs.md)]가 설치된 컴퓨터에 업그레이드 관리자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0147f-106">To analyze an instance of [!INCLUDE[ssRS](../../includes/ssrs.md)], Upgrade Advisor must be installed on the computer where [!INCLUDE[ssRS](../../includes/ssrs.md)] is installed.</span></span>  
>   
>  <span data-ttu-id="0147f-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Integration Services를 분석 하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 동일한 컴퓨터에를 설치 하 고 설치 해야 합니다 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0147f-107">To analyze [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services, you must have the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] installed and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed on the same computer.</span></span>  
  
## <a name="running-the-upgrade-advisor-analysis-wizard"></a><span data-ttu-id="0147f-108">업그레이드 관리자 분석 마법사 실행</span><span class="sxs-lookup"><span data-stu-id="0147f-108">Running the Upgrade Advisor Analysis Wizard</span></span>  
 <span data-ttu-id="0147f-109">업그레이드 관리자 분석 마법사는 다음과 같은 여섯 단계로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0147f-109">Running the Upgrade Advisor Analysis Wizard has six steps:</span></span>  
  
1.  <span data-ttu-id="0147f-110">업그레이드 관리자 시작 페이지에서 마법사를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0147f-110">Launch the wizard from the Upgrade Advisor start page.</span></span>  
  
2.  <span data-ttu-id="0147f-111">분석할 서버 및 구성 요소를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="0147f-111">Identify server and components to analyze.</span></span>  
  
3.  <span data-ttu-id="0147f-112">인증 정보를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="0147f-112">Gather authentication information.</span></span>  
  
4.  <span data-ttu-id="0147f-113">구성 요소 유형에 따라 추가 매개 변수를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="0147f-113">Gather additional parameters based on component type.</span></span>  
  
5.  <span data-ttu-id="0147f-114">선택한 구성 요소를 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="0147f-114">Analyze selected components.</span></span>  
  
6.  <span data-ttu-id="0147f-115">업그레이드 문제에 대한 보고서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="0147f-115">Generate report of upgrade issues.</span></span>  
  
 <span data-ttu-id="0147f-116">업그레이드 관리자 분석 마법사에 대 한 자세한 내용은 [방법: 업그레이드 관리자 분석 마법사 실행](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0147f-116">For more information about the Upgrade Advisor Analysis Wizard, see [How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md).</span></span>  
  
 <span data-ttu-id="0147f-117">각 단계에 필요한 특정 정보는 [업그레이드 관리자 사용자 인터페이스 참조](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0147f-117">For specific information that is required for each step, see [Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md).</span></span>  
  
## <a name="running-the-upgrade-advisor-report-viewer"></a><span data-ttu-id="0147f-118">업그레이드 관리자 보고서 뷰어 실행</span><span class="sxs-lookup"><span data-stu-id="0147f-118">Running the Upgrade Advisor Report Viewer</span></span>  
 <span data-ttu-id="0147f-119">업그레이드 관리자 분석 마법사에서 생성된 보고서를 보려면 업그레이드 관리자 보고서 뷰어를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0147f-119">You use the Upgrade Advisor Report Viewer to view reports generated by the Upgrade Advisor Analysis Wizard.</span></span> <span data-ttu-id="0147f-120">보고서가 로드되면 다음 요인을 기준으로 보고서의 구성 요소를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0147f-120">When the report is loaded, you can filter the components of the report by the following factors:</span></span>  
  
-   <span data-ttu-id="0147f-121">모든 문제</span><span class="sxs-lookup"><span data-stu-id="0147f-121">All issues</span></span>  
  
-   <span data-ttu-id="0147f-122">모든 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="0147f-122">All upgrade issues</span></span>  
  
-   <span data-ttu-id="0147f-123">업그레이드 이전 문제</span><span class="sxs-lookup"><span data-stu-id="0147f-123">Pre-upgrade issues</span></span>  
  
-   <span data-ttu-id="0147f-124">모든 마이그레이션 문제</span><span class="sxs-lookup"><span data-stu-id="0147f-124">All migration issues</span></span>  
  
-   <span data-ttu-id="0147f-125">해결된 문제</span><span class="sxs-lookup"><span data-stu-id="0147f-125">Resolved issues</span></span>  
  
-   <span data-ttu-id="0147f-126">해결되지 않은 문제</span><span class="sxs-lookup"><span data-stu-id="0147f-126">Unresolved issues</span></span>  
  
 <span data-ttu-id="0147f-127">보고서 뷰어를 사용하는 방법에 대한 단계별 지침은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0147f-127">For step-by-step instructions for using the report viewer, see the following topics:</span></span>  
  
-   [<span data-ttu-id="0147f-128">방법: 업그레이드 관리자 보고서 보기</span><span class="sxs-lookup"><span data-stu-id="0147f-128">How to: View an Upgrade Advisor Report</span></span>](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)  
  
-   [<span data-ttu-id="0147f-129">방법: 보고서 필터링</span><span class="sxs-lookup"><span data-stu-id="0147f-129">How to: Filter Reports</span></span>](../../../2014/sql-server/install/how-to-filter-reports.md)  
  
-   [<span data-ttu-id="0147f-130">방법: 보고서 내보내기</span><span class="sxs-lookup"><span data-stu-id="0147f-130">How to: Export Reports</span></span>](../../../2014/sql-server/install/how-to-export-reports.md)  
  
## <a name="see-also"></a><span data-ttu-id="0147f-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0147f-131">See Also</span></span>  
 <span data-ttu-id="0147f-132">[방법: 업그레이드 관리자 분석 마법사 실행](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="0147f-132">[How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span></span>  
 <span data-ttu-id="0147f-133">[업그레이드 관리자 사용자 인터페이스 참조](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0147f-133">[Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md) </span></span>  
 <span data-ttu-id="0147f-134">[업그레이드 문제 해결](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="0147f-134">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="0147f-135">업그레이드 관리자 작업</span><span class="sxs-lookup"><span data-stu-id="0147f-135">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
