---
title: MSSQLSERVER_41307 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41307 (Database Engine error)
ms.assetid: 56f56410-b07d-4379-b01c-702c95761070
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 98407a65d5529fd73bccc638df11167131bd9f8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734100"
---
# <a name="mssqlserver_41307"></a><span data-ttu-id="1f6b1-102">MSSQLSERVER_41307</span><span class="sxs-lookup"><span data-stu-id="1f6b1-102">MSSQLSERVER_41307</span></span>
    
## <a name="details"></a><span data-ttu-id="1f6b1-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="1f6b1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1f6b1-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="1f6b1-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="1f6b1-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="1f6b1-105">Event ID</span></span>|<span data-ttu-id="1f6b1-106">41307</span><span class="sxs-lookup"><span data-stu-id="1f6b1-106">41307</span></span>|  
|<span data-ttu-id="1f6b1-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="1f6b1-107">Event Source</span></span>|<span data-ttu-id="1f6b1-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1f6b1-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1f6b1-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="1f6b1-109">Component</span></span>|<span data-ttu-id="1f6b1-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1f6b1-110">SQLEngine</span></span>|  
|<span data-ttu-id="1f6b1-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="1f6b1-111">Symbolic Name</span></span>|<span data-ttu-id="1f6b1-112">HK_HEKATON_ROW_LIMIT</span><span class="sxs-lookup"><span data-stu-id="1f6b1-112">HK_HEKATON_ROW_LIMIT</span></span>|  
|<span data-ttu-id="1f6b1-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="1f6b1-113">Message Text</span></span>|<span data-ttu-id="1f6b1-114">메모리 액세스에 최적화된 테이블의 행 크기 제한인 *number*바이트를 초과했습니다.</span><span class="sxs-lookup"><span data-stu-id="1f6b1-114">The row size limit of *number* bytes for memory optimized tables has been exceeded.</span></span> <span data-ttu-id="1f6b1-115">테이블 정의를 단순하게 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="1f6b1-115">Please simplify the table definition.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1f6b1-116">설명</span><span class="sxs-lookup"><span data-stu-id="1f6b1-116">Explanation</span></span>  
 <span data-ttu-id="1f6b1-117">메모리 액세스에 최적화된 테이블의 행 크기 제한은 8,060바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="1f6b1-117">The row size limit for memory optimized tables is 8,060 bytes.</span></span> <span data-ttu-id="1f6b1-118">자세한 내용은 [메모리 액세스에 최적화된 테이블의 테이블 및 행 크기](../in-memory-oltp/memory-optimized-tables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1f6b1-118">For more information, see [Table and Row Size in Memory-Optimized Tables](../in-memory-oltp/memory-optimized-tables.md).</span></span> <span data-ttu-id="1f6b1-119">자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1f6b1-119">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f6b1-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1f6b1-120">See Also</span></span>  
 [<span data-ttu-id="1f6b1-121">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="1f6b1-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
