---
title: MSSQLSERVER_2020 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2020 (Database Engine error)
ms.assetid: 4a8bf90f-a083-4c53-84f0-d23c711c8081
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5939267c37e90e7b8456dc01a4af79545e775656
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653920"
---
# <a name="mssqlserver_2020"></a><span data-ttu-id="d7ff1-102">MSSQLSERVER_2020</span><span class="sxs-lookup"><span data-stu-id="d7ff1-102">MSSQLSERVER_2020</span></span>
    
## <a name="details"></a><span data-ttu-id="d7ff1-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="d7ff1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d7ff1-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="d7ff1-104">Product Name</span></span>|<span data-ttu-id="d7ff1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d7ff1-105">SQL Server</span></span>|  
|<span data-ttu-id="d7ff1-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="d7ff1-106">Event ID</span></span>|<span data-ttu-id="d7ff1-107">2020</span><span class="sxs-lookup"><span data-stu-id="d7ff1-107">2020</span></span>|  
|<span data-ttu-id="d7ff1-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="d7ff1-108">Event Source</span></span>|<span data-ttu-id="d7ff1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d7ff1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d7ff1-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="d7ff1-110">Component</span></span>|<span data-ttu-id="d7ff1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d7ff1-111">SQLEngine</span></span>|  
|<span data-ttu-id="d7ff1-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="d7ff1-112">Symbolic Name</span></span>||  
|<span data-ttu-id="d7ff1-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="d7ff1-113">Message Text</span></span>|<span data-ttu-id="d7ff1-114">엔터티 "%.\*ls"에 대해 보고된 종속성이 열에 대한 참조를 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-114">The dependencies reported for entity "%.\*ls" do not include references to columns.</span></span> <span data-ttu-id="d7ff1-115">이는 해당 엔터티가 존재하지 않는 개체를 참조하거나 엔터티 문 중 하나 이상에 오류가 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-115">This is either because the entity references an object that does not exist or because of an error in one or more statements in the entity.</span></span>  <span data-ttu-id="d7ff1-116">쿼리를 다시 실행하기 전에 엔터티에 오류가 있지 않은지 그리고 해당 엔터티에서 참조하는 개체가 모두 존재하는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-116">Before rerunning the query, ensure that there are no errors in the entity and that all objects referenced by the entity exist.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d7ff1-117">설명</span><span class="sxs-lookup"><span data-stu-id="d7ff1-117">Explanation</span></span>  
 <span data-ttu-id="d7ff1-118">**sys.dm_sql_referenced_entities** 시스템 함수는 스키마 바운드 참조에 대한 열 수준 종속성을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-118">The **sys.dm_sql_referenced_entities** system function will report any column-level dependency for schema-bound references.</span></span> <span data-ttu-id="d7ff1-119">예를 들어 이 함수는 인덱싱된 뷰에 스키마 바인딩이 필요하기 때문에 인덱싱된 뷰에 대한 모든 열 수준 종속성을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-119">For example, the function will report all column-level dependencies for an indexed view because an indexed view requires schema binding.</span></span> <span data-ttu-id="d7ff1-120">그러나 참조된 엔터티가 스키마 바인딩되지 않으면 열이 참조되는 모든 문을 바인딩할 수 있는 경우에만 열 종속성이 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-120">However, when the referenced entity is not schema-bound, column dependencies are reported only when all statements in which the columns are referenced can be bound.</span></span> <span data-ttu-id="d7ff1-121">문은 해당 문이 구문 분석될 때 모든 개체가 존재하는 경우에만 성공적으로 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-121">Statements can be successfully bound only if all objects exist at the time the statements are parsed.</span></span> <span data-ttu-id="d7ff1-122">엔터티에 정의된 문을 바인딩할 수 없으면 열 종속성이 보고되지 않고 **referenced_minor_id** 열이 0을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-122">If any statement defined in the entity fails to bind, column dependencies will not be reported and the **referenced_minor_id** column will return 0.</span></span> <span data-ttu-id="d7ff1-123">열 종속성을 확인할 수 없으면 오류 2020이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-123">When column dependencies cannot be resolved, error 2020 is raised.</span></span> <span data-ttu-id="d7ff1-124">이 오류가 발생해도 쿼리는 개체 수준 종속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-124">This error does not prevent the query from returning object-level dependencies.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d7ff1-125">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="d7ff1-125">User Action</span></span>  
 <span data-ttu-id="d7ff1-126">오류 2020보다 먼저 나타나는 메시지에서 확인된 모든 오류를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-126">Correct any errors identified in the message before error 2020.</span></span> <span data-ttu-id="d7ff1-127">예를 들어 다음 코드 예에서 `Production.ApprovedDocuments` 뷰는 `Title` 테이블의 `ChangeNumber`, `Status` 및 `Production.Document` 열에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-127">For example, in the following code example the view `Production.ApprovedDocuments` is defined on the columns `Title`, `ChangeNumber`, and `Status` in the `Production.Document` table.</span></span> <span data-ttu-id="d7ff1-128">**sys.dm_sql_referenced_entities** 시스템 함수는 `ApprovedDocuments` 뷰가 종속된 개체와 열에 대해 쿼리됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-128">The **sys.dm_sql_referenced_entities** system function is queried for the objects and columns on which the `ApprovedDocuments` view depends.</span></span> <span data-ttu-id="d7ff1-129">이 뷰는 WITH SCHEMA_BINDING 절을 사용하여 만들어지지 않기 때문에 이 뷰에서 참조되는 열은 참조된 테이블에서 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-129">Because the view is not created using the WITH SCHEMA_BINDING clause, the columns referenced in the view can be modified in the referenced table.</span></span> <span data-ttu-id="d7ff1-130">이 예에서는 `ChangeNumber` 테이블에 있는 `Production.Document` 열의 이름을 `TrackingNumber`로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-130">The example alters the column `ChangeNumber` in the `Production.Document` table by renaming it to `TrackingNumber`.</span></span> <span data-ttu-id="d7ff1-131">카탈로그 뷰는 `ApprovedDocuments` 뷰에 대해 다시 쿼리되지만 이 뷰에 정의된 모든 열에 바인딩할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-131">The catalog view is queried again for the `ApprovedDocuments` view; however it cannot bind to all the columns defined in the view.</span></span> <span data-ttu-id="d7ff1-132">그러면 문제를 나타내는 오류 207 및 2020이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-132">Errors 207 and 2020 are returned identifying the problem.</span></span> <span data-ttu-id="d7ff1-133">이 문제를 해결하려면 열의 새 이름을 반영하도록 뷰를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-133">To resolve the problem, the view must be altered to reflect the new name of the column.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `CREATE VIEW Production.ApprovedDocuments`  
  
 `AS`  
  
 `SELECT Title, ChangeNumber, Status`  
  
 `FROM Production.Document`  
  
 `WHERE Status = 2;`  
  
 `GO`  
  
 `SELECT referenced_schema_name AS schema_name`  
  
 `,referenced_entity_name AS table_name`  
  
 `,referenced_minor_name AS referenced_column`  
  
 `FROM sys.dm_sql_referenced_entities ('Production.ApprovedDocuments', 'OBJECT');`  
  
 `GO`  
  
 `EXEC sp_rename 'Production.Document.ChangeNumber', 'TrackingNumber', 'COLUMN';`  
  
 `GO`  
  
 `SELECT referenced_schema_name AS schema_name`  
  
 `,referenced_entity_name AS table_name`  
  
 `,referenced_minor_name AS referenced_column`  
  
 `FROM sys.dm_sql_referenced_entities ('Production.ApprovedDocuments', 'OBJECT');`  
  
 `GO`  
  
 <span data-ttu-id="d7ff1-134">이 쿼리는 다음과 같은 오류 메시지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-134">The query returns the following error messages.</span></span>  
  
 `Msg 207, Level 16, State 1, Procedure ApprovedDocuments, Line 3`  
  
 `Invalid column name 'ChangeNumber'.`  
  
 `Msg 2020, Level 16, State 1, Line 1`  
  
 `The dependencies reported for entity`  
  
 `"Production.ApprovedDocuments" do not include references to`  
  
 `columns. This is either because the entity references an`  
  
 `object that does not exist or because of an error in one or`  
  
 `more statements in the entity. Before rerunning the query,`  
  
 `ensure that there are no errors in the entity and that all`  
  
 `objects referenced by the entity exist.`  
  
 <span data-ttu-id="d7ff1-135">다음 예에서는 뷰의 열 이름을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7ff1-135">The following example corrects the column name in the view.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `ALTER VIEW Production.ApprovedDocuments`  
  
 `AS`  
  
 `SELECT Title,TrackingNumber, Status`  
  
 `FROM Production.Document`  
  
 `WHERE Status = 2;`  
  
 `GO`  
  
## <a name="see-also"></a><span data-ttu-id="d7ff1-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d7ff1-136">See Also</span></span>  
 [<span data-ttu-id="d7ff1-137">sys.dm_sql_referenced_entities&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d7ff1-137">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
  
