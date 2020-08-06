---
title: '9 단원: 큐브 뷰 및 번역 정의 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a040fa65-d5d6-4156-9f2c-307a4d18e1a6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6a36449eb3156d9ff52d6cc7085f9e0cb929b51e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732171"
---
# <a name="lesson-9-defining-perspectives-and-translations"></a><span data-ttu-id="9bd1b-102">9단원: 큐브 뷰 및 번역 정의</span><span class="sxs-lookup"><span data-stu-id="9bd1b-102">Lesson 9: Defining Perspectives and Translations</span></span>
  <span data-ttu-id="9bd1b-103">이 단원에서는 큐브 뷰 및 번역을 정의하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="9bd1b-103">In this lesson, you learn to define perspectives and translations.</span></span> <span data-ttu-id="9bd1b-104">큐브 뷰를 정의하여 큐브의 복잡성을 줄이고 사용자들이 선택한 언어로 큐브 메타데이터를 볼 수 있도록 하는 번역을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd1b-104">You can define perspectives to reduce the apparent complexity of a cube, and define translations that let users view the cube metadata in the language of their choice.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9bd1b-105">이 자습서의 모든 단원에 대한 완료된 프로젝트를 온라인으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd1b-105">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="9bd1b-106">이전 단원에서 완료된 프로젝트를 시작 지점으로 사용하여 어떠한 단원으로든 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd1b-106">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="9bd1b-107">이 자습서와 함께 제공되는 샘플 프로젝트를 다운로드하려면[여기를 클릭](https://go.microsoft.com/fwlink/?LinkID=221866) 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9bd1b-107">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="9bd1b-108">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="9bd1b-108">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="9bd1b-109">큐브 뷰 정의 및 찾아보기</span><span class="sxs-lookup"><span data-stu-id="9bd1b-109">Defining and Browsing Perspectives</span></span>](multidimensional-models-olap-logical-cube-objects/perspectives.md)  
 <span data-ttu-id="9bd1b-110">이 태스크에서는 큐브 뷰를 정의하고 검색하여 특정 사용자나 사용에 대해 표시되는 큐브 뷰를 단순화합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd1b-110">In this task, you define and browse perspectives to simplify the view of the cube for specific users or uses.</span></span>  
  
 [<span data-ttu-id="9bd1b-111">번역 정의 및 찾아보기</span><span class="sxs-lookup"><span data-stu-id="9bd1b-111">Defining and Browsing Translations</span></span>](lesson-9-2-defining-and-browsing-translations.md)  
 <span data-ttu-id="9bd1b-112">이 태스크에서는 특정 언어로의 특정 메타데이터 번역을 정의하고 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd1b-112">In this task, you define and browse translations of specific metadata to certain languages.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="9bd1b-113">다음 단원</span><span class="sxs-lookup"><span data-stu-id="9bd1b-113">Next Lesson</span></span>  
 [<span data-ttu-id="9bd1b-114">10단원: 관리자 역할 정의</span><span class="sxs-lookup"><span data-stu-id="9bd1b-114">Lesson 10: Defining Administrative Roles</span></span>](lesson-10-defining-administrative-roles.md)  
  
## <a name="see-also"></a><span data-ttu-id="9bd1b-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9bd1b-115">See Also</span></span>  
 <span data-ttu-id="9bd1b-116">[Analysis Services 자습서 시나리오](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="9bd1b-116">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="9bd1b-117">[&#40;의 다차원 모델링은 놀이 Works 자습서&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="9bd1b-117">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 <span data-ttu-id="9bd1b-118">[전망을](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-cube-objects/perspectives) </span><span class="sxs-lookup"><span data-stu-id="9bd1b-118">[Perspectives](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-cube-objects/perspectives) </span></span>  
 <span data-ttu-id="9bd1b-119">[다차원 모델의 큐브 뷰](multidimensional-models/perspectives-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="9bd1b-119">[Perspectives in Multidimensional Models](multidimensional-models/perspectives-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="9bd1b-120">[차원 번역](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md) </span><span class="sxs-lookup"><span data-stu-id="9bd1b-120">[Dimension Translations](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md) </span></span>  
 <span data-ttu-id="9bd1b-121">[큐브 번역](multidimensional-models-olap-logical-cube-objects/cube-translations.md) </span><span class="sxs-lookup"><span data-stu-id="9bd1b-121">[Cube Translations](multidimensional-models-olap-logical-cube-objects/cube-translations.md) </span></span>  
 [<span data-ttu-id="9bd1b-122">번역 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="9bd1b-122">Translations &#40;Analysis Services&#41;</span></span>](translations-analysis-services.md)  
  
  
