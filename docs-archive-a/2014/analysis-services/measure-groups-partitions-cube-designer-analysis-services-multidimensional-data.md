---
title: 측정값 그룹 (파티션 탭, 큐브 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionspane.measuregroupdetail.f1
ms.assetid: 58e44b24-cfcd-4908-b445-d4374b961b98
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b73b77bd62c38881be20450f0b7506917014461
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741468"
---
# <a name="measure-groups-partitions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="59fdd-102">측정값 그룹(파티션 탭, 큐브 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="59fdd-102">Measure Groups (Partitions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="59fdd-103">큐브 디자이너의 **파티션** 탭에 있는 **측정값 그룹** 창을 사용하여 큐브의 각 측정값 그룹과 연결된 파티션을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-103">Use the **Measure Groups** pane on the **Partitions** tab in Cube Designer to manage the partitions associated with each measure group in the cube.</span></span>  
  
## <a name="options"></a><span data-ttu-id="59fdd-104">옵션</span><span class="sxs-lookup"><span data-stu-id="59fdd-104">Options</span></span>  
 <span data-ttu-id="59fdd-105">**파티션**</span><span class="sxs-lookup"><span data-stu-id="59fdd-105">**Partitions**</span></span>  
 <span data-ttu-id="59fdd-106">선택한 측정값 그룹을 지원하는 파티션의 목록을 포함하는 표를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-106">Displays a grid containing the list of partitions that support the selected measure group.</span></span> <span data-ttu-id="59fdd-107">표에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-107">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="59fdd-108">**순서로**</span><span class="sxs-lookup"><span data-stu-id="59fdd-108">**(Ordinal)**</span></span>  
 <span data-ttu-id="59fdd-109">측정값 그룹 내 파티션의 서수 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-109">Displays the ordinal position of the partition within the measure group.</span></span>  
  
 <span data-ttu-id="59fdd-110">파티션의 전체 행을 선택하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-110">Click to select the entire row for the partition.</span></span>  
  
 <span data-ttu-id="59fdd-111">**파티션 이름**</span><span class="sxs-lookup"><span data-stu-id="59fdd-111">**Partition Name**</span></span>  
 <span data-ttu-id="59fdd-112">파티션 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-112">Type the name of the selected partition.</span></span>  
  
 <span data-ttu-id="59fdd-113">**원본**</span><span class="sxs-lookup"><span data-stu-id="59fdd-113">**Source**</span></span>  
 <span data-ttu-id="59fdd-114">선택한 파티션에 대한 팩트 테이블 데이터를 제공하는 테이블 이름(테이블 바인딩의 경우) 또는 쿼리(쿼리 바인딩의 경우)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-114">Type the table name (for table binding) or query (for query binding) that provides the fact table data for the selected partition.</span></span>  
  
 <span data-ttu-id="59fdd-115">**...** 단추를 클릭하여 **파티션 원본** 대화 상자를 표시하고 선택한 파티션의 원본을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-115">Click the **...** button to display the **Partition Source** dialog box and define the source for the selected partition.</span></span>  
  
 <span data-ttu-id="59fdd-116">**요약**</span><span class="sxs-lookup"><span data-stu-id="59fdd-116">**Aggregation**</span></span>  
 <span data-ttu-id="59fdd-117">파티션의 집계 모드 및 스토리지 모드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-117">Displays the aggregation mode and the storage mode of the partition.</span></span> <span data-ttu-id="59fdd-118">먼저 ROLAP(관계형 온라인 분석 처리), MOLAP(다차원 온라인 분석 처리) 또는 HOLAP(하이브리드 온라인 분석 처리) 등의 스토리지 모드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-118">The storage mode is displayed first: relational online analytical processing (ROLAP), multidimensional online analytical processing (MOLAP), or hybrid online analytical processing (HOLAP).</span></span> <span data-ttu-id="59fdd-119">집계 모드는 요청된 최적화 비율, 요청되거나 사용된 공간의 측정값 또는 생성된 집계 수로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-119">The aggregation mode is displayed as a percentage of optimization requested, as a measure of space requested or used, or as the number of aggregations created.</span></span> <span data-ttu-id="59fdd-120">**...** 단추를 클릭하여 **집계 디자인 마법사** 를 표시하고 지정한 파티션에 대한 집계 디자인을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-120">Click the **...** button to display the **Aggregation Design Wizard** and define the aggregation design for the specified partition.</span></span>  
  
 <span data-ttu-id="59fdd-121">**설명**</span><span class="sxs-lookup"><span data-stu-id="59fdd-121">**Description**</span></span>  
 <span data-ttu-id="59fdd-122">파티션에 대한 선택적 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-122">Type the optional description of the partition.</span></span>  
  
 <span data-ttu-id="59fdd-123">**새 파티션...**</span><span class="sxs-lookup"><span data-stu-id="59fdd-123">**New Partition...**</span></span>  
 <span data-ttu-id="59fdd-124">**파티션 마법사** 를 표시하고 선택한 측정값 그룹에 새 파티션을 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-124">Click to display the **Partition Wizard** and create a new partition in the selected measure group.</span></span>  
  
 <span data-ttu-id="59fdd-125">**스토리지 설정...**</span><span class="sxs-lookup"><span data-stu-id="59fdd-125">**Storage settings...**</span></span>  
 <span data-ttu-id="59fdd-126">**스토리지 설정** 대화 상자를 표시하고 선택한 파티션에 대한 스토리지 모드, 자동 관리 캐싱 및 알림 설정을 지정하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-126">Click to display the **Storage Settings** dialog box and specify storage mode, proactive caching, and notification settings for the selected partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59fdd-127">이 옵션은 선택한 측정값 그룹의 **파티션** 표에서 임의의 파티션 셀을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-127">This option is enabled only if any cell of a partition is selected in the **Partitions** grid of the selected measure group.</span></span>  
  
 <span data-ttu-id="59fdd-128">**쓰기 저장 설정...**</span><span class="sxs-lookup"><span data-stu-id="59fdd-128">**Writeback settings...**</span></span>  
 <span data-ttu-id="59fdd-129">**쓰기 저장 사용/사용 안 함** 대화 상자를 표시하고 선택한 측정값 그룹에 대한 쓰기 저장 설정을 지정하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-129">Click to display the **Enable/Disable Writeback** dialog box and specify writeback settings for the selected measure group.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="59fdd-130">상황에 맞는 메뉴</span><span class="sxs-lookup"><span data-stu-id="59fdd-130">Context Menu</span></span>  
 <span data-ttu-id="59fdd-131">다음 옵션은 선택한 측정값 그룹의 **파티션** 표에서 행을 마우스 오른쪽 단추로 클릭하면 표시되는 상황에 맞는 메뉴를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-131">The following options are available in the context menu displayed by right-clicking a row in the **Partitions** grid of a selected measure group:</span></span>  
  
|<span data-ttu-id="59fdd-132">옵션</span><span class="sxs-lookup"><span data-stu-id="59fdd-132">Option</span></span>|<span data-ttu-id="59fdd-133">정의</span><span class="sxs-lookup"><span data-stu-id="59fdd-133">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="59fdd-134">**비즈니스 인텔리전스 추가**</span><span class="sxs-lookup"><span data-stu-id="59fdd-134">**Add Business Intelligence**</span></span>|<span data-ttu-id="59fdd-135">**비즈니스 인텔리전스 마법사** 를 표시하고 비즈니스 인텔리전스 기능을 큐브에 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-135">Click to display the **Business Intelligence Wizard** and add business intelligence features to the cube.</span></span> <span data-ttu-id="59fdd-136">**비즈니스 인텔리전스 마법사**에 대한 자세한 내용은 [비즈니스 인텔리전스 마법사 F1 도움말](business-intelligence-wizard-f1-help.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59fdd-136">For more information about the **Business Intelligence Wizard**, see [Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md).</span></span>|  
|<span data-ttu-id="59fdd-137">**새 파티션**</span><span class="sxs-lookup"><span data-stu-id="59fdd-137">**New Partition**</span></span>|<span data-ttu-id="59fdd-138">**파티션 마법사** 를 표시하고 선택한 측정값 그룹에 새 파티션을 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-138">Click to display the **Partition Wizard** and create a new partition in the selected measure group.</span></span>|  
|<span data-ttu-id="59fdd-139">**파티션 이름 바꾸기**</span><span class="sxs-lookup"><span data-stu-id="59fdd-139">**Rename Partition**</span></span>|<span data-ttu-id="59fdd-140">선택한 파티션의 이름을 바꾸려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-140">Select to rename the selected partition.</span></span>|  
|<span data-ttu-id="59fdd-141">**삭제**</span><span class="sxs-lookup"><span data-stu-id="59fdd-141">**Delete**</span></span>|<span data-ttu-id="59fdd-142">**개체 삭제** 대화 상자를 표시하고 선택한 동작을 삭제하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-142">Click to display the **Delete Objects** dialog box and delete the selected action.</span></span><br /><br /> <span data-ttu-id="59fdd-143">참고: 이 옵션은 쓰기 저장 파티션을 선택하면 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-143">Note: This option is disabled if a writeback partition is selected.</span></span>|  
|<span data-ttu-id="59fdd-144">**집계 디자인**</span><span class="sxs-lookup"><span data-stu-id="59fdd-144">**Design Aggregations**</span></span>|<span data-ttu-id="59fdd-145">**집계 디자인 마법사** 를 표시하고 선택한 파티션에 대한 집계 디자인을 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-145">Click to display the **Aggregation Design Wizard** and create an aggregation design for the selected partition.</span></span><br /><br /> <span data-ttu-id="59fdd-146">참고: 이 옵션은 쓰기 저장 파티션을 선택하면 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-146">Note: This option is disabled if a writeback partition is selected.</span></span>|  
|<span data-ttu-id="59fdd-147">**저장소 설정**</span><span class="sxs-lookup"><span data-stu-id="59fdd-147">**Storage Settings**</span></span>|<span data-ttu-id="59fdd-148">**스토리지 설정** 대화 상자를 표시하고 선택한 파티션에 대한 스토리지 모드, 자동 관리 캐싱 및 알림 설정을 지정하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-148">Click to display the **Storage Settings** dialog box and specify storage mode, proactive caching, and notification settings for the selected partition.</span></span>|  
|<span data-ttu-id="59fdd-149">**쓰기 저장 (Writeback) 설정**</span><span class="sxs-lookup"><span data-stu-id="59fdd-149">**Writeback Settings**</span></span>|<span data-ttu-id="59fdd-150">**쓰기 저장 사용/사용 안 함** 대화 상자를 표시하고 선택한 파티션을 포함하는 측정값 그룹에 대한 쓰기 저장 설정을 지정하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-150">Click to display the **Enable/Disable Writeback** dialog box and specify writeback settings for the measure group containing the selected partition.</span></span>|  
|<span data-ttu-id="59fdd-151">**사용 빈도 기반 최적화**</span><span class="sxs-lookup"><span data-stu-id="59fdd-151">**Usage Based Optimization**</span></span>|<span data-ttu-id="59fdd-152">**사용 빈도 기반 최적화 마법사**를 표시하고 선택한 파티션의 기존 사용 패턴을 기반으로 집계 디자인을 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-152">Click to display the **Usage-Based Optimization Wizard** and create an aggregation design based on existing usage patterns for the selected partition.</span></span><br /><br /> <span data-ttu-id="59fdd-153">참고: 이 옵션은 쓰기 저장 파티션을 선택하면 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-153">Note: This option is disabled if a writeback partition is selected.</span></span>|  
|<span data-ttu-id="59fdd-154">**Process**</span><span class="sxs-lookup"><span data-stu-id="59fdd-154">**Process**</span></span>|<span data-ttu-id="59fdd-155">**처리** 대화 상자를 표시하고 선택한 파티션을 처리하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-155">Click to display the **Process** dialog box and process the selected partition.</span></span>|  
|<span data-ttu-id="59fdd-156">**복사**</span><span class="sxs-lookup"><span data-stu-id="59fdd-156">**Copy**</span></span>|<span data-ttu-id="59fdd-157">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-157">This option is disabled.</span></span>|  
|<span data-ttu-id="59fdd-158">**붙여넣기**</span><span class="sxs-lookup"><span data-stu-id="59fdd-158">**Paste**</span></span>|<span data-ttu-id="59fdd-159">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-159">This option is disabled.</span></span>|  
|<span data-ttu-id="59fdd-160">**속성**</span><span class="sxs-lookup"><span data-stu-id="59fdd-160">**Properties**</span></span>|<span data-ttu-id="59fdd-161">**에서 선택한 파티션에 대한** 속성 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 창을 표시하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="59fdd-161">Select to display the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the selected partition.</span></span>|  
  
  
