---
title: MSSQLSERVER_1222 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1222 (Database Engine error)
ms.assetid: c5b1c2f4-f591-4cc1-aa17-204636a27f29
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ac3fe9314386836633a11f17d6775c75019de93a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638820"
---
# <a name="mssqlserver_1222"></a><span data-ttu-id="46999-102">MSSQLSERVER_1222</span><span class="sxs-lookup"><span data-stu-id="46999-102">MSSQLSERVER_1222</span></span>
    
## <a name="details"></a><span data-ttu-id="46999-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="46999-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="46999-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="46999-104">Product Name</span></span>|<span data-ttu-id="46999-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="46999-105">SQL Server</span></span>|  
|<span data-ttu-id="46999-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="46999-106">Event ID</span></span>|<span data-ttu-id="46999-107">1222</span><span class="sxs-lookup"><span data-stu-id="46999-107">1222</span></span>|  
|<span data-ttu-id="46999-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="46999-108">Event Source</span></span>|<span data-ttu-id="46999-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="46999-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="46999-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="46999-110">Component</span></span>|<span data-ttu-id="46999-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="46999-111">SQLEngine</span></span>|  
|<span data-ttu-id="46999-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="46999-112">Symbolic Name</span></span>|<span data-ttu-id="46999-113">LK_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="46999-113">LK_TIMEOUT</span></span>|  
|<span data-ttu-id="46999-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="46999-114">Message Text</span></span>|<span data-ttu-id="46999-115">잠금 요청 제한 시간이 초과되었습니다.</span><span class="sxs-lookup"><span data-stu-id="46999-115">Lock request time out period exceeded.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="46999-116">설명</span><span class="sxs-lookup"><span data-stu-id="46999-116">Explanation</span></span>  
 <span data-ttu-id="46999-117">이 쿼리에서 대기할 수 있는 시간보다 긴 시간 동안 다른 트랜잭션이 요청된 리소스에 대해 잠금을 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46999-117">Another transaction held a lock on a required resource longer than this query could wait for it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="46999-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="46999-118">User Action</span></span>  
 <span data-ttu-id="46999-119">이 문제를 완화하려면 다음 태스크를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="46999-119">Perform the following tasks to alleviate the problem:</span></span>  
  
1.  <span data-ttu-id="46999-120">가능한 경우 요청한 리소스에 대한 잠금을 보유한 트랜잭션을 찾으십시오.</span><span class="sxs-lookup"><span data-stu-id="46999-120">Locate the transaction that is holding the lock on the required resource, if possible.</span></span> <span data-ttu-id="46999-121">**sys.dm_os_waiting_tasks** 및 **sys.dm_tran_locks** 동적 관리 뷰를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="46999-121">Use **sys.dm_os_waiting_tasks** and **sys.dm_tran_locks** dynamic management views.</span></span>  
  
2.  <span data-ttu-id="46999-122">트랜잭션이 여전히 잠금을 보유 중이면 트랜잭션을 종료하십시오(가능한 경우).</span><span class="sxs-lookup"><span data-stu-id="46999-122">If the transaction is still holding the lock, terminate that transaction if appropriate.</span></span>  
  
3.  <span data-ttu-id="46999-123">쿼리를 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="46999-123">Execute the query again.</span></span>  
  
 <span data-ttu-id="46999-124">이 오류가 자주 발생하면 잠금 제한 시간을 변경하거나 문제가 되는 트랜잭션을 수정하여 잠금을 보유하는 시간을 줄이십시오.</span><span class="sxs-lookup"><span data-stu-id="46999-124">If this error occurs frequently change the lock time-out period or modify the offending transactions so that they hold the lock for less time.</span></span>  
  
  
