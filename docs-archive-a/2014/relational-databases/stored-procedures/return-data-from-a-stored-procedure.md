---
title: 저장 프로시저에서 데이터 반환 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], returning data
- returning data from stored procedure
ms.assetid: 7a428ffe-cd87-4f42-b3f1-d26aa8312bf7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 472ca5cf27f7e7ea2b18daa961c19faadcf2251f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661619"
---
# <a name="return-data-from-a-stored-procedure"></a><span data-ttu-id="4b6d4-102">저장 프로시저에서 데이터 반환</span><span class="sxs-lookup"><span data-stu-id="4b6d4-102">Return Data from a Stored Procedure</span></span>
  <span data-ttu-id="4b6d4-103">결과 집합 또는 데이터를 프로시저에서 호출 프로그램으로 반환하는 두 가지 방법인 출력 매개 변수 및 반환 코드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-103">There are two ways of returning result sets or data from a procedure to a calling program: output parameters and return codes.</span></span> <span data-ttu-id="4b6d4-104">이 항목은 두 방법에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-104">This topic provides information on both approaches.</span></span>  
  
## <a name="returning-data-using-an-output-parameter"></a><span data-ttu-id="4b6d4-105">출력 매개 변수를 사용하여 데이터 반환</span><span class="sxs-lookup"><span data-stu-id="4b6d4-105">Returning Data Using an Output Parameter</span></span>  
 <span data-ttu-id="4b6d4-106">프로시저 정의에서 매개 변수에 OUTPUT 키워드를 지정하면 해당 프로시저는 종료될 때 매개 변수의 현재 값을 호출 프로그램에 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-106">If you specify the OUTPUT keyword for a parameter in the procedure definition, the procedure can return the current value of the parameter to the calling program when the procedure exits.</span></span> <span data-ttu-id="4b6d4-107">호출 프로그램에서 사용할 수 있는 변수에 매개 변수 값을 저장하려면 호출 프로그램이 프로시저를 실행할 때 OUTPUT 키워드를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-107">To save the value of the parameter in a variable that can be used in the calling program, the calling program must use the OUTPUT keyword when executing the procedure.</span></span> <span data-ttu-id="4b6d4-108">출력 매개 변수로 사용될 수 있는 데이터 형식에 대한 자세한 내용은 [CREATE PROCEDURE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-108">For more information about what data types can be used as output parameters, see [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).</span></span>  
  
### <a name="examples-of-output-parameter"></a><span data-ttu-id="4b6d4-109">출력 매개 변수의 예</span><span class="sxs-lookup"><span data-stu-id="4b6d4-109">Examples of Output Parameter</span></span>  
 <span data-ttu-id="4b6d4-110">다음 예에서는 입력 및 출력 매개 변수가 있는 프로시저를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-110">The following example shows a procedure with an input and an output parameter.</span></span> <span data-ttu-id="4b6d4-111">`@SalesPerson` 매개 변수는 호출 프로그램이 지정한 입력 값을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-111">The `@SalesPerson` parameter would receive an input value specified by the calling program.</span></span> <span data-ttu-id="4b6d4-112">SELECT 문은 입력 매개 변수에 전달된 값을 사용하여 정확한 `SalesYTD` 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-112">The SELECT statement uses the value passed into the input parameter to obtain the correct `SalesYTD` value.</span></span> <span data-ttu-id="4b6d4-113">또한 SELECT 문은 `@SalesYTD` 출력 매개 변수에 값을 할당하여 해당 프로시저가 종료될 때 호출 프로그램으로 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-113">The SELECT statement also assigns the value to the `@SalesYTD` output parameter, which returns the value to the calling program when the procedure exits.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('Sales.uspGetEmployeeSalesYTD', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.uspGetEmployeeSalesYTD;  
GO  
CREATE PROCEDURE Sales.uspGetEmployeeSalesYTD  
@SalesPerson nvarchar(50),  
@SalesYTD money OUTPUT  
AS    
  
    SET NOCOUNT ON;  
    SELECT @SalesYTD = SalesYTD  
    FROM Sales.SalesPerson AS sp  
    JOIN HumanResources.vEmployee AS e ON e.BusinessEntityID = sp.BusinessEntityID  
    WHERE LastName = @SalesPerson;  
RETURN  
GO  
  
```  
  
 <span data-ttu-id="4b6d4-114">다음 예에서는 첫 번째 예에 생성된 프로시저를 호출하고 호출 프로그램의 지역 변수인 `@SalesYTD` 변수의 호출된 프로시저로부터 반환된 출력 값을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-114">The following example calls the procedure created in the first example and saves the output value returned from the called procedure in the `@SalesYTD` variable, which is local to the calling program.</span></span>  
  
```  
-- Declare the variable to receive the output value of the procedure.  
DECLARE @SalesYTDBySalesPerson money;  
-- Execute the procedure specifying a last name for the input parameter  
-- and saving the output value in the variable @SalesYTDBySalesPerson  
EXECUTE Sales.uspGetEmployeeSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDBySalesPerson OUTPUT;  
-- Display the value returned by the procedure.  
PRINT 'Year-to-date sales for this employee is ' +   
    convert(varchar(10),@SalesYTDBySalesPerson);  
GO  
  
```  
  
 <span data-ttu-id="4b6d4-115">프로시저를 실행할 때 OUTPUT 매개 변수에 입력 값을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-115">Input values can also be specified for OUTPUT parameters when the procedure is executed.</span></span> <span data-ttu-id="4b6d4-116">이렇게 하면 프로시저가 호출 프로그램으로부터 값을 받아 변경하거나 연산을 수행한 다음 호출 프로그램에 새 값을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-116">This allows the procedure to receive a value from the calling program, change or perform operations with the value, and then return the new value to the calling program.</span></span> <span data-ttu-id="4b6d4-117">이전 예에서는 프로그램이 `@SalesYTDBySalesPerson` 프로시저를 호출하기 전에 `Sales.uspGetEmployeeSalesYTD` 변수에 값을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-117">In the previous example, the `@SalesYTDBySalesPerson` variable can be assigned a value before the program calls the `Sales.uspGetEmployeeSalesYTD` procedure.</span></span> <span data-ttu-id="4b6d4-118">execute 문은 `@SalesYTDBySalesPerson` 변수 값을 `@SalesYTD` OUTPUT 매개 변수로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-118">The execute statement would pass the `@SalesYTDBySalesPerson` variable value into the `@SalesYTD` OUTPUT parameter.</span></span> <span data-ttu-id="4b6d4-119">그러면 프로시저 본문에서 해당 값을 새로운 값을 생성하는 계산에 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-119">Then in the procedure body, the value could be used for calculations that generate a new value.</span></span> <span data-ttu-id="4b6d4-120">새로운 값은 OUTPUT 매개 변수를 통해 프로시저 밖으로 다시 전달되어 프로시저가 종료될 때 `@SalesYTDBySalesPerson` 변수의 값으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-120">The new value would be passed back out of the procedure through the OUTPUT parameter, updating the value in the `@SalesYTDBySalesPerson` variable when the procedure exits.</span></span> <span data-ttu-id="4b6d4-121">이것을 "참조 전달(pass-by-reference) 기능"이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-121">This is often referred to as "pass-by-reference capability."</span></span>  
  
 <span data-ttu-id="4b6d4-122">프로시저를 호출할 때 매개 변수에 OUTPUT을 지정하고 그 매개 변수가 프로시저 정의에서 OUTPUT을 사용하여 정의되지 않은 경우 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-122">If you specify OUTPUT for a parameter when you call a procedure and that parameter is not defined by using OUTPUT in the procedure definition, you get an error message.</span></span> <span data-ttu-id="4b6d4-123">그러나 출력 매개 변수가 있는 프로시저를 실행할 수는 있지만 프로시저를 실행할 때는 OUTPUT을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-123">However, you can execute a procedure with output parameters and not specify OUTPUT when executing the procedure.</span></span> <span data-ttu-id="4b6d4-124">오류가 반환되지는 않지만 호출 프로그램에서 출력 값을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-124">No error is returned, but you cannot use the output value in the calling program.</span></span>  
  
### <a name="using-the-cursor-data-type-in-output-parameters"></a><span data-ttu-id="4b6d4-125">OUTPUT 매개 변수에 Cursor 데이터 형식 사용</span><span class="sxs-lookup"><span data-stu-id="4b6d4-125">Using the Cursor Data Type in OUTPUT Parameters</span></span>  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)]<span data-ttu-id="4b6d4-126">프로시저는 `cursor` 출력 매개 변수에만 데이터 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-126">procedures can use the `cursor` data type only for OUTPUT parameters.</span></span> <span data-ttu-id="4b6d4-127">`cursor`매개 변수에 대해 데이터 형식이 지정 된 경우 프로시저 정의에서 해당 매개 변수에 대해 다양 한 키워드와 출력 키워드를 모두 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-127">If the `cursor` data type is specified for a parameter, both the VARYING and OUTPUT keywords must be specified for that parameter in the procedure definition.</span></span> <span data-ttu-id="4b6d4-128">매개 변수는 OUTPUT 으로만 지정 될 수 있지만 매개 변수 선언에 가변 키워드가 지정 된 경우에는 데이터 형식이 여야 `cursor` 하 고 OUTPUT 키워드도 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-128">A parameter can be specified as only OUTPUT but if the VARYING keyword is specified in the parameter declaration, the data type must be `cursor` and the OUTPUT keyword must also be specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b6d4-129">`cursor` 데이터 형식은 OLE DB, ODBC, ADO, DB-Library 등의 데이터베이스 API를 통해 애플리케이션 변수에 바인딩할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-129">The `cursor` data type cannot be bound to application variables through the database APIs such as OLE DB, ODBC, ADO, and DB-Library.</span></span> <span data-ttu-id="4b6d4-130">OUTPUT 매개 변수는 애플리케이션이 프로시저를 실행하기 전에 바인딩되어야 하므로 `cursor` OUTPUT 매개 변수가 있는 프로시저는 데이터베이스 API에서 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-130">Because OUTPUT parameters must be bound before an application can execute a procedure, procedures with `cursor` OUTPUT parameters cannot be called from the database APIs.</span></span> <span data-ttu-id="4b6d4-131">이러한 프로시저는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 로컬 `cursor` 변수에 `cursor` OUTPUT 변수가 할당된 경우에만 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 일괄 처리, 프로시저 또는 트리거에서 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-131">These procedures can be called from [!INCLUDE[tsql](../../../includes/tsql-md.md)] batches, procedures, or triggers only when the `cursor` OUTPUT variable is assigned to a [!INCLUDE[tsql](../../../includes/tsql-md.md)] local `cursor` variable.</span></span>  
  
### <a name="rules-for-cursor-output-parameters"></a><span data-ttu-id="4b6d4-132">Cursor Output 매개 변수 규칙</span><span class="sxs-lookup"><span data-stu-id="4b6d4-132">Rules for Cursor Output Parameters</span></span>  
 <span data-ttu-id="4b6d4-133">프로시저 실행 시 `cursor` Output 매개 변수에는 다음 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-133">The following rules pertain to `cursor` output parameters when the procedure is executed:</span></span>  
  
-   <span data-ttu-id="4b6d4-134">정방향 전용 커서의 경우, 프로시저의 실행이 끝났을 때 커서의 결과 집합에는 커서 위치와 같거나 이보다 뒤에 있는 행만 반환됩니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-134">For a forward-only cursor, the rows returned in the cursor's result set are only those rows at and beyond the position of the cursor at the conclusion of the procedure execution, for example:</span></span>  
  
    -   <span data-ttu-id="4b6d4-135">비스크롤형 커서는 프로시저에서 100개의 행이 있는 RS라는 결과 집합에 열려 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-135">A nonscrollable cursor is opened in a procedure on a result set named RS of 100 rows.</span></span>  
  
    -   <span data-ttu-id="4b6d4-136">프로시저는 RS 결과 집합의 처음 5개 행을 인출합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-136">The procedure fetches the first 5 rows of result set RS.</span></span>  
  
    -   <span data-ttu-id="4b6d4-137">프로시저가 호출자에게 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-137">The procedure returns to its caller.</span></span>  
  
    -   <span data-ttu-id="4b6d4-138">호출자에게 반환된 RS 결과 집합은 6에서 100 사이인 RS의 행으로 구성되며 호출자의 커서는 RS의 첫 번째 행 앞에 놓입니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-138">The result set RS returned to the caller consists of rows from 6 through 100 of RS, and the cursor in the caller is positioned before the first row of RS.</span></span>  
  
-   <span data-ttu-id="4b6d4-139">정방향 전용 커서의 경우, 프로시저의 실행이 끝났을 때 커서가 첫 번째 행보다 앞에 있으면 호출한 일괄 처리, 프로시저, 트리거에 전체 결과 집합이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-139">For a forward-only cursor, if the cursor is positioned before the first row when the procedure exits, the entire result set is returned to the calling batch, procedure, or trigger.</span></span> <span data-ttu-id="4b6d4-140">반환될 때 커서 위치는 첫 번째 행 앞으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-140">When returned, the cursor position is set before the first row.</span></span>  
  
-   <span data-ttu-id="4b6d4-141">정방향 전용 커서의 경우, 프로시저의 실행이 끝났을 때 커서가 마지막 행보다 뒤에 있으면 호출한 일괄 처리, 프로시저, 트리거에 빈 결과 집합이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-141">For a forward-only cursor, if the cursor is positioned beyond the end of the last row when the procedure exits, an empty result set is returned to the calling batch, procedure, or trigger.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b6d4-142">빈 결과 집합은 Null 값과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-142">An empty result set is not the same as a null value.</span></span>  
  
-   <span data-ttu-id="4b6d4-143">스크롤형 커서의 경우, 프로시저의 실행이 끝났을 때 결과 집합의 모든 행이 호출한 일괄 처리, 프로시저, 트리거에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-143">For a scrollable cursor, all the rows in the result set are returned to the calling batch, procedure, or trigger when the procedure exits.</span></span> <span data-ttu-id="4b6d4-144">반환될 때 커서 위치는 프로시저에서 마지막으로 실행된 인출 위치가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-144">When returned, the cursor position is left at the position of the last fetch executed in the procedure.</span></span>  
  
-   <span data-ttu-id="4b6d4-145">커서의 종류에 관계없이 커서를 닫으면 호출한 일괄 처리, 프로시저, 트리거에 Null 값이 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-145">For any type of cursor, if the cursor is closed, then a null value is passed back to the calling batch, procedure, or trigger.</span></span> <span data-ttu-id="4b6d4-146">매개 변수에 커서를 할당했지만 해당 커서를 전혀 열지 않은 경우도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-146">This will also be the case if a cursor is assigned to a parameter, but that cursor is never opened.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b6d4-147">커서의 닫힌 상태는 반환 시에만 문제가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-147">The closed state matters only at return time.</span></span> <span data-ttu-id="4b6d4-148">예를 들어 프로시저를 통해 커서를 일부 닫은 후 프로시저에서 나중에 다시 열어 호출한 일괄 처리, 프로시저, 트리거에 커서의 결과 집합을 반환하는 것은 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-148">For example, it is valid to close a cursor part of the way through the procedure, to open it again later in the procedure, and return that cursor's result set to the calling batch, procedure, or trigger.</span></span>  
  
### <a name="examples-of-cursor-output-parameters"></a><span data-ttu-id="4b6d4-149">Cursor Output 매개 변수의 예</span><span class="sxs-lookup"><span data-stu-id="4b6d4-149">Examples of Cursor Output Parameters</span></span>  
 <span data-ttu-id="4b6d4-150">다음 예에서는 `@currency` `cursor` 데이터 형식을 사용 하 여 출력 매개 변수 _를 지정 하는 프로시저를 만듭니다 `cursor` .</span><span class="sxs-lookup"><span data-stu-id="4b6d4-150">In the following example, a procedure is created that specified an output parameter, `@currency`_`cursor` using the `cursor` data type.</span></span> <span data-ttu-id="4b6d4-151">그런 다음 일괄 처리로 프로시저가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-151">The procedure is then called in a batch.</span></span>  
  
 <span data-ttu-id="4b6d4-152">먼저 선언된 프로시저를 만들고 Currency 테이블에서 커서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-152">First, create the procedure that declares and then opens a cursor on the Currency table.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'dbo.uspCurrencyCursor', 'P' ) IS NOT NULL  
    DROP PROCEDURE dbo.uspCurrencyCursor;  
GO  
CREATE PROCEDURE dbo.uspCurrencyCursor   
    @CurrencyCursor CURSOR VARYING OUTPUT  
AS  
    SET NOCOUNT ON;  
    SET @CurrencyCursor = CURSOR  
    FORWARD_ONLY STATIC FOR  
      SELECT CurrencyCode, Name  
      FROM Sales.Currency;  
    OPEN @CurrencyCursor;  
GO  
  
```  
  
 <span data-ttu-id="4b6d4-153">다음으로 지역 커서 변수를 선언하는 일괄 처리를 실행하고, 지역 변수에 커서를 할당하는 프로시저를 실행한 다음, 커서에서 행을 인출합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-153">Next, execute a batch that declares a local cursor variable, executes the procedure to assign the cursor to the local variable, and then fetches the rows from the cursor.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyCursor CURSOR;  
EXEC dbo.uspCurrencyCursor @CurrencyCursor = @MyCursor OUTPUT;  
WHILE (@@FETCH_STATUS = 0)  
BEGIN;  
     FETCH NEXT FROM @MyCursor;  
END;  
CLOSE @MyCursor;  
DEALLOCATE @MyCursor;  
GO  
  
```  
  
## <a name="returning-data-using-a-return-code"></a><span data-ttu-id="4b6d4-154">반환 코드를 사용하여 데이터 반환</span><span class="sxs-lookup"><span data-stu-id="4b6d4-154">Returning Data Using a Return Code</span></span>  
 <span data-ttu-id="4b6d4-155">프로시저는 반환 코드라고 하는 정수 값을 반환하여 프로시저의 실행 상태를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-155">A procedure can return an integer value called a return code to indicate the execution status of a procedure.</span></span> <span data-ttu-id="4b6d4-156">RETURN 문을 사용하여 프로시저의 반환 코드를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-156">You specify the return code for a procedure using the RETURN statement.</span></span> <span data-ttu-id="4b6d4-157">OUTPUT 매개 변수에서와 같이 프로시저가 실행될 때 호출 프로그램에서 사용할 수 있도록 반환 코드 값을 변수에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-157">As with OUTPUT parameters, you must save the return code in a variable when the procedure is executed in order to use the return code value in the calling program.</span></span> <span data-ttu-id="4b6d4-158">예를 들어 데이터 형식의 할당 변수는 `@result` `int` 다음과 같은 프로시저의 반환 코드를 저장 하는 데 사용 됩니다 `my_proc` .</span><span class="sxs-lookup"><span data-stu-id="4b6d4-158">For example, the assignment variable `@result` of data type `int` is used to store the return code from the procedure `my_proc`, such as:</span></span>  
  
```  
DECLARE @result int;  
EXECUTE @result = my_proc;  
```  
  
 <span data-ttu-id="4b6d4-159">반환 코드는 대개 프로시저의 흐름 제어 블록에서 발생 가능한 각 오류 상태의 반환 코드 값을 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-159">Return codes are commonly used in control-of-flow blocks within procedures to set the return code value for each possible error situation.</span></span> <span data-ttu-id="4b6d4-160">[!INCLUDE[tsql](../../../includes/tsql-md.md)] 문 다음에 @@ERROR 함수를 사용하면 문이 실행될 때 오류가 발생했는지 여부를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-160">You can use the @@ERROR function after a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement to detect whether an error occurred during the execution of the statement.</span></span>  
  
### <a name="examples-of-return-codes"></a><span data-ttu-id="4b6d4-161">반환 코드의 예</span><span class="sxs-lookup"><span data-stu-id="4b6d4-161">Examples of Return Codes</span></span>  
 <span data-ttu-id="4b6d4-162">다음 예에서는 여러 오류에 대한 특정 반환 코드 값을 설정하는 오류 처리가 포함된 `usp_GetSalesYTD` 프로시저를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-162">The following example shows the `usp_GetSalesYTD` procedure with error handling that sets special return code values for various errors.</span></span> <span data-ttu-id="4b6d4-163">다음 표에서는 발생 가능한 각 오류에 프로시저에서 할당한 정수 값 및 각 값에 해당하는 의미를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-163">The following table shows the integer value that is assigned by the procedure to each possible error, and the corresponding meaning for each value.</span></span>  
  
|<span data-ttu-id="4b6d4-164">반환 코드 값</span><span class="sxs-lookup"><span data-stu-id="4b6d4-164">Return code value</span></span>|<span data-ttu-id="4b6d4-165">의미</span><span class="sxs-lookup"><span data-stu-id="4b6d4-165">Meaning</span></span>|  
|-----------------------|-------------|  
|<span data-ttu-id="4b6d4-166">0</span><span class="sxs-lookup"><span data-stu-id="4b6d4-166">0</span></span>|<span data-ttu-id="4b6d4-167">성공한 실행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-167">Successful execution.</span></span>|  
|<span data-ttu-id="4b6d4-168">1</span><span class="sxs-lookup"><span data-stu-id="4b6d4-168">1</span></span>|<span data-ttu-id="4b6d4-169">필요한 매개 변수 값이 지정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-169">Required parameter value is not specified.</span></span>|  
|<span data-ttu-id="4b6d4-170">2</span><span class="sxs-lookup"><span data-stu-id="4b6d4-170">2</span></span>|<span data-ttu-id="4b6d4-171">지정된 매개 변수 값이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-171">Specified parameter value is not valid.</span></span>|  
|<span data-ttu-id="4b6d4-172">3</span><span class="sxs-lookup"><span data-stu-id="4b6d4-172">3</span></span>|<span data-ttu-id="4b6d4-173">판매량을 가져오는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-173">Error has occurred getting sales value.</span></span>|  
|<span data-ttu-id="4b6d4-174">4</span><span class="sxs-lookup"><span data-stu-id="4b6d4-174">4</span></span>|<span data-ttu-id="4b6d4-175">판매 직원의 NULL 판매량을 찾았습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-175">NULL sales value found for the salesperson.</span></span>|  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('Sales.usp_GetSalesYTD', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.usp_GetSalesYTD;  
GO  
CREATE PROCEDURE Sales.usp_GetSalesYTD  
@SalesPerson nvarchar(50) = NULL,  -- NULL default value  
@SalesYTD money = NULL OUTPUT  
AS    
  
-- Validate the @SalesPerson parameter.  
IF @SalesPerson IS NULL  
   BEGIN  
       PRINT 'ERROR: You must specify a last name for the sales person.'  
       RETURN(1)  
   END  
ELSE  
   BEGIN  
   -- Make sure the value is valid.  
   IF (SELECT COUNT(*) FROM HumanResources.vEmployee  
          WHERE LastName = @SalesPerson) = 0  
      RETURN(2)  
   END  
-- Get the sales for the specified name and   
-- assign it to the output parameter.  
SELECT @SalesYTD = SalesYTD   
FROM Sales.SalesPerson AS sp  
JOIN HumanResources.vEmployee AS e ON e.BusinessEntityID = sp.BusinessEntityID  
WHERE LastName = @SalesPerson;  
-- Check for SQL Server errors.  
IF @@ERROR <> 0   
   BEGIN  
      RETURN(3)  
   END  
ELSE  
   BEGIN  
   -- Check to see if the ytd_sales value is NULL.  
     IF @SalesYTD IS NULL  
       RETURN(4)   
     ELSE  
      -- SUCCESS!!  
        RETURN(0)  
   END  
-- Run the stored procedure without specifying an input value.  
EXEC Sales.usp_GetSalesYTD;  
GO  
-- Run the stored procedure with an input value.  
DECLARE @SalesYTDForSalesPerson money, @ret_code int;  
-- Execute the procedure specifying a last name for the input parameter  
-- and saving the output value in the variable @SalesYTD  
EXECUTE Sales.usp_GetSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDForSalesPerson OUTPUT;  
PRINT N'Year-to-date sales for this employee is ' +  
    CONVERT(varchar(10), @SalesYTDForSalesPerson);  
  
```  
  
 <span data-ttu-id="4b6d4-176">다음 예에서는 `usp_GetSalesYTD` 프로시저에서 반환되는 반환 코드를 처리하기 위한 프로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-176">The following example creates a program to handle the return codes that are returned from the `usp_GetSalesYTD` procedure.</span></span>  
  
```  
-- Declare the variables to receive the output value and return code   
-- of the procedure.  
DECLARE @SalesYTDForSalesPerson money, @ret_code int;  
  
-- Execute the procedure with a title_id value  
-- and save the output value and return code in variables.  
EXECUTE @ret_code = Sales.usp_GetSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDForSalesPerson OUTPUT;  
--  Check the return codes.  
IF @ret_code = 0  
BEGIN  
   PRINT 'Procedure executed successfully'  
   -- Display the value returned by the procedure.  
   PRINT 'Year-to-date sales for this employee is ' + CONVERT(varchar(10),@SalesYTDForSalesPerson)  
END  
ELSE IF @ret_code = 1  
   PRINT 'ERROR: You must specify a last name for the sales person.'  
ELSE IF @ret_code = 2   
   PRINT 'EERROR: You must enter a valid last name for the sales person.'  
ELSE IF @ret_code = 3  
   PRINT 'ERROR: An error occurred getting sales value.'  
ELSE IF @ret_code = 4  
   PRINT 'ERROR: No sales recorded for this employee.'     
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b6d4-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b6d4-177">See Also</span></span>  
 <span data-ttu-id="4b6d4-178">[DECLARE @local_variable&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4b6d4-178">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span></span>  
 <span data-ttu-id="4b6d4-179">[PRINT&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/print-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4b6d4-179">[PRINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/print-transact-sql) </span></span>  
 <span data-ttu-id="4b6d4-180">[SET @local_variable&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-local-variable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4b6d4-180">[SET @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-local-variable-transact-sql) </span></span>  
 <span data-ttu-id="4b6d4-181">[커서](../cursors.md) </span><span class="sxs-lookup"><span data-stu-id="4b6d4-181">[Cursors](../cursors.md) </span></span>  
 <span data-ttu-id="4b6d4-182">[RETURN&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/return-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4b6d4-182">[RETURN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/return-transact-sql) </span></span>  
 [<span data-ttu-id="4b6d4-183">@@ERROR&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4b6d4-183">@@ERROR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/error-transact-sql)  
  
  
