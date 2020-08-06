---
title: MSSQL_ENG021076 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021076 error
ms.assetid: 612e5c59-ba3e-49c3-a3df-56bac3d850a2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4161428767ce78726436c0cf794f5250140d35b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730504"
---
# <a name="mssql_eng021076"></a><span data-ttu-id="4e50a-102">MSSQL_ENG021076</span><span class="sxs-lookup"><span data-stu-id="4e50a-102">MSSQL_ENG021076</span></span>
    
## <a name="message-details"></a><span data-ttu-id="4e50a-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="4e50a-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4e50a-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="4e50a-104">Product Name</span></span>|<span data-ttu-id="4e50a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4e50a-105">SQL Server</span></span>|  
|<span data-ttu-id="4e50a-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="4e50a-106">Event ID</span></span>|<span data-ttu-id="4e50a-107">21076</span><span class="sxs-lookup"><span data-stu-id="4e50a-107">21076</span></span>|  
|<span data-ttu-id="4e50a-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="4e50a-108">Event Source</span></span>|<span data-ttu-id="4e50a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4e50a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4e50a-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="4e50a-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="4e50a-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="4e50a-111">Symbolic Name</span></span>||  
|<span data-ttu-id="4e50a-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="4e50a-112">Message Text</span></span>|<span data-ttu-id="4e50a-113">아티클 '%s'의 초기 스냅샷을 아직 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4e50a-113">The initial snapshot for article '%s' is not yet available.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4e50a-114">설명</span><span class="sxs-lookup"><span data-stu-id="4e50a-114">Explanation</span></span>  
 <span data-ttu-id="4e50a-115">스냅샷 에이전트에서 스냅샷 생성을 완료하기 전에 배포 에이전트가 시작되는 경우 MSSQL_ENG021076 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e50a-115">Error MSSQL_ENG021076 can be raised if the Distribution Agent is started before the Snapshot Agent has finished generating the snapshot.</span></span> <span data-ttu-id="4e50a-116">이 오류는 게시에 아티클이 하나만 있을 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4e50a-116">This error is raised only if the publication contains a single article.</span></span> <span data-ttu-id="4e50a-117">게시에 두 개 이상의 아티클이 있으면 MSSQL_ENG021075 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4e50a-117">If the publication contains more than one article, MSSQL_ENG021075 is raised instead.</span></span> <span data-ttu-id="4e50a-118">자세한 내용은 [MSSQL_ENG021075](mssql-eng021075.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e50a-118">For more information, see [MSSQL_ENG021075](mssql-eng021075.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4e50a-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="4e50a-119">User Action</span></span>  
 <span data-ttu-id="4e50a-120">구독이 생성된 후 게시의 스냅샷 에이전트가 시작되지 않은 경우 또는 구독을 다시 초기화하도록 마지막으로 선택한 후 스냅샷 에이전트가 시작되지 않은 경우 배포 에이전트를 시작하기 전에 스냅샷 에이전트를 시작한 다음 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e50a-120">If the Snapshot Agent for the publication has not been started since the subscription was created, or if it has not been started since the last time you chose to reinitialize the subscription, start the Snapshot Agent and let it complete before starting the Distribution Agent.</span></span> <span data-ttu-id="4e50a-121">자세한 내용은 [스냅샷 만들기 및 적용](create-and-apply-the-snapshot.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e50a-121">For more information, see [Create and Apply the Snapshot](create-and-apply-the-snapshot.md).</span></span>  
  
 <span data-ttu-id="4e50a-122">스냅샷 에이전트가 완료되지 않는 경우 스냅샷 에이전트 기록에서 오류를 확인한 후 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="4e50a-122">If the Snapshot Agent does not complete, check the Snapshot Agent history for errors and address them.</span></span> <span data-ttu-id="4e50a-123">복제 모니터에서 에이전트 상태 및 오류 정보를 보는 방법에 대한 자세한 내용은 [복제 모니터를 사용하여 정보 보기 및 작업 수행](monitor/view-information-and-perform-tasks-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e50a-123">For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="4e50a-124">오류가 계속 발생하면 에이전트의 로깅을 늘리고 해당 로그의 출력 파일을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="4e50a-124">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="4e50a-125">오류의 컨텍스트에 따라 이러한 작업을 수행하면 오류 및/또는 추가 오류 메시지가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e50a-125">Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e50a-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4e50a-126">See Also</span></span>  
 [<span data-ttu-id="4e50a-127">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="4e50a-127">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
