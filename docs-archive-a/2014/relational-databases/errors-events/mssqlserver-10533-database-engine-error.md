---
title: MSSQLSERVER_10533 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10533 (Database Engine error)
ms.assetid: cc2fbdab-7b90-415f-a1f9-066824344283
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ccef25bc8f594cb6ea0b60aefab838ef27cda6f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651054"
---
# <a name="mssqlserver_10533"></a><span data-ttu-id="c9781-102">MSSQLSERVER_10533</span><span class="sxs-lookup"><span data-stu-id="c9781-102">MSSQLSERVER_10533</span></span>
    
## <a name="details"></a><span data-ttu-id="c9781-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="c9781-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c9781-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="c9781-104">Product Name</span></span>|<span data-ttu-id="c9781-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c9781-105">SQL Server</span></span>|  
|<span data-ttu-id="c9781-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="c9781-106">Event ID</span></span>|<span data-ttu-id="c9781-107">10533</span><span class="sxs-lookup"><span data-stu-id="c9781-107">10533</span></span>|  
|<span data-ttu-id="c9781-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="c9781-108">Event Source</span></span>|<span data-ttu-id="c9781-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c9781-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c9781-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="c9781-110">Component</span></span>|<span data-ttu-id="c9781-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c9781-111">SQLEngine</span></span>|  
|<span data-ttu-id="c9781-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="c9781-112">Symbolic Name</span></span>|<span data-ttu-id="c9781-113">PG_NAME_TOO_BIG</span><span class="sxs-lookup"><span data-stu-id="c9781-113">PG_NAME_TOO_BIG</span></span>|  
|<span data-ttu-id="c9781-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="c9781-114">Message Text</span></span>|<span data-ttu-id="c9781-115">계획 지침 이름이 허용된 최대 문자 수인 124자를 초과하므로 계획 지침 '%.\*ls'을(를) 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9781-115">Cannot create plan guide '%.\*ls' because the plan guide name exceeds 124 characters, the maximum number allowed.</span></span> <span data-ttu-id="c9781-116">125자 미만의 이름을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="c9781-116">Specify a name that contains fewer than 125 characters.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c9781-117">설명</span><span class="sxs-lookup"><span data-stu-id="c9781-117">Explanation</span></span>  
 <span data-ttu-id="c9781-118">계획 지침 이름이 허용된 최대 문자 수인 124자를 초과합니다.</span><span class="sxs-lookup"><span data-stu-id="c9781-118">The plan guide name exceeds 124 characters, the maximum number allowed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c9781-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="c9781-119">User Action</span></span>  
 <span data-ttu-id="c9781-120">125자 미만의 이름을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="c9781-120">Specify a name that contains fewer than 125 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9781-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c9781-121">See Also</span></span>  
 <span data-ttu-id="c9781-122">[계획 지침](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="c9781-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="c9781-123">[sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9781-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="c9781-124">sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c9781-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
