---
title: MSSQLSERVER_8649 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b39ed0d8ffe5f7f601b6cb1393596d0d6546e557
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652850"
---
# <a name="mssqlserver_8649"></a><span data-ttu-id="129fe-102">MSSQLSERVER_8649</span><span class="sxs-lookup"><span data-stu-id="129fe-102">MSSQLSERVER_8649</span></span>
    
## <a name="details"></a><span data-ttu-id="129fe-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="129fe-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="129fe-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="129fe-104">Product Name</span></span>|<span data-ttu-id="129fe-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="129fe-105">SQL Server</span></span>|  
|<span data-ttu-id="129fe-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="129fe-106">Event ID</span></span>|<span data-ttu-id="129fe-107">8649</span><span class="sxs-lookup"><span data-stu-id="129fe-107">8649</span></span>|  
|<span data-ttu-id="129fe-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="129fe-108">Event Source</span></span>|<span data-ttu-id="129fe-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="129fe-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="129fe-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="129fe-110">Component</span></span>|<span data-ttu-id="129fe-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="129fe-111">SQLEngine</span></span>|  
|<span data-ttu-id="129fe-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="129fe-112">Symbolic Name</span></span>|<span data-ttu-id="129fe-113">COST_TOO_HIGH</span><span class="sxs-lookup"><span data-stu-id="129fe-113">COST_TOO_HIGH</span></span>|  
|<span data-ttu-id="129fe-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="129fe-114">Message Text</span></span>|<span data-ttu-id="129fe-115">이 쿼리의 예상 비용(%d)이 구성 임계값 %d을(를) 초과하여 쿼리가 취소되었습니다.</span><span class="sxs-lookup"><span data-stu-id="129fe-115">The query has been canceled because the estimated cost of this query (%d) exceeds the configured threshold of %d.</span></span> <span data-ttu-id="129fe-116">시스템 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="129fe-116">Contact the system administrator.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="129fe-117">설명</span><span class="sxs-lookup"><span data-stu-id="129fe-117">Explanation</span></span>  
 <span data-ttu-id="129fe-118">쿼리의 예상 비용이 QUERY_GOVERNOR_COST_LIMIT에 설정된 구성 임계값을 초과하여 쿼리가 취소되었습니다.</span><span class="sxs-lookup"><span data-stu-id="129fe-118">The query was canceled because the estimated cost of this query exceeds the configured threshold set for the QUERY_GOVERNOR_COST_LIMIT.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="129fe-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="129fe-119">User Action</span></span>  
 <span data-ttu-id="129fe-120">QUERY_GOVERNOR_COST_LIMIT 옵션을 더 큰 값으로 설정하십시오.</span><span class="sxs-lookup"><span data-stu-id="129fe-120">Set the QUERY_GOVERNOR_COST_LIMIT option to a higher value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="129fe-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="129fe-121">See Also</span></span>  
 [<span data-ttu-id="129fe-122">SET QUERY_GOVERNOR_COST_LIMIT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="129fe-122">SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql)  
  
  
