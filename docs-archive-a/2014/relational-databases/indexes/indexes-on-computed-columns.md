---
title: 계산 열의 인덱스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- computed columns, index creation
- index creation [SQL Server], computed columns
- imprecise columns
- persisted computed columns
- precise [SQL Server]
ms.assetid: 8d17ac9c-f3af-4bbb-9cc1-5cf647e994c4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2ecbca9e7838c4c9395a8bcb6e11351c40f7037f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742060"
---
# <a name="indexes-on-computed-columns"></a><span data-ttu-id="418e8-102">계산 열의 인덱스</span><span class="sxs-lookup"><span data-stu-id="418e8-102">Indexes on Computed Columns</span></span>
  <span data-ttu-id="418e8-103">다음 요구 사항을 충족하면 계산 열에 인덱스를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-103">You can define indexes on computed columns as long as the following requirements are met:</span></span>  
  
-   <span data-ttu-id="418e8-104">소유권 요구 사항</span><span class="sxs-lookup"><span data-stu-id="418e8-104">Ownership requirements</span></span>  
  
-   <span data-ttu-id="418e8-105">결정성 요구 사항</span><span class="sxs-lookup"><span data-stu-id="418e8-105">Determinism requirements</span></span>  
  
-   <span data-ttu-id="418e8-106">정밀도 요구 사항</span><span class="sxs-lookup"><span data-stu-id="418e8-106">Precision requirements</span></span>  
  
-   <span data-ttu-id="418e8-107">데이터 형식 요구 사항</span><span class="sxs-lookup"><span data-stu-id="418e8-107">Data type requirements</span></span>  
  
-   <span data-ttu-id="418e8-108">SET 옵션 요구 사항</span><span class="sxs-lookup"><span data-stu-id="418e8-108">SET option requirements</span></span>  
  
 <span data-ttu-id="418e8-109">**소유권 요구 사항**</span><span class="sxs-lookup"><span data-stu-id="418e8-109">**Ownership Requirements**</span></span>  
  
 <span data-ttu-id="418e8-110">계산 열에서 모든 함수 참조의 소유자는 테이블 소유자와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-110">All function references in the computed column must have the same owner as the table.</span></span>  
  
 <span data-ttu-id="418e8-111">**명확성 요구 사항**</span><span class="sxs-lookup"><span data-stu-id="418e8-111">**Determinism Requirements**</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="418e8-112">지정된 입력 집합에 대해 항상 같은 결과 집합을 반환하는 식은 결정적입니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-112">Expressions are deterministic if they always return the same result for a specified set of inputs.</span></span> <span data-ttu-id="418e8-113">**COLUMNPROPERTY** 함수의 [IsDeterministic](/sql/t-sql/functions/columnproperty-transact-sql) 속성은 *computed_column_expression* 이 결정적인지 여부를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-113">The **IsDeterministic** property of the [COLUMNPROPERTY](/sql/t-sql/functions/columnproperty-transact-sql) function reports whether a *computed_column_expression* is deterministic.</span></span>  
  
 <span data-ttu-id="418e8-114">*computed_column_expression* 은 결정적이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-114">The *computed_column_expression* must be deterministic.</span></span> <span data-ttu-id="418e8-115">*computed_column_expression* 은 다음 조건 중 하나 이상이 충족되는 경우 결정적입니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-115">A *computed_column_expression* is deterministic when one or more of the following is true:</span></span>  
  
-   <span data-ttu-id="418e8-116">식에서 참조하는 모든 함수가 결정적이고 정확합니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-116">All functions that are referenced by the expression are deterministic and precise.</span></span> <span data-ttu-id="418e8-117">이러한 함수에는 사용자 정의 함수와 기본 제공 함수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-117">These functions include both user-defined and built-in functions.</span></span> <span data-ttu-id="418e8-118">자세한 내용은 [Deterministic and Nondeterministic Functions](../user-defined-functions/deterministic-and-nondeterministic-functions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="418e8-118">For more information, see [Deterministic and Nondeterministic Functions](../user-defined-functions/deterministic-and-nondeterministic-functions.md).</span></span> <span data-ttu-id="418e8-119">계산 열이 PERSISTED일 경우 함수가 정확하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-119">Functions might be imprecise if the computed column is PERSISTED.</span></span> <span data-ttu-id="418e8-120">자세한 내용은 이 항목의 뒤에 나오는 [지속형 계산 열에 인덱스 만들기](#BKMK_persisted) 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="418e8-120">For more information, see [Creating Indexes on Persisted Computed Columns](#BKMK_persisted) later in this topic.</span></span>  
  
-   <span data-ttu-id="418e8-121">식에서 참조하는 모든 열은 계산 열이 있는 테이블에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-121">All columns that are referenced in the expression come from the table that contains the computed column.</span></span>  
  
-   <span data-ttu-id="418e8-122">여러 행에서 데이터를 끌어 오는 열 참조가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-122">No column reference pulls data from multiple rows.</span></span> <span data-ttu-id="418e8-123">예를 들어 SUM 또는 AVG와 같은 집계 함수는 여러 행의 데이터에 의존하므로 *computed_column_expression* 은 비결정적입니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-123">For example, aggregate functions such as SUM or AVG depend on data from multiple rows and would make a *computed_column_expression* nondeterministic.</span></span>  
  
-   <span data-ttu-id="418e8-124">*computed_column_expression* 에는 시스템 데이터 액세스 또는 사용자 데이터 액세스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-124">The *computed_column_expression* has no system data access or user data access.</span></span>  
  
 <span data-ttu-id="418e8-125">CLR(공용 언어 런타임) 식이 포함된 계산 열에 인덱스를 만들려면 열이 결정적이어야 하고 PERSISTED로 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-125">Any computed column that contains a common language runtime (CLR) expression must be deterministic and marked PERSISTED before the column can be indexed.</span></span> <span data-ttu-id="418e8-126">CLR 사용자 정의 형식 식은 계산 열 정의에서 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-126">CLR user-defined type expressions are allowed in computed column definitions.</span></span> <span data-ttu-id="418e8-127">CLR 사용자 정의 형식의 계산 열은 형식이 비교 가능하면 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-127">Computed columns whose type is a CLR user-defined type can be indexed as long as the type is comparable.</span></span> <span data-ttu-id="418e8-128">자세한 내용은 [CLR 사용자 정의 형식](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="418e8-128">For more information, see [CLR User-Defined Types](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="418e8-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 인덱싱된 계산 열의 날짜 데이터 형식의 문자열 리터럴을 참조할 때 결정적 날짜 형식 스타일을 사용하여 리터럴을 원하는 날짜 유형으로 명시적으로 변환하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-129">When you refer to string literals of the date data type in indexed computed columns in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], we recommend that you explicitly convert the literal to the date type that you want by using a deterministic date format style.</span></span> <span data-ttu-id="418e8-130">결정적 날짜 형식 스타일 목록은 [CAST 및 CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="418e8-130">For a list of the date format styles that are deterministic, see [CAST and CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span> <span data-ttu-id="418e8-131">데이터베이스 호환성 수준이 80 이하로 설정되지 않은 경우 문자열을 날짜 데이터 형식으로 암시적으로 변환하는 작업과 관련된 식은 비결정적인 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-131">Expressions that involve implicit conversion of character strings to date data types are considered nondeterministic, unless the database compatibility level is set to 80 or earlier.</span></span> <span data-ttu-id="418e8-132">이는 결과가 서버 세션의 [LANGUAGE](/sql/t-sql/statements/set-language-transact-sql) 및 [DATEFORMAT](/sql/t-sql/statements/set-dateformat-transact-sql) 설정에 따라 달라 지기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-132">This is because the results depend on the [LANGUAGE](/sql/t-sql/statements/set-language-transact-sql) and [DATEFORMAT](/sql/t-sql/statements/set-dateformat-transact-sql) settings of the server session.</span></span> <span data-ttu-id="418e8-133">예를 들어 ' `CONVERT (datetime, '30 listopad 1996', 113)` ' 문자열이 다른 언어에서는 다른 월을 의미하므로`30 listopad 1996`식의 결과는 LANGUAGE 설정에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-133">For example, the results of the expression `CONVERT (datetime, '30 listopad 1996', 113)` depend on the LANGUAGE setting because the string '`30 listopad 1996`' means different months in different languages.</span></span> <span data-ttu-id="418e8-134">마찬가지로 `DATEADD(mm,3,'2000-12-01')`에서는 DATEFORMAT 설정에 따라 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 식의 `'2000-12-01'` 문자열을 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-134">Similarly, in the expression `DATEADD(mm,3,'2000-12-01')`, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] interprets the string `'2000-12-01'` based on the DATEFORMAT setting.</span></span>  
>   
>  <span data-ttu-id="418e8-135">호환성 수준이 80 이하로 설정되지 않은 경우에 데이터 정렬 간의 비유니코드 문자 데이터를 암시적으로 변환하는 작업도 비결정적인 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-135">Implicit conversion of non-Unicode character data between collations is also considered nondeterministic, unless the compatibility level is set to 80 or earlier.</span></span>  
>   
>  <span data-ttu-id="418e8-136">데이터베이스 호환성 수준 설정이 90이면 이러한 식이 포함된 계산 열에 인덱스를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-136">When the database compatibility level setting is 90, you cannot create indexes on computed columns that contain these expressions.</span></span> <span data-ttu-id="418e8-137">그러나 업그레이드된 데이터베이스로부터 이러한 식을 포함하는 기존 계산 열은 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-137">However, existing computed columns that contain these expressions from an upgraded database are maintainable.</span></span> <span data-ttu-id="418e8-138">문자열에서 날짜로의 암시적 변환이 포함된 인덱싱된 계산 열을 사용하는 경우 인덱스 손상을 방지하려면 데이터베이스와 애플리케이션에서 LANGUAGE 및 DATEFORMAT 설정이 일치하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-138">If you use indexed computed columns that contain implicit string to date conversions, to avoid possible index corruption, make sure that the LANGUAGE and DATEFORMAT settings are consistent in your databases and applications.</span></span>  
  
 <span data-ttu-id="418e8-139">**전체 자릿수 요구 사항**</span><span class="sxs-lookup"><span data-stu-id="418e8-139">**Precision Requirements**</span></span>  
  
 <span data-ttu-id="418e8-140">*computed_column_expression* 은 정확해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-140">The *computed_column_expression* must be precise.</span></span> <span data-ttu-id="418e8-141">*computed_column_expression* 은 다음 조건 중 하나 이상이 충족되는 경우 정확합니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-141">A *computed_column_expression* is precise when one or more of the following is true:</span></span>  
  
-   <span data-ttu-id="418e8-142">`float` 또는 `real` 데이터 형식의 식이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-142">It is not an expression of the `float` or `real` data types.</span></span>  
  
-   <span data-ttu-id="418e8-143">정의에 `float` 또는 `real` 데이터 형식을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-143">It does not use a `float` or `real` data type in its definition.</span></span> <span data-ttu-id="418e8-144">예를 들어 다음 문에서 열 `y`는 `int`이고 결정적이지만 정확하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-144">For example, in the following statement, column `y` is `int` and deterministic but not precise.</span></span>  
  
    ```  
    CREATE TABLE t2 (a int, b int, c int, x float,   
       y AS CASE x   
             WHEN 0 THEN a   
             WHEN 1 THEN b   
             ELSE c   
          END);  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="418e8-145">`float` 또는 `real` 식은 정확하지 않은 것으로 간주되므로 인덱스의 키가 될 수 없습니다. `float` 또는 `real` 식은 인덱싱된 뷰에서 사용할 수 있지만 키로는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-145">Any `float` or `real` expression is considered imprecise and cannot be a key of an index; a `float` or `real` expression can be used in an indexed view but not as a key.</span></span> <span data-ttu-id="418e8-146">계산 열의 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-146">This is true also for computed columns.</span></span> <span data-ttu-id="418e8-147">함수, 식 또는 사용자 정의 함수에 `float` 또는 `real` 식이 포함되어 있으면 정확하지 않은 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-147">Any function, expression, or user-defined function is considered imprecise if it contains any `float` or `real` expressions.</span></span> <span data-ttu-id="418e8-148">논리 식(비교)이 여기에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-148">This includes logical ones (comparisons).</span></span>  
  
 <span data-ttu-id="418e8-149">COLUMNPROPERTY 함수의 **IsPrecise** 속성은 *computed_column_expression* 이 정확한지 여부를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-149">The **IsPrecise** property of the COLUMNPROPERTY function reports whether a *computed_column_expression* is precise.</span></span>  
  
 <span data-ttu-id="418e8-150">**데이터 형식 요구 사항**</span><span class="sxs-lookup"><span data-stu-id="418e8-150">**Data Type Requirements**</span></span>  
  
-   <span data-ttu-id="418e8-151">계산 열에 대해 정의 된 *computed_column_expression* 는 `text` , `ntext` 또는 데이터 형식으로 계산 될 수 없습니다 `image` .</span><span class="sxs-lookup"><span data-stu-id="418e8-151">The *computed_column_expression* defined for the computed column cannot evaluate to the `text`, `ntext`, or `image` data types.</span></span>  
  
-   <span data-ttu-id="418e8-152">`image`, `ntext`, `text`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)` 및 `xml` 데이터 형식에서 파생된 계산 열의 경우 해당 데이터 형식을 인덱스 키 열로 사용할 수 있으면 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-152">Computed columns derived from `image`, `ntext`, `text`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, and `xml` data types can be indexed as long as the computed column data type is allowable as an index key column.</span></span>  
  
-   <span data-ttu-id="418e8-153">`image`, `ntext` 및 `text` 데이터 형식에서 파생된 계산 열의 경우 해당 데이터 형식을 키가 아닌 인덱스 열로 사용할 수 있으면 비클러스터형 인덱스에서 키가 아닌(포함된) 열이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-153">Computed columns derived from `image`, `ntext`, and `text` data types can be nonkey (included) columns in a nonclustered index as long as the computed column data type is allowable as a nonkey index column.</span></span>  
  
 <span data-ttu-id="418e8-154">**SET 옵션 요구 사항**</span><span class="sxs-lookup"><span data-stu-id="418e8-154">**SET Option Requirements**</span></span>  
  
-   <span data-ttu-id="418e8-155">계산 열을 정의하는 CREATE TABLE 또는 ALTER TABLE 문이 실행될 때 ANSI_NULLS 연결 수준 옵션이 ON으로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-155">The ANSI_NULLS connection-level option must be set to ON when the CREATE TABLE or ALTER TABLE statement that defines the computed column is executed.</span></span> <span data-ttu-id="418e8-156">[OBJECTPROPERTY](/sql/t-sql/functions/objectpropertyex-transact-sql) 함수의 **IsAnsiNullsOn** 속성을 통해 이 옵션이 ON으로 설정되었는지 여부를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-156">The [OBJECTPROPERTY](/sql/t-sql/functions/objectpropertyex-transact-sql) function reports whether the option is on through the **IsAnsiNullsOn** property.</span></span>  
  
-   <span data-ttu-id="418e8-157">인덱스가 만들어진 연결과 인덱스에서 값을 변경하는 INSERT, UPDATE 또는 DELETE 문을 실행하려 하는 모든 연결에서 6개의 SET 옵션이 ON으로 설정되어야 하고 하나의 옵션만 OFF로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-157">The connection on which the index is created, and all connections trying INSERT, UPDATE, or DELETE statements that will change values in the index, must have six SET options set to ON and one option set to OFF.</span></span> <span data-ttu-id="418e8-158">최적화 프로그램은 옵션 설정이 이와 다른 연결에서 실행된 SELECT 문에 대해 계산 열의 인덱스를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-158">The optimizer ignores an index on a computed column for any SELECT statement executed by a connection that does not have these same option settings.</span></span>  
  
    -   <span data-ttu-id="418e8-159">NUMERIC_ROUNDABORT 옵션이 OFF로 설정되어야 하고 다음 옵션이 ON으로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-159">The NUMERIC_ROUNDABORT option must be set to OFF, and the following options must be set to ON:</span></span>  
  
    -   <span data-ttu-id="418e8-160">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="418e8-160">ANSI_NULLS</span></span>  
  
    -   <span data-ttu-id="418e8-161">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="418e8-161">ANSI_PADDING</span></span>  
  
    -   <span data-ttu-id="418e8-162">ANSI_WARNINGS</span><span class="sxs-lookup"><span data-stu-id="418e8-162">ANSI_WARNINGS</span></span>  
  
    -   <span data-ttu-id="418e8-163">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="418e8-163">ARITHABORT</span></span>  
  
    -   <span data-ttu-id="418e8-164">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="418e8-164">CONCAT_NULL_YIELDS_NULL</span></span>  
  
    -   <span data-ttu-id="418e8-165">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="418e8-165">QUOTED_IDENTIFIER</span></span>  
  
     <span data-ttu-id="418e8-166">데이터베이스 호환성 수준이 90 이상으로 설정된 경우 ANSI_WARNINGS를 ON으로 설정하면 암시적으로 ARITHABORT가 ON으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-166">Setting ANSI_WARNINGS to ON implicitly sets ARITHABORT to ON when the database compatibility level is set to 90 or higher.</span></span>  
  
##  <a name="creating-indexes-on-persisted-computed-columns"></a><a name="BKMK_persisted"></a> <span data-ttu-id="418e8-167">지속형 계산 열에 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="418e8-167">Creating Indexes on Persisted Computed Columns</span></span>  
 <span data-ttu-id="418e8-168">CREATE TABLE 또는 ALTER TABLE 문에서 열이 PERSISTED로 표시된 경우 결정적이지만 정확하지 않은 식으로 정의된 계산 열에 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-168">You can create an index on a computed column that is defined with a deterministic, but imprecise, expression if the column is marked PERSISTED in the CREATE TABLE or ALTER TABLE statement.</span></span> <span data-ttu-id="418e8-169">즉 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] ,는 열에 인덱스를 만들 때와 쿼리에서 인덱스가 참조 될 때 이러한 지속형 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-169">This means that the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] uses these persisted values when it creates an index on the column, and when the index is referenced in a query.</span></span> <span data-ttu-id="418e8-170">이 옵션을 사용 하면 [!INCLUDE[ssDE](../../../includes/dnprdnshort-md.md)] 가 결정적이 고 정확 하 게 인 경우 계산 열에 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="418e8-170">This option enables you to create an index on a computed column when [!INCLUDE[ssDE](../../../includes/dnprdnshort-md.md)], is both deterministic and precise.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="418e8-171">관련 내용</span><span class="sxs-lookup"><span data-stu-id="418e8-171">Related Content</span></span>  
 [<span data-ttu-id="418e8-172">COLUMNPROPERTY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="418e8-172">COLUMNPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/columnproperty-transact-sql)  
  
  
