---
title: MSSQLSERVER_10509 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10509 (Database Engine error)
ms.assetid: e9dd5357-ee3d-420a-9a89-d12ab5404e73
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 73194c7da553bf27acb78d8c4e7d71bc93f457d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741060"
---
# <a name="mssqlserver_10509"></a><span data-ttu-id="82708-102">MSSQLSERVER_10509</span><span class="sxs-lookup"><span data-stu-id="82708-102">MSSQLSERVER_10509</span></span>
    
## <a name="details"></a><span data-ttu-id="82708-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="82708-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="82708-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="82708-104">Product Name</span></span>|<span data-ttu-id="82708-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="82708-105">SQL Server</span></span>|  
|<span data-ttu-id="82708-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="82708-106">Event ID</span></span>|<span data-ttu-id="82708-107">10509</span><span class="sxs-lookup"><span data-stu-id="82708-107">10509</span></span>|  
|<span data-ttu-id="82708-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="82708-108">Event Source</span></span>|<span data-ttu-id="82708-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="82708-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="82708-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="82708-110">Component</span></span>|<span data-ttu-id="82708-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="82708-111">SQLEngine</span></span>|  
|<span data-ttu-id="82708-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="82708-112">Symbolic Name</span></span>|<span data-ttu-id="82708-113">PG_INVALID_STMT</span><span class="sxs-lookup"><span data-stu-id="82708-113">PG_INVALID_STMT</span></span>|  
|<span data-ttu-id="82708-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="82708-114">Message Text</span></span>|<span data-ttu-id="82708-115">`@stmt` 또는 `@statement_start_offset`으로 지정된 문에 구문 오류가 있거나 계획 지침으로 사용하기에 적합하지 않아 계획 지침 '%.\*ls'을(를) 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82708-115">Cannot create plan guide '%.\*ls' because the statement specified by `@stmt` or `@statement_start_offset` either contains a syntax error or is ineligible for use in a plan guide.</span></span> <span data-ttu-id="82708-116">올바른 단일 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문 또는 일괄 처리 안에 있는 문의 올바른 시작 위치를 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="82708-116">Provide a single valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or a valid starting position of the statement within the batch.</span></span> <span data-ttu-id="82708-117">올바른 시작 위치를 가져오려면 sys.dm_exec_query_stats 동적 관리 함수의 statement_start_offset 열을 쿼리하십시오.</span><span class="sxs-lookup"><span data-stu-id="82708-117">To obtain a valid starting position, query the statement_start_offset column in the sys.dm_exec_query_stats dynamic management function.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="82708-118">설명</span><span class="sxs-lookup"><span data-stu-id="82708-118">Explanation</span></span>  
 <span data-ttu-id="82708-119">`@stmt` 또는 `@statement_start_offset`으로 지정된 문에 구문 오류가 있거나 계획 지침으로 사용하기에 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82708-119">The statement specified by `@stmt` or `@statement_start_offset` either contains a syntax error or is ineligible for use in a plan guide.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="82708-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="82708-120">User Action</span></span>  
 <span data-ttu-id="82708-121">올바른 단일 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문 또는 일괄 처리 안에 있는 문의 올바른 시작 위치를 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="82708-121">Provide a single valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or a valid starting position of the statement within the batch.</span></span> <span data-ttu-id="82708-122">올바른 시작 위치를 가져오려면 sys.dm_exec_query_stats 동적 관리 함수의 statement_start_offset 열을 쿼리하십시오.</span><span class="sxs-lookup"><span data-stu-id="82708-122">To obtain a valid starting position, query the statement_start_offset column in the sys.dm_exec_query_stats dynamic management function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82708-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82708-123">See Also</span></span>  
 <span data-ttu-id="82708-124">[sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="82708-124">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="82708-125">[계획 지침](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="82708-125">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="82708-126">[dm_exec_query_stats &#40;Transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="82708-126">[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql) </span></span>  
 [<span data-ttu-id="82708-127">sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="82708-127">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
