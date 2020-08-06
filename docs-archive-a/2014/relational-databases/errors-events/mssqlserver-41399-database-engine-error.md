---
title: MSSQLSERVER_41399 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41399 (Database Engine error)
ms.assetid: 5e5acb07-16ca-4329-8210-cd2bab0c904f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2e134cbc8b39a3c65d9c515183243f0b4caed434
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649570"
---
# <a name="mssqlserver_41399"></a><span data-ttu-id="3a8eb-102">MSSQLSERVER_41399</span><span class="sxs-lookup"><span data-stu-id="3a8eb-102">MSSQLSERVER_41399</span></span>
    
## <a name="details"></a><span data-ttu-id="3a8eb-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="3a8eb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3a8eb-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="3a8eb-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="3a8eb-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="3a8eb-105">Event ID</span></span>|<span data-ttu-id="3a8eb-106">41399</span><span class="sxs-lookup"><span data-stu-id="3a8eb-106">41399</span></span>|  
|<span data-ttu-id="3a8eb-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="3a8eb-107">Event Source</span></span>|<span data-ttu-id="3a8eb-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3a8eb-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3a8eb-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="3a8eb-109">Component</span></span>|<span data-ttu-id="3a8eb-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3a8eb-110">SQLEngine</span></span>|  
|<span data-ttu-id="3a8eb-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="3a8eb-111">Symbolic Name</span></span>|<span data-ttu-id="3a8eb-112">MAX_SORT_ROW_WIDTH_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="3a8eb-112">MAX_SORT_ROW_WIDTH_EXCEEDED</span></span>|  
|<span data-ttu-id="3a8eb-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="3a8eb-113">Message Text</span></span>|<span data-ttu-id="3a8eb-114">정렬 작업이 너무 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="3a8eb-114">The sort operation is too complex.</span></span> <span data-ttu-id="3a8eb-115">자세한 내용은 SQL Server 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3a8eb-115">Consult SQL Server Books Online for more information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3a8eb-116">설명</span><span class="sxs-lookup"><span data-stu-id="3a8eb-116">Explanation</span></span>  
 <span data-ttu-id="3a8eb-117">조인 및 집계 작업의 결과 정렬 작업은 정렬 버퍼의 행 크기를 늘려 정렬 작업의 복잡성을 가중시킵니다.</span><span class="sxs-lookup"><span data-stu-id="3a8eb-117">Sorting the result of join and aggregation operations increases the complexity of the sort operation by increasing the size of the row in the sort buffer.</span></span> <span data-ttu-id="3a8eb-118">이 오류는 행 크기가 고유하게 컴파일된 저장 프로시저의 정렬 연산자에 지원되는 최대 크기보다 크다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="3a8eb-118">This error means that the size of the row is larger than the maximum size supported by the sort operator in natively compiled stored procedures.</span></span> <span data-ttu-id="3a8eb-119">정렬 버퍼의 행 크기는 전적으로 조인 수 및 집계 함수의 수와 유형에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a8eb-119">Note that the size of a row in the sort buffer is determined solely by the number of joins and the number and type of aggregate functions.</span></span> <span data-ttu-id="3a8eb-120">기본 테이블의 행 크기는 버퍼의 행 크기에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a8eb-120">The size of the rows in the base tables does not affect the size of the row in the buffer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3a8eb-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="3a8eb-121">User Action</span></span>  
 <span data-ttu-id="3a8eb-122">조인이나 집계 함수를 제거하여 쿼리를 단순화하십시오.</span><span class="sxs-lookup"><span data-stu-id="3a8eb-122">Decrease the complexity of the query by removing joins or aggregate functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a8eb-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a8eb-123">See Also</span></span>  
 [<span data-ttu-id="3a8eb-124">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="3a8eb-124">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
