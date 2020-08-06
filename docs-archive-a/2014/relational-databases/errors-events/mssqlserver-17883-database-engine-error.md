---
title: MSSQLSERVER_17883 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17883 (Database Engine error)
ms.assetid: adaf1c04-e397-4a69-90b8-9353a37277ea
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 46488fb6f7adac2c1109871f2aad4c79352829ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729523"
---
# <a name="mssqlserver_17883"></a><span data-ttu-id="4c788-102">MSSQLSERVER_17883</span><span class="sxs-lookup"><span data-stu-id="4c788-102">MSSQLSERVER_17883</span></span>
    
## <a name="details"></a><span data-ttu-id="4c788-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="4c788-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4c788-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="4c788-104">Product Name</span></span>|<span data-ttu-id="4c788-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4c788-105">SQL Server</span></span>|  
|<span data-ttu-id="4c788-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="4c788-106">Event ID</span></span>|<span data-ttu-id="4c788-107">17883</span><span class="sxs-lookup"><span data-stu-id="4c788-107">17883</span></span>|  
|<span data-ttu-id="4c788-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="4c788-108">Event Source</span></span>|<span data-ttu-id="4c788-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4c788-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4c788-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="4c788-110">Component</span></span>|<span data-ttu-id="4c788-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4c788-111">SQLEngine</span></span>|  
|<span data-ttu-id="4c788-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="4c788-112">Symbolic Name</span></span>|<span data-ttu-id="4c788-113">SRV_SCHEDULER_NONYIELDING</span><span class="sxs-lookup"><span data-stu-id="4c788-113">SRV_SCHEDULER_NONYIELDING</span></span>|  
|<span data-ttu-id="4c788-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="4c788-114">Message Text</span></span>|<span data-ttu-id="4c788-115">프로세스 %ld:%ld:%ld(0x%lx) 작업자 0x%p이(가) 스케줄러 %ld에서 잠긴 것 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4c788-115">Process %ld:%ld:%ld (0x%lx) Worker 0x%p appears to be non-yielding on Scheduler %ld.</span></span> <span data-ttu-id="4c788-116">스레드 만든 시간: %I64d.</span><span class="sxs-lookup"><span data-stu-id="4c788-116">Thread creation time: %I64d.</span></span> <span data-ttu-id="4c788-117">대략적인 스레드 CPU 사용량: 커널 %I64dms, 사용자 %I64dms.</span><span class="sxs-lookup"><span data-stu-id="4c788-117">Approx Thread CPU Used: kernel %I64d ms, user %I64d ms.</span></span> <span data-ttu-id="4c788-118">프로세스 사용률 %d%%.</span><span class="sxs-lookup"><span data-stu-id="4c788-118">Process Utilization %d%%.</span></span> <span data-ttu-id="4c788-119">시스템 유휴 시간 %d%%.</span><span class="sxs-lookup"><span data-stu-id="4c788-119">System Idle %d%%.</span></span> <span data-ttu-id="4c788-120">간격: %I64dms.</span><span class="sxs-lookup"><span data-stu-id="4c788-120">Interval: %I64d ms.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4c788-121">설명</span><span class="sxs-lookup"><span data-stu-id="4c788-121">Explanation</span></span>  
 <span data-ttu-id="4c788-122">스케줄러에서 잠긴 스레드와 관련된 문제가 있을 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4c788-122">Indicates that there is a possible problem with a thread not yielding on a scheduler.</span></span>  <span data-ttu-id="4c788-123">이 오류는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 버그 때문에 발생하거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 충분한 실행 주기가 없는 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c788-123">This could be caused by a bug in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not getting enough cycles to execute.</span></span>  <span data-ttu-id="4c788-124">이 오류는 스레드가 결국 양도되면 나타나지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c788-124">This error could go away if the thread eventually yields.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4c788-125">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="4c788-125">User Action</span></span>  
 <span data-ttu-id="4c788-126">시스템 로드가 너무 많으면 로드를 줄이고, 그렇지 않으면 Microsoft 고객 지원 서비스에 문의합니다.</span><span class="sxs-lookup"><span data-stu-id="4c788-126">If excessive load on system reduce load otherwise contact Microsoft Customer Support Services.</span></span>  
  
  
