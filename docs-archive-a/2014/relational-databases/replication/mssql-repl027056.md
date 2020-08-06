---
title: MSSQL_REPL027056 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL027056 error
ms.assetid: 92d62f3c-b8ae-482e-a348-2e9a8ee9786e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 44fb130321ec54c39559d52e493cc8f3424172fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736207"
---
# <a name="mssql_repl027056"></a><span data-ttu-id="61c62-102">MSSQL_REPL027056</span><span class="sxs-lookup"><span data-stu-id="61c62-102">MSSQL_REPL027056</span></span>
    
## <a name="message-details"></a><span data-ttu-id="61c62-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="61c62-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="61c62-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="61c62-104">Product Name</span></span>|<span data-ttu-id="61c62-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="61c62-105">SQL Server</span></span>|  
|<span data-ttu-id="61c62-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="61c62-106">Event ID</span></span>|<span data-ttu-id="61c62-107">27056</span><span class="sxs-lookup"><span data-stu-id="61c62-107">27056</span></span>|  
|<span data-ttu-id="61c62-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="61c62-108">Event Source</span></span>|<span data-ttu-id="61c62-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="61c62-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="61c62-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="61c62-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="61c62-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="61c62-111">Symbolic Name</span></span>||  
|<span data-ttu-id="61c62-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="61c62-112">Message Text</span></span>|<span data-ttu-id="61c62-113">병합 프로세스에서 '%1'의 생성 기록을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="61c62-113">The merge process was unable to change generation history at the '%1'.</span></span> <span data-ttu-id="61c62-114">문제를 해결하려면 자세한 기록 로깅으로 동기화를 다시 시작하고 기록할 출력 파일을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="61c62-114">When troubleshooting, restart the synchronization with verbose history logging and specify an output file to which to write.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="61c62-115">설명</span><span class="sxs-lookup"><span data-stu-id="61c62-115">Explanation</span></span>  
 <span data-ttu-id="61c62-116">일반적으로 이 오류는 과도하게 커진 병합 복제 시스템 테이블에서 발생한 경합으로 인해 생깁니다.</span><span class="sxs-lookup"><span data-stu-id="61c62-116">This error is typically raised as a result of contention in merge replication system tables that have grown excessively large.</span></span> <span data-ttu-id="61c62-117">게시 보존 기간이 긴 경우에 주로 시스템 테이블이 방대해지며 이는 보존 기간 동안 메타데이터가 이러한 테이블에 저장되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="61c62-117">Large system tables are typically caused by a long publication retention period, because metadata must be stored in these tables until the retention period is reached.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="61c62-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="61c62-118">User Action</span></span>  
 <span data-ttu-id="61c62-119">**이 문제를 해결하려면**</span><span class="sxs-lookup"><span data-stu-id="61c62-119">**To resolve the issue:**</span></span>  
  
1.  <span data-ttu-id="61c62-120">병합 에이전트에 대한 -**DownloadGenerationsPerBatch** 및 **-UploadGenerationsPerBatch** 매개 변수 값을 줄여 오류를 발생시키는 근본 문제를 해결하는 동안 처리가 계속 진행되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="61c62-120">Decrease the value of the -**DownloadGenerationsPerBatch** and **-UploadGenerationsPerBatch** parameters for the Merge Agent to allow processing to continue while you address the underlying issue causing the error.</span></span> <span data-ttu-id="61c62-121">에이전트 프로필 및 명령줄에서 에이전트 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61c62-121">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="61c62-122">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="61c62-122">For more information, see:</span></span>  
  
    -   [<span data-ttu-id="61c62-123">복제 에이전트 프로필 작업</span><span class="sxs-lookup"><span data-stu-id="61c62-123">Work with Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
    -   [<span data-ttu-id="61c62-124">복제 에이전트의 명령 프롬프트 매개 변수 보기 및 수정&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="61c62-124">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   <span data-ttu-id="61c62-125">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md)에 할당될 최소 및 최대 메모리 양을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="61c62-125">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
2.  <span data-ttu-id="61c62-126">게시 보존 기간에 대해 가능한 낮은 설정 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="61c62-126">Specify the lowest setting possible for the publication retention period.</span></span> <span data-ttu-id="61c62-127">자세한 내용은 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="61c62-127">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
3.  <span data-ttu-id="61c62-128">병합 복제 유지 관리의 한 부분으로 병합 복제와 연결된 **MSmerge_contents**, **MSmerge_genhistory**및 **MSmerge_tombstone**, **MSmerge_current_partition_mappings**및 **MSmerge_past_partition_mappings**시스템 테이블의 증가를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="61c62-128">As part of maintenance for merge replication, occasionally check the growth of the system tables associated with merge replication: **MSmerge_contents**, **MSmerge_genhistory**, and **MSmerge_tombstone**, **MSmerge_current_partition_mappings**, and **MSmerge_past_partition_mappings**.</span></span> <span data-ttu-id="61c62-129">이러한 테이블의 인덱스를 주기적으로 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="61c62-129">Periodically re-index these tables.</span></span> <span data-ttu-id="61c62-130">자세한 내용은 [인덱스 다시 구성 및 다시 작성](../indexes/indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="61c62-130">For more information, see [Reorganize and Rebuild Indexes](../indexes/indexes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61c62-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="61c62-131">See Also</span></span>  
 [<span data-ttu-id="61c62-132">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="61c62-132">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
