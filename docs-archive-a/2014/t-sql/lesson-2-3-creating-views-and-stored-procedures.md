---
title: 뷰 및 저장 프로시저 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- creating views and stored procedures
ms.assetid: 53a0426d-07d8-4b7c-aa21-22632753bad8
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 76f6ecec446536191e8be4b05547ba5fd44c9d8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727731"
---
# <a name="creating-views-and-stored-procedures"></a><span data-ttu-id="79150-102">뷰 및 저장 프로시저 만들기</span><span class="sxs-lookup"><span data-stu-id="79150-102">Creating Views and Stored Procedures</span></span>
  <span data-ttu-id="79150-103">이제 Mary는 **TestData** 데이터베이스에 액세스할 수 있으므로 뷰 및 저장 프로시저와 같은 일부 데이터베이스 개체를 만든 다음 이러한 개체에 대한 액세스 권한을 Mary에게 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79150-103">Now that Mary can access the **TestData** database, you may want to create some database objects, such as a view and a stored procedure, and then grant Mary access to them.</span></span> <span data-ttu-id="79150-104">뷰는 저장된 SELECT 문이며 저장 프로시저는 일괄 처리로 실행되는 하나 이상의 [!INCLUDE[tsql](../includes/tsql-md.md)] 문입니다.</span><span class="sxs-lookup"><span data-stu-id="79150-104">A view is a stored SELECT statement, and a stored procedure is one or more [!INCLUDE[tsql](../includes/tsql-md.md)] statements that execute as a batch.</span></span>  
  
 <span data-ttu-id="79150-105">뷰는 테이블처럼 쿼리되며 매개 변수를 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79150-105">Views are queried like tables and do not accept parameters.</span></span> <span data-ttu-id="79150-106">저장 프로시저는 뷰보다 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="79150-106">Stored procedures are more complex than views.</span></span> <span data-ttu-id="79150-107">저장 프로시저는 입력 및 출력 매개 변수를 가질 수 있으며 코드 흐름을 제어하기 위해 IF 및 WHILE 문과 같은 문을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79150-107">Stored procedures can have both input and output parameters and can contain statements to control the flow of the code, such as IF and WHILE statements.</span></span> <span data-ttu-id="79150-108">데이터베이스의 모든 반복되는 동작에 저장 프로시저를 사용하는 것이 바람직한 프로그래밍 방식입니다.</span><span class="sxs-lookup"><span data-stu-id="79150-108">It is good programming practice to use stored procedures for all repetitive actions in the database.</span></span>  
  
 <span data-ttu-id="79150-109">예를 들어 CREATE VIEW를 사용하여 **Products** 테이블에 있는 두 개의 열만 선택하는 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="79150-109">For this example, you will use CREATE VIEW to create a view that selects only two of the columns in the **Products** table.</span></span> <span data-ttu-id="79150-110">그런 다음 CREATE PROCEDURE를 사용하여 가격 매개 변수를 허용하고 지정된 매개 변수 값보다 가격이 낮은 제품만 반환하는 저장 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="79150-110">Then, you will use CREATE PROCEDURE to create a stored procedure that accepts a price parameter and returns only those products that cost less than the specified parameter value.</span></span>  
  
### <a name="to-create-a-view"></a><span data-ttu-id="79150-111">뷰를 만들려면</span><span class="sxs-lookup"><span data-stu-id="79150-111">To create a view</span></span>  
  
1.  <span data-ttu-id="79150-112">다음 문을 실행하여 select 문을 실행하고 제품의 이름과 가격을 사용자에게 반환하는 매우 간단한 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="79150-112">Execute the following statement to create a very simple view that executes a select statement, and returns the names and prices of our products to the user.</span></span>  
  
    ```  
    CREATE VIEW vw_Names  
       AS  
       SELECT ProductName, Price FROM Products;  
    GO  
  
    ```  
  
### <a name="test-the-view"></a><span data-ttu-id="79150-113">뷰 테스트</span><span class="sxs-lookup"><span data-stu-id="79150-113">Test the view</span></span>  
  
1.  <span data-ttu-id="79150-114">뷰는 테이블처럼 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="79150-114">Views are treated just like tables.</span></span> <span data-ttu-id="79150-115">`SELECT` 문을 사용하여 뷰에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79150-115">Use a `SELECT` statement to access a view.</span></span>  
  
    ```  
    SELECT * FROM vw_Names;  
    GO  
  
    ```  
  
### <a name="to-create-a-stored-procedure"></a><span data-ttu-id="79150-116">저장 프로시저를 만들려면</span><span class="sxs-lookup"><span data-stu-id="79150-116">To create a stored procedure</span></span>  
  
1.  <span data-ttu-id="79150-117">다음 문은 저장 프로시저 이름인 `pr_Names`를 만들고 `@VarPrice` 데이터 형식의 `money`라는 입력 매개 변수를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="79150-117">The following statement creates a stored procedure name `pr_Names`, accepts an input parameter named `@VarPrice` of data type `money`.</span></span> <span data-ttu-id="79150-118">이 저장 프로시저는 `Products less than` 데이터 형식에서 `money` 문자 데이터 형식으로 변경되는 입력 매개 변수와 연결된 `varchar(10)` 문을 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="79150-118">The stored procedure prints the statement `Products less than` concatenated with the input parameter that is changed from the `money` data type into a `varchar(10)` character data type.</span></span> <span data-ttu-id="79150-119">그런 다음 이 저장 프로시저는 입력 매개 변수를 `SELECT` 절의 일부로 전달하며 뷰에서 `WHERE` 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="79150-119">Then, the procedure executes a `SELECT` statement on the view, passing the input parameter as part of the `WHERE` clause.</span></span> <span data-ttu-id="79150-120">이렇게 하면 입력 매개 변수 값보다 가격이 낮은 모든 제품이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="79150-120">This returns all products that cost less than the input parameter value.</span></span>  
  
    ```  
    CREATE PROCEDURE pr_Names @VarPrice money  
       AS  
       BEGIN  
          -- The print statement returns text to the user  
          PRINT 'Products less than ' + CAST(@VarPrice AS varchar(10));  
          -- A second statement starts here  
          SELECT ProductName, Price FROM vw_Names  
                WHERE Price < @varPrice;  
       END  
    GO  
  
    ```  
  
### <a name="test-the-stored-procedure"></a><span data-ttu-id="79150-121">저장 프로시저 테스트</span><span class="sxs-lookup"><span data-stu-id="79150-121">Test the stored procedure</span></span>  
  
1.  <span data-ttu-id="79150-122">저장 프로시저를 테스트하려면 다음 문을 입력하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="79150-122">To test the stored procedure, type and execute the following statement.</span></span> <span data-ttu-id="79150-123">이 프로시저는 1단원에서 가격이 `Products` 보다 낮은 `10.00`테이블에 입력한 제품 두 개의 이름을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79150-123">The procedure should return the names of the two products entered into the `Products` table in Lesson 1 with a price that is less than `10.00`.</span></span>  
  
    ```  
    EXECUTE pr_Names 10.00;  
    GO  
  
    ```  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="79150-124">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="79150-124">Next Task in Lesson</span></span>  
 [<span data-ttu-id="79150-125">데이터베이스 개체에 대한 액세스 권한 부여</span><span class="sxs-lookup"><span data-stu-id="79150-125">Granting Access to a Database Object</span></span>](lesson-2-4-granting-access-to-a-database-object.md)  
  
## <a name="see-also"></a><span data-ttu-id="79150-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="79150-126">See Also</span></span>  
 <span data-ttu-id="79150-127">[CREATE VIEW&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="79150-127">[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) </span></span>  
 [<span data-ttu-id="79150-128">CREATE PROCEDURE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="79150-128">CREATE PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)  
  
  
