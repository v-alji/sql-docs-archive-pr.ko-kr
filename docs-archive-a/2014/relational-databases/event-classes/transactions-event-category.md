---
title: Transactions 이벤트 범주 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Transactions event category
- event classes [SQL Server], Transactions event category
- Transactions event category [SQL Server]
ms.assetid: bfc75c5b-7115-49d8-9148-a0c84ee66a9a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3b68a91fb166797c220cb0c4f5cf2607ca267538
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653407"
---
# <a name="transactions-event-category"></a><span data-ttu-id="1e8bf-102">Transactions 이벤트 범주</span><span class="sxs-lookup"><span data-stu-id="1e8bf-102">Transactions Event Category</span></span>
  <span data-ttu-id="1e8bf-103">**Transactions** 이벤트 클래스를 사용하면 트랜잭션 상태를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e8bf-103">The **Transactions** event classes can be used to monitor the status of transactions.</span></span> <span data-ttu-id="1e8bf-104">접두사 **TM:** 으로 시작되는 이벤트 클래스 이름은 트랜잭션 관리 인터페이스를 통해 전송되는 트랜잭션 관련 작업을 추적하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e8bf-104">The event class names that are prefixed with **TM:** are used to track the transaction-related operations that are sent through the transaction management interface.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1e8bf-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="1e8bf-105">In This Section</span></span>  
  
|<span data-ttu-id="1e8bf-106">항목</span><span class="sxs-lookup"><span data-stu-id="1e8bf-106">Topic</span></span>|<span data-ttu-id="1e8bf-107">Description</span><span class="sxs-lookup"><span data-stu-id="1e8bf-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1e8bf-108">DTCTransaction 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1e8bf-108">DTCTransaction Event Class</span></span>](dtctransaction-event-class.md)|<span data-ttu-id="1e8bf-109">MS DTC( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator)가 관리하는 트랜잭션을 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="1e8bf-109">Tracks transactions coordinated by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC).</span></span> <span data-ttu-id="1e8bf-110">이러한 트랜잭션은 둘 이상의 데이터베이스 또는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]인스턴스 간에 분산된 트랜잭션입니다.</span><span class="sxs-lookup"><span data-stu-id="1e8bf-110">These are transactions distributed between two or more databases or instances of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>|  
|[<span data-ttu-id="1e8bf-111">SQLTransaction 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1e8bf-111">SQLTransaction Event Class</span></span>](sqltransaction-event-class.md)|<span data-ttu-id="1e8bf-112">[!INCLUDE[tsql](../../includes/tsql-md.md)] BEGIN TRAN, COMMIT TRAN, SAVE TRAN 및 ROLLBACK TRAN 문을 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="1e8bf-112">Tracks [!INCLUDE[tsql](../../includes/tsql-md.md)] BEGIN TRAN, COMMIT TRAN, SAVE TRAN, and ROLLBACK TRAN statements.</span></span>|  
|[<span data-ttu-id="1e8bf-113">TM: Begin Tran Completed 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1e8bf-113">TM: Begin Tran Completed Event Class</span></span>](tm-begin-tran-completed-event-class.md)|<span data-ttu-id="1e8bf-114">BEGIN TRANSACTION 요청이 완료되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e8bf-114">Indicates that a BEGIN TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="1e8bf-115">TM: Begin Tran Starting 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1e8bf-115">TM: Begin Tran Starting Event Class</span></span>](tm-begin-tran-starting-event-class.md)|<span data-ttu-id="1e8bf-116">BEGIN TRANSACTION 요청이 시작 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e8bf-116">Indicates that a BEGIN TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="1e8bf-117">TM: Commit Tran Completed 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1e8bf-117">TM: Commit Tran Completed Event Class</span></span>](tm-commit-tran-completed-event-class.md)|<span data-ttu-id="1e8bf-118">COMMIT TRANSACTION 요청이 완료되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e8bf-118">Indicates that a COMMIT TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="1e8bf-119">TM: Commit Tran Starting 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1e8bf-119">TM: Commit Tran Starting Event Class</span></span>](tm-commit-tran-starting-event-class.md)|<span data-ttu-id="1e8bf-120">COMMIT TRANSACTION 요청이 시작 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e8bf-120">Indicates that a COMMIT TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="1e8bf-121">TM: Promote Tran Completed 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1e8bf-121">TM: Promote Tran Completed Event Class</span></span>](tm-promote-tran-completed-event-class.md)|<span data-ttu-id="1e8bf-122">PROMOTE TRANSACTION 요청이 완료되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e8bf-122">Indicates that a PROMOTE TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="1e8bf-123">TM: Promote Tran Starting 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1e8bf-123">TM: Promote Tran Starting Event Class</span></span>](tm-promote-tran-starting-event-class.md)|<span data-ttu-id="1e8bf-124">PROMOTE TRANSACTION 요청이 시작 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e8bf-124">Indicates that a PROMOTE TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="1e8bf-125">TM: Rollback Tran Completed 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1e8bf-125">TM: Rollback Tran Completed Event Class</span></span>](tm-rollback-tran-completed-event-class.md)|<span data-ttu-id="1e8bf-126">ROLLBACK TRANSACTION 요청이 완료되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e8bf-126">Indicates that a ROLLBACK TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="1e8bf-127">TM: Rollback Tran Starting 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1e8bf-127">TM: Rollback Tran Starting Event Class</span></span>](tm-rollback-tran-starting-event-class.md)|<span data-ttu-id="1e8bf-128">ROLLBACK TRANSACTION 요청이 시작 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e8bf-128">Indicates that a ROLLBACK TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="1e8bf-129">TM: Save Tran Completed 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1e8bf-129">TM: Save Tran Completed Event Class</span></span>](tm-save-tran-completed-event-class.md)|<span data-ttu-id="1e8bf-130">SAVE TRANSACTION 요청이 완료되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e8bf-130">Indicates that a SAVE TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="1e8bf-131">TM: Save Tran Starting 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1e8bf-131">TM: Save Tran Starting Event Class</span></span>](tm-save-tran-starting-event-class.md)|<span data-ttu-id="1e8bf-132">SAVE TRANSACTION 요청이 시작 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e8bf-132">Indicates that a SAVE TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="1e8bf-133">TransactionLog 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1e8bf-133">TransactionLog Event Class</span></span>](transactionlog-event-class.md)|<span data-ttu-id="1e8bf-134">트랜잭션이 데이터베이스 트랜잭션 로그에 기록되는 시기를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="1e8bf-134">Tracks when transactions are written to a database transaction log.</span></span>|  
  
  
