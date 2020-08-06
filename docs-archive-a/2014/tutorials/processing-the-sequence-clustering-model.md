---
title: 시퀀스 클러스터링 모델 처리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4a7545fd-37a3-4766-ad59-0946f1bd3524
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9975105fb6779e150e3a498bc87654d21292a1b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735616"
---
# <a name="processing-the-sequence-clustering-model"></a><span data-ttu-id="67e8b-102">시퀀스 클러스터링 모델 처리</span><span class="sxs-lookup"><span data-stu-id="67e8b-102">Processing the Sequence Clustering Model</span></span>
  <span data-ttu-id="67e8b-103">새 마이닝 구조를 만든 후에는 데이터 마이닝 솔루션에 적용한 변경 사항을 배포하고 구조를 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67e8b-103">After you create a new mining structure, you must deploy the changes that you made to the data mining solution, and then process the structure.</span></span> <span data-ttu-id="67e8b-104">새 구조와 마이닝 모델 처리가 모두 완료되면 마이닝 모델을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67e8b-104">After processing of both the new structure and the mining model is complete, you can browse the mining model.</span></span>  
  
 <span data-ttu-id="67e8b-105">새 데이터 마이닝 구조를 만들 때 처리가 항상 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="67e8b-105">Processing is always required when you create a new data mining structure.</span></span> <span data-ttu-id="67e8b-106">그러나 새 마이닝 모델을 기존 구조에 추가하면 해당 마이닝 모델만 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67e8b-106">However, if you add a new mining model to an existing structure, you can process just the mining model.</span></span> <span data-ttu-id="67e8b-107">이 시나리오에서는 새 마이닝 구조와 새 마이닝 모델을 만들었으므로 구조와 모델을 모두 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67e8b-107">In this scenario, because you have created a new mining structure and a new mining model, you must process both.</span></span>  
  
### <a name="to-process-the-mining-structure-and-model"></a><span data-ttu-id="67e8b-108">마이닝 구조 및 모델을 처리하려면</span><span class="sxs-lookup"><span data-stu-id="67e8b-108">To process the mining structure and model</span></span>  
  
1.  <span data-ttu-id="67e8b-109">의 **마이닝 모델** 메뉴에서 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] **마이닝 구조 및 모든 모델 처리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="67e8b-109">On the **Mining Model** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], select **Process Mining Structure and All Models**.</span></span>  
  
2.  <span data-ttu-id="67e8b-110">프로젝트를 빌드 및 배포할지를 요청 하는 경고에서 **예**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="67e8b-110">At the warning asking whether you want to build and deploy the project, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="67e8b-111">**마이닝 구조 처리-하위 지역에서 시퀀스 클러스터링** 대화 상자에서 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="67e8b-111">In the **Process Mining Structure - Sequence Clustering with Region** dialog box, click **Run**.</span></span>  
  
     <span data-ttu-id="67e8b-112">**처리 진행률** 대화 상자가 열리고 모델 처리에 대 한 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="67e8b-112">The **Process Progress** dialog box opens to display information about model processing.</span></span> <span data-ttu-id="67e8b-113">새 구조 및 모델을 처리하는 데에는 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67e8b-113">Processing of the new structure and model might take some time.</span></span>  
  
4.  <span data-ttu-id="67e8b-114">처리가 완료 되 면 **닫기** 를 클릭 하 여 처리 **진행률** 대화 상자를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="67e8b-114">After processing is complete, click **Close** to exit the **Process Progress** dialog box.</span></span>  
  
5.  <span data-ttu-id="67e8b-115">[ **닫기** ]를 다시 클릭 하 여 **마이닝 구조 처리-지역에 대 한 시퀀스 클러스터링** 대화 상자를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="67e8b-115">Click **Close** again to exit the **Process Mining Structure - Sequence Clustering with Region** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="67e8b-116">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="67e8b-116">Next Task in Lesson</span></span>  
 [<span data-ttu-id="67e8b-117">시퀀스 클러스터링 모델 탐색 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="67e8b-117">Exploring the Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="67e8b-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="67e8b-118">See Also</span></span>  
 <span data-ttu-id="67e8b-119">[데이터 마이닝 디자이너](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="67e8b-119">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 <span data-ttu-id="67e8b-120">[Microsoft 시퀀스 클러스터링 알고리즘](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="67e8b-120">[Microsoft Sequence Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md) </span></span>  
 [<span data-ttu-id="67e8b-121">처리 요구 사항 및 고려 사항&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="67e8b-121">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
