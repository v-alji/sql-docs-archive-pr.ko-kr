---
title: '2 단원: 타겟 메일링 구조 구축 (기본 데이터 마이닝 자습서) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9d0d6ceb-49b5-47c7-9ee6-464da43cc1f6
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 005baa09e802a9ffe98f87239070401f170ddfa9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639174"
---
# <a name="lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial"></a><span data-ttu-id="b5cb3-102">2 단원: 타겟 메일링 구조 구축 (기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="b5cb3-102">Lesson 2: Building a Targeted Mailing Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="b5cb3-103">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]의 마케팅 부서에서 특정 고객 대상의 메일 캠페인을 실시하여 판매를 증진하고자 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5cb3-103">The Marketing department of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] wants to increase sales by targeting specific customers for a mailing campaign.</span></span> <span data-ttu-id="b5cb3-104">회사의 데이터베이스에는 이전 고객의 목록과 잠재적 새 고객 목록이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5cb3-104">The company's database contains a list of past customers and a list of potential new customers.</span></span> <span data-ttu-id="b5cb3-105">회사는 이전 고객의 특성을 조사 하 여 잠재 고객에 게 적용할 수 있는 패턴을 검색 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5cb3-105">By investigating the attributes of previous customers, the company hopes to discover patterns that they can then apply to potential customers.</span></span> <span data-ttu-id="b5cb3-106">예를 들어 과거 추세를 사용 하 여 자전거를 구매할 가능성이 높은 잠재 고객을 예측 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 하거나 이후 마케팅 캠페인을 위해 고객 세그먼트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5cb3-106">For example, they might use past trends to predict which potential customers are most likely to purchase a bike from [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], or create customer segments for future marketing campaigns.</span></span>  
  
 <span data-ttu-id="b5cb3-107">이 단원에서는 **데이터 마이닝 마법사** 를 사용 하 여 타겟 메일링 구조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b5cb3-107">In this lesson you will use the **Data Mining Wizard** to create the targeted mailing structure.</span></span> <span data-ttu-id="b5cb3-108">이 단원의 태스크를 마치면 단일 모델이 있는 마이닝 구조가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b5cb3-108">After you complete the tasks in this lesson, you will have a mining structure with a single model.</span></span> <span data-ttu-id="b5cb3-109">구조 만들기와 관련된 여러 단계와 중요한 개념이 있으므로 이 프로세스를 다음 3개의 태스크로 구분했습니다.</span><span class="sxs-lookup"><span data-stu-id="b5cb3-109">Because there are many steps and important concepts involved in creating a structure, we have separated this process into the following three tasks:</span></span>  
  
 [<span data-ttu-id="b5cb3-110">기본 데이터 마이닝 자습서를 &#40;타겟 메일링 마이닝 모델 구조 만들기&#41;</span><span class="sxs-lookup"><span data-stu-id="b5cb3-110">Creating a Targeted Mailing Mining Model Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="b5cb3-111">기본 데이터 마이닝 자습서 &#40;데이터 형식 및 내용 유형 지정&#41;</span><span class="sxs-lookup"><span data-stu-id="b5cb3-111">Specifying the Data Type and Content Type &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="b5cb3-112">구조 &#40;기본 데이터 마이닝 자습서에 대 한 테스트 데이터 집합 지정&#41;</span><span class="sxs-lookup"><span data-stu-id="b5cb3-112">Specifying a Testing Data Set for the Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial.md)  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="b5cb3-113">단원의 첫 번째 태스크</span><span class="sxs-lookup"><span data-stu-id="b5cb3-113">First Task in Lesson</span></span>  
 [<span data-ttu-id="b5cb3-114">기본 데이터 마이닝 자습서를 &#40;타겟 메일링 마이닝 모델 구조 만들기&#41;</span><span class="sxs-lookup"><span data-stu-id="b5cb3-114">Creating a Targeted Mailing Mining Model Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="b5cb3-115">이전 단원</span><span class="sxs-lookup"><span data-stu-id="b5cb3-115">Previous Lesson</span></span>  
 [<span data-ttu-id="b5cb3-116">1 단원: 기본 데이터 마이닝 자습서 &#40;Analysis Services 데이터베이스 준비&#41;</span><span class="sxs-lookup"><span data-stu-id="b5cb3-116">Lesson 1: Preparing the Analysis Services Database &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-preparing-the-analysis-services-database-basic-data-mining-tutorial.md)  
  
## <a name="next--lesson"></a><span data-ttu-id="b5cb3-117">다음 단원</span><span class="sxs-lookup"><span data-stu-id="b5cb3-117">Next  Lesson</span></span>  
 [<span data-ttu-id="b5cb3-118">3단원: 모델 추가 및 처리</span><span class="sxs-lookup"><span data-stu-id="b5cb3-118">Lesson 3: Adding and Processing Models</span></span>](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="see-also"></a><span data-ttu-id="b5cb3-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5cb3-119">See Also</span></span>  
 <span data-ttu-id="b5cb3-120">[데이터 마이닝 마법사 &#40;데이터 마이닝 구조를 만듭니다&#41;](../../2014/analysis-services/create-the-data-mining-structure-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="b5cb3-120">[Create the Data Mining Structure &#40;Data Mining Wizard&#41;](../../2014/analysis-services/create-the-data-mining-structure-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="b5cb3-121">관계형 마이닝 구조 만들기</span><span class="sxs-lookup"><span data-stu-id="b5cb3-121">Create a Relational Mining Structure</span></span>](../../2014/analysis-services/data-mining/create-a-relational-mining-structure.md)  
  
  
