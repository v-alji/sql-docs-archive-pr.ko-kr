---
title: 피벗 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.pivottrans.f1
helpviewer_keywords:
- Pivot transformation
- normalized data [Integration Services]
- PivotUsage property
- datasets [Integration Services], normalized data
- less normalized data set [Integration Services]
ms.assetid: 55f5db6e-6777-435f-8a06-b68c129f8437
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 43bdc5be709ea00d4be4601f52c38e96fe3f1ce4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743411"
---
# <a name="pivot-transformation"></a><span data-ttu-id="0bf73-102">피벗 변환</span><span class="sxs-lookup"><span data-stu-id="0bf73-102">Pivot Transformation</span></span>
  <span data-ttu-id="0bf73-103">피벗 변환은 입력 데이터를 열 값으로 피벗함으로써 정규화된 데이터 집합을 정규화 상태는 낮지만 좀 더 압축된 버전으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-103">The Pivot transformation makes a normalized data set into a less normalized but more compact version by pivoting the input data on a column value.</span></span> <span data-ttu-id="0bf73-104">예를 들어 고객 이름, 제품 및 구매 수량이 나열된 정규화된 **Orders** 데이터 집합에는 일반적으로 여러 제품을 구매한 고객에 대해 여러 행이 포함되어 있으며, 각 행에는 해당 고객의 각 제품 주문 정보가 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-104">For example, a normalized **Orders** data set that lists customer name, product, and quantity purchased typically has multiple rows for any customer who purchased multiple products, with each row for that customer showing order details for a different product.</span></span> <span data-ttu-id="0bf73-105">피벗 변환을 사용하여 이 데이터 집합을 제품 열로 피벗하면 각 고객별로 단일 행만 포함된 데이터 집합을 출력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-105">By pivoting the data set on the product column, the Pivot transformation can output a data set with a single row per customer.</span></span> <span data-ttu-id="0bf73-106">이 단일 행에는 해당 고객의 모든 구매 정보가 나열되며, 제품 이름은 열 이름으로, 그리고 수량은 제품 열에 값으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-106">That single row lists all the purchases by the customer, with the product names shown as column names, and the quantity shown as a value in the product column.</span></span> <span data-ttu-id="0bf73-107">모든 고객이 모든 제품을 구매하는 것은 아니기 때문에 여러 열에 Null 값이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-107">Because not every customer purchases every product, many columns may contain null values.</span></span>  
  
 <span data-ttu-id="0bf73-108">데이터 세트가 피벗되면 입력 열은 피벗 프로세스에서 서로 다른 역할을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-108">When a dataset is pivoted, input columns perform different roles in the pivoting process.</span></span> <span data-ttu-id="0bf73-109">열은 다음과 같은 방식으로 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-109">A column can participate in the following ways:</span></span>  
  
-   <span data-ttu-id="0bf73-110">열이 변경되지 않은 상태로 출력에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-110">The column is passed through unchanged to the output.</span></span> <span data-ttu-id="0bf73-111">여러 입력 행이 단일 출력 행으로 될 수 있기 때문에 변환에서 열의 첫 번째 입력 값만 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-111">Because many input rows can result only in one output row, the transformation copies only the first input value for the column.</span></span>  
  
-   <span data-ttu-id="0bf73-112">열이 레코드 집합을 식별하는 키 또는 키의 일부 역할을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-112">The column acts as the key or part of the key that identifies a set of records.</span></span>  
  
-   <span data-ttu-id="0bf73-113">열이 피벗을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-113">The column defines the pivot.</span></span> <span data-ttu-id="0bf73-114">이 열의 값은 피벗된 데이터 세트의 열과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-114">The values in this column are associated with columns in the pivoted dataset.</span></span>  
  
-   <span data-ttu-id="0bf73-115">열에 포함된 값이 피벗으로 생성된 열에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-115">The column contains values that are placed in the columns that the pivot creates.</span></span>  
  
 <span data-ttu-id="0bf73-116">이 변환에는 하나의 입력, 하나의 일반 출력 및 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-116">This transformation has one input, one regular output, and one error output.</span></span>  
  
## <a name="sort-and-duplicate-rows"></a><span data-ttu-id="0bf73-117">행 정렬 및 중복</span><span class="sxs-lookup"><span data-stu-id="0bf73-117">Sort and Duplicate Rows</span></span>  
 <span data-ttu-id="0bf73-118">출력 데이터 세트에서 레코드를 가능한 적게 만들 수 있도록 데이터를 효율적으로 피벗하려면 입력 데이터가 피벗 열에서 정렬되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-118">To pivot data efficiently, which means creating as few records in the output dataset as possible, the input data must be sorted on the pivot column.</span></span> <span data-ttu-id="0bf73-119">데이터가 정렬되어 있지 않을 때 피벗 변환을 수행하면 집합 멤버 자격을 정의하는 열인 집합 키에서 각 값에 대해 여러 레코드가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-119">If the data is not sorted, the Pivot transformation might generate multiple records for each value in the set key, which is the column that defines set membership.</span></span> <span data-ttu-id="0bf73-120">예를 들어 데이터 세트를 **Name** 열로 피벗할 때 이름이 정렬되어 있지 않으면 **Name** 의 값이 변경될 때마다 피벗이 발생하기 때문에 각 고객에 대해 두 개 이상의 행이 출력 데이터 세트에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-120">For example, if a dataset is pivoted on a **Name** column but the names are not sorted, the output dataset could have more than one row for each customer, because a pivot occurs every time that the value in **Name** changes.</span></span>  
  
 <span data-ttu-id="0bf73-121">입력 데이터에는 중복 행이 포함될 수 있는데 이 경우 피벗 변환이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-121">The input data might contain duplicate rows, which will cause the Pivot transformation to fail.</span></span> <span data-ttu-id="0bf73-122">"중복 행"은 집합 키 열과 피벗 열에 동일한 값이 있는 행을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-122">"Duplicate rows" means rows that have the same values in the set key columns and the pivot columns.</span></span> <span data-ttu-id="0bf73-123">오류를 방지하려면 오류 행이 오류 출력으로 리디렉션되도록 변환을 구성하거나 중복 행이 없도록 값을 미리 집계합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-123">To avoid failure, you can either configure the transformation to redirect error rows to an error output or you can pre-aggregate values to ensure there are no duplicate rows.</span></span>  
  
##  <a name="options-in-the-pivot-dialog-box"></a><a name="options"></a> <span data-ttu-id="0bf73-124">피벗 대화 상자의 옵션</span><span class="sxs-lookup"><span data-stu-id="0bf73-124">Options in the Pivot Dialog Box</span></span>  
 <span data-ttu-id="0bf73-125">**피벗** 대화 상자에서 옵션을 설정하여 피벗 작업을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-125">You configure the pivot operation by setting the options in the **Pivot** dialog box.</span></span> <span data-ttu-id="0bf73-126">**피벗** 대화 상자를 열려면 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서 피벗 변환을 패키지에 추가한 후 구성 요소를 마우스 오른쪽 단추로 클릭하고 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-126">To open the **Pivot** dialog box, add the Pivot transformation to the package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], and then right-click the component and click **Edit**.</span></span>  
  
 <span data-ttu-id="0bf73-127">다음 목록에서는 **피벗** 대화 상자의 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-127">The following list describes the options in the **Pivot** dialog box.</span></span>  
  
 <span data-ttu-id="0bf73-128">**피벗 키**</span><span class="sxs-lookup"><span data-stu-id="0bf73-128">**Pivot Key**</span></span>  
 <span data-ttu-id="0bf73-129">테이블의 맨 위 행(머리글 행)에서 값에 사용할 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-129">Specifies the column to use for values across the top row (header row) of the table.</span></span>  
  
 <span data-ttu-id="0bf73-130">**키 설정**</span><span class="sxs-lookup"><span data-stu-id="0bf73-130">**Set Key**</span></span>  
 <span data-ttu-id="0bf73-131">테이블의 왼쪽 열에 있는 값에 사용할 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-131">Specifies the column to use for values in the left column of the table.</span></span> <span data-ttu-id="0bf73-132">입력 날짜는 이 열에서 정렬되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-132">The input date must be sorted on this column.</span></span>  
  
 <span data-ttu-id="0bf73-133">**피벗 값**</span><span class="sxs-lookup"><span data-stu-id="0bf73-133">**Pivot Value**</span></span>  
 <span data-ttu-id="0bf73-134">머리글 행 및 왼쪽 열에 있는 값이 아닌 다른 값으로 테이블 값에 사용할 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-134">Specifies the column to use for the table values, other than the values in the header row and the left column.</span></span>  
  
 <span data-ttu-id="0bf73-135">**일치하지 않는 피벗 키 값을 무시하고 DataFlow 실행 후 보고**</span><span class="sxs-lookup"><span data-stu-id="0bf73-135">**Ignore un-matched Pivot Key values and report them after DataFlow execution**</span></span>  
 <span data-ttu-id="0bf73-136">패키지를 실행할 때 **피벗 키** 열에서 인식되지 않은 값이 포함된 행을 무시하고 모든 피벗 키 값을 로그 메시지로 출력하도록 피벗 변환을 구성하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-136">Select this option to configure the Pivot transformation to ignore rows containing unrecognized values in the **Pivot Key** column and to output all of the pivot key values to a log message, when the package is run.</span></span>  
  
 <span data-ttu-id="0bf73-137">`PassThroughUnmatchedPivotKeys` 사용자 지정 속성을 `True`로 설정하여 값을 출력하도록 변환을 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-137">You can also configure the transformation to output the values by setting the `PassThroughUnmatchedPivotKeys` custom property to `True`.</span></span>  
  
 <span data-ttu-id="0bf73-138">**값에서 피벗 출력 열 생성**</span><span class="sxs-lookup"><span data-stu-id="0bf73-138">**Generate pivot output columns from values**</span></span>  
 <span data-ttu-id="0bf73-139">각 값에 대해 출력 열을 만들기 위해 피벗 변환을 설정하려면 이 상자에 피벗 키 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-139">Enter the pivot key values in this box to enable the Pivot transformation to create output columns for each value.</span></span> <span data-ttu-id="0bf73-140">패키지를 실행하기 전 값을 입력하거나 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-140">You can either enter the values prior to running the package, or do the following.</span></span>  
  
1.  <span data-ttu-id="0bf73-141">**일치하지 않는 피벗 키 값을 무시하고 DataFlow 실행 후 보고** 옵션을 선택한 후 **피벗** 대화 상자에서 **확인** 을 클릭하여 피벗 변환에 대한 변경 사항을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-141">Select the **Ignore un-matched Pivot Key values and report them after DataFlow execution** option, and then click **OK** in the **Pivot** dialog box to save the changes to the Pivot transformation.</span></span>  
  
2.  <span data-ttu-id="0bf73-142">패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-142">Run the package.</span></span>  
  
3.  <span data-ttu-id="0bf73-143">패키지가 성공하면 **진행률** 탭을 클릭하고 피벗 변환에서 피벗 키 값이 포함된 정보 로그를 찾아 봅니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-143">When the package succeeds, click the **Progress** tab and look for the information log message from the Pivot transformation that contains the pivot key values.</span></span>  
  
4.  <span data-ttu-id="0bf73-144">메시지를 마우스 오른쪽 단추로 클릭한 다음 **메시지 텍스트 복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-144">Right-click the message and click **Copy Message Text**.</span></span>  
  
5.  <span data-ttu-id="0bf73-145">**디버그** 메뉴에서 **디버깅 중지** 를 클릭하여 디자인 모드로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-145">Click **Stop Debugging** on the **Debug** menu to switch to the design mode.</span></span>  
  
6.  <span data-ttu-id="0bf73-146">피벗 변환을 마우스 오른쪽 단추로 클릭한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-146">Right-click the Pivot transformation, and then click **Edit**.</span></span>  
  
7.  <span data-ttu-id="0bf73-147">**일치하지 않는 피벗 키 값을 무시하고 DataFlow 실행 후 보고** 옵션을 선택 취소하고 다음 형식을 사용하여 **값에서 피벗 출력 열 생성** 상자에 피벗 키 값을 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-147">Uncheck the **Ignore un-matched Pivot Key values and report them after DataFlow execution** option, and then paste the pivot key values in the **Generate pivot output columns from values** box using the following format.</span></span>  
  
     <span data-ttu-id="0bf73-148">[value1],[value2],[value3]</span><span class="sxs-lookup"><span data-stu-id="0bf73-148">[value1],[value2],[value3]</span></span>  
  
 <span data-ttu-id="0bf73-149">**지금 열 생성**</span><span class="sxs-lookup"><span data-stu-id="0bf73-149">**Generate Columns Now**</span></span>  
 <span data-ttu-id="0bf73-150">**값에서 피벗 출력 열 생성** 상자에 나열된 각 피벗 키 값에 대해 출력 열을 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-150">Click to create an output column for each pivot key value that is listed in the **Generate pivot output columns from values** box.</span></span>  
  
 <span data-ttu-id="0bf73-151">출력 열이 **피벗된 기존 출력 열** 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-151">The output columns appear in the **Existing pivoted output columns** box.</span></span>  
  
 <span data-ttu-id="0bf73-152">**피벗된 기존 출력 열**</span><span class="sxs-lookup"><span data-stu-id="0bf73-152">**Existing pivoted output columns**</span></span>  
 <span data-ttu-id="0bf73-153">피벗 키 값에 대한 출력 열 나열</span><span class="sxs-lookup"><span data-stu-id="0bf73-153">Lists the output columns for the pivot key values</span></span>  
  
 <span data-ttu-id="0bf73-154">다음 표에서는 **Year** 열로 데이터가 피벗되기 전의 데이터 집합을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-154">The following table shows a data set before the data is pivoted on the **Year** column.</span></span>  
  
|<span data-ttu-id="0bf73-155">Year</span><span class="sxs-lookup"><span data-stu-id="0bf73-155">Year</span></span>|<span data-ttu-id="0bf73-156">제품 이름</span><span class="sxs-lookup"><span data-stu-id="0bf73-156">Product Name</span></span>|<span data-ttu-id="0bf73-157">합계</span><span class="sxs-lookup"><span data-stu-id="0bf73-157">Total</span></span>|  
|----------|------------------|-----------|  
|<span data-ttu-id="0bf73-158">2004</span><span class="sxs-lookup"><span data-stu-id="0bf73-158">2004</span></span>|<span data-ttu-id="0bf73-159">HL Mountain Tire</span><span class="sxs-lookup"><span data-stu-id="0bf73-159">HL Mountain Tire</span></span>|<span data-ttu-id="0bf73-160">1504884.15</span><span class="sxs-lookup"><span data-stu-id="0bf73-160">1504884.15</span></span>|  
|<span data-ttu-id="0bf73-161">2003</span><span class="sxs-lookup"><span data-stu-id="0bf73-161">2003</span></span>|<span data-ttu-id="0bf73-162">Road Tire Tube</span><span class="sxs-lookup"><span data-stu-id="0bf73-162">Road Tire Tube</span></span>|<span data-ttu-id="0bf73-163">35920.50</span><span class="sxs-lookup"><span data-stu-id="0bf73-163">35920.50</span></span>|  
|<span data-ttu-id="0bf73-164">2004</span><span class="sxs-lookup"><span data-stu-id="0bf73-164">2004</span></span>|<span data-ttu-id="0bf73-165">Water Bottle – 30 oz.</span><span class="sxs-lookup"><span data-stu-id="0bf73-165">Water Bottle - 30 oz.</span></span>|<span data-ttu-id="0bf73-166">2805.00</span><span class="sxs-lookup"><span data-stu-id="0bf73-166">2805.00</span></span>|  
|<span data-ttu-id="0bf73-167">2002</span><span class="sxs-lookup"><span data-stu-id="0bf73-167">2002</span></span>|<span data-ttu-id="0bf73-168">Touring Tire</span><span class="sxs-lookup"><span data-stu-id="0bf73-168">Touring Tire</span></span>|<span data-ttu-id="0bf73-169">62364.225</span><span class="sxs-lookup"><span data-stu-id="0bf73-169">62364.225</span></span>|  
  
 <span data-ttu-id="0bf73-170">다음 표에서는 **Year** 열로 데이터를 피벗한 후의 데이터 집합을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-170">The following table shows a data set after the data has been pivoted on the **Year** column.</span></span>  
  
||<span data-ttu-id="0bf73-171">2002</span><span class="sxs-lookup"><span data-stu-id="0bf73-171">2002</span></span>|<span data-ttu-id="0bf73-172">2003</span><span class="sxs-lookup"><span data-stu-id="0bf73-172">2003</span></span>|<span data-ttu-id="0bf73-173">2004</span><span class="sxs-lookup"><span data-stu-id="0bf73-173">2004</span></span>|  
|-|----------|----------|----------|  
|<span data-ttu-id="0bf73-174">HL Mountain Tire</span><span class="sxs-lookup"><span data-stu-id="0bf73-174">HL Mountain Tire</span></span>|<span data-ttu-id="0bf73-175">141164.10</span><span class="sxs-lookup"><span data-stu-id="0bf73-175">141164.10</span></span>|<span data-ttu-id="0bf73-176">446297.775</span><span class="sxs-lookup"><span data-stu-id="0bf73-176">446297.775</span></span>|<span data-ttu-id="0bf73-177">1504884.15</span><span class="sxs-lookup"><span data-stu-id="0bf73-177">1504884.15</span></span>|  
|<span data-ttu-id="0bf73-178">Road Tire Tube</span><span class="sxs-lookup"><span data-stu-id="0bf73-178">Road Tire Tube</span></span>|<span data-ttu-id="0bf73-179">3592.05</span><span class="sxs-lookup"><span data-stu-id="0bf73-179">3592.05</span></span>|<span data-ttu-id="0bf73-180">35920.50</span><span class="sxs-lookup"><span data-stu-id="0bf73-180">35920.50</span></span>|<span data-ttu-id="0bf73-181">89801.25</span><span class="sxs-lookup"><span data-stu-id="0bf73-181">89801.25</span></span>|  
|<span data-ttu-id="0bf73-182">Water Bottle – 30 oz.</span><span class="sxs-lookup"><span data-stu-id="0bf73-182">Water Bottle - 30 oz.</span></span>|<span data-ttu-id="0bf73-183">*NULL*</span><span class="sxs-lookup"><span data-stu-id="0bf73-183">*NULL*</span></span>|<span data-ttu-id="0bf73-184">*NULL*</span><span class="sxs-lookup"><span data-stu-id="0bf73-184">*NULL*</span></span>|<span data-ttu-id="0bf73-185">2805.00</span><span class="sxs-lookup"><span data-stu-id="0bf73-185">2805.00</span></span>|  
|<span data-ttu-id="0bf73-186">Touring Tire</span><span class="sxs-lookup"><span data-stu-id="0bf73-186">Touring Tire</span></span>|<span data-ttu-id="0bf73-187">62364.225</span><span class="sxs-lookup"><span data-stu-id="0bf73-187">62364.225</span></span>|<span data-ttu-id="0bf73-188">375051.60</span><span class="sxs-lookup"><span data-stu-id="0bf73-188">375051.60</span></span>|<span data-ttu-id="0bf73-189">1041810.00</span><span class="sxs-lookup"><span data-stu-id="0bf73-189">1041810.00</span></span>|  
  
 <span data-ttu-id="0bf73-190">**Year** 열로 데이터를 피벗하기 위해 아래 표시된 것처럼 다음과 같은 옵션이 **피벗** 대화 상자에 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-190">To pivot the data on the **Year** column, as shown above, the following options are set in the **Pivot** dialog box.</span></span>  
  
-   <span data-ttu-id="0bf73-191">**피벗 키** 목록 상자에는 Year가 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-191">Year is selected in the **Pivot Key** list box.</span></span>  
  
-   <span data-ttu-id="0bf73-192">**집합 키** 목록 상자에는 Product Name이 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-192">Product Name is selected in the **Set Key** list box.</span></span>  
  
-   <span data-ttu-id="0bf73-193">**피벗 값** 목록 상자에는 Total이 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-193">Total is selected in the **Pivot Value** list box.</span></span>  
  
-   <span data-ttu-id="0bf73-194">**값에서 피벗 출력 열 생성** 상자에는 다음 값이 입력되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-194">The following values are entered in the **Generate pivot output columns from values** box.</span></span>  
  
     <span data-ttu-id="0bf73-195">[2002],[2003],[2004]</span><span class="sxs-lookup"><span data-stu-id="0bf73-195">[2002],[2003],[2004]</span></span>  
  
## <a name="configuration-of-the-pivot-transformation"></a><span data-ttu-id="0bf73-196">피벗 변환 구성</span><span class="sxs-lookup"><span data-stu-id="0bf73-196">Configuration of the Pivot Transformation</span></span>  
 <span data-ttu-id="0bf73-197">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bf73-197">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="0bf73-198">**고급 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="0bf73-198">For more information about the properties that you can set in the **Advanced Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="0bf73-199">Common Properties</span><span class="sxs-lookup"><span data-stu-id="0bf73-199">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="0bf73-200">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="0bf73-200">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-content"></a><span data-ttu-id="0bf73-201">관련 내용</span><span class="sxs-lookup"><span data-stu-id="0bf73-201">Related Content</span></span>  
 <span data-ttu-id="0bf73-202">이 구성 요소의 속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](../set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0bf73-202">For information about how to set the properties of this component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bf73-203">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0bf73-203">See Also</span></span>  
 <span data-ttu-id="0bf73-204">[피벗 해제 변환](pivot-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="0bf73-204">[Unpivot Transformation](pivot-transformation.md) </span></span>  
 <span data-ttu-id="0bf73-205">[데이터 흐름](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="0bf73-205">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="0bf73-206">Integration Services 변환</span><span class="sxs-lookup"><span data-stu-id="0bf73-206">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
