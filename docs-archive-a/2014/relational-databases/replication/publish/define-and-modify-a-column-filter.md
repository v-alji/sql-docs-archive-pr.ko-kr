---
title: 열 필터 정의 및 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication], column
- modifying filters, column
- modifying filters
- column filters [SQL Server replication]
ms.assetid: d7c3186a-9a8c-45d8-ab34-05beec4c26dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a655976f925f83d8c9446cab99016f32ab14887
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661022"
---
# <a name="define-and-modify-a-column-filter"></a><span data-ttu-id="c831f-102">열 필터 정의 및 수정</span><span class="sxs-lookup"><span data-stu-id="c831f-102">Define and Modify a Column Filter</span></span>
  <span data-ttu-id="c831f-103">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 열 필터를 정의하고 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-103">This topic describes how to define and modify a column filter in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="c831f-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="c831f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c831f-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="c831f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c831f-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="c831f-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="c831f-107">**다음을 사용하여 열 필터를 정의하고 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="c831f-107">**To define and modify a column filter, using:**</span></span>  
  
     [<span data-ttu-id="c831f-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c831f-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c831f-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c831f-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c831f-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c831f-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c831f-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="c831f-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c831f-112">일부 열은 필터링할 수 없습니다. 자세한 내용은 [게시된 데이터 필터링](filter-published-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c831f-112">Some columns cannot be filtered; for more information, see [Filter Published Data](filter-published-data.md).</span></span> <span data-ttu-id="c831f-113">구독을 초기화한 후 열 필터를 수정할 경우 새 스냅샷을 만들고 변경 내용을 적용한 후 모든 구독을 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-113">If you modify a column filter after subscriptions have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="c831f-114">속성 변경 요구 사항에 대한 자세한 내용은 [게시 및 아티클 속성 변경](change-publication-and-article-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c831f-114">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c831f-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="c831f-115">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="c831f-116">새 게시 마법사의 **아티클** 페이지에서 열 필터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-116">Define column filters on the **Articles** page of the New Publication Wizard.</span></span> <span data-ttu-id="c831f-117">새 게시 마법사 사용 방법에 대한 자세한 내용은 [게시 만들기](create-a-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c831f-117">For more information about using the New Publication Wizard, see [Create a Publication](create-a-publication.md).</span></span>  
  
 <span data-ttu-id="c831f-118">**게시 속성 - \<Publication>** 대화 상자의 **아티클** 페이지에서 열 필터를 정의하고 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-118">Define and modify column filters on the **Articles** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="c831f-119">게시 및 아티클 속성에 대한 자세한 내용은 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c831f-119">For more information about publication and article properties, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-define-a-column-filter"></a><span data-ttu-id="c831f-120">열 필터를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="c831f-120">To define a column filter</span></span>  
  
1.  <span data-ttu-id="c831f-121">새 게시 마법사의 **아티클** 페이지에 있는 **게시할 개체** 창에서 필터링할 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-121">On the **Articles** page of the New Publication Wizard, expand the table to be filtered in the **Objects to publish** pane.</span></span>  
  
2.  <span data-ttu-id="c831f-122">필터링할 각 열 옆에 있는 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-122">Clear the check box next to each column you want to filter.</span></span>  
  
#### <a name="to-modify-column-filtering"></a><span data-ttu-id="c831f-123">열 필터링을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="c831f-123">To modify column filtering</span></span>  
  
1.  <span data-ttu-id="c831f-124">**게시 속성 - \<Publication>** 대화 상자의 **아티클** 페이지에 있는 **게시할 개체** 창에서 필터링할 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-124">On the **Articles** page of the **Publication Properties - \<Publication>** dialog box, expand the table to be filtered in the **Objects to publish** pane.</span></span>  
  
2.  <span data-ttu-id="c831f-125">필터링할 각 열 옆에 있는 확인란의 선택은 취소하고 아티클에 포함시킬 각 열에 대한 확인란은 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-125">Clear the check box next to each column you want to filter, and ensure that the check box is selected for each column that should be included in the article.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c831f-126">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="c831f-126">Using Transact-SQL</span></span>  
 <span data-ttu-id="c831f-127">테이블 아티클을 만들 때 아티클에 포함할 열을 정의할 수 있으며 아티클이 정의된 후 이 열을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-127">When creating table articles, you can define which columns to include in the article and change the columns after the article has been defined.</span></span> <span data-ttu-id="c831f-128">복제 저장 프로시저를 사용하여 프로그래밍 방식으로 필터링된 열을 만들고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-128">You can create and modify filtered columns programmatically using replication stored procedures.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c831f-129">다음 절차에서는 기본 테이블이 변경되지 않은 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-129">The following procedures assume that the underlying table has not changed.</span></span> <span data-ttu-id="c831f-130">DDL(데이터 정의 언어) 변경 내용을 게시된 테이블에 복제하는 방법에 대한 자세한 내용은 [게시 데이터베이스의 스키마 변경](make-schema-changes-on-publication-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c831f-130">For information on replicating data definition language (DDL) changes to published tables, see [Make Schema Changes on Publication Databases](make-schema-changes-on-publication-databases.md).</span></span>  
  
#### <a name="to-define-a-column-filter-for-an-article-published-in-a-snapshot-or-transactional-publication"></a><span data-ttu-id="c831f-131">스냅샷 또는 트랜잭션 게시에 게시된 아티클에 대한 열 필터를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="c831f-131">To define a column filter for an article published in a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="c831f-132">필터링할 아티클을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-132">Define the article to filter.</span></span> <span data-ttu-id="c831f-133">자세한 내용은 [아티클을 정의](define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c831f-133">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="c831f-134">게시 데이터베이스의 게시자에서 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-134">At the Publisher on the publication database, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql).</span></span> <span data-ttu-id="c831f-135">이렇게 하면 아티클에 포함할 열 또는 아티클에서 제거할 열이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-135">This defines the columns to include or remove from the article.</span></span>  
  
    -   <span data-ttu-id="c831f-136">많은 열을 포함한 테이블에서 몇 개의 열만 게시하는 경우 추가할 각 열에 대해 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) 을 한 번씩 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-136">If publishing only a few columns from a table with many columns, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) once for each column being added.</span></span> <span data-ttu-id="c831f-137">**\@column**에 대한 열 이름 및 **\@operation**에 대한 **add** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-137">Specify the column name for **\@column** and a value of **add** for **\@operation**.</span></span>  
  
    -   <span data-ttu-id="c831f-138">많은 열을 포함한 테이블에서 대부분의 열을 게시하는 경우 **\@column**에 **null** 값, **\@operation**에 **add** 값을 지정하고 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql)을 실행하여 모든 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-138">If publishing most of the columns in a table with many columns, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql), specifying a value of **null** for **\@column** and a value of **add** for **\@operation** to add all columns.</span></span> <span data-ttu-id="c831f-139">그런 다음 **\@operation**에 **drop** 값, **\@column**에 제외되는 열 이름을 지정하고 제외할 각 열에 대해 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql)을 한 번씩 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-139">Then execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql), once for each column being excluded, specifying a value of **drop** for **\@operation** and the excluded column name for **\@column**.</span></span>  
  
3.  <span data-ttu-id="c831f-140">게시 데이터베이스의 게시자에서 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-140">At the Publisher on the publication database, execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="c831f-141">**\@publication**에 대한 게시 이름 및 **\@article**에 대한 필터링된 아티클의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-141">Specify the publication name for **\@publication** and the name of the filtered article for **\@article**.</span></span> <span data-ttu-id="c831f-142">이렇게 하면 필터링된 아티클에 대한 동기화 개체가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-142">This creates the synchronization objects for the filtered article.</span></span>  
  
#### <a name="to-change-a-column-filter-to-include-additional-columns-for-an-article-published-in-a-snapshot-or-transactional-publication"></a><span data-ttu-id="c831f-143">스냅샷 또는 트랜잭션 게시에 게시된 아티클에 대한 추가 열을 포함하도록 열 필터를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="c831f-143">To change a column filter to include additional columns for an article published in a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="c831f-144">게시 데이터베이스의 게시자에서 추가할 각 열에 대해 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) 을 한 번씩 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-144">At the Publisher on the publication database, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) once for each column being added.</span></span> <span data-ttu-id="c831f-145">**\@column**에 대한 열 이름 및 **\@operation**에 대한 **add** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-145">Specify the column name for **\@column** and a value of **add** for **\@operation**.</span></span>  
  
2.  <span data-ttu-id="c831f-146">게시 데이터베이스의 게시자에서 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-146">At the Publisher on the publication database, execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="c831f-147">**\@publication**에 대한 게시 이름 및 **\@article**에 대한 필터링된 아티클의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-147">Specify the publication name for **\@publication** and the name of the filtered article for **\@article**.</span></span> <span data-ttu-id="c831f-148">게시에 기존 구독이 있는 경우 **\@change_active**에 **1** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-148">If the publication has existing subscriptions, specify a value of **1** for **\@change_active**.</span></span> <span data-ttu-id="c831f-149">이렇게 하면 필터링된 아티클에 대한 동기화 개체가 다시 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-149">This re-creates the synchronization objects for the filtered article.</span></span>  
  
3.  <span data-ttu-id="c831f-150">게시에 대해 스냅샷 에이전트 작업을 다시 실행하여 업데이트된 스냅샷을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-150">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span>  
  
4.  <span data-ttu-id="c831f-151">구독을 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-151">Reinitialize subscriptions.</span></span> <span data-ttu-id="c831f-152">자세한 내용은 [구독 다시 초기화](../reinitialize-subscriptions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c831f-152">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-change-a-column-filter-to-remove-columns-for-an-article-published-in-a-snapshot-or-transactional-publication"></a><span data-ttu-id="c831f-153">스냅샷 또는 트랜잭션 게시에 게시된 아티클에 대한 열을 제거하도록 열 필터를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="c831f-153">To change a column filter to remove columns for an article published in a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="c831f-154">게시 데이터베이스의 게시자에서 제거할 각 열에 대해 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) 을 한 번씩 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-154">At the Publisher on the publication database, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) once for each column being removed.</span></span> <span data-ttu-id="c831f-155">**\@column**에 열 이름, **\@operation**에 **drop** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-155">Specify the column name for **\@column** and a value of **drop** for **\@operation**.</span></span>  
  
2.  <span data-ttu-id="c831f-156">게시 데이터베이스의 게시자에서 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-156">At the Publisher on the publication database, execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="c831f-157">**\@publication**에 대한 게시 이름 및 **\@article**에 대한 필터링된 아티클의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-157">Specify the publication name for **\@publication** and the name of the filtered article for **\@article**.</span></span> <span data-ttu-id="c831f-158">게시에 기존 구독이 있는 경우 **\@change_active**에 **1** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-158">If the publication has existing subscriptions, specify a value of **1** for **\@change_active**.</span></span> <span data-ttu-id="c831f-159">이렇게 하면 필터링된 아티클에 대한 동기화 개체가 다시 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-159">This re-creates the synchronization objects for the filtered article.</span></span>  
  
3.  <span data-ttu-id="c831f-160">게시에 대해 스냅샷 에이전트 작업을 다시 실행하여 업데이트된 스냅샷을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-160">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span>  
  
4.  <span data-ttu-id="c831f-161">구독을 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-161">Reinitialize subscriptions.</span></span> <span data-ttu-id="c831f-162">자세한 내용은 [구독 다시 초기화](../reinitialize-subscriptions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c831f-162">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-define-a-column-filter-for-an-article-published-in-a-merge-publication"></a><span data-ttu-id="c831f-163">병합 게시에 게시된 아티클에 대한 열 필터를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="c831f-163">To define a column filter for an article published in a merge publication</span></span>  
  
1.  <span data-ttu-id="c831f-164">필터링할 아티클을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-164">Define the article to filter.</span></span> <span data-ttu-id="c831f-165">자세한 내용은 [아티클을 정의](define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c831f-165">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="c831f-166">게시 데이터베이스의 게시자에서 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-166">At the Publisher on the publication database, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql).</span></span> <span data-ttu-id="c831f-167">이렇게 하면 아티클에 포함할 열 또는 아티클에서 제거할 열이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-167">This defines the columns to include or remove from the article.</span></span>  
  
    -   <span data-ttu-id="c831f-168">많은 열을 포함한 테이블에서 몇 개의 열만 게시하는 경우 추가할 각 열에서 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) 을 한 번씩 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-168">If publishing only a few columns from a table with many columns, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) once for each column being added.</span></span> <span data-ttu-id="c831f-169">**\@column**에 대한 열 이름 및 **\@operation**에 대한 **add** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-169">Specify the column name for **\@column** and a value of **add** for **\@operation**.</span></span>  
  
    -   <span data-ttu-id="c831f-170">많은 열을 포함한 테이블에서 대부분의 열을 게시하는 경우 **\@column**에 **null** 값을, **\@operation**에 **add** 값을 지정하고 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql)을 실행하여 모든 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-170">If publishing most of the columns in a table with many columns, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql), specifying a value of **null** for **\@column** and a value of **add** for **\@operation** to add all columns.</span></span> <span data-ttu-id="c831f-171">그런 다음, **\@operation**에 **drop** 값, **\@column**에 제외할 열 이름을 지정하고 제외할 각 열에 대해 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql)을 한 번씩 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-171">Then execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql), once for each column being excluded, specifying a value of **drop** for **\@operation** and the excluded column name for **\@column**.</span></span>  
  
#### <a name="to-change-a-column-filter-to-include-additional-columns-for-an-article-published-in-a-merge-publication"></a><span data-ttu-id="c831f-172">병합 게시에 게시된 아티클에 대한 추가 열을 포함하도록 열 필터를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="c831f-172">To change a column filter to include additional columns for an article published in a merge publication</span></span>  
  
1.  <span data-ttu-id="c831f-173">게시 데이터베이스의 게시자에서 추가할 각 열에 대해 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) 을 한 번씩 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-173">At the Publisher on the publication database, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) once for each column being added.</span></span> <span data-ttu-id="c831f-174">**\@column**에 열 이름, **\@operation**에 **add** 값을 지정하고 **\@force_invalidate_snapshot** 및 **\@force_reinit_subscription**에 모두 **1** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-174">Specify the column name for **\@column**, a value of **add** for **\@operation** and a value of **1** for both **\@force_invalidate_snapshot** and **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="c831f-175">게시에 대해 스냅샷 에이전트 작업을 다시 실행하여 업데이트된 스냅샷을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-175">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span>  
  
3.  <span data-ttu-id="c831f-176">구독을 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-176">Reinitialize subscriptions.</span></span> <span data-ttu-id="c831f-177">자세한 내용은 [구독 다시 초기화](../reinitialize-subscriptions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c831f-177">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-change-a-column-filter-to-remove-columns-for-an-article-published-in-a-merge-publication"></a><span data-ttu-id="c831f-178">병합 게시에 게시된 아티클에 대한 열을 제거하도록 열 필터를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="c831f-178">To change a column filter to remove columns for an article published in a merge publication</span></span>  
  
1.  <span data-ttu-id="c831f-179">게시 데이터베이스의 게시자에서 제거할 각 열에 대해 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) 을 한 번씩 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-179">At the Publisher on the publication database, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) once for each column being removed.</span></span> <span data-ttu-id="c831f-180">**\@column**에 열 이름, **\@operation**에 **drop** 값을 지정하고 **\@force_invalidate_snapshot** 및 **\@force_reinit_subscription** 에 모두 **1** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-180">Specify the column name for **\@column**, a value of **drop** for **\@operation** and a value of **1** for both **\@force_invalidate_snapshot** and **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="c831f-181">게시에 대해 스냅샷 에이전트 작업을 다시 실행하여 업데이트된 스냅샷을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-181">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span>  
  
3.  <span data-ttu-id="c831f-182">구독을 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-182">Reinitialize subscriptions.</span></span> <span data-ttu-id="c831f-183">자세한 내용은 [구독 다시 초기화](../reinitialize-subscriptions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c831f-183">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="c831f-184">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c831f-184">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="c831f-185">이 트랜잭션 복제 예제에서는 `DaysToManufacture` 테이블에 기반한 아티클에서 `Product` 열이 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-185">In this transactional replication example, the `DaysToManufacture` column is removed from an article based on the `Product` table.</span></span>  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 <span data-ttu-id="c831f-186">이 병합 복제 예제에서는 `CreditCardApprovalCode` 테이블에 기반한 아티클에서 `SalesOrderHeader` 열이 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c831f-186">In this merge replication example, the `CreditCardApprovalCode` column is removed from an article based on the `SalesOrderHeader` table.</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="see-also"></a><span data-ttu-id="c831f-187">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c831f-187">See Also</span></span>  
 <span data-ttu-id="c831f-188">[게시 및 아티클 속성 변경](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="c831f-188">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="c831f-189">[게시된 데이터 필터링](filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="c831f-189">[Filter Published Data](filter-published-data.md) </span></span>  
 [<span data-ttu-id="c831f-190">병합 복제의 게시된 데이터 필터링</span><span class="sxs-lookup"><span data-stu-id="c831f-190">Filter Published Data for Merge Replication</span></span>](../merge/filter-published-data-for-merge-replication.md)  
  
  
