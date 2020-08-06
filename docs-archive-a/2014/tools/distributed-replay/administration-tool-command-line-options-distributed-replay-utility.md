---
title: 관리 도구 명령줄 옵션(Distributed Replay Utility) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: c01b0ed3-67e4-4561-92d2-a8fbb086aca8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 506be071f44937d82902585e5a0621212083dfa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651955"
---
# <a name="administration-tool-command-line-options-distributed-replay-utility"></a><span data-ttu-id="ea71a-102">관리 도구 명령줄 옵션(Distributed Replay Utility)</span><span class="sxs-lookup"><span data-stu-id="ea71a-102">Administration Tool Command-line Options (Distributed Replay Utility)</span></span>
  <span data-ttu-id="ea71a-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 관리 도구인는 `DReplay.exe` Distributed Replay controller와 통신 하는 데 사용할 수 있는 명령줄 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="ea71a-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="ea71a-104">이 관리 도구를 사용하여 컨트롤러에서 작업을 시작, 모니터링 및 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea71a-104">Use the administration tool to initiate, monitor, and cancel operations on the controller.</span></span>  
  
 <span data-ttu-id="ea71a-105">![항목 링크 아이콘](../../database-engine/media/topic-link.gif "항목 링크 아이콘") 관리 도구 구문에서 사용되는 구문 표기 규칙에 대한 자세한 내용은 [Transact-SQL 구문 표기 규칙&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea71a-105">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea71a-106">구문</span><span class="sxs-lookup"><span data-stu-id="ea71a-106">Syntax</span></span>  
  
```  
  
      dreplay {preprocess|replay|status|cancel} [options] [-?]}  
  
Usage:  
  
  dreplay preprocess [-mcontroller] -iinput_trace_file  
    -dcontroller_working_dir [-cconfig_file] [-fstatus_interval]  
  
  dreplay replay [-mcontroller] -dcontroller_working_dir [-o]  
    [-starget_server] -wclients [-cconfig_file]  
    [-fstatus_interval]  
  
  dreplay status [-mcontroller] [-fstatus_interval]  
  
  dreplay cancel [-mcontroller] [-q]   
```  
  
## <a name="remarks"></a><span data-ttu-id="ea71a-107">설명</span><span class="sxs-lookup"><span data-stu-id="ea71a-107">Remarks</span></span>  
 <span data-ttu-id="ea71a-108">`DReplay.exe`에서 다음 명령줄 옵션을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea71a-108">You can issue the following command-line options with `DReplay.exe`:</span></span>  
  
 <span data-ttu-id="ea71a-109">**preprocess**</span><span class="sxs-lookup"><span data-stu-id="ea71a-109">**preprocess**</span></span>  
 <span data-ttu-id="ea71a-110">전처리 단계를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ea71a-110">Initiates the preprocess stage.</span></span> <span data-ttu-id="ea71a-111">컨트롤러는 대상 서버에 대해 재생할 입력 추적 데이터(프로덕션 환경에서 캡처한 데이터)를 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="ea71a-111">The controller prepares the input trace data, which you captured from the production environment, for replay against the target server.</span></span>  
  
 <span data-ttu-id="ea71a-112">**재생(replay)**</span><span class="sxs-lookup"><span data-stu-id="ea71a-112">**replay**</span></span>  
 <span data-ttu-id="ea71a-113">이벤트 재생 단계를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ea71a-113">Initiates the event replay stage.</span></span> <span data-ttu-id="ea71a-114">컨트롤러는 재생 데이터를 지정된 클라이언트로 발송하고 분산 재생을 시작하며 클라이언트를 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="ea71a-114">The controller dispatches replay data to the specified clients, launches the distributed replay, and synchronizes the clients.</span></span> <span data-ttu-id="ea71a-115">필요에 따라 선택된 각 클라이언트는 재생 작업을 기록하고 결과 추적 파일을 로컬에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ea71a-115">Optionally, each client that was selected records the replay activity and saves result trace files locally.</span></span>  
  
 <span data-ttu-id="ea71a-116">**status**</span><span class="sxs-lookup"><span data-stu-id="ea71a-116">**status**</span></span>  
 <span data-ttu-id="ea71a-117">컨트롤러를 쿼리하여 현재 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ea71a-117">Queries the controller and displays the current status.</span></span>  
  
 <span data-ttu-id="ea71a-118">**cancel**</span><span class="sxs-lookup"><span data-stu-id="ea71a-118">**cancel**</span></span>  
 <span data-ttu-id="ea71a-119">컨트롤러에서 실행 중인 현재 작업을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="ea71a-119">Cancels the current operation that is running on the controller.</span></span>  
  
 <span data-ttu-id="ea71a-120">명령 인수 및 예가 포함된 자세한 구문 정보는 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ea71a-120">For detailed syntax information that includes the command arguments and examples, see the following topics:</span></span>  
  
-   [<span data-ttu-id="ea71a-121">전처리 옵션&#40;Distributed Replay Utility Administration Tool&#41;</span><span class="sxs-lookup"><span data-stu-id="ea71a-121">Preprocess Option &#40;Distributed Replay Administration Tool&#41;</span></span>](preprocess-option-distributed-replay-administration-tool.md)  
  
-   [<span data-ttu-id="ea71a-122">재생 옵션&#40;Distributed Replay Administration Tool&#41;</span><span class="sxs-lookup"><span data-stu-id="ea71a-122">Replay Option &#40;Distributed Replay Administration Tool&#41;</span></span>](replay-option-distributed-replay-administration-tool.md)  
  
-   [<span data-ttu-id="ea71a-123">상태 옵션&#40;Distributed Replay Administration Tool&#41;</span><span class="sxs-lookup"><span data-stu-id="ea71a-123">Status Option &#40;Distributed Replay Administration Tool&#41;</span></span>](status-option-distributed-replay-administration-tool.md)  
  
-   [<span data-ttu-id="ea71a-124">취소 옵션&#40;Distributed Replay Administration Tool&#41;</span><span class="sxs-lookup"><span data-stu-id="ea71a-124">Cancel Option &#40;Distributed Replay Administration Tool&#41;</span></span>](cancel-option-distributed-replay-administration-tool.md)  
  
 <span data-ttu-id="ea71a-125">RPC는 언어 이벤트가 아닌 RPC로 재생됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea71a-125">RPCs are replayed as RPCs and not as language events.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="ea71a-126">사용 권한</span><span class="sxs-lookup"><span data-stu-id="ea71a-126">Permissions</span></span>  
 <span data-ttu-id="ea71a-127">관리 도구는 로컬 사용자 또는 도메인 사용자 등의 대화형 사용자 계정으로 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea71a-127">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="ea71a-128">로컬 사용자 계정을 사용하려면 관리 도구와 컨트롤러가 동일한 컴퓨터에서 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea71a-128">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>  
  
 <span data-ttu-id="ea71a-129">자세한 내용은 [Distributed Replay Security](distributed-replay-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea71a-129">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea71a-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea71a-130">See Also</span></span>  
 [<span data-ttu-id="ea71a-131">SQL Server Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="ea71a-131">SQL Server Distributed Replay</span></span>](sql-server-distributed-replay.md)  
  
  
