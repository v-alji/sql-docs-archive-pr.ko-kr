---
title: 큐브 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8aa4ac2d-857f-4048-baa0-0f314e207cf6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 354a05840dd2e091f956454858edd5c75c8c4bdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639040"
---
# <a name="defining-a-cube"></a><span data-ttu-id="93bc0-102">큐브 정의</span><span class="sxs-lookup"><span data-stu-id="93bc0-102">Defining a Cube</span></span>
  <span data-ttu-id="93bc0-103">큐브 마법사를 통해 큐브에 대한 측정값 그룹과 차원을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-103">The Cube Wizard helps you define the measure groups and dimensions for a cube.</span></span> <span data-ttu-id="93bc0-104">다음 태스크에서는 큐브 마법사를 사용하여 큐브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-104">In the following task, you will use the Cube Wizard to build a cube.</span></span>  
  
### <a name="to-define-a-cube-and-its-properties"></a><span data-ttu-id="93bc0-105">큐브 및 해당 속성을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="93bc0-105">To define a cube and its properties</span></span>  
  
1.  <span data-ttu-id="93bc0-106">솔루션 탐색기에서 **큐브**를 마우스 오른쪽 단추로 클릭한 다음 **새 큐브**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-106">In Solution Explorer, right-click **Cubes**, and then click **New Cube**.</span></span> <span data-ttu-id="93bc0-107">큐브 마법사가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-107">The Cube Wizard appears.</span></span>  
  
2.  <span data-ttu-id="93bc0-108">**큐브 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-108">On the **Welcome to the Cube Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="93bc0-109">**생성 방법 선택** 페이지에서 **기존 테이블 사용** 옵션이 선택되어 있는지 확인하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-109">On the **Select Creation Method** page, verify that the **Use existing tables** option is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="93bc0-110">**측정값 그룹 테이블 선택** 페이지에서 **Adventure Works DW 2012** 데이터 원본 뷰가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-110">On the **Select Measure Group Tables** page, verify that the **Adventure Works DW 2012** data source view is selected.</span></span>  
  
5.  <span data-ttu-id="93bc0-111">**제안** 을 클릭하여 측정값 그룹을 만드는 데 사용할 테이블을 큐브 마법사가 제안하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-111">Click **Suggest** to have the cube wizard suggest tables to use to create measure groups.</span></span>  
  
     <span data-ttu-id="93bc0-112">마법사는 테이블을 검사한 후 **InternetSales** 를 측정값 그룹 테이블로 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-112">The wizard examines the tables and suggests **InternetSales** as a measure group table.</span></span> <span data-ttu-id="93bc0-113">팩트 테이블이라고도 하는 측정값 그룹 테이블에는 판매된 단위의 수와 같이 사용자가 관심을 가지는 측정값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-113">Measure group tables, also called fact tables, contain the measures you are interested in, such as the number of units sold.</span></span>  
  
6.  <span data-ttu-id="93bc0-114">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-114">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="93bc0-115">**측정값 선택** 페이지에서 **Internet Sales** 측정값 그룹에서 선택한 측정값을 검토한 후 다음과 같은 측정값 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-115">On the **Select Measures** page, review the selected measures in the **Internet Sales** measure group, and then clear the check boxes for the following measures:</span></span>  
  
    -   <span data-ttu-id="93bc0-116">**Promotion Key**</span><span class="sxs-lookup"><span data-stu-id="93bc0-116">**Promotion Key**</span></span>  
  
    -   <span data-ttu-id="93bc0-117">**Currency Key**</span><span class="sxs-lookup"><span data-stu-id="93bc0-117">**Currency Key**</span></span>  
  
    -   <span data-ttu-id="93bc0-118">**Sales Territory Key**</span><span class="sxs-lookup"><span data-stu-id="93bc0-118">**Sales Territory Key**</span></span>  
  
    -   <span data-ttu-id="93bc0-119">**Revision Number**</span><span class="sxs-lookup"><span data-stu-id="93bc0-119">**Revision Number**</span></span>  
  
     <span data-ttu-id="93bc0-120">기본적으로 마법사에서는 차원에 연결되지 않은 팩트 테이블의 모든 숫자 열을 측정값으로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-120">By default, the wizard selects as measures all numeric columns in the fact table that are not linked to dimensions.</span></span> <span data-ttu-id="93bc0-121">그러나 이러한 4개의 열은 실제 측정값이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-121">However, these four columns are not actual measures.</span></span> <span data-ttu-id="93bc0-122">처음 3개 열은 이 큐브의 처음 버전에서 사용되지 않은 차원 테이블과 팩트 테이블을 연결하는 키 값입니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-122">The first three are key values that link the fact table with dimension tables that are not used in the initial version of this cube.</span></span>  
  
8.  <span data-ttu-id="93bc0-123">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-123">Click **Next**.</span></span>  
  
9. <span data-ttu-id="93bc0-124">**기존 차원 선택** 페이지에서 앞서 만든 **Date** 차원을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-124">On the **Select Existing Dimensions** page, make sure the **Date** dimension that you created earlier is selected, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="93bc0-125">**새 차원 선택** 페이지에서 새로 만들 차원을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-125">On the **Select New Dimensions** page, select the new dimensions to be created.</span></span> <span data-ttu-id="93bc0-126">이렇게 하려면 **Customer**, **Geography**및 **Product** 확인란을 선택하고 **InternetSales** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-126">To do this, verify that the **Customer**, **Geography**, and **Product** check boxes are selected, and then clear the **InternetSales** check box.</span></span>  
  
11. <span data-ttu-id="93bc0-127">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-127">Click **Next**.</span></span>  
  
12. <span data-ttu-id="93bc0-128">**마법사 완료** 페이지에서 큐브 이름을로 변경 `Analysis Services Tutorial` 합니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-128">On the **Completing the Wizard** page, change the name of the cube to `Analysis Services Tutorial`.</span></span> <span data-ttu-id="93bc0-129">미리 보기 창에서 **InternetSales** 측정값 그룹 및 이 그룹의 측정값을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-129">In the Preview pane, you can see the **InternetSales** measure group and its measures.</span></span> <span data-ttu-id="93bc0-130">**Date**, **Customer** 및 **Product** 차원도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-130">You can also see the **Date**, **Customer,** and **Product** dimensions.</span></span>  
  
13. <span data-ttu-id="93bc0-131">**마침**을 클릭하여 마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-131">Click **Finish** to complete the wizard.</span></span>  
  
     <span data-ttu-id="93bc0-132">솔루션 탐색기의 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브는 **큐브** 폴더에 나타나고 Customer 및 Product 데이터베이스 차원은 **차원** 폴더에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-132">In Solution Explorer, in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube appears in the **Cubes** folder, and the Customer and Product database dimensions appear in the **Dimensions** folder.</span></span> <span data-ttu-id="93bc0-133">또한 개발 환경에서 가장 중요한 큐브 구조 탭에는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-133">Additionally, in the center of the development environment, the Cube Structure tab displays the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>  
  
14. <span data-ttu-id="93bc0-134">큐브 구조 탭의 도구 모음에서 큐브의 차원 및 팩트 테이블을 보다 쉽게 볼 수 있도록 **확대/축소** 수준을 50%로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-134">On the toolbar of the Cube Structure tab, change the **Zoom** level to 50 percent, so that you can more easily see the dimensions and fact tables in the cube.</span></span> <span data-ttu-id="93bc0-135">팩트 테이블은 노란색, 차원 테이블은 파란색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-135">Notice that the fact table is yellow and the dimension tables are blue.</span></span>  
  
15. <span data-ttu-id="93bc0-136">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93bc0-136">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="93bc0-137">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="93bc0-137">Next Task in Lesson</span></span>  
 [<span data-ttu-id="93bc0-138">차원에 특성 추가</span><span class="sxs-lookup"><span data-stu-id="93bc0-138">Adding Attributes to Dimensions</span></span>](lesson-2-3-adding-attributes-to-dimensions.md)  
  
## <a name="see-also"></a><span data-ttu-id="93bc0-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="93bc0-139">See Also</span></span>  
 <span data-ttu-id="93bc0-140">[다차원 모델의 큐브](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="93bc0-140">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="93bc0-141">다차원 모델의 차원</span><span class="sxs-lookup"><span data-stu-id="93bc0-141">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
