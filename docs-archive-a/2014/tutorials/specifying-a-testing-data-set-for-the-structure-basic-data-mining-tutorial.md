---
title: 구조에 대 한 테스트 데이터 집합 지정 (기본 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 75cd508f-b126-418b-848d-3c4c3e6c303f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c1430706a0ec2cd3ddc0eaee18d7001d05fefae1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639164"
---
# <a name="specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial"></a><span data-ttu-id="5f35e-102">구조에 대한 테스트 데이터 집합 지정(기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="5f35e-102">Specifying a Testing Data Set for the Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="5f35e-103">데이터 마이닝 마법사의 마지막 화면에서 데이터를 테스트 집합과 학습 집합으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="5f35e-103">In the final few screens of the Data Mining Wizard you will split your data into a testing set and a training set.</span></span> <span data-ttu-id="5f35e-104">그런 다음 구조에 이름을 지정하고 모델에 드릴스루를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5f35e-104">You will then name your structure and enable drillthrough on the model.</span></span>  
  
## <a name="specifying-a-testing-set"></a><span data-ttu-id="5f35e-105">학습 집합 지정</span><span class="sxs-lookup"><span data-stu-id="5f35e-105">Specifying a Testing Set</span></span>  
 <span data-ttu-id="5f35e-106">마이닝 구조를 만들 때 학습 집합과 테스트 집합으로 데이터를 분리하면 나중에 만드는 마이닝 모델의 정확도를 쉽게 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f35e-106">Separating data into training and testing sets when you create a mining structure makes it possible to easily assess the accuracy of the mining models that you create later.</span></span> <span data-ttu-id="5f35e-107">테스트 집합에 대 한 자세한 내용은 [데이터 집합 학습 및 테스트](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5f35e-107">For more information on testing sets, see [Training and Testing Data Sets](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md).</span></span>  
  
#### <a name="to-specify-the-testing-set"></a><span data-ttu-id="5f35e-108">테스트 집합을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="5f35e-108">To specify the testing set</span></span>  
  
1.  <span data-ttu-id="5f35e-109">테스트 **집합 만들기** 페이지에서 **테스트할 데이터의 백분율**에 대해 기본값인를 그대로 둡니다 `30` .</span><span class="sxs-lookup"><span data-stu-id="5f35e-109">On the **Create Testing Set** page, for **Percentage of data for testing**, leave the default value of `30`.</span></span>  
  
2.  <span data-ttu-id="5f35e-110">**테스트 데이터 집합의 최대 사례 수**에 대해을 입력 `1000` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f35e-110">For **Maximum number of cases in testing data set**, type `1000`.</span></span>  
  
3.  <span data-ttu-id="5f35e-111">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f35e-111">Click **Next**.</span></span>  
  
## <a name="specifying-drillthrough"></a><span data-ttu-id="5f35e-112">드릴스루 지정</span><span class="sxs-lookup"><span data-stu-id="5f35e-112">Specifying Drillthrough</span></span>  
 <span data-ttu-id="5f35e-113">모델 및 구조에 드릴스루를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f35e-113">Drillthrough can be enabled on models and on structures.</span></span> <span data-ttu-id="5f35e-114">이 대화 상자에서 확인란을 선택하여 명명된 모델에 대한 드릴스루를 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f35e-114">The checkbox in this dialog box enables drillthrough on the named model.</span></span> <span data-ttu-id="5f35e-115">모델을 처리한 후에는 모델을 만드는 데 사용된 학습 데이터에서 자세한 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f35e-115">After the model has been processed,  you will be able to retrieve detailed information from the training data that were used to create the model.</span></span>  
  
 <span data-ttu-id="5f35e-116">기본 마이닝 구조도 드릴스루를 허용하도록 구성한 경우 마이닝 모델에 포함되지 않은 열을 비롯하여 모델 사례 및 마이닝 구조 모두의 세부 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f35e-116">If the underlying mining structure has also been configured to allow drillthrough, you can retrieve detailed information from both the model cases and the mining structure, including columns that were not included in the mining model.</span></span> <span data-ttu-id="5f35e-117">자세한 내용은 [드릴스루 쿼리&#40;데이터 마이닝&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5f35e-117">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).</span></span>  
  
#### <a name="to-name-the-model-and-structure-and-specify-drillthrough"></a><span data-ttu-id="5f35e-118">모델 및 구조에 이름을 지정하고 드릴스루를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="5f35e-118">To name the model and structure and specify drillthrough</span></span>  
  
1.  <span data-ttu-id="5f35e-119">**마법사 완료** 페이지의 **마이닝 구조 이름**에을 입력 `Targeted Mailing` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f35e-119">On the **Completing the Wizard** page, in **Mining structure name**, type `Targeted Mailing`.</span></span>  
  
2.  <span data-ttu-id="5f35e-120">**마이닝 모델 이름**에을 입력 `TM_Decision_Tree` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f35e-120">In **Mining model name**, type `TM_Decision_Tree`.</span></span>  
  
3.  <span data-ttu-id="5f35e-121">**드릴스루 허용** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f35e-121">Select the **Allow drill through** check box.</span></span>  
  
4.  <span data-ttu-id="5f35e-122">**미리 보기** 창을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f35e-122">Review the **Preview** pane.</span></span> <span data-ttu-id="5f35e-123">**키**, **입력** 또는 **예측** 가능으로 선택한 열만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f35e-123">Notice that only those columns selected as **Key**, **Input** or **Predictable** are shown.</span></span> <span data-ttu-id="5f35e-124">선택한 다른 열(예: AddressLine1)은 모델 작성에 사용되지 않지만 기존 구조에 사용할 수 있으며 모델이 처리 및 배포된 후에 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f35e-124">The other columns you selected (e.g., AddressLine1) are not used for building the model but will be available in the underlying structure, and can be queried after the model is processed and deployed.</span></span>  
  
5.  <span data-ttu-id="5f35e-125">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f35e-125">Click **Finish**.</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="5f35e-126">단원의 이전 태스크</span><span class="sxs-lookup"><span data-stu-id="5f35e-126">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="5f35e-127">기본 데이터 마이닝 자습서 &#40;데이터 형식 및 내용 유형 지정&#41;</span><span class="sxs-lookup"><span data-stu-id="5f35e-127">Specifying the Data Type and Content Type &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="5f35e-128">다음 단원</span><span class="sxs-lookup"><span data-stu-id="5f35e-128">Next Lesson</span></span>  
 [<span data-ttu-id="5f35e-129">3단원: 모델 추가 및 처리</span><span class="sxs-lookup"><span data-stu-id="5f35e-129">Lesson 3: Adding and Processing Models</span></span>](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="see-also"></a><span data-ttu-id="5f35e-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f35e-130">See Also</span></span>  
 <span data-ttu-id="5f35e-131">[마이닝 모델에 드릴스루 사용](../../2014/analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="5f35e-131">[Enable Drillthrough for a Mining Model](../../2014/analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md) </span></span>  
 <span data-ttu-id="5f35e-132">[드릴스루 쿼리 &#40;데이터 마이닝&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="5f35e-132">[Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md) </span></span>  
 [<span data-ttu-id="5f35e-133">데이터 마이닝 마법사 &#40;학습 데이터를 지정&#41;</span><span class="sxs-lookup"><span data-stu-id="5f35e-133">Specify the Training Data &#40;Data Mining Wizard&#41;</span></span>](../../2014/analysis-services/specify-the-training-data-data-mining-wizard.md)  
  
  
