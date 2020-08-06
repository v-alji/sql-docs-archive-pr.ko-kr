---
title: 데이터 흐름 분석 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5654cb30-cad2-470c-97b3-59cb331033e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 184b53d3e982cd80d7c9c0909538a751585ae21d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648525"
---
# <a name="analysis-of-data-flow"></a><span data-ttu-id="94b23-102">데이터 흐름 분석</span><span class="sxs-lookup"><span data-stu-id="94b23-102">Analysis of Data Flow</span></span>
  <span data-ttu-id="94b23-103">[catalog.execution_data_statistics](../relational-databases/statistics/statistics.md) `SSISDB` 데이터베이스 뷰를 사용 하 여 패키지의 데이터 흐름을 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94b23-103">You can use the [catalog.execution_data_statistics](../relational-databases/statistics/statistics.md)`SSISDB` database view to analyze the data flow of packages.</span></span> <span data-ttu-id="94b23-104">이 뷰는 데이터 흐름 구성 요소가 다운스트림 구성 요소에 데이터를 전송할 때마다 행을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="94b23-104">This view displays a row each time a data flow component sends data to a downstream component.</span></span> <span data-ttu-id="94b23-105">이 정보를 사용하여 각 구성 요소로 보내진 행을 자세하게 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94b23-105">The information can be used to gain a deeper understanding of the rows that are sent to each component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="94b23-106">catalog.execution_data_statistics 뷰를 사용하여 정보를 캡처하려면 로깅 수준을 **자세히** 로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="94b23-106">The logging level must be set to **Verbose** in order to capture information with the catalog.execution_data_statistics view.</span></span>  
  
 <span data-ttu-id="94b23-107">다음 예에서는 패키지의 구성 요소 간에 보내진 행 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="94b23-107">The following example displays the number of rows sent between components of a package.</span></span>  
  
```  
use SSISDB  
select package_name, task_name, source_component_name, destination_component_name, rows_sent  
from catalog.execution_data_statistics  
where execution_id = 132  
order by source_component_name, destination_component_name  
  
```  
  
 <span data-ttu-id="94b23-108">다음 예에서는 특정 실행 중 각 구성 요소가 보낸 밀리초당 행 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="94b23-108">The following example calculates the number of rows per millisecond sent by each component for a specific execution.</span></span> <span data-ttu-id="94b23-109">계산되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="94b23-109">The calculated values are:</span></span>  
  
-   <span data-ttu-id="94b23-110">**total_rows** - 구성 요소가 보낸 모든 행의 합계</span><span class="sxs-lookup"><span data-stu-id="94b23-110">**total_rows** - the sum of all the rows sent by the component</span></span>  
  
-   <span data-ttu-id="94b23-111">**wall_clock_time_ms** - 각 구성 요소에 대한 총 실행 경과 시간(밀리초)</span><span class="sxs-lookup"><span data-stu-id="94b23-111">**wall_clock_time_ms** - the total elapsed execution time, in milliseconds, for each component</span></span>  
  
-   <span data-ttu-id="94b23-112">**num_rows_per_millisecond** - 각 구성 요소가 보낸 밀리초당 행 수</span><span class="sxs-lookup"><span data-stu-id="94b23-112">**num_rows_per_millisecond** - the number of rows per millisecond sent by each component</span></span>  
  
 <span data-ttu-id="94b23-113">`HAVING`절은 계산에서 0으로 나누기 오류를 방지 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="94b23-113">The `HAVING` clause is used to prevent a divide-by-zero error in the calculations.</span></span>  
  
```  
use SSISDB  
select source_component_name, destination_component_name,  
    sum(rows_sent) as total_rows,  
    DATEDIFF(ms,min(created_time),max(created_time)) as wall_clock_time_ms,  
    ((0.0+sum(rows_sent)) / (datediff(ms,min(created_time),max(created_time)))) as [num_rows_per_millisecond]  
from [catalog].[execution_data_statistics]  
where execution_id = 132  
group by source_component_name, destination_component_name  
having (datediff(ms,min(created_time),max(created_time))) > 0  
order by source_component_name desc  
  
```  
  
## <a name="related-tasks"></a><span data-ttu-id="94b23-114">관련 작업</span><span class="sxs-lookup"><span data-stu-id="94b23-114">Related Tasks</span></span>  
 [<span data-ttu-id="94b23-115">데이터 흐름 디버깅</span><span class="sxs-lookup"><span data-stu-id="94b23-115">Debugging Data Flow</span></span>](troubleshooting/debugging-data-flow.md)  
  
 [<span data-ttu-id="94b23-116">패키지 실행 문제 해결 도구</span><span class="sxs-lookup"><span data-stu-id="94b23-116">Troubleshooting Tools for Package Execution</span></span>](troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
## <a name="see-also"></a><span data-ttu-id="94b23-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="94b23-117">See Also</span></span>  
 [<span data-ttu-id="94b23-118">데이터 흐름의 데이터</span><span class="sxs-lookup"><span data-stu-id="94b23-118">Data in Data Flows</span></span>](data-flow/data-in-data-flows.md)  
  
  
