---
title: '8 단원: 동작 정의 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 15459396-83c9-48a0-b10a-99ae38768c79
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4d4daaed3f1992478b309529fc15e2e903a27920
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737167"
---
# <a name="lesson-8-defining-actions"></a><span data-ttu-id="c3a75-102">8단원: 작업 정의</span><span class="sxs-lookup"><span data-stu-id="c3a75-102">Lesson 8: Defining Actions</span></span>
  <span data-ttu-id="c3a75-103">이 단원에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트에 동작을 정의하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="c3a75-103">In this lesson, you will learn to define actions in your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="c3a75-104">동작은 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에 저장되며 클라이언트 애플리케이션에 통합되고 사용자가 시작할 수 있는 MDX(Multidimensional Expressions) 문입니다.</span><span class="sxs-lookup"><span data-stu-id="c3a75-104">An action is just a Multidimensional Expressions (MDX) statement that is stored in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and which can be incorporated into client applications and started by a user.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3a75-105">이 자습서의 모든 단원에 대한 완료된 프로젝트를 온라인으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a75-105">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="c3a75-106">이전 단원에서 완료된 프로젝트를 시작 지점으로 사용하여 어떠한 단원으로든 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a75-106">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="c3a75-107">이 자습서와 함께 제공되는 샘플 프로젝트를 다운로드하려면[여기를 클릭](https://go.microsoft.com/fwlink/?LinkID=221866) 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c3a75-107">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="c3a75-108">에서는 다음 표에 설명된 동작 유형을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a75-108">supports the types of actions that are described in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c3a75-109">명령줄</span><span class="sxs-lookup"><span data-stu-id="c3a75-109">CommandLine</span></span>|<span data-ttu-id="c3a75-110">명령 프롬프트에서 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a75-110">Executes a command at the command prompt</span></span>|  
|<span data-ttu-id="c3a75-111">데이터 세트</span><span class="sxs-lookup"><span data-stu-id="c3a75-111">Dataset</span></span>|<span data-ttu-id="c3a75-112">데이터 세트를 클라이언트 애플리케이션으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a75-112">Returns a dataset to a client application.</span></span>|  
|<span data-ttu-id="c3a75-113">드릴스루</span><span class="sxs-lookup"><span data-stu-id="c3a75-113">Drillthrough</span></span>|<span data-ttu-id="c3a75-114">행 집합을 반환하기 위해 클라이언트가 실행하는 드릴스루 문을 식으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a75-114">Returns a drillthrough statement as an expression, which the client executes to return a rowset</span></span>|  
|<span data-ttu-id="c3a75-115">Html</span><span class="sxs-lookup"><span data-stu-id="c3a75-115">Html</span></span>|<span data-ttu-id="c3a75-116">인터넷 브라우저에서 HTML 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a75-116">Executes an HTML script in an Internet browser</span></span>|  
|<span data-ttu-id="c3a75-117">소유</span><span class="sxs-lookup"><span data-stu-id="c3a75-117">Proprietary</span></span>|<span data-ttu-id="c3a75-118">이 표에 나열되지 않은 인터페이스를 사용하여 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a75-118">Performs an operation by using an interface other than those listed in this table.</span></span>|  
|<span data-ttu-id="c3a75-119">보고서</span><span class="sxs-lookup"><span data-stu-id="c3a75-119">Report</span></span>|<span data-ttu-id="c3a75-120">매개 변수가 있는 URL 기반 요청을 보고서 서버로 전송하고 보고서를 클라이언트 애플리케이션으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a75-120">Submits a parameterized URL-based request to a report server and returns a report to a client application.</span></span>|  
|<span data-ttu-id="c3a75-121">행 집합</span><span class="sxs-lookup"><span data-stu-id="c3a75-121">Rowset</span></span>|<span data-ttu-id="c3a75-122">행 집합을 클라이언트 애플리케이션으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a75-122">Returns a rowset to a client application.</span></span>|  
|<span data-ttu-id="c3a75-123">문</span><span class="sxs-lookup"><span data-stu-id="c3a75-123">Statement</span></span>|<span data-ttu-id="c3a75-124">OLE DB 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a75-124">Runs an OLE DB command.</span></span>|  
|<span data-ttu-id="c3a75-125">URL</span><span class="sxs-lookup"><span data-stu-id="c3a75-125">URL</span></span>|<span data-ttu-id="c3a75-126">동적 웹 페이지를 인터넷 브라우저로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a75-126">Displays a dynamic Web page in an Internet browser.</span></span>|  
  
 <span data-ttu-id="c3a75-127">동작을 사용하여 애플리케이션을 시작하거나 선택한 항목의 컨텍스트 내에서 다른 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a75-127">Actions let users start an application or perform other steps within the context of a selected item.</span></span> <span data-ttu-id="c3a75-128">자세한 내용은 [동작&#40;Analysis Services - 다차원 데이터&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md)및 [다차원 모델의 동작](multidimensional-models/actions-in-multidimensional-models.md)</span><span class="sxs-lookup"><span data-stu-id="c3a75-128">For more information, see [Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md), [Actions in Multidimensional Models](multidimensional-models/actions-in-multidimensional-models.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3a75-129">동작의 예는 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 예제 데이터 웨어하우스에 있는 예나 계산 도구 창의 템플릿 탭에 있는 동작 예를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c3a75-129">For examples of actions, see the action examples on the Templates tab in the Calculation Tools pane or in the examples in the [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW sample data warehouse.</span></span> <span data-ttu-id="c3a75-130">이 데이터베이스를 설치하는 방법에 대한 자세한 내용은 [Analysis Services 다차원 모델링 자습서에 사용할 샘플 데이터 및 프로젝트 설치](install-sample-data-and-projects.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c3a75-130">For more information about installing this database, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).</span></span>  
  
 <span data-ttu-id="c3a75-131">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="c3a75-131">This lesson includes the following task:</span></span>  
  
 [<span data-ttu-id="c3a75-132">드릴스루 동작 정의 및 사용</span><span class="sxs-lookup"><span data-stu-id="c3a75-132">Defining and Using a Drillthrough Action</span></span>](lesson-8-1-defining-and-using-a-drillthrough-action.md)  
 <span data-ttu-id="c3a75-133">이 태스크에서는 자습서 앞부분에서 정의한 팩트 차원 관계를 통해 드릴스루 동작을 정의, 사용 및 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a75-133">In this task, you define, use, and then modify a drillthrough action through the fact dimension relationship that you defined earlier in this tutorial.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="c3a75-134">다음 단원</span><span class="sxs-lookup"><span data-stu-id="c3a75-134">Next Lesson</span></span>  
 [<span data-ttu-id="c3a75-135">9단원: 큐브 뷰 및 번역 정의</span><span class="sxs-lookup"><span data-stu-id="c3a75-135">Lesson 9: Defining Perspectives and Translations</span></span>](lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a><span data-ttu-id="c3a75-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3a75-136">See Also</span></span>  
 <span data-ttu-id="c3a75-137">[Analysis Services 자습서 시나리오](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="c3a75-137">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="c3a75-138">[&#40;의 다차원 모델링은 놀이 Works 자습서&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="c3a75-138">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 <span data-ttu-id="c3a75-139">[작업 &#40;Analysis Services 다차원 데이터&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c3a75-139">[Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="c3a75-140">다차원 모델의 동작</span><span class="sxs-lookup"><span data-stu-id="c3a75-140">Actions in Multidimensional Models</span></span>](multidimensional-models/actions-in-multidimensional-models.md)  
  
  
