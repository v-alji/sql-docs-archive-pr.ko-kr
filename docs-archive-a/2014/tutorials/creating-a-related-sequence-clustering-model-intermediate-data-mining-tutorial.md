---
title: 관련 된 시퀀스 클러스터링 모델 만들기 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1fb4f5bc-1756-45ca-9cd7-411a8c5992a9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d015ed8a9887cb6164020806bf4136f58629ad11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734735"
---
# <a name="creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="b3944-102">관련된 시퀀스 클러스터링 모델 만들기(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="b3944-102">Creating a Related Sequence Clustering Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="b3944-103">시퀀스 클러스터링 모델 탐색을 통해 Region 또는 Income과 같은 다른 특성이 모델에 중요한 영향을 준다는 것을 알게 되었습니다. 따라서 시퀀스를 보다 잘 이해하려면 관련된 시퀀스 클러스터링 모델을 만들고 고객 인구 통계와 관련된 특성을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-103">Through your exploration of the sequence clustering model, you learned that other attributes such as Region or Income have a strong effect on the models; therefore, to understand the sequences better, you will create a related sequence clustering model and remove the attributes related to customer demographics.</span></span>  
  
 <span data-ttu-id="b3944-104">이 태스크에서 지역 시퀀스 클러스터링 모델의 복사본을 만들고 모델에서 시퀀스와 직접 관련되지 않은 열을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-104">In this task, you will create a copy of the regional sequence clustering model, and then remove from the model any columns that are not directly related to the sequences.</span></span>  
  
 <span data-ttu-id="b3944-105">새 모델에 새 모델의 기반이 되는 마이닝 모델과 동일한 열이 모두 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-105">The new model will contain all the same columns as the mining model on which it is based.</span></span> <span data-ttu-id="b3944-106">그러나 마이닝 구조에서 열을 제거하지 않아도 되며, 새 마이닝 모델이 열을 무시하도록 지정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-106">However, you do not need to remove the columns from the mining structure, only specify that the new mining model ignore the columns.</span></span>  
  
### <a name="to-make-a-copy-of-the-sequence-clustering-model"></a><span data-ttu-id="b3944-107">시퀀스 클러스터링 모델의 복사본을 만들려면</span><span class="sxs-lookup"><span data-stu-id="b3944-107">To make a copy of the sequence clustering model</span></span>  
  
1.  <span data-ttu-id="b3944-108">의 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 데이터 마이닝 디자이너에서 **마이닝 모델** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in the Data Mining Designer, click the **Mining Models** tab.</span></span>  
  
2.  <span data-ttu-id="b3944-109">복사할 모델을 마우스 오른쪽 단추로 클릭 하 고 **새 마이닝 모델**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-109">Right-click the model you want to copy, and select **New Mining Model**.</span></span>  
  
3.  <span data-ttu-id="b3944-110">**새 마이닝 모델** 대화 상자에서 모델 이름을 입력 하 고 Microsoft를 선택 `Sequence Clustering` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-110">In the **New Mining Model** dialog box, type a model name, and select Microsoft `Sequence Clustering`.</span></span>  
  
     <span data-ttu-id="b3944-111">이 자습서에서는 이름을 입력 `Sequence Clustering` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-111">For this tutorial, type the name `Sequence Clustering`.</span></span>  
  
4.  <span data-ttu-id="b3944-112">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-112">Click **OK**.</span></span>  
  
### <a name="to-remove-columns-from-the-mining-model"></a><span data-ttu-id="b3944-113">마이닝 모델에서 열을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="b3944-113">To remove columns from the mining model</span></span>  
  
1.  <span data-ttu-id="b3944-114">**마이닝 모델** 탭의 시퀀스 클러스터링 이라는 새 모델의 열에서 **소득 그룹** 특성에 대 한 행을 클릭 하 고 **무시**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-114">In the **Mining Model** tab, in the column for the new model named Sequence Clustering, click the row for the **Income Group** attribute, and select **Ignore**.</span></span>  
  
2.  <span data-ttu-id="b3944-115">특성 **영역**에 대해이 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-115">Repeat this step for the attribute **Region**.</span></span>  
  
3.  <span data-ttu-id="b3944-116">테이블 이름, **v Assoc Seq Line Items**옆에 있는 더하기 기호를 클릭 하 여 테이블을 확장 하 고 중첩 테이블에서 열을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-116">Click the plus sign next to the table name, **v Assoc Seq Line Items**, to expand the table and view the columns from the nested table.</span></span>  
  
     <span data-ttu-id="b3944-117">새 모델에는 다음 열만 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-117">The new model should have only the following columns:</span></span>  
  
     <span data-ttu-id="b3944-118">**주문 번호 키**</span><span class="sxs-lookup"><span data-stu-id="b3944-118">**Order NumberKey**</span></span>  
  
     <span data-ttu-id="b3944-119">**줄 번호 키**</span><span class="sxs-lookup"><span data-stu-id="b3944-119">**Line Number Key**</span></span>  
  
     <span data-ttu-id="b3944-120">**모델 예측**</span><span class="sxs-lookup"><span data-stu-id="b3944-120">**Model Predict**</span></span>  
  
### <a name="to-process-the-new-sequence-clustering-model"></a><span data-ttu-id="b3944-121">새 시퀀스 클러스터링 모델을 처리하려면</span><span class="sxs-lookup"><span data-stu-id="b3944-121">To process the new sequence clustering model</span></span>  
  
1.  <span data-ttu-id="b3944-122">**마이닝 모델** 탭에서 라는 새 모델을 마우스 오른쪽 단추로 클릭 `Sequence Clustering` 하 고 **모델 처리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-122">In the **Mining Model** tab, right-click the new model named `Sequence Clustering`, and select **Process Model**.</span></span>  
  
     <span data-ttu-id="b3944-123">간단한 새 마이닝 모델은 이미 처리된 구조를 기반으로 하므로 구조를 다시 처리하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-123">Because the new simplified mining model is based on a structure that has already been processed, you do not need to reprocess the structure.</span></span> <span data-ttu-id="b3944-124">이제 새 마이닝 모델을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-124">You can process just the new mining model.</span></span>  
  
2.  <span data-ttu-id="b3944-125">업데이트 된 데이터 마이닝 프로젝트를 서버에 배포 하려면 **예** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-125">Click **Yes** to deploy the updated data mining project to the server.</span></span>  
  
3.  <span data-ttu-id="b3944-126">**마이닝 모델 처리** 대화 상자에서 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-126">In the **Process Mining Model** dialog box, click **Run**.</span></span>  
  
4.  <span data-ttu-id="b3944-127">**닫기** 를 클릭 하 여 **처리 진행률** 대화 상자를 닫은 다음 **마이닝 모델 처리** 대화 상자에서 **닫기** 를 다시 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3944-127">Click **Close** to close the **Process Progress** dialog box, and then click **Close** again in the **Process Mining Model** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="b3944-128">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="b3944-128">Next Task in Lesson</span></span>  
 [<span data-ttu-id="b3944-129">시퀀스 클러스터링 모델에서 예측 만들기 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="b3944-129">Creating Predictions on a Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="b3944-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3944-130">See Also</span></span>  
 [<span data-ttu-id="b3944-131">처리 요구 사항 및 고려 사항&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="b3944-131">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
