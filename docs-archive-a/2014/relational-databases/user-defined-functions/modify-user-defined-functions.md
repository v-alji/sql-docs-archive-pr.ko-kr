---
title: 사용자 정의 함수 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 891c37b3-cb72-411f-9937-ee87e6d95f34
author: rothja
ms.author: jroth
ms.openlocfilehash: 1cf25fef91834e237f5cbaac26350220840830bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660365"
---
# <a name="modify-user-defined-functions"></a><span data-ttu-id="4d765-102">사용자 정의 함수 수정</span><span class="sxs-lookup"><span data-stu-id="4d765-102">Modify User-defined Functions</span></span>
  <span data-ttu-id="4d765-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 사용자 정의 함수를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d765-103">You can modify user-defined functions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="4d765-104">아래 설명과 같이 사용자 정의 함수를 수정하면 함수의 권한이 변경되거나 종속 함수, 저장 프로시저 또는 트리거에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4d765-104">Modifying user-defined functions as described below will not change the functions' permissions, nor will it affect any dependent functions, stored procedures, or triggers.</span></span>  
  
 <span data-ttu-id="4d765-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="4d765-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4d765-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="4d765-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4d765-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4d765-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4d765-108">보안</span><span class="sxs-lookup"><span data-stu-id="4d765-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4d765-109">**다음을 사용하여 사용자 정의 함수를 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="4d765-109">**To modify a user-defined function, using:**</span></span>  
  
     [<span data-ttu-id="4d765-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4d765-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4d765-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4d765-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4d765-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="4d765-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4d765-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4d765-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="4d765-114">ALTER FUNCTION을 사용하여 다음 동작을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4d765-114">ALTER FUNCTION cannot be used to perform any of the following actions:</span></span>  
  
-   <span data-ttu-id="4d765-115">스칼라 반환 함수를 테이블 반환 함수로 변경하거나 반대로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="4d765-115">Change a scalar-valued function to a table-valued function, or vice versa.</span></span>  
  
-   <span data-ttu-id="4d765-116">인라인 함수를 다중 문 함수로 변경하거나 반대로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="4d765-116">Change an inline function to a multistatement function, or vice versa.</span></span>  
  
-   <span data-ttu-id="4d765-117">Transact-SQL 함수를 CLR 함수로 변경하거나 반대로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="4d765-117">Change a Transact-SQL function to a CLR function, or vice-versa.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4d765-118">보안</span><span class="sxs-lookup"><span data-stu-id="4d765-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4d765-119">권한</span><span class="sxs-lookup"><span data-stu-id="4d765-119">Permissions</span></span>  
 <span data-ttu-id="4d765-120">함수 또는 스키마에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4d765-120">Requires ALTER permission on the function or on the schema.</span></span> <span data-ttu-id="4d765-121">함수에 사용자 정의 형식이 지정되면 해당 유형에 대한 EXECUTE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4d765-121">If the function specifies a user-defined type, requires EXECUTE permission on the type.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4d765-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="4d765-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-user-defined-function"></a><span data-ttu-id="4d765-123">사용자 정의 함수를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="4d765-123">To modify a user-defined function</span></span>  
  
1.  <span data-ttu-id="4d765-124">수정할 함수가 포함된 데이터베이스 옆의 더하기 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4d765-124">Click on the plus sign next to the database that contains the function you wish to modify.</span></span>  
  
2.  <span data-ttu-id="4d765-125">**프로그래밍 기능** 폴더 옆의 더하기 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4d765-125">Click on the plus sign next to the **Programmability** folder.</span></span>  
  
3.  <span data-ttu-id="4d765-126">수정할 함수가 포함된 폴더 옆의 더하기 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4d765-126">Click the plus sign next to the folder that contains the function you wish to modify:</span></span>  
  
    -   <span data-ttu-id="4d765-127">테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="4d765-127">Table-valued Function</span></span>  
  
    -   <span data-ttu-id="4d765-128">스칼라 반환 함수</span><span class="sxs-lookup"><span data-stu-id="4d765-128">Scalar-valued Function</span></span>  
  
    -   <span data-ttu-id="4d765-129">Aggregate 함수</span><span class="sxs-lookup"><span data-stu-id="4d765-129">Aggregate Function</span></span>  
  
4.  <span data-ttu-id="4d765-130">수정할 함수를 마우스 오른쪽 단추로 클릭하고 **수정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4d765-130">Right-click the function you want to modify and select **Modify**.</span></span>  
  
5.  <span data-ttu-id="4d765-131">쿼리 창에서 ALTER FUNCTION 문을 필요에 따라 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="4d765-131">In the Query Window, make the necessary changes to the ALTER FUNCTION statement.</span></span>  
  
6.  <span data-ttu-id="4d765-132">**파일** 메뉴에서 _function_name_**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4d765-132">On the **File** menu, click **Save**_function_name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4d765-133">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="4d765-133">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-user-defined-function"></a><span data-ttu-id="4d765-134">사용자 정의 함수를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="4d765-134">To modify a user-defined function</span></span>  
  
1.  <span data-ttu-id="4d765-135">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4d765-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4d765-136">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4d765-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4d765-137">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4d765-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Scalar-Valued Function  
    USE [AdventureWorks2012]  
    GO  
    ALTER FUNCTION [dbo].[ufnGetAccountingEndDate]()  
    RETURNS [datetime]   
    AS   
    BEGIN  
        RETURN DATEADD(millisecond, -2, CONVERT(datetime, '20040701', 112));  
    END;  
    ```  
  
    ```  
    -- Table-Valued Function   
    USE [AdventureWorks2012]  
    GO  
    ALTER FUNCTION [dbo].[ufnGetContactInformation](@PersonID int)  
    RETURNS @retContactInformation TABLE   
    (  
        -- Columns returned by the function  
        [PersonID] int NOT NULL,   
        [FirstName] [nvarchar](50) NULL,   
        [LastName] [nvarchar](50) NULL,   
        [JobTitle] [nvarchar](50) NULL,  
        [BusinessEntityType] [nvarchar](50) NULL  
    )  
    AS   
    -- Returns the first name, last name, job title and business entity type for the specified contact.  
    -- Since a contact can serve multiple roles, more than one row may be returned.  
    BEGIN  
    IF @PersonID IS NOT NULL   
    BEGIN  
         IF EXISTS(SELECT * FROM [HumanResources].[Employee] e   
         WHERE e.[BusinessEntityID] = @PersonID)   
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, e.[JobTitle], 'Employee'  
              FROM [HumanResources].[Employee] AS e  
              INNER JOIN [Person].[Person] p ON p.[BusinessEntityID] = e.[BusinessEntityID]  
              WHERE e.[BusinessEntityID] = @PersonID;  
  
         IF EXISTS(SELECT * FROM [Purchasing].[Vendor] AS v  
         INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = v.[BusinessEntityID]  
         WHERE bec.[PersonID] = @PersonID)  
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, ct.[Name], 'Vendor Contact'   
              FROM [Purchasing].[Vendor] AS v  
              INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = v.[BusinessEntityID]  
              INNER JOIN [Person].ContactType ct ON ct.[ContactTypeID] = bec.[ContactTypeID]  
              INNER JOIN [Person].[Person] p ON p.[BusinessEntityID] = bec.[PersonID]  
              WHERE bec.[PersonID] = @PersonID;  
  
         IF EXISTS(SELECT * FROM [Sales].[Store] AS s  
         INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = s.[BusinessEntityID]  
         WHERE bec.[PersonID] = @PersonID)  
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, ct.[Name], 'Store Contact'   
              FROM [Sales].[Store] AS s  
              INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = s.[BusinessEntityID]  
              INNER JOIN [Person].ContactType ct ON ct.[ContactTypeID] = bec.[ContactTypeID]  
              INNER JOIN [Person].[Person] p ON p.[BusinessEntityID] = bec.[PersonID]  
              WHERE bec.[PersonID] = @PersonID;  
  
         IF EXISTS(SELECT * FROM [Person].[Person] AS p  
         INNER JOIN [Sales].[Customer] AS c ON c.[PersonID] = p.[BusinessEntityID]  
         WHERE p.[BusinessEntityID] = @PersonID AND c.[StoreID] IS NULL)   
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, NULL, 'Consumer'   
              FROM [Person].[Person] AS p  
              INNER JOIN [Sales].[Customer] AS c ON c.[PersonID] = p.[BusinessEntityID]  
              WHERE p.[BusinessEntityID] = @PersonID AND c.[StoreID] IS NULL;   
         END  
    RETURN;  
    END;  
    ```  
  
 <span data-ttu-id="4d765-138">자세한 내용은 [ALTER FUNCTION&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-function-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d765-138">For more information, see [ALTER FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-function-transact-sql).</span></span>  
  
  
