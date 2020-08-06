---
title: MSSQLSERVER_10536 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 00d08f4555f38b61661a917ba94c023f9dd6c4a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734127"
---
# <a name="mssqlserver_10536"></a><span data-ttu-id="01658-102">MSSQLSERVER_10536</span><span class="sxs-lookup"><span data-stu-id="01658-102">MSSQLSERVER_10536</span></span>
    
## <a name="details"></a><span data-ttu-id="01658-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="01658-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="01658-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="01658-104">Product Name</span></span>|<span data-ttu-id="01658-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="01658-105">SQL Server</span></span>|  
|<span data-ttu-id="01658-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="01658-106">Event ID</span></span>|<span data-ttu-id="01658-107">10536</span><span class="sxs-lookup"><span data-stu-id="01658-107">10536</span></span>|  
|<span data-ttu-id="01658-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="01658-108">Event Source</span></span>|<span data-ttu-id="01658-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="01658-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="01658-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="01658-110">Component</span></span>|<span data-ttu-id="01658-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="01658-111">SQLEngine</span></span>|  
|<span data-ttu-id="01658-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="01658-112">Symbolic Name</span></span>|<span data-ttu-id="01658-113">PG_TOO_MANY_STMTS</span><span class="sxs-lookup"><span data-stu-id="01658-113">PG_TOO_MANY_STMTS</span></span>|  
|<span data-ttu-id="01658-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="01658-114">Message Text</span></span>|<span data-ttu-id="01658-115">지정된 `@plan_handle`에 해당하는 일괄 처리 또는 모듈에 적합한 문이 1000개 이상 포함되어 있으므로 계획 지침 '%\*\*ls'을(를) 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="01658-115">Cannot create plan guide '%.\*ls' because the batch or module corresponding to the specified `@plan_handle` contains more than 1000 eligible statements.</span></span> <span data-ttu-id="01658-116">각 문에 `statement_start_offset` 값을 지정하여 일괄 처리 또는 모듈의 각 문에 대해 계획 지침을 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="01658-116">Create a plan guide for each statement in the batch or module by specifying a `statement_start_offset` value for each statement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="01658-117">설명</span><span class="sxs-lookup"><span data-stu-id="01658-117">Explanation</span></span>  
 <span data-ttu-id="01658-118">지정된 `@plan_handle`에 해당하는 일괄 처리 또는 모듈에 적합한 문이 1000개 이상 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01658-118">The batch or module corresponding to the specified `@plan_handle` contains more than 1000 eligible statements.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="01658-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="01658-119">User Action</span></span>  
 <span data-ttu-id="01658-120">각 문에 `statement_start_offset` 값을 지정하여 일괄 처리 또는 모듈의 각 문에 대해 계획 지침을 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="01658-120">Create a plan guide for each statement in the batch or module by specifying a `statement_start_offset` value for each statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01658-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="01658-121">See Also</span></span>  
 <span data-ttu-id="01658-122">[sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="01658-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="01658-123">[계획 지침](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="01658-123">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="01658-124">sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="01658-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
