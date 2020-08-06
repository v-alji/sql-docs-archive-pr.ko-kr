---
title: 큐브 스키마 보기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 82fc715c-e08e-447d-8fc8-9c9005f145f0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e7d324db1e0c41588694031d3c121fdb47233f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740516"
---
# <a name="view-the-cube-schema"></a><span data-ttu-id="d4980-102">큐브 스키마 보기</span><span class="sxs-lookup"><span data-stu-id="d4980-102">View the Cube Schema</span></span>
  <span data-ttu-id="d4980-103">**큐브 디자이너** 에서 **큐브 구조** 탭의 **데이터 원본 뷰** 에는 큐브 스키마가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-103">The **Data Source View** pane of the **Cube Structure** tab in **Cube Designer** displays the cube schema.</span></span> <span data-ttu-id="d4980-104">이 스키마는 큐브의 측정값과 차원이 파생된 원본 테이블 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-104">The schema is the set of tables from which the measures and dimensions for a cube are derived.</span></span> <span data-ttu-id="d4980-105">모든 큐브 스키마는 해당 큐브의 측정값과 차원의 기반이 되는 하나 이상의 팩트 테이블과 하나 이상의 차원 테이블로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-105">Every cube schema consists of one or more fact tables and one or more dimension tables on which the measures and dimensions in the cube are based.</span></span>  
  
 <span data-ttu-id="d4980-106">**큐브 구조** 탭의 **데이터 원본 뷰** 창에는 큐브의 기반이 되는 데이터 원본 뷰의 다이어그램이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-106">The **Data Source View** pane of the **Cube Structure** tab displays a diagram of the data source view on which the cube is based.</span></span> <span data-ttu-id="d4980-107">이 다이어그램은 데이터 원본 뷰의 주 다이어그램의 하위 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-107">This diagram is a subset of the main diagram of the data source view.</span></span> <span data-ttu-id="d4980-108">**데이터 원본 뷰** 창에서 테이블을 숨기고 표시할 수 있으며, 기존 다이어그램을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-108">You can hide and show tables in the **Data Source View** pane and view any existing diagrams.</span></span> <span data-ttu-id="d4980-109">하지만 새 관계나 명명된 쿼리를 추가하는 등의 기본 스키마를 변경하는 작업은 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-109">However, you cannot make changes (such as adding new relationships or named queries) to the underlying schema.</span></span> <span data-ttu-id="d4980-110">스키마를 변경하려면 데이터 원본 뷰 디자이너를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-110">To make changes to the schema, use Data Source View Designer.</span></span>  
  
 <span data-ttu-id="d4980-111">큐브를 만들 때 **큐브 구조** 탭의 **데이터 원본 뷰** 창에 표시되는 다이어그램은 처음에는 프로젝트나 데이터베이스의 데이터 원본 뷰에 있는 **모든 테이블 표시** 다이어그램과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-111">When you create a cube, the diagram displayed in the **Data Source View** pane of the **Cube Structure** tab is initially the same as the **Show All Tables** diagram in the data source view for the project or database.</span></span> <span data-ttu-id="d4980-112">이 다이어그램을 데이터 원본 뷰에 있는 임의의 기존 다이어그램으로 바꿀 수 있으며 **데이터 원본 뷰** 창에서 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-112">You can replace this diagram with any existing diagram in the data source view and make adjustments in the **Data Source View** pane.</span></span>  
  
 <span data-ttu-id="d4980-113">**큐브 디자이너**의 다이어그램 작업을 할 경우 탭 또는 탭에서 선택한 개체에 적용되는 명령을 **데이터 원본 보기** 메뉴에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-113">While you work with the diagram in **Cube Designer**, commands that act on the tab or on any selected object in the tab are available on the **Data Source View** menu.</span></span> <span data-ttu-id="d4980-114">다이어그램 배경 또는 다이어그램의 개체를 마우스 오른쪽 단추로 클릭하여 다이어그램이나 선택한 개체에 적용되는 명령을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-114">You can also right-click the background of the diagram or any object in the diagram to use commands that act on the diagram or selected object.</span></span> <span data-ttu-id="d4980-115">다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-115">You can:</span></span>  
  
-   <span data-ttu-id="d4980-116">다이어그램 형식과 트리 형식 간 전환</span><span class="sxs-lookup"><span data-stu-id="d4980-116">Switch between diagram and tree formats.</span></span>  
  
-   <span data-ttu-id="d4980-117">정렬, 찾기, 표시 및 테이블 숨기기</span><span class="sxs-lookup"><span data-stu-id="d4980-117">Arrange, find, show, and hide tables.</span></span>  
  
-   <span data-ttu-id="d4980-118">이름 표시</span><span class="sxs-lookup"><span data-stu-id="d4980-118">Show friendly names.</span></span>  
  
-   <span data-ttu-id="d4980-119">레이아웃 전환</span><span class="sxs-lookup"><span data-stu-id="d4980-119">Switch layouts.</span></span>  
  
-   <span data-ttu-id="d4980-120">배율 변경</span><span class="sxs-lookup"><span data-stu-id="d4980-120">Change the magnification.</span></span>  
  
-   <span data-ttu-id="d4980-121">속성 보기</span><span class="sxs-lookup"><span data-stu-id="d4980-121">View properties.</span></span>  
  
 <span data-ttu-id="d4980-122">또한 다음 표에 나열된 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-122">Additionally, you can perform the actions listed in the following table:</span></span>  
  
|<span data-ttu-id="d4980-123">대상</span><span class="sxs-lookup"><span data-stu-id="d4980-123">To</span></span>|<span data-ttu-id="d4980-124">단계</span><span class="sxs-lookup"><span data-stu-id="d4980-124">Do this</span></span>|  
|--------|-------------|  
|<span data-ttu-id="d4980-125">큐브의 데이터 원본 뷰의 다이어그램 사용</span><span class="sxs-lookup"><span data-stu-id="d4980-125">Use a diagram from the data source view of the cube</span></span>|<span data-ttu-id="d4980-126">**데이터 원본 뷰** 메뉴에서 **복사할 다이어그램 위치**를 가리킨 다음 사용할 데이터 원본 뷰 다이어그램을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-126">On the **Data Source View** menu, point to **Copy Diagram from**, and then click the data source view diagram you want to use.</span></span><br /><br /> <span data-ttu-id="d4980-127">또는</span><span class="sxs-lookup"><span data-stu-id="d4980-127">- or -</span></span><br /><br /> <span data-ttu-id="d4980-128">**데이터 원본 뷰** 창의 배경을 마우스 오른쪽 단추로 클릭하고 **복사할 다이어그램 위치**를 가리킨 다음 보려는 데이터 원본 뷰의 다이어그램을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-128">Right-click the background of the **Data Source View** pane, point to **Copy Diagram from**, and then click the diagram in the data source view that you want.</span></span> <span data-ttu-id="d4980-129">이 방법을 사용하면 독립적인 다이어그램 사본이 만들어지므로 **큐브 작성기** 탭에서 변경하는 내용이 원본 다이어그램에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-129">This method creates an independent copy of the diagram, so any changes you make on the **Cube Builder** tab do not appear in the original diagram.</span></span>|  
|<span data-ttu-id="d4980-130">큐브에 사용되는 테이블만 표시</span><span class="sxs-lookup"><span data-stu-id="d4980-130">Show only the tables that are used in the cube</span></span>|<span data-ttu-id="d4980-131">**데이터 원본 뷰** 메뉴에서 **사용된 테이블만 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-131">On the **Data Source View** menu, click **Show Only Used Tables**.</span></span><br /><br /> <span data-ttu-id="d4980-132">또는</span><span class="sxs-lookup"><span data-stu-id="d4980-132">- or -</span></span><br /><br /> <span data-ttu-id="d4980-133">**데이터 원본 뷰** 창의 배경을 마우스 오른쪽 단추로 클릭한 다음 **사용된 테이블만 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-133">Right-click the background of the **Data Source View** pane, and then click **Show Only Used Tables**.</span></span>|  
|<span data-ttu-id="d4980-134">데이터 원본 뷰 스키마를 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-134">Edit the data source view schema</span></span>|<span data-ttu-id="d4980-135">**데이터 원본 뷰** 메뉴에서 **데이터 원본 뷰 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-135">On the **Data Source View** menu, click **Edit Data Source View**.</span></span><br /><br /> <span data-ttu-id="d4980-136">또는</span><span class="sxs-lookup"><span data-stu-id="d4980-136">- or -</span></span><br /><br /> <span data-ttu-id="d4980-137">**데이터 원본 뷰** 창의 배경을 마우스 오른쪽 단추로 클릭한 다음 **데이터 원본 뷰 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4980-137">Right-click the background of the **Data Source View** pane, and then click **Edit Data Source View**.</span></span>|  
  
  
