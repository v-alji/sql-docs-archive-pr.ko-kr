---
title: 보고서 실행 확인 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- auditing [Reporting Services]
- verifying report execution
- logs [Reporting Services], verifying report run
- report execution data [Reporting Services]
- status information [Reporting Services]
- report processing [Reporting Services], verifying execution
- checking report execution
ms.assetid: 18a98f2f-6b40-454e-9b37-568ed1a96458
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c11c57f7c5f67b2557f5637ad10658abc9f80606
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650611"
---
# <a name="verifying-a-report-run"></a><span data-ttu-id="c298f-102">보고서 실행 확인</span><span class="sxs-lookup"><span data-stu-id="c298f-102">Verifying a Report Run</span></span>
  <span data-ttu-id="c298f-103">보고서 처리 상태에 대한 정보를 보려면 로그 파일을 사용하거나 보고서 관리자에서 보고서와 함께 표시되는 상태 정보를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-103">To view information about the status of report processing, you can use log files or refer to status information that is displayed with the report in Report Manager.</span></span>  
  
## <a name="sources-of-report-execution-data"></a><span data-ttu-id="c298f-104">보고서 실행 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="c298f-104">Sources of Report Execution Data</span></span>  
 <span data-ttu-id="c298f-105">보고서 실행 로그는 보고서 이름, 보고서를 실행한 사용자 이름, 보고서 실행 시간 및 보고서 배포에 사용되는 배달 확장 프로그램 등 보고서 실행에 대한 포괄적인 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-105">The report execution logs provide comprehensive information about report execution, including the name of the report, the name of the user who ran the report, report execution time, and the delivery extension used to distribute the report.</span></span> <span data-ttu-id="c298f-106">이 데이터를 확인하고 분석하려면 쿼리하고 보고서를 작성하기 쉬운 데이터베이스 테이블로 보고서 실행 로그를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-106">To view and analyze this data, you can copy the report execution log into database tables that are easy to query and report on.</span></span>  
  
 <span data-ttu-id="c298f-107">로그 파일에는 보고서 실행 및 다른 서버 작업에 대한 여러 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-107">Log files contain many entries about report execution and other server activity.</span></span> <span data-ttu-id="c298f-108">로그 파일에는 매우 다양한 데이터가 있기 때문에 보고서가 마지막으로 실행된 시간만 확인하려는 경우에는 보고서 관리자를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-108">Because log files contain so much data, you may want to use Report Manager if you only want to verify when the report last ran.</span></span> <span data-ttu-id="c298f-109">다른 정보가 필요하면 로그 파일을 검토해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-109">If you require additional information, you must view the log files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c298f-110">보고서 관리자에는 요청 시에 실행되는 보고서의 처리 시간은 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-110">Report Manager does not show the processing times of reports that run on demand.</span></span>  
  
 <span data-ttu-id="c298f-111">다음 표에서는 다양한 종류의 보고서에 대한 처리 날짜 및 시간을 확인하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-111">The following table describes how to view the processing date and time for various types of reports.</span></span>  
  
|<span data-ttu-id="c298f-112">보고서 종류</span><span class="sxs-lookup"><span data-stu-id="c298f-112">For this type of report</span></span>|<span data-ttu-id="c298f-113">날짜 및 시간 정보 표시 위치</span><span class="sxs-lookup"><span data-stu-id="c298f-113">Date and time information is located here</span></span>|<span data-ttu-id="c298f-114">정보 확인 방법</span><span class="sxs-lookup"><span data-stu-id="c298f-114">To view the information, do the following</span></span>|  
|-----------------------------|-----------------------------------------------|-----------------------------------------------|  
|<span data-ttu-id="c298f-115">보고서 스냅샷으로 실행되는 보고서</span><span class="sxs-lookup"><span data-stu-id="c298f-115">A report that runs as a report snapshot.</span></span>|<span data-ttu-id="c298f-116">내용 페이지.</span><span class="sxs-lookup"><span data-stu-id="c298f-116">On the Contents page.</span></span> <span data-ttu-id="c298f-117">자세한 내용은 [내용 페이지&#40;보고서 관리자&#41;](../contents-page-report-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c298f-117">For more information, see [Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md).</span></span>|<span data-ttu-id="c298f-118">1) 보고서가 포함된 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-118">1) Locate the folder that contains the report.</span></span><br /><span data-ttu-id="c298f-119">2) 폴더를 자세히 보기로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-119">2) Set the folder in Details view.</span></span><br /><span data-ttu-id="c298f-120">3) 3) **실행** 날짜 열에서 날짜 및 시간을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-120">3) 3) Note the date and time in the **When Run** column.</span></span>|  
|<span data-ttu-id="c298f-121">보고서 기록의 스냅샷</span><span class="sxs-lookup"><span data-stu-id="c298f-121">A snapshot in report history.</span></span>|<span data-ttu-id="c298f-122">기록 속성 페이지.</span><span class="sxs-lookup"><span data-stu-id="c298f-122">On the History Properties page.</span></span> <span data-ttu-id="c298f-123">자세한 내용은 [스냅샷 옵션 속성 페이지&#40;보고서 관리자&#41;](../snapshot-options-properties-page-report-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c298f-123">For more information, see [Snapshot Options Properties Page &#40;Report Manager&#41;](../snapshot-options-properties-page-report-manager.md).</span></span>|<span data-ttu-id="c298f-124">1) 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-124">1) Open the report.</span></span><br /><span data-ttu-id="c298f-125">2) **속성** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-125">2) Click the **Properties** page.</span></span><br /><span data-ttu-id="c298f-126">3) **기록** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-126">3) Click the **History** tab.</span></span><br /><span data-ttu-id="c298f-127">4) **실행 날짜** 열에서 날짜 및 시간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-127">4) Note the date and time in the **When Run** column.</span></span>|  
|<span data-ttu-id="c298f-128">캐시된 보고서</span><span class="sxs-lookup"><span data-stu-id="c298f-128">A cached report.</span></span>|<span data-ttu-id="c298f-129">캐시된 보고서를 만들고 새로 고치는 데 사용되는 일정</span><span class="sxs-lookup"><span data-stu-id="c298f-129">In the schedule used to create and refresh the cached report.</span></span>|<span data-ttu-id="c298f-130">1) 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-130">1) Open the report.</span></span><br /><span data-ttu-id="c298f-131">2) **속성** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-131">2) Click the **Properties** page.</span></span><br /><span data-ttu-id="c298f-132">3) **실행** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-132">3) Click the **Execution** tab.</span></span><br /><span data-ttu-id="c298f-133">4) 일정을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c298f-133">4) Open the schedule.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c298f-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c298f-134">See Also</span></span>  
 <span data-ttu-id="c298f-135">[Reporting Services 로그 파일 및 소스](../report-server/reporting-services-log-files-and-sources.md) </span><span class="sxs-lookup"><span data-stu-id="c298f-135">[Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md) </span></span>  
 <span data-ttu-id="c298f-136">[보고서 처리 속성 설정](set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="c298f-136">[Set Report Processing Properties](set-report-processing-properties.md) </span></span>  
 [<span data-ttu-id="c298f-137">보고서 관리자&#40;SSRS 기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="c298f-137">Report Manager  &#40;SSRS Native Mode&#41;</span></span>](../report-manager-ssrs-native-mode.md)  
  
  
