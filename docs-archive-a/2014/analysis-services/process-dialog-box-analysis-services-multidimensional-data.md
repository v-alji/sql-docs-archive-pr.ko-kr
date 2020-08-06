---
title: 처리 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.processdialog.f1
ms.assetid: c065248c-9001-4f0c-928f-9c59eccb618b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 369c121713894bba9b2ce6c40aa2869de49eaa72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741360"
---
# <a name="process-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="82d76-102">처리 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="82d76-102">Process Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="82d76-103">**및** 의 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 처리 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 대화 상자를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-103">Use the **Process** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to process [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects.</span></span> <span data-ttu-id="82d76-104">다음과 같은 방법으로 **에서** 처리 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-104">You can display the **Process** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] by:</span></span>  
  
-   <span data-ttu-id="82d76-105">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 솔루션 탐색기 **에서** 프로젝트, 큐브, 차원 또는 마이닝 구조를 마우스 오른쪽 단추로 클릭한 다음 **처리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-105">Right-clicking an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, cube, dimension, or mining structure in **Solution Explorer** and selecting **Process**.</span></span>  
  
-   <span data-ttu-id="82d76-106">모든 **큐브 디자이너** 페이지, 모든 **차원 디자이너**페이지 또는 **데이터 마이닝 모델 디자이너**의 **마이닝 구조** 및 **마이닝 모델** 페이지의 도구 모음에서 **처리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-106">Selecting **Process** from the toolbar on every page of **Cube Designer**, every page of **Dimension Designer**, or the **Mining Structure** and **Mining Models** pages of **Data Mining Model Designer**.</span></span>  
  
-   <span data-ttu-id="82d76-107">**데이터 마이닝 모델 디자이너** 의 **마이닝 모델** 페이지에서 마이닝 모델을 마우스 오른쪽 단추로 클릭한 다음 **마이닝 구조 및 모든 모델 처리** 또는 **모델 처리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-107">Right-clicking a mining model in the **Mining Models** page of **Data Mining Model Designer** and selecting **Process Mining Structure and All Models** or **Process Model**.</span></span>  
  
 <span data-ttu-id="82d76-108">다음과 같은 방법으로 **SQL Server Management Studio** 에서 **처리** 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-108">You can display the **Process** dialog box in **SQL Server Management Studio** by:</span></span>  
  
-   <span data-ttu-id="82d76-109">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체 탐색기 **에서** 데이터베이스, 큐브, 측정값 그룹, 파티션, 차원, 마이닝 구조 또는 마이닝 모델을 마우스 오른쪽 단추로 클릭한 다음 **처리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-109">Right-clicking an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, cube, measure group, partition, dimension, mining structure, or mining model in **Object Explorer** and selecting **Process**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="82d76-110">옵션</span><span class="sxs-lookup"><span data-stu-id="82d76-110">Options</span></span>  
 <span data-ttu-id="82d76-111">**개체 목록**</span><span class="sxs-lookup"><span data-stu-id="82d76-111">**Object list**</span></span>  
 <span data-ttu-id="82d76-112">처리할 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체와 적용할 처리 옵션 및 설정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-112">Select the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects to be processed and the processing options and settings to be applied.</span></span> <span data-ttu-id="82d76-113">표에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-113">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="82d76-114">**개체 이름**</span><span class="sxs-lookup"><span data-stu-id="82d76-114">**Object Name**</span></span>  
 <span data-ttu-id="82d76-115">처리할 개체의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-115">Displays the name of the object to be processed.</span></span> <span data-ttu-id="82d76-116">이름 왼쪽에 있는 아이콘은 개체 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-116">The icon to the left of the name indicates the object type.</span></span>  
  
 <span data-ttu-id="82d76-117">**형식**</span><span class="sxs-lookup"><span data-stu-id="82d76-117">**Type**</span></span>  
 <span data-ttu-id="82d76-118">처리할 개체 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-118">Displays the type of the object to be processed.</span></span>  
  
 <span data-ttu-id="82d76-119">**처리 옵션**</span><span class="sxs-lookup"><span data-stu-id="82d76-119">**Process Options**</span></span>  
 <span data-ttu-id="82d76-120">선택한 개체에 대해 수행할 처리 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-120">Select the type of processing to perform on the selected object.</span></span> <span data-ttu-id="82d76-121">사용 가능한 처리 옵션에 대 한 자세한 내용은 [다차원 모델 개체 처리](multidimensional-models/processing-a-multidimensional-model-analysis-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="82d76-121">For more information about available processing options, see [Multidimensional Model Object Processing](multidimensional-models/processing-a-multidimensional-model-analysis-services.md).</span></span>  
  
 <span data-ttu-id="82d76-122">**설정**</span><span class="sxs-lookup"><span data-stu-id="82d76-122">**Settings**</span></span>  
 <span data-ttu-id="82d76-123">큐브, 측정값 그룹 또는 파티션에 대한 **처리 옵션** 에서 **증분 처리** 를 선택한 경우 **구성** 하이퍼링크가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-123">Displays the **Configure** hyperlink when you choose **Process Incremental** in **Process Options** for cubes, measure groups, or partitions.</span></span> <span data-ttu-id="82d76-124">**구성** 을 클릭하여 **증분 업데이트** 대화 상자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-124">Click **Configure** to launch the **Incremental Update** dialog box.</span></span> <span data-ttu-id="82d76-125">**증분 업데이트** 대화 상자에 대한 자세한 내용은 [증분 업데이트 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](incremental-update-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82d76-125">For more information about the **Incremental Update** dialog box, see [Incremental Update Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](incremental-update-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="82d76-126">**제거**</span><span class="sxs-lookup"><span data-stu-id="82d76-126">**Remove**</span></span>  
 <span data-ttu-id="82d76-127">**개체 목록**에서 선택한 항목을 제거하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-127">Click to remove the selected items from **Object list**.</span></span>  
  
 <span data-ttu-id="82d76-128">**영향 분석**</span><span class="sxs-lookup"><span data-stu-id="82d76-128">**Impact Analysis**</span></span>  
 <span data-ttu-id="82d76-129">**영향 분석** 대화 상자를 열고 처리 태스크의 영향을 받게 될 개체를 표시하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-129">Click to open the **Impact Analysis** dialog box and display the objects that will be affected by the processing task.</span></span> <span data-ttu-id="82d76-130">**영향 분석** 대화 상자에 대한 자세한 내용은 [영향 분석 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](impact-analysis-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82d76-130">For more information about the **Impact Analysis** dialog box, see [Impact Analysis Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](impact-analysis-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82d76-131"> 이 옵션은 **설정 변경** 대화 상자에서 **영향을 받는 개체 처리** 옵션을 선택한 경우 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-131">This option is disabled when the **Process affected objects** option is selected in the **Change Settings** dialog box.</span></span>  
  
 <span data-ttu-id="82d76-132">**설정 변경**</span><span class="sxs-lookup"><span data-stu-id="82d76-132">**Change Settings**</span></span>  
 <span data-ttu-id="82d76-133">**설정 변경** 대화 상자를 열고 일괄 처리 설정, 쓰기 저장 설정 및 차원 키 오류 설정을 포함하여 선택한 개체의 처리를 제어하는 설정을 변경하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-133">Click to open the **Change Settings** dialog box and change the settings that govern processing of the selected objects, including batch processing settings, writeback settings, and dimension key error settings.</span></span> <span data-ttu-id="82d76-134">**설정 변경** 대화 상자에 대한 자세한 내용은 [설정 변경 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](change-settings-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82d76-134">For more information about the **Change Settings** dialog box, see [Change Settings Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](change-settings-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="82d76-135">**Run**</span><span class="sxs-lookup"><span data-stu-id="82d76-135">**Run**</span></span>  
 <span data-ttu-id="82d76-136">개체를 처리하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82d76-136">Click to process the objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82d76-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82d76-137">See Also</span></span>  
 <span data-ttu-id="82d76-138">[Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="82d76-138">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="82d76-139">처리 진행률 대화 상자 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="82d76-139">Process Progress Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](process-progress-dialog-box-analysis-services-multidimensional-data.md)  
  
  
