---
title: MSSQLSERVER_10507 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10507 (Database Engine error)
ms.assetid: cd83fa81-ac37-4eda-a3c3-17610b051de2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a80e48948c03b370c07742fabbb3cf8eb3e74315
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738451"
---
# <a name="mssqlserver_10507"></a><span data-ttu-id="71260-102">MSSQLSERVER_10507</span><span class="sxs-lookup"><span data-stu-id="71260-102">MSSQLSERVER_10507</span></span>
    
## <a name="details"></a><span data-ttu-id="71260-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="71260-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="71260-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="71260-104">Product Name</span></span>|<span data-ttu-id="71260-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="71260-105">SQL Server</span></span>|  
|<span data-ttu-id="71260-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="71260-106">Event ID</span></span>|<span data-ttu-id="71260-107">10507</span><span class="sxs-lookup"><span data-stu-id="71260-107">10507</span></span>|  
|<span data-ttu-id="71260-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="71260-108">Event Source</span></span>|<span data-ttu-id="71260-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="71260-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="71260-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="71260-110">Component</span></span>|<span data-ttu-id="71260-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="71260-111">SQLEngine</span></span>|  
|<span data-ttu-id="71260-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="71260-112">Symbolic Name</span></span>|<span data-ttu-id="71260-113">PG_STMT_DOES_NOT_MATCH</span><span class="sxs-lookup"><span data-stu-id="71260-113">PG_STMT_DOES_NOT_MATCH</span></span>|  
|<span data-ttu-id="71260-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="71260-114">Message Text</span></span>|<span data-ttu-id="71260-115">`@stmt` 및 `@module_or_batch` 또는 `@plan_handle` 및 `@statement_start_offset`으로 지정된 문이 지정된 모듈 또는 일괄 처리 문과 일치하지 않아 계획 지침 '%.\*ls'을(를) 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="71260-115">Cannot create plan guide '%.\*ls' because the statement specified by `@stmt` and `@module_or_batch`, or by `@plan_handle` and `@statement_start_offset`, does not match any statement in the specified module or batch.</span></span> <span data-ttu-id="71260-116">모듈 또는 일괄 처리 문과 일치하도록 값을 수정하십시오.</span><span class="sxs-lookup"><span data-stu-id="71260-116">Modify the values to match a statement in the module or batch.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="71260-117">설명</span><span class="sxs-lookup"><span data-stu-id="71260-117">Explanation</span></span>  
 <span data-ttu-id="71260-118">지정한 모듈 또는 일괄 처리 문이 지정된 문 또는 문 오프셋 값과 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="71260-118">A statement in the specified module or batch could not be matched to the specified statement or statement offset value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="71260-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="71260-119">User Action</span></span>  
 <span data-ttu-id="71260-120">모듈 또는 일괄 처리 문과 일치하도록 지정된 매개 변수 값을 수정하십시오.</span><span class="sxs-lookup"><span data-stu-id="71260-120">Modify the specified parameter values to match a statement in the module or batch.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71260-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71260-121">See Also</span></span>  
 <span data-ttu-id="71260-122">[계획 지침](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="71260-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="71260-123">[sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="71260-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="71260-124">sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="71260-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
