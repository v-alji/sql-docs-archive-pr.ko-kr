---
title: 매개 변수가 있는 행 필터 최적화 | Microsoft 문서
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- precomputed partitions [SQL Server replication]
- filters [SQL Server replication], parameterized
- merge replication precomputed partitions [SQL Server replication], SQL Server Management Studio
- parameterized filters [SQL Server replication], optimizing
ms.assetid: 49349605-ebd0-4757-95be-c0447f30ba13
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f1c6448d8e2dba7a68fab441d4d08fd4a4a1db4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740819"
---
# <a name="optimize-parameterized-row-filters"></a><span data-ttu-id="f895a-102">매개 변수가 있는 행 필터 최적화</span><span class="sxs-lookup"><span data-stu-id="f895a-102">Optimize Parameterized Row Filters</span></span>
  <span data-ttu-id="f895a-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 매개 변수가 있는 행 필터를 최적화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-103">This topic describes how to optimize parameterized row filters in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f895a-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="f895a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f895a-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="f895a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f895a-106">권장 사항</span><span class="sxs-lookup"><span data-stu-id="f895a-106">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="f895a-107">**매개 변수가 있는 행 필터를 최적화하려면:**</span><span class="sxs-lookup"><span data-stu-id="f895a-107">**To optimize parameterized row filters, using:**</span></span>  
  
     [<span data-ttu-id="f895a-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f895a-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f895a-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f895a-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f895a-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f895a-110">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="f895a-111">권장 사항</span><span class="sxs-lookup"><span data-stu-id="f895a-111">Recommendations</span></span>  
  
-   <span data-ttu-id="f895a-112">매개 변수가 있는 필터를 사용하는 경우 게시를 만들 때 **use partition groups** 옵션 또는 **keep partition changes** 옵션을 지정하여 병합 복제에서 필터가 처리되는 방법을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-112">When you use parameterized filters, you can control how the filters are processed by merge replication by specifying either the **use partition groups** option or the **keep partition changes** option when you create a publication.</span></span> <span data-ttu-id="f895a-113">이러한 옵션은 게시 데이터베이스에 추가 메타데이터를 저장함으로써 필터링된 아티클이 있는 게시의 동기화 성능을 개선합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-113">These options improve the synchronization performance for publications with filtered articles by storing additional metadata in the publication database.</span></span> <span data-ttu-id="f895a-114">아티클을 만들 때 **partition options** 를 설정하면 구독자 간에 데이터가 공유되는 방법을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-114">You can control how the data is shared among Subscribers by setting **partition options** when you create an article.</span></span> <span data-ttu-id="f895a-115">이러한 요구 사항에 대한 자세한 내용은 [매개 변수가 있는 행 필터](../merge/parameterized-filters-parameterized-row-filters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f895a-115">For more information about these requirements, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
     <span data-ttu-id="f895a-116">삭제가 올바르게 전파되도록 보장하려면 [!INCLUDE[ssEW](../../../includes/ssew-md.md)]SQL Server Compact 구독자에서 keep_partition_changes를 true로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-116">With [!INCLUDE[ssEW](../../../includes/ssew-md.md)]SQL Server Compact subscribers, keep_partition_changes must be set to true to ensure that deletes are correctly propagated.</span></span> <span data-ttu-id="f895a-117">false로 설정한 경우 구독자에 예상한 것보다 많은 행이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-117">When set to false, the subscriber might have more rows than expected.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f895a-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="f895a-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f895a-119">다음 설정을 사용하여 매개 변수가 있는 행 필터를 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-119">The following settings can be used to optimize parameterized row filters:</span></span>  
  
 <span data-ttu-id="f895a-120">**Partition Options**</span><span class="sxs-lookup"><span data-stu-id="f895a-120">**Partition Options**</span></span>  
 <span data-ttu-id="f895a-121">**아티클 속성 - \<Article>** 대화 상자 또는 **필터 추가** 대화 상자의 **속성** 페이지에서 이 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-121">Set this option on the **Properties** page of the **Article Properties - \<Article>** dialog box, or in the **Add Filter** dialog box.</span></span> <span data-ttu-id="f895a-122">두 대화 상자는 새 게시 마법사 및 **게시 속성 - \<Publication>** 대화 상자에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-122">Both dialog boxes are available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="f895a-123">**아티클 속성 - \<Article>** 대화 상자에서는 **필터 추가** 대화 상자에서 사용할 수 없는 이 옵션에 대해 값을 추가로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-123">The **Article Properties - \<Article>** dialog box allows you to specify additional values for this option that are not available in the **Add Filter** dialog box.</span></span>  
  
 <span data-ttu-id="f895a-124">**파티션 미리 계산**</span><span class="sxs-lookup"><span data-stu-id="f895a-124">**Precompute Partitions**</span></span>  
 <span data-ttu-id="f895a-125">게시의 아티클이 일련의 요구 사항을 충족하는 경우 이 옵션은 기본적으로 **True** 로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-125">This option is set to **True** by default if the articles in your publication adhere to a set of requirements.</span></span> <span data-ttu-id="f895a-126">이러한 요구 사항에 대한 자세한 내용은 [사전 계산 파티션으로 매개 변수가 있는 필터 성능 최적화](../merge/parameterized-filters-optimize-for-precomputed-partitions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f895a-126">For more information about these requirements, see [Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span> <span data-ttu-id="f895a-127">**게시 속성 - \<Publication>** 대화 상자의 **구독 옵션** 페이지에서 이 옵션을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-127">Modify this option on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span>  
  
 <span data-ttu-id="f895a-128">**동기화 최적화**</span><span class="sxs-lookup"><span data-stu-id="f895a-128">**Optimize Synchronization**</span></span>  
 <span data-ttu-id="f895a-129">**파티션 미리 계산** 이 **False** 로 설정된 경우에만 이 옵션을 **True**로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-129">This option should be set to **True** only if **Precompute Partitions** is set to **False**.</span></span> <span data-ttu-id="f895a-130">**게시 속성 - \<Publication>** 대화 상자의 **구독 옵션** 페이지에서 이 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-130">Set this option on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span>  
  
 <span data-ttu-id="f895a-131">새 게시 마법사 사용 및 **게시 속성 - \<Publication>** 대화 상자 액세스에 대한 자세한 내용은 [게시 만들기](create-a-publication.md) 및 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f895a-131">For more information about using the New Publication Wizard and accessing the **Publication Properties - \<Publication>** dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-set-partition-options-in-the-add-filter-or-edit-filter-dialog-box"></a><span data-ttu-id="f895a-132">필터 추가 또는 필터 편집 대화 상자에서 파티션 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="f895a-132">To set Partition options in the Add Filter or Edit Filter dialog box</span></span>  
  
1.  <span data-ttu-id="f895a-133">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자의 **행 필터** 페이지에서 **추가**를 클릭하고 **필터 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-133">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, click **Add**, and then click **Add Filter**.</span></span>  
  
2.  <span data-ttu-id="f895a-134">매개 변수가 있는 필터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-134">Create a parameterized filter.</span></span> <span data-ttu-id="f895a-135">자세한 내용은 [병합 아티클에 대한 매개 변수가 있는 행 필터 정의 및 수정](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f895a-135">For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span></span>  
  
3.  <span data-ttu-id="f895a-136">구독자 간에 데이터를 공유하는 방식과 일치하는 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-136">Select the option that matches how data will be shared among Subscribers:</span></span>  
  
    -   <span data-ttu-id="f895a-137">**이 테이블의 행을 여러 구독으로 이동**</span><span class="sxs-lookup"><span data-stu-id="f895a-137">**A row from this table will go to multiple subscriptions**</span></span>  
  
    -   <span data-ttu-id="f895a-138">**이 테이블의 행을 단일 구독으로 이동**</span><span class="sxs-lookup"><span data-stu-id="f895a-138">**A row from this table will go to only one subscription**</span></span>  
  
     <span data-ttu-id="f895a-139">**이 테이블의 행을 단일 구독으로 이동**을 선택하면 병합 복제에서는 보다 작은 메타데이터를 저장하고 처리하여 성능을 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-139">If you select **A row from this table will go to only one subscription**, merge replication can optimize performance by storing and processing less metadata.</span></span> <span data-ttu-id="f895a-140">그러나 한 행이 둘 이상의 구독자로 복제될 수 없도록 데이터가 분할되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-140">However, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber.</span></span> <span data-ttu-id="f895a-141">자세한 내용은 [매개 변수가 있는 행 필터](../merge/parameterized-filters-parameterized-row-filters.md)항목의 "'partition options' 설정" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f895a-141">For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="f895a-142">**게시 속성 - \<Publication>** 대화 상자에서 **확인**을 클릭하여 저장하고 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-142">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-set-partition-options-in-the-article-properties---article-dialog-box"></a><span data-ttu-id="f895a-143">아티클 속성 - \<Article> 대화 상자에서 파티션 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="f895a-143">To set Partition Options in the Article Properties - \<Article> dialog box</span></span>  
  
1.  <span data-ttu-id="f895a-144">새 게시 마법사의 **아티클** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자에서 테이블을 선택한 다음 **아티클 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-144">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a table, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="f895a-145">**선택한 테이블 아티클 속성 설정** 또는 **모든 테이블 아티클 속성 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-145">Click **Set Properties of Highlighted Table Article** or **Set Properties of All Table Articles**.</span></span>  
  
3.  <span data-ttu-id="f895a-146">**아티클 속성 - \<Article>** 대화 상자의 **속성** 탭에 있는 **대상 개체** 섹션에서 **파티션 옵션**에 대해 다음 값 중 하나를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-146">In the **Destination Object** section of the **Properties** tab of the **Article Properties - \<Article>** dialog box, specify one of the following values for **Partition Options**:</span></span>  
  
    -   <span data-ttu-id="f895a-147">**겹침**</span><span class="sxs-lookup"><span data-stu-id="f895a-147">**Overlapping**</span></span>  
  
    -   <span data-ttu-id="f895a-148">**겹침, 파티션 외부 데이터 변경 내용 허용 안 함**</span><span class="sxs-lookup"><span data-stu-id="f895a-148">**Overlapping, disallow out-of-partition data changes**</span></span>  
  
    -   <span data-ttu-id="f895a-149">**겹치지 않음, 단일 구독**</span><span class="sxs-lookup"><span data-stu-id="f895a-149">**Nonoverlapping, single subscription**</span></span>  
  
    -   <span data-ttu-id="f895a-150">**겹치지 않음, 구독 간 공유**</span><span class="sxs-lookup"><span data-stu-id="f895a-150">**Nonoverlapping, shared between subscriptions**</span></span>  
  
     <span data-ttu-id="f895a-151">이러한 옵션 및 이 옵션이 **필터 추가** 및 **필터 편집** 대화 상자에서 사용 가능한 옵션과 어떻게 관련되어 있는지에 대한 자세한 내용은 [매개 변수가 있는 행 필터](../merge/parameterized-filters-parameterized-row-filters.md)의 "'partition options' 설정" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f895a-151">For more information about these options and how they relate to the options available in the **Add Filter** and **Edit Filter** dialog boxes, see the "Setting 'partition options'" section of [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="f895a-152">**게시 속성 - \<Publication>** 대화 상자에서 **확인**을 클릭하여 저장하고 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-152">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-set-precompute-partitions"></a><span data-ttu-id="f895a-153">파티션 미리 계산을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="f895a-153">To set Precompute Partitions</span></span>  
  
1.  <span data-ttu-id="f895a-154">**게시 속성 - \<Publication>** 대화 상자의 **구독 옵션** 페이지에서 **파티션 사전 계산** 옵션의 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-154">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select a value for the **Precompute Partitions** option.</span></span> <span data-ttu-id="f895a-155">다음과 같은 경우 이 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-155">The property is read-only if:</span></span>  
  
    -   <span data-ttu-id="f895a-156">게시가 사전 계산 파티션의 요구 사항을 충족시키지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-156">The publication does not meet the requirements for precomputed partitions.</span></span>  
  
    -   <span data-ttu-id="f895a-157">게시에 대한 스냅샷이 아직 생성되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-157">A snapshot has not yet been generated for the publication.</span></span> <span data-ttu-id="f895a-158">이 경우 해당 옵션은 **스냅샷 생성 시기 자동 설정**의 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-158">In this case, the option displays a value of **Set automatically when a snapshot is created**.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-set-optimize-synchronization"></a><span data-ttu-id="f895a-159">동기화 최적화를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="f895a-159">To set Optimize Synchronization</span></span>  
  
1.  <span data-ttu-id="f895a-160">\*\*게시 속성- \<Publication> \*\* 대화 상자의 **구독 옵션** 페이지에서 **동기화 최적화** 옵션에 대해 **True** 값을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-160">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select a value of **True** for the **Optimize Synchronization** option.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f895a-161">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="f895a-161">Using Transact-SQL</span></span>  
 <span data-ttu-id="f895a-162">\*\* \@ Keep_partition_changes\*\* 및 \*\* \@ use_partition_groups\*\*에 대 한 필터링 옵션의 정의는 [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f895a-162">For definitions of the filtering options for **\@keep_partition_changes** and **\@use_partition_groups**, see [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span>  
  
#### <a name="to-specify-merge-filter-optimizations-when-creating-a-new-publication"></a><span data-ttu-id="f895a-163">새 게시를 만들 때 병합 필터 최적화를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="f895a-163">To specify merge filter optimizations when creating a new publication</span></span>  
  
1.  <span data-ttu-id="f895a-164">게시 데이터베이스의 게시자에서 [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-164">At the Publisher on the publication database, execute [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span> <span data-ttu-id="f895a-165">\*\* \@ 게시\*\* 를 지정 하 고 `true` 다음 매개 변수 중 하나에 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-165">Specify **\@publication** and a value of `true` for one the following parameters:</span></span>  
  
    -   <span data-ttu-id="f895a-166">\*\* \@ use_partition_groups\*\*:-아티클이 사전 계산 파티션에 대 한 요구 사항을 충족 하는 경우 가장 높은 성능 최적화를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-166">**\@use_partition_groups**: - the highest performance optimization, provided that the articles conform to the requirements for precomputed partitions.</span></span> <span data-ttu-id="f895a-167">자세한 내용은 [사전 계산 파티션으로 매개 변수가 있는 필터 성능 최적화](../merge/parameterized-filters-optimize-for-precomputed-partitions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f895a-167">For more information, see [Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span>  
  
    -   <span data-ttu-id="f895a-168">\*\* \@ keep_partition_changes\*\* -사전 계산 파티션을 사용할 수 없는 경우이 최적화를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-168">**\@keep_partition_changes** - use this optimization if precomputed partitions cannot be used.</span></span>  
  
2.  <span data-ttu-id="f895a-169">게시에 대한 스냅샷 작업을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-169">Add a snapshot job for the publication.</span></span> <span data-ttu-id="f895a-170">자세한 내용은 [게시 만들기](create-a-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f895a-170">For more information see [Create a Publication](create-a-publication.md).</span></span>  
  
3.  <span data-ttu-id="f895a-171">게시 데이터베이스의 게시자에서 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)을 실행하고 다음 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-171">At the Publisher on the publication database, execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql), specifying the following parameters:</span></span>  
  
    -   <span data-ttu-id="f895a-172">\*\* \@ 게시\*\* -1 단계에서 게시 한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-172">**\@publication** - the name of the publication from step 1.</span></span>  
  
    -   <span data-ttu-id="f895a-173">\*\* \@ 문서\*\* -아티클의 이름</span><span class="sxs-lookup"><span data-stu-id="f895a-173">**\@article** - a name for the article</span></span>  
  
    -   <span data-ttu-id="f895a-174">\*\* \@ source_object\*\* -게시 되는 데이터베이스 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-174">**\@source_object** - the database object being published.</span></span>  
  
    -   <span data-ttu-id="f895a-175">\*\* \@ subset_filterclause\*\* -아티클을 행 필터링 하는 데 사용 되는 선택적 매개 변수가 있는 필터 절입니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-175">**\@subset_filterclause** - the optional parameterized filter clause used to horizontally filter the article.</span></span>  
  
    -   <span data-ttu-id="f895a-176">\*\* \@ partition_options\*\* -필터링 된 아티클에 대 한 파티션 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-176">**\@partition_options** - the partition options for the filtered article.</span></span>  
  
4.  <span data-ttu-id="f895a-177">게시의 각 아티클에 대해 3단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-177">Repeat step 3 for each article in the publication.</span></span>  
  
5.  <span data-ttu-id="f895a-178">필요에 따라 게시 데이터베이스의 게시자에서 [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) 를 실행하여 두 아티클 간의 조인 필터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-178">(Optional) At the Publisher on the publication database, execute [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) to define a join filter between two articles.</span></span> <span data-ttu-id="f895a-179">자세한 내용은 [병합 아티클 사이에서 조인 필터 정의 및 수정](define-and-modify-a-join-filter-between-merge-articles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f895a-179">For more information, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
#### <a name="to-view-and-modify-merge-filter-behaviors-for-an-existing-publication"></a><span data-ttu-id="f895a-180">기존 게시에 대한 병합 필터 동작을 확인 및 수정하려면</span><span class="sxs-lookup"><span data-stu-id="f895a-180">To view and modify merge filter behaviors for an existing publication</span></span>  
  
1.  <span data-ttu-id="f895a-181">필드 게시 데이터베이스의 게시자에서 \*\* \@ 게시\*\*를 지정 하 여 [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-181">(Optional) At the Publisher on the publication database, execute [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specifying **\@publication**.</span></span> <span data-ttu-id="f895a-182">결과 집합에서 **keep_partition_changes** 및 **use_partition_groups** 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-182">Note the value of **keep_partition_changes** and **use_partition_groups** in the result set.</span></span>  
  
2.  <span data-ttu-id="f895a-183">필요에 따라 게시 데이터베이스의 게시자에서 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-183">(Optional) At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="f895a-184">\*\* \@ 속성\*\* 에 **use_partition_groups** 값을 지정 하 고 `true` `false` 값에 또는 \*\* \@ 값\*\*을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-184">Specify a value of **use_partition_groups** for **\@property** and either `true` or `false` for **\@value**.</span></span>  
  
3.  <span data-ttu-id="f895a-185">필요에 따라 게시 데이터베이스의 게시자에서 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-185">(Optional) At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="f895a-186">\*\* \@ 속성\*\* 에 **keep_partition_changes** 값을 지정 하 고 `true` `false` 값에 또는 \*\* \@ 값\*\*을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-186">Specify a value of **keep_partition_changes** for **\@property** and either `true` or `false` for **\@value**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f895a-187">**Keep_partition_changes**를 사용 하도록 설정 하는 경우 먼저 **use_partition_groups** 를 사용 하지 않도록 설정 하 고 \*\* \@ force_reinit_subscription\*\*에 값 **1** 을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-187">When enabling **keep_partition_changes**, you must first disable **use_partition_groups** and specify a value of **1** for **\@force_reinit_subscription**.</span></span>  
  
4.  <span data-ttu-id="f895a-188">필요에 따라 게시 데이터베이스의 게시자에서 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-188">(Optional) At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="f895a-189">\*\* \@ 속성\*\* 에 **partition_options** 값을 지정 하 고 \*\* \@ 값\*\*에 적절 한 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-189">Specify a value of **partition_options** for **\@property** and the appropriate value for **\@value**.</span></span> <span data-ttu-id="f895a-190">이러한 필터링 옵션의 정의는 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f895a-190">See [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) for definitions of these filtering options.</span></span>  
  
5.  <span data-ttu-id="f895a-191">필요에 따라 스냅샷 에이전트를 시작하여 스냅샷을 다시 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f895a-191">(Optional) Start the Snapshot Agent to regenerate the snapshot if necessary.</span></span> <span data-ttu-id="f895a-192">새 스냅샷을 생성해야 하는 변경에 대한 자세한 내용은 [게시 및 아티클 속성 변경](change-publication-and-article-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f895a-192">For information about which changes require a new snapshot to be generated, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f895a-193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f895a-193">See Also</span></span>  
 <span data-ttu-id="f895a-194">[병합 아티클 간의 조인 필터 집합 자동 생성&#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md) </span><span class="sxs-lookup"><span data-stu-id="f895a-194">[Automatically Generate a Set of Join Filters Between Merge Articles &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md) </span></span>  
 <span data-ttu-id="f895a-195">[병합 아티클에 대한 매개 변수가 있는 행 필터 정의 및 수정](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="f895a-195">[Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span></span>  
 [<span data-ttu-id="f895a-196">매개 변수가 있는 행 필터</span><span class="sxs-lookup"><span data-stu-id="f895a-196">Parameterized Row Filters</span></span>](../merge/parameterized-filters-parameterized-row-filters.md)  
  
  
