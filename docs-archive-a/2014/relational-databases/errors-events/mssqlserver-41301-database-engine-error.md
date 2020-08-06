---
title: MSSQLSERVER_41301 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41301 (Database Engine error)
ms.assetid: c6127e1e-2846-4ee9-bc42-2d896ea9730e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d4fa78b334f32033f96df002aeaf039994b396cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652144"
---
# <a name="mssqlserver_41301"></a><span data-ttu-id="916bd-102">MSSQLSERVER_41301</span><span class="sxs-lookup"><span data-stu-id="916bd-102">MSSQLSERVER_41301</span></span>
    
## <a name="details"></a><span data-ttu-id="916bd-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="916bd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="916bd-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="916bd-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="916bd-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="916bd-105">Event ID</span></span>|<span data-ttu-id="916bd-106">41301</span><span class="sxs-lookup"><span data-stu-id="916bd-106">41301</span></span>|  
|<span data-ttu-id="916bd-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="916bd-107">Event Source</span></span>|<span data-ttu-id="916bd-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="916bd-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="916bd-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="916bd-109">Component</span></span>|<span data-ttu-id="916bd-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="916bd-110">SQLEngine</span></span>|  
|<span data-ttu-id="916bd-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="916bd-111">Symbolic Name</span></span>|<span data-ttu-id="916bd-112">COMMIT_DEPENDENCY_FAILURE</span><span class="sxs-lookup"><span data-stu-id="916bd-112">COMMIT_DEPENDENCY_FAILURE</span></span>|  
|<span data-ttu-id="916bd-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="916bd-113">Message Text</span></span>|<span data-ttu-id="916bd-114">현재 트랜잭션이 종속성을 갖고 있는 이전 트랜잭션이 중단되어 현재 트랜잭션을 더 이상 커밋할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="916bd-114">A previous transaction that the current transaction took a dependency on has aborted, and the current transaction can no longer commit.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="916bd-115">설명</span><span class="sxs-lookup"><span data-stu-id="916bd-115">Explanation</span></span>  
 <span data-ttu-id="916bd-116">종속성 오류가 발생하여 트랜잭션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="916bd-116">The transaction encountered a dependency failure, and is now doomed.</span></span>  
  
 <span data-ttu-id="916bd-117">종속 트랜잭션이 너무 많아도 이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916bd-117">This error can also be caused by too many dependent transactions.</span></span> <span data-ttu-id="916bd-118">모든 쓰기 트랜잭션은 제한된 수의 종속 트랜잭션을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916bd-118">Any write transaction can have a limited number of dependent transactions.</span></span> <span data-ttu-id="916bd-119">예를 들어, 너무 많은 읽기 트랜잭션에서 업데이트 트랜잭션에 대한 종속성을 가지려고 할 경우 이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916bd-119">For example, this error can occur if too many read transactions try to take a dependency on the update transaction.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="916bd-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="916bd-120">User Action</span></span>  
 <span data-ttu-id="916bd-121">트랜잭션에서 어떤 작업도 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="916bd-121">Don't do any work on the transaction.</span></span> <span data-ttu-id="916bd-122">ROLLBACK TRAN을 호출하여 트랜잭션을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="916bd-122">Call ROLLBACK TRAN to roll back the transaction.</span></span> <span data-ttu-id="916bd-123">자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="916bd-123">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="916bd-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="916bd-124">See Also</span></span>  
 [<span data-ttu-id="916bd-125">AlwaysOn 가용성 그룹 활성화 및 비활성화&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="916bd-125">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
  
