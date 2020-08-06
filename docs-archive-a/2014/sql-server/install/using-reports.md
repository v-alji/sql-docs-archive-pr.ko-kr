---
title: 보고서 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- displaying reports
- overriding reports
- Upgrade Advisor Report Viewer
- reports [Upgrade Advisor], about reports
- formatting reports
- resolved issues [Upgrade Advisor]
- distributing reports [Reporting Services]
- filtering reports [Reporting Services]
- removing report items
- viewing reports
- rerunning analysis
- information issues [Upgrade Advisor]
- deleting report items
- icons [Upgrade Advisor]
- Upgrade Advisor [SQL Server], reports
- sending reports
- blocking issues [Upgrade Advisor]
- sharing reports
- reports [Upgrade Advisor]
- SQL Server Upgrade Advisor, reports
- modifying reports
- distributing reports [Reporting Services], about report distribution
- warnings [Upgrade Advisor]
- analyzing system [Upgrade Advisor], reports
ms.assetid: 4a3cb94a-a7ac-4cec-94c7-db26fcf6d161
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f52afcfdaa7de33d83d64a049f9a350f0463b4c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742756"
---
# <a name="using-reports"></a><span data-ttu-id="b9510-102">보고서 사용</span><span class="sxs-lookup"><span data-stu-id="b9510-102">Using Reports</span></span>
  <span data-ttu-id="b9510-103">업그레이드 관리자 분석 마법사가 서버에서 분석하는 각 구성 요소에 대해 별도의 보고서가 생성되며, 필요한 경우 각 인스턴스에 대해서도 별도의 보고서가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-103">A separate report is generated for each component, and, where necessary, each instance, that the Upgrade Advisor Analysis Wizard analyzes on a server.</span></span> <span data-ttu-id="b9510-104">보고서에는 업그레이드에 영향을 주는 알려진 문제에 대한 세부 정보가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-104">The report provides details about known issues that affect an upgrade.</span></span> <span data-ttu-id="b9510-105">또한 보고서에는 식별된 문제를 해결하기 위한 정보 및 권장 동작의 링크도 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-105">It also provides links to information and suggested actions for addressing the identified issues.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b9510-106">업그레이드 관리자 보고서 뷰어가 기본 보고서 디렉터리에서 보고서를 찾지 못하는 경우에는 **보고서 열기** 링크를 사용 하 여 다른 디렉터리에서 보고서를 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-106">If the Upgrade Advisor Report Viewer does not find any reports in the default reports directory, you can load a report from a different directory by using the **Open Report** link.</span></span>  
  
## <a name="viewing-reports"></a><span data-ttu-id="b9510-107">보고서 보기</span><span class="sxs-lookup"><span data-stu-id="b9510-107">Viewing Reports</span></span>  
 <span data-ttu-id="b9510-108">업그레이드 관리자 보고서 뷰어를 사용하여 업그레이드 관리자 보고서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-108">You use the Upgrade Advisor Report Viewer to view Upgrade Advisor reports.</span></span> <span data-ttu-id="b9510-109">보고서를 보려면 업그레이드 관리자 시작 페이지에서 **업그레이드 관리자 보고서 뷰어 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-109">To view reports, on the Upgrade Advisor start page, click **Launch Upgrade Advisor Report Viewer**.</span></span>  
  
 <span data-ttu-id="b9510-110">서버에 대한 보고서를 로드한 후에는 업그레이드 문제를 확인할 구성 요소를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-110">After you load a report for a server, you can select a component for which you want to see upgrade issues.</span></span> <span data-ttu-id="b9510-111">**필터 기준** 상자에서 필터를 적용 하 여 다음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-111">You can apply a filter from the **Filter By** box to see the following:</span></span>  
  
-   <span data-ttu-id="b9510-112">모든 문제</span><span class="sxs-lookup"><span data-stu-id="b9510-112">All issues</span></span>  
  
-   <span data-ttu-id="b9510-113">모든 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="b9510-113">All upgrade issues</span></span>  
  
-   <span data-ttu-id="b9510-114">업그레이드 이전 문제</span><span class="sxs-lookup"><span data-stu-id="b9510-114">Pre-upgrade issues</span></span>  
  
-   <span data-ttu-id="b9510-115">모든 마이그레이션 문제</span><span class="sxs-lookup"><span data-stu-id="b9510-115">All migration issues</span></span>  
  
-   <span data-ttu-id="b9510-116">해결된 문제</span><span class="sxs-lookup"><span data-stu-id="b9510-116">Resolved issues</span></span>  
  
-   <span data-ttu-id="b9510-117">해결되지 않은 문제</span><span class="sxs-lookup"><span data-stu-id="b9510-117">Unresolved issues</span></span>  
  
 <span data-ttu-id="b9510-118">보고서의 문제가 20 개를 넘는 경우 문제 목록의 위쪽 또는 아래쪽에 있는 **다음 20** 개 또는 **이전 20 개** 를 클릭 하 여 다음 또는 이전 문제 그룹으로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-118">If your report has more than 20 issues, you can move to the next or previous group of issues by clicking **Next 20** or **Previous 20** at the top or bottom of the issues list.</span></span>  
  
 <span data-ttu-id="b9510-119">**보고서** 드롭다운 목록 상자에서 보고서를 선택 하 여 최대 5 개의 저장 된 보고서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-119">You can view up to five saved reports by selecting the reports from the **Report** drop-down list box.</span></span> <span data-ttu-id="b9510-120">보고서는 보고서가 생성될 때의 타임스탬프를 기준으로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-120">The reports are listed by the timestamp from when they were generated.</span></span>  
  
## <a name="report-format"></a><span data-ttu-id="b9510-121">보고서 형식</span><span class="sxs-lookup"><span data-stu-id="b9510-121">Report Format</span></span>  
 <span data-ttu-id="b9510-122">보고서 뷰어는 3개의 열에 보고서 문제를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-122">The report viewer displays report issues in three columns.</span></span> <span data-ttu-id="b9510-123">표시된 각 문제는 축소가 가능하기 때문에 설명을 숨기고 중요한 정보만 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-123">Each issue is collapsible so that you can hide the description and view only the key information.</span></span>  
  
 <span data-ttu-id="b9510-124">첫 번째 열은 **중요도** 열입니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-124">The first column is the **Importance** column.</span></span> <span data-ttu-id="b9510-125">차단 문제 또는 중요한 문제에 대해서는 빨간색 원에 X표시가 있는 아이콘, 경고 및 정보 수준에 대해서는 노란색 삼각형에 느낌표 기호가 있는 아이콘으로 문제의 중요도가 구분되어 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-125">Icons indicate the importance for each issue by displaying either a red circle with an X for blocking or important issues or a yellow triangle with an exclamation mark for Warning and Information issues.</span></span> <span data-ttu-id="b9510-126">두 번째 열을 **수정 하는 경우**문제를 해결 해야 하는 시기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-126">The second column, **When to fix**, indicates when you must resolve the issue.</span></span> <span data-ttu-id="b9510-127">**중요도** 또는 **해결 시기** 열을 기준으로 보고서를 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-127">You can sort the report on either the **Importance** or **When to fix** column.</span></span> <span data-ttu-id="b9510-128">세 번째 열인 **설명**에는 문제의 제목이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-128">The third column, **Description**, lists the title of the issue.</span></span>  
  
 <span data-ttu-id="b9510-129">문제를 확장하면 추가 정보, 문제 해결에 대한 자세한 정보를 보여 주는 링크 및 문제에 대한 세부 정보를 보여 주는 링크를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-129">You can expand an issue to display additional information, a link to detailed information about resolving the issue, and a link to show issue details.</span></span> <span data-ttu-id="b9510-130">문제에 대한 세부 정보를 보여 주는 링크를 클릭하면 해당 문제에 대한 정보 및 문제 해결을 위한 지침이 포함된 도움말 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-130">When you click the link to get detailed information for the issue, a Help topic with information about the issue and instructions for addressing the issue is displayed.</span></span> <span data-ttu-id="b9510-131">문제를 해결 하거나 작업 항목을 관리 하려면 **이 문제가 해결** 되었습니다. 확인란을 선택 하 여 문제를 완료로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-131">After you have fixed an issue, or to manage your action items, you can mark issues as complete by selecting the **This issue has been resolved** check box.</span></span> <span data-ttu-id="b9510-132">업그레이드 문제 목록에서 해결 된 문제를 제거 하려면 **새로 고침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-132">If you want to remove the resolved issues from the list of upgrade issues, click **Refresh**.</span></span> <span data-ttu-id="b9510-133">이 문제는 동일한 구성 요소에 대해 업그레이드 관리자 분석 마법사를 실행 하거나 **필터** 옵션에서 **해결 된 문제** 필터를 적용할 때까지 다시 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-133">The issue is not displayed again until you either run the Upgrade Advisor Analysis Wizard against the same component or apply the **Resolved Issues** filter from the **Filter By** option.</span></span>  
  
## <a name="report-files"></a><span data-ttu-id="b9510-134">보고서 파일</span><span class="sxs-lookup"><span data-stu-id="b9510-134">Report Files</span></span>  
 <span data-ttu-id="b9510-135">업그레이드 관리자 분석 마법사는 내 문서 upgrade Advisor\110\Reports 디렉터리에 보고서를 만들고 \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 분석 하는 각 서버에 대 한 하위 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-135">The Upgrade Advisor Analysis Wizard creates reports in the My Documents\\[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports directory and creates a subdirectory for each server that you analyze.</span></span> <span data-ttu-id="b9510-136">보고서 파일은 특정 명명 규칙을 따르는 XML 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-136">The report files are XML files that follow a specific naming convention.</span></span> <span data-ttu-id="b9510-137">업그레이드 관리자 보고서 뷰어를 시작하면 기본 디렉터리의 보고서 파일이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-137">When you launch the Upgrade Advisor Report Viewer, the report files in the default directory are displayed.</span></span> <span data-ttu-id="b9510-138">이 폴더로 보고서 파일을 복사할 경우 복사된 파일이 명명 규칙에 부합하지 않으면 보고서 뷰어에 자동으로 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-138">If you copy report files into this folder, they must adhere to the naming convention or the report viewer will not display them automatically.</span></span>  
  
 <span data-ttu-id="b9510-139">다른 사용자에게 XML 보고서를 보내 정보를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-139">If you want to share the information with other people, you can send them the XML report.</span></span> <span data-ttu-id="b9510-140">다른 애플리케이션을 사용하려는 경우에는 쉼표로 구분된 값 파일로 보고서를 내보내 이 파일을 사용하여 스프레드시트, 텍스트 파일 또는 전자 메일 메시지를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9510-140">Or, if you want to use another application, you can export the report into a comma-separated value file that you can use to create a spreadsheet, text file, or e-mail message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9510-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b9510-141">See Also</span></span>  
 <span data-ttu-id="b9510-142">[방법: 업그레이드 관리자 보고서 보기](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md) </span><span class="sxs-lookup"><span data-stu-id="b9510-142">[How to: View an Upgrade Advisor Report](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md) </span></span>  
 <span data-ttu-id="b9510-143">[방법: 보고서 내보내기](../../../2014/sql-server/install/how-to-export-reports.md) </span><span class="sxs-lookup"><span data-stu-id="b9510-143">[How to: Export Reports](../../../2014/sql-server/install/how-to-export-reports.md) </span></span>  
 <span data-ttu-id="b9510-144">[방법: 보고서 필터링](../../../2014/sql-server/install/how-to-filter-reports.md) </span><span class="sxs-lookup"><span data-stu-id="b9510-144">[How to: Filter Reports](../../../2014/sql-server/install/how-to-filter-reports.md) </span></span>  
 <span data-ttu-id="b9510-145">[업그레이드 문제 해결](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="b9510-145">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="b9510-146">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="b9510-146">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
