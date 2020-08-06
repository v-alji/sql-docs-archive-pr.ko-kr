---
title: 끌어오기 구독 속성 보기 및 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- modifying subscriptions
- viewing replication properties
- modifying replication properties, pull subscriptions
- pull subscriptions [SQL Server replication], modifying
- subscriptions [SQL Server replication], pull
- pull subscriptions [SQL Server replication], properties
- modifying subscriptions, SQL Server Management Studio
ms.assetid: 1601e54f-86f0-49e8-b023-87a5d1def033
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b847a22d31bbf3ea7540c55339fe27531134125
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646301"
---
# <a name="view-and-modify-pull-subscription-properties"></a><span data-ttu-id="9c553-102">끌어오기 구독 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="9c553-102">View and Modify Pull Subscription Properties</span></span>
  <span data-ttu-id="9c553-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 끌어오기 구독 속성을 보고 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-103">This topic describes how to view and modify pull subscription properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="9c553-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="9c553-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9c553-105">**끌어오기 구독 속성을 보고 수정하려면:**</span><span class="sxs-lookup"><span data-stu-id="9c553-105">**To view and modify pull subscription properties, using:**</span></span>  
  
     [<span data-ttu-id="9c553-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9c553-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9c553-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9c553-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="9c553-108">RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="9c553-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9c553-109">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="9c553-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="9c553-110">**구독 속성 - \<Publisher>: \<PublicationDatabase>** 대화 상자의 게시자 또는 구독자에서 끌어오기 구독 속성을 볼 수 있으며, 이 대화 상자는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-110">View pull subscription properties from the Publisher or the Subscriber in the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box, which is available from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="9c553-111">구독자에서 더 많은 속성을 볼 수 있으며 구독자에서 속성을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-111">More properties are visible from the Subscriber, and properties can be modified at the Subscriber.</span></span> <span data-ttu-id="9c553-112">복제 모니터에서 사용 가능한 **모든 구독** 탭의 게시자에서 속성을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-112">You can also view properties from the Publisher on the **All Subscriptions** tab, which is available in Replication Monitor.</span></span> <span data-ttu-id="9c553-113">복제 모니터를 시작하는 방법은 [복제 모니터 시작](monitor/start-the-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9c553-113">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span>  
  
#### <a name="to-view-pull-subscription-properties-from-the-publisher-in-management-studio"></a><span data-ttu-id="9c553-114">Management Studio의 게시자에서 끌어오기 구독 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="9c553-114">To view pull subscription properties from the Publisher in Management Studio</span></span>  
  
1.  <span data-ttu-id="9c553-115">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-115">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="9c553-116">**복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-116">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="9c553-117">해당 게시를 확장하고 구독을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-117">Expand the appropriate publication, right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="9c553-118">속성을 점검한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-118">View properties, and then click **OK**.</span></span>  
  
#### <a name="to-view-and-modify-pull-subscription-properties-from-the-subscriber-in-management-studio"></a><span data-ttu-id="9c553-119">Management Studio의 구독자에서 끌어오기 구독 속성을 보고 수정하려면</span><span class="sxs-lookup"><span data-stu-id="9c553-119">To view and modify pull subscription properties from the Subscriber in Management Studio</span></span>  
  
1.  <span data-ttu-id="9c553-120">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 구독자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-120">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="9c553-121">**복제** 폴더를 확장한 다음 **로컬 구독** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-121">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="9c553-122">해당 구독을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-122">Right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="9c553-123">필요한 경우 속성을 수정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-123">Modify any properties if necessary, and then click **OK**.</span></span>  
  
#### <a name="to-view-pull-subscription-properties-from-the-publisher-in-replication-monitor"></a><span data-ttu-id="9c553-124">복제 모니터의 게시자에서 끌어오기 구독 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="9c553-124">To view pull subscription properties from the Publisher in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="9c553-125">복제 모니터에서 왼쪽 창의 게시자 그룹을 확장하고 해당 게시자를 확장한 다음 해당 게시를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-125">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="9c553-126">**모든 구독** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-126">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="9c553-127">해당 구독을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-127">Right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="9c553-128">속성을 점검한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-128">View properties, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9c553-129">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="9c553-129">Using Transact-SQL</span></span>  
 <span data-ttu-id="9c553-130">끌어오기 구독은 수정할 수 있으며 속성은 복제 저장 프로시저를 사용하여 프로그래밍 방식으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-130">Pull subscriptions can be modified and their properties accessed programmatically using replication stored procedures.</span></span> <span data-ttu-id="9c553-131">사용되는 저장 프로시저는 구독이 속한 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-131">The stored procedures used depend on the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-view-the-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="9c553-132">스냅샷 또는 트랜잭션 게시에 대한 끌어오기 구독의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="9c553-132">To view the properties of a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="9c553-133">구독자에서 [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-133">At the Subscriber, execute [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql).</span></span> <span data-ttu-id="9c553-134">**@publisher**, **@publisher_db** 및를 지정 **@publication** 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-134">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span> <span data-ttu-id="9c553-135">이렇게 하면 구독자의 시스템 테이블에 저장된 구독에 대한 정보가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-135">This returns information about the subscription that is stored in system tables at the Subscriber.</span></span>  
  
2.  <span data-ttu-id="9c553-136">게시자에서 [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-136">At the Subscriber, execute [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql).</span></span> <span data-ttu-id="9c553-137">**@publisher**,, **@publisher_db** 를 지정 **@publication** 하 고에 다음 값 중 하나를 지정 합니다 **@publication_type** .</span><span class="sxs-lookup"><span data-stu-id="9c553-137">Specify **@publisher**, **@publisher_db**, **@publication**, and one of the following values for **@publication_type**:</span></span>  
  
    -   <span data-ttu-id="9c553-138">**0** - 구독이 트랜잭션 게시에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-138">**0** - Subscription belongs to a transactional publication.</span></span>  
  
    -   <span data-ttu-id="9c553-139">**1** - 구독이 스냅샷 게시에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-139">**1** - Subscription belongs to a snapshot publication.</span></span>  
  
3.  <span data-ttu-id="9c553-140">게시자에서 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-140">At the Publisher, execute [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span> <span data-ttu-id="9c553-141">**@publication**및를 지정 **@subscriber** 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-141">Specify **@publication** and **@subscriber**.</span></span>  
  
4.  <span data-ttu-id="9c553-142">게시자에서를 지정 하 여 [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)를 실행 **@subscriber** 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-142">At the Publisher, execute [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), specifying **@subscriber**.</span></span> <span data-ttu-id="9c553-143">이렇게 하면 구독자에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-143">This displays information about the Subscriber.</span></span>  
  
#### <a name="to-change-the-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="9c553-144">스냅샷 또는 트랜잭션 게시에 대한 끌어오기 구독의 속성을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="9c553-144">To change the properties of a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="9c553-145">구독자에서 [sp_change_subscription_properties](/sql/relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql)를 실행 하 고,,을 지정 하 고, **@publisher** **@publisher_db** **@publication** 에 대해 **0** (트랜잭션) 또는 **1** (스냅숏) 값을 지정 하 **@publication_type** 고, 구독 속성을로 변경 하 **@property** 고, 새 값을로 **@value** 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-145">At the Subscriber, execute [sp_change_subscription_properties](/sql/relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql), specifying **@publisher**, **@publisher_db**, **@publication**, a value of either **0** (transactional) or **1** (snapshot) for **@publication_type**, the subscription property being changed as **@property**, and the new value as **@value**.</span></span>  
  
2.  <span data-ttu-id="9c553-146">(옵션) 구독 데이터베이스의 구독자에서 [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-146">(Optional) At the Subscriber on the subscription database, execute [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql).</span></span> <span data-ttu-id="9c553-147">에 배포 에이전트 작업의 ID를 지정 **@jobid** 하 고 다음 DTS (데이터 변환 서비스) 패키지 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-147">Specify the ID of the Distribution Agent job for **@jobid**, and the following Data Transformation Services (DTS) package properties:</span></span>  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     <span data-ttu-id="9c553-148">이렇게 하면 구독의 DTS 패키지 속성이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-148">This changes the DTS package properties of a subscription.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9c553-149">작업 ID는 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)을 실행하여 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-149">The job ID can be obtained by executing [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span>  
  
#### <a name="to-view-the-properties-of-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="9c553-150">병합 게시에 대한 끌어오기 구독의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="9c553-150">To view the properties of a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="9c553-151">구독자에서 [sp_helpmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-151">At the Subscriber, execute [sp_helpmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="9c553-152">**@publisher**, **@publisher_db** 및를 지정 **@publication** 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-152">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span>  
  
2.  <span data-ttu-id="9c553-153">게시자에서 [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-153">At the Subscriber, execute [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql).</span></span> <span data-ttu-id="9c553-154">**@publisher**에, **@publisher_db** , **@publication** 및 값 2를 지정 **@publication_type** 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-154">Specify **@publisher**, **@publisher_db**, **@publication**, and a value of 2 for **@publication_type**.</span></span>  
  
3.  <span data-ttu-id="9c553-155">게시자에서 [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql) 을 실행하여 구독 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-155">At the Publisher, execute [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql) to display subscription information.</span></span> <span data-ttu-id="9c553-156">특정 구독에 대 한 정보를 반환 하려면 **@publication** , **@subscriber** 및에 대 한 **pull** 값을 지정 해야 합니다 **@subscription_type** .</span><span class="sxs-lookup"><span data-stu-id="9c553-156">To return information on a specific subscription, you must specify **@publication**, **@subscriber**, and a value of **pull** for **@subscription_type**.</span></span>  
  
4.  <span data-ttu-id="9c553-157">게시자에서를 지정 하 여 [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)를 실행 **@subscriber** 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-157">At the Publisher, execute [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), specifying **@subscriber**.</span></span> <span data-ttu-id="9c553-158">이렇게 하면 구독자에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-158">This displays information about the Subscriber.</span></span>  
  
#### <a name="to-change-the-properties-of-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="9c553-159">병합 게시에 대한 끌어오기 구독의 속성을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="9c553-159">To change the properties of a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="9c553-160">구독자에서 [sp_changemergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-160">At the Subscriber, execute [sp_changemergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql).</span></span> <span data-ttu-id="9c553-161">**@publication**, **@publisher** , **@publisher_db** , 변경 되는 구독 속성 **@property** , 새 값 **@value** 을로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-161">Specify **@publication**, **@publisher**, **@publisher_db**, the subscription property being changed as **@property**, and the new value as **@value**.</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="9c553-162">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="9c553-162">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="9c553-163">끌어오기 구독 속성을 보거나 수정하는 데 사용되는 RMO 클래스는 끌어오기 구독을 구독하는 게시 유형에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-163">The RMO classes you use to view or modify pull subscription properties depend on the type of publication to which the pull subscription is subscribed.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="9c553-164">스냅샷 또는 트랜잭션 게시에 대한 끌어오기 구독의 속성을 보거나 수정하려면</span><span class="sxs-lookup"><span data-stu-id="9c553-164">To view or modify properties of a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="9c553-165"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 구독자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-165">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="9c553-166"><xref:Microsoft.SqlServer.Replication.TransPullSubscription> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-166">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class.</span></span>  
  
3.  <span data-ttu-id="9c553-167"><xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>및 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-167">Set the <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="9c553-168"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성에 대해 1단계에서 만든 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-168">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="9c553-169"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-169">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="9c553-170">이 메서드가 `false`를 반환하는 경우 3단계에서 구독 속성이 잘못 정의되었거나 서버에 구독이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-170">If this method returns `false`, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist on the server.</span></span>  
  
6.  <span data-ttu-id="9c553-171">(옵션) 속성을 변경하려면 설정할 수 있는 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 속성 중 하나에 대해 새 값을 설정한 다음 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-171">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> properties that can be set, and then call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="9c553-172">(옵션) 새 설정을 보려면 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 메서드를 호출하여 아티클 속성을 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-172">(Optional) To view the new settings, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> method to reload the properties for the article.</span></span>  
  
8.  <span data-ttu-id="9c553-173">모든 연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-173">Close all connections.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="9c553-174">병합 게시에 대한 끌어오기 구독의 속성을 보거나 수정하려면</span><span class="sxs-lookup"><span data-stu-id="9c553-174">To view or modify properties of a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="9c553-175"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 구독자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-175">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="9c553-176"><xref:Microsoft.SqlServer.Replication.MergePullSubscription> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-176">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class.</span></span>  
  
3.  <span data-ttu-id="9c553-177"><xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>및 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-177">Set the <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="9c553-178"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성에 대해 1단계에서 만든 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-178">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="9c553-179"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-179">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="9c553-180">이 메서드가 `false`를 반환하는 경우 3단계에서 구독 속성이 잘못 정의되었거나 서버에 구독이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-180">If this method returns `false`, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist on the server.</span></span>  
  
6.  <span data-ttu-id="9c553-181">(옵션) 속성을 변경하려면 설정할 수 있는 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 속성 중 하나에 대해 새 값을 설정한 다음 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-181">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> properties that can be set, and then call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="9c553-182">(옵션) 새 설정을 보려면 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 메서드를 호출하여 아티클 속성을 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-182">(Optional) To view the new settings, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> method to reload the properties for the article.</span></span>  
  
8.  <span data-ttu-id="9c553-183">모든 연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="9c553-183">Close all connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c553-184">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9c553-184">See Also</span></span>  
 <span data-ttu-id="9c553-185">[복제 모니터를 사용하여 정보 보기 및 태스크 수행](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="9c553-185">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="9c553-186">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="9c553-186">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="9c553-187">게시 구독</span><span class="sxs-lookup"><span data-stu-id="9c553-187">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
