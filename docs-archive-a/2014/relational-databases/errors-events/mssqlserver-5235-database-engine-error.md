---
title: MSSQLSERVER_5235 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5235 (Database Engine error)
ms.assetid: 1aa7e6a5-7ccb-43c8-a1fd-d50e92e0a798
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 42c807944d7506a6a118de97ccd8c2c488942c8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740024"
---
# <a name="mssqlserver_5235"></a><span data-ttu-id="3bf96-102">MSSQLSERVER_5235</span><span class="sxs-lookup"><span data-stu-id="3bf96-102">MSSQLSERVER_5235</span></span>
    
## <a name="details"></a><span data-ttu-id="3bf96-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="3bf96-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3bf96-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="3bf96-104">Product Name</span></span>|<span data-ttu-id="3bf96-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3bf96-105">SQL Server</span></span>|  
|<span data-ttu-id="3bf96-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="3bf96-106">Event ID</span></span>|<span data-ttu-id="3bf96-107">5235</span><span class="sxs-lookup"><span data-stu-id="3bf96-107">5235</span></span>|  
|<span data-ttu-id="3bf96-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="3bf96-108">Event Source</span></span>|<span data-ttu-id="3bf96-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3bf96-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3bf96-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="3bf96-110">Component</span></span>|<span data-ttu-id="3bf96-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3bf96-111">SQLEngine</span></span>|  
|<span data-ttu-id="3bf96-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="3bf96-112">Symbolic Name</span></span>|<span data-ttu-id="3bf96-113">DBCC4_ERRORLOG_SUMMARY_PREMATURE_TERMINATION</span><span class="sxs-lookup"><span data-stu-id="3bf96-113">DBCC4_ERRORLOG_SUMMARY_PREMATURE_TERMINATION</span></span>|  
|<span data-ttu-id="3bf96-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="3bf96-114">Message Text</span></span>|<span data-ttu-id="3bf96-115">[응급] USER_NAME이(가) 실행한 DBCC DBCC_COMMAND_DETAILS이(가) 오류 상태 ERROR_STATE(으)로 인해 비정상적으로 종료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-115">[EMERGENCY] DBCC DBCC_COMMAND_DETAILS executed by USER_NAME terminated abnormally due to error state ERROR_STATE.</span></span> <span data-ttu-id="3bf96-116">경과된 시간: HOURS 시간 MINUTES 분 SECONDS 초</span><span class="sxs-lookup"><span data-stu-id="3bf96-116">Elapsed time: HOURS hours MINUTES minutes SECONDS seconds.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3bf96-117">설명</span><span class="sxs-lookup"><span data-stu-id="3bf96-117">Explanation</span></span>  
 <span data-ttu-id="3bf96-118">이는 명령이 실행되는 동안 예기치 않게 종료되는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그에 인쇄되는 DBCC 요약 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-118">This is the summary message that DBCC prints to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log when an unexpected termination occurs while the command is running.</span></span> <span data-ttu-id="3bf96-119">메시지에 보고되는 오류 상태는 예기치 않은 종료 유형을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-119">The error state reported in the message defines the type of unexpected termination.</span></span>  
  
 <span data-ttu-id="3bf96-120">다음 표에서는 오류 상태를 나열 및 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-120">The following table lists and defines the error states.</span></span>  
  
|<span data-ttu-id="3bf96-121">오류 상태</span><span class="sxs-lookup"><span data-stu-id="3bf96-121">Error state</span></span>|<span data-ttu-id="3bf96-122">정의</span><span class="sxs-lookup"><span data-stu-id="3bf96-122">Definition</span></span>|  
|-----------------|----------------|  
|<span data-ttu-id="3bf96-123">상태 0</span><span class="sxs-lookup"><span data-stu-id="3bf96-123">State 0</span></span>|<span data-ttu-id="3bf96-124">메타데이터가 손상되어 문이 종료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-124">The statement was terminated because of a fatal metadata corruption.</span></span> <span data-ttu-id="3bf96-125">이 메시지는 하나 이상의 오류 8930과 함께 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-125">This message will be accompanied by one or more instances of error 8930.</span></span>|  
|<span data-ttu-id="3bf96-126">상태 1</span><span class="sxs-lookup"><span data-stu-id="3bf96-126">State 1</span></span>|<span data-ttu-id="3bf96-127">내부 검사에 실패하여 문이 종료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-127">The statement was terminated because of an internal check failure.</span></span> <span data-ttu-id="3bf96-128">이 메시지는 하나 이상의 오류 8967과 함께 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-128">This message will be accompanied by one or more instances of error 8967.</span></span>|  
|<span data-ttu-id="3bf96-129">상태 2</span><span class="sxs-lookup"><span data-stu-id="3bf96-129">State 2</span></span>|<span data-ttu-id="3bf96-130">핵심 스토리지 엔진 시스템 테이블에 대한 기본 시스템 테이블 검사가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-130">Basic system table checks of the core storage engine system tables failed.</span></span> <span data-ttu-id="3bf96-131">이 메시지는 하나 이상의 오류 [7984](mssqlserver-7984-database-engine-error.md), 7985, [7986](mssqlserver-7986-database-engine-error.md), [7987](mssqlserver-7987-database-engine-error.md) 또는 [7988](mssqlserver-7988-database-engine-error.md)과 함께 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-131">This message will be accompanied by one or more instances of error [7984](mssqlserver-7984-database-engine-error.md), 7985, [7986](mssqlserver-7986-database-engine-error.md), [7987](mssqlserver-7987-database-engine-error.md), or [7988](mssqlserver-7988-database-engine-error.md).</span></span>|  
|<span data-ttu-id="3bf96-132">상태 3</span><span class="sxs-lookup"><span data-stu-id="3bf96-132">State 3</span></span>|<span data-ttu-id="3bf96-133">트랜잭션 로그를 다시 작성한 후 데이터베이스를 시작할 수 없어 DBCC 응급 모드 복구가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-133">DBCC emergency-mode repair failed because the database could not be started after rebuilding the transaction log.</span></span> <span data-ttu-id="3bf96-134">이 메시지는 오류 7909와 함께 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-134">This message will be accompanied by error 7909.</span></span>|  
|<span data-ttu-id="3bf96-135">상태 4</span><span class="sxs-lookup"><span data-stu-id="3bf96-135">State 4</span></span>|<span data-ttu-id="3bf96-136">명령을 실행하는 동안 어설션 오류나 액세스 위반이 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-136">A failed assertion or access violation occurred during the execution of the command.</span></span>|  
|<span data-ttu-id="3bf96-137">상태 5</span><span class="sxs-lookup"><span data-stu-id="3bf96-137">State 5</span></span>|<span data-ttu-id="3bf96-138">알 수 없는 오류가 발생하여 DBCC 명령이 예기치 않게 종료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-138">An unknown failure occurred that unexpectedly terminated the DBCC command.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="3bf96-139">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="3bf96-139">User Action</span></span>  
 <span data-ttu-id="3bf96-140">다음 표에서는 특정 오류 상태에 적합한 사용자 동작을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-140">The following table provides the user action that is appropriate for the specified error state.</span></span>  
  
|<span data-ttu-id="3bf96-141">오류 상태</span><span class="sxs-lookup"><span data-stu-id="3bf96-141">Error state</span></span>|<span data-ttu-id="3bf96-142">사용자 조치</span><span class="sxs-lookup"><span data-stu-id="3bf96-142">User action</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="3bf96-143">상태 0</span><span class="sxs-lookup"><span data-stu-id="3bf96-143">State 0</span></span>|<span data-ttu-id="3bf96-144">백업에서 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-144">Restore from backup.</span></span>|  
|<span data-ttu-id="3bf96-145">상태 1</span><span class="sxs-lookup"><span data-stu-id="3bf96-145">State 1</span></span>|<span data-ttu-id="3bf96-146">[!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS(고객 서비스 지원 센터)에 문의합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-146">Contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>|  
|<span data-ttu-id="3bf96-147">상태 2</span><span class="sxs-lookup"><span data-stu-id="3bf96-147">State 2</span></span>|<span data-ttu-id="3bf96-148">백업에서 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-148">Restore from backup.</span></span>|  
|<span data-ttu-id="3bf96-149">상태 3</span><span class="sxs-lookup"><span data-stu-id="3bf96-149">State 3</span></span>|<span data-ttu-id="3bf96-150">백업에서 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-150">Restore from backup.</span></span>|  
|<span data-ttu-id="3bf96-151">상태 4</span><span class="sxs-lookup"><span data-stu-id="3bf96-151">State 4</span></span>|<span data-ttu-id="3bf96-152">CSS에 문의합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-152">Contact CSS.</span></span>|  
|<span data-ttu-id="3bf96-153">상태 5</span><span class="sxs-lookup"><span data-stu-id="3bf96-153">State 5</span></span>|<span data-ttu-id="3bf96-154">명령을 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-154">Run the command again.</span></span> <span data-ttu-id="3bf96-155">문제가 지속되면 CSS에 문의합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf96-155">If the problem persists, contact CSS.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3bf96-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3bf96-156">See Also</span></span>  
 [<span data-ttu-id="3bf96-157">DBCC&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf96-157">DBCC &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-transact-sql)  
  
  
