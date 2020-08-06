---
title: 새 계획 지침 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.designer.newplanguide.f1
helpviewer_keywords:
- creating plan guides
- plan guides [SQL Server]. creating
ms.assetid: e1ad78bb-4857-40ea-a0c6-dcf5c28aef2f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 60ba31e2a63575a316db5befb397bea59c0ad1e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661082"
---
# <a name="create-a-new-plan-guide"></a><span data-ttu-id="90485-102">새 계획 지침 만들기</span><span class="sxs-lookup"><span data-stu-id="90485-102">Create a New Plan Guide</span></span>
  <span data-ttu-id="90485-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 계획 지침을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90485-103">You can create a plan guide in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="90485-104">계획 지침은 쿼리 힌트나 정해진 쿼리 계획을 쿼리에 연결하여 쿼리 최적화에 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="90485-104">Plan guides influence query optimization by attaching query hints or a fixed query plan to them.</span></span> <span data-ttu-id="90485-105">계획 지침에서 최적화하려는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 지정하고 사용할 쿼리 힌트가 들어 있는 OPTION 절이나 쿼리를 최적화하는 데 사용할 특정 쿼리 계획을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-105">In the plan guide, you specify the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that you want optimized and either an OPTION clause that contains the query hints you want to use or a specific query plan you want to use to optimize the query.</span></span> <span data-ttu-id="90485-106">쿼리가 실행하면 쿼리 최적화 프로그램이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 계획 지침과 비교하여 런타임에 쿼리에 OPTION 절을 추가하거나 지정된 쿼리 계획을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-106">When the query executes, the query optimizer matches the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to the plan guide and either attaches the OPTION clause to the query at run time or uses the specified query plan.</span></span>  
  
 <span data-ttu-id="90485-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="90485-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="90485-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="90485-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="90485-109">제한 사항</span><span class="sxs-lookup"><span data-stu-id="90485-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="90485-110">보안</span><span class="sxs-lookup"><span data-stu-id="90485-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="90485-111">**계획 지침을 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="90485-111">**To create a plan guide, using:**</span></span>  
  
     [<span data-ttu-id="90485-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="90485-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="90485-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="90485-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="90485-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="90485-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="90485-115">제한 사항</span><span class="sxs-lookup"><span data-stu-id="90485-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="90485-116">sp_create_plan_guide 인수는 표시된 순서대로 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-116">The arguments to sp_create_plan_guide must be provided in the order that is shown.</span></span> <span data-ttu-id="90485-117">`sp_create_plan_guide` 매개 변수 값을 제공하는 경우 모든 매개 변수 이름을 명시적으로 지정하거나 모두 지정하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-117">When you supply values for the parameters of `sp_create_plan_guide`, all parameter names must be specified explicitly, or none at all.</span></span> <span data-ttu-id="90485-118">예를 들어 `@name =`을 지정한 경우 `@stmt =`, `@type =` 등도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-118">For example, if `@name =` is specified, then `@stmt =` , `@type =`, and so on, must also be specified.</span></span> <span data-ttu-id="90485-119">마찬가지로 `@name =`을 생략하고 매개 변수 값만 제공한 경우 나머지 매개 변수 이름도 생략하고 해당 값만 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-119">Likewise, if `@name =` is omitted and only the parameter value is provided, the remaining parameter names must also be omitted, and only their values provided.</span></span> <span data-ttu-id="90485-120">인수 이름은 구문 이해를 위한 설명 용도로만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="90485-120">Argument names are for descriptive purposes only, to help understand the syntax.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="90485-121">는 지정된 매개 변수 이름과 해당 이름이 사용된 위치의 매개 변수 이름이 일치하는지 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90485-121">does not verify that the specified parameter name matches the name for the parameter in the position where the name is used.</span></span>  
  
-   <span data-ttu-id="90485-122">같은 쿼리 및 일괄 처리나 모듈에 대해 두 개 이상의 OBJECT 또는 SQL 계획 지침을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90485-122">You can create more than one OBJECT or SQL plan guide for the same query and batch or module.</span></span> <span data-ttu-id="90485-123">그러나 지정된 시간에 한 개의 계획 지침만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90485-123">However, only one plan guide can be enabled at any given time.</span></span>  
  
-   <span data-ttu-id="90485-124">저장 프로시저, 함수 또는 WITH ENCRYPTION 절을 지정하거나 임시인 DML 트리거를 참조하는 @module_or_batch 값에 대해서는 OBJECT 유형의 계획 지침을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90485-124">Plan guides of type OBJECT cannot be created for an @module_or_batch value that references a stored procedure, function, or DML trigger that specifies the WITH ENCRYPTION clause or that is temporary.</span></span>  
  
-   <span data-ttu-id="90485-125">활성화 여부에 관계없이 계획 지침에서 참조하는 함수, 저장 프로시저 또는 DML 트리거를 삭제하거나 수정하려고 하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-125">Trying to drop or modify a function, stored procedure, or DML trigger that is referenced by a plan guide, either enabled or disabled, causes an error.</span></span> <span data-ttu-id="90485-126">계획 지침에서 참조하는 트리거가 정의되어 있는 테이블을 삭제하려는 경우에도 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-126">Trying to drop a table that has a trigger defined on it that is referenced by a plan guide also causes an error.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="90485-127">보안</span><span class="sxs-lookup"><span data-stu-id="90485-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="90485-128">권한</span><span class="sxs-lookup"><span data-stu-id="90485-128">Permissions</span></span>  
 <span data-ttu-id="90485-129">OBJECT 유형의 계획 지침을 만들려면 참조된 개체에 ALTER 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-129">To create a plan guide of type OBJECT, requires ALTER permission on the referenced object.</span></span> <span data-ttu-id="90485-130">SQL 또는 TEMPLATE 유형의 계획 지침을 만들려면 현재 데이터베이스에 대한 ALTER 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-130">To create a plan guide of type SQL or TEMPLATE, requires ALTER permission on the current database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="90485-131">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="90485-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-plan-guide"></a><span data-ttu-id="90485-132">계획 지침을 만들려면</span><span class="sxs-lookup"><span data-stu-id="90485-132">To create a plan guide</span></span>  
  
1.  <span data-ttu-id="90485-133">더하기 기호를 클릭하여 계획 지침을 만들 데이터베이스를 확장한 다음 더하기 기호를 클릭하여 **프로그래밍 기능** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-133">Click the plus sign to expand the database in which you want to create a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="90485-134">**계획 지침** 폴더를 마우스 오른쪽 단추로 클릭 하 고 **새 계획 지침 ...** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-134">Right-click the **Plan Guides** folder and select **New Plan Guide...**.</span></span>  
  
3.  <span data-ttu-id="90485-135">**새 계획 지침** 대화 상자의 **이름** 입력란에 계획 지침 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-135">In the **New Plan Guide** dialog box, in the **Name** box, enter the name of the plan guide.</span></span>  
  
4.  <span data-ttu-id="90485-136">**문** 입력란에 계획 지침이 적용되는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-136">In the **Statement** box, enter the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement against which the plan guide is to be applied.</span></span>  
  
5.  <span data-ttu-id="90485-137">**범위 유형** 목록에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 나타나는 엔터티 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-137">In the **Scope type** list, select the type of entity in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span> <span data-ttu-id="90485-138">이것은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 계획 지침과 일치시키기 위한 컨텍스트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-138">This specifies the context for matching the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to the plan guide.</span></span> <span data-ttu-id="90485-139">가능한 값은 **OBJECT**, **SQL**및 **TEMPLATE**입니다.</span><span class="sxs-lookup"><span data-stu-id="90485-139">Possible values are **OBJECT**, **SQL**, and **TEMPLATE**.</span></span>  
  
6.  <span data-ttu-id="90485-140">**범위 일괄 처리** 입력란에 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 나타나는 일괄 처리 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-140">In the **Scope batch** box, enter the batch text in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span> <span data-ttu-id="90485-141">일괄 처리 텍스트는 USE\`\`*database* 문을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90485-141">The batch text cannot include a USE\`\`*database* statement.</span></span> <span data-ttu-id="90485-142">**범위 일괄 처리** 입력란은 **SQL** 이 범위 유형으로 선택되어 있는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90485-142">The **Scope batch** box is only available when **SQL** is selected as a scope type.</span></span> <span data-ttu-id="90485-143">범위 유형이 SQL인 경우 범위 일괄 처리 입력란에 아무 것도 입력하지 않으면 일괄 처리 텍스트 값은 **문** 입력란의 값과 동일한 값으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="90485-143">If nothing is entered in the scope batch box when SQL is the scope type, then the value of the batch text is set to the same value as is in the **Statement** box.</span></span>  
  
7.  <span data-ttu-id="90485-144">**범위 스키마 이름** 목록에 개체가 포함되는 스키마의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-144">In the **Scope schema name** list, enter the name of the schema in which the object is contained.</span></span> <span data-ttu-id="90485-145">**범위 스키마 이름** 입력란은 **개체** 가 범위 유형으로 선택되어 있는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90485-145">The **Scope schema name** box is only available when **Object** is selected as a scope type.</span></span>  
  
8.  <span data-ttu-id="90485-146">**범위 개체 이름** 입력란에 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 나타나는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저의 이름, 사용자 정의 스칼라 함수, 다중 문 테이블 반환 함수 또는 DML 트리거를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-146">In the **Scope object name** box, enter the name of the [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, user-defined scalar function, multistatement table-valued function, or DML trigger in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span> <span data-ttu-id="90485-147">**범위 개체 이름** 입력란은 **개체** 가 범위 유형으로 선택되어 있는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90485-147">The **Scope object name** box is only available when **Object** is selected as a scope type.</span></span>  
  
9. <span data-ttu-id="90485-148">**매개 변수** 입력란에 [!INCLUDE[tsql](../../includes/tsql-md.md)] 에 포함된 모든 매개 변수의 데이터 형식과 매개 변수 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-148">In the **Parameters** box, enter the parameter name and data type of all parameters that are embedded in the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
     <span data-ttu-id="90485-149">매개 변수는 다음 중 하나에 해당하는 경우에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="90485-149">Parameters apply only when either of the following is true:</span></span>  
  
    -   <span data-ttu-id="90485-150">범위 유형이 **SQL** 또는 **TEMPLATE**인 경우.</span><span class="sxs-lookup"><span data-stu-id="90485-150">The scope type is **SQL** or **TEMPLATE**.</span></span> <span data-ttu-id="90485-151">**TEMPLATE**일 경우 매개 변수는 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90485-151">If **TEMPLATE**, parameters must not be NULL.</span></span>  
  
    -   <span data-ttu-id="90485-152">sp_executesql을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 전송되고 매개 변수에 대한 값이 지정된 경우 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 문을 매개 변수화한 후에 내부에서 전송하는 경우.</span><span class="sxs-lookup"><span data-stu-id="90485-152">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is submitted by using sp_executesql and a value for the parameter is specified, or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] internally submits a statement after parameterizing it.</span></span>  
  
10. <span data-ttu-id="90485-153">**힌트** 입력란에 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에 적용되는 쿼리 힌트 또는 쿼리 계획을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-153">In the **Hints** box, enter the query hints or query plan to be applied to the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="90485-154">하나 이상의 쿼리 힌트를 지정하려면 유효한 OPTION 절을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-154">To specify one or more query hints, enter a valid OPTION clause.</span></span>  
  
11. <span data-ttu-id="90485-155">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-155">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="90485-156">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="90485-156">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-plan-guide"></a><span data-ttu-id="90485-157">계획 지침을 만들려면</span><span class="sxs-lookup"><span data-stu-id="90485-157">To create a plan guide</span></span>  
  
1.  <span data-ttu-id="90485-158">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-158">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="90485-159">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-159">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="90485-160">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90485-160">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- creates a plan guide named Guide1 based on a SQL statement  
    EXEC sp_create_plan_guide   
        @name = N'Guide1',   
        @stmt = N'SELECT TOP 1 *   
                  FROM Sales.SalesOrderHeader   
                  ORDER BY OrderDate DESC',   
        @type = N'SQL',  
        @module_or_batch = NULL,   
        @params = NULL,   
        @hints = N'OPTION (MAXDOP 1)';  
  
    ```  
  
 <span data-ttu-id="90485-161">자세한 내용은 [sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90485-161">For more information, see [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql).</span></span>  
  
  
