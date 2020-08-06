---
title: Analysis Services DMX 쿼리 디자이너 사용자 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10012"
- sql12.rtp.rptdesigner.dataview.asquerydesigner.f1
helpviewer_keywords:
- Analysis Services [DMX]
- DMX [Analysis Services], user interface
- query designers [DMX]
ms.assetid: 5fd726a4-aed7-4e6c-9404-ccb2db66cf26
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b641423ad9563f252ba89f51fcd8cafb0ed7bbe8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647467"
---
# <a name="analysis-services-dmx-query-designer-user-interface"></a><span data-ttu-id="d2126-102">Analysis Services DMX 쿼리 디자이너 사용자 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d2126-102">Analysis Services DMX Query Designer User Interface</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="d2126-103">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 데이터 원본에 대한 DMX(Data Mining Expressions) 쿼리 및 MDX(Multidimensional Expressions) 쿼리를 작성하기 위한 그래픽 쿼리 디자이너를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-103">provides graphical query designers for building Data Mining Expressions (DMX) queries and Multidimensional Expression (MDX) queries for an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="d2126-104">이 항목에서는 DMX 쿼리 디자이너에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-104">This topic describes the DMX query designer.</span></span> <span data-ttu-id="d2126-105">MDX 쿼리 디자이너에 대한 자세한 내용은 [Analysis Services MDX Query Designer User Interface](analysis-services-mdx-query-designer-user-interface.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d2126-105">For more information about the MDX query designer, see [Analysis Services MDX Query Designer User Interface](analysis-services-mdx-query-designer-user-interface.md).</span></span>  
  
 <span data-ttu-id="d2126-106">DMX 그래픽 쿼리 디자이너에는 디자인, 쿼리 및 결과의 3가지 모드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-106">The DMX graphical query designer has three modes: Design, Query, and Result.</span></span> <span data-ttu-id="d2126-107">모드를 전환하려면 쿼리 디자인 창을 마우스 오른쪽 단추로 클릭하고 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-107">To switch modes, right-click on the Query Design pane, and select the mode.</span></span> <span data-ttu-id="d2126-108">각 모드는 메타데이터 창을 제공하며 이 창에서는 선택한 큐브에서 멤버를 끌어서 보고서 처리 시 데이터 세트의 데이터를 검색하는 DMX 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-108">Each mode provides a Metadata pane from which you can drag members from the selected cubes to build a DMX query that retrieves data for a dataset when the report is processed.</span></span>  
  
## <a name="graphical-dmx-query-designer-toolbar"></a><span data-ttu-id="d2126-109">그래픽 DMX 쿼리 디자이너 도구 모음</span><span class="sxs-lookup"><span data-stu-id="d2126-109">Graphical DMX Query Designer Toolbar</span></span>  
 <span data-ttu-id="d2126-110">쿼리 디자이너 도구 모음은 그래픽 인터페이스를 사용하여 DMX 쿼리를 디자인하는 데 도움이 되는 단추를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-110">The query designer toolbar provides buttons to help you design DMX queries using the graphical interface.</span></span> <span data-ttu-id="d2126-111">다음 표에서는 단추와 해당 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-111">The following table describes the buttons and their functions.</span></span>  
  
|<span data-ttu-id="d2126-112">단추</span><span class="sxs-lookup"><span data-stu-id="d2126-112">Button</span></span>|<span data-ttu-id="d2126-113">Description</span><span class="sxs-lookup"><span data-stu-id="d2126-113">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d2126-114">**텍스트로 편집**</span><span class="sxs-lookup"><span data-stu-id="d2126-114">**Edit As Text**</span></span>|<span data-ttu-id="d2126-115">이 데이터 원본 유형에 대해서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-115">Disabled for this data source type.</span></span>|  
|<span data-ttu-id="d2126-116">**가져오기**</span><span class="sxs-lookup"><span data-stu-id="d2126-116">**Import**</span></span>|<span data-ttu-id="d2126-117">파일 시스템의 보고서 정의 파일(.rdl)에서 기존 쿼리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-117">Import an existing query from a report definition (.rdl) file on the file system.</span></span> <span data-ttu-id="d2126-118">자세한 내용은 [보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2126-118">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>|  
|<span data-ttu-id="d2126-119">![MDX 쿼리 뷰로 변경](../media/rsqdicon-commandtypemdx.gif "MDX 쿼리 뷰로 변경")</span><span class="sxs-lookup"><span data-stu-id="d2126-119">![Change to MDX query view](../media/rsqdicon-commandtypemdx.gif "Change to MDX query view")</span></span>|<span data-ttu-id="d2126-120">MDX 쿼리 디자이너 모드로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-120">Switch to the MDX query designer mode.</span></span>|  
|<span data-ttu-id="d2126-121">![DMX 쿼리 언어 뷰로 변경](../media/rsqdicon-commandtypedmx.gif "DMX 쿼리 언어 뷰로 변경")</span><span class="sxs-lookup"><span data-stu-id="d2126-121">![Change to DMX query language view](../media/rsqdicon-commandtypedmx.gif "Change to DMX query language view")</span></span>|<span data-ttu-id="d2126-122">DMX 쿼리 디자이너 모드로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-122">Switch to the DMX query designer mode.</span></span>|  
|<span data-ttu-id="d2126-123">![결과 데이터 새로 고침](../media/rsqdicon-refresh.gif "결과 데이터 새로 고침")</span><span class="sxs-lookup"><span data-stu-id="d2126-123">![Refresh result data](../media/rsqdicon-refresh.gif "Refresh result data")</span></span>|<span data-ttu-id="d2126-124">데이터 원본의 메타데이터를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-124">Refresh metadata from the data source.</span></span>|  
|<span data-ttu-id="d2126-125">![Delete](../media/rsqdicon-delete.gif "DELETE")</span><span class="sxs-lookup"><span data-stu-id="d2126-125">![Delete](../media/rsqdicon-delete.gif "Delete")</span></span>|<span data-ttu-id="d2126-126">데이터 창의 선택된 열을 쿼리에서 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-126">Delete the selected column in the Data pane from the query.</span></span>|  
|<span data-ttu-id="d2126-127">![쿼리 매개 변수 대화 상자 아이콘](../media/iconqueryparameter.gif "쿼리 매개 변수 대화 상자 아이콘")</span><span class="sxs-lookup"><span data-stu-id="d2126-127">![Icon for the Query Parameters dialog box](../media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")</span></span>|<span data-ttu-id="d2126-128">**쿼리 매개 변수** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-128">Display the **Query Parameters** dialog box.</span></span> <span data-ttu-id="d2126-129">기본값을 변수에 할당할 경우 보고서 디자이너에서 레이아웃 뷰로 전환할 때 해당 보고서 매개 변수가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-129">When you assign a default value to a variable, a corresponding report parameter is created when you switch to the Layout view in Report Designer.</span></span>|  
|<span data-ttu-id="d2126-130">![쿼리 실행](../media/rsqdicon-run.gif "쿼리 실행")</span><span class="sxs-lookup"><span data-stu-id="d2126-130">![Run the query](../media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="d2126-131">쿼리를 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-131">Prepare the query.</span></span>|  
|<span data-ttu-id="d2126-132">![디자인 모드로 전환](../media/rsqdicon-designmode.gif "디자인 모드로 전환")</span><span class="sxs-lookup"><span data-stu-id="d2126-132">![Switch to Design mode](../media/rsqdicon-designmode.gif "Switch to Design mode")</span></span>|<span data-ttu-id="d2126-133">디자인 모드와 쿼리 모드 사이를 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-133">Toggle between Design mode and Query mode.</span></span> <span data-ttu-id="d2126-134">결과 뷰로 변경하려면 디자인 창을 마우스 오른쪽 단추로 클릭하고 **결과**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-134">To change to result view, right-click on the Design pane and choose **Result**.</span></span>|  
  
## <a name="graphical-dmx-query-designer-in-design-mode"></a><span data-ttu-id="d2126-135">디자인 모드의 그래픽 DMX 쿼리 디자이너</span><span class="sxs-lookup"><span data-stu-id="d2126-135">Graphical DMX Query Designer in Design Mode</span></span>  
 <span data-ttu-id="d2126-136">올바른 큐브는 없지만 올바른 마이닝 모델이 있는 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 데이터 원본을 사용하는 데이터 세트를 편집하는 경우 그래픽 쿼리 디자이너가 디자인 모드에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-136">When you edit a dataset that uses an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source that has no valid cubes but that does have valid mining models, the graphical query designer opens in Design mode.</span></span> <span data-ttu-id="d2126-137">다음 그림에서는 디자인 모드에서 표시되는 창을 해당 레이블과 함께 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-137">The following figure labels the panes for Design mode.</span></span>  
  
 <span data-ttu-id="d2126-138">![Analysis Services DMX 쿼리 디자이너, 디자인 뷰](../media/rsqd-dsawas-dmx-designmode.gif "Analysis Services DMX 쿼리 디자이너, 디자인 뷰")</span><span class="sxs-lookup"><span data-stu-id="d2126-138">![Analysis Services DMX query designer, design view](../media/rsqd-dsawas-dmx-designmode.gif "Analysis Services DMX query designer, design view")</span></span>  
  
 <span data-ttu-id="d2126-139">다음 표에서는 각 창의 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-139">The following table describes the function of each pane.</span></span>  
  
|<span data-ttu-id="d2126-140">창</span><span class="sxs-lookup"><span data-stu-id="d2126-140">Pane</span></span>|<span data-ttu-id="d2126-141">함수</span><span class="sxs-lookup"><span data-stu-id="d2126-141">Function</span></span>|  
|----------|--------------|  
|<span data-ttu-id="d2126-142">쿼리 디자인 창</span><span class="sxs-lookup"><span data-stu-id="d2126-142">Query Design pane</span></span>|<span data-ttu-id="d2126-143">**마이닝 모델** 및 **입력 테이블 선택** 대화 상자를 사용하여 DMX 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-143">Use the **Mining Model** and **Select Input Table** dialog boxes to build the DMX query.</span></span>|  
|<span data-ttu-id="d2126-144">표 형태 창</span><span class="sxs-lookup"><span data-stu-id="d2126-144">Grid pane</span></span>|<span data-ttu-id="d2126-145">표의 각 행에 대해 **원본** 드롭다운 목록을 사용하여 함수나 식을 선택하고 DMX 쿼리에서 사용할 필드, 그룹 및 조건이나 인수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-145">For each row in the grid, use the **Source** drop-down list to select a function or expression, and choose fields, groups, and criteria or arguments to use in your DMX query.</span></span> <span data-ttu-id="d2126-146">선택 항목에 따라 생성되는 DMX 쿼리 텍스트를 보려면 도구 모음에서 **디자인 모드** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-146">To see the DMX query text generated by your selections, click the **Design Mode** button on the toolbar.</span></span>|  
  
 <span data-ttu-id="d2126-147">DMX 쿼리를 실행하고 결과 창에 결과를 표시하려면 쿼리 디자인 창을 마우스 오른쪽 단추로 클릭하고 **결과**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-147">To run the DMX query and show results in the Result pane, right-click on the Query Design pane and select **Result**.</span></span>  
  
## <a name="graphical-dmx-query-designer-in-query-mode"></a><span data-ttu-id="d2126-148">쿼리 모드의 그래픽 DMX 쿼리 디자이너</span><span class="sxs-lookup"><span data-stu-id="d2126-148">Graphical DMX Query Designer in Query Mode</span></span>  
 <span data-ttu-id="d2126-149">그래픽 쿼리 디자이너를 쿼리 모드로 변경하려면 도구 모음에서 **디자인 모드** 단추를 클릭하거나 쿼리 디자인 화면을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **쿼리** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-149">To change the graphical query designer to Query mode, click the **Design Mode** button on the toolbar or right-click on the query design surface, and choose **Query** from the shortcut menu.</span></span> <span data-ttu-id="d2126-150">이 모드를 사용하여 DMX 텍스트를 쿼리 창에 직접 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-150">Use this mode to enter DMX text directly into the Query pane.</span></span>  
  
 <span data-ttu-id="d2126-151">다음 그림에서는 레이블과 함께 쿼리 모드에 표시되는 창을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-151">The following figure labels the panes for Query mode.</span></span>  
  
 <span data-ttu-id="d2126-152">![Analysis Services DMX 쿼리 디자이너, 쿼리 뷰](../media/rsqd-dsawas-dmx-querymode.gif "Analysis Services DMX 쿼리 디자이너, 쿼리 뷰")</span><span class="sxs-lookup"><span data-stu-id="d2126-152">![Analysis Services DMX query designer, query view](../media/rsqd-dsawas-dmx-querymode.gif "Analysis Services DMX query designer, query view")</span></span>  
  
 <span data-ttu-id="d2126-153">다음 표에서는 각 창의 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-153">The following table describes the function of each pane.</span></span>  
  
|<span data-ttu-id="d2126-154">창</span><span class="sxs-lookup"><span data-stu-id="d2126-154">Pane</span></span>|<span data-ttu-id="d2126-155">함수</span><span class="sxs-lookup"><span data-stu-id="d2126-155">Function</span></span>|  
|----------|--------------|  
|<span data-ttu-id="d2126-156">쿼리 디자인 창</span><span class="sxs-lookup"><span data-stu-id="d2126-156">Query Design pane</span></span>|<span data-ttu-id="d2126-157">**마이닝 모델** 및 **입력 테이블 선택** 대화 상자를 사용하여 DMX 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-157">Use the **Mining Model** and **Select Input Table** dialog boxes to build the DMX query.</span></span>|  
|<span data-ttu-id="d2126-158">쿼리 창</span><span class="sxs-lookup"><span data-stu-id="d2126-158">Query pane</span></span>|<span data-ttu-id="d2126-159">이 창에서 DMX 쿼리 텍스트를 보고 직접 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-159">View or edit DMX query text directly in the pane.</span></span> <span data-ttu-id="d2126-160">**디자인** 모드로 다시 전환하면 DMX 쿼리 텍스트의 변경 내용이 지속되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-160">Changes to the DMX query text do not persist if you change back to **Design** mode.</span></span>|  
  
 <span data-ttu-id="d2126-161">DMX 쿼리를 실행하고 결과 창에 결과를 표시하려면 쿼리 디자인 창을 마우스 오른쪽 단추로 클릭하고 **결과**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-161">To run the DMX query and show results in the Result pane, right-click on the Query Design pane and select **Result**.</span></span>  
  
## <a name="graphical-dmx-query-designer-in-result-mode"></a><span data-ttu-id="d2126-162">결과 모드의 그래픽 DMX 쿼리 디자이너</span><span class="sxs-lookup"><span data-stu-id="d2126-162">Graphical DMX Query Designer in Result Mode</span></span>  
 <span data-ttu-id="d2126-163">결과 모드를 표시하려면 쿼리 디자인 화면을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **결과** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-163">To display the Result mode, right-click the query design surface and choose **Result** from the shortcut menu.</span></span> <span data-ttu-id="d2126-164">결과 모드로 전환하면 DMX 쿼리가 자동으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-164">When you switch to Result mode, the DMX query runs automatically.</span></span>  
  
 <span data-ttu-id="d2126-165">다음 그림에서는 결과 모드의 쿼리 디자이너를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-165">The following figure shows the query designer in Result mode.</span></span>  
  
 <span data-ttu-id="d2126-166">![Analysis Services DMX 쿼리 디자이너, 결과 뷰](../media/rsqd-dsawas-dmx-resultmode.gif "Analysis Services DMX 쿼리 디자이너, 결과 뷰")</span><span class="sxs-lookup"><span data-stu-id="d2126-166">![Analysis Services DMX query designer, result view](../media/rsqd-dsawas-dmx-resultmode.gif "Analysis Services DMX query designer, result view")</span></span>  
  
 <span data-ttu-id="d2126-167">디자인 모드나 쿼리 모드로 다시 전환하려면 결과 창을 마우스 오른쪽 단추로 클릭하고 **디자인** 또는 **쿼리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2126-167">To switch back to Design mode or Query mode, right-click on the Result pane and select **Design** or **Query**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2126-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d2126-168">See Also</span></span>  
 <span data-ttu-id="d2126-169">[Analysis Services용 MDX 쿼리 디자이너에서 매개 변수 정의&#40;보고서 작성기 및 SSRS&#41;](define-parameters-in-the-mdx-query-designer-for-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="d2126-169">[Define Parameters in the MDX Query Designer for Analysis Services &#40;Report Builder and SSRS&#41;](define-parameters-in-the-mdx-query-designer-for-analysis-services.md) </span></span>  
 <span data-ttu-id="d2126-170">[공유 데이터 세트 또는 포함된 데이터 세트 만들기&#40;보고서 작성기 및 SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d2126-170">[Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d2126-171">[DMX용 Analysis Services 연결 형식&#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d2126-171">[Analysis Services Connection Type for DMX &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md) </span></span>  
 <span data-ttu-id="d2126-172">[데이터 마이닝 모델에서 데이터 검색&#40;DMX&#41;&#40;SSRS&#41;](retrieve-data-from-a-data-mining-model-dmx-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d2126-172">[Retrieve Data from a Data Mining Model &#40;DMX&#41; &#40;SSRS&#41;](retrieve-data-from-a-data-mining-model-dmx-ssrs.md) </span></span>  
 <span data-ttu-id="d2126-173">[RSReportDesigner 구성 파일](../report-server/rsreportdesigner-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="d2126-173">[RSReportDesigner Configuration File](../report-server/rsreportdesigner-configuration-file.md) </span></span>  
 <span data-ttu-id="d2126-174">[MDX용 Analysis Services 연결 형식&#40;SSRS&#41;](analysis-services-connection-type-for-mdx-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d2126-174">[Analysis Services Connection Type for MDX &#40;SSRS&#41;](analysis-services-connection-type-for-mdx-ssrs.md) </span></span>  
 [<span data-ttu-id="d2126-175">DMX용 Analysis Services 연결 형식&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d2126-175">Analysis Services Connection Type for DMX &#40;SSRS&#41;</span></span>](analysis-services-connection-type-for-dmx-ssrs.md)  
  
  
