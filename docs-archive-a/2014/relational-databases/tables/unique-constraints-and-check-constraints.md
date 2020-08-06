---
title: UNIQUE 제약 조건 및 CHECK 제약 조건 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- constraints [SQL Server], Visual Database Tools
- Visual Database Tools [SQL Server], constraints
ms.assetid: 637098af-2567-48f8-90f4-b41df059833e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 205e4ae3d6f89f10a933bf357d1eeda458852584
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728124"
---
# <a name="unique-constraints-and-check-constraints"></a><span data-ttu-id="3d7a3-102">UNIQUE 제약 조건 및 CHECK 제약 조건</span><span class="sxs-lookup"><span data-stu-id="3d7a3-102">Unique Constraints and Check Constraints</span></span>
  <span data-ttu-id="3d7a3-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에서 데이터 무결성을 강제 적용하는 데 사용할 수 있는 두 가지 유형의 제약 조건으로 UNIQUE 제약 조건과 CHECK 제약 조건이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-103">UNIQUE constraints and CHECK constraints are two types of constraints that can be used to enforce data integrity in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span> <span data-ttu-id="3d7a3-104">이들 키는 중요한 데이터베이스 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-104">These are important database objects.</span></span>  
  
 <span data-ttu-id="3d7a3-105">이 항목에는 다음과 같은 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-105">This topic contains the following sections.</span></span>  
  
 [<span data-ttu-id="3d7a3-106">UNIQUE 제약 조건</span><span class="sxs-lookup"><span data-stu-id="3d7a3-106">UNIQUE Constraints</span></span>](#Unique)  
  
 [<span data-ttu-id="3d7a3-107">CHECK 제약 조건</span><span class="sxs-lookup"><span data-stu-id="3d7a3-107">CHECK Constraints</span></span>](#Check)  
  
 [<span data-ttu-id="3d7a3-108">관련 작업</span><span class="sxs-lookup"><span data-stu-id="3d7a3-108">Related Tasks</span></span>](#Tasks)  
  
##  <a name="unique-constraints"></a><a name="Unique"></a> <span data-ttu-id="3d7a3-109">UNIQUE 제약 조건</span><span class="sxs-lookup"><span data-stu-id="3d7a3-109">UNIQUE Constraints</span></span>  
 <span data-ttu-id="3d7a3-110">제약 조건은 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 에서 사용자에게 적용하는 규칙입니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-110">Constraints are rules that the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] enforces for you.</span></span> <span data-ttu-id="3d7a3-111">예를 들어 UNIQUE 제약 조건을 사용하면 기본 키에 참여하고 있지 않은 특정 열에 중복 값이 입력되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-111">For example, you can use UNIQUE constraints to make sure that no duplicate values are entered in specific columns that do not participate in a primary key.</span></span> <span data-ttu-id="3d7a3-112">UNIQUE 제약 조건과 PRIMARY KEY 제약 조건이 모두 고유성을 강제 적용하지만 기본 키가 아닌 열 또는 열 조합에 대해 고유성을 강제 적용하려면 PRIMARY KEY 제약 조건 대신 UNIQUE 제약 조건을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-112">Although both a UNIQUE constraint and a PRIMARY KEY constraint enforce uniqueness, use a UNIQUE constraint instead of a PRIMARY KEY constraint when you want to enforce the uniqueness of a column, or combination of columns, that is not the primary key.</span></span>  
  
 <span data-ttu-id="3d7a3-113">PRIMARY KEY 제약 조건과 달리 UNIQUE 제약 조건에서는 NULL 값이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-113">Unlike PRIMARY KEY constraints, UNIQUE constraints allow for the value NULL.</span></span> <span data-ttu-id="3d7a3-114">단 UNIQUE 제약 조건에서 사용되는 다른 값과 마찬가지로 Null 값도 열당 하나만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-114">However, as with any value participating in a UNIQUE constraint, only one null value is allowed per column.</span></span> <span data-ttu-id="3d7a3-115">UNIQUE 제약 조건은 FOREIGN KEY 제약 조건에서 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-115">A UNIQUE constraint can be referenced by a FOREIGN KEY constraint.</span></span>  
  
 <span data-ttu-id="3d7a3-116">테이블의 기존 열에 UNIQUE 제약 조건이 추가되면 기본적으로 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 열의 기존 데이터를 검사하여 모든 값이 고유한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-116">When a UNIQUE constraint is added to an existing column or columns in the table, by default, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] examines the existing data in the columns to make sure all values are unique.</span></span> <span data-ttu-id="3d7a3-117">중복된 값이 있는 열에 UNIQUE 제약 조건을 추가하면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 오류를 반환하고 제약 조건이 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-117">If a UNIQUE constraint is added to a column that has duplicated values, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] returns an error and does not add the constraint.</span></span>  
  
 <span data-ttu-id="3d7a3-118">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 자동으로 UNIQUE 인덱스를 만들어 UNIQUE 제약 조건의 고유성 요구 사항을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-118">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] automatically creates a UNIQUE index to enforce the uniqueness requirement of the UNIQUE constraint.</span></span> <span data-ttu-id="3d7a3-119">따라서 중복 행을 삽입하려고 하면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 UNIQUE 제약 조건을 위반하여 테이블에 행을 추가할 수 없다는 오류 메시지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-119">Therefore, if an attempt to insert a duplicate row is made, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] returns an error message that states the UNIQUE constraint has been violated and does not add the row to the table.</span></span> <span data-ttu-id="3d7a3-120">클러스터형 인덱스가 명시적으로 지정되지 않는 한 고유한 비클러스터형 인덱스가 기본적으로 생성되어 UNIQUE 제약 조건을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-120">Unless a clustered index is explicitly specified, a unique, nonclustered index is created by default to enforce the UNIQUE constraint.</span></span>  
  
##  <a name="check-constraints"></a><a name="Check"></a> <span data-ttu-id="3d7a3-121">CHECK 제약 조건</span><span class="sxs-lookup"><span data-stu-id="3d7a3-121">CHECK Constraints</span></span>  
 <span data-ttu-id="3d7a3-122">CHECK 제약 조건은 하나 이상의 열에서 허용되는 값을 제한하여 도메인 무결성을 강제 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-122">CHECK constraints enforce domain integrity by limiting the values that are accepted by one or more columns.</span></span> <span data-ttu-id="3d7a3-123">논리 연산자에 따라 TRUE 또는 FALSE를 반환하는 논리(부울) 식을 사용하여 CHECK 제약 조건을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-123">You can create a CHECK constraint with any logical (Boolean) expression that returns TRUE or FALSE based on the logical operators.</span></span> <span data-ttu-id="3d7a3-124">예를 들어 15,000달러부터 100,000달러까지의 데이터만 허용하는 CHECK 제약 조건을 만들어 **salary** 열의 값 범위를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-124">For example, the range of values for a **salary** column can be limited by creating a CHECK constraint that allows for only data that ranges from $15,000 through $100,000.</span></span> <span data-ttu-id="3d7a3-125">이렇게 하면 정상 월급 범위를 벗어나는 월급은 입력되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-125">This prevents salaries from being entered beyond the regular salary range.</span></span> <span data-ttu-id="3d7a3-126">논리 식은 다음과 같습니다. `salary >= 15000 AND salary <= 100000`</span><span class="sxs-lookup"><span data-stu-id="3d7a3-126">The logical expression would be the following: `salary >= 15000 AND salary <= 100000`.</span></span>  
  
 <span data-ttu-id="3d7a3-127">열 하나에 여러 개의 CHECK 제약 조건을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-127">You can apply multiple CHECK constraints to a single column.</span></span> <span data-ttu-id="3d7a3-128">테이블 수준에서 CHECK 제약 조건을 만들어 여러 열에 적용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-128">You can also apply a single CHECK constraint to multiple columns by creating it at the table level.</span></span> <span data-ttu-id="3d7a3-129">예를 들어 여러 열에 대한 CHECK 제약 조건을 사용하여 **country_region** 열 값이 **USA** 인 모든 행이 **state** 열에서 두 문자의 값을 갖도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-129">For example, a multiple-column CHECK constraint could be used to confirm that any row with a **country_region** column value of **USA** also has a two-character value in the **state** column.</span></span> <span data-ttu-id="3d7a3-130">이렇게 한 위치에서 여러 조건을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-130">This allows for multiple conditions to be checked in one location.</span></span>  
  
 <span data-ttu-id="3d7a3-131">CHECK 제약 조건은 열에 있는 값을 다룬다는 점에서는 FOREIGN KEY 제약 조건과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-131">CHECK constraints are similar to FOREIGN KEY constraints in that they control the values that are put in a column.</span></span> <span data-ttu-id="3d7a3-132">어떤 값이 유효한지 결정하는 방법은 서로 다릅니다. FOREIGN KEY 제약 조건은 다른 테이블로부터 유효한 값을 가져오는 반면 CHECK 제약 조건은 논리 식으로부터 유효한 값을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-132">The difference is in how they determine which values are valid: FOREIGN KEY constraints obtain the list of valid values from another table, while CHECK constraints determine the valid values from a logical expression.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="3d7a3-133">제약 조건에 암시적 또는 명시적 데이터 형식 변환이 포함된 경우 특정 작업이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-133">Constraints that include implicit or explicit data type conversion may cause certain operations to fail.</span></span> <span data-ttu-id="3d7a3-134">예를 들어 파티션 전환의 원본인 테이블에 정의된 이러한 제약 조건으로 인해 ALTER TABLE...SWITCH 작업이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-134">For example, such constraints defined on tables that are sources of partition switching may cause an ALTER TABLE...SWITCH operation to fail.</span></span> <span data-ttu-id="3d7a3-135">제약 조건 정의에서 데이터 형식을 변환하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-135">Avoid data type conversion in constraint definitions.</span></span>  
  
### <a name="limitations-of-check-constraints"></a><span data-ttu-id="3d7a3-136">CHECK 제약 조건의 제한 사항</span><span class="sxs-lookup"><span data-stu-id="3d7a3-136">Limitations of CHECK Constraints</span></span>  
 <span data-ttu-id="3d7a3-137">CHECK 제약 조건은 FALSE로 평가되는 값을 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-137">CHECK constraints reject values that evaluate to FALSE.</span></span> <span data-ttu-id="3d7a3-138">Null 값은 UNKNOWN으로 평가되므로 식에 Null 값이 있으면 제약 조건이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-138">Because null values evaluate to UNKNOWN, their presence in expressions may override a constraint.</span></span> <span data-ttu-id="3d7a3-139">예를 들어 mycolumn `int` **= 10**과 같이 **mycolumn** 에 값 10만 포함할 수 있도록 열 **mycolumn** 에 대 한 제약 조건을 지정 한다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-139">For example, suppose you place a constraint on an `int` column **MyColumn** specifying that **MyColumn** can contain only the value 10 (**MyColumn=10**).</span></span> <span data-ttu-id="3d7a3-140">**MyColumn**에 NULL 값을 삽입할 경우 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서는 NULL을 삽입하고 오류를 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-140">If you insert the value NULL into **MyColumn**, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] inserts NULL and does not return an error.</span></span>  
  
 <span data-ttu-id="3d7a3-141">CHECK 제약 조건은 확인 중인 조건이 테이블의 모든 행에 대해 FALSE가 아니면 TRUE를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-141">A CHECK constraint returns TRUE when the condition it is checking is not FALSE for any row in the table.</span></span> <span data-ttu-id="3d7a3-142">CHECK 제약 조건은 행 수준에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-142">A CHECK constraint works at the row level.</span></span> <span data-ttu-id="3d7a3-143">방금 만든 테이블에 행이 없어도 이 테이블의 CHECK 제약 조건은 유효한 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-143">If a table that has just been created does not have any rows, any CHECK constraint on this table is considered valid.</span></span> <span data-ttu-id="3d7a3-144">다음 예와 같이 이러한 상황은 예기치 않은 결과를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-144">This situation can produce unexpected results, as in the following example.</span></span>  
  
```  
CREATE TABLE CheckTbl (col1 int, col2 int);  
GO  
CREATE FUNCTION CheckFnctn()  
RETURNS int  
AS   
BEGIN  
   DECLARE @retval int  
   SELECT @retval = COUNT(*) FROM CheckTbl  
   RETURN @retval  
END;  
GO  
ALTER TABLE CheckTbl  
ADD CONSTRAINT chkRowCount CHECK (dbo.CheckFnctn() >= 1 );  
GO  
```  
  
 <span data-ttu-id="3d7a3-145">추가 중인 `CHECK` 제약 조건은 `CheckTbl`테이블에 행이 적어도 하나 이상 있어야 함을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-145">The `CHECK` constraint being added specifies that there must be at least one row in table `CheckTbl`.</span></span> <span data-ttu-id="3d7a3-146">그러나 이 제약 조건이 적용되는 테이블에 행이 없기 때문에 ALTER TABLE 문이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-146">However, because there are no rows in the table against which to check the condition of this constraint, the ALTER TABLE statement succeeds.</span></span>  
  
 <span data-ttu-id="3d7a3-147">DELETE 문을 실행하는 동안에는 CHECK 제약 조건이 확인되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-147">CHECK constraints are not validated during DELETE statements.</span></span> <span data-ttu-id="3d7a3-148">따라서 특정 유형의 CHECK 제약 조건이 있는 테이블에 대해 DELETE 문을 실행하면 예기치 않은 결과가 생성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-148">Therefore, executing DELETE statements on tables with certain types of check constraints may produce unexpected results.</span></span> <span data-ttu-id="3d7a3-149">예를 들어 `CheckTbl`테이블에서 다음 문을 실행하는 경우를 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-149">For example, consider the following statements executed on table `CheckTbl`.</span></span>  
  
```  
INSERT INTO CheckTbl VALUES (10, 10);  
GO  
DELETE CheckTbl WHERE col1 = 10;  
```  
  
 <span data-ttu-id="3d7a3-150">`DELETE` 제약 조건에서 `CHECK` 테이블에 행이 적어도 `CheckTbl` 개 이상 있어야 한다고 지정해도 `1` 문이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-150">The `DELETE` statement succeeds, even though the `CHECK` constraint specifies that table `CheckTbl` must have at least `1` row.</span></span>  
  
##  <a name="related-tasks"></a><a name="Tasks"></a> <span data-ttu-id="3d7a3-151">관련 작업</span><span class="sxs-lookup"><span data-stu-id="3d7a3-151">Related Tasks</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3d7a3-152">테이블이 복제용으로 게시된 경우 Transact-SQL 문 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 또는 SMO(SQL Server 관리 개체)를 사용하여 스키마를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-152">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="3d7a3-153">테이블 디자이너 또는 데이터베이스 다이어그램 디자이너를 사용하여 스키마를 변경하면 테이블 삭제 및 재생성이 시도됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-153">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="3d7a3-154">게시된 개체를 삭제할 수 없으므로 스키마가 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-154">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
|<span data-ttu-id="3d7a3-155">Task</span><span class="sxs-lookup"><span data-stu-id="3d7a3-155">Task</span></span>|<span data-ttu-id="3d7a3-156">항목</span><span class="sxs-lookup"><span data-stu-id="3d7a3-156">Topic</span></span>|  
|----------|-----------|  
|<span data-ttu-id="3d7a3-157">UNIQUE 제약 조건을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-157">Describes how to create a unique constraint.</span></span>|[<span data-ttu-id="3d7a3-158">UNIQUE 제약 조건 만들기</span><span class="sxs-lookup"><span data-stu-id="3d7a3-158">Create Unique Constraints</span></span>](../tables/create-unique-constraints.md)|  
|<span data-ttu-id="3d7a3-159">UNIQUE 제약 조건을 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-159">Describes how to modify a unique constraint.</span></span>|[<span data-ttu-id="3d7a3-160">UNIQUE 제약 조건 수정</span><span class="sxs-lookup"><span data-stu-id="3d7a3-160">Modify Unique Constraints</span></span>](../tables/modify-unique-constraints.md)|  
|<span data-ttu-id="3d7a3-161">UNIQUE 제약 조건을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-161">Describes how to delete a unique constraint.</span></span>|[<span data-ttu-id="3d7a3-162">UNIQUE 제약 조건 삭제</span><span class="sxs-lookup"><span data-stu-id="3d7a3-162">Delete Unique Constraints</span></span>](../tables/delete-unique-constraints.md)|  
|<span data-ttu-id="3d7a3-163">복제 에이전트가 테이블에 데이터를 삽입 또는 업데이트하는 경우 CHECK 제약 조건을 사용하지 않도록 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-163">Describes how to disable a check constraint when a replication agent inserts or updates data in your table.</span></span>|[<span data-ttu-id="3d7a3-164">복제할 때 CHECK 제약 조건 해제</span><span class="sxs-lookup"><span data-stu-id="3d7a3-164">Disable Check Constraints for Replication</span></span>](../tables/disable-check-constraints-for-replication.md)|  
|<span data-ttu-id="3d7a3-165">테이블에서 데이터를 추가, 업데이트 또는 삭제할 때 CHECK 제약 조건을 사용하지 않도록 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-165">Describes how to disable a check constraint when data is added to, updated in, or deleted from a table.</span></span>|[<span data-ttu-id="3d7a3-166">INSERT 및 UPDATE 문에서 CHECK 제약 조건 해제</span><span class="sxs-lookup"><span data-stu-id="3d7a3-166">Disable Check Constraints with INSERT and UPDATE Statements</span></span>](../tables/disable-check-constraints-with-insert-and-update-statements.md)|  
|<span data-ttu-id="3d7a3-167">제약 조건 식 또는 특정 조건에 따라 제약 조건을 사용하거나 사용할 수 없게 하는 옵션을 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-167">Describes how to change the constraint expression or the options that enable or disable the constraint for specific conditions.</span></span>|[<span data-ttu-id="3d7a3-168">CHECK 제약 조건 수정</span><span class="sxs-lookup"><span data-stu-id="3d7a3-168">Modify Check Constraints</span></span>](../tables/modify-check-constraints.md)|  
|<span data-ttu-id="3d7a3-169">CHECK 제약 조건을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-169">Describes how to delete a check constraint.</span></span>|[<span data-ttu-id="3d7a3-170">CHECK 제약 조건 삭제</span><span class="sxs-lookup"><span data-stu-id="3d7a3-170">Delete Check Constraints</span></span>](../tables/delete-check-constraints.md)|  
|<span data-ttu-id="3d7a3-171">CHECK 제약 조건의 속성을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7a3-171">Describes how to view the properties of a check constraint.</span></span>|[<span data-ttu-id="3d7a3-172">UNIQUE 제약 조건 및 CHECK 제약 조건</span><span class="sxs-lookup"><span data-stu-id="3d7a3-172">Unique Constraints and Check Constraints</span></span>](../tables/unique-constraints-and-check-constraints.md)|  
  
  
