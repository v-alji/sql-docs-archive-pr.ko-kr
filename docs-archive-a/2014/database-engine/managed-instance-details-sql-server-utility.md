---
title: Managed Instance 세부 정보 (SQL Server 유틸리티) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 6e51b7bb-a733-4852-8c33-7f4dbdf931c2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f895f9978511ab7b2b40b3f161185a68a497b2eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738691"
---
# <a name="managed-instance-details-sql-server-utility"></a><span data-ttu-id="15b73-102">관리되는 인스턴스 세부 정보(SQL Server 유틸리티)</span><span class="sxs-lookup"><span data-stu-id="15b73-102">Managed Instance Details (SQL Server Utility)</span></span>
  <span data-ttu-id="15b73-103">유틸리티 탐색기의 관리되는 인스턴스 뷰에 나오는 정보는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 개별 인스턴스에 대한 사용 데이터, CPU 사용 기록, 파일 수준의 스토리지 사용 세부 정보, 그리고 정책 임계 값을 확인 및 업데이트하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-103">Information in the Managed Instances view of Utility Explorer provides utilization data for individual instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], CPU utilization history, storage utilization details at the file level, and the ability to view and update policy thresholds.</span></span> <span data-ttu-id="15b73-104">정책 임계 값은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스 수준, 컴퓨터, 데이터베이스 파일과 로그 파일, 그리고 스토리지 볼륨 수준에서 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-104">Policy thresholds can be controlled at the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance level, for a computer, for database files and log files, and at the level of storage volumes.</span></span> <span data-ttu-id="15b73-105">개별 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 관리되는 인스턴스 속성 정보를 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-105">You can also view property details for individual managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="15b73-106">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="15b73-106">UI element list</span></span>  
 <span data-ttu-id="15b73-107">목록 보기</span><span class="sxs-lookup"><span data-stu-id="15b73-107">List view</span></span>  
 <span data-ttu-id="15b73-108">창 맨 위에 있는 목록 뷰에는 개별 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 대한 정보가 ComputerName\InstanceName 형식의 행으로 나열 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-108">The list view in the top pane displays data about individual instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] listed in rows by ComputerName\InstanceName.</span></span>  
  
 <span data-ttu-id="15b73-109">상태 아이콘은 각 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스의 상태 요약을 사용 범주별로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-109">Health state icons provide summary status for each instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by utilization category:</span></span>  
  
-   <span data-ttu-id="15b73-110">녹색 확인 표시 - ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") - 리소스 사용 정책을 위반하지 않는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 관리형 인스턴스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-110">Green check - ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") - Number of managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] which are not violating resource utilization policies.</span></span> <span data-ttu-id="15b73-111">리소스 사용이 정상적입니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-111">Resources are well-utilized.</span></span>  
  
-   <span data-ttu-id="15b73-112">녹색 아래쪽 화살표 - ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") - 리소스가 사용 미달 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-112">Green down arrow - ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") - Resources are underutilized.</span></span>  
  
-   <span data-ttu-id="15b73-113">빨강 위쪽 화살표 - ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") - 리소스가 사용 과다 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-113">Red up arrow - ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") - Resources are overutilized.</span></span>  
  
 <span data-ttu-id="15b73-114">목록 뷰의 열 순서는 마우스로 왼쪽이나 오른쪽으로 끌어서 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-114">The sequence of columns in the list view can be changed by dragging them to the left or the right.</span></span> <span data-ttu-id="15b73-115">목록 뷰에서 열 머리글을 마우스 오른쪽 단추로 클릭하고 열을 선택하거나 선택을 취소하여 열을 추가하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-115">Columns in the list view can be added or deleted by right-clicking on the column headings and selecting or unselecting columns.</span></span> <span data-ttu-id="15b73-116">오른쪽 클릭 메뉴에도 정렬 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-116">The right-click menu also provides sort options.</span></span> <span data-ttu-id="15b73-117">열 이름 위쪽을 클릭하여 정렬을 활성화할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-117">Sorting can also be activated by clicking at the top of a column name.</span></span>  
  
 <span data-ttu-id="15b73-118">유틸리티 목록 뷰의 필터 옵션에 액세스하려면 유틸리티 탐색기 탐색 창의 **관리되는 인스턴스** 노드를 마우스 오른쪽 단추로 클릭하고 **필터**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-118">To access filter options for the Utility list view, right-click on the **Managed Instances** node in the Utility Explorer navigation pane, and select **Filter**.</span></span> <span data-ttu-id="15b73-119">필터 설정이 구현된 후에는 유틸리티 탐색기의 **관리되는 인스턴스** 노드가 **관리되는 인스턴스(필터링됨)** 라고 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-119">After filter settings have been implemented, the **Managed Instances** node in Utility Explorer will be labeled **Managed Instances (filtered)**.</span></span> <span data-ttu-id="15b73-120">자세한 내용은 [필터 설정&#40;개체 탐색기 및 유틸리티 탐색기&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15b73-120">For more information, see [Filter Settings &#40;Object Explorer and Utility Explorer&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md).</span></span>  
  
 <span data-ttu-id="15b73-121">기본적으로 각 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 관리되는 인스턴스 상태 정보가 다음과 같은 열에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-121">By default, the following columns display health state information about each managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="15b73-122">인스턴스 CPU – 이 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에 할당된 프로세서 사용률의 성능 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-122">Instance CPU - Displays the health state of processor utilization allocated to this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="15b73-123">이 매개 변수의 상태는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 설정된 CPU 사용 정책과 일시적 리소스 평가 정책의 구성 설정에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-123">The health state for this parameter is determined according to CPU utilization policy set for the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and the configuration setting for volatile resource evaluation policy.</span></span> <span data-ttu-id="15b73-124">자세한 내용은 [CPU 사용 정책에서 노이즈 줄이기&#40;SQL Server 유틸리티&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15b73-124">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
     <span data-ttu-id="15b73-125">이 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스의 프로세서 사용 기록을 보거나 정책 제한을 확인 또는 변경하려면 **CPU 사용** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-125">To view the processor utilization history for this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], or to view or change the policy limits, click on the **CPU Utilization** tab.</span></span>  
  
-   <span data-ttu-id="15b73-126">컴퓨터 CPU - 컴퓨터 프로세서 사용 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-126">Computer CPU - Displays the health state of computer processor utilization.</span></span> <span data-ttu-id="15b73-127">이 매개 변수의 상태는 컴퓨터에 설정된 CPU 사용 정책과 일시적 리소스 평가 정책의 구성 설정에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-127">The health state for this parameter is determined according to CPU utilization policy set for the computer and the configuration setting for volatile resource evaluation policy.</span></span> <span data-ttu-id="15b73-128">자세한 내용은 [CPU 사용 정책에서 노이즈 줄이기&#40;SQL Server 유틸리티&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15b73-128">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
     <span data-ttu-id="15b73-129">이 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스의 프로세서 사용 기록을 보거나 정책 제한을 확인 또는 변경하려면 **CPU 사용** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-129">To view the processor utilization history for this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], or to view or change the policy limits, click on the **CPU Utilization** tab.</span></span>  
  
-   <span data-ttu-id="15b73-130">파일 공간 - 선택된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에 속하는 모든 데이터베이스에 대한 파일 공간 사용률 상태의 요약을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-130">File Space - Displays a summary of health states of file space utilization for all databases that belong to the selected instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="15b73-131">초과 사용 상태의 데이터베이스가 있으면 파일 공간 상태가 목록 뷰에 초과 사용으로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-131">If the health state of any database is overutilized, then the file space health state will be reported in the list view as overutilized.</span></span> <span data-ttu-id="15b73-132">미달 사용 상태의 데이터베이스가 있고 초과 사용 상태의 데이터베이스가 없으면 파일 공간 상태가 목록 뷰에 미달 사용으로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-132">If the health state of any database is underutilized, and no database is overutilized, then the file space health state will be reported in the list view as underutilized.</span></span> <span data-ttu-id="15b73-133">이러한 경우가 아니면 목록 뷰에 파일 공간 상태가 정상 사용으로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-133">Otherwise, the file space health state will be reported in the list view as well-utilized.</span></span> <span data-ttu-id="15b73-134">정책 제한을 보거나 변경하려면 **스토리지 사용** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-134">To view or change the policy limits, click on the **Storage Utilization** tab.</span></span>  
  
-   <span data-ttu-id="15b73-135">볼륨 공간 – 선택된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에 속하는 데이터베이스를 포함하는 모든 볼륨의 볼륨 공간 사용 상태 요약이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-135">Volume Space - Displays a summary of the health states of volume space utilization for all volumes that contain databases belonging to the selected instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="15b73-136">사용 과다 상태의 볼륨이 있으면 목록 뷰에 볼륨 공간 상태가 사용 과다로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-136">If the health state of any volume is overutilized, then the volume space health state will be reported in the list view as overutilized.</span></span> <span data-ttu-id="15b73-137">사용 미달 상태의 볼륨이 있고 사용 초과인 볼륨이 없으면 목록 뷰에 볼륨 공간 상태가 사용 미달로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-137">If the health state of any volume is underutilized, and no volume is overutilized, then the volume space health state will be reported in the list view as underutilized.</span></span> <span data-ttu-id="15b73-138">이러한 경우가 아니면 목록 뷰에 볼륨 공간 상태가 정상 사용으로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-138">Otherwise, the volume space health state will be reported in the list view as well-utilized.</span></span> <span data-ttu-id="15b73-139">정책 제한을 보거나 변경하려면 **스토리지 사용** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-139">To view or change the policy limits, click on the **Storage Utilization** tab.</span></span>  
  
-   <span data-ttu-id="15b73-140">정책 유형 - [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 관리되는 인스턴스에 "전역" 기본 정책과 "덮어쓰기" 사용자 지정 정책 중 어떤 것이 적용되는지 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-140">Policy Type - Indicates whether "Global" default policies or "Override" custom policies are in effect for the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="15b73-141">목록 뷰의 열 머리글 영역에서 오른쪽 클릭 메뉴를 사용하여 표시할 수 있는 다른 열은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-141">Other columns that can be displayed using the right-click menu in the column heading area of the list view:</span></span>  
  
-   <span data-ttu-id="15b73-142">프로세서 이름:</span><span class="sxs-lookup"><span data-stu-id="15b73-142">Processor Name:</span></span>  
  
-   <span data-ttu-id="15b73-143">프로세서 속도(MHz):</span><span class="sxs-lookup"><span data-stu-id="15b73-143">Processor Speed (MHz):</span></span>  
  
-   <span data-ttu-id="15b73-144">프로세서 수:</span><span class="sxs-lookup"><span data-stu-id="15b73-144">Processor Count:</span></span>  
  
-   <span data-ttu-id="15b73-145">실제 메모리(MB):</span><span class="sxs-lookup"><span data-stu-id="15b73-145">Physical Memory (MB):</span></span>  
  
-   <span data-ttu-id="15b73-146">운영 체제 버전:</span><span class="sxs-lookup"><span data-stu-id="15b73-146">Operating System Version:</span></span>  
  
-   <span data-ttu-id="15b73-147">SQL Server 버전:</span><span class="sxs-lookup"><span data-stu-id="15b73-147">SQL Server Version:</span></span>  
  
-   <span data-ttu-id="15b73-148">SQL Server 에디션:</span><span class="sxs-lookup"><span data-stu-id="15b73-148">SQL Server Edition:</span></span>  
  
-   <span data-ttu-id="15b73-149">클러스터형: (True 또는 False)</span><span class="sxs-lookup"><span data-stu-id="15b73-149">Clustered: (True or False)</span></span>  
  
-   <span data-ttu-id="15b73-150">백업 디렉터리:</span><span class="sxs-lookup"><span data-stu-id="15b73-150">Backup Directory:</span></span>  
  
-   <span data-ttu-id="15b73-151">데이터 정렬:</span><span class="sxs-lookup"><span data-stu-id="15b73-151">Collation:</span></span>  
  
-   <span data-ttu-id="15b73-152">대/소문자 구분: (True 또는 False)</span><span class="sxs-lookup"><span data-stu-id="15b73-152">Case Sensitive: (True or False)</span></span>  
  
-   <span data-ttu-id="15b73-153">언어:</span><span class="sxs-lookup"><span data-stu-id="15b73-153">Language:</span></span>  
  
-   <span data-ttu-id="15b73-154">마지막 보고 시간: 이 열에는 datetime 데이터 형식을 사용하여 UCP 로컬 날짜 및 시간이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-154">Last Reported Time: This column shows the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="15b73-155">자세한 내용은 SQL Server 온라인 설명서의 [datetime(Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15b73-155">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="15b73-156">유틸리티 개체 모델을 사용할 때는 SSMS가 datetimeoffset 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-156">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="15b73-157">자세한 내용은 SQL Server 온라인 설명서의 [datetimeoffset(Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15b73-157">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="15b73-158">CPU 사용 탭</span><span class="sxs-lookup"><span data-stu-id="15b73-158">CPU Utilization tab</span></span>  
 <span data-ttu-id="15b73-159">CPU 사용 탭에는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스와 컴퓨터 CPU 사용의 기록 데이터 그래프가 함께 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-159">The CPU utilization tab shows side-by-side graphs of historical data for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance and computer CPU utilization.</span></span>  
  
 <span data-ttu-id="15b73-160">그래프에는 표시 영역 오른쪽에 있는 라디오 단추에 지정된 간격에 따라 프로세서 사용 기록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-160">The graph displays the processor utilization history for the interval specified in the radio buttons on the right side of the display area.</span></span> <span data-ttu-id="15b73-161">표시 간격을 변경하고 데이터 집합을 새로 고치려면 목록에서 라디오 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-161">To change the display interval and refresh the data set, select a radio button from the list.</span></span>  
  
 <span data-ttu-id="15b73-162">다음과 같은 간격 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-162">Interval options are as follows:</span></span>  
  
-   <span data-ttu-id="15b73-163">1일, 15분 간격으로 표시</span><span class="sxs-lookup"><span data-stu-id="15b73-163">1 Day, displayed in 15-minute intervals.</span></span>  
  
-   <span data-ttu-id="15b73-164">1주, 1일 간격으로 표시</span><span class="sxs-lookup"><span data-stu-id="15b73-164">1 Week, displayed in 1-day intervals.</span></span>  
  
-   <span data-ttu-id="15b73-165">1개월, 1주 간격으로 표시</span><span class="sxs-lookup"><span data-stu-id="15b73-165">1 Month, displayed in 1-week intervals.</span></span>  
  
-   <span data-ttu-id="15b73-166">1년, 1개월 간격으로 표시</span><span class="sxs-lookup"><span data-stu-id="15b73-166">1 Year, displayed in 1-month intervals.</span></span>  
  
 <span data-ttu-id="15b73-167">스토리지 사용 탭</span><span class="sxs-lookup"><span data-stu-id="15b73-167">Storage Utilization tab</span></span>  
 <span data-ttu-id="15b73-168">스토리지 사용 탭에는 스토리지 사용 세부 정보를 표시하는 트리 뷰가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-168">The Storage Utilization tab has a tree view that displays storage utilization details.</span></span> <span data-ttu-id="15b73-169">시간 데이터는 datetime 데이터 형식을 사용하여 UCP 로컬 날짜 및 시간을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-169">Note that time data show the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="15b73-170">자세한 내용은 SQL Server 온라인 설명서의 [datetime(Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15b73-170">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="15b73-171">유틸리티 개체 모델을 사용할 때는 SSMS가 datetimeoffset 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-171">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="15b73-172">자세한 내용은 SQL Server 온라인 설명서의 [datetimeoffset(Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15b73-172">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="15b73-173">표시는 데이터베이스별 또는 볼륨별로 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-173">Display can be grouped by database or by volume.</span></span> <span data-ttu-id="15b73-174">데이터베이스 트리 뷰를 사용하려면 **파일 그룹화 방법:** 선택에서 **데이터베이스** 라디오 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-174">To use the database tree view, select the **Database** radio button in the **Group files by:** selection.</span></span> <span data-ttu-id="15b73-175">개별 데이터베이스 파일의 스토리지 사용 상태를 보려면 트리 뷰에서 데이터베이스 이름 옆에 있는 더하기 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-175">To view storage utilization status for individual database files, click on the plus sign next to a database name in the tree view.</span></span> <span data-ttu-id="15b73-176">나열되는 데이터베이스 파일에는 목록 뷰에서 선택한 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 관리되는 인스턴스에 속한 모든 시스템 및 사용자 데이터베이스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-176">The database files listed include all system and user databases that belong to the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] you selected in the list view.</span></span>  
  
 <span data-ttu-id="15b73-177">트리 구조는 스토리지의 계층과 상응합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-177">The tree structure corresponds to the storage hierarchy.</span></span> <span data-ttu-id="15b73-178">트리 뷰의 루트 노드는 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-178">The root node in the tree view is the database.</span></span> <span data-ttu-id="15b73-179">트리 뷰의 다음 수준에는 파일 그룹 노드 한 개 또는 데이터베이스에 속한 여러 노드, 그리고 데이터베이스에 속한 로그에 대한 로그 파일 노드 한 개가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-179">The next level of the tree view contains a filegroup node or nodes that belong to the database, and a log file node for the logs that belong to the database.</span></span> <span data-ttu-id="15b73-180">다음 수준에는 파일 그룹에 속한 데이터 파일이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-180">The next level contains the data files that belong to the filegroup.</span></span>  
  
 <span data-ttu-id="15b73-181">스토리지 사용 기록 그래프에 표시되는 데이터는 트리 뷰에 선택된 노드에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-181">Data displayed in the graph of storage utilization history changes depending on the node selected in the tree view:</span></span>  
  
-   <span data-ttu-id="15b73-182">파일 그룹 노드를 선택하면 선택된 파일 그룹에 속한 모든 데이터 파일에 사용되는 파일 공간 그래프가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-182">Select the file group node to display a graph of file space used by all data files that belong to the selected file group.</span></span>  
  
-   <span data-ttu-id="15b73-183">로그 파일 노드를 선택하면 선택된 데이터베이스에 속한 모든 로그 파일에 사용되는 파일 공간 그래프가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-183">Select the log file node to display a graph of file space used by all log files that belong to the selected database.</span></span>  
  
-   <span data-ttu-id="15b73-184">데이터베이스 노드를 선택하면 선택된 데이터베이스에 속한 모든 데이터 파일과 모든 로그 파일에 사용되는 파일 공간을 더한 그래프가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-184">Select the database node to display a graph that adds file space used by all data files and all log files that belong to the selected database.</span></span>  
  
 <span data-ttu-id="15b73-185">상태 아이콘은 데이터베이스 파일, 파일 그룹 및 로그 파일에 대한 알아보기 쉬운 요약입니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-185">Health state icons provide at-a-glance status for database files, filegroups, and log files:</span></span>  
  
 <span data-ttu-id="15b73-186">데이터베이스:</span><span class="sxs-lookup"><span data-stu-id="15b73-186">For databases:</span></span>  
  
-   <span data-ttu-id="15b73-187">녹색 확인 표시 - 모든 파일 그룹과 로그 파일이 사용 과다 또는 사용 미달 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-187">Green check - Health states of all filegroups and log files a neither overutilized or underutilized.</span></span>  
  
-   <span data-ttu-id="15b73-188">녹색 아래쪽 화살표 - 하나 이상의 파일 그룹이나 로그 파일이 사용 미달 상태이며 사용 과다 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-188">Green down arrow - Health states of at least one filegroup or log file is underutilized, and no health states are overutilized.</span></span>  
  
-   <span data-ttu-id="15b73-189">빨강 위쪽 화살표 - 하나 이상의 파일 그룹이나 로그 파일이 사용 과다 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-189">Red up arrow - The health state of at least one filegroup or log file is overutilized.</span></span>  
  
 <span data-ttu-id="15b73-190">파일 그룹 및 로그 파일:</span><span class="sxs-lookup"><span data-stu-id="15b73-190">For filegroups and log files:</span></span>  
  
-   <span data-ttu-id="15b73-191">녹색 확인 표시 - 파일 그룹 내 모든 파일의 파일 공간 사용이 사용 과다 또는 사용 미달이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-191">Green check - File space utilization for all files in the filegroup are neither overutilized or underutilized.</span></span>  
  
-   <span data-ttu-id="15b73-192">녹색 아래쪽 화살표 - 파일 그룹에서 하나 이상 파일의 파일 공간 사용이 사용 미달이며 파일 그룹에 사용 과다인 파일이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-192">Green down arrow - File space utilization for at least one file in the filegroup is underutilized, and no files in the filegroup are overutilized.</span></span>  
  
-   <span data-ttu-id="15b73-193">빨강 위쪽 화살표 - 파일 그룹 내 모든 데이터 파일의 파일 공간 사용이 사용 과다입니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-193">Red up arrow - File space utilization for all data files in the filegroup are overutilized.</span></span>  
  
 <span data-ttu-id="15b73-194">볼륨별로 파일을 보려면 **파일 그룹화 방법:** 선택에서 **볼륨** 라디오 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-194">To view files by volume, select the **Volume** radio button in the **Group files by:** selection.</span></span> <span data-ttu-id="15b73-195">스토리지 사용 기록 그래프에는 스토리지 볼륨의 모든 데이터 파일과 모든 로그 파일에 사용되는 파일 공간이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-195">The graph of storage utilization history displays file space used by all data files and all log files on the storage volume.</span></span> <span data-ttu-id="15b73-196">각 데이터베이스 데이터 파일과 로그 파일의 세부 정보를 보려면 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-196">Expand the tree to view details for individual database data files and log files.</span></span>  
  
 <span data-ttu-id="15b73-197">각 볼륨의 상태를 표시하는 데 다음 상태 아이콘이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-197">Status icons are used to provide status for each volume:</span></span>  
  
-   <span data-ttu-id="15b73-198">녹색 확인 표시 - 리소스 사용이 정상적입니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-198">Green check - Resources are well-utilized.</span></span>  
  
-   <span data-ttu-id="15b73-199">녹색 아래쪽 화살표 - 리소스가 사용 미달 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-199">Green down arrow - Resources are underutilized.</span></span>  
  
-   <span data-ttu-id="15b73-200">빨강 위쪽 화살표 - 리소스가 사용 과다 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-200">Red up arrow - Resources are overutilized.</span></span>  
  
 <span data-ttu-id="15b73-201">스토리지 사용 탭에서 각 파일 이름 옆의 계기에는 파일에 사용되는 공간 크기가 파일의 유효 용량을 기준으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-201">The gauge next to each file name on the Storage Utilization tab represents the amount of space used by the file relative to the effective capacity of the file.</span></span> <span data-ttu-id="15b73-202">계기 옆에 표시되는 백분율 값은 파일의 유효 용량을 기준으로 한 파일 사용 공간 크기의 비율입니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-202">The percentage value displayed next to the gauge is the ratio of the amount of space used by the file relative to the effective capacity of the file.</span></span> <span data-ttu-id="15b73-203">도구 설명에는 유효 용량과 비교하여 각 볼륨과 각 파일의 백분율을 계산하는 데 사용된 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-203">Tool tips provide data used to calculate percentages for each volume and each file compared to effective capacity.</span></span>  
  
 <span data-ttu-id="15b73-204">파일이 자동 증가하도록 구성되지 않은 경우 유효 용량은 파일에 할당된 공간의 양입니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-204">If the file is not configured to auto-grow, then the effective capacity is the amount of space allocated to the file.</span></span> <span data-ttu-id="15b73-205">파일이 자동 증가하도록 구성된 경우 유효 용량은 현재 파일에 할당된 공간의 양과 볼륨에서 현재 사용 가능한 공간의 양의 합계입니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-205">If the file is configured to auto-grow, then the effective capacity is the sum of the amount of space currently allocated to the file and the amount of free space currently available on the volume.</span></span>  
  
 <span data-ttu-id="15b73-206">스토리지 사용 정책은 데이터 파일과 로그 파일에 대해 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-206">Storage utilization policies can be configured for data files and for log files.</span></span> <span data-ttu-id="15b73-207">파일의 스토리지 사용 정책 임계 값을 보거나 변경하려면 스토리지 사용 창 아래쪽에 **파일 정책** 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-207">To view or change the storage utilization policy thresholds for files, click on the **File Policy** link at the bottom of the Storage Utilization pane.</span></span> <span data-ttu-id="15b73-208">스토리지 볼륨의 스토리지 사용 정책 임계 값을 보거나 변경하려면 스토리지 사용 창 아래쪽에 **볼륨 정책** 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-208">To view or change the storage utilization policy thresholds for a storage volume, click on the **Volume Policy** link at the bottom of the Storage Utilization pane.</span></span>  
  
 <span data-ttu-id="15b73-209">기본 정책 임계값을 덮어쓰려면 **기본 정책 재정의**라디오 단추를 클릭하고 상한과 하한에 값을 지정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-209">To override the default policy thresholds, click on the radio button to **Override the default policy**, specify values for the upper and lower limits, then click **OK**.</span></span>  
  
 <span data-ttu-id="15b73-210">정책 위반에 대한 허용 오차를 변경하는 방법에 대한 자세한 내용은 [CPU 사용 정책에서 노이즈 줄이기&#40;SQL Server 유틸리티&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15b73-210">For more information about changing the tolerance for policy violations, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="15b73-211">속성 정보 탭</span><span class="sxs-lookup"><span data-stu-id="15b73-211">Property Details tab</span></span>  
 <span data-ttu-id="15b73-212">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 대한 속성 정보에는 다음 범주가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b73-212">Property details listed for instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] include the following categories:</span></span>  
  
-   <span data-ttu-id="15b73-213">프로세서 이름:</span><span class="sxs-lookup"><span data-stu-id="15b73-213">Processor Name:</span></span>  
  
-   <span data-ttu-id="15b73-214">프로세서 속도(MHz):</span><span class="sxs-lookup"><span data-stu-id="15b73-214">Processor Speed (MHz):</span></span>  
  
-   <span data-ttu-id="15b73-215">프로세서 수:</span><span class="sxs-lookup"><span data-stu-id="15b73-215">Processor Count:</span></span>  
  
-   <span data-ttu-id="15b73-216">실제 메모리(MB):</span><span class="sxs-lookup"><span data-stu-id="15b73-216">Physical Memory (MB):</span></span>  
  
-   <span data-ttu-id="15b73-217">운영 체제 버전:</span><span class="sxs-lookup"><span data-stu-id="15b73-217">Operating System Version:</span></span>  
  
-   <span data-ttu-id="15b73-218">SQL Server 버전:</span><span class="sxs-lookup"><span data-stu-id="15b73-218">SQL Server Version:</span></span>  
  
-   <span data-ttu-id="15b73-219">SQL Server 에디션:</span><span class="sxs-lookup"><span data-stu-id="15b73-219">SQL Server Edition:</span></span>  
  
-   <span data-ttu-id="15b73-220">클러스터형: (True 또는 False)</span><span class="sxs-lookup"><span data-stu-id="15b73-220">Clustered: (True or False)</span></span>  
  
-   <span data-ttu-id="15b73-221">백업 디렉터리:</span><span class="sxs-lookup"><span data-stu-id="15b73-221">Backup Directory:</span></span>  
  
-   <span data-ttu-id="15b73-222">데이터 정렬:</span><span class="sxs-lookup"><span data-stu-id="15b73-222">Collation:</span></span>  
  
-   <span data-ttu-id="15b73-223">대/소문자 구분: (True 또는 False)</span><span class="sxs-lookup"><span data-stu-id="15b73-223">Case Sensitive: (True or False)</span></span>  
  
-   <span data-ttu-id="15b73-224">언어:</span><span class="sxs-lookup"><span data-stu-id="15b73-224">Language:</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b73-225">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15b73-225">See Also</span></span>  
 <span data-ttu-id="15b73-226">[배포된 데이터 계층 애플리케이션 세부 정보&#40;SQL Server 유틸리티&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="15b73-226">[Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span></span>  
 <span data-ttu-id="15b73-227">[유틸리티 대시보드 &#40;SQL Server 유틸리티&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="15b73-227">[Utility Dashboard &#40;SQL Server Utility&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span></span>  
 <span data-ttu-id="15b73-228">[SQL Server 유틸리티에서 SQL Server 인스턴스 모니터링](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="15b73-228">[Monitor Instances of SQL Server in the SQL Server Utility](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md) </span></span>  
 <span data-ttu-id="15b73-229">[SQL Server 유틸리티 기능 및 태스크](../relational-databases/manage/sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="15b73-229">[SQL Server Utility Features and Tasks](../relational-databases/manage/sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="15b73-230">SQL Server 유틸리티 문제 해결</span><span class="sxs-lookup"><span data-stu-id="15b73-230">Troubleshoot the SQL Server Utility</span></span>](../../2014/database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
