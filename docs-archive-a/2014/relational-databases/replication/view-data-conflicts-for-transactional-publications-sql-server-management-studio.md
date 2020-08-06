---
title: 트랜잭션 게시에 대 한 데이터 충돌 보기 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- queued updating subscriptions [SQL Server replication]
- viewing conflict information
ms.assetid: 9977dd75-b0de-4376-9c13-86d80567d8aa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 228753c113bcf43ed276d989a3996e9bf23bfc16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653807"
---
# <a name="view-data-conflicts-for-transactional-publications-sql-server-management-studio"></a><span data-ttu-id="e4c78-102">트랜잭션 게시의 데이터 충돌 확인(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e4c78-102">View Data Conflicts for Transactional Publications (SQL Server Management Studio)</span></span>
  <span data-ttu-id="e4c78-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 복제 충돌 뷰어에서 피어 투 피어 트랜잭션 복제와 지연 업데이트 구독이 포함된 트랜잭션 복제의 충돌을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-103">You can view conflicts for peer-to-peer transactional replication and transactional replication with queued updating subscriptions in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Replication Conflict Viewer.</span></span> <span data-ttu-id="e4c78-104">충돌 감지 및 해결 방법은 [피어 투 피어 복제에서 충돌 검색](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md) 및 [지연 업데이트 충돌 해결 옵션 설정&#40;SQL Server Management Studio&#41;](publish/create-an-updatable-subscription-to-a-transactional-publication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4c78-104">For information about how conflicts are detected and resolved, see [Conflict Detection in Peer-to-Peer Replication](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md) and [Set Queued Updating Conflict Resolution Options &#40;SQL Server Management Studio&#41;](publish/create-an-updatable-subscription-to-a-transactional-publication.md).</span></span>  
  
 <span data-ttu-id="e4c78-105">충돌 데이터의 가용성은 복제 유형 및 충돌 보존 기간에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-105">The availability of conflict data depends on the type of replication and the conflict retention period:</span></span>  
  
-   <span data-ttu-id="e4c78-106">피어 투 피어 복제의 경우 충돌이 감지되면 기본적으로 배포 에이전트가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-106">For peer-to-peer replication, by default, the Distribution Agent fails when it detects a conflict.</span></span> <span data-ttu-id="e4c78-107">오류 로그에 충돌 오류가 기록되지만 충돌 테이블에는 충돌 데이터가 기록되지 않으므로 해당 데이터를 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-107">A conflict error is logged into the error log, but no conflict data is logged into the conflict table; therefore it is not available for viewing.</span></span> <span data-ttu-id="e4c78-108">배포 에이전트가 계속할 수 있으면 충돌이 감지된 각 노드에 로컬로 충돌이 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-108">If the Distribution Agent is allowed to continue, a conflict is logged locally on each node where it was detected.</span></span> <span data-ttu-id="e4c78-109">자세한 내용은 [Conflict Detection in Peer-to-Peer Replication](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)의 "충돌 처리"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e4c78-109">For more information, see "Handling Conflicts" in [Conflict Detection in Peer-to-Peer Replication](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).</span></span>  
  
-   <span data-ttu-id="e4c78-110">지연 업데이트 구독의 경우 모든 충돌에 대한 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-110">For queued updating subscriptions, data is available for every conflict.</span></span> <span data-ttu-id="e4c78-111">지정된 충돌 보존 기간(기본값: 14일) 동안 복제 충돌 뷰어에서 충돌 데이터를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-111">Conflict data is available in the Replication Conflict Viewer for the amount of time specified for the conflict retention period, with a default of 14 days.</span></span> <span data-ttu-id="e4c78-112">충돌 보존 기간을 설정하려면 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-112">To set the conflict retention period, perform either of the following:</span></span>  
  
    -   <span data-ttu-id="e4c78-113">@conflict_retention sp_addpublication [의](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)매개 변수에 보존 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-113">Specify a retention value for the @conflict_retention parameter of [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql).</span></span>  
  
    -   <span data-ttu-id="e4c78-114">매개 변수에 값을 지정 `'conflict_retention'` @property 하 고 @value [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)의 매개 변수에 보존 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-114">Specify a value of `'conflict_retention'` for the @property parameter and a retention value for the @value parameter of [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql).</span></span>  
  
### <a name="to-view-conflicts"></a><span data-ttu-id="e4c78-115">충돌을 보려면</span><span class="sxs-lookup"><span data-stu-id="e4c78-115">To view conflicts</span></span>  
  
1.  <span data-ttu-id="e4c78-116">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 해당 서버에 연결한 후 다음과 같은 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-116">Connect to the appropriate server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node:</span></span>  
  
    -   <span data-ttu-id="e4c78-117">피어 투 피어 복제의 경우 충돌이 발생한 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-117">For peer-to-peer replication, this is the node at which the conflict occurred.</span></span>  
  
    -   <span data-ttu-id="e4c78-118">지연 업데이트 구독의 경우 게시자입니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-118">For queued updating subscriptions, this is the Publisher.</span></span>  
  
2.  <span data-ttu-id="e4c78-119">**복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-119">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="e4c78-120">충돌을 확인할 게시를 마우스 오른쪽 단추로 클릭한 다음 **충돌 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-120">Right-click the publication for which you want to view conflicts, and then click **View Conflicts**.</span></span>  
  
4.  <span data-ttu-id="e4c78-121">**충돌 테이블 선택** 대화 상자에서 충돌을 확인하려는 데이터베이스, 게시 및 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-121">In the **Select Conflict Table** dialog box, select a database, publication, and table for which to view conflicts.</span></span>  
  
5.  <span data-ttu-id="e4c78-122">복제 충돌 뷰어에서 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-122">In the Replication Conflict Viewer, you can:</span></span>  
  
    -   <span data-ttu-id="e4c78-123">상단 표 오른쪽의 단추를 사용하여 행을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-123">Filter rows with the buttons to the right of the upper grid.</span></span>  
  
    -   <span data-ttu-id="e4c78-124">상단 표에서 행을 선택하여 해당 행에 대한 정보를 하단 표에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-124">Select a row in the upper grid to display information on that row in the lower grid.</span></span>  
  
    -   <span data-ttu-id="e4c78-125">상단 표에서 행을 하나 이상 선택한 다음 **제거**를 클릭하여 충돌 메타데이터 테이블에서 행을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-125">Select one or more rows in the upper grid, and then click **Remove**, which removes the row from the conflicts metadata table.</span></span>  
  
    -   <span data-ttu-id="e4c78-126">속성 단추(**...**)를 클릭하여 충돌과 관련된 열에 대한 자세한 정보를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-126">Click the properties button (**...**) to view more information on a column involved in a conflict.</span></span>  
  
    -   <span data-ttu-id="e4c78-127">**이 충돌 정보 기록** 을 선택하여 충돌 데이터를 파일에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-127">Select **Log the details of this conflict** to log conflict data to a file.</span></span> <span data-ttu-id="e4c78-128">파일의 위치를 지정하려면 **보기** 메뉴를 가리킨 다음 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-128">To specify a location for the file, point to the **View** menu, and then click **Options**.</span></span> <span data-ttu-id="e4c78-129">값을 입력하거나 찾아보기 단추 (**...**)를 클릭한 다음 해당 파일을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-129">Enter a value, or click the browse button (**...**), and then navigate to the appropriate file.</span></span> <span data-ttu-id="e4c78-130">**확인**을 클릭하여 **옵션** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-130">Click **OK** to close the **Options** dialog box.</span></span>  
  
6.  <span data-ttu-id="e4c78-131">복제 충돌 뷰어를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e4c78-131">Close the Replication Conflict Viewer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4c78-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e4c78-132">See Also</span></span>  
 <span data-ttu-id="e4c78-133">[Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="e4c78-133">[Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md) </span></span>  
 [<span data-ttu-id="e4c78-134">Queued Updating Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="e4c78-134">Queued Updating Conflict Detection and Resolution</span></span>](transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)  
  
  
