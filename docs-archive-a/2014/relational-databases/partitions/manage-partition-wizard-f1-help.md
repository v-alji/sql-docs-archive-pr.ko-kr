---
title: 파티션 관리 마법사 F1 도움말 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.managepartition.getstart.f1
- sql12.swb.managepartition.selectoutput.f1
- sql12.swb.managepartition.partitionaction.f1
- sql12.swb.managepartition.switchout.f1
- sql12.swb.managepartition.summary.f1
- sql12.swb.managepartition.createjob.f1
- sql12.swb.managepartition.stagingtable.f1
- sql12.swb.managepartition.progress.f1
- sql12.swb.managepartition.switchin.f1
- sql12.swb.managepartition.selectswitchtables.f1
helpviewer_keywords:
- wizards [SQL Server Management Studio] See Manage Partition Wizard
ms.assetid: e2478d26-dea4-428d-98c5-aad2d2a30da8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 09b3e774168e9a48a0a387c3474b29f96081d875
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729424"
---
# <a name="manage-partition-wizard-f1-help"></a><span data-ttu-id="b2667-102">파티션 관리 마법사 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="b2667-102">Manage Partition Wizard F1 Help</span></span>
  <span data-ttu-id="b2667-103">**파티션 관리 마법사** 를 사용하여 파티션 전환이나 슬라이딩 윈도우(Sliding Window) 시나리오의 구현을 통해 기존 파티션 테이블을 관리하고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-103">Use the **Manage Partition Wizard** to manage and modify existing partitioned tables through partition switching or the implementation of a sliding window scenario.</span></span> <span data-ttu-id="b2667-104">이 마법사는 파티션 관리를 용이하게 하고 테이블로 또는 테이블로부터의 정기적인 데이터 마이그레이션을 단순화합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-104">This wizard can ease the management of your partitions and simplify the regular migration of data in and out of your tables.</span></span>  
  
### <a name="to-start-the-manage-partition-wizard"></a><span data-ttu-id="b2667-105">파티션 관리 마법사를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="b2667-105">To start the Manage Partition Wizard</span></span>  
  
-   <span data-ttu-id="b2667-106">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 데이터베이스를 선택하고 파티션을 만들려는 테이블을 마우스 오른쪽 단추로 클릭하고 **스토리지**를 가리킨 후 **파티션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-106">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the database, right-click the table on which you want to create partitions, point to **Storage**, and then click **Manage Partition**.</span></span>  
  
     <span data-ttu-id="b2667-107">`Note`**파티션 관리** 를 사용할 수 없는 경우에는 파티션이 없는 테이블을 선택 했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-107">`Note` If **Manage Partition** is unavailable, you may have selected a table that does not contain partitions.</span></span> <span data-ttu-id="b2667-108">테이블에 파티션을 만들려면 **스토리지** 하위 메뉴에서 **파티션 만들기** 를 클릭하고 **파티션 작성 마법사** 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-108">Click **Create Partition** on the **Storage** submenu and use the **Create Partition Wizard** to create partitions in your table.</span></span>  
  
 <span data-ttu-id="b2667-109">파티션과 인덱스에 대한 자세한 내용은 [Partitioned Tables and Indexes](partitioned-tables-and-indexes.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b2667-109">For general information about partitions and indexes, see [Partitioned Tables and Indexes](partitioned-tables-and-indexes.md).</span></span>  
  
 <span data-ttu-id="b2667-110">이 섹션에서는 **파티션 관리 마법사**를 사용하여 파티션을 관리, 수정 및 구현하는 데 필요한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-110">This section provides the information that is required to manage, modify, and implement partitions using the **Manage Partition Wizard**.</span></span>  
  
##  <a name="in-this-section"></a><a name="Top"></a> <span data-ttu-id="b2667-111">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="b2667-111">In This Section</span></span>  
 <span data-ttu-id="b2667-112">다음 섹션에서는 **파티션 관리 마법사**페이지에 대한 도움말을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-112">The following sections provide help on the pages of the **Manage Partition Wizard**.</span></span>  
  
 [<span data-ttu-id="b2667-113">파티션 관리 마법사(파티션 동작 선택 페이지)</span><span class="sxs-lookup"><span data-stu-id="b2667-113">Manage Partition Wizard (Select Partition Action Page)</span></span>](#SelectPartitionAction)  
  
 [<span data-ttu-id="b2667-114">파티션 관리 마법사(내부 전환 페이지)</span><span class="sxs-lookup"><span data-stu-id="b2667-114">Manage Partition Wizard (Switch In Page)</span></span>](#SwitchIn)  
  
 [<span data-ttu-id="b2667-115">파티션 관리 마법사(외부 전환 페이지)</span><span class="sxs-lookup"><span data-stu-id="b2667-115">Manage Partition Wizard (Switch Out Page)</span></span>](#SwitchOut)  
  
 [<span data-ttu-id="b2667-116">파티션 관리 마법사(준비 테이블 옵션 선택 페이지)</span><span class="sxs-lookup"><span data-stu-id="b2667-116">Manage Partition Wizard (Select Staging Table Options Page)</span></span>](#StagingTableOptions)  
  
 [<span data-ttu-id="b2667-117">파티션 관리 마법사(출력 옵션 선택 페이지)</span><span class="sxs-lookup"><span data-stu-id="b2667-117">Manage Partition Wizard (Select Output Option Page)</span></span>](#OutputOption)  
  
 [<span data-ttu-id="b2667-118">파티션 관리 마법사(새 작업 일정 페이지)</span><span class="sxs-lookup"><span data-stu-id="b2667-118">Manage Partition Wizard (New Job Schedule Page)</span></span>](#NewJob)  
  
 [<span data-ttu-id="b2667-119">파티션 관리 마법사(요약 페이지)</span><span class="sxs-lookup"><span data-stu-id="b2667-119">Manage Partition Wizard (Summary Page)</span></span>](#Summary)  
  
 [<span data-ttu-id="b2667-120">파티션 관리 마법사(진행률 페이지)</span><span class="sxs-lookup"><span data-stu-id="b2667-120">Manage Partition Wizard (Progress Page)</span></span>](#Progress)  
  
##  <a name="select-partition-action-page"></a><a name="SelectPartitionAction"></a> <span data-ttu-id="b2667-121">파티션 작업 페이지 선택</span><span class="sxs-lookup"><span data-stu-id="b2667-121">Select Partition Action Page</span></span>  
 <span data-ttu-id="b2667-122">**파티션 동작 선택** 페이지를 사용하여 파티션에서 수행할 동작을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-122">Use the **Select Partition Action** page to choose the action you want to perform on your partition.</span></span>  
  
### <a name="create-a-staging-table"></a><span data-ttu-id="b2667-123">준비 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="b2667-123">Create a Staging Table</span></span>  
 <span data-ttu-id="b2667-124">파티션 전환은 정기적으로 데이터 마이그레이션을 수행하는 분할된 테이블에서 일반적으로 수행되는 분할 태스크입니다. 예를 들어 현재 분기 데이터를 저장하는 분할된 테이블이 있을 경우 새 데이터를 이 테이블로 이동하고 오래된 데이터를 각 분기 끝에 보관해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-124">Partition switching is a common partitioning task if you have a partitioned table that you migrate data into and out of on a regular basis; for example, you have a partitioned table that stores current quarterly data, and you must move in new data and archive older data at the end of each quarter.</span></span>  
  
 <span data-ttu-id="b2667-125">이 마법사는 동일한 분할 열, 테이블/열 구조 및 인덱스를 사용하여 준비 테이블을 디자인하고 원본 파티션이 있는 파일 그룹에 새 테이블을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-125">The wizard designs the staging table with the same partitioning column, table and column structure, and indexes, and stores the new table in the filegroup where your source partition is located.</span></span>  
  
 <span data-ttu-id="b2667-126">준비 테이블을 사용하여 파티션 데이터를 전환하려면 **파티션 전환용 준비 테이블 만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-126">To create a staging table to switch in or switch out partition data, select **Create a staging table for partition switching**.</span></span>  
  
### <a name="sliding-window-scenario"></a><span data-ttu-id="b2667-127">슬라이딩 윈도우(Sliding Window) 시나리오</span><span class="sxs-lookup"><span data-stu-id="b2667-127">Sliding Window Scenario</span></span>  
 <span data-ttu-id="b2667-128">슬라이딩 윈도우(Sliding Window) 시나리오에서 파티션을 관리하려면 **슬라이딩 윈도우 시나리오에서 분할된 데이터 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-128">To manage your partitions in a sliding-window scenario, select **Manage partitioned data in a sliding window scenario**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b2667-129">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="b2667-129">UI element list</span></span>  
 <span data-ttu-id="b2667-130">**파티션 전환용 준비 테이블 만들기**</span><span class="sxs-lookup"><span data-stu-id="b2667-130">**Create a staging table for partition switching**</span></span>  
 <span data-ttu-id="b2667-131">분할된 기존 테이블로 또는 분할된 기존 테이블에서 내부 전환하거나 외부 전환할 데이터의 준비 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-131">Creates a staging table for the data you are switching in or switching out of the existing partitioned table.</span></span>  
  
 <span data-ttu-id="b2667-132">**외부 전환 파티션**</span><span class="sxs-lookup"><span data-stu-id="b2667-132">**Switch out partition**</span></span>  
 <span data-ttu-id="b2667-133">테이블에서 파티션을 제거할 때의 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-133">Provides options when removing a partition from the table.</span></span>  
  
 <span data-ttu-id="b2667-134">**내부 전환 파티션**</span><span class="sxs-lookup"><span data-stu-id="b2667-134">**Switch in partition**</span></span>  
 <span data-ttu-id="b2667-135">테이블에 파티션을 추가할 때의 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-135">Provides options when adding a partition to the table.</span></span>  
  
 <span data-ttu-id="b2667-136">**슬라이딩 윈도우 시나리오에서 분할된 데이터 관리**</span><span class="sxs-lookup"><span data-stu-id="b2667-136">**Manage partitioned data in a sliding window scenario**</span></span>  
 <span data-ttu-id="b2667-137">데이터 전환에 사용할 수 있는 기존 테이블에 빈 파티션을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-137">Appends an empty partition to the existing table that can be used for switching in data.</span></span> <span data-ttu-id="b2667-138">이 마법사는 현재 마지막 파티션으로의 전환과 첫 번째 파티션으로부터의 전환을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-138">The wizard currently supports switching into the last partition and switching out the first partition.</span></span>  
  
 <span data-ttu-id="b2667-139">![맨 위로 이동 링크와 함께 사용되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [섹션 내용](#Top)</span><span class="sxs-lookup"><span data-stu-id="b2667-139">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="select-partition-switching-in-options-page"></a><a name="SwitchIn"></a> <span data-ttu-id="b2667-140">파티션 내부 전환 옵션 선택 페이지</span><span class="sxs-lookup"><span data-stu-id="b2667-140">Select Partition Switching-In Options Page</span></span>  
 <span data-ttu-id="b2667-141">**파티션 내부 전환 옵션 선택** 페이지를 사용하여 분할된 테이블로 내부 전환할 준비 테이블을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-141">Use the **Select Partition Switching-In options** page to select the staging table you are switching into the partitioned table.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b2667-142">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="b2667-142">UI element list</span></span>  
 <span data-ttu-id="b2667-143">**모든 파티션 표시**</span><span class="sxs-lookup"><span data-stu-id="b2667-143">**Show All Partitions**</span></span>  
 <span data-ttu-id="b2667-144">분할된 테이블의 현재 파티션을 포함한 모든 파티션을 표시하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-144">Select to show all partitions, including the partitions currently in the partitioned table.</span></span>  
  
 <span data-ttu-id="b2667-145">**파티션 표**</span><span class="sxs-lookup"><span data-stu-id="b2667-145">**Partition grid**</span></span>  
 <span data-ttu-id="b2667-146">선택한 파티션의 파티션 이름, **왼쪽 경계**, **오른쪽 경계**, **파일 그룹**및 **행 개수** 를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-146">Displays the partition name, **Left boundary**, **Right boundary**, **Filegroup**, and **Row count** of the partitions you selected.</span></span>  
  
 <span data-ttu-id="b2667-147">**내부 전환 테이블**</span><span class="sxs-lookup"><span data-stu-id="b2667-147">**Switch in table**</span></span>  
 <span data-ttu-id="b2667-148">분할된 테이블에 추가할 파티션이 포함된 준비 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-148">Select the staging table that contains the partition that you want to add to your partitioned table.</span></span> <span data-ttu-id="b2667-149">**파티션 관리 마법사**를 사용하여 파티션을 내부 전환하기 전에 이 준비 테이블을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-149">You must create this staging table before you switch-in partitions with the **Manage PartitionsWizard**.</span></span>  
  
 <span data-ttu-id="b2667-150">![맨 위로 이동 링크와 함께 사용되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [섹션 내용](#Top)</span><span class="sxs-lookup"><span data-stu-id="b2667-150">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="select-partition-switching-out-options-page"></a><a name="SwitchOut"></a> <span data-ttu-id="b2667-151">파티션 외부 전환 옵션 선택 페이지</span><span class="sxs-lookup"><span data-stu-id="b2667-151">Select Partition Switching-Out Options Page</span></span>  
 <span data-ttu-id="b2667-152">**파티션 외부 전환 옵션 선택** 페이지를 사용하여 분할된 테이블에서 외부 전환할 분할된 데이터를 저장하기 위한 파티션 및 준비 테이블을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-152">Use the **Select Partition Switching-Out options** page to select the partition and the staging table to hold the partitioned data that you are switching out of the partitioned table.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b2667-153">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="b2667-153">UI element list</span></span>  
 <span data-ttu-id="b2667-154">**파티션 표**</span><span class="sxs-lookup"><span data-stu-id="b2667-154">**Partition grid**</span></span>  
 <span data-ttu-id="b2667-155">선택한 파티션의 파티션 이름, **왼쪽 경계**, **오른쪽 경계**, **파일 그룹**및 **행 개수** 를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-155">Displays the partition name, **Left boundary**, **Right boundary**, **Filegroup**, and **Row count** of the partitions you selected.</span></span>  
  
 <span data-ttu-id="b2667-156">**외부 전환 테이블**</span><span class="sxs-lookup"><span data-stu-id="b2667-156">**Switch out table**</span></span>  
 <span data-ttu-id="b2667-157">데이터를 외부 전환할 대상으로 새 테이블이나 기존 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-157">Choose a new table or an existing table to switch-out your data to.</span></span>  
  
 <span data-ttu-id="b2667-158">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="b2667-158">**New**</span></span>  
 <span data-ttu-id="b2667-159">현재 원본 테이블에서 외부 전환할 파티션에 사용할 준비 테이블의 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-159">Enter a new name for the staging table you want to use for the partition to switch out of the current source table.</span></span>  
  
 <span data-ttu-id="b2667-160">**기존**</span><span class="sxs-lookup"><span data-stu-id="b2667-160">**Existing**</span></span>  
 <span data-ttu-id="b2667-161">현재 원본 테이블에서 외부 전환하려는 파티션에 사용할 기존 준비 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-161">Select an existing staging table you want to use for the partition you want to switch out of the current source table.</span></span> <span data-ttu-id="b2667-162">기존 테이블에 데이터가 포함된 경우 외부 전환하는 데이터가 이 데이터를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-162">If the existing table contains data, this data will be overwritten with the data you are switching out.</span></span>  
  
 <span data-ttu-id="b2667-163">![맨 위로 이동 링크와 함께 사용되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [섹션 내용](#Top)</span><span class="sxs-lookup"><span data-stu-id="b2667-163">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="select-the-staging-table-options-page"></a><a name="StagingTableOptions"></a> <span data-ttu-id="b2667-164">준비 테이블 옵션 선택 페이지</span><span class="sxs-lookup"><span data-stu-id="b2667-164">Select the Staging Table Options Page</span></span>  
 <span data-ttu-id="b2667-165">**준비 테이블 옵션 선택** 페이지를 사용하여 분할된 데이터를 전환하는 데 사용할 준비 테이블을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-165">Use the **Select the Staging Table Options** page to create the staging table you want to use for switching your partitioned data.</span></span>  
  
 <span data-ttu-id="b2667-166">준비 테이블은 선택한 파티션에서 원본 테이블이 위치하는 파일 그룹과 같은 파일 그룹에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-166">Staging tables must reside in the same filegroup of the selected partition where the source table is located.</span></span> <span data-ttu-id="b2667-167">준비 테이블은 원본 테이블과 대상 테이블의 디자인을 모두 반영해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-167">The staging table must mirror the design of both the source table and the destination table.</span></span>  
  
 <span data-ttu-id="b2667-168">원본 파티션에 존재하는 준비 테이블에 동일한 인덱스를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-168">You can also create the same indexes in the staging table that exist in the source partition.</span></span> <span data-ttu-id="b2667-169">준비 테이블에는 원본 파티션의 요소를 기반으로 하는 제약 조건이 자동으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-169">The staging table automatically contains a constraint based on the elements of the source partition.</span></span> <span data-ttu-id="b2667-170">이 제약 조건은 일반적으로 원본 파티션의 경계 값에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-170">This constraint is typically generated from the boundary value of the source partition.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b2667-171">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="b2667-171">UI element list</span></span>  
 <span data-ttu-id="b2667-172">**준비 테이블 이름**</span><span class="sxs-lookup"><span data-stu-id="b2667-172">**Staging table name**</span></span>  
 <span data-ttu-id="b2667-173">준비 테이블에 대한 이름을 만들거나 입력란에 표시되는 기본 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-173">Create a name for the staging table or accept the default name displayed in the edit box.</span></span>  
  
 <span data-ttu-id="b2667-174">**파티션 전환**</span><span class="sxs-lookup"><span data-stu-id="b2667-174">**Switch partition**</span></span>  
 <span data-ttu-id="b2667-175">현재 테이블에서 외부 전환하려는 원본 파티션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-175">Select the source partition that you want to switch out of the current table.</span></span>  
  
 <span data-ttu-id="b2667-176">**새 경계 값**</span><span class="sxs-lookup"><span data-stu-id="b2667-176">**New boundary value**</span></span>  
 <span data-ttu-id="b2667-177">준비 테이블의 파티션에 대해 원하는 경계 값을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-177">Select or enter the boundary value you want for the partition in the staging table.</span></span>  
  
 <span data-ttu-id="b2667-178">**파일 그룹**</span><span class="sxs-lookup"><span data-stu-id="b2667-178">**Filegroup**</span></span>  
 <span data-ttu-id="b2667-179">새 테이블의 파일 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-179">Select a filegroup for the new table.</span></span>  
  
 <span data-ttu-id="b2667-180">![맨 위로 이동 링크와 함께 사용되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [섹션 내용](#Top)</span><span class="sxs-lookup"><span data-stu-id="b2667-180">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="select-output-option-page"></a><a name="OutputOption"></a> <span data-ttu-id="b2667-181">출력 옵션 선택 페이지</span><span class="sxs-lookup"><span data-stu-id="b2667-181">Select Output Option Page</span></span>  
 <span data-ttu-id="b2667-182">**출력 옵션 선택** 페이지를 사용하여 파티션에 대한 수정을 완료하는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-182">Use the **Select Output Option** page to specify how you want to complete the modifications to your partitions.</span></span>  
  
### <a name="create-script"></a><span data-ttu-id="b2667-183">스크립트 만들기</span><span class="sxs-lookup"><span data-stu-id="b2667-183">Create Script</span></span>  
 <span data-ttu-id="b2667-184">마법사가 완료되면 쿼리 편집기에 테이블의 파티션을 수정하는 스크립트가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-184">When the wizard finishes, it creates a script in Query Editor to modify partitions in the table.</span></span> <span data-ttu-id="b2667-185">이 스크립트를 검토하려면 **스크립트 만들기** 를 선택한 다음 수동으로 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-185">Select **Create Script** if you want to review the script, and then execute the script manually.</span></span>  
  
 <span data-ttu-id="b2667-186">**파일로 스크립팅**</span><span class="sxs-lookup"><span data-stu-id="b2667-186">**Script to file**</span></span>  
 <span data-ttu-id="b2667-187">스크립트를 .sql 파일로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-187">Generate the script to a .sql file.</span></span> <span data-ttu-id="b2667-188">**유니코드** 또는 **ANSI 텍스트**를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-188">Specify either **Unicode** or **ANSI text**.</span></span> <span data-ttu-id="b2667-189">파일의 이름과 위치를 지정하려면 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-189">To specify a name and location for the file, click **Browse**.</span></span>  
  
 <span data-ttu-id="b2667-190">**클립보드로 스크립팅**</span><span class="sxs-lookup"><span data-stu-id="b2667-190">**Script to Clipboard**</span></span>  
 <span data-ttu-id="b2667-191">스크립트를 클립보드에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-191">Save the script to the Clipboard.</span></span>  
  
 <span data-ttu-id="b2667-192">**새 쿼리 창으로 스크립팅**</span><span class="sxs-lookup"><span data-stu-id="b2667-192">**Script to New Query Window**</span></span>  
 <span data-ttu-id="b2667-193">쿼리 편집기 창에 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-193">Generate the script to a Query Editor window.</span></span> <span data-ttu-id="b2667-194">열려 있는 편집기 창이 없으면 스크립트 대상으로 사용할 새 편집기 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-194">If no editor window is open, a new editor window opens as the target for the script.</span></span>  
  
### <a name="run-immediately"></a><span data-ttu-id="b2667-195">즉시 실행</span><span class="sxs-lookup"><span data-stu-id="b2667-195">Run Immediately</span></span>  
 <span data-ttu-id="b2667-196">**Run immediately**</span><span class="sxs-lookup"><span data-stu-id="b2667-196">**Run immediately**</span></span>  
 <span data-ttu-id="b2667-197">**다음** 또는 **마침**을 클릭하면 마법사가 파티션에 대한 수정을 마치도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-197">Have the wizard finish modifications to the partitions when you click **Next** or **Finish**.</span></span>  
  
### <a name="schedule"></a><span data-ttu-id="b2667-198">일정</span><span class="sxs-lookup"><span data-stu-id="b2667-198">Schedule</span></span>  
 <span data-ttu-id="b2667-199">예약된 날짜 및 시간에 테이블 파티션을 수정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-199">Select to modify the table partitions at a scheduled date and time.</span></span>  
  
 <span data-ttu-id="b2667-200">**일정 변경**</span><span class="sxs-lookup"><span data-stu-id="b2667-200">**Change schedule**</span></span>  
 <span data-ttu-id="b2667-201">예약된 작업의 속성을 선택, 변경하거나 볼 수 있는 **새 작업 일정** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-201">Opens the **New Job Schedule** dialog box, where you can select, change, or view the properties of the scheduled job.</span></span>  
  
 <span data-ttu-id="b2667-202">![맨 위로 이동 링크와 함께 사용되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [섹션 내용](#Top)</span><span class="sxs-lookup"><span data-stu-id="b2667-202">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="new-job-schedule-page"></a><a name="NewJob"></a> <span data-ttu-id="b2667-203">새 작업 일정 페이지</span><span class="sxs-lookup"><span data-stu-id="b2667-203">New Job Schedule Page</span></span>  
 <span data-ttu-id="b2667-204">**새 작업 일정** 페이지를 사용하여 일정 속성을 확인하고 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-204">Use the **New Job Schedule** page to view and change the properties of the schedule.</span></span>  
  
### <a name="options"></a><span data-ttu-id="b2667-205">옵션</span><span class="sxs-lookup"><span data-stu-id="b2667-205">Options</span></span>  
 <span data-ttu-id="b2667-206">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업에 대해 원하는 일정 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-206">Select the type of schedule you want for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>  
  
 <span data-ttu-id="b2667-207">**이름**</span><span class="sxs-lookup"><span data-stu-id="b2667-207">**Name**</span></span>  
 <span data-ttu-id="b2667-208">새 일정 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-208">Type a new name for the schedule.</span></span>  
  
 <span data-ttu-id="b2667-209">**이 일정 내의 작업**</span><span class="sxs-lookup"><span data-stu-id="b2667-209">**Jobs in schedule**</span></span>  
 <span data-ttu-id="b2667-210">이 일정을 사용하는 기존 작업을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-210">View the existing jobs that use the schedule.</span></span>  
  
 <span data-ttu-id="b2667-211">**일정 유형**</span><span class="sxs-lookup"><span data-stu-id="b2667-211">**Schedule type**</span></span>  
 <span data-ttu-id="b2667-212">일정 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-212">Select the type of schedule.</span></span>  
  
 <span data-ttu-id="b2667-213">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="b2667-213">**Enabled**</span></span>  
 <span data-ttu-id="b2667-214">일정을 사용하거나 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-214">Enable or disable the schedule.</span></span>  
  
### <a name="recurring-schedule-types-options"></a><span data-ttu-id="b2667-215">되풀이 일정 유형 옵션</span><span class="sxs-lookup"><span data-stu-id="b2667-215">Recurring Schedule Types Options</span></span>  
 <span data-ttu-id="b2667-216">예약된 작업의 빈도를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-216">Select the frequency of the scheduled job.</span></span>  
  
 <span data-ttu-id="b2667-217">**되풀이**</span><span class="sxs-lookup"><span data-stu-id="b2667-217">**Occurs**</span></span>  
 <span data-ttu-id="b2667-218">일정 되풀이 간격을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-218">Select the interval at which the schedule recurs.</span></span>  
  
 <span data-ttu-id="b2667-219">**매**</span><span class="sxs-lookup"><span data-stu-id="b2667-219">**Recurs every**</span></span>  
 <span data-ttu-id="b2667-220">일정 되풀이 간격을 일 또는 주 단위(수)로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-220">Select the number of days or weeks between recurrences of the schedule.</span></span> <span data-ttu-id="b2667-221">월별 일정에는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-221">This option is not available for monthly schedules.</span></span>  
  
 <span data-ttu-id="b2667-222">**월요일**</span><span class="sxs-lookup"><span data-stu-id="b2667-222">**Monday**</span></span>  
 <span data-ttu-id="b2667-223">월요일에 작업이 수행되도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-223">Set the job to occur on a Monday.</span></span> <span data-ttu-id="b2667-224">주별 일정에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-224">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="b2667-225">**화요일**</span><span class="sxs-lookup"><span data-stu-id="b2667-225">**Tuesday**</span></span>  
 <span data-ttu-id="b2667-226">화요일에 작업이 수행되도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-226">Set the job to occur on a Tuesday.</span></span> <span data-ttu-id="b2667-227">주별 일정에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-227">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="b2667-228">**수요일**</span><span class="sxs-lookup"><span data-stu-id="b2667-228">**Wednesday**</span></span>  
 <span data-ttu-id="b2667-229">수요일에 작업이 수행되도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-229">Set the job to occur on a Wednesday.</span></span> <span data-ttu-id="b2667-230">주별 일정에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-230">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="b2667-231">**목요일**</span><span class="sxs-lookup"><span data-stu-id="b2667-231">**Thursday**</span></span>  
 <span data-ttu-id="b2667-232">목요일에 작업이 수행되도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-232">Set the job to occur on a Thursday.</span></span> <span data-ttu-id="b2667-233">주별 일정에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-233">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="b2667-234">**금요일**</span><span class="sxs-lookup"><span data-stu-id="b2667-234">**Friday**</span></span>  
 <span data-ttu-id="b2667-235">금요일에 작업이 수행되도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-235">Set the job to occur on a Friday.</span></span> <span data-ttu-id="b2667-236">주별 일정에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-236">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="b2667-237">**토요일**</span><span class="sxs-lookup"><span data-stu-id="b2667-237">**Saturday**</span></span>  
 <span data-ttu-id="b2667-238">토요일에 작업이 수행되도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-238">Set the job to occur on a Saturday.</span></span> <span data-ttu-id="b2667-239">주별 일정에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-239">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="b2667-240">**일요일**</span><span class="sxs-lookup"><span data-stu-id="b2667-240">**Sunday**</span></span>  
 <span data-ttu-id="b2667-241">일요일에 작업이 수행되도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-241">Set the job to occur on a Sunday.</span></span> <span data-ttu-id="b2667-242">주별 일정에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-242">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="b2667-243">**Day**</span><span class="sxs-lookup"><span data-stu-id="b2667-243">**Day**</span></span>  
 <span data-ttu-id="b2667-244">일정이 시작되는 날짜를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-244">Select the day of the month the schedule occurs.</span></span> <span data-ttu-id="b2667-245">월별 일정에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-245">Only available for monthly schedules.</span></span>  
  
 <span data-ttu-id="b2667-246">**일 /**</span><span class="sxs-lookup"><span data-stu-id="b2667-246">**of every**</span></span>  
 <span data-ttu-id="b2667-247">일정 되풀이 간격을 월 단위(수)로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-247">Select the number of months between occurrences of the schedule.</span></span> <span data-ttu-id="b2667-248">월별 일정에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-248">Only available for monthly schedules.</span></span>  
  
 <span data-ttu-id="b2667-249">**이**</span><span class="sxs-lookup"><span data-stu-id="b2667-249">**The**</span></span>  
 <span data-ttu-id="b2667-250">해당 월의 특정 주에 있는 특정 요일에 대한 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-250">Specify a schedule for a specific day of the week on a specific week within the month.</span></span> <span data-ttu-id="b2667-251">월별 일정에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-251">Only available for monthly schedules.</span></span>  
  
 <span data-ttu-id="b2667-252">**한 번 수행**</span><span class="sxs-lookup"><span data-stu-id="b2667-252">**Occurs once at**</span></span>  
 <span data-ttu-id="b2667-253">매일 작업이 수행되도록 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-253">Set the time for a job to occur daily.</span></span>  
  
 <span data-ttu-id="b2667-254">**되풀이 수행**</span><span class="sxs-lookup"><span data-stu-id="b2667-254">**Occurs every**</span></span>  
 <span data-ttu-id="b2667-255">작업 발생 간격을 시와 분으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-255">Set the number of hours or minutes between occurrences.</span></span>  
  
 <span data-ttu-id="b2667-256">**시작 날짜**</span><span class="sxs-lookup"><span data-stu-id="b2667-256">**Start date**</span></span>  
 <span data-ttu-id="b2667-257">이 일정을 개시할 날짜를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-257">Set the date when this schedule will become effective.</span></span>  
  
 <span data-ttu-id="b2667-258">**종료 날짜**</span><span class="sxs-lookup"><span data-stu-id="b2667-258">**End date**</span></span>  
 <span data-ttu-id="b2667-259">일정을 종료할 날짜를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-259">Set the date when the schedule will no longer be effective.</span></span>  
  
 <span data-ttu-id="b2667-260">**종료 날짜 없음**</span><span class="sxs-lookup"><span data-stu-id="b2667-260">**No end date**</span></span>  
 <span data-ttu-id="b2667-261">일정을 무기한 유지하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-261">Specify that the schedule will remain effective indefinitely.</span></span>  
  
### <a name="one-time-schedule-types-options"></a><span data-ttu-id="b2667-262">일회 일정 유형 옵션</span><span class="sxs-lookup"><span data-stu-id="b2667-262">One Time Schedule Types Options</span></span>  
 <span data-ttu-id="b2667-263">작업을 한 번 실행하도록 예약할 경우 미래의 날짜와 시간을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-263">If you schedule a job to run once, you must select a date and time in the future.</span></span>  
  
 <span data-ttu-id="b2667-264">**Date**</span><span class="sxs-lookup"><span data-stu-id="b2667-264">**Date**</span></span>  
 <span data-ttu-id="b2667-265">작업을 실행할 날짜를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-265">Select the date for the job to run.</span></span>  
  
 <span data-ttu-id="b2667-266">**Time**</span><span class="sxs-lookup"><span data-stu-id="b2667-266">**Time**</span></span>  
 <span data-ttu-id="b2667-267">작업을 실행할 시간을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-267">Select the time for the job to run.</span></span>  
  
 <span data-ttu-id="b2667-268">![맨 위로 이동 링크와 함께 사용되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [섹션 내용](#Top)</span><span class="sxs-lookup"><span data-stu-id="b2667-268">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="b2667-269">요약 페이지</span><span class="sxs-lookup"><span data-stu-id="b2667-269">Summary Page</span></span>  
 <span data-ttu-id="b2667-270">**요약** 페이지를 사용하여 이전 페이지에서 선택한 옵션을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-270">Use the **Summary** page to review the options that you have selected on the previous pages.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b2667-271">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="b2667-271">UI element list</span></span>  
 <span data-ttu-id="b2667-272">**선택 항목 검토**</span><span class="sxs-lookup"><span data-stu-id="b2667-272">**Review your selections**</span></span>  
 <span data-ttu-id="b2667-273">마법사의 각 페이지에서 사용자가 선택한 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-273">Displays the selections you have made for each page of the wizard.</span></span> <span data-ttu-id="b2667-274">이전에 선택한 옵션을 확장하고 보려면 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-274">Click a node to expand and view your previously selected options.</span></span>  
  
 <span data-ttu-id="b2667-275">![맨 위로 이동 링크와 함께 사용되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [섹션 내용](#Top)</span><span class="sxs-lookup"><span data-stu-id="b2667-275">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="progress-page"></a><a name="Progress"></a> <span data-ttu-id="b2667-276">진행률 페이지</span><span class="sxs-lookup"><span data-stu-id="b2667-276">Progress Page</span></span>  
 <span data-ttu-id="b2667-277">**진행률** 페이지를 사용하여 **파티션 관리 마법사**의 동작에 대한 상태 정보를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-277">Use the **Progress** page to monitor status information about the actions of the **Manage Partition Wizard**.</span></span> <span data-ttu-id="b2667-278">마법사에서 선택한 옵션에 따라 **진행률** 페이지에 하나 이상의 동작이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-278">Depending on the options that you selected in the wizard, the **Progress** page might contain one or more actions.</span></span> <span data-ttu-id="b2667-279">맨 위에 있는 상자에는 전반적인 마법사 상태와 수신된 상태, 오류 및 경고 메시지의 수가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-279">The top box displays the overall status of the wizard and the number of status, error, and warning messages that the wizard has received.</span></span>  
  
### <a name="options"></a><span data-ttu-id="b2667-280">옵션</span><span class="sxs-lookup"><span data-stu-id="b2667-280">Options</span></span>  
 <span data-ttu-id="b2667-281">**세부 정보**</span><span class="sxs-lookup"><span data-stu-id="b2667-281">**Details**</span></span>  
 <span data-ttu-id="b2667-282">동작, 상태 및 마법사가 수행한 동작의 결과로 반환된 모든 메시지를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-282">Provides the action, status, and any messages that are returned from action taken by the wizard.</span></span>  
  
 <span data-ttu-id="b2667-283">**동작**</span><span class="sxs-lookup"><span data-stu-id="b2667-283">**Action**</span></span>  
 <span data-ttu-id="b2667-284">각 동작의 이름과 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-284">Specifies the type and name of each action.</span></span>  
  
 <span data-ttu-id="b2667-285">**상태**</span><span class="sxs-lookup"><span data-stu-id="b2667-285">**Status**</span></span>  
 <span data-ttu-id="b2667-286">마법사 동작 결과 전체적으로 **성공** 값을 반환했는지 또는 **실패**값을 반환했는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-286">Indicates whether the wizard action as a whole returned the value of **Success** or **Failure**.</span></span>  
  
 <span data-ttu-id="b2667-287">**메시지**</span><span class="sxs-lookup"><span data-stu-id="b2667-287">**Message**</span></span>  
 <span data-ttu-id="b2667-288">프로세스에서 반환된 모든 오류 또는 경고 메시지를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-288">Provides any error or warning messages that are returned from the process.</span></span>  
  
 <span data-ttu-id="b2667-289">**중지**</span><span class="sxs-lookup"><span data-stu-id="b2667-289">**Stop**</span></span>  
 <span data-ttu-id="b2667-290">마법사의 동작을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-290">Stop the action of the wizard.</span></span>  
  
 <span data-ttu-id="b2667-291">**Report**</span><span class="sxs-lookup"><span data-stu-id="b2667-291">**Report**</span></span>  
 <span data-ttu-id="b2667-292">**파티션 관리 마법사**의 결과가 포함된 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-292">Create a report that contains the results of the **Manage Partition Wizard**.</span></span> <span data-ttu-id="b2667-293">옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-293">The options are:</span></span>  
  
-   <span data-ttu-id="b2667-294">**보고서 보기**</span><span class="sxs-lookup"><span data-stu-id="b2667-294">**View Report**</span></span>  
  
-   <span data-ttu-id="b2667-295">**보고서를 파일로 저장**</span><span class="sxs-lookup"><span data-stu-id="b2667-295">**Save Report to File**</span></span>  
  
-   <span data-ttu-id="b2667-296">**클립보드에 보고서 복사**</span><span class="sxs-lookup"><span data-stu-id="b2667-296">**Copy Report to Clipboard**</span></span>  
  
-   <span data-ttu-id="b2667-297">**보고서를 전자 메일로 보내기**</span><span class="sxs-lookup"><span data-stu-id="b2667-297">**Send Report as Email**</span></span>  
  
 <span data-ttu-id="b2667-298">**보고서 보기**</span><span class="sxs-lookup"><span data-stu-id="b2667-298">**View Report**</span></span>  
 <span data-ttu-id="b2667-299">**보고서 보기** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-299">Open the **View Report** dialog box.</span></span> <span data-ttu-id="b2667-300">이 대화 상자에는 **파티션 관리 마법사**의 진행률에 대한 텍스트 보고서가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-300">This dialog box contains a text report of the progress of the **Manage Partition Wizard**.</span></span>  
  
 <span data-ttu-id="b2667-301">**닫기**</span><span class="sxs-lookup"><span data-stu-id="b2667-301">**Close**</span></span>  
 <span data-ttu-id="b2667-302">마법사를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b2667-302">Close the wizard.</span></span>  
  
 <span data-ttu-id="b2667-303">![맨 위로 이동 링크와 함께 사용되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [섹션 내용](#Top)</span><span class="sxs-lookup"><span data-stu-id="b2667-303">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2667-304">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b2667-304">See Also</span></span>  
 [<span data-ttu-id="b2667-305">Partitioned Tables and Indexes</span><span class="sxs-lookup"><span data-stu-id="b2667-305">Partitioned Tables and Indexes</span></span>](partitioned-tables-and-indexes.md)  
  
  
