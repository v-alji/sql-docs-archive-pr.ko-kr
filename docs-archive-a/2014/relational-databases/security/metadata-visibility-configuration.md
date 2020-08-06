---
title: 메타데이터 표시 유형 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- subcomponents visibility [SQL Server]
- metadata [SQL Server], visibility
- permissions [SQL Server], metadata access
- viewing metadata
- objects [SQL Server], metadata
- displaying metadata
- database metadata [SQL Server]
- metadata [SQL Server], permissions
ms.assetid: 50d2e015-05ae-4014-a1cd-4de7866ad651
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 5198dc4ba4e81bc1d7a8dd2411da59da81596102
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651604"
---
# <a name="metadata-visibility-configuration"></a><span data-ttu-id="6661b-102">메타데이터 표시 유형 구성</span><span class="sxs-lookup"><span data-stu-id="6661b-102">Metadata Visibility Configuration</span></span>
  <span data-ttu-id="6661b-103">사용자가 소유하고 있거나 일부 사용 권한이 부여된 보안 개체에 대해서만 메타데이터를 볼 수 있도록 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-103">The visibility of metadata is limited to securables that a user either owns or on which the user has been granted some permission.</span></span> <span data-ttu-id="6661b-104">예를 들어 다음 쿼리는 사용자에게 `myTable`테이블에 대한 SELECT 또는 INSERT와 같은 권한을 부여한 경우에 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-104">For example, the following query returns a row if the user has been granted a permission such as SELECT or INSERT on the table `myTable`.</span></span>  
  
```  
SELECT name, object_id  
FROM sys.tables  
WHERE name = 'myTable';  
GO  
```  
  
 <span data-ttu-id="6661b-105">하지만 사용자에게 `myTable`에 대한 사용 권한이 없으면 쿼리가 빈 결과 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-105">However, if the user does not have any permission on `myTable`, the query returns an empty result set.</span></span>  
  
## <a name="scope-and-impact-of-metadata-visibility-configuration"></a><span data-ttu-id="6661b-106">메타데이터 표시 유형 범위 및 영향 구성</span><span class="sxs-lookup"><span data-stu-id="6661b-106">Scope and Impact of Metadata Visibility Configuration</span></span>  
 <span data-ttu-id="6661b-107">메타데이터 표시 유형 구성은 다음 보안 개체에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-107">Metadata visibility configuration only applies to the following securables.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6661b-108">카탈로그 뷰</span><span class="sxs-lookup"><span data-stu-id="6661b-108">Catalog views</span></span>|[!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="6661b-109">**sp_help** 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="6661b-109">**sp_help** stored procedures</span></span>|  
|<span data-ttu-id="6661b-110">메타데이터를 제공하는 기본 제공 함수</span><span class="sxs-lookup"><span data-stu-id="6661b-110">Metadata exposing built-in functions</span></span>|<span data-ttu-id="6661b-111">정보 스키마 뷰</span><span class="sxs-lookup"><span data-stu-id="6661b-111">Information schema views</span></span>|  
|<span data-ttu-id="6661b-112">호환성 뷰</span><span class="sxs-lookup"><span data-stu-id="6661b-112">Compatibility views</span></span>|<span data-ttu-id="6661b-113">확장 속성</span><span class="sxs-lookup"><span data-stu-id="6661b-113">Extended properties</span></span>|  
  
 <span data-ttu-id="6661b-114">메타데이터 표시 유형 구성이 적용되지 않는 보안 개체는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-114">Metadata visibility configuration does not apply to the following securables.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6661b-115">로그 전달 시스템 테이블</span><span class="sxs-lookup"><span data-stu-id="6661b-115">Log shipping system tables</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6661b-116">에이전트 시스템 테이블</span><span class="sxs-lookup"><span data-stu-id="6661b-116">Agent system tables</span></span>|  
|<span data-ttu-id="6661b-117">데이터베이스 유지 관리 계획 시스템 테이블</span><span class="sxs-lookup"><span data-stu-id="6661b-117">Database maintenance plan system tables</span></span>|<span data-ttu-id="6661b-118">백업 시스템 테이블</span><span class="sxs-lookup"><span data-stu-id="6661b-118">Backup system tables</span></span>|  
|<span data-ttu-id="6661b-119">복제 시스템 테이블</span><span class="sxs-lookup"><span data-stu-id="6661b-119">Replication system tables</span></span>|<span data-ttu-id="6661b-120">복제 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 **sp_help** 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="6661b-120">Replication and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **sp_help** stored procedures</span></span>|  
  
 <span data-ttu-id="6661b-121">제한된 메타데이터 액세스란 다음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-121">Limited metadata accessibility means the following:</span></span>  
  
-   <span data-ttu-id="6661b-122">**public** 메타데이터 액세스가 사용되는 애플리케이션이 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-122">Applications that assume **public** metadata access will break.</span></span>  
  
-   <span data-ttu-id="6661b-123">시스템 뷰에 대한 쿼리는 행의 하위 집합이나 일부 경우에는 빈 결과 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-123">Queries on system views might only return a subset of rows, or sometimes an empty result set.</span></span>  
  
-   <span data-ttu-id="6661b-124">OBJECTPROPERTYEX와 같은 메타데이터 내보내기 기본 제공 함수가 NULL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-124">Metadata-emitting, built-in functions such as OBJECTPROPERTYEX may return NULL.</span></span>  
  
-   <span data-ttu-id="6661b-125">[!INCLUDE[ssDE](../../includes/ssde-md.md)] **sp_help** 저장 프로시저는 행의 하위 집합이나 NULL만 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-125">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] **sp_help** stored procedures might return only a subset of rows, or NULL.</span></span>  
  
 <span data-ttu-id="6661b-126">저장 프로시저 및 트리거와 같은 SQL 모듈은 호출자의 보안 컨텍스트에서 실행되므로 메타데이터 액세스가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-126">SQL modules, such as stored procedures and triggers, run under the security context of the caller and, therefore, have limited metadata accessibility.</span></span> <span data-ttu-id="6661b-127">예를 들어 다음 코드에서 저장 프로시저가 호출자에게 권한이 없는 `myTable` 테이블에 액세스하려고 시도하면 빈 결과 집합이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-127">For example, in the following code, when the stored procedure tries to access metadata for the table `myTable` on which the caller has no rights, an empty result set is returned.</span></span> <span data-ttu-id="6661b-128">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 행이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-128">In earlier releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a row is returned.</span></span>  
  
```  
CREATE PROCEDURE assumes_caller_can_access_metadata  
BEGIN  
SELECT name, id   
FROM sysobjects   
WHERE name = 'myTable';  
END;  
GO  
```  
  
 <span data-ttu-id="6661b-129">호출자가 메타데이터를 볼 수 있도록 개체 수준, 데이터베이스 수준 또는 서버 수준의 적합한 범위에서 VIEW DEFINITION 권한을 호출자에게 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-129">To allow callers to view metadata, you can grant the callers VIEW DEFINITION permission at an appropriate scope: object level, database level or server level.</span></span> <span data-ttu-id="6661b-130">따라서 이전 예에서 호출자에게 `myTable`에 대한 VIEW DEFINITION 권한이 있으면 저장 프로시저가 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-130">Therefore, in the previous example, if the caller has VIEW DEFINITION permission on `myTable`, the stored procedure returns a row.</span></span> <span data-ttu-id="6661b-131">자세한 내용은 [GRANT&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) 및 [GRANT 데이터베이스 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6661b-131">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) and [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
 <span data-ttu-id="6661b-132">또한 소유자의 자격 증명에 따라 실행되도록 저장 프로시저를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-132">You can also modify the stored procedure so that it executes under the credentials of the owner.</span></span> <span data-ttu-id="6661b-133">프로시저 소유자와 테이블 소유자가 같은 경우 소유권 체인이 적용되며 프로시저 소유자의 보안 컨텍스트로 `myTable`에 대한 메타데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-133">When the procedure owner and the table owner are the same owner, ownership chaining applies, and the security context of the procedure owner enables access to the metadata for `myTable`.</span></span> <span data-ttu-id="6661b-134">이 경우 다음 코드는 호출자에게 메타데이터 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-134">Under this scenario, the following code returns a row of metadata to the caller.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6661b-135">다음 예제에서는 [sys.sysobjects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) 호환성 뷰 대신 [sys.objects](/sql/relational-databases/system-compatibility-views/sys-sysobjects-transact-sql) 카탈로그 뷰가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-135">The following example uses the [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) catalog view instead of the [sys.sysobjects](/sql/relational-databases/system-compatibility-views/sys-sysobjects-transact-sql) compatibility view.</span></span>  
  
```  
CREATE PROCEDURE does_not_assume_caller_can_access_metadata  
WITH EXECUTE AS OWNER  
AS  
BEGIN  
SELECT name, id  
FROM sys.objects   
WHERE name = 'myTable'   
END;  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="6661b-136">EXECUTE AS를 사용하여 호출자의 보안 컨텍스트로 임시 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-136">You can use EXECUTE AS to temporarily switch to the security context of the caller.</span></span> <span data-ttu-id="6661b-137">자세한 내용은 [EXECUTE AS&#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6661b-137">For more information, see [EXECUTE AS &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-transact-sql).</span></span>  
  
## <a name="benefits-and-limits-of-metadata-visibility-configuration"></a><span data-ttu-id="6661b-138">메타데이터 표시 유형 구성의 이점과 한계</span><span class="sxs-lookup"><span data-stu-id="6661b-138">Benefits and Limits of Metadata Visibility Configuration</span></span>  
 <span data-ttu-id="6661b-139">메타데이터 표시 유형 구성은 전체적인 보안 계획에서 중요한 역할을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-139">Metadata visibility configuration can play an important role in your overall security plan.</span></span> <span data-ttu-id="6661b-140">하지만 경우에 따라서는 결정권을 가진 사용자가 일부 메타데이터를 공개할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-140">However, there are cases in which a skilled and determined user can force the disclosure of some metadata.</span></span> <span data-ttu-id="6661b-141">메타데이터 사용 권한은 여러 가지 방어적 관점을 고려하여 배포하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-141">We recommend that you deploy metadata permissions as one of many defenses-in-depth.</span></span>  
  
 <span data-ttu-id="6661b-142">이론상 쿼리의 조건자 평가 순서를 조작하여 강제로 오류 메시지에 메타데이터를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-142">It is theoretically possible to force the emission of metadata in error messages by manipulating the order of predicate evaluation in queries.</span></span> <span data-ttu-id="6661b-143">이러한 *trial-and-error 공격* 가능성이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 반드시 관련된 것은 아니며</span><span class="sxs-lookup"><span data-stu-id="6661b-143">The possibility of such *trial-and-error attacks* is not specific to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6661b-144">관계형 대수에서 허용되는 연관 및 누적 변환에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-144">It is implied by the associative and commutative transformations permitted in relational algebra.</span></span> <span data-ttu-id="6661b-145">오류 메시지에 반환되는 정보를 제한하여 이 위험을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-145">You can mitigate this risk by limiting the information returned in error messages.</span></span> <span data-ttu-id="6661b-146">이런 방식으로 메타데이터의 표시 유형을 더욱 제한하려면 추적 플래그 3625로 서버를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-146">To further restrict the visibility of metadata in this way, you can start the server with trace flag 3625.</span></span> <span data-ttu-id="6661b-147">이 추적 플래그는 오류 메시지에 표시되는 정보를 제한하므로</span><span class="sxs-lookup"><span data-stu-id="6661b-147">This trace flag limits the amount of information shown in error messages.</span></span> <span data-ttu-id="6661b-148">정보 공개를 방지하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-148">In turn, this helps to prevent forced disclosures.</span></span> <span data-ttu-id="6661b-149">이 경우 오류 메시지가 상세하지 않아 디버깅 용도로 사용하기 어려운 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-149">The tradeoff is that error messages will be terse and might be difficult to use for debugging purposes.</span></span> <span data-ttu-id="6661b-150">자세한 내용은 [데이터베이스 엔진 서비스 시작 옵션](../../database-engine/configure-windows/database-engine-service-startup-options.md) 및 [추적 플래그&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6661b-150">For more information, see [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md) and [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
 <span data-ttu-id="6661b-151">다음과 같은 메타데이터는 공개되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-151">The following metadata is not subject to forced disclosure:</span></span>  
  
-   <span data-ttu-id="6661b-152">**sys.servers** 의 **provider_string**열에 저장된 값.</span><span class="sxs-lookup"><span data-stu-id="6661b-152">The value stored in the **provider_string** column of **sys.servers**.</span></span> <span data-ttu-id="6661b-153">ALTER ANY LINKED SERVER 권한이 없는 사용자에게는 이 열에 NULL 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-153">A user that does not have ALTER ANY LINKED SERVER permission will see a NULL value in this column.</span></span>  
  
-   <span data-ttu-id="6661b-154">저장 프로시저 또는 트리거와 같은 사용자 정의 개체에 대한 원본 정의.</span><span class="sxs-lookup"><span data-stu-id="6661b-154">Source definition of a user-defined object such as a stored procedure or trigger.</span></span> <span data-ttu-id="6661b-155">원본 코드는 다음 조건 중 하나에 부합하는 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-155">The source code is visible only when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="6661b-156">사용자에게 개체에 대한 VIEW DEFINITION 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-156">The user has VIEW DEFINITION permission on the object.</span></span>  
  
    -   <span data-ttu-id="6661b-157">사용자에게 개체에 대한 VIEW DEFINITION 권한이 거부되지 않았고 개체에 대한 CONTROL, ALTER 또는 TAKE OWNERSHIP 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-157">The user has not been denied VIEW DEFINITION permission on the object and has CONTROL, ALTER, or TAKE OWNERSHIP permission on the object.</span></span> <span data-ttu-id="6661b-158">다른 모든 사용자에게는 NULL이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-158">All other users will see NULL.</span></span>  
  
-   <span data-ttu-id="6661b-159">다음 카탈로그 뷰에 있는 정의 열</span><span class="sxs-lookup"><span data-stu-id="6661b-159">The definition columns found in the following catalog views:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="6661b-160">**sys.all_sql_modules**</span><span class="sxs-lookup"><span data-stu-id="6661b-160">**sys.all_sql_modules**</span></span>|<span data-ttu-id="6661b-161">**sys.sql_modules**</span><span class="sxs-lookup"><span data-stu-id="6661b-161">**sys.sql_modules**</span></span>|  
    |<span data-ttu-id="6661b-162">**sys.server_sql_modules**</span><span class="sxs-lookup"><span data-stu-id="6661b-162">**sys.server_sql_modules**</span></span>|<span data-ttu-id="6661b-163">**sys.check_constraints**</span><span class="sxs-lookup"><span data-stu-id="6661b-163">**sys.check_constraints**</span></span>|  
    |<span data-ttu-id="6661b-164">**sys.default_constraints**</span><span class="sxs-lookup"><span data-stu-id="6661b-164">**sys.default_constraints**</span></span>|<span data-ttu-id="6661b-165">**sys.computed_columns**</span><span class="sxs-lookup"><span data-stu-id="6661b-165">**sys.computed_columns**</span></span>|  
    |<span data-ttu-id="6661b-166">**sys.numbered_procedures**</span><span class="sxs-lookup"><span data-stu-id="6661b-166">**sys.numbered_procedures**</span></span>||  
  
-   <span data-ttu-id="6661b-167">**syscomments** 호환성 뷰에 있는 **ctext** 열</span><span class="sxs-lookup"><span data-stu-id="6661b-167">The **ctext** column in the **syscomments** compatibility view.</span></span>  
  
-   <span data-ttu-id="6661b-168">**sp_helptext** 프로시저의 출력</span><span class="sxs-lookup"><span data-stu-id="6661b-168">The output of the **sp_helptext** procedure.</span></span>  
  
-   <span data-ttu-id="6661b-169">정보 스키마 뷰에 있는 다음 열</span><span class="sxs-lookup"><span data-stu-id="6661b-169">The following columns in the information schema views:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="6661b-170">INFORMATION_SCHEMA.CHECK_CONSTRAINTS.CHECK_CLAUSE</span><span class="sxs-lookup"><span data-stu-id="6661b-170">INFORMATION_SCHEMA.CHECK_CONSTRAINTS.CHECK_CLAUSE</span></span>|<span data-ttu-id="6661b-171">INFORMATION_SCHEMA.COLUMNS.COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6661b-171">INFORMATION_SCHEMA.COLUMNS.COLUMN_DEFAULT</span></span>|  
    |<span data-ttu-id="6661b-172">INFORMATION_SCHEMA.DOMAINS.DOMAIN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6661b-172">INFORMATION_SCHEMA.DOMAINS.DOMAIN_DEFAULT</span></span>|<span data-ttu-id="6661b-173">INFORMATION_SCHEMA.ROUTINE_COLUMNS.COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6661b-173">INFORMATION_SCHEMA.ROUTINE_COLUMNS.COLUMN_DEFAULT</span></span>|  
    |<span data-ttu-id="6661b-174">INFORMATION_SCHEMA.ROUTINES.ROUTINE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6661b-174">INFORMATION_SCHEMA.ROUTINES.ROUTINE_DEFINITION</span></span>|<span data-ttu-id="6661b-175">INFORMATION_SCHEMA.VIEWS.VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6661b-175">INFORMATION_SCHEMA.VIEWS.VIEW_DEFINITION</span></span>|  
  
-   <span data-ttu-id="6661b-176">OBJECT_DEFINITION() 함수</span><span class="sxs-lookup"><span data-stu-id="6661b-176">OBJECT_DEFINITION() function</span></span>  
  
-   <span data-ttu-id="6661b-177">**sys.sql_logins**의 password_hash 열에 저장된 값.</span><span class="sxs-lookup"><span data-stu-id="6661b-177">The value stored in the password_hash column of **sys.sql_logins**.</span></span>  <span data-ttu-id="6661b-178">CONTROL SERVER 권한이 없는 사용자에게는 이 열에 NULL 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-178">A user that does not have CONTROL SERVER permission will see a NULL value in this column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6661b-179">기본 제공 시스템 프로시저 및 함수에 대한 SQL 정의는 **sys.system_sql_modules** 카탈로그 뷰, **sp_helptext** 저장 프로시저 및 OBJECT_DEFINITION() 함수를 통해 공개적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-179">The SQL definitions of built-in system procedures and functions are publicly visible through the **sys.system_sql_modules** catalog view, the **sp_helptext** stored procedure, and the OBJECT_DEFINITION() function.</span></span>  
  
## <a name="general-principles-of-metadata-visibility"></a><span data-ttu-id="6661b-180">메타데이터 표시 유형에 대한 일반 원칙</span><span class="sxs-lookup"><span data-stu-id="6661b-180">General Principles of Metadata Visibility</span></span>  
 <span data-ttu-id="6661b-181">다음은 메타데이터 표시 유형과 관련하여 고려해야 할 일반적인 원칙들입니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-181">The following are some general principles to consider regarding metadata visibility:</span></span>  
  
-   <span data-ttu-id="6661b-182">고정 역할의 암시적 사용 권한</span><span class="sxs-lookup"><span data-stu-id="6661b-182">Fixed roles implicit permissions</span></span>  
  
-   <span data-ttu-id="6661b-183">사용 권한 범위</span><span class="sxs-lookup"><span data-stu-id="6661b-183">Scope of permissions</span></span>  
  
-   <span data-ttu-id="6661b-184">DENY 선행 조건</span><span class="sxs-lookup"><span data-stu-id="6661b-184">Precedence of DENY</span></span>  
  
-   <span data-ttu-id="6661b-185">하위 구성 요소의 메타데이터에 대한 표시 유형</span><span class="sxs-lookup"><span data-stu-id="6661b-185">Visibility of subcomponent metadata</span></span>  
  
### <a name="fixed-roles-and-implicit-permissions"></a><span data-ttu-id="6661b-186">고정 역할과 암시적 사용 권한</span><span class="sxs-lookup"><span data-stu-id="6661b-186">Fixed Roles and Implicit Permissions</span></span>  
 <span data-ttu-id="6661b-187">고정 역할로 액세스할 수 있는 메타데이터는 해당 암시적 사용 권한에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-187">Metadata that can be accessed by fixed roles depends upon their corresponding implicit permissions.</span></span>  
  
### <a name="scope-of-permissions"></a><span data-ttu-id="6661b-188">사용 권한 범위</span><span class="sxs-lookup"><span data-stu-id="6661b-188">Scope of Permissions</span></span>  
 <span data-ttu-id="6661b-189">한 범위의 사용 권한에는 해당 범위와 포함된 모든 범위에서 메타데이터를 볼 수 있는 기능이 내재됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-189">Permissions at one scope imply the ability to see metadata at that scope and at all enclosed scopes.</span></span> <span data-ttu-id="6661b-190">예를 들어 특정 스키마에 대한 SELECT 권한은 해당 스키마에 포함된 모든 보안 개체에 대한 SELECT 권한을 암시합니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-190">For example, SELECT permission on a schema implies that the grantee has SELECT permission on all securables that are contained by that schema.</span></span> <span data-ttu-id="6661b-191">따라서 스키마에 대한 SELECT 권한을 사용자에게 부여하면 이 사용자가 해당 스키마에 대한 메타데이터뿐만 아니라 이 스키마에 포함된 모든 테이블, 뷰, 함수, 프로시저, 큐, 동의어, 유형 및 XML 스키마 컬렉션을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-191">The granting of SELECT permission on a schema therefore enables a user to see the metadata of the schema and also all tables, views, functions, procedures, queues, synonyms, types, and XML schema collections within it.</span></span> <span data-ttu-id="6661b-192">범위에 대한 자세한 내용은 [사용 권한 계층&#40;데이터베이스 엔진&#41;](permissions-hierarchy-database-engine.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6661b-192">For more information about scopes, see [Permissions Hierarchy &#40;Database Engine&#41;](permissions-hierarchy-database-engine.md).</span></span>  
  
### <a name="precedence-of-deny"></a><span data-ttu-id="6661b-193">DENY 선행 조건</span><span class="sxs-lookup"><span data-stu-id="6661b-193">Precedence of DENY</span></span>  
 <span data-ttu-id="6661b-194">DENY는 일반적으로 다른 사용 권한보다 우선적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-194">DENY typically takes precedence over other permissions.</span></span> <span data-ttu-id="6661b-195">예를 들어 데이터베이스 사용자에게 스키마에 대한 EXECUTE 권한이 부여되었지만 해당 스키마에 있는 저장 프로시저에 대한 EXECUTE 권한이 거부된 경우 이 사용자는 해당 저장 프로시저에 대한 메타데이터를 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-195">For example, if a database user is granted EXECUTE permission on a schema but has been denied EXECUTE permission on a stored procedure in that schema, the user cannot view the metadata for that stored procedure.</span></span>  
  
 <span data-ttu-id="6661b-196">또한 사용자에게 스키마에 대한 EXECUTE 권한이 거부되었지만 해당 스키마에 있는 저장 프로시저에 대한 EXECUTE 권한이 부여된 경우에도 이 사용자는 해당 저장 프로시저에 대한 메타데이터를 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-196">Additionally, if a user is denied EXECUTE permission on a schema but has been granted EXECUTE permission on a stored procedure in that schema, the user cannot view the metadata for that stored procedure.</span></span>  
  
 <span data-ttu-id="6661b-197">또 다른 예로 여러 역할 멤버 자격을 통해 사용자에게 저장 프로시저에 대한 EXECUTE 권한이 부여되고 거부된 경우 DENY가 우선적으로 적용되며, 이 사용자는 해당 저장 프로시저에 대한 메타데이터를 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-197">For another example, if a user has been granted and denied EXECUTE permission on a stored procedure, which is possible through your various role memberships, DENY takes precedence and the user cannot view the metadata of the stored procedure.</span></span>  
  
### <a name="visibility-of-subcomponent-metadata"></a><span data-ttu-id="6661b-198">하위 구성 요소의 메타데이터에 대한 표시 유형</span><span class="sxs-lookup"><span data-stu-id="6661b-198">Visibility of Subcomponent Metadata</span></span>  
 <span data-ttu-id="6661b-199">인덱스, CHECK 제약 조건 및 트리거와 같은 하위 구성 요소의 표시 유형은 부모 구성 요소의 사용 권한에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-199">The visibility of subcomponents, such as indexes, check constraints, and triggers is determined by permissions on the parent.</span></span> <span data-ttu-id="6661b-200">이러한 하위 구성 요소에는 부여 가능한 사용 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-200">These subcomponents do not have grantable permissions.</span></span> <span data-ttu-id="6661b-201">예를 들어 사용자에게 테이블에 대한 일부 사용 권한이 부여된 경우 이 사용자는 해당 테이블, 열, 인덱스, CHECK 제약 조건, 트리거 및 기타 하위 구성 요소에 대한 메타데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-201">For example, if a user has been granted some permission on a table, the user can view the metadata for the tables, columns, indexes, check constraints, triggers, and other such subcomponents.</span></span>  
  
#### <a name="metadata-that-is-accessible-to-all-database-users"></a><span data-ttu-id="6661b-202">모든 데이터베이스 사용자가 액세스할 수 있는 메타데이터</span><span class="sxs-lookup"><span data-stu-id="6661b-202">Metadata That Is Accessible to All Database Users</span></span>  
 <span data-ttu-id="6661b-203">일부 메타데이터는 특정 데이터베이스에서 모든 사용자가 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-203">Some metadata must be accessible to all users in a specific database.</span></span> <span data-ttu-id="6661b-204">예를 들어 파일 그룹에는 수여 가능한 사용 권한이 없기 때문에 사용자는 파일 그룹의 메타데이터를 볼 수 있는 사용 권한을 부여 받을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-204">For example, filegroups do not have conferrable permissions; therefore, a user cannot be granted permission to view the metadata of a filegroup.</span></span> <span data-ttu-id="6661b-205">하지만 테이블을 만들 수 있는 사용자는 CREATE TABLE 문에서 ON *filegroup* 또는 TEXTIMAGE_ON *filegroup* 절을 사용하기 위해 파일 그룹 메타데이터에 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-205">However, any user that can create a table must be able to access filegroup metadata to use the ON *filegroup* or TEXTIMAGE_ON *filegroup* clauses of the CREATE TABLE statement.</span></span>  
  
 <span data-ttu-id="6661b-206">DB_ID() 및 DB_NAME() 함수로 반환된 메타데이터는 모든 사용자에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-206">The metadata that is returned by the DB_ID() and DB_NAME() functions is visible to all users.</span></span>  
  
 <span data-ttu-id="6661b-207">다음 표에서는 **public** 역할에 표시할 수 있는 카탈로그 뷰 목록을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="6661b-207">The following table lists the catalog views that are visible to the **public** role.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6661b-208">**sys.partition_functions**</span><span class="sxs-lookup"><span data-stu-id="6661b-208">**sys.partition_functions**</span></span>|<span data-ttu-id="6661b-209">**sys.partition_range_values**</span><span class="sxs-lookup"><span data-stu-id="6661b-209">**sys.partition_range_values**</span></span>|  
|<span data-ttu-id="6661b-210">**sys.partition_schemes**</span><span class="sxs-lookup"><span data-stu-id="6661b-210">**sys.partition_schemes**</span></span>|<span data-ttu-id="6661b-211">**sys.data_spaces**</span><span class="sxs-lookup"><span data-stu-id="6661b-211">**sys.data_spaces**</span></span>|  
|<span data-ttu-id="6661b-212">**sys.filegroups**</span><span class="sxs-lookup"><span data-stu-id="6661b-212">**sys.filegroups**</span></span>|<span data-ttu-id="6661b-213">**sys.destination_data_spaces**</span><span class="sxs-lookup"><span data-stu-id="6661b-213">**sys.destination_data_spaces**</span></span>|  
|<span data-ttu-id="6661b-214">**sys.database_files**</span><span class="sxs-lookup"><span data-stu-id="6661b-214">**sys.database_files**</span></span>|<span data-ttu-id="6661b-215">**sys.allocation_units**</span><span class="sxs-lookup"><span data-stu-id="6661b-215">**sys.allocation_units**</span></span>|  
|<span data-ttu-id="6661b-216">**sys.partitions**</span><span class="sxs-lookup"><span data-stu-id="6661b-216">**sys.partitions**</span></span>|<span data-ttu-id="6661b-217">**sys.messages**</span><span class="sxs-lookup"><span data-stu-id="6661b-217">**sys.messages**</span></span>|  
|<span data-ttu-id="6661b-218">**sys.schemas**</span><span class="sxs-lookup"><span data-stu-id="6661b-218">**sys.schemas**</span></span>|<span data-ttu-id="6661b-219">**sys.configurations**</span><span class="sxs-lookup"><span data-stu-id="6661b-219">**sys.configurations**</span></span>|  
|<span data-ttu-id="6661b-220">**sys.sql_dependencies**</span><span class="sxs-lookup"><span data-stu-id="6661b-220">**sys.sql_dependencies**</span></span>|<span data-ttu-id="6661b-221">**sys.type_assembly_usages**</span><span class="sxs-lookup"><span data-stu-id="6661b-221">**sys.type_assembly_usages**</span></span>|  
|<span data-ttu-id="6661b-222">**sys.parameter_type_usages**</span><span class="sxs-lookup"><span data-stu-id="6661b-222">**sys.parameter_type_usages**</span></span>|<span data-ttu-id="6661b-223">**sys.column_type_usages**</span><span class="sxs-lookup"><span data-stu-id="6661b-223">**sys.column_type_usages**</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6661b-224">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6661b-224">See Also</span></span>  
 <span data-ttu-id="6661b-225">[GRANT&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6661b-225">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 <span data-ttu-id="6661b-226">[DENY&#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6661b-226">[DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql) </span></span>  
 <span data-ttu-id="6661b-227">[REVOKE&#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6661b-227">[REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) </span></span>  
 <span data-ttu-id="6661b-228">[EXECUTE AS 절&#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6661b-228">[EXECUTE AS Clause &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql) </span></span>  
 <span data-ttu-id="6661b-229">[카탈로그 뷰&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6661b-229">[Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql) </span></span>  
 [<span data-ttu-id="6661b-230">호환성 뷰&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6661b-230">Compatibility Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql)  
  
  
