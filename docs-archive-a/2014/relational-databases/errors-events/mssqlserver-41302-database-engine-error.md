---
title: MSSQLSERVER_41302 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41302 (Database Engine error)
ms.assetid: 01e75618-afec-4232-ba68-93ab7bc31003
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 751dac91378c002a7e6c6c619ddaf12be8173400
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649571"
---
# <a name="mssqlserver_41302"></a><span data-ttu-id="6e924-102">MSSQLSERVER_41302</span><span class="sxs-lookup"><span data-stu-id="6e924-102">MSSQLSERVER_41302</span></span>
    
## <a name="details"></a><span data-ttu-id="6e924-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="6e924-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6e924-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="6e924-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="6e924-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="6e924-105">Event ID</span></span>|<span data-ttu-id="6e924-106">41302</span><span class="sxs-lookup"><span data-stu-id="6e924-106">41302</span></span>|  
|<span data-ttu-id="6e924-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="6e924-107">Event Source</span></span>|<span data-ttu-id="6e924-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6e924-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6e924-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="6e924-109">Component</span></span>|<span data-ttu-id="6e924-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6e924-110">SQLEngine</span></span>|  
|<span data-ttu-id="6e924-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="6e924-111">Symbolic Name</span></span>|<span data-ttu-id="6e924-112">WRITE_WRITE_CONFLICT</span><span class="sxs-lookup"><span data-stu-id="6e924-112">WRITE_WRITE_CONFLICT</span></span>|  
|<span data-ttu-id="6e924-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="6e924-113">Message Text</span></span>|<span data-ttu-id="6e924-114">현재 트랜잭션이 시작된 이후에 업데이트된 레코드를 업데이트하려고 시도했습니다.</span><span class="sxs-lookup"><span data-stu-id="6e924-114">The current transaction attempted to update a record that has been updated since this transaction started.</span></span> <span data-ttu-id="6e924-115">트랜잭션이 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6e924-115">The transaction was aborted.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6e924-116">설명</span><span class="sxs-lookup"><span data-stu-id="6e924-116">Explanation</span></span>  
 <span data-ttu-id="6e924-117">트랜잭션에서 쓰기/쓰기 충돌이 발생하여 문이 종료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6e924-117">The transaction encountered a write/write conflict and the statement terminated.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6e924-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="6e924-118">User Action</span></span>  
 <span data-ttu-id="6e924-119">나중에 다른 트랜잭션에서 작업을 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="6e924-119">Retry the operation later in a different transaction.</span></span> <span data-ttu-id="6e924-120">자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e924-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e924-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e924-121">See Also</span></span>  
 [<span data-ttu-id="6e924-122">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="6e924-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
