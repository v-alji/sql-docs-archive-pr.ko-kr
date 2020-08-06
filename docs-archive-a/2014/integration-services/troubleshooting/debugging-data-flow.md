---
title: 데이터 흐름 디버깅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- progress reporting [Integration Services]
- data viewers [Integration Services]
- data flow [Integration Services], debugging
- debugging [Integration Services], data flow
- counting rows
ms.assetid: 1c574f1b-54f7-4c05-8e42-8620e2c1df0f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ed1d1b7ebb119d452ca3de92fdad47552d1cc36c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734271"
---
# <a name="debugging-data-flow"></a><span data-ttu-id="781eb-102">데이터 흐름 디버깅</span><span class="sxs-lookup"><span data-stu-id="781eb-102">Debugging Data Flow</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="781eb-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 및 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지에서 데이터 흐름 문제를 해결하는 데 사용할 수 있는 기능과 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] and the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer include features and tools that you can use to troubleshoot the data flows in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>  
  
-   [!INCLUDE[ssIS](../../includes/ssis-md.md)] <span data-ttu-id="781eb-104">디자이너는 데이터 뷰어를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-104">Designer provides data viewers.</span></span>  
  
-   [!INCLUDE[ssIS](../../includes/ssis-md.md)] <span data-ttu-id="781eb-105">디자이너와 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 변환은 행 개수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-105">Designer and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] transformations provide row counts.</span></span>  
  
-   [!INCLUDE[ssIS](../../includes/ssis-md.md)] <span data-ttu-id="781eb-106">디자이너는 런타임에 진행률을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-106">Designer provides progress reporting at run time.</span></span>  
  
## <a name="data-viewers"></a><span data-ttu-id="781eb-107">데이터 뷰어</span><span class="sxs-lookup"><span data-stu-id="781eb-107">Data Viewers</span></span>  
 <span data-ttu-id="781eb-108">데이터 뷰어는 두 구성 요소 간 데이터를 데이터 흐름으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-108">Data viewers display data between two components in a data flow.</span></span> <span data-ttu-id="781eb-109">데이터 뷰어는 데이터 원본에서 데이터가 추출되어 처음으로 데이터 흐름에 들어갈 때, 변환으로 데이터가 업데이트되기 전/후와 데이터가 해당 대상으로 로드되기 전에 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-109">Data viewers can display data when the data is extracted from a data source and first enters a data flow, before and after a transformation updates the data, and before the data is loaded into its destination.</span></span>  
  
 <span data-ttu-id="781eb-110">데이터를 보려면 두 데이터 흐름 구성 요소를 연결하는 경로에 데이터 뷰어를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-110">To view the data, you attach data viewers to the path that connects two data flow components.</span></span> <span data-ttu-id="781eb-111">데이터 흐름 구성 요소 간의 데이터를 확인하면 예기치 않은 데이터 값을 확인하고, 변환으로 열 값이 변경되는 방식을 확인하고, 변환이 실패하는 이유를 확인하는 등의 작업을 더 쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-111">The ability to view data between data flow components makes it easier to identify unexpected data values, view the way a transformation changes column values, and discover the reason that a transformation fails.</span></span> <span data-ttu-id="781eb-112">예를 들어 참조 테이블에서 실패한 조회를 확인하고 이를 수정하기 위해 빈 열에 대해 기본 데이터를 제공하는 변환을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-112">For example, you may find that a lookup in a reference table fails, and to correct this you may want to add a transformation that provides default data for blank columns.</span></span>  
  
 <span data-ttu-id="781eb-113">데이터 뷰어는 표에 데이터를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-113">A data viewer can display data in a grid.</span></span> <span data-ttu-id="781eb-114">표를 사용하면 표시할 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-114">Using a grid, you select the columns to display.</span></span> <span data-ttu-id="781eb-115">선택한 열의 값은 표 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-115">The values for the selected columns display in a tabular format.</span></span>  
  
 <span data-ttu-id="781eb-116">또한 경로에 여러 데이터 뷰어를 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-116">You can also include multiple data viewers on a path.</span></span> <span data-ttu-id="781eb-117">동일 데이터를 여러 형식으로 표시하거나(예: 데이터의 차트 뷰 및 표 뷰 만들기) 데이터의 여러 열에 대해 서로 다른 데이터 뷰어를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-117">You can display the same data in different formats-for example, create a chart view and a grid view of the data-or create different data viewers for different columns of data.</span></span>  
  
 <span data-ttu-id="781eb-118">데이터 뷰어를 경로에 추가하면 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너는 **데이터 흐름** 탭의 디자인 화면에서 경로 옆에 데이터 뷰어 아이콘을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-118">When you add a data viewer to a path, [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer adds a data viewer icon to the design surface of the **Data Flow** tab, next to the path.</span></span> <span data-ttu-id="781eb-119">조건부 분할 변환과 같이 여러 출력을 포함할 수 있는 변환에는 각 경로에 데이터 뷰어가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-119">Transformations that can have multiple outputs, such as the Conditional Split transformation, can include a data viewer on each path.</span></span>  
  
 <span data-ttu-id="781eb-120">런타임에 **데이터 뷰어** 창이 열리고 데이터 뷰어 형식으로 지정된 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-120">At run time, a **Data Viewer** window opens and displays the information specified by the data viewer format.</span></span> <span data-ttu-id="781eb-121">예를 들어 표 형식을 사용하는 데이터 뷰어는 선택된 열, 데이터 흐름 구성 요소로 전달된 출력 행의 수 및 표시된 행의 수에 대한 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-121">For example, a data viewer that uses the grid format shows data for the selected columns, the number of output rows passed to the data flow component, and the number of rows displayed.</span></span> <span data-ttu-id="781eb-122">이 정보는 버퍼별로 표시되며 버퍼에 포함되는 행의 수는 데이터 흐름에서 행의 폭에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-122">The information displays buffer by buffer and, depending on the width of the rows in the data flow, a buffer may contain more or fewer rows.</span></span>  
  
 <span data-ttu-id="781eb-123">**데이터 뷰어** 대화 상자에서 데이터를 클립보드로 복사하고, 테이블에서 모든 데이터를 삭제하고, 데이터 뷰어를 다시 구성하고, 데이터 흐름을 재개하고, 데이터 뷰어를 연결하거나 연결을 끊을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-123">In the **Data Viewer** dialog box, you can copy the data to the Clipboard, clear all data from the table, reconfigure the data viewer, resume the flow of data, and detach or attach the data viewer.</span></span>  
  
#### <a name="to-add-a-data-viewer"></a><span data-ttu-id="781eb-124">데이터 뷰어를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="781eb-124">To add a data viewer</span></span>  
  
-   [<span data-ttu-id="781eb-125">데이터 흐름에 데이터 뷰어 추가</span><span class="sxs-lookup"><span data-stu-id="781eb-125">Add a Data Viewer to a Data Flow</span></span>](../add-a-data-viewer-to-a-data-flow.md)  
  
## <a name="row-counts"></a><span data-ttu-id="781eb-126">행 개수</span><span class="sxs-lookup"><span data-stu-id="781eb-126">Row Counts</span></span>  
 <span data-ttu-id="781eb-127">경로를 통해 전달된 행 개수가 **디자이너의** 데이터 흐름 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 탭의 디자인 화면에서 경로 옆에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-127">The number of rows that have passed through a path is displayed on the design surface of the **Data Flow** tab in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer next to the path.</span></span> <span data-ttu-id="781eb-128">데이터가 경로를 통해 이동하는 동안 개수가 주기적으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-128">The number is updated periodically while the data moves through the path.</span></span>  
  
 <span data-ttu-id="781eb-129">또한 행 개수 변환을 데이터 흐름에 추가하여 변수에서 마지막 행 개수를 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-129">You can also add a Row Count transformation to the data flow to capture the final row count in a variable.</span></span> <span data-ttu-id="781eb-130">자세한 내용은 [Row Count Transformation](../data-flow/transformations/row-count-transformation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="781eb-130">For more information, see [Row Count Transformation](../data-flow/transformations/row-count-transformation.md).</span></span>  
  
## <a name="progress-reporting"></a><span data-ttu-id="781eb-131">진행률 보고</span><span class="sxs-lookup"><span data-stu-id="781eb-131">Progress Reporting</span></span>  
 <span data-ttu-id="781eb-132">패키지를 실행할 때 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너는 상태를 나타내는 색으로 각 데이터 흐름 구성 요소를 표시하여 **데이터 흐름** 탭의 디자인 화면에 진행률을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-132">When you run a package, [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer depicts progress on the design surface of the **Data Flow** tab by displaying each data flow component in a color that indicates status.</span></span> <span data-ttu-id="781eb-133">각 구성 요소에서 해당 작업 수행을 시작하면 색이 노란색으로 바뀌고, 성공적으로 완료되면 녹색으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-133">When each component starts to perform its work, it changes from no color to yellow, and when it finishes successfully, it changes to green.</span></span> <span data-ttu-id="781eb-134">빨간색은 구성 요소가 실패했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-134">A red color indicates that the component failed.</span></span>  
  
 <span data-ttu-id="781eb-135">다음 표에서는 색 구분 기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-135">The following table describes the color-coding.</span></span>  
  
|<span data-ttu-id="781eb-136">색</span><span class="sxs-lookup"><span data-stu-id="781eb-136">Color</span></span>|<span data-ttu-id="781eb-137">Description</span><span class="sxs-lookup"><span data-stu-id="781eb-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="781eb-138">색 없음</span><span class="sxs-lookup"><span data-stu-id="781eb-138">No color</span></span>|<span data-ttu-id="781eb-139">데이터 흐름 엔진의 호출을 대기 중입니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-139">Waiting to be called by the data flow engine.</span></span>|  
|<span data-ttu-id="781eb-140">노란색</span><span class="sxs-lookup"><span data-stu-id="781eb-140">Yellow</span></span>|<span data-ttu-id="781eb-141">변환 수행, 데이터 추출 또는 데이터 로드 중입니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-141">Performing a transformation, extracting data, or loading data.</span></span>|  
|<span data-ttu-id="781eb-142">녹색</span><span class="sxs-lookup"><span data-stu-id="781eb-142">Green</span></span>|<span data-ttu-id="781eb-143">성공적으로 실행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-143">Ran successfully.</span></span>|  
|<span data-ttu-id="781eb-144">red</span><span class="sxs-lookup"><span data-stu-id="781eb-144">red</span></span>|<span data-ttu-id="781eb-145">실행 중 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="781eb-145">Ran with errors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="781eb-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="781eb-146">See Also</span></span>  
 [<span data-ttu-id="781eb-147">패키지 배포 문제 해결 도구</span><span class="sxs-lookup"><span data-stu-id="781eb-147">Troubleshooting Tools for Package Development</span></span>](troubleshooting-tools-for-package-development.md)  
  
  
