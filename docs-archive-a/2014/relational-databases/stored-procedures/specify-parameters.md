---
title: 매개 변수 지정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- parameters [SQL Server], stored procedures
- stored procedures [SQL Server], parameters
- output parameters [SQL Server]
- input parameters [SQL Server]
ms.assetid: 902314fe-5f9c-4d0d-a0b7-27e67c9c70ec
author: stevestein
ms.author: sstein
ms.openlocfilehash: d93a04281839c4db26cbab16ac166af3cdb7c9a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661618"
---
# <a name="specify-parameters"></a><span data-ttu-id="85402-102">매개 변수 지정</span><span class="sxs-lookup"><span data-stu-id="85402-102">Specify Parameters</span></span>
  <span data-ttu-id="85402-103">프로시저 매개 변수를 지정하여 호출 프로그램이 값을 프로시저 본문에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85402-103">By specifying procedure parameters, calling programs are able to pass values into the body of the procedure.</span></span> <span data-ttu-id="85402-104">이러한 값은 프로시저 실행 시 다양한 목적으로 쓰일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85402-104">Those values can be used for a variety of purposes during procedure execution.</span></span> <span data-ttu-id="85402-105">프로시저 매개 변수는 매개 변수가 OUTPUT 매개 변수로 표시된 경우 호출 프로그램에 값을 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85402-105">Procedure parameters can also return values to the calling program if the parameter is marked as an OUTPUT parameter.</span></span>  
  
 <span data-ttu-id="85402-106">프로시저는 최대 2100개의 매개 변수를 사용할 수 있으며 각각 이름, 데이터 형식, 방향이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="85402-106">A procedure can have a maximum of 2100 parameters; each assigned a name, data type, and direction.</span></span> <span data-ttu-id="85402-107">필요에 따라 매개 변수가 기본값으로 할당될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85402-107">Optionally, parameters can be assigned default values.</span></span>  
  
 <span data-ttu-id="85402-108">다음 섹션에서는 값을 매개 변수에 전달하는 것과 프로시저 호출 시 각 매개 변수 특성이 어떻게 사용되는지 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="85402-108">The following section provides information about passing values into parameters and about how each of the parameter attributes is used during a procedure call.</span></span>  
  
## <a name="passing-values-into-parameters"></a><span data-ttu-id="85402-109">값을 매개 변수로 전달</span><span class="sxs-lookup"><span data-stu-id="85402-109">Passing Values into Parameters</span></span>  
 <span data-ttu-id="85402-110">프로시저 호출과 함께 입력된 매개 변수 값은 상수 또는 변수여야 합니다. 함수 이름은 매개 변수 값으로 사용될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="85402-110">The parameter values supplied with a procedure call must be constants or a variable; a function name cannot be used as a parameter value.</span></span> <span data-ttu-id="85402-111">변수는 \@\@spid와 같은 시스템 변수이거나 사용자 정의 변수일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85402-111">Variables can be user-defined or system variables such as \@\@spid.</span></span>  
  
 <span data-ttu-id="85402-112">다음 예에서는 프로시저 `uspGetWhereUsedProductID`에 매개 변수 값을 전달하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="85402-112">The following examples demonstrate passing parameter values to the procedure `uspGetWhereUsedProductID`.</span></span> <span data-ttu-id="85402-113">다음 예에서는 상수와 변수로 매개 변수를 전달하는 방법과 변수를 사용하여 함수 값을 전달하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="85402-113">They illustrate how to pass parameters as constants and variables and also how to use a variable to pass the value of a function.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
-- Passing values as constants.  
EXEC dbo.uspGetWhereUsedProductID 819, '20050225';  
GO  
-- Passing values as variables.  
DECLARE @ProductID int, @CheckDate datetime;  
SET @ProductID = 819;  
SET @CheckDate = '20050225';  
EXEC dbo.uspGetWhereUsedProductID @ProductID, @CheckDate;  
GO  
-- Try to use a function as a parameter value.  
-- This produces an error message.  
EXEC dbo.uspGetWhereUsedProductID 819, GETDATE();  
GO  
-- Passing the function value as a variable.  
DECLARE @CheckDate datetime;  
SET @CheckDate = GETDATE();  
EXEC dbo.uspGetWhereUsedProductID 819, @CheckDate;  
GO  
```  
  
## <a name="specifying-parameter-names"></a><span data-ttu-id="85402-114">매개 변수 이름 지정</span><span class="sxs-lookup"><span data-stu-id="85402-114">Specifying Parameter Names</span></span>  
 <span data-ttu-id="85402-115">프로시저를 생성하고 매개 변수를 선언할 때 매개 변수 이름은 하나의 \@ 문자로 시작해야 하며 프로시저 범위 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85402-115">When creating a procedure and declaring a parameter name, the parameter name must begin with a single \@ character and must be unique in the scope of the procedure.</span></span>  
  
 <span data-ttu-id="85402-116">매개 변수 이름을 명시적으로 지정하고 프로시저 호출 시 적절한 값을 각 매개 변수에 할당하면 매개 변수를 임의의 순서로 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85402-116">Explicitly naming the parameters and assigning the appropriate values to each parameter in a procedure call allows the parameters to be supplied in any order.</span></span> <span data-ttu-id="85402-117">예를 들어, 프로시저 **my_proc**에서 **\@first**, **\@second** 및 **\@third**라는 세 개의 매개 변수를 사용하는 경우 `EXECUTE my_proc @second = 2, @first = 1, @third = 3;`과 같이 프로시저에 전달된 값을 매개 변수 이름에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85402-117">For example, if the procedure **my_proc** expects three parameters named **\@first**, **\@second**, and **\@third**, the values passed to the procedure can be assigned to the parameter names, such as: `EXECUTE my_proc @second = 2, @first = 1, @third = 3;`</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85402-118">**\@parameter =** _value_ 형식에 하나의 매개 변수 값이 입력되는 경우 모든 후속 매개 변수도 이러한 방식으로 입력되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85402-118">If one parameter value is supplied in the form **\@parameter =**_value_, all subsequent parameters must be supplied in this manner.</span></span> <span data-ttu-id="85402-119">**\@parameter =** _value_ 형식에 매개 변수 값이 전달되지 않은 경우 해당 값은 CREATE PROCEDURE 문에 나열된 매개 변수를 따라 동일한 순서(왼쪽에서 오른쪽)로 제공되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85402-119">If the parameter values are not passed in the form **\@parameter =**_value_, the values must be supplied in the identical order (left to right) as the parameters are listed in the CREATE PROCEDURE statement.</span></span>  
> 
> [!WARNING]
>  <span data-ttu-id="85402-120">철자가 잘못 입력된 매개 변수와 함께 **\@parameter =** _value_ 형식으로 매개 변수가 전달될 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 오류가 발생하여 프로시저 실행을 방해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85402-120">Any parameter passed in the form **\@parameter =**_value_ with the parameter misspelled, will cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to generate an error and prevent procedure execution.</span></span>  
  
## <a name="specifying-parameter-data-types"></a><span data-ttu-id="85402-121">매개 변수 데이터 형식 지정</span><span class="sxs-lookup"><span data-stu-id="85402-121">Specifying Parameter Data Types</span></span>  
 <span data-ttu-id="85402-122">CREATE PROCEDURE 문에서 매개 변수가 선언될 때에는 데이터 형식이 함께 정의되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85402-122">Parameters must be defined with a data type when they are declared in a CREATE PROCEDURE statement.</span></span> <span data-ttu-id="85402-123">프로시저가 호출될 때 매개 변수의 데이터 형식에 따라 매개 변수에 허용되는 값의 형식과 범위가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="85402-123">The data type of a parameter determines the type and range of values that are accepted for the parameter when the procedure is called.</span></span> <span data-ttu-id="85402-124">예를 들어 `tinyint` 데이터 형식으로 매개 변수를 정의하면 해당 매개 변수로는 0에서 255까지의 숫자 값만 전달될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85402-124">For example, if you define a parameter with a `tinyint` data type, only numeric values ranging from 0 to 255 are accepted when passed into that parameter.</span></span> <span data-ttu-id="85402-125">데이터 형식과 맞지 않는 값으로 프로시저를 실행하면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="85402-125">An error is returned if a procedure is executed with a value incompatible with the data type.</span></span>  
  
## <a name="specifying-parameter-default-values"></a><span data-ttu-id="85402-126">매개 변수 기본값 지정</span><span class="sxs-lookup"><span data-stu-id="85402-126">Specifying Parameter Default Values</span></span>  
 <span data-ttu-id="85402-127">매개 변수가 선언될 때 매개 변수에 지정된 기본값이 있는 경우 매개 변수는 선택적으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="85402-127">A parameter is considered optional if the parameter has a default value specified when it is declared.</span></span> <span data-ttu-id="85402-128">프로시저 호출 시 선택적 매개 변수로 값을 제공해야 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="85402-128">It is not necessary to provide a value for an optional parameter in a procedure call.</span></span>  
  
 <span data-ttu-id="85402-129">매개 변수의 기본값은 다음 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85402-129">The default value of a parameter is used when:</span></span>  
  
-   <span data-ttu-id="85402-130">프로시저 호출 시 매개 변수에 값이 지정되어 있지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="85402-130">No value for the parameter is specified in the procedure call.</span></span>  
  
-   <span data-ttu-id="85402-131">프로시저 호출에서 DEFAULT 키워드가 값으로 지정된 경우</span><span class="sxs-lookup"><span data-stu-id="85402-131">The DEFAULT keyword is specified as the value in the procedure call.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85402-132">기본값이 공백 또는 문장 부호가 포함된 문자열이거나 6xxx와 같이 숫자로 시작하면 기본값을 곧은 작은 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85402-132">If the default value is a character string that contains embedded blanks or punctuation, or if it starts with a number (for example, 6xxx), it must be enclosed in single, straight quotation marks.</span></span>  
  
 <span data-ttu-id="85402-133">매개 변수에 적당한 기본값을 지정할 수 없을 때는 NULL을 기본값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="85402-133">If no value can be specified appropriately as a default for the parameter, specify NULL as the default.</span></span> <span data-ttu-id="85402-134">프로시저가 매개 변수 값이 없이 실행되는 경우 프로시저에서 사용자 지정 메시지를 반환하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="85402-134">It is a good idea to have the procedure return a customized message if the procedure is executed without a value for the parameter.</span></span>  
  
 <span data-ttu-id="85402-135">다음 예는 한 개의 입력 매개 변수 `usp_GetSalesYTD` 을 사용하여 `@SalesPerson`프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="85402-135">The following example creates the `usp_GetSalesYTD` procedure with one input parameter, `@SalesPerson`.</span></span> <span data-ttu-id="85402-136">`@SalesPerson` 매개 변수 값 없이 프로시저를 실행할 경우 NULL이 이 매개 변수의 기본값으로 할당되고 사용자 지정 오류 메시지를 반환하는 오류 처리 문에서 NULL이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="85402-136">NULL is assigned as the default value for the parameter and is used in error handling statements to return a custom error message for cases when the procedure is executed without a value for the `@SalesPerson` parameter.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('Sales.uspGetSalesYTD', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.uspGetSalesYTD;  
GO  
CREATE PROCEDURE Sales.uspGetSalesYTD  
@SalesPerson nvarchar(50) = NULL  -- NULL default value  
AS   
    SET NOCOUNT ON;   
  
-- Validate the @SalesPerson parameter.  
IF @SalesPerson IS NULL  
BEGIN  
   PRINT 'ERROR: You must specify the last name of the sales person.'  
   RETURN  
END  
-- Get the sales for the specified sales person and   
-- assign it to the output parameter.  
SELECT SalesYTD  
FROM Sales.SalesPerson AS sp  
JOIN HumanResources.vEmployee AS e ON e.BusinessEntityID = sp.BusinessEntityID  
WHERE LastName = @SalesPerson;  
RETURN  
GO  
  
```  
  
 <span data-ttu-id="85402-137">다음 예는 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="85402-137">The following example executes the procedure.</span></span> <span data-ttu-id="85402-138">첫 번째 문은 입력 값을 지정하지 않고 프로시저를 실행하므로</span><span class="sxs-lookup"><span data-stu-id="85402-138">The first statement executes the procedure without specifying an input value.</span></span> <span data-ttu-id="85402-139">프로시저의 오류 처리 문이 사용자 지정 오류 메시지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="85402-139">This causes the error handling statements in the procedure to return the custom error message.</span></span> <span data-ttu-id="85402-140">두 번째 문은 입력 값을 제공하고 예상 결과 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="85402-140">The second statement supplies an input value and returns the expected result set.</span></span>  
  
```  
-- Run the procedure without specifying an input value.  
EXEC Sales.usp_GetSalesYTD;  
GO  
-- Run the procedure with an input value.  
EXEC Sales.usp_GetSalesYTD N'Blythe';  
GO  
```  
  
 <span data-ttu-id="85402-141">기본값이 있는 매개 변수는 생략될 수 있지만 실제로는 매개 변수의 목록이 잘리는 것뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="85402-141">Although parameters for which defaults have been supplied can be omitted, the list of parameters can only be truncated.</span></span> <span data-ttu-id="85402-142">예를 들어 한 프로시저가 다섯 개의 매개 변수를 갖는 경우 4번째, 5번째 매개 변수는 생략될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85402-142">For example, if a procedure has five parameters, both the fourth and the fifth parameters can be omitted.</span></span> <span data-ttu-id="85402-143">하지만 매개 변수가 **\@parameter =** _value_ 형식으로 입력되지 않는 한 5번째 매개 변수가 있는 경우 4번째 매개 변수는 생략할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="85402-143">However the fourth parameter cannot be skipped as long as the fifth parameter is included, unless the parameters are supplied in the form **\@parameter =**_value_.</span></span>  
  
## <a name="specifying-parameter-direction"></a><span data-ttu-id="85402-144">매개 변수 방향 지정</span><span class="sxs-lookup"><span data-stu-id="85402-144">Specifying Parameter Direction</span></span>  
 <span data-ttu-id="85402-145">매개 변수의 방향은 프로시저 본문으로 전달되는 값을 의미하는 입력 또는 프로시저가 호출 프로그램에 값을 반환함을 의미하는 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="85402-145">The direction of a parameter is either input, a value is passed into the body of the procedure, or output, the procedure returns a value to the calling program.</span></span> <span data-ttu-id="85402-146">기본값은 입력 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="85402-146">The default is an input parameter.</span></span>  
  
 <span data-ttu-id="85402-147">출력 매개 변수를 지정하려면 CREATE PROCEDURE 문의 매개 변수 정의에서 OUTPUT 키워드를 반드시 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85402-147">To specify an output parameter, the OUTPUT keyword must be specified in the definition of the parameter in the CREATE PROCEDURE statement.</span></span> <span data-ttu-id="85402-148">프로시저는 출력 매개 변수의 현재 값을 프로시저가 끝날 때 호출 프로그램에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="85402-148">The procedure returns the current value of the output parameter to the calling program when the procedure exits.</span></span> <span data-ttu-id="85402-149">호출 프로그램에서 프로시저를 실행할 때 OUTPUT 키워드도 사용해야 호출 프로그램에서 사용할 수 있는 변수에 매개 변수 값을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85402-149">The calling program must also use the OUTPUT keyword when executing the procedure to save the parameter's value in a variable that can be used in the calling program.</span></span>  
  
 <span data-ttu-id="85402-150">다음 예에서는 지정된 가격을 초과하지 않는 제품 목록을 반환하는 `Production.usp`_`GetList` 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="85402-150">The following example creates the `Production.usp`_`GetList` procedure, which returns a list of products that have prices that do not exceed a specified amount.</span></span> <span data-ttu-id="85402-151">다음 예에서는 여러 SELECT 문과 여러 OUTPUT 매개 변수의 사용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="85402-151">The example shows using multiple SELECT statements and multiple OUTPUT parameters.</span></span> <span data-ttu-id="85402-152">OUTPUT 매개 변수를 사용하면 프로시저를 실행하는 동안 외부 프로시저, 일괄 처리 또는 한 개 이상의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 값 집합에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85402-152">OUTPUT parameters allow an external procedure, a batch, or more than one [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to access a value set during the procedure execution.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'Production.uspGetList', 'P' ) IS NOT NULL   
    DROP PROCEDURE Production.uspGetList;  
GO  
CREATE PROCEDURE Production.uspGetList @Product varchar(40)   
    , @MaxPrice money   
    , @ComparePrice money OUTPUT  
    , @ListPrice money OUT  
AS  
    SET NOCOUNT ON;  
    SELECT p.[Name] AS Product, p.ListPrice AS 'List Price'  
    FROM Production.Product AS p  
    JOIN Production.ProductSubcategory AS s   
      ON p.ProductSubcategoryID = s.ProductSubcategoryID  
    WHERE s.[Name] LIKE @Product AND p.ListPrice < @MaxPrice;  
-- Populate the output variable @ListPprice.  
SET @ListPrice = (SELECT MAX(p.ListPrice)  
        FROM Production.Product AS p  
        JOIN  Production.ProductSubcategory AS s   
          ON p.ProductSubcategoryID = s.ProductSubcategoryID  
        WHERE s.[Name] LIKE @Product AND p.ListPrice < @MaxPrice);  
-- Populate the output variable @compareprice.  
SET @ComparePrice = @MaxPrice;  
GO  
  
```  
  
 <span data-ttu-id="85402-153">`usp_GetList` 를 실행하여 가격이 $700 미만인 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] 제품(자전거) 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="85402-153">Execute `usp_GetList` to return a list of [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] products (Bikes) that cost less than $700.</span></span> <span data-ttu-id="85402-154">OUTPUT 매개 변수인 **\@cost**와 **\@compareprices**는 **메시지** 창의 메시지를 반환하기 위해 흐름 제어 언어와 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="85402-154">The OUTPUT parameters **\@cost** and **\@compareprices** are used with control-of-flow language to return a message in the **Messages** window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85402-155">OUTPUT 변수는 프로시저를 만들 때와 변수를 사용할 때 정의되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85402-155">The OUTPUT variable must be defined during the procedure creation and also during the use of the variable.</span></span> <span data-ttu-id="85402-156">매개 변수 이름과 변수 이름은 일치하지 않아도 되지만</span><span class="sxs-lookup"><span data-stu-id="85402-156">The parameter name and variable name do not have to match.</span></span> <span data-ttu-id="85402-157">**\@listprice=** _variable_을 사용하지 않는 경우 데이터 형식과 매개 변수 위치는 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85402-157">However, the data type and parameter positioning must match (unless **\@listprice=** _variable_ is used).</span></span>  
  
```  
DECLARE @ComparePrice money, @Cost money ;  
EXECUTE Production.uspGetList '%Bikes%', 700,   
    @ComparePrice OUT,   
    @Cost OUTPUT  
IF @Cost <= @ComparePrice   
BEGIN  
    PRINT 'These products can be purchased for less than   
    $'+RTRIM(CAST(@ComparePrice AS varchar(20)))+'.'  
END  
ELSE  
    PRINT 'The prices for all products in this category exceed   
    $'+ RTRIM(CAST(@ComparePrice AS varchar(20)))+'.';  
  
```  
  
 <span data-ttu-id="85402-158">다음은 결과 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="85402-158">Here is the partial result set:</span></span>  
  
```  
Product                                            List Price  
-------------------------------------------------- ------------------  
Road-750 Black, 58                                 539.99  
Mountain-500 Silver, 40                            564.99  
Mountain-500 Silver, 42                            564.99  
...  
Road-750 Black, 48                                 539.99  
Road-750 Black, 52                                 539.99  
  
(14 row(s) affected)  
  
These items can be purchased for less than $700.00.  
```  
  
## <a name="see-also"></a><span data-ttu-id="85402-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="85402-159">See Also</span></span>  
 [<span data-ttu-id="85402-160">CREATE PROCEDURE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="85402-160">CREATE PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)  
  
  
