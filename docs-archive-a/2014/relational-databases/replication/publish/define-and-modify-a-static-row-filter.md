---
title: 정적 행 필터 정의 및 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- modifying filters, static row
- static row filters
- filters [SQL Server replication], static row
ms.assetid: a6ebb026-026f-4c39-b6a9-b9998c3babab
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d13fd93b6afdcce6b55e9b181f52087fd620913c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647614"
---
# <a name="define-and-modify-a-static-row-filter"></a><span data-ttu-id="579db-102">정적 행 필터 정의 및 수정</span><span class="sxs-lookup"><span data-stu-id="579db-102">Define and Modify a Static Row Filter</span></span>
  <span data-ttu-id="579db-103">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 정적 행 필터를 정의하고 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-103">This topic describes how to define and modify a static row filter in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="579db-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="579db-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="579db-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="579db-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="579db-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="579db-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="579db-107">권장 사항</span><span class="sxs-lookup"><span data-stu-id="579db-107">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="579db-108">**다음을 사용하여 정적 행 필터를 정의하고 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="579db-108">**To define and modify a static row filter, using:**</span></span>  
  
     [<span data-ttu-id="579db-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="579db-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="579db-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="579db-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="579db-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="579db-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="579db-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="579db-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="579db-113">게시에 대한 구독이 초기화된 후 정적 행 필터를 추가, 수정 또는 삭제한 경우에는 변경 내용을 적용한 후에 새 스냅샷을 생성하고 모든 구독을 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-113">If you add, modify, or delete a static row filter after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="579db-114">속성 변경 요구 사항에 대한 자세한 내용은 [게시 및 아티클 속성 변경](change-publication-and-article-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="579db-114">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
-   <span data-ttu-id="579db-115">게시에서 피어 투 피어 트랜잭션 복제를 사용할 수 있도록 설정한 경우에는 테이블을 필터링할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="579db-115">If the publication is enabled for peer-to-peer transactional replication, tables cannot be filtered.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="579db-116">권장 사항</span><span class="sxs-lookup"><span data-stu-id="579db-116">Recommendations</span></span>  
  
-   <span data-ttu-id="579db-117">이러한 필터는 정적이므로 모든 구독자가 데이터의 동일한 하위 집합을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="579db-117">Because these filters are static, all subscribers will receive the same subset of the data.</span></span> <span data-ttu-id="579db-118">병합 게시에 속한 테이블 아티클에서 동적으로 행을 필터링하여 각 구독자가 서로 다른 데이터 파티션을 받게 하려면 [병합 아티클에 대한 매개 변수가 있는 행 필터 정의 및 수정](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="579db-118">If you need to dynamically filter rows in a table article belonging to a merge publication so that each subscriber receives a different partition of the data, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span></span> <span data-ttu-id="579db-119">병합 게시에서도 기존 행 필터에 따라 관련 행을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="579db-119">Merge replication also enables you to filter related rows based on an existing row filter.</span></span> <span data-ttu-id="579db-120">자세한 내용은 [병합 아티클 사이에서 조인 필터 정의 및 수정](define-and-modify-a-join-filter-between-merge-articles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="579db-120">For more information, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="579db-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="579db-121">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="579db-122">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자의 **행 필터** 페이지에서 정적 행 필터를 정의, 수정 및 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-122">Define, modify, and delete static row filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="579db-123">마법사 사용 및 대화 상자 액세스에 대한 자세한 내용은 [게시 만들기](create-a-publication.md) 및 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="579db-123">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-define-a-static-row-filter"></a><span data-ttu-id="579db-124">정적 행 필터를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="579db-124">To define a static row filter</span></span>  
  
1.  <span data-ttu-id="579db-125">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자의 **행 필터** 페이지에서 수행하는 작업은 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="579db-125">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, the action you take depends on the type of publication:</span></span>  
  
    -   <span data-ttu-id="579db-126">스냅샷 또는 트랜잭션 게시의 경우 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-126">For a snapshot or transactional publication, click **Add**.</span></span>  
  
    -   <span data-ttu-id="579db-127">병합 게시의 경우 **추가**를 클릭한 다음 **필터 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-127">For a merge publication, click **Add**, and then click **Add Filter**.</span></span>  
  
2.  <span data-ttu-id="579db-128">**필터 추가** 대화 상자의 드롭다운 목록 상자에서 필터링할 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-128">In the **Add Filter** dialog box, select a table to filter from the drop-down list box.</span></span>  
  
3.  <span data-ttu-id="579db-129">**필터 문** 텍스트 영역에서 필터 문을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="579db-129">Create a filter statement in the **Filter statement** text area.</span></span> <span data-ttu-id="579db-130">텍스트 영역에 직접 입력할 수도 있고 **열** 목록 상자에서 열을 끌어서 놓을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="579db-130">You can type directly in the text area, and you can also drag and drop columns from the **Columns** list box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="579db-131">WHERE 절은 두 부분으로 구성된 이름을 사용해야 하며 세 부분 또는 네 부분으로 구성된 이름은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="579db-131">The WHERE clause should use two-part naming; three-part naming and four-part naming are not supported.</span></span> <span data-ttu-id="579db-132">Oracle 게시자의 게시인 경우 WHERE 절은 Oracle 구문과 호환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-132">If the publication is from an Oracle Publisher, the WHERE clause must be compliant with Oracle syntax.</span></span>  
  
    -   <span data-ttu-id="579db-133">**필터 문** 텍스트 영역에는 다음 형식의 기본 텍스트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="579db-133">The **Filter statement** text area includes the default text, which is in the form of:</span></span>  
  
        ```sql  
        SELECT <published_columns> FROM [schema].[tablename] WHERE  
        ```  
  
    -   <span data-ttu-id="579db-134">기본 텍스트는 변경할 수 없습니다. 표준 SQL 구문을 사용하여 WHERE 키워드 뒤에 필터 절을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-134">The default text cannot be changed; type the filter clause after the WHERE keyword using standard SQL syntax.</span></span> <span data-ttu-id="579db-135">전체 필터 절은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="579db-135">The complete filter clause would appear like:</span></span>  
  
        ```sql  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE [LoginID] = 'adventure-works\ranjit0'  
        ```  
  
    -   <span data-ttu-id="579db-136">정적 행 필터에는 사용자 정의 함수가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="579db-136">A static row filter can include a user-defined function.</span></span> <span data-ttu-id="579db-137">사용자 정의 함수가 있는 정적 행 필터에 대한 전체 필터 절은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="579db-137">The complete filter clause for a static row filter with a user-defined function would appear like:</span></span>  
  
        ```sql  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] WHERE MyFunction([Freight]) > 100  
        ```  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="579db-138">**게시 속성 - \<Publication>** 대화 상자에서 **확인**을 클릭하여 저장하고 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="579db-138">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-modify-a-static-row-filter"></a><span data-ttu-id="579db-139">정적 행 필터를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="579db-139">To modify a static row filter</span></span>  
  
1.  <span data-ttu-id="579db-140">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자의 **행 필터** 페이지에 있는 **필터링된 테이블** 창에서 필터를 선택하고 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-140">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, select a filter in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="579db-141">**필터 편집** 대화 상자에서 필터를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-141">In the **Edit Filter** dialog box, modify the filter.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-static-row-filter"></a><span data-ttu-id="579db-142">정적 행 필터를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="579db-142">To delete a static row filter</span></span>  
  
1.  <span data-ttu-id="579db-143">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자의 **행 필터** 페이지에 있는 **필터링된 테이블** 창에서 필터를 선택하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-143">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="579db-144">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="579db-144">Using Transact-SQL</span></span>  
 <span data-ttu-id="579db-145">테이블 아티클을 만들 때 WHERE 절을 정의하여 아티클에서 행을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="579db-145">When creating table articles, you can define a WHERE clause to filter rows out of an article.</span></span> <span data-ttu-id="579db-146">정의한 행 필터를 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="579db-146">You can also change a row filter after it has been defined.</span></span> <span data-ttu-id="579db-147">복제 저장 프로시저를 사용하면 정적 행 필터를 프로그래밍 방식으로 만들거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="579db-147">Static row filters can be created and modified programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-define-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="579db-148">스냅샷 또는 트랜잭션 게시에 대한 정적 행 필터를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="579db-148">To define a static row filter for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="579db-149">필터링할 아티클을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-149">Define the article to filter.</span></span> <span data-ttu-id="579db-150">자세한 내용은 [아티클을 정의](define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="579db-150">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="579db-151">게시 데이터베이스의 게시자에서 [sp_articlefilter&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-151">At the Publisher on the publication database, execute [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql).</span></span> <span data-ttu-id="579db-152">이때 **\@article**에 아티클 이름, **\@publication**에 게시 이름, **\@filter_name**에 필터 이름, **\@filter_clause**에 필터링 절(`WHERE`를 포함하지 않음)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-152">Specify the name of the article for **\@article**, the name of the publication for **\@publication**, a name for the filter for **\@filter_name**, and the filtering clause for **\@filter_clause** (not including `WHERE`).</span></span>  
  
3.  <span data-ttu-id="579db-153">계속 열 필터를 정의하려면 [열 필터 정의 및 수정](define-and-modify-a-column-filter.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="579db-153">If a column filter must still be defined, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span> <span data-ttu-id="579db-154">그러지 않으면 [sp_articleview&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-154">Otherwise, execute [sp_articleview &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="579db-155">이때 **\@publication**에 게시 이름, **\@article**에 필터링된 아티클 이름, **\@filter_clause**에 2단계에서 지정한 필터 절을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-155">Specify the publication name for **\@publication**, the name of the filtered article for **\@article**, and the filter clause specified in step 2 for **\@filter_clause**.</span></span> <span data-ttu-id="579db-156">이렇게 하면 필터링된 아티클에 대한 동기화 개체가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="579db-156">This creates the synchronization objects for the filtered article.</span></span>  
  
#### <a name="to-modify-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="579db-157">스냅샷 또는 트랜잭션 게시에 대한 정적 행 필터를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="579db-157">To modify a static row filter for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="579db-158">게시 데이터베이스의 게시자에서 [sp_articlefilter&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-158">At the Publisher on the publication database, execute [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql).</span></span> <span data-ttu-id="579db-159">이때 **\@article**에 아티클 이름, **\@publication**에 게시 이름, **\@filter_name**에 새 필터 이름, **\@filter_clause**에 새 필터링 절(`WHERE`를 포함하지 않음)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-159">Specify the name of the article for **\@article**, the name of the publication for **\@publication**, a name for the new filter for **\@filter_name**, and the new filtering clause for **\@filter_clause** (not including `WHERE`).</span></span> <span data-ttu-id="579db-160">이와 같이 변경하면 기존 구독의 데이터가 무효화되므로 **\@force_reinit_subscription**에 **1** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-160">Because this change will invalidate data in existing subscriptions, specify a value of **1** for **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="579db-161">게시 데이터베이스의 게시자에서 [sp_articleview&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-161">At the Publisher on the publication database, execute [sp_articleview &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="579db-162">이때 **\@publication**에 게시 이름, **\@article**에 필터링된 아티클 이름, **\@filter_clause**에 1단계에서 지정한 필터 절을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-162">Specify the publication name for **\@publication**, the name of the filtered article for **\@article**, and the filter clause specified in step 1 for **\@filter_clause**.</span></span> <span data-ttu-id="579db-163">이렇게 하면 필터링된 아티클을 정의하는 뷰가 다시 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="579db-163">This re-creates the view that defines the filtered article.</span></span>  
  
3.  <span data-ttu-id="579db-164">게시에 대해 스냅샷 에이전트 작업을 다시 실행하여 업데이트된 스냅샷을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-164">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span> <span data-ttu-id="579db-165">자세한 내용은 [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="579db-165">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
4.  <span data-ttu-id="579db-166">구독을 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-166">Reinitialize subscriptions.</span></span> <span data-ttu-id="579db-167">자세한 내용은 [구독 다시 초기화](../reinitialize-subscriptions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="579db-167">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-delete-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="579db-168">스냅샷 또는 트랜잭션 게시에 대한 정적 행 필터를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="579db-168">To delete a static row filter for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="579db-169">게시 데이터베이스의 게시자에서 [sp_articlefilter&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-169">At the Publisher on the publication database, execute [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql).</span></span> <span data-ttu-id="579db-170">이때 **\@article**에 아티클 이름, **\@publication**에 게시 이름, **\@filter_name**에 NULL 값, **\@filter_clause**에 NULL 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-170">Specify the name of the article for **\@article**, the name of the publication for **\@publication**, a value of NULL for **\@filter_name**, and a value of NULL for **\@filter_clause**.</span></span> <span data-ttu-id="579db-171">이와 같이 변경하면 기존 구독의 데이터가 무효화되므로 **\@force_reinit_subscription**에 **1** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-171">Because this change will invalidate data in existing subscriptions, specify a value of **1** for **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="579db-172">게시에 대해 스냅샷 에이전트 작업을 다시 실행하여 업데이트된 스냅샷을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-172">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span> <span data-ttu-id="579db-173">자세한 내용은 [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="579db-173">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
3.  <span data-ttu-id="579db-174">구독을 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-174">Reinitialize subscriptions.</span></span> <span data-ttu-id="579db-175">자세한 내용은 [구독 다시 초기화](../reinitialize-subscriptions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="579db-175">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-define-a-static-row-filter-for-a-merge-publication"></a><span data-ttu-id="579db-176">병합 게시에 대한 정적 행 필터를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="579db-176">To define a static row filter for a merge publication</span></span>  
  
1.  <span data-ttu-id="579db-177">게시 데이터베이스의 게시자에서 [sp_addmergearticle&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-177">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="579db-178">이때 **\@subset_filterclause** 에 필터링 절( `WHERE`를 포함하지 않음)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-178">Specify the filtering clause for **\@subset_filterclause** (not including `WHERE`).</span></span> <span data-ttu-id="579db-179">자세한 내용은 [아티클을 정의](define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="579db-179">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="579db-180">계속 열 필터를 정의하려면 [열 필터 정의 및 수정](define-and-modify-a-column-filter.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="579db-180">If a column filter must still be defined, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>  
  
#### <a name="to-modify-a-static-row-filter-for-a-merge-publication"></a><span data-ttu-id="579db-181">병합 게시에 대한 정적 행 필터를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="579db-181">To modify a static row filter for a merge publication</span></span>  
  
1.  <span data-ttu-id="579db-182">게시 데이터베이스의 게시자에서 [sp_changemergearticle&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-182">At the Publisher on the publication database, execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="579db-183">이때 **\@publication**에 게시 이름, **\@article**에 필터링된 아티클 이름, **\@property**에 **subset_filterclause** 값, **\@value**에 새 필터링 절(`WHERE`를 포함하지 않음)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-183">Specify the publication name for **\@publication**, the name of the filtered article for **\@article**, a value of **subset_filterclause** for **\@property**, and the new filtering clause for **\@value** (not including `WHERE`).</span></span> <span data-ttu-id="579db-184">이와 같이 변경하면 기존 구독의 데이터가 무효화되므로 **\@force_reinit_subscription**에 1 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-184">Because this change will invalidate data in existing subscriptions, specify a value of 1 for **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="579db-185">게시에 대해 스냅샷 에이전트 작업을 다시 실행하여 업데이트된 스냅샷을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-185">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span> <span data-ttu-id="579db-186">자세한 내용은 [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="579db-186">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
3.  <span data-ttu-id="579db-187">구독을 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-187">Reinitialize subscriptions.</span></span> <span data-ttu-id="579db-188">자세한 내용은 [구독 다시 초기화](../reinitialize-subscriptions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="579db-188">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="579db-189">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="579db-189">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="579db-190">다음 트랜잭션 복제 예에서는 지원되지 않는 모든 제품을 제거하도록 아티클을 행 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-190">In this transactional replication example, the article is filtered horizontally to remove all discontinued products.</span></span>  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 <span data-ttu-id="579db-191">다음 병합 복제 예에서는 지정된 영업 사원에 속한 행만 반환하도록 아티클을 행 필터링하고</span><span class="sxs-lookup"><span data-stu-id="579db-191">In this merge replication example, the articles are filtered horizontally to return only rows that belong to the specified salesperson.</span></span> <span data-ttu-id="579db-192">조인 필터도 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="579db-192">A join filter is also used.</span></span> <span data-ttu-id="579db-193">자세한 내용은 [병합 아티클 사이에서 조인 필터 정의 및 수정](define-and-modify-a-join-filter-between-merge-articles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="579db-193">For more information, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="see-also"></a><span data-ttu-id="579db-194">참고 항목</span><span class="sxs-lookup"><span data-stu-id="579db-194">See Also</span></span>  
 <span data-ttu-id="579db-195">[병합 아티클에 대한 매개 변수가 있는 행 필터 정의 및 수정](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="579db-195">[Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span></span>  
 <span data-ttu-id="579db-196">[게시 및 아티클 속성 변경](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="579db-196">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="579db-197">[게시된 데이터 필터링](filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="579db-197">[Filter Published Data](filter-published-data.md) </span></span>  
 [<span data-ttu-id="579db-198">병합 복제의 게시된 데이터 필터링</span><span class="sxs-lookup"><span data-stu-id="579db-198">Filter Published Data for Merge Replication</span></span>](../merge/filter-published-data-for-merge-replication.md)  
  
  
