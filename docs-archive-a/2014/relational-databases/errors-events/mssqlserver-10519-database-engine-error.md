---
title: MSSQLSERVER_10519 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10519 (Database Engine error)
ms.assetid: 3be393a1-b186-41ae-afb9-a3d07ff354bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0ec584649842f787b1de9d2ea6d161aea6970250
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736364"
---
# <a name="mssqlserver_10519"></a><span data-ttu-id="23f76-102">MSSQLSERVER_10519</span><span class="sxs-lookup"><span data-stu-id="23f76-102">MSSQLSERVER_10519</span></span>
    
## <a name="details"></a><span data-ttu-id="23f76-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="23f76-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="23f76-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="23f76-104">Product Name</span></span>|<span data-ttu-id="23f76-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="23f76-105">SQL Server</span></span>|  
|<span data-ttu-id="23f76-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="23f76-106">Event ID</span></span>|<span data-ttu-id="23f76-107">10519</span><span class="sxs-lookup"><span data-stu-id="23f76-107">10519</span></span>|  
|<span data-ttu-id="23f76-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="23f76-108">Event Source</span></span>|<span data-ttu-id="23f76-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="23f76-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="23f76-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="23f76-110">Component</span></span>|<span data-ttu-id="23f76-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="23f76-111">SQLEngine</span></span>|  
|<span data-ttu-id="23f76-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="23f76-112">Symbolic Name</span></span>|<span data-ttu-id="23f76-113">PG_INCOMPATIBLE_STMT_AND_HINTS</span><span class="sxs-lookup"><span data-stu-id="23f76-113">PG_INCOMPATIBLE_STMT_AND_HINTS</span></span>|  
|<span data-ttu-id="23f76-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="23f76-114">Message Text</span></span>|<span data-ttu-id="23f76-115">`@hints`에 지정된 힌트를 `@stmt` 또는 `@statement_start_offset`으로 지정된 문에 적용할 수 없으므로 계획 지침 '%.\*ls'을(를) 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23f76-115">Cannot create plan guide '%.\*ls' because the hints specified in `@hints` cannot be applied to the statement specified by either `@stmt` or `@statement_start_offset`.</span></span> <span data-ttu-id="23f76-116">힌트를 문에 적용할 수 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="23f76-116">Verify that the hints can be applied to the statement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="23f76-117">설명</span><span class="sxs-lookup"><span data-stu-id="23f76-117">Explanation</span></span>  
 <span data-ttu-id="23f76-118">`@hints`에 지정된 힌트를 `@stmt` 또는 `@statement_start_offset`으로 지정된 문에 적용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23f76-118">The hints specified in `@hints` cannot be applied to the statement specified by either `@stmt` or `@statement_start_offset`.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="23f76-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="23f76-119">User Action</span></span>  
 <span data-ttu-id="23f76-120">문에 적용할 수 있는 힌트를 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="23f76-120">Specify hints that can be applied to the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f76-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="23f76-121">See Also</span></span>  
 <span data-ttu-id="23f76-122">[sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="23f76-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="23f76-123">[계획 지침](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="23f76-123">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="23f76-124">sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="23f76-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
