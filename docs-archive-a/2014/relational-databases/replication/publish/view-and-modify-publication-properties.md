---
title: 게시 속성 보기 및 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- modifying replication properties, articles
- articles [SQL Server replication], modifying
- publications [SQL Server replication], properties
- articles [SQL Server replication], properties
- modifying replication properties, publications
- publications [SQL Server replication], modifying
ms.assetid: 27d72ea4-bcb6-48f2-b4aa-eb1410da7efc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 89b969bc3e285bbdc633a2b39d237968b216069a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646330"
---
# <a name="view-and-modify-publication-properties"></a><span data-ttu-id="8ba2c-102">게시 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="8ba2c-102">View and Modify Publication Properties</span></span>
  <span data-ttu-id="8ba2c-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 게시 속성을 보고 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-103">This topic describes how to view and modify publication properties in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="8ba2c-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="8ba2c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8ba2c-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="8ba2c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8ba2c-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="8ba2c-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="8ba2c-107">권장 사항</span><span class="sxs-lookup"><span data-stu-id="8ba2c-107">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="8ba2c-108">**게시 속성을 보고 수정하려면:**</span><span class="sxs-lookup"><span data-stu-id="8ba2c-108">**To view and modify publication properties, using:**</span></span>  
  
     [<span data-ttu-id="8ba2c-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8ba2c-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8ba2c-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8ba2c-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="8ba2c-111">RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="8ba2c-111">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8ba2c-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="8ba2c-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8ba2c-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="8ba2c-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="8ba2c-114">게시를 만든 다음 일부 속성은 수정할 수 없고, 게시에 대한 구독이 있는 경우에 수정할 수 없는 속성도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-114">Some properties cannot be modified after a publication has been created, and others cannot be modified if there are subscriptions to the publication.</span></span> <span data-ttu-id="8ba2c-115">수정할 수 없는 속성은 읽기 전용으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-115">Properties that cannot be modified are displayed as read-only.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="8ba2c-116">권장 사항</span><span class="sxs-lookup"><span data-stu-id="8ba2c-116">Recommendations</span></span>  
  
-   <span data-ttu-id="8ba2c-117">게시가 생성되면 일부 속성 변경으로 인해 새 스냅샷이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-117">After a publication is created, some property changes require a new snapshot.</span></span> <span data-ttu-id="8ba2c-118">게시에 구독이 있는 경우에는 이러한 변경 내용으로 인해 모든 구독도 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-118">If a publication has subscriptions, some changes also require all subscriptions to be reinitialized.</span></span> <span data-ttu-id="8ba2c-119">자세한 내용은 [게시 및 아티클 속성 변경](change-publication-and-article-properties.md) 및 [기존 게시에 대한 아티클 추가 및 삭제](add-articles-to-and-drop-articles-from-existing-publications.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-119">For more information, see [Change Publication and Article Properties](change-publication-and-article-properties.md) and [Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8ba2c-120">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="8ba2c-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="8ba2c-121">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 및 복제 모니터에서 사용할 수 있는 **게시 속성 - \<Publication>** 대화 상자에서 게시 속성을 확인하고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-121">View and modify publication properties in the **Publication Properties - \<Publication>** dialog box, which is available in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and Replication Monitor.</span></span> <span data-ttu-id="8ba2c-122">복제 모니터를 시작하는 방법은 [복제 모니터 시작](../monitor/start-the-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-122">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="8ba2c-123">**게시 속성 - \<Publication>** 대화 상자에는 다음 페이지가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-123">The **Publication Properties - \<Publication>** dialog box includes the following pages:</span></span>  
  
-   <span data-ttu-id="8ba2c-124">**일반** 페이지에는 게시 이름 및 설명, 데이터베이스 이름, 게시 유형 및 구독 만료 설정이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-124">The **General** page includes the publication name and description, the database name, the type of publication, and the subscription expiration settings.</span></span>  
  
-   <span data-ttu-id="8ba2c-125">**아티클** 페이지는 새 게시 마법사의 **아티클** 페이지에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-125">The **Articles** page corresponds to the **Articles** page in the New Publication Wizard.</span></span> <span data-ttu-id="8ba2c-126">이 페이지를 사용하여 아티클을 추가 및 삭제하고 아티클의 속성 및 열 필터링을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-126">Use this page to add and delete articles, and to change properties and column filtering for articles.</span></span>  
  
-   <span data-ttu-id="8ba2c-127">**행 필터** 페이지는 새 게시 마법사의 **테이블 행 필터** 페이지에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-127">The **Filter Rows** page corresponds to the **Filter Table Rows** page in the New Publication Wizard.</span></span> <span data-ttu-id="8ba2c-128">이 페이지를 사용하여 모든 게시 유형에 대해 정적 행 필터를 추가, 편집 및 삭제하고 병합 게시에 대해 매개 변수가 있는 행 필터 및 조인 필터를 추가, 편집 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-128">Use this page to add, edit, and delete static row filters for all types of publications, and to add, edit, and delete parameterized row filters and join filters for merge publications.</span></span>  
  
-   <span data-ttu-id="8ba2c-129">**스냅샷** 페이지를 사용하면 스냅샷의 형식 및 위치, 스냅샷의 압축 여부 및 스냅샷이 적용되기 전과 후에 실행할 스크립트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-129">The **Snapshot** page allows you to specify the format and location of the snapshot, whether the snapshot should be compressed, and scripts to run before and after the snapshot is applied.</span></span>  
  
-   <span data-ttu-id="8ba2c-130">**FTP 스냅샷** 페이지(SQL Server 2005 이전 버전을 실행하는 게시자에 대한 병합 게시와 스냅샷 및 트랜잭션 게시의 경우)를 사용하면 구독자가 FTP(파일 전송 프로토콜)를 통해 스냅샷 파일을 다운로드할 수 있는지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-130">The **FTP Snapshot** page (for snapshot and transactional publications, and merge publications for Publishers running versions prior to SQL Server 2005) allows you to specify whether Subscribers can download snapshot files through File Transfer Protocol (FTP).</span></span>  
  
-   <span data-ttu-id="8ba2c-131">**FTP 스냅샷 및 인터넷** 페이지(SQL Server 2005 이후 버전을 실행하는 게시자에 대한 병합 게시의 경우)를 사용하면 구독자가 FTP를 통해 스냅샷 파일을 다운로드할 수 있는지 여부와 구독자가 HTTPS를 통해 구독을 동기화할 수 있는지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-131">The **FTP Snapshot and Internet** page (for merge publications from Publishers running SQL Server 2005 or later) allows you to specify whether Subscribers can download snapshot files through FTP, and whether Subscribers can synchronize subscriptions through HTTPS.</span></span>  
  
-   <span data-ttu-id="8ba2c-132">**구독 옵션** 페이지를 사용하면 모든 구독에 적용되는 여러 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-132">The **Subscription Options** page allows you to set a number of options that apply to all subscriptions.</span></span> <span data-ttu-id="8ba2c-133">사용할 수 있는 옵션은 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-133">The options differ depending on the type of publication.</span></span>  
  
-   <span data-ttu-id="8ba2c-134">**게시 액세스 목록** 페이지를 사용하면 게시에 액세스할 수 있는 로그인 및 그룹을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-134">The **Publication Access List** page allows you to specify which logins and groups can access a publication.</span></span>  
  
-   <span data-ttu-id="8ba2c-135">**에이전트 보안** 페이지를 사용하여 모든 게시에 대한 스냅샷 에이전트, 모든 트랜잭션 게시에 대한 로그 판독기 에이전트, 지연 업데이트 구독을 허용하는 트랜잭션 게시에 대한 큐 판독기 에이전트 등 실행하고 복제 토폴로지의 컴퓨터에 이러한 에이전트를 연결하는 계정에 대한 설정에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-135">The **Agent Security** page allows you to access settings for the accounts under which the following agents run and make connections to the computers in a replication topology: the Snapshot Agent for all publications; the Log Reader Agent for all transactional publications; and the Queue Reader Agent for transactional publications that allow queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="8ba2c-136">**데이터 파티션** 페이지(SQL Server 2005 이후 버전을 실행하는 게시자의 병합 게시의 경우)를 사용하면 매개 변수가 있는 필터가 있는 게시에 대한 구독자가 스냅샷을 사용할 수 없는 경우 스냅샷을 요청할 수 있는지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-136">The **Data Partitions** page (for merge publications from Publishers running SQL Server 2005 or later) allows you to specify whether Subscribers to publications with parameterized filters can request a snapshot if one is not available.</span></span> <span data-ttu-id="8ba2c-137">또한 하나 이상의 파티션에 대해 스냅샷을 한 번 또는 되풀이되는 일정에 따라 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-137">It also allows you to generate snapshots for one or more partitions, either once or on a recurring schedule.</span></span>  
  
#### <a name="to-view-and-modify-publication-properties-in-management-studio"></a><span data-ttu-id="8ba2c-138">Management Studio에서 게시 속성을 보고 수정하려면</span><span class="sxs-lookup"><span data-stu-id="8ba2c-138">To view and modify publication properties in Management Studio</span></span>  
  
1.  <span data-ttu-id="8ba2c-139">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-139">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="8ba2c-140">**복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-140">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="8ba2c-141">게시를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-141">Right-click a publication, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="8ba2c-142">필요한 경우 속성을 수정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-142">Modify any properties if necessary, and then click **OK**.</span></span>  
  
#### <a name="to-view-and-modify-publication-properties-in-replication-monitor"></a><span data-ttu-id="8ba2c-143">복제 모니터에서 게시 속성을 보고 수정하려면</span><span class="sxs-lookup"><span data-stu-id="8ba2c-143">To view and modify publication properties in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="8ba2c-144">복제 모니터의 왼쪽 창에서 게시자 그룹을 확장한 다음 게시자를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-144">Expand a Publisher group in the left pane of Replication Monitor, and then expand a Publisher.</span></span>  
  
2.  <span data-ttu-id="8ba2c-145">게시를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-145">Right-click a publication, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="8ba2c-146">필요한 경우 속성을 수정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-146">Modify any properties if necessary, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8ba2c-147">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="8ba2c-147">Using Transact-SQL</span></span>  
 <span data-ttu-id="8ba2c-148">게시는 수정할 수 있으며 게시 속성은 복제 저장 프로시저를 사용하여 프로그래밍 방식으로 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-148">Publications can be modified and their properties returned programmatically using replication stored procedures.</span></span> <span data-ttu-id="8ba2c-149">사용하는 저장 프로시저는 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-149">The stored procedures that you use will depend on the type of publication.</span></span>  
  
#### <a name="to-view-the-properties-of-a-snapshot-or-transactional-publication"></a><span data-ttu-id="8ba2c-150">스냅샷 또는 트랜잭션 게시의 속성을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="8ba2c-150">To view the properties of a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="8ba2c-151">**\@publication** 매개 변수에 게시 이름을 지정하여 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-151">Execute [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql), specifying the name of the publication for the **\@publication** parameter.</span></span> <span data-ttu-id="8ba2c-152">이 매개 변수를 지정하지 않으면 게시자에 있는 모든 게시에 대한 정보가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-152">If you do not specify this parameter, information on all publications at the Publisher is returned.</span></span>  
  
#### <a name="to-change-the-properties-of-a-snapshot-or-transactional-publication"></a><span data-ttu-id="8ba2c-153">스냅샷 또는 트랜잭션 게시의 속성을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="8ba2c-153">To change the properties of a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="8ba2c-154">**\@property** 매개 변수에 변경할 게시 속성, **\@value** 매개 변수에 이 속성의 새 값을 지정하여 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-154">Execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying the publication property to change in the **\@property** parameter and the new value of this property in the **\@value** parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8ba2c-155">변경 시 새 스냅샷을 생성해야 하는 경우 **\@force_invalidate_snapshot** 값도 **1**로 지정해야 합니다. 변경 시 구독자를 초기화해야 하는 경우 **\@force_reinit_subscription**에 값 **1**을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-155">If the change will require the generation of a new snapshot, you must also specify a value of **1** for **\@force_invalidate_snapshot**, and if the change will require that Subscribers be reinitialized, you must specify a value of **1** for **\@force_reinit_subscription**.</span></span> <span data-ttu-id="8ba2c-156">변경된 경우 새 스냅샷 또는 다시 초기화가 필요한 속성에 대한 자세한 내용은 [게시 및 아티클 속성 변경](change-publication-and-article-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-156">For more information on the properties that, when changed, require a new snapshot or reinitialization, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
#### <a name="to-view-the-properties-of-a-merge-publication"></a><span data-ttu-id="8ba2c-157">병합 게시의 속성을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="8ba2c-157">To view the properties of a merge publication</span></span>  
  
1.  <span data-ttu-id="8ba2c-158">**\@publication** 매개 변수에 게시 이름을 지정하여 [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-158">Execute [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specifying the name of the publication for the **\@publication** parameter.</span></span> <span data-ttu-id="8ba2c-159">이 매개 변수를 지정하지 않으면 게시자에 있는 모든 게시에 대한 정보가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-159">If you do not specify this parameter, information on all publications at the Publisher is returned.</span></span>  
  
#### <a name="to-change-the-properties-of-a-merge-publication"></a><span data-ttu-id="8ba2c-160">병합 게시의 속성을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="8ba2c-160">To change the properties of a merge publication</span></span>  
  
1.  <span data-ttu-id="8ba2c-161">**\@property** 매개 변수에 변경할 게시 속성, **\@value** 매개 변수에 이 속성의 새 값을 지정하여 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-161">Execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying the publication property being changed in the **\@property** parameter and the new value of this property in the **\@value** parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8ba2c-162">변경 시 새 스냅샷을 생성해야 하는 경우 **\@force_invalidate_snapshot** 값도 **1**로 지정해야 합니다. 변경 시 구독자를 초기화해야 하는 경우 **\@force_reinit_subscription**에 값 **1**을 지정해야 합니다. 변경 시 새 스냅샷 또는 재초기화가 필요한 속성에 관한 자세한 내용은 [게시 및 아티클 속성 변경](change-publication-and-article-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-162">If the change will require the generation of a new snapshot, you must also specify a value of **1** for **\@force_invalidate_snapshot**, and if the change will require that Subscribers be reinitialized, you must specify a value of **1** for **\@force_reinit_subscription** For more information on the properties that, when changed, require a new snapshot or reinitialization, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
#### <a name="to-view-the-properties-of-a-snapshot"></a><span data-ttu-id="8ba2c-163">스냅샷의 속성을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="8ba2c-163">To view the properties of a snapshot</span></span>  
  
1.  <span data-ttu-id="8ba2c-164">**\@publication** 매개 변수에 게시 이름을 지정하여 [sp_helppublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-164">Execute [sp_helppublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql), specifying the name of the publication for the **\@publication** parameter.</span></span>  
  
#### <a name="to-change-the-properties-of-a-snapshot"></a><span data-ttu-id="8ba2c-165">스냅샷의 속성을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="8ba2c-165">To change the properties of a snapshot</span></span>  
  
1.  <span data-ttu-id="8ba2c-166">적절한 스냅샷 매개 변수에 하나 이상의 새 스냅샷 속성을 지정하여 [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-166">Execute [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql), specifying one or more of the new snapshot properties for the appropriate snapshot parameters.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="8ba2c-167">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8ba2c-167">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="8ba2c-168">다음 트랜잭션 복제 예에서는 게시 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-168">This transactional replication example returns the properties of the publication.</span></span>  
  
 [!code-sql[HowTo#sp_helppublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranpub.sql#sp_helppublication)]  
  
 <span data-ttu-id="8ba2c-169">다음 트랜잭션 복제 예에서는 게시에 대한 스키마 복제를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-169">This transactional replication example disables schema replication for the publication.</span></span>  
  
 [!code-sql[HowTo#sp_changepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranpub.sql#sp_changepublication)]  
  
 <span data-ttu-id="8ba2c-170">다음 병합 복제 예에서는 게시 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-170">This merge replication example returns the properties of the publication.</span></span>  
  
 [!code-sql[HowTo#sp_helpmergepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergepub.sql#sp_helpmergepublication)]  
  
 <span data-ttu-id="8ba2c-171">다음 병합 복제 예에서는 게시에 대한 스키마 복제를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-171">This merge replication example disables schema replication for the publication.</span></span>  
  
 [!code-sql[HowTo#sp_changemergepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergepub.sql#sp_changemergepublication)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="8ba2c-172">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="8ba2c-172">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="8ba2c-173">RMO(복제 관리 개체)를 사용하여 프로그래밍 방식으로 게시를 수정하고 해당 속성에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-173">You can modify publications and access their properties programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="8ba2c-174">게시 속성을 보거나 수정하는 데 사용되는 RMO 클래스는 게시의 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-174">The RMO classes that you use to view or modify publication properties depend on the type of publication.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-snapshot-or-transactional-publication"></a><span data-ttu-id="8ba2c-175">스냅샷 또는 트랜잭션 게시의 속성을 보거나 수정하려면</span><span class="sxs-lookup"><span data-stu-id="8ba2c-175">To view or modify properties of a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="8ba2c-176"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-176">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="8ba2c-177"><xref:Microsoft.SqlServer.Replication.TransPublication> 클래스의 인스턴스를 만들고 게시에 대한 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 및 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 속성을 설정한 다음, 1단계에서 만든 연결에 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-177">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPublication> class, set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
3.  <span data-ttu-id="8ba2c-178"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-178">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="8ba2c-179">이 메서드가 `false`를 반환하는 경우 2단계에서 게시 속성이 올바르게 정의되지 않았거나 게시가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-179">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="8ba2c-180">(옵션) 속성을 변경하려면 설정할 수 있는 한 개 이상의 속성에 대해 새 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-180">(Optional) To change properties, set a new value for one or more of the settable properties.</span></span> <span data-ttu-id="8ba2c-181">논리 AND 연산자(Microsoft Visual C#에서는 `&`, Microsoft Visual Basic에서는 `And`)를 사용하여 지정된 <xref:Microsoft.SqlServer.Replication.PublicationAttributes> 값이 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 속성에 대해 설정되어 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-181">Use the logical AND operator (`&` in Microsoft Visual C# and `And` in Microsoft Visual Basic) to determine if a given <xref:Microsoft.SqlServer.Replication.PublicationAttributes> value is set for the <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> property.</span></span> <span data-ttu-id="8ba2c-182">포함 논리 OR 연산자(Visual C#에서는 `|`, Visual Basic에서는 `Or`) 및 배타적 논리 OR 연산자(Visual C#에서는 `^`, Visual Basic에서는 `Xor`)를 사용하여 <xref:Microsoft.SqlServer.Replication.PublicationAttributes> 속성에 대한 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-182">Use the inclusive logical OR operator (`|` in Visual C# and `Or` in Visual Basic) and the exclusive logical OR operator (`^` in Visual C# and `Xor` in Visual Basic) to change the <xref:Microsoft.SqlServer.Replication.PublicationAttributes> values for the <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> property.</span></span>  
  
5.  <span data-ttu-id="8ba2c-183">(옵션) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>에 대해 `true` 값을 지정했으면 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 메서드를 호출하여 서버의 변경 내용을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-183">(Optional) If you specified a value of `true` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit changes on the server.</span></span> <span data-ttu-id="8ba2c-184"><xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>에 대해 `false` 값을 지정했으면(기본값) 변경 내용이 즉시 서버로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-184">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (the default), changes are sent to the server immediately.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-merge-publication"></a><span data-ttu-id="8ba2c-185">병합 게시의 속성을 보거나 수정하려면</span><span class="sxs-lookup"><span data-stu-id="8ba2c-185">To view or modify properties of a merge publication</span></span>  
  
1.  <span data-ttu-id="8ba2c-186"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-186">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="8ba2c-187"><xref:Microsoft.SqlServer.Replication.MergePublication> 클래스의 인스턴스를 만들고 게시에 대한 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 및 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 속성을 설정한 다음, 1단계에서 만든 연결에 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-187">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class, set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
3.  <span data-ttu-id="8ba2c-188"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-188">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="8ba2c-189">이 메서드가 `false`를 반환하는 경우 2단계에서 게시 속성이 올바르게 정의되지 않았거나 게시가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-189">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="8ba2c-190">(옵션) 속성을 변경하려면 설정할 수 있는 한 개 이상의 속성에 대해 새 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-190">(Optional) To change properties, set a new value for one or more of the settable properties.</span></span> <span data-ttu-id="8ba2c-191">논리 AND 연산자(Visual C#에서는 `&`, Visual Basic에서는 `And`)를 사용하여 지정된 <xref:Microsoft.SqlServer.Replication.PublicationAttributes> 값이 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 속성에 대해 설정되어 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-191">Use the logical AND operator (`&` in Visual C# and `And` in Visual Basic) to determine if a given <xref:Microsoft.SqlServer.Replication.PublicationAttributes> value is set for the <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> property.</span></span> <span data-ttu-id="8ba2c-192">포함 논리 OR 연산자(Visual C#에서는 `|`, Visual Basic에서는 `Or`) 및 배타적 논리 OR 연산자(Visual C#에서는 `^`, Visual Basic에서는 `Xor`)를 사용하여 <xref:Microsoft.SqlServer.Replication.PublicationAttributes> 속성에 대한 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-192">Use the inclusive logical OR operator (`|` in Visual C# and `Or` in Visual Basic) and the exclusive logical OR operator (`^` in Visual C# and `Xor` in Visual Basic) to change the <xref:Microsoft.SqlServer.Replication.PublicationAttributes> values for the <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> property.</span></span>  
  
5.  <span data-ttu-id="8ba2c-193">(옵션) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>에 대해 `true` 값을 지정했으면 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 메서드를 호출하여 서버의 변경 내용을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-193">(Optional) If you specified a value of `true` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit changes on the server.</span></span> <span data-ttu-id="8ba2c-194"><xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>에 대해 `false` 값을 지정했으면(기본값) 변경 내용이 즉시 서버로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-194">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (the default), changes are sent to the server immediately.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="8ba2c-195">예(RMO)</span><span class="sxs-lookup"><span data-stu-id="8ba2c-195">Examples (RMO)</span></span>  
 <span data-ttu-id="8ba2c-196">이 예에서는 트랜잭션 게시에 대한 게시 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-196">This example sets publication attributes for a transactional publication.</span></span> <span data-ttu-id="8ba2c-197">변경 내용은 명시적으로 서버로 전송될 때까지 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-197">The changes are cached until explicitly sent to the server.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeTranPub_cached](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changetranpub_cached)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeTranPub_cached](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changetranpub_cached)]  
  
 <span data-ttu-id="8ba2c-198">이 예에서는 병합 게시에 대한 DDL 복제를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba2c-198">This example disables DDL replication for a merge publication.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeMergePub_ddl](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changemergepub_ddl)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergePub_ddl](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changemergepub_ddl)]  
  
## <a name="see-also"></a><span data-ttu-id="8ba2c-199">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ba2c-199">See Also</span></span>  
 <span data-ttu-id="8ba2c-200">[데이터 및 데이터베이스 개체 게시](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="8ba2c-200">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="8ba2c-201">[게시 및 아티클 속성 변경](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="8ba2c-201">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="8ba2c-202">[게시 데이터베이스의 스키마 변경](make-schema-changes-on-publication-databases.md) </span><span class="sxs-lookup"><span data-stu-id="8ba2c-202">[Make Schema Changes on Publication Databases](make-schema-changes-on-publication-databases.md) </span></span>  
 <span data-ttu-id="8ba2c-203">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="8ba2c-203">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 <span data-ttu-id="8ba2c-204">[게시에 대 한 아티클 추가 및 삭제](add-articles-to-and-drop-articles-from-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="8ba2c-204">[Add Articles to and Drop Articles from a Publication](add-articles-to-and-drop-articles-from-a-publication.md) </span></span>  
 <span data-ttu-id="8ba2c-205">[복제 모니터를 사용하여 정보 보기 및 태스크 수행](../monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="8ba2c-205">[View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="8ba2c-206">아티클 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="8ba2c-206">View and Modify Article Properties</span></span>](view-and-modify-article-properties.md)  
  
  
