---
title: 보고서 기록 페이지 (보고서 관리자) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 4070be8c1d6b0633131e96c665d4551c1b676a9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650641"
---
# <a name="report-history-page-report-manager"></a><span data-ttu-id="13e4d-102">보고서 기록 페이지(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="13e4d-102">Report History Page (Report Manager)</span></span>

<span data-ttu-id="13e4d-103">보고서 기록 페이지를 사용하여 시간에 따라 생성 및 저장된 보고서 스냅샷을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-103">Use the Report History page to view report snapshots that are generated and stored over time.</span></span> <span data-ttu-id="13e4d-104">보고서 서버에 설정된 옵션에 따라 보고서 기록에 최근 스냅샷만 포함되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-104">Depending on options that are set on the report server, report history may contain only the more recent snapshots.</span></span>  
  

<span data-ttu-id="13e4d-105">보고서 기록은 항상 이 기록의 원본으로 사용되는 보고서의 컨텍스트 내에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-105">Report history is always viewed within the context of the report from which it originates.</span></span> <span data-ttu-id="13e4d-106">보고서 서버의 모든 보고서 기록을 한 곳에서 볼 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-106">You cannot view the history of all reports on a report server in one place.</span></span>  
  
<span data-ttu-id="13e4d-107">보고서 기록을 생성하려면 보고서가 무인 모드로 실행될 수 있어야 합니다. 즉, 보고서에서 저장된 자격 증명을 사용해야 하며, 매개 변수 있는 보고서의 경우 모든 매개 변수에 대한 기본 매개 변수 값을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-107">To generate report history, the report must be able to run unattended (that is, it must use stored credentials; parameterized reports must contain default parameter values for all parameters).</span></span> <span data-ttu-id="13e4d-108">보고서 기록은 수동으로 또는 예약된 작업으로 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-108">Report history can be generated manually or as a scheduled operation.</span></span> <span data-ttu-id="13e4d-109">보고서의 기록 속성에 따라 보고서 기록을 만드는 방법이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-109">History properties on the report determine the ways in which report history can be created.</span></span>  
  
<span data-ttu-id="13e4d-110">보고서 기록 스냅샷을 클릭하면 이 스냅샷을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-110">You can click a report history snapshot to view it.</span></span> <span data-ttu-id="13e4d-111">보고서 기록에 표시되는 스냅샷은 스냅샷이 만들어진 날짜와 시간으로만 구별됩니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-111">Snapshots that appear in report history are distinguished only by the date and time at which they were created.</span></span> <span data-ttu-id="13e4d-112">스냅샷이 예약된 작업에 따라 생성된 것인지 수동 작업으로 생성된 것인지는 시각적으로 구분할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-112">There is no visual indication to distinguish whether a snapshot was generated in response to a schedule or a manual operation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="13e4d-113">이 기능은 일부 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]버전에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-113">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="13e4d-114">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="13e4d-114">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="13e4d-115">탐색</span><span class="sxs-lookup"><span data-stu-id="13e4d-115">Navigation</span></span>  
 <span data-ttu-id="13e4d-116">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="13e4d-116">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-report-history-page"></a><span data-ttu-id="13e4d-117">보고서 기록 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="13e4d-117">To open the Report History page</span></span>  
  
1.  <span data-ttu-id="13e4d-118">보고서 관리자를 열고 보고서 스냅샷을 보려는 보고서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-118">Open Report Manager, and locate the report for which you want to view report snapshots.</span></span>  
  
2.  <span data-ttu-id="13e4d-119">보고서 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-119">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="13e4d-120">드롭다운 메뉴에서 **보고서 기록 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-120">In the drop-down menu, click **View Report History**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="13e4d-121">옵션</span><span class="sxs-lookup"><span data-stu-id="13e4d-121">Options</span></span>  
 <span data-ttu-id="13e4d-122">**삭제**</span><span class="sxs-lookup"><span data-stu-id="13e4d-122">**Delete**</span></span>  
 <span data-ttu-id="13e4d-123">하나 이상의 스냅샷을 삭제하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-123">Click to delete one or more snapshots.</span></span> <span data-ttu-id="13e4d-124">**삭제**를 클릭하기 전에 삭제할 스냅샷 옆의 확인란을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="13e4d-124">Before clicking **Delete**, select the check box next to the snapshot that you want to delete.</span></span>  
  
 <span data-ttu-id="13e4d-125">**새 스냅샷**</span><span class="sxs-lookup"><span data-stu-id="13e4d-125">**New Snapshot**</span></span>  
 <span data-ttu-id="13e4d-126">보고서 기록에 스냅샷을 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-126">Click to add a snapshot to report history.</span></span> <span data-ttu-id="13e4d-127">이 단추는 보고서의 기록 속성 페이지에서 **수동으로 기록 작성 허용** 옵션을 선택하는 경우에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-127">This button is available when you choose the option **Allow history to be created manually** on the History properties page of the report.</span></span>  
  
 <span data-ttu-id="13e4d-128">**마지막 실행**</span><span class="sxs-lookup"><span data-stu-id="13e4d-128">**Last Run**</span></span>  
 <span data-ttu-id="13e4d-129">스냅샷이 만들어진 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-129">Displays the date and time at which the snapshot was created.</span></span> <span data-ttu-id="13e4d-130">특정 스냅샷을 보려면 설명을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="13e4d-130">Click a description to view a particular snapshot.</span></span>  
  
 <span data-ttu-id="13e4d-131">**크기**</span><span class="sxs-lookup"><span data-stu-id="13e4d-131">**Size**</span></span>  
 <span data-ttu-id="13e4d-132">보고서 정의와 보고서 데이터를 합한 크기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-132">Displays the size of the report definition plus the data in the report.</span></span> <span data-ttu-id="13e4d-133">이 값은 보고서 정의와 데이터에서 사용하는 보고서 서버 데이터베이스 공간 크기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-133">This value indicates how much space in the report server database is used by the report definition and data.</span></span> <span data-ttu-id="13e4d-134">서식을 포함하는 렌더링된 보고서의 크기는 실제로 더 큽니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-134">The size of the rendered report, which includes formatting, is actually larger.</span></span> <span data-ttu-id="13e4d-135">괄호 안에 표시된 전체 크기는 현재 보고서에 대한 보고서 기록의 모든 스냅샷 크기의 합계입니다.</span><span class="sxs-lookup"><span data-stu-id="13e4d-135">The total size, indicated in parentheses, sums the sizes of all snapshots in the report history for the current report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e4d-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="13e4d-136">See Also</span></span>  
 <span data-ttu-id="13e4d-137">[보고서 기록을 보거나 삭제 &#40;보고서 관리자&#41;](../../2014/reporting-services/view-or-delete-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="13e4d-137">[View or Delete Report History &#40;Report Manager&#41;](../../2014/reporting-services/view-or-delete-report-history-report-manager.md) </span></span>  
 <span data-ttu-id="13e4d-138">[보고서 기록에 스냅숏을 추가 &#40;보고서 관리자&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="13e4d-138">[Add a Snapshot to Report History &#40;Report Manager&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md) </span></span>  
 <span data-ttu-id="13e4d-139">[일반 속성 페이지, 보고서 &#40;보고서 관리자&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="13e4d-139">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 <span data-ttu-id="13e4d-140">[F1 도움말 보고서 관리자](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="13e4d-140">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 [<span data-ttu-id="13e4d-141">스냅숏 옵션 속성 페이지 &#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="13e4d-141">Snapshot Options Properties Page &#40;Report Manager&#41;</span></span>](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md)