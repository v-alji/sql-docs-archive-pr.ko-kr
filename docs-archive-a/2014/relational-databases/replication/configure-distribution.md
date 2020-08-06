---
title: 배포 구성 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], distribution
- distribution configuration [SQL Server replication]
- remote Distributors [SQL Server replication]
- transactional replication, configuring distribution
- distribution databases [SQL Server replication], sizing
- Distributors [SQL Server replication], configuring
- distribution databases [SQL Server replication], about distribution databases
- distribution databases [SQL Server replication]
- merge replication [SQL Server replication], configuring distribution
ms.assetid: 94d52169-384e-4885-84eb-2304e967d9f7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b0378fe285ba57e1420b7e6bebf5e2e6fe13d29e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648940"
---
# <a name="configure-distribution"></a><span data-ttu-id="d3f05-102">배포 구성</span><span class="sxs-lookup"><span data-stu-id="d3f05-102">Configure Distribution</span></span>
  <span data-ttu-id="d3f05-103">배포자는 배포 데이터베이스를 포함하는 서버이며 배포 데이터베이스는 트랜잭션 복제에 대한 모든 유형의 복제 및 트랜잭션에 대한 메타데이터와 기록 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-103">The Distributor is a server that contains the distribution database, which stores metadata and history data for all types of replication and transactions for transactional replication.</span></span> <span data-ttu-id="d3f05-104">복제를 설정하려면 배포자를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-104">To set up replication, you must configure a Distributor.</span></span> <span data-ttu-id="d3f05-105">각 게시자는 하나의 배포자 인스턴스에만 할당될 수 있지만 여러 게시자가 하나의 배포자를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-105">Each Publisher can be assigned to only a single Distributor instance, but multiple publishers can share a Distributor.</span></span> <span data-ttu-id="d3f05-106">배포자가 있는 서버에는 다음과 같은 추가 리소스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-106">The Distributor uses these additional resources on the server where it is located:</span></span>  
  
-   <span data-ttu-id="d3f05-107">게시에 대한 스냅샷 파일이 배포자에 저장되어 있는 경우(일반적으로 배포자에 저장되어 있음) 추가 디스크 공간</span><span class="sxs-lookup"><span data-stu-id="d3f05-107">Additional disk space if the snapshot files for the publication are stored on the Distributor (which they typically are).</span></span>  
  
-   <span data-ttu-id="d3f05-108">배포 데이터베이스를 저장할 추가 디스크 공간</span><span class="sxs-lookup"><span data-stu-id="d3f05-108">Additional disk space to store the distribution database.</span></span>  
  
-   <span data-ttu-id="d3f05-109">배포자에서 실행되는 밀어넣기 구독에 대해 복제 에이전트가 사용할 추가 프로세서</span><span class="sxs-lookup"><span data-stu-id="d3f05-109">Additional processor usage by replication agents for push subscriptions running on the Distributor.</span></span>  
  
 <span data-ttu-id="d3f05-110">배포자로 선택된 서버는 복제 및 해당 서버의 다른 작업을 지원하기 위해 충분한 디스크 공간과 처리 성능이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-110">The server you select as the Distributor should have adequate disk space and processor power to support replication and any other activities on that server.</span></span> <span data-ttu-id="d3f05-111">배포자를 구성할 때 다음과 같은 사항을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-111">When you configure the Distributor, you specify the following:</span></span>  
  
-   <span data-ttu-id="d3f05-112">이 배포자를 사용하는 모든 게시자에 대해 기본적으로 사용되는 스냅샷 폴더.</span><span class="sxs-lookup"><span data-stu-id="d3f05-112">A snapshot folder, which is used, by default, for all Publishers that use this Distributor.</span></span> <span data-ttu-id="d3f05-113">이 폴더가 이미 공유되어 있고 적절한 권한 집합이 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-113">Ensure that this folder is already shared and has the appropriate permissions set.</span></span> <span data-ttu-id="d3f05-114">자세한 내용은 [스냅샷 폴더 보안 설정](security/secure-the-snapshot-folder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3f05-114">For more information, see [Secure the Snapshot Folder](security/secure-the-snapshot-folder.md).</span></span>  
  
-   <span data-ttu-id="d3f05-115">배포 데이터베이스의 이름 및 파일 위치.</span><span class="sxs-lookup"><span data-stu-id="d3f05-115">A name and file locations for the distribution database.</span></span> <span data-ttu-id="d3f05-116">배포 데이터베이스를 만든 후에는 이름을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-116">The distribution database cannot be renamed after it is created.</span></span> <span data-ttu-id="d3f05-117">데이터베이스에 다른 이름을 사용하려면 배포를 해제하고 다시 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-117">To use a different name for the database, you must disable distribution and reconfigure it.</span></span>  
  
-   <span data-ttu-id="d3f05-118">배포자 사용을 허가받은 게시자.</span><span class="sxs-lookup"><span data-stu-id="d3f05-118">Any Publishers authorized to use the Distributor.</span></span> <span data-ttu-id="d3f05-119">배포자가 실행되는 인스턴스 이외의 게시자를 지정하면 게시자가 원격 배포자에 연결할 때 사용할 암호도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-119">If you specify Publishers other than the instance on which the Distributor runs, you must also specify a password for the connections the Publishers make to the remote Distributor.</span></span>  
  
 <span data-ttu-id="d3f05-120">트랜잭션 복제의 경우 배포를 구성한 후 다음을 수행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-120">For transactional replication, after you configure distribution, we recommend that you:</span></span>  
  
-   <span data-ttu-id="d3f05-121">배포 데이터베이스 크기를 적절히 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-121">Size the distribution database appropriately.</span></span> <span data-ttu-id="d3f05-122">시스템에서 명령 저장에 필요한 공간을 결정할 수 있도록 일반적인 로드 상태에서 복제를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-122">Test replication with a typical load for your system to determine how much space is required to store commands.</span></span> <span data-ttu-id="d3f05-123">데이터베이스는 자주 자동 증가되지 않고도 명령을 저장할 수 있을 만큼 충분히 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-123">Ensure the database is large enough to store commands without having to auto-grow frequently.</span></span> <span data-ttu-id="d3f05-124">데이터베이스의 크기 변경에 대한 자세한 내용은 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3f05-124">For more information about changing the size of a database, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="d3f05-125">배포 데이터베이스에 **sync with backup** 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-125">Set the **sync with backup** option on the distribution database.</span></span> <span data-ttu-id="d3f05-126">자세한 내용은 [스냅샷 및 트랜잭션 복제의 백업 및 복원을 위한 전략](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md) 및 [트랜잭션 복제에 통합 백업 사용&#40;복제 Transact-SQL 프로그래밍&#41;](administration/enable-coordinated-backups-for-transactional-replication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3f05-126">For more information, see [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md) and [Enable Coordinated Backups for Transactional Replication &#40;Replication Transact-SQL Programming&#41;](administration/enable-coordinated-backups-for-transactional-replication.md).</span></span>  
  
## <a name="local-and-remote-distributors"></a><span data-ttu-id="d3f05-127">로컬 및 원격 배포자</span><span class="sxs-lookup"><span data-stu-id="d3f05-127">Local and Remote Distributors</span></span>  
 <span data-ttu-id="d3f05-128">기본적으로 배포자는 게시자와 같은 서버(로컬 배포자)이지만 게시자와는 다른 별도의 서버(원격 배포자)일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-128">By default, the Distributor is the same server as the Publisher (a local Distributor), but it can also be a separate server from the Publisher (a remote Distributor).</span></span> <span data-ttu-id="d3f05-129">일반적으로 다음 작업을 수행하려는 경우 원격 배포자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-129">Typically, you would choose to use a remote Distributor if you want to:</span></span>  
  
-   <span data-ttu-id="d3f05-130">게시자에 대한 복제의 영향을 최소화하기 위해(예: 게시자가 OLTP 서버인 경우) 처리를 다른 컴퓨터로 오프로드</span><span class="sxs-lookup"><span data-stu-id="d3f05-130">Offload processing to another computer if you want minimal impact from replication on the Publisher (for example, if the Publisher is an OLTP server).</span></span>  
  
-   <span data-ttu-id="d3f05-131">여러 게시자에 대해 중앙 집중식 배포자 구성</span><span class="sxs-lookup"><span data-stu-id="d3f05-131">Configure a centralized Distributor for multiple Publishers.</span></span>  
  
 <span data-ttu-id="d3f05-132">다음과 같은 두 가지 이유로 원격 배포자는 병합 복제보다 트랜잭션 복제에서 더 많이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-132">Remote Distributors are more common in transactional replication than they are in merge replication for two reasons:</span></span>  
  
-   <span data-ttu-id="d3f05-133">복제한 모든 트랜잭션은 배포 데이터베이스에 작성되고 배포 데이터베이스에서 읽어 오기 때문에 배포자는 트랜잭션 복제에서 더 큰 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-133">The Distributor plays a larger role in transactional replication because all replicated transactions are written to and read from the distribution database.</span></span>  
  
-   <span data-ttu-id="d3f05-134">병합 복제 토폴로지는 일반적으로 끌어오기 구독을 사용하므로 에이전트는 배포자에서 모두 실행되기 보다는 각각의 구독자에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-134">Merge replication topologies typically use pull subscriptions, so agents run at each Subscriber, rather than all running at the Distributor.</span></span> <span data-ttu-id="d3f05-135">자세한 내용은 [게시 구독](subscribe-to-publications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3f05-135">For more information, see [Subscribe to Publications](subscribe-to-publications.md).</span></span> <span data-ttu-id="d3f05-136">대부분의 경우 병합 복제에 대해서는 로컬 배포자를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f05-136">In most cases, you should use a local Distributor for merge replication.</span></span>  
  
 <span data-ttu-id="d3f05-137">게시 및 배포를 구성하려면 [Configure Publishing and Distribution](configure-publishing-and-distribution.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d3f05-137">To configure publishing and distribution, see [Configure Publishing and Distribution](configure-publishing-and-distribution.md).</span></span>  
  
 <span data-ttu-id="d3f05-138">게시자 및 배포자 속성을 수정하려면 [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d3f05-138">To modify Publisher and Distributor properties, see [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f05-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d3f05-139">See Also</span></span>  
 <span data-ttu-id="d3f05-140">[데이터 및 데이터베이스 개체 게시](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="d3f05-140">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="d3f05-141">배포자 보안 설정</span><span class="sxs-lookup"><span data-stu-id="d3f05-141">Secure the Distributor</span></span>](security/secure-the-distributor.md)  
  
  
