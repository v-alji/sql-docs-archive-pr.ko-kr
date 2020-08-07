---
title: 업데이트된 백업이 필요한 일반 동작 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- recovery [SQL Server replication], actions requiring a backup
- restoring [SQL Server replication], actions requiring a backup
- backups [SQL Server replication], actions requiring a backup
ms.assetid: a5975bf4-183e-42e3-b7d1-ad02f89d2e1d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3eb10bdca8ee188f7b322a46665c38129d57052b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729355"
---
# <a name="common-actions-requiring-an-updated-backup"></a><span data-ttu-id="af2a4-102">업데이트된 백업이 필요한 일반 동작</span><span class="sxs-lookup"><span data-stu-id="af2a4-102">Common Actions Requiring an Updated Backup</span></span>
  <span data-ttu-id="af2a4-103">정기적인 로그 백업을 수행할 경우 모든 복제 관련 변경 내용은 로그 백업에 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2a4-103">If you perform regular log backups, any replication-related changes should be captured in the log backups.</span></span> <span data-ttu-id="af2a4-104">로그 백업을 수행하지 않는 경우 복제 스키마 또는 토폴로지에 변경 작업을 수행한 후 게시, 배포, 구독, **msdb**및 **master** 데이터베이스 백업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="af2a4-104">If you don't perform log backups, perform a backup of the publication, distribution, subscription, **msdb**, and **master** databases after making modifications to your replication schema or topology.</span></span>  
  
## <a name="publication-database"></a><span data-ttu-id="af2a4-105">게시 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="af2a4-105">Publication Database</span></span>  
 <span data-ttu-id="af2a4-106">다음 작업 후 게시 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="af2a4-106">Backup the publication database after:</span></span>  
  
-   <span data-ttu-id="af2a4-107">새 게시 만들기</span><span class="sxs-lookup"><span data-stu-id="af2a4-107">Creating new publications.</span></span>  
  
-   <span data-ttu-id="af2a4-108">필터링을 포함한 게시 속성 변경</span><span class="sxs-lookup"><span data-stu-id="af2a4-108">Changing any publication property, including filtering.</span></span>  
  
-   <span data-ttu-id="af2a4-109">기존 게시에 아티클 추가</span><span class="sxs-lookup"><span data-stu-id="af2a4-109">Adding articles to an existing publication.</span></span>  
  
-   <span data-ttu-id="af2a4-110">구독을 게시 차원에서 다시 초기화</span><span class="sxs-lookup"><span data-stu-id="af2a4-110">Performing a publication-wide reinitialization of subscriptions.</span></span>  
  
-   <span data-ttu-id="af2a4-111">게시된 테이블의 스키마 변경</span><span class="sxs-lookup"><span data-stu-id="af2a4-111">Making a schema change on a published table.</span></span>  
  
-   <span data-ttu-id="af2a4-112">[sp_addscriptexec&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql)를 사용한 요청 시 스크립트 수행</span><span class="sxs-lookup"><span data-stu-id="af2a4-112">Performing on-demand script execution with [sp_addscriptexec &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql).</span></span>  
  
-   <span data-ttu-id="af2a4-113">아티클 속성 변경</span><span class="sxs-lookup"><span data-stu-id="af2a4-113">Changing any article property.</span></span>  
  
-   <span data-ttu-id="af2a4-114">게시 삭제</span><span class="sxs-lookup"><span data-stu-id="af2a4-114">Dropping any publications.</span></span>  
  
-   <span data-ttu-id="af2a4-115">아티클 삭제</span><span class="sxs-lookup"><span data-stu-id="af2a4-115">Dropping any articles.</span></span>  
  
-   <span data-ttu-id="af2a4-116">복제 해제</span><span class="sxs-lookup"><span data-stu-id="af2a4-116">Disabling replication.</span></span>  
  
## <a name="distribution-database"></a><span data-ttu-id="af2a4-117">배포 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="af2a4-117">Distribution Database</span></span>  
 <span data-ttu-id="af2a4-118">다음 작업 후 배포 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="af2a4-118">Backup the distribution database after:</span></span>  
  
-   <span data-ttu-id="af2a4-119">복제 에이전트 프로필 만들기 또는 수정</span><span class="sxs-lookup"><span data-stu-id="af2a4-119">Creating or modifying replication agent profiles.</span></span>  
  
-   <span data-ttu-id="af2a4-120">복제 에이전트 프로필 매개 변수 수정</span><span class="sxs-lookup"><span data-stu-id="af2a4-120">Modifying replication agent profile parameters.</span></span>  
  
-   <span data-ttu-id="af2a4-121">밀어넣기 구독의 일정을 비롯한 복제 에이전트 속성 변경</span><span class="sxs-lookup"><span data-stu-id="af2a4-121">Changing the replication agent properties (including schedules) for any push subscriptions.</span></span>  
  
-   <span data-ttu-id="af2a4-122">ID 범위 자동 관리 기능으로 새로운 범위의 ID 지정</span><span class="sxs-lookup"><span data-stu-id="af2a4-122">A new range of identities is assigned by the automatic identity range management feature.</span></span>  
  
## <a name="subscription-database"></a><span data-ttu-id="af2a4-123">구독 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="af2a4-123">Subscription Database</span></span>  
 <span data-ttu-id="af2a4-124">다음 작업 후 구독 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="af2a4-124">Backup the subscription database after:</span></span>  
  
-   <span data-ttu-id="af2a4-125">구독 속성 변경</span><span class="sxs-lookup"><span data-stu-id="af2a4-125">Changing any subscription property.</span></span>  
  
-   <span data-ttu-id="af2a4-126">게시자에서 병합 구독 속성 변경</span><span class="sxs-lookup"><span data-stu-id="af2a4-126">Changing the priority for a merge subscription at the Publisher.</span></span>  
  
-   <span data-ttu-id="af2a4-127">구독 삭제</span><span class="sxs-lookup"><span data-stu-id="af2a4-127">Dropping any subscriptions.</span></span>  
  
-   <span data-ttu-id="af2a4-128">복제 해제</span><span class="sxs-lookup"><span data-stu-id="af2a4-128">Disabling replication.</span></span>  
  
## <a name="msdb-database"></a><span data-ttu-id="af2a4-129">msdb 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="af2a4-129">msdb Database</span></span>  
 <span data-ttu-id="af2a4-130">다음 작업 후 해당 노드에서 **msdb** 시스템 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="af2a4-130">Backup the **msdb** system database at the appropriate node after:</span></span>  
  
-   <span data-ttu-id="af2a4-131">복제 활성화 또는 비활성화</span><span class="sxs-lookup"><span data-stu-id="af2a4-131">Enabling or disabling replication.</span></span>  
  
-   <span data-ttu-id="af2a4-132">배포자에서 배포 데이터베이스 추가 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="af2a4-132">Adding or dropping a distribution database (at the Distributor).</span></span>  
  
-   <span data-ttu-id="af2a4-133">게시자에서 데이터베이스에 게시 활성화 또는 비활성화</span><span class="sxs-lookup"><span data-stu-id="af2a4-133">Enabling or disabling a database for publishing (at the Publisher).</span></span>  
  
-   <span data-ttu-id="af2a4-134">배포자에서 복제 에이전트 프로필 만들기 또는 수정</span><span class="sxs-lookup"><span data-stu-id="af2a4-134">Creating or modifying replication agent profiles (at the Distributor).</span></span>  
  
-   <span data-ttu-id="af2a4-135">배포자에서 복제 에이전트 프로필 매개 변수 수정</span><span class="sxs-lookup"><span data-stu-id="af2a4-135">Modifying any replication agent profile parameters (at the Distributor).</span></span>  
  
-   <span data-ttu-id="af2a4-136">배포자에서 밀어넣기 구독의 일정을 비롯한 복제 에이전트 속성 변경</span><span class="sxs-lookup"><span data-stu-id="af2a4-136">Changing the replication agent properties (including schedules) for any push subscriptions (at the Distributor).</span></span>  
  
-   <span data-ttu-id="af2a4-137">구독자에서 밀어넣기 구독의 일정을 비롯한 복제 에이전트 속성 변경</span><span class="sxs-lookup"><span data-stu-id="af2a4-137">Changing the replication agent properties (including schedules) for any pull subscriptions (at the Subscriber).</span></span>  
  
-   <span data-ttu-id="af2a4-138">배포자 및 구독자에서 변환 가능한 구독을 사용하는 트랜잭션 게시와 연결된 DTS 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="af2a4-138">Creating a DTS package associated with a transactional publication that uses transformable subscriptions (at the Distributor and Subscriber).</span></span>  
  
-   <span data-ttu-id="af2a4-139">배포자 및 구독자에서 변환 가능한 구독 추가 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="af2a4-139">Adding or dropping a transformable subscription (at the Distributor and Subscriber).</span></span>  
  
## <a name="master-database"></a><span data-ttu-id="af2a4-140">master 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="af2a4-140">master Database</span></span>  
 <span data-ttu-id="af2a4-141">다음 작업 후 해당 노드에서 **master** 시스템 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="af2a4-141">Backup the **master** system database at the appropriate node after:</span></span>  
  
-   <span data-ttu-id="af2a4-142">복제 활성화 또는 비활성화</span><span class="sxs-lookup"><span data-stu-id="af2a4-142">Enabling or disabling replication.</span></span>  
  
-   <span data-ttu-id="af2a4-143">배포자에서 배포 데이터베이스 추가 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="af2a4-143">Adding or dropping a distribution database (at the Distributor).</span></span>  
  
-   <span data-ttu-id="af2a4-144">게시자에서 데이터베이스에 게시 활성화 또는 비활성화</span><span class="sxs-lookup"><span data-stu-id="af2a4-144">Enabling or disabling a database for publishing (at the Publisher).</span></span>  
  
-   <span data-ttu-id="af2a4-145">게시자의 데이터베이스에 첫 번째 게시 추가 또는 마지막 게시 삭제</span><span class="sxs-lookup"><span data-stu-id="af2a4-145">Adding the first or dropping the last publication in any database (at the Publisher).</span></span>  
  
-   <span data-ttu-id="af2a4-146">구독자의 데이터베이스에 첫 번째 구독 추가 또는 마지막 구독 삭제</span><span class="sxs-lookup"><span data-stu-id="af2a4-146">Adding the first or dropping the last subscription in any database (at the Subscriber).</span></span>  
  
-   <span data-ttu-id="af2a4-147">게시자 및 배포자의 배포 게시자에서 게시자 활성화 또는 비활성화</span><span class="sxs-lookup"><span data-stu-id="af2a4-147">Enabling or disabling a Publisher at a Distribution Publisher (at the Publisher and Distributor).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af2a4-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="af2a4-148">See Also</span></span>  
 <span data-ttu-id="af2a4-149">[SQL Server 데이터베이스 백업 및 복원](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="af2a4-149">[Back Up and Restore of SQL Server Databases](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="af2a4-150">복제된 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="af2a4-150">Back Up and Restore Replicated Databases</span></span>](back-up-and-restore-replicated-databases.md)  
  
  
