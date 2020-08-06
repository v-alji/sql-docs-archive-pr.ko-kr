---
title: XTP 트랜잭션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 443d67e4-1c7f-41d7-b18d-2d657f58c22a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 75fa8bc9a673d9e0e018b8578a35af2e46b5044c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730563"
---
# <a name="xtp-transactions"></a><span data-ttu-id="6507a-102">XTP 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="6507a-102">XTP Transactions</span></span>
  <span data-ttu-id="6507a-103">XTP 트랜잭션 성능 개체에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 XTP 엔진 트랜잭션과 관련된 카운터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6507a-103">The XTP Transactions performance object contains counters related to XTP engine transactions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6507a-104">이 표에서는 **XTP 트랜잭션** 카운터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6507a-104">This table describes the **XTP Transactions** counters.</span></span>  
  
|<span data-ttu-id="6507a-105">카운터</span><span class="sxs-lookup"><span data-stu-id="6507a-105">Counter</span></span>|<span data-ttu-id="6507a-106">Description</span><span class="sxs-lookup"><span data-stu-id="6507a-106">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6507a-107">**Cascading aborts/sec**</span><span class="sxs-lookup"><span data-stu-id="6507a-107">**Cascading aborts/sec**</span></span>|<span data-ttu-id="6507a-108">커밋 종속성 롤백으로 인해 롤백되는 초당 트랜잭션 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="6507a-108">The number of transactions that rolled back to due a commit dependency rollback (on average), per second.</span></span>|  
|<span data-ttu-id="6507a-109">**Commit dependencies taken/sec**</span><span class="sxs-lookup"><span data-stu-id="6507a-109">**Commit dependencies taken/sec**</span></span>|<span data-ttu-id="6507a-110">트랜잭션에 의해 사용되는 초당 커밋 종속성 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="6507a-110">The number of commit dependencies taken by transactions (on average), per second.</span></span>|  
|<span data-ttu-id="6507a-111">**Read-only transactions prepared/sec**</span><span class="sxs-lookup"><span data-stu-id="6507a-111">**Read-only transactions prepared/sec**</span></span>|<span data-ttu-id="6507a-112">커밋 처리를 위해 준비된 초당 읽기 전용 트랜잭션 수입니다.</span><span class="sxs-lookup"><span data-stu-id="6507a-112">The number of read-only transactions that were prepared for commit processing, per second.</span></span>|  
|<span data-ttu-id="6507a-113">**Save point refreshes/sec**</span><span class="sxs-lookup"><span data-stu-id="6507a-113">**Save point refreshes/sec**</span></span>|<span data-ttu-id="6507a-114">저장점을 "새로 고친" 초당 횟수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="6507a-114">The number of times a savepoint was "refreshed", (on average), per second.</span></span> <span data-ttu-id="6507a-115">저장점 새로 고침은 기존 저장점이 트랜잭션의 수명에서 현재 지점으로 재설정될 때 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="6507a-115">A savepoint refresh is when an existing savepoint is reset to the current point in the transaction's lifetime.</span></span>|  
|<span data-ttu-id="6507a-116">**Save point rollbacks/sec**</span><span class="sxs-lookup"><span data-stu-id="6507a-116">**Save point rollbacks/sec**</span></span>|<span data-ttu-id="6507a-117">트랜잭션이 저장점으로 롤백된 초당 횟수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="6507a-117">The number of times a transaction rolled back to a save point (on average), per second.</span></span>|  
|<span data-ttu-id="6507a-118">**Save points created /sec**</span><span class="sxs-lookup"><span data-stu-id="6507a-118">**Save points created /sec**</span></span>|<span data-ttu-id="6507a-119">초당 생성된 저장점 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="6507a-119">The number of save points created (on average), per second.</span></span>|  
|<span data-ttu-id="6507a-120">**Transaction validation failure/sec**</span><span class="sxs-lookup"><span data-stu-id="6507a-120">**Transaction validation failure/sec**</span></span>|<span data-ttu-id="6507a-121">유효성 검사 처리에 실패한 초당 트랜잭션 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="6507a-121">The number of transactions that failed validation processing (on average), per second.</span></span>|  
|<span data-ttu-id="6507a-122">**Transactions aborted by user/sec**</span><span class="sxs-lookup"><span data-stu-id="6507a-122">**Transactions aborted by user/sec**</span></span>|<span data-ttu-id="6507a-123">사용자에 의해 중단된 초당 트랜잭션 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="6507a-123">The number of transactions that were aborted by the user (on average), per second.</span></span>|  
|<span data-ttu-id="6507a-124">**Transactions aborted/sec**</span><span class="sxs-lookup"><span data-stu-id="6507a-124">**Transactions aborted/sec**</span></span>|<span data-ttu-id="6507a-125">사용자 및 시스템에 의해 중단된 초당 트랜잭션 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="6507a-125">The number of transactions that aborted (both by the user and the system, on average), per second.</span></span>|  
|<span data-ttu-id="6507a-126">**Transactions created/sec**</span><span class="sxs-lookup"><span data-stu-id="6507a-126">**Transactions created/sec**</span></span>|<span data-ttu-id="6507a-127">시스템에서 생성된 초당 트랜잭션 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="6507a-127">The number of transactions created in the system (on average), per second.</span></span><br /><br /> <span data-ttu-id="6507a-128">XTP 트랜잭션은 디스크 기반 트랜잭션과 다르게 계산됩니다(Databases:Transactions/sec에 반영됨).</span><span class="sxs-lookup"><span data-stu-id="6507a-128">XTP transactions are counted differently than disk-based transactions (as reflected in Databases:Transactions/sec).</span></span> <span data-ttu-id="6507a-129">예를 들어, created/sec 트랜잭션은 read/only 트랜잭션을 계산하지만 Databases:Transactions/sec는 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6507a-129">For example, Transactions created/sec counts read/only transactions, while Databases:Transactions/sec does not.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6507a-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6507a-130">See Also</span></span>  
 [<span data-ttu-id="6507a-131">XTP &#40;메모리 내 OLTP&#41; 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="6507a-131">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
