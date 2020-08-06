---
title: MSSQLSERVER_10539 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10539 (Database Engine error)
ms.assetid: 49c26ff7-18b8-4f07-a087-f45f63463b3b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5fd1f190b8f5d3ab9755409bdd034fa374ea5314
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731683"
---
# <a name="mssqlserver_10539"></a><span data-ttu-id="62210-102">MSSQLSERVER_10539</span><span class="sxs-lookup"><span data-stu-id="62210-102">MSSQLSERVER_10539</span></span>
    
## <a name="details"></a><span data-ttu-id="62210-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="62210-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="62210-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="62210-104">Product Name</span></span>|<span data-ttu-id="62210-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="62210-105">SQL Server</span></span>|  
|<span data-ttu-id="62210-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="62210-106">Event ID</span></span>|<span data-ttu-id="62210-107">10539</span><span class="sxs-lookup"><span data-stu-id="62210-107">10539</span></span>|  
|<span data-ttu-id="62210-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="62210-108">Event Source</span></span>|<span data-ttu-id="62210-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="62210-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="62210-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="62210-110">Component</span></span>|<span data-ttu-id="62210-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="62210-111">SQLEngine</span></span>|  
|<span data-ttu-id="62210-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="62210-112">Symbolic Name</span></span>|<span data-ttu-id="62210-113">PG_NO_PLAN_FOR_STMT</span><span class="sxs-lookup"><span data-stu-id="62210-113">PG_NO_PLAN_FOR_STMT</span></span>|  
|<span data-ttu-id="62210-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="62210-114">Message Text</span></span>|<span data-ttu-id="62210-115">시작 오프셋이 %d인 문에 쿼리 계획을 사용할 수 없으므로 캐시에서 계획 지침 '%.\*ls'을(를) 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="62210-115">Cannot create plan guide '%.\*ls' from cache because a query plan is not available for the statement with start offset %d.</span></span> <span data-ttu-id="62210-116">이 문제는 아직 만들지 않은 데이터베이스 개체에 문이 종속될 때 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62210-116">This problem can occur if the statement depends on database objects that have not yet been created.</span></span> <span data-ttu-id="62210-117">필요한 모든 데이터베이스 개체가 있는지 확인하고 계획 지침을 만들기 전에 문을 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="62210-117">Make sure that all necessary database objects exist, and execute the statement before creating the plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="62210-118">설명</span><span class="sxs-lookup"><span data-stu-id="62210-118">Explanation</span></span>  
 <span data-ttu-id="62210-119">지정한 시작 오프셋을 가진 문에 대한 계획 캐시에서 쿼리 계획을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="62210-119">A query plan is not available in the plan cache for the statement with the specified starting offset.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="62210-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="62210-120">User Action</span></span>  
 <span data-ttu-id="62210-121">필요한 모든 데이터베이스 개체가 있는지 확인하고 계획 지침을 만들기 전에 문을 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="62210-121">Make sure that all necessary database objects exist, and execute the statement before creating the plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62210-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="62210-122">See Also</span></span>  
 [<span data-ttu-id="62210-123">sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="62210-123">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
