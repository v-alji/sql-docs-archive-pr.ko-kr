---
title: 데이터 원본 뷰에서 명명 된 쿼리 정의 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- named queries [Analysis Services], creating
- modifying named queries
- data source views [Analysis Services], named queries
ms.assetid: f09ba8aa-950e-4c0d-961e-970de13200be
author: minewiskan
ms.author: owend
ms.openlocfilehash: dfe2dbc6081e0c33f681ba894b16057c8890e0b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648653"
---
# <a name="define-named-queries-in-a-data-source-view-analysis-services"></a><span data-ttu-id="3b4a8-102">데이터 원본 뷰에서 명명된 쿼리 정의(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="3b4a8-102">Define Named Queries in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="3b4a8-103">명명된 쿼리는 테이블로 표현된 SQL 식입니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-103">A named query is a SQL expression represented as a table.</span></span> <span data-ttu-id="3b4a8-104">명명된 쿼리에 SQL 식을 지정하여 하나 이상의 데이터 원본에 있는 하나 이상의 테이블에서 반환된 행 및 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-104">In a named query, you can specify an SQL expression to select rows and columns returned from one or more tables in one or more data sources.</span></span> <span data-ttu-id="3b4a8-105">식을 기반으로 한다는 점을 제외하면 명명된 쿼리는 관계 및 행이 있는 데이터 원본 뷰(DSV)의 다른 테이블과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-105">A named query is like any other table in a data source view (DSV) with rows and relationships, except that the named query is based on an expression.</span></span>  
  
 <span data-ttu-id="3b4a8-106">명명된 쿼리를 사용하면 기본 데이터 원본을 수정하지 않고 DSV에 있는 기존 테이블의 관계형 스키마를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-106">A named query lets you extend the relational schema of existing tables in DSV without modifying the underlying data source.</span></span> <span data-ttu-id="3b4a8-107">예를 들어 일련의 명명된 쿼리를 사용하여 복잡한 차원 테이블을 데이터베이스 차원에서 사용할 수 있도록 더 작고 간단한 차원 테이블로 분할할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-107">For example, a series of named queries can be used to split up a complex dimension table into smaller, simpler dimension tables for use in database dimensions.</span></span> <span data-ttu-id="3b4a8-108">명명된 쿼리를 사용하여 하나 이상의 데이터 원본의 여러 데이터베이스 테이블을 하나의 데이터 원본 뷰 테이블로 조인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-108">A named query can also be used to join multiple database tables from one or more data sources into a single data source view table.</span></span>  
  
## <a name="creating-a-named-query"></a><span data-ttu-id="3b4a8-109">명명된 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="3b4a8-109">Creating a Named Query</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b4a8-110">명명된 계산을 명명된 쿼리에 추가할 수 없으며 명명된 계산이 포함된 테이블을 명명된 쿼리의 기반으로 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-110">You cannot add a named calculation to a named query, nor can you base a named query on a table that contains a named calculation.</span></span>  
  
 <span data-ttu-id="3b4a8-111">명명된 쿼리를 만들 때는 테이블의 열과 데이터를 반환하는 SQL 쿼리 및 쿼리의 이름을 지정하고 필요에 따라 명명된 쿼리에 대한 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-111">When you create a named query, you specify a name, the SQL query returning the columns and data for the table, and optionally, a description of the named query.</span></span> <span data-ttu-id="3b4a8-112">SQL 식은 데이터 원본 뷰에서 다른 테이블을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-112">The SQL expression can refer to other tables in the data source view.</span></span> <span data-ttu-id="3b4a8-113">명명된 쿼리를 정의하면 명명된 쿼리의 SQL 쿼리가 데이터 원본의 공급자에게 전송되어 유효성이 전체적으로 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-113">After the named query is defined, the SQL query in a named query is sent to the provider for the data source and validated as a whole.</span></span> <span data-ttu-id="3b4a8-114">공급자가 SQL 쿼리에서 오류를 찾을 수 없으면 해당 열이 테이블에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-114">If the provider does not find any errors in the SQL query, the column is added to the table.</span></span>  
  
 <span data-ttu-id="3b4a8-115">SQL 쿼리에서 참조되는 테이블 및 열은 한정되어서는 안 되며 한정할 경우 테이블 이름으로만 한정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-115">Tables and columns referenced in the SQL query should not be qualified or should be qualified by the table name only.</span></span> <span data-ttu-id="3b4a8-116">예를 들어 테이블의 SaleAmount 열을 참조하려면 `SaleAmount` 나 `Sales.SaleAmount` 는 유효하지만 `dbo.Sales.SaleAmount` 는 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-116">For example, to refer to the SaleAmount column in a table, `SaleAmount` or `Sales.SaleAmount` is valid, but `dbo.Sales.SaleAmount` generates an error.</span></span>  
  
 <span data-ttu-id="3b4a8-117">**참고**[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 데이터 원본을 쿼리하는 명명된 쿼리를 정의할 때 상관 하위 쿼리 및 GROUP BY 절을 포함하는 명명된 쿼리는 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-117">**Note** When defining a named query that queries a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 data source, a named query that contains a correlated subquery and a GROUP BY clause will fail.</span></span> <span data-ttu-id="3b4a8-118">자세한 내용은 [기술 문서에서](https://support.microsoft.com/kb/274729) 버그: 상관 하위 쿼리 및 GROUP BY를 포함하는 SELECT 문의 내부 오류(BUG: Internal Error with SELECT Statement Containing Correlated Subquery and GROUP BY) [!INCLUDE[msCoName](../../includes/msconame-md.md)] 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-118">For more information, see [Internal Error with SELECT Statement Containing Correlated Subquery and GROUP BY](https://support.microsoft.com/kb/274729) in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base.</span></span>  
  
## <a name="add-or-edit-a-named-query"></a><span data-ttu-id="3b4a8-119">명명된 쿼리 추가 또는 편집</span><span class="sxs-lookup"><span data-stu-id="3b4a8-119">Add or Edit a Named Query</span></span>  
  
1.  <span data-ttu-id="3b4a8-120">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 명명된 쿼리를 추가할 데이터 원본 뷰가 포함된 프로젝트를 열거나 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-120">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you want to add a named query.</span></span>  
  
2.  <span data-ttu-id="3b4a8-121">솔루션 탐색기에서 **데이터 원본 뷰** 폴더를 확장한 다음 해당 데이터 원본 뷰를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-121">In Solution Explorer, expand the **Data Source Views** folder, then double-click the data source view.</span></span>  
  
3.  <span data-ttu-id="3b4a8-122">**테이블** 또는 **다이어그램** 창에서 열린 영역을 마우스 오른쪽 단추로 클릭한 다음 **새 명명된 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-122">In the **Tables** or **Diagram** pane, right-click an open area and then click **New Named Query**.</span></span>  
  
4.  <span data-ttu-id="3b4a8-123">**명명된 쿼리 만들기** 대화 상자에서 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-123">In the **Create Named Query** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="3b4a8-124">**이름** 입력란에 쿼리 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-124">In the **Name** text box, type a query name.</span></span>  
  
    2.  <span data-ttu-id="3b4a8-125">필요에 따라 **설명** 입력란에 쿼리에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-125">Optionally, in the **Description** text box, type a description for the query.</span></span>  
  
    3.  <span data-ttu-id="3b4a8-126">**데이터 원본** 목록 상자에서 명명된 쿼리가 실행될 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-126">In the **Data Source** list box, select the data source against which the named query will execute.</span></span>  
  
    4.  <span data-ttu-id="3b4a8-127">아래쪽 창에 쿼리를 입력하거나 그래픽 쿼리 작성 도구를 사용하여 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-127">Type the query in the bottom pane, or use the graphical query building tools to create a query.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3b4a8-128">쿼리 작성 UI(사용자 인터페이스)는 데이터 원본에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-128">The query-building user interface (UI) depends on the data source.</span></span> <span data-ttu-id="3b4a8-129">그래픽 UI가 아닌 텍스트 기반의 일반 UI가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-129">Instead of getting a graphical UI, you can get a generic UI, which is text-based.</span></span> <span data-ttu-id="3b4a8-130">이렇게 다른 UI를 사용해도 같은 작업을 수행할 수 있지만 수행 방식은 서로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-130">You can accomplish the same things with these different UIs, but you must do so in different ways.</span></span> <span data-ttu-id="3b4a8-131">자세한 내용은 [명명된 쿼리 만들기 또는 편집 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](../create-or-edit-named-query-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-131">For more information, see [Create or Edit Named Query Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../create-or-edit-named-query-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
5.  <span data-ttu-id="3b4a8-132">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-132">Click **OK**.</span></span> <span data-ttu-id="3b4a8-133">테이블이 명명된 쿼리로 바뀌었음을 나타내기 위해 겹치는 두 개의 테이블을 표시하는 아이콘이 테이블 머리글에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-133">An icon showing two overlapping tables appears in the table header to indicate that the table has been replaced by a named query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b4a8-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3b4a8-134">See Also</span></span>  
 <span data-ttu-id="3b4a8-135">[다차원 모델의 데이터 원본 뷰](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="3b4a8-135">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="3b4a8-136">데이터 원본 뷰에서 명명된 계산 정의&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3b4a8-136">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  
