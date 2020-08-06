---
title: MSSQLSERVER_845 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 845 (Database Engine error)
ms.assetid: 8fff6ad4-234c-44be-b123-e25d5e1cd63e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 24bfb8b3758d0656dad96e4af4ed3b94aa51e07f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649565"
---
# <a name="mssqlserver_845"></a><span data-ttu-id="f7155-102">MSSQLSERVER_845</span><span class="sxs-lookup"><span data-stu-id="f7155-102">MSSQLSERVER_845</span></span>
    
## <a name="details"></a><span data-ttu-id="f7155-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="f7155-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f7155-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="f7155-104">Product Name</span></span>|<span data-ttu-id="f7155-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f7155-105">SQL Server</span></span>|  
|<span data-ttu-id="f7155-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="f7155-106">Event ID</span></span>|<span data-ttu-id="f7155-107">845</span><span class="sxs-lookup"><span data-stu-id="f7155-107">845</span></span>|  
|<span data-ttu-id="f7155-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="f7155-108">Event Source</span></span>|<span data-ttu-id="f7155-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f7155-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f7155-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="f7155-110">Component</span></span>|<span data-ttu-id="f7155-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f7155-111">SQLEngine</span></span>|  
|<span data-ttu-id="f7155-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="f7155-112">Symbolic Name</span></span>|<span data-ttu-id="f7155-113">BUFLATCH_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f7155-113">BUFLATCH_TIMEOUT</span></span>|  
|<span data-ttu-id="f7155-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="f7155-114">Message Text</span></span>|<span data-ttu-id="f7155-115">데이터베이스 ID %d, 페이지 %S_PGID에 대한 버퍼 래치 유형 %d을(를) 기다리는 중 시간이 초과되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-115">Time-out occurred while waiting for buffer latch type %d for page %S_PGID, database ID %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f7155-116">설명</span><span class="sxs-lookup"><span data-stu-id="f7155-116">Explanation</span></span>  
 <span data-ttu-id="f7155-117">프로세스가 래치를 획득하려고 대기했지만, 제한 시간이 초과되어 래치를 획득하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-117">A process was waiting to acquire a latch, but the process waited until the time limit expired and failed to acquire one.</span></span> <span data-ttu-id="f7155-118">이 오류는 일반적으로 시스템 프로세스를 차단하는 다른 태스크로 인해 I/O 작업을 완료하는 데 너무 많은 시간이 소요되는 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-118">This can occur if an I/O operation takes too long to complete, usually as a result of other tasks blocking system processes.</span></span> <span data-ttu-id="f7155-119">하드웨어 오류로 인해 이 오류가 발생하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-119">In some instances, this error may be the result of hardware failure.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f7155-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="f7155-120">User Action</span></span>  
 <span data-ttu-id="f7155-121">다음 태스크를 수행하면 이 오류를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-121">Performing the following tasks may prevent this error:</span></span>  
  
-   <span data-ttu-id="f7155-122">작업을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-122">Reduce the workload.</span></span>  
  
-   <span data-ttu-id="f7155-123">오류 로그나 이벤트 로그에 관련된 I/O 오류가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-123">Verify whether there are associated I/O failures in the error log or event log.</span></span> <span data-ttu-id="f7155-124">I/O 오류는 일반적으로 디스크 오류로 인해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-124">I/O failures are typically caused by disk malfunction.</span></span>  
  
-   <span data-ttu-id="f7155-125">오류 로그에 잠겨 있는 태스크 및 기타 오류가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-125">Check error log for non-yielding tasks and other critical errors.</span></span>  
  
-   <span data-ttu-id="f7155-126">어설션과 같은 오류가 자주 발생하면 이 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="f7155-126">If critical errors such as asserts frequently occur, resolve these problems.</span></span>  
  
 <span data-ttu-id="f7155-127">오류가 지속되면 Microsoft 고객 서비스 지원 센터에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="f7155-127">If the error persists, contact Microsoft Customer Service and Support.</span></span>  
  
  
