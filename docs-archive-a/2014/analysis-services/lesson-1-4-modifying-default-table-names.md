---
title: 기본 테이블 이름 수정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ddd97483-a76d-43c1-8b40-fc7cc57fb0c2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 254f797be95f60211983400b019415431d4cf39c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639060"
---
# <a name="modifying-default-table-names"></a><span data-ttu-id="d94ab-102">기본 테이블 이름 수정</span><span class="sxs-lookup"><span data-stu-id="d94ab-102">Modifying Default Table Names</span></span>
  <span data-ttu-id="d94ab-103">데이터 원본 뷰에서 개체에 대한 **FriendlyName** 속성의 값을 변경하여 알아보기 쉽고 사용이 간편한 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d94ab-103">You can change the value of the **FriendlyName** property for objects in the data source view to make them easier to notice and use.</span></span>  
  
 <span data-ttu-id="d94ab-104">아래의 태스크에서 데이터 원본 뷰에 있는 각 테이블의 이름에서 "**Dim**" 및 "**Fact**" 접두사를 제거하여 테이블의 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d94ab-104">In the following task, you will change the friendly name of each table in the data source view by removing the "**Dim**" and "**Fact**" prefixes from these tables.</span></span> <span data-ttu-id="d94ab-105">이렇게 하면 다음 단원에서 정의하게 될 큐브 및 차원 개체를 알아보기 쉽고 사용이 간편하게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d94ab-105">This will make the cube and dimension objects (that you will define in the next lesson) easier to notice and use.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d94ab-106">또한 열의 이름을 변경하고, 계산 열을 정의하고, 데이터 원본 뷰에 있는 테이블이나 뷰를 조인하여 사용하기 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d94ab-106">You can also change the friendly names of columns, define calculated columns, and join tables or views in the data source view to make them easier to use.</span></span>  
  
### <a name="to-modify-the-default-name-of-a-table"></a><span data-ttu-id="d94ab-107">테이블의 기본 이름을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="d94ab-107">To modify the default name of a table</span></span>  
  
1.  <span data-ttu-id="d94ab-108">**데이터 원본 뷰 디자이너** 의 **테이블**창에서 **FactInternetSales** 테이블을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d94ab-108">In the **Tables** pane of **Data Source View Designer**, right-click the **FactInternetSales** table, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="d94ab-109">Microsoft Visual Studio 창의 오른쪽에 속성 창이 표시되지 않으면 속성 창의 제목 표시줄에서 **자동 숨기기** 를 클릭하여 속성 창이 계속 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d94ab-109">If the Properties window on the right side of the Microsoft Visual Studio window is not displayed, click the **Auto Hide** button on the title bar of the Properties window so that this window remains visible.</span></span>  
  
     <span data-ttu-id="d94ab-110">속성 창이 계속 열려 있으면 데이터 원본 뷰에 있는 각 테이블에 대한 속성을 보다 쉽게 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d94ab-110">It is easier to change the properties for each table in the data source view when the Properties window remains open.</span></span> <span data-ttu-id="d94ab-111">**자동 숨기기** 단추를 사용하여 속성 창을 계속 열어 놓지 않으면 **다이어그램** 창에서 다른 개체를 클릭할 때 창이 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="d94ab-111">If you do not pin the window open by using the **Auto Hide** button, the window will close when you click a different object in the **Diagram** pane.</span></span>  
  
3.  <span data-ttu-id="d94ab-112">**FactInternetSales** 개체에 대 한 **FriendlyName** 속성을로 변경 합니다 *`InternetSales`* .</span><span class="sxs-lookup"><span data-stu-id="d94ab-112">Change the **FriendlyName** property for the **FactInternetSales** object to *`InternetSales`*.</span></span>  
  
     <span data-ttu-id="d94ab-113">**FriendlyName** 속성의 셀에서 떨어진 곳을 클릭하면 변경 내용이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d94ab-113">When you click away from the cell for the **FriendlyName** property, the change is applied.</span></span> <span data-ttu-id="d94ab-114">다음 단원에서는 이 팩트 테이블을 기반으로 하는 측정값 그룹을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d94ab-114">In the next lesson, you will define a measure group that is based on this fact table.</span></span> <span data-ttu-id="d94ab-115">이 단원에서 수행한 변경 작업으로 인해 팩트 테이블의 이름은 FactInternetSales가 아닌 InternetSales가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d94ab-115">The name of the fact table will be InternetSales instead of FactInternetSales because of the change you made in this lesson.</span></span>  
  
4.  <span data-ttu-id="d94ab-116">**테이블** 창에서 **DimProduct** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d94ab-116">Click **DimProduct** in the **Tables** pane.</span></span> <span data-ttu-id="d94ab-117">속성 창에서 **FriendlyName** 속성을로 변경 합니다 *`Product`* .</span><span class="sxs-lookup"><span data-stu-id="d94ab-117">In the Properties window, change the **FriendlyName** property to *`Product`*.</span></span>  
  
5.  <span data-ttu-id="d94ab-118">데이터 원본 뷰에 있는 나머지 테이블 각각의 **FriendlyName** 속성도 같은 방법으로 변경합니다. 즉 "**Dim**" 접두사를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="d94ab-118">Change the **FriendlyName** property of each remaining table in the data source view in the same way, to remove the "**Dim**" prefix.</span></span>  
  
6.  <span data-ttu-id="d94ab-119">다 변경했으면 **자동 숨기기** 단추를 클릭하여 속성 창을 다시 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="d94ab-119">When you have finished, click the **Auto Hide** button to hide the Properties window again.</span></span>  
  
7.  <span data-ttu-id="d94ab-120">**파일** 메뉴 또는 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]의 도구 모음에서 **모두 저장** 을 클릭하여 지금까지의 변경 내용을 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d94ab-120">On the **File** menu, or on the toolbar of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Save All** to save the changes you have made to this point in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project.</span></span> <span data-ttu-id="d94ab-121">원할 경우 여기에서 자습서를 중지했다가 나중에 계속 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d94ab-121">You can stop the tutorial here if you want and resume it later.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="d94ab-122">다음 단원</span><span class="sxs-lookup"><span data-stu-id="d94ab-122">Next Lesson</span></span>  
 [<span data-ttu-id="d94ab-123">2단원: 큐브 정의 및 배포</span><span class="sxs-lookup"><span data-stu-id="d94ab-123">Lesson 2: Defining and Deploying a Cube</span></span>](lesson-2-defining-and-deploying-a-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="d94ab-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d94ab-124">See Also</span></span>  
 <span data-ttu-id="d94ab-125">[다차원 모델의 데이터 원본 뷰](multidimensional-models/data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="d94ab-125">[Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="d94ab-126">데이터 원본 뷰에서 속성 변경&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d94ab-126">Change Properties in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/change-properties-in-a-data-source-view-analysis-services.md)  
  
  
