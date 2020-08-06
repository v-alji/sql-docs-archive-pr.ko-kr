---
title: 계획 지침 속성 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.planguideprop.general.f1
helpviewer_keywords:
- plan guides [SQL Server], view plan guide properties
- viewing plan guide properties
ms.assetid: 8c0d2f39-59c1-4168-a649-65473f6a771b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: af29c66690a43f89106c1f77aca8c3a02eff2ba9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731551"
---
# <a name="view-plan-guide-properties"></a><span data-ttu-id="4fdc9-102">계획 지침 속성 보기</span><span class="sxs-lookup"><span data-stu-id="4fdc9-102">View Plan Guide Properties</span></span>
  <span data-ttu-id="4fdc9-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 다음을 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 계획 지침의 속성을 확인할 수 있습니다. [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fdc9-103">You can view the properties of plan guides in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
 <span data-ttu-id="4fdc9-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="4fdc9-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4fdc9-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="4fdc9-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4fdc9-106">보안</span><span class="sxs-lookup"><span data-stu-id="4fdc9-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4fdc9-107">**계획 지침의 속성을 보려면:**</span><span class="sxs-lookup"><span data-stu-id="4fdc9-107">**To view the properties of plan guides, using:**</span></span>  
  
     [<span data-ttu-id="4fdc9-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4fdc9-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4fdc9-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4fdc9-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4fdc9-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="4fdc9-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4fdc9-111">보안</span><span class="sxs-lookup"><span data-stu-id="4fdc9-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4fdc9-112">권한</span><span class="sxs-lookup"><span data-stu-id="4fdc9-112">Permissions</span></span>  
 <span data-ttu-id="4fdc9-113">사용자가 소유하고 있거나 사용 권한을 부여 받은 보안 개체에 대해서만 카탈로그 뷰의 메타데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-113">The visibility of the metadata in catalog views is limited to securables that either a user owns or on which the user has been granted some permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4fdc9-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="4fdc9-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-properties-of-a-plan-guide"></a><span data-ttu-id="4fdc9-115">계획 지침의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="4fdc9-115">To view the properties of a plan guide</span></span>  
  
1.  <span data-ttu-id="4fdc9-116">더하기 기호를 클릭하여 계획 지침의 속성을 보려는 데이터베이스를 확장한 다음 더하기 기호를 클릭하여 **프로그래밍 기능** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-116">Click the plus sign to expand the database in which you want to view the properties of a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="4fdc9-117">더하기 기호를 클릭하여 **계획 지침** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-117">Click the plus sign to expand the **Plan Guides** folder.</span></span>  
  
3.  <span data-ttu-id="4fdc9-118">속성을 보려는 계획 지침을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-118">Right-click the plan guide of which you want to view the properties and select **Properties**.</span></span>  
  
     <span data-ttu-id="4fdc9-119">다음 속성이 **계획 지침 속성** 대화 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-119">The following properties show in the **Plan Guide Properties** dialog box.</span></span>  
  
     <span data-ttu-id="4fdc9-120">**힌트**</span><span class="sxs-lookup"><span data-stu-id="4fdc9-120">**Hints**</span></span>  
     <span data-ttu-id="4fdc9-121">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문에 적용되는 쿼리 힌트 또는 쿼리 계획을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-121">Displays the query hints or query plan to be applied to the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="4fdc9-122">쿼리 계획이 힌트로 지정되면 해당 계획의 XML 실행 계획 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-122">When a query plan is specified as a hint, the XML Showplan output for the plan is displayed.</span></span>  
  
     <span data-ttu-id="4fdc9-123">**사용 안 함**</span><span class="sxs-lookup"><span data-stu-id="4fdc9-123">**Is disabled**</span></span>  
     <span data-ttu-id="4fdc9-124">계획 지침의 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-124">Displays the status of the plan guide.</span></span> <span data-ttu-id="4fdc9-125">가능한 값은 **True** 및 **False**입니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-125">Possible values are **True** and **False**.</span></span>  
  
     <span data-ttu-id="4fdc9-126">**이름**</span><span class="sxs-lookup"><span data-stu-id="4fdc9-126">**Name**</span></span>  
     <span data-ttu-id="4fdc9-127">계획 지침의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-127">Displays the name of the plan guide.</span></span>  
  
     <span data-ttu-id="4fdc9-128">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="4fdc9-128">**Parameters**</span></span>  
     <span data-ttu-id="4fdc9-129">범위 유형이 SQL 또는 TEMPLATE인 경우 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에 포함된 모든 매개 변수의 데이터 형식과 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-129">When the scope type is SQL or TEMPLATE, displays the name and data type of all parameters that are embedded in the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
     <span data-ttu-id="4fdc9-130">**범위 일괄 처리**</span><span class="sxs-lookup"><span data-stu-id="4fdc9-130">**Scope batch**</span></span>  
     <span data-ttu-id="4fdc9-131">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 나타나는 일괄 처리 텍스트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-131">Displays the batch text in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span>  
  
     <span data-ttu-id="4fdc9-132">**범위 개체 이름**</span><span class="sxs-lookup"><span data-stu-id="4fdc9-132">**Scope object name**</span></span>  
     <span data-ttu-id="4fdc9-133">범위 유형이 OBJECT인 경우 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 나타나는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저의 이름, 사용자 정의 스칼라 함수, 다중 문 테이블 반환 함수 또는 DML 트리거를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-133">When the scope type is OBJECT, displays the name of the [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, user-defined scalar function, multistatement table-valued function, or DML trigger in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span>  
  
     <span data-ttu-id="4fdc9-134">**범위 스키마 이름**</span><span class="sxs-lookup"><span data-stu-id="4fdc9-134">**Scope schema name**</span></span>  
     <span data-ttu-id="4fdc9-135">범위 유형이 OBJECT인 경우 개체가 포함되는 스키마의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-135">When the scope type is OBJECT, displays the name of the schema in which the object is contained.</span></span>  
  
     <span data-ttu-id="4fdc9-136">**범위 유형**</span><span class="sxs-lookup"><span data-stu-id="4fdc9-136">**Scope type**</span></span>  
     <span data-ttu-id="4fdc9-137">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 나타나는 엔터티 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-137">Displays the type of entity in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span> <span data-ttu-id="4fdc9-138">이것은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 계획 지침과 일치시키기 위한 컨텍스트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-138">This specifies the context for matching the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to the plan guide.</span></span> <span data-ttu-id="4fdc9-139">가능한 값은 **OBJECT**, **SQL**및 **TEMPLATE**입니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-139">Possible values are **OBJECT**, **SQL**, and **TEMPLATE**.</span></span>  
  
     <span data-ttu-id="4fdc9-140">**문**</span><span class="sxs-lookup"><span data-stu-id="4fdc9-140">**Statement**</span></span>  
     <span data-ttu-id="4fdc9-141">계획 지침이 적용되는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-141">Displays the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement against which the plan guide is applied.</span></span>  
  
4.  <span data-ttu-id="4fdc9-142">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-142">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4fdc9-143">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="4fdc9-143">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-properties-of-a-plan-guide"></a><span data-ttu-id="4fdc9-144">계획 지침의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="4fdc9-144">To view the properties of a plan guide</span></span>  
  
1.  <span data-ttu-id="4fdc9-145">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-145">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4fdc9-146">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-146">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4fdc9-147">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-147">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- If a plan guide named "Guide1" already exists in the AdventureWorks2012 database, delete it.  
    USE AdventureWorks2012;  
    GO  
    IF OBJECT_ID(N'Guide1') IS NOT NULL  
       EXEC sp_control_plan_guide N'DROP', N'Guide1';  
    GO  
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
    GO  
    -- Gets the name, created date, and all other relevant property information on the plan guide created above.   
    SELECT name AS plan_guide_name,  
       create_date,  
       query_text,  
       scope_type_desc,  
       OBJECT_NAME(scope_object_id) AS scope_object_name,  
       scope_batch,  
       parameters,  
       hints,  
       is_disabled  
    FROM sys.plan_guides  
    WHERE name = N'Guide1';  
    GO  
    ```  
  
 <span data-ttu-id="4fdc9-148">자세한 내용은 [sys.plan_guides&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-plan-guides-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fdc9-148">For more information, see [sys.plan_guides &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-plan-guides-transact-sql).</span></span>  
  
  
