---
title: 컬렉션 집합 보고서 보기(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.reporthistory.calendar.f1
helpviewer_keywords:
- collection sets [SQL Server], viewing reports
- reports [SQL Server], viewing collection set
ms.assetid: c3b1e791-9aa1-4bba-9622-4954568e1820
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cb8755c67e6c03bb318fdb86d703f6d647d5a3eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659478"
---
# <a name="view-a-collection-set-report-sql-server-management-studio"></a><span data-ttu-id="6a34b-102">컬렉션 집합 보고서 보기(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="6a34b-102">View a Collection Set Report (SQL Server Management Studio)</span></span>
  <span data-ttu-id="6a34b-103">관리 데이터 웨어하우스를 구성한 다음에는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 컬렉션 집합 보고서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-103">After you have configured the management data warehouse, you can view a collection set report in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="6a34b-104">설치 프로그램 실행 중 설치되는 시스템 데이터 컬렉션 집합에 대해 보고서가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-104">Reports are provided for the System Data collection sets that are installed during Setup.</span></span> <span data-ttu-id="6a34b-105">보고서에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-105">The reports include the following:</span></span>  
  
-   <span data-ttu-id="6a34b-106">디스크 사용 요약</span><span class="sxs-lookup"><span data-stu-id="6a34b-106">Disk Usage Summary</span></span>  
  
-   <span data-ttu-id="6a34b-107">쿼리 통계 기록</span><span class="sxs-lookup"><span data-stu-id="6a34b-107">Query Statistics History</span></span>  
  
-   <span data-ttu-id="6a34b-108">서버 작업 기록</span><span class="sxs-lookup"><span data-stu-id="6a34b-108">Server Activity History</span></span>  
  
 <span data-ttu-id="6a34b-109">이 절차에서 **디스크 사용** 컬렉션 집합에 대한 보고서가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-109">This procedure displays the report for the **Disk Usage** collection set.</span></span> <span data-ttu-id="6a34b-110">동일한 일반 절차에 따라 다른 시스템 데이터 컬렉션 집합에 대한 보고서도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-110">You can follow the same general procedure to view the reports for the other System Data collection sets.</span></span>  
  
### <a name="to-view-a-collection-set-report"></a><span data-ttu-id="6a34b-111">컬렉션 집합 보고서를 보려면</span><span class="sxs-lookup"><span data-stu-id="6a34b-111">To view a collection set report</span></span>  
  
1.  <span data-ttu-id="6a34b-112">보고서에 대한 테이블은 수집된 데이터를 처음으로 업로드할 때 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-112">The tables for a report are created the first time that the collected data is uploaded.</span></span> <span data-ttu-id="6a34b-113">첫 번째 업로드 전에 보고서를 보려고 하면 오류가 발생하고 보고서가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-113">If you try to view a report before this first upload, an error occurs and no report is displayed.</span></span> <span data-ttu-id="6a34b-114">디스크 사용 컬렉션 집합에 대한 데이터를 업로드하려면 개체 탐색기에서 **관리** 폴더, **데이터 컬렉션**, **시스템 데이터 컬렉션 집합**을 차례로 확장하고 **디스크 사용** 컬렉션 집합을 마우스 오른쪽 단추로 클릭한 다음 **지금 수집 및 업로드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-114">To upload data for the Disk Usage collection set, in Object Explorer, expand the **Management** folder, expand **Data Collection**, expand **System Data Collection Sets**, right-click the **Disk Usage** collection set, and then click **Collect and Upload Now**.</span></span>  
  
2.  <span data-ttu-id="6a34b-115">보고서를 보려면 개체 탐색기에서 **관리** 폴더를 확장하고 **데이터 컬렉션**을 마우스 오른쪽 단추로 클릭한 다음 **보고서**, **관리 데이터 웨어하우스**를 차례로 가리키고 **디스크 사용 요약**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-115">To view the report, in Object Explorer, expand the **Management** folder, right-click **Data Collection**, point to **Reports**, point to **Management Data Warehouse**, and then click **Disk Usage Summary**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6a34b-116">일부 보고서는 데이터 컬렉션 시간대에 따라 달력 단추를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-116">Some reports might display a calendar button under the data collection timeline.</span></span> <span data-ttu-id="6a34b-117">**데이터 컬렉션 보고서 달력**에 액세스하려면 이 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-117">Click this button to access the **Data Collection Report Calendar**.</span></span>  
  
#### <a name="data-collection-report-calendar"></a><span data-ttu-id="6a34b-118">데이터 컬렉션 보고서 달력</span><span class="sxs-lookup"><span data-stu-id="6a34b-118">Data Collection Report Calendar</span></span>  
 <span data-ttu-id="6a34b-119">이 대화 상자를 사용하여 보고하려는 데이터의 시작 날짜, 시작 시간 및 기간을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-119">Use this dialog box to specify the start date, start time, and duration of the data that you want to report on.</span></span> <span data-ttu-id="6a34b-120">예를 들어 지난 수요일의 특정 12시간 동안 서버의 디스크 사용 동작을 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-120">For example, you may want to report on the disk usage activity of a server for a specific 12-hour period last Wednesday.</span></span>  
  
 <span data-ttu-id="6a34b-121">**시작 날짜**</span><span class="sxs-lookup"><span data-stu-id="6a34b-121">**Start date**</span></span>  
 <span data-ttu-id="6a34b-122">보고서 데이터의 시작 날짜를 입력하거나 달력에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-122">Enter a beginning date for the report data, or select one from the calendar.</span></span>  
  
 <span data-ttu-id="6a34b-123">**시작 시간**</span><span class="sxs-lookup"><span data-stu-id="6a34b-123">**Start time**</span></span>  
 <span data-ttu-id="6a34b-124">보고서 데이터의 시작 시간을 입력하거나 화살표를 클릭하여 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-124">Enter a beginning time for the report data or specify one by clicking the arrows.</span></span>  
  
 <span data-ttu-id="6a34b-125">**Duration**</span><span class="sxs-lookup"><span data-stu-id="6a34b-125">**Duration**</span></span>  
 <span data-ttu-id="6a34b-126">보고서에 포함할 시간 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-126">Specify the time range to include in the report.</span></span> <span data-ttu-id="6a34b-127">기본값은 240분입니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-127">The default value is 240 minutes.</span></span> <span data-ttu-id="6a34b-128">선택 가능한 값은 15분, 60분, 240분(4시간), 720분(12시간) 및 1440분(24시간)입니다.</span><span class="sxs-lookup"><span data-stu-id="6a34b-128">The possible values to select from are 15 minutes, 60 minutes, 240 minutes (4 hours), 720 minutes (12 hours), and 1440 minutes (24 hours).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a34b-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a34b-129">See Also</span></span>  
 <span data-ttu-id="6a34b-130">[데이터 컬렉션](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="6a34b-130">[Data Collection](data-collection.md) </span></span>  
 <span data-ttu-id="6a34b-131">[Management Studio의 사용자 지정 보고서](../../ssms/object/custom-reports-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="6a34b-131">[Custom Reports in Management Studio](../../ssms/object/custom-reports-in-management-studio.md) </span></span>  
 [<span data-ttu-id="6a34b-132">관리 데이터 웨어하우스 구성&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="6a34b-132">Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;</span></span>](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
