---
title: '방법: 업그레이드 관리자 보고서 보기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- displaying reports
- viewing reports
- Upgrade Advisor [SQL Server], reports
- SQL Server Upgrade Advisor, reports
- reports [Upgrade Advisor], viewing
ms.assetid: d13b38af-0ac3-4030-83cd-e7d7825dd09f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9e6df35b869186a601458889c348153093ccbce4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660300"
---
# <a name="how-to-view-an-upgrade-advisor-report"></a><span data-ttu-id="2e7f8-102">방법: 업그레이드 관리자 보고서 보기</span><span class="sxs-lookup"><span data-stu-id="2e7f8-102">How to: View an Upgrade Advisor Report</span></span>
  <span data-ttu-id="2e7f8-103">업그레이드 관리자는 사용자가 분석하도록 선택한 각 구성 요소에 대해 보고서를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-103">Upgrade Advisor creates reports for each component that you select to analyze.</span></span> <span data-ttu-id="2e7f8-104">이 항목에서는 업그레이드 관리자 시작 페이지에서 업그레이드 관리자 보고서를 보는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-104">This topic describes how to view an Upgrade Advisor report from the Upgrade Advisor start page.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2e7f8-105">보고서 뷰어는 표준 파일 이름을 기준으로 파일을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-105">The report viewer loads files based on standard file names.</span></span> <span data-ttu-id="2e7f8-106">파일의 이름이 바뀐 경우 보고서 뷰어는 해당 파일을 로드하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-106">If the files have been renamed, the report viewer will not load them.</span></span>  
  
### <a name="to-view-a-report"></a><span data-ttu-id="2e7f8-107">보고서를 보려면</span><span class="sxs-lookup"><span data-stu-id="2e7f8-107">To view a report</span></span>  
  
1.  <span data-ttu-id="2e7f8-108">**시작**, **모든 프로그램**,을 차례로 클릭 한 **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]** 다음 \*\* [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 업그레이드 관리자\*\*를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-108">Click **Start**, click **All Programs**, click **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**, and then click **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor**.</span></span>  
  
2.  <span data-ttu-id="2e7f8-109">업그레이드 관리자 시작 페이지에서 **업그레이드 관리자 보고서 뷰어 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-109">On the Upgrade Advisor start page, click **Launch Upgrade Advisor Report Viewer**.</span></span>  
  
3.  <span data-ttu-id="2e7f8-110">컴퓨터의 기본 위치에 있는 보고서를 선택하려면</span><span class="sxs-lookup"><span data-stu-id="2e7f8-110">To select a report in the default location on your computer:</span></span>  
  
    1.  <span data-ttu-id="2e7f8-111">**서버** 목록에서 서버를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-111">In the **Server** list, select a server.</span></span>  
  
    2.  <span data-ttu-id="2e7f8-112">**인스턴스 또는 구성 요소** 목록에서 구성 요소 또는 구성 요소/인스턴스 조합을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-112">In the **Instance or component** list, select a component or component/instance combination.</span></span>  
  
     <span data-ttu-id="2e7f8-113">다른 위치의 보고서를 선택하려면</span><span class="sxs-lookup"><span data-stu-id="2e7f8-113">To select a report at another location:</span></span>  
  
    1.  <span data-ttu-id="2e7f8-114">**보고서 열기** 링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-114">Click the **Open Report** link.</span></span>  
  
    2.  <span data-ttu-id="2e7f8-115">보고서 위치를 찾은 다음 XML 파일을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-115">Browse to the report location and then double-click the XML file.</span></span>  
  
     <span data-ttu-id="2e7f8-116">업그레이드 관리자는 이전 분석에서 생성된 최대 다섯 개의 보고서를 기록으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-116">Upgrade Advisor stores up to five reports from previous analysis as history.</span></span> <span data-ttu-id="2e7f8-117">이러한 보고서를 보려면 **보고서** 드롭다운 목록 상자를 클릭 하 고 보고서를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-117">To view these reports, click the **Report** drop-down list box, and select a report.</span></span> <span data-ttu-id="2e7f8-118">보고서는 보고서가 생성될 때의 타임스탬프를 기준으로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-118">The reports are listed by the timestamp from when they were generated.</span></span>  
  
     <span data-ttu-id="2e7f8-119">보고서에는 검색된 모든 문제에 대해 다음과 같은 세부 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-119">The report contains the following details for all detected issues:</span></span>  
  
    -   <span data-ttu-id="2e7f8-120">**중요도**-문제를 해결 하는 것이 얼마나 중요 한지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-120">**Importance**, which indicates how important it is to fix the issue.</span></span>  
  
    -   <span data-ttu-id="2e7f8-121">을 **수정 하는 경우**, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 응용 프로그램이 나 데이터를 마이그레이션하기 전이나 후 또는 언제 든 지로 업그레이드 전이나 후에 문제를 해결 해야 하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-121">**When to fix**, which indicates if you should (or must) fix the issue before or after upgrading to [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], before or after migrating the application or data, or anytime.</span></span>  
  
    -   <span data-ttu-id="2e7f8-122">문제에 대한 간단한 설명</span><span class="sxs-lookup"><span data-stu-id="2e7f8-122">A brief description of the issue.</span></span>  
  
4.  <span data-ttu-id="2e7f8-123">보고서에 포함된 항목이 20개를 초과하는 경우 보고서의 위 또는 아래에 있는 녹색 앞으로 화살표를 클릭하면 다음 항목 집합을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-123">If the report contains more than 20 items, click the green forward arrow at the top or bottom of the report to view the next set of items.</span></span> <span data-ttu-id="2e7f8-124">이전 20개 항목을 보려면 녹색 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-124">Click the green back button to view the previous 20 items.</span></span>  
  
5.  <span data-ttu-id="2e7f8-125">보고서를 정렬하려면 열 제목을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-125">To sort the report, click a column heading.</span></span>  
  
6.  <span data-ttu-id="2e7f8-126">특정 항목에 대한 세부 정보를 보려면 해당 항목을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-126">To view details for a specific item, click the item.</span></span> <span data-ttu-id="2e7f8-127">문제에 대한 설명이 다음 추가 옵션과 함께 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-127">A description of the issue appears, along with additional options:</span></span>  
  
    -   <span data-ttu-id="2e7f8-128">이 문제가 발견 된 개체를 보려면 **영향을 받는 개체 표시**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-128">To view the objects where this issue was found, click **Show affected objects**.</span></span>  
  
    -   <span data-ttu-id="2e7f8-129">문제에 대 한 도움말을 보려면 **이 문제에 대 한 자세한 설명 및 문제 해결 방법**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-129">To view help for the issue, click **Tell me more about this issue and how to resolve it**.</span></span>  
  
    -   <span data-ttu-id="2e7f8-130">문제를 해결 된 것으로 표시 하려면 보고서를 다시 볼 때 발생 하는 문제를 숨기는 **이 문제가 해결**되었습니다 .를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-130">To mark the issue as resolved, which hides the issue when you view the report again, select **This issue has been resolved**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2e7f8-131">보고서에는 검색할 수 없는 문제에 대한 항목이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-131">The report may contain an item for undetectable issues.</span></span> <span data-ttu-id="2e7f8-132">이러한 문제는 검색할 수 없는 문제, 또는 거짓 긍정 결과를 지나치게 많이 생성하는 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-132">These are issues that cannot be detected or that would generate too many false-positive results.</span></span> <span data-ttu-id="2e7f8-133">구성 요소에 대 한 검색할 수 없는 문제 목록을 보려면 **이 문제에 대 한 자세한 설명 및이 문제를 해결 하는 방법** 링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7f8-133">Click the **Tell me more about this issue and how to resolve it** link to see a list of undetectable issues for the component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e7f8-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2e7f8-134">See Also</span></span>  
 <span data-ttu-id="2e7f8-135">[방법: 보고서 내보내기](../../../2014/sql-server/install/how-to-export-reports.md) </span><span class="sxs-lookup"><span data-stu-id="2e7f8-135">[How to: Export Reports](../../../2014/sql-server/install/how-to-export-reports.md) </span></span>  
 <span data-ttu-id="2e7f8-136">[방법: 업그레이드 관리자 분석 마법사 실행](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="2e7f8-136">[How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span></span>  
 <span data-ttu-id="2e7f8-137">[업그레이드 문제 해결](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="2e7f8-137">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 <span data-ttu-id="2e7f8-138">[업그레이드 관리자 방법 도움말 항목](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="2e7f8-138">[Upgrade Advisor How-to Topics](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md) </span></span>  
 [<span data-ttu-id="2e7f8-139">업그레이드 관리자 작업</span><span class="sxs-lookup"><span data-stu-id="2e7f8-139">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
