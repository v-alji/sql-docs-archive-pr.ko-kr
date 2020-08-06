---
title: 사용자 정의 함수 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: db1d668a-23b7-4757-a9c5-1bd848ba7f6d
author: rothja
ms.author: jroth
ms.openlocfilehash: e5f6b2b306c4fe8db08b088d9607cfb19ab0f25e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660368"
---
# <a name="delete-user-defined-functions"></a><span data-ttu-id="a86be-102">사용자 정의 함수 삭제</span><span class="sxs-lookup"><span data-stu-id="a86be-102">Delete User-defined Functions</span></span>
  <span data-ttu-id="a86be-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 다음을 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 사용자 정의 함수를 삭제할 수 있습니다. [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a86be-103">You can delete (drop) user-defined functions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
 <span data-ttu-id="a86be-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="a86be-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a86be-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="a86be-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a86be-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="a86be-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a86be-107">보안</span><span class="sxs-lookup"><span data-stu-id="a86be-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a86be-108">**다음을 사용하여 사용자 정의 함수를 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="a86be-108">**To delete a user-defined function, using:**</span></span>  
  
     [<span data-ttu-id="a86be-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a86be-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a86be-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a86be-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a86be-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="a86be-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a86be-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="a86be-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="a86be-113">데이터베이스에 이 함수를 참조하고 SCHEMABINDING을 사용하여 만든 Transact-SQL 함수나 뷰가 있는 경우 또는 해당 함수를 참조하는 계산 열, CHECK 제약 조건 또는 DEFAULT 제약 조건이 있는 경우 함수를 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a86be-113">You will not be able to delete the function if there are Transact-SQL functions or views in the database that reference this function and were created by using SCHEMABINDING, or if there are computed columns, CHECK constraints, or DEFAULT constraints that reference the function.</span></span>  
  
-   <span data-ttu-id="a86be-114">이 함수를 참조하고 인덱싱된 계산 열이 있는 경우 함수를 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a86be-114">You will not be able to delete the function if there are computed columns that reference this function and have been indexed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a86be-115">보안</span><span class="sxs-lookup"><span data-stu-id="a86be-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a86be-116">권한</span><span class="sxs-lookup"><span data-stu-id="a86be-116">Permissions</span></span>  
 <span data-ttu-id="a86be-117">함수가 속한 스키마에 대한 ALTER 권한 또는 함수에 대한 CONTROL 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a86be-117">Requires ALTER permission on the schema to which the function belongs, or CONTROL permission on the function.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a86be-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="a86be-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-user-defined-function"></a><span data-ttu-id="a86be-119">사용자 정의 함수를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="a86be-119">To delete a user-defined function</span></span>  
  
1.  <span data-ttu-id="a86be-120">수정할 함수가 포함된 데이터베이스 옆의 더하기 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86be-120">Click on the plus sign next to the database that contains the function you wish to modify.</span></span>  
  
2.  <span data-ttu-id="a86be-121">**프로그래밍 기능** 폴더 옆의 더하기 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86be-121">Click on the plus sign next to the **Programmability** folder.</span></span>  
  
3.  <span data-ttu-id="a86be-122">수정할 함수가 포함된 폴더 옆의 더하기 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86be-122">Click the plus sign next to the folder that contains the function you wish to modify:</span></span>  
  
    -   <span data-ttu-id="a86be-123">테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="a86be-123">Table-valued Function</span></span>  
  
    -   <span data-ttu-id="a86be-124">스칼라 반환 함수</span><span class="sxs-lookup"><span data-stu-id="a86be-124">Scalar-valued Function</span></span>  
  
    -   <span data-ttu-id="a86be-125">Aggregate 함수</span><span class="sxs-lookup"><span data-stu-id="a86be-125">Aggregate Function</span></span>  
  
4.  <span data-ttu-id="a86be-126">삭제할 함수를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a86be-126">Right-click the function you want to delete and select **Delete**.</span></span>  
  
5.  <span data-ttu-id="a86be-127">**개체 삭제** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86be-127">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a86be-128">**개체 삭제** 대화 상자에서 **종속성 표시** 를 클릭 하 여 _function_name_**종속성** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a86be-128">Click **Show Dependencies** in the **Delete Object** dialog box to open the _function_name_**Dependencies** dialog box.</span></span> <span data-ttu-id="a86be-129">이 대화 상자에는 해당 함수에 종속된 모든 개체와 해당 함수가 종속된 모든 개체가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86be-129">This will show all of the objects that depend on the function and all of the objects on which the function depends.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a86be-130">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="a86be-130">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-user-defined-function"></a><span data-ttu-id="a86be-131">사용자 정의 함수를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="a86be-131">To delete a user-defined function</span></span>  
  
1.  <span data-ttu-id="a86be-132">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a86be-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a86be-133">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86be-133">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a86be-134">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86be-134">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- creates function called "Sales.ufn_SalesByStore"  
    USE AdventureWorks2012;  
    GO  
    CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
    RETURNS TABLE  
    AS  
    RETURN   
    (  
        SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
        FROM Production.Product AS P   
        JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
        JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
        JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
        WHERE C.StoreID = @storeid  
        GROUP BY P.ProductID, P.Name  
    );  
    GO  
    ```  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- determines if function exists in database  
    IF OBJECT_ID (N'Sales.fn_SalesByStore', N'IF') IS NOT NULL  
    -- deletes function  
        DROP FUNCTION Sales.fn_SalesByStore;  
    GO  
    ```  
  
 <span data-ttu-id="a86be-135">자세한 내용은 [DROP FUNCTION&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a86be-135">For more information, see [DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql).</span></span>  
  
  
