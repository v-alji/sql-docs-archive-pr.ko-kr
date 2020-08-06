---
title: 병합 아티클 사이에서 조인 필터 정의 및 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication], join
- merge replication join filters [SQL Server replication]
- modifying filters, join
- join filters
ms.assetid: f7f23415-43ff-40f5-b3e0-0be1d148ee5b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0770a17ce4c50c9c0e3b8728db85c0f9e80b555b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661021"
---
# <a name="define-and-modify-a-join-filter-between-merge-articles"></a><span data-ttu-id="4241e-102">병합 아티클 사이에서 조인 필터 정의 및 수정</span><span class="sxs-lookup"><span data-stu-id="4241e-102">Define and Modify a Join Filter Between Merge Articles</span></span>
  <span data-ttu-id="4241e-103">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 병합 아티클 간의 조인 필터를 정의하고 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-103">This topic describes how to define and modify a join filter between merge articles in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="4241e-104">병합 복제는 조인 필터를 지원합니다. 조인 필터는 일반적으로 테이블 파티션을 다른 관련 테이블 아티클로 확장하기 위해 매개 변수가 있는 필터와 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-104">Merge replication supports join filters, which are typically used in conjunction with parameterized filters to extend table partitioning to other related table articles.</span></span>  
  
 <span data-ttu-id="4241e-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="4241e-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4241e-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="4241e-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4241e-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4241e-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4241e-108">권장 사항</span><span class="sxs-lookup"><span data-stu-id="4241e-108">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="4241e-109">**다음을 사용하여 병합 아티클 간의 조인 필터를 정의하고 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="4241e-109">**To define and modify a join filter between merge articles, using:**</span></span>  
  
     [<span data-ttu-id="4241e-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4241e-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4241e-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4241e-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4241e-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="4241e-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4241e-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4241e-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="4241e-114">조인 필터를 만들려면 게시에 최소한 두 개 이상의 관련 테이블이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-114">To create a join filter, a publication must contain at least two related tables.</span></span> <span data-ttu-id="4241e-115">조인 필터는 행 필터를 확장하므로 다른 테이블과의 조인으로 필터를 확장하려면 한 테이블의 행 필터를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-115">A join filter extends a row filter; therefore you must define a row filter on one table before you can extend the filter with a join to another table.</span></span> <span data-ttu-id="4241e-116">게시에 추가 관련 테이블이 포함되는 경우 한 조인 필터를 정의한 후에 다른 조인 필터를 사용하여 이 조인 필터를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-116">After one join filter is defined, you can extend this join filter with another join filter if the publication contains additional related tables.</span></span>  
  
-   <span data-ttu-id="4241e-117">게시에 대한 구독이 초기화된 후 조인 필터를 추가, 수정 또는 삭제한 경우에는 변경 내용을 적용한 후에 새 스냅샷을 생성하고 모든 구독을 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-117">If you add, modify, or delete a join filter after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="4241e-118">속성 변경 요구 사항에 대한 자세한 내용은 [게시 및 아티클 속성 변경](change-publication-and-article-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4241e-118">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="4241e-119">권장 사항</span><span class="sxs-lookup"><span data-stu-id="4241e-119">Recommendations</span></span>  
  
-   <span data-ttu-id="4241e-120">테이블 집합에 대한 조인 필터를 수동으로 만들거나 테이블에 정의된 외래 키와 기본 키 간의 관계를 기반으로 복제에서 필터를 자동으로 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-120">Join filters can be created manually for a set of tables, or replication can generate the filters automatically based on the relationships between foreign keys and primary keys defined on the tables.</span></span> <span data-ttu-id="4241e-121">조인 필터 집합을 자동으로 생성하는 방법에 대한 자세한 내용은 [병합 아티클 간의 조인 필터 집합 자동 생성&#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4241e-121">For more information on generating a set of join filters automatically, see [Automatically Generate a Set of Join Filters Between Merge Articles &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4241e-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="4241e-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="4241e-123">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자의 **행 필터** 페이지에서 조인 필터를 정의, 수정 및 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-123">Define, modify, and delete join filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="4241e-124">마법사 사용 및 대화 상자 액세스에 대한 자세한 내용은 [게시 만들기](create-a-publication.md) 및 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4241e-124">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-define-a-join-filter"></a><span data-ttu-id="4241e-125">조인 필터를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="4241e-125">To define a join filter</span></span>  
  
1.  <span data-ttu-id="4241e-126">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 의 **행 필터** 페이지에 있는 **필터링된 테이블** 창에서 기존 행 필터 또는 조인 필터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-126">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select an existing row filter or join filter in the **Filtered Tables** pane.</span></span>  
  
2.  <span data-ttu-id="4241e-127">**추가**를 클릭한 다음 **선택한 필터 확장을 위해 조인 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-127">Click **Add**, and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
3.  <span data-ttu-id="4241e-128">조인 문을 작성합니다. 새 조인을 추가하는 경우 **작성기를 사용하여 문 작성** 또는 **조인 문 직접 작성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-128">Create the join statement: select either **Use the builder to create the statement** or **Write the join the statement manually**.</span></span>  
  
    -   <span data-ttu-id="4241e-129">작성기 사용을 선택하면 표의 열(**결합**, **필터링된 테이블 열**, **연산자**및 **조인된 테이블 열**)을 사용하여 조인 문을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-129">If you select to use the builder, use the columns in the grid (**Conjunction**, **Filtered table column**, **Operator**, and **Joined table column**) to build a join statement.</span></span>  
  
         <span data-ttu-id="4241e-130">표의 각 열에는 드롭다운 콤보 상자가 들어 있습니다. 여기서 두 개의 열과 연산자 1개( **=** , **<>** , **<=** , **\<**, **>=** , **>** 및 **like**)를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-130">Each column in the grid contains a drop-down combo box, allowing you to select two columns and an operator (**=**, **<>**, **<=**, **\<**, **>=**, **>**, and **like**).</span></span> <span data-ttu-id="4241e-131">결과는 **미리 보기** 텍스트 영역에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-131">The results are displayed in the **Preview** text area.</span></span> <span data-ttu-id="4241e-132">조인이 둘 이상의 열 쌍을 포함하면 **결합** 열에서 결합(AND 또는 OR)을 선택한 다음 두 개 이상의 열과 연산자를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-132">If the join involves more than one pair of columns, select a conjunction (AND or OR) from the **Conjunction** column, and then enter two more columns and an operator.</span></span>  
  
    -   <span data-ttu-id="4241e-133">수동으로 문 작성을 선택하면 **조인 문** 텍스트 영역에 조인 문을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-133">If you select to write the statement manually, write the join statement in the **Join statement** text area.</span></span> <span data-ttu-id="4241e-134">**필터링된 테이블 열** 목록 상자 및 **조인된 테이블 열** 목록 상자를 사용하여 열을 **조인 문** 텍스트 영역에 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-134">Use the **Filtered table columns** list box and the **Joined table columns** list box to drag and drop columns to the **Join statement** text area.</span></span>  
  
    -   <span data-ttu-id="4241e-135">완전한 조인 문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-135">The complete join statement would appear like:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] INNER JOIN [Sales].[SalesOrderDetail] ON [SalesOrderHeader].[SalesOrderID] = [SalesOrderDetail].[SalesOrderID]  
        ```  
  
         <span data-ttu-id="4241e-136">JOIN 절은 두 부분으로 구성된 이름을 사용해야 하며 세 부분 또는 네 부분으로 구성된 이름은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-136">The JOIN clause should use two-part naming; three-part naming and four-part naming are not supported.</span></span>  
  
4.  <span data-ttu-id="4241e-137">조인 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-137">Specify join options:</span></span>  
  
    -   <span data-ttu-id="4241e-138">필터링된 테이블(부모 테이블)에서 조인하는 열이 고유하면 **고유 키**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-138">If the column on which you join in the filtered table (the parent table) is unique, select **Unique key**.</span></span>  
  
        > [!CAUTION]  
        >  <span data-ttu-id="4241e-139">이 옵션을 선택하면 조인 필터에서의 자식 테이블과 부모 테이블 간의 관계가 일대일 또는 일대다가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-139">Selecting this option indicates that the relationship between the child and parent tables in a join filter is one to one or one to many.</span></span> <span data-ttu-id="4241e-140">자식 테이블에 있는 조인 열이 고유해야 하는 경우에만 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-140">Only select this option if you have a constraint on the joining column in the child table that guarantees uniqueness.</span></span> <span data-ttu-id="4241e-141">이 옵션이 잘못 설정되면 데이터가 일치하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-141">If the option is set incorrectly, non-convergence of data can occur.</span></span>  
  
    -   <span data-ttu-id="4241e-142">기본적으로 병합 복제는 동기화 과정에서 행별로 변경 내용을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-142">By default, merge replication processes changes on a row-by-row basis during synchronization.</span></span> <span data-ttu-id="4241e-143">필터링된 테이블과 조인된 테이블 행의 관련 변경 내용을 하나의 단위로 처리하려면 **논리적 레코드**를 선택합니다([!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 이상 버전에만 해당).</span><span class="sxs-lookup"><span data-stu-id="4241e-143">To have related changes in rows of both the filtered table and the joined table processed as a unit, select **Logical record** ([!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] and later versions only).</span></span> <span data-ttu-id="4241e-144">논리적 레코드를 사용하기 위한 아티클 및 게시 요구 사항이 충족되는 경우에만 이 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-144">This option is available only if the article and publication requirements for using logical records are met.</span></span> <span data-ttu-id="4241e-145">자세한 내용은 [논리적 레코드를 사용하여 관련된 행의 변경 내용 그룹화](../merge/group-changes-to-related-rows-with-logical-records.md)에서 "논리적 레코드 사용 시 고려 사항" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4241e-145">For more information see the section "Considerations for Using Logical Records" in [Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="4241e-146">**게시 속성 - \<Publication>** 대화 상자에서 **확인**을 클릭하여 저장하고 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-146">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-modify-a-join-filter"></a><span data-ttu-id="4241e-147">조인 필터를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="4241e-147">To modify a join filter</span></span>  
  
1.  <span data-ttu-id="4241e-148">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자의 **행 필터** 페이지에 있는 **필터링된 테이블** 창에서 필터를 선택하고 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-148">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="4241e-149">**조인 편집** 대화 상자에서 필터를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-149">In the **Edit Join** dialog box, modify the filter.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-join-filter"></a><span data-ttu-id="4241e-150">조인 필터를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="4241e-150">To delete a join filter</span></span>  
  
1.  <span data-ttu-id="4241e-151">새 게시 마법사의 **테이블 행 필터** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자의 **행 필터** 페이지에 있는 **필터링된 테이블** 창에서 필터를 선택하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-151">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span> <span data-ttu-id="4241e-152">삭제하는 조인 필터가 다른 조인에 의해 확장된 경우 해당 조인 또한 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-152">If the join filter you delete is itself extended by other joins, those joins will also be deleted.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4241e-153">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="4241e-153">Using Transact-SQL</span></span>  
 <span data-ttu-id="4241e-154">다음 절차에서는 부모 아티클의 매개 변수가 있는 필터 및 이 아티클과 관련 자식 아티클 간의 조인 필터를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-154">These procedures show a parameterized filter on a parent article with join filters between this article and related child articles.</span></span> <span data-ttu-id="4241e-155">조인 필터는 복제 저장 프로시저를 사용하여 프로그래밍 방식으로 정의 및 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-155">Join filters can be defined and modified programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-define-a-join-filter-to-extend-an-article-filter-to-related-articles-in-a-merge-publication"></a><span data-ttu-id="4241e-156">아티클 필터를 병합 복제의 관련 아티클로 확장하도록 조인 필터를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="4241e-156">To define a join filter to extend an article filter to related articles in a merge publication</span></span>  
  
1.  <span data-ttu-id="4241e-157">조인되는 아티클, 즉 부모 아티클에 대한 필터링을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-157">Define the filtering for the article being joined to, which is also known as the parent article.</span></span>  
  
    -   <span data-ttu-id="4241e-158">매개 변수가 있는 행 필터를 사용하여 필터링되는 아티클의 경우 [병합 아티클에 대한 매개 변수가 있는 행 필터 정의 및 수정](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4241e-158">For an article filtered using a parameterized row filter, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span></span>  
  
    -   <span data-ttu-id="4241e-159">정적 행 필터를 사용하여 필터링되는 아티클의 경우 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4241e-159">For an article filtered using a static row filter, see [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span>  
  
2.  <span data-ttu-id="4241e-160">게시 데이터베이스의 게시자에서 [sp_addmergearticle&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)을 실행하여 게시에 대한 하나 이상의 관련 아티클, 즉 자식 아티클을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-160">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) to define one or more related articles, which are also known as child articles, for the publication.</span></span> <span data-ttu-id="4241e-161">자세한 내용은 [아티클을 정의](define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4241e-161">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
3.  <span data-ttu-id="4241e-162">게시 데이터베이스의 게시자에서 [sp_addmergefilter&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-162">At the Publisher on the publication database, execute [sp_addmergefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql).</span></span> <span data-ttu-id="4241e-163">을 지정 하 고,에 대해 **@publication** 이 필터의 고유 이름을, **@filtername** 에 2 단계에서 만든 자식 아티클의 이름,에 **@article** 조인 되는 부모 아티클의 이름을, **@join_articlename** 에 다음 값 중 하나 **@join_unique_key** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-163">Specify **@publication**, a unique name for this filter for **@filtername**, the name of the child article created in step 2 for **@article**, the name of the parent article being joined to for **@join_articlename**, and one of the following values for **@join_unique_key**:</span></span>  
  
    -   <span data-ttu-id="4241e-164">**0** - 부모 아티클과 자식 아티클 간의 다 대 일 또는 다 대 다 조인을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-164">**0** - indicates a many-to-one or many-to-many join between the parent and child articles.</span></span>  
  
    -   <span data-ttu-id="4241e-165">**1** - 부모 아티클과 자식 아티클 간의 일 대 일 또는 일 대 다 조인을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-165">**1** - indicates a one-to-one or one-to-many join between the parent and child articles.</span></span>  
  
     <span data-ttu-id="4241e-166">이는 두 아티클 간의 조인 필터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-166">This defines a join filter between the two articles.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="4241e-167">**@join_unique_key**부모 아티클의 기본 테이블에 있는 조인 열에 고유성을 보장 하는 제약 조건이 있는 경우에만 **1** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-167">Only set **@join_unique_key** to **1** if you have a constraint on the joining column in the underlying table for the parent article that guarantees uniqueness.</span></span> <span data-ttu-id="4241e-168">**@join_unique_key**가 **1** 로 잘못 설정 된 경우 데이터가 일치 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-168">If **@join_unique_key** is set to **1** incorrectly, non-convergence of data may occur.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="4241e-169">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4241e-169">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="4241e-170">다음 예에서는 정적 행 필터를 사용하여 자체 필터링되는 `SalesOrderDetail` 테이블에 대해 `SalesOrderHeader` 테이블 아티클을 필터링하는 병합 게시에 대한 아티클을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-170">This example defines an article for a merge publication, where the `SalesOrderDetail` table article is filtered against the `SalesOrderHeader` table that is itself filtered using a static row filter.</span></span> <span data-ttu-id="4241e-171">자세한 내용은 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4241e-171">For more information, see [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
 <span data-ttu-id="4241e-172">다음 예에서는 병합 게시의 아티클 그룹을 정의합니다. 이 병합 게시에서는 `Employee` LoginID [열의](/sql/t-sql/functions/host-name-transact-sql) HOST_NAME **값을 대상으로 매개 변수가 있는 행 필터를 사용하여 자체 필터링되는** 테이블에 대해 일련의 조인 필터로 아티클이 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="4241e-172">This example defines a group of articles in a merge publication where the articles are filtered with a series of join filters against the `Employee` table that is itself filtered using a parameterized row filter on the value of [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) in the **LoginID** column.</span></span> <span data-ttu-id="4241e-173">자세한 내용은 [병합 아티클에 대한 매개 변수가 있는 행 필터 정의 및 수정](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4241e-173">For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span></span>  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubdynamic1.sql#sp_mergedynamicpub1)]  
  
## <a name="see-also"></a><span data-ttu-id="4241e-174">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4241e-174">See Also</span></span>  
 <span data-ttu-id="4241e-175">[Join Filters](../merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="4241e-175">[Join Filters](../merge/join-filters.md) </span></span>  
 <span data-ttu-id="4241e-176">[매개 변수가 있는 행 필터](../merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="4241e-176">[Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 <span data-ttu-id="4241e-177">[게시 및 아티클 속성 변경](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="4241e-177">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="4241e-178">[병합 복제의 게시된 데이터 필터링](../merge/filter-published-data-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="4241e-178">[Filter Published Data for Merge Replication](../merge/filter-published-data-for-merge-replication.md) </span></span>  
 <span data-ttu-id="4241e-179">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="4241e-179">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 <span data-ttu-id="4241e-180">[Define a Logical Record Relationship Between Merge Table Articles](define-a-logical-record-relationship-between-merge-table-articles.md) </span><span class="sxs-lookup"><span data-stu-id="4241e-180">[Define a Logical Record Relationship Between Merge Table Articles](define-a-logical-record-relationship-between-merge-table-articles.md) </span></span>  
 [<span data-ttu-id="4241e-181">병합 아티클에 대한 매개 변수가 있는 행 필터 정의 및 수정</span><span class="sxs-lookup"><span data-stu-id="4241e-181">Define and Modify a Parameterized Row Filter for a Merge Article</span></span>](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
  
