---
title: MSSQLSERVER_10532 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26ab34c319eff62737eae337828247fdfd7e901b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740011"
---
# <a name="mssqlserver_10532"></a><span data-ttu-id="8b5b8-102">MSSQLSERVER_10532</span><span class="sxs-lookup"><span data-stu-id="8b5b8-102">MSSQLSERVER_10532</span></span>
    
## <a name="details"></a><span data-ttu-id="8b5b8-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="8b5b8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8b5b8-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="8b5b8-104">Product Name</span></span>|<span data-ttu-id="8b5b8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8b5b8-105">SQL Server</span></span>|  
|<span data-ttu-id="8b5b8-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="8b5b8-106">Event ID</span></span>|<span data-ttu-id="8b5b8-107">10532</span><span class="sxs-lookup"><span data-stu-id="8b5b8-107">10532</span></span>|  
|<span data-ttu-id="8b5b8-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="8b5b8-108">Event Source</span></span>|<span data-ttu-id="8b5b8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8b5b8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8b5b8-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="8b5b8-110">Component</span></span>|<span data-ttu-id="8b5b8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8b5b8-111">SQLEngine</span></span>|  
|<span data-ttu-id="8b5b8-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="8b5b8-112">Symbolic Name</span></span>|<span data-ttu-id="8b5b8-113">PG_NO_ELIGIBLE_STMT</span><span class="sxs-lookup"><span data-stu-id="8b5b8-113">PG_NO_ELIGIBLE_STMT</span></span>|  
|<span data-ttu-id="8b5b8-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="8b5b8-114">Message Text</span></span>|<span data-ttu-id="8b5b8-115">`@plan_handle`로 지정된 일괄 처리 또는 모듈이 계획 지침에 적합한 문을 포함하지 않으므로 계획 지침 '%.\*ls'을(를) 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8b5b8-115">Cannot create plan guide '%.\*ls' because the batch or module specified by `@plan_handle` does not contain a statement that is eligible for a plan guide.</span></span> <span data-ttu-id="8b5b8-116">`@plan_handle`에 다른 값을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="8b5b8-116">Specify a different value for `@plan_handle`.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8b5b8-117">설명</span><span class="sxs-lookup"><span data-stu-id="8b5b8-117">Explanation</span></span>  
 <span data-ttu-id="8b5b8-118">`@plan_handle`로 지정된 일괄 처리 또는 모듈이 계획 지침에 적합한 문을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b5b8-118">The batch or module specified by `@plan_handle` does not contain a statement that is eligible for a plan guide.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8b5b8-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="8b5b8-119">User Action</span></span>  
 <span data-ttu-id="8b5b8-120">`@plan_handle`에 다른 값을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="8b5b8-120">Specify a different value for `@plan_handle`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5b8-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8b5b8-121">See Also</span></span>  
 <span data-ttu-id="8b5b8-122">[계획 지침](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="8b5b8-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="8b5b8-123">[sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8b5b8-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="8b5b8-124">sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8b5b8-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
