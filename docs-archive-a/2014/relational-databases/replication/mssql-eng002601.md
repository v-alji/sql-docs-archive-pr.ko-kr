---
title: MSSQL_ENG002601 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG002601 error
ms.assetid: 657c3ae6-9e4b-4c60-becc-4caf7435c1dc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2e8340fef83749fd6d041af42566b10ed3542c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740832"
---
# <a name="mssql_eng002601"></a><span data-ttu-id="f4a04-102">MSSQL_ENG002601</span><span class="sxs-lookup"><span data-stu-id="f4a04-102">MSSQL_ENG002601</span></span>
    
## <a name="message-details"></a><span data-ttu-id="f4a04-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="f4a04-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4a04-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="f4a04-104">Product Name</span></span>|<span data-ttu-id="f4a04-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f4a04-105">SQL Server</span></span>|  
|<span data-ttu-id="f4a04-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="f4a04-106">Event ID</span></span>|<span data-ttu-id="f4a04-107">2601</span><span class="sxs-lookup"><span data-stu-id="f4a04-107">2601</span></span>|  
|<span data-ttu-id="f4a04-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="f4a04-108">Event Source</span></span>|<span data-ttu-id="f4a04-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f4a04-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f4a04-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="f4a04-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="f4a04-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="f4a04-111">Symbolic Name</span></span>|<span data-ttu-id="f4a04-112">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f4a04-112">N/A</span></span>|  
|<span data-ttu-id="f4a04-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="f4a04-113">Message Text</span></span>|<span data-ttu-id="f4a04-114">고유 인덱스가 '%.\*ls'인 개체 '%.\*ls'에 중복 키 행을 삽입할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-114">Cannot insert duplicate key row in object '%.\*ls' with unique index '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f4a04-115">설명</span><span class="sxs-lookup"><span data-stu-id="f4a04-115">Explanation</span></span>  
 <span data-ttu-id="f4a04-116">이 오류는 데이터베이스의 복제 여부에 관계없이 발생할 수 있는 일반 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-116">This is a general error that can be raised regardless of whether a database is replicated.</span></span> <span data-ttu-id="f4a04-117">복제된 데이터베이스에서 이 오류는 일반적으로 토폴로지 내에서 기본 키가 제대로 관리되지 않았기 때문에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-117">In replicated databases, the error is typically raised because primary keys have not been managed appropriately across the topology.</span></span> <span data-ttu-id="f4a04-118">분산 환경에서는 둘 이상의 노드에서 기본 키 열 또는 다른 고유 열에 동일한 값이 삽입되지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-118">In a distributed environment it is essential to ensure that the same value is not inserted into a primary key column or any other unique column at more than one node.</span></span> <span data-ttu-id="f4a04-119">가능한 원인은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-119">Possible causes include the following:</span></span>  
  
-   <span data-ttu-id="f4a04-120">둘 이상의 노드에서 행 삽입 및 업데이트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-120">Inserts and updates to a row are occurring at more than one node.</span></span> <span data-ttu-id="f4a04-121">병합 복제 및 트랜잭션 복제에 대한 업데이트할 수 있는 구독은 둘 다 충돌 감지 및 해결 기능을 제공하지만 한 노드에서만 특정 행을 삽입 또는 업데이트하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-121">Merge replication and updatable subscriptions for transactional replication both provide conflict detection and resolution, but it is still preferable to insert or update a given row at only one node.</span></span> <span data-ttu-id="f4a04-122">피어 투 피어 트랜잭션은 충돌 감지 및 해결 기능을 제공하지 않으므로 삽입과 업데이트를 분할해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-122">Peer-to-peer transactional does not provide conflict detection and resolution; it requires that inserts and updates be partitioned.</span></span>  
  
-   <span data-ttu-id="f4a04-123">읽기 전용이어야 하는 구독자에서 행이 삽입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-123">A row was inserted at a Subscriber that should be read-only.</span></span> <span data-ttu-id="f4a04-124">업데이트할 수 있는 구독 또는 피어 투 피어 트랜잭션 복제를 사용하는 경우가 아니면 트랜잭션 게시에 대한 구독자와 마찬가지로 스냅샷 게시에 대한 구독자는 읽기 전용으로 취급되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-124">Subscribers to snapshot publications should be treated as read-only, as should Subscribers to transactional publications unless updatable subscriptions or peer-to-peer transactional replication is used.</span></span>  
  
-   <span data-ttu-id="f4a04-125">ID 열이 있는 테이블이 사용되지만 해당 열이 적절히 관리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-125">A table with an identity column is being used, but the column is not managed appropriately.</span></span>  
  
-   <span data-ttu-id="f4a04-126">병합 복제에서 이 오류는 시스템 테이블인 **MSmerge_contents**에 삽입하는 동안에도 발생할 수 있습니다. 발생하는 오류는 "고유 인덱스가 'ucl1SycContents'인 개체 'MSmerge_contents'에 중복 키 행을 삽입할 수 없습니다"와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-126">In merge replication, this error can also occur during an insert into the system table **MSmerge_contents**; the error raised is similar to: Cannot insert duplicate key row in object 'MSmerge_contents' with unique index 'ucl1SycContents.'</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f4a04-127">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="f4a04-127">User Action</span></span>  
 <span data-ttu-id="f4a04-128">필요한 동작은 오류 발생 원인에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-128">The action required depends on the reason the error was raised:</span></span>  
  
-   <span data-ttu-id="f4a04-129">둘 이상의 노드에서 행 삽입 및 업데이트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-129">Inserts and updates to a row are occurring at more than one node.</span></span>  
  
     <span data-ttu-id="f4a04-130">사용된 복제 유형에 관계없이 가능한 경우 삽입 및 업데이트를 분할하는 것이 좋습니다. 이렇게 하면 충돌 감지 및 해결 과정이 간편해집니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-130">Regardless of the type of replication used, we recommend that you partition inserts and updates whenever possible, because this reduces the processing required for conflict detection and resolution.</span></span> <span data-ttu-id="f4a04-131">피어 투 피어 트랜잭션 복제의 경우 삽입과 업데이트를 분할해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-131">For peer-to-peer transactional replication, partitioning inserts and updates is required.</span></span> <span data-ttu-id="f4a04-132">자세한 내용은 [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4a04-132">For more information, see [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="f4a04-133">읽기 전용이어야 하는 구독자에서 행이 삽입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-133">A row was inserted at a Subscriber that should be read-only.</span></span>  
  
     <span data-ttu-id="f4a04-134">병합 복제, 업데이트할 수 있는 구독이 있는 트랜잭션 복제 또는 피어 투 피어 트랜잭션 복제를 사용하는 경우가 아니면 구독자에서 행을 삽입 또는 업데이트하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f4a04-134">Do not insert or update rows at the Subscriber unless you are using merge replication, transactional replication with updatable subscriptions, or peer-to-peer transactional replication.</span></span>  
  
-   <span data-ttu-id="f4a04-135">ID 열이 있는 테이블이 사용되지만 해당 열이 적절히 관리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-135">A table with an identity column is being used, but the column is not managed appropriately.</span></span>  
  
     <span data-ttu-id="f4a04-136">병합 복제 및 업데이트할 수 있는 구독이 있는 트랜잭션 복제의 경우 ID 열은 복제에 의해 자동으로 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-136">For merge replication and transactional replication with updatable subscriptions, identity columns should be managed automatically by replication.</span></span> <span data-ttu-id="f4a04-137">피어 투 피어 트랜잭션 복제의 경우 ID 열을 수동으로 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-137">For peer-to-peer transactional replication, they must be managed manually.</span></span> <span data-ttu-id="f4a04-138">자세한 내용은 [ID 열 복제](publish/replicate-identity-columns.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4a04-138">For more information, see [Replicate Identity Columns](publish/replicate-identity-columns.md).</span></span>  
  
-   <span data-ttu-id="f4a04-139">시스템 테이블인 **MSmerge_contents**에 삽입하는 동안 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-139">The error occurs during an insert into the system table **MSmerge_contents**.</span></span>  
  
     <span data-ttu-id="f4a04-140">이 오류는 **join_unique_key**조인 필터 속성에 대한 값이 잘못되었기 때문에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-140">This error can occur because of an incorrect value for the join filter property **join_unique_key**.</span></span> <span data-ttu-id="f4a04-141">부모 테이블의 조인된 열이 고유한 경우에만 이 속성을 TRUE로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-141">This property should be set to TRUE only if the joined column in the parent table is unique.</span></span> <span data-ttu-id="f4a04-142">속성이 TRUE로 설정되어 있지만 열이 고유하지 않은 경우에는 이 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a04-142">If the property is set to TRUE, but the column is not unique, this error is raised.</span></span> <span data-ttu-id="f4a04-143">이 속성을 설정하는 방법은 [병합 아티클 사이에서 조인 필터 정의 및 수정](publish/define-and-modify-a-join-filter-between-merge-articles.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4a04-143">For more information on setting this property, see [Define and Modify a Join Filter Between Merge Articles](publish/define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4a04-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4a04-144">See Also</span></span>  
 [<span data-ttu-id="f4a04-145">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="f4a04-145">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
