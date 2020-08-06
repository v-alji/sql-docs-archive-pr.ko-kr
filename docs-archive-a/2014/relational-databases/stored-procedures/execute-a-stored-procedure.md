---
title: 저장 프로시저 실행 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.executeprocedure.f1
- sql12.swb.executeprocedure.general.f1
helpviewer_keywords:
- stored procedures [SQL Server], parameters
- extended stored procedures [SQL Server], executing
- system stored procedures [SQL Server], executing
- stored procedures [SQL Server], executing
- user-defined stored procedures [SQL Server]
ms.assetid: a0b1337d-2059-4872-8c62-3f967d8b170f
author: stevestein
ms.author: sstein
ms.openlocfilehash: c679ba7af3ac9f60d312b33c0346e50687387476
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659867"
---
# <a name="execute-a-stored-procedure"></a><span data-ttu-id="d4dbb-102">저장 프로시저 실행</span><span class="sxs-lookup"><span data-stu-id="d4dbb-102">Execute a Stored Procedure</span></span>
  <span data-ttu-id="d4dbb-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 저장 프로시저를 실행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-103">This topic describes how to execute a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="d4dbb-104">두 가지 방법으로 저장 프로시저를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-104">There are two different ways to execute a stored procedure.</span></span> <span data-ttu-id="d4dbb-105">가장 일반적인 첫 번째 방법은 애플리케이션 또는 사용자가 프로시저를 호출하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-105">The first and most common approach is for an application or user to call the procedure.</span></span> <span data-ttu-id="d4dbb-106">두 번째 방법은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 시작될 때 자동 실행되도록 프로시저를 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-106">The second approach is to set the procedure to run automatically when an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] starts.</span></span> <span data-ttu-id="d4dbb-107">애플리케이션이나 사용자가 프로시저를 호출할 때 [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE 또는 EXEC 키워드가 호출에서 명시적으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-107">When a procedure is called by an application or user, the [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE or EXEC keyword is explicitly stated in the call.</span></span> <span data-ttu-id="d4dbb-108">또는 프로시저가 [!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리의 첫 번째 문이면 키워드를 사용하지 않고 프로시저를 호출하고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-108">Alternatively, the procedure can be called and executed without the keyword if the procedure is the first statement in the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch.</span></span>  
  
 <span data-ttu-id="d4dbb-109">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="d4dbb-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d4dbb-110">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="d4dbb-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d4dbb-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d4dbb-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d4dbb-112">권장 사항</span><span class="sxs-lookup"><span data-stu-id="d4dbb-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="d4dbb-113">보안</span><span class="sxs-lookup"><span data-stu-id="d4dbb-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d4dbb-114">**저장 프로시저를 실행하려면:**</span><span class="sxs-lookup"><span data-stu-id="d4dbb-114">**To execute a stored procedure, using:**</span></span>  
  
     [<span data-ttu-id="d4dbb-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d4dbb-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d4dbb-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d4dbb-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d4dbb-117">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d4dbb-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d4dbb-118">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d4dbb-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="d4dbb-119">시스템 프로시저 이름을 일치시킬 때 호출 데이터베이스 데이터 정렬이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-119">The calling database collation is used when matching system procedure names.</span></span> <span data-ttu-id="d4dbb-120">따라서 프로시저 호출에서 대/소문자를 구분하여 시스템 프로시저 이름을 항상 정확하게 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-120">Therefore, always use the exact case of system procedure names in procedure calls.</span></span> <span data-ttu-id="d4dbb-121">예를 들어 다음 코드는 대/소문자를 구분하는 데이터 정렬을 사용하는 데이터베이스 컨텍스트에서 실행할 경우 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-121">For example, this code will fail if it is executed in the context of a database that has a case-sensitive collation:</span></span>  
  
    ```sql  
    EXEC SP_heLP; -- Will fail to resolve because SP_heLP does not equal sp_help  
    ```  
  
     <span data-ttu-id="d4dbb-122">정확한 시스템 프로시저 이름을 표시하려면 [sys.system_objects](/sql/relational-databases/system-catalog-views/sys-system-objects-transact-sql) 및 [sys.system_parameters](/sql/relational-databases/system-catalog-views/sys-system-parameters-transact-sql) 카탈로그 뷰를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-122">To display the exact system procedure names, query the [sys.system_objects](/sql/relational-databases/system-catalog-views/sys-system-objects-transact-sql) and [sys.system_parameters](/sql/relational-databases/system-catalog-views/sys-system-parameters-transact-sql) catalog views.</span></span>  
  
-   <span data-ttu-id="d4dbb-123">사용자 정의 프로시저의 이름이 시스템 프로시저의 이름과 같으면 사용자 정의 프로시저가 실행되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-123">If a user-defined procedure has the same name as a system procedure, the user-defined procedure might not ever execute.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="d4dbb-124">권장 사항</span><span class="sxs-lookup"><span data-stu-id="d4dbb-124">Recommendations</span></span>  
  
-   <span data-ttu-id="d4dbb-125">시스템 저장 프로시저 실행</span><span class="sxs-lookup"><span data-stu-id="d4dbb-125">Executing System Stored Procedures</span></span>  
  
     <span data-ttu-id="d4dbb-126">시스템 프로시저는 접두사 **sp_** 로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-126">System procedures begin with the prefix **sp_**.</span></span> <span data-ttu-id="d4dbb-127">시스템 프로시저는 모든 사용자 정의 데이터베이스와 시스템 정의 데이터베이스에 논리적으로 나타나기 때문에 프로시저 이름을 완전히 한정하지 않고도 모든 데이터베이스에서 시스템 프로시저를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-127">Because they logically appear in all user- and system- defined databases, they can be executed from any database without having to fully quality the procedure name.</span></span> <span data-ttu-id="d4dbb-128">그러나 이름 충돌이 발생하지 않도록 **sys** 스키마 이름으로 모든 시스템 프로시저 이름을 스키마로 한정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-128">However, we recommend schema-qualifying all system procedure names with the **sys** schema name to prevent name conflicts.</span></span> <span data-ttu-id="d4dbb-129">다음 예에서는 권장되는 시스템 프로시저 호출 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-129">The following example demonstrates the recommended method of calling a system procedure.</span></span>  
  
    ```sql  
    EXEC sys.sp_who;  
    ```  
  
-   <span data-ttu-id="d4dbb-130">사용자 정의 저장 프로시저 실행</span><span class="sxs-lookup"><span data-stu-id="d4dbb-130">Executing User-defined Stored Procedures</span></span>  
  
     <span data-ttu-id="d4dbb-131">사용자 정의 프로시저를 실행할 때 프로시저 이름을 스키마 이름으로 한정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-131">When executing a user-defined procedure, we recommend qualifying the procedure name with the schema name.</span></span> <span data-ttu-id="d4dbb-132">이렇게 하면 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 에서 여러 스키마를 검색할 필요가 없기 때문에 성능이 약간 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-132">This practice gives a small performance boost because the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] does not have to search multiple schemas.</span></span> <span data-ttu-id="d4dbb-133">또한 데이터베이스에 여러 스키마에서 이름이 동일한 프로시저가 있는 경우 잘못된 프로시저를 실행하는 문제가 방지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-133">It also prevents executing the wrong procedure if a database has procedures with the same name in multiple schemas.</span></span>  
  
     <span data-ttu-id="d4dbb-134">다음 예에서는 권장되는 사용자 정의 프로시저 실행 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-134">The following example demonstrates the recommended method to execute a user-defined procedure.</span></span> <span data-ttu-id="d4dbb-135">프로시저는 하나의 입력 매개 변수를 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-135">Notice that the procedure accepts one input parameter.</span></span> <span data-ttu-id="d4dbb-136">입력 및 출력 매개 변수를 지정하는 방법은 [매개 변수 지정](specify-parameters.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-136">For information about specifying input and output parameters, see [Specify Parameters](specify-parameters.md).</span></span>  
  
    ```sql  
    USE AdventureWorks2012;  
    GO  
    EXEC dbo.uspGetEmployeeManagers @BusinessEntityID = 50;  
    ```  
  
     <span data-ttu-id="d4dbb-137">-또는-</span><span class="sxs-lookup"><span data-stu-id="d4dbb-137">-Or-</span></span>  
  
    ```sql  
    EXEC AdventureWorks2012.dbo.uspGetEmployeeManagers 50;  
    GO  
    ```  
  
     <span data-ttu-id="d4dbb-138">정규화되지 않은 사용자 정의 프로시저를 지정하면 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 은 다음 순서로 프로시저를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-138">If a nonqualified user-defined procedure is specified, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] searches for the procedure in the following order:</span></span>  
  
    1.  <span data-ttu-id="d4dbb-139">현재 데이터베이스의 **sys** 스키마</span><span class="sxs-lookup"><span data-stu-id="d4dbb-139">The **sys** schema of the current database.</span></span>  
  
    2.  <span data-ttu-id="d4dbb-140">일괄 처리나 동적 SQL에서 실행된 경우 호출자의 기본 스키마.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-140">The caller's default schema if it is executed in a batch or in dynamic SQL.</span></span> <span data-ttu-id="d4dbb-141">또는 다른 프로시저 정의 본문에 한정되지 않은 프로시저 이름이 있는 경우 이 다른 프로시저를 포함하는 스키마가 다음으로 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-141">Or, if the nonqualified procedure name appears inside the body of another procedure definition, the schema that contains this other procedure is searched next.</span></span>  
  
    3.  <span data-ttu-id="d4dbb-142">현재 데이터베이스의 **dbo** 스키마</span><span class="sxs-lookup"><span data-stu-id="d4dbb-142">The **dbo** schema in the current database.</span></span>  
  
-   <span data-ttu-id="d4dbb-143">저장 프로시저 자동 실행</span><span class="sxs-lookup"><span data-stu-id="d4dbb-143">Executing Stored Procedures Automatically</span></span>  
  
     <span data-ttu-id="d4dbb-144">자동 실행되도록 표시된 프로시저는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 시작될 때마다 실행되며 **master** 데이터베이스는 이 시작 프로세스 중에 복구됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-144">Procedures marked for automatic execution are executed every time [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] starts and the **master** database is recovered during that startup process.</span></span> <span data-ttu-id="d4dbb-145">자동 실행되도록 프로시저를 설정하면 데이터베이스 유지 관리 작업을 수행하거나 프로시저가 백그라운드 프로세스로 계속 실행되도록 하는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-145">Setting up procedures to execute automatically can be useful for performing database maintenance operations or for having procedures run continuously as background processes.</span></span> <span data-ttu-id="d4dbb-146">또는 프로시저가 전역 임시 테이블을 만드는 작업처럼 **tempdb**에서 시스템 또는 유지 관리 태스크를 수행하도록 하는 것이 자동 실행을 사용하는 또 다른 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-146">Another use for automatic execution is to have the procedure perform system or maintenance tasks in **tempdb**, such as creating a global temporary table.</span></span> <span data-ttu-id="d4dbb-147">이렇게 하면 **시작 중에** tempdb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 다시 만들어질 때 이러한 임시 테이블이 항상 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-147">This makes sure that such a temporary table will always exist when **tempdb** is re-created during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup.</span></span>  
  
     <span data-ttu-id="d4dbb-148">자동 실행되는 프로시저는 **sysadmin** 고정 서버 역할의 멤버와 같은 권한을 사용하여 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-148">A procedure that is automatically executed operates with the same permissions as members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="d4dbb-149">프로시저에서 생성되는 오류 메시지는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-149">Any error messages generated by the procedure are written to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>  
  
     <span data-ttu-id="d4dbb-150">시작 프로시저의 개수에는 제한이 없지만 각 시작 프로시저는 실행하는 동안 하나의 작업자 스레드를 소비합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-150">There is no limit to the number of startup procedures you can have, but be aware that each consumes one worker thread while executing.</span></span> <span data-ttu-id="d4dbb-151">따라서 시작할 때 여러 프로시저를 실행해야 하지만 동시에 실행할 필요가 없다면 한 프로시저만 시작 프로시저로 지정하고 그 프로시저에서 다른 프로시저를 호출하도록 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-151">If you must execute multiple procedures at startup but do not need to execute them in parallel, make one procedure the startup procedure and have that procedure call the other procedures.</span></span> <span data-ttu-id="d4dbb-152">이렇게 하면 하나의 작업자 스레드만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-152">This uses only one worker thread.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="d4dbb-153">자동 실행되는 프로시저의 결과 집합은 반환하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-153">Do not return any result sets from a procedure that is executed automatically.</span></span> <span data-ttu-id="d4dbb-154">프로시저는 애플리케이션이나 사용자가 아닌 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 의해 실행되므로 결과 집합을 반환할 대상이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-154">Because the procedure is being executed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instead of an application or user, there is nowhere for the result sets to go.</span></span>  
  
-   <span data-ttu-id="d4dbb-155">자동 실행 설정, 해제 및 제어</span><span class="sxs-lookup"><span data-stu-id="d4dbb-155">Setting, Clearing, and Controlling Automatic Execution</span></span>  
  
     <span data-ttu-id="d4dbb-156">시스템 관리자(**sa**)만 프로시저가 자동 실행되도록 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-156">Only the system administrator (**sa**) can mark a procedure to execute automatically.</span></span> <span data-ttu-id="d4dbb-157">또한 프로시저는 **master** 데이터베이스에 있고 **sa**에 의해 소유되어야 하며 입력 또는 출력 매개 변수를 가질 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-157">In addition, the procedure must be in the **master** database, owned by **sa**, and cannot have input or output parameters.</span></span>  
  
     <span data-ttu-id="d4dbb-158">[sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) 을 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-158">Use [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) to:</span></span>  
  
    1.  <span data-ttu-id="d4dbb-159">기존 프로시저를 시작 프로시저로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-159">Designate an existing procedure as a startup procedure.</span></span>  
  
    2.  <span data-ttu-id="d4dbb-160">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 시작할 때 프로시저가 실행되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-160">Stop a procedure from executing at [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d4dbb-161">보안</span><span class="sxs-lookup"><span data-stu-id="d4dbb-161">Security</span></span>  
 <span data-ttu-id="d4dbb-162">자세한 내용은 [EXECUTE AS&#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-transact-sql) 및 [EXECUTE AS 절&#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-162">For more information, see [EXECUTE AS &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-transact-sql) and [EXECUTE AS Clause &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d4dbb-163">권한</span><span class="sxs-lookup"><span data-stu-id="d4dbb-163">Permissions</span></span>  
 <span data-ttu-id="d4dbb-164">자세한 내용은 [EXECUTE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql)을 사용하여 저장 프로시저를 실행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-164">For more information, see the "Permissions" section in [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d4dbb-165">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="d4dbb-165">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-execute-a-stored-procedure"></a><span data-ttu-id="d4dbb-166">저장 프로시저를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="d4dbb-166">To execute a stored procedure</span></span>  
  
1.  <span data-ttu-id="d4dbb-167">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결하고 해당 인스턴스를 확장한 다음 **데이터베이스**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-167">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="d4dbb-168">원하는 데이터베이스를 확장하고 **프로그래밍 기능**을 확장한 다음 **저장 프로시저**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-168">Expand the database that you want, expand **Programmability**, and then expand **Stored Procedures**.</span></span>  
  
3.  <span data-ttu-id="d4dbb-169">원하는 사용자 정의 저장 프로시저를 마우스 오른쪽 단추로 클릭하고 **저장 프로시저 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-169">Right-click the user-defined stored procedure that you want and click **Execute Stored Procedure**.</span></span>  
  
4.  <span data-ttu-id="d4dbb-170">**프로시저 실행** 대화 상자에서 각 매개 변수의 값과 null 값을 전달해야 하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-170">In the **Execute Procedure** dialog box, specify a value for each parameter and whether it should pass a null value.</span></span>  
  
     <span data-ttu-id="d4dbb-171">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="d4dbb-171">**Parameter**</span></span>  
     <span data-ttu-id="d4dbb-172">매개 변수의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-172">Indicates the name of the parameter.</span></span>  
  
     <span data-ttu-id="d4dbb-173">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="d4dbb-173">**Data Type**</span></span>  
     <span data-ttu-id="d4dbb-174">매개 변수의 데이터 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-174">Indicates the data type of the parameter.</span></span>  
  
     <span data-ttu-id="d4dbb-175">**출력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="d4dbb-175">**Output Parameter**</span></span>  
     <span data-ttu-id="d4dbb-176">매개 변수가 출력 매개 변수인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-176">Indicates if this is an output parameter.</span></span>  
  
     <span data-ttu-id="d4dbb-177">**Null 값 전달**</span><span class="sxs-lookup"><span data-stu-id="d4dbb-177">**Pass Null Value**</span></span>  
     <span data-ttu-id="d4dbb-178">매개 변수의 값으로 NULL 값을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-178">Pass a NULL as the value of the parameter.</span></span>  
  
     <span data-ttu-id="d4dbb-179">**값**</span><span class="sxs-lookup"><span data-stu-id="d4dbb-179">**Value**</span></span>  
     <span data-ttu-id="d4dbb-180">프로시저를 호출할 때 매개 변수의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-180">Type the value for the parameter when calling the procedure.</span></span>  
  
5.  <span data-ttu-id="d4dbb-181">저장 프로시저를 실행하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-181">To execute the stored procedure, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d4dbb-182">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="d4dbb-182">Using Transact-SQL</span></span>  
  
#### <a name="to-execute-a-stored-procedure"></a><span data-ttu-id="d4dbb-183">저장 프로시저를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="d4dbb-183">To execute a stored procedure</span></span>  
  
1.  <span data-ttu-id="d4dbb-184">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-184">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d4dbb-185">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-185">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d4dbb-186">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-186">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d4dbb-187">이 예에서는 하나의 매개 변수를 예상하는 저장 프로시저를 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-187">This example shows how to execute a stored procedure that expects one parameter.</span></span> <span data-ttu-id="d4dbb-188">또한 `uspGetEmployeeManagers` 매개 변수로 지정된 값인  `6` 을 사용하여 `@EmployeeID` 저장 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-188">The example executes the `uspGetEmployeeManagers` stored procedure with the value  `6` specified as the `@EmployeeID` parameter.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC dbo.uspGetEmployeeManagers 6;  
GO  
```  
  
#### <a name="to-set-or-clear-a-procedure-for-executing-automatically"></a><span data-ttu-id="d4dbb-189">자동 실행되도록 프로시저를 설정하거나 해제하려면</span><span class="sxs-lookup"><span data-stu-id="d4dbb-189">To set or clear a procedure for executing automatically</span></span>  
  
1.  <span data-ttu-id="d4dbb-190">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-190">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d4dbb-191">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-191">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d4dbb-192">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-192">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d4dbb-193">이 예에서는 [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) 을 사용하여 자동 실행되도록 프로시저를 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-193">This example shows how to use [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) to set a procedure for automatic execution.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionName = ] 'startup'   
    , @OptionValue = 'on';  
```  
  
#### <a name="to-stop-a-procedure-from-executing-automatically"></a><span data-ttu-id="d4dbb-194">프로시저가 자동 실행되는 것을 중지하려면</span><span class="sxs-lookup"><span data-stu-id="d4dbb-194">To stop a procedure from executing automatically</span></span>  
  
1.  <span data-ttu-id="d4dbb-195">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-195">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d4dbb-196">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-196">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d4dbb-197">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-197">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d4dbb-198">이 예에서는 [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) 을 사용하여 프로시저가 자동 실행되는 것을 중지하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4dbb-198">This example shows how to use [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) to stop a procedure from executing automatically.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionValue = 'off';  
```  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="d4dbb-199">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d4dbb-199">Example (Transact-SQL)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4dbb-200">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4dbb-200">See Also</span></span>  
 <span data-ttu-id="d4dbb-201">[매개 변수 지정](specify-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="d4dbb-201">[Specify Parameters](specify-parameters.md) </span></span>  
 <span data-ttu-id="d4dbb-202">[scan for startup procs 서버 구성 옵션 구성](../../database-engine/configure-windows/configure-the-scan-for-startup-procs-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="d4dbb-202">[Configure the scan for startup procs Server Configuration Option](../../database-engine/configure-windows/configure-the-scan-for-startup-procs-server-configuration-option.md) </span></span>  
 <span data-ttu-id="d4dbb-203">[EXECUTE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d4dbb-203">[EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql) </span></span>  
 <span data-ttu-id="d4dbb-204">[CREATE PROCEDURE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d4dbb-204">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span></span>  
 [<span data-ttu-id="d4dbb-205">저장 프로시저&#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="d4dbb-205">Stored Procedures &#40;Database Engine&#41;</span></span>](stored-procedures-database-engine.md)  
  
  
