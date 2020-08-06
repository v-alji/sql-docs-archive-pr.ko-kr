---
title: 병합 테이블 아티클 간의 논리적 레코드 관계 정의 | Microsoft 문서
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication logical records [SQL Server replication]
- articles [SQL Server replication], logical records
- logical records [SQL Server replication]
ms.assetid: ff847b3a-c6b0-4eaf-b225-2ffc899c5558
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60c92a237562704e5bc5d43717f863aa78a14b55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741787"
---
# <a name="define-a-logical-record-relationship-between-merge-table-articles"></a><span data-ttu-id="4d7f3-102">병합 테이블 아티클 간의 논리적 레코드 관계 정의</span><span class="sxs-lookup"><span data-stu-id="4d7f3-102">Define a Logical Record Relationship Between Merge Table Articles</span></span>
  <span data-ttu-id="4d7f3-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 테이블 아티클 간 논리적 레코드 관계를 정의하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-103">This topic describes how to define a logical record relationship between merge table articles in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="4d7f3-104">병합 복제를 사용하면 서로 다른 테이블에 있는 관련 행 간의 관계를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-104">Merge replication allows you to define a relationship between related rows in different tables.</span></span> <span data-ttu-id="4d7f3-105">그러면 동기화 중에 이러한 행을 하나의 트랜잭션 단위로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-105">These rows can then be processed as a transactional unit during synchronization.</span></span> <span data-ttu-id="4d7f3-106">논리적 레코드는 조인 필터 관계가 있는지 여부와 관계없이 두 아티클 간에 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-106">A logical record can be defined between two articles whether or not they have a join filter relationship.</span></span> <span data-ttu-id="4d7f3-107">자세한 내용은 [논리적 레코드를 사용하여 관련된 행의 변경 내용 그룹화](../merge/group-changes-to-related-rows-with-logical-records.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-107">For more information, see [Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="4d7f3-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="4d7f3-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4d7f3-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="4d7f3-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4d7f3-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4d7f3-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="4d7f3-111">**다음을 사용하여 병합 테이블 아티클 간의 논리적 레코드 관계를 정의하려면**</span><span class="sxs-lookup"><span data-stu-id="4d7f3-111">**To define a logical record relationship between merge table articles, using:**</span></span>  
  
     [<span data-ttu-id="4d7f3-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4d7f3-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4d7f3-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4d7f3-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="4d7f3-114">RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="4d7f3-114">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4d7f3-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="4d7f3-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4d7f3-116">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4d7f3-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="4d7f3-117">게시에 대한 구독이 초기화된 후 논리적 레코드를 추가, 수정 또는 삭제한 경우에는 변경 내용을 적용한 후에 새 스냅샷을 생성하고 모든 구독을 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-117">If you add, modify, or delete a logical record after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="4d7f3-118">속성 변경 요구 사항에 대한 자세한 내용은 [게시 및 아티클 속성 변경](change-publication-and-article-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-118">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4d7f3-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="4d7f3-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="4d7f3-120">새 게시 마법사 및 **게시 속성 - \<Publication>** 대화 상자에서 사용할 수 있는 **조인 추가** 대화 상자에서 논리적 레코드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-120">Define logical records in the **Add Join** dialog box, which is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="4d7f3-121">마법사 사용 및 대화 상자 액세스에 대한 자세한 내용은 [게시 만들기](create-a-publication.md) 및 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-121">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
 <span data-ttu-id="4d7f3-122">논리적 레코드가 병합 게시의 조인 필터에 적용되고 게시가 사전 계산 파티션을 사용하기 위한 요구 사항을 따르는 경우에만 **조인 추가** 대화 상자에서 논리적 레코드를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-122">Logical records can be defined in the **Add Join** dialog box only if they are applied to a join filter in a merge publication, and the publication follows the requirements for using precomputed partitions.</span></span> <span data-ttu-id="4d7f3-123">조인 필터에 적용되지 않는 논리적 레코드를 정의하고 논리적 레코드 수준에서 충돌 감지 및 해결을 설정하려면 저장 프로시저를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-123">To define logical records that are not applied to join filters and to set conflict detection and resolution at the logical record level, you must use stored procedures.</span></span>  
  
#### <a name="to-define-a-logical-record-relationship"></a><span data-ttu-id="4d7f3-124">논리적 레코드 관계를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="4d7f3-124">To define a logical record relationship</span></span>  
  
1.  <span data-ttu-id="4d7f3-125">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자의 **행 필터** 페이지에 있는 **필터링된 테이블** 창에서 행 필터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-125">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, select a row filter in the **Filtered Tables** pane.</span></span>  
  
     <span data-ttu-id="4d7f3-126">논리적 레코드 관계는 조인 필터와 연결된 행 필터를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-126">A logical record relationship is associated with a join filter, which extends a row filter.</span></span> <span data-ttu-id="4d7f3-127">따라서 조인 필터로 확장하기 전에 행 필터를 정의한 다음 논리적 레코드 관계를 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-127">Therefore you must define a row filter before you can extend the filter with a join and apply a logical record relationship.</span></span> <span data-ttu-id="4d7f3-128">한 조인 필터를 정의한 후에 다른 조인 필터를 사용하여 이 조인 필터를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-128">After one join filter is defined, you can extend this join filter with another join filter.</span></span> <span data-ttu-id="4d7f3-129">조인 필터 정의 방법은 [병합 아티클 사이에서 조인 필터 정의 및 수정](define-and-modify-a-join-filter-between-merge-articles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-129">For more information about defining join filters, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
2.  <span data-ttu-id="4d7f3-130">**추가**를 클릭한 다음 **선택한 필터 확장을 위해 조인 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-130">Click **Add**, and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
3.  <span data-ttu-id="4d7f3-131">**조인 추가** 대화 상자에서 조인 필터를 정의한 다음 **논리적 레코드**확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-131">Define a join filter in the **Add Join** dialog box, and then select the check box **Logical Record**.</span></span>  
  
4.  <span data-ttu-id="4d7f3-132">**게시 속성 - \<Publication>** 대화 상자에서 **확인**을 클릭하여 저장하고 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-132">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-delete-a-logical-record-relationship"></a><span data-ttu-id="4d7f3-133">논리적 레코드 관계를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="4d7f3-133">To delete a logical record relationship</span></span>  
  
-   <span data-ttu-id="4d7f3-134">논리적 레코드 관계만 삭제하거나 논리적 레코드 관계 및 이와 관련된 조인 필터를 함께 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-134">Delete only the logical record relationship or delete the logical record relationship and the join filter associated with it.</span></span>  
  
     <span data-ttu-id="4d7f3-135">논리적 레코드 관계만 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="4d7f3-135">To delete only the logical record relationship:</span></span>  
  
    1.  <span data-ttu-id="4d7f3-136">새 게시 마법사의 **행 필터** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자의 **행 필터** 페이지에 있는 **필터링된 테이블** 창에서 논리적 레코드 관계와 연결된 조인 필터를 선택하고 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-136">On the **Filter Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, select the join filter associated with the logical record relationship in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
    2.  <span data-ttu-id="4d7f3-137">**조인 편집** 대화 상자에서 **논리적 레코드**확인란 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-137">In the **Edit Join** dialog box, clear the check box **Logical Record**.</span></span>  
  
    3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="4d7f3-138">논리적 레코드 관계 및 이와 관련된 조인 필터를 함께 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="4d7f3-138">To delete the logical record relationship and join filter associated with it:</span></span>  
  
    -   <span data-ttu-id="4d7f3-139">새 게시 마법사의 **행 필터** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자의 **필터링된 테이블** 창에서 필터를 선택하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-139">On the **Filter Rows** page of the New Publication Wizard or **Publication Properties - \<Publication>** dialog box, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span> <span data-ttu-id="4d7f3-140">삭제하는 조인 필터가 다른 조인에 의해 확장된 경우 해당 조인 또한 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-140">If the join filter you delete is itself extended by other joins, those joins will also be deleted.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4d7f3-141">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="4d7f3-141">Using Transact-SQL</span></span>  
 <span data-ttu-id="4d7f3-142">복제 저장 프로시저를 사용하여 아티클 간 논리적 레코드 관계를 프로그래밍 방식으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-142">You can programmatically specify logical record relationships between articles using replication stored procedures.</span></span>  
  
#### <a name="to-define-a-logical-record-relationship-without-an-associated-join-filter"></a><span data-ttu-id="4d7f3-143">관련된 조인 필터 없이 논리적 레코드 관계를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="4d7f3-143">To define a logical record relationship without an associated join filter</span></span>  
  
1.  <span data-ttu-id="4d7f3-144">게시에 필터링된 아티클이 포함되어 있으면 [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)을 실행하고 결과 집합에서 **use_partition_groups** 의 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-144">If the publication contains any articles that are filtered, execute [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), and note the value of **use_partition_groups** in the result set.</span></span>  
  
    -   <span data-ttu-id="4d7f3-145">이 값이 **1**이면 사전 계산 파티션이 이미 사용되고 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-145">If the value is **1**, then precomputed partitions are already being used.</span></span>  
  
    -   <span data-ttu-id="4d7f3-146">이 값이 **0**이면 게시 데이터베이스의 게시자에서 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) 을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-146">If the value is **0**, then execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="4d7f3-147">**@property**에 **use_partition_groups** 값을, **@value**에 **true** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-147">Specify a value of **use_partition_groups** for **@property** and a value of **true** for **@value**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="4d7f3-148">게시에서 사전 계산 파티션을 지원하지 않으면 논리적 레코드를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-148">If the publication does not support precomputed partitions, then logical records cannot be used.</span></span> <span data-ttu-id="4d7f3-149">자세한 내용은 [사전 계산 파티션으로 매개 변수가 있는 필터 성능 최적화](../merge/parameterized-filters-optimize-for-precomputed-partitions.md) 항목에서 사전 계산 파티션을 사용하기 위한 요구 사항을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-149">For more information, see Requirements for Using Precomputed Partitions in the topic [Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span>  
  
    -   <span data-ttu-id="4d7f3-150">이 값이 NULL이면 스냅샷 에이전트를 실행하여 게시에 대한 초기 스냅샷을 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-150">If the value is NULL, then the Snapshot Agent needs to be run to generate the initial snapshot for the publication.</span></span>  
  
2.  <span data-ttu-id="4d7f3-151">논리적 레코드를 구성하는 아티클이 없으면 게시 데이터베이스의 게시자에서 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-151">If the articles that will comprise the logical record do not exist, execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="4d7f3-152">논리적 레코드에 대해 다음 충돌 감지 및 해결 옵션 중 하나를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-152">Specify one of the following conflict detection and resolution options for the logical record:</span></span>  
  
    -   <span data-ttu-id="4d7f3-153">논리적 레코드의 관련 행 내에서 발생하는 충돌을 감지하여 해결하려면 **@value** 에 **@logical_record_level_conflict_detection** 및 **@logical_record_level_conflict_resolution**을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-153">To detect and resolve conflicts that occur within related rows in the logic record, specify a value of **true** for **@logical_record_level_conflict_detection** and **@logical_record_level_conflict_resolution**.</span></span>  
  
    -   <span data-ttu-id="4d7f3-154">표준 행 수준 또는 열 수준 충돌 검색 및 해결을 사용 하려면 `false` 기본값인 및에 값을 지정 합니다 **@logical_record_level_conflict_detection** **@logical_record_level_conflict_resolution** .</span><span class="sxs-lookup"><span data-stu-id="4d7f3-154">To use the standard row- or column-level conflict detection and resolution, specify a value of `false` for **@logical_record_level_conflict_detection** and **@logical_record_level_conflict_resolution**, which is the default.</span></span>  
  
3.  <span data-ttu-id="4d7f3-155">논리적 레코드를 구성하는 각 아티클에 대해 2단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-155">Repeat step 2 for each article that will comprise the logical record.</span></span> <span data-ttu-id="4d7f3-156">논리적 레코드의 각 아티클에 대해 동일한 충돌 감지 및 해결 옵션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-156">You must use the same conflict detection and resolution option for each article in the logical record.</span></span> <span data-ttu-id="4d7f3-157">자세한 내용은 [논리적 레코드에서 충돌 감지 및 해결](../merge/advanced-merge-replication-conflict-resolving-in-logical-record.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-157">For more information, see [Detecting and Resolving Conflicts in Logical Records](../merge/advanced-merge-replication-conflict-resolving-in-logical-record.md).</span></span>  
  
4.  <span data-ttu-id="4d7f3-158">게시 데이터베이스의 게시자에서 [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-158">At the publisher on the publication database, execute [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql).</span></span> <span data-ttu-id="4d7f3-159">을 지정 하 고에 **@publication** 관계에서 한 아티클의 이름을, **@article** 에 두 번째 아티클의 이름을,에 관계의 이름을,에 **@join_articlename** **@filtername** 두 아티클 간의 관계를 정의 하는 절,에 대 한 **@join_filterclause** 조인 유형 **@join_unique_key** 및 다음 값 중 하나 **@filter_type** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-159">Specify **@publication**, the name of one article in the relationship for **@article**, the name of the second article for **@join_articlename**, a name for the relationship for **@filtername**, a clause that defines the relationship between the two articles for **@join_filterclause**, the type of join for **@join_unique_key** and one of the following values for **@filter_type**:</span></span>  
  
    -   <span data-ttu-id="4d7f3-160">**2** - 논리적 관계를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-160">**2** - Defines a logical relationship.</span></span>  
  
    -   <span data-ttu-id="4d7f3-161">**3** - 조인 필터를 포함하는 논리적 관계를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-161">**3** - Defines a logical relationship with a join filter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4d7f3-162">조인 필터를 사용하지 않는 경우 두 아티클 간의 관계 방향은 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-162">If a join filter is not used, the direction of the relationship between the two articles is not important.</span></span>  
  
5.  <span data-ttu-id="4d7f3-163">게시에서 남은 각각의 논리적 레코드 관계에 대해 2단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-163">Repeat step 2 for each remaining logical record relationship in the publication.</span></span>  
  
#### <a name="to-change-conflict-detection-and-resolution-for-logical-records"></a><span data-ttu-id="4d7f3-164">논리적 레코드에 대한 충돌 감지 및 해결을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="4d7f3-164">To change conflict detection and resolution for logical records</span></span>  
  
1.  <span data-ttu-id="4d7f3-165">논리적 레코드의 관련 행 내에서 발생하는 충돌을 감지하고 해결하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-165">To detect and resolve conflicts that occur within related rows in the logical record:</span></span>  
  
    -   <span data-ttu-id="4d7f3-166">게시 데이터베이스의 게시자에서 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-166">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="4d7f3-167">**@property**에 **logical_record_level_conflict_detection** 값을, **@value**에 **true** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-167">Specify a value of **logical_record_level_conflict_detection** for **@property** and a value of **true** for **@value**.</span></span> <span data-ttu-id="4d7f3-168">**@force_invalidate_snapshot** 및 **@force_reinit_subscription**에 **1** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-168">Specify a value of **1** for **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
    -   <span data-ttu-id="4d7f3-169">게시 데이터베이스의 게시자에서 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-169">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="4d7f3-170">**@property**에 **logical_record_level_conflict_resolution** 값을, **@value**에 **true** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-170">Specify a value of **logical_record_level_conflict_resolution** for **@property** and a value of **true** for **@value**.</span></span> <span data-ttu-id="4d7f3-171">**@force_invalidate_snapshot** 및 **@force_reinit_subscription**에 **1** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-171">Specify a value of **1** for **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="4d7f3-172">표준 행 수준 또는 열 수준의 충돌 감지 및 해결을 사용하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-172">To use the standard row-level or column-level conflict detection and resolution:</span></span>  
  
    -   <span data-ttu-id="4d7f3-173">게시 데이터베이스의 게시자에서 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-173">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="4d7f3-174">에 **logical_record_level_conflict_detection** 값을 지정 **@property** 하 고에 값을 `false` 지정 **@value** 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-174">Specify a value of **logical_record_level_conflict_detection** for **@property** and a value of `false` for **@value**.</span></span> <span data-ttu-id="4d7f3-175">**@force_invalidate_snapshot** 및 **@force_reinit_subscription**에 **1** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-175">Specify a value of **1** for **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
    -   <span data-ttu-id="4d7f3-176">게시 데이터베이스의 게시자에서 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-176">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="4d7f3-177">에 **logical_record_level_conflict_resolution** 값을 지정 **@property** 하 고에 값을 `false` 지정 **@value** 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-177">Specify a value of **logical_record_level_conflict_resolution** for **@property** and a value of `false` for **@value**.</span></span> <span data-ttu-id="4d7f3-178">**@force_invalidate_snapshot** 및 **@force_reinit_subscription**에 **1** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-178">Specify a value of **1** for **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
#### <a name="to-remove-a-logical-record-relationship"></a><span data-ttu-id="4d7f3-179">논리적 레코드 관계를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="4d7f3-179">To remove a logical record relationship</span></span>  
  
1.  <span data-ttu-id="4d7f3-180">게시 데이터베이스의 게시자에서 다음 쿼리를 실행하여 지정된 게시에 대해 정의된 모든 논리적 레코드 관계 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-180">At the Publisher on the publication database, execute the following query to return information about all logical record relationships defined for the specified publication:</span></span>  
  
     [!code-sql[HowTo#sp_ReturnMergeLogicalRecords](../../../snippets/tsql/SQL15/replication/howto/tsql/createlogicalrecordpub.sql#sp_returnmergelogicalrecords)]  
  
     <span data-ttu-id="4d7f3-181">결과 집합의 `filtername` 열에서 제거되고 있는 논리적 레코드 관계의 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-181">Note the name of the logical record relationship being removed in the `filtername` column in the result set.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4d7f3-182">이 쿼리는 [sp_helpmergefilter](/sql/relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql)와 동일한 정보를 반환하지만, 이 시스템 저장 프로시저는 조인 필터이기도 한 논리적 레코드 관계에 대한 정보만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-182">This query returns the same information as [sp_helpmergefilter](/sql/relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql); however, this system stored procedure only returns information about logical record relationships that are also join filters.</span></span>  
  
2.  <span data-ttu-id="4d7f3-183">게시 데이터베이스의 게시자에서 [sp_dropmergefilter](/sql/relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-183">At the Publisher on the publication database, execute [sp_dropmergefilter](/sql/relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql).</span></span> <span data-ttu-id="4d7f3-184">을 지정 하 **@publication** 고에 대 한 관계에 있는 아티클 중 하나의 이름을, **@article** 에 대해 1 단계에서 가져온 관계의 이름을 지정 합니다 **@filtername** .</span><span class="sxs-lookup"><span data-stu-id="4d7f3-184">Specify **@publication**, the name of one of the articles in the relationship for **@article**, and the name of the relationship from step 1 for **@filtername**.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="4d7f3-185">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4d7f3-185">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="4d7f3-186">이 예에서는 기존 게시에 사전 계산 파티션을 사용하고 `SalesOrderHeader` 및 `SalesOrderDetail` 테이블에 대한 두 개의 새 아티클을 구성하는 논리적 레코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-186">This example enables precomputed partitions on an existing publication, and creates a logical record comprising the two new articles for the `SalesOrderHeader` and `SalesOrderDetail` tables.</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeLogicalRecord](../../../snippets/tsql/SQL15/replication/howto/tsql/createlogicalrecordpub.sql#sp_addmergelogicalrecord)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="4d7f3-187">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="4d7f3-187">Using Replication Management Objects (RMO)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d7f3-188">병합 복제를 사용하면 충돌을 추적하고 논리적 레코드 수준에서 충돌을 해결하도록 지정할 수도 있지만 RMO를 사용하는 경우에는 이러한 옵션을 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-188">Merge replication allows you to specify that conflicts be tracked and resolved at the logical record level, but these options cannot be set using RMO.</span></span>  
  
#### <a name="to-define-a-logical-record-relationship-without-an-associated-join-filter"></a><span data-ttu-id="4d7f3-189">관련된 조인 필터 없이 논리적 레코드 관계를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="4d7f3-189">To define a logical record relationship without an associated join filter</span></span>  
  
1.  <span data-ttu-id="4d7f3-190"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-190">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="4d7f3-191"><xref:Microsoft.SqlServer.Replication.MergePublication> 클래스의 인스턴스를 만들고 게시에 대한 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 및 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 속성을 설정한 다음, 1단계에서 만든 연결에 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-191">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class, set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
3.  <span data-ttu-id="4d7f3-192"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-192">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="4d7f3-193">이 메서드가 `false`를 반환하는 경우 2단계에서 게시 속성이 올바르게 정의되지 않았거나 게시가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-193">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="4d7f3-194"><xref:Microsoft.SqlServer.Replication.MergePublication.PartitionGroupsOption%2A> 속성이 <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.False>로 설정된 경우 <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.True>로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-194">If the <xref:Microsoft.SqlServer.Replication.MergePublication.PartitionGroupsOption%2A> property is set to <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.False>, set it to <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.True>.</span></span>  
  
5.  <span data-ttu-id="4d7f3-195">논리적 레코드를 구성하는 아티클이 없으면 <xref:Microsoft.SqlServer.Replication.MergeArticle> 클래스의 인스턴스를 만들고 다음 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-195">If the articles that are to comprise the logical record do not exist, create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class, and set the following properties:</span></span>  
  
    -   <span data-ttu-id="4d7f3-196"><xref:Microsoft.SqlServer.Replication.Article.Name%2A>에 대한 아티클의 이름</span><span class="sxs-lookup"><span data-stu-id="4d7f3-196">The name of the article for <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.</span></span>  
  
    -   <span data-ttu-id="4d7f3-197"><xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>에 대한 게시의 이름</span><span class="sxs-lookup"><span data-stu-id="4d7f3-197">The name of the publication for <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="4d7f3-198">(옵션) 아티클이 행 필터링된 경우 <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> 속성에 대해 행 필터 절을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-198">(Optional) If the article is horizontally filtered, specify the row filter clause for the <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> property.</span></span> <span data-ttu-id="4d7f3-199">이 속성을 사용하여 정적 또는 매개 변수가 있는 행 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-199">Use this property to specify a static or parameterized row filter.</span></span> <span data-ttu-id="4d7f3-200">자세한 내용은 [매개 변수가 있는 행 필터](../merge/parameterized-filters-parameterized-row-filters.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-200">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
     <span data-ttu-id="4d7f3-201">자세한 내용은 [아티클을 정의](define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-201">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
6.  <span data-ttu-id="4d7f3-202"><xref:Microsoft.SqlServer.Replication.Article.Create%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-202">Call the <xref:Microsoft.SqlServer.Replication.Article.Create%2A> method.</span></span>  
  
7.  <span data-ttu-id="4d7f3-203">논리적 레코드를 구성하는 각 아티클별로 5단계와 6단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-203">Repeat steps 5 and 6 for each article comprising the logical record.</span></span>  
  
8.  <span data-ttu-id="4d7f3-204"><xref:Microsoft.SqlServer.Replication.MergeJoinFilter> 클래스의 인스턴스를 만들어 아티클 간 논리적 레코드 관계를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-204">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> class to define the logical record relationship between articles.</span></span> <span data-ttu-id="4d7f3-205">그런 후 다음 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-205">Then, set the following properties:</span></span>  
  
    -   <span data-ttu-id="4d7f3-206"><xref:Microsoft.SqlServer.Replication.MergeJoinFilter.ArticleName%2A> 속성에서 논리적 레코드 관계의 하위 아티클 이름.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-206">The name of the child article in the logical record relationship for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.ArticleName%2A> property.</span></span>  
  
    -   <span data-ttu-id="4d7f3-207"><xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinArticleName%2A> 속성에서 논리적 레코드 관계의 기존 상위 아티클 이름.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-207">The name of the existing, parent article in the logical record relationship for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinArticleName%2A> property.</span></span>  
  
    -   <span data-ttu-id="4d7f3-208"><xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterName%2A> 속성에서 논리적 레코드 관계 이름.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-208">A name for the logical record relationship for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterName%2A> property.</span></span>  
  
    -   <span data-ttu-id="4d7f3-209"><xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinFilterClause%2A> 속성에서 관계를 정의하는 식.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-209">The expression that defines the relationship for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinFilterClause%2A> property.</span></span>  
  
    -   <span data-ttu-id="4d7f3-210"><xref:Microsoft.SqlServer.Replication.FilterTypes.LogicalRecordLink> 속성에서 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterTypes%2A> 값.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-210">A value of <xref:Microsoft.SqlServer.Replication.FilterTypes.LogicalRecordLink> for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterTypes%2A> property.</span></span> <span data-ttu-id="4d7f3-211">논리적 레코드 관계가 조인 필터이기도 한 경우 이 속성에 <xref:Microsoft.SqlServer.Replication.FilterTypes.JoinFilterAndLogicalRecordLink> 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-211">If the logical record relationship is also a join filter, specify a value of <xref:Microsoft.SqlServer.Replication.FilterTypes.JoinFilterAndLogicalRecordLink> for this property.</span></span> <span data-ttu-id="4d7f3-212">자세한 내용은 [논리적 레코드를 사용하여 관련된 행의 변경 내용 그룹화](../merge/group-changes-to-related-rows-with-logical-records.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-212">For more information, see [Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
9. <span data-ttu-id="4d7f3-213">관계의 하위 아티클을 나타내는 개체에서 <xref:Microsoft.SqlServer.Replication.MergeArticle.AddMergeJoinFilter%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-213">Call the <xref:Microsoft.SqlServer.Replication.MergeArticle.AddMergeJoinFilter%2A> method on the object that represents the child article in the relationship.</span></span> <span data-ttu-id="4d7f3-214">8단계에서 만든 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> 개체를 전달하여 관계를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-214">Pass the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> object from step 8 to define the relationship.</span></span>  
  
10. <span data-ttu-id="4d7f3-215">게시의 나머지 논리적 레코드 관계별로 8단계와 9단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-215">Repeat steps 8 and 9 for each remaining logical record relationship in the publication.</span></span>  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="4d7f3-216">예(RMO)</span><span class="sxs-lookup"><span data-stu-id="4d7f3-216">Example (RMO)</span></span>  
 <span data-ttu-id="4d7f3-217">이 예제에서는 `SalesOrderHeader` 및 `SalesOrderDetail` 테이블의 새 아티클 두 개를 구성하는 논리적 레코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4d7f3-217">This example creates a logical record comprising the two new articles for the `SalesOrderHeader` and `SalesOrderDetail` tables.</span></span>  
  
 [!code-csharp[HowTo#rmo_CreateLogicalRecord](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createlogicalrecord)]  
  
 [!code-vb[HowTo#rmo_vb_CreateLogicalRecord](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createlogicalrecord)]  
  
## <a name="see-also"></a><span data-ttu-id="4d7f3-218">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4d7f3-218">See Also</span></span>  
 <span data-ttu-id="4d7f3-219">[병합 아티클 사이에서 조인 필터 정의 및 수정](define-and-modify-a-join-filter-between-merge-articles.md) </span><span class="sxs-lookup"><span data-stu-id="4d7f3-219">[Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md) </span></span>  
 <span data-ttu-id="4d7f3-220">[병합 아티클에 대한 매개 변수가 있는 행 필터 정의 및 수정](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="4d7f3-220">[Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span></span>  
 <span data-ttu-id="4d7f3-221">[정적 행 필터 정의 및 수정](define-and-modify-a-static-row-filter.md) </span><span class="sxs-lookup"><span data-stu-id="4d7f3-221">[Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) </span></span>  
 <span data-ttu-id="4d7f3-222">[논리적 레코드를 사용하여 관련된 행의 변경 내용 그룹화](../merge/group-changes-to-related-rows-with-logical-records.md) </span><span class="sxs-lookup"><span data-stu-id="4d7f3-222">[Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md) </span></span>  
 <span data-ttu-id="4d7f3-223">[사전 계산 파티션으로 매개 변수가 있는 필터 성능 최적화](../merge/parameterized-filters-optimize-for-precomputed-partitions.md) </span><span class="sxs-lookup"><span data-stu-id="4d7f3-223">[Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md) </span></span>  
 [<span data-ttu-id="4d7f3-224">논리적 레코드를 사용하여 관련된 행의 변경 내용 그룹화</span><span class="sxs-lookup"><span data-stu-id="4d7f3-224">Group Changes to Related Rows with Logical Records</span></span>](../merge/group-changes-to-related-rows-with-logical-records.md)  
  
  
