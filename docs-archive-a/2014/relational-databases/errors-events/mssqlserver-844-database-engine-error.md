---
title: MSSQLSERVER_844 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 844 (Database Engine error)
ms.assetid: 2060c886-1226-4066-bc0c-de90a1cfb82b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c4870d6e43ec12b49033ea3b5f88fa0d0cdd597a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649569"
---
# <a name="mssqlserver_844"></a><span data-ttu-id="e3787-102">MSSQLSERVER_844</span><span class="sxs-lookup"><span data-stu-id="e3787-102">MSSQLSERVER_844</span></span>
    
## <a name="details"></a><span data-ttu-id="e3787-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="e3787-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e3787-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="e3787-104">Product Name</span></span>|<span data-ttu-id="e3787-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e3787-105">SQL Server</span></span>|  
|<span data-ttu-id="e3787-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="e3787-106">Event ID</span></span>|<span data-ttu-id="e3787-107">844</span><span class="sxs-lookup"><span data-stu-id="e3787-107">844</span></span>|  
|<span data-ttu-id="e3787-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="e3787-108">Event Source</span></span>|<span data-ttu-id="e3787-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e3787-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e3787-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="e3787-110">Component</span></span>|<span data-ttu-id="e3787-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e3787-111">SQLEngine</span></span>|  
|<span data-ttu-id="e3787-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="e3787-112">Symbolic Name</span></span>|<span data-ttu-id="e3787-113">BUFLATCH_TIMEOUT_CONTINUE</span><span class="sxs-lookup"><span data-stu-id="e3787-113">BUFLATCH_TIMEOUT_CONTINUE</span></span>|  
|<span data-ttu-id="e3787-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="e3787-114">Message Text</span></span>|<span data-ttu-id="e3787-115">버퍼 래치를 기다리는 동안 시간이 초과되었습니다.-- 유형 %d, bp %p, 페이지 %d:%d, 상태 %#x, 데이터베이스 ID: %d, 할당 단위 ID: %I64d%ls, 태스크 0x%p : %d, 대기 시간 %d, 플래그 0x%I64x, 소유 태스크 0x%p.</span><span class="sxs-lookup"><span data-stu-id="e3787-115">Time-out occurred while waiting for buffer latch -- type %d, bp %p, page %d:%d, stat %#x, database id: %d, allocation unit id: %I64d%ls, task 0x%p : %d, waittime %d, flags 0x%I64x, owning task 0x%p.</span></span>  <span data-ttu-id="e3787-116">계속 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="e3787-116">Continuing to wait.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e3787-117">설명</span><span class="sxs-lookup"><span data-stu-id="e3787-117">Explanation</span></span>  
 <span data-ttu-id="e3787-118">프로세스에서 래치를 얻기 위해 대기 중입니다.</span><span class="sxs-lookup"><span data-stu-id="e3787-118">A process is waiting to acquire a latch.</span></span> <span data-ttu-id="e3787-119">이 문제는 완료하는 데 시간이 너무 오래 걸리는 I/O 작업으로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3787-119">This problem can be caused by an I/O operation taking too long to complete.</span></span> <span data-ttu-id="e3787-120">일반적으로 이 오류 유형은 시스템 프로세스를 차단하는 다른 태스크로 인해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="e3787-120">Typically this type of error is the result of other tasks blocking system processes.</span></span> <span data-ttu-id="e3787-121">하드웨어 오류로 인해 이 오류가 발생하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3787-121">In some instances, this error may be the result of hardware failure.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e3787-122">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="e3787-122">User Action</span></span>  
 <span data-ttu-id="e3787-123">이 오류가 발생하는 것을 방지하려면 다음을 시도하십시오.</span><span class="sxs-lookup"><span data-stu-id="e3787-123">Try the following to prevent this error from occurring:</span></span>  
  
-   <span data-ttu-id="e3787-124">작업을 줄이십시오.</span><span class="sxs-lookup"><span data-stu-id="e3787-124">Reduce workload.</span></span>  
  
-   <span data-ttu-id="e3787-125">오류 로그 또는 이벤트 로그에서 관련 I/O 오류를 검사하십시오.</span><span class="sxs-lookup"><span data-stu-id="e3787-125">Check for associated I/O failures in error log or event log.</span></span> <span data-ttu-id="e3787-126">I/O 오류는 일반적으로 디스크 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e3787-126">I/O failures typically point to a disk malfunction.</span></span>  
  
-   <span data-ttu-id="e3787-127">잠겨 있는 태스크 및 기타 오류에 대한 오류 로그를 검사하십시오.</span><span class="sxs-lookup"><span data-stu-id="e3787-127">Check the error log for non-yielding tasks and other critical errors.</span></span>  
  
-   <span data-ttu-id="e3787-128">어설션과 같은 오류가 자주 발생하면 이 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="e3787-128">If critical errors such as asserts frequently occur, resolve these problems.</span></span>  
  
 <span data-ttu-id="e3787-129">오류가 지속되면 Microsoft 고객 서비스 지원 센터에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="e3787-129">If the error persists, contact Microsoft Customer Service and Support.</span></span>  
  
  
