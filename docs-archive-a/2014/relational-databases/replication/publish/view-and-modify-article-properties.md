---
title: 아티클 속성 보기 및 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_changearticle
- sp_helparticle
- viewing replication properties
- sp_changemergearticle
- sp_helpmergearticle
- modifying replication properties, articles
- articles [SQL Server replication], modifying
- articles [SQL Server replication], properties
ms.assetid: e71831fa-3d39-4e4a-9706-4d3a497082cc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8194b5cc2d4c4a2f1f116ca5a99ea16e18156f13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735199"
---
# <a name="view-and-modify-article-properties"></a><span data-ttu-id="573a9-102">아티클 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="573a9-102">View and Modify Article Properties</span></span>
  <span data-ttu-id="573a9-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 아티클 속성을 보고 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-103">This topic describes how to view and modify article properties in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="573a9-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="573a9-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="573a9-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="573a9-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="573a9-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="573a9-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="573a9-107">권장 사항</span><span class="sxs-lookup"><span data-stu-id="573a9-107">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="573a9-108">**다음을 사용하여 아티클 속성을 보고 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="573a9-108">**To view and modify article properties, using:**</span></span>  
  
     [<span data-ttu-id="573a9-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="573a9-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="573a9-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="573a9-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="573a9-111">RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="573a9-111">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="573a9-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="573a9-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="573a9-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="573a9-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="573a9-114">게시를 만든 다음 일부 속성은 수정할 수 없고, 게시에 대한 구독이 있는 경우에 수정할 수 없는 속성도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-114">Some properties cannot be modified after a publication has been created, and others cannot be modified if there are subscriptions to the publication.</span></span> <span data-ttu-id="573a9-115">수정할 수 없는 속성은 읽기 전용으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-115">Properties that cannot be modified are displayed as read-only.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="573a9-116">권장 사항</span><span class="sxs-lookup"><span data-stu-id="573a9-116">Recommendations</span></span>  
  
-   <span data-ttu-id="573a9-117">게시가 생성되면 일부 속성 변경으로 인해 새 스냅샷이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-117">After a publication is created, some property changes require a new snapshot.</span></span> <span data-ttu-id="573a9-118">게시에 구독이 있는 경우에는 이러한 변경 내용으로 인해 모든 구독도 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-118">If a publication has subscriptions, some changes also require all subscriptions to be reinitialized.</span></span> <span data-ttu-id="573a9-119">자세한 내용은 [게시 및 아티클 속성 변경](change-publication-and-article-properties.md) 및 [기존 게시에 대한 아티클 추가 및 삭제](add-articles-to-and-drop-articles-from-existing-publications.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="573a9-119">For more information, see [Change Publication and Article Properties](change-publication-and-article-properties.md) and [Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="573a9-120">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="573a9-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="573a9-121">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 및 복제 모니터에서 사용할 수 있는 **게시 속성 - \<Publication>** 대화 상자에서 아티클 속성을 확인하고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-121">View and modify article properties in the **Publication Properties - \<Publication>** dialog box, which is available in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and Replication Monitor.</span></span> <span data-ttu-id="573a9-122">복제 모니터를 시작하는 방법은 [복제 모니터 시작](../monitor/start-the-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="573a9-122">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="573a9-123">**일반** 페이지에는 게시 이름 및 설명, 데이터베이스 이름, 게시 유형 및 구독 만료 설정이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-123">The **General** page includes the publication name and description, the database name, the type of publication, and the subscription expiration settings.</span></span>  
  
-   <span data-ttu-id="573a9-124">**아티클** 페이지는 새 게시 마법사의 **아티클** 페이지에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-124">The **Articles** page corresponds to the **Articles** page in the New Publication Wizard.</span></span> <span data-ttu-id="573a9-125">이 페이지를 사용하여 아티클을 추가 및 삭제하고 아티클의 속성 및 열 필터링을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-125">Use this page to add and delete articles, and to change properties and column filtering for articles.</span></span>  
  
-   <span data-ttu-id="573a9-126">**행 필터** 페이지는 새 게시 마법사의 **테이블 행 필터** 페이지에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-126">The **Filter Rows** page corresponds to the **Filter Table Rows** page in the New Publication Wizard.</span></span> <span data-ttu-id="573a9-127">이 페이지를 사용하여 모든 게시 유형에 대해 정적 행 필터를 추가, 편집 및 삭제하고 병합 게시에 대해 매개 변수가 있는 행 필터 및 조인 필터를 추가, 편집 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-127">Use this page to add, edit, and delete static row filters for all types of publications, and to add, edit, and delete parameterized row filters and join filters for merge publications.</span></span>  
  
-   <span data-ttu-id="573a9-128">**스냅샷** 페이지를 사용하면 스냅샷의 형식 및 위치, 스냅샷의 압축 여부 및 스냅샷이 적용되기 전과 후에 실행할 스크립트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-128">The **Snapshot** page allows you to specify the format and location of the snapshot, whether the snapshot should be compressed, and scripts to run before and after the snapshot is applied.</span></span>  
  
-   <span data-ttu-id="573a9-129">**FTP 스냅샷** 페이지(SQL Server 2005 이전 버전을 실행하는 게시자에 대한 병합 게시와 스냅샷 및 트랜잭션 게시의 경우)를 사용하면 구독자가 FTP(파일 전송 프로토콜)를 통해 스냅샷 파일을 다운로드할 수 있는지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-129">The **FTP Snapshot** page (for snapshot and transactional publications, and merge publications for Publishers running versions prior to SQL Server 2005) allows you to specify whether Subscribers can download snapshot files through File Transfer Protocol (FTP).</span></span>  
  
-   <span data-ttu-id="573a9-130">**FTP 스냅샷 및 인터넷** 페이지(SQL Server 2005 이후 버전을 실행하는 게시자에 대한 병합 게시의 경우)를 사용하면 구독자가 FTP를 통해 스냅샷 파일을 다운로드할 수 있는지 여부와 구독자가 HTTPS를 통해 구독을 동기화할 수 있는지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-130">The **FTP Snapshot and Internet** page (for merge publications from Publishers running SQL Server 2005 or later) allows you to specify whether Subscribers can download snapshot files through FTP, and whether Subscribers can synchronize subscriptions through HTTPS.</span></span>  
  
-   <span data-ttu-id="573a9-131">**구독 옵션** 페이지를 사용하면 모든 구독에 적용되는 여러 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-131">The **Subscription Options** page allows you to set a number of options that apply to all subscriptions.</span></span> <span data-ttu-id="573a9-132">사용할 수 있는 옵션은 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-132">The options differ depending on the type of publication.</span></span>  
  
-   <span data-ttu-id="573a9-133">**게시 액세스 목록** 페이지를 사용하면 게시에 액세스할 수 있는 로그인 및 그룹을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-133">The **Publication Access List** page allows you to specify which logins and groups can access a publication.</span></span>  
  
-   <span data-ttu-id="573a9-134">**에이전트 보안** 페이지를 사용하여 모든 게시에 대한 스냅샷 에이전트, 모든 트랜잭션 게시에 대한 로그 판독기 에이전트, 지연 업데이트 구독을 허용하는 트랜잭션 게시에 대한 큐 판독기 에이전트 등 실행하고 복제 토폴로지의 컴퓨터에 이러한 에이전트를 연결하는 계정에 대한 설정에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-134">The **Agent Security** page allows you to access settings for the accounts under which the following agents run and make connections to the computers in a replication topology: the Snapshot Agent for all publications; the Log Reader Agent for all transactional publications; and the Queue Reader Agent for transactional publications that allow queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="573a9-135">**데이터 파티션** 페이지(SQL Server 2005 이후 버전을 실행하는 게시자의 병합 게시의 경우)를 사용하면 매개 변수가 있는 필터가 있는 게시에 대한 구독자가 스냅샷을 사용할 수 없는 경우 스냅샷을 요청할 수 있는지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-135">The **Data Partitions** page (for merge publications from Publishers running SQL Server 2005 or later) allows you to specify whether Subscribers to publications with parameterized filters can request a snapshot if one is not available.</span></span> <span data-ttu-id="573a9-136">또한 하나 이상의 파티션에 대해 스냅샷을 한 번 또는 되풀이되는 일정에 따라 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-136">It also allows you to generate snapshots for one or more partitions, either once or on a recurring schedule.</span></span>  
  
#### <a name="to-view-and-modify-article-properties"></a><span data-ttu-id="573a9-137">아티클 속성을 보고 수정하려면</span><span class="sxs-lookup"><span data-stu-id="573a9-137">To view and modify article properties</span></span>  
  
1.  <span data-ttu-id="573a9-138">**게시 속성 - \<Publication>** 대화 상자의 **아티클** 페이지에서 아티클을 선택한 후 **아티클 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-138">On the **Articles** Page of the **Publication Properties - \<Publication>** dialog box, select an article, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="573a9-139">속성 변경 내용을 적용할 아티클을 다음과 같이 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-139">Select which articles property changes should apply to:</span></span>  
  
    -   <span data-ttu-id="573a9-140">**선택한 \<ObjectType> 아티클 속성 설정**을 클릭하여 **아티클 속성 - \<ObjectName>** 대화 상자를 엽니다. 이 대화 상자에서 변경한 속성은 **아티클** 페이지의 개체 창에 강조 표시된 개체에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-140">Click **Set Properties of Highlighted \<ObjectType> Article** to launch the **Article Properties - \<ObjectName>** dialog box; property changes made in this dialog box are applied only to the object that is highlighted in the object pane on the **Articles** page.</span></span>  
  
    -   <span data-ttu-id="573a9-141">**모든 \<ObjectType> 아티클 속성 설정**을 클릭하여 **모든 \<ObjectType> 아티클의 속성** 대화 상자를 엽니다. 이 대화 상자에서 변경한 속성은 게시용으로, 아직 선택하지 않은 개체를 비롯하여 **아티클** 페이지의 개체 창에서 해당 형식을 갖는 모든 개체에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-141">Click **Set Properties of All \<ObjectType> Articles**, to launch the **Properties for All \<ObjectType> Articles** dialog box; property changes made in this dialog box are applied to all objects of that type in the object pane on the **Articles** page, including ones not yet selected for publication.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="573a9-142">**모든 \<ObjectType> 아티클의 속성** 대화 상자에서 변경한 속성은 이전에 **아티클 속성 - \<ObjectName>** 대화 상자에서 지정한 내용을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-142">Property changes made in the **Properties for All \<ObjectType> Articles** dialog box override any made previously in the **Article Properties - \<ObjectName>** dialog box.</span></span> <span data-ttu-id="573a9-143">예를 들어 특정 개체 유형의 모든 아티클에 대해 여러 기본값을 설정하고 개별 개체에 대해 일부 속성도 설정하려면 먼저 모든 아티클의 기본값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-143">If, for example, you want to set a number of defaults for all articles of an object type, but also want to set some properties for individual objects, set the defaults for all articles first.</span></span> <span data-ttu-id="573a9-144">그런 다음 개별 개체에 대해 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-144">Then set the properties for the individual objects.</span></span>  
  
3.  <span data-ttu-id="573a9-145">필요한 경우 속성을 수정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-145">Modify any properties if necessary, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="573a9-146">**게시 속성 - \<Publication>** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-146">Click **OK** on the **Publication Properties - \<Publication>** dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="573a9-147">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="573a9-147">Using Transact-SQL</span></span>  
 <span data-ttu-id="573a9-148">아티클은 수정할 수 있으며 복제 저장 프로시저를 사용하여 프로그래밍 방식으로 해당 속성을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-148">Articles can be modified and their properties returned programmatically using replication stored procedures.</span></span> <span data-ttu-id="573a9-149">사용되는 저장 프로시저는 아티클이 속한 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-149">The stored procedures that you use depend on the type of publication to which the article belongs.</span></span>  
  
#### <a name="to-view-the-properties-of-an-article-belonging-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="573a9-150">스냅샷 또는 트랜잭션 게시에 속한 아티클의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="573a9-150">To view the properties of an article belonging to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="573a9-151">\*\* \@ 게시\*\* 매개 변수에 게시의 이름을 지정 하 고 \*\* \@ article\*\* 매개 변수에 아티클의 이름을 지정 하 여 [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-151">Execute [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql), specifying the name of the publication for the **\@publication** parameter and the name of the article for the **\@article** parameter.</span></span> <span data-ttu-id="573a9-152">\*\* \@ 아티클을\*\*지정 하지 않으면 게시의 모든 아티클에 대 한 정보가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-152">If you do not specify **\@article**, information will be returned for all articles in the publication.</span></span>  
  
2.  <span data-ttu-id="573a9-153">테이블 아티클에 대해 [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) 를 실행하여 기본 테이블에서 사용할 수 있는 모든 열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-153">Execute [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) for table articles to list all columns available in the base table.</span></span>  
  
#### <a name="to-modify-the-properties-of-an-article-belonging-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="573a9-154">스냅샷 또는 트랜잭션 게시에 속한 아티클의 속성을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="573a9-154">To modify the properties of an article belonging to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="573a9-155">\*\* \@ Property\*\* 매개 변수에 변경 되는 아티클 속성을 지정 하 고 \*\* \@ value\*\* 매개 변수에이 속성의 새 값을 지정 하 여 [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-155">Execute [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql), specifying the article property being changed in the **\@property** parameter and the new value of this property in the **\@value** parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="573a9-156">변경 시 새 스냅숏을 생성 해야 하는 경우 \*\* \@ force_invalidate_snapshot**에 값 **1** 을 지정 해야 하며, 변경으로 인해 구독자를 다시 초기화 해야 하는 경우에는 \*\* \@ force_reinit_subscription**에 대해 값 **1** 도 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-156">If the change requires the generation of a new snapshot, you must also specify a value of **1** for **\@force_invalidate_snapshot**, and if the change requires that Subscribers be reinitialized, you must also specify a value of **1** for **\@force_reinit_subscription**.</span></span> <span data-ttu-id="573a9-157">변경된 경우 새 스냅샷 또는 다시 초기화가 필요한 속성에 대한 자세한 내용은 [게시 및 아티클 속성 변경](change-publication-and-article-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="573a9-157">For more information on the properties that, when changed, require a new snapshot or reinitialization, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
#### <a name="to-view-the-properties-of-an-article-belonging-to-a-merge-publication"></a><span data-ttu-id="573a9-158">병합 게시에 속한 아티클의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="573a9-158">To view the properties of an article belonging to a merge publication</span></span>  
  
1.  <span data-ttu-id="573a9-159">\*\* \@ 게시\*\* 매개 변수에 게시의 이름을 지정 하 고 \*\* \@ article\*\* 매개 변수에 아티클의 이름을 지정 하 여 [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-159">Execute [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql), specifying the name of the publication for the **\@publication** parameter and the name of the article for the **\@article** parameter.</span></span> <span data-ttu-id="573a9-160">이러한 매개 변수를 지정하지 않으면 게시 또는 게시자에 있는 모든 아티클에 대한 정보가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-160">If you do not specify these parameters, information will be returned for all articles in a publication or at the publisher.</span></span>  
  
2.  <span data-ttu-id="573a9-161">테이블 아티클에 대해 [sp_helpmergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-helpmergearticlecolumn-transact-sql) 을 실행하여 기본 테이블에서 사용할 수 있는 모든 열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-161">Execute [sp_helpmergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-helpmergearticlecolumn-transact-sql) for table articles to list all columns available in the base table.</span></span>  
  
#### <a name="to-modify-the-properties-of-an-article-belonging-to-a-merge-publication"></a><span data-ttu-id="573a9-162">병합 게시에 속한 아티클의 속성을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="573a9-162">To modify the properties of an article belonging to a merge publication</span></span>  
  
1.  <span data-ttu-id="573a9-163">\*\* \@ Property\*\* 매개 변수에 변경 되는 아티클 속성을 지정 하 고 \*\* \@ value\*\* 매개 변수에이 속성의 새 값을 지정 하 여 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-163">Execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying the article property being changed in the **\@property** parameter and the new value of this property in the **\@value** parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="573a9-164">변경 시 새 스냅숏을 생성 해야 하는 경우 \*\* \@ force_invalidate_snapshot**에 값 **1** 을 지정 해야 하며, 변경으로 인해 구독자를 다시 초기화 해야 하는 경우에는 \*\* \@ force_reinit_subscription**에 대해 값 **1** 도 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-164">If the change requires the generation of a new snapshot, you must also specify a value of **1** for **\@force_invalidate_snapshot**, and if the change requires that Subscribers be reinitialized, you must also specify a value of **1** for **\@force_reinit_subscription**.</span></span> <span data-ttu-id="573a9-165">변경된 경우 새 스냅샷 또는 다시 초기화가 필요한 속성에 대한 자세한 내용은 [게시 및 아티클 속성 변경](change-publication-and-article-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="573a9-165">For more information on the properties that, when changed, require a new snapshot or reinitialization, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="573a9-166">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="573a9-166">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="573a9-167">이 트랜잭션 복제 예에서는 게시된 아티클의 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-167">This transactional replication example returns the properties of the published article.</span></span>  
  
 [!code-sql[HowTo#sp_helptranarticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranart.sql#sp_helptranarticle)]  
  
 <span data-ttu-id="573a9-168">이 트랜잭션 복제 예에서는 게시된 아티클에 대한 스키마 옵션을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-168">This transactional replication example changes the schema options for the published article.</span></span>  
  
 [!code-sql[HowTo#sp_changetranarticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranart.sql#sp_changetranarticle)]  
  
 <span data-ttu-id="573a9-169">이 병합 복제 예에서는 게시된 아티클의 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-169">This merge replication example returns the properties of the published article.</span></span>  
  
 [!code-sql[HowTo#sp_helpmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergeart.sql#sp_helpmergearticle)]  
  
 <span data-ttu-id="573a9-170">이 병합 복제 예에서는 게시된 아티클에 대한 충돌 검색 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-170">This merge replication example changes the conflict detection settings for a published article.</span></span>  
  
 [!code-sql[HowTo#sp_changemergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergeart.sql#sp_changemergearticle)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="573a9-171">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="573a9-171">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="573a9-172">RMO(복제 관리 개체)를 사용하여 프로그래밍 방식으로 아티클을 수정하고 해당 속성에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-172">You can modify articles and access their properties programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="573a9-173">아티클 속성을 보거나 수정하는 데 사용되는 RMO 클래스는 아티클이 속한 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-173">The RMO classes you use to view or modify article properties depend on the type of publication to which the article belongs.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-an-article-that-belongs-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="573a9-174">스냅샷 또는 트랜잭션 게시에 속하는 아티클의 속성을 보거나 수정하려면</span><span class="sxs-lookup"><span data-stu-id="573a9-174">To view or modify properties of an article that belongs to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="573a9-175"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-175">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="573a9-176"><xref:Microsoft.SqlServer.Replication.TransArticle> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-176">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransArticle> class.</span></span>  
  
3.  <span data-ttu-id="573a9-177"><xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>및 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-177">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="573a9-178"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성에 대해 1단계에서 만든 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-178">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="573a9-179"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-179">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="573a9-180">이 메서드가 `false`를 반환하는 경우 3단계에서 아티클 속성이 올바르게 정의되지 않았거나 아티클이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-180">If this method returns `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span>  
  
6.  <span data-ttu-id="573a9-181">(옵션) 속성을 변경하려면 설정할 수 있는 <xref:Microsoft.SqlServer.Replication.TransArticle> 속성 중 하나에 대해 새 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-181">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.TransArticle> properties that can be set.</span></span>  
  
7.  <span data-ttu-id="573a9-182">(옵션) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>에 대해 `true` 값을 지정했으면 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 메서드를 호출하여 서버의 변경 내용을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-182">(Optional) If you specified a value of `true` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit changes on the server.</span></span> <span data-ttu-id="573a9-183"><xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>에 대해 `false` 값을 지정했으면(기본값) 변경 내용이 즉시 서버로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-183">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (the default), changes are sent to the server immediately.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-an-article-that-belongs-to-a-merge-publication"></a><span data-ttu-id="573a9-184">병합 게시에 속하는 아티클의 속성을 보거나 수정하려면</span><span class="sxs-lookup"><span data-stu-id="573a9-184">To view or modify properties of an article that belongs to a merge publication</span></span>  
  
1.  <span data-ttu-id="573a9-185"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-185">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="573a9-186"><xref:Microsoft.SqlServer.Replication.MergeArticle> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-186">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class.</span></span>  
  
3.  <span data-ttu-id="573a9-187"><xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>및 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-187">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="573a9-188"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성에 대해 1단계에서 만든 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-188">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="573a9-189"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-189">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="573a9-190">이 메서드가 `false`를 반환하는 경우 3단계에서 아티클 속성이 올바르게 정의되지 않았거나 아티클이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-190">If this method returns `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span>  
  
6.  <span data-ttu-id="573a9-191">(옵션) 속성을 변경하려면 설정할 수 있는 <xref:Microsoft.SqlServer.Replication.MergeArticle> 속성 중 하나에 대해 새 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-191">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.MergeArticle> properties that can be set.</span></span>  
  
7.  <span data-ttu-id="573a9-192">(옵션) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>에 대해 `true` 값을 지정했으면 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 메서드를 호출하여 서버의 변경 내용을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-192">(Optional) If you specified a value of `true` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit changes on the server.</span></span> <span data-ttu-id="573a9-193"><xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>에 대해 `false` 값을 지정했으면(기본값) 변경 내용이 즉시 서버로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-193">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (the default), changes are sent to the server immediately.</span></span>  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="573a9-194">예(RMO)</span><span class="sxs-lookup"><span data-stu-id="573a9-194">Example (RMO)</span></span>  
 <span data-ttu-id="573a9-195">다음 예에서는 병합 아티클을 변경하여 아티클에서 사용하는 비즈니스 논리 처리기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="573a9-195">This example changes a merge article to specify the business logic handler used by the article.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## <a name="see-also"></a><span data-ttu-id="573a9-196">참고 항목</span><span class="sxs-lookup"><span data-stu-id="573a9-196">See Also</span></span>  
 <span data-ttu-id="573a9-197">[병합 아티클에 대한 비즈니스 논리 처리기 구현](../implement-a-business-logic-handler-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="573a9-197">[Implement a Business Logic Handler for a Merge Article](../implement-a-business-logic-handler-for-a-merge-article.md) </span></span>  
 <span data-ttu-id="573a9-198">[데이터 및 데이터베이스 개체 게시](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="573a9-198">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="573a9-199">[게시 및 아티클 속성 변경](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="573a9-199">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="573a9-200">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="573a9-200">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="573a9-201">Advanced Merge Replication Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="573a9-201">Advanced Merge Replication Conflict Detection and Resolution</span></span>](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
