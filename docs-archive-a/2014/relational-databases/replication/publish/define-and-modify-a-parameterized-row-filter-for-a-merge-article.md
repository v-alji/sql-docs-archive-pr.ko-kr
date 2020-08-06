---
title: 병합 아티클에 대한 매개 변수가 있는 행 필터 정의 및 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/02/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- parameterized filters [SQL Server replication], defining
- parameterized filters [SQL Server replication], modifying
- merge replication [SQL Server replication], dynamic filters
- merge replication parameterized filters [SQL Server replication]
- filters [SQL Server replication], parameterized
- modifying filters, parameterized row
- dynamic filters [SQL Server replication]
ms.assetid: de0482a2-3cc8-4030-8a4a-14364549ac9f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d80ad53661aced22795220507398e2fcc510edd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736167"
---
# <a name="define-and-modify-a-parameterized-row-filter-for-a-merge-article"></a><span data-ttu-id="e79f0-102">병합 아티클에 대한 매개 변수가 있는 행 필터 정의 및 수정</span><span class="sxs-lookup"><span data-stu-id="e79f0-102">Define and Modify a Parameterized Row Filter for a Merge Article</span></span>
  <span data-ttu-id="e79f0-103">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 매개 변수가 있는 행 필터를 정의하고 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-103">This topic describes how to define and modify a parameterized row filter in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="e79f0-104">테이블 아티클을 만들 때 매개 변수가 있는 행 필터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-104">When creating table articles, you can use parameterized row filters.</span></span> <span data-ttu-id="e79f0-105">이러한 필터에서는 게시할 해당 데이터를 선택하기 위해 [WHERE](/sql/t-sql/queries/where-transact-sql) 절을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-105">These filters use a [WHERE](/sql/t-sql/queries/where-transact-sql) clause to select the appropriate data to be published.</span></span> <span data-ttu-id="e79f0-106">정적 행 필터와는 달리 해당 절에 리터럴 값을 지정하는 대신 [SUSER_SNAME](/sql/t-sql/functions/suser-sname-transact-sql) 및 [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) 시스템 함수를 하나 또는 둘 모두 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-106">Rather than specifying a literal value in the clause (as you do with a static row filter), you specify one or both of the following system functions: [SUSER_SNAME](/sql/t-sql/functions/suser-sname-transact-sql) and [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql).</span></span> <span data-ttu-id="e79f0-107">자세한 내용은 [매개 변수가 있는 행 필터](../merge/parameterized-filters-parameterized-row-filters.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e79f0-107">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e79f0-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e79f0-108">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e79f0-109">제한 사항</span><span class="sxs-lookup"><span data-stu-id="e79f0-109">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e79f0-110">게시에 대한 구독이 초기화된 후 매개 변수가 있는 행 필터를 추가, 수정 또는 삭제한 경우에는 변경 내용을 적용한 후에 새 스냅샷을 생성하고 모든 구독을 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-110">If you add, modify, or delete a parameterized row filter after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="e79f0-111">속성 변경 요구 사항에 대한 자세한 내용은 [게시 및 아티클 속성 변경](change-publication-and-article-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e79f0-111">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="e79f0-112">권장 사항</span><span class="sxs-lookup"><span data-stu-id="e79f0-112">Recommendations</span></span>  
  
-   <span data-ttu-id="e79f0-113">성능상의 이유로 `LEFT([MyColumn]) = SUSER_SNAME()`과 같은 매개 변수가 있는 행 필터 절의 열 이름에는 함수를 적용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-113">For performance reasons, we recommend that you not apply functions to column names in parameterized row filter clauses, such as `LEFT([MyColumn]) = SUSER_SNAME()`.</span></span> <span data-ttu-id="e79f0-114">필터 절에 HOST_NAME을 사용하고 HOST_NAME 값을 재지정할 경우 CONVERT를 사용하여 데이터 형식을 변환해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-114">If you use HOST_NAME in a filter clause and override the HOST_NAME value, it might be necessary to convert data types using CONVERT.</span></span> <span data-ttu-id="e79f0-115">이를 위한 최선의 구현 방법은 [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)항목의 "HOST_NAME() 값 재정의" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e79f0-115">For more information about best practices for this case, see the section "Overriding the HOST_NAME() Value" in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e79f0-116">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="e79f0-116">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="e79f0-117">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자의 **행 필터** 페이지에서 매개 변수가 있는 행 필터를 정의, 수정 및 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-117">Define, modify, and delete parameterized row filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="e79f0-118">마법사 사용 및 대화 상자 액세스에 대한 자세한 내용은 [게시 만들기](create-a-publication.md) 및 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e79f0-118">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-define-a-parameterized-row-filter"></a><span data-ttu-id="e79f0-119">매개 변수가 있는 행 필터를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="e79f0-119">To define a parameterized row filter</span></span>  
  
1.  <span data-ttu-id="e79f0-120">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 의 **행 필터** 페이지에서 **추가**를 클릭하고 **필터 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-120">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, click **Add**, and then click **Add Filter**.</span></span>  
  
2.  <span data-ttu-id="e79f0-121">**필터 추가** 대화 상자의 드롭다운 목록 상자에서 필터링할 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-121">In the **Add Filter** dialog box, select a table to filter from the drop-down list box.</span></span>  
  
3.  <span data-ttu-id="e79f0-122">**필터 문** 입력란에서 필터 문을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-122">Create a filter statement in the **Filter statement** text box.</span></span> <span data-ttu-id="e79f0-123">텍스트 영역에 직접 입력할 수도 있고 **열** 목록 상자에서 열을 끌어서 놓을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-123">You can type directly in the text area, and you can also drag and drop columns from the **Columns** list box.</span></span>  
  
    -   <span data-ttu-id="e79f0-124">**필터 문** 텍스트 영역에는 다음 형식의 기본 텍스트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-124">The **Filter statement** text area includes the default text, which is in the form of:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [tableowner].[tablename] WHERE  
        ```  
  
    -   <span data-ttu-id="e79f0-125">기본 텍스트는 변경할 수 없습니다. 표준 SQL 구문을 사용하여 WHERE 키워드 뒤에 필터 절을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-125">The default text cannot be changed; type the filter clause after the WHERE keyword using standard SQL syntax.</span></span> <span data-ttu-id="e79f0-126">매개 변수가 있는 필터는 `HOST_NAME()` 및/또는 `SUSER_SNAME()` 시스템 함수 또는 이러한 함수 중 하나 또는 둘 다를 참조하는 사용자 정의 함수에 대한 호출을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-126">A parameterized filter includes a call to the system function `HOST_NAME()` and/or `SUSER_SNAME()`, or a user-defined function that references one or both of these functions.</span></span> <span data-ttu-id="e79f0-127">다음 예에서는 매개 변수가 있는 행 필터에 대한 전체 필터 절입니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-127">The following is an example of a complete filter clause for a parameterized row filter:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE LoginID = SUSER_SNAME()  
        ```  
  
         <span data-ttu-id="e79f0-128">WHERE 절은 두 부분으로 구성된 이름을 사용해야 하며 세 부분 또는 네 부분으로 구성된 이름은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-128">The WHERE clause should use two-part naming; three-part naming and four-part naming are not supported.</span></span>  
  
4.  <span data-ttu-id="e79f0-129">구독자 간에 데이터를 공유하는 방식과 일치하는 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-129">Select the option that matches how data will be shared among Subscribers:</span></span>  
  
    -   <span data-ttu-id="e79f0-130">**이 테이블의 행을 여러 구독으로 이동**</span><span class="sxs-lookup"><span data-stu-id="e79f0-130">**A row from this table will go to multiple subscriptions**</span></span>  
  
    -   <span data-ttu-id="e79f0-131">**이 테이블의 행을 단일 구독으로 이동**</span><span class="sxs-lookup"><span data-stu-id="e79f0-131">**A row from this table will go to only one subscription**</span></span>  
  
     <span data-ttu-id="e79f0-132">**이 테이블의 행을 단일 구독으로 이동**을 선택하면 병합 복제에서는 보다 작은 메타데이터를 저장하고 처리하여 성능을 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-132">If you select **A row from this table will go to only one subscription**, merge replication can optimize performance by storing and processing less metadata.</span></span> <span data-ttu-id="e79f0-133">그러나 한 행이 둘 이상의 구독자로 복제될 수 없도록 데이터가 분할되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-133">However, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber.</span></span> <span data-ttu-id="e79f0-134">자세한 내용은 [매개 변수가 있는 행 필터](../merge/parameterized-filters-parameterized-row-filters.md)항목의 "'partition options' 설정" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e79f0-134">For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="e79f0-135">**게시 속성 - \<Publication>** 대화 상자에서 **확인**을 클릭하여 저장하고 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-135">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-modify-a-parameterized-row-filter"></a><span data-ttu-id="e79f0-136">매개 변수가 있는 행 필터를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="e79f0-136">To modify a parameterized row filter</span></span>  
  
1.  <span data-ttu-id="e79f0-137">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자의 **행 필터** 페이지에 있는 **필터링된 테이블** 창에서 필터를 선택하고 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-137">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="e79f0-138">**필터 편집** 대화 상자에서 필터를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-138">In the **Edit Filter** dialog box, modify the filter.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-parameterized-row-filter"></a><span data-ttu-id="e79f0-139">매개 변수가 있는 행 필터를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="e79f0-139">To delete a parameterized row filter</span></span>  
  
1.  <span data-ttu-id="e79f0-140">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자의 **행 필터** 페이지에 있는 **필터링된 테이블** 창에서 필터를 선택하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-140">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span>  
  

  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e79f0-141">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="e79f0-141">Using Transact-SQL</span></span>  
 <span data-ttu-id="e79f0-142">복제 저장 프로시저를 사용하여 매개 변수가 있는 행 필터를 프로그래밍 방식으로 만들거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-142">Parameterized row filters can be created and modified programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-define-a-parameterized-row-filter-for-an-article-in-a-merge-publication"></a><span data-ttu-id="e79f0-143">병합 게시에서 아티클에 대한 매개 변수가 있는 행 필터를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="e79f0-143">To define a parameterized row filter for an article in a merge publication</span></span>  
  
1.  <span data-ttu-id="e79f0-144">게시 데이터베이스의 게시자에서 [sp_addmergearticle&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-144">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="e79f0-145">에 **@publication** 아티클의 이름,에 **@article** 게시 되는 테이블,에 **@source_object** 매개 변수가 있는 필터를 정의 하는 where 절 **@subset_filterclause** (포함 하지 않음), `WHERE` 에 매개 변수가 있는 **@partition_options** 행 필터의 결과로 생성 되는 분할 유형을 설명 하는에 대 한 다음 값 중 하나를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-145">Specify **@publication**, a name for the article for **@article**, the table being published for **@source_object**, the WHERE clause that defines the parameterized filter for **@subset_filterclause** (not including `WHERE`), and one of the following values for **@partition_options**, which describes the type of partitioning that will result from the parameterized row filter:</span></span>  
  
    -   <span data-ttu-id="e79f0-146">**0** - 아티클의 필터링이 정적이거나 각 파티션에 대한 데이터의 고유 하위 집합을 생성합니다. 즉 "겹치는" 파티션을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-146">**0** - Filtering for the article either is static or does not yield a unique subset of data for each partition (an "overlapping" partition).</span></span>  
  
    -   <span data-ttu-id="e79f0-147">**1** - 결과 파티션이 겹치며 구독자에 변경된 내용이 있어도 행이 속한 파티션이 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-147">**1** - Resulting partitions are overlapping, and updates made at the Subscriber cannot change the partition to which a row belongs.</span></span>  
  
    -   <span data-ttu-id="e79f0-148">**2** - 아티클을 필터링하면 겹치지 않는 파티션이 생성되지만 여러 구독자가 동일한 파티션을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-148">**2** - Filtering for the article yields nonoverlapping partitions, but multiple Subscribers can receive the same partition.</span></span>  
  
    -   <span data-ttu-id="e79f0-149">**3** - 아티클을 필터링하면 각 구독에 고유한 겹치지 않는 파티션이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-149">**3** - Filtering for the article yields nonoverlapping partitions that are unique for each subscription.</span></span>  
  
#### <a name="to-change-a-parameterized-row-filter-for-an-article-in-a-merge-publication"></a><span data-ttu-id="e79f0-150">병합 게시에서 아티클에 대한 매개 변수가 있는 행 필터를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="e79f0-150">To change a parameterized row filter for an article in a merge publication</span></span>  
  
1.  <span data-ttu-id="e79f0-151">게시 데이터베이스의 게시자에서 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-151">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="e79f0-152">**@publication**, **@article** ,에 값, `subset_filterclause` 에 **@property** 매개 변수가 있는 필터를 정의 하는 식 **@value** (포함 하지 않음 `WHERE` ), 및에 대해 값 **1** 을 **@force_invalidate_snapshot** **@force_reinit_subscription** 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-152">Specify **@publication**, **@article**, a value of `subset_filterclause` for **@property**, the expression that defines the parameterized filter for **@value** (not including `WHERE`), and a value of **1** for both **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="e79f0-153">이 변경 내용으로 인해 파티션에 변화가 생기면 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) 을 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-153">If this change results in different partitioning behavior, then execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) again.</span></span> <span data-ttu-id="e79f0-154">에 **@publication** 을 지정 하 **@article** `partition_options` 고에 값을,에 가장 적합 한 분할 옵션을 지정 합니다 .이 옵션은 다음 중 **@property** **@value** 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-154">Specify **@publication**, **@article**, a value of `partition_options` for **@property**, and the most appropriate partitioning option for **@value**, which can be one of the following:</span></span>  
  
    -   <span data-ttu-id="e79f0-155">**0** - 아티클의 필터링이 정적이거나 각 파티션에 대한 데이터의 고유 하위 집합을 생성합니다. 즉 "겹치는" 파티션을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-155">**0** - Filtering for the article either is static or does not yield a unique subset of data for each partition (an "overlapping" partition).</span></span>  
  
    -   <span data-ttu-id="e79f0-156">**1** - 결과 파티션이 겹치며 구독자에 변경된 내용이 있어도 행이 속한 파티션이 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-156">**1** - Resulting partitions are overlapping, and updates made at the Subscriber cannot change the partition to which a row belongs.</span></span>  
  
    -   <span data-ttu-id="e79f0-157">**2** - 아티클을 필터링하면 겹치지 않는 파티션이 생성되지만 여러 구독자가 동일한 파티션을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-157">**2** - Filtering for the article yields nonoverlapping partitions, but multiple Subscribers can receive the same partition.</span></span>  
  
    -   <span data-ttu-id="e79f0-158">**3** - 아티클을 필터링하면 각 구독에 고유한 겹치지 않는 파티션이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-158">**3** - Filtering for the article yields nonoverlapping partitions that are unique for each subscription.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="e79f0-159">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e79f0-159">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="e79f0-160">다음 예에서는 병합 게시의 아티클 그룹을 정의합니다. 이 병합 게시에서는 `Employee` LoginID **열을 기준으로 매개 변수가 있는 행 필터를 사용하여 자체 필터링되는** 테이블에 대해 일련의 조인 필터로 아티클이 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-160">This example defines a group of articles in a merge publication where the articles are filtered with a series of join filters against the `Employee` table that is itself filtered using a parameterized row filter on the **LoginID** column.</span></span> <span data-ttu-id="e79f0-161">동기화 중에 [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) 함수에서 반환하는 값은 재정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e79f0-161">During synchronization, the value returned by the [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) function is overridden.</span></span> <span data-ttu-id="e79f0-162">자세한 내용은 [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)항목의 HOST_NAME() 값 재정의를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e79f0-162">For more information, see Overriding the HOST_NAME() Value in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubdynamic1.sql#sp_mergedynamicpub1)]  
  
  
## <a name="see-also"></a><span data-ttu-id="e79f0-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e79f0-163">See Also</span></span>  
 <span data-ttu-id="e79f0-164">[병합 아티클 사이에서 조인 필터 정의 및 수정](define-and-modify-a-join-filter-between-merge-articles.md) </span><span class="sxs-lookup"><span data-stu-id="e79f0-164">[Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md) </span></span>  
 <span data-ttu-id="e79f0-165">[게시 및 아티클 속성 변경](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="e79f0-165">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="e79f0-166">[Join Filters](../merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="e79f0-166">[Join Filters](../merge/join-filters.md) </span></span>  
 [<span data-ttu-id="e79f0-167">매개 변수가 있는 행 필터</span><span class="sxs-lookup"><span data-stu-id="e79f0-167">Parameterized Row Filters</span></span>](../merge/parameterized-filters-parameterized-row-filters.md)  
  
  
