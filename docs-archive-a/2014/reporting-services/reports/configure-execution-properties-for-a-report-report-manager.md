---
title: 보고서에 실행 속성 구성(보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report execution properties [Reporting Services]
- reports [Reporting Services], properties
- reports [Reporting Services], execution options
ms.assetid: 73cc8dcc-ef80-40d7-9739-d33bba0eb28a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 51cd7b5db225b39f5a061ed750b2ef5cdd265b9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661521"
---
# <a name="configure-execution-properties-for-a-report--report-manager"></a><span data-ttu-id="bae83-102">보고서에 실행 속성 구성(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="bae83-102">Configure Execution Properties for a Report  (Report Manager)</span></span>
  <span data-ttu-id="bae83-103">보고서에 대한 데이터를 검색할 시기를 지정하도록 보고서 처리 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-103">You can set report processing options to specify when data is retrieved for a report.</span></span> <span data-ttu-id="bae83-104">외부 데이터 원본이 특정 시간에 새로 고쳐지고(예: 매일 또는 매주 새로 고쳐지는 데이터 웨어하우스) 보고서가 요청될 때마다 같은 데이터를 검색하는 오버헤드가 발생하지 않도록 하려는 경우에 보고서에 대한 데이터 처리를 예약하는 것이 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-104">It is useful to schedule data processing for a report if the external data source is refreshed at specific times (for example, a data warehouse that is refreshed daily or weekly) and you want to avoid the overhead of retrieving the same data each time a report is requested.</span></span> <span data-ttu-id="bae83-105">외부 데이터베이스 서버의 처리 로드를 제어하거나 동일한 데이터 집합을 사용해야 하는 여러 사용자에게 일관된 결과를 제공하려는 경우에도 데이터 처리를 예약하는 것이 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-105">Scheduling data processing is also useful if you want to control the processing load on the external database server or when you want to provide consistent results for multiple users who must work with identical sets of data.</span></span> <span data-ttu-id="bae83-106">일시적인 데이터로 요청 시 실행 보고서를 사용하면 매 시간마다 다른 결과를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-106">With volatile data, an on-demand report can produce different results from one minute to the next.</span></span> <span data-ttu-id="bae83-107">하지만 보고서 스냅샷을 사용하면 같은 시점의 데이터가 들어 있는 다른 보고서나 분석 도구와 비교하여 유효한 결과를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-107">A report snapshot, by contrast, allows you to make valid comparisons against other reports or analytical tools that contain data from the same point in time.</span></span>  
  
 <span data-ttu-id="bae83-108">보고서 스냅샷은 레이아웃 지침 및 특정 시점에 검색된 쿼리 결과가 들어 있는 보고서입니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-108">A report snapshot is a report that contains layout instructions and query results that were retrieved at a specific point in time.</span></span> <span data-ttu-id="bae83-109">보고서를 선택할 때 최신 쿼리 결과를 얻을 수 있는 요청 시 실행 보고서와 달리 보고서 스냅샷은 예약된 시간에 처리되고 보고서 서버에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-109">Unlike on-demand reports, which get up-to-date query results when you select the report, report snapshots are processed on a schedule and then saved to a report server.</span></span> <span data-ttu-id="bae83-110">표시할 보고서 스냅샷을 선택하면 보고서 서버가 보고서 서버 데이터베이스에서 저장된 보고서를 검색하고 스냅샷이 만들어진 시점에 따른 보고서의 현재 데이터 및 레이아웃을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-110">When you select a report snapshot for viewing, the report server retrieves the stored report from the report server database and shows the data and layout that were current for the report at the time the snapshot was created.</span></span>  
  
 <span data-ttu-id="bae83-111">보고서 스냅샷은 특정 렌더링 형식으로 저장되지 않으며</span><span class="sxs-lookup"><span data-stu-id="bae83-111">Report snapshots are not saved in a particular rendering format.</span></span> <span data-ttu-id="bae83-112">사용자나 애플리케이션이 보고서 스냅샷을 요청할 때만 HTML과 같은 최종 보기 형식으로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-112">Instead, report snapshots are rendered in a final viewing format (such as HTML) only when a user or an application requests it.</span></span> <span data-ttu-id="bae83-113">지연된 렌더링은 스냅샷을 이동 가능하게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-113">Deferred rendering makes a snapshot portable.</span></span> <span data-ttu-id="bae83-114">요청 디바이스나 웹 브라우저에 적합한 형식으로 보고서를 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-114">The report can be rendered in the correct format for the requesting device or Web browser.</span></span>  
  
### <a name="to-configure-report-processing-options"></a><span data-ttu-id="bae83-115">보고서 처리 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="bae83-115">To configure report processing options</span></span>  
  
1.  <span data-ttu-id="bae83-116">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-116">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="bae83-117">처리 옵션을 설정할 보고서를 찾아 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-117">Navigate to and open the report for which you want to set processing options.</span></span>  
  
 <span data-ttu-id="bae83-118">보고서 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-118">Hover over the report, and click the drop-down arrow.</span></span>  
  
1.  <span data-ttu-id="bae83-119">드롭다운 메뉴에서 **관리** 를 클릭한 다음 **처리 옵션** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-119">In the drop-down menu, click **Manage** and then select the **Processing Options** tab.</span></span>  
  
2.  <span data-ttu-id="bae83-120">**보고서 실행 스냅샷에서 이 보고서 렌더링**을 클릭하고 다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-120">Click **Render this report from an execution snapshot, and then select one of the following options:**</span></span>  
  
    -   <span data-ttu-id="bae83-121">스냅샷을 만들려면 **다음 일정을 사용하여 보고서 실행 스냅샷 만들기**를 선택한 다음 보고서별 일정을 정의하거나 **공유 일정** 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-121">If you want to create a snapshot, select **Use the following schedule to create report execution snapshots**, and then either define a report-specific schedule or select from the **Shared schedule** list.</span></span>  
  
    -   <span data-ttu-id="bae83-122">스냅샷을 즉시 만들려면 **이 페이지에서 [적용] 단추를 클릭할 때 보고서 스냅샷 만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-122">If you want to create a snapshot immediately, select **Create a report snapshot when you click the Apply button on this page**.</span></span>  
  
3.  <span data-ttu-id="bae83-123">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bae83-123">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bae83-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bae83-124">See Also</span></span>  
 <span data-ttu-id="bae83-125">[보고서 처리 속성 설정](../report-server/set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="bae83-125">[Set Report Processing Properties](../report-server/set-report-processing-properties.md) </span></span>  
 <span data-ttu-id="bae83-126">[보고서 &#40;보고서 관리자을 열고 닫습니다&#41;](../reports/open-and-close-a-report-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="bae83-126">[Open and Close a Report &#40;Report Manager&#41;](../reports/open-and-close-a-report-report-manager.md) </span></span>  
 <span data-ttu-id="bae83-127">[내용 페이지&#40;보고서 관리자&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="bae83-127">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="bae83-128">[보고서 서버 콘텐츠 관리&#40;SSRS 기본 모드&#41;](../report-server/report-server-content-management-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="bae83-128">[Report Server Content Management &#40;SSRS Native Mode&#41;](../report-server/report-server-content-management-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="bae83-129">처리 옵션 속성 페이지&#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="bae83-129">Processing Options Properties Page &#40;Report Manager&#41;</span></span>](../processing-options-properties-page-report-manager.md)  
  
  
