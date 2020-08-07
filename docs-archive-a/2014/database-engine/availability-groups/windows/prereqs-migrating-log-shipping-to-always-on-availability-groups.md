---
title: 로그 전달에서 AlwaysOn 가용성 그룹 (SQL Server)로 마이그레이션하기 위한 필수 구성 요소 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 2738ce65-205e-4682-92d8-dc7e37c58b2b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 76b50d5af8eb520b3764ff56397c040f2d0d0141
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734460"
---
# <a name="prerequisites-for-migrating-from-log-shipping-to-alwayson-availability-groups-sql-server"></a><span data-ttu-id="cde36-102">로그 전달에서 AlwaysOn 가용성 그룹(SQL Server)으로 마이그레이션하기 위한 사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="cde36-102">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="cde36-103">이 항목에서는 하나 이상의 보조 데이터베이스와 함께 로그 전달 주 데이터베이스를 AlwaysOn 주 데이터베이스 및 보조 데이터베이스로 변환하기 위한 사전 요구 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cde36-103">This topic describes the prerequisites for converting a log shipping primary database along with one or more of its secondary databases to an AlwaysOn primary database and secondary database(s).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cde36-104">가용성 그룹에서 읽기 가능한 주 데이터베이스 또는 보조 데이터베이스를 로그 전달 주 데이터베이스로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cde36-104">You can configure any primary or secondary database (possibly readable) in an availability group as a log shipping primary database.</span></span>  
  
 <span data-ttu-id="cde36-105">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="cde36-105">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="cde36-106">가용성 그룹 사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="cde36-106">Availability Group Prerequisites</span></span>](#AGPrereqsRealAddress)  
  
-   [<span data-ttu-id="cde36-107">로그 전달 사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="cde36-107">Log Shipping Prerequisites</span></span>](#LogShipPrereqs)  
  
-   [<span data-ttu-id="cde36-108">관련 작업</span><span class="sxs-lookup"><span data-stu-id="cde36-108">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="cde36-109">관련 내용</span><span class="sxs-lookup"><span data-stu-id="cde36-109">Related Content</span></span>](#RelatedContent)  
  
##  <a name="availability-group-prerequisites"></a><a name="AGPrereqsRealAddress"></a><span data-ttu-id="cde36-110">가용성 그룹 필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="cde36-110">Availability Group Prerequisites</span></span>  
 <span data-ttu-id="cde36-111">가용성 그룹의 주 복제본에서 백업 작업이 실행되도록 허용하려면 다음 AlwaysOn 가용성 그룹 백업 설정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cde36-111">To allow backup jobs to run on the primary replica of the availability group, use the following AlwaysOn Availability Groups backup settings:</span></span>  
  
|<span data-ttu-id="cde36-112">속성</span><span class="sxs-lookup"><span data-stu-id="cde36-112">Property</span></span>|<span data-ttu-id="cde36-113">설정</span><span class="sxs-lookup"><span data-stu-id="cde36-113">Setting</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="cde36-114">가용성 그룹의 자동화된 백업 기본 설정</span><span class="sxs-lookup"><span data-stu-id="cde36-114">Automated backup preference of availability group</span></span>|<span data-ttu-id="cde36-115">주 복제본에만</span><span class="sxs-lookup"><span data-stu-id="cde36-115">Only on the primary replica</span></span>|  
|<span data-ttu-id="cde36-116">주 복제본의 백업 우선 순위</span><span class="sxs-lookup"><span data-stu-id="cde36-116">Backup priority of the primary replica.</span></span>|<span data-ttu-id="cde36-117">>0</span><span class="sxs-lookup"><span data-stu-id="cde36-117">>0</span></span>|  
  
 <span data-ttu-id="cde36-118">**추가 정보**</span><span class="sxs-lookup"><span data-stu-id="cde36-118">**For more information:**</span></span>  
  
 [<span data-ttu-id="cde36-119">가용성 그룹 속성 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cde36-119">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
 [<span data-ttu-id="cde36-120">가용성 복제본에 백업 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cde36-120">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="log-shipping-prerequisites"></a><a name="LogShipPrereqs"></a><span data-ttu-id="cde36-121">로그 전달 필수 조건</span><span class="sxs-lookup"><span data-stu-id="cde36-121">Log Shipping Prerequisites</span></span>  
  
-   <span data-ttu-id="cde36-122">로그 전달 주 데이터베이스가 가용성 그룹의 초기/현재 주 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cde36-122">The log shipping primary database must reside on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the initial/current primary replica of the availability group.</span></span>  
  
-   <span data-ttu-id="cde36-123">AlwaysOn 보조 데이터베이스로 변환할 지정된 로그 전달 보조 데이터베이스는 다음 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cde36-123">For a given log shipping secondary database to be converted to an AlwaysOn secondary database, it must:</span></span>  
  
    -   <span data-ttu-id="cde36-124">주 데이터베이스와 동일한 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cde36-124">Use the same name as the primary database.</span></span>  
  
    -   <span data-ttu-id="cde36-125">가용성 그룹에 대한 보조 복제본을 호스팅하는 서버 인스턴스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cde36-125">Reside on a server instance that hosts a secondary replica for the availability group.</span></span>  
  
 <span data-ttu-id="cde36-126">주 데이터베이스에서 백업 작업이 실행되고 나면 백업 작업을 사용하지 않도록 설정하고, 지정된 보조 데이터베이스에서 복원 작업이 실행되고 나면 복원 작업을 사용하지 않도록 설정하십시오.</span><span class="sxs-lookup"><span data-stu-id="cde36-126">Once the backup job has run on the primary database, disable the backup job, and once the restore job has run on a given secondary database, disable the restore job.</span></span>  
  
 <span data-ttu-id="cde36-127">가용성 그룹에 대해 모든 보조 데이터베이스를 만든 후에는 보조 복제본에서 백업을 수행할 경우 가용성 그룹의 자동화된 백업 기본 설정을 다시 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cde36-127">After you have created all the secondary databases for the availability group, if you want to perform backups on secondary replicas, you need to re-configure the automated backup preference of the availability group.</span></span>  
  
 <span data-ttu-id="cde36-128">**추가 정보**</span><span class="sxs-lookup"><span data-stu-id="cde36-128">**For more information:**</span></span>  
  
 <span data-ttu-id="cde36-129">[로그 전달 구성을 가용성 그룹으로 변환](https://blogs.msdn.com/b/sqlalwayson/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx) (SQL Server 블로그)</span><span class="sxs-lookup"><span data-stu-id="cde36-129">[Converting a logshipping configuration to Availability Group](https://blogs.msdn.com/b/sqlalwayson/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx) (a SQL Server blog)</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="cde36-130">관련 작업</span><span class="sxs-lookup"><span data-stu-id="cde36-130">Related Tasks</span></span>  
 <span data-ttu-id="cde36-131">**로그 전달**</span><span class="sxs-lookup"><span data-stu-id="cde36-131">**Log shipping**</span></span>  
  
-   [<span data-ttu-id="cde36-132">SQL Server 2014 &#40;Transact-sql&#41;로그 전달 업그레이드</span><span class="sxs-lookup"><span data-stu-id="cde36-132">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](../../log-shipping/upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="cde36-133">로그 전달 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cde36-133">Remove Log Shipping &#40;SQL Server&#41;</span></span>](../../log-shipping/remove-log-shipping-sql-server.md)  
  
 <span data-ttu-id="cde36-134">**AlwaysOn 가용성 그룹**</span><span class="sxs-lookup"><span data-stu-id="cde36-134">**AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="cde36-135">가용성 그룹 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="cde36-135">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="cde36-136">새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="cde36-136">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="cde36-137">가용성 그룹 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cde36-137">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="cde36-138">가용성 그룹 만들기&#40;SQL Server PowerShell&#41;</span><span class="sxs-lookup"><span data-stu-id="cde36-138">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
-   [<span data-ttu-id="cde36-139">가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cde36-139">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="cde36-140">가용성 복제본에 백업 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cde36-140">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="cde36-141">관련 내용</span><span class="sxs-lookup"><span data-stu-id="cde36-141">Related Content</span></span>  
  
-   <span data-ttu-id="cde36-142">**블로그:**</span><span class="sxs-lookup"><span data-stu-id="cde36-142">**Blogs:**</span></span>  
  
     [<span data-ttu-id="cde36-143">로그 전달 구성을 가용성 그룹으로 변환</span><span class="sxs-lookup"><span data-stu-id="cde36-143">Converting a logshipping configuration to Availability Group</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/converting-a-logshipping-configuration-to-availability-group)  
  
     [<span data-ttu-id="cde36-144">기존 가용성 그룹에 로그 전달 주 데이터베이스 및 보조 데이터베이스 추가</span><span class="sxs-lookup"><span data-stu-id="cde36-144">Add a Log Shipping Primary Database and Secondary Database(s) to an Existing Availability Group</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/add-a-log-shipping-primary-database-and-secondary-databases-to-an-existing-availability-group)  
  
     [<span data-ttu-id="cde36-145">SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그</span><span class="sxs-lookup"><span data-stu-id="cde36-145">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/)  
  
     [<span data-ttu-id="cde36-146">CSS SQL Server 엔지니어 블로그</span><span class="sxs-lookup"><span data-stu-id="cde36-146">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="cde36-147">**백서:**</span><span class="sxs-lookup"><span data-stu-id="cde36-147">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="cde36-148">마이그레이션 가이드: 데이터베이스 미러링 및 로그 전달을 조합하는 이전 배포에서 AlwaysOn 가용성 그룹으로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="cde36-148">Migration Guide: Migrating to AlwaysOn Availability Groups from Prior Deployments Combining Database Mirroring and Log Shipping</span></span>](https://msdn.microsoft.com/library/jj635217)  
  
     [<span data-ttu-id="cde36-149">SQL Server 2012에 대한 Microsoft 백서</span><span class="sxs-lookup"><span data-stu-id="cde36-149">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="cde36-150">SQL Server 고객 자문 팀 백서</span><span class="sxs-lookup"><span data-stu-id="cde36-150">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="cde36-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cde36-151">See Also</span></span>  
 <span data-ttu-id="cde36-152">[로그 전달 정보&#40;SQL Server&#41;](../../log-shipping/about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cde36-152">[About Log Shipping &#40;SQL Server&#41;](../../log-shipping/about-log-shipping-sql-server.md) </span></span>  
 <span data-ttu-id="cde36-153">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cde36-153">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="cde36-154">가용성 그룹 모니터링&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cde36-154">Monitoring of Availability Groups &#40;SQL Server&#41;</span></span>](monitoring-of-availability-groups-sql-server.md)  
  
  
