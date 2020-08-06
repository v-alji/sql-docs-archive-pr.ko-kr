---
title: MSSQLSERVER_41305 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41305 (Database Engine error)
ms.assetid: a96e5083-ff97-4003-a900-07942454151d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9c00e20ec220d7fcee0da4e99c2ef35817dae67f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652139"
---
# <a name="mssqlserver_41305"></a><span data-ttu-id="81704-102">MSSQLSERVER_41305</span><span class="sxs-lookup"><span data-stu-id="81704-102">MSSQLSERVER_41305</span></span>
    
## <a name="details"></a><span data-ttu-id="81704-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="81704-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="81704-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="81704-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="81704-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="81704-105">Event ID</span></span>|<span data-ttu-id="81704-106">41305</span><span class="sxs-lookup"><span data-stu-id="81704-106">41305</span></span>|  
|<span data-ttu-id="81704-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="81704-107">Event Source</span></span>|<span data-ttu-id="81704-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="81704-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="81704-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="81704-109">Component</span></span>|<span data-ttu-id="81704-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="81704-110">SQLEngine</span></span>|  
|<span data-ttu-id="81704-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="81704-111">Symbolic Name</span></span>|<span data-ttu-id="81704-112">HK_TX_COMMIT_RR_VALIDATION</span><span class="sxs-lookup"><span data-stu-id="81704-112">HK_TX_COMMIT_RR_VALIDATION</span></span>|  
|<span data-ttu-id="81704-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="81704-113">Message Text</span></span>|<span data-ttu-id="81704-114">반복 읽기 유효성 검사 실패로 인해 현재 트랜잭션을 커밋하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="81704-114">The current transaction failed to commit due to a repeatable read validation failure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="81704-115">설명</span><span class="sxs-lookup"><span data-stu-id="81704-115">Explanation</span></span>  
 <span data-ttu-id="81704-116">유효성 검사 오류가 발생하여 트랜잭션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="81704-116">The transaction encountered a validation failure and is now doomed.</span></span>  
  
 <span data-ttu-id="81704-117">자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81704-117">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="81704-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="81704-118">User Action</span></span>  
 <span data-ttu-id="81704-119">실패한 트랜잭션을 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="81704-119">Retry the failed transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81704-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="81704-120">See Also</span></span>  
 [<span data-ttu-id="81704-121">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="81704-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
