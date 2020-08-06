---
title: 데이터 마이닝 알고리즘 (SQL Server 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- segmentation
- data mining algorithms
- clustering [data mining]
- linear regression
- association [data mining]
- neural networks
- logistic regression
- regression
- sequence analysis
- decision tree [data mining]
- Naive Bayes
- time series [data mining]
ms.assetid: 3a1a62e4-9fb5-4cdb-a6c6-1b8b30d417ef
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3a73ce5a538756a740afd2db72d585fa54f03cae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659746"
---
# <a name="data-mining-algorithms-sql-server-data-mining-add-ins"></a><span data-ttu-id="4b173-102">데이터 마이닝 알고리즘(SQL Server 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="4b173-102">Data Mining Algorithms (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="4b173-103">Office용 데이터 마이닝 추가 기능은 다음과 같은 데이터 마이닝 알고리즘을 사용하여 분석 모델을 만드는 작업을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4b173-103">The Data Mining Add-ins for Office supports creation of analytical models using the following data mining algorithms.</span></span> <span data-ttu-id="4b173-104">모든 알고리즘은 잘 알려진 시스템 학습 방법을 기반으로 하며 Microsoft Research에서 구현되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4b173-104">All algorithms are based on well-known machine learning methods and have been implemented by Microsoft Research.</span></span>  
  
## <a name="algorithms"></a><span data-ttu-id="4b173-105">알고리즘</span><span class="sxs-lookup"><span data-stu-id="4b173-105">Algorithms</span></span>  
  
|<span data-ttu-id="4b173-106">시스템 학습 방법</span><span class="sxs-lookup"><span data-stu-id="4b173-106">Machine learning method</span></span>|<span data-ttu-id="4b173-107">작동 방법</span><span class="sxs-lookup"><span data-stu-id="4b173-107">How it works</span></span>|  
|-----------------------------|------------------|  
|<span data-ttu-id="4b173-108">Microsoft 연결 규칙 알고리즘</span><span class="sxs-lookup"><span data-stu-id="4b173-108">Microsoft Association Rules  algorithm</span></span>|<span data-ttu-id="4b173-109">함께 구입하는 제품이나 함께 발생하는 이벤트를 발견하고 모델을 사용하여 권장 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b173-109">Discover which products are purchased together or which events occur together, and use the model to create recommendations.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174916.aspx](https://msdn.microsoft.com/library/ms174916.aspx)|  
|<span data-ttu-id="4b173-110">Microsoft 클러스터링 알고리즘</span><span class="sxs-lookup"><span data-stu-id="4b173-110">Microsoft Clustering algorithm</span></span>|<span data-ttu-id="4b173-111">시장 세그먼트를 정의하거나, 관련 고객을 자동으로 함께 그룹화하거나, 이후 마이닝에서 사용할 관계를 데이터에서 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4b173-111">Define market segments, automatically group related customers together, or find relationships in data to use in further mining.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174879.aspx](https://msdn.microsoft.com/library/ms174879.aspx)|  
|<span data-ttu-id="4b173-112">Microsoft 의사 결정 트리 알고리즘</span><span class="sxs-lookup"><span data-stu-id="4b173-112">Microsoft Decision Trees algorithm</span></span>|<span data-ttu-id="4b173-113">다양한 데이터 요소 간의 이전에 알려지지 않은 관계를 식별하여 결정에 더 많은 정보를 제공하거나, 특정 결과로 이끄는 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4b173-113">Identify previously unknown relationships between various elements of your data to better inform your decisions, or find the factors that lead to specific outcomes.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174923.aspx](https://msdn.microsoft.com/library/ms174923.aspx)|  
|<span data-ttu-id="4b173-114">Microsoft 선형 회귀 알고리즘</span><span class="sxs-lookup"><span data-stu-id="4b173-114">Microsoft Linear Regression algorithm</span></span>|<span data-ttu-id="4b173-115">숫자 결과에 영향을 주는 요소를 설명하는 수식을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4b173-115">Find a mathematical formula that describes factors that contribute to a numeric outcome.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174824.aspx](https://msdn.microsoft.com/library/ms174824.aspx)|  
|<span data-ttu-id="4b173-116">Microsoft 로지스틱 회귀 알고리즘</span><span class="sxs-lookup"><span data-stu-id="4b173-116">Microsoft Logistic Regression algorithm</span></span>|<span data-ttu-id="4b173-117">이진 결과에 영향을 주는 요소를 식별하고 이러한 요소를 사용하여 결과에 영향을 주는 방법을 파악합니다.</span><span class="sxs-lookup"><span data-stu-id="4b173-117">Identify the factors that contribute to binary outcomes, and learn how to use those to affect results.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174828.aspx](https://msdn.microsoft.com/library/ms174828.aspx)|  
|<span data-ttu-id="4b173-118">Microsoft Naïve Bayes 알고리즘</span><span class="sxs-lookup"><span data-stu-id="4b173-118">Microsoft Naïve Bayes algorithm</span></span>|<span data-ttu-id="4b173-119">데이터에서 관계를 탐색하고 결과와 가장 밀접히 연관된 관계를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4b173-119">Explore relationships in your data and find those mostly closely correlated with an outcome.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174806.aspx](https://msdn.microsoft.com/library/ms174806.aspx)|  
|<span data-ttu-id="4b173-120">Microsoft 신경망 알고리즘</span><span class="sxs-lookup"><span data-stu-id="4b173-120">Microsoft Neural Networks algorithm</span></span>|<span data-ttu-id="4b173-121">여러 입력과 여러 출력 간의 숨겨진 관계를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4b173-121">Find hidden relationships among multiple inputs and even multiple outputs.</span></span> <span data-ttu-id="4b173-122">탐색이나 예측에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4b173-122">Use for exploration or for prediction.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174941.aspx](https://msdn.microsoft.com/library/ms174941.aspx)|  
|<span data-ttu-id="4b173-123">Microsoft Time Series 알고리즘</span><span class="sxs-lookup"><span data-stu-id="4b173-123">Microsoft Time Series algorithm</span></span>|<span data-ttu-id="4b173-124">기록 데이터를 사용하여 미래 가치를 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="4b173-124">Use historical data to forecast future values.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174923.aspx](https://msdn.microsoft.com/library/ms174923.aspx)|  
  
## <a name="advanced-options"></a><span data-ttu-id="4b173-125">고급 옵션</span><span class="sxs-lookup"><span data-stu-id="4b173-125">Advanced Options</span></span>  
 <span data-ttu-id="4b173-126">Excel용 데이터 마이닝 클라이언트를 사용할 때는 사용자 고유의 데이터 마이닝 구조 및 모델을 만들거나 알고리즘의 매개 변수를 세밀하게 조정하는 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b173-126">When you use the Data Mining Client for Excel, you have the option to create your own data mining structures and models, or to fine-tune the parameters of the algorithms.</span></span>  
  
 [<span data-ttu-id="4b173-127">알고리즘 매개 변수 SQL Server 데이터 마이닝 추가 기능을 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="4b173-127">Algorithm Parameters &#40;SQL Server Data Mining Add-ins&#41;</span></span>](algorithm-parameters-sql-server-data-mining-add-ins.md)  
  
 <span data-ttu-id="4b173-128">이러한 고급 옵션을 사용하여 모델을 사용자 지정하는 방법은 다음 두 가지입니다.</span><span class="sxs-lookup"><span data-stu-id="4b173-128">There are two ways to customize your models using these advanced options:</span></span>  
  
-   <span data-ttu-id="4b173-129">**데이터 마이닝 쿼리** 마법사를 사용하여 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b173-129">Use the **Data Mining Query** wizard to create your model.</span></span>  
  
-   <span data-ttu-id="4b173-130">**데이터 마이닝 클라이언트**에서 마법사를 시작한 후 **매개 변수**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4b173-130">In the **Data Mining Client**, after you start the wizard, click **Parameters**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b173-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b173-131">See Also</span></span>  
 <span data-ttu-id="4b173-132">[쿼리 &#40;SQL Server 데이터 마이닝 추가 기능&#41;](query-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="4b173-132">[Query &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="4b173-133">Excel 용 데이터 마이닝 추가 기능에 대 한 고급 모델링 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="4b173-133">Advanced Modeling &#40;Data Mining Add-ins for Excel&#41;</span></span>](advanced-modeling-data-mining-add-ins-for-excel.md)  
  
  
