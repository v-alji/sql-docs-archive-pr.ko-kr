---
title: MSSQLSERVER_10521 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10521 (Database Engine error)
ms.assetid: ba2d7e44-207c-4428-b5f0-c975ac122c0d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c034bd13e212b9b39bfd348353d59e23fc748079
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731707"
---
# <a name="mssqlserver_10521"></a><span data-ttu-id="e2b6d-102">MSSQLSERVER_10521</span><span class="sxs-lookup"><span data-stu-id="e2b6d-102">MSSQLSERVER_10521</span></span>
    
## <a name="details"></a><span data-ttu-id="e2b6d-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="e2b6d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e2b6d-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="e2b6d-104">Product Name</span></span>|<span data-ttu-id="e2b6d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e2b6d-105">SQL Server</span></span>|  
|<span data-ttu-id="e2b6d-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="e2b6d-106">Event ID</span></span>|<span data-ttu-id="e2b6d-107">10521</span><span class="sxs-lookup"><span data-stu-id="e2b6d-107">10521</span></span>|  
|<span data-ttu-id="e2b6d-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="e2b6d-108">Event Source</span></span>|<span data-ttu-id="e2b6d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e2b6d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e2b6d-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="e2b6d-110">Component</span></span>|<span data-ttu-id="e2b6d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e2b6d-111">SQLEngine</span></span>|  
|<span data-ttu-id="e2b6d-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="e2b6d-112">Symbolic Name</span></span>|<span data-ttu-id="e2b6d-113">PG_PARAM_NEEDED</span><span class="sxs-lookup"><span data-stu-id="e2b6d-113">PG_PARAM_NEEDED</span></span>|  
|<span data-ttu-id="e2b6d-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="e2b6d-114">Message Text</span></span>|<span data-ttu-id="e2b6d-115">`@type`이 '%ls'(으)로 지정되었고 매개 변수 '%ls'이(가) NULL이므로 계획 지침 '%.\*ls'을(를) 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2b6d-115">Cannot create plan guide '%.\*ls' because `@type` was specified as '%ls' and the parameter '%ls' is NULL.</span></span> <span data-ttu-id="e2b6d-116">이 유형은 매개 변수에 NULL이 아닌 값이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e2b6d-116">This type requires a non-NULL value for the parameter.</span></span> <span data-ttu-id="e2b6d-117">매개 변수에 NULL이 아닌 값을 지정하거나, 매개 변수에 NULL 값을 허용하는 유형으로 유형을 변경하십시오.</span><span class="sxs-lookup"><span data-stu-id="e2b6d-117">Specify a non-NULL value for the parameter, or change the type to one that allows a NULL value for the parameter.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e2b6d-118">설명</span><span class="sxs-lookup"><span data-stu-id="e2b6d-118">Explanation</span></span>  
 <span data-ttu-id="e2b6d-119">`@type`에 지정된 유형이 지정된 매개 변수에 대해 NULL 값을 허용하지 않지만 NULL 값이 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e2b6d-119">The type specified in `@type` requires a non-NULL value for the specified parameter; however a NULL value was supplied.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e2b6d-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="e2b6d-120">User Action</span></span>  
 <span data-ttu-id="e2b6d-121">매개 변수에 NULL이 아닌 값을 지정하거나, 매개 변수에 NULL 값을 허용하는 유형으로 유형을 변경하십시오.</span><span class="sxs-lookup"><span data-stu-id="e2b6d-121">Specify a non-NULL value for the parameter, or change the type to one that allows a NULL value for the parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2b6d-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2b6d-122">See Also</span></span>  
 <span data-ttu-id="e2b6d-123">[sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e2b6d-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="e2b6d-124">[계획 지침](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="e2b6d-124">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="e2b6d-125">sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2b6d-125">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
