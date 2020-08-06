---
title: MSSQL_ENG020574 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG02574 error
ms.assetid: 4e98f8de-287c-4090-81ee-dc8f80dfa6a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e224e9a87d40fa826a05c669216649c45185037
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661052"
---
# <a name="mssql_eng020574"></a><span data-ttu-id="c23af-102">MSSQL_ENG020574</span><span class="sxs-lookup"><span data-stu-id="c23af-102">MSSQL_ENG020574</span></span>
    
## <a name="message-details"></a><span data-ttu-id="c23af-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="c23af-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c23af-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="c23af-104">Product Name</span></span>|<span data-ttu-id="c23af-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c23af-105">SQL Server</span></span>|  
|<span data-ttu-id="c23af-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="c23af-106">Event ID</span></span>|<span data-ttu-id="c23af-107">20574</span><span class="sxs-lookup"><span data-stu-id="c23af-107">20574</span></span>|  
|<span data-ttu-id="c23af-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="c23af-108">Event Source</span></span>|<span data-ttu-id="c23af-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c23af-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c23af-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="c23af-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="c23af-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="c23af-111">Symbolic Name</span></span>||  
|<span data-ttu-id="c23af-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="c23af-112">Message Text</span></span>|<span data-ttu-id="c23af-113">게시 '%s'의 아티클 '%s'에 대한 구독자 '%s'의 구독이 데이터 유효성 검사에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="c23af-113">Subscriber '%s' subscription to article '%s' in publication '%s' failed data validation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c23af-114">설명</span><span class="sxs-lookup"><span data-stu-id="c23af-114">Explanation</span></span>  
 <span data-ttu-id="c23af-115">구독자의 데이터를 게시자의 데이터와 비교하여 유효성을 검사했는데 데이터가 일치하지 않아 유효성 검사가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="c23af-115">The data at the Subscriber was validated against the data at the Publisher, and the data did not match; therefore validation failed.</span></span> <span data-ttu-id="c23af-116">유효성 검사에 대한 자세한 내용은 [Validate Replicated Data](validate-data-at-the-subscriber.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c23af-116">For more information about validation, see [Validate Replicated Data](validate-data-at-the-subscriber.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c23af-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="c23af-117">User Action</span></span>  
 <span data-ttu-id="c23af-118">다음을 수행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c23af-118">We recommend that you do the following:</span></span>  
  
-   <span data-ttu-id="c23af-119">유효성 검사 실패 원인을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c23af-119">Determine why validation failed.</span></span>  
  
-   <span data-ttu-id="c23af-120">실패 원인의 기본 문제를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="c23af-120">Correct the underlying issue that caused the failure.</span></span>  
  
-   <span data-ttu-id="c23af-121">구독을 다시 초기화하거나 다른 메서드를 통해 데이터를 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="c23af-121">Bring the data into convergence by reinitializing the subscription or through another method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c23af-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c23af-122">See Also</span></span>  
 [<span data-ttu-id="c23af-123">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="c23af-123">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
