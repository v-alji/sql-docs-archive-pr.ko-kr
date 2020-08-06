---
title: 데이터 원본 뷰 디자이너 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.f1
helpviewer_keywords:
- Data Source View Designer
ms.assetid: 6f40a074-761f-440b-a999-09b755bd86ce
author: minewiskan
ms.author: owend
ms.openlocfilehash: 31e70f3f9b577f44b9ebb61b5ae2975c0a129828
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733308"
---
# <a name="data-source-view-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="36f3c-102">데이터 원본 뷰 디자이너(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="36f3c-102">Data Source View Designer (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="36f3c-103">DSV(데이터 원본 뷰)는 다차원 모델에서 큐브 및 차원을 만들기 위해 사용되는 외부 관계형 데이터 원본에 대한 논리적 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-103">A data source view (DSV) is a logical view of an external relational data source used to create cubes and dimensions in a multidimensional model.</span></span>

 <span data-ttu-id="36f3c-104">DSV를 생성한 후에는 **에서** 데이터 원본 뷰 디자이너 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 를 사용하여 DSV에서 직접 작업할 수 있으므로, 기본 데이터 원본이 다차원 모델에 필요한 누락된 데이터 요소인 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-104">After a DSV is generated, you can use the **Data Source View Designer** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to work directly on the DSV, which can be useful if the underlying data source is missing data elements needed in a multidimensional model.</span></span>

 <span data-ttu-id="36f3c-105">**데이터 원본 뷰 디자이너** 를 열려면:</span><span class="sxs-lookup"><span data-stu-id="36f3c-105">To open **Data Source View Designer** :</span></span>

-   <span data-ttu-id="36f3c-106">**솔루션 탐색기**에서 데이터 원본 뷰를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-106">Double-click a data source view in **Solution Explorer**.</span></span>

-   <span data-ttu-id="36f3c-107">**솔루션 탐색기** 에서 데이터 원본 뷰를 마우스 오른쪽 단추로 클릭한 다음 **열기** 또는 **디자이너 보기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-107">Right-click a data source view in **Solution Explorer** and select **Open** or **View Designer**.</span></span>

 <span data-ttu-id="36f3c-108">**데이터 원본 뷰 디자이너** 에는 도구 모음, DSV의 개체 및 관계를 나타내는 다이어그램, 테이블 및 명명된 쿼리가 알파벳 순서로 나열된 테이블 창, DSV의 특정 다이어그램을 만들고 보는 데 사용되는 다이어그램 구성 도우미 창이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-108">The **Data Source View Designer** contains a toolbar, a diagram showing the objects and relationships in the DSV, a table pane listing tables and named queries in alphabetical order, and a Diagram Organizer pane used to create and view specific diagrams of the DSV.</span></span> <span data-ttu-id="36f3c-109">테이블 또는 관계를 마우스 오른쪽 단추로 클릭하면 상황에 맞는 명령에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-109">You can right-click a table or relationship to access context-sensitive commands.</span></span>

 <span data-ttu-id="36f3c-110">![데이터 원본 뷰 디자이너](media/ssas-dsvdesigner.PNG "데이터 원본 뷰 디자이너")</span><span class="sxs-lookup"><span data-stu-id="36f3c-110">![Data Source View Designer](media/ssas-dsvdesigner.PNG "Data Source View Designer")</span></span>

 <span data-ttu-id="36f3c-111">최소한 DSV에는 처리 중 모델 개체를 채우는 데 사용되는 관계형 데이터베이스 테이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-111">At a minimum, a DSV shows the relational database tables that will be used to populate model objects during processing.</span></span> <span data-ttu-id="36f3c-112">DSV는 일반적으로 데이터 원본 뷰 마법사를 사용해서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-112">A DSV is generated, usually by using the Data Source View wizard.</span></span> <span data-ttu-id="36f3c-113">DSV에 있는 테이블, 열 및 관계는 큐브의 측정값 및 차원의 기초가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-113">Tables, columns, and relationships in the DSV become the basis for dimensions and measures in a cube.</span></span> <span data-ttu-id="36f3c-114">DSV가 생성된 다음에는 데이터 원본 뷰 디자이너를 사용하여 이를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-114">Once the DSV is created, you can use the Data Source View Designer to modify it.</span></span>

 <span data-ttu-id="36f3c-115">대부분의 Analysis Services 개발자는 생성된 DSV를 거의 수정하지 않고 있는 그대로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-115">Most Analysis Services developers use a generated DSV as is, with few customizations.</span></span> <span data-ttu-id="36f3c-116">특히 원본 데이터가 SQL Server 데이터베이스에 있는 뷰에서 온 경우에는 수정이 거의 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-116">This is especially common if source data originates from a view in a SQL Server database.</span></span> <span data-ttu-id="36f3c-117">이 경우, Analysis Services DSV보다 T-SQL 뷰에서 데이터 관계 및 계산을 관리하는 것이 더 편리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-117">In this case, you might prefer to manage data relationships and calculations in a T-SQL view rather than an Analysis Services DSV.</span></span> <span data-ttu-id="36f3c-118">하지만 기본 데이터베이스의 소유자가 아닐 경우에는 Analysis Services에서 DSV를 수정하여 모델에 사용되는 데이터 구조를 추가로 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-118">However, if you are not the owner of the underlying database, you can modify the DSV in Analysis Services to further develop the data structures used in your model.</span></span>

## <a name="tasks-in-data-source-view-designer"></a><span data-ttu-id="36f3c-119">데이터 원본 뷰 디자이너의 작업</span><span class="sxs-lookup"><span data-stu-id="36f3c-119">Tasks in Data Source View Designer</span></span>
 <span data-ttu-id="36f3c-120">데이터 원본 뷰 디자이너에서는 DSV를 다음과 같이 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-120">Using Data Source View Designer, you can make the following edits to a DSV:</span></span>

|||
|-|-|
|<span data-ttu-id="36f3c-121">열 또는 테이블의 이름을 바꾸거나 새 계산 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-121">Rename columns or tables, or create new calculated columns.</span></span> <span data-ttu-id="36f3c-122">예를 들어 이름과 성을 새로운 전체 이름 열로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-122">For example, concatenate a first name and last name into a new full-name column.</span></span>|[<span data-ttu-id="36f3c-123">데이터 원본 뷰에서 명명된 계산 정의&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="36f3c-123">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)|
|<span data-ttu-id="36f3c-124">테이블 관계 수동 추가</span><span class="sxs-lookup"><span data-stu-id="36f3c-124">Manually add table relationships</span></span>|[<span data-ttu-id="36f3c-125">데이터 원본 뷰에서 논리적 관계 정의&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="36f3c-125">Define Logical Relationships in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-logical-relationships-in-a-data-source-view-analysis-services.md)|
|<span data-ttu-id="36f3c-126">T-SQL 쿼리를 기반으로 새로운 개체를 정의하기 위한 명명된 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-126">Create a named query to define a new object based on a T-SQL query.</span></span>|[<span data-ttu-id="36f3c-127">데이터 원본 뷰에서 명명된 쿼리 정의&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="36f3c-127">Define Named Queries in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-named-queries-in-a-data-source-view-analysis-services.md)|
|<span data-ttu-id="36f3c-128">기본 데이터를 탐색하여 모델 개체로 표시되는 실제 데이터 값을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-128">Explore underlying data to view actual data values represented by model objects.</span></span><br /><br /> <span data-ttu-id="36f3c-129">데이터 탐색을 사용하여 기본 차원 테이블 또는 쿼리에서 반환되는 데이터를 시각적으로 검사하고 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-129">Data exploration lets you visually inspect and copy data that is returned from the underlying dimensional table or query.</span></span> <span data-ttu-id="36f3c-130">데이터 탐색 시 기본적으로 샘플 개수 5000개의 최대 개수 샘플링 방법이 사용되지만 이러한 설정을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f3c-130">By default, data exploration uses the top count sampling methodology, with a sample count of 5000, but you can revise these settings.</span></span>|[<span data-ttu-id="36f3c-131">데이터 원본 뷰에서 데이터 탐색&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="36f3c-131">Explore Data in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/explore-data-in-a-data-source-view-analysis-services.md)|
|<span data-ttu-id="36f3c-132">DSV에 있는 테이블 및 관계의 일부 또는 전체를 다이어그램으로 작성</span><span class="sxs-lookup"><span data-stu-id="36f3c-132">Diagram all or part of the tables and relationships in a DSV</span></span>|[<span data-ttu-id="36f3c-133">데이터 원본 뷰 디자이너에서의 다이어그램 작업&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="36f3c-133">Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;</span></span>](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)|

## <a name="see-also"></a><span data-ttu-id="36f3c-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="36f3c-134">See Also</span></span>
 <span data-ttu-id="36f3c-135">[다차원 모델의 데이터 원본 뷰](multidimensional-models/data-source-views-in-multidimensional-models.md) [데이터 원본 뷰에서 테이블이 나 뷰를 추가 하거나 제거 &#40;Analysis Services&#41;](multidimensional-models/adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)</span><span class="sxs-lookup"><span data-stu-id="36f3c-135">[Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md) [Adding or Removing Tables or Views in a Data Source View &#40;Analysis Services&#41;](multidimensional-models/adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)</span></span>


