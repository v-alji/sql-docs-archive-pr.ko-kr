---
title: 테이블 또는 인덱스에서 압축 해제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- data compression [SQL Server], disabling
ms.assetid: bda1e452-397b-4757-82a4-181217361589
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 80b5775d3b6f7a3f47ab75c5348b556c17b6e676
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659472"
---
# <a name="disable-compression-on-a-table-or-index"></a><span data-ttu-id="876be-102">테이블 또는 인덱스에서 압축 해제</span><span class="sxs-lookup"><span data-stu-id="876be-102">Disable Compression on a Table or Index</span></span>
  <span data-ttu-id="876be-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 테이블이나 인덱스에서 압축을 해제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-103">This topic describes how to disable compression on a table or index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="876be-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="876be-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="876be-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="876be-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="876be-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="876be-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="876be-107">보안</span><span class="sxs-lookup"><span data-stu-id="876be-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="876be-108">**다음을 사용하여 테이블이나 인덱스에서 압축 해제**</span><span class="sxs-lookup"><span data-stu-id="876be-108">**To disable compression on a table or index, using:**</span></span>  
  
     [<span data-ttu-id="876be-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="876be-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="876be-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="876be-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="876be-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="876be-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="876be-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="876be-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="876be-113">테이블이 힙인 경우 ONLINE 모드의 다시 작성 작업은 단일 스레드 작업이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="876be-113">If the table is a heap, the rebuild operation for ONLINE mode will be single threaded.</span></span> <span data-ttu-id="876be-114">다중 스레드 힙 다시 작성 작업에는 OFFLINE 모드를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="876be-114">Use OFFLINE mode for a multi-threaded heap rebuild operation.</span></span> <span data-ttu-id="876be-115">데이터 압축에 대한 자세한 내용은 [데이터 압축](data-compression.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="876be-115">For a more information about data compression, see [Data Compression](data-compression.md).</span></span>  
  
-   <span data-ttu-id="876be-116">압축 상태를 변경할 경우 테이블, 인덱스 또는 파티션에 어떤 영향을 주는지 확인하려면 [sp_estimate_data_compression_savings](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) 저장 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-116">To evaluate how changing the compression state will affect a table, an index, or a partition, use the [sp_estimate_data_compression_savings](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) stored procedure.</span></span>  
  
-   <span data-ttu-id="876be-117">테이블에 정렬되지 않은 인덱스가 있으면 단일 파티션의 압축 설정을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="876be-117">You cannot change the compression setting of a single partition if the table has nonaligned indexes.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="876be-118">보안</span><span class="sxs-lookup"><span data-stu-id="876be-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="876be-119">권한</span><span class="sxs-lookup"><span data-stu-id="876be-119">Permissions</span></span>  
 <span data-ttu-id="876be-120">테이블이나 인덱스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-120">Requires ALTER permission on the table or index.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="876be-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="876be-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-compression-on-a-table"></a><span data-ttu-id="876be-122">테이블에서 압축을 해제하려면</span><span class="sxs-lookup"><span data-stu-id="876be-122">To disable compression on a table</span></span>  
  
1.  <span data-ttu-id="876be-123">개체 탐색기에서 압축을 해제할 테이블이 포함된 데이터베이스를 확장한 다음 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-123">In Object Explorer, expand the database that contains the table on which you want to disable compression and then expand the **Tables** folder.</span></span>  
  
2.  <span data-ttu-id="876be-124">압축을 해제할 테이블이나 인덱스를 마우스 오른쪽 단추로 클릭하고 **스토리지**를 가리킨 후 **압축 관리...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-124">Right-click the table or index on which you want to disable compression, point to **Storage** and select **Manage Compression...**.</span></span>  
  
3.  <span data-ttu-id="876be-125">인덱스에서 압축을 해제하려면 인덱스가 포함된 테이블을 확장한 다음 **인덱스** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-125">To disable compression on an index, expand the table that contains the index and then expand the **Indexes** folder.</span></span>  
  
4.  <span data-ttu-id="876be-126">데이터 압축 마법사의 **데이터 압축 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-126">In the Data Compression Wizard, on the **Welcome to the Data Compression Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="876be-127">**압축 유형 선택** 페이지에서 압축을 해제할 인덱스의 각 파티션에 적용할 압축 유형으로 **없음** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-127">On the **Select Compression Type** page, select **None** as the compression type to apply to each partition in the index on which you want to disable compression.</span></span> <span data-ttu-id="876be-128">완료되면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-128">When finished, click **Next**.</span></span>  
  
     <span data-ttu-id="876be-129">다음은 **압축 유형 선택** 페이지에서 선택할 수 있는 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="876be-129">The following options are available on the **Select Compression Type** page:</span></span>  
  
     <span data-ttu-id="876be-130">**모든 파티션에 동일한 압축 유형 사용** 확인란</span><span class="sxs-lookup"><span data-stu-id="876be-130">**Use the same compression type for all partitions** check box</span></span>  
     <span data-ttu-id="876be-131">모든 파티션에 동일한 압축 설정을 구성하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-131">Select to configure the same compression setting for all partitions.</span></span> <span data-ttu-id="876be-132">이렇게 하면 선택 상자가 활성화되고 표의 **압축 유형** 열이 비활성화됩니다</span><span class="sxs-lookup"><span data-stu-id="876be-132">This enables the selection box and disables the **Compression Type** column in the grid.</span></span> <span data-ttu-id="876be-133">이 옵션을 선택하면 인접 목록의 옵션은 **없음**, **행**및 **페이지**입니다.</span><span class="sxs-lookup"><span data-stu-id="876be-133">When selected, the options in the adjacent list are **None**, **Row**, and **Page**.</span></span>  
  
     <span data-ttu-id="876be-134">**파티션 번호**</span><span class="sxs-lookup"><span data-stu-id="876be-134">**Partition Number**</span></span>  
     <span data-ttu-id="876be-135">테이블이나 인덱스에 있는 각 파티션을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-135">Lists each partition in the table or index.</span></span> <span data-ttu-id="876be-136">이 열은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="876be-136">This column is read-only.</span></span>  
  
     <span data-ttu-id="876be-137">**압축 유형**</span><span class="sxs-lookup"><span data-stu-id="876be-137">**Compression Type**</span></span>  
     <span data-ttu-id="876be-138">각 파티션의 압축 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-138">Select the compression option for each partition.</span></span> <span data-ttu-id="876be-139">**모든 파티션에 동일한 압축 유형 사용** 을 선택한 경우에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="876be-139">Is not available when **Use the same compression type for all partitions** is selected.</span></span> <span data-ttu-id="876be-140">목록의 옵션은 **없음**, **행**및 **페이지**입니다.</span><span class="sxs-lookup"><span data-stu-id="876be-140">List options are **None**, **Row**, and **Page**.</span></span>  
  
     <span data-ttu-id="876be-141">**경계**</span><span class="sxs-lookup"><span data-stu-id="876be-141">**Boundary**</span></span>  
     <span data-ttu-id="876be-142">파티션 경계를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-142">Displays the partition boundary.</span></span> <span data-ttu-id="876be-143">이 열은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="876be-143">This column is read-only.</span></span>  
  
     <span data-ttu-id="876be-144">**행 개수**</span><span class="sxs-lookup"><span data-stu-id="876be-144">**Row Count**</span></span>  
     <span data-ttu-id="876be-145">이 파티션의 행 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-145">Displays the number of rows in this partition.</span></span> <span data-ttu-id="876be-146">이 열은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="876be-146">This column is read-only.</span></span>  
  
     <span data-ttu-id="876be-147">**현재 공간**</span><span class="sxs-lookup"><span data-stu-id="876be-147">**Current Space**</span></span>  
     <span data-ttu-id="876be-148">이 파티션이 차지하는 현재 공간(MB)을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-148">Displays the current space this partition occupies in megabytes (MB).</span></span> <span data-ttu-id="876be-149">이 열은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="876be-149">This column is read-only.</span></span>  
  
     <span data-ttu-id="876be-150">**요청한 압축 공간**</span><span class="sxs-lookup"><span data-stu-id="876be-150">**Requested Compressed Space**</span></span>  
     <span data-ttu-id="876be-151">**계산**을 클릭하면 **압축 유형** 열에서 지정한 설정을 사용하여 압축 후 각 파티션의 예상 크기가 이 열에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="876be-151">After you click **Calculate**, this column displays the estimated size of each partition after compression by using the setting specified in the **Compression Type** column.</span></span> <span data-ttu-id="876be-152">이 열은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="876be-152">This column is read-only.</span></span>  
  
     <span data-ttu-id="876be-153">**계산**</span><span class="sxs-lookup"><span data-stu-id="876be-153">**Calculate**</span></span>  
     <span data-ttu-id="876be-154">**압축 유형** 열에서 지정한 설정을 사용하여 압축 후 각 파티션의 크기를 예측하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-154">Click to estimate the size of each partition after compression by using the setting specified in the **Compression Type** column.</span></span>  
  
6.  <span data-ttu-id="876be-155">**출력 옵션 선택** 페이지에서 이 태스크를 완료하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-155">In the **Select an Output Option** page, specify how you want to complete this task.</span></span> <span data-ttu-id="876be-156">마법사의 이전 페이지를 기반으로 SQL 스크립트를 만들려면 **스크립트 만들기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-156">Select **Create Script** to create a SQL script based the previous pages in the wizard.</span></span> <span data-ttu-id="876be-157">마법사의 남은 페이지를 모두 완료한 후 새 분할된 테이블을 만들려면 **즉시 실행** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-157">Select **Run immediately** to create the new partitioned table after completing all remaining pages in the wizard.</span></span> <span data-ttu-id="876be-158">향후 미리 결정된 시간에 새 분할된 테이블을 만들려면 **일정** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-158">Select **Schedule** to create the new partitioned table at a predetermined time in the future.</span></span>  
  
     <span data-ttu-id="876be-159">**스크립트 만들기**를 선택하는 경우 **스크립트 옵션**에서 다음과 같은 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876be-159">If you select **Create script**, the following options are available under **Script options**:</span></span>  
  
     <span data-ttu-id="876be-160">**파일로 스크립팅**</span><span class="sxs-lookup"><span data-stu-id="876be-160">**Script to file**</span></span>  
     <span data-ttu-id="876be-161">스크립트를 .sql 파일로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-161">Generates the script as a .sql file.</span></span> <span data-ttu-id="876be-162">**파일 이름** 상자에 파일 이름 및 위치를 입력하거나 **찾아보기** 를 클릭하여 **스크립트 파일 위치** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="876be-162">Enter a file name and location in the **File name** box or click **Browse** to open the **Script File Location** dialog box.</span></span> <span data-ttu-id="876be-163">**다른 이름으로 저장**에서 **유니코드 텍스트** 또는 **ANSI 텍스트**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-163">From **Save As**, select **Unicode text** or **ANSI text**.</span></span>  
  
     <span data-ttu-id="876be-164">**클립보드로 스크립팅**</span><span class="sxs-lookup"><span data-stu-id="876be-164">**Script to Clipboard**</span></span>  
     <span data-ttu-id="876be-165">스크립트를 클립보드에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-165">Saves the script to the Clipboard.</span></span>  
  
     <span data-ttu-id="876be-166">**새 쿼리 창으로 스크립팅**</span><span class="sxs-lookup"><span data-stu-id="876be-166">**Script to New Query Window**</span></span>  
     <span data-ttu-id="876be-167">새 쿼리 편집기 창에 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-167">Generates the script to a new Query Editor window.</span></span> <span data-ttu-id="876be-168">이 옵션이 기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="876be-168">This is the default selection.</span></span>  
  
     <span data-ttu-id="876be-169">**일정**을 선택하는 경우 **일정 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-169">If you select **Schedule**, click **Change schedule**.</span></span>  
  
    1.  <span data-ttu-id="876be-170">**새 작업 일정** 대화 상자의 **이름** 상자에 작업 일정 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-170">In the **New Job Schedule** dialog box, in the **Name** box, enter the job schedule's name.</span></span>  
  
    2.  <span data-ttu-id="876be-171">**일정 유형** 목록에서 다음과 같은 일정 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-171">On the **Schedule type** list, select the type of schedule:</span></span>  
  
        -   <span data-ttu-id="876be-172">**SQL Server 에이전트가 시작될 때 자동으로 시작**</span><span class="sxs-lookup"><span data-stu-id="876be-172">**Start automatically when SQL Server Agent starts**</span></span>  
  
        -   <span data-ttu-id="876be-173">**CPU가 유휴 상태로 될 때마다 시작**</span><span class="sxs-lookup"><span data-stu-id="876be-173">**Start whenever the CPUs become idle**</span></span>  
  
        -   <span data-ttu-id="876be-174">**되풀이**.</span><span class="sxs-lookup"><span data-stu-id="876be-174">**Recurring**.</span></span> <span data-ttu-id="876be-175">새 분할된 테이블을 정기적으로 새로운 정보로 업데이트하는 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-175">Select this option if your new partitioned table updates with new information on a regular basis.</span></span>  
  
        -   <span data-ttu-id="876be-176">**한 번**.</span><span class="sxs-lookup"><span data-stu-id="876be-176">**One time**.</span></span> <span data-ttu-id="876be-177">이 옵션이 기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="876be-177">This is the default selection.</span></span>  
  
    3.  <span data-ttu-id="876be-178">일정을 사용하거나 사용하지 않으려면 **사용** 확인란을 선택하거나 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-178">Select or clear the **Enabled** check box to enable or disable the schedule.</span></span>  
  
    4.  <span data-ttu-id="876be-179">**되풀이**를 선택하는 경우 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-179">If you select **Recurring**:</span></span>  
  
        1.  <span data-ttu-id="876be-180">**빈도**아래의 **되풀이** 목록에서 다음과 같이 발생 빈도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-180">Under **Frequency**, on the **Occurs** list, specify the frequency of occurrence:</span></span>  
  
            -   <span data-ttu-id="876be-181">**일별**을 선택하는 경우 **매** 상자에 작업 일정을 반복하는 일 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-181">If you select **Daily**, in the **Recurs every** box, enter how often the job schedule repeats in days.</span></span>  
  
            -   <span data-ttu-id="876be-182">**주별**을 선택하는 경우 **매** 상자에 작업 일정을 반복하는 주 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-182">If you select **Weekly**, in the **Recurs every** box, enter how often the job schedule repeats in weeks.</span></span> <span data-ttu-id="876be-183">작업 일정을 실행할 요일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-183">Select the day or days of the week on which the job schedule is run.</span></span>  
  
            -   <span data-ttu-id="876be-184">**월별**을 선택한 경우 **매(Day)** 또는 **매(The)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-184">If you select **Monthly**, select either **Day** or **The**.</span></span>  
  
                -   <span data-ttu-id="876be-185">**매(Day)** 를 선택한 경우 작업 일정을 실행할 날짜와 작업 일정을 반복할 월 수를 모두 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-185">If you select **Day**, enter both the date of the month you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="876be-186">예를 들어 작업 일정을 격월로 15일에 실행하려면 **매(Day)** 를 선택하고 첫 번째 상자에 "15", 두 번째 상자에 "2"를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-186">For example, if you want the job schedule to run on the 15th day of the month every other month, select **Day** and enter "15" in the first box and "2" in the second box.</span></span> <span data-ttu-id="876be-187">두 번째 상자에 허용되는 가장 큰 숫자는 "99"입니다.</span><span class="sxs-lookup"><span data-stu-id="876be-187">Please note that the largest number allowed in the second box is "99".</span></span>  
  
                -   <span data-ttu-id="876be-188">**매(The)** 를 선택한 경우 작업 일정을 실행할 요일 및 작업 일정을 반복할 월 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-188">If you select **The**, select the specific day of the week within the month that you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="876be-189">예를 들어 작업 일정을 격월로 마지막 평일에 실행하려면 **매(Day)** 를 선택하고 첫 번째 목록에서 **마지막**, 두 번째 목록에서 **평일**을 선택한 다음, 마지막 상자에 "2"를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-189">For example, if you want the job schedule to run on the last weekday of the month every other month, select **Day**, select **last** from the first list and **weekday** from the second list, and then enter "2" in the last box.</span></span> <span data-ttu-id="876be-190">**첫 번째**, **두 번째**, **세 번째** 또는 **네 번째** 또는 특정 평일(예: 일요일 또는 수요일)을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876be-190">You can also select **first**, **second**, **third**, or **fourth**, as well as specific weekdays (for example: Sunday or Wednesday) from the first two lists.</span></span> <span data-ttu-id="876be-191">마지막 상자에 허용되는 가장 큰 숫자는 "99"입니다.</span><span class="sxs-lookup"><span data-stu-id="876be-191">Please note that the largest number allowed in the last box is "99".</span></span>  
  
        2.  <span data-ttu-id="876be-192">**일별 빈도**에서 작업 일정이 실행되는 날에 작업 일정을 반복하는 빈도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-192">Under **Daily frequency**, specify how often the job schedule repeats on the day the job schedule runs:</span></span>  
  
            -   <span data-ttu-id="876be-193">**한 번 수행**을 선택하는 경우 **한 번 수행** 상자에 작업 일정을 실행할 특정 시간을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-193">If you select **Occurs once at**, enter the specific time of day when the job schedule should run in the **Occurs once at** box.</span></span> <span data-ttu-id="876be-194">시간, 분, 초와 오전 또는 오후를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-194">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
            -   <span data-ttu-id="876be-195">**되풀이 수행**을 선택하는 경우 **빈도**에 선택한 날 동안 작업 일정을 실행할 빈도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-195">If you select **Occurs every**, specify how often the job schedule runs during the day chosen under **Frequency**.</span></span> <span data-ttu-id="876be-196">예를 들어 작업 일정을 실행하는 날에 2시간마다 작업 일정을 반복하려면 **되풀이 수행**을 선택하고 첫 번째 상자에 "2"를 입력한 다음, 목록에서 **시간**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-196">For example, if you want the job schedule to repeat every 2 hours during the day that the job schedule is run, select **Occurs every**, enter "2" in the first box, and then select **hour(s)** from the list.</span></span> <span data-ttu-id="876be-197">이 목록에서 **분** 과 **초**도 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876be-197">From this list you can also select **minute(s)** and **second(s)**.</span></span> <span data-ttu-id="876be-198">첫 번째 상자에 허용되는 가장 큰 숫자는 "100"입니다.</span><span class="sxs-lookup"><span data-stu-id="876be-198">Please note that the largest number allowed in the first box is "100".</span></span>  
  
                 <span data-ttu-id="876be-199">**시작** 상자에 작업 일정 실행을 시작할 시간을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-199">In the **Starting at** box, enter the time that the job schedule should start running.</span></span> <span data-ttu-id="876be-200">**종료** 상자에 작업 일정 반복을 중지할 시간을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-200">In the **Ending at** box, enter the time that the job schedule should stop repeating.</span></span> <span data-ttu-id="876be-201">시간, 분, 초와 오전 또는 오후를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-201">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
        3.  <span data-ttu-id="876be-202">**기간**아래의 **시작 날짜**에 작업 일정 실행을 시작할 날짜를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-202">Under **Duration**, in **Start date**, enter the date that you want the job schedule to start running.</span></span> <span data-ttu-id="876be-203">**종료 날짜** 또는 **종료 날짜 없음** 을 선택하여 작업 일정 실행을 중지할 시기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="876be-203">Select **End date** or **No end date** to indicate when the job schedule should stop running.</span></span> <span data-ttu-id="876be-204">**종료 날짜**를 선택하는 경우 작업 일정 실행을 중지할 날짜를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-204">If you select **End date**, enter the date that you want to job schedule to stop running.</span></span>  
  
    5.  <span data-ttu-id="876be-205">**한 번**을 선택하는 경우 **한 번 발생**아래 **날짜** 상자에 작업 일정을 실행할 날짜를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-205">If you select **One Time**, under **One-time occurrence**, in the **Date** box, enter the date that the job schedule will be run.</span></span> <span data-ttu-id="876be-206">**시간** 상자에 작업 일정을 실행할 시간을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-206">In the **Time** box, enter the time that the job schedule will be run.</span></span> <span data-ttu-id="876be-207">시간, 분, 초와 오전 또는 오후를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-207">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
    6.  <span data-ttu-id="876be-208">**요약**아래 **설명**에서 모든 작업 일정 설정이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-208">Under **Summary**, in **Description**, verify that all job schedule settings are correct.</span></span>  
  
    7.  <span data-ttu-id="876be-209">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-209">Click **OK**.</span></span>  
  
     <span data-ttu-id="876be-210">이 페이지를 마쳤으면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-210">After completing this page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="876be-211">**요약 검토** 페이지의 **선택 항목 검토**아래에서 사용 가능한 옵션을 모두 확장하여 모든 설정이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-211">On the **Review Summary** page, under **Review your selections**, expand all available options to verify that all settings are correct.</span></span> <span data-ttu-id="876be-212">모두 맞으면 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-212">If everything is as expected, click **Finish**.</span></span>  
  
8.  <span data-ttu-id="876be-213">**압축 마법사 진행률** 페이지에서 파티션 작성 마법사의 동작에 대한 상태 정보를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876be-213">On the **Compression Wizard Progress** page, monitor status information about the actions of the Create Partition Wizard.</span></span> <span data-ttu-id="876be-214">마법사에서 선택한 옵션에 따라 진행률 페이지에 하나 이상의 동작이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876be-214">Depending on the options that you selected in the wizard, the progress page might contain one or more actions.</span></span> <span data-ttu-id="876be-215">맨 위에 있는 상자에는 전반적인 마법사 상태와 수신된 상태, 오류 및 경고 메시지의 수가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="876be-215">The top box displays the overall status of the wizard and the number of status, error, and warning messages that the wizard has received.</span></span>  
  
     <span data-ttu-id="876be-216">다음은 **압축 마법사 진행률** 페이지에서 선택할 수 있는 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="876be-216">The following options are available on the **Compression Wizard Progress** page:</span></span>  
  
     <span data-ttu-id="876be-217">**세부 정보**</span><span class="sxs-lookup"><span data-stu-id="876be-217">**Details**</span></span>  
     <span data-ttu-id="876be-218">동작, 상태 및 마법사가 수행한 동작의 결과로 반환된 모든 메시지를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-218">Provides the action, status, and any messages that are returned from action taken by the wizard.</span></span>  
  
     <span data-ttu-id="876be-219">**동작**</span><span class="sxs-lookup"><span data-stu-id="876be-219">**Action**</span></span>  
     <span data-ttu-id="876be-220">각 동작의 이름과 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-220">Specifies the type and name of each action.</span></span>  
  
     <span data-ttu-id="876be-221">**상태**</span><span class="sxs-lookup"><span data-stu-id="876be-221">**Status**</span></span>  
     <span data-ttu-id="876be-222">마법사 동작 결과 전체적으로 **성공** 값을 반환했는지 또는 **실패**값을 반환했는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="876be-222">Indicates whether the wizard action as a whole returned the value of **Success** or **Failure**.</span></span>  
  
     <span data-ttu-id="876be-223">**메시지**</span><span class="sxs-lookup"><span data-stu-id="876be-223">**Message**</span></span>  
     <span data-ttu-id="876be-224">프로세스에서 반환된 모든 오류 또는 경고 메시지를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-224">Provides any error or warning messages that are returned from the process.</span></span>  
  
     <span data-ttu-id="876be-225">**Report**</span><span class="sxs-lookup"><span data-stu-id="876be-225">**Report**</span></span>  
     <span data-ttu-id="876be-226">파티션 작성 마법사의 결과가 포함된 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="876be-226">Creates a report that contains the results of the Create Partition Wizard.</span></span> <span data-ttu-id="876be-227">**보고서 보기**, **보고서를 파일로 저장**, **클립보드에 보고서 복사**및 **보고서를 전자 메일로 보내기**중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876be-227">The options are **View Report**, **Save Report to File**, **Copy Report to Clipboard**, and **Send Report as Email**.</span></span>  
  
     <span data-ttu-id="876be-228">**보고서 보기**</span><span class="sxs-lookup"><span data-stu-id="876be-228">**View Report**</span></span>  
     <span data-ttu-id="876be-229">파티션 작성 마법사의 진행률에 대한 텍스트 보고서가 포함된 **보고서 보기** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="876be-229">Opens the **View Report** dialog box, which contains a text report of the progress of the Create Partition Wizard.</span></span>  
  
     <span data-ttu-id="876be-230">**보고서를 파일로 저장**</span><span class="sxs-lookup"><span data-stu-id="876be-230">**Save Report to File**</span></span>  
     <span data-ttu-id="876be-231">**보고서를 다른 이름으로 저장** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="876be-231">Opens the **Save Report As** dialog box.</span></span>  
  
     <span data-ttu-id="876be-232">**클립보드에 보고서 복사**</span><span class="sxs-lookup"><span data-stu-id="876be-232">**Copy Report to Clipboard**</span></span>  
     <span data-ttu-id="876be-233">마법사의 진행률 보고서 결과를 클립보드에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-233">Copies the results of the wizard's progress report to the Clipboard.</span></span>  
  
     <span data-ttu-id="876be-234">**보고서를 전자 메일로 보내기**</span><span class="sxs-lookup"><span data-stu-id="876be-234">**Send Report as Email**</span></span>  
     <span data-ttu-id="876be-235">마법사의 진행률 보고서 결과를 이메일 메시지에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-235">Copies the results of the wizard's progress report into an email message.</span></span>  
  
     <span data-ttu-id="876be-236">완료되면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-236">When complete, click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="876be-237">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="876be-237">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-compression-on-a-table"></a><span data-ttu-id="876be-238">테이블에서 압축을 해제하려면</span><span class="sxs-lookup"><span data-stu-id="876be-238">To disable compression on a table</span></span>  
  
1.  <span data-ttu-id="876be-239">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-239">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="876be-240">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-240">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="876be-241">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-241">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Person.Person REBUILD PARTITION = ALL  
    WITH (DATA_COMPRESSION = NONE);  
    GO  
    ```  
  
#### <a name="to-disable-compression-on-an-index"></a><span data-ttu-id="876be-242">인덱스에서 압축을 해제하려면</span><span class="sxs-lookup"><span data-stu-id="876be-242">To disable compression on an index</span></span>  
  
1.  <span data-ttu-id="876be-243">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-243">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="876be-244">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-244">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="876be-245">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="876be-245">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER INDEX AK_Person_rowguid ON Person.Person REBUILD PARTITION = ALL WITH (DATA_COMPRESSION = NONE);  
    GO  
    ```  
  
 <span data-ttu-id="876be-246">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) 및 [ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="876be-246">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) and [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
