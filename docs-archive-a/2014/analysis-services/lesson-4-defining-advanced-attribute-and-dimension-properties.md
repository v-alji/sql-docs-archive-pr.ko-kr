---
title: '4 단원: 고급 특성 및 차원 속성 정의 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0e86b9be-e47d-4bb4-87eb-136ff3a61aef
author: minewiskan
ms.author: owend
ms.openlocfilehash: deb2d9c40ad5024f6cc4ba6e9148df41a168c6e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734555"
---
# <a name="lesson-4-defining-advanced-attribute-and-dimension-properties"></a><span data-ttu-id="1479a-102">4단원: 고급 특성 및 차원 속성 정의</span><span class="sxs-lookup"><span data-stu-id="1479a-102">Lesson 4: Defining Advanced Attribute and Dimension Properties</span></span>
  <span data-ttu-id="1479a-103">이 단원에서는 특성의 일부 고급 속성, 특성 계층 및 차원 속성을 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1479a-103">In this lesson, you will learn how to use some of the advanced properties of attributes, attribute hierarchies, and dimension properties.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1479a-104">이 단원은 본 자습서의 1 - 3단원에서 작성한 향상된 버전의 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1479a-104">This lesson is based on an enhanced version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project that you completed in the first three lessons of this tutorial.</span></span> <span data-ttu-id="1479a-105">이 단원의 첫 번째 태스크에서는 단원에 사용할 적절한 예제 프로젝트를 찾을 위치 및 이 프로젝트와 1 - 3단원에서 만든 프로젝트 간 차이점에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1479a-105">The first task in this lesson describes where to locate the appropriate sample project to use for the lesson, and the difference between this project and the project that you created in the first three lessons.</span></span>  
  
 <span data-ttu-id="1479a-106">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="1479a-106">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="1479a-107">Analysis Services Tutorial 프로젝트의 수정된 버전 사용</span><span class="sxs-lookup"><span data-stu-id="1479a-107">Using a Modified Version of the Analysis Services Tutorial Project</span></span>](lesson-4-1-using-a-modified-version-of-the-analysis-services-tutorial-project.md)  
 <span data-ttu-id="1479a-108">이 태스크에서는 여러 측정값 그룹과 추가 차원이 있는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트의 수정된 버전을 열어서 검토하고 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="1479a-108">In this task, you open, review, and deploy a modified version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, which has multiple measure groups and additional dimensions.</span></span>  
  
 [<span data-ttu-id="1479a-109">부모-자식 계층의 부모 특성 속성 정의</span><span class="sxs-lookup"><span data-stu-id="1479a-109">Defining Parent Attribute Properties in a Parent-Child Hierarchy</span></span>](lesson-4-2-defining-parent-attribute-properties-in-a-parent-child-hierarchy.md)  
 <span data-ttu-id="1479a-110">이 태스크에서는 부모-자식 차원의 수준 이름을 정의하고 부모 멤버에 관련된 데이터의 표시 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1479a-110">In this task, you define level names in a parent-child dimension and specify whether data related to parent members is displayed.</span></span> <span data-ttu-id="1479a-111">자세한 내용은 부모-자식 [계층](multidimensional-models/parent-child-dimension.md) 및 부모 [-자식 계층의 특성](multidimensional-models/parent-child-dimension-attributes.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1479a-111">For more information, see [Parent-Child Hierarchy](multidimensional-models/parent-child-dimension.md) and [Attributes in Parent-Child Hierarchies](multidimensional-models/parent-child-dimension-attributes.md).</span></span>  
  
 [<span data-ttu-id="1479a-112">자동으로 특성 멤버 그룹화</span><span class="sxs-lookup"><span data-stu-id="1479a-112">Automatically Grouping Attribute Members</span></span>](lesson-4-3-automatically-grouping-attribute-members.md)  
 <span data-ttu-id="1479a-113">이 태스크에서는 특성 계층 내에서 멤버의 분포에 따라 특성 멤버 그룹을 자동으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1479a-113">In this task, you automatically create groupings of attribute members based on the distribution of the members within the attribute hierarchy.</span></span> <span data-ttu-id="1479a-114">자세한 내용은 [특성 멤버 그룹화&#40;불연속화&#41;](multidimensional-models/attribute-properties-group-attribute-members.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1479a-114">For more information, see [Group Attribute Members &#40;Discretization&#41;](multidimensional-models/attribute-properties-group-attribute-members.md).</span></span>  
  
 [<span data-ttu-id="1479a-115">특성 계층 숨기기 및 비활성화</span><span class="sxs-lookup"><span data-stu-id="1479a-115">Hiding and Disabling Attribute Hierarchies</span></span>](lesson-4-4-hiding-and-disabling-attribute-hierarchies.md)  
 <span data-ttu-id="1479a-116">이 태스크에서는 특성 계층을 해제하거나 숨기는 방법과 시기에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="1479a-116">In this task, you learn how and when to disable or hide attribute hierarchies.</span></span>  
  
 [<span data-ttu-id="1479a-117">보조 특성을 기준으로 특성 멤버 정렬</span><span class="sxs-lookup"><span data-stu-id="1479a-117">Sorting Attribute Members Based on a Secondary Attribute</span></span>](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md)  
 <span data-ttu-id="1479a-118">이 태스크에서는 보조 특성에 따라 차원 멤버를 정렬하여 원하는 대로 정렬하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="1479a-118">In this task, you learn how to sort dimension members based on a secondary attribute, to achieve the sort order that you want.</span></span>  
  
 [<span data-ttu-id="1479a-119">사용자 정의 계층의 특성 간 특성 관계 지정</span><span class="sxs-lookup"><span data-stu-id="1479a-119">Specifying Attribute Relationships Between Attributes in a User-Defined Hierarchy</span></span>](4-6-specifying-attribute-relationships-in-user-defined-hierarchy.md)  
 <span data-ttu-id="1479a-120">이 태스크에서는 특성에 대한 멤버 속성을 정의하고 특성 간 집계 관계를 지정하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="1479a-120">In this task, you learn how to define member properties for attributes and to specify aggregation relationships between them.</span></span> <span data-ttu-id="1479a-121">자세한 내용은 [특성 관계 정의](multidimensional-models/attribute-relationships-define.md) 및 [사용자 계층 속성](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1479a-121">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) and [User Hierarchy Properties](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md).</span></span>  
  
 [<span data-ttu-id="1479a-122">알 수 없는 멤버 및 Null 처리 속성 정의</span><span class="sxs-lookup"><span data-stu-id="1479a-122">Defining the Unknown Member and Null Processing Properties</span></span>](lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md)  
 <span data-ttu-id="1479a-123">이 태스크에서는 UnknownMember 및 UnknownMemberName 속성을 구성하여 Null 차원 멤버가 발생시킨 오류 조건을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="1479a-123">In this task, you configure the UnknownMember and UnknownMemberName properties to handle error conditions caused by null dimension members.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="1479a-124">다음 단원</span><span class="sxs-lookup"><span data-stu-id="1479a-124">Next Lesson</span></span>  
 [<span data-ttu-id="1479a-125">5단원: 차원과 측정값 그룹의 관계 정의</span><span class="sxs-lookup"><span data-stu-id="1479a-125">Lesson 5: Defining Relationships Between Dimensions and Measure Groups</span></span>](lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)  
  
## <a name="see-also"></a><span data-ttu-id="1479a-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1479a-126">See Also</span></span>  
 <span data-ttu-id="1479a-127">[Analysis Services 자습서 시나리오](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="1479a-127">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="1479a-128">[&#40;의 다차원 모델링은 놀이 Works 자습서&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="1479a-128">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 [<span data-ttu-id="1479a-129">다차원 모델의 차원</span><span class="sxs-lookup"><span data-stu-id="1479a-129">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
