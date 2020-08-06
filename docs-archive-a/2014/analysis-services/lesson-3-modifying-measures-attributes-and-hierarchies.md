---
title: '3 단원: 측정값, 특성 및 계층 수정 | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 17d243cb-9bfb-43d7-8e6f-4d601fd62150
author: minewiskan
ms.author: owend
ms.openlocfilehash: c410136540a0ba85d50fbabc8b2d3c52be1823f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652424"
---
# <a name="lesson-3-modifying-measures-attributes-and-hierarchies"></a><span data-ttu-id="39871-102">3단원: 측정값, 특성 및 계층 수정</span><span class="sxs-lookup"><span data-stu-id="39871-102">Lesson 3: Modifying Measures, Attributes and Hierarchies</span></span>
  <span data-ttu-id="39871-103">처음 큐브를 정의한 후에는 큐브를 보다 유용하고 친숙하게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39871-103">After defining your initial cube, you are ready to improve the usefulness and friendliness of the cube.</span></span> <span data-ttu-id="39871-104">이렇게 하려면 다양한 수준에서 탐색 및 집계를 지원하는 계층을 추가하고 특정 측정값에 형식을 적용하고 계산 및 관계를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39871-104">You can do this by adding hierarchies that support navigation and aggregation at various levels, by applying formats to specific measure, and by defining calculations and relationships.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39871-105">이 자습서의 모든 단원에 대한 완료된 프로젝트를 온라인으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39871-105">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="39871-106">이전 단원에서 완료된 프로젝트를 시작 지점으로 사용하여 어떠한 단원으로든 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39871-106">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="39871-107">이 자습서와 함께 제공되는 샘플 프로젝트를 다운로드하려면[여기를 클릭](https://go.microsoft.com/fwlink/?LinkID=221866) 하십시오.</span><span class="sxs-lookup"><span data-stu-id="39871-107">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="39871-108">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="39871-108">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="39871-109">측정값 수정</span><span class="sxs-lookup"><span data-stu-id="39871-109">Modifying Measures</span></span>](lesson-3-1-modifying-measures.md)  
 <span data-ttu-id="39871-110">이 태스크에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 통화 및 백분율 측정값에 대한 서식 속성을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="39871-110">In this task, you specify formatting properties for the currency and percentage measures in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>  
  
 [<span data-ttu-id="39871-111">Customer 차원 수정</span><span class="sxs-lookup"><span data-stu-id="39871-111">Modifying the Customer Dimension</span></span>](lesson-3-2-modifying-the-customer-dimension.md)  
 <span data-ttu-id="39871-112">이 태스크에서는 사용자 계층을 정의하고, 명명된 계산을 만들고, 명명된 계산을 사용하도록 특성을 수정하고, 표시 폴더에 특성과 사용자 계층을 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="39871-112">In this task, you define a user hierarchy, create named calculations, modify attributes to use named calculations, and group attributes and user hierarchies into display folders.</span></span>  
  
 [<span data-ttu-id="39871-113">Product 차원 수정</span><span class="sxs-lookup"><span data-stu-id="39871-113">Modifying the Product Dimension</span></span>](lesson-3-3-modifying-the-product-dimension.md)  
 <span data-ttu-id="39871-114">이 태스크에서는 사용자 계층을 정의하고, 명명된 계산을 만들고, All 멤버 이름을 정의하고, 표시 폴더를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="39871-114">In this task, you define a user hierarchy, create named calculations, define the All member name, and define display folders.</span></span>  
  
 [<span data-ttu-id="39871-115">Date 차원 수정</span><span class="sxs-lookup"><span data-stu-id="39871-115">Modifying the Date Dimension</span></span>](lesson-3-4-modifying-the-date-dimension.md)  
 <span data-ttu-id="39871-116">이 태스크에서는 사용자 계층을 정의하고, 특성 멤버 이름을 수정하고, 복합 키를 사용하여 고유 특성 멤버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="39871-116">In this task, you define a user hierarchy, modify attribute member names, and use composite keys to specify unique attribute members.</span></span>  
  
 [<span data-ttu-id="39871-117">배포된 큐브 찾아보기</span><span class="sxs-lookup"><span data-stu-id="39871-117">Browsing the Deployed Cube</span></span>](lesson-3-5-browsing-the-deployed-cube.md)  
 <span data-ttu-id="39871-118">이 태스크에서는 큐브 디자이너의 브라우저를 사용하여 큐브 데이터를 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="39871-118">In this task, you browse cube data by using the browser in Cube Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39871-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="39871-119">See Also</span></span>  
 <span data-ttu-id="39871-120">[Analysis Services 자습서 시나리오](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="39871-120">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 [<span data-ttu-id="39871-121">다차원 모델링&#40;Adventure Works 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="39871-121">Multidimensional Modeling &#40;Adventure Works Tutorial&#41;</span></span>](multidimensional-modeling-adventure-works-tutorial.md)  
  
  
