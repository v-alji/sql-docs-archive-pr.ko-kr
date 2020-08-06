---
title: 병합 게시에 대한 호환성 수준 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], replication
- backward compatibility [SQL Server], replication
- publications [SQL Server replication], backward compatibility
ms.assetid: db47ac73-948b-4d77-b272-bb3565135ea5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 04ad80b0c99e7282ff2acfa459a08665efbdee1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661017"
---
# <a name="set-the-compatibility-level-for-merge-publications"></a><span data-ttu-id="1117a-102">병합 게시에 대한 호환성 수준 설정</span><span class="sxs-lookup"><span data-stu-id="1117a-102">Set the Compatibility Level for Merge Publications</span></span>
  <span data-ttu-id="1117a-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 병합 게시의 호환성 수준을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-103">This topic describes how to set the compatibility level for merge publications in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="1117a-104">병합 복제는 게시 호환성 수준을 사용하여 지정된 데이터베이스에서 게시에 사용할 수 있는 기능을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-104">Merge replication uses the publication compatibility level to determine which features can be used by publications in a given database.</span></span>  
  
 <span data-ttu-id="1117a-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="1117a-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1117a-106">**다음을 사용하여 병합 게시에 대한 호환성 수준을 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="1117a-106">**To set the compatibility level for merge publications, using:**</span></span>  
  
     [<span data-ttu-id="1117a-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1117a-107">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1117a-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1117a-108">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1117a-109">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="1117a-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="1117a-110">새 게시 마법사의 **구독자 유형** 페이지에서 호환성 수준을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-110">Set the compatibility level on the **Subscriber Types** page of the New Publication Wizard.</span></span> <span data-ttu-id="1117a-111">이 마법사에 액세스하는 방법은 [Create a Publication](create-a-publication.md)에서 병합 게시의 호환성 수준을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-111">For more information on accessing this wizard, see [Create a Publication](create-a-publication.md).</span></span> <span data-ttu-id="1117a-112">게시 스냅샷이 생성된 후 호환성 수준을 증가시킬 수는 있지만 감소시킬 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-112">After a publication snapshot is created, the compatibility level can be increased but cannot be decreased.</span></span> <span data-ttu-id="1117a-113">**게시 속성 - \<Publication>** 대화 상자의 **일반** 페이지에서 호환성 수준을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-113">Increase the compatibility level on the **General** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="1117a-114">이 대화 상자에 액세스하는 방법은 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1117a-114">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span> <span data-ttu-id="1117a-115">게시 호환성 수준을 증가시키면 이전 버전의 호환성 수준을 실행하는 서버에 있는 기존 구독은 더 이상 동기화할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-115">If you increase the publication compatibility level, any existing subscriptions at servers running versions prior to the compatibility level will no longer be able to synchronize.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1117a-116">호환성 수준은 다른 게시 속성 및 유효한 아티클 속성을 결정하는 데에도 의미를 가지므로 대화 상자를 동일하게 사용할 때는 호환성 수준 및 다른 속성을 변경하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="1117a-116">Because the compatibility level has implications for other publication properties and for which article properties are valid, do not change the compatibility level and other properties in the same use of the dialog box.</span></span> <span data-ttu-id="1117a-117">속성을 변경하면 게시를 위한 스냅샷을 다시 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-117">The snapshot for the publication should be regenerated after the property is changed.</span></span>  
  
#### <a name="to-set-the-publication-compatibility-level"></a><span data-ttu-id="1117a-118">게시 호환성 수준을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="1117a-118">To set the publication compatibility level</span></span>  
  
-   <span data-ttu-id="1117a-119">새 게시 마법사의 **구독자 유형** 페이지에서 게시가 지원해야 하는 구독자의 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-119">On the **Subscriber Types** page of the New Publication Wizard, select the types of Subscribers that the publication should support.</span></span>  
  
#### <a name="to-increase-the-publication-compatibility-level"></a><span data-ttu-id="1117a-120">게시 호환성 수준을 증가시키려면</span><span class="sxs-lookup"><span data-stu-id="1117a-120">To increase the publication compatibility level</span></span>  
  
-   <span data-ttu-id="1117a-121">**게시 속성 - \<Publication>** 대화 상자의 **일반** 페이지에서 **호환성 수준**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-121">On the **General** page of the **Publication Properties - \<Publication>** dialog box, select for **Compatibility level**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1117a-122">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="1117a-122">Using Transact-SQL</span></span>  
 <span data-ttu-id="1117a-123">병합 게시의 호환성 수준은 게시를 만들 때 설정하거나 이후에 프로그래밍 방식으로 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-123">The compatibility level for a merge publication can either be set programmatically when a publication is created or modified programmatically at a later time.</span></span> <span data-ttu-id="1117a-124">병합 저장 프로시저를 사용하여 이 게시 속성을 설정 또는 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-124">You can use replication stored procedures to set or change this publication property.</span></span>  
  
#### <a name="to-set-the-publication-compatibility-level-for-a-merge-publication"></a><span data-ttu-id="1117a-125">병합 게시에 대한 게시 호환성 수준을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="1117a-125">To set the publication compatibility level for a merge publication</span></span>  
  
1.  <span data-ttu-id="1117a-126">게시자에서 [sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)를 실행 하 고의 값을 지정 하 여 **@publication_compatibility_level** 이전 버전의와 호환 되는 게시를 만듭니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1117a-126">At the Publisher, execute [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), specifying a value for **@publication_compatibility_level** to make the publication compatible with older versions of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1117a-127">자세한 내용은 [게시 만들기](create-a-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1117a-127">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-change-the-publication-compatibility-level-of-a-merge-publication"></a><span data-ttu-id="1117a-128">병합 게시의 게시 호환성 수준을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="1117a-128">To change the publication compatibility level of a merge publication</span></span>  
  
1.  <span data-ttu-id="1117a-129">**Publication_compatibility_level** 를 지정 하 고에 대 한 적절 한 게시 호환성 수준을 지정 하 여 [sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)를 실행 **@property** **@value** 합니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-129">Execute [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying **publication_compatibility_level** for **@property** and the appropriate publication compatibility level for **@value**.</span></span>  
  
#### <a name="to-determine-the-publication-compatibility-level-of-a-merge-publication"></a><span data-ttu-id="1117a-130">병합 게시의 게시 호환성 수준을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="1117a-130">To determine the publication compatibility level of a merge publication</span></span>  
  
1.  <span data-ttu-id="1117a-131">원하는 게시를 지정하여 [sp_helpmergepublication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-131">Execute [sp_helpmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specifying the desired publication.</span></span>  
  
2.  <span data-ttu-id="1117a-132">결과 집합의 **backward_comp_level** 열에서 게시 호환성 수준을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-132">Locate the publication compatibility level in the **backward_comp_level** column in the result set.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="1117a-133">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1117a-133">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="1117a-134">다음 예에서는 병합 게시를 만들고 게시 호환성 수준을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-134">This example creates a merge publication and sets the publication compatibility level.</span></span>  
  
```  
-- To avoid storing the login and password in the script file, the values   
-- are passed into SQLCMD as scripting variables. For information about   
-- how to use scripting variables on the command line and in SQL Server  
-- Management Studio, see the "Executing Replication Scripts" section in  
-- the topic "Programming Replication Using System Stored Procedures".  
  
--Add a new merge publication.  
DECLARE @publicationDB AS sysname;  
DECLARE @publication AS sysname;  
DECLARE @login AS sysname;  
DECLARE @password AS sysname;  
SET @publicationDB = N'AdventureWorks2012';   
SET @publication = N'AdvWorksSalesOrdersMerge'   
SET @login = $(Login);  
SET @password = $(Password);  
  
-- Create a new merge publication.   
USE [AdventureWorks2012]  
EXEC sp_addmergepublication   
@publication = @publication,   
-- Set the compatibility level to SQL Server 2014.  
@publication_compatibility_level = '120RTM';   
  
-- Create the snapshot job for the publication.  
EXEC sp_addpublication_snapshot   
@publication = @publication,  
@job_login = @login,  
@job_password = @password;  
GO  
```  
  
 <span data-ttu-id="1117a-135">다음 예에서는 병합 게시에 대한 게시 호환성 수준을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-135">This example changes the publication compatibility level for the merge publication.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1117a-136">게시에서 특정 호환성 수준이 필요한 기능을 사용하고 있는 경우에는 게시 호환성 수준 변경이 허용되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-136">Changing the publication compatibility level might not be allowed if the publication uses any features that require a particular compatibility level.</span></span> <span data-ttu-id="1117a-137">자세한 내용은 [복제의 이전 버전과의 호환성](../replication-backward-compatibility.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1117a-137">For more information, see [Replication Backward Compatibility](../replication-backward-compatibility.md).</span></span>  
  
```  
DECLARE @publication AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge' ;  
  
-- Change the publication compatibility level to   
-- SQL Server 2012.  
EXEC sp_changemergepublication   
@publication = @publication,   
@property = N'publication_compatibility_level',   
@value = N'110RTM';  
GO  
  
```  
  
 <span data-ttu-id="1117a-138">다음 예에서는 병합 게시에 대한 현재 게시 호환성 수준을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1117a-138">This example returns the current publication compatibility level for the merge publication.</span></span>  
  
```  
DECLARE @publication AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge' ;  
EXEC sp_helpmergepublication   
@publication = @publication;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="1117a-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1117a-139">See Also</span></span>  
 [<span data-ttu-id="1117a-140">게시 만들기</span><span class="sxs-lookup"><span data-stu-id="1117a-140">Create a Publication</span></span>](create-a-publication.md)  
  
  
