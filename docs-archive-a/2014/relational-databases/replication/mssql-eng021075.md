---
title: MSSQL_ENG021075 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021075 error
ms.assetid: c8c29543-d1f6-49d5-b6c8-e8c3aa373090
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 20f2428038326681f5f8eb877e5c3017ced30f00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653285"
---
# <a name="mssql_eng021075"></a><span data-ttu-id="9f53d-102">MSSQL_ENG021075</span><span class="sxs-lookup"><span data-stu-id="9f53d-102">MSSQL_ENG021075</span></span>
    
## <a name="message-details"></a><span data-ttu-id="9f53d-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="9f53d-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9f53d-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="9f53d-104">Product Name</span></span>|<span data-ttu-id="9f53d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9f53d-105">SQL Server</span></span>|  
|<span data-ttu-id="9f53d-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="9f53d-106">Event ID</span></span>|<span data-ttu-id="9f53d-107">21075</span><span class="sxs-lookup"><span data-stu-id="9f53d-107">21075</span></span>|  
|<span data-ttu-id="9f53d-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="9f53d-108">Event Source</span></span>|<span data-ttu-id="9f53d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9f53d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9f53d-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="9f53d-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="9f53d-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="9f53d-111">Symbolic Name</span></span>||  
|<span data-ttu-id="9f53d-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="9f53d-112">Message Text</span></span>|<span data-ttu-id="9f53d-113">게시 '%s'의 초기 스냅샷을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9f53d-113">The initial snapshot for publication '%s' is not yet available.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9f53d-114">설명</span><span class="sxs-lookup"><span data-stu-id="9f53d-114">Explanation</span></span>  
 <span data-ttu-id="9f53d-115">MSSQL_ENG021075 오류는 스냅샷 에이전트가 스냅샷 생성을 완료하기 전에 배포 에이전트 또는 병합 에이전트를 시작한 경우 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9f53d-115">Error MSSQL_ENG021075 is raised if the Distribution Agent or Merge Agent is started before the Snapshot Agent has finished generating the snapshot.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9f53d-116">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="9f53d-116">User Action</span></span>  
 <span data-ttu-id="9f53d-117">구독이 생성된 후 게시에 대한 스냅샷 에이전트가 시작되지 않았거나 마지막으로 구독을 다시 초기화한 이후 스냅샷 에이전트가 시작되지 않은 경우 스냅샷 에이전트를 시작하고 완료될 때까지 기다린 다음 배포 에이전트 또는 병합 에이전트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9f53d-117">If the Snapshot Agent for the publication has not been started since the subscription was created, or if it has not been started since the last time you chose to reinitialize the subscription, start the Snapshot Agent and let it complete before starting the Distribution Agent or Merge Agent.</span></span> <span data-ttu-id="9f53d-118">자세한 내용은 [스냅샷 만들기 및 적용](create-and-apply-the-snapshot.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9f53d-118">For more information, see [Create and Apply the Snapshot](create-and-apply-the-snapshot.md).</span></span>  
  
 <span data-ttu-id="9f53d-119">스냅샷 에이전트가 완료되지 않는 경우 스냅샷 에이전트 기록에서 오류를 확인한 후 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="9f53d-119">If the Snapshot Agent does not complete, check the Snapshot Agent history for errors and address them.</span></span> <span data-ttu-id="9f53d-120">복제 모니터에서 에이전트 상태 및 오류 정보를 보는 방법에 대한 자세한 내용은 [복제 모니터를 사용하여 정보 보기 및 작업 수행](monitor/view-information-and-perform-tasks-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9f53d-120">For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="9f53d-121">오류가 계속 발생하면 에이전트의 로깅을 늘리고 해당 로그의 출력 파일을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="9f53d-121">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="9f53d-122">오류의 컨텍스트에 따라 이러한 작업을 수행하면 오류 및/또는 추가 오류 메시지가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f53d-122">Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f53d-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9f53d-123">See Also</span></span>  
 [<span data-ttu-id="9f53d-124">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="9f53d-124">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
