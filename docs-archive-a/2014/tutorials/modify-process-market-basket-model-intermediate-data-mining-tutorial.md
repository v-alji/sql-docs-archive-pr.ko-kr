---
title: 시장 바구니 모델 수정 및 처리 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b6019413-aebd-4ff7-831a-644572ad88b1
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 369de98e944c5ccf5d06ef61eaa16c06bb864e7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639173"
---
# <a name="modifying-and-processing-the-market-basket-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="87203-102">시장 바구니 모델 수정 및 처리(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="87203-102">Modifying and Processing the Market Basket Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="87203-103">만든 연결 마이닝 모델을 처리 하기 전에 두 매개 변수 ( *지원* 및 *확률*)의 기본값을 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87203-103">Before you process the association mining model that you created, you must change the default values of two of the parameters: *Support* and *Probability*.</span></span>  
  
-   <span data-ttu-id="87203-104">*지원은* 규칙이 유효한 것으로 간주 되기 전에 존재 해야 하는 사례의 비율을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="87203-104">*Support* defines the percentage of cases in which a rule must exist before it is considered valid.</span></span> <span data-ttu-id="87203-105">적어도 총 사례 수의 1% 이상에서 규칙을 발견하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="87203-105">You will specify that a rule must be found in at least 1 percent of cases.</span></span>  
  
-   <span data-ttu-id="87203-106">*확률* 은 연결이 유효한 것으로 간주 되기 전에 연결 해야 하는 가능성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="87203-106">*Probability* defines how likely an association must be before it is considered valid.</span></span> <span data-ttu-id="87203-107">모든 연결의 확률은 적어도 10% 이상이라고 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="87203-107">You will consider any association with a probability of at least 10 percent.</span></span>  
  
 <span data-ttu-id="87203-108">지원 및 확률을 늘리거나 줄이는 효과에 대 한 자세한 내용은 [Microsoft 연결 알고리즘 기술 참조](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="87203-108">For more information about the effects of increasing or decreasing support and probability, see [Microsoft Association Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="87203-109">**연결** 마이닝 모델에 대 한 구조와 매개 변수를 정의한 후에는 모델을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="87203-109">After you have defined the structure and parameters for the **Association** mining model, you will process the model.</span></span>  
  
### <a name="to-adjust-the-parameters-of-the-association-model"></a><span data-ttu-id="87203-110">Association 모델의 매개 변수를 조정하려면</span><span class="sxs-lookup"><span data-stu-id="87203-110">To adjust the parameters of the Association model</span></span>  
  
1.  <span data-ttu-id="87203-111">데이터 마이닝 디자이너의 **마이닝 모델** 탭을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="87203-111">Open the **Mining Models** tab of Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="87203-112">디자이너의 표에서 **연결** 열을 마우스 오른쪽 단추로 클릭 하 고 **알고리즘 매개 변수 설정을 선택 하 여 알고리즘 매개 변수 대화 상자를 엽니다** .</span><span class="sxs-lookup"><span data-stu-id="87203-112">Right-click the **Association** column in the grid in the designer and select **Set Algorithm Parameters to open the Algorithm Parameters** dialog box.</span></span>  
  
3.  <span data-ttu-id="87203-113">**알고리즘 매개 변수** 대화 상자의 **값** 열에서 다음 매개 변수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="87203-113">In the **Value** column of the **Algorithm Parameters** dialog box, set the following parameters:</span></span>  
  
     <span data-ttu-id="87203-114">MINIMUM_PROBABILITY = 0.1</span><span class="sxs-lookup"><span data-stu-id="87203-114">MINIMUM_PROBABILITY = 0.1</span></span>  
  
     <span data-ttu-id="87203-115">MINIMUM_SUPPORT = 0.01</span><span class="sxs-lookup"><span data-stu-id="87203-115">MINIMUM_SUPPORT = 0.01</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-process-the-mining-model"></a><span data-ttu-id="87203-116">마이닝 모델을 처리하려면</span><span class="sxs-lookup"><span data-stu-id="87203-116">To process the mining model</span></span>  
  
1.  <span data-ttu-id="87203-117">의 **마이닝 모델** 메뉴에서 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] **마이닝 구조 및 모든 모델 처리** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="87203-117">On the **Mining Model** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], select **Process Mining Structure and All Models.**</span></span>  
  
2.  <span data-ttu-id="87203-118">프로젝트를 빌드 및 배포할지를 요청 하는 경고에서 **예**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="87203-118">At the warning asking whether you want to build and deploy the project, click **Yes**.</span></span>  
  
     <span data-ttu-id="87203-119">**마이닝 구조 처리-연결** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="87203-119">The **Process Mining Structure - Association** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="87203-120">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87203-120">Click **Run**.</span></span>  
  
     <span data-ttu-id="87203-121">**처리 진행률** 대화 상자가 열리고 모델 처리에 대 한 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="87203-121">The **Process Progress** dialog box opens to display information about model processing.</span></span> <span data-ttu-id="87203-122">새 구조 및 모델을 처리하는 데에는 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87203-122">Processing of the new structure and model might take some time.</span></span>  
  
4.  <span data-ttu-id="87203-123">처리가 완료 되 면 **닫기** 를 클릭 하 여 처리 **진행률** 대화 상자를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="87203-123">After processing is complete, click **Close** to exit the **Process Progress** dialog box.</span></span>  
  
5.  <span data-ttu-id="87203-124">**닫기** 를 다시 클릭 하 여 **마이닝 구조 처리-연결** 대화 상자를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="87203-124">Click **Close** again to exit the **Process Mining Structure - Association** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="87203-125">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="87203-125">Next Task in Lesson</span></span>  
 [<span data-ttu-id="87203-126">시장 바구니 모델 탐색 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="87203-126">Exploring the Market Basket Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="87203-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="87203-127">See Also</span></span>  
 [<span data-ttu-id="87203-128">처리 요구 사항 및 고려 사항&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="87203-128">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
