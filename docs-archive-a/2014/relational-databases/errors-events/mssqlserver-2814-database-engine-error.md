---
title: MSSQLSERVER_2814 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2814 (Database Engine error)
ms.assetid: 22800748-9be9-4511-9428-6b8b40e5bef9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26b1fae5b683ed72cb93c3f81981bd41e2f4ad4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651036"
---
# <a name="mssqlserver_2814"></a><span data-ttu-id="0e7d5-102">MSSQLSERVER_2814</span><span class="sxs-lookup"><span data-stu-id="0e7d5-102">MSSQLSERVER_2814</span></span>
    
## <a name="details"></a><span data-ttu-id="0e7d5-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="0e7d5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0e7d5-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="0e7d5-104">Product Name</span></span>|<span data-ttu-id="0e7d5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0e7d5-105">SQL Server</span></span>|  
|<span data-ttu-id="0e7d5-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="0e7d5-106">Event ID</span></span>|<span data-ttu-id="0e7d5-107">2814</span><span class="sxs-lookup"><span data-stu-id="0e7d5-107">2814</span></span>|  
|<span data-ttu-id="0e7d5-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="0e7d5-108">Event Source</span></span>|<span data-ttu-id="0e7d5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0e7d5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0e7d5-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="0e7d5-110">Component</span></span>|<span data-ttu-id="0e7d5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0e7d5-111">SQLEngine</span></span>|  
|<span data-ttu-id="0e7d5-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="0e7d5-112">Symbolic Name</span></span>|<span data-ttu-id="0e7d5-113">PR_POSSIBLE_INFINITE_RECOMPILE</span><span class="sxs-lookup"><span data-stu-id="0e7d5-113">PR_POSSIBLE_INFINITE_RECOMPILE</span></span>|  
|<span data-ttu-id="0e7d5-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="0e7d5-114">Message Text</span></span>|<span data-ttu-id="0e7d5-115">SQLHANDLE %hs, PlanHandle %hs, 시작 오프셋 %d, 끝 오프셋 %d에 대해 발생 가능한 무한 재컴파일이 검색되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0e7d5-115">A possible infinite recompile was detected for SQLHANDLE %hs, PlanHandle %hs, starting offset %d, ending offset %d.</span></span> <span data-ttu-id="0e7d5-116">마지막 재컴파일 이유는 %d이었습니다.</span><span class="sxs-lookup"><span data-stu-id="0e7d5-116">The last recompile reason was %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0e7d5-117">설명</span><span class="sxs-lookup"><span data-stu-id="0e7d5-117">Explanation</span></span>  
 <span data-ttu-id="0e7d5-118">하나 이상의 문으로 인해 쿼리 일괄 처리가 50회 이상 재컴파일되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0e7d5-118">One or more statements caused the query batch to recompile at least 50 times.</span></span> <span data-ttu-id="0e7d5-119">재컴파일이 더 이상 수행되지 않도록 하려면 지정된 문을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7d5-119">The specified statement should be corrected to avoid further recompilations.</span></span>  
  
 <span data-ttu-id="0e7d5-120">다음 표에서는 재컴파일의 이유를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7d5-120">The following table lists the reasons for recompilation.</span></span>  
  
|<span data-ttu-id="0e7d5-121">이유 코드</span><span class="sxs-lookup"><span data-stu-id="0e7d5-121">Reason code</span></span>|<span data-ttu-id="0e7d5-122">Description</span><span class="sxs-lookup"><span data-stu-id="0e7d5-122">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="0e7d5-123">1</span><span class="sxs-lookup"><span data-stu-id="0e7d5-123">1</span></span>|<span data-ttu-id="0e7d5-124">스키마가 변경됨</span><span class="sxs-lookup"><span data-stu-id="0e7d5-124">Schema changed</span></span>|  
|<span data-ttu-id="0e7d5-125">2</span><span class="sxs-lookup"><span data-stu-id="0e7d5-125">2</span></span>|<span data-ttu-id="0e7d5-126">통계가 변경됨</span><span class="sxs-lookup"><span data-stu-id="0e7d5-126">Statistics changed</span></span>|  
|<span data-ttu-id="0e7d5-127">3</span><span class="sxs-lookup"><span data-stu-id="0e7d5-127">3</span></span>|<span data-ttu-id="0e7d5-128">컴파일이 지연됨</span><span class="sxs-lookup"><span data-stu-id="0e7d5-128">Deferred compile</span></span>|  
|<span data-ttu-id="0e7d5-129">4</span><span class="sxs-lookup"><span data-stu-id="0e7d5-129">4</span></span>|<span data-ttu-id="0e7d5-130">설정된 옵션이 변경됨</span><span class="sxs-lookup"><span data-stu-id="0e7d5-130">Set option changed</span></span>|  
|<span data-ttu-id="0e7d5-131">5</span><span class="sxs-lookup"><span data-stu-id="0e7d5-131">5</span></span>|<span data-ttu-id="0e7d5-132">임시 테이블이 변경됨</span><span class="sxs-lookup"><span data-stu-id="0e7d5-132">Temp table changed</span></span>|  
|<span data-ttu-id="0e7d5-133">6</span><span class="sxs-lookup"><span data-stu-id="0e7d5-133">6</span></span>|<span data-ttu-id="0e7d5-134">원격 행 집합이 변경됨</span><span class="sxs-lookup"><span data-stu-id="0e7d5-134">Remote rowset changed</span></span>|  
|<span data-ttu-id="0e7d5-135">7</span><span class="sxs-lookup"><span data-stu-id="0e7d5-135">7</span></span>|<span data-ttu-id="0e7d5-136">찾아보기 권한이 변경됨</span><span class="sxs-lookup"><span data-stu-id="0e7d5-136">For Browse permissions changed</span></span>|  
|<span data-ttu-id="0e7d5-137">8</span><span class="sxs-lookup"><span data-stu-id="0e7d5-137">8</span></span>|<span data-ttu-id="0e7d5-138">쿼리 알림 환경이 변경됨</span><span class="sxs-lookup"><span data-stu-id="0e7d5-138">Query notification environment changed</span></span>|  
|<span data-ttu-id="0e7d5-139">9</span><span class="sxs-lookup"><span data-stu-id="0e7d5-139">9</span></span>|<span data-ttu-id="0e7d5-140">파티션 뷰가 변경됨</span><span class="sxs-lookup"><span data-stu-id="0e7d5-140">Partition view changed</span></span>|  
|<span data-ttu-id="0e7d5-141">10</span><span class="sxs-lookup"><span data-stu-id="0e7d5-141">10</span></span>|<span data-ttu-id="0e7d5-142">커서 옵션이 변경됨</span><span class="sxs-lookup"><span data-stu-id="0e7d5-142">Cursor options changed</span></span>|  
|<span data-ttu-id="0e7d5-143">11</span><span class="sxs-lookup"><span data-stu-id="0e7d5-143">11</span></span>|<span data-ttu-id="0e7d5-144">옵션(recompile)이 요청됨</span><span class="sxs-lookup"><span data-stu-id="0e7d5-144">Option (recompile) requested</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="0e7d5-145">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="0e7d5-145">User Action</span></span>  
  
1.  <span data-ttu-id="0e7d5-146">다음 쿼리를 실행하여 재컴파일을 발생시키는 문을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="0e7d5-146">View the statement causing the recompilation by running the following query.</span></span> <span data-ttu-id="0e7d5-147">*sql_handle*, *starting_offset*, *ending_offset* 및 *plan_handle* 자리 표시자를 오류 메시지에 지정된 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="0e7d5-147">Replace the *sql_handle*, *starting_offset*, *ending_offset*, and *plan_handle* placeholders with the values specified in the error message.</span></span> <span data-ttu-id="0e7d5-148">임시 및 준비된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문의 경우 **database_name** 및 **object_name** 열은 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="0e7d5-148">Note that the **database_name** and **object_name** columns will be NULL for ad hoc and prepared [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
     <span data-ttu-id="0e7d5-149">SELECT DB_NAME(st.dbid) AS database_name</span><span class="sxs-lookup"><span data-stu-id="0e7d5-149">SELECT DB_NAME(st.dbid) AS database_name</span></span>  
  
     <span data-ttu-id="0e7d5-150">, OBJECT_NAME(st.objectid) AS object_name</span><span class="sxs-lookup"><span data-stu-id="0e7d5-150">, OBJECT_NAME(st.objectid) AS object_name</span></span>  
  
     <span data-ttu-id="0e7d5-151">, st.text</span><span class="sxs-lookup"><span data-stu-id="0e7d5-151">, st.text</span></span>  
  
     <span data-ttu-id="0e7d5-152">FROM sys.dm_exec_query_stats AS qs</span><span class="sxs-lookup"><span data-stu-id="0e7d5-152">FROM sys.dm_exec_query_stats AS qs</span></span>  
  
     <span data-ttu-id="0e7d5-153">CROSS APPLY sys.dm_exec_sql_text (*sql_handle*) AS st</span><span class="sxs-lookup"><span data-stu-id="0e7d5-153">CROSS APPLY sys.dm_exec_sql_text (*sql_handle*) AS st</span></span>  
  
     <span data-ttu-id="0e7d5-154">WHERE qs.statement_start_offset = *starting_offset*</span><span class="sxs-lookup"><span data-stu-id="0e7d5-154">WHERE qs.statement_start_offset = *starting_offset*</span></span>  
  
     <span data-ttu-id="0e7d5-155">AND qs.statement_end_offset = *ending_offset*</span><span class="sxs-lookup"><span data-stu-id="0e7d5-155">AND qs.statement_end_offset = *ending_offset*</span></span>  
  
     <span data-ttu-id="0e7d5-156">AND qs.plan_handle = *plan_handle*;</span><span class="sxs-lookup"><span data-stu-id="0e7d5-156">AND qs.plan_handle = *plan_handle*;</span></span>  
  
2.  <span data-ttu-id="0e7d5-157">이유 코드 설명에 따라 문, 일괄 처리 또는 프로시저를 수정하여 재컴파일을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7d5-157">Based on the reason code description, modify the statement, batch, or procedure to avoid recompilations.</span></span> <span data-ttu-id="0e7d5-158">예를 들어 저장 프로시저에는 하나 이상의 SET 문이 포함되어 있을 수 있는데,</span><span class="sxs-lookup"><span data-stu-id="0e7d5-158">For example, a stored procedure may contain one or more SET statements.</span></span> <span data-ttu-id="0e7d5-159">이러한 문을 프로시저에서 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7d5-159">These statements should be removed from the procedure.</span></span> <span data-ttu-id="0e7d5-160">재컴파일의 원인 및 해결 방법에 대한 추가 예는 [Batch Compilation, Recompilation, and Plan Caching Issues in SQL Server 2005](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/administrator/cc966425(v=technet.10))(SQL Server 2005에서의 일괄 컴파일, 다시 컴파일 및 계획 캐싱 문제)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0e7d5-160">For additional examples of recompilation causes and resolutions, see [Batch Compilation, Recompilation, and Plan Caching Issues in SQL Server 2005](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/administrator/cc966425(v=technet.10)).</span></span>  
  
3.  <span data-ttu-id="0e7d5-161">문제가 지속되면 Microsoft 고객 지원 서비스에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="0e7d5-161">If the problem persists, contact Microsoft Customer Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e7d5-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e7d5-162">See Also</span></span>  
 [<span data-ttu-id="0e7d5-163">SQL:StmtRecompile 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="0e7d5-163">SQL:StmtRecompile Event Class</span></span>](../event-classes/sql-stmtrecompile-event-class.md)  
  
  
