---
title: MSSQLSERVER_10520 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10520 (Database Engine error)
ms.assetid: cc8799f1-5b90-4248-b209-e1d5087f9529
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b8bdf080703fa6bd02fc34b8c31f59407814b93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731711"
---
# <a name="mssqlserver_10520"></a><span data-ttu-id="beac5-102">MSSQLSERVER_10520</span><span class="sxs-lookup"><span data-stu-id="beac5-102">MSSQLSERVER_10520</span></span>
    
## <a name="details"></a><span data-ttu-id="beac5-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="beac5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="beac5-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="beac5-104">Product Name</span></span>|<span data-ttu-id="beac5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="beac5-105">SQL Server</span></span>|  
|<span data-ttu-id="beac5-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="beac5-106">Event ID</span></span>|<span data-ttu-id="beac5-107">10520</span><span class="sxs-lookup"><span data-stu-id="beac5-107">10520</span></span>|  
|<span data-ttu-id="beac5-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="beac5-108">Event Source</span></span>|<span data-ttu-id="beac5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="beac5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="beac5-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="beac5-110">Component</span></span>|<span data-ttu-id="beac5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="beac5-111">SQLEngine</span></span>|  
|<span data-ttu-id="beac5-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="beac5-112">Symbolic Name</span></span>|<span data-ttu-id="beac5-113">PG_PARAM_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="beac5-113">PG_PARAM_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="beac5-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="beac5-114">Message Text</span></span>|<span data-ttu-id="beac5-115">@type이 '%ls'(으)로 지정되었고 매개 변수 '%ls'에 NULL이 아닌 값이 지정되었으므로 계획 지침 '%.\*ls'을(를) 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="beac5-115">Cannot create plan guide '%.\*ls' because @type was specified as '%ls' and a non-NULL value is specified for the parameter '%ls'.</span></span> <span data-ttu-id="beac5-116">이 유형은 매개 변수에 NULL 값이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="beac5-116">This type requires a NULL value for the parameter.</span></span> <span data-ttu-id="beac5-117">매개 변수에 NULL을 지정하거나, 매개 변수에 NULL이 아닌 값을 허용하는 유형으로 유형을 변경하십시오.</span><span class="sxs-lookup"><span data-stu-id="beac5-117">Specify NULL for the parameter, or change the type to one that allows a non-NULL value for the parameter.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="beac5-118">설명</span><span class="sxs-lookup"><span data-stu-id="beac5-118">Explanation</span></span>  
 <span data-ttu-id="beac5-119">@type에 지정된 유형에서 지정된 매개 변수에 NULL 값이 필요하지만 NULL이 아닌 값이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="beac5-119">The type specified in @type requires a NULL value for the specified parameter, however a non-NULL value was supplied.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="beac5-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="beac5-120">User Action</span></span>  
 <span data-ttu-id="beac5-121">매개 변수에 NULL을 지정하거나, 매개 변수에 NULL이 아닌 값을 허용하는 유형으로 유형을 변경하십시오.</span><span class="sxs-lookup"><span data-stu-id="beac5-121">Specify NULL for the parameter, or change the type to one that allows a non-NULL value for the parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beac5-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="beac5-122">See Also</span></span>  
 <span data-ttu-id="beac5-123">[sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="beac5-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="beac5-124">계획 지침</span><span class="sxs-lookup"><span data-stu-id="beac5-124">Plan Guides</span></span>](../performance/plan-guides.md)  
  
  
