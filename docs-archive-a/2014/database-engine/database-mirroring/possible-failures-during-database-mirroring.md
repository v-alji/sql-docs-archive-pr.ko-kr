---
title: 데이터베이스 미러링 중에 발생 가능한 오류 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- time-out period [SQL Server database mirroring]
- soft errors [SQL Server]
- database mirroring [SQL Server], troubleshooting
- timeout errors [SQL Server]
- troubleshooting [SQL Server], database mirroring
- hard errors
- failed database mirroring sessions [SQL Server]
ms.assetid: d7031f58-5f49-4e6d-9a62-9b420f2bb17e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 25ba1ccc87c024fa3da370f2ff19251a1bee9f30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733107"
---
# <a name="possible-failures-during-database-mirroring"></a><span data-ttu-id="11cb9-102">Possible Failures During Database Mirroring</span><span class="sxs-lookup"><span data-stu-id="11cb9-102">Possible Failures During Database Mirroring</span></span>
  <span data-ttu-id="11cb9-103">물리적, 운영 체제 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문제로 인해 데이터베이스 미러링 세션에서 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-103">Physical, operating system, or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] problems can cause a failure in a database mirroring session.</span></span> <span data-ttu-id="11cb9-104">데이터베이스 미러링은 Sqlservr.exe에서 사용하는 구성 요소를 정기적으로 검사하여 구성 요소가 올바르게 작동하는지, 아니면 실패했는지를 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-104">Database mirroring does not regularly check the components on which Sqlservr.exe relies to verify whether they are functioning correctly or have failed.</span></span> <span data-ttu-id="11cb9-105">하지만 일부 오류 유형의 경우 영향을 받는 구성 요소가 Sqlservr.exe에 오류를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-105">However, for some types of failures, the affected component reports an error to Sqlservr.exe.</span></span> <span data-ttu-id="11cb9-106">다른 구성 요소에서 보고된 오류를 *하드 오류*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-106">An error reported by another component is called a *hard error*.</span></span> <span data-ttu-id="11cb9-107">확인되지 않는 다른 오류를 감지하기 위해 데이터베이스 미러링은 자체적으로 제한 시간 메커니즘을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-107">To detect other failures that would otherwise go unnoticed, database mirroring implements its own time-out mechanism.</span></span> <span data-ttu-id="11cb9-108">미러링 제한 시간이 발생하면 데이터베이스 미러링은 오류가 발생했다고 가정하고 *소프트 오류*를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-108">When a mirroring time-out occurs, database mirroring assumes that a failure has occurred and declares a *soft error*.</span></span> <span data-ttu-id="11cb9-109">하지만 SQL Server 인스턴스 수준에서 발생하는 일부 오류는 미러링 제한 시간을 일으키지 않으며, 발견되지 않은 상태로 진행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-109">However, some failures that happen at the SQL Server instance level do not cause mirroring to time-out and can go undetected.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="11cb9-110">미러된 데이터베이스가 아닌 다른 데이터베이스의 오류는 데이터베이스 미러링 세션에서 감지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-110">Failures in databases other than the mirrored database are not detectable in a database mirroring session.</span></span> <span data-ttu-id="11cb9-111">또한 데이터베이스가 데이터 디스크 오류로 인해 다시 시작되지 않는 한 데이터 디스크 오류도 감지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-111">Moreover, a data disk failure is unlikely to be detected, unless the database is restarted because of a data disk failure.</span></span>  
  
 <span data-ttu-id="11cb9-112">오류 감지 속도 그리고 이에 따른 미러링 세션의 오류 반응 속도는 오류가 하드 오류인지 소프트 오류인지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-112">The speed of error detection and, therefore, the reaction time of the mirroring session to a failure, depends on whether the error is hard or soft.</span></span> <span data-ttu-id="11cb9-113">네트워크 오류와 같은 일부 하드 오류는 즉시 보고되지만</span><span class="sxs-lookup"><span data-stu-id="11cb9-113">Some hard errors, such as network failures are reported immediately.</span></span> <span data-ttu-id="11cb9-114">경우에 따라 구성 요소별 제한 시간으로 인해 일부 하드 오류 보고가 지연될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-114">However, in some cases, component-specific time-out periods can delay the reporting of some hard errors.</span></span> <span data-ttu-id="11cb9-115">소프트 오류의 경우 미러링 제한 시간의 길이가 오류 검색 속도를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-115">For soft errors, the length of the mirroring time-out period determines the speed of error detection.</span></span> <span data-ttu-id="11cb9-116">기본적으로 이 시간은 10초(</span><span class="sxs-lookup"><span data-stu-id="11cb9-116">By default, this period is 10 seconds.</span></span> <span data-ttu-id="11cb9-117">최소 권장 값)입니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-117">This is the minimum recommended value.</span></span>  
  
## <a name="failures-due-to-hard-errors"></a><span data-ttu-id="11cb9-118">하드 오류로 인한 실패</span><span class="sxs-lookup"><span data-stu-id="11cb9-118">Failures Due to Hard Errors</span></span>  
 <span data-ttu-id="11cb9-119">하드 오류를 일으킬 수 있는 원인 중에는 다음 조건이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-119">Possible causes of hard errors include (but are not limited to) the following conditions:</span></span>  
  
-   <span data-ttu-id="11cb9-120">연결 또는 전선의 끊어짐</span><span class="sxs-lookup"><span data-stu-id="11cb9-120">A broken connection or wire</span></span>  
  
-   <span data-ttu-id="11cb9-121">잘못된 네트워크 카드</span><span class="sxs-lookup"><span data-stu-id="11cb9-121">A bad network card</span></span>  
  
-   <span data-ttu-id="11cb9-122">라우터 변경</span><span class="sxs-lookup"><span data-stu-id="11cb9-122">A router change</span></span>  
  
-   <span data-ttu-id="11cb9-123">방화벽 내의 변경 사항</span><span class="sxs-lookup"><span data-stu-id="11cb9-123">Changes in the firewall</span></span>  
  
-   <span data-ttu-id="11cb9-124">엔드포인트 다시 구성</span><span class="sxs-lookup"><span data-stu-id="11cb9-124">Endpoint reconfiguration</span></span>  
  
-   <span data-ttu-id="11cb9-125">트랜잭션 로그가 있는 드라이브 손실</span><span class="sxs-lookup"><span data-stu-id="11cb9-125">Loss of the drive where the transaction log resides</span></span>  
  
-   <span data-ttu-id="11cb9-126">운영 체제 또는 프로세스 오류</span><span class="sxs-lookup"><span data-stu-id="11cb9-126">Operating system or process failure</span></span>  
  
 <span data-ttu-id="11cb9-127">예를 들어 주 데이터베이스의 로그 드라이브가 응답하지 않거나 실패하면 운영 체제에서 Sqlservr.exe에 심각한 오류 발생 사실을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-127">For example, when the log drive on the principal database becomes unresponsive and fails, the operating system informs Sqlservr.exe that a serious error has occurred.</span></span>  
  
 <span data-ttu-id="11cb9-128">네트워크 구성 요소 및 일부 IO 하위 시스템과 같은 구성 요소에는 자체적으로 오류를 확인하기 위한 제한 시간이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-128">Some components, such as network components and some IO subsystems, have their own time-outs to determine failures.</span></span> <span data-ttu-id="11cb9-129">이러한 제한 시간은 데이터베이스 미러링에 독립적이므로 데이터베이스 미러링에 대해 알지 못하며 데이터베이스 미러링 동작을 전혀 파악할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-129">Such time-outs are independent of database mirroring, which has no knowledge of them and is completely unaware of their behavior.</span></span> <span data-ttu-id="11cb9-130">이러한 경우 제한 시간이 지연되어 오류가 발생한 다음 데이터베이스 미러링이 결과 하드 오류를 수신할 때까지의  시간이 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-130">In these cases, the time-out delay increases the time between a failure and when database mirroring receive the resulting hard error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11cb9-131">데이터베이스 미러링에 대한 활성 오류 검사는 소프트웨어 오류의 경우에만 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-131">The only active error checking performed for database mirroring occurs for soft error cases.</span></span> <span data-ttu-id="11cb9-132">자세한 내용은 이 항목의 뒷부분에 나오는 "소프트 오류로 인한 오류"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11cb9-132">For more information, see "Failures Due to Soft Errors," later in this topic.</span></span>  
  
 <span data-ttu-id="11cb9-133">네트워크에서 발생하는 오류 상황을 해석하는 데 도움이 되도록 네트워크 엔지니어에게 TCP 연결에서 다음 이벤트가 발생할 경우 어떤 오류 메시지가 포트로 전송되는지 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="11cb9-133">To help you interpret the error conditions that occur on the network, ask a network engineer what error messages are sent to a port when the following events occur on a TCP connection:</span></span>  
  
-   <span data-ttu-id="11cb9-134">DNS가 작동하지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="11cb9-134">DNS is not working.</span></span>  
  
-   <span data-ttu-id="11cb9-135">케이블이 연결되어 있지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="11cb9-135">Cables are unplugged.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="11cb9-136">Windows에 특정 포트를 차단하는 방화벽이 있는 경우</span><span class="sxs-lookup"><span data-stu-id="11cb9-136">Windows has a firewall that blocks a specific port.</span></span>  
  
-   <span data-ttu-id="11cb9-137">포트를 모니터링하는 애플리케이션에서 오류가 발생한 경우</span><span class="sxs-lookup"><span data-stu-id="11cb9-137">The application that is monitoring a port fails.</span></span>  
  
-   <span data-ttu-id="11cb9-138">Windows 기반 서버 이름이 바뀐 경우</span><span class="sxs-lookup"><span data-stu-id="11cb9-138">A Windows-based server is renamed.</span></span>  
  
-   <span data-ttu-id="11cb9-139">Windows 기반 서버가 다시 부팅된 경우</span><span class="sxs-lookup"><span data-stu-id="11cb9-139">A Windows-based server is rebooted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11cb9-140">미러링은 서버에 액세스하는 클라이언트 관련 문제에 대해 보호하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-140">Mirroring does not protect against problems specific to client accessing the servers.</span></span> <span data-ttu-id="11cb9-141">예를 들어 프라이빗 네트워크 인터페이스 카드가 서버 인스턴스 간의 모든 미러링 트래픽을 처리하는 동안 퍼블릭 네트워크 어댑터가 주 서버 인스턴스에 대한 클라이언트 연결을 처리하는 경우</span><span class="sxs-lookup"><span data-stu-id="11cb9-141">For example, consider a case in which a public network adapter handles client connections to the principal server instance, while a private network interface card handles all mirroring traffic among server instances.</span></span> <span data-ttu-id="11cb9-142">데이터베이스를 계속 미러링하려고 하지만 공용 네트워크 어댑터의 오류로 인해 클라이언트가 데이터베이스에 액세스하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-142">In this case, failure of the public network adapter would prevent clients from accessing the database, though the database would continue to be mirrored.</span></span>  
  
## <a name="failures-due-to-soft-errors"></a><span data-ttu-id="11cb9-143">소프트 오류로 인한 오류</span><span class="sxs-lookup"><span data-stu-id="11cb9-143">Failures Due to Soft Errors</span></span>  
 <span data-ttu-id="11cb9-144">미러링 제한 시간 초과가 발생할 수 있는 상황은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-144">Conditions that might cause mirroring time-outs include (but are not limited to) the following:</span></span>  
  
-   <span data-ttu-id="11cb9-145">TCP 연결 제한 시간 초과, 삭제되거나 손상된 패킷, 잘못된 순서의 패킷 등의 네트워크 오류</span><span class="sxs-lookup"><span data-stu-id="11cb9-145">Network errors such as TCP link time-outs, dropped or corrupted packets, or packets that are in an incorrect order.</span></span>  
  
-   <span data-ttu-id="11cb9-146">응답하지 않는 운영 체제, 서버 또는 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="11cb9-146">An operating system, server, or database that is not responding.</span></span>  
  
-   <span data-ttu-id="11cb9-147">Windows 서버 제한 시간 초과</span><span class="sxs-lookup"><span data-stu-id="11cb9-147">A Windows server timing out.</span></span>  
  
-   <span data-ttu-id="11cb9-148">CPU 또는 디스크 오버로드, 꽉 찬 트랜잭션 로그 또는 시스템의 메모리나 스레드 부족과 같은 컴퓨팅 리소스 부족.</span><span class="sxs-lookup"><span data-stu-id="11cb9-148">Insufficient computing resources, such as a CPU or disk overload, the transaction log filling up, or the system is running out of memory or threads.</span></span> <span data-ttu-id="11cb9-149">이런 경우에는 제한 시간을 늘이거나, 작업을 줄이거나, 작업을 처리할 수 있도록 하드웨어를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-149">In these cases, you must increase the time-out period, reduce the workload, or change the hardware to handle the workload.</span></span>  
  
### <a name="the-mirroring-time-out-mechanism"></a><span data-ttu-id="11cb9-150">미러링 제한 시간 메커니즘</span><span class="sxs-lookup"><span data-stu-id="11cb9-150">The Mirroring Time-Out Mechanism</span></span>  
 <span data-ttu-id="11cb9-151">소프트 오류는 서버 인스턴스에서 직접 감지되지 않으므로 소프트 오류 발생 시 서버 인스턴스가 무기한 대기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-151">Because soft errors are not detectable directly by a server instance, a soft error could potentially cause a server instance to wait indefinitely.</span></span> <span data-ttu-id="11cb9-152">이를 방지하기 위해 데이터베이스 미러링은 미러링 세션의 각 서버 인스턴스를 기반으로 열려 있는 각 연결에서 일정한 간격으로 ping을 보내는 제한 시간 메커니즘을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-152">To prevent this, database mirroring implements its own time-out mechanism, based on each server instance in a mirroring session sending out a ping on each open connection at a fixed interval.</span></span>  
  
 <span data-ttu-id="11cb9-153">연결이 열려 있으려면 서버 인스턴스가 ping을 하나 더 보내는 데 필요한 시간을 더하여 정의되는 제한 시간에서 해당 연결에 대한 ping을 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-153">To keep a connection open, a server instance must receive a ping on that connection in the time-out period defined, plus the time that is required to send one more ping.</span></span> <span data-ttu-id="11cb9-154">제한 시간 내에 ping을 받은 경우 연결이 열려 있으며 서버 인스턴스가 해당 연결을 통해 통신하고 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-154">Receiving a ping during the time-out period indicates that the connection is still open and that the server instances are communicating over it.</span></span> <span data-ttu-id="11cb9-155">ping을 받으면 서버 인스턴스는 해당 연결의 제한 시간 카운터를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-155">On receiving a ping, a server instance resets its time-out counter on that connection.</span></span>  
  
 <span data-ttu-id="11cb9-156">제한 시간 내에 ping을 받지 못한 경우 서버 인스턴스는 해당 연결이 제한 시간을 초과했다고 간주하고 연결을 닫은 후 세션의 상태와 운영 모드에 따라 제한 시간 이벤트를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-156">If no ping is received on a connection during the time-out period, a server instance considers the connection to have timed out. The server instance closes the timed-out connection and handles the time-out event according to the state and operating mode of the session.</span></span>  
  
 <span data-ttu-id="11cb9-157">실제로 다른 서버가 올바로 실행되고 있는 경우에도 제한 시간 초과는 오류로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-157">Even if the other server is actually proceeding correctly, a time-out is considered a failure.</span></span> <span data-ttu-id="11cb9-158">각 파트너의 일반 응답에 비해 세션의 제한 시간 값이 지나치게 짧은 경우 거짓 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-158">If the time-out value for a session is too short for the regular responsiveness of either partner, false failures can occur.</span></span> <span data-ttu-id="11cb9-159">거짓 오류는 한 서버 인스턴스가 다른 서버 인스턴스에 성공적으로 연결하지만 해당 서버 인스턴스의 응답 시간이 너무 느려 제한 시간이 만료되기 전에 ping을 받을 수 없는 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-159">A false failure occurs when one server instance successfully contacts another whose response time is so slow that its pings are not received before the time-out period expires.</span></span>  
  
 <span data-ttu-id="11cb9-160">성능 우선 모드 세션에서 제한 시간은 항상 10초이며</span><span class="sxs-lookup"><span data-stu-id="11cb9-160">In high-performance mode sessions, the time-out period is always 10 seconds.</span></span> <span data-ttu-id="11cb9-161">이는 일반적으로 거짓 오류를 방지하기에 충분한 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-161">This is generally enough to avoid false failures.</span></span> <span data-ttu-id="11cb9-162">보안 우선 모드 세션에서 기본 제한 시간은 10초이지만 이 시간을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-162">In high-safety mode sessions, the default time-out period is 10 seconds, but you can change the duration.</span></span> <span data-ttu-id="11cb9-163">거짓 오류를 방지하려면 미러링 제한 시간을 항상 10초 이상으로 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-163">To avoid false failures, we recommend that the mirroring time-out period always be 10 seconds or more.</span></span>  
  
 <span data-ttu-id="11cb9-164">**제한 시간 값을 변경하려면(보안 우선 모드 전용)**</span><span class="sxs-lookup"><span data-stu-id="11cb9-164">**To change the time-out value (high-safety mode only)**</span></span>  
  
-   <span data-ttu-id="11cb9-165">[ALTER DATABASE \<database> SET PARTNER TIMEOUT \<integer>](/sql/t-sql/statements/alter-database-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-165">Use the [ALTER DATABASE \<database> SET PARTNER TIMEOUT \<integer>](/sql/t-sql/statements/alter-database-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="11cb9-166">**현재 제한 시간 값을 보려면**</span><span class="sxs-lookup"><span data-stu-id="11cb9-166">**To view the current time-out value**</span></span>  
  
-   <span data-ttu-id="11cb9-167">**sys.database_mirroring** 에서 [mirroring_connection_timeout](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql)을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-167">Query **mirroring_connection_timeout** in [sys.database_mirroring](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).</span></span>  
  
## <a name="responding-to-an-error"></a><span data-ttu-id="11cb9-168">오류에 대한 응답</span><span class="sxs-lookup"><span data-stu-id="11cb9-168">Responding to an Error</span></span>  
 <span data-ttu-id="11cb9-169">오류 유형에 관계없이 오류를 감지하는 서버 인스턴스는 인스턴스의 역할, 세션의 운영 모드 및 세션 내 다른 연결의 상태를 기반으로 적절하게 오류에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="11cb9-169">Regardless of the type of error, a server instance that detects an error responds appropriately based on the role of the instance, the operating mode of the session, and the state of any other connection in the session.</span></span> <span data-ttu-id="11cb9-170">파트너 손실로 인해 발생하는 상황에 대한 자세한 내용은 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11cb9-170">For information about what occurs on the loss of a partner, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11cb9-171">참고 항목</span><span class="sxs-lookup"><span data-stu-id="11cb9-171">See Also</span></span>  
 <span data-ttu-id="11cb9-172">[역할 전환 중 서비스 중단 예측&#40;데이터베이스 미러링&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="11cb9-172">[Estimate the Interruption of Service During Role Switching &#40;Database Mirroring&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md) </span></span>  
 <span data-ttu-id="11cb9-173">[데이터베이스 미러링 운영 모드](database-mirroring-operating-modes.md) </span><span class="sxs-lookup"><span data-stu-id="11cb9-173">[Database Mirroring Operating Modes](database-mirroring-operating-modes.md) </span></span>  
 <span data-ttu-id="11cb9-174">[데이터베이스 미러링 세션 중 역할 전환&#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="11cb9-174">[Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span></span>  
 [<span data-ttu-id="11cb9-175">데이터베이스 미러링&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="11cb9-175">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
