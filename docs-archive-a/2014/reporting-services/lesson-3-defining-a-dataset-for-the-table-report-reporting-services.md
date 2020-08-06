---
title: '3단원: 테이블 보고서에 대한 데이터 세트 정의(Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ee93dfcb-8f52-4d63-b4f6-0d38e00fd350
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 33fe48a60db2e7d15d205a4bff6205347f95c61c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648853"
---
# <a name="lesson-3-defining-a-dataset-for-the-table-report-reporting-services"></a><span data-ttu-id="4233b-102">3단원: 테이블 보고서에 대한 데이터 세트 정의(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="4233b-102">Lesson 3: Defining a Dataset for the Table Report (Reporting Services)</span></span>
  <span data-ttu-id="4233b-103">데이터 원본을 정의한 후에는 데이터 세트를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-103">After you define the data source, you need to define a dataset.</span></span> <span data-ttu-id="4233b-104">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]에서 보고서에 사용하는 데이터는 *데이터 세트*에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-104">In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], data that you use in reports is contained in a *dataset*.</span></span> <span data-ttu-id="4233b-105">데이터 세트에는 데이터 원본에 대한 포인터와 보고서에서 사용하는 쿼리는 물론 계산된 필드 및 변수도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-105">A dataset includes a pointer to a data source and a query to be used by the report, as well as calculated fields and variables.</span></span>  
  
 <span data-ttu-id="4233b-106">보고서 디자이너에서 쿼리 디자이너를 사용하여 쿼리를 디자인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-106">You can use the query designer in Report Designer to design the query.</span></span> <span data-ttu-id="4233b-107">이 자습서에서는 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]**2008** 데이터베이스에서 판매 주문 정보를 검색하는 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-107">For this tutorial, you will create a query that retrieves sales order information from the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]**2008** database.</span></span>  
  
### <a name="to-define-a-transact-sql-query-for-report-data"></a><span data-ttu-id="4233b-108">보고서 데이터에 대한 Transact-SQL 쿼리를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="4233b-108">To define a Transact-SQL query for report data</span></span>  
  
1.  <span data-ttu-id="4233b-109">**보고서 데이터** 창에서 **새로 만들기**를 클릭 한 다음 **데이터 집합 ...** 을 클릭 합니다. **데이터 집합 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-109">In the **Report Data** pane, click **New**, and then click **Dataset...**. The **Dataset Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="4233b-110">**이름** 상자에 **AdventureWorksDataset**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-110">In the **Name** box, type **AdventureWorksDataset**.</span></span>  
  
3.  <span data-ttu-id="4233b-111">**내 보고서에 포함된 데이터 집합 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-111">Click **Use a dataset embedded in my report**.</span></span>  
  
4.  <span data-ttu-id="4233b-112">데이터 원본의 이름 AdventureWorks2012가 **데이터 원본** 입력란에 있고 **쿼리 유형** 이 **텍스트**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-112">Make sure the name of your data source, AdventureWorks2012, is in the **Data source** text box, and that the **Query type** is **Text**.</span></span>  
  
5.  <span data-ttu-id="4233b-113">다음 Transact-SQL 쿼리를 **쿼리** 상자에 입력하거나, 복사하여 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-113">Type, or copy and paste, the following Transact-SQL query into the **Query** box.</span></span>  
  
    ```  
    SELECT   
       soh.OrderDate AS [Date],   
       soh.SalesOrderNumber AS [Order],   
       pps.Name AS Subcat, pp.Name as Product,    
       SUM(sd.OrderQty) AS Qty,  
       SUM(sd.LineTotal) AS LineTotal  
    FROM Sales.SalesPerson sp   
       INNER JOIN Sales.SalesOrderHeader AS soh   
          ON sp.BusinessEntityID = soh.SalesPersonID  
       INNER JOIN Sales.SalesOrderDetail AS sd   
          ON sd.SalesOrderID = soh.SalesOrderID  
       INNER JOIN Production.Product AS pp   
          ON sd.ProductID = pp.ProductID  
       INNER JOIN Production.ProductSubcategory AS pps   
          ON pp.ProductSubcategoryID = pps.ProductSubcategoryID  
       INNER JOIN Production.ProductCategory AS ppc   
          ON ppc.ProductCategoryID = pps.ProductCategoryID  
    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name,   
       soh.SalesPersonID  
    HAVING ppc.Name = 'Clothing'  
    ```  
  
6.  <span data-ttu-id="4233b-114">(옵션) **쿼리 디자이너** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-114">(Optional) Click the **Query Designer** button.</span></span> <span data-ttu-id="4233b-115">쿼리가 텍스트 기반 쿼리 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-115">The query is displayed in the text-based query designer.</span></span> <span data-ttu-id="4233b-116">**텍스트로 편집**을 클릭하여 그래픽 쿼리 디자이너로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-116">You can toggle to the graphical query designer by clicking **Edit As Text**.</span></span> <span data-ttu-id="4233b-117">쿼리 디자이너 도구 모음에서 실행 **(!)** 단추를 클릭하여 쿼리 결과를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-117">View the results of the query by clicking the run **(!)** button on the query designer toolbar.</span></span>  
  
     <span data-ttu-id="4233b-118">[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 데이터베이스에서 네 가지 테이블의 여섯 필드에 있는 데이터를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-118">You see the data from six fields from four different tables in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="4233b-119">쿼리는 Transact-SQL 기능을 별칭으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-119">The query makes use of Transact-SQL functionality such as aliases.</span></span> <span data-ttu-id="4233b-120">예를 들어 SalesOrderHeader 테이블을 soh라고 부릅니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-120">For example, the SalesOrderHeader table is called soh.</span></span>  
  
     <span data-ttu-id="4233b-121">**확인** 을 클릭하여 쿼리 디자이너를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-121">Click **OK** to exit the query designer.</span></span>  
  
7.  <span data-ttu-id="4233b-122">**확인**을 클릭하여 **데이터 세트 속성** 대화 상자를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-122">Click **OK** to exit the **Dataset Properties** dialog box.</span></span>  
  
     <span data-ttu-id="4233b-123">**AdventureWorksDataset** 데이터 세트 및 필드가 보고서 데이터 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-123">Your **AdventureWorksDataset** dataset and fields appear in the Report Data pane.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="4233b-124">다음 태스크</span><span class="sxs-lookup"><span data-stu-id="4233b-124">Next Task</span></span>  
 <span data-ttu-id="4233b-125">보고서에 대한 데이터를 검색하는 쿼리를 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-125">You have successfully specified a query that retrieves data for your report.</span></span> <span data-ttu-id="4233b-126">다음 단원에서는 보고서 레이아웃을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4233b-126">Next, you will create the report layout.</span></span> <span data-ttu-id="4233b-127">[4단원: 보고서에 테이블 추가&#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4233b-127">See [Lesson 4: Adding a Table to the Report &#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4233b-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4233b-128">See Also</span></span>  
 <span data-ttu-id="4233b-129">[SSRS&#41;&#40;보고서 디자이너 SQL Server Data Tools의 쿼리 디자인 도구](report-data/query-design-tools-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4233b-129">[Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md) </span></span>  
 <span data-ttu-id="4233b-130">[SSRS &#40;SQL Server 연결 유형&#41;](report-data/sql-server-connection-type-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4233b-130">[SQL Server Connection Type &#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md) </span></span>  
 [<span data-ttu-id="4233b-131">자습서: Transact-SQL 문 작성</span><span class="sxs-lookup"><span data-stu-id="4233b-131">Tutorial: Writing Transact-SQL Statements</span></span>](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
