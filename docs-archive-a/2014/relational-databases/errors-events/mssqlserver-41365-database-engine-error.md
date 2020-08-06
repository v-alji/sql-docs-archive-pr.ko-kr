---
title: MSSQLSERVER_41365 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41365 (Database Engine error)
ms.assetid: 4fc7ec15-b722-4e3d-b7f9-3d39d171e96e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1382a6395f1929a5d5552113e07376bcbf80bf35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652138"
---
# <a name="mssqlserver_41365"></a><span data-ttu-id="dad2b-102">MSSQLSERVER_41365</span><span class="sxs-lookup"><span data-stu-id="dad2b-102">MSSQLSERVER_41365</span></span>
    
## <a name="details"></a><span data-ttu-id="dad2b-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="dad2b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dad2b-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="dad2b-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="dad2b-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="dad2b-105">Event ID</span></span>|<span data-ttu-id="dad2b-106">41365</span><span class="sxs-lookup"><span data-stu-id="dad2b-106">41365</span></span>|  
|<span data-ttu-id="dad2b-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="dad2b-107">Event Source</span></span>|<span data-ttu-id="dad2b-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="dad2b-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="dad2b-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="dad2b-109">Component</span></span>|<span data-ttu-id="dad2b-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="dad2b-110">SQLEngine</span></span>|  
|<span data-ttu-id="dad2b-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="dad2b-111">Symbolic Name</span></span>|<span data-ttu-id="dad2b-112">HK_MERGE_SCHEDULE_ERROR</span><span class="sxs-lookup"><span data-stu-id="dad2b-112">HK_MERGE_SCHEDULE_ERROR</span></span>|  
|<span data-ttu-id="dad2b-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="dad2b-113">Message Text</span></span>|<span data-ttu-id="dad2b-114">%.\*ls 데이터베이스의 트랜잭션 범위 [%ld, %ld]에 대한 병합 요청이 예약되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="dad2b-114">Merge request for transaction range [%ld, %ld] on database %.\*ls was not scheduled.</span></span> <span data-ttu-id="dad2b-115">범위를 나타내는 검사점 파일이 병합에 사용할 수 없거나 진행 중인 병합의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="dad2b-115">The checkpoint files representing the range are either not available for merge or part of an ongoing merge.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dad2b-116">설명</span><span class="sxs-lookup"><span data-stu-id="dad2b-116">Explanation</span></span>  
 <span data-ttu-id="dad2b-117">범위를 나타내는 검사점 파일이 병합에 사용할 수 없거나 진행 중인 병합의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="dad2b-117">The checkpoint files representing the range are either not available for merge or part of an ongoing merge.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dad2b-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="dad2b-118">User Action</span></span>  
 <span data-ttu-id="dad2b-119">같은 요청을 다시 실행하기 전에 병합/대기에 사용할 더 나은 트랜잭션 범위를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dad2b-119">Provide a better transaction range for merge/wait before issuing the same request again.</span></span> <span data-ttu-id="dad2b-120">자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dad2b-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad2b-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dad2b-121">See Also</span></span>  
 [<span data-ttu-id="dad2b-122">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="dad2b-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
