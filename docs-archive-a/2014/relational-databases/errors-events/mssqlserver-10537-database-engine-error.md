---
title: MSSQLSERVER_10537 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10537 (Database Engine error)
ms.assetid: 728469a4-6523-4a37-925f-a950d75420fa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b1baccad5236bd8c1a71024b7dd542cc9d11cbd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734128"
---
# <a name="mssqlserver_10537"></a><span data-ttu-id="a239c-102">MSSQLSERVER_10537</span><span class="sxs-lookup"><span data-stu-id="a239c-102">MSSQLSERVER_10537</span></span>
    
## <a name="details"></a><span data-ttu-id="a239c-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="a239c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a239c-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="a239c-104">Product Name</span></span>|<span data-ttu-id="a239c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a239c-105">SQL Server</span></span>|  
|<span data-ttu-id="a239c-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="a239c-106">Event ID</span></span>|<span data-ttu-id="a239c-107">10537</span><span class="sxs-lookup"><span data-stu-id="a239c-107">10537</span></span>|  
|<span data-ttu-id="a239c-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="a239c-108">Event Source</span></span>|<span data-ttu-id="a239c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a239c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a239c-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="a239c-110">Component</span></span>|<span data-ttu-id="a239c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a239c-111">SQLEngine</span></span>|  
|<span data-ttu-id="a239c-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="a239c-112">Symbolic Name</span></span>|<span data-ttu-id="a239c-113">PG_DUP_ENABLED</span><span class="sxs-lookup"><span data-stu-id="a239c-113">PG_DUP_ENABLED</span></span>|  
|<span data-ttu-id="a239c-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="a239c-114">Message Text</span></span>|<span data-ttu-id="a239c-115">활성화된 계획 지침 '%.\*ls'에 문의 시작 오프셋 값 및 동일한 범위가 들어 있으므로 계획 지침 '%.\*ls'을(를) 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a239c-115">Cannot enable plan guide '%.\*ls' because the enabled plan guide '%.\*ls' contains the same scope and starting offset value as the statement.</span></span> <span data-ttu-id="a239c-116">지정된 계획 지침을 활성화하기 전에 기존 계획 지침을 비활성화하십시오.</span><span class="sxs-lookup"><span data-stu-id="a239c-116">Disable the existing plan guide before enabling the specified plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a239c-117">설명</span><span class="sxs-lookup"><span data-stu-id="a239c-117">Explanation</span></span>  
 <span data-ttu-id="a239c-118">기존 계획 지침에 지정된 계획 지침의 문과 동일한 범위 및 시작 오프셋 값이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a239c-118">An existing plan guide contains the same scope and starting offset value as the statement in the specified plan guide.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a239c-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="a239c-119">User Action</span></span>  
 <span data-ttu-id="a239c-120">지정된 계획 지침을 활성화하기 전에 기존 계획 지침을 비활성화하십시오.</span><span class="sxs-lookup"><span data-stu-id="a239c-120">Disable the existing plan guide before enabling the specified plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a239c-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a239c-121">See Also</span></span>  
 <span data-ttu-id="a239c-122">[sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a239c-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="a239c-123">[계획 지침](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="a239c-123">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="a239c-124">sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a239c-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
