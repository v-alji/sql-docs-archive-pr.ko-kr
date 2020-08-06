---
title: 조인 필터 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication], join
- publications [SQL Server replication], join filters
- merge replication join filters [SQL Server replication]
- join filters
ms.assetid: dd78fd8f-56e3-4582-9abd-6bc25c91e075
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b97e7d7b53e6a3fdb242d1272e013bbd45f0ed17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638700"
---
# <a name="join-filters"></a><span data-ttu-id="e9f2e-102">Join Filters</span><span class="sxs-lookup"><span data-stu-id="e9f2e-102">Join Filters</span></span>
  <span data-ttu-id="e9f2e-103">조인 필터를 사용하여 게시의 관련 테이블이 필터링되는 방식에 따라 테이블을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-103">A join filter allows a table to be filtered based on how a related table in the publication is filtered.</span></span> <span data-ttu-id="e9f2e-104">일반적으로 부모 테이블은 매개 변수가 있는 필터를 사용하여 필터링됩니다. 그리고 나서 테이블 간 조인을 정의하는 방식과 매우 유사하게 하나 이상의 조인 필터가 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-104">Typically a parent table is filtered using a parameterized filter; then one or more join filters are defined in much the same way that you define a join between tables.</span></span> <span data-ttu-id="e9f2e-105">조인 필터는 매개 변수가 있는 필터를 확장하므로 관련 테이블의 데이터는 조인 필터 절과 일치할 경우에만 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-105">The join filters extend the parameterized filter so that the data in the related tables is only replicated if it matches the join filter clause.</span></span>  
  
 <span data-ttu-id="e9f2e-106">일반적으로 조인 필터는 조인 필터가 적용되는 테이블에 대해 정의된 기본 키/외래 키 관계를 따르지만 기본 키/외래 키 관계를 엄격하게 따르지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-106">Join filters typically follow the primary key/foreign key relationships defined for the tables to which they are applied, but they are not limited strictly to primary key/foreign key relationships.</span></span> <span data-ttu-id="e9f2e-107">조인 필터는 두 테이블의 관련 데이터를 비교하는 논리를 기반으로 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-107">The join filter can be based on any logic that compares related data in two tables.</span></span>  
  
 <span data-ttu-id="e9f2e-108">[!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] 샘플 데이터베이스에 기본 키/외래 키 관계를 따르는 다음과 같은 테이블이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-108">Consider the following tables in the [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] sample database, which are related through primary key to foreign key relationships:</span></span>  
  
-   <span data-ttu-id="e9f2e-109">**HumanResources.Employee**</span><span class="sxs-lookup"><span data-stu-id="e9f2e-109">**HumanResources.Employee**</span></span>  
  
-   <span data-ttu-id="e9f2e-110">**Sales.SalesOrderHeader**</span><span class="sxs-lookup"><span data-stu-id="e9f2e-110">**Sales.SalesOrderHeader**</span></span>  
  
-   <span data-ttu-id="e9f2e-111">**Sales.SalesOrderDetail**</span><span class="sxs-lookup"><span data-stu-id="e9f2e-111">**Sales.SalesOrderDetail**</span></span>  
  
 <span data-ttu-id="e9f2e-112">이러한 테이블을 이동이 잦은 영업 직원을 지원하는 애플리케이션에 사용할 수 있지만 **HumanResources.Employee** 테이블의 각 영업 직원이 고객 주문과 관련된 데이터만 받도록 필터링해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-112">These tables could be used in an application to support a mobile sales force, but they must be filtered so that each sales person in the **HumanResources.Employee** table receives only the data relevant to their customers' orders.</span></span>  
  
 <span data-ttu-id="e9f2e-113">이를 위해서는 먼저 부모 테이블에 매개 변수가 있는 필터를 정의해야 합니다. 이 예에서는 **HumanResources.Employee** 테이블이 부모 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-113">The first step is to define a parameterized filter on the parent table, which in this example is the **HumanResources.Employee** table.</span></span> <span data-ttu-id="e9f2e-114">이 테이블의 **LoginID**열에는 각 직원에 대한 로그인이 *domain\login*형식으로 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-114">This table includes the column **LoginID**, which contains the login for each employee in the form *domain\login*.</span></span> <span data-ttu-id="e9f2e-115">각 직원이 자신에게 관련된 데이터만 받을 수 있도록 이 테이블을 필터링하려면 다음과 같은 매개 변수가 있는 필터 절을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-115">To filter this table so that each employee receives only the data related to them, specify a parameterized filter clause of:</span></span>  
  
```  
LoginID = SUSER_SNAME()  
```  
  
 <span data-ttu-id="e9f2e-116">이 필터는 각 직원의 구독이 **HumanResources.Employee** 테이블에서 해당 직원(이 경우에는 단일 행임)과 관련된 데이터만 포함하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-116">This filter ensures that each employee's subscription only contains data from the **HumanResources.Employee** table that is relevant to that employee (which in this case is a single row).</span></span> <span data-ttu-id="e9f2e-117">자세한 내용은 [매개 변수가 있는 행 필터](parameterized-filters-parameterized-row-filters.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-117">For more information, see [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="e9f2e-118">다음 단계는 두 테이블 간에 조인을 지정하는 데 사용된 구문과 유사한 구문을 사용하여 이 필터를 각 관련 테이블로 확장하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-118">The next step is to extend this filter to each of the related tables, using syntax similar to that used to specify a join between two tables.</span></span> <span data-ttu-id="e9f2e-119">첫 번째 조인 필터 절은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-119">The first join filter clause is:</span></span>  
  
```  
Employee.EmployeeID = SalesOrderHeader.SalesPersonID  
```  
  
 <span data-ttu-id="e9f2e-120">이 절은 구독이 각 영업 직원과 관련된 주문 데이터만 포함하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-120">This ensures the subscription contains only the order data relevant to each sales person.</span></span> <span data-ttu-id="e9f2e-121">두 번째 조인 필터 절은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-121">The second join filter clause is:</span></span>  
  
```  
SalesOrderHeader.SalesOrderID = SalesOrderDetail.SalesOrderID  
```  
  
 <span data-ttu-id="e9f2e-122">이 절은 구독이 각 영업 직원의 주문 데이터와 관련된 정보 데이터만 포함하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-122">This ensures the subscription contains only the detail data related to the order data for each sales person.</span></span> <span data-ttu-id="e9f2e-123">이 예에서는 각 지점에서 조인하는 단일 테이블을 보여 줍니다. 각 지점에 둘 이상의 테이블을 조인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-123">This example shows a single table being joined at each point; it is also possible to join more than one table at each point.</span></span>  
  
 <span data-ttu-id="e9f2e-124">조인 필터는 새 게시 마법사 및 **게시 속성** 대화 상자를 통해 한 번에 하나씩 추가하거나 프로그래밍 방식으로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-124">Join filters can be added one at a time through the New Publication Wizard and the **Publication Properties** dialog box, or they can be added programmatically.</span></span> <span data-ttu-id="e9f2e-125">또한 새 게시 마법사를 통해 조인 필터를 자동으로 생성할 수 있습니다. 테이블에 대한 행 필터를 지정하면 조인 필터가 모든 관련 테이블에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-125">They can also be generated automatically through the New Publication Wizard: you specify a row filter for a table and join filters are applied to all related tables.</span></span> <span data-ttu-id="e9f2e-126">자세한 내용은 [병합 아티클 사이에서 조인 필터 정의 및 수정](../publish/define-and-modify-a-join-filter-between-merge-articles.md), [병합 아티클 간의 조인 필터 집합 자동 생성&#40;SQL Server Management Studio&#41;](../publish/automatically-generate-join-filters-between-merge-articles.md) 및 [아티클 정의](../publish/define-an-article.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-126">For more information, see [Define and Modify a Join Filter Between Merge Articles](../publish/define-and-modify-a-join-filter-between-merge-articles.md), [Automatically Generate a Set of Join Filters Between Merge Articles &#40;SQL Server Management Studio&#41;](../publish/automatically-generate-join-filters-between-merge-articles.md), and [Define an Article](../publish/define-an-article.md).</span></span>  
  
## <a name="optimizing-join-filter-performance"></a><span data-ttu-id="e9f2e-127">조인 필터 성능 최적화</span><span class="sxs-lookup"><span data-stu-id="e9f2e-127">Optimizing Join Filter Performance</span></span>  
 <span data-ttu-id="e9f2e-128">다음 지침에 따라 조인 필터 성능을 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-128">Join filter performance can be optimized by following these guidelines:</span></span>  
  
-   <span data-ttu-id="e9f2e-129">조인 필터 계층에서 테이블의 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-129">Limit the number of tables in the join filter hierarchy.</span></span>  
  
     <span data-ttu-id="e9f2e-130">조인 필터는 테이블을 무제한 포함할 수 있지만 테이블 수가 많은 필터는 병합 처리 중 성능에 상당한 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-130">Join Filters can involve an unlimited number of tables, but filters with a large number of tables can significantly impact performance during merge processing.</span></span> <span data-ttu-id="e9f2e-131">5개 이상의 테이블을 가진 조인 필터를 생성하는 경우 다른 해결책을 고려하는 것이 좋습니다. 크기가 작거나, 변경될 가능성이 없거나, 기본적으로 조회 테이블에 해당하는 테이블은 필터링하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-131">If you are generating join filters of five or more tables, consider other solutions: do not filter tables that are small, not subject to change, or are primarily lookup tables.</span></span> <span data-ttu-id="e9f2e-132">구독 간에 분할해야 하는 테이블 사이에서만 조인 필터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-132">Use join filters only between tables that must be partitioned among subscriptions.</span></span>  
  
-   <span data-ttu-id="e9f2e-133">필요한 경우 **join unique key** 옵션을 **True** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-133">Set the **join unique key** option to **True** where appropriate.</span></span>  
  
     <span data-ttu-id="e9f2e-134">병합 프로세스는 부모 테이블에서 조인된 열이 고유한 경우 사용할 수 있는 특별 성능 최적화를 가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-134">The merge process has special performance optimizations available if the joined column in the parent is unique.</span></span> <span data-ttu-id="e9f2e-135">조인 조건이 고유 열을 기반으로 하는 경우에는 조인 필터에 대해 **join unique key** 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-135">If the join condition is based on a unique column, set the **join unique key** option for the join filter.</span></span> <span data-ttu-id="e9f2e-136">이러한 옵션을 설정하는 방법은 이전 섹션에 나열된 방법 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-136">For information about setting this option, see the how-to topics listed in the previous section.</span></span>  
  
-   <span data-ttu-id="e9f2e-137">조인 필터에서 참조된 열은 인덱싱되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-137">Ensure that the columns referenced in join filters are indexed.</span></span>  
  
     <span data-ttu-id="e9f2e-138">필터에서 참조된 열이 인덱싱된 경우 복제는 필터를 보다 효과적으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-138">If the columns referenced in the filter are indexed, replication can process the filters more efficiently.</span></span>  
  
-   <span data-ttu-id="e9f2e-139">조인 필터와 비슷하게 실행되는 행 필터는 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-139">Do not create row filters that mimic join filters.</span></span>  
  
     <span data-ttu-id="e9f2e-140">다음과 같이 WHERE 절에서 하위 쿼리를 사용하여 조인 필터와 비슷하게 실행되는 행 필터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-140">It is possible to create row filters that mimic join filters by using a subquery in a WHERE clause, such as:</span></span>  
  
    ```  
    WHERE Customer.SalesPersonID IN (SELECT EmployeeID FROM Employee WHERE LoginID = SUSER_SNAME())   
    ```  
  
     <span data-ttu-id="e9f2e-141">하지만 이러한 모든 논리를 하위 쿼리가 아닌 조인 필터로 표시하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-141">It is strongly recommended that all such logic be expressed in a join filter rather than a subquery.</span></span> <span data-ttu-id="e9f2e-142">애플리케이션에서 행 필터에 하위 쿼리를 사용해야 할 경우에는 하위 쿼리가 변경하지 않는 조회 데이터만 참조하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-142">If your application requires a row filter to use a subsquery, ensure that the subquery only references lookup data that does not change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f2e-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e9f2e-143">See Also</span></span>  
 <span data-ttu-id="e9f2e-144">[병합 복제의 게시된 데이터 필터링](filter-published-data-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="e9f2e-144">[Filter Published Data for Merge Replication](filter-published-data-for-merge-replication.md) </span></span>  
 [<span data-ttu-id="e9f2e-145">매개 변수가 있는 행 필터</span><span class="sxs-lookup"><span data-stu-id="e9f2e-145">Parameterized Row Filters</span></span>](parameterized-filters-parameterized-row-filters.md)  
  
  
