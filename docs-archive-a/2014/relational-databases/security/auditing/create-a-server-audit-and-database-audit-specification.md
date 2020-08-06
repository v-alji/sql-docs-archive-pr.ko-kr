---
title: 서버 감사 및 데이터베이스 감사 사양 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlaudit.dbaudit.general.f1
helpviewer_keywords:
- audits [SQL Server], creating database specification
- database audit [SQL Server]
ms.assetid: 26ee85de-6e97-4318-b526-900924d96e62
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0cad01eae45d534f0f74911ce8f57827858cc920
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732519"
---
# <a name="create-a-server-audit-and-database-audit-specification"></a><span data-ttu-id="6e75c-102">서버 감사 및 데이터베이스 감사 사양 만들기</span><span class="sxs-lookup"><span data-stu-id="6e75c-102">Create a Server Audit and Database Audit Specification</span></span>
  <span data-ttu-id="6e75c-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 서버 감사 및 데이터베이스 감사 사양을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-103">This topic describes how to create a server audit and database audit specification in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="6e75c-104">*인스턴스 또는* 데이터베이스 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 감사 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에는 시스템에서 발생하는 추적 이벤트 및 로깅 이벤트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-104">*Auditing* an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database involves tracking and logging events that occur on the system.</span></span> <span data-ttu-id="6e75c-105">*SQL Server Audit* 개체는 사용자가 모니터링하려는 서버 또는 데이터베이스 수준 동작 및 동작 그룹에 대한 하나의 인스턴스를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-105">The *SQL Server Audit* object collects a single instance of server- or database-level actions and groups of actions to monitor.</span></span> <span data-ttu-id="6e75c-106">감사는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스 수준으로 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-106">The audit is at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance level.</span></span> <span data-ttu-id="6e75c-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스별로 여러 개의 감사를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-107">You can have multiple audits per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="6e75c-108">*데이터베이스 수준 감사 사양* 개체는 감사에 속해 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-108">The *Database-Level Audit Specification* object belongs to an audit.</span></span> <span data-ttu-id="6e75c-109">감사의 SQL Server 데이터베이스당 하나의 데이터베이스 감사 사양을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-109">You can create one database audit specification per SQL Server database per audit.</span></span> <span data-ttu-id="6e75c-110">자세한 내용은 [SQL Server Audit&#40;데이터베이스 엔진&#41;](sql-server-audit-database-engine.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e75c-110">For more information, see [SQL Server Audit &#40;Database Engine&#41;](sql-server-audit-database-engine.md).</span></span>  
  
 <span data-ttu-id="6e75c-111">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="6e75c-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6e75c-112">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="6e75c-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6e75c-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="6e75c-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="6e75c-114">보안</span><span class="sxs-lookup"><span data-stu-id="6e75c-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6e75c-115">**서버 감사 및 데이터베이스 감사 사양을 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="6e75c-115">**To create a server audit and database audit specification, using:**</span></span>  
  
     [<span data-ttu-id="6e75c-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6e75c-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6e75c-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6e75c-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6e75c-118">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="6e75c-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6e75c-119">제한 사항</span><span class="sxs-lookup"><span data-stu-id="6e75c-119">Limitations and Restrictions</span></span>  
 <span data-ttu-id="6e75c-120">데이터베이스 감사 사양은 지정된 데이터베이스에 있는 비보안 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-120">Database audit specifications are non-securable objects that reside in a given database.</span></span> <span data-ttu-id="6e75c-121">데이터베이스 감사 사양을 처음 만들 때는 사용할 수 없는 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-121">When a database audit specification is created, it is in a disabled state.</span></span>  
  
 <span data-ttu-id="6e75c-122">사용자 데이터베이스에 데이터베이스 감사 사양을 만들거나 사양을 수정할 때 시스템 뷰와 같은 서버 범위 개체에 대한 감사 동작은 포함하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="6e75c-122">When you are creating or modifying a database audit specification in a user database, do not include audit actions on server-scope objects, such as the system views.</span></span> <span data-ttu-id="6e75c-123">서버 범위 개체를 포함하더라도 감사가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-123">If server-scoped objects are included, the audit will be created.</span></span> <span data-ttu-id="6e75c-124">그러나 서버 범위 개체가 포함되지는 않으며 별도의 오류도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-124">However, the server-scoped objects will not be included, and no error will be returned.</span></span> <span data-ttu-id="6e75c-125">서버 범위 개체를 감사하려면 master 데이터베이스의 데이터베이스 감사 사양을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-125">To audit server-scope objects, use a database audit specification in the master database.</span></span>  
  
 <span data-ttu-id="6e75c-126">데이터베이스 감사 사양은 해당 사양이 생성된 데이터베이스 내에 있습니다(`tempdb` 시스템 데이터베이스 제외).</span><span class="sxs-lookup"><span data-stu-id="6e75c-126">Database audit specifications reside in the database where they are created, with the exception of the `tempdb` system database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6e75c-127">보안</span><span class="sxs-lookup"><span data-stu-id="6e75c-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6e75c-128">권한</span><span class="sxs-lookup"><span data-stu-id="6e75c-128">Permissions</span></span>  
  
-   <span data-ttu-id="6e75c-129">ALTER ANY DATABASE AUDIT 권한이 있는 사용자는 데이터베이스 감사 사양을 만들어 모든 감사에 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-129">Users with the ALTER ANY DATABASE AUDIT permission can create database audit specifications and bind them to any audit.</span></span>  
  
-   <span data-ttu-id="6e75c-130">생성된 데이터베이스 감사 사양은 CONTROL SERVER, ALTER ANY DATABASE AUDIT 권한이 있는 보안 주체나 sysadmin 계정이 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-130">After a database audit specification is created, it can be viewed by principals with the CONTROL SERVER,  ALTER ANY DATABASE AUDIT permissions, or the sysadmin account.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6e75c-131">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="6e75c-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-server-audit"></a><span data-ttu-id="6e75c-132">서버 감사를 만들려면</span><span class="sxs-lookup"><span data-stu-id="6e75c-132">To create a server audit</span></span>  
  
1.  <span data-ttu-id="6e75c-133">개체 탐색기에서 **보안** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-133">In Object Explorer, expand the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="6e75c-134">**감사** 폴더를 마우스 오른쪽 단추로 클릭 하 고 **새 감사 ...** 를 선택 합니다. 자세한 내용은 [서버 감사 및 서버 감사 사양 만들기](create-a-server-audit-and-server-audit-specification.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e75c-134">Right-click the **Audits** folder and select **New Audit...**. For more information, see [Create a Server Audit and Server Audit Specification](create-a-server-audit-and-server-audit-specification.md).</span></span>  
  
3.  <span data-ttu-id="6e75c-135">옵션 선택을 마쳤으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-135">When you are finished selecting options, click **OK**.</span></span>  
  
#### <a name="to-create-a-database-level-audit-specification"></a><span data-ttu-id="6e75c-136">데이터베이스 수준 감사 사양을 만들려면</span><span class="sxs-lookup"><span data-stu-id="6e75c-136">To create a database-level audit specification</span></span>  
  
1.  <span data-ttu-id="6e75c-137">개체 탐색기에서 감사 사양을 만들 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-137">In Object Explorer, expand the database where you want to create an audit specification.</span></span>  
  
2.  <span data-ttu-id="6e75c-138">**보안** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-138">Expand the **Security** folder.</span></span>  
  
3.  <span data-ttu-id="6e75c-139">**데이터베이스 감사 사양** 폴더를 마우스 오른쪽 단추로 클릭 하 고 **새 데이터베이스 감사 사양 ...** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-139">Right-click the **Database Audit Specifications** folder and select **New Database Audit Specification...**.</span></span>  
  
     <span data-ttu-id="6e75c-140">**데이터베이스 감사 사양 만들기** 대화 상자에는 다음과 같은 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-140">The following options are available on the **Create Database Audit Specification** dialog box.</span></span>  
  
     <span data-ttu-id="6e75c-141">**이름**</span><span class="sxs-lookup"><span data-stu-id="6e75c-141">**Name**</span></span>  
     <span data-ttu-id="6e75c-142">데이터베이스 감사 사양의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-142">The name of the database audit specification.</span></span> <span data-ttu-id="6e75c-143">새 서버 감사 사양을 만들 때 자동 생성되지만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-143">This is generated automatically when you create a new server audit specification but is editable.</span></span>  
  
     <span data-ttu-id="6e75c-144">**감사**</span><span class="sxs-lookup"><span data-stu-id="6e75c-144">**Audit**</span></span>  
     <span data-ttu-id="6e75c-145">기존 데이터베이스 감사의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-145">The name of an existing database audit.</span></span> <span data-ttu-id="6e75c-146">감사 이름을 입력하거나 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-146">Either type in the name of the audit or select it from the list.</span></span>  
  
     <span data-ttu-id="6e75c-147">**감사 동작 유형**</span><span class="sxs-lookup"><span data-stu-id="6e75c-147">**Audit Action Type**</span></span>  
     <span data-ttu-id="6e75c-148">캡처할 데이터베이스 수준 감사 동작 그룹 및 감사 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-148">Specifies the database-level audit action groups and audit actions to capture.</span></span> <span data-ttu-id="6e75c-149">데이터베이스 수준 감사 동작 그룹 및 감사 동작의 목록과 여기에 포함된 이벤트에 대한 설명은 [SQL Server Audit 동작 그룹 및 동작](sql-server-audit-action-groups-and-actions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e75c-149">For the list of database-level audit action groups and audit actions and a description of the events they contain, see [SQL Server Audit Action Groups and Actions](sql-server-audit-action-groups-and-actions.md).</span></span>  
  
     <span data-ttu-id="6e75c-150">**개체 스키마**</span><span class="sxs-lookup"><span data-stu-id="6e75c-150">**Object Schema**</span></span>  
     <span data-ttu-id="6e75c-151">지정된 **개체 이름**에 대한 스키마를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-151">Displays the schema for the specified **Object Name**.</span></span>  
  
     <span data-ttu-id="6e75c-152">**개체 이름**</span><span class="sxs-lookup"><span data-stu-id="6e75c-152">**Object Name**</span></span>  
     <span data-ttu-id="6e75c-153">감사할 개체의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-153">The name of the object to audit.</span></span> <span data-ttu-id="6e75c-154">이 이름은 감사 동작에만 사용할 수 있으며 감사 그룹에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-154">This is only available for audit actions; it does not apply to audit groups.</span></span>  
  
     <span data-ttu-id="6e75c-155">**줄임표(...)**</span><span class="sxs-lookup"><span data-stu-id="6e75c-155">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="6e75c-156">**개체 선택** 대화 상자를 열고 지정된 **감사 동작 유형**에 따라 사용 가능한 개체를 찾아 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-156">Opens the **Select Objects** dialog to browse for and select an available object, based on the specified **Audit Action Type**.</span></span>  
  
     <span data-ttu-id="6e75c-157">**보안 주체 이름**</span><span class="sxs-lookup"><span data-stu-id="6e75c-157">**Principal Name**</span></span>  
     <span data-ttu-id="6e75c-158">감사 중인 개체에 대한 감사 필터링의 기준이 되는 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-158">The account to filter the audit by for the object being audited.</span></span>  
  
     <span data-ttu-id="6e75c-159">**줄임표(...)**</span><span class="sxs-lookup"><span data-stu-id="6e75c-159">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="6e75c-160">**개체 선택** 대화 상자를 열고 지정된 **개체 이름**에 따라 사용 가능한 개체를 찾아 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-160">Opens the **Select Objects** dialog to browse for and select an available object, based on the specified **Object Name**.</span></span>  
  
4.  <span data-ttu-id="6e75c-161">옵션 선택을 마쳤으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-161">When you are finished selecting option, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6e75c-162">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="6e75c-162">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-server-audit"></a><span data-ttu-id="6e75c-163">서버 감사를 만들려면</span><span class="sxs-lookup"><span data-stu-id="6e75c-163">To create a server audit</span></span>  
  
1.  <span data-ttu-id="6e75c-164">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-164">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6e75c-165">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-165">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6e75c-166">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-166">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE master ;  
    GO  
    -- Create the server audit.   
    CREATE SERVER AUDIT Payrole_Security_Audit  
        TO FILE ( FILEPATH =   
    'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA' ) ;   
    GO  
    -- Enable the server audit.   
    ALTER SERVER AUDIT Payrole_Security_Audit   
    WITH (STATE = ON) ;  
    ```  
  
#### <a name="to-create-a-database-level-audit-specification"></a><span data-ttu-id="6e75c-167">데이터베이스 수준 감사 사양을 만들려면</span><span class="sxs-lookup"><span data-stu-id="6e75c-167">To create a database-level audit specification</span></span>  
  
1.  <span data-ttu-id="6e75c-168">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-168">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6e75c-169">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-169">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6e75c-170">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-170">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6e75c-171">이 예에서는 위에 정의된 서버 감사를 기반으로 `Audit_Pay_Tables` 테이블에 대해 `dbo` 사용자가 SELECT 및 INSERT 문을 감사하는 `HumanResources.EmployeePayHistory` 이라는 데이터베이스 감사 사양을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6e75c-171">The example creates a database audit specification called `Audit_Pay_Tables` that audits SELECT and INSERT statements by the `dbo` user, for the `HumanResources.EmployeePayHistory` table based on the server audit defined above.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    -- Create the database audit specification.   
    CREATE DATABASE AUDIT SPECIFICATION Audit_Pay_Tables  
    FOR SERVER AUDIT Payrole_Security_Audit  
    ADD (SELECT , INSERT  
         ON HumanResources.EmployeePayHistory BY dbo )   
    WITH (STATE = ON) ;   
    GO  
  
    ```  
  
 <span data-ttu-id="6e75c-172">자세한 내용은 [CREATE SERVER AUDIT&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql) 및 [CREATE DATABASE AUDIT SPECIFICATION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-audit-specification-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e75c-172">For more information, see [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql) and [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-audit-specification-transact-sql).</span></span>  
  
  
