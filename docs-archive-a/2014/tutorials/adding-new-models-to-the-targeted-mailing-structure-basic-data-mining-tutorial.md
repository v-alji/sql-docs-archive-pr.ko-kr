---
title: 대상 메일 구조에 새 모델 추가 (기본 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 512c6888-60f1-46e4-9639-bc448395b8d7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b83dfc6c9e218eecf3f2abe636b8c24d69d1b507
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735671"
---
# <a name="adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial"></a><span data-ttu-id="2eeb6-102">대상 메일 구조에 새 모델 추가(기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="2eeb6-102">Adding New Models to the Targeted Mailing Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="2eeb6-103">이 태스크에서는 데이터 마이닝 디자이너의 **마이닝 모델** 탭을 사용 하 여 두 개의 추가 모델을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-103">In this task, you will define two additional models by using the **Mining Models** tab of Data Mining Designer.</span></span> <span data-ttu-id="2eeb6-104">Microsoft 클러스터링 및 Microsoft Naive Bayes 알고리즘을 사용하여 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-104">You will use the Microsoft Clustering and Microsoft Naive Bayes algorithms to create the models.</span></span> <span data-ttu-id="2eeb6-105">이 두 알고리즘의 기능으로 불연속 값(예: 자전거 구매)을 예측할 수 있으므로 이 알고리즘이 선택되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-105">These two algorithms are selected because of their ability to predict a discrete value (i.e., bike purchase).</span></span> <span data-ttu-id="2eeb6-106">이러한 알고리즘에 대 한 자세한 내용은 [Microsoft 클러스터링 알고리즘](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md) 및 [Microsoft Naive Bayes 알고리즘](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-106">For more information about these algorithms, see [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md) and [Microsoft Naive Bayes Algorithm](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)</span></span>  
  
### <a name="to-create-a-clustering-mining-model"></a><span data-ttu-id="2eeb6-107">클러스터링 마이닝 모델을 만들려면</span><span class="sxs-lookup"><span data-stu-id="2eeb6-107">To create a clustering mining model</span></span>  
  
1.  <span data-ttu-id="2eeb6-108">의 데이터 마이닝 디자이너에서 **마이닝 모델** 탭으로 전환 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-108">Switch to the **Mining Models** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="2eeb6-109">디자이너에는 마이닝 구조에 대 한 열과 `TM_Decision_Tree` 이전 단원에서 만든 마이닝 모델에 대 한 두 개의 열이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-109">Notice that the designer displays two columns, one for the mining structure and one for the `TM_Decision_Tree` mining model, which you created in the previous lesson.</span></span>  
  
2.  <span data-ttu-id="2eeb6-110">**구조** 열을 마우스 오른쪽 단추로 클릭 하 고 **새 마이닝 모델**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-110">Right-click the **Structure** column and select **New Mining Model**.</span></span>  
  
3.  <span data-ttu-id="2eeb6-111">**새 마이닝 모델** 대화 상자의 **모델 이름**에을 입력 `TM_Clustering` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-111">In the **New Mining Model** dialog box, in **Model name**, type `TM_Clustering`.</span></span>  
  
4.  <span data-ttu-id="2eeb6-112">**알고리즘 이름**에서 **Microsoft 클러스터링**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-112">In **Algorithm name**, select **Microsoft Clustering**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 <span data-ttu-id="2eeb6-113">이제 데이터 마이닝 디자이너의 **마이닝 모델** 탭에 새 모델이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-113">The new model now appears in the **Mining Models** tab of Data Mining Designer.</span></span> <span data-ttu-id="2eeb6-114">클러스터링 알고리즘을 사용 하 여 작성 된이 모델 [!INCLUDE[msCoName](../includes/msconame-md.md)] 은 클러스터에 유사한 특성을 가진 고객을 그룹화 하 고 각 클러스터에 대 한 자전거 구매를 예측 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-114">This model, built with the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm, groups customers with similar characteristics into clusters and predicts bike buying for each cluster.</span></span> <span data-ttu-id="2eeb6-115">새 모델에 대 한 열 사용 및 속성을 수정할 수 있지만 `TM_Clustering` 이 자습서에서는 모델을 변경할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-115">Although you can modify the column usage and properties for the new model, no changes to the `TM_Clustering` model are necessary for this tutorial.</span></span>  
  
### <a name="to-create-a-naive-bayes-mining-model"></a><span data-ttu-id="2eeb6-116">Naive Bayes 마이닝 모델을 만들려면</span><span class="sxs-lookup"><span data-stu-id="2eeb6-116">To create a Naive Bayes mining model</span></span>  
  
1.  <span data-ttu-id="2eeb6-117">데이터 마이닝 디자이너의 **마이닝 모델** 탭에서 **구조** 열을 마우스 오른쪽 단추로 클릭 하 고 **새 마이닝 모델**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-117">In the **Mining Models** tab of Data Mining Designer, right-clickthe **Structure** column, and select **New Mining Model**.</span></span>  
  
2.  <span data-ttu-id="2eeb6-118">**새 마이닝 모델** 대화 상자의 **모델 이름**에을 입력 `TM_NaiveBayes` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-118">In the **New Mining Model** dialog box, under **Model name**, type `TM_NaiveBayes`.</span></span>  
  
3.  <span data-ttu-id="2eeb6-119">**알고리즘 이름**에서 **Microsoft Naive Bayes**를 선택한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-119">In **Algorithm name**, select **Microsoft Naive Bayes**, then click **OK**.</span></span>  
  
     <span data-ttu-id="2eeb6-120">[!INCLUDE[msCoName](../includes/msconame-md.md)]Naive Bayes 알고리즘이 연속 인 **Age** 및 **연간 소득** 열을 지원 하지 않음을 나타내는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-120">A message appears stating that the [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes algorithm does not support the **Age** and **Yearly Income** columns, which are continuous.</span></span>  
  
4.  <span data-ttu-id="2eeb6-121">**예** 를 클릭 하 여 메시지를 승인 하 고 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-121">Click **Yes** to acknowledge the message and continue.</span></span>  
  
 <span data-ttu-id="2eeb6-122">데이터 마이닝 디자이너의 **마이닝 모델** 탭에 새 모델이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-122">A new model appears in the **Mining Models** tab of Data Mining Designer.</span></span> <span data-ttu-id="2eeb6-123">이 탭의 모든 모델에 대 한 열 사용 및 속성을 수정할 수 있지만 `TM_NaiveBayes` 이 자습서에서는 모델을 변경할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2eeb6-123">Although you can modify the column usage and properties for all the models in this tab, no changes to the `TM_NaiveBayes` model are necessary for this tutorial.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2eeb6-124">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="2eeb6-124">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2eeb6-125">기본 데이터 마이닝 자습서 &#40;대상 메일 구조에서 모델 처리&#41;</span><span class="sxs-lookup"><span data-stu-id="2eeb6-125">Processing Models in the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="2eeb6-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2eeb6-126">See Also</span></span>  
 <span data-ttu-id="2eeb6-127">[Analysis Services 데이터 마이닝 &#40;구조에 마이닝 모델을 추가&#41;](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="2eeb6-127">[Add Mining Models to a Structure &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="2eeb6-128">[데이터 마이닝 디자이너](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="2eeb6-128">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 [<span data-ttu-id="2eeb6-129">데이터 마이닝 개체 이동</span><span class="sxs-lookup"><span data-stu-id="2eeb6-129">Moving Data Mining Objects</span></span>](../../2014/analysis-services/data-mining/moving-data-mining-objects.md)  
  
  
