---
title: MSSQLSERVER_10531 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10531 (Database Engine error)
ms.assetid: bb40e994-231c-44ce-933f-8d767fb2f450
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6230c046a9eb7b900377888c59a3a492f2b89f73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731704"
---
# <a name="mssqlserver_10531"></a><span data-ttu-id="358ba-102">MSSQLSERVER_10531</span><span class="sxs-lookup"><span data-stu-id="358ba-102">MSSQLSERVER_10531</span></span>
    
## <a name="details"></a><span data-ttu-id="358ba-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="358ba-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="358ba-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="358ba-104">Product Name</span></span>|<span data-ttu-id="358ba-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="358ba-105">SQL Server</span></span>|  
|<span data-ttu-id="358ba-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="358ba-106">Event ID</span></span>|<span data-ttu-id="358ba-107">10531</span><span class="sxs-lookup"><span data-stu-id="358ba-107">10531</span></span>|  
|<span data-ttu-id="358ba-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="358ba-108">Event Source</span></span>|<span data-ttu-id="358ba-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="358ba-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="358ba-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="358ba-110">Component</span></span>|<span data-ttu-id="358ba-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="358ba-111">SQLEngine</span></span>|  
|<span data-ttu-id="358ba-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="358ba-112">Symbolic Name</span></span>|<span data-ttu-id="358ba-113">PG_NO_ELIGIBLE_STMT</span><span class="sxs-lookup"><span data-stu-id="358ba-113">PG_NO_ELIGIBLE_STMT</span></span>|  
|<span data-ttu-id="358ba-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="358ba-114">Message Text</span></span>|<span data-ttu-id="358ba-115">사용자에게 적절한 권한이 없으므로 캐시에서 계획 지침 '%.\*ls'을(를) 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="358ba-115">Cannot create plan guide '%.\*ls' from cache because the user does not have adequate permissions.</span></span> <span data-ttu-id="358ba-116">사용자가 계획 지침을 만들 수 있도록 VIEW SERVER STATE 권한을 부여하십시오.</span><span class="sxs-lookup"><span data-stu-id="358ba-116">Grant the VIEW SERVER STATE permission to the user creating the plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="358ba-117">설명</span><span class="sxs-lookup"><span data-stu-id="358ba-117">Explanation</span></span>  
 <span data-ttu-id="358ba-118">사용자에게 계획 캐시에서 지정된 계획 지침을 만들 수 있는 적절한 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="358ba-118">The user does not have adequate permissions to create the specified plan guide from the plan cache.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="358ba-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="358ba-119">User Action</span></span>  
 <span data-ttu-id="358ba-120">사용자가 계획 지침을 만들 수 있도록 VIEW SERVER STATE 권한을 부여하십시오.</span><span class="sxs-lookup"><span data-stu-id="358ba-120">Grant VIEW SERVER STATE permission to the user creating the plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="358ba-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="358ba-121">See Also</span></span>  
 <span data-ttu-id="358ba-122">[계획 지침](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="358ba-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="358ba-123">[sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="358ba-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="358ba-124">sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="358ba-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
