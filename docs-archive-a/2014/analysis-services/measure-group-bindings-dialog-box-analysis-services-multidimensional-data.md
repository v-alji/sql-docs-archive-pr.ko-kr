---
title: 측정값 그룹 바인딩 대화 상자 (다차원 데이터 Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.dimensionusage.definerelationship.measuregroupbindings.f1
helpviewer_keywords:
- Measure Group Bindings dialog box
ms.assetid: ed642780-5350-438e-af73-b9ceab3f876d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 78693901a5898b140d6efeed16b6f0eaa7577e69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741464"
---
# <a name="measure-group-bindings-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="f9284-102">측정값 그룹 바인딩 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="f9284-102">Measure Group Bindings Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="f9284-103">**관계 정의** 대화 상자에서 액세스할 수 있는 **측정값 그룹 바인딩** 대화 상자를 사용하여 큐브 차원의 모든 특성에 대해 Null 처리 옵션을 지정할 수 있을 뿐만 아니라 일반 차원 관계에 대해 큐브 차원의 비세분성 특성과 측정값 그룹 열 간의 직접 관계를 생성 및 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9284-103">Use the **Measure Group Bindings** dialog box to create and modify direct relationships between non-granularity attributes in a cube dimension and columns in a measure group for a regular dimension relationship, as well as to specify null processing options for any attribute in a cube dimension, from the **Define Relationship** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f9284-104">옵션</span><span class="sxs-lookup"><span data-stu-id="f9284-104">Options</span></span>  
 <span data-ttu-id="f9284-105">**측정값 그룹 테이블**</span><span class="sxs-lookup"><span data-stu-id="f9284-105">**Measure group table**</span></span>  
 <span data-ttu-id="f9284-106">선택한 측정값 그룹에 대한 팩트 테이블의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f9284-106">Displays the name of the fact table for the selected measure group.</span></span>  
  
 <span data-ttu-id="f9284-107">**특성**</span><span class="sxs-lookup"><span data-stu-id="f9284-107">**Attributes**</span></span>  
 <span data-ttu-id="f9284-108">특성 및 차원 테이블이 포함된 표를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f9284-108">Displays a grid of attributes and dimension tables.</span></span> <span data-ttu-id="f9284-109">만들 특성을 선택하거나 선택한 특성에 대해 **관계** 에서 속성을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9284-109">Select an attribute to create or modify properties in **Relationship** for the selected attribute.</span></span> <span data-ttu-id="f9284-110">표에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9284-110">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="f9284-111">옵션</span><span class="sxs-lookup"><span data-stu-id="f9284-111">Option</span></span>|<span data-ttu-id="f9284-112">정의</span><span class="sxs-lookup"><span data-stu-id="f9284-112">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="f9284-113">**특성 이름**</span><span class="sxs-lookup"><span data-stu-id="f9284-113">**Attribute Name**</span></span>|<span data-ttu-id="f9284-114">특성 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f9284-114">Displays the name of the attribute.</span></span>|  
|<span data-ttu-id="f9284-115">**차원 테이블**</span><span class="sxs-lookup"><span data-stu-id="f9284-115">**Dimension Table**</span></span>|<span data-ttu-id="f9284-116">특성이 기준으로 하는 차원 테이블의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f9284-116">Displays the name of the dimension table on which the attribute is based.</span></span>|  
  
 <span data-ttu-id="f9284-117">**관계**</span><span class="sxs-lookup"><span data-stu-id="f9284-117">**Relationship**</span></span>  
 <span data-ttu-id="f9284-118">선택한 특성에 대한 차원 테이블 열과 선택한 측정값 그룹에 대한 팩트 테이블 열 간의 관계와 이 관계에 대한 Null 처리 옵션을 나타내는 표를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f9284-118">Displays a grid of relationships between dimension table columns for the selected attribute and fact table columns for the selected measure group as well as the null processing option for the relationship.</span></span> <span data-ttu-id="f9284-119">표에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9284-119">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="f9284-120">옵션</span><span class="sxs-lookup"><span data-stu-id="f9284-120">Option</span></span>|<span data-ttu-id="f9284-121">정의</span><span class="sxs-lookup"><span data-stu-id="f9284-121">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="f9284-122">**차원 열**</span><span class="sxs-lookup"><span data-stu-id="f9284-122">**Dimension Columns**</span></span>|<span data-ttu-id="f9284-123">**특성** 에서 선택한 특성이 기준으로 하는 차원 테이블의 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f9284-123">Displays the columns from the dimension table on which the attribute selected in **Attributes** is based.</span></span>|  
|<span data-ttu-id="f9284-124">**측정값 그룹 열**</span><span class="sxs-lookup"><span data-stu-id="f9284-124">**Measure Group Columns**</span></span>|<span data-ttu-id="f9284-125">차원에서 상속한 측정값 그룹 관계를 사용하려면 **차원에서 상속** 을 선택하고 관계를 명시적으로 정의하려면 측정값 그룹이 기준으로 하는 팩트 테이블의 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f9284-125">Select either **Inherited from dimension** to use the measure group relationship inherited from the dimension, or select a column from the fact table on which the measure group is based to explicitly define a relationship.</span></span>|  
|<span data-ttu-id="f9284-126">**Null 처리**</span><span class="sxs-lookup"><span data-stu-id="f9284-126">**Null Processing**</span></span>|<span data-ttu-id="f9284-127">특성에 대한 Null 처리 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f9284-127">Select a null processing option for the attribute.</span></span> <span data-ttu-id="f9284-128">Null 처리 옵션에 대한 자세한 내용은 [NullProcessing 요소&#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/nullprocessing-element-assl)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9284-128">For more information about null processing options, see [NullProcessing Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/nullprocessing-element-assl).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9284-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f9284-129">See Also</span></span>  
 <span data-ttu-id="f9284-130">[Analysis Services 다차원 데이터를 &#40;관계 정의 대화 상자&#41;](define-relationship-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f9284-130">[Define Relationship Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](define-relationship-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="f9284-131">Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="f9284-131">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
