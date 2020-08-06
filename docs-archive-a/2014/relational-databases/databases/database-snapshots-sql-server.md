---
title: 데이터베이스 스냅샷(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- static database views
- snapshots [SQL Server database snapshots]
- source databases [SQL Server]
- snapshots [SQL Server database snapshots], about database snapshots
- database snapshots [SQL Server]
- read-only database views
- database snapshots [SQL Server], about database snapshots
ms.assetid: 00179314-f23e-47cb-a35c-da6f180f86d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8a0fa9b6cee2287d4e6060d4cb39f34d909e7db9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742215"
---
# <a name="database-snapshots-sql-server"></a><span data-ttu-id="0243c-102">데이터베이스 스냅샷(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0243c-102">Database Snapshots (SQL Server)</span></span>
  <span data-ttu-id="0243c-103">데이터베이스 스냅샷은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스( *원본 데이터베이스*)의 읽기 전용 정적 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-103">A database snapshot is a read-only, static view of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database (the *source database*).</span></span> <span data-ttu-id="0243c-104">데이터베이스 스냅샷은 스냅샷을 만든 시점의 원본 데이터베이스와 트랜잭션이 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-104">The database snapshot is transactionally consistent with the source database as of the moment of the snapshot's creation.</span></span> <span data-ttu-id="0243c-105">데이터베이스 스냅샷은 항상 원본 데이터베이스와 동일한 서버 인스턴스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-105">A database snapshot always resides on the same server instance as its source database.</span></span> <span data-ttu-id="0243c-106">원본 데이터베이스가 업데이트되면 데이터베이스 스냅샷도 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-106">As the source database is updated, the database snapshot is updated.</span></span> <span data-ttu-id="0243c-107">따라서 데이터베이스 스냅샷을 오래 보관할수록 사용 가능한 공간이 소모될 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-107">Therefore, the longer a database snapshot exists, the more likely it is to use up its available disk space.</span></span>  
  
 <span data-ttu-id="0243c-108">지정된 원본 데이터베이스에 스냅샷이 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-108">Multiple snapshots can exist on a given source database.</span></span> <span data-ttu-id="0243c-109">각 데이터베이스 스냅샷은 데이터베이스 소유자가 명시적으로 삭제하기 전까지 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-109">Each database snapshot persists until it is explicitly dropped by the database owner.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0243c-110">데이터베이스 스냅샷은 스냅샷 백업, 트랜잭션의 스냅샷 격리 또는 스냅샷 복제와 관련이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-110">Database snapshots are unrelated to snapshot backups, snapshot isolation of transactions, or snapshot replication.</span></span>  
  
 <span data-ttu-id="0243c-111">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="0243c-111">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="0243c-112">기능 개요</span><span class="sxs-lookup"><span data-stu-id="0243c-112">Feature Overview</span></span>](#FeatureOverview)  
  
-   [<span data-ttu-id="0243c-113">데이터베이스 스냅샷의 이점</span><span class="sxs-lookup"><span data-stu-id="0243c-113">Benefits of Database Snapshots</span></span>](#Benefits)  
  
-   [<span data-ttu-id="0243c-114">용어 및 정의</span><span class="sxs-lookup"><span data-stu-id="0243c-114">Terms and Definitions</span></span>](#TermsAndDefinitions)  
  
-   [<span data-ttu-id="0243c-115">데이터베이스 스냅샷 사전 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="0243c-115">Prerequisites for and Limitations on Database Snapshots</span></span>](#LimitationsRequirements)  
  
-   [<span data-ttu-id="0243c-116">관련 작업</span><span class="sxs-lookup"><span data-stu-id="0243c-116">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="feature-overview"></a><a name="FeatureOverview"></a> <span data-ttu-id="0243c-117">기능 개요</span><span class="sxs-lookup"><span data-stu-id="0243c-117">Feature Overview</span></span>  
 <span data-ttu-id="0243c-118">데이터베이스 스냅샷은 데이터 페이지 수준에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-118">Database snapshots operate at the data-page level.</span></span> <span data-ttu-id="0243c-119">원본 데이터베이스의 페이지를 처음 수정하기 전에 원본 페이지는 원본 데이터베이스에서 스냅샷으로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-119">Before a page of the source database is modified for the first time, the original page is copied from the source database to the snapshot.</span></span> <span data-ttu-id="0243c-120">스냅샷은 원본 페이지를 저장하여 스냅샷이 만들어질 때 상태 그대로 데이터 레코드를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-120">The snapshot stores the original page, preserving the data records as they existed when the snapshot was created.</span></span> <span data-ttu-id="0243c-121">처음 수정하는 모든 페이지에 같은 프로세스가 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-121">The same process is repeated for every page that is being modified for the first time.</span></span> <span data-ttu-id="0243c-122">사용자에게 데이터베이스 스냅샷은 변경되지 않는 것으로 보입니다. 데이터베이스 스냅샷의 읽기 작업은 원본 데이터 페이지의 위치에 관계없이 항상 원본 데이터 페이지에 액세스하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-122">To the user, a database snapshot appears never to change, because read operations on a database snapshot always access the original data pages, regardless of where they reside.</span></span>  
  
 <span data-ttu-id="0243c-123">복사된 원본 페이지를 저장하기 위해 스냅샷은 하나 이상의 *스파스 파일*을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-123">To store the copied original pages, the snapshot uses one or more *sparse files*.</span></span> <span data-ttu-id="0243c-124">처음에 스파스 파일은 기본적으로 사용자 데이터가 없는 빈 파일이며 사용자 데이터에 대한 디스크 공간이 할당되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-124">Initially, a sparse file is an essentially empty file that contains no user data and has not yet been allocated disk space for user data.</span></span> <span data-ttu-id="0243c-125">원본 데이터베이스에서 페이지를 업데이트할수록 파일 크기가 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-125">As more and more pages are updated in the source database, the size of the file grows.</span></span> <span data-ttu-id="0243c-126">다음 그림은 스냅샷 크기에 대한 두 가지 상반된 업데이트 패턴의 효과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-126">The following figure illustrates the effects of two contrasting update patterns on the size of a snapshot.</span></span> <span data-ttu-id="0243c-127">업데이트 패턴 A는 스냅샷 수명 동안 원본 페이지의 30%가 업데이트되는 환경을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-127">Update pattern A reflects an environment in which only 30 percent of the original pages are updated during the life of the snapshot.</span></span> <span data-ttu-id="0243c-128">업데이트 패턴 B는 스냅샷 수명 동안 원본 페이지의 80%가 업데이트되는 환경을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-128">Update pattern B reflects an environment in which 80 percent of the original pages are updated during the life of the snapshot.</span></span>  
  
 <span data-ttu-id="0243c-129">![대체 업데이트 패턴 및 스냅샷 크기](../../database-engine/media/dbview-04.gif "대체 업데이트 패턴 및 스냅샷 크기")</span><span class="sxs-lookup"><span data-stu-id="0243c-129">![Alternative update patterns and snapshot size](../../database-engine/media/dbview-04.gif "Alternative update patterns and snapshot size")</span></span>  
  
##  <a name="benefits-of-database-snapshots"></a><a name="Benefits"></a> <span data-ttu-id="0243c-130">데이터베이스 스냅샷의 이점</span><span class="sxs-lookup"><span data-stu-id="0243c-130">Benefits of Database Snapshots</span></span>  
  
-   <span data-ttu-id="0243c-131">스냅샷은 보고 용도로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-131">Snapshots can be used for reporting purposes.</span></span>  
  
     <span data-ttu-id="0243c-132">클라이언트는 데이터베이스 스냅샷을 쿼리할 수 있으며 이 기능은 스냅샷 생성 시의 데이터를 기준으로 보고서를 작성하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-132">Clients can query a database snapshot, which makes it useful for writing reports based on the data at the time of snapshot creation.</span></span>  
  
-   <span data-ttu-id="0243c-133">보고서 생성을 위해 기록 데이터 유지 관리</span><span class="sxs-lookup"><span data-stu-id="0243c-133">Maintaining historical data for report generation.</span></span>  
  
     <span data-ttu-id="0243c-134">스냅샷은 사용자 액세스를 특정 지정 시간의 데이터로 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-134">A snapshot can extend user access to data from a particular point in time.</span></span> <span data-ttu-id="0243c-135">예를 들어 회계 분기와 같은 지정된 기간이 끝나는 시점에 데이터베이스 스냅샷을 만들어 향후 보고 시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-135">For example, you can create a database snapshot at the end of a given time period (such as a financial quarter) for later reporting.</span></span> <span data-ttu-id="0243c-136">그런 다음 스냅샷을 통해 기말 보고서를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-136">You can then run end-of-period reports on the snapshot.</span></span> <span data-ttu-id="0243c-137">또한 디스크 공간이 충분하다면 기말 스냅샷을 무제한 보관하여 조직 성과 조사 등의 목적을 위해 해당 기간의 결과를 대상으로 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-137">If disk space permits, you can also maintain end-of-period snapshots indefinitely, allowing queries against the results from these periods; for example, to investigate organizational performance.</span></span>  
  
-   <span data-ttu-id="0243c-138">가용성 목적으로 유지 관리 중인 미러 데이터베이스를 활용하여 보고 작업 오프로드</span><span class="sxs-lookup"><span data-stu-id="0243c-138">Using a mirror database that you are maintaining for availability purposes to offload reporting.</span></span>  
  
     <span data-ttu-id="0243c-139">데이터베이스 스냅샷을 데이터베이스 미러링에 사용하면 보고를 위해 미러 서버의 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-139">Using database snapshots with database mirroring permits you to make the data on the mirror server accessible for reporting.</span></span> <span data-ttu-id="0243c-140">또한 미러 데이터베이스에서 쿼리를 실행하면 주 데이터베이스의 리소스를 확보할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-140">Additionally, running queries on the mirror database can free up resources on the principal.</span></span> <span data-ttu-id="0243c-141">자세한 내용은 [데이터베이스 미러링 및 데이터베이스 스냅샷&#40;SQL Server&#41;](database-snapshots-sql-server.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-141">For more information, see [Database Mirroring and Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md).</span></span>  
  
-   <span data-ttu-id="0243c-142">관리 오류로부터 데이터 보호</span><span class="sxs-lookup"><span data-stu-id="0243c-142">Safeguarding data against administrative error.</span></span>  
  
-   <span data-ttu-id="0243c-143">원본 데이터베이스에서 사용자 오류가 발생할 경우 지정된 데이터베이스 스냅샷을 생성했을 때의 상태로 원본 데이터베이스를 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-143">In the event of a user error on a source database, you can revert the source database to the state it was in when a given database snapshot was created.</span></span> <span data-ttu-id="0243c-144">데이터 손실은 스냅샷 생성 이후의 데이터베이스 업데이트로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-144">Data loss is confined to updates to the database since the snapshot's creation.</span></span>  
  
     <span data-ttu-id="0243c-145">예를 들어 대량 업데이트 또는 스키마 변경과 같은 주요 업데이트를 수행하기 전에 데이터베이스에 데이터베이스 스냅샷을 만들어 데이터를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-145">For example, before doing major updates, such as a bulk update or a schema change, create a database snapshot on the database protects data.</span></span> <span data-ttu-id="0243c-146">오류가 발생하면 스냅샷을 사용하여 데이터베이스를 해당 스냅샷으로 되돌려 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-146">If you make a mistake, you can use the snapshot to recover by reverting the database to the snapshot.</span></span> <span data-ttu-id="0243c-147">이러한 용도에는 백업에서 복원하는 것보다 되돌리는 것이 훨씬 빠를 가능성이 높지만 되돌린 시점 이후로는 롤포워드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-147">Reverting is potentially much faster for this purpose than restoring from a backup; however, you cannot roll forward afterward.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="0243c-148">오프라인 또는 손상된 데이터베이스에서는 되돌릴 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-148">Reverting does not work in an offline or corrupted database.</span></span> <span data-ttu-id="0243c-149">따라서 데이터베이스를 보호하려면 정기적으로 백업하고 복원 계획을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-149">Therefore, taking regular backups and testing your restore plan are necessary to protect a database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0243c-150">데이터베이스 스냅샷은 원본 데이터베이스에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-150">Database snapshots are dependent on the source database.</span></span> <span data-ttu-id="0243c-151">따라서 데이터베이스 스냅샷을 사용하여 데이터베이스를 되돌리는 기능은 백업 및 복원 전략을 대체하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-151">Therefore, using database snapshots for reverting a database is not a substitute for your backup and restore strategy.</span></span> <span data-ttu-id="0243c-152">예약된 백업 일정도 반드시 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-152">Performing all your scheduled backups remains essential.</span></span> <span data-ttu-id="0243c-153">데이터베이스 스냅샷을 만든 시점까지 원본 데이터베이스를 복원해야 하는 경우 이 작업을 수행할 수 있는 백업 정책을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-153">If you must restore the source database to the point in time at which you created a database snapshot, implement a backup policy that enables you to do that.</span></span>  
  
-   <span data-ttu-id="0243c-154">사용자 오류로부터 데이터 보호</span><span class="sxs-lookup"><span data-stu-id="0243c-154">Safeguarding data against user error.</span></span>  
  
     <span data-ttu-id="0243c-155">정기적으로 데이터베이스 스냅샷을 만들면 테이블 삭제와 같은 주요 사용자 오류의 영향을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-155">By creating database snapshots on a regular basis, you can mitigate the impact of a major user error, such as a dropped table.</span></span> <span data-ttu-id="0243c-156">철저한 보호를 위해 충분한 기간에 걸쳐 일련의 데이터베이스 스냅샷을 만들어 대부분의 사용자 오류를 찾아내고 이에 대처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-156">For a high level of protection, you can create a series of database snapshots spanning enough time to recognize and respond to most user errors.</span></span> <span data-ttu-id="0243c-157">예를 들어 디스크 리소스에 따라 24시간 간격으로 6개에서 12개 사이의 연속된 스냅샷을 유지 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-157">For instance, you might maintain 6 to 12 rolling snapshots spanning a 24-hour interval, depending on your disk resources.</span></span> <span data-ttu-id="0243c-158">그러면 새 스냅샷이 생성될 때마다 가장 오래된 스냅샷을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-158">Then, each time a new snapshot is created, the earliest snapshot can be deleted.</span></span>  
  
    -   <span data-ttu-id="0243c-159">사용자 오류로부터 복구하려면 오류 발생 직전의 스냅샷으로 데이터베이스를 되돌리면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-159">To recover from a user error, you can revert the database to the snapshot immediately before the error.</span></span> <span data-ttu-id="0243c-160">이러한 용도에는 백업에서 복원하는 것보다 되돌리는 것이 훨씬 빠를 가능성이 높지만 되돌린 시점 이후로는 롤포워드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-160">Reverting is potentially much faster for this purpose than restoring from a backup; however, you cannot roll forward afterward.</span></span>  
  
    -   <span data-ttu-id="0243c-161">또는 스냅샷의 정보를 사용하여 삭제된 테이블이나 그 밖의 손실된 데이터를 직접 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-161">Alternatively, you may be able to manually reconstruct a dropped table or other lost data from the information in a snapshot.</span></span> <span data-ttu-id="0243c-162">예를 들어 스냅샷의 데이터를 데이터베이스로 대량 복사하고 이 데이터를 데이터베이스에 직접 다시 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-162">For instance, you could bulk copy the data out of the snapshot into the database and manually merge the data back into the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0243c-163">데이터베이스 스냅샷의 사용 목적에 따라 데이터베이스에 필요한 동시 스냅샷의 수, 새 스냅샷 생성 간격 및 보관 기간이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-163">Your reasons for using database snapshots determine how many concurrent snapshots you need on a database, how frequently to create a new snapshot, and how long to keep it.</span></span>  
  
-   <span data-ttu-id="0243c-164">테스트 데이터베이스 관리</span><span class="sxs-lookup"><span data-stu-id="0243c-164">Managing a test database</span></span>  
  
     <span data-ttu-id="0243c-165">테스트 환경에서 테스트 프로토콜을 반복 실행하는 경우 각 테스트 시작 시 데이터베이스에 동일한 데이터가 있는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-165">In a testing environment, it can be useful when repeatedly running a test protocol for the database to contain identical data at the start of each round of testing.</span></span> <span data-ttu-id="0243c-166">첫 번째 테스트를 실행하기 전에 애플리케이션 개발자나 테스터는 테스트 데이터베이스에서 데이터베이스 스냅샷을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-166">Before running the first round, an application developer or tester can create a database snapshot on the test database.</span></span> <span data-ttu-id="0243c-167">각 테스트를 실행한 후 데이터베이스 스냅샷을 되돌리면 신속하게 데이터베이스를 이전 상태로 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-167">After each test run, the database can be quickly returned to its prior state by reverting the database snapshot.</span></span>  
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="0243c-168">용어 및 정의</span><span class="sxs-lookup"><span data-stu-id="0243c-168">Terms and Definitions</span></span>  
 <span data-ttu-id="0243c-169">database snapshot</span><span class="sxs-lookup"><span data-stu-id="0243c-169">database snapshot</span></span>  
 <span data-ttu-id="0243c-170">데이터베이스(원본 데이터베이스)의 트랜잭션이 일치하는 읽기 전용 정적 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-170">A transactionally consistent, read-only, static view of a database (the source database).</span></span>  
  
 <span data-ttu-id="0243c-171">원본 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="0243c-171">source database</span></span>  
 <span data-ttu-id="0243c-172">데이터베이스 스냅샷의 경우 스냅샷이 만들어진 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-172">For a database snapshot, the database on which the snapshot was created.</span></span> <span data-ttu-id="0243c-173">데이터베이스 스냅샷은 원본 데이터베이스에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-173">Database snapshots are dependent on the source database.</span></span> <span data-ttu-id="0243c-174">데이터베이스 스냅샷은 데이터베이스와 동일한 서버 인스턴스에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-174">The snapshots of a database must be on the same server instance as the database.</span></span> <span data-ttu-id="0243c-175">또한 어떤 이유에서든 데이터베이스를 사용할 수 없게 되면 해당 데이터베이스 스냅샷도 모두 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-175">Furthermore, if that database becomes unavailable for any reason, all of its database snapshots also become unavailable.</span></span>  
  
 <span data-ttu-id="0243c-176">스파스 파일(sparse file)</span><span class="sxs-lookup"><span data-stu-id="0243c-176">sparse file</span></span>  
 <span data-ttu-id="0243c-177">NTFS 파일 시스템에서 제공하는 파일로, 다른 경우보다 훨씬 더 적은 디스크 공간만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-177">A file provided by the NTFS file system that requires much less disk space than would otherwise be needed.</span></span> <span data-ttu-id="0243c-178">스파스 파일은 데이터베이스 스냅샷에 복사된 페이지를 저장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-178">A sparse file is used to store pages copied to a database snapshot.</span></span> <span data-ttu-id="0243c-179">스파스 파일은 처음 만들어질 때 디스크 공간을 거의 차지하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-179">When first created, a sparse file takes up little disk space.</span></span> <span data-ttu-id="0243c-180">데이터베이스 스냅샷에 데이터를 쓸수록 NTFS는 해당하는 스파스 파일에 점진적으로 디스크 공간을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-180">As data is written to a database snapshot, NTFS allocates disk space gradually to the corresponding sparse file.</span></span>  
  
##  <a name="prerequisites-for-and-limitations-on-database-snapshots"></a><a name="LimitationsRequirements"></a> <span data-ttu-id="0243c-181">데이터베이스 스냅샷 사전 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="0243c-181">Prerequisites for and Limitations on Database Snapshots</span></span>  
 <span data-ttu-id="0243c-182">**섹션 내용**</span><span class="sxs-lookup"><span data-stu-id="0243c-182">**In This Section:**</span></span>  
  
-   [<span data-ttu-id="0243c-183">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="0243c-183">Prerequisites</span></span>](#Prerequisites)  
  
-   [<span data-ttu-id="0243c-184">원본 데이터베이스에 대한 제한 사항</span><span class="sxs-lookup"><span data-stu-id="0243c-184">Limitations on the Source Database</span></span>](#LimitsOnSourceDb)  
  
-   [<span data-ttu-id="0243c-185">데이터베이스 스냅샷에 대한 제한 사항</span><span class="sxs-lookup"><span data-stu-id="0243c-185">Limitations on Database Snapshots</span></span>](#LimitsOnDbSS)  
  
-   [<span data-ttu-id="0243c-186">디스크 공간 요구 사항</span><span class="sxs-lookup"><span data-stu-id="0243c-186">Disk Space Requirements</span></span>](#DiskSpace)  
  
-   [<span data-ttu-id="0243c-187">오프라인 파일 그룹의 데이터베이스 스냅샷</span><span class="sxs-lookup"><span data-stu-id="0243c-187">Database Snapshots with Offline Filegroups</span></span>](#OfflineFGs)  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="0243c-188">필수 조건</span><span class="sxs-lookup"><span data-stu-id="0243c-188">Prerequisites</span></span>  
 <span data-ttu-id="0243c-189">복구 모델을 사용할 수 있는 원본 데이터베이스는 다음 사전 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-189">The source database, which can use any recovery model, must meet the following prerequisites:</span></span>  
  
-   <span data-ttu-id="0243c-190">서버 인스턴스는 데이터베이스 스냅샷을 지원하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 버전을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-190">The server instance must be running on an edition of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that supports database snapshots.</span></span> <span data-ttu-id="0243c-191">자세한 내용은 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0243c-191">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="0243c-192">데이터베이스 미러링 세션의 미러 데이터베이스가 아닌 경우 원본 데이터베이스는 온라인 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-192">The source database must be online, unless the database is a mirror database within a database mirroring session.</span></span>  
  
-   <span data-ttu-id="0243c-193">가용성 그룹의 주 데이터베이스 또는 보조 데이터베이스에서 데이터베이스 스냅샷을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-193">You can create a database snapshot on any primary or secondary database in an availability group.</span></span> <span data-ttu-id="0243c-194">복제본 역할은 RESOLVING 상태가 아닌 PRIMARY 또는 SECONDARY 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-194">The replica role must be either PRIMARY or SECONDARY, not in the RESOLVING state.</span></span>  
  
     <span data-ttu-id="0243c-195">데이터베이스 동기화 상태가 SYNCHRONIZING 또는 SYNCHRONIZED인 상태에서 데이터베이스 스냅샷을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-195">We recommend that the database synchronization state be SYNCHRONIZING or SYNCHRONIZED when you create a database snapshot.</span></span> <span data-ttu-id="0243c-196">데이터베이스 동기화 상태가 NOT SYNCHRONIZING인 경우에도 데이터베이스 스냅샷을 만들 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-196">However, database snapshots can be created when the database synchronization state is NOT SYNCHRONIZING.</span></span>  
  
     <span data-ttu-id="0243c-197">자세한 내용은 [AlwaysOn 가용성 그룹이 있는 데이터베이스 스냅샷&#40;SQL Server&#41;](../../database-engine/availability-groups/windows/database-snapshots-with-always-on-availability-groups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0243c-197">For more information, see [Database Snapshots with AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/database-snapshots-with-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="0243c-198">미러 데이터베이스에서 데이터베이스 스냅샷을 만들려면 데이터베이스가 SYNCHRONIZED 미러링 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-198">To create a database snapshot on a mirror database, the database must be in the SYNCHRONIZED mirroring state.</span></span>  
  
-   <span data-ttu-id="0243c-199">원본 데이터베이스는 확장 가능한 공유 데이터베이스로 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-199">The source database cannot be configured as a scalable shared database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0243c-200">모든 복구 모델에서 데이터베이스 스냅샷을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-200">All recovery models support database snapshots.</span></span>  
  
###  <a name="limitations-on-the-source-database"></a><a name="LimitsOnSourceDb"></a> <span data-ttu-id="0243c-201">원본 데이터베이스에 대한 제한 사항</span><span class="sxs-lookup"><span data-stu-id="0243c-201">Limitations on the Source Database</span></span>  
 <span data-ttu-id="0243c-202">데이터베이스 스냅샷이 있는 경우 스냅샷의 원본 데이터베이스에 다음 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-202">As long as a database snapshot exists, the following limitations exist on the snapshot's source database:</span></span>  
  
-   <span data-ttu-id="0243c-203">데이터베이스를 삭제, 분리 또는 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-203">The database cannot be dropped, detached, or restored.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0243c-204">원본 데이터베이스의 백업은 정상적으로 수행되며 데이터베이스 스냅샷의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-204">Backing up the source database works normally; it is unaffected by database snapshots.</span></span>  
  
-   <span data-ttu-id="0243c-205">페이지가 업데이트될 때마다 스냅샷에 대한 쓰기 시 복사 작업으로 인해 원본 데이터베이스의 I/O가 증가하여 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-205">Performance is reduced, due to increased I/O on the source database resulting from a copy-on-write operation to the snapshot every time a page is updated.</span></span>  
  
-   <span data-ttu-id="0243c-206">원본 데이터베이스 또는 모든 스냅샷에서 파일을 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-206">Files cannot be dropped from the source database or from any snapshots.</span></span>  
  
###  <a name="limitations-on-database-snapshots"></a><a name="LimitsOnDbSS"></a> <span data-ttu-id="0243c-207">데이터베이스 스냅샷에 대한 제한 사항</span><span class="sxs-lookup"><span data-stu-id="0243c-207">Limitations on Database Snapshots</span></span>  
 <span data-ttu-id="0243c-208">데이터베이스 스냅샷에 다음 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-208">The following limitations apply to database snapshots:</span></span>  
  
-   <span data-ttu-id="0243c-209">데이터베이스 스냅샷은 원본 데이터베이스와 같은 서버 인스턴스에서 생성 및 유지되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-209">A database snapshot must be created and remain on the same server instance as the source database.</span></span>  
  
-   <span data-ttu-id="0243c-210">데이터베이스 스냅샷은 항상 전체 데이터베이스에 대해 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-210">Database snapshots always work on an entire database.</span></span>  
  
-   <span data-ttu-id="0243c-211">데이터베이스 스냅샷은 원본 데이터베이스에 따라 달라지며 중복 스토리지가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-211">Database snapshots are dependent on the source database and are not redundant storage.</span></span> <span data-ttu-id="0243c-212">데이터베이스 스냅숏은 디스크 오류나 다른 유형의 손상을 방지하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-212">They do not protect against disk errors or other types of corruption.</span></span> <span data-ttu-id="0243c-213">따라서 데이터베이스 스냅샷을 사용하여 데이터베이스를 되돌리는 기능은 백업 및 복원 전략을 대체하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-213">Therefore, using database snapshots for reverting a database is not a substitute for your backup and restore strategy.</span></span> <span data-ttu-id="0243c-214">예약된 백업 일정도 반드시 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-214">Performing all your scheduled backups remains essential.</span></span> <span data-ttu-id="0243c-215">데이터베이스 스냅샷을 만든 시점까지 원본 데이터베이스를 복원해야 하는 경우 이 작업을 수행할 수 있는 백업 정책을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-215">If you must restore the source database to the point in time at which you created a database snapshot, implement a backup policy that enables you to do that.</span></span>  
  
-   <span data-ttu-id="0243c-216">원본 데이터베이스에서 업데이트되는 페이지를 스냅샷으로 밀어넣을 때 스냅샷이 디스크 공간을 모두 소모했거나 다른 오류가 발생한 경우 스냅샷이 주의 대상이 되어 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-216">When a page getting updated on the source database is pushed to a snapshot, if the snapshot runs out of disk space or encounters some other error, the snapshot becomes suspect and must be deleted.</span></span>  
  
-   <span data-ttu-id="0243c-217">스냅샷은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-217">Snapshots are read-only.</span></span> <span data-ttu-id="0243c-218">읽기 전용이므로 업그레이드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-218">Since they are read only, they cannot be upgraded.</span></span> <span data-ttu-id="0243c-219">따라서 업그레이드 후 데이터베이스 스냅샷은 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-219">Therefore, database snapshots are not expected to be viable after an upgrade.</span></span>  
  
-   <span data-ttu-id="0243c-220">**model**, **master**및 **tempdb** 데이터베이스의 스냅샷은 금지됩니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-220">Snapshots of the **model**, **master**, and **tempdb** databases are prohibited.</span></span>  
  
-   <span data-ttu-id="0243c-221">데이터베이스 스냅샷 파일의 사양을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-221">You cannot change any of the specifications of the database snapshot files.</span></span>  
  
-   <span data-ttu-id="0243c-222">데이터베이스 스냅샷에서 파일을 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-222">You cannot drop files from a database snapshot.</span></span>  
  
-   <span data-ttu-id="0243c-223">데이터베이스 스냅샷은 백업 또는 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-223">You cannot back up or restore database snapshots.</span></span>  
  
-   <span data-ttu-id="0243c-224">데이터베이스 스냅샷은 연결 또는 분리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-224">You cannot attach or detach database snapshots.</span></span>  
  
-   <span data-ttu-id="0243c-225">FAT32 파일 시스템 또는 RAW 파티션에 데이터베이스 스냅샷을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-225">You cannot create database snapshots on FAT32 file system or RAW partitions.</span></span> <span data-ttu-id="0243c-226">데이터베이스 스냅샷에 사용되는 스파스 파일은 NTFS 파일 시스템에서 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-226">The sparse files used by database snapshots are provided by the NTFS file system.</span></span>  
  
-   <span data-ttu-id="0243c-227">데이터베이스 스냅샷에서는 전체 텍스트 인덱싱이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-227">Full-text indexing is not supported on database snapshots.</span></span> <span data-ttu-id="0243c-228">전체 텍스트 카탈로그가 원본 데이터베이스로부터 전파되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-228">Full-text catalogs are not propagated from the source database.</span></span>  
  
-   <span data-ttu-id="0243c-229">데이터베이스 스냅샷은 스냅샷을 만든 시점의 원본 데이터베이스의 보안 제약 조건을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-229">A database snapshot inherits the security constraints of its source database at the time of snapshot creation.</span></span> <span data-ttu-id="0243c-230">스냅샷은 읽기 전용이므로 상속된 사용 권한을 변경할 수 없으며 원본의 사용 권한을 변경해도 기존의 스냅샷은 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-230">Because snapshots are read-only, inherited permissions cannot be changed and permission changes made to the source will not be reflected in existing snapshots.</span></span>  
  
-   <span data-ttu-id="0243c-231">스냅샷은 항상 스냅샷을 만든 시점의 파일 그룹 상태를 반영합니다. 즉, 온라인 파일 그룹은 온라인 상태를 유지하고 오프라인 파일 그룹은 오프라인 상태를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-231">A snapshot always reflects the state of filegroups at the time of snapshot creation: online filegroups remain online, and offline filegroups remain offline.</span></span> <span data-ttu-id="0243c-232">자세한 내용은 이 항목 뒷부분의 "오프라인 파일 그룹의 데이터베이스 스냅샷"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0243c-232">For more information, see "Database Snapshots with Offline Filegroups" later in this topic.</span></span>  
  
-   <span data-ttu-id="0243c-233">원본 데이터베이스가 RECOVERY_PENDING이 되면 해당 데이터베이스 스냅샷에 액세스하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-233">If a source database becomes RECOVERY_PENDING, its database snapshots may become inaccessible.</span></span> <span data-ttu-id="0243c-234">그러나 원본 데이터베이스의 문제가 해결되면 스냅샷을 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-234">After the issue on the source database is resolved, however, its snapshots should become available again.</span></span>  
  
-   <span data-ttu-id="0243c-235">압축된 파일 그룹과 읽기 전용 파일 그룹은 되돌리기가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-235">Reverting is unsupported for read-only filegroups and for compressed filegroups.</span></span> <span data-ttu-id="0243c-236">두 유형의 파일 그룹 중 하나가 포함된 데이터베이스를 되돌리려고 하면 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-236">Attempts to revert a database containing either of these types of filegroups fail.</span></span>  
  
-   <span data-ttu-id="0243c-237">로그 전달 구성에서는 보조 데이터베이스가 아닌 주 데이터베이스에서만 데이터베이스 스냅샷을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-237">In a log shipping configuration, database snapshots can be created only on the primary database, not on a secondary database.</span></span> <span data-ttu-id="0243c-238">주 서버 인스턴스와 보조 서버 인스턴스의 역할을 전환하는 경우 주 데이터베이스를 보조 데이터베이스로 설정하려면 먼저 모든 데이터베이스 스냅샷을 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-238">If you switch roles between the primary server instance and a secondary server instance, you must drop all the database snapshots before you can set the primary database up as a secondary database.</span></span>  
  
-   <span data-ttu-id="0243c-239">데이터베이스 스냅샷은 확장 가능한 공유 데이터베이스로 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-239">A database snapshot cannot be configured as a scalable shared database.</span></span>  
  
-   <span data-ttu-id="0243c-240">FILESTREAM 파일 그룹은 데이터베이스 스냅샷에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-240">FILESTREAM filegroups are not supported by database snapshots.</span></span> <span data-ttu-id="0243c-241">FILESTREAM 파일 그룹이 원본 데이터베이스에 있으면 해당 데이터베이스 스냅샷에서 이 파일 그룹이 오프라인 상태로 표시되고 데이터베이스를 되돌리는 데 데이터베이스 스냅샷을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-241">If FILESTREAM filegroups exist in a source database, they are marked as offline in its database snapshots, and the database snapshots cannot be used for reverting the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0243c-242">데이터베이스 스냅샷에 대해 실행되는 SELECT 문에는 FILESTREAM 열을 지정하지 말아야 합니다. 그렇지 않으면 다음 오류 메시지가 반환됩니다. `Could not continue scan with NOLOCK due to data movement.`</span><span class="sxs-lookup"><span data-stu-id="0243c-242">A SELECT statement that is executed on a database snapshot must not specify a FILESTREAM column; otherwise, the following error message will be returned: `Could not continue scan with NOLOCK due to data movement.`</span></span>  
  
-   <span data-ttu-id="0243c-243">읽기 전용 스냅샷에 대한 통계가 없거나 유효하지 않을 경우 [!INCLUDE[ssDE](../../includes/ssde-md.md)]은 tempdb에서 임시 통계를 만들어 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-243">When statistics on a read-only snapshot are missing or stale, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] creates and maintains temporary statistics in tempdb.</span></span> <span data-ttu-id="0243c-244">자세한 내용은 [통계](../statistics/statistics.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0243c-244">For more information, see [Statistics](../statistics/statistics.md).</span></span>  
  
###  <a name="disk-space-requirements"></a><a name="DiskSpace"></a> <span data-ttu-id="0243c-245">디스크 공간 요구 사항</span><span class="sxs-lookup"><span data-stu-id="0243c-245">Disk Space Requirements</span></span>  
 <span data-ttu-id="0243c-246">데이터베이스 스냅샷은 디스크 공간을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-246">Database snapshots consume disk space.</span></span> <span data-ttu-id="0243c-247">데이터베이스 스냅샷이 디스크 공간을 모두 소모하면 스냅샷이 주의 대상으로 표시되어 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-247">If a database snapshot runs out of disk space, it is marked as suspect and must be dropped.</span></span> <span data-ttu-id="0243c-248">그러나 원본 데이터베이스는 영향을 받지 않으며 정상적으로 동작이 계속됩니다. 그러나 데이터베이스의 전체 복사본과 비교할 때 스냅샷은 공간을 매우 효율적으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-248">(The source database, however, is not affected; actions on it continue normally.) Compared to a full copy of a database, however, snapshots are highly space efficient.</span></span> <span data-ttu-id="0243c-249">스냅샷은 사용 기간 동안 변경되는 페이지를 스토리지할 수 있는 공간만 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-249">A snapshot requires only enough storage for the pages that change during its lifetime.</span></span> <span data-ttu-id="0243c-250">일반적으로 스냅샷은 제한된 시간 동안 보관되므로 크기는 중요한 문제가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-250">Generally, snapshots are kept for a limited time, so their size is not a major concern.</span></span>  
  
 <span data-ttu-id="0243c-251">그러나 스냅샷을 오래 보관할수록 사용 가능한 공간을 모두 소모할 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-251">The longer you keep a snapshot, however, the more likely it is to use up available space.</span></span> <span data-ttu-id="0243c-252">스파스 파일이 커질 수 있는 최대 크기는 스냅샷을 만든 시점의 해당 원본 데이터베이스 파일의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-252">The maximum size to which a sparse file can grow is the size of the corresponding source database file at the time of the snapshot creation.</span></span>  
  
 <span data-ttu-id="0243c-253">데이터베이스 스냅샷이 디스크 공간을 모두 소모한 경우 스냅샷을 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-253">If a database snapshot runs out of disk space, it must be deleted (dropped).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0243c-254">파일 공간을 제외하고 데이터베이스 스냅샷은 대략 데이터베이스와 같은 양의 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-254">Except for file space, a database snapshot consumes roughly as many resources as a database.</span></span>  
  
###  <a name="database-snapshots-with-offline-filegroups"></a><a name="OfflineFGs"></a> <span data-ttu-id="0243c-255">오프라인 파일 그룹의 데이터베이스 스냅샷</span><span class="sxs-lookup"><span data-stu-id="0243c-255">Database Snapshots with Offline Filegroups</span></span>  
 <span data-ttu-id="0243c-256">원본 데이터베이스의 오프라인 파일 그룹은 다음 작업을 수행하려 할 때 데이터베이스 스냅샷에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-256">Offline filegroups in the source database affect database snapshots when you try to do any of the following:</span></span>  
  
-   <span data-ttu-id="0243c-257">스냅샷 만들기</span><span class="sxs-lookup"><span data-stu-id="0243c-257">Create a snapshot</span></span>  
  
     <span data-ttu-id="0243c-258">원본 데이터베이스에 하나 이상의 오프라인 파일 그룹이 있는 경우 오프라인 파일 그룹의 스냅샷 만들기가 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-258">When a source database has one or more offline filegroups, snapshot creation succeeds with the filegroups offline.</span></span> <span data-ttu-id="0243c-259">오프라인 파일 그룹의 경우 스파스 파일이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-259">Sparse files are not created for the offline filegroups.</span></span>  
  
-   <span data-ttu-id="0243c-260">파일 그룹을 오프라인 상태로 만들기</span><span class="sxs-lookup"><span data-stu-id="0243c-260">Take a filegroup offline</span></span>  
  
     <span data-ttu-id="0243c-261">원본 데이터베이스에서 파일 그룹을 오프라인 상태로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-261">You can take a file offline in the source database.</span></span> <span data-ttu-id="0243c-262">그러나 스냅샷을 만들 때 온라인 상태였던 파일 그룹은 데이터베이스 스냅샷에서 온라인 상태를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-262">However, the filegroup remains online in database snapshots if it was online when the snapshot was created.</span></span> <span data-ttu-id="0243c-263">스냅샷을 만든 후 쿼리한 데이터가 변경된 경우 스냅샷에서 해당 원본 데이터 페이지에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-263">If the queried data has changed since snapshot creation, the original data page will be accessible in the snapshot.</span></span> <span data-ttu-id="0243c-264">그러나 스냅샷을 사용하여 파일 그룹의 수정되지 않은 데이터에 액세스하는 쿼리는 입출력 오류로 인해 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-264">However, queries that use the snapshot to access unmodified data in the filegroup are likely to fail with input/output (I/O) errors.</span></span>  
  
-   <span data-ttu-id="0243c-265">파일 그룹을 온라인 상태로 만들기</span><span class="sxs-lookup"><span data-stu-id="0243c-265">Bring a filegroup online</span></span>  
  
     <span data-ttu-id="0243c-266">데이터베이스 스냅샷이 있는 데이터베이스의 파일 그룹은 온라인 상태로 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-266">You cannot bring a filegroup online in a database that has any database snapshots.</span></span> <span data-ttu-id="0243c-267">스냅샷 생성 시 파일 그룹이 오프라인 상태이거나 데이터베이스 스냅샷이 있는 동안 오프라인 상태로 만들면 이 파일 그룹은 계속 오프라인 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-267">If a filegroup is offline at the time of snapshot creation or is taken offline while a database snapshot exists, the filegroup remains offline.</span></span> <span data-ttu-id="0243c-268">이는 파일을 다시 온라인 상태로 만들려면 파일을 복원해야 하는데, 데이터베이스에 데이터베이스 스냅샷이 있을 경우 복원할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-268">This is because bringing a file back online involves restoring it, which is not possible if a database snapshot exists on the database.</span></span>  
  
-   <span data-ttu-id="0243c-269">원본 데이터베이스를 스냅샷으로 되돌리기</span><span class="sxs-lookup"><span data-stu-id="0243c-269">Revert the source database to the snapshot</span></span>  
  
     <span data-ttu-id="0243c-270">원본 데이터베이스를 데이터베이스 스냅샷으로 되돌리려면 스냅샷을 만들 때 오프라인 상태였던 파일 그룹을 제외하고 모든 파일 그룹이 온라인 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0243c-270">Reverting a source database to a database snapshot requires that all of the filegroups are online except for filegroups that were offline when the snapshot was created.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="0243c-271">관련 작업</span><span class="sxs-lookup"><span data-stu-id="0243c-271">Related Tasks</span></span>  
  
-   [<span data-ttu-id="0243c-272">데이터베이스 스냅샷 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0243c-272">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="0243c-273">데이터베이스 스냅샷 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0243c-273">View a Database Snapshot &#40;SQL Server&#41;</span></span>](view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="0243c-274">데이터베이스 스냅샷 스파스 파일의 크기 보기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0243c-274">View the Size of the Sparse File of a Database Snapshot &#40;Transact-SQL&#41;</span></span>](view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="0243c-275">데이터베이스를 데이터베이스 스냅샷으로 되돌리기</span><span class="sxs-lookup"><span data-stu-id="0243c-275">Revert a Database to a Database Snapshot</span></span>](revert-a-database-to-a-database-snapshot.md)  
  
-   [<span data-ttu-id="0243c-276">데이터베이스 스냅샷 삭제&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0243c-276">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="0243c-277">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0243c-277">See Also</span></span>  
 [<span data-ttu-id="0243c-278">데이터베이스 미러링 및 데이터베이스 스냅샷&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0243c-278">Database Mirroring and Database Snapshots &#40;SQL Server&#41;</span></span>](database-snapshots-sql-server.md)  
  
  
