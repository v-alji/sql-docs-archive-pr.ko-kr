---
title: '5 단원: 차원과 측정값 그룹 간의 관계 정의 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 31aeb271-47a1-433b-a8a5-120bcb4584d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6dbdf20e64e3cd8adc751b69122a380d7b3b3648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649789"
---
# <a name="lesson-5-defining-relationships-between-dimensions-and-measure-groups"></a><span data-ttu-id="cb9a8-102">5단원: 차원과 측정값 그룹의 관계 정의</span><span class="sxs-lookup"><span data-stu-id="cb9a8-102">Lesson 5: Defining Relationships Between Dimensions and Measure Groups</span></span>
  <span data-ttu-id="cb9a8-103">이 자습서의 이전 단원에서는 큐브에 추가한 데이터베이스 차원을 하나 이상의 큐브 차원에 대한 기준으로 사용하는 방법에 대해 설명했습니다.</span><span class="sxs-lookup"><span data-stu-id="cb9a8-103">In the previous lessons in this tutorial, you learned that database dimensions added to a cube can be used as the basis for one or more cube dimensions.</span></span> <span data-ttu-id="cb9a8-104">이 단원에서는 큐브 차원과 측정값 그룹 간에 서로 다른 유형의 관계를 정의하고 이 관계의 속성을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9a8-104">In this lesson, you learn to define different types of relationships between cube dimensions and measure groups, and to specify the properties of these relationships.</span></span>  
  
 <span data-ttu-id="cb9a8-105">자세한 내용은 [차원 관계](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb9a8-105">For more information, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb9a8-106">이 자습서의 모든 단원에 대한 완료된 프로젝트를 온라인으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb9a8-106">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="cb9a8-107">이전 단원에서 완료된 프로젝트를 시작 지점으로 사용하여 어떠한 단원으로든 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb9a8-107">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="cb9a8-108">이 자습서와 함께 제공되는 샘플 프로젝트를 다운로드하려면[여기를 클릭](https://go.microsoft.com/fwlink/?LinkID=221866) 하십시오.</span><span class="sxs-lookup"><span data-stu-id="cb9a8-108">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="cb9a8-109">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="cb9a8-109">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="cb9a8-110">참조 관계 정의</span><span class="sxs-lookup"><span data-stu-id="cb9a8-110">Defining a Referenced Relationship</span></span>](lesson-5-1-defining-a-referenced-relationship.md)  
 <span data-ttu-id="cb9a8-111">이 태스크에서는 기본 키-외래 키 관계를 통해 직접 연결 된 차원을 통해 팩트 테이블에 차원을 간접적으로 연결 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="cb9a8-111">In this task, you learn to link a dimension to a fact table indirectly through a dimension that is linked directly through a primary key-foreign key relationship.</span></span>  
  
 [<span data-ttu-id="cb9a8-112">팩트 관계 정의</span><span class="sxs-lookup"><span data-stu-id="cb9a8-112">Defining a Fact Relationship</span></span>](lesson-5-2-defining-a-fact-relationship.md)  
 <span data-ttu-id="cb9a8-113">이 태스크에서는 팩트 테이블의 데이터를 기반으로 차원을 정의하고 차원 관계를 팩트 관계로 정의하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="cb9a8-113">In this task, you learn to define a dimension based on data in the fact table, and to define the dimension relationship as a fact relationship.</span></span>  
  
 [<span data-ttu-id="cb9a8-114">다 대 다 관계 정의</span><span class="sxs-lookup"><span data-stu-id="cb9a8-114">Defining a Many-to-Many Relationship</span></span>](lesson-5-3-defining-a-many-to-many-relationship.md)  
 <span data-ttu-id="cb9a8-115">이 태스크에서는 차원 테이블과 팩트 테이블의 다 대 다 관계 정의를 통해 팩트를 여러 차원 멤버에 연결하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="cb9a8-115">In this task, you learn to relate a fact to multiple dimension members through the definition of a many-to-many relationship between dimension tables and fact tables.</span></span>  
  
 [<span data-ttu-id="cb9a8-116">측정값 그룹의 차원 세분성 정의</span><span class="sxs-lookup"><span data-stu-id="cb9a8-116">Defining Dimension Granularity within a Measure Group</span></span>](lesson-5-4-defining-dimension-granularity-within-a-measure-group.md)  
 <span data-ttu-id="cb9a8-117">이 태스크에서는 특정 측정값 그룹의 차원 세분성을 수정하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="cb9a8-117">In this task, you learn to modify the granularity of a dimension for a specific measure group.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="cb9a8-118">다음 단원</span><span class="sxs-lookup"><span data-stu-id="cb9a8-118">Next Lesson</span></span>  
 [<span data-ttu-id="cb9a8-119">6단원: 계산 정의</span><span class="sxs-lookup"><span data-stu-id="cb9a8-119">Lesson 6: Defining Calculations</span></span>](lesson-6-defining-calculations.md)  
  
## <a name="see-also"></a><span data-ttu-id="cb9a8-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cb9a8-120">See Also</span></span>  
 <span data-ttu-id="cb9a8-121">[Analysis Services 자습서 시나리오](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="cb9a8-121">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="cb9a8-122">[&#40;의 다차원 모델링은 놀이 Works 자습서&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="cb9a8-122">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 [<span data-ttu-id="cb9a8-123">차원 관계</span><span class="sxs-lookup"><span data-stu-id="cb9a8-123">Dimension Relationships</span></span>](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)  
  
  
