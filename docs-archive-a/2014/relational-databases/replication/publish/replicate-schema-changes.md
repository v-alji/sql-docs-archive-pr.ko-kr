---
title: 스키마 변경 내용 복제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: c09007f0-9374-4f60-956b-8a87670cd043
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bec2f363cd8c4f7dea45935568a88722b19323fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651648"
---
# <a name="replicate-schema-changes"></a><span data-ttu-id="21bac-102">스키마 변경 내용 복제</span><span class="sxs-lookup"><span data-stu-id="21bac-102">Replicate Schema Changes</span></span>
  <span data-ttu-id="21bac-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 스키마 변경 내용을 복제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="21bac-103">This topic describes how to replicate schema changes in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="21bac-104">게시된 아티클에서 다음 스키마를 변경하면 기본적으로 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 구독자에 변경 내용이 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="21bac-104">If you make the following schema changes to a published article, they are propagated, by default, to [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers:</span></span>  
  
-   <span data-ttu-id="21bac-105">ALTER TABLE</span><span class="sxs-lookup"><span data-stu-id="21bac-105">ALTER TABLE</span></span>  
  
-   <span data-ttu-id="21bac-106">ALTER VIEW</span><span class="sxs-lookup"><span data-stu-id="21bac-106">ALTER VIEW</span></span>  
  
-   <span data-ttu-id="21bac-107">ALTER PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="21bac-107">ALTER PROCEDURE</span></span>  
  
-   <span data-ttu-id="21bac-108">ALTER FUNCTION</span><span class="sxs-lookup"><span data-stu-id="21bac-108">ALTER FUNCTION</span></span>  
  
-   <span data-ttu-id="21bac-109">ALTER TRIGGER</span><span class="sxs-lookup"><span data-stu-id="21bac-109">ALTER TRIGGER</span></span>  
  
 <span data-ttu-id="21bac-110">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="21bac-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="21bac-111">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="21bac-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="21bac-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="21bac-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="21bac-113">**다음을 사용하여 스키마 변경을 복제하려면**</span><span class="sxs-lookup"><span data-stu-id="21bac-113">**To replicate schema changes, using:**</span></span>  
  
     [<span data-ttu-id="21bac-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="21bac-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="21bac-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="21bac-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="21bac-116">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="21bac-116">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="21bac-117">제한 사항</span><span class="sxs-lookup"><span data-stu-id="21bac-117">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="21bac-118">ALTER TABLE ... DROP COLUMN 문은 스키마 변경 내용 복제를 해제한 경우에도 항상 삭제된 열이 있는 구독이 포함된 모든 구독자에 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="21bac-118">The ALTER TABLE ... DROP COLUMN statement is always replicated to all Subscribers whose subscription contains the columns being dropped, even if you disable the replication of schema changes.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="21bac-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="21bac-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="21bac-120">게시에 대한 스키마 변경 내용을 복제하지 않으려면 **게시 속성 - \<Publication>** 대화 상자에서 스키마 변경 내용 복제를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="21bac-120">If you do not want to replicate schema changes for a publication, disable the replication of schema changes in the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="21bac-121">이 대화 상자에 액세스하는 방법은 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21bac-121">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-disable-replication-of-schema-changes"></a><span data-ttu-id="21bac-122">스키마 변경 내용 복제를 해제하려면</span><span class="sxs-lookup"><span data-stu-id="21bac-122">To disable replication of schema changes</span></span>  
  
1.  <span data-ttu-id="21bac-123">**게시 속성 - \<Publication>** 대화 상자의 **구독 옵션** 페이지에서 **스키마 변경 내용 복제** 속성의 값을 **False**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="21bac-123">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, set the value of the **Replicate schema changes** property to **False**.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="21bac-124">특정 스키마 변경 내용만 전파하려면 스키마를 변경하기 전에 해당 속성을 **True** 로 설정한 다음 스키마 변경 후 **False** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="21bac-124">To propagate only specific schema changes, set the property to **True** before a schema change, and then set it to **False** after the change is made.</span></span> <span data-ttu-id="21bac-125">반대로 지정된 변경 내용을 제외한 대부분의 스키마 변경 내용을 전파하려면 스키마를 변경하기 전에 해당 속성을 **False** 로 설정한 다음 스키마 변경 후 **True** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="21bac-125">Conversely, to propagate most schema changes, but not a given change, set the property to **False** before the schema change, and then set it to **True** after the change is made.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="21bac-126">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="21bac-126">Using Transact-SQL</span></span>  
 <span data-ttu-id="21bac-127">복제 저장 프로시저를 사용하여 이러한 스키마 변경 내용을 복제할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21bac-127">You can use replication stored procedures to specify whether these schema changes are replicated.</span></span> <span data-ttu-id="21bac-128">사용하는 저장 프로시저는 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="21bac-128">The stored procedure that you use depends on the type of publication.</span></span>  
  
#### <a name="to-create-a-snapshot-or-transactional-publication-that-does-not-replicate-schema-changes"></a><span data-ttu-id="21bac-129">스키마 변경 내용을 복제하지 않는 스냅샷 또는 트랜잭션 게시를 만들려면</span><span class="sxs-lookup"><span data-stu-id="21bac-129">To create a snapshot or transactional publication that does not replicate schema changes</span></span>  
  
1.  <span data-ttu-id="21bac-130">게시 데이터베이스의 게시자에서 \*\* \@ replicate_ddl\*\*에 값 **0** 을 지정 하 여 [transact-sql&#41;&#40;sp_addpublication ](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="21bac-130">At the Publisher on the publication database, execute [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql), specifying a value of **0** for **\@replicate_ddl**.</span></span> <span data-ttu-id="21bac-131">자세한 내용은 [게시 만들기](create-a-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21bac-131">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-create-a-merge-publication-that-does-not-replicate-schema-changes"></a><span data-ttu-id="21bac-132">스키마 변경 내용을 복제하지 않는 병합 게시를 만들려면</span><span class="sxs-lookup"><span data-stu-id="21bac-132">To create a merge publication that does not replicate schema changes</span></span>  
  
1.  <span data-ttu-id="21bac-133">게시 데이터베이스의 게시자에서 \*\* \@ replicate_ddl\*\*에 값 **0** 을 지정 하 여 [transact-sql&#41;&#40;sp_addmergepublication ](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="21bac-133">At the Publisher on the publication database, execute [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), specifying a value of **0** for **\@replicate_ddl**.</span></span> <span data-ttu-id="21bac-134">자세한 내용은 [게시 만들기](create-a-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21bac-134">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="21bac-135">스냅샷 또는 트랜잭션 게시에 대해 스키마 변경 내용 복제를 일시적으로 해제하려면</span><span class="sxs-lookup"><span data-stu-id="21bac-135">To temporarily disable replicating schema changes for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="21bac-136">스키마 변경 내용 복제를 사용 하는 게시의 경우 \*\* \@ 속성\*\* 에 **replicate_ddl** 값을 지정 하 고 \*\* \@ 값\*\*에 **0** 값을 지정 하 여 [sp_changepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="21bac-136">For a publication with replication of schema changes, execute [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying a value of **replicate_ddl** for **\@property** and a value of **0** for **\@value**.</span></span>  
  
2.  <span data-ttu-id="21bac-137">게시된 개체에서 DDL 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="21bac-137">Execute the DDL command on the published object.</span></span>  
  
3.  <span data-ttu-id="21bac-138">필드 \*\* \@ 속성\*\* 에 **replicate_ddl** 값을 지정 하 고 \*\* \@ 값\*\*에 **1** 값을 지정 하 여 [sp_changepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)를 실행 하 여 스키마 변경 내용 복제를 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21bac-138">(Optional) Re-enable replicating schema changes by executing [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying a value of **replicate_ddl** for **\@property** and a value of **1** for **\@value**.</span></span>  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-merge-publication"></a><span data-ttu-id="21bac-139">병합 게시에 대한 스키마 변경 내용 복제를 일시적으로 해제하려면</span><span class="sxs-lookup"><span data-stu-id="21bac-139">To temporarily disable replicating schema changes for a merge publication</span></span>  
  
1.  <span data-ttu-id="21bac-140">스키마 변경 내용 복제를 사용 하는 게시의 경우 \*\* \@ 속성\*\* 에 **replicate_ddl** 값을 지정 하 고 \*\* \@ 값\*\*에 **0** 값을 지정 하 여 [sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="21bac-140">For a publication with replication of schema changes, execute [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying a value of **replicate_ddl** for **\@property** and a value of **0** for **\@value**.</span></span>  
  
2.  <span data-ttu-id="21bac-141">게시된 개체에서 DDL 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="21bac-141">Execute the DDL command on the published object.</span></span>  
  
3.  <span data-ttu-id="21bac-142">필드 \*\* \@ 속성\*\* 에 **replicate_ddl** 값을 지정 하 고 \*\* \@ 값\*\*에 **1** 값을 지정 하 여 [sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)를 실행 하 여 스키마 변경 내용 복제를 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21bac-142">(Optional) Re-enable replicating schema changes by executing [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying a value of **replicate_ddl** for **\@property** and a value of **1** for **\@value**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21bac-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="21bac-143">See Also</span></span>  
 <span data-ttu-id="21bac-144">[게시 데이터베이스의 스키마 변경](make-schema-changes-on-publication-databases.md) </span><span class="sxs-lookup"><span data-stu-id="21bac-144">[Make Schema Changes on Publication Databases](make-schema-changes-on-publication-databases.md) </span></span>  
 [<span data-ttu-id="21bac-145">게시 데이터베이스의 스키마 변경</span><span class="sxs-lookup"><span data-stu-id="21bac-145">Make Schema Changes on Publication Databases</span></span>](make-schema-changes-on-publication-databases.md)  
  
  
