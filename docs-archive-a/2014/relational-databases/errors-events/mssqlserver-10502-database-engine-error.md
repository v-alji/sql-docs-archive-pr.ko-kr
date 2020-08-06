---
title: MSSQLSERVER_10502 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10502 (Database Engine error)
ms.assetid: 26d9b64d-4299-4b55-92d0-0a32a3688c0a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: eeec3a3adf318cadc96501938f8a5565f1c07670
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646539"
---
# <a name="mssqlserver_10502"></a><span data-ttu-id="7f521-102">MSSQLSERVER_10502</span><span class="sxs-lookup"><span data-stu-id="7f521-102">MSSQLSERVER_10502</span></span>
    
## <a name="details"></a><span data-ttu-id="7f521-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="7f521-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7f521-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="7f521-104">Product Name</span></span>|<span data-ttu-id="7f521-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7f521-105">SQL Server</span></span>|  
|<span data-ttu-id="7f521-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="7f521-106">Event ID</span></span>|<span data-ttu-id="7f521-107">10502</span><span class="sxs-lookup"><span data-stu-id="7f521-107">10502</span></span>|  
|<span data-ttu-id="7f521-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="7f521-108">Event Source</span></span>|<span data-ttu-id="7f521-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7f521-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7f521-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="7f521-110">Component</span></span>|<span data-ttu-id="7f521-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7f521-111">SQLEngine</span></span>|  
|<span data-ttu-id="7f521-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="7f521-112">Symbolic Name</span></span>|<span data-ttu-id="7f521-113">PG_DUP_FOUND</span><span class="sxs-lookup"><span data-stu-id="7f521-113">PG_DUP_FOUND</span></span>|  
|<span data-ttu-id="7f521-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="7f521-114">Message Text</span></span>|<span data-ttu-id="7f521-115">@stmt 및 @module_or_batch 또는 @plan_handle 및 @statement_start_offset으로 지정된 문이 데이터베이스의 기존 계획 지침 '%.\*ls'과(와) 일치하므로 계획 지침 '%.\*ls'을(를) 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7f521-115">Cannot create plan guide '%.\*ls' because the statement specified by @stmt and @module_or_batch, or by @plan_handle and @statement_start_offset, matches the existing plan guide '%.\*ls' in the database.</span></span> <span data-ttu-id="7f521-116">새 계획 지침을 만들기 전에 기존 계획 지침을 삭제하십시오.</span><span class="sxs-lookup"><span data-stu-id="7f521-116">Drop the existing plan guide before creating the new plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7f521-117">설명</span><span class="sxs-lookup"><span data-stu-id="7f521-117">Explanation</span></span>  
 <span data-ttu-id="7f521-118">지정된 문에 대한 계획 지침이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f521-118">A plan guide exists for the specified statement.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7f521-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="7f521-119">User Action</span></span>  
 <span data-ttu-id="7f521-120">새 계획 지침을 만들기 전에 기존 계획 지침을 삭제하십시오.</span><span class="sxs-lookup"><span data-stu-id="7f521-120">Drop the existing plan guide before creating the new plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f521-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7f521-121">See Also</span></span>  
 <span data-ttu-id="7f521-122">[계획 지침](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="7f521-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="7f521-123">[sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7f521-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="7f521-124">sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7f521-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
