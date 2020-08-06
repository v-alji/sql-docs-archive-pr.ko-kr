---
title: 테이블에서 계산 열 지정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- computed columns, define
ms.assetid: 731a4576-09c1-47f0-a8f6-edd0b55679f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 22e4df8d67b61e50383ffd8e33f982990ff3f2ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653752"
---
# <a name="specify-computed-columns-in-a-table"></a><span data-ttu-id="1620b-102">테이블에서 계산 열 지정</span><span class="sxs-lookup"><span data-stu-id="1620b-102">Specify Computed Columns in a Table</span></span>
  <span data-ttu-id="1620b-103">계산 열은 해당 열에 PERSISTED 표시가 없는 한 테이블에 물리적으로 저장되지 않는 가상의 열입니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-103">A computed column is a virtual column that is not physically stored in the table, unless the column is marked PERSISTED.</span></span> <span data-ttu-id="1620b-104">계산 열 식에서는 이 식이 속한 열의 값을 계산하기 위해 다른 열의 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-104">A computed column expression can use data from other columns to calculate a value for the column to which it belongs.</span></span> <span data-ttu-id="1620b-105">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 계산 열의 식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-105">You can specify an expression for a computed column in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1620b-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="1620b-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1620b-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="1620b-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1620b-108">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1620b-108">Limitations and Restrictions</span></span>](#Limitations)  
  
     [<span data-ttu-id="1620b-109">보안</span><span class="sxs-lookup"><span data-stu-id="1620b-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1620b-110">**계산 열을 지정하려면**</span><span class="sxs-lookup"><span data-stu-id="1620b-110">**To specify a computed column, using:**</span></span>  
  
     [<span data-ttu-id="1620b-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1620b-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1620b-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1620b-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1620b-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="1620b-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Limitations"></a> <span data-ttu-id="1620b-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1620b-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="1620b-115">계산 열은 DEFAULT 또는 FOREIGN KEY 제약 조건 정의로 사용하거나 NOT NULL 제약 조건 정의와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-115">A computed column cannot be used as a DEFAULT or FOREIGN KEY constraint definition or with a NOT NULL constraint definition.</span></span> <span data-ttu-id="1620b-116">그러나 계산 열 값이 명확한 식에 의해 정의되고 결과의 데이터 형식이 인덱스 열에 허용되는 경우에는 계산 열을 인덱스의 키 열이나 PRIMARY KEY 또는 UNIQUE 제약 조건의 일부로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-116">However, if the computed column value is defined by a deterministic expression and the data type of the result is allowed in index columns, a computed column can be used as a key column in an index or as part of any PRIMARY KEY or UNIQUE constraint.</span></span> <span data-ttu-id="1620b-117">예를 들어 테이블에 a와 b라는 정수 열이 있을 때 계산 열 a + b에는 인덱스를 작성할 수 있지만 계산 열 a+DATEPART(dd, GETDATE())는 다음 호출 시 값이 바뀌므로 인덱스를 작성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-117">For example, if the table has integer columns a and b, the computed column a + b may be indexed, but computed column a + DATEPART(dd, GETDATE()) cannot be indexed, because the value might change in subsequent invocations.</span></span>  
  
-   <span data-ttu-id="1620b-118">계산 열은 INSERT 또는 UPDATE 문의 대상이 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-118">A computed column cannot be the target of an INSERT or UPDATE statement.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1620b-119">보안</span><span class="sxs-lookup"><span data-stu-id="1620b-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1620b-120">권한</span><span class="sxs-lookup"><span data-stu-id="1620b-120">Permissions</span></span>  
 <span data-ttu-id="1620b-121">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-121">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1620b-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="1620b-122">Using SQL Server Management Studio</span></span>  
  
###  <a name="to-add-a-new-computed-column"></a><a name="NewColumn"></a> <span data-ttu-id="1620b-123">새 계산 열을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="1620b-123">To add a new computed column</span></span>  
  
1.  <span data-ttu-id="1620b-124">**개체 탐색기**에서 새 계산 열을 추가할 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-124">In **Object Explorer**, expand the table for which you want to add the new computed column.</span></span> <span data-ttu-id="1620b-125">**열** 을 마우스 오른쪽 단추로 클릭하고 **새 열**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-125">Right-click **Columns** and select **New Column**.</span></span>  
  
2.  <span data-ttu-id="1620b-126">열 이름을 입력하고 기본 데이터 형식 `nchar`(10)을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-126">Enter the column name and accept the default data type (`nchar`(10)).</span></span> <span data-ttu-id="1620b-127">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서는 수식에 지정된 식에 데이터 형식 우선 순위 규칙을 적용하여 계산 열의 데이터 형식을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-127">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] determines the data type of the computed column by applying the rules of data type precedence to the expressions specified in the formula.</span></span> <span data-ttu-id="1620b-128">예를 들어 수식에서 `money` 형식 열과 `int` 형식 열을 참조하는 경우 데이터 형식의 우선 순위가 더 높으므로 계산 열은 `money` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-128">For example, if the formula references a column of type `money` and a column of type `int`, the computed column will be of type `money` because that data type has the higher precedence.</span></span> <span data-ttu-id="1620b-129">자세한 내용은 [데이터 형식 우선 순위&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-type-precedence-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1620b-129">For more information, see [Data Type Precedence &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-type-precedence-transact-sql).</span></span>  
  
3.  <span data-ttu-id="1620b-130">**열 속성** 탭에서 **계산 열 사양** 속성을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-130">In the **Column Properties** tab, expand the **Computed Column Specification** property.</span></span>  
  
4.  <span data-ttu-id="1620b-131">**(수식)** 자식 속성에서 오른쪽에 있는 표 형태 셀에 현재 열의 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-131">In the **(Formula)** child property, enter the expression for this column in the grid cell to the right.</span></span> <span data-ttu-id="1620b-132">예를 들어 `SalesTotal` 열에 입력한 수식이 `SubTotal+TaxAmt+Freight`일 경우 이 수식은 테이블의 각 행에 대해 이 열에 값을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-132">For example, in a `SalesTotal` column, the formula you enter might be `SubTotal+TaxAmt+Freight`, which adds the value in these columns for each row in the table.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="1620b-133">수식으로 데이터 형식이 다른 두 식을 결합할 경우 데이터 형식 우선 순위 규칙에 따라 우선 순위가 낮은 데이터 형식이 우선 순위가 높은 데이터 형식으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-133">When a formula combines two expressions of different data types, the rules for data type precedence specify that the data type with the lower precedence is converted to the data type with the higher precedence.</span></span> <span data-ttu-id="1620b-134">이 암시적 변환이 지원되지 않으면 "`Error validating the formula for column column_name.`" 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-134">If the conversion is not a supported implicit conversion, the error "`Error validating the formula for column column_name.`" is returned.</span></span> <span data-ttu-id="1620b-135">CAST 또는 CONVERT 함수를 사용하여 데이터 형식 충돌을 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-135">Use the CAST or CONVERT function to resolve the data type conflict.</span></span> <span data-ttu-id="1620b-136">예를 들어 `nvarchar` 형식 열을 `int` 형식 열과 결합할 경우 `('Prod'+CONVERT(nvarchar(23),ProductID))` 수식에 표시된 대로 정수 형식을 `nvarchar`으로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-136">For example, if a column of type `nvarchar` is combined with a column of type `int`, the integer type must be converted to `nvarchar` as shown in this formula `('Prod'+CONVERT(nvarchar(23),ProductID))`.</span></span> <span data-ttu-id="1620b-137">자세한 내용은 [CAST 및 CONVERT&#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1620b-137">For more information, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
5.  <span data-ttu-id="1620b-138">**지속형** 자식 속성 드롭다운에서 **예** 또는 **아니요** 를 선택하여 데이터를 지속할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-138">Indicate whether the data is persisted by choosing **Yes** or **No** from the drop-down for the **Is Persisted** child property.</span></span>  
  
6.  <span data-ttu-id="1620b-139">**파일** 메뉴에서 ‘테이블 이름’ **저장**을 클릭합니다.__</span><span class="sxs-lookup"><span data-stu-id="1620b-139">On the **File** menu, click **Save**_table name_.</span></span>  
  
#### <a name="to-add-a-computed-column-definition-to-an-existing-column"></a><span data-ttu-id="1620b-140">기존 열에 계산 열 정의를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="1620b-140">To add a computed column definition to an existing column</span></span>  
  
1.  <span data-ttu-id="1620b-141">**개체 탐색기**에서 변경할 열이 포함된 테이블을 마우스 오른쪽 단추로 클릭하고 **열** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-141">In **Object Explorer**, right-click the table with the column for which you want to change and expand the **Columns** folder.</span></span>  
  
2.  <span data-ttu-id="1620b-142">계산 열 수식을 지정할 열을 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-142">Right-click the column for which you want to specify a computed column formula and click **Delete**.</span></span> <span data-ttu-id="1620b-143">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-143">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="1620b-144">새 열을 추가하고 이전 절차에 따라 새 계산 열을 추가하여 계산 열 수식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-144">Add a new column and specify the computed column formula by following the previous procedure to add a new computed column.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1620b-145">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="1620b-145">Using Transact-SQL</span></span>  
  
#### <a name="to-add-a-computed-column-when-creating-a-table"></a><span data-ttu-id="1620b-146">테이블을 만들 때 계산 열을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="1620b-146">To add a computed column when creating a table</span></span>  
  
1.  <span data-ttu-id="1620b-147">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-147">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1620b-148">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-148">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1620b-149">다음 예를 복사하여 쿼리 창에 붙여 넣은 후 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-149">Copy and paste the following example into the query window and then click **Execute**.</span></span> <span data-ttu-id="1620b-150">이 예에서는 `QtyAvailable` 열의 값을 `UnitPrice` 열의 값으로 곱하는 계산 열을 포함하는 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-150">The example creates a table with a computed column that multiplies the value in the `QtyAvailable` column times the value in the `UnitPrice` column.</span></span>  
  
    ```  
    CREATE TABLE dbo.Products   
    (  
        ProductID int IDENTITY (1,1) NOT NULL  
      , QtyAvailable smallint  
      , UnitPrice money  
      , InventoryValue AS QtyAvailable * UnitPrice  
    );  
  
    -- Insert values into the table.  
    INSERT INTO dbo.Products (QtyAvailable, UnitPrice)  
    VALUES (25, 2.00), (10, 1.5);  
  
    -- Display the rows in the table.  
    SELECT ProductID, QtyAvailable, UnitPrice, InventoryValue  
    FROM dbo.Products;  
  
    ```  
  
#### <a name="to-add-a-new-computed-column-to-an-existing-table"></a><span data-ttu-id="1620b-151">기존 테이블에 새 계산 열을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="1620b-151">To add a new computed column to an existing table</span></span>  
  
1.  <span data-ttu-id="1620b-152">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-152">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1620b-153">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-153">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1620b-154">다음 예를 복사하여 쿼리 창에 붙여 넣은 후 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-154">Copy and paste the following example into the query window and then click **Execute**.</span></span> <span data-ttu-id="1620b-155">다음 예에서는 이전 예에서 만든 테이블에 새 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-155">The following example adds a new column to the table created in the previous example.</span></span>  
  
    ```  
    ALTER TABLE dbo.Products ADD RetailValue AS (QtyAvailable * UnitPrice * 1.35);  
  
    ```  
  
#### <a name="to-change-an-existing-column-to-a-computed-column"></a><span data-ttu-id="1620b-156">기존 열을 계산 열로 변경하려면</span><span class="sxs-lookup"><span data-stu-id="1620b-156">To change an existing column to a computed column</span></span>  
  
1.  <span data-ttu-id="1620b-157">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-157">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1620b-158">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-158">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1620b-159">기존 열을 계산 열로 변경하려면 계산 열을 삭제한 후 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-159">To change an existing column to a computed column you must drop and re-create the computed column.</span></span> <span data-ttu-id="1620b-160">다음 예를 복사하여 쿼리 창에 붙여 넣은 후 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-160">Copy and paste the following example into the query window and then click **Execute**.</span></span> <span data-ttu-id="1620b-161">다음 예에서는 이전 예에서 추가한 열을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="1620b-161">The following example modifies the column added in the previous example.</span></span>  
  
    ```  
    ALTER TABLE dbo.Products DROP COLUMN RetailValue;  
    GO  
    ALTER TABLE dbo.Products ADD RetailValue AS (QtyAvailable * UnitPrice * 1.5);  
  
    ```  
  
     <span data-ttu-id="1620b-162">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1620b-162">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
