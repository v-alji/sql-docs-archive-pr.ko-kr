---
title: MSSQLSERVER_10538 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10538 (Database Engine error)
ms.assetid: 284d19b4-4979-4cbe-a9be-ac1104433c69
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: edc6abf192a3341f9b84c99e99071343cc882c3d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731688"
---
# <a name="mssqlserver_10538"></a><span data-ttu-id="28e40-102">MSSQLSERVER_10538</span><span class="sxs-lookup"><span data-stu-id="28e40-102">MSSQLSERVER_10538</span></span>
    
## <a name="details"></a><span data-ttu-id="28e40-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="28e40-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="28e40-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="28e40-104">Product Name</span></span>|<span data-ttu-id="28e40-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="28e40-105">SQL Server</span></span>|  
|<span data-ttu-id="28e40-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="28e40-106">Event ID</span></span>|<span data-ttu-id="28e40-107">10538</span><span class="sxs-lookup"><span data-stu-id="28e40-107">10538</span></span>|  
|<span data-ttu-id="28e40-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="28e40-108">Event Source</span></span>|<span data-ttu-id="28e40-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="28e40-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="28e40-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="28e40-110">Component</span></span>|<span data-ttu-id="28e40-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="28e40-111">SQLEngine</span></span>|  
|<span data-ttu-id="28e40-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="28e40-112">Symbolic Name</span></span>|<span data-ttu-id="28e40-113">PG_INVALID_PLANGUIDE_HANDLE</span><span class="sxs-lookup"><span data-stu-id="28e40-113">PG_INVALID_PLANGUIDE_HANDLE</span></span>|  
|<span data-ttu-id="28e40-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="28e40-114">Message Text</span></span>|<span data-ttu-id="28e40-115">계획 지침을 찾을 수 없습니다. 지정된 계획 지침 ID가 NULL이거나 잘못되었거나 계획 지침에서 참조하는 개체에 대한 사용 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="28e40-115">Cannot find the plan guide either because the specified plan guide ID is NULL or invalid, or you do not have permission on the object referenced by the plan guide.</span></span> <span data-ttu-id="28e40-116">계획 지침 ID가 올바른지, 현재 세션이 올바른 데이터베이스 컨텍스트로 설정되어 있는지, 계획 지침에서 참조하는 개체에 대한 ALTER 권한 또는 ALTER DATABASE 권한이 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="28e40-116">Verify that the plan guide ID is valid, the current session is set to the correct database context, and you have either ALTER DATABASE permission or ALTER permission on the object referenced by the plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="28e40-117">설명</span><span class="sxs-lookup"><span data-stu-id="28e40-117">Explanation</span></span>  
 <span data-ttu-id="28e40-118">지정된 계획 지침 ID가 NULL이거나 잘못되었거나 계획 지침에서 참조하는 개체에 대한 사용 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="28e40-118">The ID of the specified plan guide is NULL or invalid, or you do not have permission on the object referenced by the plan guide.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="28e40-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="28e40-119">User Action</span></span>  
 <span data-ttu-id="28e40-120">계획 지침 ID가 올바른지, 현재 세션이 올바른 데이터베이스 컨텍스트로 설정되어 있는지, 계획 지침에서 참조하는 개체에 대한 ALTER 권한 또는 ALTER DATABASE 권한이 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="28e40-120">Verify that the plan guide ID is valid, the current session is set to the correct database context, and you have ALTER DATABASE permission or ALTER permission on the object referenced by the plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28e40-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="28e40-121">See Also</span></span>  
 <span data-ttu-id="28e40-122">[sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="28e40-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="28e40-123">[계획 지침](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="28e40-123">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="28e40-124">sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="28e40-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
