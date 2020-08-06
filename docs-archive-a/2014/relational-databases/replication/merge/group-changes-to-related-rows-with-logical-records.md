---
title: 논리적 레코드를 사용하여 관련된 행의 변경 내용 그룹화 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication logical records [SQL Server replication]
- articles [SQL Server replication], logical records
- logical records [SQL Server replication]
ms.assetid: ad76799c-4486-4b98-9705-005433041321
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 433e0edbe83d102e6002bd133f967f27a236f66e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638711"
---
# <a name="group-changes-to-related-rows-with-logical-records"></a><span data-ttu-id="23dd7-102">논리적 레코드를 사용하여 관련된 행의 변경 내용 그룹화</span><span class="sxs-lookup"><span data-stu-id="23dd7-102">Group Changes to Related Rows with Logical Records</span></span>
  
> [!NOTE]
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]

 <span data-ttu-id="23dd7-103">기본적으로 병합 복제는 행 단위로 데이터 변경 내용을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-103">By default, merge replication processes data changes on a row-by-row basis.</span></span> <span data-ttu-id="23dd7-104">대부분의 경우 이 방법이 적합하지만 일부 애플리케이션에서는 관련된 행을 하나의 단위로 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-104">In many circumstances this is appropriate, but for some applications, it is essential that related rows be processed as a unit.</span></span> <span data-ttu-id="23dd7-105">병합 복제의 논리적 레코드 기능을 사용하면 서로 다른 테이블에 있는 관련 행 간의 관계를 정의하여 이러한 행을 하나의 단위로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-105">The logical records feature of merge replication allows you to define a relationship between related rows in different tables so that the rows are processed as a unit.</span></span>

> [!NOTE]
>  <span data-ttu-id="23dd7-106">논리적 레코드 기능은 단독으로 사용되거나 조인 필터와 함께 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-106">The logical records feature can be used alone or in conjunction with join filters.</span></span> <span data-ttu-id="23dd7-107">조인 필터에 대한 자세한 내용은 [Join Filters](join-filters.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="23dd7-107">For more information about join filters, see [Join Filters](join-filters.md).</span></span> <span data-ttu-id="23dd7-108">논리적 레코드를 사용하려면 게시의 호환성 수준이 적어도 90RTM 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-108">To use logical records, the compatibility level of the publication must be at least 90RTM.</span></span>

 <span data-ttu-id="23dd7-109">다음과 같은 3개의 관련된 테이블을 살펴보십시오.</span><span class="sxs-lookup"><span data-stu-id="23dd7-109">Consider these three related tables:</span></span>

 <span data-ttu-id="23dd7-110">![열 이름만 포함하는 3개 테이블 논리적 레코드](../media/logical-records-01.gif "열 이름만 포함하는 3개 테이블 논리적 레코드")</span><span class="sxs-lookup"><span data-stu-id="23dd7-110">![Three table logical record, with column names only](../media/logical-records-01.gif "Three table logical record, with column names only")</span></span>

 <span data-ttu-id="23dd7-111">이 관계의 부모 테이블인 **Customers** 테이블에는 기본 키 열 **CustID**가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-111">The **Customers** table is the parent table in this relationship and has a primary key column **CustID**.</span></span> <span data-ttu-id="23dd7-112">**Orders** 테이블에는 기본 키 열 **OrderID**가 있으며 **Customers** 테이블의 **CustID** 열을 참조하는 FOREIGN KEY 제약 조건이 이 테이블의 **CustID** 열에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-112">The **Orders** table has a primary key column **OrderID**, with a foreign key constraint on the **CustID** column that references the **CustID** column in the **Customers** table.</span></span> <span data-ttu-id="23dd7-113">마찬가지로 **OrderItems** 테이블에는 기본 키 열 **OrderItemID**가 있으며 **Orders** 테이블의 **OrderID** 열을 참조하는 FOREIGN KEY 제약 조건이 이 테이블의 **OrderID** 열에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-113">Similarly, the **OrderItems** table has a primary key column **OrderItemID**, with a foreign key constraint on the **OrderID** column that references the **OrderID** column in the **Orders** table.</span></span>

 <span data-ttu-id="23dd7-114">이 예에서 논리적 레코드는 단일 **CustID** 값에 관련된 **Orders** 테이블의 모든 행 및 **Orders** 테이블의 해당 행과 관련된 **OrderItems** 테이블의 모든 행으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-114">In this example, a logical record consists of all the rows in the **Orders** table that are related to a single **CustID** value and all of the rows in the **OrderItems** table that are related to those rows in the **Orders** table.</span></span> <span data-ttu-id="23dd7-115">이 다이어그램에서는 Customer2에 대한 논리적 레코드에 있는 3개 테이블의 모든 행을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-115">This diagram shows all the rows in the three tables that are in the logical record for Customer2:</span></span>

 <span data-ttu-id="23dd7-116">![값을 포함하는 3개 테이블 논리적 레코드](../media/logical-records-02.gif "값을 포함하는 3개 테이블 논리적 레코드")</span><span class="sxs-lookup"><span data-stu-id="23dd7-116">![Three table logical record with values](../media/logical-records-02.gif "Three table logical record with values")</span></span>

 <span data-ttu-id="23dd7-117">아티클 간 논리적 레코드 관계를 정의하려면 [병합 테이블 기사 간의 논리적 레코드 관계 정의](../publish/define-a-logical-record-relationship-between-merge-table-articles.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="23dd7-117">To define a logical record relationship between articles, see [Define a Logical Record Relationship Between Merge Table Articles](../publish/define-a-logical-record-relationship-between-merge-table-articles.md).</span></span>

## <a name="benefits-of-logical-records"></a><span data-ttu-id="23dd7-118">논리적 레코드의 장점</span><span class="sxs-lookup"><span data-stu-id="23dd7-118">Benefits of Logical Records</span></span>
 <span data-ttu-id="23dd7-119">논리적 레코드 기능에는 다음과 같은 두 가지 주요 장점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-119">The logical records feature has two primary benefits:</span></span>

-   <span data-ttu-id="23dd7-120">데이터 변경 내용을 하나의 단위로 적용</span><span class="sxs-lookup"><span data-stu-id="23dd7-120">Application of data changes as a unit.</span></span>

-   <span data-ttu-id="23dd7-121">여러 테이블의 여러 행에서 동시에 충돌 감지 및 해결</span><span class="sxs-lookup"><span data-stu-id="23dd7-121">The detection and resolution of conflicts simultaneously on multiple rows from multiple tables.</span></span>

### <a name="the-application-of-changes-as-a-unit"></a><span data-ttu-id="23dd7-122">변경 내용을 하나의 단위로 적용</span><span class="sxs-lookup"><span data-stu-id="23dd7-122">The Application of Changes As a Unit</span></span>
 <span data-ttu-id="23dd7-123">연결이 끊기는 경우와 같이 병합 프로세스가 중단되는 경우 논리적 레코드를 사용하면 관련 복제된 변경 내용 중 부분적으로 완료된 변경 내용 집합이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-123">If merge processing is interrupted, such as in the case of a dropped connection, the partially completed set of related replicated changes is rolled back if logical records are used.</span></span> <span data-ttu-id="23dd7-124">예를 들어 구독자가 **OrderID** = 6인 새 주문과 **OrderID** = 6에 대해 **OrderItemID** = 10 및 **OrderItemID** = 11인 두 개의 새 행을 **OrderItems** 테이블에 추가하는 경우를 살펴봅시다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-124">For example, consider the case where a Subscriber adds a new order with **OrderID** = 6 and two new rows in the **OrderItems** table with **OrderItemID** = 10 and **OrderItemID** = 11 for **OrderID** = 6.</span></span>

 <span data-ttu-id="23dd7-125">![값을 포함하는 3개 테이블 논리적 레코드](../media/logical-records-04.gif "값을 포함하는 3개 테이블 논리적 레코드")</span><span class="sxs-lookup"><span data-stu-id="23dd7-125">![Three table logical record with values](../media/logical-records-04.gif "Three table logical record with values")</span></span>

 <span data-ttu-id="23dd7-126">**OrderID** = 6에 대한 **Orders** 행은 완료되었지만 **OrderItems** 10 및 11이 완료되기 전에 복제 프로세스가 중단되고 논리적 레코드가 사용되지 않는 경우 **OrderID** = 6에 대한 **OrderTotal** 값이 **OrderItems** 행에 대한 **OrderAmount** 값의 합계와 일치하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-126">If the replication process is interrupted after the **Orders** row for **OrderID** = 6 is complete, but before the **OrderItems** 10 and 11 are completed, and logical records are not used, the **OrderTotal** value for **OrderID** = 6 will not be consistent with the sum of the **OrderAmount** values for the **OrderItems** rows.</span></span> <span data-ttu-id="23dd7-127">논리적 레코드가 사용되는 경우에는 관련 **OrderItems** 변경 내용이 복제될 때까지 **OrderID** = 6에 대한 **Orders** 행이 커밋되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-127">If logical records are used, the **Orders** row for **OrderID** = 6 is not committed until the related **OrderItems** changes are replicated.</span></span>

 <span data-ttu-id="23dd7-128">다른 시나리오에서 논리적 레코드가 사용되고 병합 프로세스가 변경 내용을 적용하는 동안 다른 사용자가 테이블을 쿼리하는 경우 부분적으로 복제된 변경 내용은 모두 완료될 때까지 사용자에게 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-128">In a different scenario, if logical records are used, and someone is querying tables when the merge process is applying changes, the user will not see the partially replicated changes until they are all complete.</span></span> <span data-ttu-id="23dd7-129">예를 들어 복제 프로세스가 **OrderID** = 6에 대한 Orders 행을 업로드했지만 복제 프로세스가 **OrderItems** 행을 복제하기 전에 사용자가 해당 테이블을 쿼리하는 경우 **OrderTotal** 값이 **OrderAmount** 값의 합계와 같지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-129">For example, the replication process has uploaded the Orders row for **OrderID** = 6, but a user queries the tables before the replication process has replicated the **OrderItems** rows, the **OrderTotal** value would not be the same as the sum of the **OrderAmount** values.</span></span> <span data-ttu-id="23dd7-130">논리적 레코드가 사용되는 경우 **OrderItems** 행이 완료되고 트랜잭션이 하나의 단위로 커밋될 때까지 **Orders** 행이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-130">If logical records are used, the **Orders** row would not be visible until the **OrderItems** rows are complete and the transaction has been committed as a unit.</span></span>

### <a name="the-application-of-conflict-handling-to-more-than-one-table"></a><span data-ttu-id="23dd7-131">둘 이상의 테이블에 대한 충돌 처리 적용</span><span class="sxs-lookup"><span data-stu-id="23dd7-131">The Application of Conflict Handling to More Than One Table</span></span>
 <span data-ttu-id="23dd7-132">두 구독자에 위의 데이터 집합이 있는 경우를 살펴봅시다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-132">Consider the case where two Subscribers have the data set above:</span></span>

-   <span data-ttu-id="23dd7-133">첫 번째 구독자의 사용자가 **OrderItemID** 5의 **OrderAmount** 를 100에서 150으로 변경하고 **OrderID** 3의 **OrderTotal** 을 200에서 250으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-133">A user at the first Subscriber changes the **OrderAmount** of **OrderItemID** 5 from 100 to 150 and the **OrderTotal** of **OrderID** 3 from 200 to 250.</span></span>

-   <span data-ttu-id="23dd7-134">두 번째 구독자의 사용자가 **OrderItemID** 6의 **OrderAmount** 를 25에서 125로 변경하고 **OrderID** 3의 **OrderTotal** 을 200에서 300으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-134">A user at the second Subscriber changes the **OrderAmount** of **OrderItemID** 6 from 25 to 125 and the **OrderTotal** of **OrderID** 3 from 200 to 300.</span></span>

 <span data-ttu-id="23dd7-135">이러한 변경 내용을 논리적 레코드를 사용하지 않고 복제하면 서로 다른 **OrderTotal** 값으로 인해 충돌이 발생하고 둘 중 하나만 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-135">If these changes are replicated without using logical records, the different **OrderTotal** values would result in a conflict and only one of them would be replicated.</span></span> <span data-ttu-id="23dd7-136">그러나 **OrderItems** 테이블의 충돌하지 않는 변경 내용은 충돌 발생 없이 복제되고 **OrderTotal** 의 최종값이 **OrderItems** 행에 대해 일치하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-136">But the non-conflicting changes in the **OrderItems** table would be replicated without conflict, leaving the final **OrderTotal** values in an inconsistent state with respect to the **OrderItems** rows.</span></span> <span data-ttu-id="23dd7-137">이 시나리오에서 논리적 레코드를 사용하면 **Orders** 테이블의 무시되는 변경 내용과 연결된 **OrderItems** 의 변경 내용도 롤백되므로 **OrderTotal** 의 최종값이 **OrderItems** 행의 합계와 일치하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-137">If logical records are used in this scenario, the **OrderItems** change associated with the losing **Orders** table change would also be rolled back, and the final **OrderTotal** value would be an accurate summary of the **OrderItems** rows.</span></span>

 <span data-ttu-id="23dd7-138">논리적 레코드를 사용하는 경우의 충돌 감지 및 해결과 관련된 옵션에 대한 자세한 내용은 [논리적 레코드에서 충돌 감지 및 해결](advanced-merge-replication-conflict-resolving-in-logical-record.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23dd7-138">For more information about options related to conflict detection and resolution with logical records, see [Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md).</span></span>

## <a name="considerations-for-using-logical-records"></a><span data-ttu-id="23dd7-139">논리적 레코드 사용 시 고려 사항</span><span class="sxs-lookup"><span data-stu-id="23dd7-139">Considerations for Using Logical Records</span></span>
 <span data-ttu-id="23dd7-140">논리적 레코드 사용 시 다음 사항을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="23dd7-140">Keep the following considerations in mind when using logical records.</span></span>

### <a name="general-considerations"></a><span data-ttu-id="23dd7-141">일반적인 고려 사항</span><span class="sxs-lookup"><span data-stu-id="23dd7-141">General Considerations</span></span>

-   <span data-ttu-id="23dd7-142">논리적 레코드의 테이블 수는 적을수록 좋으므로 테이블 수를 5개 이하로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-142">It is recommended that you keep the number of tables in a logical record as low as possible; five tables or less is recommended.</span></span>

-   <span data-ttu-id="23dd7-143">논리적 레코드는 다음 데이터 형식의 열은 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-143">Logical records cannot reference columns with any of the following data types:</span></span>

    -   <span data-ttu-id="23dd7-144">`varchar(max)` 및 `nvarchar(max)`</span><span class="sxs-lookup"><span data-stu-id="23dd7-144">`varchar(max)` and `nvarchar(max)`</span></span>

    -   `varbinary(max)`

    -   <span data-ttu-id="23dd7-145">`text` 및 `ntext`</span><span class="sxs-lookup"><span data-stu-id="23dd7-145">`text` and `ntext`</span></span>

    -   `image`

    -   `XML`

    -   `UDT`

-   <span data-ttu-id="23dd7-146">게시된 테이블의 외래 키 관계는 CASCADE 옵션으로 정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-146">Foreign key relationships in published tables cannot be defined with the CASCADE option.</span></span> <span data-ttu-id="23dd7-147">자세한 내용은 [CREATE TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) 및 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23dd7-147">For more information, see [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) and [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>

-   <span data-ttu-id="23dd7-148">논리적 관계 절에 사용되는 열은 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-148">You cannot update any columns that are used in the logical relation clause.</span></span>

-   <span data-ttu-id="23dd7-149">논리적 레코드에 포함된 아티클에 대해서는 비즈니스 논리 처리기 또는 사용자 지정 해결 프로그램을 사용하는 사용자 지정 충돌 해결이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-149">Custom conflict resolution with business logic handlers or custom resolvers is not supported for articles that are included in a logical record.</span></span>

-   <span data-ttu-id="23dd7-150">매개 변수가 있는 필터를 포함하는 게시에서 논리적 레코드를 사용하는 경우에는 각 구독자를 해당 파티션에 대한 스냅샷으로 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-150">If logical records are used in a publication that includes parameterized filters, you must initialize each Subscriber with a snapshot for its partition.</span></span> <span data-ttu-id="23dd7-151">다른 방법으로 구독자를 초기화하면 병합 에이전트는 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-151">If you initialize a Subscriber with another method, the Merge Agent will fail.</span></span> <span data-ttu-id="23dd7-152">자세한 내용은 [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23dd7-152">For more information, see [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md).</span></span>

-   <span data-ttu-id="23dd7-153">논리적 레코드와 관련된 충돌은 충돌 뷰어에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-153">Conflicts that involve logical records are not displayed in Conflict Viewer.</span></span> <span data-ttu-id="23dd7-154">이러한 충돌에 대한 정보를 보려면 복제 저장 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-154">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="23dd7-155">자세한 내용은 [병합 게시에 대한 충돌 정보 보기&#40;복제 Transact-SQL 프로그래밍&#41;](../view-conflict-information-for-merge-publications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23dd7-155">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](../view-conflict-information-for-merge-publications.md).</span></span>

### <a name="publication-settings"></a><span data-ttu-id="23dd7-156">게시 설정</span><span class="sxs-lookup"><span data-stu-id="23dd7-156">Publication Settings</span></span>

-   <span data-ttu-id="23dd7-157">게시의 호환성 수준은 90RTM 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-157">The publication must have a compatibility level of 90RTM or greater.</span></span> <span data-ttu-id="23dd7-158">자세한 내용은 [복제의 이전 버전과의 호환성](../replication-backward-compatibility.md)의 "게시 호환성 수준" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23dd7-158">For more information, see the "Publication Compatibility Level" section of [Replication Backward Compatibility](../replication-backward-compatibility.md).</span></span>

-   <span data-ttu-id="23dd7-159">게시는 기본 스냅샷 모드를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-159">The publication must use native snapshot mode.</span></span> <span data-ttu-id="23dd7-160">논리적 레코드를 지원하지 않는 [!INCLUDE[ssEW](../../../includes/ssew-md.md)]에 복제하지 않는 한 기본 스냅숏 모드가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-160">This is the default unless you are replicating to [!INCLUDE[ssEW](../../../includes/ssew-md.md)], which does not support logical records.</span></span>

-   <span data-ttu-id="23dd7-161">게시는 웹 동기화를 허용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-161">The publication cannot allow Web synchronization.</span></span> <span data-ttu-id="23dd7-162">웹 동기화에 대한 자세한 내용은 [Web Synchronization for Merge Replication](../web-synchronization-for-merge-replication.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="23dd7-162">For more information about Web synchronization, see [Web Synchronization for Merge Replication](../web-synchronization-for-merge-replication.md).</span></span>

-   <span data-ttu-id="23dd7-163">필터링된 게시에 논리적 레코드를 사용하려면 다음을 준수하십시오.</span><span class="sxs-lookup"><span data-stu-id="23dd7-163">In order to use logical records on a filtered publication:</span></span>

    -   <span data-ttu-id="23dd7-164">사전 계산 파티션도 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-164">Precomputed partitions must also be used.</span></span> <span data-ttu-id="23dd7-165">이때 사전 계산 파티션의 요구 사항도 논리적 레코드에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-165">The requirements of precomputed partitions also apply to logical records.</span></span> <span data-ttu-id="23dd7-166">자세한 내용은 [사전 계산 파티션으로 매개 변수가 있는 필터 성능 최적화](parameterized-filters-optimize-for-precomputed-partitions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23dd7-166">For more information, see [Optimize Parameterized Filter Performance with Precomputed Partitions](parameterized-filters-optimize-for-precomputed-partitions.md).</span></span>

    -   <span data-ttu-id="23dd7-167">겹치지 않는 매개 변수가 있는 필터는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-167">You cannot use nonoverlapping parameterized filters.</span></span> <span data-ttu-id="23dd7-168">자세한 내용은 [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md)의 "'partition options' 설정" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="23dd7-168">For more information, see the "Setting 'partition options'" section of [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).</span></span>

-   <span data-ttu-id="23dd7-169">게시에서 조인 필터를 사용하는 경우 논리적 레코드 관계에 관련된 모든 조인 필터에 대해 **join unique key** 속성을 **true** 로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-169">If the publication uses join filters, the **join unique key** property must be set to **true** for all join filters that are involved in logical record relationships.</span></span> <span data-ttu-id="23dd7-170">자세한 내용은 [Join Filters](join-filters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23dd7-170">For more information, see [Join Filters](join-filters.md).</span></span>

### <a name="relationships-between-tables"></a><span data-ttu-id="23dd7-171">테이블 간 관계</span><span class="sxs-lookup"><span data-stu-id="23dd7-171">Relationships Between Tables</span></span>

-   <span data-ttu-id="23dd7-172">논리적 레코드를 통해 관련된 테이블에는 기본 키-외래 키 관계가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-172">Tables related through logical records must have a primary key-foreign key relationship.</span></span>

-   <span data-ttu-id="23dd7-173">FOREIGN KEY 제약 조건에 대해서는 NOT FOR REPLICATION 옵션을 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-173">The NOT FOR REPLICATION option cannot be set for foreign key constraints.</span></span>

-   <span data-ttu-id="23dd7-174">자식 테이블에는 부모 테이블이 하나만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-174">Child tables can have only one parent table.</span></span>

     <span data-ttu-id="23dd7-175">예를 들어 수업 및 학생 데이터를 추적하는 데이터베이스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-175">For example, a database tracking classes and students might have a design similar to:</span></span>

     <span data-ttu-id="23dd7-176">![둘 이상의 부모 테이블이 있는 자식 테이블](../media/logical-records-03.gif "둘 이상의 부모 테이블이 있는 자식 테이블")</span><span class="sxs-lookup"><span data-stu-id="23dd7-176">![Child table with more than one parent table](../media/logical-records-03.gif "Child table with more than one parent table")</span></span>

     <span data-ttu-id="23dd7-177">**ClassMembers** 의 행이 기본 키 행과 연결되어 있지 않았기 때문에 논리적 레코드를 사용하여 이 관계에 있는 3개의 테이블을 나타낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-177">You cannot use a logical record to represent the three tables in this relationship, because the rows in **ClassMembers** are not associated with a single primary key row.</span></span> <span data-ttu-id="23dd7-178">**ClassMembers** 테이블과 **Students** 테이블 간에 논리적 레코드를 만들 수 있듯이 **Classes** 테이블과 **ClassMembers**테이블 간에도 논리적 레코드를 만들 수 있지만 이 3개의 테이블 간에는 논리적 레코드를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-178">The tables **Classes** and **ClassMembers** could still form a logical record, as could the tables **ClassMembers** and **Students**, but not all three.</span></span>

-   <span data-ttu-id="23dd7-179">게시에는 순환 조인 필터 관계가 포함될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-179">The publication cannot contain circular join filter relationships.</span></span>

     <span data-ttu-id="23dd7-180">**Customers**, **Orders**및 **OrderItems**테이블의 예를 들면 **Orders** 테이블에도 **OrderItems** 테이블을 참조하는 FOREIGN KEY 제약 조건이 있는 경우에는 논리적 레코드를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-180">Using the example with the tables **Customers**, **Orders**, and **OrderItems**, you could not use logical records if the **Orders** table also had a foreign key constraint that referenced the **OrderItems** table.</span></span>

## <a name="performance-implications-of-logical-records"></a><span data-ttu-id="23dd7-181">논리적 레코드가 성능에 미치는 영향</span><span class="sxs-lookup"><span data-stu-id="23dd7-181">Performance implications of logical records</span></span>
 <span data-ttu-id="23dd7-182">논리적 레코드 기능을 사용하면 성능이 다소 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-182">The logical record feature does come with a performance cost.</span></span> <span data-ttu-id="23dd7-183">논리적 레코드를 사용하지 않는 경우 복제 에이전트는 지정된 아티클에 대한 모든 변경 내용을 동시에 처리할 수 있으며 변경 내용이 행 단위로 적용되므로 변경 내용 적용에 대해 최소의 잠금 및 트랜잭션 로그 요구 사항만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-183">If logical records are not used, the replication agent can process all of the changes for a given article at the same time, and because the changes are applied in a row-by-row fashion, the locking and transaction log requirements necessary for applying the changes are minimal.</span></span>

 <span data-ttu-id="23dd7-184">논리적 레코드를 사용하는 경우 복제 에이전트는 각각의 전체 논리적 레코드에 대한 변경 내용을 한 번에 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-184">If logical records are used, the Merge Agent must process the changes for each entire logical record together.</span></span> <span data-ttu-id="23dd7-185">이 방식은 병합 에이전트가 행을 복제하는 데 걸리는 시간에 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-185">This has an effect on the amount of time it takes the Merge Agent to replicate the rows.</span></span> <span data-ttu-id="23dd7-186">또한 에이전트가 각 논리적 레코드에 대해 별도의 트랜잭션을 열기 때문에 잠금 요구 사항이 증가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23dd7-186">Additionally, because the agent opens a separate transaction for each logical record, locking requirements can increase.</span></span>

## <a name="see-also"></a><span data-ttu-id="23dd7-187">참고 항목</span><span class="sxs-lookup"><span data-stu-id="23dd7-187">See Also</span></span>
 [<span data-ttu-id="23dd7-188">병합 복제를 위한 아티클 옵션</span><span class="sxs-lookup"><span data-stu-id="23dd7-188">Article Options for Merge Replication</span></span>](article-options-for-merge-replication.md)


