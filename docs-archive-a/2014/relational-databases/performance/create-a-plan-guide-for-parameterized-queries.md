---
title: 매개 변수가 있는 쿼리를 위한 계획 지침 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- parameterized queries, plan guides for
- plan guides [SQL Server], parameterized queries
ms.assetid: b532ae16-66e7-4641-9bc8-b0d805853477
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 565610826f704274724ea05d821205a5b3391060
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661078"
---
# <a name="create-a-plan-guide-for-parameterized-queries"></a><span data-ttu-id="6a936-102">매개 변수가 있는 쿼리를 위한 계획 지침 만들기</span><span class="sxs-lookup"><span data-stu-id="6a936-102">Create a Plan Guide for Parameterized Queries</span></span>
  <span data-ttu-id="6a936-103">TEMPLATE 계획 지침은 지정된 형식으로 매개 변수화되는 독립 실행형 쿼리와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="6a936-103">A TEMPLATE plan guide matches stand-alone queries that parameterize to a specified form.</span></span>  
  
 <span data-ttu-id="6a936-104">다음 예에서는 지정된 형식으로 매개 변수화되는 쿼리와 일치하는 계획 지침을 만들고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 쿼리를 매개 변수화하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6a936-104">The following example creates a plan guide that matches any query that parameterizes to a specified form, and directs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to force parameterization of the query.</span></span> <span data-ttu-id="6a936-105">다음 두 개의 쿼리는 구문이 같고 상수 리터럴 값만 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="6a936-105">The following two queries are syntactically equivalent, but differ only in their constant literal values.</span></span>  
  
```  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45639;  
  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45640;  
```  
  
 <span data-ttu-id="6a936-106">매개 변수가 있는 쿼리 형식에 대한 계획 지침은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6a936-106">Here is the plan guide on the parameterized form of the query:</span></span>  
  
```  
EXEC sp_create_plan_guide   
    @name = N'TemplateGuide1',  
    @stmt = N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
              INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
                  ON h.SalesOrderID = d.SalesOrderID  
              WHERE h.SalesOrderID = @0',  
    @type = N'TEMPLATE',  
    @module_or_batch = NULL,  
    @params = N'@0 int',  
    @hints = N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
 <span data-ttu-id="6a936-107">앞의 예에서 `@stmt` 매개 변수의 값은 매개 변수가 있는 쿼리 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="6a936-107">In the previous example, the value for the `@stmt` parameter is the parameterized form of the query.</span></span> <span data-ttu-id="6a936-108">sp_create_plan_guide에서 사용하기 위해 이 값을 얻는 안정적인 한 가지 방법은 [sp_get_query_template](/sql/relational-databases/system-stored-procedures/sp-get-query-template-transact-sql) 시스템 저장 프로시저를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6a936-108">The only reliable way to obtain this value for use in sp_create_plan_guide is to use the [sp_get_query_template](/sql/relational-databases/system-stored-procedures/sp-get-query-template-transact-sql) system stored procedure.</span></span> <span data-ttu-id="6a936-109">다음 스크립트는 매개 변수가 있는 쿼리를 얻고 이에 대한 계획 지침을 만들기 위해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a936-109">The following script can be used both to obtain the parameterized query and then create a plan guide on it.</span></span>  
  
```  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
      INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
          ON h.SalesOrderID = d.SalesOrderID  
      WHERE h.SalesOrderID = 45639;',  
    @stmt OUTPUT,   
    @params OUTPUT  
EXEC sp_create_plan_guide N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6a936-110">`@stmt` 에 전달된 `sp_get_query_template` 매개 변수에 있는 상수 리터럴 값은 리터럴을 대체하는 매개 변수에 대해 선택한 데이터 형식에 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a936-110">The value of the constant literals in the `@stmt` parameter passed to `sp_get_query_template` might affect the data type that is chosen for the parameter that replaces the literal.</span></span> <span data-ttu-id="6a936-111">이는 계획 지침 일치에도 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="6a936-111">This will affect plan guide matching.</span></span> <span data-ttu-id="6a936-112">둘 이상의 계획 지침을 만들어 서로 다른 매개 변수 값 범위를 처리해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a936-112">You may have to create more than one plan guide to handle different parameter value ranges.</span></span>  
  
 <span data-ttu-id="6a936-113">또한 TEMPLATE 계획 지침은 SQL 계획 지침과도 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a936-113">You can also use TEMPLATE plan guides together with SQL plan guides.</span></span> <span data-ttu-id="6a936-114">예를 들어 쿼리 클래스가 매개 변수화되도록 TEMPLATE 계획 지침을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a936-114">For example, you can create a TEMPLATE plan guide to make sure that a class of queries is parameterized.</span></span> <span data-ttu-id="6a936-115">그런 다음 매개 변수가 있는 해당 쿼리 형식에 대한 SQL 계획 지침을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a936-115">You can then create an SQL plan guide on the parameterized form of that query.</span></span>  
  
  
