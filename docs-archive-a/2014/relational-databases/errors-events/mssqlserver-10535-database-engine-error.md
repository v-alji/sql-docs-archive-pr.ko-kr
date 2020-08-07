---
title: MSSQLSERVER_10535 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10535 (Database Engine error)
ms.assetid: 478fd978-11d9-4155-8329-f599fdbec14b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 439d282f18490a4353d6528276eaf7e4231c503b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731695"
---
# <a name="mssqlserver_10535"></a><span data-ttu-id="b4905-102">MSSQLSERVER_10535</span><span class="sxs-lookup"><span data-stu-id="b4905-102">MSSQLSERVER_10535</span></span>
    
## <a name="details"></a><span data-ttu-id="b4905-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="b4905-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b4905-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="b4905-104">Product Name</span></span>|<span data-ttu-id="b4905-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b4905-105">SQL Server</span></span>|  
|<span data-ttu-id="b4905-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="b4905-106">Event ID</span></span>|<span data-ttu-id="b4905-107">10535</span><span class="sxs-lookup"><span data-stu-id="b4905-107">10535</span></span>|  
|<span data-ttu-id="b4905-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="b4905-108">Event Source</span></span>|<span data-ttu-id="b4905-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b4905-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b4905-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="b4905-110">Component</span></span>|<span data-ttu-id="b4905-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b4905-111">SQLEngine</span></span>|  
|<span data-ttu-id="b4905-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="b4905-112">Symbolic Name</span></span>|<span data-ttu-id="b4905-113">PG_NO_PLAN</span><span class="sxs-lookup"><span data-stu-id="b4905-113">PG_NO_PLAN</span></span>|  
|<span data-ttu-id="b4905-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="b4905-114">Message Text</span></span>|<span data-ttu-id="b4905-115">지정된 계획 핸들에 해당하는 계획 캐시에 계획이 없으므로 계획 지침 '%.\*ls'을(를) 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4905-115">Cannot create plan guide '%.\*ls' because a plan was not found in the plan cache that corresponds to the specified plan handle.</span></span> <span data-ttu-id="b4905-116">캐시된 계획 핸들을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4905-116">Specify a cached plan handle.</span></span> <span data-ttu-id="b4905-117">캐시된 계획 핸들 목록을 보려면 sys.dm_exec_query_stats 동적 관리 뷰를 쿼리하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4905-117">For a list of cached plan handles, query the sys.dm_exec_query_stats dynamic management view.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b4905-118">설명</span><span class="sxs-lookup"><span data-stu-id="b4905-118">Explanation</span></span>  
 <span data-ttu-id="b4905-119">지정된 계획 핸들에 해당하는 계획 캐시에 계획이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4905-119">A plan was not found in the plan cache that corresponds to the specified plan handle.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b4905-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="b4905-120">User Action</span></span>  
 <span data-ttu-id="b4905-121">캐시된 계획 핸들을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4905-121">Specify a cached plan handle.</span></span> <span data-ttu-id="b4905-122">캐시된 계획 핸들 목록을 보려면 sys.dm_exec_query_stats 동적 관리 뷰를 쿼리하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4905-122">For a list of cached plan handles, query the sys.dm_exec_query_stats dynamic management view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4905-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4905-123">See Also</span></span>  
 <span data-ttu-id="b4905-124">[sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b4905-124">[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) </span></span>  
 [<span data-ttu-id="b4905-125">sys.dm_exec_query_stats&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b4905-125">sys.dm_exec_query_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql)  
  
  
