---
title: MSSQLSERVER_10534 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10534 (Database Engine error)
ms.assetid: e65bb118-99d5-4fdb-b1d5-0ec70f0a677b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 793bb0bf5048e30624d9566f65e7c6752bd14386
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731700"
---
# <a name="mssqlserver_10534"></a><span data-ttu-id="c927b-102">MSSQLSERVER_10534</span><span class="sxs-lookup"><span data-stu-id="c927b-102">MSSQLSERVER_10534</span></span>
    
## <a name="details"></a><span data-ttu-id="c927b-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="c927b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c927b-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="c927b-104">Product Name</span></span>|<span data-ttu-id="c927b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c927b-105">SQL Server</span></span>|  
|<span data-ttu-id="c927b-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="c927b-106">Event ID</span></span>|<span data-ttu-id="c927b-107">10534</span><span class="sxs-lookup"><span data-stu-id="c927b-107">10534</span></span>|  
|<span data-ttu-id="c927b-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="c927b-108">Event Source</span></span>|<span data-ttu-id="c927b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c927b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c927b-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="c927b-110">Component</span></span>|<span data-ttu-id="c927b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c927b-111">SQLEngine</span></span>|  
|<span data-ttu-id="c927b-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="c927b-112">Symbolic Name</span></span>|<span data-ttu-id="c927b-113">PG_INVALID_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c927b-113">PG_INVALID_PARAMS</span></span>|  
|<span data-ttu-id="c927b-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="c927b-114">Message Text</span></span>|<span data-ttu-id="c927b-115">`@params`에 지정된 값이 잘못되었으므로 계획 지침 '%.\*ls'을(를) 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c927b-115">Cannot create plan guide '%.\*ls' because the value specified for `@params` is invalid.</span></span> <span data-ttu-id="c927b-116">*parameter_name parameter_type* 형식으로 값을 지정하거나 NULL을 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="c927b-116">Specify the value in the form *parameter_name parameter_type*, or specify NULL.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c927b-117">설명</span><span class="sxs-lookup"><span data-stu-id="c927b-117">Explanation</span></span>  
 <span data-ttu-id="c927b-118">`@params`에 지정된 값이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c927b-118">The value specified for `@params` is invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c927b-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="c927b-119">User Action</span></span>  
 <span data-ttu-id="c927b-120">*parameter_name parameter_type* 형식으로 값을 지정하거나 NULL을 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="c927b-120">Specify the value in the form *parameter_name parameter_type*, or specify NULL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c927b-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c927b-121">See Also</span></span>  
 <span data-ttu-id="c927b-122">[계획 지침](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="c927b-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="c927b-123">[sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c927b-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="c927b-124">sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c927b-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
