---
title: 보고서 매개 변수의 사용 가능한 값 추가, 변경 또는 삭제 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportparameters.availablevalues.f1
- "10455"
- "10071"
ms.assetid: 0e03264c-523f-4c59-b71b-ceef600f75f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 985ab3e8dc1d74f94e7242ff57f46ffe4fba9586
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650752"
---
# <a name="add-change-or-delete-available-values-for-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="149e5-102">보고서 매개 변수의 사용 가능한 값 추가, 변경 또는 삭제(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="149e5-102">Add, Change, or Delete Available Values for a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="149e5-103">보고서 매개 변수를 만든 다음에는 사용자에게 표시할 사용 가능한 값 목록을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-103">After you create a report parameter, you can specify a list of available values to display to the user.</span></span> <span data-ttu-id="149e5-104">사용 가능한 값 목록은 사용자가 매개 변수에 적합한 값만 선택할 수 있도록 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-104">An available values list limits the choices a user can make to only valid values for the parameter.</span></span>  
  
 <span data-ttu-id="149e5-105">사용 가능한 값은 보고서를 실행할 때 도구 모음의 보고서 매개 변수 옆에 있는 드롭다운 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-105">Available values appear in a drop-down list next to the report parameter on the toolbar when the report runs.</span></span> <span data-ttu-id="149e5-106">보고서 매개 변수는 단일 값이나 여러 값을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-106">Report parameters can represent one value or multiple values.</span></span> <span data-ttu-id="149e5-107">여러 값의 경우 목록 맨 위가 **모두 선택** 기능으로 시작되어 사용자가 클릭 한 번으로 모든 값을 선택하거나 선택 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-107">For multiple values, the top of list begins with a **Select All** feature so the user can select or clear all values with a single click.</span></span>  
  
 <span data-ttu-id="149e5-108">정적 값 목록 또는 보고서 데이터 세트에서 가져온 목록을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-108">You can provide a static list of values or a list from a report dataset.</span></span> <span data-ttu-id="149e5-109">필요에 따라 레이블 필드를 지정하여 값에 대한 이름을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-109">You can optionally provide a friendly name for values by specifying a label field.</span></span> <span data-ttu-id="149e5-110">예를 들어 `ProductID` 필드를 기반으로 하는 매개 변수의 경우 매개 변수 레이블에 `ProductName` 필드를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-110">For example, for a parameter based on a `ProductID` field, you can display the `ProductName` field in the parameter label.</span></span> <span data-ttu-id="149e5-111">보고서를 실행할 때 사용자는 제품 이름에서 선택할 수 있지만 실제 선택된 값은 해당 `ProductID`입니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-111">When the report runs, the user can choose from the product names, but the actual chosen value is the corresponding `ProductID`.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="149e5-112">보고서를 게시한 후에는 보고서 서버에서 매개 변수 속성 값을 설정하여 보고서 제작 도구에서 보고서에 정의한 사용 가능한 값을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-112">After you publish a report, you can override the available values that you define in the report in the report authoring tool, by setting parameter property values on the report server.</span></span> <span data-ttu-id="149e5-113">자세한 내용은 [보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](report-parameters-report-builder-and-report-designer.md)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-113">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md).</span></span>  
  
### <a name="to-add-or-change-the-available-values-for-a-report-parameter"></a><span data-ttu-id="149e5-114">보고서 매개 변수에 대한 사용 가능한 값을 추가 또는 변경하려면</span><span class="sxs-lookup"><span data-stu-id="149e5-114">To add or change the available values for a report parameter</span></span>  
  
1.  <span data-ttu-id="149e5-115">보고서 데이터 창에서 매개 변수 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-115">In the Report Data pane, expand the Parameters node.</span></span> <span data-ttu-id="149e5-116">매개 변수를 마우스 오른쪽 단추로 클릭하고 **매개 변수 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-116">Right-click the parameter and click **Parameter Properties**.</span></span> <span data-ttu-id="149e5-117">**보고서 매개 변수 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-117">The **Report Parameter Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="149e5-118">보고서 데이터 창이 표시되지 않는 경우 **보기** , **보고서 데이터**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-118">If the Report Data pane is not visible, click **View** and then click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="149e5-119">**사용 가능한 값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-119">Click **Available Values**.</span></span> <span data-ttu-id="149e5-120">사용 가능한 값 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-120">Select an available values option:</span></span>  
  
    -   <span data-ttu-id="149e5-121">**값 지정** 을 클릭하여 직접 값 목록과 필요에 따라 값에 대한 이름(레이블)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-121">Click **Specify values** to manually provide a list of values, and optionally, friendly names (the labels) for the values.</span></span>  
  
         <span data-ttu-id="149e5-122">**추가** 를 클릭한 다음 **값** 입력란에 값을 입력하고 필요에 따라 **레이블** 입력란에 레이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-122">Click **Add** and then enter the value in the **Value** text box, and optionally, the label in the **Label** text box.</span></span> <span data-ttu-id="149e5-123">레이블을 제공하지 않으면 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-123">If you do not provide a label, the value is used.</span></span> <span data-ttu-id="149e5-124">값에 대한 식을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-124">You can write an expression for a value.</span></span> <span data-ttu-id="149e5-125">데이터 형식은 매개 변수의 데이터 형식과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-125">The data type must match the data type of the parameter.</span></span> <span data-ttu-id="149e5-126">필드 이름은 매개 변수의 식에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-126">Field names cannot be used in an expression for a parameter.</span></span> <span data-ttu-id="149e5-127">예를 보려면 [일반적으로 사용되는 필터&#40;보고서 작성기 및 SSRS&#41;](commonly-used-filters-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="149e5-127">For examples, see [Commonly Used Filters &#40;Report Builder and SSRS&#41;](commonly-used-filters-report-builder-and-ssrs.md).</span></span>  
  
         <span data-ttu-id="149e5-128">제공할 값 개수만큼 이 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-128">Repeat this step for as many values as you want to provide.</span></span> <span data-ttu-id="149e5-129">이 목록에 표시되는 항목의 순서에 따라 드롭다운 목록에 표시되는 항목의 순서가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-129">The order of items you see in this list determines the order that the user sees them in the drop-down list.</span></span> <span data-ttu-id="149e5-130">목록에서 항목의 순서를 변경하려면 **값** 또는 **레이블** 입력란을 클릭하여 항목을 선택한 다음 위쪽 및 아래쪽 화살표 단추를 사용하여 항목을 목록의 위나 아래로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-130">To change the order of an item in the list, click a **Value** or **Label** text box to select the item, and then use the up and down arrow buttons to move the item higher or lower in the list.</span></span>  
  
    -   <span data-ttu-id="149e5-131">**쿼리에서 값 가져오기**를 클릭하여 이 매개 변수에 대한 값과 필요에 따라 이름을 검색하는 기존 데이터 세트의 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-131">Click **Get values from a query** to provide the name of an existing dataset that retrieves the values, and optionally, the friendly names for this parameter.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="149e5-132">동일한 데이터 세트에 보고서 매개 변수에 대한 해당 쿼리 매개 변수가 있는 경우 보고서를 실행하려고 하면 보고서에서 오류 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-132">If the same dataset contains the corresponding query parameter for the report parameter, the report will display an error message when you try to run it.</span></span> <span data-ttu-id="149e5-133">다른 데이터 세트를 사용하여 값을 검색하면 이 오류를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-133">You resolve this error by using a different dataset to retrieve the values.</span></span>  
  
         <span data-ttu-id="149e5-134">**데이터 세트**에서 데이터 세트의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-134">In **Dataset**, choose the name of the dataset.</span></span>  
  
         <span data-ttu-id="149e5-135">**값 필드**에서 매개 변수 값을 제공하는 필드의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-135">In **Value field**, choose the name of the field that provides parameter values.</span></span>  
  
         <span data-ttu-id="149e5-136">**레이블 필드**에서 매개 변수에 대한 이름을 제공하는 필드의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-136">In **Label field**, choose the name of the field that provides the friendly names for the parameter.</span></span> <span data-ttu-id="149e5-137">이름에 대한 개별 필드가 없으면 **값** 필드에 대해 선택한 동일한 필드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-137">If there is no separate field for friendly names, choose the same field as you chose for the **Value** field.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="149e5-138">보고서를 미리 볼 때 매개 변수에 대한 사용 가능한 값의 드롭다운 목록이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-138">When you preview the report, you see a drop-down list of available values for the parameter.</span></span>  
  
### <a name="to-remove-the-available-values-for-a-report-parameter"></a><span data-ttu-id="149e5-139">보고서 매개 변수에 대한 사용 가능한 값을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="149e5-139">To remove the available values for a report parameter</span></span>  
  
1.  <span data-ttu-id="149e5-140">보고서 데이터 창에서 매개 변수 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-140">In the Report Data pane, expand the Parameters node.</span></span> <span data-ttu-id="149e5-141">매개 변수를 마우스 오른쪽 단추로 클릭하고 **매개 변수 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-141">Right-click the parameter and click **Parameter Properties**.</span></span> <span data-ttu-id="149e5-142">**보고서 매개 변수** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-142">The **Report Parameters** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="149e5-143">**사용 가능한 값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-143">Click **Available Values**.</span></span>  
  
3.  <span data-ttu-id="149e5-144">**다음 옵션 중 하나 선택**에서 **없음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-144">In **Select from one of the following options**, click **None**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="149e5-145">보고서를 미리 볼 때 매개 변수에 대한 사용 가능한 값의 드롭다운 목록이 더 이상 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="149e5-145">When you preview the report, you the drop-down list of available values for the parameter no longer appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="149e5-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="149e5-146">See Also</span></span>  
 <span data-ttu-id="149e5-147">[보고서 매개 변수의 순서 변경&#40;보고서 작성기 및 SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="149e5-147">[Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="149e5-148">[보고서 매개 변수 추가, 변경 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="149e5-148">[Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="149e5-149">[보고서에 연계 매개 변수 추가&#40;보고서 작성기 및 SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="149e5-149">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="149e5-150">[보고서 매개 변수의 기본값 추가, 변경 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md) </span><span class="sxs-lookup"><span data-stu-id="149e5-150">[Add, Change, or Delete Default Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md) </span></span>  
 <span data-ttu-id="149e5-151">[매개 변수 컬렉션 참조&#40;보고서 작성기 및 SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="149e5-151">[Parameters Collection References &#40;Report Builder and SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span></span>  
 <span data-ttu-id="149e5-152">[자습서: 보고서에 매개 변수 추가&#40;보고서 작성기&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="149e5-152">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 [<span data-ttu-id="149e5-153">식&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="149e5-153">Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)  
  
  
