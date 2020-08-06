---
title: MSSQLSERVER_17884 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17884 (Database Engine error)
ms.assetid: 8d05ba05-3f71-4dc3-bd81-2ea5ac9fe843
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bd5beca2a7dfd20afbf9eff196d89452ef3533d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734111"
---
# <a name="mssqlserver_17884"></a><span data-ttu-id="f84b9-102">MSSQLSERVER_17884</span><span class="sxs-lookup"><span data-stu-id="f84b9-102">MSSQLSERVER_17884</span></span>
    
## <a name="details"></a><span data-ttu-id="f84b9-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="f84b9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f84b9-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="f84b9-104">Product Name</span></span>|<span data-ttu-id="f84b9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f84b9-105">SQL Server</span></span>|  
|<span data-ttu-id="f84b9-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="f84b9-106">Event ID</span></span>|<span data-ttu-id="f84b9-107">17884</span><span class="sxs-lookup"><span data-stu-id="f84b9-107">17884</span></span>|  
|<span data-ttu-id="f84b9-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="f84b9-108">Event Source</span></span>|<span data-ttu-id="f84b9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f84b9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f84b9-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="f84b9-110">Component</span></span>|<span data-ttu-id="f84b9-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f84b9-111">SQLEngine</span></span>|  
|<span data-ttu-id="f84b9-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="f84b9-112">Symbolic Name</span></span>|<span data-ttu-id="f84b9-113">SRV_SCHEDULER_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="f84b9-113">SRV_SCHEDULER_DEADLOCK</span></span>|  
|<span data-ttu-id="f84b9-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="f84b9-114">Message Text</span></span>|<span data-ttu-id="f84b9-115">노드 %d의 프로세스에 할당된 새 쿼리가 최근 %d초 내에 작업자 스레드에 의해 선택되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f84b9-115">New queries assigned to process on Node %d have not been picked  up by a worker thread in the last %d seconds.</span></span> <span data-ttu-id="f84b9-116">차단 쿼리 또는 오래 실행되는 쿼리가 이 상황을 유발할 수 있으며 클라이언트 응답 시간을 저하시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f84b9-116">Blocking or long-running queries can contribute to this condition, and may degrade client response time.</span></span> <span data-ttu-id="f84b9-117">"max worker threads" 구성 옵션을 사용하여 허용 스레드 수를 늘리거나 현재 실행 중인 쿼리를 최적화하십시오.</span><span class="sxs-lookup"><span data-stu-id="f84b9-117">Use the "max worker threads" configuration option to increase number  of allowable threads, or optimize current running queries.</span></span>  <span data-ttu-id="f84b9-118">SQL 프로세스 사용률: %d%%.</span><span class="sxs-lookup"><span data-stu-id="f84b9-118">SQL Process Utilization: %d%%.</span></span> <span data-ttu-id="f84b9-119">시스템 유휴 시간: %d%%.</span><span class="sxs-lookup"><span data-stu-id="f84b9-119">System Idle: %d%%.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f84b9-120">설명</span><span class="sxs-lookup"><span data-stu-id="f84b9-120">Explanation</span></span>  
 <span data-ttu-id="f84b9-121">각 스케줄러에서 진행률 기호가 표시되지 않습니다. 이 오류는 스레드를 더 이상 진행할 수 없고 새 작업을 선택 및 처리할 수 없는 교착 상태로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f84b9-121">There is no sign of progress in each of the schedulers and could be caused by deadlocks where none of the threads can advance and/or no new work can be picked up and processed.</span></span> <span data-ttu-id="f84b9-122">프로세스 사용률이 시스템에 있는 다른 프로세스보다 낮으면 서버 프로세스 CPU가 고갈될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f84b9-122">If process utilization is low then other processes on the machine may be causing the server process CPU starvation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f84b9-123">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="f84b9-123">User Action</span></span>  
 <span data-ttu-id="f84b9-124">차단이 발생하고 진행이 이루어지지 않는 원인을 확인하고 상황을 적절히 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="f84b9-124">Determine why there is blocking and no progress being made and resolve situation accordingly.</span></span> <span data-ttu-id="f84b9-125">프로세스 사용률이 낮으면 다른 프로세스에 의해 발생한 시스템 로드를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f84b9-125">If process utilization is low check the load on the system caused by other processes.</span></span>  
  
  
