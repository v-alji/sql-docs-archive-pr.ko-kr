---
title: 사용자 정의 함수 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.udfproperties.general.f1
- sql12.swb.functionproperties.general.f1
helpviewer_keywords:
- displaying user-defined functions
- viewing user-defined functions
- user-defined functions [SQL Server], viewing
- status information [SQL Server], user-defined functions
ms.assetid: a45dfab5-6384-4311-b935-2e23a70c5c10
author: rothja
ms.author: jroth
ms.openlocfilehash: 5248f75540b72b489a7605b2cca34144dfcfedbf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638599"
---
# <a name="view-user-defined-functions"></a><span data-ttu-id="fd761-102">사용자 정의 함수 보기</span><span class="sxs-lookup"><span data-stu-id="fd761-102">View User-defined Functions</span></span>
  <span data-ttu-id="fd761-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 사용자 정의 함수의 정의 또는 속성에 대한 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-103">You can gain information about the definition or properties of a user-defined function in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="fd761-104">함수 정의를 보면 어떻게 데이터가 원본 테이블에서 파생되었는지 알 수 있고 함수에서 정의한 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-104">You may need to see the definition of the function to understand how its data is derived from the source tables or to see the data defined by the function.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fd761-105">함수가 참조하는 개체의 이름을 변경하려면 함수를 수정하여 함수의 텍스트에 새 이름이 적용되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-105">If you change the name of an object referenced by a function, you must modify that function so that its text reflects the new name.</span></span> <span data-ttu-id="fd761-106">따라서 개체 이름을 바꾸기 전에 먼저 개체의 종속성을 표시하여 영향을 받는 함수가 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-106">Therefore, before renaming an object, display the dependencies of the object first to determine if any functions are affected by the proposed change.</span></span>  
  
 <span data-ttu-id="fd761-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="fd761-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fd761-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="fd761-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fd761-109">보안</span><span class="sxs-lookup"><span data-stu-id="fd761-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fd761-110">**함수에 대한 정보를 얻으려면:**</span><span class="sxs-lookup"><span data-stu-id="fd761-110">**To get information about a function, using:**</span></span>  
  
     [<span data-ttu-id="fd761-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fd761-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fd761-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fd761-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fd761-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="fd761-113">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fd761-114">보안</span><span class="sxs-lookup"><span data-stu-id="fd761-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fd761-115">권한</span><span class="sxs-lookup"><span data-stu-id="fd761-115">Permissions</span></span>  
 <span data-ttu-id="fd761-116">**sys.sql_expression_dependencies** 를 사용하여 함수에 대한 모든 종속성을 찾으려면 데이터베이스에 대한 VIEW DEFINITION 권한과 데이터베이스의 **sys.sql_expression_dependencies** 에 대한 SELECT 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-116">Using **sys.sql_expression_dependencies** to find all the dependencies on a function requires VIEW DEFINITION permission on the database and SELECT permission on **sys.sql_expression_dependencies** for the database.</span></span> <span data-ttu-id="fd761-117">OBJECT_DEFINITION에 반환되는 정의와 같은 시스템 개체 정의는 모두에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-117">System object definitions, like the ones returned in OBJECT_DEFINITION, are publicly visible.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fd761-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="fd761-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-show-a-user-defined-functions-properties"></a><span data-ttu-id="fd761-119">사용자 정의 함수의 속성을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="fd761-119">To show a user-defined function's properties</span></span>  
  
1.  <span data-ttu-id="fd761-120">**개체 탐색기**에서 속성을 볼 함수가 포함된 데이터베이스 옆의 더하기 기호를 클릭한 다음 더하기 기호를 클릭하여 **프로그래밍 기능** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-120">In **Object Explorer**, click the plus sign next to the database that contains the function to which you want to view the properties, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="fd761-121">더하기 기호를 클릭하여 **함수** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-121">Click the plus sign to expand the **Functions** folder.</span></span>  
  
3.  <span data-ttu-id="fd761-122">더하기 기호를 클릭하여 속성을 볼 함수가 포함된 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-122">Click the plus sign to expand the folder that contains the function to which you want to view the properties:</span></span>  
  
    -   <span data-ttu-id="fd761-123">테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="fd761-123">Table-valued Function</span></span>  
  
    -   <span data-ttu-id="fd761-124">스칼라 반환 함수</span><span class="sxs-lookup"><span data-stu-id="fd761-124">Scalar-valued Function</span></span>  
  
    -   <span data-ttu-id="fd761-125">Aggregate 함수</span><span class="sxs-lookup"><span data-stu-id="fd761-125">Aggregate Function</span></span>  
  
4.  <span data-ttu-id="fd761-126">속성을 볼 함수를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-126">Right-click the function of which you want to view the properties and select **Properties**.</span></span>  
  
     <span data-ttu-id="fd761-127">다음 속성이 **함수 속성 –** _function_name_ 대화 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-127">The following properties appear in the **Function Properties -** _function_name_ dialog box.</span></span>  
  
     <span data-ttu-id="fd761-128">**Database**</span><span class="sxs-lookup"><span data-stu-id="fd761-128">**Database**</span></span>  
     <span data-ttu-id="fd761-129">이 함수를 포함하는 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-129">The name of the database containing this function.</span></span>  
  
     <span data-ttu-id="fd761-130">**Server**</span><span class="sxs-lookup"><span data-stu-id="fd761-130">**Server**</span></span>  
     <span data-ttu-id="fd761-131">현재 서버 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-131">The name of the current server instance.</span></span>  
  
     <span data-ttu-id="fd761-132">**사용자**</span><span class="sxs-lookup"><span data-stu-id="fd761-132">**User**</span></span>  
     <span data-ttu-id="fd761-133">이 연결을 사용하는 사용자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-133">The name of the user of this connection.</span></span>  
  
     <span data-ttu-id="fd761-134">**만든 날짜**</span><span class="sxs-lookup"><span data-stu-id="fd761-134">**Created date**</span></span>  
     <span data-ttu-id="fd761-135">함수를 만든 날짜를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-135">Displays the date the function was created.</span></span>  
  
     <span data-ttu-id="fd761-136">**다음으로 실행**</span><span class="sxs-lookup"><span data-stu-id="fd761-136">**Execute As**</span></span>  
     <span data-ttu-id="fd761-137">함수에 대한 실행 컨텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-137">Execution context for the function.</span></span>  
  
     <span data-ttu-id="fd761-138">**이름**</span><span class="sxs-lookup"><span data-stu-id="fd761-138">**Name**</span></span>  
     <span data-ttu-id="fd761-139">현재 함수의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-139">The name of the current function.</span></span>  
  
     <span data-ttu-id="fd761-140">**스키마**</span><span class="sxs-lookup"><span data-stu-id="fd761-140">**Schema**</span></span>  
     <span data-ttu-id="fd761-141">함수를 소유하는 스키마를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-141">Displays the schema that owns the function.</span></span>  
  
     <span data-ttu-id="fd761-142">**시스템 개체**</span><span class="sxs-lookup"><span data-stu-id="fd761-142">**System object**</span></span>  
     <span data-ttu-id="fd761-143">함수가 시스템 개체인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-143">Indicates whether the function is a system object.</span></span> <span data-ttu-id="fd761-144">사용 가능한 값은 True와 False입니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-144">Values are True and False.</span></span>  
  
     <span data-ttu-id="fd761-145">**ANSI NULL**</span><span class="sxs-lookup"><span data-stu-id="fd761-145">**ANSI NULLs**</span></span>  
     <span data-ttu-id="fd761-146">개체가 ANSI NULL 옵션으로 생성되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-146">Indicates if the object was created with the ANSI NULLs option.</span></span>  
  
     <span data-ttu-id="fd761-147">**암호화됨**</span><span class="sxs-lookup"><span data-stu-id="fd761-147">**Encrypted**</span></span>  
     <span data-ttu-id="fd761-148">함수를 암호화하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-148">Indicates whether the function is encrypted.</span></span> <span data-ttu-id="fd761-149">사용 가능한 값은 True와 False입니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-149">Values are True and False.</span></span>  
  
     <span data-ttu-id="fd761-150">**함수 유형**</span><span class="sxs-lookup"><span data-stu-id="fd761-150">**Function Type**</span></span>  
     <span data-ttu-id="fd761-151">사용자 정의 함수의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-151">The type of user defined function.</span></span>  
  
     <span data-ttu-id="fd761-152">**따옴표 붙은 식별자**</span><span class="sxs-lookup"><span data-stu-id="fd761-152">**Quoted identifier**</span></span>  
     <span data-ttu-id="fd761-153">개체가 따옴표 붙은 식별자 옵션으로 생성되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-153">Indicates if the object was created with the quoted identifier option.</span></span>  
  
     <span data-ttu-id="fd761-154">**스키마 바운드**</span><span class="sxs-lookup"><span data-stu-id="fd761-154">**Schema bound**</span></span>  
     <span data-ttu-id="fd761-155">스키마 바운드 함수인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-155">Indicates whether the function is schema-bound.</span></span> <span data-ttu-id="fd761-156">사용 가능한 값은 True와 False입니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-156">Values are True and False.</span></span> <span data-ttu-id="fd761-157">스키마 바운드 함수에 대한 자세한 내용은 [CREATE FUNCTION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql)의 SCHEMABINDING 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd761-157">For information about schema-bound functions, see the SCHEMABINDING section of [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fd761-158">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="fd761-158">Using Transact-SQL</span></span>  
  
#### <a name="to-get-the-definition-and-properties-of-a-function"></a><span data-ttu-id="fd761-159">함수의 정의 및 속성을 가져오려면</span><span class="sxs-lookup"><span data-stu-id="fd761-159">To get the definition and properties of a function</span></span>  
  
1.  <span data-ttu-id="fd761-160">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-160">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fd761-161">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-161">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fd761-162">다음 예 중 하나를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-162">Copy and paste one of the following examples into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Get the function name, definition, and relevant properties  
    SELECT sm.object_id,   
       OBJECT_NAME(sm.object_id) AS object_name,   
       o.type,   
       o.type_desc,   
       sm.definition,  
       sm.uses_ansi_nulls,  
       sm.uses_quoted_identifier,  
       sm.is_schema_bound,  
       sm.execute_as_principal_id  
    -- using the two system tables sys.sql_modules and sys.objects  
    FROM sys.sql_modules AS sm  
    JOIN sys.objects AS o ON sm.object_id = o.object_id  
    -- from the function 'dbo.ufnGetProductDealerPrice'  
    WHERE sm.object_id = OBJECT_ID('dbo.ufnGetProductDealerPrice')  
    ORDER BY o.type;  
    GO  
  
    ```  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Get the definition of the function dbo.ufnGetProductDealerPrice  
    SELECT OBJECT_DEFINITION (OBJECT_ID('dbo.ufnGetProductDealerPrice')) AS ObjectDefinition;  
    GO  
    ```  
  
 <span data-ttu-id="fd761-163">자세한 내용은 [sys.sql_modules&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) 및 [OBJECT_DEFINITION&#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd761-163">For more information, see [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) and [OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql).</span></span>  
  
#### <a name="to-get-the-dependencies-of-a-function"></a><span data-ttu-id="fd761-164">함수의 종속성을 가져오려면</span><span class="sxs-lookup"><span data-stu-id="fd761-164">To get the dependencies of a function</span></span>  
  
1.  <span data-ttu-id="fd761-165">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-165">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fd761-166">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-166">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fd761-167">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd761-167">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Get all of the dependency information  
    SELECT OBJECT_NAME(sed.referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(sed.referencing_id, sed.referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        sed.referencing_class_desc, sed.referenced_class_desc,  
        sed.referenced_server_name, sed.referenced_database_name, sed.referenced_schema_name,  
        sed.referenced_entity_name,   
        COALESCE(COL_NAME(sed.referenced_id, sed.referenced_minor_id), '(n/a)') AS referenced_column_name,  
        sed.is_caller_dependent, sed.is_ambiguous  
    -- from the two system tables sys.sql_expression_dependencies and sys.object  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    -- on the function dbo.ufnGetProductDealerPrice  
    WHERE sed.referencing_id = OBJECT_ID('dbo.ufnGetProductDealerPrice');  
    GO  
    ```  
  
 <span data-ttu-id="fd761-168">자세한 내용은 [sys.sql_expression_dependencies&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) 및 [sys.objects&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd761-168">For more information, see [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) and [sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql).</span></span>  
  
  
