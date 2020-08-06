---
title: 데이터 집합 속성 대화 상자, 필터 (보고서 작성기) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10025"
ms.assetid: 933a6f44-4eb7-4e73-9c40-ac0fd17b23d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7bc13b0eeff1eaf27fb0ec0c4279ff00d0809e4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647531"
---
# <a name="dataset-properties-dialog-box-filters-report-builder"></a><span data-ttu-id="e1b0b-102">데이터 세트 속성 대화 상자, 필터(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="e1b0b-102">Dataset Properties Dialog Box, Filters (Report Builder)</span></span>
  <span data-ttu-id="e1b0b-103">**데이터 세트 속성** 대화 상자에서 **필터**를 선택하여 데이터 세트에 대한 필터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-103">Select **Filters** on the **Dataset Properties** dialog box to create filters for the dataset.</span></span>  
  
 <span data-ttu-id="e1b0b-104">보고서 서버에 있는 공유 데이터 세트 정의의 일부인 필터는 공유 데이터 세트를 사용하는 모든 보고서에 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-104">Filters that are part of a shared dataset definition on the report server affect all reports that use the shared dataset.</span></span> <span data-ttu-id="e1b0b-105">공유 데이터 세트에 대한 추가 필터는 보고서에 추가된 후 지정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-105">Additional filters for the shared dataset can be specified after it is added to a report.</span></span> <span data-ttu-id="e1b0b-106">이러한 필터는 해당 필터가 정의된 보고서에만 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-106">These filters affect only the report in which they are defined.</span></span>  
  
 <span data-ttu-id="e1b0b-107">포함된 데이터 세트에 대한 필터는 해당 필터가 정의된 보고서에만 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-107">Filters for an embedded dataset affect only the report in which they are defined.</span></span>  
  
 <span data-ttu-id="e1b0b-108">자세한 내용은 [데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-108">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e1b0b-109">옵션</span><span class="sxs-lookup"><span data-stu-id="e1b0b-109">Options</span></span>  
 <span data-ttu-id="e1b0b-110">**추가**</span><span class="sxs-lookup"><span data-stu-id="e1b0b-110">**Add**</span></span>  
 <span data-ttu-id="e1b0b-111">새 필터 절을 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-111">Add a new filter clause to the list.</span></span>  
  
 <span data-ttu-id="e1b0b-112">**삭제**</span><span class="sxs-lookup"><span data-stu-id="e1b0b-112">**Delete**</span></span>  
 <span data-ttu-id="e1b0b-113">선택한 필터 절을 목록에서 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-113">Delete the selected filter clause from the list.</span></span>  
  
 <span data-ttu-id="e1b0b-114">**위쪽 화살표**</span><span class="sxs-lookup"><span data-stu-id="e1b0b-114">**Up arrow**</span></span>  
 <span data-ttu-id="e1b0b-115">선택한 필터를 목록에서 위로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-115">Move the selected filter up in the list.</span></span>  
  
 <span data-ttu-id="e1b0b-116">**아래쪽 화살표**</span><span class="sxs-lookup"><span data-stu-id="e1b0b-116">**Down arrow**</span></span>  
 <span data-ttu-id="e1b0b-117">선택한 필터를 목록에서 아래로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-117">Move the selected filter down in the list</span></span>  
  
 <span data-ttu-id="e1b0b-118">**식**</span><span class="sxs-lookup"><span data-stu-id="e1b0b-118">**Expression**</span></span>  
 <span data-ttu-id="e1b0b-119">필터를 적용할 식을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-119">Type or choose the expression to which you want to apply a filter.</span></span> <span data-ttu-id="e1b0b-120">식을 편집 하려면 식 단추 (**fx**)를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-120">Click the Expression (**fx**) button to edit the expression.</span></span>  
  
 <span data-ttu-id="e1b0b-121">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="e1b0b-121">**Data type**</span></span>  
 <span data-ttu-id="e1b0b-122">**값**에 대한 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-122">Choose the data type for **Value**.</span></span> <span data-ttu-id="e1b0b-123">가능하면 **식**에 대한 데이터 형식과 일치하는 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-123">When possible, choose a data type that matches the data type for **Expression**.</span></span>  
  
 <span data-ttu-id="e1b0b-124">**식** 및 **값** 의 값은 동일한 데이터 형식으로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-124">The values in **Expression** and **Value** must evaluate to the same data type.</span></span> <span data-ttu-id="e1b0b-125">예를 들어 **식** 을 데이터 형식이 System.Int32인 필드로 설정하고 **값** 을 7로 설정한 경우 드롭다운 목록에서 **정수**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-125">For example, if **Expression** is set to a field that has the data type System.Int32 and **Value** is set to 7, from the drop-down list, choose **Integer**.</span></span>  
  
 <span data-ttu-id="e1b0b-126">필요한 데이터 형식 옵션이 드롭다운 목록에 없으면 값을 올바른 데이터 형식으로 변환하는 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-126">If the data type option you need is not in the drop-down list, write an expression to convert the value to the correct data type.</span></span> <span data-ttu-id="e1b0b-127">자세한 내용은 [필터 수식 예&#40;보고서 작성기 및 SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-127">For more information, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="e1b0b-128">**연산자**</span><span class="sxs-lookup"><span data-stu-id="e1b0b-128">**Operator**</span></span>  
 <span data-ttu-id="e1b0b-129">식과 값을 비교하는 데 사용할 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-129">Choose the operator to use to compare the expression and the value.</span></span>  
  
 <span data-ttu-id="e1b0b-130">**값**</span><span class="sxs-lookup"><span data-stu-id="e1b0b-130">**Value**</span></span>  
 <span data-ttu-id="e1b0b-131">**식** 상자에 지정된 식을 계산할 때 사용할 값이나 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-131">Type the expression or value to use when evaluating the expression specified in the **Expression** box.</span></span> <span data-ttu-id="e1b0b-132">식을 편집 하려면 식 단추 (**fx**)를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b0b-132">Click the Expression (**fx**) button to edit the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1b0b-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e1b0b-133">See Also</span></span>  
 <span data-ttu-id="e1b0b-134">[보고서 포함 된 데이터 집합 및 공유 데이터 집합 &#40;보고서 작성기 및 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e1b0b-134">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e1b0b-135">[보고서 매개 변수 &#40;보고서 작성기 및 보고서 디자이너&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="e1b0b-135">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="e1b0b-136">[데이터 집합 &#40;보고서 작성기 및 SSRS에 필터를 추가&#41;](report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e1b0b-136">[Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;](report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e1b0b-137">보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e1b0b-137">Expression Uses in Reports &#40;Report Builder and SSRS&#41;</span></span>](report-design/expression-uses-in-reports-report-builder-and-ssrs.md)  
  
  
