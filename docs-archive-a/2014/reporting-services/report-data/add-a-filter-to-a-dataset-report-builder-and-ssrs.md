---
title: 데이터 세트에 필터 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eed37e74-6a43-4d7c-9959-2d5fa6a6aba9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f51411d31d8ee29bf0f163085077dcee8fd79bdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639351"
---
# <a name="add-a-filter-to-a-dataset-report-builder-and-ssrs"></a><span data-ttu-id="b0f79-102">데이터 세트에 필터 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="b0f79-102">Add a Filter to a Dataset (Report Builder and SSRS)</span></span>
  <span data-ttu-id="b0f79-103">데이터 세트에 필터를 추가하여 데이터를 외부 데이터 원본에서 검색한 후에 보고서의 데이터를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-103">Add a filter to a dataset to limit the data in a report after the data is retrieved from an external data source.</span></span> <span data-ttu-id="b0f79-104">필터를 데이터 세트에 추가하면 모든 보고서 파트 또는 데이터 영역은 필터 조건과 일치하는 데이터만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-104">When you add a filter to a dataset, all report parts or data regions use only data that matches the filter conditions.</span></span>  
  
 <span data-ttu-id="b0f79-105">공유 데이터 세트의 경우 모든 종속 항목에 적용되는 필터는 보고서 서버에 있는 공유 데이터 세트 정의의 일부여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-105">For a shared dataset, a filter that applies to all dependent items must be part of the shared dataset definition on the report server.</span></span> <span data-ttu-id="b0f79-106">공유 데이터 세트 인스턴스를 포함하는 보고서 또는 보고서 파트는 해당 인스턴스에만 적용되는 필터를 추가로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-106">A report or report part that contains an instance of a shared dataset can create an additional filter that applies only to the instance.</span></span>  
  
 <span data-ttu-id="b0f79-107">필터를 추가하려면 하나 이상의 조건(필터 수식)을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-107">To add a filter, you must specify one or more conditions that are filter equations.</span></span> <span data-ttu-id="b0f79-108">필터 수식은 필터링할 데이터를 식별하는 식, 연산자 및 비교할 값으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-108">A filter equation consists of an expression that identifies the data that you want to filter, an operator, and the value to compare to.</span></span> <span data-ttu-id="b0f79-109">필터링된 데이터와 값의 데이터 형식은 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-109">The data types of the filtered data and the value must match.</span></span> <span data-ttu-id="b0f79-110">데이터 세트에는 집계 값에 대한 필터링이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-110">Filtering on aggregate values for a dataset is not supported.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-filter-to-a-shared-dataset"></a><span data-ttu-id="b0f79-111">공유 데이터 세트에 필터를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="b0f79-111">To add a filter to a shared dataset</span></span>  
  
1.  <span data-ttu-id="b0f79-112">공유 데이터 세트 모드에서 공유 데이터 세트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-112">Open a shared dataset in shared dataset mode.</span></span>  
  
2.  <span data-ttu-id="b0f79-113">**홈** 탭의 **공유 데이터 세트** 그룹에서 데이터 세트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-113">On the **Home** tab, in the **Shared Datasets** group, click Datasets.</span></span> <span data-ttu-id="b0f79-114">**데이터 세트 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-114">The **Dataset Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="b0f79-115">**필터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-115">Click **Filters**.</span></span> <span data-ttu-id="b0f79-116">그러면 현재 필터 수식 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-116">This displays the current list of filter equations.</span></span> <span data-ttu-id="b0f79-117">기본적으로 이 목록은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-117">By default, the list is empty.</span></span>  
  
4.  <span data-ttu-id="b0f79-118">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-118">Click **Add**.</span></span> <span data-ttu-id="b0f79-119">새로운 빈 필터 수식이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-119">A new blank filter equation appears.</span></span>  
  
5.  <span data-ttu-id="b0f79-120">**식**에서 필터링할 필드에 대한 식을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-120">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="b0f79-121">식을 편집하려면 식(*fx*) 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-121">To edit the expression, click the expression (*fx*) button.</span></span>  
  
6.  <span data-ttu-id="b0f79-122">5단계에서 만든 식의 데이터 형식과 일치하는 데이터 형식을 목록 상자에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-122">From the list box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
7.  <span data-ttu-id="b0f79-123">**연산자** 상자에서 해당 필터로 **식** 상자와 **값** 상자의 값을 비교하는 데 사용할 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-123">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="b0f79-124">선택한 연산자에 따라 다음 단계에서 사용하는 값의 수가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-124">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
8.  <span data-ttu-id="b0f79-125">**값** 상자에 해당 필터로 **식**의 값을 계산하는 데 기준이 되는 식 또는 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-125">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="b0f79-126">필터 수식의 예는 [필터 수식 예&#40;보고서 작성기 및 SSRS&#41;](../report-design/filter-equation-examples-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b0f79-126">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](../report-design/filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-a-filter-to-an-embedded-dataset-or-a-shared-dataset-instance"></a><span data-ttu-id="b0f79-127">포함된 데이터 세트 또는 공유 데이터 세트 인스턴스에 필터를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="b0f79-127">To add a filter to an embedded dataset or a shared dataset instance</span></span>  
  
1.  <span data-ttu-id="b0f79-128">보고서 디자인 모드에서 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-128">Open a report in report design mode.</span></span>  
  
2.  <span data-ttu-id="b0f79-129">**보고서 데이터** 창에서 데이터 세트를 마우스 오른쪽 단추로 클릭한 다음, **데이터 세트 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-129">Right-click a dataset in the **Report Data** pane and then click **Dataset Properties**.</span></span> <span data-ttu-id="b0f79-130">**데이터 세트 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-130">The **Dataset Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="b0f79-131">**필터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-131">Click **Filters**.</span></span> <span data-ttu-id="b0f79-132">그러면 현재 필터 수식 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-132">This displays the current list of filter equations.</span></span> <span data-ttu-id="b0f79-133">기본적으로 이 목록은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-133">By default, the list is empty.</span></span>  
  
4.  <span data-ttu-id="b0f79-134">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-134">Click **Add**.</span></span> <span data-ttu-id="b0f79-135">새로운 빈 필터 수식이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-135">A new blank filter equation appears.</span></span>  
  
5.  <span data-ttu-id="b0f79-136">**식**에서 필터링할 필드에 대한 식을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-136">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="b0f79-137">식을 편집하려면 식(*fx*) 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-137">To edit the expression, click the expression (*fx*) button.</span></span>  
  
6.  <span data-ttu-id="b0f79-138">5단계에서 만든 식의 데이터 형식과 일치하는 데이터 형식을 드롭다운 상자에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-138">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
7.  <span data-ttu-id="b0f79-139">**연산자** 상자에서 해당 필터로 **식** 상자와 **값** 상자의 값을 비교하는 데 사용할 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-139">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="b0f79-140">선택한 연산자에 따라 다음 단계에서 사용하는 값의 수가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-140">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
8.  <span data-ttu-id="b0f79-141">**값** 상자에 해당 필터로 **식**의 값을 계산하는 데 기준이 되는 식 또는 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f79-141">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="b0f79-142">필터 수식의 예는 [필터 수식 예&#40;보고서 작성기 및 SSRS&#41;](../report-design/filter-equation-examples-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b0f79-142">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](../report-design/filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b0f79-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b0f79-143">See Also</span></span>  
 <span data-ttu-id="b0f79-144">[데이터 세트 필터, 데이터 영역 필터 및 그룹 필터 추가&#40;보고서 작성기 및 SSRS&#41;](../report-design/add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="b0f79-144">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](../report-design/add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="b0f79-145">[식 예&#40;보고서 작성기 및 SSRS&#41;](../report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b0f79-145">[Expression Examples &#40;Report Builder and SSRS&#41;](../report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b0f79-146">필터 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b0f79-146">Add a Filter &#40;Report Builder and SSRS&#41;</span></span>](../report-design/add-a-filter-report-builder-and-ssrs.md)  
  
  
