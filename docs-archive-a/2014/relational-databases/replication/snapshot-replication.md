---
title: 스냅샷 복제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], about snapshot replication
- snapshot replication [SQL Server]
ms.assetid: 5d745f22-9c6b-4e11-8c62-bc50e9a8bf38
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6192c196e31c4c5772099074c79b3c6c4ca7aeed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743224"
---
# <a name="snapshot-replication"></a><span data-ttu-id="19a98-102">Snapshot Replication</span><span class="sxs-lookup"><span data-stu-id="19a98-102">Snapshot Replication</span></span>
  <span data-ttu-id="19a98-103">스냅샷 복제는 특정 시간에 나타나는 그대로 데이터를 배포하고 데이터 업데이트를 모니터링하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-103">Snapshot replication distributes data exactly as it appears at a specific moment in time and does not monitor for updates to the data.</span></span> <span data-ttu-id="19a98-104">동기화가 일어나면 전체 스냅샷이 생성되어 구독자에게 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-104">When synchronization occurs, the entire snapshot is generated and sent to Subscribers.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19a98-105">스냅샷 복제는 단독으로 사용할 수 있지만 게시에서 지정한 모든 개체 및 데이터의 복사본을 만드는 스냅샷 프로세스는 일반적으로 트랜잭션 및 병합 게시에 대한 초기 데이터 및 데이터베이스 개체 집합을 제공하는 데에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-105">Snapshot replication can be used by itself, but the snapshot process (which creates a copy of all of the objects and data specified by a publication) is also commonly used to provide the initial set of data and database objects for transactional and merge publications.</span></span>  
  
 <span data-ttu-id="19a98-106">다음 조건 중 하나 이상이 해당될 경우 스냅샷 복제를 단독으로 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-106">Using snapshot replication by itself is most appropriate when one or more of the following is true:</span></span>  
  
-   <span data-ttu-id="19a98-107">데이터가 자주 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-107">Data changes infrequently.</span></span>  
  
-   <span data-ttu-id="19a98-108">게시자 측에서 최신이 아닌 데이터 복사본을 일정 기간 동안 보유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-108">It is acceptable to have copies of data that are out of date with respect to the Publisher for a period of time.</span></span>  
  
-   <span data-ttu-id="19a98-109">소량의 데이터를 복제합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-109">Replicating small volumes of data.</span></span>  
  
-   <span data-ttu-id="19a98-110">짧은 기간 동안 많은 양의 데이터가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-110">A large volume of changes occurs over a short period of time.</span></span>  
  
 <span data-ttu-id="19a98-111">스냅샷 복제는 많은 양의 데이터가 변경되지만 자주 변경되지는 않을 때 가장 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-111">Snapshot replication is most appropriate when data changes are substantial but infrequent.</span></span> <span data-ttu-id="19a98-112">예를 들어 한 판매 조직이 제품 가격 목록을 유지 관리하면서 일년에 한 번이나 두 번 가격을 동시에 업데이트한다면 데이터 전체 스냅샷이 변경된 후 복제하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-112">For example, if a sales organization maintains a product price list and the prices are all updated at the same time once or twice each year, replicating the entire snapshot of data after it has changed is recommended.</span></span> <span data-ttu-id="19a98-113">특정 유형의 데이터에 대해서는 스냅샷을 더 자주 복제하는 것이 적합할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-113">Given certain types of data, more frequent snapshots may also be appropriate.</span></span> <span data-ttu-id="19a98-114">예를 들어 게시자에서 비교적 작은 테이블이 낮에 업데이트되었지만 어느 정도의 대기 시간이 허용되는 경우에는 변경 내용을 밤마다 스냅샷으로 배달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-114">For example, if a relatively small table is updated at the Publisher during the day, but some latency is acceptable, changes can be delivered nightly as a snapshot.</span></span>  
  
 <span data-ttu-id="19a98-115">증분 변경 내용은 추적되지 않으므로 스냅샷 복제에는 게시자에 트랜잭션 복제보다 낮은 연속 오버헤드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-115">Snapshot replication has a lower continuous overhead on the Publisher than transactional replication, because incremental changes are not tracked.</span></span> <span data-ttu-id="19a98-116">그러나 복제 중인 데이터 세트가 아주 큰 경우에는 스냅샷을 생성하고 적용하는 데 상당히 많은 리소스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-116">However, if the dataset set being replicated is very large, it will require substantial resources to generate and apply the snapshot.</span></span> <span data-ttu-id="19a98-117">그러므로 스냅샷 복제 사용 여부를 평가할 때 전체 데이터 집합의 크기와 데이터 변경 빈도를 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="19a98-117">Consider the size of the entire data set and the frequency of changes to the data when evaluating whether to utilize snapshot replication.</span></span>  
  
 <span data-ttu-id="19a98-118">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="19a98-118">**In this topic**</span></span>  
  
 [<span data-ttu-id="19a98-119">스냅샷 복제 작동 방법</span><span class="sxs-lookup"><span data-stu-id="19a98-119">How Snapshot Replication Works</span></span>](#HowWorks)  
  
 [<span data-ttu-id="19a98-120">스냅샷 에이전트</span><span class="sxs-lookup"><span data-stu-id="19a98-120">Snapshot Agent</span></span>](#SnapshotAgent)  
  
 [<span data-ttu-id="19a98-121">배포 및 병합 에이전트</span><span class="sxs-lookup"><span data-stu-id="19a98-121">Distribution and Merge Agents</span></span>](#DistAgent)  
  
##  <a name="how-snapshot-replication-works"></a><a name="HowWorks"></a> <span data-ttu-id="19a98-122">스냅샷 복제 작동 방법</span><span class="sxs-lookup"><span data-stu-id="19a98-122">How Snapshot Replication Works</span></span>  
 <span data-ttu-id="19a98-123">기본적으로 3가지 복제 유형은 모두 스냅샷을 사용하여 구독자를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-123">By default, all three types of replication use a snapshot to initialize Subscribers.</span></span> <span data-ttu-id="19a98-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 스냅샷 에이전트는 항상 스냅샷 파일을 생성하지만 이 파일을 배달하는 에이전트는 사용하는 복제 유형에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-124">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Snapshot Agent always generates the snapshot files, but the agent that delivers the files differs depending on the type of replication being used.</span></span> <span data-ttu-id="19a98-125">스냅샷 복제 및 트랜잭션 복제는 배포 에이전트를 사용하여 파일을 배달하지만 병합 복제는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 병합 에이전트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-125">Snapshot replication and transactional replication use the Distribution Agent to deliver the files, whereas merge replication uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Merge Agent.</span></span> <span data-ttu-id="19a98-126">배포자에서 스냅샷 에이전트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-126">The Snapshot Agent runs at the Distributor.</span></span> <span data-ttu-id="19a98-127">배포 에이전트와 병합 에이전트는 밀어넣기 구독을 위한 배포자에서 실행되거나 끌어오기 구독을 위한 구독자에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-127">The Distribution Agent and Merge Agent run at the Distributor for push subscriptions, or at Subscribers for pull subscriptions.</span></span>  
  
 <span data-ttu-id="19a98-128">구독을 만든 즉시 또는 게시를 만들 때 설정한 일정에 따라 스냅샷을 생성하고 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-128">Snapshots can be generated and applied either immediately after the subscription is created or according to a schedule set at the time the publication is created.</span></span> <span data-ttu-id="19a98-129">스냅샷 에이전트는 게시된 테이블 및 데이터베이스 개체의 스키마 및 데이터를 포함하는 스냅샷 파일을 준비하여 게시자의 스냅샷 폴더에 저장하고 배포자의 배포 데이터베이스에 추적 정보를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-129">The Snapshot Agent prepares snapshot files containing the schema and data of published tables and database objects, stores the files in the snapshot folder for the Publisher, and records tracking information in the distribution database on the Distributor.</span></span> <span data-ttu-id="19a98-130">배포자를 구성할 때 기본 스냅샷 폴더를 지정하지만 기본 위치 대신 또는 기본 위치에 추가로 게시에 대한 대체 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-130">You specify a default snapshot folder when you configure a Distributor, but you can specify an alternate location for a publication instead of or in addition to the default.</span></span>  
  
 <span data-ttu-id="19a98-131">이 항목에 설명된 표준 스냅샷 프로세스 외에도 매개 변수가 있는 필터가 포함된 병합 게시에 대해 두 부분으로 구성된 스냅샷 프로세스가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-131">In addition to the standard snapshot process described in this topic, a two-part snapshot process is used for merge publications with parameterized filters.</span></span>  
  
 <span data-ttu-id="19a98-132">다음 그림에서는 스냅샷 복제의 주요 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-132">The following illustration shows the principal components of snapshot replication.</span></span>  
  
 <span data-ttu-id="19a98-133">![스냅샷 복제 구성 요소 및 데이터 흐름](media/snapshot.gif "스냅샷 복제 구성 요소 및 데이터 흐름")</span><span class="sxs-lookup"><span data-stu-id="19a98-133">![Snapshot replication components and data flow](media/snapshot.gif "Snapshot replication components and data flow")</span></span>  
  
##  <a name="snapshot-agent"></a><a name="SnapshotAgent"></a> <span data-ttu-id="19a98-134">스냅샷 에이전트</span><span class="sxs-lookup"><span data-stu-id="19a98-134">Snapshot Agent</span></span>  
 <span data-ttu-id="19a98-135">병합 복제의 경우 스냅샷 에이전트가 실행될 때마다 스냅샷이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-135">For merge replication, a snapshot is generated every time the Snapshot Agent runs.</span></span> <span data-ttu-id="19a98-136">트랜잭션 복제의 경우 게시 속성 **immediate_sync**의 설정에 따라 스냅샷 생성이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-136">For transactional replication, snapshot generation depends on the setting of the publication property **immediate_sync**.</span></span> <span data-ttu-id="19a98-137">이 속성을 TRUE(새 게시 마법사 사용 시 기본 설정)로 설정하면 스냅샷 에이전트가 실행될 때마다 스냅샷이 생성되고 언제든지 스냅샷을 구독자에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-137">If the property is set to TRUE (the default when using the New Publication Wizard), a snapshot is generated every time the Snapshot Agent runs, and it can be applied to a Subscriber at any time.</span></span> <span data-ttu-id="19a98-138">이 속성을 FALSE( **sp_addpublication**사용 시 기본 설정)로 설정하면 스냅샷 에이전트가 마지막으로 실행된 후에 새 구독이 추가된 경우에만 스냅샷이 생성됩니다. 구독자는 동기화하기 위해 스냅샷 에이전트가 완료될 때까지 기다려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-138">If the property is set to FALSE (the default when using **sp_addpublication**), the snapshot is generated only if a new subscription has been added since the last Snapshot Agent run; Subscribers must wait for the Snapshot Agent to complete before they can synchronize.</span></span>  
  
 <span data-ttu-id="19a98-139">스냅샷 에이전트는 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="19a98-139">The Snapshot Agent performs the following steps:</span></span>  
  
1.  <span data-ttu-id="19a98-140">배포자에서 게시자로 연결을 설정한 다음 필요한 경우 게시된 테이블에 잠금을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-140">Establishes a connection from the Distributor to the Publisher, and then takes locks on published tables if necessary:</span></span>  
  
    -   <span data-ttu-id="19a98-141">병합 게시의 경우 스냅샷 에이전트는 잠금을 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-141">For merge publications, the Snapshot Agent does not take any locks.</span></span>  
  
    -   <span data-ttu-id="19a98-142">트랜잭션 게시의 경우 기본적으로 스냅샷 에이전트는 스냅샷 생성의 초기 단계에서만 잠금을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-142">For transactional publications, by default the Snapshot Agent take locks only during the initial phase of snapshot generation.</span></span>  
  
    -   <span data-ttu-id="19a98-143">스냅샷 게시의 경우 잠금은 전체 스냅샷 생성 프로세스 동안 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-143">For snapshot publications, locks are held during the entire snapshot generation process.</span></span>  
  
2.  <span data-ttu-id="19a98-144">각 아티클에 대한 테이블 스키마 복사본을 .sch 파일에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-144">Writes a copy of the table schema for each article to a .sch file.</span></span> <span data-ttu-id="19a98-145">인덱스, 제약 조건, 저장 프로시저, 뷰, 사용자 정의 함수 등과 같은 다른 데이터베이스 개체가 게시되면 추가 스크립트 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-145">If other database objects are published, such as indexes, constraints, stored procedures, views, user-defined functions, and so on, additional script files are generated.</span></span>  
  
3.  <span data-ttu-id="19a98-146">게시자에서 게시된 테이블의 데이터를 복사하고 이 데이터를 스냅샷 폴더에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-146">Copies the data from the published table at the Publisher and writes the data to the snapshot folder.</span></span> <span data-ttu-id="19a98-147">스냅샷은 BCP(대량 복사 프로그램) 파일의 집합으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-147">The snapshot is generated as a set of bulk copy program (BCP) files.</span></span>  
  
4.  <span data-ttu-id="19a98-148">스냅샷 및 트랜잭션 게시의 경우 스냅샷 에이전트는 행을 배포 데이터베이스의 **MSrepl_commands** 및 **MSrepl_transactions** 테이블에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-148">For snapshot and transactional publications, the Snapshot Agent appends rows to the **MSrepl_commands** and **MSrepl_transactions** tables in the distribution database.</span></span> <span data-ttu-id="19a98-149">**MSrepl_commands** 테이블의 항목은 .sch 및 .bcp 파일, 다른 스냅샷 파일, 프리 스냅샷 및 포스트 스냅샷 스크립트에 대한 참조 위치를 나타내는 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-149">The entries in the **MSrepl_commands** table are commands indicating the location of .sch and .bcp files, any other snapshot files, and references to any pre- or post-snapshot scripts.</span></span> <span data-ttu-id="19a98-150">**MSrepl_transactions** 테이블의 항목은 구독자 동기화와 관련된 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-150">The entries in the **MSrepl_transactions** table are commands relevant to synchronizing the Subscriber.</span></span>  
  
     <span data-ttu-id="19a98-151">병합 게시의 경우 스냅샷 에이전트는 추가 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-151">For merge publications, the Snapshot Agent performs additional steps.</span></span>  
  
5.  <span data-ttu-id="19a98-152">게시된 테이블에서 모든 잠금을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-152">Releases any locks on published tables.</span></span>  
  
 <span data-ttu-id="19a98-153">스냅샷을 생성하는 동안에는 게시된 테이블에서 스키마를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-153">During snapshot generation, you cannot make schema changes on published tables.</span></span> <span data-ttu-id="19a98-154">스냅샷 파일을 생성한 후에는 Windows 탐색기를 사용하여 스냅샷 폴더에서 해당 파일을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-154">After the snapshot files are generated, you can view them in the snapshot folder using Windows Explorer.</span></span>  
  
##  <a name="distribution-agent-and-merge-agent"></a><a name="DistAgent"></a> <span data-ttu-id="19a98-155">배포 에이전트 및 병합 에이전트</span><span class="sxs-lookup"><span data-stu-id="19a98-155">Distribution Agent and Merge Agent</span></span>  
 <span data-ttu-id="19a98-156">스냅샷 게시의 경우 배포 에이전트가 게시에 대해 실행될 때마다 아직 동기화되지 않았거나, 다시 초기화로 표시되었거나, 새 아티클을 포함하는 각 구독자로 새 스냅샷을 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-156">For snapshot publications, each time the Distribution Agent runs for the publication, it moves a new snapshot to each Subscriber that has not yet been synchronized, has been marked for reinitialization, or includes new articles.</span></span>  
  
 <span data-ttu-id="19a98-157">스냅샷 및 트랜잭션 복제의 경우 배포 에이전트는 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="19a98-157">For snapshot and transactional replication, the Distribution Agent performs the following steps:</span></span>  
  
1.  <span data-ttu-id="19a98-158">배포자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-158">Establishes a connection to the Distributor.</span></span>  
  
2.  <span data-ttu-id="19a98-159">배포자의 배포 데이터베이스에서 **MSrepl_commands** 및 **MSrepl_transactions** 테이블을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-159">Examines the **MSrepl_commands** and **MSrepl_transactions** tables in the distribution database on the Distributor.</span></span> <span data-ttu-id="19a98-160">에이전트는 첫 번째 테이블에서 스냅샷 파일의 위치를 읽고 두 테이블 모두에서 구독자 동기화 명령을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-160">The agent reads the location of the snapshot files from the first table and Subscriber synchronization commands from both tables.</span></span>  
  
3.  <span data-ttu-id="19a98-161">스키마 및 명령을 구독 데이터베이스로 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-161">Applies the schema and commands to the subscription database.</span></span>  
  
 <span data-ttu-id="19a98-162">필터링되지 않은 병합 복제 게시의 경우 병합 에이전트는 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="19a98-162">For an unfiltered merge replication publication, the Merge Agent performs the following steps:</span></span>  
  
1.  <span data-ttu-id="19a98-163">게시자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-163">Establishes a connection to the Publisher.</span></span>  
  
2.  <span data-ttu-id="19a98-164">게시자의 **sysmergeschemachange** 테이블을 검사하고 구독자에 적용해야 하는 새 스냅샷이 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-164">Examines the **sysmergeschemachange** table on the Publisher and determines whether there is a new snapshot that should be applied at the Subscriber.</span></span>  
  
3.  <span data-ttu-id="19a98-165">새 스냅샷이 있는 경우 병합 에이전트는 **sysmergeschemachange**에 지정된 위치에 있는 스냅샷 파일을 구독 데이터베이스에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="19a98-165">If a new snapshot is available, the Merge Agent applies to the subscription database the snapshot files from the location specified in **sysmergeschemachange**.</span></span>  
  
  
