---
title: MSSQLSERVER_41396 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41396 (Database Engine error)
ms.assetid: 4ff04042-8367-46f3-8a16-c94682d6eedb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2386c805b61631c9b843753d74ba6616e7344223
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731620"
---
# <a name="mssqlserver_41396"></a><span data-ttu-id="7fdf7-102">MSSQLSERVER_41396</span><span class="sxs-lookup"><span data-stu-id="7fdf7-102">MSSQLSERVER_41396</span></span>
    
## <a name="details"></a><span data-ttu-id="7fdf7-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="7fdf7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7fdf7-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="7fdf7-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="7fdf7-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="7fdf7-105">Event ID</span></span>|<span data-ttu-id="7fdf7-106">41396</span><span class="sxs-lookup"><span data-stu-id="7fdf7-106">41396</span></span>|  
|<span data-ttu-id="7fdf7-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="7fdf7-107">Event Source</span></span>|<span data-ttu-id="7fdf7-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7fdf7-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7fdf7-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="7fdf7-109">Component</span></span>|<span data-ttu-id="7fdf7-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7fdf7-110">SQLEngine</span></span>|  
|<span data-ttu-id="7fdf7-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="7fdf7-111">Symbolic Name</span></span>|<span data-ttu-id="7fdf7-112">MAX_SORT_ROWS_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="7fdf7-112">MAX_SORT_ROWS_EXCEEDED</span></span>|  
|<span data-ttu-id="7fdf7-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="7fdf7-113">Message Text</span></span>|<span data-ttu-id="7fdf7-114">정렬 작업에서 버퍼 제한을 초과했습니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf7-114">The sort operation exceeded the buffer limit.</span></span> <span data-ttu-id="7fdf7-115">저장 프로시저 실행이 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf7-115">The stored procedure execution was aborted.</span></span> <span data-ttu-id="7fdf7-116">자세한 내용은 SQL Server 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7fdf7-116">Consult SQL Server Books Online for more information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7fdf7-117">설명</span><span class="sxs-lookup"><span data-stu-id="7fdf7-117">Explanation</span></span>  
 <span data-ttu-id="7fdf7-118">고유하게 컴파일된 저장 프로시저는 메모리에서 정렬 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf7-118">Natively compiled stored procedures perform sort operations in memory.</span></span> <span data-ttu-id="7fdf7-119">정렬 버퍼 크기에 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf7-119">There is a limit on the size of the sort buffer.</span></span> <span data-ttu-id="7fdf7-120">이 오류는 정렬 버퍼 크기가 이 제한을 초과했음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf7-120">This error means that the size of the sort buffer exceeds this limit.</span></span> <span data-ttu-id="7fdf7-121">정렬 작업 및 저장 프로시저 실행이 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf7-121">The sort operation and the stored procedure execution aborted.</span></span>  
  
 <span data-ttu-id="7fdf7-122">정렬 버퍼의 각 행 또는 항목의 크기는 정렬되는 행 수, 쿼리에 사용된 조인 수, 집계 함수의 수 및 유형에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf7-122">The size of each row or entry in the sort buffer is determined by the number of rows sorted as well as the number of joins and the number and type of aggregate functions in the query.</span></span> <span data-ttu-id="7fdf7-123">쿼리를 단순화하여 각 행의 크기를 줄이고 정렬 버퍼에 더 많은 행이 들어가도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf7-123">By simplifying the query, you can reduce the size of each row thereby fitting more rows in the sort buffer.</span></span> <span data-ttu-id="7fdf7-124">기본 테이블의 행 크기는 정렬 버퍼의 각 행 또는 항목의 크기에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7fdf7-124">The size of the rows in the base tables does not affect the size of each row or entry in the sort buffer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7fdf7-125">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="7fdf7-125">User Action</span></span>  
 <span data-ttu-id="7fdf7-126">더 적은 수의 행을 선택하거나 조인 또는 집계 함수를 제거하여 쿼리를 단순화하십시오.</span><span class="sxs-lookup"><span data-stu-id="7fdf7-126">Select fewer rows or decrease the complexity of the query by removing joins or aggregate functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fdf7-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7fdf7-127">See Also</span></span>  
 [<span data-ttu-id="7fdf7-128">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="7fdf7-128">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
