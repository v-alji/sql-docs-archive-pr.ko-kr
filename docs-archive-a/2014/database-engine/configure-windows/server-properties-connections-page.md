---
title: 서버 속성(연결 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.connections.f1
ms.assetid: 33be8ac5-12dd-4b8a-99e0-68261c219dd2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 80943bc542209fd34cf83e8db7aa76becd04194a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738709"
---
# <a name="server-properties-connections-page"></a><span data-ttu-id="e3410-102">서버 속성(연결 페이지)</span><span class="sxs-lookup"><span data-stu-id="e3410-102">Server Properties (Connections Page)</span></span>
  <span data-ttu-id="e3410-103">이 페이지를 사용하여 연결 옵션을 확인하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-103">Use this page to view or modify your connection options.</span></span>  
  
## <a name="connections"></a><span data-ttu-id="e3410-104">Connections</span><span class="sxs-lookup"><span data-stu-id="e3410-104">Connections</span></span>  
 <span data-ttu-id="e3410-105">**최대 동시 연결 수(0 = 제한 없음)**</span><span class="sxs-lookup"><span data-stu-id="e3410-105">**Maximum number of concurrent connections (0 = unlimited)**</span></span>  
 <span data-ttu-id="e3410-106">이 값을 0이 아닌 값으로 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 허용하는 연결 수가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-106">If set to a value other than zero, limits the number of connections that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will allow.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="e3410-107">이 값을 1이나 2와 같은 작은 값으로 설정하면 관리자가 서버를 관리하기 위해 연결하지 못할 수도 있습니다. 하지만 관리자 전용 연결을 통한 연결은 언제든지 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-107">Setting this to a small value, such as 1 or 2, can prevent administrators from connecting to administer the server; however, the Dedicated Admin Connection can always connect.</span></span>  
  
## <a name="default-connection-options"></a><span data-ttu-id="e3410-108">기본 연결 옵션</span><span class="sxs-lookup"><span data-stu-id="e3410-108">Default Connection Options</span></span>  
 <span data-ttu-id="e3410-109">**Default connection options**</span><span class="sxs-lookup"><span data-stu-id="e3410-109">**Default connection options**</span></span>  
 <span data-ttu-id="e3410-110">다음 표에서 설명하는 기본 연결 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-110">Specifies the default connection options, as described in the following table.</span></span>  
  
|<span data-ttu-id="e3410-111">구성 옵션</span><span class="sxs-lookup"><span data-stu-id="e3410-111">Configuration option</span></span>|<span data-ttu-id="e3410-112">Description</span><span class="sxs-lookup"><span data-stu-id="e3410-112">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="e3410-113">**지연된 제약 조건 검사 비활성화**</span><span class="sxs-lookup"><span data-stu-id="e3410-113">**disable deferred constraint checking**</span></span>|<span data-ttu-id="e3410-114">중간 또는 지연된 제약 조건 검사를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-114">Controls interim or deferred constraint checking.</span></span>|  
|<span data-ttu-id="e3410-115">**암시적 트랜잭션**</span><span class="sxs-lookup"><span data-stu-id="e3410-115">**implicit transactions**</span></span>|<span data-ttu-id="e3410-116">문 실행 시 트랜잭션을 암시적으로 실행할지 여부를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-116">Controls whether a transaction is started implicitly when a statement is run.</span></span>|  
|<span data-ttu-id="e3410-117">**커밋 시 커서 닫기**</span><span class="sxs-lookup"><span data-stu-id="e3410-117">**cursor close on commit**</span></span>|<span data-ttu-id="e3410-118">커밋 작업 수행 후 커서의 동작을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-118">Controls behavior of cursors after a commit operation has been performed.</span></span>|  
|<span data-ttu-id="e3410-119">**ANSI 경고**</span><span class="sxs-lookup"><span data-stu-id="e3410-119">**ansi warnings**</span></span>|<span data-ttu-id="e3410-120">집계 경고의 잘림과 NULL을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-120">Controls truncation and NULL in aggregate warnings.</span></span>|  
|<span data-ttu-id="e3410-121">**ANSI 패딩**</span><span class="sxs-lookup"><span data-stu-id="e3410-121">**ansi padding**</span></span>|<span data-ttu-id="e3410-122">고정 길이 변수의 패딩을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-122">Controls padding of fixed-length variables.</span></span>|  
|<span data-ttu-id="e3410-123">**ANSI NULL**</span><span class="sxs-lookup"><span data-stu-id="e3410-123">**ansi nulls**</span></span>|<span data-ttu-id="e3410-124">등호 연산자 사용 시 `NULL` 처리를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-124">Controls `NULL` handling when using equality operators.</span></span>|  
|<span data-ttu-id="e3410-125">**산술 연산 중단**</span><span class="sxs-lookup"><span data-stu-id="e3410-125">**arithmetic abort**</span></span>|<span data-ttu-id="e3410-126">쿼리 실행 중 오버플로 또는 0으로 나누기 오류가 발생하면 쿼리를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-126">Terminates a query when an overflow or divide-by-zero error occurs during query execution.</span></span>|  
|<span data-ttu-id="e3410-127">**산술 연산 무시**</span><span class="sxs-lookup"><span data-stu-id="e3410-127">**arithmetic ignore**</span></span>|<span data-ttu-id="e3410-128">쿼리 실행 중 오버플로 또는 0으로 나누기 오류가 발생하면 NULL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-128">Returns NULL when an overflow or divide-by-zero error occurs during a query.</span></span>|  
|<span data-ttu-id="e3410-129">**따옴표 붙은 식별자**</span><span class="sxs-lookup"><span data-stu-id="e3410-129">**quoted identifier**</span></span>|<span data-ttu-id="e3410-130">식을 평가할 때 큰따옴표와 작은따옴표를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-130">Differentiates between single and double quotation marks when evaluating an expression.</span></span>|  
|<span data-ttu-id="e3410-131">**열 개수 표시 안 함**</span><span class="sxs-lookup"><span data-stu-id="e3410-131">**no count**</span></span>|<span data-ttu-id="e3410-132">영향 받는 행 수를 지정하는 각 문의 끝에 반환되는 메시지를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-132">Turns off the message returned at the end of each statement that states how many rows were affected.</span></span>|  
|<span data-ttu-id="e3410-133">**ANSI NULL 기본값 설정**</span><span class="sxs-lookup"><span data-stu-id="e3410-133">**ansi null default on**</span></span>|<span data-ttu-id="e3410-134">세션에서 Null 허용에 대해 ANSI 호환성을 사용할 때 경고합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-134">Alters the session's behavior to use ANSI compatibility for nullability.</span></span> <span data-ttu-id="e3410-135">명시적 Null 허용 없이 정의된 새 열은 Null을 허용하도록 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-135">New columns defined without explicit nullability are defined to allow nulls.</span></span>|  
|<span data-ttu-id="e3410-136">**ANSI NULL 기본값 해제**</span><span class="sxs-lookup"><span data-stu-id="e3410-136">**ansi null default off**</span></span>|<span data-ttu-id="e3410-137">세션이 null 허용에 대해 ANSI 호환성을 사용하지 않을 때 경고합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-137">Alters the session's behavior not to use ANSI compatibility for nullability.</span></span> <span data-ttu-id="e3410-138">명시적 Null 허용 없이 정의된 새 열은 Null을 허용하지 않도록 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-138">New columns defined without explicit nullability are defined not to allow nulls.</span></span>|  
|<span data-ttu-id="e3410-139">**Null 연결 시 Null 생성**</span><span class="sxs-lookup"><span data-stu-id="e3410-139">**concat null yields null**</span></span>|<span data-ttu-id="e3410-140">문자열이 있는 NULL 값을 연결할 때 NULL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-140">Returns NULL when concatenating a NULL value with a string.</span></span>|  
|<span data-ttu-id="e3410-141">**숫자 반올림 시 중단**</span><span class="sxs-lookup"><span data-stu-id="e3410-141">**numeric round abort**</span></span>|<span data-ttu-id="e3410-142">식의 전체 자릿수가 떨어지면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-142">Generates an error when a loss of precision occurs in an expression.</span></span>|  
|<span data-ttu-id="e3410-143">**트랜잭션 중단**</span><span class="sxs-lookup"><span data-stu-id="e3410-143">**xact abort**</span></span>|<span data-ttu-id="e3410-144">Transact-SQL 문이 런타임 오류를 일으키면 트랜잭션을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-144">Rolls back a transaction if a Transact-SQL statement raises a run-time error.</span></span>|  
  
 <span data-ttu-id="e3410-145">연결 옵션에 대한 자세한 내용을 보려면 온라인 설명서에서 해당 옵션을 검색하십시오.</span><span class="sxs-lookup"><span data-stu-id="e3410-145">For more information on connection options, search Books Online for the specific option.</span></span>  
  
## <a name="remote-server-connections"></a><span data-ttu-id="e3410-146">원격 서버 연결</span><span class="sxs-lookup"><span data-stu-id="e3410-146">Remote Server Connections</span></span>  
 <span data-ttu-id="e3410-147">**이 서버에 대한 원격 연결 허용**</span><span class="sxs-lookup"><span data-stu-id="e3410-147">**Allow remote connections to this server**</span></span>  
 <span data-ttu-id="e3410-148">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 실행하는 원격 서버에서의 저장 프로시저 실행을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-148">Controls the execution of stored procedures from remote servers running instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e3410-149">이 확인란을 선택하는 것은 **sp_configure remote access** 옵션을 1로 설정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-149">Selecting this check box has the same effect as setting the **sp_configureremote access** option to 1.</span></span> <span data-ttu-id="e3410-150">확인란의 선택을 취소하면 원격 서버에서 저장 프로시저를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-150">Clearing it prevents execution of stored procedures from a remote server.</span></span>  
  
 <span data-ttu-id="e3410-151">**원격 쿼리 제한 시간(초, 0 = 제한 시간 없음)**</span><span class="sxs-lookup"><span data-stu-id="e3410-151">**Remote query timeout (in seconds, 0 = no timeout)**</span></span>  
 <span data-ttu-id="e3410-152">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 제한 시간이 초과될 때까지 원격 작업을 수행할 수 있는 시간을 초 단위로 지정합니다. 기본값은 600이며 10분 대기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-152">Specifies how long (in seconds) a remote operation may take before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] times out. The default is 600 seconds, or a 10-minute wait.</span></span>  
  
 <span data-ttu-id="e3410-153">**서버 간 통신에 분산 트랜잭션 필요**</span><span class="sxs-lookup"><span data-stu-id="e3410-153">**Require distributed transactions for server-to-server communication**</span></span>  
 <span data-ttu-id="e3410-154">MS DTC( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator) 트랜잭션을 통해 서버 간 프로시저 동작을 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-154">Protects the actions of a server-to-server procedure through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) transaction.</span></span> <span data-ttu-id="e3410-155">자세한 내용은 [원격 프로시저 트랜잭션 서버 구성 옵션 구성](configure-the-remote-proc-trans-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e3410-155">For more information, see [Configure the remote proc trans Server Configuration Option](configure-the-remote-proc-trans-server-configuration-option.md).</span></span>  
  
## <a name="property-page-display-options"></a><span data-ttu-id="e3410-156">속성 페이지 표시 옵션</span><span class="sxs-lookup"><span data-stu-id="e3410-156">Property Page Display Options</span></span>  
 <span data-ttu-id="e3410-157">**구성 값**</span><span class="sxs-lookup"><span data-stu-id="e3410-157">**Configured Values**</span></span>  
 <span data-ttu-id="e3410-158">이 창의 옵션에 대해 구성된 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-158">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="e3410-159">이러한 값을 변경한 후에는 **실행 값** 을 클릭하여 변경 사항이 적용되었는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-159">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="e3410-160">변경 사항이 적용되지 않은 경우 먼저 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-160">If they have not, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restarted first.</span></span>  
  
 <span data-ttu-id="e3410-161">**실행 값**</span><span class="sxs-lookup"><span data-stu-id="e3410-161">**Running Values**</span></span>  
 <span data-ttu-id="e3410-162">이 창의 옵션에 대한 현재 실행 값을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-162">View the currently running values for the options on this pane.</span></span> <span data-ttu-id="e3410-163">이 값은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="e3410-163">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3410-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3410-164">See Also</span></span>  
 <span data-ttu-id="e3410-165">[쿼리 실행 &#40;옵션: SQL Server: 고급 페이지&#41;](../options-query-execution-sql-server-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="e3410-165">[Options &#40;Query Execution:SQL Server:Advanced Page&#41;](../options-query-execution-sql-server-advanced-page.md) </span></span>  
 [<span data-ttu-id="e3410-166">서버 구성 옵션&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e3410-166">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
