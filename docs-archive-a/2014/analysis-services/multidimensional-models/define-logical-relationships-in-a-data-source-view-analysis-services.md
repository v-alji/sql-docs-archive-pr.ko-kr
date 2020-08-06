---
title: 데이터 원본 뷰에서 논리적 관계 정의 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- adding relationships
- relationships [Analysis Services], data source views
- data source views [Analysis Services], relationships
ms.assetid: a20d6dae-e769-4131-8a59-7ef56f174220
author: minewiskan
ms.author: owend
ms.openlocfilehash: c46c2b360a4528aeb0eb88348d0d1242b22d8ef5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651381"
---
# <a name="define-logical-relationships-in-a-data-source-view-analysis-services"></a><span data-ttu-id="2dcc5-102">데이터 원본 뷰에서 논리적 관계 정의(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="2dcc5-102">Define Logical Relationships in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="2dcc5-103">데이터 원본 뷰 마법사와 데이터 원본 뷰 디자이너에서는 기본 데이터베이스 관계 또는 지정한 이름 일치 조건을 기반으로 데이터 원본 뷰(DSV)에 추가된 테이블 간의 관계를 자동으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-103">The Data Source View Wizard and Data Source View Designer automatically define relationships between tables added to a data source view (DSV) based on underlying database relationships or name matching criteria you specify.</span></span>  
  
 <span data-ttu-id="2dcc5-104">여러 데이터 원본의 데이터를 사용하여 작업할 경우 자동으로 정의되는 관계를 보완하기 위해 DSV에서 수동으로 논리적 관계를 정의해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-104">In cases where you are working with data from multiple data sources, you may need to manually define logical relationships in the DSV to supplement those relationships that are defined automatically.</span></span> <span data-ttu-id="2dcc5-105">관계는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 팩트 테이블과 차원 테이블을 식별하고, 기본 데이터 원본에서 데이터 및 메타데이터를 검색할 쿼리를 작성하며, 고급 비즈니스 인텔리전스 기능을 사용하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-105">Relationships are required in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to identify fact and dimension tables, to construct queries for retrieving data and metadata from underlying data sources, and to take advantage of advanced business intelligence features.</span></span>  
  
 <span data-ttu-id="2dcc5-106">데이터 원본 뷰 디자이너에서는 다음과 같은 유형의 관계를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-106">You can define the following types of relationships in Data Source View Designer:</span></span>  
  
-   <span data-ttu-id="2dcc5-107">같은 데이터 원본의 서로 다른 테이블 간 관계</span><span class="sxs-lookup"><span data-stu-id="2dcc5-107">A relationship from one table to another table in the same data source.</span></span>  
  
-   <span data-ttu-id="2dcc5-108">부모-자식 관계처럼 테이블과 테이블 자신 간 관계</span><span class="sxs-lookup"><span data-stu-id="2dcc5-108">A relationship from one table to itself, as in a parent-child relationship.</span></span>  
  
-   <span data-ttu-id="2dcc5-109">서로 다른 데이터 원본의 테이블 간 관계</span><span class="sxs-lookup"><span data-stu-id="2dcc5-109">A relationship from one table in a data source to another table in a different data source.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2dcc5-110">데이터 원본 뷰에 정의된 관계는 논리적이므로 기본 DSV에 정의된 실제 관계에 반영되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-110">The relationships defined in a DSV are logical and may not reflect the actual relationships defined in the underlying data source.</span></span> <span data-ttu-id="2dcc5-111">데이터 원본 뷰 디자이너에서 기본 데이터 원본에 없는 관계를 만들고 기본 데이터 원본의 기존 외래 키 관계에서 데이터 원본 뷰 디자이너를 사용하여 만든 관계를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-111">You can create relationships in Data Source View Designer that do not exist in the underlying data source, and remove relationships created by Data Source View Designer from existing foreign key relationships in the underlying data source.</span></span>  
  
 <span data-ttu-id="2dcc5-112">관계의 방향이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-112">Relationships are directed.</span></span> <span data-ttu-id="2dcc5-113">원본 열의 모든 값은 대상 열에 해당 값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-113">For every value in the source column, there is a corresponding value in the destination column.</span></span> <span data-ttu-id="2dcc5-114">**다이어그램** 창에 표시되는 다이어그램처럼 데이터 원본 뷰 다이어그램에서 두 테이블 사이의 선에 있는 화살표는 관계의 방향을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-114">In a data source view diagram, such as the diagrams displayed in the **Diagram** pane, an arrow on the line between two tables indicates the direction of the relationship.</span></span>  
  
 <span data-ttu-id="2dcc5-115">이 항목에는 다음 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-115">This topic includes the following sections:</span></span>  
  
 [<span data-ttu-id="2dcc5-116">테이블, 명명된 쿼리 또는 뷰 간의 관계를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="2dcc5-116">To add a relationship between tables, named queries, or views</span></span>](#bkmk_addRel)  
  
 [<span data-ttu-id="2dcc5-117">다이어그램 창에서 관계를 보거나 수정하려면</span><span class="sxs-lookup"><span data-stu-id="2dcc5-117">To view or modify a relationship in the Diagram pane</span></span>](#bkmk_diagrampane)  
  
 [<span data-ttu-id="2dcc5-118">테이블 창에서 관계를 보거나 수정하려면</span><span class="sxs-lookup"><span data-stu-id="2dcc5-118">To view or modify a relationship in the Tables pane</span></span>](#bkmk_tablespane)  
  
##  <a name="to-add-a-relationship-between-tables-named-queries-or-views"></a><a name="bkmk_addRel"></a><span data-ttu-id="2dcc5-119">테이블, 명명 된 쿼리 또는 뷰 간의 관계를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="2dcc5-119">To add a relationship between tables, named queries, or views</span></span>  
  
1.  <span data-ttu-id="2dcc5-120">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 논리적 관계를 추가할 데이터 원본 뷰가 포함된 프로젝트를 열거나 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-120">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you wish to add a logical relationship.</span></span>  
  
2.  <span data-ttu-id="2dcc5-121">솔루션 탐색기에서 **데이터 원본 뷰** 폴더를 확장하고 데이터 원본 뷰를 두 번 클릭하여 **데이터 원본 뷰 디자이너**에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-121">In Solution Explorer, expand the **Data Source Views** folder, then double-click the data source view to open it in **Data Source View Designer**.</span></span>  
  
3.  <span data-ttu-id="2dcc5-122">**테이블** 창에서 관계를 추가할 테이블, 명명된 쿼리 또는 뷰를 마우스 오른쪽 단추로 클릭한 다음 **새 관계**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-122">Right-click the table, named query or view to which you want to add a relationship in either the **Tables** pane and then click **New Relationship**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2dcc5-123">테이블, 뷰 또는 명명된 쿼리를 찾으려면 **데이터 원본 뷰** 메뉴를 클릭하거나 **테이블** 또는 **다이어그램** 창의 열린 영역을 마우스 오른쪽 단추로 클릭하여 **테이블 찾기** 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-123">To locate a table, view or named query, you can use the **Find Table** option by either clicking the **Data Source View** menu or right-clicking in an open area of the **Tables** or **Diagram** panes.</span></span>  
  
4.  <span data-ttu-id="2dcc5-124">**관계 지정** 대화 상자에서 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-124">In the **Specify Relationship** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="2dcc5-125">**원본(외래 키) 테이블** 목록에서 해당 테이블, 명명된 쿼리 또는 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-125">Select the appropriate table, named query, or view in the **Source (foreign key) table** list.</span></span>  
  
    2.  <span data-ttu-id="2dcc5-126">**대상(기본 키) 테이블** 목록에서 해당 테이블, 명명된 쿼리 또는 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-126">Select the appropriate table, named query, or view in the **Destination (primary key) table** lists.</span></span>  
  
    3.  <span data-ttu-id="2dcc5-127">**원본 열** 및 **대상 열** 목록에서 열을 선택하여 두 테이블 간의 관계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-127">Select columns from the **Source Columns** and **Destination Columns** lists to create a relationship between the two tables.</span></span>  
  
         <span data-ttu-id="2dcc5-128">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에서 기본 테이블, 뷰 또는 명명된 쿼리의 데이터를 샘플링하여 잘못된 방향(외래 키에서 기본 키로의 방향이 아닌 기본 키에서 외래 키로의 방향)으로 관계가 정의된 것을 감지하면 순서를 반대로 바꾸라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-128">If [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] detects, by sampling the data in the underlying table, view, or named query, that you have defined the relationship in the wrong direction (from the primary key to the foreign key rather than from the foreign key to the primary key), you will be prompted to reverse the order.</span></span> <span data-ttu-id="2dcc5-129">신속하게 순서를 반대로 바꾸려면 **반대로**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-129">To quickly reverse the order, click **Reverse**.</span></span>  
  
         <span data-ttu-id="2dcc5-130">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에서 선택한 열에 대한 관계가 이미 있음을 감지하면 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-130">If [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] detects that a relationship already exists for the columns you have selected, you will be prompted.</span></span> <span data-ttu-id="2dcc5-131">중복 관계는 정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-131">You cannot define duplicate relationships.</span></span>  
  
    4.  <span data-ttu-id="2dcc5-132">필요에 따라 **설명** 입력란에 관계에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-132">Optionally, in the **Description** box, type a description for the relationship.</span></span>  
  
##  <a name="to-view-or-modify-a-relationship-in-the-diagram-pane"></a><a name="bkmk_diagrampane"></a><span data-ttu-id="2dcc5-133">다이어그램 창에서 관계를 보거나 수정 하려면</span><span class="sxs-lookup"><span data-stu-id="2dcc5-133">To view or modify a relationship in the Diagram pane</span></span>  
  
-   <span data-ttu-id="2dcc5-134">**데이터 원본 뷰 디자이너** 의 **다이어그램**창에서 보려는 관계를 마우스 오른쪽 단추로 클릭한 다음 **관계 편집** 을 클릭하거나 간단하게 관계 화살표를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-134">In the **Diagram** pane in **Data Source View Designer**, right-click the relationship that you want to view and click **Edit Relationship** (or simply double-click the relationship arrow).</span></span>  <span data-ttu-id="2dcc5-135">**관계 편집** 대화 상자를 사용하여 관계를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-135">Use the **Edit Relationship** dialog box to modify the relationship.</span></span>  
  
##  <a name="to-view-or-modify-a-relationship-in-the-tables-pane"></a><a name="bkmk_tablespane"></a><span data-ttu-id="2dcc5-136">테이블 창에서 관계를 보거나 수정 하려면</span><span class="sxs-lookup"><span data-stu-id="2dcc5-136">To view or modify a relationship in the Tables pane</span></span>  
  
1.  <span data-ttu-id="2dcc5-137">**데이터 원본 뷰 디자이너** 의 **테이블**창에서 관계를 보거나 수정하려는 테이블, 뷰 또는 명명된 쿼리를 찾아 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-137">In the **Tables** pane in **Data Source View Designer**, locate and then expand the table, view or named query containing the relationship that you wish to view or modify.</span></span>  
  
2.  <span data-ttu-id="2dcc5-138">**관계** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-138">Expand the **Relationships** folder.</span></span>  <span data-ttu-id="2dcc5-139">선택한 테이블, 뷰 또는 명명된 쿼리와 다른 테이블, 뷰 및 명명된 쿼리 간의 관계가 표시되고 관계 열이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-139">The relationships between the selected table, view or named query and other tables, views and named queries appear with the relationship column listed.</span></span>  
  
3.  <span data-ttu-id="2dcc5-140">수정하려는 관계를 마우스 오른쪽 단추로 클릭한 다음 **관계 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dcc5-140">Right-click the relationship you want to modify, and then click **Edit Relationship**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dcc5-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2dcc5-141">See Also</span></span>  
 [<span data-ttu-id="2dcc5-142">다차원 모델의 데이터 원본 뷰</span><span class="sxs-lookup"><span data-stu-id="2dcc5-142">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)  
  
  
