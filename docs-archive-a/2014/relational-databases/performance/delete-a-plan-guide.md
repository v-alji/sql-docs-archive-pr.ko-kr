---
title: 계획 지침 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], deleting
ms.assetid: aa4d3188-6927-43de-a3e3-90fc16eeaca7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 303ad6f59cbe24265aec66f3cb780a5b4ad4f157
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730543"
---
# <a name="delete-a-plan-guide"></a><span data-ttu-id="a9c14-102">계획 지침 삭제</span><span class="sxs-lookup"><span data-stu-id="a9c14-102">Delete a Plan Guide</span></span>
  <span data-ttu-id="a9c14-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 계획 지침을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9c14-103">You can delete (drop) a plan guide in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a9c14-104">[!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 데이터베이스에서 모든 계획 지침을 삭제할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9c14-104">Using [!INCLUDE[tsql](../../includes/tsql-md.md)], you can also delete all of the plan guides in a database.</span></span>  
  
 <span data-ttu-id="a9c14-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="a9c14-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a9c14-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="a9c14-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a9c14-107">보안</span><span class="sxs-lookup"><span data-stu-id="a9c14-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a9c14-108">**계획 지침을 삭제하려면:**</span><span class="sxs-lookup"><span data-stu-id="a9c14-108">**To delete a plan guide, using:**</span></span>  
  
     [<span data-ttu-id="a9c14-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a9c14-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a9c14-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a9c14-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a9c14-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="a9c14-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a9c14-112">보안</span><span class="sxs-lookup"><span data-stu-id="a9c14-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a9c14-113">권한</span><span class="sxs-lookup"><span data-stu-id="a9c14-113">Permissions</span></span>  
 <span data-ttu-id="a9c14-114">OBJECT 계획 지침을 삭제하려면 계획 지침에서 참조되는 개체(예: 함수, 저장 프로시저)에 대한 변경 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c14-114">Deleting an OBJECT plan guide requires ALTER permission on the object (for example: function, stored procedure) that is referenced by the plan guide.</span></span> <span data-ttu-id="a9c14-115">다른 모든 계획 지침에는 ALTER DATABASE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c14-115">All other plan guides require ALTER DATABASE permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a9c14-116">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="a9c14-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-plan-guide"></a><span data-ttu-id="a9c14-117">계획 지침을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="a9c14-117">To delete a plan guide</span></span>  
  
1.  <span data-ttu-id="a9c14-118">더하기 기호를 클릭하여 계획 지침을 삭제할 데이터베이스를 확장한 다음 더하기 기호를 클릭하여 **프로그래밍 기능** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c14-118">Click the plus sign to expand the database in which you want to delete a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="a9c14-119">더하기 기호를 클릭하여 **계획 지침** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c14-119">Click the plus sign to expand the **Plan Guides** folder.</span></span>  
  
3.  <span data-ttu-id="a9c14-120">삭제할 계획 지침을 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c14-120">Right-click the plan guide you want to delete and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="a9c14-121">**개체 삭제** 대화 상자에서 올바른 계획 지침을 선택했는지 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c14-121">In the **Delete Object** dialog box, ensure that the correct plan guide is selected and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a9c14-122">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="a9c14-122">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-single-plan-guide"></a><span data-ttu-id="a9c14-123">단일 계획 지침을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="a9c14-123">To delete a single plan guide</span></span>  
  
1.  <span data-ttu-id="a9c14-124">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c14-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a9c14-125">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c14-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a9c14-126">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c14-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    --Create a procedure on which to define the plan guide.  
    IF OBJECT_ID(N'Sales.GetSalesOrderByCountry', N'P') IS NOT NULL  
        DROP PROCEDURE Sales.GetSalesOrderByCountry;  
    GO  
    CREATE PROCEDURE Sales.GetSalesOrderByCountry   
        (@Country nvarchar(60))  
    AS  
    BEGIN  
        SELECT *  
        FROM Sales.SalesOrderHeader AS h   
        INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
        INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
        WHERE t.CountryRegionCode = @Country;  
    END  
    GO  
    --Create the plan guide.  
    EXEC sp_create_plan_guide N'Guide3',  
        N'SELECT *  
        FROM Sales.SalesOrderHeader AS h   
        INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
        INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
        WHERE t.CountryRegionCode = @Country',  
        N'OBJECT',  
        N'Sales.GetSalesOrderByCountry',  
        NULL,  
        N'OPTION (OPTIMIZE FOR (@Country = N''US''))';  
    GO  
    --Drop the plan guide.  
    EXEC sp_control_plan_guide N'DROP', N'Guide3';  
    GO  
    ```  
  
#### <a name="to-delete-all-plan-guides-in-a-database"></a><span data-ttu-id="a9c14-127">데이터베이스의 모든 계획 지침을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="a9c14-127">To delete all plan guides in a database</span></span>  
  
1.  <span data-ttu-id="a9c14-128">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c14-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a9c14-129">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c14-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a9c14-130">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c14-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_control_plan_guide N'DROP ALL';  
    GO  
    ```  
  
 <span data-ttu-id="a9c14-131">자세한 내용은 [sp_control_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9c14-131">For more information, see [sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql).</span></span>  
  
  
