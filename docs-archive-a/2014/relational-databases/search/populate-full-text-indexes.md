---
title: 전체 텍스트 인덱스 채우기 | Microsoft 문서
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- index populations [full-text search]
- incremental populations [full-text search]
- populations [full-text search]
- full-text search [SQL Server], populations
- crawls [full-text search]
- automatic full-text index updates
- change tracking-based populations [full-text search]
- manual updates [full-text search]
- manual populations [full-text search]
- auto populations [full-text search]
- full-text indexes [SQL Server], key column
- full populations [full-text search]
- full-text indexes [SQL Server], populations
ms.assetid: 76767b20-ef55-49ce-8dc4-e77cb8ff618a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9ab93a3514fa260c8c3836da85c767da3c3051a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653784"
---
# <a name="populate-full-text-indexes"></a><span data-ttu-id="65507-102">전체 텍스트 인덱스 채우기</span><span class="sxs-lookup"><span data-stu-id="65507-102">Populate Full-Text Indexes</span></span>
  <span data-ttu-id="65507-103">전체 텍스트 인덱스를 만들고 유지 관리하려면 *채우기* ( *탐색*이라고도 함)라는 프로세스를 사용하여 인덱스를 채워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-103">Creating and maintaining a full-text index involves populating the index by using a process called a *population* (also known as a *crawl*).</span></span>  
  
##  <a name="types-of-population"></a><a name="types"></a><span data-ttu-id="65507-104">채우기 유형</span><span class="sxs-lookup"><span data-stu-id="65507-104">Types of Population</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="65507-105">는 전체 채우기, 변경 내용 추적 기반 자동 또는 수동 채우기 및 증분 타임 스탬프 기반 채우기와 같은 채우기 유형을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-105">supports the following types of population: full population, change tracking-based automatic or manual population, and incremental timestamp-based population.</span></span>  
  
### <a name="full-population"></a><span data-ttu-id="65507-106">전체 채우기</span><span class="sxs-lookup"><span data-stu-id="65507-106">Full Population</span></span>  
 <span data-ttu-id="65507-107">전체 채우기 중에는 테이블 또는 인덱싱된 뷰의 모든 행에 대해 인덱스 항목이 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="65507-107">During a full population, index entries are built for all the rows of a table or indexed view.</span></span> <span data-ttu-id="65507-108">전체 텍스트 인덱스의 전체 채우기는 기본 테이블 또는 인덱싱된 뷰의 모든 행에 대해 인덱스 항목을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-108">A full population of a full-text index, builds index entries for all the rows of the base table or indexed view.</span></span>  
  
 <span data-ttu-id="65507-109">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 새 전체 텍스트 인덱스를 만드는 즉시 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="65507-109">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] populates a new full-text index fully as soon as it is created.</span></span> <span data-ttu-id="65507-110">그러나 전체 채우기는 많은 양의 리소스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-110">However, a full population can consume a significant amount of resources.</span></span> <span data-ttu-id="65507-111">따라서 리소스 사용량이 많을 때 전체 텍스트 인덱스를 만들 경우, 특히 전체 텍스트 인덱스의 기본 테이블이 클 경우 리소스 사용량이 많지 않을 때까지 전체 채우기를 지연시키는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-111">Therefore, when creating a full-text index during peak periods, it is often a best practice to delay the full population until an off-peak time, particularly if the base table of an full-text index is large.</span></span> <span data-ttu-id="65507-112">그러나 인덱스가 속한 전체 텍스트 카탈로그는 전체 텍스트 인덱스가 모두 채워질 때까지 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-112">However, the full-text catalog to which the index belongs is not usable until all of its full-text indexes are populated.</span></span> <span data-ttu-id="65507-113">전체 텍스트 인덱스를 즉시 채우지 않고 만들려면 CREATE FULLTEXT INDEX 문에 CHANGE_TRACKING OFF, NO POPULATION 절을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-113">To create a full-text index without populating it immediately, specify the CHANGE_TRACKING OFF, NO POPULATION clause in the CREATE FULLTEXT INDEX statement.</span></span> <span data-ttu-id="65507-114">CHANGE_TRACKING MANUAL을 지정하면 전체 텍스트 엔진에서 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-114">If you specify CHANGE_TRACKING MANUAL, the Full-Text Engine uses statement.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="65507-115">는 START FULL 채우기 또는 START 증분 채우기 절을 사용 하 여 ALTER 전체 텍스트 인덱스 문을 실행할 때까지 새로운 전체 텍스트 인덱스를 채우지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-115">will not populate the new full-text index until you execute an ALTER FULLTEXT INDEX statement using the START FULL POPULATION or START INCREMENTAL POPULATION clause.</span></span> <span data-ttu-id="65507-116">자세한 내용은 이 항목의 뒷부분에 나오는 예 "1.</span><span class="sxs-lookup"><span data-stu-id="65507-116">For more information, see examples "A.</span></span> <span data-ttu-id="65507-117">전체 채우기를 실행하지 않고 전체 텍스트 인덱스 만들기" 및 "2.</span><span class="sxs-lookup"><span data-stu-id="65507-117">Creating a full-text index without running a full population" and "B.</span></span> <span data-ttu-id="65507-118">테이블에 대해 전체 채우기 실행"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="65507-118">Running a full population on table," later in this topic.</span></span>  
  

  
### <a name="change-tracking-based-population"></a><span data-ttu-id="65507-119">변경 내용 추적 기반 채우기</span><span class="sxs-lookup"><span data-stu-id="65507-119">Change Tracking-Based Population</span></span>  
 <span data-ttu-id="65507-120">경우에 따라 초기 전체 채우기 후에 변경 내용 추적을 사용하여 전체 텍스트 인덱스를 유지 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-120">Optionally, you can use change tracking to maintain a full-text index after its initial full population.</span></span> <span data-ttu-id="65507-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 마지막 채우기 후에 기본 테이블의 변경 내용을 추적하는 테이블을 유지 관리하기 때문에 변경 내용 추적을 사용할 경우 약간의 오버헤드가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-121">There is a small overhead associated with change tracking because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] maintains a table in which it tracks changes to the base table since the last population.</span></span> <span data-ttu-id="65507-122">변경 내용 추적을 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 업데이트, 삭제 또는 삽입에 의해 수정된 기본 테이블 또는 인덱싱된 뷰의 행 레코드를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-122">When change tracking is used, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] maintains a record of the rows in the base table or indexed view that have been modified by updates, deletes, or inserts.</span></span> <span data-ttu-id="65507-123">WRITETEXT 및 UPDATETEXT를 통한 데이터 변경 내용은 전체 텍스트 인덱스에 반영되지 않고 변경 내용 추적 시 선택되지도 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-123">Data changes through WRITETEXT and UPDATETEXT are not reflected in the full-text index, and are not picked up with change tracking.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65507-124">`timestamp` 열이 포함된 테이블에 대해서는 증분 채우기를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-124">For tables containing a `timestamp` column, you can use incremental populations.</span></span>  
  
 <span data-ttu-id="65507-125">인덱스를 만드는 동안 변경 내용 추적을 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 새 전체 텍스트 인덱스를 만드는 즉시 완전히 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="65507-125">When change tracking is enabled during index creation, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fully populates the new full-text index immediately after it is created.</span></span> <span data-ttu-id="65507-126">그 이후에는 변경 내용이 추적되고 전체 텍스트 인덱스로 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="65507-126">Thereafter, changes are tracked and propagated to the full-text index.</span></span> <span data-ttu-id="65507-127">변경 내용 추적에는 두 가지 유형, 자동(CHANGE_TRACKING AUTO 옵션)과 수동(CHANGE_TRACKING MANUAL 옵션)이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-127">There are two types of change tracking, automatic (CHANGE_TRACKING AUTO option) and manual (CHANGE_TRACKING MANUAL option).</span></span> <span data-ttu-id="65507-128">자동 변경 내용 추적이 기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="65507-128">Automatic change tracking is the default behavior.</span></span>  
  
 <span data-ttu-id="65507-129">변경 내용 추적의 유형에 따라 전체 텍스트 인덱스가 채워지는 방법이 다음과 같이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="65507-129">The type of change tracking determines how the full-text index is populated, as follows:</span></span>  
  
-   <span data-ttu-id="65507-130">자동 채우기</span><span class="sxs-lookup"><span data-stu-id="65507-130">Automatic population</span></span>  
  
     <span data-ttu-id="65507-131">기본적으로 또는 CHANGE_TRACKING AUTO를 지정한 경우 전체 텍스트 엔진은 전체 텍스트 인덱스에 대해 자동 채우기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-131">By default, or if you specify CHANGE_TRACKING AUTO, the Full-Text Engine uses automatic population on the full-text index.</span></span> <span data-ttu-id="65507-132">초기 전체 채우기가 완료된 후 기본 테이블의 데이터가 수정되면 변경 내용이 추적되고 추적된 변경 내용이 자동으로 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="65507-132">After the initial full population completes, changes are tracked as data is modified in the base table, and the tracked changes are propagated automatically.</span></span> <span data-ttu-id="65507-133">그러나 전체 텍스트 인덱스가 백그라운드에서 업데이트되기 때문에 전파된 변경 내용은 인덱스에 즉시 반영되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-133">The full-text index is updated in the background, however, so propagated changes might not be reflected immediately in the index.</span></span>  
  
     <span data-ttu-id="65507-134">**자동 채우기를 사용하는 변경 내용 추적을 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="65507-134">**To set up tracking changes with automatic population**</span></span>  
  
    -   <span data-ttu-id="65507-135">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ... WITH CHANGE_TRACKING AUTO</span><span class="sxs-lookup"><span data-stu-id="65507-135">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ... WITH CHANGE_TRACKING AUTO</span></span>  
  
    -   <span data-ttu-id="65507-136">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ... SET CHANGE_TRACKING AUTO</span><span class="sxs-lookup"><span data-stu-id="65507-136">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ... SET CHANGE_TRACKING AUTO</span></span>  
  
     <span data-ttu-id="65507-137">자세한 내용은 이 항목의 뒷부분에 나오는 예 "5.</span><span class="sxs-lookup"><span data-stu-id="65507-137">For more information, see example "E.</span></span> <span data-ttu-id="65507-138">자동 변경 내용 추적을 사용하도록 전체 텍스트 인덱스 변경"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="65507-138">Altering a full-text index to use automatic change tracking," later in this topic.</span></span>  
  
-   <span data-ttu-id="65507-139">수동 채우기</span><span class="sxs-lookup"><span data-stu-id="65507-139">Manual population</span></span>  
  
     <span data-ttu-id="65507-140">CHANGE_TRACKING MANUAL을 지정한 경우 전체 텍스트 엔진에서는 전체 텍스트 인덱스에 대해 수동 채우기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-140">If you specify CHANGE_TRACKING MANUAL, the Full-Text Engine uses manual population on the full-text index.</span></span> <span data-ttu-id="65507-141">초기 전체 채우기가 완료된 후 기본 테이블의 데이터가 수정되면 변경 내용이 추적됩니다.</span><span class="sxs-lookup"><span data-stu-id="65507-141">After the initial full population completes, changes are tracked as data is modified in the base table.</span></span> <span data-ttu-id="65507-142">그러나 추적된 변경 내용은 ALTER FULLTEXT INDEX…를 실행할 때까지 전체 텍스트 인덱스로 전파되지 않습니다. START UPDATE POPULATION 문을 사용하여 수동으로 변경 내용을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-142">However, they are not propagated to the full-text index until you execute an ALTER FULLTEXT INDEX ... START UPDATE POPULATION statement.</span></span> <span data-ttu-id="65507-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 사용하여 이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 주기적으로 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-143">You can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to call this [!INCLUDE[tsql](../../includes/tsql-md.md)] statement periodically.</span></span>  
  
     <span data-ttu-id="65507-144">**수동 채우기가 있는 변경 내용 추적을 시작하려면**</span><span class="sxs-lookup"><span data-stu-id="65507-144">**To start tracking changes with manual population**</span></span>  
  
    -   <span data-ttu-id="65507-145">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ... WITH CHANGE_TRACKING MANUAL</span><span class="sxs-lookup"><span data-stu-id="65507-145">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ... WITH CHANGE_TRACKING MANUAL</span></span>  
  
    -   <span data-ttu-id="65507-146">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ... SET CHANGE_TRACKING MANUAL</span><span class="sxs-lookup"><span data-stu-id="65507-146">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ... SET CHANGE_TRACKING MANUAL</span></span>  
  
     <span data-ttu-id="65507-147">자세한 내용은 이 항목의 뒷부분에 나오는 예 "3.</span><span class="sxs-lookup"><span data-stu-id="65507-147">For more information, see examples "C.</span></span> <span data-ttu-id="65507-148">수동 변경 내용 추적이 있는 전체 텍스트 인덱스 만들기" 및 "4.</span><span class="sxs-lookup"><span data-stu-id="65507-148">Creating a full-text index with manual change tracking" and "D.</span></span> <span data-ttu-id="65507-149">수동 채우기 실행"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="65507-149">Running a manual population," later in this topic.</span></span>  
  
 <span data-ttu-id="65507-150">**변경 내용 추적을 해제하려면**</span><span class="sxs-lookup"><span data-stu-id="65507-150">**To turn off change tracking**</span></span>  
  
-   <span data-ttu-id="65507-151">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ... WITH CHANGE_TRACKING OFF</span><span class="sxs-lookup"><span data-stu-id="65507-151">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ... WITH CHANGE_TRACKING OFF</span></span>  
  
-   <span data-ttu-id="65507-152">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ... SET CHANGE_TRACKING OFF</span><span class="sxs-lookup"><span data-stu-id="65507-152">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ... SET CHANGE_TRACKING OFF</span></span>  
  

  
### <a name="incremental-timestamp-based-population"></a><span data-ttu-id="65507-153">증분 타임스탬프 기반 채우기</span><span class="sxs-lookup"><span data-stu-id="65507-153">Incremental Timestamp-Based Population</span></span>  
 <span data-ttu-id="65507-154">증분 채우기는 전체 텍스트 인덱스를 수동으로 채우는 대체 메커니즘으로,</span><span class="sxs-lookup"><span data-stu-id="65507-154">An incremental population is an alternative mechanism for manually populating a full-text index.</span></span> <span data-ttu-id="65507-155">CHANGE_TRACKING이 MANUAL 또는 OFF로 설정된 전체 텍스트 인덱스에 대해 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-155">You can run an incremental population for a full-text index that has CHANGE_TRACKING set to MANUAL or OFF.</span></span> <span data-ttu-id="65507-156">전체 텍스트 인덱스에 대해 처음으로 실행하는 채우기가 증분 채우기이면 모든 행이 인덱싱되므로 그 결과가 전체 채우기의 경우와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-156">If the first population on a full-text index is an incremental population, it indexes all rows, making it equivalent to a full population.</span></span>  
  
 <span data-ttu-id="65507-157">증분 채우기를 사용하려면 인덱싱된 테이블에 `timestamp` 데이터 형식의 열이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-157">The requirement for incremental population is that the indexed table must have a column of the `timestamp` data type.</span></span> <span data-ttu-id="65507-158">`timestamp` 열이 없으면 증분 채우기를 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-158">If a `timestamp` column does not exist, incremental population cannot be performed.</span></span> <span data-ttu-id="65507-159">`timestamp` 열이 없는 테이블에 대해 증분 채우기를 요청하면 전체 채우기 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="65507-159">A request for incremental population on a table without a `timestamp` column results in a full population operation.</span></span> <span data-ttu-id="65507-160">또한 테이블의 전체 텍스트 인덱스에 영향을 주는 메타데이터가 마지막 채우기 후에 변경된 경우 증분 채우기 요청은 전체 채우기로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="65507-160">Also, if any metadata that affects the full-text index for the table has changed since the last population, incremental population requests are implemented as full populations.</span></span> <span data-ttu-id="65507-161">여기에는 열, 인덱스 또는 전체 텍스트 인덱스 정의의 변경으로 인한 메타데이터 변경 내용이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="65507-161">This includes metadata changes caused by altering any column, index, or full-text index definitions.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="65507-162">에서는 `timestamp` 열을 사용하여 마지막 채우기 후에 변경된 행을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-162">uses the `timestamp` column to identify rows that have changed since the last population.</span></span> <span data-ttu-id="65507-163">그러면 증분 채우기는 마지막 채우기 후 또는 마지막 채우기를 진행 중인 동안 추가, 삭제 또는 수정된 행에 대해 전체 텍스트 인덱스를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-163">The incremental population then updates the full-text index for rows added, deleted, or modified after the last population, or while the last population was in progress.</span></span> <span data-ttu-id="65507-164">테이블에서 대량 삽입이 발생하는 경우 증분 채우기를 사용하는 것이 수동 채우기를 사용하는 것보다 효율적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-164">If a table experiences a high volume of inserts, using incremental population can be more efficient that using manual population.</span></span>  
  
 <span data-ttu-id="65507-165">채우기 완료 시 전체 텍스트 엔진은 새 `timestamp` 값을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-165">At the end of a population, the Full-Text Engine records a new `timestamp` value.</span></span> <span data-ttu-id="65507-166">이 값은 SQL Gatherer에서 발생한 가장 큰 `timestamp` 값입니다.</span><span class="sxs-lookup"><span data-stu-id="65507-166">This value is the largest `timestamp` value that SQL Gatherer has encountered.</span></span> <span data-ttu-id="65507-167">이 값은 후속 증분 채우기가 시작될 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="65507-167">This value will be used when a subsequent incremental population starts.</span></span>  
  
 <span data-ttu-id="65507-168">증분 채우기를 실행하려면 START INCREMENTAL POPULATION 절을 사용하여 ALTER FULLTEXT INDEX 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-168">To run an incremental population, execute an ALTER FULLTEXT INDEX statement using the START INCREMENTAL POPULATION clause.</span></span>  
  

  
##  <a name="examples-of-populating-full-text-indexes"></a><a name="examples"></a><span data-ttu-id="65507-169">전체 텍스트 인덱스를 채우는 예</span><span class="sxs-lookup"><span data-stu-id="65507-169">Examples of Populating Full-Text Indexes</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65507-170">이 섹션의 예에서는 `Production.Document` 예제 데이터베이스의 `HumanResources.JobCandidate` 또는 `AdventureWorks` 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-170">The examples in this section use the `Production.Document` or `HumanResources.JobCandidate` table of the `AdventureWorks` sample database.</span></span>  
  
### <a name="a-creating-a-full-text-index-without-running-a-full-population"></a><span data-ttu-id="65507-171">A.</span><span class="sxs-lookup"><span data-stu-id="65507-171">A.</span></span> <span data-ttu-id="65507-172">전체 채우기를 실행하지 않고 전체 텍스트 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="65507-172">Creating a full-text index without running a full population</span></span>  
 <span data-ttu-id="65507-173">다음 예에서는 `Production.Document` 예제 데이터베이스의 `AdventureWorks` 테이블에서 전체 텍스트 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="65507-173">The following example creates a full-text index on the `Production.Document` table of the `AdventureWorks` sample database.</span></span> <span data-ttu-id="65507-174">이 예에서는 WITH CHANGE_TRACKING OFF, NO POPULATION을 사용하여 초기 전체 채우기를 지연시킵니다.</span><span class="sxs-lookup"><span data-stu-id="65507-174">This example uses WITH CHANGE_TRACKING OFF, NO POPULATION to delay the initial full population.</span></span>  
  
```  
CREATE UNIQUE INDEX ui_ukDoc ON Production.Document(DocumentID);  
CREATE FULLTEXT CATALOG AW_Production_FTCat;  
CREATE FULLTEXT INDEX ON Production.Document  
(  
    Document                         --Full-text index column name   
        TYPE COLUMN FileExtension    --Name of column that contains file type information  
        Language 1033                 --1033 is LCID for the English language  
)  
    KEY INDEX ui_ukDoc  
    ON AW_Production_FTCat  
    WITH CHANGE_TRACKING OFF, NO POPULATION;  
GO  
  
```  
  
### <a name="b-running-a-full-population-on-table"></a><span data-ttu-id="65507-175">B.</span><span class="sxs-lookup"><span data-stu-id="65507-175">B.</span></span> <span data-ttu-id="65507-176">테이블에 대해 전체 채우기 실행</span><span class="sxs-lookup"><span data-stu-id="65507-176">Running a full population on table</span></span>  
 <span data-ttu-id="65507-177">다음 예에서는 `Production.Document` 예제 데이터베이스의 `AdventureWorks` 테이블에 대해 전체 채우기를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-177">The following example runs a full population on the `Production.Document` table of the `AdventureWorks` sample database.</span></span>  
  
```  
ALTER FULLTEXT INDEX ON Production.Document  
   START FULL POPULATION;  
```  
  
### <a name="c-creating-a-full-text-index-with-manual-change-tracking"></a><span data-ttu-id="65507-178">C.</span><span class="sxs-lookup"><span data-stu-id="65507-178">C.</span></span> <span data-ttu-id="65507-179">수동 변경 내용 추적이 있는 전체 텍스트 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="65507-179">Creating a full-text index with manual change tracking</span></span>  
 <span data-ttu-id="65507-180">다음 예에서는 `HumanResources.JobCandidate` 예제 데이터베이스의 `AdventureWorks` 테이블에 대해 수동 채우기가 있는 변경 내용 추적을 사용하는 전체 텍스트 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="65507-180">The following example creates a full-text index that will use change tracking with manual population on the `HumanResources.JobCandidate` table of the `AdventureWorks` sample database.</span></span>  
  
```  
USE AdventureWorks;  
GO  
CREATE UNIQUE INDEX ui_ukJobCand ON HumanResources.JobCandidate(JobCandidateID);  
CREATE FULLTEXT CATALOG ft AS DEFAULT;  
CREATE FULLTEXT INDEX ON HumanResources.JobCandidate(Resume)   
   KEY INDEX ui_ukJobCand   
   WITH CHANGE_TRACKING=MANUAL;  
GO  
```  
  
### <a name="d-running-a-manual-population"></a><span data-ttu-id="65507-181">D.</span><span class="sxs-lookup"><span data-stu-id="65507-181">D.</span></span> <span data-ttu-id="65507-182">수동 채우기 실행</span><span class="sxs-lookup"><span data-stu-id="65507-182">Running a manual population</span></span>  
 <span data-ttu-id="65507-183">다음 예에서는 `HumanResources.JobCandidate` 예제 데이터베이스의 `AdventureWorks` 테이블에서 변경 내용 추적이 설정된 전체 텍스트 인덱스에 대해 수동 채우기를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-183">The following example runs a manual population on the change-tracked full-text index of the `HumanResources.JobCandidate` table of the `AdventureWorks` sample database.</span></span>  
  
```  
USE AdventureWorks;  
GO  
ALTER FULLTEXT INDEX ON HumanResources.JobCandidate START UPDATE POPULATION;  
GO  
```  
  
### <a name="e-altering-a-full-text-index-to-use-automatic-change-tracking"></a><span data-ttu-id="65507-184">E.</span><span class="sxs-lookup"><span data-stu-id="65507-184">E.</span></span> <span data-ttu-id="65507-185">자동 변경 내용 추적을 사용하도록 전체 텍스트 인덱스 변경</span><span class="sxs-lookup"><span data-stu-id="65507-185">Altering a full-text index to use automatic change tracking</span></span>  
 <span data-ttu-id="65507-186">다음 예에서는 자동 채우기와 함께 변경 내용 추적을 사용하도록 `HumanResources.JobCandidate` 예제 데이터베이스의 `AdventureWorks` 테이블에 대한 전체 텍스트 인덱스를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-186">The following example changes the full-text index of the `HumanResources.JobCandidate` table of the `AdventureWorks` sample database to use change tracking with automatic population.</span></span>  
  
```  
USE AdventureWorks;  
GO  
ALTER FULLTEXT INDEX ON HumanResources.JobCandidate SET CHANGE_TRACKING AUTO;  
GO   
```  
  

  
##  <a name="creating-or-changing-a-schedule-for-incremental-population"></a><a name="create"></a><span data-ttu-id="65507-187">증분 채우기 일정 만들기 또는 변경</span><span class="sxs-lookup"><span data-stu-id="65507-187">Creating or Changing a Schedule for Incremental Population</span></span>  
  
#### <a name="to-create-or-change-a-schedule-for-incremental-population-in-management-studio"></a><span data-ttu-id="65507-188">Management Studio에서 증분 채우기 일정을 만들거나 변경하려면</span><span class="sxs-lookup"><span data-stu-id="65507-188">To create or change a schedule for incremental population in Management Studio</span></span>  
  
1.  <span data-ttu-id="65507-189">개체 탐색기에서 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-189">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="65507-190">**데이터베이스**를 확장한 다음 전체 텍스트 인덱스가 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-190">Expand **Databases**, and then expand the database that contains the full-text index.</span></span>  
  
3.  <span data-ttu-id="65507-191">**테이블**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-191">Expand **Tables**.</span></span>  
  
 <span data-ttu-id="65507-192">전체 텍스트 인덱스가 정의된 테이블을 마우스 오른쪽 단추로 클릭하고 **전체 텍스트 인덱스**를 선택한 다음 **전체 텍스트 인덱스** 상황에 맞는 메뉴에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-192">Right-click the table on which the full-text index is defined, select **Full-Text index**, and on the **Full-Text index** context menu, click **Properties**.</span></span> <span data-ttu-id="65507-193">그러면 **전체 텍스트 인덱스 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="65507-193">This opens the **Full-text index Properties** dialog box.</span></span>  
  
1.  <span data-ttu-id="65507-194">**페이지 선택** 창에서 일정을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-194">In the **Select a page** pane, select Schedules.</span></span>  
  
     <span data-ttu-id="65507-195">이 페이지를 사용하여 전체 텍스트 인덱스의 기본 테이블 또는 인덱싱된 뷰에 대한 증분 테이블 채우기를 시작하는 SQL Server 에이전트 작업의 일정을 만들거나 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-195">Use this page to create or manage schedules for a SQL Server Agent job that starts an incremental table population on the base table or indexed view of the full-text index.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="65507-196">기본 테이블이나 뷰에 `timestamp` 데이터 형식의 열이 포함되어 있지 않으면 전체 채우기가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="65507-196">If the base table or view does not contain a column of the `timestamp` data type, a full population is performed.</span></span>  
  
     <span data-ttu-id="65507-197">옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-197">The options are as follows:</span></span>  
  
    -   <span data-ttu-id="65507-198">새 일정을 만들려면 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-198">To create a new schedule, click **New**.</span></span>  
  
         <span data-ttu-id="65507-199">그러면 일정을 만들 수 있는 **새 전체 텍스트 인덱싱 테이블 일정** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="65507-199">This opens the **New Full-Text Indexing Table Schedule** dialog box, where you can create a schedule.</span></span> <span data-ttu-id="65507-200">일정을 저장하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-200">To save the schedule, click **OK**.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="65507-201">*전체 텍스트 인덱스 속성*대화 상자를 닫으면 SQL Server 에이전트 작업(*database_name*. **table_name** 에 대한 증분 테이블 채우기 시작)이 새 일정에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="65507-201">A SQL Server Agent job (Start Incremental Table Population on *database_name*.*table_name*) is associated with a new schedule after you exit the **Full-Text Index Properties** dialog box.</span></span> <span data-ttu-id="65507-202">전체 텍스트 인덱스 일정을 여러 개 만들 경우 모두 동일한 작업을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-202">If you create multiple schedules for the full-text index, they all use the same job.</span></span>  
  
    -   <span data-ttu-id="65507-203">일정을 변경하려면 일정을 선택하고 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-203">To change a schedule, select it and click **Edit**.</span></span>  
  
         <span data-ttu-id="65507-204">그러면 일정을 수정할 수 있는 **새 전체 텍스트 인덱싱 테이블 일정** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="65507-204">This opens the **New Full-Text Indexing Table Schedule** dialog box, where you can modify the schedule.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="65507-205">작업을 수정하는 방법은 [작업 수정](../../ssms/agent/modify-a-job.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65507-205">For information about modifying a job, see [Modify a Job](../../ssms/agent/modify-a-job.md).</span></span>  
  
    -   <span data-ttu-id="65507-206">일정을 제거하려면 일정을 선택하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-206">To remove a schedule, select it and click **Delete**.</span></span>  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  

  
##  <a name="troubleshooting-errors-in-a-full-text-population-crawl"></a><a name="crawl"></a><span data-ttu-id="65507-207">전체 텍스트 채우기의 오류 문제 해결 (탐색)</span><span class="sxs-lookup"><span data-stu-id="65507-207">Troubleshooting Errors in a Full-Text Population (Crawl)</span></span>  
 <span data-ttu-id="65507-208">탐색 중에 오류가 발생하면 전체 텍스트 검색 탐색 로깅 기능은 일반 텍스트 파일인 탐색 로그를 만들고 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-208">When an error occurs during a crawl, the Full-Text Search crawl logging facility creates and maintains a crawl log, which is a plain text file.</span></span> <span data-ttu-id="65507-209">각 탐색 로그는 특정 전체 텍스트 카탈로그에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="65507-209">Each crawl log corresponds to a particular full-text catalog.</span></span> <span data-ttu-id="65507-210">기본적으로 지정된 인스턴스(여기서는 첫 번째 인스턴스)의 탐색 로그는 %ProgramFiles%\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\LOG 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65507-210">By default crawl logs for a given instance, in this case, the first instance, are located in %ProgramFiles%\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\LOG folder.</span></span> <span data-ttu-id="65507-211">탐색 로그 파일은 다음 명명 구성표를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="65507-211">The crawl log file follows the following naming scheme:</span></span>  
  
 <span data-ttu-id="65507-212">SQLFT \<DatabaseID> \<FullTextCatalogID> . LOG [ \<n> ]</span><span class="sxs-lookup"><span data-stu-id="65507-212">SQLFT\<DatabaseID>\<FullTextCatalogID>.LOG[\<n>]</span></span>  
  
 <`DatabaseID`>  
 <span data-ttu-id="65507-213">데이터베이스의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="65507-213">The ID of a database.</span></span><span data-ttu-id="65507-214"> <`dbid`> 앞에 오는 0을 사용 하는 5 자리 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="65507-214"> <`dbid`> is a five digit number with leading zeros.</span></span>  
  
 <`FullTextCatalogID`>  
 <span data-ttu-id="65507-215">전체 텍스트 카탈로그 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="65507-215">Full-text catalog ID.</span></span><span data-ttu-id="65507-216"> <`catid`> 앞에 오는 0을 사용 하는 5 자리 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="65507-216"> <`catid`> is a five digit number with leading zeros.</span></span>  
  
 <`n`>  
 <span data-ttu-id="65507-217">동일한 전체 텍스트 카탈로그의 탐색 로그가 하나 이상 있음을 나타내는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="65507-217">Is an integer that indicates one or more crawl logs of the same full-text catalog exist.</span></span>  
  
 <span data-ttu-id="65507-218">예를 들어 SQLFT0000500008.2는 데이터베이스 ID = 5, 전체 텍스트 카탈로그 ID = 8인 데이터베이스의 탐색 로그 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="65507-218">For example, SQLFT0000500008.2 is the crawl log file for a database with database ID = 5, and full-text catalog ID = 8.</span></span> <span data-ttu-id="65507-219">파일 이름 끝에 있는 2는 이 데이터베이스/카탈로그 쌍의 탐색 로그 파일이 두 개 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65507-219">The 2 at the end of the file name indicates that there are two crawl log files for this database/catalog pair.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="65507-220">참고 항목</span><span class="sxs-lookup"><span data-stu-id="65507-220">See Also</span></span>  
 <span data-ttu-id="65507-221">[sys.dm_fts_index_population&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="65507-221">[sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql) </span></span>  
 <span data-ttu-id="65507-222">[전체 텍스트 검색 시작](get-started-with-full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="65507-222">[Get Started with Full-Text Search](get-started-with-full-text-search.md) </span></span>  
 <span data-ttu-id="65507-223">[전체 텍스트 인덱스 만들기 및 관리](create-and-manage-full-text-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="65507-223">[Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md) </span></span>  
 <span data-ttu-id="65507-224">[CREATE FULLTEXT INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="65507-224">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span></span>  
 [<span data-ttu-id="65507-225">ALTER FULLTEXT INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="65507-225">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
  
