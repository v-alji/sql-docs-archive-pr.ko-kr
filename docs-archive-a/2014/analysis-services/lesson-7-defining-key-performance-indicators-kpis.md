---
title: '7 단원: Kpi (핵심 성과 지표) 정의 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 36d53770-294f-43ab-8850-15d5351ff60c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 87df6fd91a66505f124144cafd9a44c6e5e70e85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731027"
---
# <a name="lesson-7-defining-key-performance-indicators-kpis"></a><span data-ttu-id="88f75-102">7단원: KPI(핵심 성과 지표) 정의</span><span class="sxs-lookup"><span data-stu-id="88f75-102">Lesson 7: Defining Key Performance Indicators (KPIs)</span></span>
  <span data-ttu-id="88f75-103">이 단원에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트에서 KPI(핵심 성과 지표)를 정의하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="88f75-103">In this lesson, you learn to define Key Performance Indicators (KPIs) in your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="88f75-104">KPI는 비즈니스를 측정하는 서버 쪽 계산을 정의하기 위한 프레임워크를 제공하며 결과 정보의 표시 방식을 표준화합니다.</span><span class="sxs-lookup"><span data-stu-id="88f75-104">KPIs provide a framework for defining server-side calculations that measure your business, and they standardize how the resulting information is displayed.</span></span> <span data-ttu-id="88f75-105">KPI는 보고서, 포털 및 대시보드에 표시할 수 있으며 데이터 액세스 API, [!INCLUDE[msCoName](../includes/msconame-md.md)] 도구 및 타사 도구를 통해 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88f75-105">KPIs can be displayed in reports, portals, and dashboards, through data access APIs, and through [!INCLUDE[msCoName](../includes/msconame-md.md)] tools and third-party tools.</span></span> <span data-ttu-id="88f75-106">KPI는 정규 측정값 및 기타 MDX(Multidimensional Expressions) 식에 대한 메타데이터 래퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="88f75-106">KPIs are metadata wrappers around regular measures and other Multidimensional Expressions (MDX) expressions.</span></span> <span data-ttu-id="88f75-107">자세한 내용은 [다차원 모델의 KPI&#40;핵심 성과 지표&#41;](multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88f75-107">For more information, see [Key Performance Indicators &#40;KPIs&#41; in Multidimensional Models](multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="88f75-108">이 자습서의 모든 단원에 대한 완료된 프로젝트를 온라인으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88f75-108">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="88f75-109">이전 단원에서 완료된 프로젝트를 시작 지점으로 사용하여 어떠한 단원으로든 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88f75-109">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="88f75-110">이 자습서와 함께 제공되는 샘플 프로젝트를 다운로드하려면[여기를 클릭](https://go.microsoft.com/fwlink/?LinkID=221866) 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88f75-110">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="88f75-111">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="88f75-111">This lesson contains the following task:</span></span>  
  
 [<span data-ttu-id="88f75-112">KPI 정의 및 찾아보기</span><span class="sxs-lookup"><span data-stu-id="88f75-112">Defining and Browsing KPIs</span></span>](lesson-7-1-defining-and-browsing-kpis.md)  
 <span data-ttu-id="88f75-113">이 태스크에서는 폼 보기에서 KPI를 정의한 후 브라우저 보기로 전환하여 KPI를 사용해 큐브 데이터를 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="88f75-113">In this task, you define KPIs in the Form view and then switch to the Browser view to browse the cube data by using the KPIs.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="88f75-114">다음 단원</span><span class="sxs-lookup"><span data-stu-id="88f75-114">Next Lesson</span></span>  
 [<span data-ttu-id="88f75-115">8단원: 작업 정의</span><span class="sxs-lookup"><span data-stu-id="88f75-115">Lesson 8: Defining Actions</span></span>](lesson-8-defining-actions.md)  
  
## <a name="see-also"></a><span data-ttu-id="88f75-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="88f75-116">See Also</span></span>  
 <span data-ttu-id="88f75-117">[Analysis Services 자습서 시나리오](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="88f75-117">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="88f75-118">[&#40;의 다차원 모델링은 놀이 Works 자습서&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="88f75-118">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 [<span data-ttu-id="88f75-119">다차원 모델의 KPI&#40;핵심 성과 지표&#41;</span><span class="sxs-lookup"><span data-stu-id="88f75-119">Key Performance Indicators &#40;KPIs&#41; in Multidimensional Models</span></span>](multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)  
  
  
