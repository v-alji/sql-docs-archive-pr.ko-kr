---
title: 디자인 창 (마이닝 모델 예측 뷰) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.prediction.design.f1
ms.assetid: 17f24c8d-43cd-4f4d-83b3-a41ee8fbe8e8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 32ac73a2d6fde38d15d1f45a8439293695749ea4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733276"
---
# <a name="design-pane-mining-model-prediction-view"></a><span data-ttu-id="78c4d-102">디자인 창(마이닝 모델 예측 뷰)</span><span class="sxs-lookup"><span data-stu-id="78c4d-102">Design Pane (Mining Model Prediction View)</span></span>
  <span data-ttu-id="78c4d-103">**디자인** 창에는 데이터 마이닝 예측을 작성할 때 사용할 수 있는 예측 쿼리 작성기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-103">The **Design** pane contains the Prediction Query Builder, which you can use to build data mining predictions.</span></span> <span data-ttu-id="78c4d-104">데이터 원본 뷰에서 입력 데이터의 테이블을 사용하는 예측 쿼리를 디자인하여 대량 예측을 생성하거나 개별 값을 제공할 수 있는 단일 예측 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-104">You can design prediction queries that use tables of input data from a data source view, to generate bulk predictions, or you can create singleton prediction queries, which let you provide individual values.</span></span>  
  
 <span data-ttu-id="78c4d-105">쿼리를 실행하고 결과를 보려면 쿼리 결과 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-105">To run the query and view the results, switch to query result view.</span></span>  
  
 <span data-ttu-id="78c4d-106">**쿼리** 뷰에는 예측 쿼리 작성기에서 만드는 DMX(Data Mining Extensions) 쿼리가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-106">The **Query** view displays the Data Mining Extensions (DMX) query that Prediction Query Builder creates.</span></span> <span data-ttu-id="78c4d-107">DMX에 익숙하면 이 쿼리를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-107">If you are familiar with DMX, you can customize this query.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="78c4d-108">쿼리를 수동으로 변경한 경우 디자인 뷰로 다시 전환하면 변경 내용이 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-108">If you make any manual changes to the query, your changes will be lost when you switch back to Design view.</span></span> <span data-ttu-id="78c4d-109">DMX 쿼리를 저장하려면 쿼리를 Windows 클립보드로 복사한 다음 텍스트 파일에 붙여 넣으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-109">If you want to save the DMX query, you can copy the query to the Windows Clipboard and then paste it to a text file.</span></span>  
  
 <span data-ttu-id="78c4d-110">**참조 항목:** [데이터 마이닝 쿼리](data-mining/data-mining-queries.md)</span><span class="sxs-lookup"><span data-stu-id="78c4d-110">**For More Information:** [Data Mining Queries](data-mining/data-mining-queries.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="78c4d-111">옵션</span><span class="sxs-lookup"><span data-stu-id="78c4d-111">Options</span></span>  
 <span data-ttu-id="78c4d-112">**쿼리 결과 뷰로 전환**</span><span class="sxs-lookup"><span data-stu-id="78c4d-112">**Switch to query result view**</span></span>  
 <span data-ttu-id="78c4d-113">**디자인**, **쿼리**및 **결과** 창 사이를 전환하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-113">Click to switch between the **Design**, **Query**, and **Result** panes.</span></span> <span data-ttu-id="78c4d-114">**결과** 창으로 전환하면 쿼리가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-114">Switching to the **Result** pane runs the query.</span></span>  
  
 <span data-ttu-id="78c4d-115">**쿼리 결과 저장**</span><span class="sxs-lookup"><span data-stu-id="78c4d-115">**Save the query result**</span></span>  
 <span data-ttu-id="78c4d-116">**데이터 마이닝 쿼리 결과 저장** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-116">Opens the **Save Data Mining Query Result** dialog box.</span></span>  
  
 <span data-ttu-id="78c4d-117">**단일 쿼리**</span><span class="sxs-lookup"><span data-stu-id="78c4d-117">**Singleton query**</span></span>  
 <span data-ttu-id="78c4d-118">알려진 데이터의 원본으로 테이블을 제공하는 대신 쿼리에 대한 값을 직접 제공할 수 있는 단일 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-118">Enables creating a singleton query, in which you can provide values directly for the query instead of providing a table as the source of the known data.</span></span> <span data-ttu-id="78c4d-119">**입력 테이블 선택** 테이블이 **단일 쿼리 입력** 테이블로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-119">The **Select Input Table(s)** table is replaced by a **Singleton Query Input** table.</span></span>  
  
 <span data-ttu-id="78c4d-120">**쿼리 결과 새로 고침**</span><span class="sxs-lookup"><span data-stu-id="78c4d-120">**Refresh query results**</span></span>  
 <span data-ttu-id="78c4d-121">예측 쿼리를 다시 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-121">Reprocesses the prediction query.</span></span> <span data-ttu-id="78c4d-122">이 옵션은 **결과** 창에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-122">This is enabled only in the **Result** pane.</span></span>  
  
 <span data-ttu-id="78c4d-123">**마이닝 모델**</span><span class="sxs-lookup"><span data-stu-id="78c4d-123">**Mining Model**</span></span>  
 <span data-ttu-id="78c4d-124">예측의 기반으로 하려고 선택한 마이닝 모델을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-124">Displays the selected mining model on which you want to base predictions.</span></span>  
  
 <span data-ttu-id="78c4d-125">**모델 선택**</span><span class="sxs-lookup"><span data-stu-id="78c4d-125">**Select Model**</span></span>  
 <span data-ttu-id="78c4d-126">**마이닝 모델 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-126">Opens the **Select Mining Model** dialog box.</span></span>  
  
 <span data-ttu-id="78c4d-127">**입력 테이블 선택**</span><span class="sxs-lookup"><span data-stu-id="78c4d-127">**Select Input Table(s)**</span></span>  
 <span data-ttu-id="78c4d-128">예측의 기반이 되는 알려진 데이터를 포함하는 선택한 입력 테이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-128">Displays the selected input tables that contain known data on which to base the predictions.</span></span>  
  
 <span data-ttu-id="78c4d-129">**테이블 삭제**</span><span class="sxs-lookup"><span data-stu-id="78c4d-129">**Delete Table**</span></span>  
 <span data-ttu-id="78c4d-130">선택한 테이블을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-130">Deletes the selected table.</span></span> <span data-ttu-id="78c4d-131">테이블이 없거나 테이블을 선택하지 않은 경우에는 이 단추를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-131">This button is disabled if a table has not been selected or does not exist.</span></span>  
  
 <span data-ttu-id="78c4d-132">**사례 테이블 선택**</span><span class="sxs-lookup"><span data-stu-id="78c4d-132">**Select Case Table**</span></span>  
 <span data-ttu-id="78c4d-133">**테이블 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-133">Opens the **Select Table** dialog box.</span></span> <span data-ttu-id="78c4d-134">이 단추는 사례 테이블을 선택하지 않은 경우에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-134">This button appears only if a case table has not been selected.</span></span>  
  
 <span data-ttu-id="78c4d-135">**중첩 테이블 선택**</span><span class="sxs-lookup"><span data-stu-id="78c4d-135">**Select Nested Table**</span></span>  
 <span data-ttu-id="78c4d-136">**테이블 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-136">Opens the **Select Table** dialog box.</span></span> <span data-ttu-id="78c4d-137">이 단추는 사례 테이블을 선택한 경우에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-137">This button appears only if a case table has been selected.</span></span> <span data-ttu-id="78c4d-138">관련 마이닝 구조에 중첩 테이블이 없는 경우에는 이 단추를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-138">If the associated mining structure does not contain a nested table, this button is disabled.</span></span>  
  
 <span data-ttu-id="78c4d-139">**조인 수정**</span><span class="sxs-lookup"><span data-stu-id="78c4d-139">**Modify Join**</span></span>  
 <span data-ttu-id="78c4d-140">**중첩 조인 지정** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-140">Opens the **Specify Nested Join** dialog box.</span></span> <span data-ttu-id="78c4d-141">이 단추는 중첩 테이블을 선택한 경우에만 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-141">This button is active only if the nested table is selected.</span></span>  
  
 <span data-ttu-id="78c4d-142">**단일 쿼리 입력**</span><span class="sxs-lookup"><span data-stu-id="78c4d-142">**Singleton Query input**</span></span>  
 <span data-ttu-id="78c4d-143">**단일 쿼리** 단추를 선택한 경우에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-143">Enabled when you select the **Singleton query** button.</span></span> <span data-ttu-id="78c4d-144">다음 열을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-144">Contains the following columns:</span></span>  
  
|<span data-ttu-id="78c4d-145">값</span><span class="sxs-lookup"><span data-stu-id="78c4d-145">Value</span></span>|<span data-ttu-id="78c4d-146">설명</span><span class="sxs-lookup"><span data-stu-id="78c4d-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="78c4d-147">**마이닝 모델 열**</span><span class="sxs-lookup"><span data-stu-id="78c4d-147">**Mining Model Column**</span></span>|<span data-ttu-id="78c4d-148">**마이닝 모델** 테이블에서 선택한 마이닝 모델에 포함된 마이닝 모델 열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-148">Lists the mining model columns contained within the mining model that is selected in the **Mining Model** table.</span></span>|  
|<span data-ttu-id="78c4d-149">**값**</span><span class="sxs-lookup"><span data-stu-id="78c4d-149">**Value**</span></span>|<span data-ttu-id="78c4d-150">선택한 마이닝 모델 열의 가능한 각 상태를 포함하는 목록에서 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-150">Select a value from the list that contains each possible state of the selected mining model column.</span></span><br /><br /> <span data-ttu-id="78c4d-151">열이 중첩 테이블 열인 경우 값 셀을 클릭하면 **중첩 테이블 입력** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-151">If the column is a nested table column, clicking the value cell opens the **Nested Table Input** dialog box.</span></span>|  
  
 <span data-ttu-id="78c4d-152">**원본**</span><span class="sxs-lookup"><span data-stu-id="78c4d-152">**Source**</span></span>  
 <span data-ttu-id="78c4d-153">열에 사용할 필드를 포함하는 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-153">Select the source that contains the field that you will use for the column.</span></span> <span data-ttu-id="78c4d-154">**마이닝 모델** 테이블에서 선택한 마이닝 모델, 입력 테이블 또는 **입력 테이블 선택** 테이블에서 선택한 테이블, 예측 함수 또는 사용자 지정 식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-154">You can either use the mining model that is selected in the **Mining Model** table, the input table or tables that are selected in the **Select Input Table(s)** table, a prediction function, or a custom expression.</span></span>  
  
 <span data-ttu-id="78c4d-155">마이닝 모델 및 입력 테이블을 포함하는 테이블에서 셀로 열을 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-155">Columns can be dragged from the tables containing the mining model and input tables onto the cell.</span></span>  
  
 <span data-ttu-id="78c4d-156">**필드**</span><span class="sxs-lookup"><span data-stu-id="78c4d-156">**Field**</span></span>  
 <span data-ttu-id="78c4d-157">원본 테이블에서 파생된 열 목록에서 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-157">Select a column from the list of columns derived from the source table.</span></span> <span data-ttu-id="78c4d-158">**원본** 에서 **예측 함수**를 선택한 경우 여기에는 선택한 마이닝 모델에 사용할 수 있는 예측 함수가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-158">If you selected **Prediction Function** in **Source**, this contains the prediction function available for the selected mining model.</span></span>  
  
 <span data-ttu-id="78c4d-159">**그룹**</span><span class="sxs-lookup"><span data-stu-id="78c4d-159">**Group**</span></span>  
 <span data-ttu-id="78c4d-160">**및/또는** 열과 함께 사용하여 식을 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-160">Use with the **And/Or** column to group expressions together.</span></span> <span data-ttu-id="78c4d-161">예들 들어 `(expr1 Or expr2) And expr3`입니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-161">For example, `(expr1 Or expr2) And expr3`.</span></span>  
  
 <span data-ttu-id="78c4d-162">**및/또는**</span><span class="sxs-lookup"><span data-stu-id="78c4d-162">**And/Or**</span></span>  
 <span data-ttu-id="78c4d-163">논리적 쿼리를 만드는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-163">Use to create a logical query.</span></span> <span data-ttu-id="78c4d-164">예들 들어 `(expr1 Or expr2) And expr3`입니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-164">For example, `(expr1 Or expr2) And expr3`.</span></span>  
  
 <span data-ttu-id="78c4d-165">**조건/인수**</span><span class="sxs-lookup"><span data-stu-id="78c4d-165">**Criteria/Argument**</span></span>  
 <span data-ttu-id="78c4d-166">열에 적용되는 조건 또는 사용자 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-166">Specify a condition or user expression that applies to the column.</span></span> <span data-ttu-id="78c4d-167">마이닝 모델 및 입력 테이블을 포함하는 테이블에서 셀로 열을 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c4d-167">Columns can be dragged from the tables containing the mining model and input tables onto the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78c4d-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="78c4d-168">See Also</span></span>  
 <span data-ttu-id="78c4d-169">[데이터 마이닝 확장 &#40;DMX&#41; 문 참조](/sql/dmx/data-mining-extensions-dmx-statements) </span><span class="sxs-lookup"><span data-stu-id="78c4d-169">[Data Mining Extensions &#40;DMX&#41; Statement Reference](/sql/dmx/data-mining-extensions-dmx-statements) </span></span>  
 <span data-ttu-id="78c4d-170">[데이터 마이닝 쿼리 인터페이스](data-mining/data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="78c4d-170">[Data Mining Query Interfaces](data-mining/data-mining-query-tools.md) </span></span>  
 [<span data-ttu-id="78c4d-171">예측 쿼리 작성기&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="78c4d-171">Prediction Query Builder &#40;Data Mining&#41;</span></span>](prediction-query-builder-data-mining.md)  
  
  
