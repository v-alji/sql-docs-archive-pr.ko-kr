---
title: 차원 속성 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.dimensionproperties.f1
helpviewer_keywords:
- Dimension Properties dialog box
ms.assetid: 7235d443-b2ce-4c53-b2eb-abceb28394bb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0523220c76c11280165bc825c5c00c5eb9e23be6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661405"
---
# <a name="dimension-properties-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="52577-102">차원 속성 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="52577-102">Dimension Properties Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="52577-103">**의** 차원 속성 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 대화 상자를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스의 차원 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52577-103">Use the **Dimension Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to set the properties of a dimension in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="52577-104">개체 탐색기에서 차원을 마우스 오른쪽 단추로 클릭하고 **속성** 을 선택하면 **차원 속성**대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="52577-104">You can display the **Dimension Properties** dialog box by right-clicking a dimension in Object Explorer and selecting **Properties**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="52577-105">옵션</span><span class="sxs-lookup"><span data-stu-id="52577-105">Options</span></span>  
  
|<span data-ttu-id="52577-106">용어</span><span class="sxs-lookup"><span data-stu-id="52577-106">Term</span></span>|<span data-ttu-id="52577-107">정의</span><span class="sxs-lookup"><span data-stu-id="52577-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="52577-108">**이름**</span><span class="sxs-lookup"><span data-stu-id="52577-108">**Name**</span></span>|<span data-ttu-id="52577-109">차원 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="52577-109">Displays the name of the dimension.</span></span>|  
|<span data-ttu-id="52577-110">**ID**</span><span class="sxs-lookup"><span data-stu-id="52577-110">**ID**</span></span>|<span data-ttu-id="52577-111">차원 식별자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="52577-111">Displays the identifier of the dimension.</span></span>|  
|<span data-ttu-id="52577-112">**설명**</span><span class="sxs-lookup"><span data-stu-id="52577-112">**Description**</span></span>|<span data-ttu-id="52577-113">차원에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="52577-113">Displays the description of the dimension.</span></span>|  
|<span data-ttu-id="52577-114">**생성된 타임스탬프**</span><span class="sxs-lookup"><span data-stu-id="52577-114">**Create Timestamp**</span></span>|<span data-ttu-id="52577-115">차원을 만든 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="52577-115">Displays the date and time the dimension was created.</span></span>|  
|<span data-ttu-id="52577-116">**최종 스키마 업데이트**</span><span class="sxs-lookup"><span data-stu-id="52577-116">**Last Schema Update**</span></span>|<span data-ttu-id="52577-117">차원에 대한 메타데이터를 마지막으로 업데이트한 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="52577-117">Displays the date and time the metadata for the dimension was last updated.</span></span>|  
|<span data-ttu-id="52577-118">**처리 모드**</span><span class="sxs-lookup"><span data-stu-id="52577-118">**Processing Mode**</span></span>|<span data-ttu-id="52577-119">차원에 사용할 처리 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52577-119">Select the processing mode to use for the dimension.</span></span> <span data-ttu-id="52577-120">이 속성 값에 대한 자세한 내용은 <xref:Microsoft.AnalysisServices.Dimension.ProcessingMode%2A>를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="52577-120">For more information about the values for this property, see <xref:Microsoft.AnalysisServices.Dimension.ProcessingMode%2A>.</span></span>|  
|<span data-ttu-id="52577-121">**State**</span><span class="sxs-lookup"><span data-stu-id="52577-121">**State**</span></span>|<span data-ttu-id="52577-122">차원의 처리 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="52577-122">Displays the processing state of the dimension.</span></span> <span data-ttu-id="52577-123">이 속성 값에 대한 자세한 내용은 <xref:Microsoft.AnalysisServices.ProcessableMajorObject.State%2A>를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="52577-123">For more information about the values for this property, see <xref:Microsoft.AnalysisServices.ProcessableMajorObject.State%2A>.</span></span>|  
|<span data-ttu-id="52577-124">**마지막 처리**</span><span class="sxs-lookup"><span data-stu-id="52577-124">**Last Processed**</span></span>|<span data-ttu-id="52577-125">차원을 마지막으로 처리한 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="52577-125">Displays the date and time the dimension was last processed.</span></span>|  
|<span data-ttu-id="52577-126">**현재 스토리지 모드**</span><span class="sxs-lookup"><span data-stu-id="52577-126">**Current Storage Mode**</span></span>|<span data-ttu-id="52577-127">차원의 현재 스토리지 모드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="52577-127">Displays the current storage mode for the dimension.</span></span> <span data-ttu-id="52577-128">이 속성 값에 대한 자세한 내용은 <xref:Microsoft.AnalysisServices.Dimension.CurrentStorageMode%2A>를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="52577-128">For more information about the values for this property, see <xref:Microsoft.AnalysisServices.Dimension.CurrentStorageMode%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52577-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52577-129">See Also</span></span>  
 <span data-ttu-id="52577-130">[Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="52577-130">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="52577-131">차원&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="52577-131">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
