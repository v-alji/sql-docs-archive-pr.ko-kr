---
title: 수동으로 데이터 처리 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.datarefreshprogressdb.f1
ms.assetid: 0918c04c-c1e6-45b4-acfa-96fa578e684b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 51bdb1b9535685db4fc35dbdd791e6b4d9bed1b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653623"
---
# <a name="manually-process-data-ssas-tabular"></a><span data-ttu-id="2dccc-102">수동으로 데이터 처리(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="2dccc-102">Manually Process Data (SSAS Tabular)</span></span>
  <span data-ttu-id="2dccc-103">이 항목에서는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 작업 영역 데이터를 수동으로 처리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-103">This topic describes how to manually process workspace data in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="2dccc-104">외부 데이터를 사용하는 테이블 형식 모델을 제작할 때 처리 명령을 사용하여 데이터를 수동으로 새로 고칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-104">When you author a tabular model that uses external data, you can manually refresh the data by using the Process command.</span></span> <span data-ttu-id="2dccc-105">단일 테이블, 모델에 있는 모든 테이블 또는 하나 이상의 파티션을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-105">You can process a single table, all tables in the model, or one or more partitions.</span></span> <span data-ttu-id="2dccc-106">데이터를 처리할 때마다 데이터를 다시 계산해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-106">Whenever you process data, you may also need to recalculate data.</span></span>  <span data-ttu-id="2dccc-107">데이터 처리는 외부 원본에서 최신 데이터를 가져오는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-107">Processing data means getting the latest data from external sources.</span></span> <span data-ttu-id="2dccc-108">다시 계산은 데이터를 사용하는 모든 수식의 결과를 업데이트하는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-108">Recalculating means updating the result of any formula that uses the data.</span></span>  
  
 <span data-ttu-id="2dccc-109">이 항목의 섹션:</span><span class="sxs-lookup"><span data-stu-id="2dccc-109">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="2dccc-110">수동으로 데이터 처리</span><span class="sxs-lookup"><span data-stu-id="2dccc-110">Manually Process Data</span></span>](#bkmk_mahually_process)  
  
-   [<span data-ttu-id="2dccc-111">데이터 처리 진행률</span><span class="sxs-lookup"><span data-stu-id="2dccc-111">Data Process Progress</span></span>](#bkmk_data_process_progress)  
  
##  <a name="manually-process-data"></a><a name="bkmk_mahually_process"></a><span data-ttu-id="2dccc-112">수동으로 데이터 처리</span><span class="sxs-lookup"><span data-stu-id="2dccc-112">Manually Process Data</span></span>  
  
#### <a name="to-process-data-for-a-single-table-or-all-tables-in-a-model"></a><span data-ttu-id="2dccc-113">모델의 단일 테이블 또는 모든 테이블의 데이터를 처리하려면</span><span class="sxs-lookup"><span data-stu-id="2dccc-113">To process data for a single table or all tables in a model</span></span>  
  
1.  <span data-ttu-id="2dccc-114">모델 디자이너에서 처리할 테이블을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-114">In the model designer, click the table you want to process.</span></span>  
  
2.  <span data-ttu-id="2dccc-115">**모델** 메뉴를 클릭하고 **처리**를 클릭한 다음 **처리** 또는 **모두 처리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-115">Click on the **Model** menu, then click **Process**, and then click **Process** or **Process All**.</span></span>  
  
#### <a name="to-process-data-for-all-tables-using-the-same-connection"></a><span data-ttu-id="2dccc-116">같은 연결을 사용하는 모든 테이블에 대한 데이터를 처리하려면</span><span class="sxs-lookup"><span data-stu-id="2dccc-116">To process data for all tables using the same connection</span></span>  
  
1.  <span data-ttu-id="2dccc-117">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 **모델** 메뉴를 클릭한 다음 **기존 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-117">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Existing Connections**.</span></span>  
  
2.  <span data-ttu-id="2dccc-118">**기존 연결** 대화 상자에서 연결을 선택한 다음 **처리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-118">In the **Existing Connections** dialog box, select a connection, and then click **Process**.</span></span>  
  
#### <a name="to-process-data-for-one-or-more-partitions"></a><span data-ttu-id="2dccc-119">하나 이상의 파티션에 대한 데이터를 처리하려면</span><span class="sxs-lookup"><span data-stu-id="2dccc-119">To process data for one or more partitions</span></span>  
  
1.  <span data-ttu-id="2dccc-120">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 **모델** 메뉴를 클릭하고 **처리**를 가리킨 다음 **파티션 처리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-120">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, then point to **Process**, and then click **Process Partitions**.</span></span>  
  
2.  <span data-ttu-id="2dccc-121">**파티션 처리** 대화 상자의 **모드**에서 다음 처리 모드 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-121">In the **Process Partitions** dialog box, in **Mode**, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="2dccc-122">Mode</span><span class="sxs-lookup"><span data-stu-id="2dccc-122">Mode</span></span>|<span data-ttu-id="2dccc-123">Description</span><span class="sxs-lookup"><span data-stu-id="2dccc-123">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="2dccc-124">**기본값 처리**</span><span class="sxs-lookup"><span data-stu-id="2dccc-124">**Process Default**</span></span>|<span data-ttu-id="2dccc-125">파티션 개체의 처리 상태를 검색하고 필요한 처리를 수행하여 처리되지 않거나 부분적으로 처리된 파티션 개체를 완전히 처리된 상태로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-125">Detects the process state of a partition object, and performs processing necessary to deliver unprocessed or partially processed partition objects to a fully processed state.</span></span> <span data-ttu-id="2dccc-126">빈 테이블 및 파티션에 대한 데이터를 로드하고 계층, 계산 열 및 관계를 작성 또는 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-126">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt.</span></span>|  
    |<span data-ttu-id="2dccc-127">**전체 처리**</span><span class="sxs-lookup"><span data-stu-id="2dccc-127">**Process Full**</span></span>|<span data-ttu-id="2dccc-128">파티션 개체와 여기에 포함된 모든 개체를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-128">Processes a partition object and all the objects that it contains.</span></span> <span data-ttu-id="2dccc-129">이미 처리된 개체에 대해 전체 처리를 실행하면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서는 개체의 모든 데이터를 삭제한 다음 개체를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-129">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="2dccc-130">개체에 구조적 변경이 발생한 경우 이러한 종류의 처리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-130">This kind of processing is required when a structural change has been made to an object.</span></span>|  
    |<span data-ttu-id="2dccc-131">**데이터 처리**</span><span class="sxs-lookup"><span data-stu-id="2dccc-131">**Process Data**</span></span>|<span data-ttu-id="2dccc-132">계층 또는 관계를 다시 작성하거나 계산 열 및 측정값을 다시 계산하지 않고 파티션 또는 테이블에 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-132">Load data into a partition or a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="2dccc-133">**지우기 처리**</span><span class="sxs-lookup"><span data-stu-id="2dccc-133">**Process Clear**</span></span>|<span data-ttu-id="2dccc-134">파티션에서 모든 데이터를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-134">Removes all data from a partition.</span></span>|  
    |<span data-ttu-id="2dccc-135">**증분 처리**</span><span class="sxs-lookup"><span data-stu-id="2dccc-135">**Process Add**</span></span>|<span data-ttu-id="2dccc-136">새 데이터로 파티션을 증분 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-136">Incrementally update partition with new data.</span></span>|  
  
3.  <span data-ttu-id="2dccc-137">파티션 목록에서 처리할 파티션을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-137">In the partitions list, select the partitions you want to process, and then click **OK**.</span></span>  
  
##  <a name="data-process-progress"></a><a name="bkmk_data_process_progress"></a> <span data-ttu-id="2dccc-138">데이터 처리 진행률</span><span class="sxs-lookup"><span data-stu-id="2dccc-138">Data Process Progress</span></span>  
 <span data-ttu-id="2dccc-139">**데이터 처리 진행률** 대화 상자를 사용하면 외부 원본에서 모델로 가져온 데이터의 처리 상태를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-139">The **Data Process Progress** dialog box enables you to monitor the processing of data that you have imported into the model from an external source.</span></span> <span data-ttu-id="2dccc-140">이 대화 상자에 액세스하려면 **모델** 메뉴를 클릭한 다음 **파티션 처리**, **테이블 처리** 또는 **모두 처리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-140">To access this dialog box, click on the **Model** menu, and then click **Process Partitions**, **Process Table** or **Process All**.</span></span>  
  
 <span data-ttu-id="2dccc-141">**상태**</span><span class="sxs-lookup"><span data-stu-id="2dccc-141">**Status**</span></span>  
 <span data-ttu-id="2dccc-142">처리 작업의 성공 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-142">Indicates whether the process operation was successful or not.</span></span>  
  
 <span data-ttu-id="2dccc-143">**세부 정보**</span><span class="sxs-lookup"><span data-stu-id="2dccc-143">**Details**</span></span>  
 <span data-ttu-id="2dccc-144">가져온 테이블 또는 뷰 목록, 가져온 행 수 정보, 문제 보고서에 대한 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-144">Lists the tables and views that were imported, the number of rows that were imported, and provides a link to a report of any issues.</span></span>  
  
 <span data-ttu-id="2dccc-145">**새로 고침 중지**</span><span class="sxs-lookup"><span data-stu-id="2dccc-145">**Stop Refresh**</span></span>  
 <span data-ttu-id="2dccc-146">처리 작업을 중지하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-146">Click to halt the process operation.</span></span> <span data-ttu-id="2dccc-147">이 옵션은 작업에 시간이 너무 많이 걸리거나 오류가 너무 많은 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="2dccc-147">This option is useful if the operation is taking too long, or if there are too many errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dccc-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2dccc-148">See Also</span></span>  
 <span data-ttu-id="2dccc-149">[SSAS 테이블 형식&#41;&#40;데이터 처리](process-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="2dccc-149">[Process Data &#40;SSAS Tabular&#41;](process-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="2dccc-150">데이터 처리 문제 해결&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="2dccc-150">Troubleshoot Process Data &#40;SSAS Tabular&#41;</span></span>](troubleshoot-process-data-ssas-tabular.md)  
  
  
