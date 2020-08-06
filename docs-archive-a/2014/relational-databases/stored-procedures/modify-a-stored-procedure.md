---
title: 저장 프로시저 수정 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying stored procedures
- editing stored procedures
- stored procedures [SQL Server], modifying
ms.assetid: 13396239-6100-48ce-aa34-461358d99c92
author: stevestein
ms.author: sstein
ms.openlocfilehash: 906f0e06650da505094d18774ce86dab53d53f38
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728127"
---
# <a name="modify-a-stored-procedure"></a><span data-ttu-id="b4eb3-102">저장 프로시저 수정</span><span class="sxs-lookup"><span data-stu-id="b4eb3-102">Modify a Stored Procedure</span></span>
    
##  <a name="this-topic-describes-how-to-modify-a-stored-procedure-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a><span data-ttu-id="b4eb3-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]의 저장 프로시저를 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-103">This topic describes how to modify a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="b4eb3-104">**시작하기 전 주의 사항:**  [제한 사항](#Restrictions), [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="b4eb3-104">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="b4eb3-105">**프로시저를 변경하려면 다음을 사용합니다.**   [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="b4eb3-105">**To alter a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b4eb3-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b4eb3-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b4eb3-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="b4eb3-107">Limitations and Restrictions</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="b4eb3-108">저장 프로시저를 CLR 저장 프로시저로 수정할 수 없으며 그 반대의 경우도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-108">stored procedures cannot be modified to be CLR stored procedures and vice versa.</span></span>  
  
 <span data-ttu-id="b4eb3-109">이전 프로시저 정의가 WITH ENCRYPTION 또는 WITH RECOMPILE을 사용하여 만들어진 경우 이러한 옵션은 ALTER PROCEDURE 문에 포함된 경우에만 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-109">If the previous procedure definition was created using WITH ENCRYPTION or WITH RECOMPILE, these options are enabled only if they are included in the ALTER PROCEDURE statement.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b4eb3-110">보안</span><span class="sxs-lookup"><span data-stu-id="b4eb3-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b4eb3-111">권한</span><span class="sxs-lookup"><span data-stu-id="b4eb3-111">Permissions</span></span>  
 <span data-ttu-id="b4eb3-112">프로시저에 대한 ALTER PROCEDURE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-112">Requires ALTER PROCEDURE permission on the procedure.</span></span>  
  
##  <a name="how-to-modify-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="b4eb3-113">저장 프로시저 수정 방법</span><span class="sxs-lookup"><span data-stu-id="b4eb3-113">How to Modify a Stored Procedure</span></span>  
 <span data-ttu-id="b4eb3-114">다음 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-114">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="b4eb3-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b4eb3-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="b4eb3-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b4eb3-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b4eb3-117">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b4eb3-117">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="b4eb3-118">**Management Studio의 프로시저를 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="b4eb3-118">**To modify a procedure in Management Studio**</span></span>  
  
1.  <span data-ttu-id="b4eb3-119">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-119">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="b4eb3-120">**데이터베이스**를 확장하고 해당 프로시저가 속한 데이터베이스를 확장한 다음 **프로그래밍 기능**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-120">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="b4eb3-121">**저장 프로시저**를 확장하고 수정할 프로시저를 마우스 오른쪽 단추로 클릭한 다음 **수정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-121">Expand **Stored Procedures**, right-click the procedure to modify, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="b4eb3-122">저장 프로시저의 텍스트를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-122">Modify the text of the stored procedure.</span></span>  
  
5.  <span data-ttu-id="b4eb3-123">구문을 테스트하려면 **쿼리** 메뉴에서 **구문 분석**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-123">To test the syntax, on the **Query** menu, click **Parse**.</span></span>  
  
6.  <span data-ttu-id="b4eb3-124">프로시저 정의의 수정 내용을 저장하려면 **쿼리** 메뉴에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-124">To save the modifications to the procedure definition, on the **Query** menu, click **Execute**.</span></span>  
  
7.  <span data-ttu-id="b4eb3-125">[!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트로 업데이트된 프로시저 정의를 저장하려면 **파일** 메뉴에서 **다른 이름으로 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-125">To save the updated procedure definition as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script, on the **File** menu, click **Save As**.</span></span> <span data-ttu-id="b4eb3-126">해당 파일 이름을 적용하거나 새 이름으로 바꾼 다음 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-126">Accept the file name or replace it with a new name, and then click **Save**.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b4eb3-127">모든 사용자 입력에 대해 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-127">Validate all user input.</span></span> <span data-ttu-id="b4eb3-128">유효성 검사를 수행하기 전에는 사용자 입력을 연결하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-128">Do not concatenate user input before you validate it.</span></span> <span data-ttu-id="b4eb3-129">유효성 검사가 수행되지 않은 사용자 입력으로부터 생성된 명령은 실행하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-129">Never execute a command constructed from unvalidated user input.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b4eb3-130">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="b4eb3-130">Using Transact-SQL</span></span>  
 <span data-ttu-id="b4eb3-131">**쿼리 편집기에서 프로시저를 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="b4eb3-131">**To modify a procedure in Query Editor**</span></span>  
  
1.  <span data-ttu-id="b4eb3-132">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="b4eb3-133">**데이터베이스**를 확장하고 프로시저가 속한 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-133">Expand **Databases**, expand the database in which the procedure belongs.</span></span> <span data-ttu-id="b4eb3-134">또는 도구 모음의 사용 가능한 데이터베이스 목록에서 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-134">Or, from the tool bar, select the database from the list of available databases.</span></span> <span data-ttu-id="b4eb3-135">이 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-135">For this example, select the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
3.  <span data-ttu-id="b4eb3-136">**파일** 메뉴에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-136">On the **File** menu, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="b4eb3-137">다음 예를 복사하여 쿼리 편집기에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-137">Copy and paste the following example into the query editor.</span></span> <span data-ttu-id="b4eb3-138">이 예에서는 `uspVendorAllInfo` 데이터베이스의 모든 공급업체 이름, 해당 공급업체가 공급하는 제품, 신용 등급 및 사용 가능성을 반환하는 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-138">The example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
    ```  
  
    IF OBJECT_ID ( 'Purchasing.uspVendorAllInfo', 'P' ) IS NOT NULL   
        DROP PROCEDURE Purchasing.uspVendorAllInfo;  
    GO  
    CREATE PROCEDURE Purchasing.uspVendorAllInfo  
    WITH EXECUTE AS CALLER  
    AS  
        SET NOCOUNT ON;  
        SELECT v.Name AS Vendor, p.Name AS 'Product name',   
          v.CreditRating AS 'Rating',   
          v.ActiveFlag AS Availability  
        FROM Purchasing.Vendor v   
        INNER JOIN Purchasing.ProductVendor pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product p  
          ON pv.ProductID = p.ProductID   
        ORDER BY v.Name ASC;  
    GO  
  
    ```  
  
5.  <span data-ttu-id="b4eb3-139">**파일** 메뉴에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-139">On the **File** menu, click **New Query**.</span></span>  
  
6.  <span data-ttu-id="b4eb3-140">다음 예를 복사하여 쿼리 편집기에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-140">Copy and paste the following example into the query editor.</span></span> <span data-ttu-id="b4eb3-141">다음 예에서는 `uspVendorAllInfo` 프로시저를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-141">The example modifies the `uspVendorAllInfo` procedure.</span></span> <span data-ttu-id="b4eb3-142">EXECUTE AS CALLER 절이 제거되고 지정된 제품을 제공하는 공급업체만 반환하도록 프로시저 본문이 수정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-142">The EXECUTE AS CALLER clause is removed and the body of the procedure is modified to return only those vendors that supply the specified product.</span></span> <span data-ttu-id="b4eb3-143">`LEFT` 및 `CASE` 함수는 결과 집합의 모양을 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-143">The `LEFT` and `CASE` functions customize the appearance of the result set.</span></span>  
  
    ```  
    ALTER PROCEDURE Purchasing.uspVendorAllInfo  
        @Product varchar(25)   
    AS  
        SET NOCOUNT ON;  
        SELECT LEFT(v.Name, 25) AS Vendor, LEFT(p.Name, 25) AS 'Product name',   
        'Rating' = CASE v.CreditRating   
            WHEN 1 THEN 'Superior'  
            WHEN 2 THEN 'Excellent'  
            WHEN 3 THEN 'Above average'  
            WHEN 4 THEN 'Average'  
            WHEN 5 THEN 'Below average'  
            ELSE 'No rating'  
            END  
        , Availability = CASE v.ActiveFlag  
            WHEN 1 THEN 'Yes'  
            ELSE 'No'  
            END  
        FROM Purchasing.Vendor AS v   
        INNER JOIN Purchasing.ProductVendor AS pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product AS p   
          ON pv.ProductID = p.ProductID   
        WHERE p.Name LIKE @Product  
        ORDER BY v.Name ASC;  
    GO  
  
    ```  
  
7.  <span data-ttu-id="b4eb3-144">프로시저 정의의 수정 내용을 저장하려면 **쿼리** 메뉴에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-144">To save the modifications to the procedure definition, on the **Query** menu, click **Execute**.</span></span>  
  
8.  <span data-ttu-id="b4eb3-145">[!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트로 업데이트된 프로시저 정의를 저장하려면 **파일** 메뉴에서 **다른 이름으로 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-145">To save the updated procedure definition as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script, on the **File** menu, click **Save As**.</span></span> <span data-ttu-id="b4eb3-146">해당 파일 이름을 적용하거나 새 이름으로 바꾼 다음 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-146">Accept the file name or replace it with a new name, and then click **Save**.</span></span>  
  
9. <span data-ttu-id="b4eb3-147">변경된 저장 프로시저를 실행하려면 다음 예시를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b4eb3-147">To run the modified stored procedure, execute the following example.</span></span>  
  
    ```  
    EXEC Purchasing.uspVendorAllInfo N'LL Crankarm';  
    GO  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b4eb3-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4eb3-148">See Also</span></span>  
 [<span data-ttu-id="b4eb3-149">ALTER PROCEDURE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b4eb3-149">ALTER PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-procedure-transact-sql)  
  
  
