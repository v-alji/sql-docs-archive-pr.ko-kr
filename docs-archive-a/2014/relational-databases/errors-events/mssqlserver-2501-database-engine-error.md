---
title: MSSQLSERVER_2501 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2501 (Database Engine error)
ms.assetid: 895aafe3-a4e7-4ed8-acc5-93be76ef3664
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 200997dcfe7bf8a5933b9fce492daabd5baffd04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734099"
---
# <a name="mssqlserver_2501"></a><span data-ttu-id="9215f-102">MSSQLSERVER_2501</span><span class="sxs-lookup"><span data-stu-id="9215f-102">MSSQLSERVER_2501</span></span>
    
## <a name="details"></a><span data-ttu-id="9215f-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="9215f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9215f-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="9215f-104">Product Name</span></span>|<span data-ttu-id="9215f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9215f-105">SQL Server</span></span>|  
|<span data-ttu-id="9215f-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="9215f-106">Event ID</span></span>|<span data-ttu-id="9215f-107">2501</span><span class="sxs-lookup"><span data-stu-id="9215f-107">2501</span></span>|  
|<span data-ttu-id="9215f-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="9215f-108">Event Source</span></span>|<span data-ttu-id="9215f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9215f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9215f-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="9215f-110">Component</span></span>|<span data-ttu-id="9215f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9215f-111">SQLEngine</span></span>|  
|<span data-ttu-id="9215f-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="9215f-112">Symbolic Name</span></span>|<span data-ttu-id="9215f-113">DBCC_NO_SUCH_TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9215f-113">DBCC_NO_SUCH_TABLE_NAME</span></span>|  
|<span data-ttu-id="9215f-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="9215f-114">Message Text</span></span>|<span data-ttu-id="9215f-115">이름이 'NAME'인 테이블 또는 개체를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9215f-115">Cannot find a table or object with the name 'NAME'.</span></span> <span data-ttu-id="9215f-116">시스템 카탈로그를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="9215f-116">Check the system catalog.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9215f-117">설명</span><span class="sxs-lookup"><span data-stu-id="9215f-117">Explanation</span></span>  
 <span data-ttu-id="9215f-118">지정한 개체를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9215f-118">The specified object cannot be found.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="9215f-119">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="9215f-119">Possible Causes</span></span>  
 <span data-ttu-id="9215f-120">이 오류는 다음과 같은 문제로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9215f-120">This error can be caused by one of the following problems:</span></span>  
  
-   <span data-ttu-id="9215f-121">개체가 올바르게 지정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="9215f-121">The object is not specified correctly.</span></span>  
  
-   <span data-ttu-id="9215f-122">개체가 없거나 문에서 사용하기 전에 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9215f-122">The object does not exist, or the object was dropped before a statement tried to use it.</span></span>  
  
-   <span data-ttu-id="9215f-123">개체가 있지만 사용자에게 표시되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="9215f-123">The object might exist, but could not be exposed to the user.</span></span> <span data-ttu-id="9215f-124">예를 들어 사용자에게 해당 개체에 대한 사용 권한이 없거나 해당 개체가 사용자에게 표시되지 않는 내부 테이블일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9215f-124">For example, the user might not have permissions on the object, or the object is an internal table that could not be seen by a user.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9215f-125">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="9215f-125">User Action</span></span>  
  
-   <span data-ttu-id="9215f-126">현재의 데이터베이스 컨텍스트가 올바른지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="9215f-126">Verify the current database context is correct.</span></span> <span data-ttu-id="9215f-127">자세한 내용은 [USE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9215f-127">For more information, see [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).</span></span>  
  
-   <span data-ttu-id="9215f-128">테이블 또는 개체 이름의 철자가 올바른지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="9215f-128">Verify that the table or object name is spelled correctly.</span></span>  
  
-   <span data-ttu-id="9215f-129">개체가 포함된 스키마 이름을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="9215f-129">Verify the schema name that contains the object.</span></span> <span data-ttu-id="9215f-130">기본(**dbo**) 스키마가 아닌 다른 스키마에 개체가 속할 경우 두 부분으로 구성된 형식 *schema_name.object_name*을 사용하여 테이블 또는 개체 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9215f-130">If the object belongs to a schema other than the default (**dbo**) schema, you must specify the table or object name by using the two-part format *schema_name.object_name*.</span></span>  
  
-   <span data-ttu-id="9215f-131">개체가 시스템 테이블에 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="9215f-131">Verify that the object exists in the system tables.</span></span> <span data-ttu-id="9215f-132">테이블 또는 기타 스키마 범위 개체가 있는지 확인하려면 [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) 카탈로그 뷰를 쿼리하세요.</span><span class="sxs-lookup"><span data-stu-id="9215f-132">To verify whether a table or other schema-scoped object exists, query the [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) catalog view.</span></span> <span data-ttu-id="9215f-133">개체가 시스템 테이블에 없는 경우 개체가 삭제되었거나 사용자에게 해당 개체 메타데이터를 볼 수 있는 권한이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9215f-133">If the object is not in the system tables, the object has been deleted, or the user does not have permissions to view the object metadata.</span></span> <span data-ttu-id="9215f-134">개체 메타데이터를 보는 방법에 대한 자세한 내용은 [메타데이터 표시 유형 구성](../security/metadata-visibility-configuration.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9215f-134">For more information about how to view object metadata, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9215f-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9215f-135">See Also</span></span>  
 [<span data-ttu-id="9215f-136">카탈로그 뷰&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9215f-136">Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql)  
  
  
