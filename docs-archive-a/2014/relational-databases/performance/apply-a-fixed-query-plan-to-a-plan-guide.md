---
title: 계획 지침에 정해진 쿼리 계획 적용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: bbf401f9-af7c-48e7-8a43-bf25e8af2fd7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 318955c4d0550e311873d8b4a6f79f72e04ac8af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729387"
---
# <a name="apply-a-fixed-query-plan-to-a-plan-guide"></a><span data-ttu-id="74ae4-102">계획 지침에 정해진 쿼리 계획 적용</span><span class="sxs-lookup"><span data-stu-id="74ae4-102">Apply a Fixed Query Plan to a Plan Guide</span></span>
  <span data-ttu-id="74ae4-103">OBJECT 또는 SQL 유형의 계획 지침에 정해진 쿼리 계획을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74ae4-103">You can apply a fixed query plan to a plan guide of type OBJECT or SQL.</span></span> <span data-ttu-id="74ae4-104">정해진 쿼리 계획을 적용하는 계획 지침은 최적화 프로그램에서 특정 쿼리에 대해 선택한 실행 계획보다 더 뛰어난 기존 실행 계획을 알고 있는 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="74ae4-104">Plan guides that apply a fixed query plan are useful when you know about an existing execution plan that performs better than the one selected by the optimizer for a particular query.</span></span>  
  
 <span data-ttu-id="74ae4-105">다음 예에서는 간단한 임시 SQL 문에 대한 계획 지침을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="74ae4-105">The following example creates a plan guide for a simple ad hoc SQL statement.</span></span> <span data-ttu-id="74ae4-106">`@hints` 매개 변수에 직접 쿼리에 대한 XML 실행 계획을 지정하여 이 문에 대해 원하는 쿼리 계획을 계획 지침에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="74ae4-106">The desired query plan for this statement is provided in the plan guide by specifying the XML Showplan for the query directly in the `@hints` parameter.</span></span> <span data-ttu-id="74ae4-107">예에서는 먼저 SQL 문을 실행하여 계획 캐시에 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="74ae4-107">The example first executes the SQL statement to generate a plan in the plan cache.</span></span> <span data-ttu-id="74ae4-108">이 예를 위해 생성된 계획이 원하는 계획이며 추가 쿼리 튜닝이 필요하지 않다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="74ae4-108">For the purposes of this example, it is assumed that the generated plan is the desired plan and no additional query tuning is required.</span></span> <span data-ttu-id="74ae4-109">쿼리에 대한 XML 실행 계획은 `sys.dm_exec_query_stats`, `sys.dm_exec_sql_text`및 `sys.dm_exec_text_query_plan` 동적 관리 뷰를 쿼리하여 가져오고 `@xml_showplan` 변수에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="74ae4-109">The XML Showplan for the query is obtained by querying the `sys.dm_exec_query_stats`, `sys.dm_exec_sql_text`, and `sys.dm_exec_text_query_plan` dynamic management views and is assigned to the `@xml_showplan` variable.</span></span> <span data-ttu-id="74ae4-110">그런 다음 `@xml_showplan` 변수는 `sp_create_plan_guide` 매개 변수의 `@hints` 문에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="74ae4-110">The `@xml_showplan` variable is then passed to the `sp_create_plan_guide` statement in the `@hints` parameter.</span></span> <span data-ttu-id="74ae4-111">또는 [sp_create_plan_guide_from_handle](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) 저장 프로시저를 사용하여 계획 캐시의 쿼리 계획에서 계획 지침을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74ae4-111">Or, you can create a plan guide from a query plan in the plan cache by using the [sp_create_plan_guide_from_handle](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) stored procedure.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;  
GO  
DECLARE @xml_showplan nvarchar(max);  
SET @xml_showplan = (SELECT query_plan  
    FROM sys.dm_exec_query_stats AS qs   
    CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
    CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, DEFAULT, DEFAULT) AS qp  
    WHERE st.text LIKE N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;%');  
  
EXEC sp_create_plan_guide   
    @name = N'Guide1_from_XML_showplan',   
    @stmt = N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = @xml_showplan;  
GO  
```  
  
  