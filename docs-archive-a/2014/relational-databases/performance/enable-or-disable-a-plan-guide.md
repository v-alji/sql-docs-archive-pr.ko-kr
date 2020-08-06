---
title: 계획 지침 사용 또는 사용 안 함 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], disabling
- enabling plan guides
- plan guides [SQL Server], enabling
- disabling plan guides
ms.assetid: b00ab550-5308-4cb8-8330-483cd1d25654
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2611697e479d318245d8306b28c826e744ae85ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736274"
---
# <a name="enable-or-disable-a-plan-guide"></a><span data-ttu-id="1754d-102">계획 지침 사용 또는 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="1754d-102">Enable or Disable a Plan Guide</span></span>
  <span data-ttu-id="1754d-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 계획 지침을 사용하거나 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-103">You can disable and enable plan guides in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="1754d-104">데이터베이스에 있는 단일 계획 지침 또는 모든 계획 지침을 사용하거나 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-104">Either a single plan guides or all plan guides in a database can be enabled or disabled.</span></span>  
  
 <span data-ttu-id="1754d-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="1754d-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1754d-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="1754d-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1754d-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1754d-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1754d-108">보안</span><span class="sxs-lookup"><span data-stu-id="1754d-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1754d-109">**계획 지침을 사용하거나 사용하지 않도록 설정하려면:**</span><span class="sxs-lookup"><span data-stu-id="1754d-109">**To disable and enable plan guides, using:**</span></span>  
  
     [<span data-ttu-id="1754d-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1754d-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1754d-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1754d-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1754d-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="1754d-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1754d-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1754d-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="1754d-114">활성화 여부에 관계없이 계획 지침에서 참조하는 함수, 저장 프로시저 또는 DML 트리거를 삭제하거나 수정하려고 하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-114">Trying to drop or modify a function, stored procedure, or DML trigger that is referenced by a plan guide, either enabled or disabled, causes an error.</span></span> <span data-ttu-id="1754d-115">위에 나열된 개체를 삭제하거나 수정하기 전에 항상 종속성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-115">Always check for dependencies before dropping or modifying any of the objects listed above.</span></span>  
  
-   <span data-ttu-id="1754d-116">비활성화된 계획 지침을 비활성화하거나 활성화된 계획 지침을 활성화하면 아무런 영향을 미치지 않고 오류 없이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-116">Disabling a disabled plan guide or enabling an enabled plan guide has no effect and runs without error.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1754d-117">보안</span><span class="sxs-lookup"><span data-stu-id="1754d-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1754d-118">권한</span><span class="sxs-lookup"><span data-stu-id="1754d-118">Permissions</span></span>  
 <span data-ttu-id="1754d-119">OBJECT 계획 지침을 사용하거나 사용하지 않도록 설정하려면 계획 지침에서 참조되는 개체(예: 함수, 저장 프로시저)에 대한 변경 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-119">Disabling or enabling an OBJECT plan guide requires ALTER permission on the object (for example: function, stored procedure) that is referenced by the plan guide.</span></span> <span data-ttu-id="1754d-120">다른 모든 계획 지침에는 ALTER DATABASE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-120">All other plan guides require ALTER DATABASE permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1754d-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="1754d-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-or-enable-a-plan-guide"></a><span data-ttu-id="1754d-122">계획 지침을 사용하거나 사용하지 않도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="1754d-122">To disable or enable a plan guide</span></span>  
  
1.  <span data-ttu-id="1754d-123">더하기 기호를 클릭하여 계획 지침을 사용하거나 사용하지 않도록 설정할 데이터베이스를 확장한 다음 더하기 기호를 클릭하여 **프로그래밍 기능** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-123">Click the plus sign to expand the database in which you want to disable or enable a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="1754d-124">더하기 기호를 클릭하여 **계획 지침** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-124">Click the plus sign to expand the **Plan Guides** folder.</span></span>  
  
3.  <span data-ttu-id="1754d-125">사용하거나 사용하지 않도록 설정할 계획 지침을 마우스 오른쪽 단추로 클릭하고 **사용 안 함** 또는 **사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-125">Right-click the plan guide you want to disable or enable and select either **Disable** or **Enable**.</span></span>  
  
4.  <span data-ttu-id="1754d-126">**계획 지침 사용 안 함** 또는 **계획 지침 사용** 대화 상자에서 선택한 작업이 성공했는지 확인한 다음 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-126">In either the **Disable Plan Guide** or **Enable Plan Guide** dialog box, verify that the chosen action was successful and then click **Close**.</span></span>  
  
#### <a name="to-disable-or-enable-all-plan-guides-in-a-database"></a><span data-ttu-id="1754d-127">데이터베이스의 모든 계획 지침을 사용하거나 사용하지 않도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="1754d-127">To disable or enable all plan guides in a database</span></span>  
  
1.  <span data-ttu-id="1754d-128">더하기 기호를 클릭하여 계획 지침을 사용하거나 사용하지 않도록 설정할 데이터베이스를 확장한 다음 더하기 기호를 클릭하여 **프로그래밍 기능** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-128">Click the plus sign to expand the database in which you want to disable or enable a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="1754d-129">**계획 지침** 폴더를 마우스 오른쪽 단추로 클릭한 다음 **모두 사용** 또는 **모두 사용 안 함**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-129">Right-click the **Plan Guides** folder and then select either **Enable All** or **Disable All**.</span></span>  
  
3.  <span data-ttu-id="1754d-130">**모든 계획 지침 사용 안 함** 또는 **모든 계획 지침 사용** 대화 상자에서 선택한 작업이 성공했는지 확인한 다음 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-130">In either the **Disable all Plan Guides** or **Enable all Plan Guides** dialog box, verify that the chosen action was successful and then click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1754d-131">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="1754d-131">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-or-enable-a-plan-guide"></a><span data-ttu-id="1754d-132">계획 지침을 사용하거나 사용하지 않도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="1754d-132">To disable or enable a plan guide</span></span>  
  
1.  <span data-ttu-id="1754d-133">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-133">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1754d-134">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-134">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1754d-135">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-135">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
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
    --Disable the plan guide.  
    EXEC sp_control_plan_guide N'DISABLE', N'Guide3';  
    GO  
    --Enable the plan guide.  
    EXEC sp_control_plan_guide N'ENABLE', N'Guide3';  
    GO  
  
    ```  
  
#### <a name="to-disable-or-enable-all-plan-guides-in-a-database"></a><span data-ttu-id="1754d-136">데이터베이스의 모든 계획 지침을 사용하거나 사용하지 않도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="1754d-136">To disable or enable all plan guides in a database</span></span>  
  
1.  <span data-ttu-id="1754d-137">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1754d-138">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1754d-139">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1754d-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    --Disable all plan guides in the database.  
    EXEC sp_control_plan_guide N'DISABLE ALL';  
    GO  
    --Enable all plan guides in the database.  
    EXEC sp_control_plan_guide N'ENABLE ALL';  
    GO  
  
    ```  
  
 <span data-ttu-id="1754d-140">자세한 내용은 [sp_control_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1754d-140">For more information, see [sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql).</span></span>  
  
  
