---
title: 교차 유효성 검사 보고서 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- validating data mining models
- mining structures [Analysis Services], how-to topics
- cross-validation [data mining]
- statistical standard deviation
ms.assetid: 7b1fec4c-7053-41eb-b030-5179257967a4
author: minewiskan
ms.author: owend
ms.openlocfilehash: ccbafe63b0026cd45a15ea71fd84e223c1b32a9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727479"
---
# <a name="create-a-cross-validation-report"></a><span data-ttu-id="57300-102">교차 유효성 검사 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="57300-102">Create a Cross-Validation Report</span></span>
  <span data-ttu-id="57300-103">이 항목에서는 데이터 마이닝 디자이너에서 정확도 차트 탭을 사용하여 교차 유효성 검사 보고서를 만드는 단계를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-103">This topic walks you through creation of a cross-validation report using the Accuracy Chart tab in Data Mining Designer.</span></span> <span data-ttu-id="57300-104">교차 유효성 검사 보고서의 표시 형태 및 해당 보고서에 포함되는 통계 측정값에 대한 일반적인 내용은 [교차 유효성 검사&#40;Analysis Services - 데이터 마이닝&#41;](cross-validation-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57300-104">For general information about what a cross-validation report looks like, and the statistical measures it includes, see [Cross-Validation &#40;Analysis Services - Data Mining&#41;](cross-validation-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="57300-105">교차 유효성 검사 보고서는 리프트 차트 또는 분류 행렬과 같은 정확도 차트와 근본적으로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="57300-105">A cross-validation report is fundamentally different from an accuracy chart, such as a lift chart or classification matrix.</span></span>  
  
-   <span data-ttu-id="57300-106">교차 유효성 검사는 모델 또는 구조에 사용되는 데이터의 전체 분포를 평가하므로 테스트 데이터 집합을 지정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="57300-106">Cross-validation assesses the overall distribution of data that is used in a model or structure; therefore, you do not specify a testing data set.</span></span> <span data-ttu-id="57300-107">교차 유효성 검사에서는 항상 모델 또는 마이닝 구조를 학습하는 데 사용된 원본 데이터만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-107">Cross-validation always uses only the original data that was used to train the model or the mining structure.</span></span>  
  
-   <span data-ttu-id="57300-108">교차 유효성 검사는 단일 예측 가능한 결과를 기준으로만 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-108">Cross-validation can only be performed with respect to a single predictable outcome.</span></span> <span data-ttu-id="57300-109">구조가 예측 가능한 여러 특성이 있는 모델을 지원하는 경우 각각의 예측 가능한 출력에 대해 별도의 보고서를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-109">If the structure supports models that have different predictable attributes, you must create separate reports for each predictable output.</span></span>  
  
-   <span data-ttu-id="57300-110">현재 선택한 구조와 관련된 모델만 교차 유효성 검사에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-110">Only models that are related to the currently selected structure are available for cross-validation.</span></span>  
  
-   <span data-ttu-id="57300-111">현재 선택되어 있는 구조가 클러스터링 모델과 클러스터링 이외의 모델 조합을 지원하는 경우 **결과 가져오기**를 클릭하면 교차 유효성 검사 저장 프로시저가 자동으로 동일한 예측 가능한 열이 있는 모델은 로드하고 동일한 예측 가능한 특성을 공유하지 않는 클러스터링 모델은 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-111">If the structure that is currently selected supports a combination of clustering and non-clustering models, when you click **Get Results**, the cross-validation stored procedure will automatically load models that have the same predicted column, and ignore clustering models that do not share the same predictable attribute.</span></span>  
  
-   <span data-ttu-id="57300-112">마이닝 구조가 다른 예측 가능한 특성을 모두 지원하지 않는 경우에만 예측 가능한 특성이 없는 클러스터링 모델에 대한 교차 유효성 검사 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-112">You can create a cross-validation report on a clustering model that does not have a predictable attribute only if the mining structure does not support any other predictable attributes.</span></span>  
  
### <a name="select-a-mining-structure"></a><span data-ttu-id="57300-113">마이닝 구조 선택</span><span class="sxs-lookup"><span data-stu-id="57300-113">Select a mining structure</span></span>  
  
1.  <span data-ttu-id="57300-114">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 데이터 마이닝 디자이너를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="57300-114">Open the Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="57300-115">솔루션 탐색기에서 보고서를 만들려는 구조 또는 모델이 포함된 데이터베이스를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="57300-115">In Solution Explorer, open the database that contains the structure or model for which you want to create a report.</span></span>  
  
3.  <span data-ttu-id="57300-116">마이닝 구조를 두 번 클릭하여 데이터 마이닝 디자이너에서 구조 및 관련된 모델을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="57300-116">Double-click the mining structure to open the structure and its related models in Data Mining Designer.</span></span>  
  
4.  <span data-ttu-id="57300-117">**마이닝 정확도 차트** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-117">Click the **Mining Accuracy Chart** tab.</span></span>  
  
5.  <span data-ttu-id="57300-118">**교차 유효성 검사** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-118">Click the **Cross Validation** tab.</span></span>  
  
### <a name="set-cross-validation-options"></a><span data-ttu-id="57300-119">교차 유효성 검사 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="57300-119">Set cross-validation options</span></span>  
  
1.  <span data-ttu-id="57300-120">**교차 유효성 검사** 탭에서 **접기 개수**에 대해 아래쪽 화살표를 클릭하여 1에서 10 사이의 숫자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-120">On the **Cross Validation** tab, for **Fold Count**, click the down arrow to select a number between 1 and 10.</span></span> <span data-ttu-id="57300-121">기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="57300-121">The default value is 10.</span></span>  
  
     <span data-ttu-id="57300-122">**접기 개수** 는 원본 데이터 집합 내에 만들어지는 파티션의 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="57300-122">The **Fold Count** represents the number of partitions that will be created within the original data set.</span></span> <span data-ttu-id="57300-123">접기 개수를 1로 설정하면 분할 없이 학습 집합이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="57300-123">If you set Fold Count to 1, the training set will be used without partitioning.</span></span>  
  
2.  <span data-ttu-id="57300-124">**대상 특성**에서 아래쪽 화살표를 클릭하고 목록에서 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-124">For **Target Attribute**, click the down arrow, and select a column from the list.</span></span> <span data-ttu-id="57300-125">클러스터링 모델인 경우 **#Cluster** 를 선택하여 모델에 예측 가능한 특성이 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="57300-125">If the model is a clustering model, select **#Cluster** to indicate that the model does not have a predictable attribute.</span></span> <span data-ttu-id="57300-126">**#Cluster**값은 마이닝 구조가 다른 유형의 예측 가능한 특성을 지원하지 않는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-126">Note that the value, **#Cluster**, is available only when the mining structure does not support other types of predictable attributes.</span></span>  
  
     <span data-ttu-id="57300-127">보고서별로 예측 가능한 특성을 한 개만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-127">You can select only one predictable attribute per report.</span></span> <span data-ttu-id="57300-128">기본적으로 같은 예측 가능한 특성을 가진 모든 관련 모델이 보고서에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="57300-128">By default, all related models that have the same predictable attribute are included in the report.</span></span>  
  
3.  <span data-ttu-id="57300-129">**최대 사례**에서 데이터가 지정된 접기 수로 분할될 때 데이터를 대표하는 샘플을 제공할 수 있도록 충분히 큰 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-129">For **Max Cases**, type a number that is large enough to provide a representative sample of data when the data is split among the specified number of folds.</span></span> <span data-ttu-id="57300-130">이 수가 모델 학습 집합의 사례 수보다 많을 경우 모든 사례가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="57300-130">If the number is greater than the count of cases in the model training set, all cases will be used.</span></span>  
  
     <span data-ttu-id="57300-131">학습 데이터 집합이 매우 큰 경우 **최대 사례** 값을 설정하면 처리되는 사례의 수를 제한하여 보고서를 보다 신속하게 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-131">If the training data set is very large, setting the value for **Max Cases** limits the total number of cases processed, and lets the report finish faster.</span></span> <span data-ttu-id="57300-132">단, **최대 사례** 를 너무 낮게 설정하면 안 됩니다. 너무 낮을 경우 교차 유효성 검사를 위한 데이터가 부족하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57300-132">However, you should not set **Max Cases** too low or there may be insufficient data for cross-validation.</span></span>  
  
4.  <span data-ttu-id="57300-133">필요에 따라 **대상 상태**에 모델링하려는 예측 가능한 특성의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-133">Optionally, for **Target State**, type the value of the predictable attribute that you want to model.</span></span> <span data-ttu-id="57300-134">예를 들어 [Bike Buyer] 열에 가능한 값이 1(예)과 2(아니요) 두 개인 경우 값 1을 입력하여 원하는 결과에 대해서만 모델의 정확도를 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-134">For example, if the column [Bike Buyer] has two possible values, 1 (Yes) and 2 (No), you can enter the value 1 to assess the accuracy of the model for just the desired outcome.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="57300-135"> 값을 입력하지 않으면 **대상 임계값** 옵션을 사용할 수 없으며 모델은 예측 가능한 특성의 모든 가능한 값에 대해 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="57300-135">If you do not enter a value, the **Target Threshold** option is not available, and the model is assessed for all possible values of the predictable attribute.</span></span>  
  
5.  <span data-ttu-id="57300-136">필요에 따라 **대상 임계값**에 0에서 1 사이의 소수를 입력하여 예측이 정확한 것으로 계산되어야 하는 최소 확률을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-136">Optionally, for **Target Threshold**, type a decimal number between 0 and 1 to specify the minimum probability that a prediction must have to be counted as accurate.</span></span>  
  
     <span data-ttu-id="57300-137">확률 임계값을 설정하는 방법에 대한 추가 정보는 [교차 유효성 검사 보고서의 측정값](measures-in-the-cross-validation-report.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57300-137">For additional tips about how to set probability thresholds, see [Measures in the Cross-Validation Report](measures-in-the-cross-validation-report.md).</span></span>  
  
6.  <span data-ttu-id="57300-138">**결과 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-138">Click **Get Results**.</span></span>  
  
### <a name="print-the-cross-validation-report"></a><span data-ttu-id="57300-139">교차 유효성 검사 보고서 인쇄</span><span class="sxs-lookup"><span data-stu-id="57300-139">Print the cross-validation report</span></span>  
  
1.  <span data-ttu-id="57300-140">**교차 유효성 검사** 탭에서 완성된 보고서를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-140">Right-click the completed report on the **Cross Validation** tab.</span></span>  
  
2.  <span data-ttu-id="57300-141">바로 가기 메뉴에서 **인쇄** 를 선택하거나 **인쇄 미리 보기** 를 선택하여 먼저 보고서를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-141">In the shortcut menu, select **Print** or **Print Preview** to review the report first.</span></span>  
  
### <a name="create-a-copy-of-the-report-in-microsoft-excel"></a><span data-ttu-id="57300-142">Microsoft Excel에서 보고서 복사본 만들기</span><span class="sxs-lookup"><span data-stu-id="57300-142">Create a copy of the report in Microsoft Excel</span></span>  
  
1.  <span data-ttu-id="57300-143">**교차 유효성 검사** 탭에서 완성된 보고서를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-143">Right-click the completed report on the **Cross Validation** tab.</span></span>  
  
2.  <span data-ttu-id="57300-144">바로 가기 메뉴에서 **모두 선택**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-144">In the shortcut menu, select **Select All**.</span></span>  
  
3.  <span data-ttu-id="57300-145">선택한 텍스트를 마우스 오른쪽 단추로 클릭한 다음 **복사**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-145">Right-click the selected text, and select **Copy**.</span></span>  
  
4.  <span data-ttu-id="57300-146">열어 놓은 Excel 통합 문서에 선택한 부분을 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-146">Paste the selection into an open Excel workbook.</span></span> <span data-ttu-id="57300-147">**붙여넣기** 옵션을 사용하면 보고서가 HTML로 Excel에 붙여넣어지며 행과 열 서식이 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="57300-147">If you use the **Paste** option, the report is pasted into Excel as HTML, which preserves row and column formatting.</span></span> <span data-ttu-id="57300-148">텍스트 또는 유니코드 텍스트에 대해 **선택하여 붙여넣기** 옵션을 사용하여 보고서를 붙여넣으면 보고서는 행으로 구분된 형식으로 붙여넣어집니다.</span><span class="sxs-lookup"><span data-stu-id="57300-148">If you paste the report by using the **Paste Special** options for text or Unicode text, the report is pasted in row-delimited format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57300-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="57300-149">See Also</span></span>  
 [<span data-ttu-id="57300-150">교차 유효성 검사 보고서의 측정값</span><span class="sxs-lookup"><span data-stu-id="57300-150">Measures in the Cross-Validation Report</span></span>](measures-in-the-cross-validation-report.md)  
  
  
