---
title: 유틸리티 대시보드 (SQL Server 유틸리티) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 999eb741-4a60-43f6-ab37-2df7dce845c1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1e6f59eca0aaaee0d0fc79f267a781b650fb3d58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731984"
---
# <a name="utility-dashboard-sql-server-utility"></a><span data-ttu-id="bfd71-102">유틸리티 대시보드(SQL Server 유틸리티)</span><span class="sxs-lookup"><span data-stu-id="bfd71-102">Utility Dashboard (SQL Server Utility)</span></span>
  <span data-ttu-id="bfd71-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유틸리티 대시보드에서 데이터를 보려면 "Utility<UCP_Name>\\(ComputerName\UCP)"라고 표시된 유틸리티 탐색기 트리의 최상위 노드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-103">To see data in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility dashboard, select the top node in the Utility Explorer tree - labeled "Utility<UCP_Name>\\(ComputerName\UCP)."</span></span> <span data-ttu-id="bfd71-104">대시보드에는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유틸리티의 모든 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 관리되는 인스턴스와 데이터 계층 애플리케이션의 요약과 세부 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-104">The dashboard includes summary and detail data from all managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and all data-tier applications in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="bfd71-105">대시보드의 데이터를 새로 고치려면 유틸리티 탐색기 트리에서 최상위 노드를 마우스 오른쪽 단추로 클릭하고 **새로 고침**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-105">To refresh data in the dashboard, right-click the top node in the Utility Explorer tree, and select **Refresh**.</span></span>  
  
 <span data-ttu-id="bfd71-106">유틸리티 제어 지점을 만드는 방법은 [SQL Server 유틸리티 제어 지점 만들기&#40;SQL Server 유틸리티&#41;](../relational-databases/manage/create-a-sql-server-utility-control-point-sql-server-utility.md)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-106">For more information about how to create a utility control point, see [Create a SQL Server Utility Control Point &#40;SQL Server Utility&#41;](../relational-databases/manage/create-a-sql-server-utility-control-point-sql-server-utility.md).</span></span> <span data-ttu-id="bfd71-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유틸리티에 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스를 추가하는 방법은 [SQL Server 인스턴스 등록&#40;SQL Server 유틸리티&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bfd71-107">For more information about how to add an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility, see [Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="bfd71-108">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="bfd71-108">UI element list</span></span>  
 <span data-ttu-id="bfd71-109">관리되는 인스턴스 상태</span><span class="sxs-lookup"><span data-stu-id="bfd71-109">Managed Instance Health</span></span>  
 <span data-ttu-id="bfd71-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 관리되는 인스턴스 상태는 유틸리티 탐색기 내용 창에서 왼쪽에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-110">Health status for managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is displayed on the left side of the Utility Explorer content pane.</span></span>  
  
 <span data-ttu-id="bfd71-111">관리되는 인스턴스 상태 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-111">Managed Instance Health parameters are as follows:</span></span>  
  
-   <span data-ttu-id="bfd71-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스의 CPU 사용</span><span class="sxs-lookup"><span data-stu-id="bfd71-112">CPU utilization for the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="bfd71-113">데이터베이스 파일 사용</span><span class="sxs-lookup"><span data-stu-id="bfd71-113">Database file utilization.</span></span>  
  
-   <span data-ttu-id="bfd71-114">스토리지 볼륨 공간 사용</span><span class="sxs-lookup"><span data-stu-id="bfd71-114">Storage volume space utilization.</span></span>  
  
-   <span data-ttu-id="bfd71-115">컴퓨터에 대한 CPU 사용</span><span class="sxs-lookup"><span data-stu-id="bfd71-115">CPU utilization for the computer.</span></span>  
  
-   <span data-ttu-id="bfd71-116">각 매개 변수의 상태는 세 범주로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-116">Status for each parameter is divided into three categories:</span></span>  
  
-   <span data-ttu-id="bfd71-117">충분히 사용됨 – 리소스 사용 정책을 위반하지 않는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 관리되는 인스턴스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-117">Well-utilized - Number of managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] which are not violating resource utilization policies.</span></span>  
  
-   <span data-ttu-id="bfd71-118">사용 미달 - 리소스 사용 미달 정책을 위반하는 관리 리소스의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-118">Underutilized - Number of managed resources which are violating resource underutilization policies.</span></span>  
  
-   <span data-ttu-id="bfd71-119">사용 과다 - 리소스 사용 과다 정책을 위반하는 관리 리소스의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-119">Overutilized - Number of managed resources which are violating resource overutilization policies.</span></span>  
  
-   <span data-ttu-id="bfd71-120">사용 가능한 데이터 없음 - SQL Server 인스턴스가 방금 등록되어 첫 번째 데이터 컬렉션 작업이 아직 완료되지 않았거나 SQL Server의 관리되는 인스턴스 수집 및 UCP로 데이터 업로드 작업에 문제가 발생하여 SQL Server의 관리되는 인스턴스에 대한 사용 가능한 데이터가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-120">No Data Available - Data is not available for managed instances of SQL Server either because the instance of SQL Server has just been enrolled and the first data collection operation has not completed, or because there is a problem with the managed instance of SQL Server collecting and uploading data to the UCP.</span></span>  
  
 <span data-ttu-id="bfd71-121">각 상태 매개 변수에 대한 자세한 상태는 슬라이딩 표시기에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-121">Detailed status for each health parameter is listed in sliding indicators.</span></span> <span data-ttu-id="bfd71-122">슬라이딩 표시기의 오른쪽 부분에는 각 상태 범주에 얼마나 많은 관리되는 인스턴스가 해당되는지 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-122">The fraction to the right of the sliding indicators shows how many managed instances are in each status category.</span></span>  
  
 <span data-ttu-id="bfd71-123">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 관리되는 인스턴스 또는 데이터 계층 애플리케이션에 대한 필터링된 뷰를 만들려면 유틸리티 대시보드에서 해당 슬라이딩 표시기 옆에 있는 사용 범주 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-123">To create a filtered view of a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or a data-tier application, click on the link for a utilization category next to its sliding indicator in the Utility dashboard.</span></span> <span data-ttu-id="bfd71-124">예를 들어 **유틸리티 탐색기 내용** 창에서 **초과 사용 인스턴스 CPU**를 클릭할 경우, SSMS에서는 현재 정책 설정을 기반으로 CPU가 초과 사용된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 관리되는 인스턴스에 대한 필터링된 목록 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-124">For example, if you click on **Overutilized Instance CPU** in the **Utility Explorer Content** pane, SSMS creates a filtered list view of managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that have overutilized CPU based on current policy settings.</span></span>  
  
 <span data-ttu-id="bfd71-125">사용 범주 링크를 클릭할 때 유틸리티 탐색기 탐색 창의 해당 노드에 **(필터링됨)** 이 추가됩니다. 즉, **관리되는 인스턴스** 레이블이 **관리되는 인스턴스(필터링됨)** 로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-125">Notice that when you click on a link for a utilization category, the corresponding node in the Utility Explorer navigation pane is appended with **(filtered)** - that is, **Managed Instances** is labeled **Managed Instances (filtered)**.</span></span> <span data-ttu-id="bfd71-126">필터 설정을 보려면 탐색 창의 노드를 마우스 오른쪽 단추로 클릭하고 **필터**를 선택한 다음 **필터 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-126">To view filter settings, right-click on the node in the navigation pane and select **Filter**, then click on **Filter Settings**.</span></span> <span data-ttu-id="bfd71-127">필터 설정을 지우려면 탐색 창의 노드를 마우스 오른쪽 단추로 클릭하고 **필터**를 선택한 다음 **필터 제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-127">To clear filter settings, right-click on the node in the navigation pane and select **Filter**, then click on **Remove Filter**.</span></span>  
  
 <span data-ttu-id="bfd71-128">개별 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스의 상태를 보는 방법과 정책 구성 설정을 보거나 변경하는 방법은 [관리되는 인스턴스 세부 정보 &#40;SQL Server 유틸리티 &#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bfd71-128">For more information about viewing health status for individual instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], or to view or change policy configuration settings, see [Managed Instance Details &#40;SQL Server Utility&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="bfd71-129">유틸리티 요약</span><span class="sxs-lookup"><span data-stu-id="bfd71-129">Utility Summary</span></span>  
 <span data-ttu-id="bfd71-130">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유틸리티에서 관리되는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 관리되는 인스턴스 수와 데이터 계층 애플리케이션의 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-130">Displays the number of managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and the number of data-tier applications managed by the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility.</span></span>  
  
 <span data-ttu-id="bfd71-131">데이터 계층 애플리케이션 상태</span><span class="sxs-lookup"><span data-stu-id="bfd71-131">Data-tier Application Health</span></span>  
 <span data-ttu-id="bfd71-132">데이터 계층 애플리케이션의 상태는 유틸리티 탐색기 내용 창에서 오른쪽에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-132">Health status for data-tier applications is displayed on the right side of the Utility Explorer content pane.</span></span>  
  
 <span data-ttu-id="bfd71-133">데이터 계층 애플리케이션 상태 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-133">Data-tier Application Health parameters are as follows:</span></span>  
  
-   <span data-ttu-id="bfd71-134">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스의 CPU 사용</span><span class="sxs-lookup"><span data-stu-id="bfd71-134">CPU utilization for the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="bfd71-135">데이터베이스 파일 사용</span><span class="sxs-lookup"><span data-stu-id="bfd71-135">Database file utilization.</span></span>  
  
-   <span data-ttu-id="bfd71-136">스토리지 볼륨 공간 사용</span><span class="sxs-lookup"><span data-stu-id="bfd71-136">Storage volume space utilization.</span></span>  
  
-   <span data-ttu-id="bfd71-137">컴퓨터에 대한 CPU 사용</span><span class="sxs-lookup"><span data-stu-id="bfd71-137">CPU utilization for the computer.</span></span>  
  
 <span data-ttu-id="bfd71-138">각 매개 변수의 상태는 세 범주로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-138">Status for each parameter is divided into three categories:</span></span>  
  
-   <span data-ttu-id="bfd71-139">충분히 사용됨 - 리소스 사용 정책을 위반하지 않는 데이터 계층 애플리케이션의 수 입니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-139">Well-utilized - Number of data-tier applications which are not violating resource utilization policies.</span></span>  
  
-   <span data-ttu-id="bfd71-140">사용 과다 - 리소스 사용 과다 정책을 위반하지 않는 데이터 계층 애플리케이션의 수 입니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-140">Overutilized - Number of data-tier applications which are violating resource overutilization policies.</span></span>  
  
-   <span data-ttu-id="bfd71-141">사용 미달 - 리소스 사용 미달 정책을 위반하지 않는 데이터 계층 애플리케이션의 수 입니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-141">Underutilized - Number of data-tier applications which are violating resource underutilization policies.</span></span>  
  
-   <span data-ttu-id="bfd71-142">사용 가능한 데이터 없음 - 데이터 계층 애플리케이션을 포함하는 SQL Server의 관리되는 인스턴스가 데이터를 보고하지 않기 때문에 데이터 계층 애플리케이션에 대한 사용 가능한 데이터가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-142">No Data Available - Data is not available for data-tier applications because the managed instance of SQL Server that contains the data-tier application is not reporting data.</span></span>  
  
 <span data-ttu-id="bfd71-143">각 상태 매개 변수에 대한 자세한 상태는 슬라이딩 표시기에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-143">Detailed status for each health parameter is listed in sliding indicators.</span></span> <span data-ttu-id="bfd71-144">슬라이딩 표시기의 오른쪽 부분에는 각 상태 범주에 얼마나 많은 데이터 계층 애플리케이션이 해당되는지 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-144">The fraction to the right of the sliding indicators shows how many data-tier applications are in each status category.</span></span> <span data-ttu-id="bfd71-145">개별 데이터 계층 애플리케이션의 상태를 보는 방법과 정책 구성 설정을 보거나 변경하는 방법은 [배포된 데이터 계층 애플리케이션 세부 정보&#40;SQL Server 유틸리티&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bfd71-145">For more information about viewing health status for individual data-tier applications, or to view or change policy configuration settings, see [Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="bfd71-146">유틸리티 스토리지 사용 기록</span><span class="sxs-lookup"><span data-stu-id="bfd71-146">Utility Storage Utilization History</span></span>  
 <span data-ttu-id="bfd71-147">사용 기록은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유틸리티 대시보드 아래쪽의 시간 그래프에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-147">Utilization history is shown in a time graph at the bottom of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility dashboard.</span></span> <span data-ttu-id="bfd71-148">시간 데이터는 datetime 데이터 형식을 사용하여 UCP 로컬 날짜 및 시간을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-148">Note that time data show the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="bfd71-149">자세한 내용은 SQL Server 온라인 설명서의 [datetime(Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bfd71-149">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="bfd71-150">유틸리티 개체 모델을 사용할 때는 SSMS가 datetimeoffset 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-150">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="bfd71-151">자세한 내용은 SQL Server 온라인 설명서의 [datetimeoffset(Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bfd71-151">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="bfd71-152">표시 영역 왼쪽에 있는 라디오 단추를 사용하여 그래프의 보고 기간을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-152">Use the radio buttons to the left of the display area to change the reporting period for the graph.</span></span>  
  
 <span data-ttu-id="bfd71-153">보고 기간 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-153">Options for the reporting interval are:</span></span>  
  
-   <span data-ttu-id="bfd71-154">1일, 15분 간격으로 표시</span><span class="sxs-lookup"><span data-stu-id="bfd71-154">1 Day, displayed in 15-minute intervals.</span></span>  
  
-   <span data-ttu-id="bfd71-155">1주, 1일 간격으로 표시</span><span class="sxs-lookup"><span data-stu-id="bfd71-155">1 Week, displayed in 1-day intervals.</span></span>  
  
-   <span data-ttu-id="bfd71-156">1개월, 1주 간격으로 표시</span><span class="sxs-lookup"><span data-stu-id="bfd71-156">1 Month, displayed in 1-week intervals.</span></span>  
  
-   <span data-ttu-id="bfd71-157">1년, 1개월 간격으로 표시</span><span class="sxs-lookup"><span data-stu-id="bfd71-157">1 Year, displayed in 1-month intervals.</span></span>  
  
 <span data-ttu-id="bfd71-158">보고 간격을 변경하면 자동으로 데이터가 새로 고쳐집니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-158">After you make a change to the reporting interval, the data refreshes automatically.</span></span>  
  
 <span data-ttu-id="bfd71-159">유틸리티 스토리지 사용</span><span class="sxs-lookup"><span data-stu-id="bfd71-159">Utility Storage Utilization</span></span>  
 <span data-ttu-id="bfd71-160">대시보드 오른쪽 아래에 있는 스토리지 사용 원형 차트는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 관리되는 인스턴스를 포함하는 컴퓨터의 볼륨에서 사용된 공간과 사용 가능한 공간의 비율을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-160">In the bottom right of the dashboard, the storage utilization pie chart displays the ratio of used space to free space on volumes residing on computers that contain managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bfd71-161">여기에 표시되는 데이터는 15분마다 새로 고쳐집니다.</span><span class="sxs-lookup"><span data-stu-id="bfd71-161">Data for this display are refreshed every 15 minutes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd71-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bfd71-162">See Also</span></span>  
 <span data-ttu-id="bfd71-163">[유틸리티 탐색기를 사용하여 SQL Server 유틸리티 관리](../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="bfd71-163">[Use Utility Explorer to Manage the SQL Server Utility](../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md) </span></span>  
 <span data-ttu-id="bfd71-164">[SQL Server 유틸리티 &#40;SQL Server 인스턴스를 등록&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="bfd71-164">[Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="bfd71-165">리소스 상태 정책 정의 수정&#40;SQL Server 유틸리티&#41;</span><span class="sxs-lookup"><span data-stu-id="bfd71-165">Modify a Resource Health Policy Definition &#40;SQL Server Utility&#41;</span></span>](../relational-databases/manage/modify-a-resource-health-policy-definition-sql-server-utility.md)  
  
  
