---
title: 동의어(데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- synonyms [SQL Server], about synonyms
ms.assetid: 6210e1d5-075f-47e4-ac8d-f84bcf26fbc0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3494f4f5b13c422efb8e2a39597e131c10d81ed1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650874"
---
# <a name="synonyms-database-engine"></a><span data-ttu-id="65263-102">동의어(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="65263-102">Synonyms (Database Engine)</span></span>
  <span data-ttu-id="65263-103">동의어란 다음 용도로 사용되는 데이터베이스 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="65263-103">A synonym is a database object that serves the following purposes:</span></span>  
  
-   <span data-ttu-id="65263-104">로컬 서버나 원격 서버에 있을 수 있는 기본 개체로 참조되는 다른 데이터베이스 개체의 대체 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-104">Provides an alternative name for another database object, referred to as the base object, that can exist on a local or remote server.</span></span>  
  
-   <span data-ttu-id="65263-105">기본 개체의 이름이나 위치의 변경으로부터 클라이언트 애플리케이션을 보호하는 추상적 계층을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-105">Provides a layer of abstraction that protects a client application from changes made to the name or location of the base object.</span></span>  
  
 <span data-ttu-id="65263-106">예를 들어 **Server1** 이라는 서버에 있는 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)]의 **Employee**테이블을 검토해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="65263-106">For example, consider the **Employee** table of [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)], located on a server named **Server1**.</span></span> <span data-ttu-id="65263-107">다른 서버 **Server2**에서 이 테이블을 참조하려면 클라이언트 애플리케이션이 네 부분으로 된 이름 **Server1.AdventureWorks.Person.Employee**를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-107">To reference this table from another server, **Server2**, a client application would have to use the four-part name **Server1.AdventureWorks.Person.Employee**.</span></span> <span data-ttu-id="65263-108">또한 테이블 위치를 다른 서버 등으로 변경하는 경우 이 변경 내용을 반영하기 위해 클라이언트 애플리케이션을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-108">Also, if the location of the table were to change, for example, to another server, the client application would have to be modified to reflect that change.</span></span>  
  
 <span data-ttu-id="65263-109">**Server1**의 **Employee** 테이블에 대한 동의어, **EmpTable** 을 **Server2**에 만들어 이러한 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-109">To address both these issues, you can create a synonym, **EmpTable**, on **Server2** for the **Employee** table on **Server1**.</span></span> <span data-ttu-id="65263-110">이제 클라이언트 애플리케이션은 단일 부분으로 된 이름인 **EmpTable**만 사용하여 **Employee** 테이블을 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-110">Now, the client application only has to use the single-part name, **EmpTable**, to reference the **Employee** table.</span></span> <span data-ttu-id="65263-111">또한 **Employee** 테이블 위치가 변경되면 동의어 **EmpTable**를 수정하여 **Employee** 테이블의 새 위치를 가리키게 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-111">Also, if the location of the **Employee** table changes, you will have to modify the synonym, **EmpTable**, to point to the new location of the **Employee** table.</span></span> <span data-ttu-id="65263-112">ALTER SYNONYM 문이 없으므로 먼저 동의어 **EmpTable**을 삭제한 다음 같은 이름으로 동의어를 다시 만들지만 **Employee**의 새 위치를 가리키게 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-112">Because there is no ALTER SYNONYM statement, you first have to drop the synonym, **EmpTable**, and then re-create the synonym with the same name, but point the synonym to the new location of **Employee**.</span></span>  
  
 <span data-ttu-id="65263-113">동의어는 스키마에 속하고 스키마의 다른 개체처럼 동의어 이름은 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-113">A synonym belongs to a schema, and like other objects in a schema, the name of a synonym must be unique.</span></span> <span data-ttu-id="65263-114">다음 데이터베이스 개체의 동의어를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-114">You can create synonyms for the following database objects:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="65263-115">어셈블리(CLR) 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="65263-115">Assembly (CLR) stored procedure</span></span>|<span data-ttu-id="65263-116">어셈블리(CLR) 테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="65263-116">Assembly (CLR) table-valued function</span></span>|  
|<span data-ttu-id="65263-117">어셈블리(CLR) 스칼라 함수</span><span class="sxs-lookup"><span data-stu-id="65263-117">Assembly (CLR) scalar function</span></span>|<span data-ttu-id="65263-118">어셈블리(CLR) 집계 함수</span><span class="sxs-lookup"><span data-stu-id="65263-118">Assembly (CLR) aggregate functions</span></span>|  
|<span data-ttu-id="65263-119">복제 필터 프로시저</span><span class="sxs-lookup"><span data-stu-id="65263-119">Replication-filter-procedure</span></span>|<span data-ttu-id="65263-120">확장 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="65263-120">Extended stored procedure</span></span>|  
|<span data-ttu-id="65263-121">SQL 스칼라 함수</span><span class="sxs-lookup"><span data-stu-id="65263-121">SQL scalar function</span></span>|<span data-ttu-id="65263-122">SQL 테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="65263-122">SQL table-valued function</span></span>|  
|<span data-ttu-id="65263-123">SQL 인라인 테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="65263-123">SQL inline-tabled-valued function</span></span>|<span data-ttu-id="65263-124">SQL 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="65263-124">SQL stored procedure</span></span>|  
|<span data-ttu-id="65263-125">View</span><span class="sxs-lookup"><span data-stu-id="65263-125">View</span></span>|<span data-ttu-id="65263-126">테이블<sup>1</sup>(사용자 정의)</span><span class="sxs-lookup"><span data-stu-id="65263-126">Table<sup>1</sup> (User-defined)</span></span>|  
  
 <span data-ttu-id="65263-127"><sup>1</sup> 로컬 및 전역 임시 테이블을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-127"><sup>1</sup> Includes local and global temporary tables</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65263-128">함수 기본 개체의 네 부분으로 된 이름은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-128">Four-part names for function base objects are not supported.</span></span>  
  
 <span data-ttu-id="65263-129">동의어는 다른 동의어의 기본 개체가 될 수 없고 사용자 정의 집계 함수를 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-129">A synonym cannot be the base object for another synonym, and a synonym cannot reference a user-defined aggregate function.</span></span>  
  
 <span data-ttu-id="65263-130">동의어와 해당 기본 개체는 이름별로만 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="65263-130">The binding between a synonym and its base object is by name only.</span></span> <span data-ttu-id="65263-131">기본 개체에 대한 모든 존재, 유형 및 권한 검사는 런타임까지 지연됩니다.</span><span class="sxs-lookup"><span data-stu-id="65263-131">All existence, type, and permissions checking on the base object is deferred until run time.</span></span> <span data-ttu-id="65263-132">따라서 기본 개체를 수정, 삭제 또는 삭제 후 원래 기본 개체와 같은 이름을 가진 다른 개체로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-132">Therefore, the base object can be modified, dropped, or dropped and replaced by another object that has the same name as the original base object.</span></span> <span data-ttu-id="65263-133">예를 들어 **의**Person.Contact **테이블을 참조하는 동의어** MyContacts [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)]를 고려해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="65263-133">For example, consider a synonym, **MyContacts**, that references the **Person.Contact** table in [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)].</span></span> <span data-ttu-id="65263-134">**Contact** 테이블을 삭제한 후 **Person.Contact**라는 뷰로 바꾸면 **MyContacts** 는 **Person.Contact** 뷰를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-134">If the **Contact** table is dropped and replaced by a view named **Person.Contact**, **MyContacts** now references the **Person.Contact** view.</span></span>  
  
 <span data-ttu-id="65263-135">동의어에 대한 참조는 스키마에 바인딩되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-135">References to synonyms are not schema-bound.</span></span> <span data-ttu-id="65263-136">따라서 동의어는 언제라도 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-136">Therefore, a synonym can be dropped at any time.</span></span> <span data-ttu-id="65263-137">그러나 동의어를 삭제하면 삭제된 동의어에 대한 참조가 현수 참조로 남게 될 위험이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-137">However, by dropping a synonym, you run the risk of leaving dangling references to the synonym that was dropped.</span></span> <span data-ttu-id="65263-138">이러한 참조는 런타임에만 발견됩니다.</span><span class="sxs-lookup"><span data-stu-id="65263-138">These references will only be found at run time.</span></span>  
  
## <a name="synonyms-and-schemas"></a><span data-ttu-id="65263-139">동의어 및 스키마</span><span class="sxs-lookup"><span data-stu-id="65263-139">Synonyms and Schemas</span></span>  
 <span data-ttu-id="65263-140">소유하지 않은 기본 스키마가 있는데 동의어를 만들려면 소유한 스키마 이름을 사용하여 동의어 이름을 적합하게 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-140">If you have a default schema that you do not own and want to create a synonym, you must qualify the synonym name with the name of a schema that you do own.</span></span> <span data-ttu-id="65263-141">예를 들어 **x**스키마를 소유하지만 **y** 스키마가 기본 스키마이고 CREATE SYNONYM 문을 사용할 경우에는 단일 부분으로 된 이름을 사용하여 동의어 이름을 지정하는 대신 **x**스키마를 동의어 이름 접두사로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-141">For example, if you own a schema **x**, but **y** is your default schema and you use the CREATE SYNONYM statement, you must prefix the name of the synonym with the schema **x**, instead of naming the synonym by using a single-part name.</span></span> <span data-ttu-id="65263-142">동의어를 만드는 방법은 [CREATE SYNONYM&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-synonym-transact-sql)테이블을 검토해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="65263-142">For more information about how to create synonyms, see [CREATE SYNONYM &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-synonym-transact-sql).</span></span>  
  
## <a name="granting-permissions-on-a-synonym"></a><span data-ttu-id="65263-143">동의어에 대한 권한 부여</span><span class="sxs-lookup"><span data-stu-id="65263-143">Granting Permissions on a Synonym</span></span>  
 <span data-ttu-id="65263-144">**db_owner**의 멤버나 **db_ddladmin** 의 멤버인 동의어 소유자만 동의어에 대한 권한을 부여 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-144">Only synonym owners, members of **db_owner**, or members of **db_ddladmin** can grant permission on a synonym.</span></span>  
  
 <span data-ttu-id="65263-145">동의어에 대한 다음과 같은 모든 권한에 대해 GRANT, DENY 및 REVOKE를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-145">You can GRANT, DENY, REVOKE all or any of the following permissions on a synonym:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="65263-146">CONTROL</span><span class="sxs-lookup"><span data-stu-id="65263-146">CONTROL</span></span>|<span data-ttu-id="65263-147">Delete</span><span class="sxs-lookup"><span data-stu-id="65263-147">DELETE</span></span>|  
|<span data-ttu-id="65263-148">CREATE 문을 실행하기 전에</span><span class="sxs-lookup"><span data-stu-id="65263-148">EXECUTE</span></span>|<span data-ttu-id="65263-149">INSERT</span><span class="sxs-lookup"><span data-stu-id="65263-149">INSERT</span></span>|  
|<span data-ttu-id="65263-150">SELECT</span><span class="sxs-lookup"><span data-stu-id="65263-150">SELECT</span></span>|<span data-ttu-id="65263-151">TAKE OWNERSHIP</span><span class="sxs-lookup"><span data-stu-id="65263-151">TAKE OWNERSHIP</span></span>|  
|<span data-ttu-id="65263-152">UPDATE</span><span class="sxs-lookup"><span data-stu-id="65263-152">UPDATE</span></span>|<span data-ttu-id="65263-153">VIEW DEFINITION</span><span class="sxs-lookup"><span data-stu-id="65263-153">VIEW DEFINITION</span></span>|  
  
## <a name="using-synonyms"></a><span data-ttu-id="65263-154">동의어 사용</span><span class="sxs-lookup"><span data-stu-id="65263-154">Using Synonyms</span></span>  
 <span data-ttu-id="65263-155">여러 SQL 문 및 식 컨텍스트에서 동의어를 해당 참조 기준 개체 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-155">You can use synonyms in place of their referenced base object in several SQL statements and expression contexts.</span></span> <span data-ttu-id="65263-156">다음 표에서는 이러한 문 및 식 컨텍스트를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-156">The following table contains a list of these statements and expression contexts:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="65263-157">SELECT</span><span class="sxs-lookup"><span data-stu-id="65263-157">SELECT</span></span>|<span data-ttu-id="65263-158">INSERT</span><span class="sxs-lookup"><span data-stu-id="65263-158">INSERT</span></span>|  
|<span data-ttu-id="65263-159">UPDATE</span><span class="sxs-lookup"><span data-stu-id="65263-159">UPDATE</span></span>|<span data-ttu-id="65263-160">Delete</span><span class="sxs-lookup"><span data-stu-id="65263-160">DELETE</span></span>|  
|<span data-ttu-id="65263-161">CREATE 문을 실행하기 전에</span><span class="sxs-lookup"><span data-stu-id="65263-161">EXECUTE</span></span>|<span data-ttu-id="65263-162">하위 SELECT</span><span class="sxs-lookup"><span data-stu-id="65263-162">Sub-selects</span></span>|  
  
 <span data-ttu-id="65263-163">앞에서 설명한 컨텍스트에서 동의어를 사용하면 기준 개체가 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-163">When you are working with synonyms in the contexts previously stated, the base object is affected.</span></span> <span data-ttu-id="65263-164">예를 들어 동의어가 테이블 기준 개체를 참조하며 동의어에 행을 삽입한 경우 실제로 참조되는 테이블에 행이 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="65263-164">For example, if a synonym references a base object that is a table and you insert a row into the synonym, you are actually inserting a row into the referenced table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65263-165">연결된 서버에 있는 동의어는 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-165">You cannot reference a synonym that is located on a linked server.</span></span>  
  
 <span data-ttu-id="65263-166">동의어를 OBJECT_ID 함수의 매개 변수로 사용할 수 있습니다. 그러나 함수는 기본 개체가 아닌 동의어의 개체 ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-166">You can use a synonym as the parameter for the OBJECT_ID function; however, the function returns the object ID of the synonym, not the base object.</span></span>  
  
 <span data-ttu-id="65263-167">DDL 문에서는 동의어를 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-167">You cannot reference a synonym in a DDL statement.</span></span> <span data-ttu-id="65263-168">예를 들어 `dbo.MyProduct`라는 동의어를 참조하는 다음 문은 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-168">For example, the following statements, which reference a synonym named `dbo.MyProduct`, generate errors:</span></span>  
  
```  
ALTER TABLE dbo.MyProduct  
   ADD NewFlag int null;  
EXEC ('ALTER TABLE dbo.MyProduct  
   ADD NewFlag int null');  
```  
  
 <span data-ttu-id="65263-169">사용 권한 제어를 위한 다음 문은 동의어에만 관련되며 기준 개체와는 관련되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-169">The following permission statements are associated only with the synonym and not the base object:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="65263-170">GRANT</span><span class="sxs-lookup"><span data-stu-id="65263-170">GRANT</span></span>|<span data-ttu-id="65263-171">거부</span><span class="sxs-lookup"><span data-stu-id="65263-171">DENY</span></span>|  
|<span data-ttu-id="65263-172">REVOKE</span><span class="sxs-lookup"><span data-stu-id="65263-172">REVOKE</span></span>||  
  
 <span data-ttu-id="65263-173">동의어는 스키마 바운드가 아니므로 다음과 같은 스키마 바운드 식 컨텍스트에서 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-173">Synonyms are not schema-bound and, therefore, cannot be referenced by the following schema-bound expression contexts:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="65263-174">CHECK 제약 조건</span><span class="sxs-lookup"><span data-stu-id="65263-174">CHECK constraints</span></span>|<span data-ttu-id="65263-175">계산 열</span><span class="sxs-lookup"><span data-stu-id="65263-175">Computed columns</span></span>|  
|<span data-ttu-id="65263-176">기본 식</span><span class="sxs-lookup"><span data-stu-id="65263-176">Default expressions</span></span>|<span data-ttu-id="65263-177">규칙 식</span><span class="sxs-lookup"><span data-stu-id="65263-177">Rule expressions</span></span>|  
|<span data-ttu-id="65263-178">스키마 바운드 뷰</span><span class="sxs-lookup"><span data-stu-id="65263-178">Schema-bound views</span></span>|<span data-ttu-id="65263-179">스키마 바운드 함수</span><span class="sxs-lookup"><span data-stu-id="65263-179">Schema-bound functions</span></span>|  
  
 <span data-ttu-id="65263-180">스키마 바운드 함수에 대한 자세한 내용은 [사용자 정의 함수 만들기&#40;데이터베이스 엔진&#41;](../user-defined-functions/create-user-defined-functions-database-engine.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65263-180">For more information about schema-bound functions, see [Create User-defined Functions &#40;Database Engine&#41;](../user-defined-functions/create-user-defined-functions-database-engine.md).</span></span>  
  
## <a name="getting-information-about-synonyms"></a><span data-ttu-id="65263-181">동의어에 대한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="65263-181">Getting Information About Synonyms</span></span>  
 <span data-ttu-id="65263-182">sys.synonyms 카탈로그 뷰에는 지정된 데이터베이스의 각 동의어에 대한 항목이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-182">The sys.synonyms catalog view contains an entry for each synonym in a given database.</span></span> <span data-ttu-id="65263-183">이 카탈로그 뷰는 동의어 이름과 기본 개체 이름과 같은 동의어 메타데이터를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-183">This catalog view exposes synonym metadata such as the name of the synonym and the name of the base object.</span></span> <span data-ttu-id="65263-184">카탈로그 뷰에 대 한 자세한 내용은 `sys.synonyms` [&#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-synonyms-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="65263-184">For more information about the `sys.synonyms` catalog view, see [sys.synonyms &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-synonyms-transact-sql).</span></span>  
  
 <span data-ttu-id="65263-185">확장 속성을 사용하면 설명이나 지시 텍스트, 입력 마스크, 서식 설정 규칙을 동의어 속성으로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-185">By using extended properties, you can add descriptive or instructional text, input masks, and formatting rules as properties of a synonym.</span></span> <span data-ttu-id="65263-186">속성이 데이터베이스에 저장되기 때문에 속성을 읽는 모든 애플리케이션은 개체를 같은 방식으로 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65263-186">Because the property is stored in the database, all applications that read the property can evaluate the object in the same way.</span></span> <span data-ttu-id="65263-187">자세한 내용은 [sp_addextendedproperty&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65263-187">For more information, see [sp_addextendedproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql).</span></span>  
  
 <span data-ttu-id="65263-188">동의어 기본 개체의 기본 유형을 찾으려면 OBJECTPROPERTYEX 함수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-188">To find the base type of the base object of a synonym, use the OBJECTPROPERTYEX function.</span></span> <span data-ttu-id="65263-189">자세한 내용은 [OBJECTPROPERTYEX&#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65263-189">For more information, see [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="65263-190">예</span><span class="sxs-lookup"><span data-stu-id="65263-190">Examples</span></span>  
 <span data-ttu-id="65263-191">다음 예에서는 로컬 개체인 동의어 기본 개체의 기본 유형을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-191">The following example returns the base type of a synonym's base object that is a local object.</span></span>  
  
```  
USE tempdb;  
GO  
CREATE SYNONYM MyEmployee   
FOR AdventureWorks2012.HumanResources.Employee;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID('MyEmployee'), 'BaseType') AS BaseType;  
```  
  
 <span data-ttu-id="65263-192">다음 예에서는 `Server1`서버에 위치한 원격 개체인 동의어 기본 개체의 기본 유형을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="65263-192">The following example returns the base type of a synonym's base object that is a remote object located on a server named `Server1`.</span></span>  
  
```  
EXECUTE sp_addlinkedserver Server1;  
GO  
CREATE SYNONYM MyRemoteEmployee  
FOR Server1.AdventureWorks2012.HumanResources.Employee;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID('MyRemoteEmployee'), 'BaseType') AS BaseType;  
GO  
```  
  
## <a name="related-content"></a><span data-ttu-id="65263-193">관련 내용</span><span class="sxs-lookup"><span data-stu-id="65263-193">Related Content</span></span>  
 [<span data-ttu-id="65263-194">동의어 만들기</span><span class="sxs-lookup"><span data-stu-id="65263-194">Create Synonyms</span></span>](create-synonyms.md)  
  
 [<span data-ttu-id="65263-195">CREATE SYNONYM &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="65263-195">CREATE SYNONYM &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-synonym-transact-sql)  
  
 [<span data-ttu-id="65263-196">DROP SYNONYM&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="65263-196">DROP SYNONYM &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-synonym-transact-sql)  
  
  
