---
title: 예측 만들기 (기본 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a8410ed2-bb98-4d51-a9eb-b239be1201c2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 456aec6c6b9d0d1a5d0ee1d9949507a37577130c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727524"
---
# <a name="creating-predictions-basic-data-mining-tutorial"></a><span data-ttu-id="57a77-102">예측 만들기(기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="57a77-102">Creating Predictions (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="57a77-103">마이닝 모델의 정확도를 테스트 하 고 결과에 만족 했다면 데이터 마이닝 디자이너의 **마이닝 모델 예측** 탭에서 예측 쿼리 작성기를 사용 하 여 예측을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-103">After you have tested the accuracy of your mining models and decided that you are satisfied with the results, you can then generate predictions by using the Prediction Query Builder on the **Mining Model Prediction** tab in the Data Mining Designer.</span></span>  
  
 <span data-ttu-id="57a77-104">예측 쿼리 작성기에는 세 가지 뷰가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-104">The Prediction Query Builder has three views.</span></span> <span data-ttu-id="57a77-105">**디자인** 뷰와 **쿼리** 뷰를 사용 하 여 쿼리를 작성 하 고 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-105">With the **Design** and **Query** views, you can build and examine your query.</span></span> <span data-ttu-id="57a77-106">그런 다음 쿼리를 실행 하 고 **결과 뷰에서 결과를 볼 수** 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-106">You can then run the query and view the results in the **Result** view.</span></span>  
  
 <span data-ttu-id="57a77-107">모든 예측 쿼리는 DMX(Data Mining Extensions) 언어를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-107">All prediction queries use DMX, which is short for the Data Mining Extensions (DMX) language.</span></span> <span data-ttu-id="57a77-108">DMX의 구문은 T-SQL의 구문과 비슷하지만 데이터 마이닝 개체에 대한 쿼리에 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-108">DMX has syntax like that of T-SQL but is used for queries against data mining objects.</span></span> <span data-ttu-id="57a77-109">DMX 구문이 복잡 하지는 않지만 이와 같은 쿼리 작성기를 사용 하거나 [Office 용 SQL Server 데이터 마이닝 추가 기능](../../2014/analysis-services/data-mining/sql-server-data-mining-add-ins-for-office.md)을 사용 하면 더 쉽게 입력을 선택 하 고 식을 작성할 수 있으므로 기본 사항을 배우는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-109">Although DMX syntax is not complicated, using a query builder like this one, or the one in the [SQL Server Data Mining Add-Ins for Office](../../2014/analysis-services/data-mining/sql-server-data-mining-add-ins-for-office.md), makes it much easier to select inputs and build expressions, so we highly recommend that you learn the basics.</span></span>  
  
## <a name="creating-the-query"></a><span data-ttu-id="57a77-110">쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="57a77-110">Creating the Query</span></span>  
 <span data-ttu-id="57a77-111">예측 쿼리를 만드는 첫 번째 단계는 마이닝 모델과 입력 테이블을 선택하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-111">The first step in creating a prediction query is to select a mining model and input table.</span></span>  
  
#### <a name="to-select-a-model-and-input-table"></a><span data-ttu-id="57a77-112">모델과 입력 테이블을 선택하려면</span><span class="sxs-lookup"><span data-stu-id="57a77-112">To select a model and input table</span></span>  
  
1.  <span data-ttu-id="57a77-113">데이터 마이닝 디자이너의 **마이닝 모델 예측** 탭에 있는 **마이닝 모델** 상자에서 **모델 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-113">On the **Mining Model Prediction** tab of Data Mining Designer, in the **Mining Model** box, click **Select Model**.</span></span>  
  
2.  <span data-ttu-id="57a77-114">**마이닝 모델 선택** 대화 상자에서 **대상 메일링** 구조로 트리를 탐색 하 고 구조를 확장 한 `TM_Decision_Tree` 다음를 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-114">In the **Select Mining Model** dialog box, navigate through the tree to the **Targeted Mailing** structure, expand the structure, select `TM_Decision_Tree`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="57a77-115">**입력 테이블 선택** 상자에서 **사례 테이블 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-115">In the **Select Input Table(s)** box, click **Select Case Table**.</span></span>  
  
4.  <span data-ttu-id="57a77-116">**테이블 선택** 대화 상자의 **데이터 원본** 목록에서 데이터 원본 뷰를 선택 합니다 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="57a77-116">In the **Select Table** dialog box, in the **Data Source** list, select the data source view [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span>  
  
5.  <span data-ttu-id="57a77-117">**테이블/뷰 이름**에서 **ProspectiveBuyer (dbo)** 테이블을 선택한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-117">In **Table/View Name**, select the **ProspectiveBuyer (dbo)** table, and then click **OK**.</span></span>  
  
     <span data-ttu-id="57a77-118">`ProspectiveBuyer`테이블은 **Vtargetmail** 사례 테이블과 가장 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-118">The `ProspectiveBuyer` table most closely resembles the **vTargetMail** case table.</span></span>  
  
## <a name="mapping-the-columns"></a><span data-ttu-id="57a77-119">열 매핑</span><span class="sxs-lookup"><span data-stu-id="57a77-119">Mapping the Columns</span></span>  
 <span data-ttu-id="57a77-120">입력 테이블을 선택하면 열 이름을 기반으로 마이닝 모델과 입력 테이블 간에 기본 매핑이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-120">After you select the input table, Prediction Query Builder creates a default mapping between the mining model and the input table, based on the names of the columns.</span></span> <span data-ttu-id="57a77-121">구조의 열 중 적어도 하나 이상의 열이 외부 데이터의 열과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-121">At least one column from the structure must match a column in the external data.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="57a77-122">모델의 정확도를 결정하는 데 사용하는 데이터에는 예측 가능한 열에 매핑될 수 있는 열이 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-122">The data that you use to determine the accuracy of the models must contain a column that can be mapped to the predictable column.</span></span> <span data-ttu-id="57a77-123">이러한 열이 존재하지 않는 경우 빈 값으로 열을 만들 수 있지만 이 열은 예측 가능한 열과 동일한 데이터 형식을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-123">If such a column does not exist, you can create one with empty values, but it must have the same data type as the predictable column.</span></span>  
  
#### <a name="to-map-the-inputs-to-the-model"></a><span data-ttu-id="57a77-124">입력을 모델에 매핑하려면</span><span class="sxs-lookup"><span data-stu-id="57a77-124">To map the inputs to the model</span></span>  
  
1.  <span data-ttu-id="57a77-125">**입력 테이블 선택** 창에 **마이닝 모델** 창을 연결 하는 선을 마우스 오른쪽 단추로 클릭 하 고 **연결 수정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-125">Right-click the lines connecting the **Mining Model** window to the **Select Input Table** window, and select **Modify Connections**.</span></span>  
  
     <span data-ttu-id="57a77-126">모든 열이 매핑되지는 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-126">Notice that not every column is mapped.</span></span> <span data-ttu-id="57a77-127">여러 **테이블 열**에 대 한 매핑을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-127">We will add mappings for several **Table Columns**.</span></span> <span data-ttu-id="57a77-128">또한 열이 더 잘 일치하도록 현재 날짜 열을 기반으로 새 생년월일 열을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-128">We will also generate a new birth date column based on the current date column, so that the columns match better.</span></span>  
  
2.  <span data-ttu-id="57a77-129">**테이블 열**아래에서 셀을 클릭 `Bike Buyer` 하 고 드롭다운에서 ProspectiveBuyer를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-129">Under **Table Column**, click the `Bike Buyer` cell and select ProspectiveBuyer.Unknown from the dropdown.</span></span>  
  
     <span data-ttu-id="57a77-130">이는 예측 가능한 열인 [Bike Buyer]를 입력 테이블 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-130">This maps the predictable column, [Bike Buyer], to an input table column.</span></span>  
  
3.  <span data-ttu-id="57a77-131">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-131">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="57a77-132">**솔루션 탐색기**에서 **대상 메일링** 데이터 원본 뷰를 마우스 오른쪽 단추로 클릭 하 고 **디자이너 보기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-132">In **Solution Explorer**, right-click the **Targeted Mailing** data source view and select **View Designer**.</span></span>  
  
5.  <span data-ttu-id="57a77-133">ProspectiveBuyer 테이블을 마우스 오른쪽 단추로 클릭 하 고 **새 명명 된 계산**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-133">Right-click the table, ProspectiveBuyer, and select **New Named Calculation**.</span></span>  
  
6.  <span data-ttu-id="57a77-134">**명명 된 계산 만들기** 대화 상자에서 **열 이름**에을 입력 `calcAge` 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-134">In the **Create Named Calculation** dialog box, for **Column name**, type `calcAge`.</span></span>  
  
7.  <span data-ttu-id="57a77-135">**설명**에 대해 **생년월일 기반 Calculate age**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-135">For **Description**, type **Calculate age based on birthdate**.</span></span>  
  
8.  <span data-ttu-id="57a77-136">**식** 상자에를 입력 한 `DATEDIFF(YYYY,[BirthDate],getdate())` 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-136">In the **Expression** box, type `DATEDIFF(YYYY,[BirthDate],getdate())` and then click **OK**.</span></span>  
  
     <span data-ttu-id="57a77-137">입력 테이블에 모델의 열에 해당 하는 **age** 열이 없기 때문에이 식을 사용 하 여 입력 테이블의 생년월일 열에서 고객 나이를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-137">Because the input table has no **Age** column corresponding to the one in the model, you can use this expression to calculate customer age from the BirthDate column in the input table.</span></span> <span data-ttu-id="57a77-138">**Age** 는 자전거 구매 예측에 가장 영향력 있는 열로 식별 되었으므로 모델과 입력 테이블에 모두 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-138">Since **Age** was identified as the most influential column for predicting bike buying, it must exist in both the model and in the input table.</span></span>  
  
9. <span data-ttu-id="57a77-139">데이터 마이닝 디자이너에서 **마이닝 모델 예측** 탭을 선택 하 고 **연결 수정** 창을 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-139">In Data Mining Designer, select the **Mining Model Prediction** tab and re-open the **Modify Connections** window.</span></span>  
  
10. <span data-ttu-id="57a77-140">**테이블 열**아래에서 **Age** 셀을 클릭 하 고 드롭다운에서 ProspectiveBuyer를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-140">Under **Table Column**, click the **Age** cell and select ProspectiveBuyer.calcAge from the dropdown.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="57a77-141">목록에 열이 표시되지 않는 경우 디자이너에 로드되는 데이터 원본 뷰의 정의를 새로 고쳐야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-141">If you do not see the column in the list, you might have to refresh the definition of the data source view that is loaded in the designer.</span></span> <span data-ttu-id="57a77-142">이렇게 하려면 **파일** 메뉴에서 **모두 저장**을 선택 하 고 디자이너에서 프로젝트를 닫았다가 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-142">To do this, from the **File** menu, select **Save all**, and then close and re-open the project in the designer.</span></span>  
  
11. <span data-ttu-id="57a77-143">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-143">Click **OK**.</span></span>  
  
## <a name="designing-the-prediction-query"></a><span data-ttu-id="57a77-144">예측 쿼리 디자인</span><span class="sxs-lookup"><span data-stu-id="57a77-144">Designing the Prediction Query</span></span>  
  
1.  <span data-ttu-id="57a77-145">**마이닝 모델 예측** 탭의 도구 모음에 있는 첫 번째 단추는 **디자인 뷰로 전환/결과 뷰로 전환/쿼리 뷰로** 전환 단추로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-145">The first button on the toolbar of the **Mining Model Prediction** tab is the **Switch to design view / Switch to result view / Switch to query view** button.</span></span> <span data-ttu-id="57a77-146">이 단추에서 아래쪽 화살표를 클릭 하 고 **디자인**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-146">Click the down arrow on this button, and select **Design**.</span></span>  
  
2.  <span data-ttu-id="57a77-147">**마이닝 모델 예측** 탭의 표에 있는 **원본** 열에서 첫 번째 빈 행의 셀을 클릭 한 다음 **예측 함수**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-147">In the grid on the **Mining Model Prediction** tab, click the cell in the first empty row in the **Source** column, and then select **Prediction Function**.</span></span>  
  
3.  <span data-ttu-id="57a77-148">**예측 함수** 행의 **필드** 열에서을 선택 `PredictProbability` 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-148">In the **Prediction Function** row, in the **Field** column, select `PredictProbability`.</span></span>  
  
     <span data-ttu-id="57a77-149">동일한 행의 **별칭** 열에 **결과의 확률**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-149">In the **Alias** column of the same row, type **Probability of result**.</span></span>  
  
4.  <span data-ttu-id="57a77-150">위의 **마이닝 모델** 창에서 [자전거 구매자]를 선택 하 고 **조건/인수** 셀로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-150">From the **Mining Model** window above, select and drag [Bike Buyer] into the **Criteria/Argument** cell.</span></span>  
  
     <span data-ttu-id="57a77-151">[TM_Decision_Tree]를 사용할 수 있습니다. [자전거 구매자]는 **조건/인수** 셀에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-151">When you let go, [TM_Decision_Tree].[Bike Buyer] appears in the **Criteria/Argument** cell.</span></span>  
  
     <span data-ttu-id="57a77-152">이렇게 하면 `PredictProbability` 함수의 대상 열이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-152">This specifies the target column for the `PredictProbability` function.</span></span> <span data-ttu-id="57a77-153">함수에 대 한 자세한 내용은 [데이터 마이닝 확장 &#40;DMX&#41; 함수 참조](/sql/dmx/data-mining-extensions-dmx-function-reference)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="57a77-153">For more information about functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
5.  <span data-ttu-id="57a77-154">**원본** 열에서 다음 빈 행을 클릭 한 다음 마이닝 모델 **TM_Decision_Tree** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-154">Click the next empty row in the **Source** column, and then select **TM_Decision_Tree** mining model.</span></span>  
  
6.  <span data-ttu-id="57a77-155">행의 `TM_Decision_Tree` **필드** 열에서을 선택 `Bike Buyer` 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-155">In the `TM_Decision_Tree` row, in the **Field** column, select `Bike Buyer`.</span></span>  
  
7.  <span data-ttu-id="57a77-156">행의 `TM_Decision_Tree` **조건/인수** 열에을 입력 `=1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-156">In the `TM_Decision_Tree` row, in the **Criteria/Argument** column, type `=1`.</span></span>  
  
8.  <span data-ttu-id="57a77-157">**원본** 열에서 다음 빈 행을 클릭 한 다음 **ProspectiveBuyer 테이블**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-157">Click the next empty row in the **Source** column, and then select **ProspectiveBuyer table**.</span></span>  
  
9. <span data-ttu-id="57a77-158">행의 `ProspectiveBuyer` **필드** 열에서 **ProspectiveBuyerKey**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-158">In the `ProspectiveBuyer` row, in the **Field** column, select **ProspectiveBuyerKey**.</span></span>  
  
     <span data-ttu-id="57a77-159">이렇게 하면 자전거 구매 가능성이 있는 고객과 구매 가능성이 없는 고객을 식별할 수 있도록 예측 쿼리에 고유 식별자가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-159">This adds the unique identifier to the prediction query so that you can identify who is and who is not likely to buy a bicycle.</span></span>  
  
10. <span data-ttu-id="57a77-160">표에 5개의 행을 더 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-160">Add five more rows to the grid.</span></span> <span data-ttu-id="57a77-161">각 행에 대해 **ProspectiveBuyer table** 을 **원본** 으로 선택 하 고 **필드** 셀에 다음 열을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-161">For each row, select **ProspectiveBuyer table** as the **Source** and then add the following columns in the **Field** cells:</span></span>  
  
    -   <span data-ttu-id="57a77-162">calcAge</span><span class="sxs-lookup"><span data-stu-id="57a77-162">calcAge</span></span>  
  
    -   <span data-ttu-id="57a77-163">LastName</span><span class="sxs-lookup"><span data-stu-id="57a77-163">LastName</span></span>  
  
    -   <span data-ttu-id="57a77-164">FirstName</span><span class="sxs-lookup"><span data-stu-id="57a77-164">FirstName</span></span>  
  
    -   <span data-ttu-id="57a77-165">AddressLine1</span><span class="sxs-lookup"><span data-stu-id="57a77-165">AddressLine1</span></span>  
  
    -   <span data-ttu-id="57a77-166">AddressLine2</span><span class="sxs-lookup"><span data-stu-id="57a77-166">AddressLine2</span></span>  
  
 <span data-ttu-id="57a77-167">마지막으로 쿼리를 실행하고 결과를 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-167">Finally, run the query and browse the results.</span></span>  
  
 <span data-ttu-id="57a77-168">**예측 쿼리 작성기** 에도 다음 컨트롤이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-168">The **Prediction Query Builder** also includes these controls:</span></span>  
  
-   <span data-ttu-id="57a77-169">**표시** 확인란</span><span class="sxs-lookup"><span data-stu-id="57a77-169">**Show** check box</span></span>  
  
     <span data-ttu-id="57a77-170">디자이너에서 삭제할 필요 없이 쿼리에서 절을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-170">Lets you remove clauses from the query without having to delete them from the designer.</span></span> <span data-ttu-id="57a77-171">이 확인란은 복잡한 쿼리로 작업할 때 DMX를 복사하여 창에 붙여 넣을 필요 없이 구문을 보존하려는 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-171">This can be useful when you are working with complex queries and want to preserve syntax without having to copy and paste DMX into the window.</span></span>  
  
-   <span data-ttu-id="57a77-172">**그룹**</span><span class="sxs-lookup"><span data-stu-id="57a77-172">**Group**</span></span>  
  
     <span data-ttu-id="57a77-173">선택한 줄의 시작 부분에 여는(왼쪽) 괄호를 삽입하거나 현재 줄의 끝에 닫는(오른쪽) 괄호를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-173">Inserts an opening (left) parentheses at the beginning of the selected line, or inserts a closing (right) parenthesis at the end of the current line.</span></span>  
  
-   <span data-ttu-id="57a77-174">**및/또는**</span><span class="sxs-lookup"><span data-stu-id="57a77-174">**AND/OR**</span></span>  
  
     <span data-ttu-id="57a77-175">현재 함수나 열 바로 뒤에 `AND` 연산자 또는 `OR` 연산자를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-175">Inserts the  `AND` operator or the `OR` operator immediately after the current function or column.</span></span>  
  
#### <a name="to-run-the-query-and-view-results"></a><span data-ttu-id="57a77-176">쿼리를 실행하고 결과를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="57a77-176">To run the query and view results</span></span>  
  
1.  <span data-ttu-id="57a77-177">**마이닝 모델 예측** 탭에서 **결과** 단추를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-177">In the **Mining Model Prediction** tab, select the **Result** button.</span></span>  
  
2.  <span data-ttu-id="57a77-178">쿼리가 실행되고 결과가 표시되면 해당 결과를 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-178">After the query runs and the results are displayed, you can review the results.</span></span>  
  
     <span data-ttu-id="57a77-179">**마이닝 모델 예측** 탭은 자전거 구매자 일 가능성이 있는 잠재 고객에 대 한 연락처 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-179">The **Mining Model Prediction** tab displays contact information for potential customers who are likely to be bike buyers.</span></span> <span data-ttu-id="57a77-180">**결과 열 확률** 은 예측이 올바른지 확률을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-180">The **Probability of result** column indicates the probability of the prediction being correct.</span></span> <span data-ttu-id="57a77-181">이러한 결과를 사용하여 메일 대상으로 삼을 잠재 고객을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-181">You can use these results to determine which potential customers to target for the mailing.</span></span>  
  
3.  <span data-ttu-id="57a77-182">이때 결과를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-182">At this point, you can save the results.</span></span> <span data-ttu-id="57a77-183">세 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-183">You have three options:</span></span>  
  
    -   <span data-ttu-id="57a77-184">결과에서 데이터 행을 마우스 오른쪽 단추로 클릭 하 고 **복사** 를 선택 하 여 해당 값 (및 열 머리글만)만 클립보드에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-184">Right-click a row of data in the results, and select **Copy** to save just that value (and the column heading) to the Clipboard.</span></span>  
  
    -   <span data-ttu-id="57a77-185">결과에서 행을 마우스 오른쪽 단추로 클릭 하 고 **모두 복사** 를 선택 하 여 열 머리글을 포함 한 전체 결과 집합을 클립보드에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-185">Right-click any row in the results, and select **Copy All** to copy the entire result set, including column headings, to the Clipboard.</span></span>  
  
    -   <span data-ttu-id="57a77-186">다음과 같이 **쿼리 결과 저장** 을 클릭 하 여 결과를 데이터베이스에 직접 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-186">Click **Save query result** to save the results directly to a database as follows:</span></span>  
  
        1.  <span data-ttu-id="57a77-187">**데이터 마이닝 쿼리 결과 저장** 대화 상자에서 데이터 원본을 선택 하거나 새 데이터 원본을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-187">In the **Save Data Mining Query Result** dialog box, select a data source, or define a new data source.</span></span>  
  
        2.  <span data-ttu-id="57a77-188">쿼리 결과를 포함할 테이블의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-188">Type a name for the table that will contain the query results.</span></span>  
  
        3.  <span data-ttu-id="57a77-189">**DSV에 추가**옵션을 사용 하 여 테이블을 만들고 기존 데이터 원본 뷰에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-189">Use the option, **Add to DSV**, to create the table and add it to an existing data source view.</span></span> <span data-ttu-id="57a77-190">이는 학습 데이터, 예측 원본 데이터 및 쿼리 결과와 같은 모델에 대 한 모든 관련 테이블을 동일한 데이터 원본 뷰에 유지 하려는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-190">This is useful if you want to keep all related tables for a model-such as training data, prediction source data, and query results-in the same data source view.</span></span>  
  
        4.  <span data-ttu-id="57a77-191">기존 테이블을 최신 결과로 업데이트 하려면 ( **있는 경우 덮어쓰기**) 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-191">Use the option, **Overwrite if exists**, to update an existing table with the latest results.</span></span>  
  
             <span data-ttu-id="57a77-192">예측 쿼리에 열을 추가한 경우, 예측 쿼리에서 열의 이름 또는 데이터 형식을 변경한 경우, 대상 테이블에서 ALTER 문을 실행한 경우 테이블을 덮어 쓰려면 이 옵션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-192">You must use the option to overwrite the table if you have added any columns to the prediction query, changed the names or data types of any columns in the prediction query, or if you have run any ALTER statements on the destination table.</span></span>  
  
             <span data-ttu-id="57a77-193">또한 여러 열의 이름이 동일한 경우 (예: 기본 열 이름 **식**) 중복 된 이름의 열에 대해 별칭을 만들어야 합니다. 그렇지 않으면 디자이너가 결과를 SQL Server에 저장 하려고 할 때 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-193">Also, if multiple columns have the same name (for example, the default column name **Expression**) you must create an alias for the columns with duplicate names, or an error will be raised when the designer tries to save the results to SQL Server.</span></span> <span data-ttu-id="57a77-194">그 이유는 SQL Server가 여러 열에서 동일한 이름을 갖도록 허용하지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="57a77-194">The reason is that SQL Server does not allow multiple columns to have the same name.</span></span>  
  
             <span data-ttu-id="57a77-195">자세한 내용은 [마이닝 모델 예측 뷰&#41;&#40;데이터 마이닝 쿼리 결과 저장 대화 상자 ](../../2014/analysis-services/save-data-mining-query-result-dialog-box-mining-model-prediction-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="57a77-195">For more information, see [Save Data Mining Query Result Dialog Box &#40;Mining Model Prediction View&#41;](../../2014/analysis-services/save-data-mining-query-result-dialog-box-mining-model-prediction-view.md).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="57a77-196">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="57a77-196">Next Task in Lesson</span></span>  
 [<span data-ttu-id="57a77-197">구조 데이터에 드릴스루 사용 &#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="57a77-197">Using Drillthrough on Structure Data &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/using-drillthrough-on-structure-data-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="57a77-198">참고 항목</span><span class="sxs-lookup"><span data-stu-id="57a77-198">See Also</span></span>  
 [<span data-ttu-id="57a77-199">예측 쿼리 작성기를 사용하여 예측 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="57a77-199">Create a Prediction Query Using the Prediction Query Builder</span></span>](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
