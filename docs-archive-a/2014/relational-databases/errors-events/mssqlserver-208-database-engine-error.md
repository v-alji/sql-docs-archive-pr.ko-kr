---
title: MSSQLSERVER_208 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 208 (Database Engine error)
ms.assetid: 4b1895f5-3197-4da1-af86-954c93507956
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 97ab3eb220c03c3de0c95251861f3b947890b090
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646527"
---
# <a name="mssqlserver_208"></a><span data-ttu-id="f8f14-102">MSSQLSERVER_208</span><span class="sxs-lookup"><span data-stu-id="f8f14-102">MSSQLSERVER_208</span></span>
    
## <a name="details"></a><span data-ttu-id="f8f14-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="f8f14-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f8f14-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="f8f14-104">Product Name</span></span>|<span data-ttu-id="f8f14-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f8f14-105">SQL Server</span></span>|  
|<span data-ttu-id="f8f14-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="f8f14-106">Event ID</span></span>|<span data-ttu-id="f8f14-107">208</span><span class="sxs-lookup"><span data-stu-id="f8f14-107">208</span></span>|  
|<span data-ttu-id="f8f14-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="f8f14-108">Event Source</span></span>|<span data-ttu-id="f8f14-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f8f14-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f8f14-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="f8f14-110">Component</span></span>|<span data-ttu-id="f8f14-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f8f14-111">SQLEngine</span></span>|  
|<span data-ttu-id="f8f14-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="f8f14-112">Symbolic Name</span></span>|<span data-ttu-id="f8f14-113">SQ_BADOBJECT</span><span class="sxs-lookup"><span data-stu-id="f8f14-113">SQ_BADOBJECT</span></span>|  
|<span data-ttu-id="f8f14-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="f8f14-114">Message Text</span></span>|<span data-ttu-id="f8f14-115">개체 이름 '%.\*ls'이(가) 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f14-115">Invalid object name '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f8f14-116">설명</span><span class="sxs-lookup"><span data-stu-id="f8f14-116">Explanation</span></span>  
 <span data-ttu-id="f8f14-117">지정한 개체를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f14-117">The specified object cannot be found.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="f8f14-118">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="f8f14-118">Possible Causes</span></span>  
 <span data-ttu-id="f8f14-119">이 오류는 다음과 같은 문제로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f14-119">This error can be caused by one of the following problems:</span></span>  
  
-   <span data-ttu-id="f8f14-120">개체가 올바르게 지정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f14-120">The object is not specified correctly.</span></span>  
  
-   <span data-ttu-id="f8f14-121">개체가 현재 데이터베이스 또는 지정된 데이터베이스에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f14-121">The object does not exist in the current database or in the specified database.</span></span>  
  
-   <span data-ttu-id="f8f14-122">개체가 있지만 사용자에게 표시되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f14-122">The object exists, but could not be exposed to the user.</span></span> <span data-ttu-id="f8f14-123">예를 들어 사용자에게 해당 개체에 대한 사용 권한이 없거나 해당 개체가 EXECUTE 문 내에서 만들어졌지만 EXECUTE 문의 외부에서 액세스되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f14-123">For example, the user might not have permissions on the object or the object is created within an EXECUTE statement but accessed outside the scope of the EXECUTE statement.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f8f14-124">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="f8f14-124">User Action</span></span>  
 <span data-ttu-id="f8f14-125">다음 정보를 확인하고 적절하게 문을 수정하십시오.</span><span class="sxs-lookup"><span data-stu-id="f8f14-125">Verify the following information and correct the statement as appropriate.</span></span>  
  
-   <span data-ttu-id="f8f14-126">개체 이름의 철자가 올바른지 여부.</span><span class="sxs-lookup"><span data-stu-id="f8f14-126">The object name is spelled correctly.</span></span>  
  
-   <span data-ttu-id="f8f14-127">현재의 데이터베이스 컨텍스트가 올바른지 여부.</span><span class="sxs-lookup"><span data-stu-id="f8f14-127">The current database context is correct.</span></span> <span data-ttu-id="f8f14-128">데이터베이스 이름이 지정되지 않은 개체는 현재 데이터베이스에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f14-128">If a database name for the object is not specified, the object must exist in the current database.</span></span> <span data-ttu-id="f8f14-129">데이터베이스 컨텍스트를 설정하는 방법은 [USE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8f14-129">For more information about setting the database context, see [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).</span></span>  
  
-   <span data-ttu-id="f8f14-130">개체가 시스템 테이블에 있는지 여부.</span><span class="sxs-lookup"><span data-stu-id="f8f14-130">The object exists in the system tables.</span></span> <span data-ttu-id="f8f14-131">테이블 또는 기타 스키마 범위 개체가 있는지 확인하려면 **sys.objects** 카탈로그 뷰를 쿼리하세요.</span><span class="sxs-lookup"><span data-stu-id="f8f14-131">To verify whether a table or other schema-scoped object exists, query the **sys.objects** catalog view.</span></span> <span data-ttu-id="f8f14-132">개체가 시스템 테이블에 없는 경우 개체가 삭제되었거나 사용자에게 해당 개체 메타데이터를 볼 수 있는 권한이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f8f14-132">If the object is not in the system tables, the object has been deleted, or the user does not have permissions to view the object metadata.</span></span> <span data-ttu-id="f8f14-133">개체 메타데이터를 볼 수 있는 권한에 대한 자세한 내용은 [메타데이터 표시 유형 구성](../security/metadata-visibility-configuration.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8f14-133">For more information about permissions to view object metadata, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
-   <span data-ttu-id="f8f14-134">개체가 사용자의 기본 스키마에 포함되어 있는지 여부.</span><span class="sxs-lookup"><span data-stu-id="f8f14-134">The object is contained in the default schema of the user.</span></span> <span data-ttu-id="f8f14-135">그렇지 않으면 *schema_name.object_name*과 같이 두 부분으로 구성된 형식을 사용하여 개체를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f14-135">If it is not, the object must be specified using the two-part format *schema_name.object_name*.</span></span> <span data-ttu-id="f8f14-136">스칼라 반환 함수는 항상 두 부분 이상으로 구성된 이름을 사용하여 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f14-136">Note that scalar-valued functions must always be invoked by using at least a two-part name.</span></span>  
  
-   <span data-ttu-id="f8f14-137">데이터베이스 데이터 정렬의 대/소문자 구분.</span><span class="sxs-lookup"><span data-stu-id="f8f14-137">The case sensitivity of the database collation.</span></span>  
  
     <span data-ttu-id="f8f14-138">데이터베이스에서 대/소문자 구분 데이터 정렬을 사용하면 개체 이름과 데이터베이스 개체의 대/소문자가 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f14-138">When a database uses a case-sensitive collation, the object name must match the case of the object in the database.</span></span> <span data-ttu-id="f8f14-139">예를 들어 대/소문자 구분 데이터 정렬을 사용하는 데이터베이스에서 개체가 **MyTable**로 지정된 경우 개체를 **mytable** 또는 **Mytable**로 지칭하는 쿼리는 개체 이름이 일치하지 않으므로 208 오류를 반환하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8f14-139">For example, when an object is specified as **MyTable** in a database with a case sensitive collation, queries that refer to the object as **mytable** or **Mytable** will cause error 208 to return because the object names do not match.</span></span>  
  
     <span data-ttu-id="f8f14-140">다음 문을 실행하여 데이터베이스 데이터 정렬을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f14-140">You can verify the database collation by running the following statement.</span></span>  
  
    ```  
    SELECT collation_name FROM sys.databases WHERE name = 'database_name';  
    ```  
  
     <span data-ttu-id="f8f14-141">데이터 정렬 이름의 약어 CS는 해당 데이터 정렬에서 대/소문자를 구분한다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="f8f14-141">The abbreviation CS in the collation name indicates the collation is case sensitive.</span></span> <span data-ttu-id="f8f14-142">예를 들어 Latin1_General_CS_AS는 대/소문자와 악센트를 구분하는 데이터 정렬입니다.</span><span class="sxs-lookup"><span data-stu-id="f8f14-142">For example, Latin1_General_CS_AS is a case sensitive, accent sensitive collation.</span></span> <span data-ttu-id="f8f14-143">CI는 대/소문자를 구분하지 않는 데이터 정렬을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f8f14-143">CI indicates a case insensitive collation.</span></span>  
  
-   <span data-ttu-id="f8f14-144">사용자에게 개체에 액세스할 수 있는 권한이 있는지 여부.</span><span class="sxs-lookup"><span data-stu-id="f8f14-144">The user has permission to access the object.</span></span> <span data-ttu-id="f8f14-145">사용자의 개체 사용 권한을 확인하려면 **Has_Perms_By_Name** 시스템 함수를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="f8f14-145">To verify the permissions the user has on the object, use the **Has_Perms_By_Name** system function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8f14-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f8f14-146">See Also</span></span>  
 <span data-ttu-id="f8f14-147">[&#40;Transact-sql&#41;사용](/sql/t-sql/language-elements/use-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f8f14-147">[USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql) </span></span>  
 <span data-ttu-id="f8f14-148">[메타 데이터 표시 유형 구성](../security/metadata-visibility-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="f8f14-148">[Metadata Visibility Configuration](../security/metadata-visibility-configuration.md) </span></span>  
 [<span data-ttu-id="f8f14-149">HAS_PERMS_BY_NAME&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f8f14-149">HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/has-perms-by-name-transact-sql)  
  
  
