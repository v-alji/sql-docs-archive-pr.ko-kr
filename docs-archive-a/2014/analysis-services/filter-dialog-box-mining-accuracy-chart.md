---
title: 필터 대화 상자 (마이닝 정확도 차트) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 71e884a9-7ec4-4459-a4c4-87f6c796d478
author: minewiskan
ms.author: owend
ms.openlocfilehash: dcdfb7cd7b425c3f8c4711e8b1812afc12898e1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653044"
---
# <a name="filter-dialog-box-mining-accuracy-chart"></a><span data-ttu-id="c1902-102">필터 대화 상자(마이닝 정확도 차트)</span><span class="sxs-lookup"><span data-stu-id="c1902-102">Filter Dialog Box (Mining Accuracy Chart)</span></span>
  <span data-ttu-id="c1902-103">**필터** 대화 상자를 사용하면 데이터 집합에 적용할 수 있는 조건을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-103">The **Filter** dialog box helps you build conditions that you can apply to a data set.</span></span> <span data-ttu-id="c1902-104">데이터 집합은 테스트에 사용되는 외부 데이터 집합이나 마이닝 모델 학습에 사용되는 사례 데이터일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-104">The data set can be an external data set used for testing, or the case data used to train a mining model.</span></span> <span data-ttu-id="c1902-105">이 대화 상자를 사용하면 **데이터 집합 필터** 대화 상자 또는 **모델 필터** 대화 상자에서 보다 복잡한 필터 조건의 일부로 저장할 수 있는 조건을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-105">This dialog box helps you build criteria that you can save as part of more complex filter criteria in either the **Data Set Filter** dialog box or the **Model Filter** dialog box.</span></span>  
  
-   <span data-ttu-id="c1902-106">**데이터 집합 필터** 대화 상자는 **마이닝 정확도 차트** 디자이너의 **입력 선택** 탭에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-106">The **Data Set Filter** dialog box is available from the **Input Selection** tab of the **Mining Accuracy Chart** designer.</span></span>  
  
-   <span data-ttu-id="c1902-107">**모델 필터** 대화 상자는 데이터 마이닝 디자이너의 **마이닝 모델** 탭에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-107">The **Model Filter** dialog box is available from the **Mining Models** tab of the Data Mining designer.</span></span>  
  
 <span data-ttu-id="c1902-108">마이닝 모델에 필터를 적용하려면 먼저 **모델 필터** 대화 상자를 사용하여 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-108">If you are applying a filter to a mining model, first you use the **Model Filter** dialog box to choose a table.</span></span> <span data-ttu-id="c1902-109">그런 다음 **필터** 대화 상자를 사용하여 해당 테이블에만 적용되는 조건을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-109">Then, you can use the **Filter** dialog box to build conditions that apply only to that table.</span></span>  
  
 <span data-ttu-id="c1902-110">외부 테스트 데이터 집합에 적용할 필터를 만들려면 먼저 **데이터 집합 필터** 대화 상자를 사용하여 데이터 원본 뷰의 테이블 목록에서 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-110">If you are creating a filter to apply to an external test data set, first you use the **Data Set Filter** dialog box to choose a table from the list of tables in a data source view.</span></span> <span data-ttu-id="c1902-111">그런 다음 **필터** 대화 상자를 사용하여 해당 테이블에만 적용되는 조건을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-111">Then, you use the **Filter** dialog box to build conditions that apply only to that table.</span></span>  
  
 <span data-ttu-id="c1902-112">단일 테이블에 적용되는 조건 집합을 만든 후 [!INCLUDE[clickOK](../includes/clickok-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1902-112">After you have created a set of conditions that apply to a single table, [!INCLUDE[clickOK](../includes/clickok-md.md)].</span></span> <span data-ttu-id="c1902-113">**필터** 대화 상자에서 적용한 변경 내용은 부모 대화 상자인 **데이터 집합 필터** 또는 **모델 필터**의 필터 식에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-113">The changes that you made in the **Filter** dialog box are automatically added to the filter expression in the parent dialog box, **Data Set Filter** or **Model Filter**.</span></span>  
  
 <span data-ttu-id="c1902-114">새 데이터 집합에 필터를 적용하면 기존 데이터 마이닝 모델을 사용하여 데이터 집합에서 조건에 맞는 사례만 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-114">If you apply the filter to the new data set, the existing data mining model is used to evaluate only those cases in the data set that meet the conditions.</span></span> <span data-ttu-id="c1902-115">그러나 마이닝 모델 자체에 필터를 적용하면 마이닝 모델 내에서 이러한 조건에 맞는 사례에 대해서만 모델의 정확도가 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-115">However, if you apply the filter to the mining model itself, the accuracy of the model is assessed for only those cases within the mining model that meet those criteria.</span></span>  
  
 <span data-ttu-id="c1902-116">**자세한 내용:** [테스트 및 유효성 검사&#40;데이터 마이닝&#41;](data-mining/testing-and-validation-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="c1902-116">**For more information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="c1902-117">옵션</span><span class="sxs-lookup"><span data-stu-id="c1902-117">Options</span></span>  
 <span data-ttu-id="c1902-118">**조건**</span><span class="sxs-lookup"><span data-stu-id="c1902-118">**Conditions**</span></span>  
 <span data-ttu-id="c1902-119">**데이터 집합 필터** 대화 상자에서 선택한 테이블의 열에 대한 조건을 지정하는 열을 포함하는 표입니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-119">A grid that contains columns where you specify conditions on columns from the table that you selected in the **Data Set Filter** dialog box.</span></span>  
  
|<span data-ttu-id="c1902-120">값</span><span class="sxs-lookup"><span data-stu-id="c1902-120">Value</span></span>|<span data-ttu-id="c1902-121">Description</span><span class="sxs-lookup"><span data-stu-id="c1902-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c1902-122">**및/또는**</span><span class="sxs-lookup"><span data-stu-id="c1902-122">**And/Or**</span></span>|<span data-ttu-id="c1902-123">이 줄의 조건에 AND 연산자를 적용할지, 아니면 OR 연산자를 적용할지를 지정하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-123">Click to specify whether to apply the AND operator or the OR operator to the condition on this line.</span></span> <span data-ttu-id="c1902-124">이러한 값은 **마이닝 구조 열** 목록에서 열을 선택한 후에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-124">These values become available only after you have selected a column from the **Mining Structure Column** list.</span></span>|  
|<span data-ttu-id="c1902-125">**마이닝 구조 열**</span><span class="sxs-lookup"><span data-stu-id="c1902-125">**Mining Structure Column**</span></span>|<span data-ttu-id="c1902-126">**데이터 집합 필터** 대화 상자의 데이터 원본에서 선택한 테이블에 포함된 열 목록에서 열을 선택하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-126">Click to select a column from the list of the columns contained in the table that you selected from the data source in the **Data Set Filter** dialog box.</span></span>|  
|<span data-ttu-id="c1902-127">**연산자**</span><span class="sxs-lookup"><span data-stu-id="c1902-127">**Operator**</span></span>|<span data-ttu-id="c1902-128">목록에서 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-128">Select an operator from the list.</span></span> <span data-ttu-id="c1902-129">사용할 수 있는 연산자는 열의 데이터 형식에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-129">The operators that are available depend on the data type of the column.</span></span><br /><br /> <span data-ttu-id="c1902-130">열에 불연속 값이 포함되어 있으면 다음 연산자만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-130">If the column contains discrete values, only the following operators are available:</span></span><br /><br /> <span data-ttu-id="c1902-131">=(같음), <>(같지 않음), IS NOT NULL, IS NULL</span><span class="sxs-lookup"><span data-stu-id="c1902-131">= (equal to), <> (not equal to), IS NOT NULL, IS NULL.</span></span><br /><br /> <span data-ttu-id="c1902-132">열에 연속 값이 포함되어 있으면 보다 큼 연산자와 보다 작음 연산자도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-132">If the column contains continuous values, operators for greater than and less than operations are also supported.</span></span>|  
|<span data-ttu-id="c1902-133">**값**</span><span class="sxs-lookup"><span data-stu-id="c1902-133">**Value**</span></span>|<span data-ttu-id="c1902-134">조건으로 사용할 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c1902-134">Type a value to use as a condition.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1902-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c1902-135">See Also</span></span>  
 <span data-ttu-id="c1902-136">[테스트 및 유효성 검사 태스크 및 방법 &#40;데이터 마이닝&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c1902-136">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="c1902-137">마이닝 정확도 차트 디자이너 &#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="c1902-137">Mining Accuracy Chart Designer &#40;Data Mining&#41;</span></span>](mining-accuracy-chart-designer-data-mining.md)  
  
  
