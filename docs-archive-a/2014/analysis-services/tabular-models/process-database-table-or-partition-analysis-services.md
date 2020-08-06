---
title: 데이터베이스, 테이블 또는 파티션 처리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.SSMS.PARTITIONS.PROCESSINGOPTIONS.IMBI.F1
ms.assetid: 307d69c3-cabb-4dfa-b90c-9852492c1213
author: minewiskan
ms.author: owend
ms.openlocfilehash: b5d3840be43798536f1bb517007a7974a1e08728
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728764"
---
# <a name="process-database-table-or-partition"></a><span data-ttu-id="368c2-102">데이터베이스, 테이블 또는 파티션 처리</span><span class="sxs-lookup"><span data-stu-id="368c2-102">Process Database, Table, or Partition</span></span>
  <span data-ttu-id="368c2-103">이 항목의 태스크에서는의 \*\*처리 \<object> \*\* 대화 상자를 사용 하 여 테이블 형식 모델 데이터베이스, 테이블 또는 파티션을 수동으로 처리 하는 방법에 대해 설명 합니다 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="368c2-103">The tasks in this topic describe how to process a tabular model database, table, or partitions manually by using the **Process \<object>** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="368c2-104">테이블 형식 모델 처리에 대한 자세한 내용은 [데이터 처리&#40;SSAS 테이블 형식&#41;](../process-data-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="368c2-104">For more information about tabular model processing, see [Process Data &#40;SSAS Tabular&#41;](../process-data-ssas-tabular.md).</span></span>  
  
##  <a name="tasks"></a><a name="bkmk_process_tasks"></a> <span data-ttu-id="368c2-105">작업</span><span class="sxs-lookup"><span data-stu-id="368c2-105">Tasks</span></span>  
  
###  <a name="to-process-a-database"></a><a name="bkmk_process_db"></a><span data-ttu-id="368c2-106">데이터베이스를 처리 하려면</span><span class="sxs-lookup"><span data-stu-id="368c2-106">To process a database</span></span>  
  
1.  <span data-ttu-id="368c2-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 처리할 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **데이터베이스 처리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-107">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click on the database you want to process, and then click **Process Database**.</span></span>  
  
2.  <span data-ttu-id="368c2-108">**데이터베이스 처리** 대화 상자의 **모드** 목록 상자에서 다음 처리 모드 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-108">In the **Process Database** dialog box, in the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="368c2-109">Mode</span><span class="sxs-lookup"><span data-stu-id="368c2-109">Mode</span></span>|<span data-ttu-id="368c2-110">Description</span><span class="sxs-lookup"><span data-stu-id="368c2-110">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="368c2-111">**기본값 처리**</span><span class="sxs-lookup"><span data-stu-id="368c2-111">**Process Default**</span></span>|<span data-ttu-id="368c2-112">데이터베이스 개체의 처리 상태를 검색하고 필요한 처리를 수행하여 처리되지 않거나 부분적으로 처리된 개체를 완전히 처리된 상태로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-112">Detects the process state of database objects, and performs processing necessary to deliver unprocessed or partially processed objects to a fully processed state.</span></span> <span data-ttu-id="368c2-113">빈 테이블 및 파티션에 대한 데이터를 로드하고 계층, 계산 열 및 관계를 작성 또는 다시 작성(다시 계산)합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-113">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt (recalculated).</span></span>|  
    |<span data-ttu-id="368c2-114">**전체 처리**</span><span class="sxs-lookup"><span data-stu-id="368c2-114">**Process Full**</span></span>|<span data-ttu-id="368c2-115">데이터베이스 및 이 데이터베이스에 포함된 모든 개체를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-115">Processes a database and all the objects that it contains.</span></span> <span data-ttu-id="368c2-116">이미 처리된 개체에 대해 전체 처리를 실행하면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 개체의 모든 데이터를 삭제한 다음 개체를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-116">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="368c2-117">개체에 구조적 변경이 발생한 경우 이러한 종류의 처리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-117">This kind of processing is required when a structural change has been made to an object.</span></span> <span data-ttu-id="368c2-118">이 옵션에 가장 많은 리소스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-118">This option requires the most resources.</span></span>|  
    |<span data-ttu-id="368c2-119">**지우기 처리**</span><span class="sxs-lookup"><span data-stu-id="368c2-119">**Process Clear**</span></span>|<span data-ttu-id="368c2-120">데이터베이스 개체에서 모든 데이터를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-120">Removes all data from database objects.</span></span>|  
    |<span data-ttu-id="368c2-121">**다시 계산 처리**</span><span class="sxs-lookup"><span data-stu-id="368c2-121">**Process Recalc**</span></span>|<span data-ttu-id="368c2-122">계층, 관계 및 계산 열을 업데이트하고 다시 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-122">Updates and recalculates hierarchies, relationships, and calculated columns.</span></span>|  
  
3.  <span data-ttu-id="368c2-123">**처리** 확인란 열에서 선택된 모드로 처리할 파티션을 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-123">In the **Process** checkbox column, select the partitions you want to process with the selected mode, and then click **Ok**.</span></span>  
  
###  <a name="to-process-a-table"></a><a name="bkmk_process_table"></a><span data-ttu-id="368c2-124">테이블을 처리 하려면</span><span class="sxs-lookup"><span data-stu-id="368c2-124">To process a table</span></span>  
  
1.  <span data-ttu-id="368c2-125">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 처리할 테이블이 포함된 테이블 형식 model 데이터베이스의 **테이블** 노드를 확장하고 처리할 테이블을 마우스 오른쪽 단추로 클릭한 다음 **테이블 처리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-125">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], in the tabular model database which contains the table you want to process, expand the **Tables** node, then right-click on the table you want to process, and then click **Process Table**.</span></span>  
  
2.  <span data-ttu-id="368c2-126">**테이블 처리** 대화 상자의 **모드** 목록 상자에서 다음 처리 모드 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-126">In the **Process Table** dialog box, in the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="368c2-127">Mode</span><span class="sxs-lookup"><span data-stu-id="368c2-127">Mode</span></span>|<span data-ttu-id="368c2-128">Description</span><span class="sxs-lookup"><span data-stu-id="368c2-128">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="368c2-129">**기본값 처리**</span><span class="sxs-lookup"><span data-stu-id="368c2-129">**Process Default**</span></span>|<span data-ttu-id="368c2-130">테이블 개체의 처리 상태를 검색하고 필요한 처리를 수행하여 처리되지 않거나 부분적으로 처리된 개체를 완전히 처리된 상태로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-130">Detects the process state of a table object, and performs processing necessary to deliver unprocessed or partially processed objects to a fully processed state.</span></span> <span data-ttu-id="368c2-131">빈 테이블 및 파티션에 대한 데이터를 로드하고 계층, 계산 열 및 관계를 작성 또는 다시 작성(다시 계산)합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-131">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt (recalculated).</span></span>|  
    |<span data-ttu-id="368c2-132">**전체 처리**</span><span class="sxs-lookup"><span data-stu-id="368c2-132">**Process Full**</span></span>|<span data-ttu-id="368c2-133">테이블 개체와 여기에 포함된 모든 개체를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-133">Processes a table object and all the objects that it contains.</span></span> <span data-ttu-id="368c2-134">이미 처리된 개체에 대해 전체 처리를 실행하면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 개체의 모든 데이터를 삭제한 다음 개체를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-134">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="368c2-135">개체에 구조적 변경이 발생한 경우 이러한 종류의 처리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-135">This kind of processing is required when a structural change has been made to an object.</span></span> <span data-ttu-id="368c2-136">이 옵션에 가장 많은 리소스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-136">This option requires the most resources.</span></span>|  
    |<span data-ttu-id="368c2-137">**데이터 처리**</span><span class="sxs-lookup"><span data-stu-id="368c2-137">**Process Data**</span></span>|<span data-ttu-id="368c2-138">계층 또는 관계를 다시 작성하거나 계산 열 및 측정값을 다시 계산하지 않고 테이블에 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-138">Load data into a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="368c2-139">**지우기 처리**</span><span class="sxs-lookup"><span data-stu-id="368c2-139">**Process Clear**</span></span>|<span data-ttu-id="368c2-140">테이블과 테이블 파티션에서 모든 데이터를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-140">Removes all data from a table and any table partitions.</span></span>|  
    |<span data-ttu-id="368c2-141">**조각 모음 처리**</span><span class="sxs-lookup"><span data-stu-id="368c2-141">**Process Defrag**</span></span>|<span data-ttu-id="368c2-142">보조 테이블 인덱스를 조각 모음합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-142">Defragments the auxiliary table indexes.</span></span>|  
  
3.  <span data-ttu-id="368c2-143">테이블 확인란 열에서 테이블을 확인하고 처리할 테이블을 추가로 선택한 후(선택 사항) **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-143">In the table checkbox column, verify the table and optionally select any additional tables you want to process, and then click **Ok**.</span></span>  
  
###  <a name="to-process-one-or-more-partitions"></a><a name="bkmk_process_partition"></a> <span data-ttu-id="368c2-144">하나 이상의 파티션을 처리하려면</span><span class="sxs-lookup"><span data-stu-id="368c2-144">To process one or more partitions</span></span>  
  
1.  <span data-ttu-id="368c2-145">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 처리할 파티션이 있는 테이블을 마우스 오른쪽 단추로 클릭한 다음 **파티션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-145">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click on the table that has the partitions you want to process, and then click **Partitions**.</span></span>  
  
2.  <span data-ttu-id="368c2-146">**파티션** 대화 상자의 **파티션**에서 처리 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-146">In the **Partitions** dialog box, in **Partitions**, click the Process button.</span></span>  
  
3.  <span data-ttu-id="368c2-147">**파티션 처리** 대화 상자의 **모드** 목록 상자에서 다음 처리 모드 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-147">In the **Process Partition** dialog box, in the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="368c2-148">Mode</span><span class="sxs-lookup"><span data-stu-id="368c2-148">Mode</span></span>|<span data-ttu-id="368c2-149">Description</span><span class="sxs-lookup"><span data-stu-id="368c2-149">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="368c2-150">**기본값 처리**</span><span class="sxs-lookup"><span data-stu-id="368c2-150">**Process Default**</span></span>|<span data-ttu-id="368c2-151">파티션 개체의 처리 상태를 검색하고 필요한 처리를 수행하여 처리되지 않거나 부분적으로 처리된 파티션 개체를 완전히 처리된 상태로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-151">Detects the process state of a partition object, and performs processing necessary to deliver unprocessed or partially processed partition objects to a fully processed state.</span></span> <span data-ttu-id="368c2-152">빈 테이블 및 파티션에 대한 데이터를 로드하고 계층, 계산 열 및 관계를 작성 또는 다시 작성(다시 계산)합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-152">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt (recalculated).</span></span>|  
    |<span data-ttu-id="368c2-153">**전체 처리**</span><span class="sxs-lookup"><span data-stu-id="368c2-153">**Process Full**</span></span>|<span data-ttu-id="368c2-154">파티션 개체와 여기에 포함된 모든 개체를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-154">Processes a partition object and all the objects that it contains.</span></span> <span data-ttu-id="368c2-155">이미 처리된 개체에 대해 전체 처리를 실행하면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 개체의 모든 데이터를 삭제한 다음 개체를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-155">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="368c2-156">개체에 구조적 변경이 발생한 경우 이러한 종류의 처리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-156">This kind of processing is required when a structural change has been made to an object.</span></span>|  
    |<span data-ttu-id="368c2-157">**데이터 처리**</span><span class="sxs-lookup"><span data-stu-id="368c2-157">**Process Data**</span></span>|<span data-ttu-id="368c2-158">계층 또는 관계를 다시 작성하거나 계산 열 및 측정값을 다시 계산하지 않고 파티션 또는 테이블에 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-158">Load data into a partition or a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="368c2-159">**지우기 처리**</span><span class="sxs-lookup"><span data-stu-id="368c2-159">**Process Clear**</span></span>|<span data-ttu-id="368c2-160">파티션에서 모든 데이터를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-160">Removes all data from a partition.</span></span>|  
    |<span data-ttu-id="368c2-161">**증분 처리**</span><span class="sxs-lookup"><span data-stu-id="368c2-161">**Process Add**</span></span>|<span data-ttu-id="368c2-162">새 데이터로 파티션을 증분 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-162">Incrementally update partition with new data.</span></span>|  
  
4.  <span data-ttu-id="368c2-163">**처리** 확인란 열에서 선택된 모드로 처리할 파티션을 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="368c2-163">In the **Process** checkbox column, select the partitions you want to process with the selected mode, and then click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="368c2-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="368c2-164">See Also</span></span>  
 <span data-ttu-id="368c2-165">[테이블 형식 모델 파티션이 SSAS 테이블 형식&#41;을 &#40;](tabular-model-partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="368c2-165">[Tabular Model Partitions &#40;SSAS Tabular&#41;](tabular-model-partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="368c2-166">테이블 형식 모델 파티션 만들기 및 관리&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="368c2-166">Create and Manage Tabular Model Partitions &#40;SSAS Tabular&#41;</span></span>](create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  
