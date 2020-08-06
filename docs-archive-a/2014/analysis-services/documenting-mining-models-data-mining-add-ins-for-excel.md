---
title: 마이닝 모델 문서화 (Excel 용 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- documenting models
- mining structures, managing
- mining models, managing
- model properties
ms.assetid: 0a663e11-e40c-4708-ad18-fabb6c976fa4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 00d84f7ff1dc27d19d497dd11315d3efde603f60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659717"
---
# <a name="documenting-mining-models-data-mining-add-ins-for-excel"></a><span data-ttu-id="e0a18-102">마이닝 모델 문서화(Excel용 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="e0a18-102">Documenting Mining Models (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="e0a18-103">![데이터 마이닝 리본, 모델 문서화 단추](media/dmc-docmodel.gif "데이터 마이닝 리본, 모델 문서화 단추")</span><span class="sxs-lookup"><span data-stu-id="e0a18-103">![Document Model button, Data Mining ribbon](media/dmc-docmodel.gif "Document Model button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="e0a18-104">**모델 문서화** 마법사는 사용자가 만든 마이닝 모델에 대 한 유용한 정보를 제공 하는 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-104">The **Document Model** wizard creates a report that provides useful information about the mining models that you have created.</span></span> <span data-ttu-id="e0a18-105">만드는 모델을 문서화하면 모델을 생성하는 데 사용한 데이터 원본을 추적하고, 모델이 처리된 시점에 대한 추가 정보를 가져오고, 모델의 결과에 영향을 주는 매개 변수 변경을 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-105">By documenting the models that you create, you can track the source of the data used to generate a model, get additional information about when the model was processed, and track parameter changes that affect the results of the model.</span></span>  
  
## <a name="using-the-document-model-wizard"></a><span data-ttu-id="e0a18-106">모델 문서화 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="e0a18-106">Using the Document Model Wizard</span></span>  
  
1.  <span data-ttu-id="e0a18-107">**데이터 마이닝** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-107">Click the **Data Mining** tab.</span></span>  
  
2.  <span data-ttu-id="e0a18-108">**모델 사용** 그룹에서 **모델 문서화**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-108">In the **Model Usage** group, click **Document Model**.</span></span>  
  
3.  <span data-ttu-id="e0a18-109">**모델 선택** 대화 상자에서 보고할 모델을 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-109">In the **Select Model** dialog box, select the model on which to report, and then click **Next**.</span></span> <span data-ttu-id="e0a18-110">문서화 하려는 각 모델에 대해 **모델 문서화** 마법사를 별도로 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-110">You must run the **Document Model** wizard separately for each model that you want to document.</span></span>  
  
4.  <span data-ttu-id="e0a18-111">**문서 세부 정보 선택** 대화 상자에서 다음 두 가지 옵션 중 하나를 선택 합니다. **전체 정보** 또는 **요약 정보**</span><span class="sxs-lookup"><span data-stu-id="e0a18-111">In the **Select documentation details** dialog box, choose one of two options: **Complete information** or **Summary information**.</span></span>  
  
5.  <span data-ttu-id="e0a18-112">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-112">Click **Finish**.</span></span>  
  
6.  <span data-ttu-id="e0a18-113">마법사가 지정 된 보고서 ( **모델 설명서**)를 포함 하는 새 워크시트를 자동으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-113">The wizard automatically creates a new worksheet that contains the specified report, titled **Model Documentation**,</span></span>  
  
## <a name="understanding-the-report"></a><span data-ttu-id="e0a18-114">보고서 이해</span><span class="sxs-lookup"><span data-stu-id="e0a18-114">Understanding the Report</span></span>  
 <span data-ttu-id="e0a18-115">데이터 마이닝 모델을 문서화하는 보고서를 만들 때 모델의 이름 및 설명 등의 기본 정보가 포함된 요약 보고서를 만들거나 마이닝 모델의 기본 구조 및 고급 정보에 대한 세부 사항이 포함된 전체 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-115">When you create a report that documents a data mining model, you can create a summary,which contains basic information containing the name and description of the model, or a complete report, which contains details about the underlying structure and advanced information about the mining model.</span></span>  
  
 <span data-ttu-id="e0a18-116">모델을 만드는 데 사용한 알고리즘에 따라 다른 유형의 정보가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-116">Depending on the algorithm that was used to create the model, different types of information is provided.</span></span> <span data-ttu-id="e0a18-117">예를 들어 연결 모델에서는 생성된 항목 집합 및 규칙의 수를 확인하는 것이 중요하고,</span><span class="sxs-lookup"><span data-stu-id="e0a18-117">For example, in an association model, you are more interested in knowing the number of itemsets and rules that were generated.</span></span> <span data-ttu-id="e0a18-118">클러스터링 모델에서는 클러스터의 수가 더 중요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-118">For a clustering model, the number of clusters is more interesting.</span></span>  
  
 <span data-ttu-id="e0a18-119">다음 표에서는 각 옵션의 보고서에서 제공되는 옵션 및 정보를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-119">The following table lists the options and the information that is provided in the report for each option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e0a18-120">보고서의 열은 기본적으로 특정 크기로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-120">The columns in the report are set to a particular size by default.</span></span> <span data-ttu-id="e0a18-121">따라서 열 이름 또는 값이 매우 길면 Excel에 표시되지 않거나 ###으로 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-121">Therefore, if any columns names or values are very long, they might not be visible, or might appear as ### in Excel.</span></span> <span data-ttu-id="e0a18-122">행의 크기를 조정하여 값을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-122">To make the values visible, you can resize the row.</span></span> <span data-ttu-id="e0a18-123">셀을 선택한 다음 수식 입력줄의 오른쪽 끝에서 이중 화살표를 클릭한 상태로 끌어 전체 값 또는 문자열을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-123">If the cell is selected, you can click and drag the double arrows at the right end of the formula bar to show the complete value or string.</span></span>  
  
### <a name="summary-report"></a><span data-ttu-id="e0a18-124">요약 보고서</span><span class="sxs-lookup"><span data-stu-id="e0a18-124">Summary Report</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="e0a18-125">**메타데이터**</span><span class="sxs-lookup"><span data-stu-id="e0a18-125">**Metadata**</span></span>|<span data-ttu-id="e0a18-126">모델 이름</span><span class="sxs-lookup"><span data-stu-id="e0a18-126">Model name</span></span><br /><br /> <span data-ttu-id="e0a18-127">모델 설명</span><span class="sxs-lookup"><span data-stu-id="e0a18-127">Model description</span></span><br /><br /> <span data-ttu-id="e0a18-128">알고리즘 이름</span><span class="sxs-lookup"><span data-stu-id="e0a18-128">Algorithm name</span></span><br /><br /> <span data-ttu-id="e0a18-129">마지막 처리 날짜</span><span class="sxs-lookup"><span data-stu-id="e0a18-129">Date last processed</span></span>||  
|<span data-ttu-id="e0a18-130">**모델 결과**</span><span class="sxs-lookup"><span data-stu-id="e0a18-130">**Model results**</span></span>|<span data-ttu-id="e0a18-131">연결</span><span class="sxs-lookup"><span data-stu-id="e0a18-131">Association</span></span>|<span data-ttu-id="e0a18-132">항목 집합 수</span><span class="sxs-lookup"><span data-stu-id="e0a18-132">Count of itemsets</span></span><br /><br /> <span data-ttu-id="e0a18-133">규칙 수</span><span class="sxs-lookup"><span data-stu-id="e0a18-133">Count of rules</span></span>|  
||<span data-ttu-id="e0a18-134">Clustering</span><span class="sxs-lookup"><span data-stu-id="e0a18-134">Clustering</span></span>|<span data-ttu-id="e0a18-135">클러스터 수</span><span class="sxs-lookup"><span data-stu-id="e0a18-135">Count of clusters</span></span><br /><br /> <span data-ttu-id="e0a18-136">각 클러스터 지원</span><span class="sxs-lookup"><span data-stu-id="e0a18-136">Support for each cluster</span></span>|  
||<span data-ttu-id="e0a18-137">의사 결정 트리</span><span class="sxs-lookup"><span data-stu-id="e0a18-137">Decision tree</span></span>|<span data-ttu-id="e0a18-138">트리 수</span><span class="sxs-lookup"><span data-stu-id="e0a18-138">Number of trees</span></span><br /><br /> <span data-ttu-id="e0a18-139">각 트리의 노드 수</span><span class="sxs-lookup"><span data-stu-id="e0a18-139">Number of nodes in each tree</span></span>|  
||<span data-ttu-id="e0a18-140">선형 회귀</span><span class="sxs-lookup"><span data-stu-id="e0a18-140">Linear regression</span></span>|<span data-ttu-id="e0a18-141">트리 수(항상 1)</span><span class="sxs-lookup"><span data-stu-id="e0a18-141">Number of trees (always 1)</span></span><br /><br /> <span data-ttu-id="e0a18-142">노드 수(항상 1)</span><span class="sxs-lookup"><span data-stu-id="e0a18-142">Number of nodes (always 1)</span></span>|  
||<span data-ttu-id="e0a18-143">Naïve Bayes</span><span class="sxs-lookup"><span data-stu-id="e0a18-143">Naïve Bayes</span></span>|<span data-ttu-id="e0a18-144">중요한 특성</span><span class="sxs-lookup"><span data-stu-id="e0a18-144">Important attributes</span></span>|  
||<span data-ttu-id="e0a18-145">신경망</span><span class="sxs-lookup"><span data-stu-id="e0a18-145">Neural network</span></span>|<span data-ttu-id="e0a18-146">입력 노드 수</span><span class="sxs-lookup"><span data-stu-id="e0a18-146">Number of input nodes</span></span><br /><br /> <span data-ttu-id="e0a18-147">출력 노드 수</span><span class="sxs-lookup"><span data-stu-id="e0a18-147">Number of output nodes</span></span><br /><br /> <span data-ttu-id="e0a18-148">숨겨진 노드 수</span><span class="sxs-lookup"><span data-stu-id="e0a18-148">Number of hidden nodes</span></span>|  
||<span data-ttu-id="e0a18-149">시퀀스 클러스터링</span><span class="sxs-lookup"><span data-stu-id="e0a18-149">Sequence clustering</span></span>|<span data-ttu-id="e0a18-150">클러스터 수</span><span class="sxs-lookup"><span data-stu-id="e0a18-150">Number of clusters</span></span>|  
  
### <a name="complete-report"></a><span data-ttu-id="e0a18-151">전체 보고서</span><span class="sxs-lookup"><span data-stu-id="e0a18-151">Complete Report</span></span>  
 <span data-ttu-id="e0a18-152">전체 보고서에는 요약 보고서의 모든 내용과 모델에 사용된 데이터 열 및 분석 결과에 대한 세부 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-152">The complete report contains everything that is in the summary report, plus  detailed information about the columns of data used in the model and the results of analysis:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="e0a18-153">**메타데이터**</span><span class="sxs-lookup"><span data-stu-id="e0a18-153">**Metadata**</span></span>|<span data-ttu-id="e0a18-154">모델 메타데이터</span><span class="sxs-lookup"><span data-stu-id="e0a18-154">Model metadata</span></span>|<span data-ttu-id="e0a18-155">알고리즘 매개 변수 및 값</span><span class="sxs-lookup"><span data-stu-id="e0a18-155">Algorithm parameters and values</span></span>|  
||<span data-ttu-id="e0a18-156">열 메타데이터</span><span class="sxs-lookup"><span data-stu-id="e0a18-156">Column metadata</span></span>|<span data-ttu-id="e0a18-157">열 이름</span><span class="sxs-lookup"><span data-stu-id="e0a18-157">Column name</span></span><br /><br /> <span data-ttu-id="e0a18-158">사용</span><span class="sxs-lookup"><span data-stu-id="e0a18-158">Usage</span></span><br /><br /> <span data-ttu-id="e0a18-159">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="e0a18-159">Data type</span></span><br /><br /> <span data-ttu-id="e0a18-160">내용 유형</span><span class="sxs-lookup"><span data-stu-id="e0a18-160">Content type</span></span><br /><br /> <span data-ttu-id="e0a18-161">값(불연속 값 목록 또는 값 범위)</span><span class="sxs-lookup"><span data-stu-id="e0a18-161">Values (list of discrete values, or range of values)</span></span>|  
|<span data-ttu-id="e0a18-162">**모델 통계**</span><span class="sxs-lookup"><span data-stu-id="e0a18-162">**Model statistics**</span></span>|<span data-ttu-id="e0a18-163">연속 열</span><span class="sxs-lookup"><span data-stu-id="e0a18-163">Continuous columns</span></span>|<span data-ttu-id="e0a18-164">평균값</span><span class="sxs-lookup"><span data-stu-id="e0a18-164">Mean value</span></span><br /><br /> <span data-ttu-id="e0a18-165">최솟값</span><span class="sxs-lookup"><span data-stu-id="e0a18-165">Minimum value</span></span><br /><br /> <span data-ttu-id="e0a18-166">최댓값</span><span class="sxs-lookup"><span data-stu-id="e0a18-166">Maximum value</span></span><br /><br /> <span data-ttu-id="e0a18-167">제곱 평균 오차</span><span class="sxs-lookup"><span data-stu-id="e0a18-167">Root mean square error</span></span><br /><br /> <span data-ttu-id="e0a18-168">절대 평균 오차</span><span class="sxs-lookup"><span data-stu-id="e0a18-168">Mean absolute error</span></span><br /><br /> <span data-ttu-id="e0a18-169">로그 점수</span><span class="sxs-lookup"><span data-stu-id="e0a18-169">Log score</span></span><br /><br /> <span data-ttu-id="e0a18-170">회귀 수식(선형 회귀 모델만 해당)</span><span class="sxs-lookup"><span data-stu-id="e0a18-170">Regression formula (for linear regression models only)</span></span>|  
||<span data-ttu-id="e0a18-171">불연속 열</span><span class="sxs-lookup"><span data-stu-id="e0a18-171">Discrete columns</span></span>|<span data-ttu-id="e0a18-172">전달 횟수</span><span class="sxs-lookup"><span data-stu-id="e0a18-172">Count of passing</span></span><br /><br /> <span data-ttu-id="e0a18-173">실패 횟수</span><span class="sxs-lookup"><span data-stu-id="e0a18-173">Count of failing</span></span><br /><br /> <span data-ttu-id="e0a18-174">로그 점수</span><span class="sxs-lookup"><span data-stu-id="e0a18-174">Log score</span></span><br /><br /> <span data-ttu-id="e0a18-175">리프트</span><span class="sxs-lookup"><span data-stu-id="e0a18-175">Lift</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="e0a18-176">SQL Server Analysis Services에서 지원하는 모든 모델 유형은 문서화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-176">You can document any model type that is supported by SQL Server Analysis Services.</span></span> <span data-ttu-id="e0a18-177">따라서 테이블 분석 도구 또는 데이터 마이닝 클라이언트의 마법사를 통해 만들 수 없는 일부 모델 유형만 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-177">Therefore, the table lists some model types that cannot be created by using the Table Analysis Tools or by using the wizards in the Data Mining Client.</span></span> <span data-ttu-id="e0a18-178">그러나 **고급 데이터 마이닝 쿼리 편집기**를 사용 하 여 모든 모델 유형을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0a18-178">However, you can create all model types by using the **Advanced Data Mining Query Editor**.</span></span> <span data-ttu-id="e0a18-179">자세한 내용은 [쿼리 &#40;SQL Server 데이터 마이닝 추가 기능&#41;](query-sql-server-data-mining-add-ins.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e0a18-179">For more information, see [Query &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a18-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e0a18-180">See Also</span></span>  
 [<span data-ttu-id="e0a18-181">Excel 용 데이터 마이닝 추가 기능 &#40;마이닝 모델 배포 및 확장&#41;</span><span class="sxs-lookup"><span data-stu-id="e0a18-181">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
