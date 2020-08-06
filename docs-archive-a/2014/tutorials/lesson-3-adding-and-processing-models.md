---
title: '3 단원: 모델 추가 및 처리 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: cc29927a-c368-4b8a-bbd0-af89a9f54dc9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5da034089d8bbe7f1a967258d195a56ddbf13c03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646744"
---
# <a name="lesson-3-adding-and-processing-models"></a><span data-ttu-id="ae052-102">3단원: 모델 추가 및 처리</span><span class="sxs-lookup"><span data-stu-id="ae052-102">Lesson 3: Adding and Processing Models</span></span>
  <span data-ttu-id="ae052-103">이전 단원에서 만든 마이닝 구조에는 [!INCLUDE[msCoName](../includes/msconame-md.md)] 의사 결정 트리 알고리즘에 기반한 단일 마이닝 모델이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae052-103">The mining structure that you created in the previous lesson contains a single mining model that is based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="ae052-104">이 모델을 사용하여 타겟 메일링 캠페인을 위한 고객을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae052-104">You can use this model to identify customers for the targeted mailing campaign.</span></span> <span data-ttu-id="ae052-105">그러나 철저한 분석을 위해서는 다양한 알고리즘을 사용하여 관련 모델을 만들고 결과를 비교하는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="ae052-105">However, to ensure that your analysis is thorough, it is a common practice to create related models using different algorithms and compare their results.</span></span> <span data-ttu-id="ae052-106">이 방법으로 다양한 이해도 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae052-106">That way you can get different insights as well.</span></span> <span data-ttu-id="ae052-107">따라서 두 개의 추가 모델을 만든 다음 모델을 처리하고 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="ae052-107">Therefore, you will create two additional models, then process and deploy the models.</span></span>  
  
 <span data-ttu-id="ae052-108">이 단원에서는 잠재 고객 목록에서 가장 가능성이 높은 고객을 제안할 마이닝 모델 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ae052-108">In this lesson, you will create a set of mining models that will suggest the most likely customers from a list of potential customers.</span></span>  
  
 <span data-ttu-id="ae052-109">이 단원의 태스크를 완료하기 위해 [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md) 및 [Microsoft Naive Bayes Algorithm](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ae052-109">To complete the tasks in this lesson, you will use the [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md) and the [Microsoft Naive Bayes Algorithm](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md).</span></span>  
  
 <span data-ttu-id="ae052-110">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="ae052-110">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="ae052-111">&#40;기본 데이터 마이닝 자습서를 대상으로 지정 된 메일링 구조에 새 모델 추가&#41;</span><span class="sxs-lookup"><span data-stu-id="ae052-111">Adding New Models to the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="ae052-112">기본 데이터 마이닝 자습서 &#40;대상 메일 구조에서 모델 처리&#41;</span><span class="sxs-lookup"><span data-stu-id="ae052-112">Processing Models in the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="ae052-113">단원의 첫 번째 태스크</span><span class="sxs-lookup"><span data-stu-id="ae052-113">First Task in Lesson</span></span>  
 [<span data-ttu-id="ae052-114">&#40;기본 데이터 마이닝 자습서를 대상으로 지정 된 메일링 구조에 새 모델 추가&#41;</span><span class="sxs-lookup"><span data-stu-id="ae052-114">Adding New Models to the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="ae052-115">이전 단원</span><span class="sxs-lookup"><span data-stu-id="ae052-115">Previous Lesson</span></span>  
 [<span data-ttu-id="ae052-116">2 단원: 기본 데이터 마이닝 자습서 &#40;대상 메일링 구조 구축&#41;</span><span class="sxs-lookup"><span data-stu-id="ae052-116">Lesson 2: Building a Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="ae052-117">다음 단원</span><span class="sxs-lookup"><span data-stu-id="ae052-117">Next Lesson</span></span>  
 [<span data-ttu-id="ae052-118">4 단원: 기본 데이터 마이닝 자습서 &#40;대상 메일링 모델 탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="ae052-118">Lesson 4: Exploring the Targeted Mailing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="ae052-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ae052-119">See Also</span></span>  
 [<span data-ttu-id="ae052-120">구조에 마이닝 모델 추가&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="ae052-120">Add Mining Models to a Structure &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md)  
  
  
