---
title: 데이터 원본 뷰 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: af00938a-5a06-4fae-b2fc-f3fb0ca3cea5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7d59c5fbe5fd4a07596745447567a72499ddabd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639061"
---
# <a name="defining-a-data-source-view"></a><span data-ttu-id="13a1e-102">데이터 원본 뷰 정의</span><span class="sxs-lookup"><span data-stu-id="13a1e-102">Defining a Data Source View</span></span>
  <span data-ttu-id="13a1e-103">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트에 사용할 데이터 원본을 정의한 후 수행해야 할 다음 단계는 일반적으로 프로젝트에 대한 데이터 원본 뷰를 정의하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-103">After you define the data sources that you will use in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, the next step is generally to define a data source view for the project.</span></span> <span data-ttu-id="13a1e-104">데이터 원본 뷰는 프로젝트에서 데이터 원본에 의해 정의되는 뷰와 지정된 테이블의 메타데이터에 대한 단일 통합 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-104">A data source view is a single, unified view of the metadata from the specified tables and views that the data source defines in the project.</span></span> <span data-ttu-id="13a1e-105">메타데이터를 데이터 원본 뷰로 저장하면 기본 데이터 원본에 대한 연결이 열려 있지 않아도 개발 중에 메타데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-105">Storing the metadata in the data source view enables you to work with the metadata during development without an open connection to any underlying data source.</span></span> <span data-ttu-id="13a1e-106">자세한 내용은 [다차원 모델의 데이터 원본 뷰](multidimensional-models/data-source-views-in-multidimensional-models.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13a1e-106">For more information, see [Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md).</span></span>  
  
 <span data-ttu-id="13a1e-107">다음 태스크에서는 **AdventureWorksDW2012** 데이터 원본의 테이블이 5개 포함된 데이터 원본 뷰를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-107">In the following task, you define a data source view that includes five tables from the **AdventureWorksDW2012** data source.</span></span>  
  
### <a name="to-define-a-new-data-source-view"></a><span data-ttu-id="13a1e-108">새 데이터 원본 뷰를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="13a1e-108">To define a new data source view</span></span>  
  
1.  <span data-ttu-id="13a1e-109">Microsoft Visual Studio 창의 오른쪽에 있는 솔루션 탐색기에서 **데이터 원본 뷰**를 마우스 오른쪽 단추로 클릭하고 **새 데이터 원본 뷰**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-109">In Solution Explorer (on the right of the Microsoft Visual Studio window), right-click **Data Source Views**, and then click **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="13a1e-110">**데이터 원본 뷰 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-110">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span> <span data-ttu-id="13a1e-111">**데이터 원본 선택** 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-111">The **Select a Data Source** page appears.</span></span>  
  
3.  <span data-ttu-id="13a1e-112">**관계형 데이터 원본**에서 **Adventure Works DW 2012** 데이터 원본이 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-112">Under **Relational data sources**, the **Adventure Works DW 2012** data source is selected.</span></span> <span data-ttu-id="13a1e-113">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-113">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="13a1e-114">여러 데이터 원본을 기반으로 하는 데이터 원본 뷰를 만들려면 단일 데이터 원본을 기반으로 하는 데이터 원본 뷰를 먼저 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-114">To create a data source view that is based on multiple data sources, first define a data source view that is based on a single data source.</span></span> <span data-ttu-id="13a1e-115">이 데이터 원본을 주 데이터 원본이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-115">This data source is then called the primary data source.</span></span> <span data-ttu-id="13a1e-116">그런 다음 보조 데이터 원본에 있는 테이블과 뷰를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-116">You can then add tables and views from a secondary data source.</span></span> <span data-ttu-id="13a1e-117">여러 데이터 원본의 관련 테이블에 기초하는 특성이 포함된 차원을 디자인할 경우 해당 분산 쿼리 엔진 기능을 사용하려면 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터 원본을 주 데이터 원본으로 정의해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-117">When designing dimensions that contain attributes based on related tables in multiple data sources, you might need to define a [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data source as the primary data source to use its distributed query engine capabilities.</span></span>  
  
4.  <span data-ttu-id="13a1e-118">**테이블 및 뷰 선택** 페이지에서 선택한 데이터 원본에서 사용할 수 있는 개체 목록을 통해 테이블과 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-118">On the **Select Tables and Views** page, select tables and views from the list of objects that are available from the selected data source.</span></span> <span data-ttu-id="13a1e-119">테이블과 뷰를 선택하는 데 도움이 되도록 이 목록을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-119">You can filter this list to help you select tables and views.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="13a1e-120">오른쪽 위 모퉁이의 최대화 단추를 클릭하여 창이 전체 화면에 꽉 차도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-120">Click the maximize button in the upper-right corner so that the window covers the full screen.</span></span> <span data-ttu-id="13a1e-121">이렇게 하면 사용할 수 있는 개체의 전체 목록을 보다 쉽게 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-121">This makes it easier to see the complete list of available objects.</span></span>  
  
     <span data-ttu-id="13a1e-122">**사용 가능한 개체** 목록에서 다음 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-122">In the **Available objects** list, select the following objects.</span></span> <span data-ttu-id="13a1e-123">Ctrl 키를 누른 채 각 테이블을 클릭하면 여러 테이블을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-123">You can select multiple tables by clicking each while holding down the CTRL key:</span></span>  
  
    -   <span data-ttu-id="13a1e-124">**DimCustomer (dbo)**</span><span class="sxs-lookup"><span data-stu-id="13a1e-124">**DimCustomer (dbo)**</span></span>  
  
    -   <span data-ttu-id="13a1e-125">**DimDate (dbo)**</span><span class="sxs-lookup"><span data-stu-id="13a1e-125">**DimDate (dbo)**</span></span>  
  
    -   <span data-ttu-id="13a1e-126">**DimGeography (dbo)**</span><span class="sxs-lookup"><span data-stu-id="13a1e-126">**DimGeography (dbo)**</span></span>  
  
    -   <span data-ttu-id="13a1e-127">**DimProduct (dbo)**</span><span class="sxs-lookup"><span data-stu-id="13a1e-127">**DimProduct (dbo)**</span></span>  
  
    -   <span data-ttu-id="13a1e-128">**FactInternetSales (dbo)**</span><span class="sxs-lookup"><span data-stu-id="13a1e-128">**FactInternetSales (dbo)**</span></span>  
  
5.  <span data-ttu-id="13a1e-129">**>** 선택한 테이블을 **포함 된 개체** 목록에 추가 하려면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-129">Click **>** to add the selected tables to the **Included objects** list.</span></span>  
  
6.  <span data-ttu-id="13a1e-130">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-130">Click **Next.**</span></span>  
  
7.  <span data-ttu-id="13a1e-131">이름 필드에서 **Adventure Works DW 2012** 가 표시되는지 확인하고 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-131">In the Name field, make sure **Adventure Works DW 2012** displays, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="13a1e-132">**Adventure Works DW 2012** 데이터 원본 뷰가 솔루션 탐색기의 **데이터 원본 뷰** 폴더에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-132">The **Adventure Works DW 2012** data source view appears in the **Data Source Views** folder in Solution Explorer.</span></span> <span data-ttu-id="13a1e-133">데이터 원본 뷰의 내용도 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 데이터 원본 뷰 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-133">The content of the data source view is also displayed in Data Source View Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="13a1e-134">이 디자이너에는 다음과 같은 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-134">This designer contains the following elements:</span></span>  
  
    -   <span data-ttu-id="13a1e-135">테이블과 테이블 관계가 그래픽으로 표시되는 **다이어그램** 창</span><span class="sxs-lookup"><span data-stu-id="13a1e-135">A **Diagram** pane in which the tables and their relationships are represented graphically.</span></span>  
  
    -   <span data-ttu-id="13a1e-136">테이블과 테이블 스키마 요소가 트리 뷰로 표시되는 **테이블** 창</span><span class="sxs-lookup"><span data-stu-id="13a1e-136">A **Tables** pane in which the tables and their schema elements are displayed in a tree view.</span></span>  
  
    -   <span data-ttu-id="13a1e-137">데이터 원본 뷰의 하위 집합을 볼 수 있도록 하위 다이어그램을 만들 수 있는 **다이어그램 구성 도우미** 창</span><span class="sxs-lookup"><span data-stu-id="13a1e-137">A **Diagram Organizer** pane in which you can create subdiagrams so that you can view subsets of the data source view.</span></span>  
  
    -   <span data-ttu-id="13a1e-138">데이터 원본 뷰 디자이너용 도구 모음</span><span class="sxs-lookup"><span data-stu-id="13a1e-138">A toolbar that is specific to Data Source View Designer.</span></span>  
  
8.  <span data-ttu-id="13a1e-139">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 개발 환경을 최대화하려면 **최대화** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-139">To maximize the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] development environment, click the **Maximize** button.</span></span>  
  
9. <span data-ttu-id="13a1e-140">**다이어그램** 창의 테이블을 50% 비율로 보려면 데이터 원본 뷰 디자이너 도구 모음의 **확대/축소** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-140">To view the tables in the **Diagram** pane at 50 percent, click the **Zoom** icon on the Data Source View Designer toolbar.</span></span> <span data-ttu-id="13a1e-141">이렇게 하면 각 테이블의 열 정보가 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-141">This will hide the column details of each table.</span></span>  
  
10. <span data-ttu-id="13a1e-142">솔루션 탐색기를 숨기려면 제목 표시줄에 압정 아이콘으로 표시되는 **자동 숨기기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-142">To hide Solution Explorer, click the **Auto Hide** button, which is the pushpin icon on the title bar.</span></span> <span data-ttu-id="13a1e-143">솔루션 탐색기를 다시 표시하려면 개발 환경의 오른쪽에 있는 솔루션 탐색기 탭 위에 포인터를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-143">To view Solution Explorer again, position your pointer over the Solution Explorer tab along the right side of the development environment.</span></span> <span data-ttu-id="13a1e-144">솔루션 탐색기 숨기기를 취소하려면 **자동 숨기기** 단추를 다시 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-144">To unhide Solution Explorer, click the **Auto Hide** button again.</span></span>  
  
11. <span data-ttu-id="13a1e-145">기본적으로 창이 숨겨진 상태가 아니면 속성 창과 솔루션 탐색기 창의 제목 표시줄에 있는 **자동 숨기기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-145">If the windows are not hidden by default, click **Auto Hide** on the title bar of the Properties and Solution Explorer windows.</span></span>  
  
     <span data-ttu-id="13a1e-146">이제 **다이어그램** 창에서 모든 테이블과 테이블 관계를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-146">You can now view all the tables and their relationships in the **Diagram** pane.</span></span> <span data-ttu-id="13a1e-147">FactInternetSales 테이블과 DimDate 테이블 간에는 3가지 관계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-147">Notice that there are three relationships between the FactInternetSales table and the DimDate table.</span></span> <span data-ttu-id="13a1e-148">각 판매에 있는 주문 날짜, 기한 및 운송 날짜라는 3가지 날짜가 판매와 관련이 있습니다</span><span class="sxs-lookup"><span data-stu-id="13a1e-148">Each sale has three dates associated with the sale: an order date, a due date, and a ship date.</span></span> <span data-ttu-id="13a1e-149">관계에 대한 세부 정보를 보려면 **다이어그램** 창에서 관계 화살표를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13a1e-149">To view the details of any relationship, double-click the relationship arrow in the **Diagram** pane.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="13a1e-150">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="13a1e-150">Next Task in Lesson</span></span>  
 [<span data-ttu-id="13a1e-151">기본 테이블 이름 수정</span><span class="sxs-lookup"><span data-stu-id="13a1e-151">Modifying Default Table Names</span></span>](lesson-1-4-modifying-default-table-names.md)  
  
## <a name="see-also"></a><span data-ttu-id="13a1e-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="13a1e-152">See Also</span></span>  
 [<span data-ttu-id="13a1e-153">다차원 모델의 데이터 원본 뷰</span><span class="sxs-lookup"><span data-stu-id="13a1e-153">Data Source Views in Multidimensional Models</span></span>](multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
