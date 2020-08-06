---
title: 알고리즘 매개 변수 확인 또는 변경 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- algorithms [data mining]
- mining models [Analysis Services], algorithms
ms.assetid: 151b899b-c27a-4a09-bcf5-5c9f0ec24168
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30719cd50e0c473cf2aab5d9689d27dff4f26343
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649816"
---
# <a name="view-or-change-algorithm-parameters"></a><span data-ttu-id="507ce-102">알고리즘 매개 변수 확인 또는 변경</span><span class="sxs-lookup"><span data-stu-id="507ce-102">View or Change Algorithm Parameters</span></span>
  <span data-ttu-id="507ce-103">데이터 마이닝 모델을 작성하여 모델 결과를 사용자 지정하는 데 사용하는 알고리즘과 함께 제공되는 매개 변수를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-103">You can change the parameters provided with the algorithms that you use to build data mining models to customize the results of the model.</span></span>  
  
 <span data-ttu-id="507ce-104">에서 제공 하는 알고리즘 매개 변수는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 모델의 속성만 변경 합니다. 이러한 매개 변수는 데이터의 처리, 그룹화 및 표시 방법을 근본적으로 변경 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-104">The algorithm parameters provided in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] change much more than just properties on the model: they can be used to fundamentally alter the way that data is processed, grouped, and displayed.</span></span> <span data-ttu-id="507ce-105">예를 들어 알고리즘 매개 변수를 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-105">For example, you can use algorithm parameters to do the following:</span></span>  
  
-   <span data-ttu-id="507ce-106">클러스터링 메서드와 같은 분석 방법을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-106">Change the method of analysis, such as the clustering method.</span></span>  
  
-   <span data-ttu-id="507ce-107">기능 선택 동작을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-107">Control feature selection behavior.</span></span>  
  
-   <span data-ttu-id="507ce-108">항목 집합 크기 또는 규칙 확률을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-108">Specify the size of itemsets or the probability of rules.</span></span>  
  
-   <span data-ttu-id="507ce-109">의사 결정 트리의 분기와 깊이를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-109">Control branching and depth of decision trees.</span></span>  
  
-   <span data-ttu-id="507ce-110">모델 생성에 사용되는 내부 홀드아웃 집합의 크기 또는 초기값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-110">Specify a seed value or the size of the internal holdout set used for model creation.</span></span>  
  
 <span data-ttu-id="507ce-111">각 알고리즘마다 제공되는 매개 변수는 크게 다릅니다. 각 알고리즘에 대해 설정할 수 있는 매개 변수 목록은 이 섹션의 기술 참조 항목 [데이터 마이닝 알고리즘&#40;Analysis Services - 데이터 마이닝&#41;](data-mining-algorithms-analysis-services-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="507ce-111">The parameters provided for each algorithm vary greatly; for a list of the parameters that you can set for each algorithm, see the technical reference topics in this section: [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
### <a name="change-an-algorithm-parameter"></a><span data-ttu-id="507ce-112">알고리즘 매개 변수 변경</span><span class="sxs-lookup"><span data-stu-id="507ce-112">Change an algorithm parameter</span></span>  
  
1.  <span data-ttu-id="507ce-113">**의 데이터 마이닝 디자이너에 있는** 마이닝 모델 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]탭에서 알고리즘을 조정할 마이닝 모델의 알고리즘 유형을 마우스 오른쪽 단추로 클릭하고 **알고리즘 매개 변수 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-113">On the **Mining Models** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], right-click the algorithm type of the mining model for which you want to tune the algorithm, and select **Set Algorithm Parameters**.</span></span>  
  
     <span data-ttu-id="507ce-114">**알고리즘 매개 변수** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-114">The **Algorithm Parameters** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="507ce-115">**값** 열에서 변경할 알고리즘의 새 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-115">In the **Value** column, set a new value for the algorithm that you want to change.</span></span>  
  
     <span data-ttu-id="507ce-116">**값** 열에 값을 입력하지 않으면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 기본 매개 변수 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-116">If you do not enter a value in the **Value** column, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses the default parameter value.</span></span> <span data-ttu-id="507ce-117">**범위** 열에서 입력할 수 있는 값을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-117">The **Range** column describes the possible values that you can enter.</span></span>  
  
3.  <span data-ttu-id="507ce-118">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-118">Click **OK**.</span></span>  
  
     <span data-ttu-id="507ce-119">알고리즘 매개 변수가 새 값으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-119">The algorithm parameter is set with the new value.</span></span> <span data-ttu-id="507ce-120">모델을 다시 처리해야 매개 변수 변경 내용이 마이닝 모델에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-120">The parameter change will not be reflected in the mining model until you reprocess the model.</span></span>  
  
### <a name="view-the-parameters-used-in-an-existing-model"></a><span data-ttu-id="507ce-121">기존 모델에 사용되는 매개 변수 보기</span><span class="sxs-lookup"><span data-stu-id="507ce-121">View the parameters used in an existing model</span></span>  
  
1.  <span data-ttu-id="507ce-122">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 DMX 쿼리 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open a DMX Query window.</span></span>  
  
2.  <span data-ttu-id="507ce-123">다음과 같은 쿼리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="507ce-123">Type a query like this one:</span></span>  
  
    ```  
    select MINING_PARAMETERS   
    from $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = '<model name>'  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="507ce-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="507ce-124">See Also</span></span>  
 [<span data-ttu-id="507ce-125">마이닝 모델 태스크 및 방법</span><span class="sxs-lookup"><span data-stu-id="507ce-125">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
