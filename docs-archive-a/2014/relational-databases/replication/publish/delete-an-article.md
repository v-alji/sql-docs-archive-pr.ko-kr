---
title: 아티클 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], dropping
- sp_droparticle
- sp_dropmergearticle
- deleting articles
- removing articles
- dropping articles
ms.assetid: 185b58fc-38c0-4abe-822e-6ec20066c863
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 082f90d33c2b8dedfae34dcada9b3935bed134ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647611"
---
# <a name="delete-an-article"></a><span data-ttu-id="98910-102">아티클 삭제</span><span class="sxs-lookup"><span data-stu-id="98910-102">Delete an Article</span></span>
  <span data-ttu-id="98910-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 에서 아티클을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98910-103">This topic describes how to delete an article in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)] or Replication Management Objects (RMO).</span></span> <span data-ttu-id="98910-104">아티클을 삭제할 수 있는 조건 및 아티클 삭제로 인해 새 스냅샷 또는 구독 다시 초기화가 필요한지 여부에 대한 자세한 내용은 [기존 게시에 대한 아티클 추가 및 삭제](add-articles-to-and-drop-articles-from-existing-publications.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="98910-104">For information about the conditions under which articles can be dropped and whether dropping an article requires a new snapshot or the reinitialization of subscriptions, see [Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="98910-105">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="98910-105">Using Transact-SQL</span></span>  
 <span data-ttu-id="98910-106">아티클은 복제 저장 프로시저를 사용하여 프로그래밍 방식으로 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98910-106">Articles can be deleted programmatically using replication stored procedures.</span></span> <span data-ttu-id="98910-107">사용되는 저장 프로시저는 아티클이 속한 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="98910-107">The stored procedures that you use depend on the type of publication to which the article belongs.</span></span>  
  
#### <a name="to-delete-an-article-from-a-snapshot-or-transactional-publication"></a><span data-ttu-id="98910-108">스냅샷 또는 트랜잭션 게시에서 아티클을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="98910-108">To delete an article from a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="98910-109">[sp_droparticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droparticle-transact-sql)을 실행하여 **\@publication**로 지정된 게시에서 **\@article**으로 지정된 아티클을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="98910-109">Execute [sp_droparticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droparticle-transact-sql) to delete an article, specified by **\@article**, from a publication, specified by **\@publication**.</span></span> <span data-ttu-id="98910-110">\*\* \@ Force_invalidate_snapshot\*\*에 값 **1** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="98910-110">Specify a value of **1** for **\@force_invalidate_snapshot**.</span></span>  
  
2.  <span data-ttu-id="98910-111">(옵션) 게시된 개체를 데이터베이스에서 완전히 제거하려면 게시 데이터베이스의 게시자에서 `DROP <objectname>` 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="98910-111">(Optional) To remove the published object from the database entirely, execute the `DROP <objectname>` command at the Publisher on the publication database.</span></span>  
  
#### <a name="to-delete-an-article-from-a-merge-publication"></a><span data-ttu-id="98910-112">병합 게시에서 아티클을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="98910-112">To delete an article from a merge publication</span></span>  
  
1.  <span data-ttu-id="98910-113">[sp_dropmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql)을 실행하여 **\@publication**로 지정된 게시에서 **\@article**으로 지정된 아티클을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="98910-113">Execute [sp_dropmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql) to delete an article, specified by **\@article**, from a publication, specified by **\@publication**.</span></span> <span data-ttu-id="98910-114">필요한 경우 \*\* \@ force_invalidate_snapshot\*\* 에 값 **1** 을 지정 하 고 \*\* \@ force_reinit_subscription\*\*값으로 **1** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="98910-114">If necessary, specify a value of **1** for **\@force_invalidate_snapshot** and a value of **1** for **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="98910-115">(옵션) 게시된 개체를 데이터베이스에서 완전히 제거하려면 게시 데이터베이스의 게시자에서 `DROP <objectname>` 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="98910-115">(Optional) To remove the published object from the database entirely, execute the `DROP <objectname>` command at the Publisher on the publication database.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="98910-116">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="98910-116">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="98910-117">다음 예에서는 트랜잭션 게시에서 아티클을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="98910-117">The following example deletes an article from a transactional publication.</span></span> <span data-ttu-id="98910-118">이 변경으로 인해 기존 스냅숏이 무효화 되므로 \*\* \@ force_invalidate_snapshot\*\* 매개 변수에 **1** 값이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98910-118">Because this change invalidates the existing snapshot, a value of **1** is specified for the **\@force_invalidate_snapshot** parameter.</span></span>  
  
 [!code-sql[HowTo#sp_droparticle](../../../snippets/tsql/SQL15/replication/howto/tsql/droptranpub.sql#sp_droparticle)]  
  
 <span data-ttu-id="98910-119">다음 예에서는 병합 게시에서 두 개의 아티클을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="98910-119">The following example deletes two articles from a merge publication.</span></span> <span data-ttu-id="98910-120">이러한 변경으로 인해 기존 스냅숏이 무효화 되므로 \*\* \@ force_invalidate_snapshot\*\* 매개 변수에 **1** 값이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98910-120">Because these changes invalidate the existing snapshot, a value of **1** is specified for the **\@force_invalidate_snapshot** parameter.</span></span>  
  
 [!code-sql[HowTo#sp_dropmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepub.sql#sp_dropmergearticle)]
 [!code-sql[HowTo#sp_dropmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergearticles.sql#sp_dropmergearticle)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="98910-121">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="98910-121">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="98910-122">RMO(복제 관리 개체)를 사용하여 프로그래밍 방식으로 아티클을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98910-122">You can delete articles programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="98910-123">아티클을 삭제하는 데 사용하는 RMO 클래스는 아티클이 속한 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="98910-123">The RMO classes you use to delete an article depend on the type of publication to which the article belongs.</span></span>  
  
#### <a name="to-delete-an-article-that-belongs-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="98910-124">스냅샷 또는 트랜잭션 게시에 속한 아티클을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="98910-124">To delete an article that belongs to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="98910-125"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="98910-125">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="98910-126"><xref:Microsoft.SqlServer.Replication.TransArticle> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="98910-126">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransArticle> class.</span></span>  
  
3.  <span data-ttu-id="98910-127"><xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>및 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="98910-127">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="98910-128"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성에 대해 1단계에서 만든 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="98910-128">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="98910-129"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 속성을 확인하여 아티클이 존재하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="98910-129">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the article exists.</span></span> <span data-ttu-id="98910-130">이 속성의 값이 `false`이면 3단계에서 아티클 속성이 올바르게 정의되지 않았거나 아티클이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="98910-130">If the value of this property is `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span>  
  
6.  <span data-ttu-id="98910-131"><xref:Microsoft.SqlServer.Replication.Article.Remove%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="98910-131">Call the <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> method.</span></span>  
  
7.  <span data-ttu-id="98910-132">모든 연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="98910-132">Close all connections.</span></span>  
  
#### <a name="to-delete-an-article-that-belongs-to-a-merge-publication"></a><span data-ttu-id="98910-133">병합 게시에 속한 아티클을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="98910-133">To delete an article that belongs to a merge publication</span></span>  
  
1.  <span data-ttu-id="98910-134"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="98910-134">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="98910-135"><xref:Microsoft.SqlServer.Replication.MergeArticle> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="98910-135">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class.</span></span>  
  
3.  <span data-ttu-id="98910-136"><xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>및 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="98910-136">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="98910-137"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성에 대해 1단계에서 만든 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="98910-137">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="98910-138"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 속성을 확인하여 아티클이 존재하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="98910-138">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the article exists.</span></span> <span data-ttu-id="98910-139">이 속성의 값이 `false`이면 3단계에서 아티클 속성이 올바르게 정의되지 않았거나 아티클이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="98910-139">If the value of this property is `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span>  
  
6.  <span data-ttu-id="98910-140"><xref:Microsoft.SqlServer.Replication.Article.Remove%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="98910-140">Call the <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> method.</span></span>  
  
7.  <span data-ttu-id="98910-141">모든 연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="98910-141">Close all connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98910-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98910-142">See Also</span></span>  
 <span data-ttu-id="98910-143">[기존 게시에 대한 아티클 추가 및 삭제](add-articles-to-and-drop-articles-from-existing-publications.md) </span><span class="sxs-lookup"><span data-stu-id="98910-143">[Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md) </span></span>  
 [<span data-ttu-id="98910-144">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="98910-144">Replication System Stored Procedures Concepts</span></span>](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
