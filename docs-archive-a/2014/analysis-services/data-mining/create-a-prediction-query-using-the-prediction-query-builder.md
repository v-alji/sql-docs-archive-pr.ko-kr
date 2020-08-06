---
title: 예측 쿼리 작성기를 사용 하 여 예측 쿼리 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- prediction queries [Analysis Services]
- Mining Model Prediction [Analysis Services], prediction queries
ms.assetid: e02836e5-dd8c-4c97-a078-840ae79d3660
author: minewiskan
ms.author: owend
ms.openlocfilehash: 13f39de4085cb74949e9540570d574c09e72ee27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647331"
---
# <a name="create-a-prediction-query-using-the-prediction-query-builder"></a><span data-ttu-id="73a9c-102">예측 쿼리 작성기를 사용하여 예측 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="73a9c-102">Create a Prediction Query Using the Prediction Query Builder</span></span>
  <span data-ttu-id="73a9c-103">BI Development Studio에서 데이터 마이닝 솔루션을 작성하는 동안이나 SQL Server Management Studio에서 기존 마이닝 모델을 마우스 오른쪽 단추로 클릭한 다음 **예측 쿼리 작성**옵션을 선택하여 예측 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-103">You can create prediction queries either while you are building a data mining solution in BI Development Studio, or by right-clicking an existing mining model in SQL Server Management Studio, and then choosing the option, **Build Prediction Query**.</span></span>  
  
 <span data-ttu-id="73a9c-104">**예측 쿼리 작성기** 에는 다음과 같은 세 가지 디자인 모드가 있습니다. 모드는 왼쪽 위 모퉁이에 있는 아이콘을 클릭하여 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-104">The **Prediction Query Builder** has the following three design modes, which you can switch among by clicking the icons in the upper-left corner.</span></span>  
  
-   <span data-ttu-id="73a9c-105">**디자인**</span><span class="sxs-lookup"><span data-stu-id="73a9c-105">**Design**</span></span>  
  
-   <span data-ttu-id="73a9c-106">**쿼리**</span><span class="sxs-lookup"><span data-stu-id="73a9c-106">**Query**</span></span>  
  
-   <span data-ttu-id="73a9c-107">**결과**</span><span class="sxs-lookup"><span data-stu-id="73a9c-107">**Result**</span></span>  
  
 <span data-ttu-id="73a9c-108">**디자인** 모드에서는 입력 데이터를 선택하고, 해당 데이터를 모델로 매핑한 다음 작성하는 문에 표를 통해 예측 함수를 추가하여 예측 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-108">**Design** mode lets you build a prediction query by choosing input data, mapping the data to the model, and then adding prediction functions into statements you build by using the grid.</span></span> <span data-ttu-id="73a9c-109">디자인 표에는 세 가지 구성 요소가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-109">The design grid contains these building blocks:</span></span>  
  
 <span data-ttu-id="73a9c-110">**원본**</span><span class="sxs-lookup"><span data-stu-id="73a9c-110">**Source**</span></span>  
 <span data-ttu-id="73a9c-111">새 열의 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-111">Choose the source of the new column.</span></span> <span data-ttu-id="73a9c-112">마이닝 모델의 열, 데이터 원본 뷰에 포함된 입력 테이블, 예측 함수 또는 사용자 지정 식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-112">You can use columns from the mining model, input tables included in the data source view, a prediction function, or a customized expression.</span></span>  
  
 <span data-ttu-id="73a9c-113">**필드**</span><span class="sxs-lookup"><span data-stu-id="73a9c-113">**Field**</span></span>  
 <span data-ttu-id="73a9c-114">**원본** 열에서 선택한 내용과 연결된 특정 열 또는 함수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-114">Determines the specific column or function that is associated with the selection in the **Source** column.</span></span>  
  
 <span data-ttu-id="73a9c-115">**앤티앨리어스**</span><span class="sxs-lookup"><span data-stu-id="73a9c-115">**Alias**</span></span>  
 <span data-ttu-id="73a9c-116">결과 집합에서 열의 이름을 지정하는 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-116">Determines how the column is to be named in the result set.</span></span>  
  
 <span data-ttu-id="73a9c-117">**표시**</span><span class="sxs-lookup"><span data-stu-id="73a9c-117">**Show**</span></span>  
 <span data-ttu-id="73a9c-118">**원본** 열에서 선택한 내용을 결과에 표시할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-118">Determines whether the selection in the **Source** column is displayed in the results.</span></span>  
  
 <span data-ttu-id="73a9c-119">**그룹**</span><span class="sxs-lookup"><span data-stu-id="73a9c-119">**Group**</span></span>  
 <span data-ttu-id="73a9c-120">**및/또는** 열과 함께 괄호를 사용하여 식을 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-120">Works with the **And/Or** column to group expressions together by using parentheses.</span></span> <span data-ttu-id="73a9c-121">예를 들어 (expr1 또는 expr2) 및 expr3입니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-121">For example, (expr1 or expr2) and expr3.</span></span>  
  
 <span data-ttu-id="73a9c-122">**및/또는**</span><span class="sxs-lookup"><span data-stu-id="73a9c-122">**And/Or**</span></span>  
 <span data-ttu-id="73a9c-123">쿼리의 논리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-123">Creates logic in the query.</span></span> <span data-ttu-id="73a9c-124">예를 들어 (expr1 또는 expr2) 및 expr3입니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-124">For example, (expr1 or expr2) and expr3.</span></span>  
  
 <span data-ttu-id="73a9c-125">**조건/인수**</span><span class="sxs-lookup"><span data-stu-id="73a9c-125">**Criteria/Argument**</span></span>  
 <span data-ttu-id="73a9c-126">열에 적용되는 조건이나 사용자 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-126">Specifies a condition or user expression that applies to the column.</span></span> <span data-ttu-id="73a9c-127">열을 테이블에서 셀로 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-127">You can drag columns from the tables to the cell.</span></span>  
  
 <span data-ttu-id="73a9c-128">**쿼리** 모드에서는 DMX(Data Mining Extensions) 언어에 직접 액세스할 수 있는 텍스트 편집기와 입력 데이터 및 모델 열 뷰를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-128">**Query** mode provides a text editor that gives you direct access to the Data Mining Extensions (DMX) language, along with a view of the input data and model columns.</span></span> <span data-ttu-id="73a9c-129">**쿼리** 모드를 선택하면 쿼리 정의에 사용된 표가 기본 텍스트 편집기로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-129">When you select **Query** mode, the grid that you used to define the query is replaced by a basic text editor.</span></span> <span data-ttu-id="73a9c-130">이 편집기를 사용하여, 작성한 쿼리를 복사 및 저장하거나 기존 DMX 쿼리 및 클립보드 내용을 붙여넣어 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-130">You can use this editor to copy and save queries you have composed, or to paste in existing DMX queries and from the Clipboard and run them.</span></span>  
  
 <span data-ttu-id="73a9c-131">**결과** 뷰는 현재 쿼리를 실행하고 결과를 표로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-131">**Result** view runs the current query and displays the results in a grid.</span></span> <span data-ttu-id="73a9c-132">기본 데이터가 변경된 경우 쿼리를 다시 실행하려면 상태 표시줄에 있는 재생 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-132">If the underlying data has changed and you want to rerun the query, click the Play button in the status bar</span></span>  
  
 <span data-ttu-id="73a9c-133">시각적 도구와 텍스트 편집기를 함께 사용하여 데이터 마이닝 쿼리를 디자인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-133">You can design a data mining query by using a combination of the visual tools and the text editor.</span></span> <span data-ttu-id="73a9c-134">텍스트 편집기에서 쿼리에 대한 변경 내용을 입력한 다음 **디자인** 뷰로 전환하면 변경 내용이 모두 손실되고 예측 쿼리 작성기로 만든 원래 쿼리로 돌아갑니다. 이 항목에서는 그래픽 쿼리 작성기 사용법을 연습합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-134">If you type changes to the query in the text editor and switch back to the **Design** view, all the changes are lost, and the query reverts to the original query created by Prediction Query Builder This topic walks you through use of the graphical query builder.</span></span>  
  
### <a name="to-create-a-prediction-query"></a><span data-ttu-id="73a9c-135">예측 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="73a9c-135">To create a prediction query</span></span>  
  
1.  <span data-ttu-id="73a9c-136">데이터 마이닝 디자이너에서 **마이닝 모델 예측** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-136">Click the **Mining Model Prediction** tab in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="73a9c-137">**마이닝 모델** 테이블에서 **모델 선택** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-137">Click **Select Model** on the **Mining Model** table.</span></span>  
  
     <span data-ttu-id="73a9c-138">**마이닝 모델 선택** 대화 상자가 열리고 현재 프로젝트에 있는 모든 마이닝 구조를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-138">The **Select Mining Model** dialog box opens to show all the mining structures that exist in the current project.</span></span>  
  
3.  <span data-ttu-id="73a9c-139">예측을 만들 모델을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-139">Select the model on which you want to create a prediction, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="73a9c-140">**입력 테이블 선택** 테이블에서 **사례 테이블 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-140">On the **Select Input Table(s)** table, click **Select Case Table**.</span></span>  
  
     <span data-ttu-id="73a9c-141">**테이블 선택** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-141">The **Select Table** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="73a9c-142">**데이터 원본** 목록에서 예측을 만들 데이터가 포함된 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-142">In the **Data Source** list, select the data source that contains the data on which to create a prediction.</span></span>  
  
6.  <span data-ttu-id="73a9c-143">**테이블/뷰 이름** 상자에서 예측을 만들 데이터가 포함된 테이블을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-143">In the **Table/View Name** box, select the table that contains the data on which to create a prediction, and then click **OK**.</span></span>  
  
     <span data-ttu-id="73a9c-144">입력 테이블을 선택하면 열 이름을 기반으로 마이닝 모델과 입력 테이블 간에 기본 매핑이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-144">After you select the input table, Prediction Query Builder creates a default mapping between the mining model and the input table, based on the names of the columns.</span></span> <span data-ttu-id="73a9c-145">매핑을 삭제하려면 **마이닝 모델** 테이블의 열을 **입력 테이블 선택** 테이블의 매핑된 열에 연결하는 선을 클릭하여 선택한 다음 Delete 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-145">To delete a mapping, click to select the line that links the column in the **Mining Model** table to the mapped column in the **Select Input Table(s)** table, and then press DELETE.</span></span> <span data-ttu-id="73a9c-146">**입력 테이블 선택** 테이블의 열을 클릭한 다음 **마이닝 모델** 테이블의 해당 열로 끌어서 매핑을 수동으로 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-146">You can also manually create mappings by clicking a column in the **Select Input Table(s)** table and dragging it onto the corresponding column in the **Mining Model** table.</span></span>  
  
7.  <span data-ttu-id="73a9c-147">예측 쿼리 작성기 표에 다음 세 유형의 정보를 원하는 대로 조합하여 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-147">Add any combination of the following three types of information to the Prediction Query Builder grid:</span></span>  
  
    -   <span data-ttu-id="73a9c-148">**마이닝 모델** 상자에서 가져온 예측 가능한 열</span><span class="sxs-lookup"><span data-stu-id="73a9c-148">Predictable columns from the **Mining Model** box.</span></span>  
  
    -   <span data-ttu-id="73a9c-149">**입력 테이블 선택** 상자에서 가져온 입력 열의 조합</span><span class="sxs-lookup"><span data-stu-id="73a9c-149">Any combination of input columns from the **Select Input Table(s)** box.</span></span>  
  
    -   <span data-ttu-id="73a9c-150">예측 함수</span><span class="sxs-lookup"><span data-stu-id="73a9c-150">Prediction functions</span></span>  
  
8.  <span data-ttu-id="73a9c-151">**마이닝 모델 예측** 탭의 도구 모음에 있는 첫 번째 단추를 누른 다음 **결과**를 선택하여 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="73a9c-151">Run the query by clicking the first button on the toolbar of the **Mining Model Prediction** tab, and then selecting **Result**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73a9c-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73a9c-152">See Also</span></span>  
 <span data-ttu-id="73a9c-153">[데이터 마이닝 디자이너에서 단일 쿼리 만들기](create-a-singleton-query-in-the-data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="73a9c-153">[Create a Singleton Query in the Data Mining Designer](create-a-singleton-query-in-the-data-mining-designer.md) </span></span>  
 [<span data-ttu-id="73a9c-154">데이터 마이닝 쿼리</span><span class="sxs-lookup"><span data-stu-id="73a9c-154">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
