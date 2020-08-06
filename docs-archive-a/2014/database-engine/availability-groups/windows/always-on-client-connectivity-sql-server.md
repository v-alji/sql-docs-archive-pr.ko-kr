---
title: Always On 클라이언트 연결(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], prerequisites and restrictions
- Availability Groups [SQL Server], client connectivity
ms.assetid: b456448d-1757-48c8-8bbb-2d1c2d6d61e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 360e448e87b16b6fb97384bb9a85525a864eeef5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650285"
---
# <a name="always-on-client-connectivity-sql-server"></a><span data-ttu-id="9b510-102">Always On 클라이언트 연결(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9b510-102">Always On Client Connectivity (SQL Server)</span></span>
  <span data-ttu-id="9b510-103">이 항목에서는 클라이언트 구성 및 설정에 대한 사전 요구 사항, 제한 사항 및 권장 사항을 비롯하여 AlwaysOn 가용성 그룹에 클라이언트를 연결할 때 고려해야 할 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9b510-103">This topic describes considerations for client connectivity to AlwaysOn Availability Groups, including prerequisites, restrictions, and recommendations for client configurations and settings.</span></span>  
  
 
  
##  <a name="client-connectivity-support"></a><a name="ClientConnSupport"></a> <span data-ttu-id="9b510-104">클라이언트 연결 지원</span><span class="sxs-lookup"><span data-stu-id="9b510-104">Client Connectivity Support</span></span>  
 <span data-ttu-id="9b510-105">아래의 섹션에서는 클라이언트 연결에 대한 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 지원에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9b510-105">The section below provides information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] support for client connectivity.</span></span>  
  
 <span data-ttu-id="9b510-106">**드라이버 지원**</span><span class="sxs-lookup"><span data-stu-id="9b510-106">**Driver Support**</span></span>  
  
 <span data-ttu-id="9b510-107">다음 표에는 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]에 대한 드라이버 지원이 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b510-107">The following table summarizes driver support for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]:</span></span>  
  
|<span data-ttu-id="9b510-108">드라이버</span><span class="sxs-lookup"><span data-stu-id="9b510-108">Driver</span></span>|<span data-ttu-id="9b510-109">다중 서브넷 장애 조치(Failover)</span><span class="sxs-lookup"><span data-stu-id="9b510-109">Multi-Subnet Failover</span></span>|<span data-ttu-id="9b510-110">애플리케이션 의도</span><span class="sxs-lookup"><span data-stu-id="9b510-110">Application Intent</span></span>|<span data-ttu-id="9b510-111">읽기 전용 라우팅</span><span class="sxs-lookup"><span data-stu-id="9b510-111">Read-Only Routing</span></span>|<span data-ttu-id="9b510-112">다중 서브넷 장애 조치(Failover): 보다 빠른 단일 서브넷 엔드포인트 장애 조치(Failover)</span><span class="sxs-lookup"><span data-stu-id="9b510-112">Multi-Subnet Failover: Faster Single Subnet Endpoint Failover</span></span>|<span data-ttu-id="9b510-113">다중 서브넷 장애 조치(Failover): SQL 클러스터형 인스턴스에 대한 명명된 인스턴스 확인</span><span class="sxs-lookup"><span data-stu-id="9b510-113">Multi-Subnet Failover: Named Instance Resolution For SQL Clustered Instances</span></span>|  
|------------|----------------------------|------------------------|------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|<span data-ttu-id="9b510-114">SQL Native Client 11.0 ODBC</span><span class="sxs-lookup"><span data-stu-id="9b510-114">SQL Native Client 11.0 ODBC</span></span>|<span data-ttu-id="9b510-115">예</span><span class="sxs-lookup"><span data-stu-id="9b510-115">Yes</span></span>|<span data-ttu-id="9b510-116">yes</span><span class="sxs-lookup"><span data-stu-id="9b510-116">Yes</span></span>|<span data-ttu-id="9b510-117">yes</span><span class="sxs-lookup"><span data-stu-id="9b510-117">Yes</span></span>|<span data-ttu-id="9b510-118">yes</span><span class="sxs-lookup"><span data-stu-id="9b510-118">Yes</span></span>|<span data-ttu-id="9b510-119">yes</span><span class="sxs-lookup"><span data-stu-id="9b510-119">Yes</span></span>|  
|<span data-ttu-id="9b510-120">SQL Native Client 11.0 OLEDB</span><span class="sxs-lookup"><span data-stu-id="9b510-120">SQL Native Client 11.0 OLEDB</span></span>|<span data-ttu-id="9b510-121">예</span><span class="sxs-lookup"><span data-stu-id="9b510-121">No</span></span>|<span data-ttu-id="9b510-122">예</span><span class="sxs-lookup"><span data-stu-id="9b510-122">Yes</span></span>|<span data-ttu-id="9b510-123">yes</span><span class="sxs-lookup"><span data-stu-id="9b510-123">Yes</span></span>|<span data-ttu-id="9b510-124">아니요</span><span class="sxs-lookup"><span data-stu-id="9b510-124">No</span></span>|<span data-ttu-id="9b510-125">예</span><span class="sxs-lookup"><span data-stu-id="9b510-125">No</span></span>|  
|<span data-ttu-id="9b510-126">연결 패치를 사용 하는 .NET Framework 4.0 ADO.NET**<sup>\*</sup>**</span><span class="sxs-lookup"><span data-stu-id="9b510-126">ADO.NET with .NET Framework 4.0 with connectivity patch**<sup>\*</sup>**</span></span> |<span data-ttu-id="9b510-127">예</span><span class="sxs-lookup"><span data-stu-id="9b510-127">Yes</span></span>|<span data-ttu-id="9b510-128">yes</span><span class="sxs-lookup"><span data-stu-id="9b510-128">Yes</span></span>|<span data-ttu-id="9b510-129">yes</span><span class="sxs-lookup"><span data-stu-id="9b510-129">Yes</span></span>|<span data-ttu-id="9b510-130">yes</span><span class="sxs-lookup"><span data-stu-id="9b510-130">Yes</span></span>|<span data-ttu-id="9b510-131">yes</span><span class="sxs-lookup"><span data-stu-id="9b510-131">Yes</span></span>|  
|<span data-ttu-id="9b510-132">.NET Framework 3.5 s p 1과 연결 패치가 있는 ADO.NET**<sup>**</sup>\*\*</span><span class="sxs-lookup"><span data-stu-id="9b510-132">ADO.NET with .NET Framework 3.5 SP1 with connectivity patch **<sup>**</sup>\*\*</span></span> |<span data-ttu-id="9b510-133">예</span><span class="sxs-lookup"><span data-stu-id="9b510-133">Yes</span></span>|<span data-ttu-id="9b510-134">yes</span><span class="sxs-lookup"><span data-stu-id="9b510-134">Yes</span></span>|<span data-ttu-id="9b510-135">yes</span><span class="sxs-lookup"><span data-stu-id="9b510-135">Yes</span></span>|<span data-ttu-id="9b510-136">yes</span><span class="sxs-lookup"><span data-stu-id="9b510-136">Yes</span></span>|<span data-ttu-id="9b510-137">yes</span><span class="sxs-lookup"><span data-stu-id="9b510-137">Yes</span></span>|  
|<span data-ttu-id="9b510-138">SQL Server용 Microsoft JDBC Driver 4.0</span><span class="sxs-lookup"><span data-stu-id="9b510-138">Microsoft JDBC driver 4.0 for SQL Server</span></span>|<span data-ttu-id="9b510-139">예</span><span class="sxs-lookup"><span data-stu-id="9b510-139">Yes</span></span>|<span data-ttu-id="9b510-140">yes</span><span class="sxs-lookup"><span data-stu-id="9b510-140">Yes</span></span>|<span data-ttu-id="9b510-141">yes</span><span class="sxs-lookup"><span data-stu-id="9b510-141">Yes</span></span>|<span data-ttu-id="9b510-142">yes</span><span class="sxs-lookup"><span data-stu-id="9b510-142">Yes</span></span>|<span data-ttu-id="9b510-143">yes</span><span class="sxs-lookup"><span data-stu-id="9b510-143">Yes</span></span>|  
  
 <span data-ttu-id="9b510-144">**<sup>\*</sup>**.NET Framework 4.0:를 사용 하 여 ADO .NET 용 연결 패치를 다운로드 [https://support.microsoft.com/kb/2600211](https://support.microsoft.com/kb/2600211) 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b510-144">**<sup>\*</sup>**  Download the connectivity patch for ADO .NET with .NET Framework 4.0: [https://support.microsoft.com/kb/2600211](https://support.microsoft.com/kb/2600211).</span></span>  
  
 <span data-ttu-id="9b510-145">**<sup>**</sup>\* \* .NET Framework 3.5 SP1:를 사용 하 여 ADO.NET에 대 한 연결 패치를 다운로드 [https://support.microsoft.com/kb/2654347](https://support.microsoft.com/kb/2654347) 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b510-145">**<sup>**</sup>\*\*  Download the connectivity patch for ADO.NET with .NET Framework 3.5 SP1: [https://support.microsoft.com/kb/2654347](https://support.microsoft.com/kb/2654347).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9b510-146">가용성 그룹 수신기에 연결하려면 클라이언트에서 TCP 연결 문자열을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b510-146">To connect to an availability group listener, a client must use a TCP connection string.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="9b510-147">관련 작업</span><span class="sxs-lookup"><span data-stu-id="9b510-147">Related Tasks</span></span>  
  
-   [<span data-ttu-id="9b510-148">가용성 그룹의 생성 및 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9b510-148">Creation and Configuration of Availability Groups &#40;SQL Server&#41;</span></span>](creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="9b510-149">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9b510-149">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="9b510-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9b510-150">See Also</span></span>  
 <span data-ttu-id="9b510-151">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9b510-151">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="9b510-152">[장애 조치 (Failover) 클러스터링 및 AlwaysOn 가용성 그룹 &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9b510-152">[Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="9b510-153">[AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 필수 조건, 제한 사항 및 권장 사항&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="9b510-153">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="9b510-154">[가용성 그룹 수신기, 클라이언트 연결 및 애플리케이션 장애 조치(failover)&#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="9b510-154">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 <span data-ttu-id="9b510-155">[가용성 복제본에 대한 클라이언트 연결 액세스 정보&#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9b510-155">[About Client Connection Access to Availability Replicas &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) </span></span>  
 <span data-ttu-id="9b510-156">[고가용성 및 재해 복구를 위한 AlwaysOn 솔루션 가이드 Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkId=227600) </span><span class="sxs-lookup"><span data-stu-id="9b510-156">[Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery](https://go.microsoft.com/fwlink/?LinkId=227600) </span></span>  
 <span data-ttu-id="9b510-157">[SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그](https://blogs.msdn.com/b/sqlalwayson/) </span><span class="sxs-lookup"><span data-stu-id="9b510-157">[SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn Team Blog](https://blogs.msdn.com/b/sqlalwayson/) </span></span>  
 <span data-ttu-id="9b510-158">[Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7 또는 Windows Server 2008 R2를 실행하는 컴퓨터에서 IPSec 연결을 다시 연결할 때 시간이 오래 지연 발생](https://support.microsoft.com/kb/980915) </span><span class="sxs-lookup"><span data-stu-id="9b510-158">[A long time delay occurs when you reconnect an IPSec connection from a computer that is running Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7, or Windows Server 2008 R2](https://support.microsoft.com/kb/980915) </span></span>  
 <span data-ttu-id="9b510-159">[클러스터 서비스가 Windows Server 2008 R2에서 IPv6 IP 주소를 장애 조치하는 데 30초 정도 걸림(영문)](https://support.microsoft.com/kb/2578113) </span><span class="sxs-lookup"><span data-stu-id="9b510-159">[The Cluster service takes about 30 seconds to fail over IPv6 IP addresses in Windows Server 2008 R2](https://support.microsoft.com/kb/2578113) </span></span>  
 [<span data-ttu-id="9b510-160">클러스터와 애플리케이션 서버 간에 라우터가 없는 경우 장애 조치(Failover) 작업이 느림</span><span class="sxs-lookup"><span data-stu-id="9b510-160">Slow failover operation if no router exists between the cluster and an application server</span></span>](https://support.microsoft.com/kb/2582281)  
  
  
