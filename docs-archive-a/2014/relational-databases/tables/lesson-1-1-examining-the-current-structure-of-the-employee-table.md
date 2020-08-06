---
title: Employee 테이블의 현재 구조 검사 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- examining the current structure of the employee
ms.assetid: d546a820-105a-417d-ac35-44a6d1d70ac6
author: stevestein
ms.author: sstein
ms.openlocfilehash: b7f63773ebc1f28fb24f8f1000c3f87ee4d50544
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638608"
---
# <a name="examining-the-current-structure-of-the-employee-table"></a><span data-ttu-id="f9ba1-102">Employee 테이블의 현재 구조 검사</span><span class="sxs-lookup"><span data-stu-id="f9ba1-102">Examining the Current Structure of the Employee Table</span></span>
  <span data-ttu-id="f9ba1-103"> 예제 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에는 **HumanResources** 스키마에 **Employee** 테이블이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ba1-103">The sample [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database contains an **Employee** table in the **HumanResources** schema.</span></span> <span data-ttu-id="f9ba1-104">원래 테이블이 변경되지 않도록 이 단계에서는 **EmployeeDemo** 라는 **Employee**테이블의 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f9ba1-104">To avoid changing the original table, this step makes a copy of the **Employee** table named **EmployeeDemo**.</span></span> <span data-ttu-id="f9ba1-105">예를 단순화하기 위해 원래 테이블에서 5개의 열만 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ba1-105">To simplify the example, you only copy five columns from the original table.</span></span> <span data-ttu-id="f9ba1-106">그런 다음 **HumanResources. EmployeeDemo** 테이블을 쿼리하여 데이터 형식을 사용 하지 않고 테이블에서 데이터를 구조화 하는 방법을 검토 합니다 `hierarchyid` .</span><span class="sxs-lookup"><span data-stu-id="f9ba1-106">Then, you query the **HumanResources.EmployeeDemo** table to review how the data is structured in a table without using the `hierarchyid` data type.</span></span>  
  
### <a name="to-copy-the-employee-table"></a><span data-ttu-id="f9ba1-107">Employee 테이블을 복사하려면</span><span class="sxs-lookup"><span data-stu-id="f9ba1-107">To copy the Employee table</span></span>  
  
1.  <span data-ttu-id="f9ba1-108">쿼리 편집기 창에서 다음 코드를 실행하여 테이블 구조와 데이터를 **Employee** 테이블에서 **EmployeeDemo**라는 새 테이블로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ba1-108">In a Query Editor window, run the following code to copy the table structure and data from the **Employee** table into a new table named **EmployeeDemo**.</span></span>  
  
    ```  
    USE AdventureWorks ;  
    GO  
  
    SELECT EmployeeID, LoginID, ManagerID, Title, HireDate   
    INTO HumanResources.EmployeeDemo   
    FROM HumanResources.Employee ;  
    GO  
    ```  
  
### <a name="to-examine-the-structure-and-data-of-the-employeedemo-table"></a><span data-ttu-id="f9ba1-109">EmployeeDemo 테이블의 구조와 데이터를 검사하려면</span><span class="sxs-lookup"><span data-stu-id="f9ba1-109">To examine the structure and data of the EmployeeDemo table</span></span>  
  
-   <span data-ttu-id="f9ba1-110">이 새 **EmployeeDemo** 테이블은 새 구조로 마이그레이션할 수 있는 기존 데이터베이스의 일반적인 테이블을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f9ba1-110">This new **EmployeeDemo** table represents a typical table in an existing database that you might want to migrate to a new structure.</span></span> <span data-ttu-id="f9ba1-111">쿼리 편집기 창에서 다음 코드를 실행하여 테이블이 자체 조인을 통해 직원/관리자 관계를 나타내는 방법을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ba1-111">In a Query Editor window, run the following code to show how the table uses a self join to display the employee/manager relationships:</span></span>  
  
    ```  
    SELECT   
         Mgr.EmployeeID AS MgrID, Mgr.LoginID AS Manager,   
         Emp.EmployeeID AS E_ID, Emp.LoginID, Emp.Title  
    FROM HumanResources.EmployeeDemo AS Emp  
    LEFT JOIN HumanResources.EmployeeDemo AS Mgr  
    ON Emp.ManagerID = Mgr.EmployeeID  
    ORDER BY MgrID, E_ID  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    MgrID Manager                 E_ID LoginID                  Title  
    NULL NULL                      109 adventure-works\ken0     Chief Executive Officer  
    3    adventure-works\roberto0  4   adventure-works\rob0     Senior Tool Designer  
    3    adventure-works\roberto0  9   adventure-works\gail0    Design Engineer  
    3    adventure-works\roberto0  11  adventure-works\jossef0  Design Engineer  
    3    adventure-works\roberto0  158 adventure-works\dylan0   Research and Development Manager  
    3    adventure-works\roberto0  263 adventure-works\ovidiu0  Senior Tool Designer  
    3    adventure-works\roberto0  267 adventure-works\michael8 Senior Design Engineer  
    3    adventure-works\roberto0  270 adventure-works\sharon0  Design Engineer  
    6    adventure-works\david0    2   adventure-works\kevin0   Marketing Assistant  
    ...  
    ```  
  
     <span data-ttu-id="f9ba1-112">결과로 총 290개의 행이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f9ba1-112">The results continue for a total of 290 rows.</span></span>  
  
 <span data-ttu-id="f9ba1-113">`ORDER BY` 절로 인해 출력에 각 관리자 수준의 직접 보고가 함께 나열되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ba1-113">Notice that the `ORDER BY` clause caused the output to list the direct reports of each management level together.</span></span> <span data-ttu-id="f9ba1-114">예를 들어 **MgrID** 3(roberto0)의 모든 직접 보고 7개가 서로 인접하게 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ba1-114">For instance, all seven of the direct reports of **MgrID** 3 (roberto0) are listed adjacent to each other.</span></span> <span data-ttu-id="f9ba1-115">불가능하지는 않지만 **MgrID** 3에게 결과적으로 보고하게 되는 모든 직원을 그룹화하기는 훨씬 더 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ba1-115">Although not impossible, it is much more difficult to group all those who eventually report to **MgrID** 3.</span></span>  
  
 <span data-ttu-id="f9ba1-116">다음 태스크에서는 `hierarchyid` 데이터 형식으로 새 테이블을 만들고 데이터를 새 테이블로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ba1-116">In the next task, we will create a new table with a `hierarchyid` data type, and move the data into the new table.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="f9ba1-117">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="f9ba1-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="f9ba1-118">기존 계층적 데이터로 테이블 채우기</span><span class="sxs-lookup"><span data-stu-id="f9ba1-118">Populating a Table with Existing Hierarchical Data</span></span>](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
  
