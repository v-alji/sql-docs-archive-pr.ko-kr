---
title: 아티클 정의 | Microsoft 문서
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], defining
- sp_addmergearticle
- adding articles
- sp_addarticle
- articles [SQL Server replication], adding
ms.assetid: 220584d8-b291-43ae-b036-fbba3cc07a2e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d7ff1f5f516d438ed07a203223acf32970a7961
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661024"
---
# <a name="define-an-article"></a><span data-ttu-id="f0eac-102">아티클 정의</span><span class="sxs-lookup"><span data-stu-id="f0eac-102">Define an Article</span></span>
  <span data-ttu-id="f0eac-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 아티클을 정의하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-103">This topic describes how to define an article in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="f0eac-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="f0eac-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f0eac-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="f0eac-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f0eac-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="f0eac-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f0eac-107">보안</span><span class="sxs-lookup"><span data-stu-id="f0eac-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f0eac-108">**아티클을 정의하려면:**</span><span class="sxs-lookup"><span data-stu-id="f0eac-108">**To define an article, using:**</span></span>  
  
     [<span data-ttu-id="f0eac-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f0eac-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f0eac-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f0eac-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="f0eac-111">RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="f0eac-111">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f0eac-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f0eac-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f0eac-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="f0eac-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f0eac-114">아티클 이름에는 %, \*, [,], |, :, ", ? 등의 문자를 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-114">Article names cannot include any of the following characters: % , \* , [ , ] , | , : , " , ?</span></span> <span data-ttu-id="f0eac-115">, ' , \ , / , \< , >.</span><span class="sxs-lookup"><span data-stu-id="f0eac-115">, ' , \ , / , \< , >.</span></span> <span data-ttu-id="f0eac-116">이러한 문자를 포함하는 데이터베이스 개체를 복제하려면 개체 이름과 다른 아티클 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-116">If objects in the database include any of these characters and you want to replicate them, you must specify an article name that is different from the object name.</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f0eac-117">보안</span><span class="sxs-lookup"><span data-stu-id="f0eac-117">Security</span></span>  
 <span data-ttu-id="f0eac-118">가능한 경우 런타임 시 사용자에게 보안 자격 증명을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-118">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="f0eac-119">자격 증명을 저장해야 하는 경우 [Windows .NET Framework에서 제공하는](https://go.microsoft.com/fwlink/?LinkId=34733) 암호화 서비스 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-119">If you must store credentials, use the [cryptographic services](https://go.microsoft.com/fwlink/?LinkId=34733) provided by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows .NET Framework.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f0eac-120">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="f0eac-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f0eac-121">새 게시 마법사를 사용하여 게시를 만들고 아티클을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-121">Create publications and define articles with the New Publication Wizard.</span></span> <span data-ttu-id="f0eac-122">게시를 만든 다음 **게시 속성 - \<Publication>** 대화 상자에서 게시 속성을 보고 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-122">After a publication is created, view and modify publication properties in the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="f0eac-123">Oracle 데이터베이스에서 게시를 만드는 방법에 대한 자세한 내용은 [Oracle 데이터베이스에서 게시 만들기](create-a-publication-from-an-oracle-database.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eac-123">For information about creating a publication from an Oracle database, see [Create a Publication from an Oracle Database](create-a-publication-from-an-oracle-database.md).</span></span>  
  
#### <a name="to-create-a-publication-and-define-articles"></a><span data-ttu-id="f0eac-124">게시를 만들고 아티클을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="f0eac-124">To create a publication and define articles</span></span>  
  
1.  <span data-ttu-id="f0eac-125">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결한 다음, 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-125">Connect to the Publisher in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="f0eac-126">**복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-126">Expand the **Replication** folder, and then right-click the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="f0eac-127">**새 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-127">Click **New Publication**.</span></span>  
  
4.  <span data-ttu-id="f0eac-128">새 게시 마법사의 페이지에 따라 다음을 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eac-128">Follow the pages in the New Publication Wizard to:</span></span>  
  
    -   <span data-ttu-id="f0eac-129">서버에 배포가 구성되어 있지 않은 경우 배포자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-129">Specify a Distributor if distribution has not been configured on the server.</span></span> <span data-ttu-id="f0eac-130">배포 구성에 대한 자세한 내용은 [게시 및 배포 구성](../configure-publishing-and-distribution.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eac-130">For more information about configuring distribution, see [Configure Publishing and Distribution](../configure-publishing-and-distribution.md).</span></span>  
  
         <span data-ttu-id="f0eac-131">**배포자** 페이지에서 게시자 서버가 자신의 고유 배포자(로컬 배포자) 역할을 하는 것으로 지정했지만 서버가 배포자로 구성되어 있지 않은 경우 새 게시 마법사가 서버를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-131">If you specify on the **Distributor** page that the Publisher server will act as its own Distributor (a local Distributor), and the server is not configured as a Distributor, the New Publication Wizard will configure the server.</span></span> <span data-ttu-id="f0eac-132">**스냅샷 폴더** 페이지에서 배포자에 대해 기본 스냅샷 폴더를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-132">You will specify a default snapshot folder for the Distributor on the **Snapshot Folder** page.</span></span> <span data-ttu-id="f0eac-133">스냅샷 폴더는 공유하도록 지정된 디렉터리일 뿐이며 이 폴더에 읽기/쓰기 작업을 수행하려면 에이전트에게 충분한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-133">The snapshot folder is simply a directory that you have designated as a share; agents that read from and write to this folder must have sufficient permissions to access it.</span></span> <span data-ttu-id="f0eac-134">폴더의 적절한 보안 유지 방법에 대한 자세한 내용은 [스냅샷 폴더 보안 설정](../security/secure-the-snapshot-folder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eac-134">For more information about securing the folder appropriately, see [Secure the Snapshot Folder](../security/secure-the-snapshot-folder.md).</span></span>  
  
         <span data-ttu-id="f0eac-135">다른 서버가 배포자의 역할을 하도록 지정한 경우 게시자에서 배포자로 연결할 때 사용할 암호를 **관리 암호** 페이지에 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-135">If you specify that another server should act as the Distributor, you must enter a password on the **Administrative Password** page for connections made from the Publisher to the Distributor.</span></span> <span data-ttu-id="f0eac-136">이 암호는 원격 배포자에서 게시자를 설정할 때 지정한 암호와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-136">This password must match the password specified when the Publisher was enabled at the remote Distributor.</span></span>  
  
         <span data-ttu-id="f0eac-137">자세한 내용은 [Configure Distribution](../configure-distribution.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eac-137">For more information, see [Configure Distribution](../configure-distribution.md).</span></span>  
  
    -   <span data-ttu-id="f0eac-138">게시 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-138">Choose a publication database.</span></span>  
  
    -   <span data-ttu-id="f0eac-139">보고서 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-139">Select a publication type.</span></span> <span data-ttu-id="f0eac-140">자세한 내용은 [복제 유형](../types-of-replication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eac-140">For more information, see [Types of Replication](../types-of-replication.md).</span></span>  
  
    -   <span data-ttu-id="f0eac-141">게시할 데이터와 데이터베이스 개체를 지정합니다. 필요에 따라 테이블 아티클에서 열을 필터링하고 아티클 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-141">Specify data and database objects to publish; optionally filter columns from table articles, and set article properties.</span></span>  
  
    -   <span data-ttu-id="f0eac-142">필요에 따라 테이블 아티클에서 행을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-142">Optionally filter rows from table articles.</span></span> <span data-ttu-id="f0eac-143">자세한 내용은 [게시된 데이터 필터링](filter-published-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eac-143">For more information, see [Filter Published Data](filter-published-data.md).</span></span>  
  
    -   <span data-ttu-id="f0eac-144">스냅샷 에이전트 일정을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-144">Set the Snapshot Agent schedule.</span></span>  
  
    -   <span data-ttu-id="f0eac-145">다음 복제 에이전트를 실행 및 연결하는 자격 증명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-145">Specify the credentials under which the following replication agents run and make connections:</span></span>  
  
         <span data-ttu-id="f0eac-146">모든 게시에 대한 \- 스냅샷 에이전트</span><span class="sxs-lookup"><span data-stu-id="f0eac-146">\- Snapshot Agent for all publications.</span></span>  
  
         <span data-ttu-id="f0eac-147">모든 트랜잭션 게시에 대한 \- 로그 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="f0eac-147">\- Log Reader Agent for all transactional publications.</span></span>  
  
         <span data-ttu-id="f0eac-148">\- 구독 업데이트를 허용하는 트랜잭션 게시에 대한 큐 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="f0eac-148">\- Queue Reader Agent for transactional publications that allow updating subscriptions.</span></span>  
  
         <span data-ttu-id="f0eac-149">자세한 내용은 [Replication Agent Security Model](../security/replication-agent-security-model.md) 및 [Replication Security Best Practices](../security/replication-security-best-practices.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eac-149">For more information, see [Replication Agent Security Model](../security/replication-agent-security-model.md) and [Replication Security Best Practices](../security/replication-security-best-practices.md).</span></span>  
  
    -   <span data-ttu-id="f0eac-150">필요에 따라 게시를 스크립팅합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-150">Optionally script the publication.</span></span> <span data-ttu-id="f0eac-151">자세한 내용은 [Scripting Replication](../scripting-replication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eac-151">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
    -   <span data-ttu-id="f0eac-152">게시의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-152">Specify a name for the publication.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f0eac-153">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="f0eac-153">Using Transact-SQL</span></span>  
 <span data-ttu-id="f0eac-154">게시를 만든 후에 복제 저장 프로시저를 사용하여 아티클을 프로그래밍 방식으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-154">After a publication has been created, articles can be created programmatically using replication stored procedures.</span></span> <span data-ttu-id="f0eac-155">아티클을 만드는 데 사용되는 저장 프로시저는 정의하려는 아티클의 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-155">The stored procedures used to create an article will depend on the type of publication for which the article is being defined.</span></span> <span data-ttu-id="f0eac-156">자세한 내용은 [게시 만들기](create-a-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eac-156">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-define-an-article-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="f0eac-157">스냅샷 또는 트랜잭션 게시에 대한 아티클을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="f0eac-157">To define an article for a Snapshot or Transactional Publication</span></span>  
  
1.  <span data-ttu-id="f0eac-158">게시 데이터베이스의 게시자에서 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-158">At the Publisher on the publication database, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="f0eac-159">\*\* \@ 게시**에 대해 아티클이 속한 게시의 이름, \*\* \@ 아티클의**아티클 이름, \*\* \@ source_object\*\*에 대해 게시 되는 데이터베이스 개체 및 기타 선택적 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-159">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, and any other optional parameters.</span></span> <span data-ttu-id="f0eac-160">**Dbo**가 아닌 경우 \*\* \@ source_owner\*\* 를 사용 하 여 개체의 스키마 소유권을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-160">Use **\@source_owner** to specify the schema ownership of the object, if not **dbo**.</span></span> <span data-ttu-id="f0eac-161">아티클이 로그 기반 테이블 아티클이 아닌 경우 \*\* \@ 유형에\*\*대 한 아티클 유형을 지정 합니다. 자세한 내용은 [복제 Transact-sql&#41;프로그래밍 &#40;아티클 유형 지정 ](specify-article-types-replication-transact-sql-programming.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eac-161">If the article is not a log-based table article, specify the article type for **\@type**; for more information, see [Specify Article Types &#40;Replication Transact-SQL Programming&#41;](specify-article-types-replication-transact-sql-programming.md).</span></span>  
  
2.  <span data-ttu-id="f0eac-162">테이블의 행을 행 필터링하거나 아티클을 보려면 [sp_articlefilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) 를 사용하여 필터 절을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-162">To horizontally filter rows in a table or view an article, use [sp_articlefilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) to define the filter clause.</span></span> <span data-ttu-id="f0eac-163">자세한 내용은 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eac-163">For more information, see [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span>  
  
3.  <span data-ttu-id="f0eac-164">테이블의 열을 열 필터링하거나 아티클을 보려면 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-164">To vertically filter columns in a table or view an article, use [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql).</span></span> <span data-ttu-id="f0eac-165">자세한 내용은 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eac-165">For more information, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>  
  
4.  <span data-ttu-id="f0eac-166">아티클이 필터링되었으면 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-166">Execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) if the article is filtered.</span></span>  
  
5.  <span data-ttu-id="f0eac-167">게시에 기존 구독이 있고 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) 이 **immediate_sync** 열에 값 **0** 을 반환하면 [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) 을 호출하여 각각의 기존 구독에 아티클을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-167">If the publication has existing subscriptions and [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) returns a value of **0** in the **immediate_sync** column, you must call [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) to add the article to each existing subscription.</span></span>  
  
6.  <span data-ttu-id="f0eac-168">게시에 기존 끌어오기 구독이 있으면 게시자에서 [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) 를 실행하여 새 아티클을 포함하는, 기존 끌어오기 구독에 대한 새 스냅샷을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-168">If the publication has existing pull subscriptions, execute [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) at the Publisher to create a new snapshot for existing pull subscriptions that contains just the new article.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f0eac-169">스냅샷을 사용하여 초기화되지 않은 구독에 대해서는 [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) 를 실행하지 않아도 됩니다. 이 절차는 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)에 의해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-169">For subscriptions that are not initialized using a snapshot, you do not need to execute [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) as this procedure is executed by [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span>  
  
#### <a name="to-define-an-article-for-a-merge-publication"></a><span data-ttu-id="f0eac-170">병합 게시에 대한 아티클을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="f0eac-170">To define an article for a Merge Publication</span></span>  
  
1.  <span data-ttu-id="f0eac-171">게시 데이터베이스의 게시자에서 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-171">At the Publisher on the publication database, execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="f0eac-172">게시에 대 한 게시 이름, \*\* \@ \*\* \*\* \@ 아티클의**아티클 이름 이름 및 \*\* \@ source_object**에 대해 게시 되는 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-172">Specify the name of the publication for **\@publication**, a name for the article name for **\@article**, and the object being published for **\@source_object**.</span></span> <span data-ttu-id="f0eac-173">테이블 행을 행 필터링 하려면 \*\* \@ subset_filterclause\*\*의 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-173">To horizontally filter table rows, specify a value for **\@subset_filterclause**.</span></span> <span data-ttu-id="f0eac-174">자세한 내용은 [병합 아티클에 대한 매개 변수가 있는 행 필터 정의 및 수정](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) 및 [정적 행 필터 정의 및 수정](define-and-modify-a-static-row-filter.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eac-174">For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) and [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span> <span data-ttu-id="f0eac-175">아티클이 테이블 아티클이 아닌 경우 \*\* \@ 유형\*\*의 아티클 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-175">If the article is not a table article, specify the article type for **\@type**.</span></span> <span data-ttu-id="f0eac-176">자세한 내용은 [아티클 유형 정의&#40;복제 Transact-SQL 프로그래밍&#41;](specify-article-types-replication-transact-sql-programming.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eac-176">For more information, see [Specify Article Types &#40;Replication Transact-SQL Programming&#41;](specify-article-types-replication-transact-sql-programming.md).</span></span>  
  
2.  <span data-ttu-id="f0eac-177">필요에 따라 게시 데이터베이스의 게시자에서 [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) 를 실행하여 두 아티클 간의 조인 필터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-177">(Optional) At the Publisher on the publication database, execute [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) to define a join filter between two articles.</span></span> <span data-ttu-id="f0eac-178">자세한 내용은 [병합 아티클 사이에서 조인 필터 정의 및 수정](define-and-modify-a-join-filter-between-merge-articles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eac-178">For more information, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
3.  <span data-ttu-id="f0eac-179">필요에 따라 게시 데이터베이스의 게시자에서 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) 을 실행하여 테이블 열을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-179">(Optional) At the Publisher on the publication database, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) to filter table columns.</span></span> <span data-ttu-id="f0eac-180">자세한 내용은 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0eac-180">For more information, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="f0eac-181">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f0eac-181">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="f0eac-182">이 예에서는 `Product` 테이블을 기반으로 트랜잭션 게시에 대한 아티클을 정의합니다. 여기에서 아티클은 행 및 열 방향으로 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-182">This example defines an article based on the `Product` table for a transactional publication, where the article is filtered both horizontally and vertically.</span></span>  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 <span data-ttu-id="f0eac-183">이 예에서는 병합 게시에 대한 아티클을 정의합니다. 여기에서 `SalesOrderHeader` 아티클은 **SalesPersonID**에 따라 정적으로 필터링되고 `SalesOrderDetail` 아티클은 `SalesOrderHeader`에 따라 조인 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-183">This example defines articles for a merge publication, where the `SalesOrderHeader` article is statically filtered based on **SalesPersonID**, and the `SalesOrderDetail` article is join filtered based on `SalesOrderHeader`.</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="f0eac-184">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="f0eac-184">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="f0eac-185">RMO(복제 관리 개체)를 사용하여 프로그래밍 방식으로 아티클을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-185">You can define articles programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="f0eac-186">아티클을 정의하는 데 사용하는 RMO 클래스는 정의되는 아티클의 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-186">The RMO classes that you use to define an article depend on the type of publication for which the article is defined.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="f0eac-187">예(RMO)</span><span class="sxs-lookup"><span data-stu-id="f0eac-187">Examples (RMO)</span></span>  
 <span data-ttu-id="f0eac-188">다음 예에서는 행 및 열 필터가 포함된 아티클을 트랜잭션 게시에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-188">The following example adds an article with row and column filters to a transactional publication.</span></span>  
  
 [!code-csharp[HowTo#rmo_CreateTranArticles](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createtranarticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranArticles](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createtranarticles)]  
  
 <span data-ttu-id="f0eac-189">다음 예에서는 병합 게시에 세 개의 아티클을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-189">The following example adds three articles to a merge publication.</span></span> <span data-ttu-id="f0eac-190">이 아티클에는 열 필터가 포함되며, 두 개의 조인 필터를 사용하여 매개 변수가 있는 행 필터를 다른 아티클에 전파합니다.</span><span class="sxs-lookup"><span data-stu-id="f0eac-190">The articles have column filters, and two join filters are used to propagate a parameterized row filter to the other articles.</span></span>  
  
 [!code-csharp[HowTo#rmo_CreateMergeArticles](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergearticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergeArticles](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergearticles)]  
  
## <a name="see-also"></a><span data-ttu-id="f0eac-191">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f0eac-191">See Also</span></span>  
 <span data-ttu-id="f0eac-192">[Create a Publication](create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="f0eac-192">[Create a Publication](create-a-publication.md) </span></span>  
 <span data-ttu-id="f0eac-193">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="f0eac-193">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 <span data-ttu-id="f0eac-194">[기존 게시에 대한 아티클 추가 및 삭제](add-articles-to-and-drop-articles-from-existing-publications.md) </span><span class="sxs-lookup"><span data-stu-id="f0eac-194">[Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md) </span></span>  
 <span data-ttu-id="f0eac-195">[게시된 데이터 필터링](filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="f0eac-195">[Filter Published Data](filter-published-data.md) </span></span>  
 <span data-ttu-id="f0eac-196">[데이터 및 데이터베이스 개체 게시](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="f0eac-196">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="f0eac-197">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="f0eac-197">Replication System Stored Procedures Concepts</span></span>](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
