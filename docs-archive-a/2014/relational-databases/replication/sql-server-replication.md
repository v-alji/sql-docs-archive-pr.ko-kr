---
title: SQL Server 복제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], about
- replication [SQL Server]
ms.assetid: 3a5f4592-3c61-4b4d-9ceb-39716aeeba41
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e51f45e06939971ada6166fb977c787ad0354926
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646308"
---
# <a name="sql-server-replication"></a><span data-ttu-id="2e811-102">SQL Server 복제</span><span class="sxs-lookup"><span data-stu-id="2e811-102">SQL Server Replication</span></span>
  <span data-ttu-id="2e811-103">복제는 한 데이터베이스에서 다른 데이터베이스로 데이터와 데이터베이스 개체를 복사 및 배포한 다음 데이터베이스 간에 동기화를 수행하여 일관성을 유지하는 일련의 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="2e811-103">Replication is a set of technologies for copying and distributing data and database objects from one database to another and then synchronizing between databases to maintain consistency.</span></span> <span data-ttu-id="2e811-104">복제를 사용하면 LAN 및 WAN, 전화 접속 연결, 무선 연결 및 인터넷을 통해 데이터를 여러 다른 위치로 배포하고 원격 또는 모바일 사용자에게 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e811-104">Using replication, you can distribute data to different locations and to remote or mobile users over local and wide area networks, dial-up connections, wireless connections, and the Internet.</span></span>  
  
 <span data-ttu-id="2e811-105">트랜잭션 복제는 일반적으로 확장성 및 가용성 향상, 데이터 웨어하우징 및 보고, 여러 사이트의 데이터 통합, 다른 유형의 데이터 통합, 일괄 처리 작업 오프로드 등을 포함하여 높은 처리량이 필요한 서버 간 시나리오에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e811-105">Transactional replication is typically used in server-to-server scenarios that require high throughput, including: improving scalability and availability; data warehousing and reporting; integrating data from multiple sites; integrating heterogeneous data; and offloading batch processing.</span></span> <span data-ttu-id="2e811-106">병합 복제는 주로 데이터 충돌 가능성이 있는 모바일 애플리케이션이나 분산 서버 애플리케이션에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e811-106">Merge replication is primarily designed for mobile applications or distributed server applications that have possible data conflicts.</span></span> <span data-ttu-id="2e811-107">일반적인 시나리오에는 모바일 사용자와 데이터 교환, 소비자 POS(Point of Sale) 애플리케이션, 여러 사이트의 데이터 통합 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e811-107">Common scenarios include: exchanging data with mobile users; consumer point of sale (POS) applications; and integration of data from multiple sites.</span></span> <span data-ttu-id="2e811-108">스냅샷 복제는 트랜잭션 및 병합 복제에 초기 데이터 집합을 제공하는 데 사용되며 전체 데이터 새로 고침이 적합한 경우에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e811-108">Snapshot replication is used to provide the initial data set for transactional and merge replication; it can also be used when complete refreshes of data are appropriate.</span></span> <span data-ttu-id="2e811-109">이러한 3가지 복제 유형을 통해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 엔터프라이즈 데이터를 동기화하는 강력하고 유연성 있는 시스템을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2e811-109">With these three types of replication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides a powerful and flexible system for synchronizing data across your enterprise.</span></span> <span data-ttu-id="2e811-110">SQLCE 3.5 및 SQLCE 4.0에 대한 복제는 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] 및 [!INCLUDE[win8](../../includes/win8-md.md)]에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e811-110">Replication to SQLCE 3.5 and SQLCE 4.0 is supported on both [!INCLUDE[win8srv](../../includes/win8srv-md.md)] and [!INCLUDE[win8](../../includes/win8-md.md)].</span></span>  
  
 <span data-ttu-id="2e811-111">복제 대신 Microsoft Sync Framework를 사용하여 데이터베이스를 동기화할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e811-111">As an alternative to replication, you can synchronize databases by using Microsoft Sync Framework.</span></span> <span data-ttu-id="2e811-112">Sync Framework에는 구성 요소뿐 아니라 SQL Server, SQL Server Express, SQL Server Compact, SQL Azure 데이터베이스 간의 동기화를 용이하게 하는 유연하고 직관적인 API를 포함하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e811-112">Sync Framework includes components and an intuitive and flexible API that make it easy to synchronize among SQL Server, SQL Server Express, SQL Server Compact, and SQL Azure databases.</span></span> <span data-ttu-id="2e811-113">또한 Sync Framework는 SQL Server 데이터베이스와 ADO.NET 호환 기타 데이터베이스 간에 동기화하도록 조정할 수 있는 클래스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2e811-113">Sync Framework also includes classes that can be adapted to synchronize between a SQL Server database and any other database that is compatible with ADO.NET.</span></span> <span data-ttu-id="2e811-114">Sync Framework 데이터베이스 동기화 구성 요소에 대한 자세한 설명서는 [데이터베이스 동기화](https://go.microsoft.com/fwlink/?LinkId=209079)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2e811-114">For detailed documentation of the Sync Framework database synchronization components, see [Synchronizing Databases](https://go.microsoft.com/fwlink/?LinkId=209079).</span></span> <span data-ttu-id="2e811-115">Sync Framework에 대한 개요는 [Microsoft Sync Framework 개발자 센터](https://go.microsoft.com/fwlink/?LinkId=209078)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2e811-115">For an overview of Sync Framework, see [Microsoft Sync Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=209078).</span></span> <span data-ttu-id="2e811-116">Sync Framework와 병합 복제 간의 비교는 [데이터베이스 동기화 개요](https://msdn.microsoft.com/library/bb902818\(SQL.110\).aspx)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2e811-116">For a comparison between Sync Framework and Merge Replication, see [Synchronizing Databases Overview](https://msdn.microsoft.com/library/bb902818\(SQL.110\).aspx)</span></span>  
  

## <a name="whats-new"></a><span data-ttu-id="2e811-117">새로운 기능</span><span class="sxs-lookup"><span data-stu-id="2e811-117">What's new</span></span> 
- <span data-ttu-id="2e811-118">SQL Server 2017은 중요한 새로운 기능을 SQL Server 복제에 도입하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2e811-118">SQL Server 2017 has not introduced significant new features to SQL Server replication.</span></span> 
- <span data-ttu-id="2e811-119">SQL Server 2016은 중요한 새로운 기능을 SQL Server 복제에 도입하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2e811-119">SQL Server 2016 has not introduced significant new features to SQL Server replication.</span></span> 

<span data-ttu-id="2e811-120">이전 버전과의 호환성 정보는 [복제의 이전 버전과의 호환성](replication-backward-compatibility.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2e811-120">For backward compatibility information see, [Replication Backward Compatibility](replication-backward-compatibility.md)</span></span> 


 ## <a name="replication-security"></a><span data-ttu-id="2e811-121">복제 보안</span><span class="sxs-lookup"><span data-stu-id="2e811-121">Replication security</span></span>
  
-   [<span data-ttu-id="2e811-122">복제 보안 설정 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="2e811-122">View and Modify Replication Security Settings</span></span>](security/view-and-modify-replication-security-settings.md)  
-   [<span data-ttu-id="2e811-123">게시 액세스 목록에서 로그인 관리</span><span class="sxs-lookup"><span data-stu-id="2e811-123">Manage Logins in the Publication Access List</span></span>](security/manage-logins-in-the-publication-access-list.md)  
  
## <a name="publishing-and-distribution"></a><span data-ttu-id="2e811-124">게시 및 배포</span><span class="sxs-lookup"><span data-stu-id="2e811-124">Publishing and Distribution</span></span>  
  
-   [<span data-ttu-id="2e811-125">게시 및 배포 구성</span><span class="sxs-lookup"><span data-stu-id="2e811-125">Configure Publishing and Distribution</span></span>](configure-publishing-and-distribution.md)   
-   [<span data-ttu-id="2e811-126">게시 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="2e811-126">View and Modify Publication Properties</span></span>](publish/view-and-modify-publication-properties.md)   
-   [<span data-ttu-id="2e811-127">게시 및 배포 해제</span><span class="sxs-lookup"><span data-stu-id="2e811-127">Disable Publishing and Distribution</span></span>](disable-publishing-and-distribution.md)  
  
## <a name="publications-and-articles"></a><span data-ttu-id="2e811-128">게시 및 문서</span><span class="sxs-lookup"><span data-stu-id="2e811-128">Publications and Articles</span></span> 
  
-   [<span data-ttu-id="2e811-129">게시 만들기</span><span class="sxs-lookup"><span data-stu-id="2e811-129">Create a Publication</span></span>](publish/create-a-publication.md)    
-   [<span data-ttu-id="2e811-130">아티클 정의</span><span class="sxs-lookup"><span data-stu-id="2e811-130">Define an Article</span></span>](publish/define-an-article.md)   
-   [<span data-ttu-id="2e811-131">게시 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="2e811-131">View and Modify Publication Properties</span></span>](publish/view-and-modify-publication-properties.md)   
-   [<span data-ttu-id="2e811-132">아티클 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="2e811-132">View and Modify Article Properties</span></span>](publish/view-and-modify-article-properties.md)    
-   [<span data-ttu-id="2e811-133">게시 삭제</span><span class="sxs-lookup"><span data-stu-id="2e811-133">Delete a Publication</span></span>](publish/delete-a-publication.md)   
-   [<span data-ttu-id="2e811-134">아티클 삭제</span><span class="sxs-lookup"><span data-stu-id="2e811-134">Delete an Article</span></span>](publish/delete-an-article.md)    
-   [<span data-ttu-id="2e811-135">Oracle 데이터베이스에서 게시 만들기</span><span class="sxs-lookup"><span data-stu-id="2e811-135">Create a Publication from an Oracle Database</span></span>](publish/create-a-publication-from-an-oracle-database.md)   
-   [<span data-ttu-id="2e811-136">구독에 대한 만료 기간 설정</span><span class="sxs-lookup"><span data-stu-id="2e811-136">Set the Expiration Period for Subscriptions</span></span>](publish/set-the-expiration-period-for-subscriptions.md)  
-   [<span data-ttu-id="2e811-137">스키마 옵션 지정</span><span class="sxs-lookup"><span data-stu-id="2e811-137">Specify Schema Options</span></span>](publish/specify-schema-options.md)  
-   [<span data-ttu-id="2e811-138">스키마 변경 내용 복제</span><span class="sxs-lookup"><span data-stu-id="2e811-138">Replicate Schema Changes</span></span>](publish/replicate-schema-changes.md)    
-   [<span data-ttu-id="2e811-139">ID 열 관리</span><span class="sxs-lookup"><span data-stu-id="2e811-139">Manage Identity Columns</span></span>](publish/manage-identity-columns.md)   
-   [<span data-ttu-id="2e811-140">병합 게시에 대한 호환성 수준 설정</span><span class="sxs-lookup"><span data-stu-id="2e811-140">Set the Compatibility Level for Merge Publications</span></span>](publish/set-the-compatibility-level-for-merge-publications.md)  
  
### <a name="snapshot-options"></a><span data-ttu-id="2e811-141">Snapshot Options</span><span class="sxs-lookup"><span data-stu-id="2e811-141">Snapshot Options</span></span>  
  
-   [<span data-ttu-id="2e811-142">스냅샷 속성 구성</span><span class="sxs-lookup"><span data-stu-id="2e811-142">Configure Snapshot Properties</span></span>](publish/configure-snapshot-properties-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="2e811-143">FTP를 통해 스냅샷 배달</span><span class="sxs-lookup"><span data-stu-id="2e811-143">Deliver a Snapshot Through FTP</span></span>](publish/deliver-a-snapshot-through-ftp.md) 
  
### <a name="filter-data"></a><span data-ttu-id="2e811-144">데이터 필터링</span><span class="sxs-lookup"><span data-stu-id="2e811-144">Filter Data</span></span>  
  
-   [<span data-ttu-id="2e811-145">열 필터 정의 및 수정</span><span class="sxs-lookup"><span data-stu-id="2e811-145">Define and Modify a Column Filter</span></span>](publish/define-and-modify-a-column-filter.md)    
-   [<span data-ttu-id="2e811-146">정적 행 필터 정의 및 수정</span><span class="sxs-lookup"><span data-stu-id="2e811-146">Define and Modify a Static Row Filter</span></span>](publish/define-and-modify-a-static-row-filter.md)    
-   [<span data-ttu-id="2e811-147">병합 아티클에 대한 매개 변수가 있는 행 필터 정의 및 수정</span><span class="sxs-lookup"><span data-stu-id="2e811-147">Define and Modify a Parameterized Row Filter for a Merge Article</span></span>](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)    
-   [<span data-ttu-id="2e811-148">매개 변수가 있는 행 필터 최적화</span><span class="sxs-lookup"><span data-stu-id="2e811-148">Optimize Parameterized Row Filters</span></span>](publish/optimize-parameterized-row-filters.md)    
-   [<span data-ttu-id="2e811-149">병합 아티클 사이에서 조인 필터 정의 및 수정</span><span class="sxs-lookup"><span data-stu-id="2e811-149">Define and Modify a Join Filter Between Merge Articles</span></span>](publish/define-and-modify-a-join-filter-between-merge-articles.md)  
  
### <a name="transactional-replication-options"></a><span data-ttu-id="2e811-150">트랜잭션 복제 옵션</span><span class="sxs-lookup"><span data-stu-id="2e811-150">Transactional Replication Options</span></span>  
  
-   [<span data-ttu-id="2e811-151">트랜잭션 아티클의 데이터 변경 내용을 전파하는 방법 설정</span><span class="sxs-lookup"><span data-stu-id="2e811-151">Set the Propagation Method for Data Changes to Transactional Articles</span></span>](publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md)    
-   [<span data-ttu-id="2e811-152">트랜잭션 게시에 대해 업데이트할 수 있는 구독 설정</span><span class="sxs-lookup"><span data-stu-id="2e811-152">Enable Updating Subscriptions for Transactional Publications</span></span>](publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
### <a name="merge-replication-options"></a><span data-ttu-id="2e811-153">병합 복제 옵션</span><span class="sxs-lookup"><span data-stu-id="2e811-153">Merge Replication Options</span></span>  
  
-   [<span data-ttu-id="2e811-154">병합 테이블 아티클 간의 논리적 레코드 관계 정의</span><span class="sxs-lookup"><span data-stu-id="2e811-154">Define a Logical Record Relationship Between Merge Table Articles</span></span>](publish/define-a-logical-record-relationship-between-merge-table-articles.md)    
-   [<span data-ttu-id="2e811-155">병합 복제 속성 지정</span><span class="sxs-lookup"><span data-stu-id="2e811-155">Specify Merge replication properties</span></span>](publish/specify-merge-replication-properties.md)    
-   [<span data-ttu-id="2e811-156">병합 아티클 해결 프로그램 지정</span><span class="sxs-lookup"><span data-stu-id="2e811-156">Specify a Merge Article Resolver</span></span>](publish/specify-a-merge-article-resolver.md)    

  
## <a name="manage-subscriptions"></a><span data-ttu-id="2e811-157">구독 관리</span><span class="sxs-lookup"><span data-stu-id="2e811-157">Manage Subscriptions</span></span>  
  
-   [<span data-ttu-id="2e811-158">끌어오기 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="2e811-158">Create a Pull Subscription</span></span>](create-a-pull-subscription.md)    
-   [<span data-ttu-id="2e811-159">끌어오기 구독 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="2e811-159">View and Modify Pull Subscription Properties</span></span>](view-and-modify-pull-subscription-properties.md)    
-   [<span data-ttu-id="2e811-160">끌어오기 구독 삭제</span><span class="sxs-lookup"><span data-stu-id="2e811-160">Delete a Pull Subscription</span></span>](delete-a-pull-subscription.md)    
-   [<span data-ttu-id="2e811-161">밀어넣기 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="2e811-161">Create a Push Subscription</span></span>](create-a-push-subscription.md)   
-   [<span data-ttu-id="2e811-162">밀어넣기 구독 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="2e811-162">View and Modify Push Subscription Properties</span></span>](view-and-modify-push-subscription-properties.md)   
-   [<span data-ttu-id="2e811-163">밀어넣기 구독 삭제</span><span class="sxs-lookup"><span data-stu-id="2e811-163">Delete a Push Subscription</span></span>](delete-a-push-subscription.md)   
-   [<span data-ttu-id="2e811-164">동기화 일정 지정</span><span class="sxs-lookup"><span data-stu-id="2e811-164">Specify Synchronization Schedules</span></span>](specify-synchronization-schedules.md)    
-   [<span data-ttu-id="2e811-165">트랜잭션 게시에 대해 업데이트할 수 있는 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="2e811-165">Create an Updatable Subscription to a Transactional Publication</span></span>](publish/create-an-updatable-subscription-to-a-transactional-publication.md)  
-   [<span data-ttu-id="2e811-166">SQL Server 이외 구독자에 대한 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="2e811-166">Create a Subscription for a Non-SQL Server Subscriber</span></span>](create-a-subscription-for-a-non-sql-server-subscriber.md)  
  
## <a name="synchronize-subscriptions"></a><span data-ttu-id="2e811-167">구독 동기화</span><span class="sxs-lookup"><span data-stu-id="2e811-167">Synchronize Subscriptions</span></span>  
  
-   [<span data-ttu-id="2e811-168">초기 스냅샷 만들기 및 적용</span><span class="sxs-lookup"><span data-stu-id="2e811-168">Create and Apply the Initial Snapshot</span></span>](create-and-apply-the-initial-snapshot.md)   
-   [<span data-ttu-id="2e811-169">매개 변수가 있는 필터로 병합 게시에 대한 스냅샷 만들기</span><span class="sxs-lookup"><span data-stu-id="2e811-169">Create a Snapshot for a Merge Publication with Parameterized Filters</span></span>](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)    
-   [<span data-ttu-id="2e811-170">트랜잭션 구독을 백업에서 초기화</span><span class="sxs-lookup"><span data-stu-id="2e811-170">Initialize a Transactional Subscription from a Backup</span></span>](initialize-a-transactional-subscription-from-a-backup.md)    
-   [<span data-ttu-id="2e811-171">수동 구독 초기화</span><span class="sxs-lookup"><span data-stu-id="2e811-171">Initialize a Subscription Manually</span></span>](initialize-a-subscription-manually.md)    
-   [<span data-ttu-id="2e811-172">끌어오기 구독 동기화</span><span class="sxs-lookup"><span data-stu-id="2e811-172">Synchronize a Pull Subscription</span></span>](synchronize-a-pull-subscription.md)    
-   [<span data-ttu-id="2e811-173">밀어넣기 구독 동기화</span><span class="sxs-lookup"><span data-stu-id="2e811-173">Synchronize a Push Subscription</span></span>](synchronize-a-push-subscription.md)   
-   [<span data-ttu-id="2e811-174">구독 다시 초기화</span><span class="sxs-lookup"><span data-stu-id="2e811-174">Reinitialize a Subscription</span></span>](reinitialize-a-subscription.md)    
-   [<span data-ttu-id="2e811-175">동기화 중 스크립트 실행</span><span class="sxs-lookup"><span data-stu-id="2e811-175">Execute Scripts During Synchronization</span></span>](execute-scripts-during-synchronization-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="2e811-176">병합 아티클에 대한 비즈니스 논리 처리기 구현</span><span class="sxs-lookup"><span data-stu-id="2e811-176">Implement a Business Logic Handler for a Merge Article</span></span>](implement-a-business-logic-handler-for-a-merge-article.md)  
-   [<span data-ttu-id="2e811-177">비즈니스 논리 처리기 디버깅&#40;복제 프로그래밍&#41;</span><span class="sxs-lookup"><span data-stu-id="2e811-177">Debug a Business Logic Handler &#40;Replication Programming&#41;</span></span>](debug-a-business-logic-handler-replication-programming.md)    
-   [<span data-ttu-id="2e811-178">동기화 하는 동안 트리거 및 제약 조건의 동작 제어</span><span class="sxs-lookup"><span data-stu-id="2e811-178">Control the Behavior of Triggers and Constraints During Synchronization</span></span>](control-behavior-of-triggers-and-constraints-in-synchronization.md)    
-   [<span data-ttu-id="2e811-179">병합 아티클용 사용자 지정 충돌 해결 프로그램 구현</span><span class="sxs-lookup"><span data-stu-id="2e811-179">Implement a Custom Conflict Resolver for a Merge Article</span></span>](implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="administeration"></a><span data-ttu-id="2e811-180">Administeration</span><span class="sxs-lookup"><span data-stu-id="2e811-180">Administeration</span></span> 
  
-   [<span data-ttu-id="2e811-181">복제 에이전트 프로필 작업</span><span class="sxs-lookup"><span data-stu-id="2e811-181">Work with Replication Agent Profiles</span></span>](agents/work-with-replication-agent-profiles.md)   
-   [<span data-ttu-id="2e811-182">구독자에서 데이터 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="2e811-182">Validate Data at the Subscriber</span></span>](validate-data-at-the-subscriber.md)    
-   [<span data-ttu-id="2e811-183">매개 변수가 있는 필터로 병합 게시에 대한 파티션 관리</span><span class="sxs-lookup"><span data-stu-id="2e811-183">Manage Partitions for a Merge Publication with Parameterized Filters</span></span>](publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)    
-   [<span data-ttu-id="2e811-184">병합 게시에서 데이터를 테이블로 대량 로드</span><span class="sxs-lookup"><span data-stu-id="2e811-184">Bulk-Load Data into Tables in a Merge Publication</span></span>](bulk-load-data-into-tables-in-a-merge-publication.md)    
-   [<span data-ttu-id="2e811-185">병합 메타 데이터 정리</span><span class="sxs-lookup"><span data-stu-id="2e811-185">Clean Up Merge Metadata</span></span>](administration/clean-up-merge-metadata-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="2e811-186">병합 아티클에 대해 더미 업데이트 수행</span><span class="sxs-lookup"><span data-stu-id="2e811-186">Perform a Dummy Update for a Merge Article</span></span>](administration/perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="2e811-187">배포 데이터베이스에서 복제 된 명령 및 기타 정보 보기</span><span class="sxs-lookup"><span data-stu-id="2e811-187">View Replicated Commands and Other Information in the Distribution Database</span></span>](monitor/view-replicated-commands-and-information-in-distribution-database.md)    
-   [<span data-ttu-id="2e811-188">트랜잭션 복제에 대해 통합 백업 사용</span><span class="sxs-lookup"><span data-stu-id="2e811-188">Enable Coordinated Backups for Transactional Replication</span></span>](administration/enable-coordinated-backups-for-transactional-replication.md)   
-   [<span data-ttu-id="2e811-189">피어 투 피어 토폴로지 관리</span><span class="sxs-lookup"><span data-stu-id="2e811-189">Administer a Peer-to-Peer Topology</span></span>](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="2e811-190">복제 토폴로지 정지</span><span class="sxs-lookup"><span data-stu-id="2e811-190">Quiesce a Replication Topology</span></span>](administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="2e811-191">Oracle 게시자에 대한 트랜잭션 집합 작업 구성</span><span class="sxs-lookup"><span data-stu-id="2e811-191">Configure the Transaction Set Job for an Oracle Publisher</span></span>](administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
-   [<span data-ttu-id="2e811-192">복제 스크립트 업그레이드</span><span class="sxs-lookup"><span data-stu-id="2e811-192">Upgrade Replication Scripts</span></span>](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)  
  
## <a name="monitor"></a><span data-ttu-id="2e811-193">모니터</span><span class="sxs-lookup"><span data-stu-id="2e811-193">Monitor</span></span>
  
-   [<span data-ttu-id="2e811-194">비관리자의 복제 모니터 사용 허용</span><span class="sxs-lookup"><span data-stu-id="2e811-194">Allow Non-Administrators to Use Replication Monitor</span></span>](monitor/allow-non-administrators-to-use-replication-monitor.md)    
-   [<span data-ttu-id="2e811-195">프로그래밍 방식으로 복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="2e811-195">Programmatically Monitor Replication</span></span>](monitor/programmatically-monitor-replication.md)    
-   [<span data-ttu-id="2e811-196">배포 데이터베이스에서 복제 된 명령 및 기타 정보 보기</span><span class="sxs-lookup"><span data-stu-id="2e811-196">View Replicated Commands and Other Information in the Distribution Database</span></span>](monitor/view-replicated-commands-and-information-in-distribution-database.md)    
-   [<span data-ttu-id="2e811-197">병합 게시에 대한 충돌 정보 보기</span><span class="sxs-lookup"><span data-stu-id="2e811-197">View Conflict Information for Merge Publications</span></span>](view-conflict-information-for-merge-publications.md) 
-   [<span data-ttu-id="2e811-198">트랜잭션 복제에 대한 대기 시간 측정 및 연결 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="2e811-198">Measure Latency and Validate Connections for Transactional Replication</span></span>](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  