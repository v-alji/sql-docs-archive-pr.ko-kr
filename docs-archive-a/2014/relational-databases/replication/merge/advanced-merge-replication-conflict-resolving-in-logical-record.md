---
title: 논리적 레코드에서 충돌 감지 및 해결 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- logical records [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
ms.assetid: f2e55040-ca69-4ccf-97d1-c362e1633f26
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f9822cd153af67538a36a894de0ec1b4716e54cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638724"
---
# <a name="detecting-and-resolving-conflicts-in-logical-records"></a><span data-ttu-id="f367b-102">논리적 레코드에서 충돌 감지 및 해결</span><span class="sxs-lookup"><span data-stu-id="f367b-102">Detecting and Resolving Conflicts in Logical Records</span></span>
  <span data-ttu-id="f367b-103">이 항목에서는 논리적 레코드에서 충돌을 감지하고 해결하는 다양한 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-103">This topic covers the various combinations of conflict detection and conflict resolution approaches possible when using logical records.</span></span> <span data-ttu-id="f367b-104">두 개 이상의 노드에서 동일한 데이터를 변경할 때 병합 복제에서 충돌이 발생하거나 병합 복제에서 변경 내용을 복제할 때 제약 조건 위반과 같은 특정 오류 유형이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-104">A conflict in merge replication occurs when more than one node changes the same data, or merge replication encounters certain types of errors, such as a constraint violation, when replicating changes.</span></span> <span data-ttu-id="f367b-105">충돌 감지 및 해결에 대한 자세한 내용은 [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f367b-105">For more information about conflict detection and resolution, see [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md).</span></span>

 <span data-ttu-id="f367b-106">아티클의 충돌 추적 및 해결 수준을 지정하려면 [병합 아티클에 대 한 충돌 추적 및 해결 수준 지정](../publish/specify-merge-replication-properties.md#interactive-conflict-resolution)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f367b-106">To specify the conflict tracking and resolution level for an article, see [Specify the Conflict Tracking and Resolution Level for Merge Articles](../publish/specify-merge-replication-properties.md#interactive-conflict-resolution).</span></span>

## <a name="conflict-detection"></a><span data-ttu-id="f367b-107">충돌 감지</span><span class="sxs-lookup"><span data-stu-id="f367b-107">Conflict Detection</span></span>
 <span data-ttu-id="f367b-108">논리적 레코드에 대한 충돌을 감지하는 방법은 두 가지 아티클 속성인 **column_tracking** 및 **logical_record_level_conflict_detection**을 확인하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-108">The way in which conflicts are detected for logical records is determined by two article properties: **column_tracking** and **logical_record_level_conflict_detection**.</span></span> [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] <span data-ttu-id="f367b-109">이상 버전에서는 논리적 레코드 수준 감지도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-109">and later versions also support logical record-level detection.</span></span>

 <span data-ttu-id="f367b-110">**logical_record_level_conflict_detection** 아티클 속성은 TRUE 또는 FALSE로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-110">The **logical_record_level_conflict_detection** article property can be set to TRUE or FALSE.</span></span> <span data-ttu-id="f367b-111">이 값은 최상위 부모 아티클에 대해서만 설정해야 하며 자식 아티클에서는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-111">The value should only be set for the top-level parent article and will be ignored by child articles.</span></span> <span data-ttu-id="f367b-112">이 값이 FALSE이면 병합 복제에서는 이전 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서처럼 아티클에 대한 **column_tracking** 속성 값만 기반으로 하여 충돌을 감지합니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-112">If this value is FALSE, merge replication detects conflicts as in previous versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], based solely on the value of the **column_tracking** property for the article.</span></span> <span data-ttu-id="f367b-113">이 값이 TRUE이면 병합 복제에서는 아티클의 **column_tracking** 속성을 무시하고 논리적 레코드가 변경된 경우 충돌을 감지합니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-113">If this value is TRUE, merge replication will ignore the **column_tracking** property of the article, and detect a conflict if changes are made anywhere in the logical record.</span></span> <span data-ttu-id="f367b-114">예를 들어 다음과 같은 시나리오를 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-114">For example, consider this scenario:</span></span>

 <span data-ttu-id="f367b-115">![값을 포함하는 3개 테이블 논리적 레코드](../media/logical-records-05.gif "값을 포함하는 3개 테이블 논리적 레코드")</span><span class="sxs-lookup"><span data-stu-id="f367b-115">![Three table logical record with values](../media/logical-records-05.gif "Three table logical record with values")</span></span>

 <span data-ttu-id="f367b-116">두 명의 사용자가 **Customers**, **Orders**또는 **OrderItems** 테이블에서 Customer2 논리적 레코드에 대한 값을 변경하는 경우 충돌이 감지됩니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-116">A conflict is detected if two users change any values for the Customer2 logical record in the **Customers**, **Orders**, or **OrderItems** tables.</span></span> <span data-ttu-id="f367b-117">이 예제에서는 주로 UPDATE 문을 통해 값을 변경한 경우를 다루지만 INSERT 또는 DELETE 문을 통해 변경한 경우에도 충돌이 감지될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-117">This example involves changes made via an UPDATE statement, but the conflict can also be detected by changes made with INSERT or DELETE statements.</span></span>

## <a name="conflict-resolution"></a><span data-ttu-id="f367b-118">충돌 해결</span><span class="sxs-lookup"><span data-stu-id="f367b-118">Conflict Resolution</span></span>
 <span data-ttu-id="f367b-119">기본적으로 병합 복제는 우선 순위 기반 논리를 사용하여 충돌을 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-119">By default, merge replication uses priority-based logic to resolve conflicts.</span></span> <span data-ttu-id="f367b-120">두 구독자 데이터베이스에서 변경 내용이 충돌하는 경우 구독 우선 순위가 높은 구독자에 대한 변경 내용이 우선 적용되고 우선 순위가 같으면 게시자에 첫 번째로 도달하는 변경 내용이 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-120">If a conflicting change is made in two Subscriber databases, the change for the Subscriber with the higher subscription priority wins, or if the priority is the same, the first change to reach the Publisher wins.</span></span> <span data-ttu-id="f367b-121">행 수준 감지와 열 수준 감지에서는 전체 적용되는 행이 무시되는 행을 항상 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-121">With row-level and column-level detection, the entire winning row always overwrites the losing row.</span></span>

 <span data-ttu-id="f367b-122">**logical_record_level_conflict_resolution** 아티클 속성은 TRUE 또는 FALSE로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-122">The **logical_record_level_conflict_resolution** article property can be set to TRUE or FALSE.</span></span> <span data-ttu-id="f367b-123">이 값은 최상위 부모 아티클에 대해서만 설정해야 하며 자식 아티클에서는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-123">The value should only be set for the top-level parent article and will be ignored by child articles.</span></span> <span data-ttu-id="f367b-124">값이 TRUE이면 전체 적용되는 논리적 레코드가 무시되는 논리적 레코드를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-124">If the value is TRUE, the entire winning logical record overwrites the losing logical record.</span></span> <span data-ttu-id="f367b-125">값이 FALSE이면 행별로 다른 구독자나 게시자의 내용이 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-125">If it is FALSE, individual winning rows can come from different Subscribers or Publishers.</span></span> <span data-ttu-id="f367b-126">예를 들어 충돌 시 **Orders** 테이블의 행에서는 구독자 A 내용이 적용되고 **OrderItems** 테이블의 관련 행에서는 구독자 B 내용이 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-126">For example, Subscriber A could win a conflict on a row from the **Orders** table, and Subscriber B could win on a related row from the **OrderItems** table.</span></span> <span data-ttu-id="f367b-127">그 결과 논리적 레코드의 **Orders** 행에는 구독자 A의 내용이, **OrderItems** 행에는 구독자 B의 내용이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-127">The result is a logical record with the **Orders** row from Subscriber A and the **OrderItems** row from Subscriber B.</span></span>

## <a name="interaction-of-conflict-resolution-and-detection-settings"></a><span data-ttu-id="f367b-128">충돌 해결 설정과 충돌 감지 설정 간의 상호 작용</span><span class="sxs-lookup"><span data-stu-id="f367b-128">Interaction of Conflict Resolution and Detection Settings</span></span>
 <span data-ttu-id="f367b-129">충돌 결과는 충돌 감지 설정과 충돌 해결 설정 간의 상호 작용에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-129">The outcome of conflicts depends on the interaction of conflict detection and resolution settings.</span></span> <span data-ttu-id="f367b-130">아래 예에서는 우선 순위 기반 충돌 해결이 사용된다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-130">For the examples below, it is assumed that the priority-based conflict resolution is being used.</span></span> <span data-ttu-id="f367b-131">논리적 레코드 사용 시 이 두 설정을 다음과 같이 조합하여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-131">When using logical records, the possibilities are:</span></span>

-   <span data-ttu-id="f367b-132">행 또는 열 수준 감지, 행 수준 해결</span><span class="sxs-lookup"><span data-stu-id="f367b-132">Row or column level detection, row level resolution</span></span>

-   <span data-ttu-id="f367b-133">열 수준 감지, 논리적 레코드 해결</span><span class="sxs-lookup"><span data-stu-id="f367b-133">Column level detection, logical record resolution</span></span>

-   <span data-ttu-id="f367b-134">행 수준 감지, 논리적 레코드 해결</span><span class="sxs-lookup"><span data-stu-id="f367b-134">Row level detection, logical record resolution</span></span>

-   <span data-ttu-id="f367b-135">논리적 레코드 감지, 논리적 레코드 해결</span><span class="sxs-lookup"><span data-stu-id="f367b-135">Logical record detection, logical record resolution</span></span>

### <a name="row-or-column-level-detection-row-level-resolution"></a><span data-ttu-id="f367b-136">행 또는 열 수준 감지, 행 수준 해결</span><span class="sxs-lookup"><span data-stu-id="f367b-136">Row or Column Level Detection, Row Level Resolution</span></span>
 <span data-ttu-id="f367b-137">이 예에서는 다음과 같이 게시가 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-137">In this example, the publication is configured with:</span></span>

-   <span data-ttu-id="f367b-138">**column_tracking** 을 TRUE 또는 FALSE로 설정</span><span class="sxs-lookup"><span data-stu-id="f367b-138">**column_tracking** is TRUE or FALSE</span></span>

-   <span data-ttu-id="f367b-139">**logical_record_level_conflict_detection** 을 FALSE로 설정</span><span class="sxs-lookup"><span data-stu-id="f367b-139">**logical_record_level_conflict_detection** is FALSE</span></span>

-   <span data-ttu-id="f367b-140">**logical_record_level_conflict_resolution** 을 FALSE로 설정</span><span class="sxs-lookup"><span data-stu-id="f367b-140">**logical_record_level_conflict_resolution** is FALSE</span></span>

 <span data-ttu-id="f367b-141">이러한 경우 감지는 행 또는 열 수준에서 수행되고 해결은 행 수준에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-141">In this case, detection is at the row or column level and resolution is at the row level.</span></span> <span data-ttu-id="f367b-142">이렇게 설정하면 논리적 레코드에 대한 모든 변경 내용을 한 단위로 복제할 수 있지만 논리적 레코드 수준에서 충돌을 감지하거나 해결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-142">These settings are used to take advantage of having all changes to a logical record replicate as a unit, but without conflict detection or resolution at the logical record level.</span></span>

### <a name="column-level-detection-logical-record-resolution"></a><span data-ttu-id="f367b-143">열 수준 감지, 논리적 레코드 해결</span><span class="sxs-lookup"><span data-stu-id="f367b-143">Column Level Detection, Logical Record Resolution</span></span>
 <span data-ttu-id="f367b-144">이 예에서는 다음과 같이 게시가 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-144">In this example, the publication is configured with:</span></span>

-   <span data-ttu-id="f367b-145">**column_tracking** 을 TRUE로 설정</span><span class="sxs-lookup"><span data-stu-id="f367b-145">**column_tracking** is TRUE</span></span>

-   <span data-ttu-id="f367b-146">**logical_record_level_conflict_detection** 을 FALSE로 설정</span><span class="sxs-lookup"><span data-stu-id="f367b-146">**logical_record_level_conflict_detection** is FALSE</span></span>

-   <span data-ttu-id="f367b-147">**logical_record_level_conflict_resolution** 을 TRUE로 설정</span><span class="sxs-lookup"><span data-stu-id="f367b-147">**logical_record_level_conflict_resolution** is TRUE</span></span>

 <span data-ttu-id="f367b-148">게시자와 구독자가 동일한 데이터 집합으로 시작하고 **orders** 테이블과 **customers** 테이블 사이에 논리적 레코드가 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-148">A Publisher and Subscriber start with the same data set, and a logical record is defined between the **orders** and **customers** tables.</span></span> <span data-ttu-id="f367b-149">게시자는 **customers** 테이블에서 **custcol1** 열을 변경하고 **orders** 테이블에서 **ordercol1** 열을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-149">The Publisher changes the **custcol1** column in the **customers** table and the **ordercol1** in the **orders** table.</span></span> <span data-ttu-id="f367b-150">구독자는 **customers** 테이블의 동일한 행에서 **custcol1** 열을 변경하고 **orders** 테이블의 동일한 행에서 **ordercol2** 열을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-150">The Subscriber changes **custcol1** in the same row of the **customers** table and the **ordercol2** column in the same row of the **orders** table.</span></span> <span data-ttu-id="f367b-151">**customer** 테이블의 동일한 열을 변경하면 충돌이 발생하지만 **orders** 테이블을 변경하면 충돌이 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-151">The changes to the same column in the **customer** table result in a conflict, but the changes to the **orders** table are not in conflict.</span></span>

 <span data-ttu-id="f367b-152">논리적 레코드 수준에서 충돌이 해결되므로 복제 처리 중 게시자에서 적용되는 변경 내용이 구독자 테이블에서의 변경 내용을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-152">Because the conflicts are resolved at the logical record level, the winning changes made at the Publisher replace the changes made in the Subscriber tables during replication processing.</span></span>

 <span data-ttu-id="f367b-153">![관련 행의 변경 내용을 보여 주는 일련의 테이블](../media/logical-records-06.gif "관련 행의 변경 내용을 보여 주는 일련의 테이블")</span><span class="sxs-lookup"><span data-stu-id="f367b-153">![Series of tables showing changes to related rows](../media/logical-records-06.gif "Series of tables showing changes to related rows")</span></span>

### <a name="row-level-detection-logical-record-resolution"></a><span data-ttu-id="f367b-154">행 수준 감지, 논리적 레코드 해결</span><span class="sxs-lookup"><span data-stu-id="f367b-154">Row Level Detection, Logical Record Resolution</span></span>
 <span data-ttu-id="f367b-155">이 예에서는 다음과 같이 게시가 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-155">In this example, the publication is configured with:</span></span>

-   <span data-ttu-id="f367b-156">**column_tracking** 을 FALSE로 설정</span><span class="sxs-lookup"><span data-stu-id="f367b-156">**column_tracking** is FALSE</span></span>

-   <span data-ttu-id="f367b-157">**logical_record_level_conflict_detection** 을 FALSE로 설정</span><span class="sxs-lookup"><span data-stu-id="f367b-157">**logical_record_level_conflict_detection** is FALSE</span></span>

-   <span data-ttu-id="f367b-158">**logical_record_level_conflict_resolution** 을 TRUE로 설정</span><span class="sxs-lookup"><span data-stu-id="f367b-158">**logical_record_level_conflict_resolution** is TRUE</span></span>

 <span data-ttu-id="f367b-159">게시자 및 구독자는 동일한 데이터 집합으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-159">A Publisher and Subscriber start with the same data set.</span></span> <span data-ttu-id="f367b-160">게시자는 **customers** 테이블에서 **custcol1** 열을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-160">The Publisher changes the **custcol1** column in the **customers** table.</span></span> <span data-ttu-id="f367b-161">구독자는 **customers** 테이블에서 **custcol2** 열을 변경하고 **orders** 테이블에서 **ordercol2** 열을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-161">The Subscriber changes **custcol2** in the **customers** table and the **ordercol2** column in the **orders** table.</span></span> <span data-ttu-id="f367b-162">**customers** 테이블의 동일한 행을 변경하면 충돌이 발생하지만 구독자가 **orders** 테이블을 변경하는 경우 충돌이 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-162">The changes to the same row in the **customers** table result in a conflict, but the Subscriber changes to the **orders** table are not in conflict.</span></span>

 <span data-ttu-id="f367b-163">논리적 레코드 수준에서 충돌이 해결되므로 동기화 중 게시자에서 적용되는 변경 내용이 구독자 테이블에서의 변경 내용을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-163">Because the conflicts are resolved at the logical record level, during synchronization the winning changes made at the Publisher replace the changes made in the Subscriber tables.</span></span>

 <span data-ttu-id="f367b-164">![관련 행의 변경 내용을 보여 주는 일련의 테이블](../media/logical-records-07.gif "관련 행의 변경 내용을 보여 주는 일련의 테이블")</span><span class="sxs-lookup"><span data-stu-id="f367b-164">![Series of tables showing changes to related rows](../media/logical-records-07.gif "Series of tables showing changes to related rows")</span></span>

### <a name="logical-record-detection-logical-record-resolution"></a><span data-ttu-id="f367b-165">논리적 레코드 감지, 논리적 레코드 해결</span><span class="sxs-lookup"><span data-stu-id="f367b-165">Logical Record Detection, Logical Record Resolution</span></span>
 <span data-ttu-id="f367b-166">이 예에서는 다음과 같이 게시가 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-166">In this example, the publication is configured with:</span></span>

-   <span data-ttu-id="f367b-167">**logical_record_level_conflict_detection** 을 TRUE로 설정</span><span class="sxs-lookup"><span data-stu-id="f367b-167">**logical_record_level_conflict_detection** is TRUE</span></span>

-   <span data-ttu-id="f367b-168">**logical_record_level_conflict_resolution** 을 TRUE로 설정</span><span class="sxs-lookup"><span data-stu-id="f367b-168">**logical_record_level_conflict_resolution** is TRUE</span></span>

 <span data-ttu-id="f367b-169">게시자 및 구독자는 동일한 데이터 집합으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-169">A Publisher and Subscriber start with the same data set.</span></span> <span data-ttu-id="f367b-170">게시자는 **customers** 테이블에서 **custcol1** 열을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-170">The Publisher changes the **custcol1** column in the **customers** table.</span></span> <span data-ttu-id="f367b-171">구독자는 **orders** 테이블에서 **ordercol1** 열을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-171">The Subscriber changes the **ordercol1** column in the **orders** table.</span></span> <span data-ttu-id="f367b-172">동일한 행 또는 열이 변경되지 않았지만 **custid**=1에 대한 동일한 논리적 레코드가 변경되었으므로 논리적 레코드 수준에서 변경 내용이 충돌로 감지됩니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-172">There are no changes to the same row or columns, but because the changes are made in the same logical record for **custid**=1, the changes are detected as a conflict at the logical record level.</span></span>

 <span data-ttu-id="f367b-173">또한 논리적 레코드 수준에서 충돌이 해결되므로 동기화 중 게시자에서 적용되는 변경 내용이 구독자 테이블에서의 변경 내용을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f367b-173">Because the conflicts are also resolved at the logical record level, during synchronization the winning change made at the Publisher replaces the change made in the Subscriber tables.</span></span>

 <span data-ttu-id="f367b-174">![관련 행의 변경 내용을 보여 주는 일련의 테이블](../media/logical-records-08.gif "관련 행의 변경 내용을 보여 주는 일련의 테이블")</span><span class="sxs-lookup"><span data-stu-id="f367b-174">![Series of tables showing changes to related rows](../media/logical-records-08.gif "Series of tables showing changes to related rows")</span></span>

## <a name="see-also"></a><span data-ttu-id="f367b-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f367b-175">See Also</span></span>
 [<span data-ttu-id="f367b-176">논리적 레코드를 사용하여 관련된 행의 변경 내용 그룹화</span><span class="sxs-lookup"><span data-stu-id="f367b-176">Group Changes to Related Rows with Logical Records</span></span>](group-changes-to-related-rows-with-logical-records.md)


