---
title: 보고서 매개 변수의 기본값 추가, 변경 또는 삭제 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10460"
- sql12.rtp.rptdesigner.reportparameters.defaultvalues.f1
- "10072"
ms.assetid: 6a87e069-b3a9-47b6-bcec-afcdd8aff65f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1d50fdbbe42a656ef839785c0968b36c8c829e11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650758"
---
# <a name="add-change-or-delete-default-values-for-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="bd130-102">보고서 매개 변수의 기본값 추가, 변경 또는 삭제(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="bd130-102">Add, Change, or Delete Default Values for a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="bd130-103">보고서 매개 변수를 만든 후에는 기본값 목록을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-103">After you create a report parameter, you can provide a list of default values.</span></span> <span data-ttu-id="bd130-104">모든 매개 변수에 유효한 기본값이 있는 경우 보고서를 처음으로 보거나 미리 볼 때 해당 보고서가 자동으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-104">If all parameters have a valid default value, the report runs automatically when you first view or preview it.</span></span>  
  
 <span data-ttu-id="bd130-105">보고서 매개 변수는 단일 값이나 여러 값을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-105">Report parameters can represent one value or multiple values.</span></span> <span data-ttu-id="bd130-106">단일 값의 경우 리터럴 또는 식을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-106">For single values, you can provide a literal or expression.</span></span> <span data-ttu-id="bd130-107">여러 값의 경우에는 정적 목록 또는 보고서 데이터 세트의 목록을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-107">For multiple values, you can provide a static list or a list from a report dataset.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="bd130-108">보고서를 게시한 후에는 보고서 서버에서 매개 변수 속성 값을 설정하여 보고서 제작 도구에서 보고서에 정의한 기본값을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-108">After you publish a report, you can override the default values that you define in the report in the report authoring tool, by setting parameter property values on the report server.</span></span> <span data-ttu-id="bd130-109">연결된 보고서를 만들어 여러 기본 매개 변수 값 집합을 제공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-109">You can also provide multiple sets of default parameter values by creating linked reports.</span></span> <span data-ttu-id="bd130-110">자세한 내용은  [보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](report-parameters-report-builder-and-report-designer.md)</span><span class="sxs-lookup"><span data-stu-id="bd130-110">For more information, see  [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md)</span></span>  
  
### <a name="to-add-or-change-the-default-values-for-a-report-parameter"></a><span data-ttu-id="bd130-111">보고서 매개 변수의 기본값을 추가 또는 변경하려면</span><span class="sxs-lookup"><span data-stu-id="bd130-111">To add or change the default values for a report parameter</span></span>  
  
1.  <span data-ttu-id="bd130-112">보고서 데이터 창에서 **매개 변수** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-112">In the Report Data pane, expand the **Parameters** node.</span></span> <span data-ttu-id="bd130-113">매개 변수를 마우스 오른쪽 단추로 클릭하고 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-113">Right-click the parameter and click **Edit**.</span></span> <span data-ttu-id="bd130-114">**보고서 매개 변수 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-114">The **Report Parameter Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bd130-115">보고서 데이터 창이 표시되지 않는 경우 **보기** , **보고서 데이터**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-115">If the Report Data pane is not visible, click **View** and then click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="bd130-116">**기본값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-116">Click **Default Values**.</span></span>  
  
3.  <span data-ttu-id="bd130-117">기본 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-117">Select a default option:</span></span>  
  
    -   <span data-ttu-id="bd130-118">값 또는 값 목록을 직접 제공하려면 **값 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-118">To manually provide a value or list of values, click **Specify values**.</span></span> <span data-ttu-id="bd130-119">**추가** 를 클릭한 다음 **값** 입력란에 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-119">Click **Add** and then enter the value in the **Value** text box.</span></span> <span data-ttu-id="bd130-120">값에 대한 식을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-120">You can write an expression for a value.</span></span> <span data-ttu-id="bd130-121">데이터 형식은 매개 변수의 데이터 형식과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-121">The data type must match the data type of the parameter.</span></span> <span data-ttu-id="bd130-122">필드 이름은 매개 변수의 식에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-122">Field names cannot be used in an expression for a parameter.</span></span>  
  
         <span data-ttu-id="bd130-123">다중값 매개 변수의 경우 제공할 값 개수만큼 이 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-123">For multivalue parameters, repeat this step for as many values as you want to provide.</span></span> <span data-ttu-id="bd130-124">이 목록에 표시되는 항목의 순서에 따라 드롭다운 목록에 표시되는 항목의 순서가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-124">The order of items you see in this list determines the order that the user sees them in the drop-down list.</span></span> <span data-ttu-id="bd130-125">목록에서 항목의 순서를 변경하려면 **값** 입력란을 클릭하여 항목을 선택한 다음 위쪽 및 아래쪽 화살표 단추를 사용하여 항목을 목록의 위 또는 아래로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-125">To change the order of an item in the list, click the **Value** text box to select the item, and then use the up and down arrow buttons to move the item higher or lower in the list.</span></span>  
  
    -   <span data-ttu-id="bd130-126">값을 검색하는 기존 데이터 세트의 이름을 제공하려면 **쿼리에서 값 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-126">To provide the name of an existing dataset that retrieves the values, click **Get values from a query**.</span></span> <span data-ttu-id="bd130-127">**데이터 세트**에서 데이터 세트의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-127">In **Dataset**, choose the name of the dataset.</span></span>  
  
         <span data-ttu-id="bd130-128">**값 필드**에서 매개 변수 값을 제공하는 필드의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-128">In **Value field**, choose the name of the field that provides parameter values.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-remove-the-default-values-for-a-report-parameter"></a><span data-ttu-id="bd130-129">보고서 매개 변수의 기본값을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="bd130-129">To remove the default values for a report parameter</span></span>  
  
1.  <span data-ttu-id="bd130-130">보고서 데이터 창에서 **매개 변수** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-130">In the Report Data pane, expand the **Parameters** node.</span></span> <span data-ttu-id="bd130-131">매개 변수를 마우스 오른쪽 단추로 클릭하고 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-131">Right-click the parameter and click **Edit**.</span></span> <span data-ttu-id="bd130-132">**보고서 매개 변수 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-132">The **Report Parameter Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="bd130-133">**기본값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-133">Click **Default Values**.</span></span>  
  
3.  <span data-ttu-id="bd130-134">**다음 옵션 중 하나 선택**에서 **기본값 없음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd130-134">In **Select from one of the following options**, click **No default value**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bd130-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bd130-135">See Also</span></span>  
 <span data-ttu-id="bd130-136">[보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="bd130-136">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="bd130-137">[보고서에 연계 매개 변수 추가&#40;보고서 작성기 및 SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bd130-137">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="bd130-138">[자습서: 보고서에 매개 변수 추가&#40;보고서 작성기&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="bd130-138">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="bd130-139">[데이터 세트 필터, 데이터 영역 필터 및 그룹 필터 추가&#40;보고서 작성기 및 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="bd130-139">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="bd130-140">[매개 변수 컬렉션 참조&#40;보고서 작성기 및 SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="bd130-140">[Parameters Collection References &#40;Report Builder and SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span></span>  
 <span data-ttu-id="bd130-141">[보고서 매개 변수의 순서 변경&#40;보고서 작성기 및 SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bd130-141">[Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="bd130-142">[보고서 매개 변수 추가, 변경 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bd130-142">[Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="bd130-143">식&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="bd130-143">Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)  
  
  
