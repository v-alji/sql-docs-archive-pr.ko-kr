---
title: 도구 및 처리 접근 방법 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- process [Analysis Services]
- processing [Analysis Services]
ms.assetid: 82347a16-4145-4655-8adf-2a300f1fdf99
author: minewiskan
ms.author: owend
ms.openlocfilehash: d2b28ecf29adc8240f76ec9888f9d4cb06dda887
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651348"
---
# <a name="tools-and-approaches-for-processing-analysis-services"></a><span data-ttu-id="2a5d2-102">도구 및 처리 접근 방법(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="2a5d2-102">Tools and Approaches for Processing (Analysis Services)</span></span>
  <span data-ttu-id="2a5d2-103">처리는 Analysis Services가 관계형 데이터 원본을 쿼리하고 해당 데이터를 사용하여 Analysis Services 개체를 채우는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-103">Processing is an operation in which Analysis Services queries a relational data source and populates Analysis Services objects using that data.</span></span>  
  
 <span data-ttu-id="2a5d2-104">Analysis Services 시스템 관리자는 다음과 같은 방법을 사용하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체의 처리를 실행하고 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-104">As an Analysis Services system administrator, you can execute and monitor the processing of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects using these approaches:</span></span>  
  
-   <span data-ttu-id="2a5d2-105">영향 분석을 실행하여 개체 종속성 및 작업 범위 이해</span><span class="sxs-lookup"><span data-stu-id="2a5d2-105">Run Impact Analysis to understand object dependencies and scope of operations</span></span>  
  
-   <span data-ttu-id="2a5d2-106">개별 개체 처리 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a5d2-106">Process individual objects in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
  
-   <span data-ttu-id="2a5d2-107">개별 개체 또는 여러 개체 처리 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a5d2-107">Process individual or multiple objects in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]</span></span>  
  
-   <span data-ttu-id="2a5d2-108">영향 분석을 실행하여 현재 동작의 결과로 처리되지 않는 관련 개체의 목록 검토</span><span class="sxs-lookup"><span data-stu-id="2a5d2-108">Run Impact Analysis to review a list of related objects that will be unprocessed as result of the current action.</span></span>  
  
-   <span data-ttu-id="2a5d2-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 의 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] XMLA 쿼리 창에서 스크립트를 생성하고 실행하여 개별 개체 또는 여러 개체 처리</span><span class="sxs-lookup"><span data-stu-id="2a5d2-109">Generate and run a script in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA Query window in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to process individual or multiple objects</span></span>  
  
-   <span data-ttu-id="2a5d2-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] PowerShell cmdlet 사용</span><span class="sxs-lookup"><span data-stu-id="2a5d2-110">Use [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] PowerShell cmdlets</span></span>  
  
-   <span data-ttu-id="2a5d2-111">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지의 제어 흐름 및 태스크 사용</span><span class="sxs-lookup"><span data-stu-id="2a5d2-111">Use control flows and tasks in [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages</span></span>  
  
-   <span data-ttu-id="2a5d2-112">SQL Server 프로파일러를 사용하여 처리 모니터링</span><span class="sxs-lookup"><span data-stu-id="2a5d2-112">Monitor processing with SQL Server Profiler</span></span>  
  
-   <span data-ttu-id="2a5d2-113">AMO를 사용하여 사용자 지정 솔루션 프로그래밍.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-113">Program a custom solution using AMO.</span></span> <span data-ttu-id="2a5d2-114">자세한 내용은 [Programming AMO OLAP Basic Objects](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-basic-objects)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-114">For more information, see [Programming AMO OLAP Basic Objects](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-basic-objects).</span></span>  
  
 <span data-ttu-id="2a5d2-115">처리는 다양하게 구성 가능한 작업으로, 개체 수준에서 전체 처리가 발생하는지 증분 처리가 발생하는지 결정하는 일련의 처리 옵션으로 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-115">Processing is a highly configurable operation, controlled by a set of processing options that determine whether full or incremental processing occurs at the object level.</span></span> <span data-ttu-id="2a5d2-116">처리 옵션 및 개체에 대한 자세한 내용은 [처리 옵션 및 설정&#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md) 및 [Analysis Services 개체 처리](processing-analysis-services-objects.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-116">For more information about processing options and objects, see [Processing Options and Settings &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md) and [Processing Analysis Services Objects](processing-analysis-services-objects.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a5d2-117">이 항목에서는 다차원 모델을 처리하기 위한 도구와 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-117">This topic describes the tools and approaches for processing multidimensional models.</span></span> <span data-ttu-id="2a5d2-118">테이블 형식 모델을 처리 하는 방법은 [데이터베이스, 테이블 또는 파티션](../tabular-models/process-database-table-or-partition-analysis-services.md) 처리 및 데이터 처리 [&#40;SSAS 테이블 형식&#41;](../process-data-ssas-tabular.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-118">For more information about processing tabular models, see [Process Database, Table, or Partition](../tabular-models/process-database-table-or-partition-analysis-services.md) and [Process Data &#40;SSAS Tabular&#41;](../process-data-ssas-tabular.md).</span></span>  
  
### <a name="processing-objects-in-sql-server-management-studio"></a><span data-ttu-id="2a5d2-119">SQL Server Management Studio에서 개체 처리</span><span class="sxs-lookup"><span data-stu-id="2a5d2-119">Processing objects in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="2a5d2-120">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 시작하고 Analysis Services에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-120">Start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and connect to Analysis Services.</span></span>  
  
2.  <span data-ttu-id="2a5d2-121">처리할 Analysis Services 개체를 마우스 오른쪽 단추로 클릭한 다음 **처리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-121">Right-click the Analysis Services object you want to process and then click **Process**.</span></span> <span data-ttu-id="2a5d2-122">다음과 같은 수준 모두에서 데이터를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-122">You can process data at any of these levels:</span></span>  
  
    -   <span data-ttu-id="2a5d2-123">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="2a5d2-123">Databases</span></span>  
  
    -   <span data-ttu-id="2a5d2-124">큐브</span><span class="sxs-lookup"><span data-stu-id="2a5d2-124">Cubes</span></span>  
  
    -   <span data-ttu-id="2a5d2-125">측정값 그룹 또는 측정값 그룹의 개별 파티션</span><span class="sxs-lookup"><span data-stu-id="2a5d2-125">Measure Groups or individual partitions in the measure group</span></span>  
  
    -   <span data-ttu-id="2a5d2-126">차원</span><span class="sxs-lookup"><span data-stu-id="2a5d2-126">Dimensions</span></span>  
  
    -   <span data-ttu-id="2a5d2-127">마이닝 모델</span><span class="sxs-lookup"><span data-stu-id="2a5d2-127">Mining Models</span></span>  
  
    -   <span data-ttu-id="2a5d2-128">마이닝 구조</span><span class="sxs-lookup"><span data-stu-id="2a5d2-128">Mining Structures</span></span>  
  
     <span data-ttu-id="2a5d2-129">Analysis Services 개체는 계층적입니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-129">Analysis Services objects are hierarchical.</span></span> <span data-ttu-id="2a5d2-130">데이터베이스를 선택하면 데이터베이스에 포함된 모든 개체에 대해 처리가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-130">If you choose database, processing can occur for all of the objects contained in the database.</span></span> <span data-ttu-id="2a5d2-131">처리가 실제로 발생하는지 여부는 선택한 처리 옵션과 개체 상태에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-131">Whether processing actually occurs will vary depending on the process option you select and the state of the object.</span></span> <span data-ttu-id="2a5d2-132">개체가 처리되지 않은 경우 해당 부모를 처리하면 해당 개체가 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-132">Specifically, if an object is unprocessed, processing its parent will result in that object getting processed.</span></span> <span data-ttu-id="2a5d2-133">개체 종속성에 대한 자세한 내용은 [Processing Analysis Services Objects](processing-analysis-services-objects.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-133">For more information about object dependencies, see [Processing Analysis Services Objects](processing-analysis-services-objects.md).</span></span>  
  
3.  <span data-ttu-id="2a5d2-134">**처리** 대화 상자의 **처리 옵션**에서 제공된 기본값을 사용하거나 목록에서 다른 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-134">In the **Process** dialog box, in **Process Options**, use the default value provided or select a different option from the list.</span></span> <span data-ttu-id="2a5d2-135">각 옵션에 대한 자세한 내용은 [처리 옵션 및 설정&#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-135">For more information about each option, see [Processing Options and Settings &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md).</span></span>  
  
4.  <span data-ttu-id="2a5d2-136">**영향 분석** 을 클릭하면 처리 대화 상자에 나열된 개체를 처리하는 경우 영향을 받는 종속 개체를 식별하고 선택적으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-136">Click **Impact Analysis** to identify and optionally process dependent objects that are affected if the objects listed in the Process dialog box are processed.</span></span>  
  
5.  <span data-ttu-id="2a5d2-137">원하는 경우 **설정 변경** 을 클릭하여 처리 순서, 특정 오류 유형에 대한 처리 동작 및 기타 설정을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-137">Optionally, click **Change Settings** to modify the processing order, processing behavior relative to specific types of errors, and other settings.</span></span>  
  
6.  <span data-ttu-id="2a5d2-138">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-138">Click **OK**.</span></span>  
  
     <span data-ttu-id="2a5d2-139">프로세스 진행률 대화 상자에 각 명령의 현재 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-139">The Process Progress dialog box provides ongoing status for each command.</span></span> <span data-ttu-id="2a5d2-140">상태 메시지가 잘리는 경우 **자세히 보기** 를 클릭하면 전체 메시지를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-140">If a status message is truncated, you can click **View Details** to read the entire message.</span></span>  
  
### <a name="processing-objects-in-sql-server-data-tools"></a><span data-ttu-id="2a5d2-141">SQL Server 데이터 도구에서 개체 처리</span><span class="sxs-lookup"><span data-stu-id="2a5d2-141">Processing Objects in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="2a5d2-142">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 를 시작하고 배포된 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-142">Start [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and open a project that has been deployed.</span></span>  
  
2.  <span data-ttu-id="2a5d2-143">솔루션 탐색기의 배포된 프로젝트에서 **차원** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-143">In Solution Explorer, under the deployed project, expand the **Dimensions** folder.</span></span>  
  
3.  <span data-ttu-id="2a5d2-144">차원을 마우스 오른쪽 단추로 클릭한 다음 **처리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-144">Right-click a dimension, and then click **Process**.</span></span> <span data-ttu-id="2a5d2-145">여러 차원을 마우스 오른쪽 단추로 클릭하여 여러 개체를 한 번에 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-145">You can right-click multiple dimensions to process multiple objects at once.</span></span> <span data-ttu-id="2a5d2-146">자세한 내용은 [일괄 처리&#40;Analysis Services&#41;](batch-processing-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-146">For more information, see [Batch Processing &#40;Analysis Services&#41;](batch-processing-analysis-services.md).</span></span>  
  
4.  <span data-ttu-id="2a5d2-147">**차원 처리** 대화 상자에 있는 **개체 목록** 의 **처리 옵션**열에서 이 열에 대한 옵션이 **전체 처리**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-147">In the **Process Dimension** dialog box, in the **Process Options** column under **Object list**, verify that the option for this column is **Process Full**.</span></span> <span data-ttu-id="2a5d2-148">그렇지 않을 경우 **처리 옵션**에서 해당 옵션을 클릭한 다음 드롭다운 목록에서 **전체 처리** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-148">If it is not, under **Process Options**, click the option, and select **Process Full** from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="2a5d2-149">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-149">Click **Run**.</span></span>  
  
6.  <span data-ttu-id="2a5d2-150">처리를 마치면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-150">When processing is finished, click **Close**.</span></span>  
  
##  <a name="run-impact-analysis-to-identify-object-dependencies-and-scope-of-operations"></a><a name="bkmk_impactanalysis"></a><span data-ttu-id="2a5d2-151">영향 분석을 실행 하 여 개체 종속성 및 작업 범위 식별</span><span class="sxs-lookup"><span data-stu-id="2a5d2-151">Run Impact Analysis to identify object dependencies and scope of operations</span></span>  
  
1.  <span data-ttu-id="2a5d2-152">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 또는 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 의 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]개체를 처리하기 전에 **개체 처리** 대화 상자 중 하나에서 **영향 분석** 을 클릭하여 관련 개체에 대한 영향을 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-152">Before you process an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object in either [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] or [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can analyze the effect on related objects by clicking **Impact Analysis** in one of the **Process Objects** dialog boxes.</span></span>  
  
2.  <span data-ttu-id="2a5d2-153">차원, 큐브, 측정값 그룹 또는 파티션을 마우스 오른쪽 단추로 클릭하여 **개체 처리** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-153">Right-click a dimension, cube, measure group, or partition to open a **Process Objects** dialog box.</span></span>  
  
3.  <span data-ttu-id="2a5d2-154">**영향 분석**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-154">Click **Impact Analysis**.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="2a5d2-155">는 모델을 검색한 후 처리하기 위해 선택한 모델과 관련된 개체에 대한 다시 처리 요구 사항에 대해 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-155">scans the model and reports on reprocessing requirements for objects that are related to the one you selected for processing.</span></span>  
  
### <a name="processing-objects-using-xmla"></a><span data-ttu-id="2a5d2-156">XMLA를 사용하여 개체 처리</span><span class="sxs-lookup"><span data-stu-id="2a5d2-156">Processing objects using XMLA</span></span>  
  
1.  <span data-ttu-id="2a5d2-157">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 시작하고 Analysis Services에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-157">Start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and connect to Analysis Services.</span></span>  
  
2.  <span data-ttu-id="2a5d2-158">처리할 개체를 마우스 오른쪽 단추로 클릭한 다음 **처리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-158">Right-click the object to be processed and then click **Process**.</span></span>  
  
3.  <span data-ttu-id="2a5d2-159">**처리** 대화 상자에서 사용할 처리 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-159">In the **Process** dialog box, select the process option you want to use.</span></span> <span data-ttu-id="2a5d2-160">기타 설정을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-160">Modify any other settings.</span></span> <span data-ttu-id="2a5d2-161">영향 분석을 실행하여 변경해야 할 사항을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-161">Run Impact Analysis to identify any changes you might need to make.</span></span>  
  
4.  <span data-ttu-id="2a5d2-162">**개체 처리** 화면에서 **스크립트** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-162">Click **Script** on the **Process Objects** screen.</span></span>  
  
     <span data-ttu-id="2a5d2-163">이렇게 하면 XMLA 스크립트가 생성되고 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA 쿼리 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-163">This generates an XMLA script and opens an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA Query window.</span></span>  
  
5.  <span data-ttu-id="2a5d2-164">대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-164">Close the dialog box.</span></span> <span data-ttu-id="2a5d2-165">스크립트에는 대화 상자에 지정된 처리 명령과 옵션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-165">The script contains the processing command and options that were specified in the dialog box.</span></span>  
  
6.  <span data-ttu-id="2a5d2-166">필요에 따라 동일한 일괄 처리의 추가 개체를 처리하려는 경우 스크립트에 계속해서 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-166">Optionally, you can continue adding to the script if you want to process additional objects in the same batch.</span></span> <span data-ttu-id="2a5d2-167">계속하려면 이전 단계를 반복하여 모든 처리 작업에 단일 스크립트를 사용할 수 있도록 생성된 스크립트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-167">To continue, repeat the previous steps, appending the generated script so that you have a single script for all processing operations.</span></span> <span data-ttu-id="2a5d2-168">예를 보려면 [Schedule SSAS Administrative Tasks with SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-168">To view an example, see [Schedule SSAS Administrative Tasks with SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md).</span></span>  
  
7.  <span data-ttu-id="2a5d2-169">메뉴 모음에서 **쿼리**를 클릭한 다음 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-169">From the menu bar, click **Query**, and then click **Execute**.</span></span>  
  
### <a name="processing-objects-using-powershell"></a><span data-ttu-id="2a5d2-170">PowerShell을 사용하여 개체 처리</span><span class="sxs-lookup"><span data-stu-id="2a5d2-170">Processing objects using PowerShell</span></span>  
  
1.  <span data-ttu-id="2a5d2-171">이 SQL Server 릴리스부터는 Analysis Services PowerShell cmdlet을 사용하여 개체를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-171">Starting in this release of SQL Server, you can use Analysis Services PowerShell cmdlets to process objects.</span></span> <span data-ttu-id="2a5d2-172">다음 cmdlet은 대화형으로 실행하거나 스크립트로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-172">The following cmdlets can be run interactively or in script:</span></span>  
  
    -   [<span data-ttu-id="2a5d2-173">Invoke-ProcessCube cmdlet</span><span class="sxs-lookup"><span data-stu-id="2a5d2-173">Invoke-ProcessCube cmdlet</span></span>](/powershell/module/sqlserver/invoke-processcube)  
  
    -   [<span data-ttu-id="2a5d2-174">Invoke-ProcessDimension cmdlet</span><span class="sxs-lookup"><span data-stu-id="2a5d2-174">Invoke-ProcessDimension cmdlet</span></span>](/powershell/module/sqlserver/invoke-processdimension)  
  
    -   [<span data-ttu-id="2a5d2-175">Invoke-ProcessPartition cmdlet</span><span class="sxs-lookup"><span data-stu-id="2a5d2-175">Invoke-ProcessPartition cmdlet</span></span>](/powershell/module/sqlserver/invoke-processpartition)  
  
    -   <span data-ttu-id="2a5d2-176">[Invoke-ASCmd cmdlet](/powershell/module/sqlserver/invoke-ascmd)- 처리 명령을 포함하는 XMLA, MDX 또는 DMX 스크립트를 실행하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-176">[Invoke-ASCmd cmdlet](/powershell/module/sqlserver/invoke-ascmd), which can be used to execute XMLA, MDX, or DMX script that includes processing commands.</span></span>  
  
### <a name="monitoring-object-processing-using-sql-server-profiler"></a><span data-ttu-id="2a5d2-177">SQL Server 프로파일러를 사용하여 개체 처리 모니터링</span><span class="sxs-lookup"><span data-stu-id="2a5d2-177">Monitoring object processing using SQL Server Profiler</span></span>  
  
1.  <span data-ttu-id="2a5d2-178">SQL Server 프로파일러의 Analysis Services 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-178">Connect to an Analysis Services instance in SQL Server Profiler.</span></span>  
  
2.  <span data-ttu-id="2a5d2-179">이벤트 선택에서 **모든 이벤트 표시** 를 클릭하여 목록에 모든 이벤트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-179">In Events Selection, click **Show all events** to add all events to the list.</span></span>  
  
3.  <span data-ttu-id="2a5d2-180">다음 이벤트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-180">Choose the following events:</span></span>  
  
    -   <span data-ttu-id="2a5d2-181">처리가 시작되고 중지되는 때를 표시하려면**명령 시작** 및 **Comm및 End** to show when processing starts 및 stops</span><span class="sxs-lookup"><span data-stu-id="2a5d2-181">**Command Begin** and **Command End** to show when processing starts and stops</span></span>  
  
    -   <span data-ttu-id="2a5d2-182">오류를 캡처하려면**오류** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-182">**Error** to capture any errors</span></span>  
  
    -   <span data-ttu-id="2a5d2-183">처리 상태에 대해 보고하고 데이터를 검색하는 데 사용되는 SQL 쿼리를 표시하려면**진행률 보고서 시작**, **진행률 보고서 현재 부분**및 **진행률 보고서 끝** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-183">**Progress Report Begin**, **Progress Report Current**, and **Progress Report End** to report on process status and show the SQL queries used to retrieve the data</span></span>  
  
    -   <span data-ttu-id="2a5d2-184">큐브 계산을 표시하려면**MDX 스크립트 실행의 시작** 및 **MDX 스크립트 실행의 끝** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-184">**Execute MDX Script Begin** and **Execute MDX Script End** to show the cube calculations</span></span>  
  
    -   <span data-ttu-id="2a5d2-185">필요에 따라 처리와 관련된 성능 문제를 진단하려는 경우 잠금 이벤트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-185">Optionally, add lock events if you are diagnosing performance problems related to processing</span></span>  
  
### <a name="process-analysis-services-objects-using-integration-services"></a><span data-ttu-id="2a5d2-186">Integration Services를 사용하여 Analysis Services 개체 처리</span><span class="sxs-lookup"><span data-stu-id="2a5d2-186">Process Analysis Services objects using Integration Services</span></span>  
  
1.  <span data-ttu-id="2a5d2-187">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 Analysis Services 처리 태스크를 사용하여 원본 관계형 데이터베이스를 정기적으로 업데이트할 때 자동으로 개체를 새 데이터로 채우는 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-187">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], create a package that uses the Analysis Services Processing Task to automatically populate objects with new data when you make regular updates to your source relational database.</span></span>  
  
2.  <span data-ttu-id="2a5d2-188">**SSIS 도구 상자**에서 **Analysis Services 처리** 를 두 번 클릭하여 패키지에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-188">In the **SSIS Toolbox**, double-click **Analysis Services Processing** to add it to the package.</span></span>  
  
3.  <span data-ttu-id="2a5d2-189">태스크를 편집하여 데이터베이스에 대한 연결, 처리할 개체 및 처리 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-189">Edit the task to specify a connection to the database, which objects to process, and the process option.</span></span> <span data-ttu-id="2a5d2-190">이 태스크의 구현 방법은 [Analysis Services Processing Task](../../integration-services/control-flow/analysis-services-processing-task.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2a5d2-190">For more information about how to implement this task, see [Analysis Services Processing Task](../../integration-services/control-flow/analysis-services-processing-task.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a5d2-191">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a5d2-191">See Also</span></span>  
 [<span data-ttu-id="2a5d2-192">다차원 모델 개체 처리</span><span class="sxs-lookup"><span data-stu-id="2a5d2-192">Multidimensional Model Object Processing</span></span>](processing-a-multidimensional-model-analysis-services.md)  
  
  
