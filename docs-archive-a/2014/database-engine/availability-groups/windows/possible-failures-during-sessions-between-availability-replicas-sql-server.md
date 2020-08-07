---
title: 가용성 복제본 간의 세션 동안 발생 가능한 오류(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting [SQL Server, HADR]
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], troubleshooting
ms.assetid: cd613898-82d9-482f-a255-0230a6c7d6fe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4cfacb7f7c75875d4f5d0b0b435d282b3f537cc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734463"
---
# <a name="possible-failures-during-sessions-between-availability-replicas-sql-server"></a><span data-ttu-id="2f550-102">가용성 복제본 간의 세션 동안 발생 가능한 오류(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2f550-102">Possible Failures During Sessions Between Availability Replicas (SQL Server)</span></span>
  <span data-ttu-id="2f550-103">물리적 문제, 운영 체제 문제 또는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 문제로 인해 두 가용성 복제본 사이의 세션에서 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-103">Physical, operating system, or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] problems can cause a failure in a session between two availability replicas.</span></span> <span data-ttu-id="2f550-104">가용성 복제본은 Sqlservr.exe에서 사용하는 구성 요소를 정기적으로 검사하여 구성 요소가 올바르게 작동하는지 아니면 실패했는지 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-104">An availability replica does not regularly check the components on which Sqlservr.exe relies to verify whether they are functioning correctly or have failed.</span></span> <span data-ttu-id="2f550-105">하지만 일부 오류 유형의 경우 영향을 받는 구성 요소가 Sqlservr.exe에 오류를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-105">However, for some types of failures, the affected component reports an error to Sqlservr.exe.</span></span> <span data-ttu-id="2f550-106">다른 구성 요소에서 보고된 오류를 *하드 오류*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-106">An error reported by another component is called a *hard error*.</span></span> <span data-ttu-id="2f550-107">확인되지 않는 다른 오류를 감지하기 위해 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 은 자체적으로 세션 제한 시간 메커니즘을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-107">To detect other failures that would otherwise go unnoticed, [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] implements its own session-timeout mechanism.</span></span> <span data-ttu-id="2f550-108">세션 제한 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-108">Specifies the session-timeout period in seconds.</span></span> <span data-ttu-id="2f550-109">이 제한 시간은 서버 인스턴스가 다른 인스턴스로부터 PING 메시지를 받기까지 기다리는 최대 시간으로, 이 시간이 경과하면 해당 인스턴스의 연결이 끊어진 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-109">This time-out period is the maximum time that a server instance waits to receive a PING message from another instance before considering that other instance to be disconnected.</span></span> <span data-ttu-id="2f550-110">두 가용성 복제본 사이에서 세션 제한 시간이 발생하면 가용성 복제본은 오류가 발생했다고 가정하고 *소프트 오류*를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-110">When a session timeout occurs between two availability replicas, the availability replicas assume that a failure has occurred and declares a *soft error*.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2f550-111">주 데이터베이스가 아닌 다른 데이터베이스의 오류는 감지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-111">Failures in databases other than the primary database are not detectable.</span></span> <span data-ttu-id="2f550-112">또한 데이터베이스가 데이터 디스크 오류로 인해 다시 시작되지 않는 한 데이터 디스크 오류도 감지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-112">Moreover, a data disk failure is unlikely to be detected unless the database is restarted because of a data disk failure.</span></span>  
  
 <span data-ttu-id="2f550-113">오류 감지 속도 그리고 이에 따른 오류 반응 속도는 오류가 하드 오류인지 소프트 오류인지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-113">The speed of error detection and, therefore, the reaction time to a failure, depends on whether the error is hard or soft.</span></span> <span data-ttu-id="2f550-114">네트워크 오류와 같은 일부 하드 오류는 즉시 보고되지만</span><span class="sxs-lookup"><span data-stu-id="2f550-114">Some hard errors, such as network failures are reported immediately.</span></span> <span data-ttu-id="2f550-115">경우에 따라 구성 요소별 제한 시간으로 인해 일부 하드 오류 보고가 지연될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-115">However, in some cases, component-specific time-out periods can delay the reporting of some hard errors.</span></span> <span data-ttu-id="2f550-116">소프트 오류의 경우 세션 제한 시간의 길이가 오류 검색 속도를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-116">For soft errors, the length of the session-timeout period determines the speed of error detection.</span></span> <span data-ttu-id="2f550-117">기본적으로 이 시간은 10초(</span><span class="sxs-lookup"><span data-stu-id="2f550-117">By default, this period is 10 seconds.</span></span> <span data-ttu-id="2f550-118">최소 권장 값)입니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-118">This is the minimum recommended value.</span></span>  
  
## <a name="failures-due-to-hard-errors"></a><span data-ttu-id="2f550-119">하드 오류로 인한 실패</span><span class="sxs-lookup"><span data-stu-id="2f550-119">Failures Due to Hard Errors</span></span>  
 <span data-ttu-id="2f550-120">하드 오류를 일으킬 수 있는 원인 중에는 다음 조건이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-120">Possible causes of hard errors include (but are not limited to) the following conditions:</span></span>  
  
-   <span data-ttu-id="2f550-121">연결 또는 전선의 끊어짐</span><span class="sxs-lookup"><span data-stu-id="2f550-121">A broken connection or wire</span></span>  
  
-   <span data-ttu-id="2f550-122">잘못된 네트워크 카드</span><span class="sxs-lookup"><span data-stu-id="2f550-122">A bad network card</span></span>  
  
-   <span data-ttu-id="2f550-123">라우터 변경</span><span class="sxs-lookup"><span data-stu-id="2f550-123">A router change</span></span>  
  
-   <span data-ttu-id="2f550-124">방화벽 내의 변경 사항</span><span class="sxs-lookup"><span data-stu-id="2f550-124">Changes in the firewall</span></span>  
  
-   <span data-ttu-id="2f550-125">엔드포인트 다시 구성</span><span class="sxs-lookup"><span data-stu-id="2f550-125">Endpoint reconfiguration</span></span>  
  
-   <span data-ttu-id="2f550-126">트랜잭션 로그가 있는 드라이브 손실</span><span class="sxs-lookup"><span data-stu-id="2f550-126">Loss of the drive where the transaction log resides</span></span>  
  
-   <span data-ttu-id="2f550-127">운영 체제 또는 프로세스 오류</span><span class="sxs-lookup"><span data-stu-id="2f550-127">Operating system or process failure</span></span>  
  
 <span data-ttu-id="2f550-128">예를 들어 주 데이터베이스의 로그 드라이브가 응답하지 않거나 실패하면 운영 체제에서 Sqlservr.exe에 심각한 오류 발생 사실을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-128">For example, when the log drive on the primary database becomes unresponsive and fails, the operating system informs Sqlservr.exe that a serious error has occurred.</span></span>  
  
 <span data-ttu-id="2f550-129">네트워크 구성 요소 및 일부 IO 하위 시스템과 같은 구성 요소에는 자체적으로 오류를 확인하기 위한 제한 시간이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-129">Some components, such as network components and some IO subsystems, have their own time-outs to determine failures.</span></span> <span data-ttu-id="2f550-130">이러한 제한 시간은 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]에 독립적이므로 데이터베이스 미러링에 대해 알지 못하며 데이터베이스 미러링 동작을 전혀 파악할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-130">Such time-outs are independent of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], which has no knowledge of them and is completely unaware of their behavior.</span></span> <span data-ttu-id="2f550-131">이러한 경우 제한 시간이 지연되어 오류가 발생한 다음 가용성 복제본이 결과 하드 오류를 수신할 때까지의 시간이 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-131">In these cases, the time-out delay increases the time between a failure and when the availability replica receives the resulting hard error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2f550-132">가용성 복제본에 대한 활성 오류 검사는 소프트웨어 오류의 경우에만 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-132">The only active error checking performed for availability replicas occurs for soft error cases.</span></span> <span data-ttu-id="2f550-133">자세한 내용은 이 항목의 뒷부분에 나오는 "소프트 오류로 인한 오류"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2f550-133">For more information, see "Failures Due to Soft Errors," later in this topic.</span></span>  
  
 <span data-ttu-id="2f550-134">네트워크에서 발생하는 오류 상황을 해석하는 데 도움이 되도록 네트워크 엔지니어에게 TCP 연결에서 다음 이벤트가 발생할 경우 어떤 오류 메시지가 포트로 전송되는지 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="2f550-134">To help you interpret the error conditions that occur on the network, ask a network engineer what error messages are sent to a port when the following events occur on a TCP connection:</span></span>  
  
-   <span data-ttu-id="2f550-135">DNS가 작동하지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="2f550-135">DNS is not working.</span></span>  
  
-   <span data-ttu-id="2f550-136">케이블이 연결되어 있지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="2f550-136">Cables are unplugged.</span></span>  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="2f550-137">Windows에 특정 포트를 차단하는 방화벽이 있는 경우</span><span class="sxs-lookup"><span data-stu-id="2f550-137">Windows has a firewall that blocks a specific port.</span></span>  
  
-   <span data-ttu-id="2f550-138">포트를 모니터링하는 애플리케이션에서 오류가 발생한 경우</span><span class="sxs-lookup"><span data-stu-id="2f550-138">The application that is monitoring a port fails.</span></span>  
  
-   <span data-ttu-id="2f550-139">Windows 기반 서버 이름이 바뀐 경우</span><span class="sxs-lookup"><span data-stu-id="2f550-139">A Windows-based server is renamed.</span></span>  
  
-   <span data-ttu-id="2f550-140">Windows 기반 서버가 다시 부팅된 경우</span><span class="sxs-lookup"><span data-stu-id="2f550-140">A Windows-based server is rebooted.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssHADRc](../../../includes/sshadrc-md.md)]<span data-ttu-id="2f550-141">은 서버에 액세스하는 클라이언트 관련 문제에 대해 보호하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-141">does not protect against problems specific to client accessing the servers.</span></span> <span data-ttu-id="2f550-142">예를 들어 프라이빗 네트워크 인터페이스 카드가 가용성 그룹 복제본을 호스팅 중인 서버 인스턴스 간의 트래픽을 처리하는 동안 퍼블릭 네트워크 어댑터가 주 복제본에 대한 클라이언트 연결을 처리하는 경우</span><span class="sxs-lookup"><span data-stu-id="2f550-142">For example, consider a case in which a public network adapter handles client connections to the primary replica, while a private network interface card handles traffic among the server instances that are hosting the replicas of an availability group.</span></span> <span data-ttu-id="2f550-143">이 경우 공용 네트워크 어댑터의 오류로 인해 클라이언트가 데이터베이스에 액세스하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-143">In this case, failure of the public network adapter would prevent clients from accessing the databases.</span></span>  
  
## <a name="failures-due-to-soft-errors"></a><span data-ttu-id="2f550-144">소프트 오류로 인한 오류</span><span class="sxs-lookup"><span data-stu-id="2f550-144">Failures Due to Soft Errors</span></span>  
 <span data-ttu-id="2f550-145">세션 제한 시간 초과가 발생할 수 있는 상황은 다음(여기에 한정되지 않음)과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-145">Conditions that might cause session timeouts include (but are not limited to) the following:</span></span>  
  
-   <span data-ttu-id="2f550-146">TCP 연결 제한 시간 초과, 삭제되거나 손상된 패킷, 잘못된 순서의 패킷 등의 네트워크 오류</span><span class="sxs-lookup"><span data-stu-id="2f550-146">Network errors such as TCP link time-outs, dropped or corrupted packets, or packets that are in an incorrect order.</span></span>  
  
-   <span data-ttu-id="2f550-147">응답하지 않는 운영 체제, 서버 또는 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="2f550-147">An operating system, server, or database that is not responding.</span></span>  
  
-   <span data-ttu-id="2f550-148">Windows 서버 제한 시간 초과</span><span class="sxs-lookup"><span data-stu-id="2f550-148">A Windows server timing out.</span></span>  
  
-   <span data-ttu-id="2f550-149">CPU 또는 디스크 오버로드, 꽉 찬 트랜잭션 로그 또는 시스템의 메모리나 스레드 부족과 같은 컴퓨팅 리소스 부족.</span><span class="sxs-lookup"><span data-stu-id="2f550-149">Insufficient computing resources, such as a CPU or disk overload, the transaction log filling up, or the system is running out of memory or threads.</span></span> <span data-ttu-id="2f550-150">이런 경우에는 제한 시간을 늘이거나, 작업을 줄이거나, 작업을 처리할 수 있도록 하드웨어를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-150">In these cases, you must increase the time-out period, reduce the workload, or change the hardware to handle the workload.</span></span>  
  
### <a name="the-session-timeout-mechanism"></a><span data-ttu-id="2f550-151">세션 제한 시간 메커니즘</span><span class="sxs-lookup"><span data-stu-id="2f550-151">The Session-Timeout Mechanism</span></span>  
 <span data-ttu-id="2f550-152">소프트 오류는 서버 인스턴스에서 직접 감지되지 않으므로 소프트 오류 발생 시 가용성 복제본이 세션 내 다른 가용성 복제본의 응답을 무기한 대기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-152">Because soft errors are not detectable directly by a server instance, a soft error could potentially cause an availability replica to wait indefinitely for a response from the other availability replica in a session.</span></span> <span data-ttu-id="2f550-153">이를 방지하기 위해 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 은 연결된 가용성 복제본을 기반으로 열려 있는 각 연결에서 일정한 간격으로 ping을 보내는 제한 시간 메커니즘을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-153">To prevent this, [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] implements a session time-out mechanism, based on the connected availability replicas sending out a ping on each open connection at a fixed interval.</span></span> <span data-ttu-id="2f550-154">제한 시간 내에 ping을 받은 경우 연결이 열려 있으며 서버 인스턴스가 해당 연결을 통해 통신하고 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-154">Receiving a ping during the time-out period indicates that the connection is still open and that the server instances are communicating over it.</span></span> <span data-ttu-id="2f550-155">ping을 받으면 복제본은 해당 연결의 제한 시간 카운터를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-155">On receiving a ping, a replica resets its time-out counter on that connection.</span></span> <span data-ttu-id="2f550-156">가용성 모드와 세션 시간 초과의 관계에 대 한 자세한 내용은 [가용성 모드 (AlwaysOn 가용성 그룹)](availability-modes-always-on-availability-groups.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2f550-156">For information about the relationship of availability mode and session timeouts, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="2f550-157">주 복제본과 보조 복제본은 서로에 대해 ping을 수행하여 자신이 아직 활성 상태임을 나타내며 세션 제한 시간은 이들 복제본이 상대 복제본의 ping을 무기한 수신 대기하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-157">The primary and secondary replicas ping each other to signal that they are still active, and a session-timeout limit prevents either replica from waiting indefinitely to receive a ping from the other replica.</span></span> <span data-ttu-id="2f550-158">세션 제한 시간은 사용자가 구성 가능한 복제본 속성이며 기본값은 0초입니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-158">The session-timeout limit is a user-configurable replica property with a default value of 10 seconds.</span></span> <span data-ttu-id="2f550-159">제한 시간 내에 ping을 받은 경우 연결이 열려 있으며 서버 인스턴스가 해당 연결을 통해 통신하고 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-159">Receiving a ping during the time-out period indicates that the connection is still open and that the server instances are communicating over it.</span></span> <span data-ttu-id="2f550-160">ping을 받으면 가용성 복제본은 해당 연결의 제한 시간 카운터를 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-160">On receiving a ping, an availability replica resets its time-out counter on that connection.</span></span>  
  
 <span data-ttu-id="2f550-161">세션 제한 시간 내에 다른 복제본 으로부터 ping을 받지 못하면 연결 시간이 초과 됩니다. 연결이 닫히고 시간 초과 된 복제본이 연결이 끊어진 상태로 전환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-161">If no ping is received from the other replica within the session-timeout period, the connection times out. The connection is closed, and the timed-out replica enters the DISCONNECTED state.</span></span> <span data-ttu-id="2f550-162">연결이 끊어진 복제본이 동기 커밋 모드로 구성되어 있더라도 트랜잭션에서는 해당 복제본이 다시 연결되어 다시 동기화될 때까지 대기하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-162">Even if a disconnected replica is configured for synchronous-commit mode, transactions will not wait for that replica to reconnect and resynchronize.</span></span>  
  
## <a name="responding-to-an-error"></a><span data-ttu-id="2f550-163">오류에 대한 응답</span><span class="sxs-lookup"><span data-stu-id="2f550-163">Responding to an Error</span></span>  
 <span data-ttu-id="2f550-164">오류 유형에 관계없이 오류를 감지하는 서버 인스턴스는 인스턴스의 역할, 세션의 가용성 모드 및 세션 내 다른 연결의 상태를 기반으로 적절하게 오류에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-164">Regardless of the type of error, a server instance that detects an error responds appropriately based on the role of the instance, the availability mode of the session, and the state of any other connection in the session.</span></span> <span data-ttu-id="2f550-165">파트너가 손실 될 때 발생 하는 상황에 대 한 자세한 내용은 [가용성 모드 (AlwaysOn 가용성 그룹)](availability-modes-always-on-availability-groups.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2f550-165">For information about what occurs on the loss of a partner, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="2f550-166">관련 작업</span><span class="sxs-lookup"><span data-stu-id="2f550-166">Related Tasks</span></span>  
 <span data-ttu-id="2f550-167">**제한 시간 값을 변경하려면(동기 커밋 가용성 모드 전용)**</span><span class="sxs-lookup"><span data-stu-id="2f550-167">**To change the time-out value (synchronous-commit availability mode only)**</span></span>  
  
-   [<span data-ttu-id="2f550-168">가용성 복제본에 대한 세션 제한 시간 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2f550-168">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="2f550-169">**현재 제한 시간 값을 보려면**</span><span class="sxs-lookup"><span data-stu-id="2f550-169">**To view the current time-out value**</span></span>  
  
-   <span data-ttu-id="2f550-170">[sys.availability_replicas&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)에서 **session_timeout**을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="2f550-170">Query **session_timeout** in [sys.availability_replicas &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f550-171">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2f550-171">See Also</span></span>  
 [<span data-ttu-id="2f550-172">AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;</span><span class="sxs-lookup"><span data-stu-id="2f550-172">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
