---
title: 매개 변수가 있는 필터로 병합 게시에 대한 파티션 관리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- partitions [SQL Server replication]
- merge replication partitions [SQL Server replication], SQL Server Management Studio
- parameterized filters [SQL Server replication], partition management
ms.assetid: fb5566fe-58c5-48f7-8464-814ea78e6221
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 983b02865c0564919259f896bf09d8bdb0cd969f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646331"
---
# <a name="manage-partitions-for-a-merge-publication-with-parameterized-filters"></a><span data-ttu-id="c66ab-102">매개 변수가 있는 필터로 병합 게시에 대한 파티션 관리</span><span class="sxs-lookup"><span data-stu-id="c66ab-102">Manage Partitions for a Merge Publication with Parameterized Filters</span></span>
  <span data-ttu-id="c66ab-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 매개 변수가 있는 필터로 병합 게시에 대한 파티션을 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-103">This topic describes how to manage partitions for a merge publication with parameterized filters in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="c66ab-104">매개 변수가 있는 행 필터를 사용하여 겹치지 않는 파티션을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-104">Parameterized row filters can be used to generate nonoverlapping partitions.</span></span> <span data-ttu-id="c66ab-105">이러한 파티션을 제한하여 특정 파티션을 하나의 구독에서만 받도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-105">These partitions can be restricted so that only one subscription receives a given partition.</span></span> <span data-ttu-id="c66ab-106">이러한 경우 구독자 수가 많으면 파티션 수가 많아지고 이에 따라 동일한 수의 분할된 스냅샷이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-106">In these cases, a large number of subscribers will result in a large number of partitions, which in turn requires an equal number of partitioned snapshots.</span></span> <span data-ttu-id="c66ab-107">자세한 내용은 [매개 변수가 있는 행 필터](../merge/parameterized-filters-parameterized-row-filters.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c66ab-107">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="c66ab-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="c66ab-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c66ab-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="c66ab-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c66ab-110">권장 사항</span><span class="sxs-lookup"><span data-stu-id="c66ab-110">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="c66ab-111">**다음을 사용하여 매개 변수가 있는 필터로 병합 게시에 대한 파티션을 관리하려면**</span><span class="sxs-lookup"><span data-stu-id="c66ab-111">**To manage partitions for a merge publication with parameterized filters, using:**</span></span>  
  
     [<span data-ttu-id="c66ab-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c66ab-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c66ab-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c66ab-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="c66ab-114">RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="c66ab-114">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c66ab-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c66ab-115">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="c66ab-116">권장 사항</span><span class="sxs-lookup"><span data-stu-id="c66ab-116">Recommendations</span></span>  
  
-   <span data-ttu-id="c66ab-117">권장하는 복제 토폴로지를 스크립팅할 경우 게시 스크립트는 데이터 파티션을 만드는 저장 프로시저 호출을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-117">If you script a replication topology, which is recommended, publication scripts contain the stored procedure calls to create data partitions.</span></span> <span data-ttu-id="c66ab-118">스크립트는 생성된 파티션에 대한 참조와 하나 이상의 파티션을 다시 만드는 방법(필요한 경우)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-118">The script provides a reference for the partitions created and a way in which to re-create one or more partitions if necessary.</span></span> <span data-ttu-id="c66ab-119">자세한 내용은 [Scripting Replication](../scripting-replication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c66ab-119">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
-   <span data-ttu-id="c66ab-120">겹치지 않는 파티션과 함께 구독을 생성하는 매개 변수가 있는 필터가 게시에 사용된 경우 특정 구독이 손실되어 다시 만들어야 하면 구독된 파티션을 제거하고 구독을 다시 만든 다음 파티션을 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-120">When a publication has parameterized filters that yield subscriptions with nonoverlapping partitions, and if a particular subscription is lost and needs to be re-created, you must do the following: remove the partition that was subscribed to, re-create the subscription, and then re-create the partition.</span></span> <span data-ttu-id="c66ab-121">자세한 내용은 [매개 변수가 있는 행 필터](../merge/parameterized-filters-parameterized-row-filters.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c66ab-121">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span> <span data-ttu-id="c66ab-122">복제에서는 게시 만들기 스크립트가 생성될 때 기존 구독자 파티션에 대한 만들기 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-122">Replication generates creation scripts for existing Subscriber partitions when a publication creation script is generated.</span></span> <span data-ttu-id="c66ab-123">자세한 내용은 [Scripting Replication](../scripting-replication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c66ab-123">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c66ab-124">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="c66ab-124">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="c66ab-125">**게시 속성 - \<Publication>** 대화 상자의 **데이터 파티션** 페이지에서 파티션을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-125">Manage partitions on the **Data Partitions** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="c66ab-126">이 대화 상자에 액세스하는 방법은 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c66ab-126">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span> <span data-ttu-id="c66ab-127">이 페이지에서는 파티션을 만들거나 삭제하고, 구독자가 스냅샷 생성 및 배달을 시작하도록 허용하고, 하나 이상의 파티션에 대한 스냅샷을 생성하고, 스냅샷을 정리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-127">On this page you can: create and delete partitions; allow Subscribers to initiate snapshot generation and delivery; generate snapshots for one or more partitions; and clean up snapshots.</span></span>  
  
#### <a name="to-create-a-partition"></a><span data-ttu-id="c66ab-128">파티션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="c66ab-128">To create a partition</span></span>  
  
1.  <span data-ttu-id="c66ab-129">**게시 속성 - \<Publication>** 대화 상자의 **데이터 파티션** 페이지에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-129">On the **Data Partitions** page of the **Publication Properties - \<Publication>** dialog box, click **Add**.</span></span>  
  
2.  <span data-ttu-id="c66ab-130">**데이터 파티션 추가** 대화 상자에서 만들려는 파티션에 연결된 **HOST_NAME()** 및/또는 **SUSER_SNAME()** 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-130">In the **Add Data Partition** dialog box, enter a value for the **HOST_NAME()** and/or **SUSER_SNAME()** value associated with the partition you want to create.</span></span>  
  
3.  <span data-ttu-id="c66ab-131">선택적으로 스냅샷을 새로 고칠 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-131">Optionally specify a schedule for refreshing snapshots:</span></span>  
  
    1.  <span data-ttu-id="c66ab-132">**이 파티션에 대한 스냅샷 에이전트의 실행 시간을 다음 시간으로 예약**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-132">Select **Schedule the Snapshot Agent for this partition to run at the following time(s)**</span></span>  
  
    2.  <span data-ttu-id="c66ab-133">기본으로 제공되는 스냅샷 새로 고침 일정을 그대로 적용하거나 **변경** 을 클릭하여 다른 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-133">Accept the default schedule for refreshing snapshots, or click **Change** to specify a different schedule.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-partition"></a><span data-ttu-id="c66ab-134">파티션을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="c66ab-134">To delete a partition</span></span>  
  
1.  <span data-ttu-id="c66ab-135">**데이터 파티션** 페이지의 표에서 파티션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-135">On the **Data Partitions** page, select a partition in the grid.</span></span>  
  
2.  <span data-ttu-id="c66ab-136">**삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-136">Click **Delete**.</span></span>  
  
#### <a name="to-allow-subscribers-to-initiate-snapshot-generation-and-delivery"></a><span data-ttu-id="c66ab-137">구독자가 스냅샷 생성 및 배달을 시작하도록 허용하려면</span><span class="sxs-lookup"><span data-stu-id="c66ab-137">To allow Subscribers to initiate snapshot generation and delivery</span></span>  
  
1.  <span data-ttu-id="c66ab-138">**데이터 파티션** 페이지에서 **새 구독자가 동기화할 때 필요한 경우 자동으로 파티션 정의 및 스냅샷 생성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-138">On the **Data Partitions** page, select **Automatically define a partition and generate a snapshot if needed when a new Subscriber tries to synchronize**.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-generate-a-snapshot-for-a-partition"></a><span data-ttu-id="c66ab-139">파티션에 대한 스냅샷을 생성하려면</span><span class="sxs-lookup"><span data-stu-id="c66ab-139">To generate a snapshot for a partition</span></span>  
  
1.  <span data-ttu-id="c66ab-140">**데이터 파티션** 페이지의 표에서 파티션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-140">On the **Data Partitions** page, select a partition in the grid.</span></span>  
  
2.  <span data-ttu-id="c66ab-141">**선택한 스냅샷 지금 생성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-141">Click **Generate the selected snapshots now**.</span></span>  
  
#### <a name="to-clean-up-a-snapshot-for-a-partition"></a><span data-ttu-id="c66ab-142">파티션에 대한 스냅샷을 정리하려면</span><span class="sxs-lookup"><span data-stu-id="c66ab-142">To clean up a snapshot for a partition</span></span>  
  
1.  <span data-ttu-id="c66ab-143">**데이터 파티션** 페이지의 표에서 파티션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-143">On the **Data Partitions** page, select a partition in the grid.</span></span>  
  
2.  <span data-ttu-id="c66ab-144">**기존 스냅샷 정리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-144">Click **Clean up the existing snapshots**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c66ab-145">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="c66ab-145">Using Transact-SQL</span></span>  
 <span data-ttu-id="c66ab-146">매개 변수가 있는 필터를 사용하여 게시를 보다 잘 관리하려면 복제 저장 프로시저를 사용하여 기존 파티션을 프로그래밍 방식으로 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-146">To better manage a publication with parameterized filters, you can programmatically enumerate the existing partitions using replication stored procedures.</span></span> <span data-ttu-id="c66ab-147">파티션을 만들거나 기존 파티션을 삭제할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-147">You can also create and delete existing partitions.</span></span> <span data-ttu-id="c66ab-148">기존 파티션의 다음 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-148">The following information on existing partitions can be obtained:</span></span>  
  
-   <span data-ttu-id="c66ab-149">파티션이 필터링되는 방법([SUSER_SNAME&#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) 또는 [HOST_NAME&#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) 사용)</span><span class="sxs-lookup"><span data-stu-id="c66ab-149">How a partition is filtered (using [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) or [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql)).</span></span>  
  
-   <span data-ttu-id="c66ab-150">분할된 스냅샷을 생성하는 작업의 이름</span><span class="sxs-lookup"><span data-stu-id="c66ab-150">The name of the job that generates a partitioned snapshot.</span></span>  
  
-   <span data-ttu-id="c66ab-151">분할된 스냅샷 작업이 마지막으로 실행된 시간</span><span class="sxs-lookup"><span data-stu-id="c66ab-151">The last time that a partitioned snapshot job ran.</span></span>  
  
 <span data-ttu-id="c66ab-152">두 부분으로 구성된 스냅샷의 두 번째 부분은 새 구독이 초기화될 때 요청에 따라 생성될 수 있지만, 아래의 절차를 사용하면 이 스냅샷이 생성되는 방식을 제어하고 가장 편리할 때 이 스냅샷을 미리 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-152">While the second part of the two-part snapshot can be generated on-demand when a new subscription is initialized, the procedures below enable you to control how this snapshot is generated and to pre-generate this snapshot when it is most convenient.</span></span> <span data-ttu-id="c66ab-153">자세한 내용은 [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c66ab-153">For more information, see [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md).</span></span>  
  
#### <a name="to-view-information-on-existing-partitions"></a><span data-ttu-id="c66ab-154">기존 파티션의 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="c66ab-154">To view information on existing partitions</span></span>  
  
1.  <span data-ttu-id="c66ab-155">게시 데이터베이스의 게시자에서 [sp_helpmergepartition&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-155">At the Publisher on the publication database, execute [sp_helpmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql).</span></span> <span data-ttu-id="c66ab-156">\*\* \@ 게시\*\*에 대 한 게시의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-156">Specify the name of the publication for **\@publication**.</span></span> <span data-ttu-id="c66ab-157">필드 단일 필터링 기준에 따라 정보만 반환 하려면 \*\* \@ suser_sname\*\* 또는 \*\* \@ host_name\*\* 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-157">(Optional) Specify **\@suser_sname** or **\@host_name** to return only information based on a single filtering criterion.</span></span>  
  
#### <a name="to-define-a-new-partition-and-generate-a-new-partitioned-snapshot"></a><span data-ttu-id="c66ab-158">새 파티션을 정의하고 새 분할된 스냅샷을 생성하려면</span><span class="sxs-lookup"><span data-stu-id="c66ab-158">To define a new partition and generate a new partitioned snapshot</span></span>  
  
1.  <span data-ttu-id="c66ab-159">게시 데이터베이스의 게시자에서 [sp_addmergepartition&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-159">At the Publisher on the publication database, execute [sp_addmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql).</span></span> <span data-ttu-id="c66ab-160">\*\* \@ 게시\*\*에 대 한 게시 이름 및 다음 중 하나에 대 한 파티션을 정의 하는 매개 변수가 있는 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-160">Specify the name of the publication for **\@publication**, and the parameterized value that defines the partition for one of the following:</span></span>  
  
    -   <span data-ttu-id="c66ab-161">\*\* \@ suser_sname\*\* -매개 변수가 있는 필터가 [SUSER_SNAME &#40;transact-sql&#41;](/sql/t-sql/functions/suser-sname-transact-sql)에서 반환 된 값으로 정의 되는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-161">**\@suser_sname** - when the parameterized filter is defined by the value returned by [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql).</span></span>  
  
    -   <span data-ttu-id="c66ab-162">\*\* \@ host_name\*\* -매개 변수가 있는 필터가 [HOST_NAME &#40;transact-sql&#41;](/sql/t-sql/functions/host-name-transact-sql)에서 반환 된 값으로 정의 되는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-162">**\@host_name** - when the parameterized filter is defined by the value returned by [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql).</span></span>  
  
2.  <span data-ttu-id="c66ab-163">이 새 파티션에 대해 매개 변수가 있는 스냅샷을 만들고 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-163">Create and initialize the parameterized snapshot for this new partition.</span></span> <span data-ttu-id="c66ab-164">자세한 내용은 [매개 변수가 있는 필터로 병합 게시에 대한 스냅샷 만들기](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c66ab-164">For more information, see [Create a Snapshot for a Merge Publication with Parameterized Filters](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).</span></span>  
  
#### <a name="to-delete-a-partition"></a><span data-ttu-id="c66ab-165">파티션을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="c66ab-165">To delete a partition</span></span>  
  
1.  <span data-ttu-id="c66ab-166">게시 데이터베이스의 게시자에서 [sp_dropmergepartition&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-166">At the Publisher on the publication database, execute [sp_dropmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql).</span></span> <span data-ttu-id="c66ab-167">\*\* \@ 게시\*\* 에 대 한 게시 이름 및 다음 중 하나에 대 한 파티션을 정의 하는 매개 변수가 있는 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-167">Specify the name of the publication for **\@publication** and the parameterized value that defines the partition for one of the following:</span></span>  
  
    -   <span data-ttu-id="c66ab-168">\*\* \@ suser_sname\*\* -매개 변수가 있는 필터가 [SUSER_SNAME &#40;transact-sql&#41;](/sql/t-sql/functions/suser-sname-transact-sql)에서 반환 된 값으로 정의 되는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-168">**\@suser_sname** - when the parameterized filter is defined by the value returned by [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql).</span></span>  
  
    -   <span data-ttu-id="c66ab-169">\*\* \@ host_name\*\* -매개 변수가 있는 필터가 [HOST_NAME &#40;transact-sql&#41;](/sql/t-sql/functions/host-name-transact-sql)에서 반환 된 값으로 정의 되는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-169">**\@host_name** - when the parameterized filter is defined by the value returned by [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql).</span></span>  
  
     <span data-ttu-id="c66ab-170">이 경우 파티션에 대한 스냅샷 작업과 스냅샷 파일도 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-170">This also removes the snapshot job and any snapshot files for the partition.</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="c66ab-171">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="c66ab-171">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="c66ab-172">매개 변수가 있는 필터를 사용하여 게시를 보다 잘 관리하려면 RMO(복제 관리 개체)를 사용하여 새 구독자 파티션을 프로그래밍 방식으로 만들고, 기존 구독자 파티션을 열거하고, 프로그래밍 방식으로 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-172">To better manage a publication with parameterized filters, you can programmatically create new Subscriber partitions, enumerate the existing Subscriber partitions, and delete Subscriber partitions by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="c66ab-173">구독자 파티션을 만드는 방법은 [Create a Snapshot for a Merge Publication with Parameterized Filters](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c66ab-173">For information about how to create Subscriber partitions, see [Create a Snapshot for a Merge Publication with Parameterized Filters](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).</span></span> <span data-ttu-id="c66ab-174">기존 파티션에 대한 다음 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-174">The following information about existing partitions can be obtained:</span></span>  
  
-   <span data-ttu-id="c66ab-175">파티션에서 기반으로 사용하는 값 및 필터링 기능</span><span class="sxs-lookup"><span data-stu-id="c66ab-175">The value and filtering function upon which the partition is based.</span></span>  
  
-   <span data-ttu-id="c66ab-176">구독자에 대해 매개 변수가 있는 스냅샷을 생성하는 작업의 이름</span><span class="sxs-lookup"><span data-stu-id="c66ab-176">The name of the job that generates a parameterized snapshot for the Subscriber.</span></span>  
  
-   <span data-ttu-id="c66ab-177">매개 변수가 있는 스냅샷 작업이 마지막으로 실행된 시간</span><span class="sxs-lookup"><span data-stu-id="c66ab-177">The last time that a parameterized snapshot job ran.</span></span>  
  
#### <a name="to-view-information-on-existing-partitions"></a><span data-ttu-id="c66ab-178">기존 파티션의 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="c66ab-178">To view information on existing partitions</span></span>  
  
1.  <span data-ttu-id="c66ab-179"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-179">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="c66ab-180"><xref:Microsoft.SqlServer.Replication.MergePublication> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-180">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class.</span></span> <span data-ttu-id="c66ab-181">게시의 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 및 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 속성을 설정하고 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 1단계에서 만든 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-181">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> created in step 1.</span></span>  
  
3.  <span data-ttu-id="c66ab-182"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-182">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="c66ab-183">이 메서드가 `false`를 반환하는 경우 2단계에서 게시 속성이 올바르게 정의되지 않았거나 게시가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-183">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="c66ab-184"><xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> 메서드를 호출하고 해당 결과를 <xref:Microsoft.SqlServer.Replication.MergePartition> 개체의 배열에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-184">Call the <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> method, and pass the result to an array of <xref:Microsoft.SqlServer.Replication.MergePartition> objects.</span></span>  
  
5.  <span data-ttu-id="c66ab-185">배열의 각 <xref:Microsoft.SqlServer.Replication.MergePartition> 개체에 대해 원하는 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-185">For each <xref:Microsoft.SqlServer.Replication.MergePartition> object in the array, get any properties of interest.</span></span>  
  
#### <a name="to-delete-existing-partitions"></a><span data-ttu-id="c66ab-186">기존 파티션을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="c66ab-186">To delete existing partitions</span></span>  
  
1.  <span data-ttu-id="c66ab-187"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-187">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="c66ab-188"><xref:Microsoft.SqlServer.Replication.MergePublication> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-188">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class.</span></span> <span data-ttu-id="c66ab-189">게시의 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 및 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 속성을 설정하고 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 1단계에서 만든 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-189">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> created in step 1.</span></span>  
  
3.  <span data-ttu-id="c66ab-190"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-190">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="c66ab-191">이 메서드가 `false`를 반환하는 경우 2단계에서 게시 속성이 올바르게 정의되지 않았거나 게시가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-191">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="c66ab-192"><xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> 메서드를 호출하고 해당 결과를 <xref:Microsoft.SqlServer.Replication.MergePartition> 개체의 배열에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-192">Call the <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> method, and pass the result to an array of <xref:Microsoft.SqlServer.Replication.MergePartition> objects.</span></span>  
  
5.  <span data-ttu-id="c66ab-193">배열의 각 <xref:Microsoft.SqlServer.Replication.MergePartition> 개체에 대해 파티션을 삭제할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-193">For each <xref:Microsoft.SqlServer.Replication.MergePartition> object in the array, determine whether the partition should be deleted.</span></span> <span data-ttu-id="c66ab-194">이를 결정할 때는 일반적으로 <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A> 속성이나 <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A> 속성의 값을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-194">This decision is usually based on the value of the <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A> property or the <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A> property.</span></span>  
  
6.  <span data-ttu-id="c66ab-195">2단계에서 만든 <xref:Microsoft.SqlServer.Replication.MergePublication.RemoveMergePartition%2A> 의 개체에서 <xref:Microsoft.SqlServer.Replication.MergePublication> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-195">Call the <xref:Microsoft.SqlServer.Replication.MergePublication.RemoveMergePartition%2A> method on the <xref:Microsoft.SqlServer.Replication.MergePublication> object from step 2.</span></span> <span data-ttu-id="c66ab-196">5단계에서 만든 <xref:Microsoft.SqlServer.Replication.MergePartition> 개체를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-196">Pass the <xref:Microsoft.SqlServer.Replication.MergePartition> object from step 5.</span></span>  
  
7.  <span data-ttu-id="c66ab-197">삭제된 각 파티션에 대해 6단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="c66ab-197">Repeat step 6 for each partition that is deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c66ab-198">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c66ab-198">See Also</span></span>  
 <span data-ttu-id="c66ab-199">[매개 변수가 있는 행 필터](../merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="c66ab-199">[Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="c66ab-200">매개 변수가 있는 필터를 사용하는 병합 게시의 스냅샷</span><span class="sxs-lookup"><span data-stu-id="c66ab-200">Snapshots for Merge Publications with Parameterized Filters</span></span>](../snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  
