---
title: 배포 된 데이터 계층 응용 프로그램 세부 정보 (SQL Server 유틸리티) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.UE.dac.details.F1
helpviewer_keywords:
- utility, management
- Utility
- SQL Server Utility [SQL Server]
- data-tier application [SQL Server], utility details
- Multi-server management [SQL Server]
ms.assetid: 79c41dd9-abcb-434e-9326-00a341d5c867
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 58d0933dcb7682210dde24c3c6d3a9a539d02b1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648560"
---
# <a name="deployed-data-tier-application-details-sql-server-utility"></a><span data-ttu-id="aa256-102">배포된 데이터 계층 애플리케이션 세부 정보(SQL Server 유틸리티)</span><span class="sxs-lookup"><span data-stu-id="aa256-102">Deployed Data-tier Application Details (SQL Server Utility)</span></span>
  <span data-ttu-id="aa256-103">유틸리티 탐색기의 배포된 데이터 계층 애플리케이션 뷰에 나오는 정보는 개별 데이터 계층 애플리케이션의 사용 데이터, CPU 사용 기록, 파일 수준의 스토리지 사용 세부 정보, 그리고 정책 임계 값을 확인 및 업데이트하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-103">Information in the Deployed Data-tier Applications view of Utility Explorer provides utilization data for individual data-tier applications, CPU utilization history, storage utilization details at the file level, and the ability to view and update policy thresholds.</span></span> <span data-ttu-id="aa256-104">정책 임계값은 데이터 계층 애플리케이션 수준에서 CPU 사용에 대해, 그리고 데이터베이스 데이터 파일 및 로그 파일에 대해 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-104">Policy thresholds can be controlled at the data-tier application level for CPU utilization and for database data files and log files.</span></span> <span data-ttu-id="aa256-105">개별 데이터 계층 애플리케이션의 속성 정보를 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-105">You can also view property details for individual data-tier applications.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="aa256-106">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="aa256-106">UI element list</span></span>  
 <span data-ttu-id="aa256-107">목록 보기</span><span class="sxs-lookup"><span data-stu-id="aa256-107">List view</span></span>  
 <span data-ttu-id="aa256-108">창 맨 위에 있는 목록 뷰에서는 개별 데이터 계층 애플리케이션에 대한 데이터를 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-108">The list view in the top pane displays data about individual data-tier applications.</span></span> <span data-ttu-id="aa256-109">상태 아이콘은 각 데이터 계층 애플리케이션의 상태 요약을 사용 범주별로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-109">Health state icons provide summary status for each data-tier application by utilization category:</span></span>  
  
-   <span data-ttu-id="aa256-110">녹색 확인 표시 - ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") - 리소스 사용 정책을 위반하지 않는 데이터 계층 애플리케이션의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-110">Green check - ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") - Number of data-tier application which are not violating resource utilization policies.</span></span> <span data-ttu-id="aa256-111">리소스 사용이 정상적입니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-111">Resources are well-utilized.</span></span>  
  
-   <span data-ttu-id="aa256-112">녹색 아래쪽 화살표 - ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") - 리소스가 사용 미달 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-112">Green down arrow - ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") - Resources are underutilized.</span></span>  
  
-   <span data-ttu-id="aa256-113">빨강 위쪽 화살표 - ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") - 리소스가 사용 과다 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-113">Red up arrow - ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") - Resources are overutilized.</span></span>  
  
 <span data-ttu-id="aa256-114">목록 뷰의 열 순서는 마우스로 왼쪽이나 오른쪽으로 끌어서 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-114">The sequence of columns in the list view can be changed by dragging them to the left or the right.</span></span> <span data-ttu-id="aa256-115">목록 뷰에서 열 머리글을 마우스 오른쪽 단추로 클릭하고 열을 선택하거나 선택을 취소하여 열을 추가하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-115">Columns in the list view can be added or deleted by right-clicking on the column headings and selecting or unselecting columns.</span></span> <span data-ttu-id="aa256-116">오른쪽 클릭 메뉴에도 정렬 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-116">The right-click menu also provides sort options.</span></span> <span data-ttu-id="aa256-117">열 이름 위쪽을 클릭하여 정렬을 활성화할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-117">Sorting can also be activated by clicking at the top of a column name.</span></span>  
  
 <span data-ttu-id="aa256-118">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유틸리티 목록 뷰의 필터 옵션에 액세스하려면 유틸리티 탐색기 탐색 창의 **배포된 데이터 계층 애플리케이션** 노드를 마우스 오른쪽 단추로 클릭하고 **필터**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-118">To access filter options for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility list view, right-click on the **Deployed Data-tier applications** node in the Utility Explorer navigation pane, and select **Filter**.</span></span> <span data-ttu-id="aa256-119">필터 설정이 구현된 후에는 유틸리티 탐색기의 **배포된 데이터 계층 애플리케이션** 노드가 **배포된 데이터 계층 애플리케이션(필터링됨)** 이라고 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-119">After filter settings have been implemented, the **Deployed Data-tier Applications** node in Utility Explorer will be labeled **Deployed Data-tier Applications (filtered)**.</span></span> <span data-ttu-id="aa256-120">자세한 내용은 [필터 설정&#40;개체 탐색기 및 유틸리티 탐색기&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa256-120">For more information, see [Filter Settings &#40;Object Explorer and Utility Explorer&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md).</span></span>  
  
 <span data-ttu-id="aa256-121">기본적으로 각 데이터 계층 애플리케이션의 상태 정보가 다음과 같은 열에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-121">By default, the following columns display health state information about each data-tier application.</span></span>  
  
-   <span data-ttu-id="aa256-122">이름 - 데이터 계층 애플리케이션의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-122">Name - the data-tier application name.</span></span>  
  
-   <span data-ttu-id="aa256-123">애플리케이션 CPU - 이 데이터 계층 애플리케이션의 프로세서 사용 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-123">Application CPU - Displays the health state of processor utilization for this data-tier application.</span></span> <span data-ttu-id="aa256-124">이 매개 변수의 상태는 데이터 계층 애플리케이션에 설정된 CPU 사용 정책과 일시적 리소스 평가 정책의 구성 설정에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-124">The health state for this parameter is determined according to CPU utilization policy set for the data-tier application and the configuration setting for volatile resource evaluation policy.</span></span> <span data-ttu-id="aa256-125">자세한 내용은 [CPU 사용 정책에서 노이즈 줄이기&#40;SQL Server 유틸리티&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa256-125">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
     <span data-ttu-id="aa256-126">이 데이터 계층 애플리케이션의 프로세서 사용 기록을 보거나 정책 제한을 확인 또는 변경하려면 **CPU 사용** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-126">To view the processor utilization history for this data-tier application, or to view or change the policy limits, click on the **CPU Utilization** tab.</span></span>  
  
-   <span data-ttu-id="aa256-127">컴퓨터 CPU - 컴퓨터 프로세서 사용 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-127">Computer CPU - Displays the health state of computer processor utilization.</span></span> <span data-ttu-id="aa256-128">이 매개 변수의 상태는 컴퓨터에 설정된 CPU 사용 정책과 일시적 리소스 평가 정책의 구성 설정에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-128">The health state for this parameter is determined according to CPU utilization policy set for the computer and the configuration setting for volatile resource evaluation policy.</span></span> <span data-ttu-id="aa256-129">자세한 내용은 [CPU 사용 정책에서 노이즈 줄이기&#40;SQL Server 유틸리티&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa256-129">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
     <span data-ttu-id="aa256-130">이 데이터 계층 애플리케이션의 프로세서 사용 기록을 보거나 정책 제한을 확인 또는 변경하려면 **CPU 사용** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-130">To view the processor utilization history for this data-tier application, or to view or change the policy limits, click on the **CPU Utilization** tab.</span></span>  
  
-   <span data-ttu-id="aa256-131">파일 공간 - 각 데이터 계층 애플리케이션의 파일 공간 사용 상태 요약을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-131">File Space - Displays a summary of health states of file space utilization for each data-tier application.</span></span>  
  
    -   <span data-ttu-id="aa256-132">녹색 확인 표시 - 모든 파일 그룹과 로그 파일 그룹이 사용 과다 또는 사용 미달 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-132">Green check - The health states for all filegroups and the log file group are neither overutilized or underutilized.</span></span>  
  
    -   <span data-ttu-id="aa256-133">녹색 아래쪽 화살표 - 하나 이상의 파일 그룹이나 로그 파일 그룹이 사용 미달 상태이며 사용 과다 상태인 파일 그룹이나 로그 파일 그룹이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-133">Green down arrow - The health state for at least one filegroup or log file group is underutilized, and no filegroup or log file group is overutilized.</span></span>  
  
    -   <span data-ttu-id="aa256-134">빨강 위쪽 화살표 - 하나 이상의 파일 그룹이나 로그 파일 그룹이 사용 과다 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-134">Red up arrow - The health state for at least one filegroup or the log file group is overutilized.</span></span> <span data-ttu-id="aa256-135">데이터베이스가 "응급" 상태인 경우 상태에는 사용 과다 상태의 로그 파일 공간이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-135">Note that if a database is in "emergency" state, the health state will display overutilized log file space.</span></span>  
  
     <span data-ttu-id="aa256-136">파일 공간 정책 제한을 보거나 변경하려면 **스토리지 사용** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-136">To view or change the file space policy limits, click on the **Storage Utilization** tab.</span></span>  
  
-   <span data-ttu-id="aa256-137">볼륨 공간 - 선택된 데이터 계층 애플리케이션에 속하는 데이터베이스를 포함하는 모든 볼륨의 볼륨 공간 사용 상태 요약이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-137">Volume Space - Displays a summary of the health states of volume space utilization for all volumes that contain databases belonging to the selected data-tier application.</span></span> <span data-ttu-id="aa256-138">사용 과다 상태의 볼륨이 있으면 목록 뷰에 볼륨 공간 상태가 사용 과다로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-138">If the health state of any volume is overutilized, then the volume space health state will be reported in the list view as overutilized.</span></span> <span data-ttu-id="aa256-139">사용 미달 상태의 볼륨이 있고 사용 초과인 볼륨이 없으면 목록 뷰에 볼륨 공간 상태가 사용 미달로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-139">If the health state of any volume is underutilized, and no volume is overutilized, then the volume space health state will be reported in the list view as underutilized.</span></span> <span data-ttu-id="aa256-140">이러한 경우가 아니면 목록 뷰에 볼륨 공간 상태가 정상 사용으로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-140">Otherwise, the volume space health state will be reported in the list view as well-utilized.</span></span> <span data-ttu-id="aa256-141">정책 제한을 보거나 변경하려면 **스토리지 사용** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-141">To view or change the policy limits, click on the **Storage Utilization** tab.</span></span>  
  
-   <span data-ttu-id="aa256-142">정책 유형 - 데이터 계층 애플리케이션에 "전역" 기본 정책과 "재정의" 사용자 지정 정책 중 어떤 것이 적용되는지 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-142">Policy Type - Indicates whether "Global" default policies or "Override" custom policies are in effect for the data-tier application.</span></span>  
  
-   <span data-ttu-id="aa256-143">인스턴스 이름 – 데이터 계층 애플리케이션을 호스팅하는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-143">Instance Name - Displays the name of the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that hosts the data-tier application.</span></span>  
  
 <span data-ttu-id="aa256-144">목록 뷰의 열 머리글 영역에서 오른쪽 클릭 메뉴를 사용하여 표시할 수 있는 다른 열은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-144">Other columns that can be displayed using the right-click menu in the column heading area of the list view:</span></span>  
  
-   <span data-ttu-id="aa256-145">데이터베이스 이름</span><span class="sxs-lookup"><span data-stu-id="aa256-145">Database Name</span></span>  
  
-   <span data-ttu-id="aa256-146">배포된 날짜</span><span class="sxs-lookup"><span data-stu-id="aa256-146">Deployed Date</span></span>  
  
-   <span data-ttu-id="aa256-147">신뢰: (True 또는 False)</span><span class="sxs-lookup"><span data-stu-id="aa256-147">Trustworthy: (True or False)</span></span>  
  
-   <span data-ttu-id="aa256-148">데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="aa256-148">Collation</span></span>  
  
-   <span data-ttu-id="aa256-149">호환성 수준: (예: Version100)</span><span class="sxs-lookup"><span data-stu-id="aa256-149">Compatibility Level: (for example, Version100)</span></span>  
  
-   <span data-ttu-id="aa256-150">암호화 사용: (True 또는 False)</span><span class="sxs-lookup"><span data-stu-id="aa256-150">Encryption Enabled: (True or False)</span></span>  
  
-   <span data-ttu-id="aa256-151">복구 모델: (단순, 전체 또는 대량 로그)</span><span class="sxs-lookup"><span data-stu-id="aa256-151">Recovery Model: (Simple, Full, or Bulk-Logged)</span></span>  
  
-   <span data-ttu-id="aa256-152">마지막 보고 시간: 이 열에는 datetime 데이터 형식을 사용하여 UCP 로컬 날짜 및 시간이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-152">Last Reported Time: This column shows the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="aa256-153">자세한 내용은 SQL Server 온라인 설명서의 [datetime(Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa256-153">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="aa256-154">유틸리티 개체 모델을 사용할 때는 SSMS가 datetimeoffset 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-154">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="aa256-155">자세한 내용은 SQL Server 온라인 설명서의 [datetimeoffset(Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa256-155">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="aa256-156">CPU 사용 탭</span><span class="sxs-lookup"><span data-stu-id="aa256-156">CPU Utilization tab</span></span>  
 <span data-ttu-id="aa256-157">CPU 사용 탭에는 데이터 계층 애플리케이션과 컴퓨터 CPU 사용의 기록 데이터 그래프가 함께 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-157">The CPU utilization tab shows side-by-side graphs of historical data for data-tier application and computer CPU utilization.</span></span>  
  
 <span data-ttu-id="aa256-158">그래프에는 표시 영역 오른쪽에 있는 라디오 단추에 지정된 간격에 따라 프로세서 사용 기록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-158">The graph displays the processor utilization history for the interval specified in the radio buttons on the right side of the display area.</span></span> <span data-ttu-id="aa256-159">표시 간격을 변경하고 데이터 집합을 새로 고치려면 목록에서 라디오 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-159">To change the display interval and refresh the data set, select a radio button from the list.</span></span>  
  
 <span data-ttu-id="aa256-160">다음과 같은 간격 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-160">Interval options are as follows:</span></span>  
  
-   <span data-ttu-id="aa256-161">1일, 15분 간격으로 표시</span><span class="sxs-lookup"><span data-stu-id="aa256-161">1 Day, displayed in 15-minute intervals.</span></span>  
  
-   <span data-ttu-id="aa256-162">1주, 1일 간격으로 표시</span><span class="sxs-lookup"><span data-stu-id="aa256-162">1 Week, displayed in 1-day intervals.</span></span>  
  
-   <span data-ttu-id="aa256-163">1개월, 1주 간격으로 표시</span><span class="sxs-lookup"><span data-stu-id="aa256-163">1 Month, displayed in 1-week intervals.</span></span>  
  
-   <span data-ttu-id="aa256-164">1년, 1개월 간격으로 표시</span><span class="sxs-lookup"><span data-stu-id="aa256-164">1 Year, displayed in 1-month intervals.</span></span>  
  
 <span data-ttu-id="aa256-165">스토리지 사용 탭</span><span class="sxs-lookup"><span data-stu-id="aa256-165">Storage Utilization tab</span></span>  
 <span data-ttu-id="aa256-166">스토리지 사용 탭에는 목록 뷰에 선택된 데이터 계층 애플리케이션에 속한 데이터베이스 파일과 로그 파일의 스토리지 사용 정보를 표시하는 트리 뷰가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-166">The Storage Utilization tab has a tree view that displays storage utilization details for database files and log files that belong to the data-tier application selected in the list view.</span></span> <span data-ttu-id="aa256-167">시간 데이터는 datetime 데이터 형식을 사용하여 UCP 로컬 날짜 및 시간을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-167">Note that time data show the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="aa256-168">자세한 내용은 SQL Server 온라인 설명서의 [datetime(Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa256-168">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="aa256-169">유틸리티 개체 모델을 사용할 때는 SSMS가 datetimeoffset 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-169">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="aa256-170">자세한 내용은 SQL Server 온라인 설명서의 [datetimeoffset(Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa256-170">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="aa256-171">표시는 파일 그룹별 또는 볼륨별로 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-171">Display can be grouped by filegroup or by volume.</span></span> <span data-ttu-id="aa256-172">파일 그룹 트리 뷰를 사용하려면 **파일 그룹화 방법:** 선택에서 **파일 그룹** 라디오 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-172">To use the filegroup tree view, select the **Filegroup** radio button in the **Group files by:** selection.</span></span>  
  
 <span data-ttu-id="aa256-173">스토리지 사용 기록 그래프에 표시되는 데이터는 트리 뷰에 선택된 노드에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-173">Data displayed in the graph of storage utilization history changes depending on the node selected in the tree view:</span></span>  
  
-   <span data-ttu-id="aa256-174">파일 그룹 노드를 선택하면 선택된 파일 그룹에 속한 모든 데이터 파일에 사용되는 파일 공간 그래프가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-174">Select the file group node to display a graph of file space used by all data files that belong to the selected file group.</span></span>  
  
-   <span data-ttu-id="aa256-175">로그 파일 노드를 선택하면 선택된 데이터베이스에 속한 모든 로그 파일에 사용되는 파일 공간 그래프가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-175">Select the log file node to display a graph of file space used by all log files that belong to the selected database.</span></span>  
  
-   <span data-ttu-id="aa256-176">데이터베이스 노드를 선택하면 선택된 데이터베이스에 속한 모든 데이터 파일과 모든 로그 파일에 사용되는 파일 공간을 더한 그래프가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-176">Select the database node to display a graph that adds file space used by all data files and all log files that belong to the selected database.</span></span>  
  
 <span data-ttu-id="aa256-177">개별 파일의 스토리지 사용 상태를 보려면 트리 뷰에서 파일 이름 옆에 있는 더하기 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-177">To view storage utilization status for individual files, click on the plus sign next to a file name in the tree view.</span></span>  
  
 <span data-ttu-id="aa256-178">상태 아이콘은 정책 임계값과 비교한 각 파일 그룹의 상태를 알기 쉽게 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-178">Health state icons provide at-a-glance status for each filegroup compared to policy thresholds:</span></span>  
  
-   <span data-ttu-id="aa256-179">녹색 확인 표시 - 파일 그룹의 하나 이상의 데이터 파일의 파일 공간 사용률이 사용 과다 또는 사용 미달이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-179">Green check - File space utilization for at least one data file in the filegroup is neither overutilized or underutilized.</span></span>  
  
-   <span data-ttu-id="aa256-180">녹색 아래쪽 화살표 - 파일 그룹에 파일 공간 사용률이 사용 미달인 데이터 파일이 하나 이상 있으며 사용 과다인 파일은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-180">Green down arrow - File space utilization for at least one data file in the filegroup is underutilized, and no files in the filegroup are overutilized.</span></span>  
  
-   <span data-ttu-id="aa256-181">빨강 위쪽 화살표 - 파일 그룹 내 모든 데이터 파일의 파일 공간 사용이 사용 과다입니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-181">Red up arrow - File space utilization for all data files in the filegroup are overutilized.</span></span> <span data-ttu-id="aa256-182">데이터베이스가 "응급" 상태인 경우 상태에는 사용 과다 상태의 로그 파일 공간이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-182">Note that if a database is in "emergency" state, the health state will display overutilized log file space.</span></span>  
  
 <span data-ttu-id="aa256-183">볼륨별로 파일을 보려면 **파일 그룹화 방법:** 선택에서 **볼륨** 라디오 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-183">To view files by volume, select the **Volume** radio button in the **Group files by:** selection.</span></span> <span data-ttu-id="aa256-184">스토리지 사용 기록 그래프에는 스토리지 볼륨의 모든 데이터 파일과 모든 로그 파일에 사용되는 파일 공간이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-184">The graph of storage utilization history displays file space used by all data files and all log files on the storage volume.</span></span> <span data-ttu-id="aa256-185">각 데이터베이스 데이터 파일과 로그 파일의 세부 정보를 보려면 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-185">Expand the tree to view details for individual database data files and log files.</span></span>  
  
 <span data-ttu-id="aa256-186">각 볼륨의 상태를 표시하는 데 다음 상태 아이콘이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-186">Status icons are used to provide status for each volume:</span></span>  
  
-   <span data-ttu-id="aa256-187">녹색 확인 표시 - 리소스 사용이 정상적입니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-187">Green check - Resources are well-utilized.</span></span>  
  
-   <span data-ttu-id="aa256-188">녹색 아래쪽 화살표 - 리소스가 사용 미달 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-188">Green down arrow - Resources are underutilized.</span></span>  
  
-   <span data-ttu-id="aa256-189">빨강 위쪽 화살표 - 리소스가 사용 과다 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-189">Red up arrow - Resources are overutilized.</span></span>  
  
 <span data-ttu-id="aa256-190">스토리지 사용 탭에서 각 파일 이름 옆의 계기에는 파일에 사용되는 공간 크기가 파일의 유효 용량을 기준으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-190">The gauge next to each file name on the Storage Utilization tab represents the amount of space used by the file relative to the effective capacity of the file.</span></span> <span data-ttu-id="aa256-191">계기 옆에 표시되는 백분율 값은 파일의 유효 용량을 기준으로 한 파일 사용 공간 크기의 비율입니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-191">The percentage value displayed next to the gauge is the ratio of the amount of space used by the file relative to the effective capacity of the file.</span></span> <span data-ttu-id="aa256-192">도구 설명에는 유효 용량과 비교하여 각 볼륨과 각 파일의 백분율을 계산하는 데 사용된 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-192">Tool tips provide data used to calculate percentages for each volume and each file compared to effective capacity.</span></span>  
  
 <span data-ttu-id="aa256-193">파일이 자동 증가하도록 구성되지 않은 경우 유효 용량은 파일에 할당된 공간의 양입니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-193">If the file is not configured to auto-grow, then the effective capacity is the amount of space allocated to the file.</span></span> <span data-ttu-id="aa256-194">파일이 자동 증가하도록 구성된 경우 유효 용량은 현재 파일에 할당된 공간의 양과 볼륨에서 현재 사용 가능한 공간의 양의 합계입니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-194">If the file is configured to auto-grow, then the effective capacity is the sum of the amount of space currently allocated to the file and the amount of free space currently available on the volume.</span></span>  
  
 <span data-ttu-id="aa256-195">스토리지 사용 정책은 데이터 파일과 로그 파일에 대해 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-195">Storage utilization policies can be configured for data files and for log files.</span></span> <span data-ttu-id="aa256-196">파일의 스토리지 사용 정책 임계 값을 보거나 변경하려면 스토리지 사용 창 아래쪽에 **파일 정책** 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-196">To view or change the storage utilization policy thresholds for files, click on the **File Policy** link at the bottom of the Storage Utilization pane.</span></span> <span data-ttu-id="aa256-197">스토리지 볼륨의 스토리지 사용 정책 임계 값을 보거나 변경하려면 스토리지 사용 창 아래쪽에 **볼륨 정책** 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-197">To view or change the storage utilization policy thresholds for a storage volume, click on the **Volume Policy** link at the bottom of the Storage Utilization pane.</span></span>  
  
 <span data-ttu-id="aa256-198">기본 정책 임계값을 덮어쓰려면 **기본 정책 재정의**라디오 단추를 클릭하고 상한과 하한에 값을 지정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-198">To override the default policy thresholds, click on the radio button to **Override the default policy**, specify values for the upper and lower limits, then click **OK**.</span></span>  
  
 <span data-ttu-id="aa256-199">정책 위반에 대한 허용 오차를 변경하는 방법에 대한 자세한 내용은 [CPU 사용 정책에서 노이즈 줄이기&#40;SQL Server 유틸리티&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa256-199">For more information about changing the tolerance for policy violations, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="aa256-200">속성 정보 탭</span><span class="sxs-lookup"><span data-stu-id="aa256-200">Property Details tab</span></span>  
 <span data-ttu-id="aa256-201">데이터 계층 애플리케이션에 대한 속성 정보에는 다음 범주가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-201">Property details listed for data-tier applications include the following categories:</span></span>  
  
-   <span data-ttu-id="aa256-202">데이터베이스 이름</span><span class="sxs-lookup"><span data-stu-id="aa256-202">Database Name</span></span>  
  
-   <span data-ttu-id="aa256-203">배포된 날짜</span><span class="sxs-lookup"><span data-stu-id="aa256-203">Deployed Date</span></span>  
  
-   <span data-ttu-id="aa256-204">신뢰: (True 또는 False)</span><span class="sxs-lookup"><span data-stu-id="aa256-204">Trustworthy: (True or False)</span></span>  
  
-   <span data-ttu-id="aa256-205">데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="aa256-205">Collation</span></span>  
  
-   <span data-ttu-id="aa256-206">호환성 수준: (예: Version100)</span><span class="sxs-lookup"><span data-stu-id="aa256-206">Compatibility Level: (for example, Version100)</span></span>  
  
-   <span data-ttu-id="aa256-207">암호화 사용: (True 또는 False)</span><span class="sxs-lookup"><span data-stu-id="aa256-207">Encryption Enabled: (True or False)</span></span>  
  
-   <span data-ttu-id="aa256-208">복구 모델: (단순, 전체 또는 대량 로그)</span><span class="sxs-lookup"><span data-stu-id="aa256-208">Recovery Model: (Simple, Full, or Bulk-Logged)</span></span>  
  
-   <span data-ttu-id="aa256-209">마지막 보고 시간: 이 열에는 datetime 데이터 형식을 사용하여 UCP 로컬 날짜 및 시간이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-209">Last Reported Time: This column shows the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="aa256-210">자세한 내용은 SQL Server 온라인 설명서의 [datetime(Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa256-210">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="aa256-211">유틸리티 개체 모델을 사용할 때는 SSMS가 datetimeoffset 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aa256-211">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="aa256-212">자세한 내용은 SQL Server 온라인 설명서의 [datetimeoffset(Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa256-212">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa256-213">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aa256-213">See Also</span></span>  
 <span data-ttu-id="aa256-214">[관리되는 인스턴스 세부 정보&#40;SQL Server 유틸리티&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="aa256-214">[Managed Instance Details &#40;SQL Server Utility&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md) </span></span>  
 <span data-ttu-id="aa256-215">[유틸리티 대시보드 &#40;SQL Server 유틸리티&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="aa256-215">[Utility Dashboard &#40;SQL Server Utility&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span></span>  
 <span data-ttu-id="aa256-216">[SQL Server 유틸리티에서 SQL Server 인스턴스 모니터링](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="aa256-216">[Monitor Instances of SQL Server in the SQL Server Utility](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="aa256-217">SQL Server 유틸리티 기능 및 태스크</span><span class="sxs-lookup"><span data-stu-id="aa256-217">SQL Server Utility Features and Tasks</span></span>](../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
