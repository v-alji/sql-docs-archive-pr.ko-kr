---
title: 게시자 속성 SQL Server 복제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distpubproperties.f1
- sql12.rep.configdistwizard.pubproperties.general.f1
- sql12.rep.configdistwizard.pubproperties.pubdb.f1
- sql12.rep.configdistwizard.pubproperties.subscribers.f1
ms.assetid: 98df1aea-0406-40bf-a917-4bd80464125c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f3e14f82e855cc29f83859d85dfdaaf85a1bda37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732572"
---
# <a name="sql-server-replication-publisher-properties"></a><span data-ttu-id="1858b-102">게시자 속성 SQL Server 복제</span><span class="sxs-lookup"><span data-stu-id="1858b-102">SQL Server Replication Publisher Properties</span></span>
  <span data-ttu-id="1858b-103">이 섹션에서는 배포자 및 게시자에서 사용할 수 있는 게시자 속성에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-103">This section contains information on Publisher properties available at the Distributor and the Publisher.</span></span> 

## <a name="general"></a><span data-ttu-id="1858b-104">일반</span><span class="sxs-lookup"><span data-stu-id="1858b-104">General</span></span>  
  <span data-ttu-id="1858b-105">**게시자 속성** 대화 상자의 **일반** 페이지는 게시자가 사용하는 배포자 및 배포 데이터베이스에 대한 읽기 전용 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-105">The **General** page of the **Publisher Properties** dialog box displays read-only information on the Distributor and distribution database that the Publisher uses.</span></span> <span data-ttu-id="1858b-106">게시자에 대한 배포자 또는 배포 데이터베이스를 변경하려면 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="1858b-106">To change the Distributor or distribution database for a Publisher:</span></span>  
  
1.  <span data-ttu-id="1858b-107">게시자에서 게시를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-107">Disable publishing on the Publisher.</span></span> <span data-ttu-id="1858b-108">자세한 내용은 [게시 및 배포 해제](disable-publishing-and-distribution.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1858b-108">For more information, see [Disable Publishing and Distribution](disable-publishing-and-distribution.md).</span></span>    
2.  <span data-ttu-id="1858b-109">게시 및 배포를 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-109">Reconfigure publishing and distribution.</span></span> <span data-ttu-id="1858b-110">자세한 내용은 [Configure Publishing and Distribution](configure-publishing-and-distribution.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1858b-110">For more information, see [Configure Publishing and Distribution](configure-publishing-and-distribution.md).</span></span>  

## <a name="distributor"></a><span data-ttu-id="1858b-111">배포자</span><span class="sxs-lookup"><span data-stu-id="1858b-111">Distributor</span></span>
  <span data-ttu-id="1858b-112">**게시자 속성** 대화 상자를 사용하여 게시자와 이 게시자의 배포자 간 관계와 연결된 속성을 보고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-112">The **Publisher Properties** dialog box allows you to view and modify properties associated with the relationship between the Publisher and its Distributor.</span></span>  
  
### <a name="options"></a><span data-ttu-id="1858b-113">옵션</span><span class="sxs-lookup"><span data-stu-id="1858b-113">Options</span></span>  
 <span data-ttu-id="1858b-114">**에이전트에서 게시자 연결**</span><span class="sxs-lookup"><span data-stu-id="1858b-114">**Agent Connection to the Publisher**</span></span>  
 <span data-ttu-id="1858b-115">다음 에이전트가 배포자에서 게시자로 연결하는 컨텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-115">Specify the context under which the following agents make connections from the Distributor to the Publisher:</span></span>  
  
-   <span data-ttu-id="1858b-116">지연 업데이트 구독을 허용하는 트랜잭션 게시에 대한 큐 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="1858b-116">The Queue Reader Agent for transactional publications that allow queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="1858b-117">Oracle 게시에 대한 스냅샷 에이전트 및 로그 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="1858b-117">The Snapshot Agent and Log Reader Agent for Oracle publications.</span></span>  
  
 <span data-ttu-id="1858b-118">이러한 에이전트가 실행되는 **Windows 계정의 컨텍스트를 사용하여 게시자에 연결하거나** SQL Server 인증 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 을 지정한 다음 **로그인**및 **암호** 에 값을 입력하려면 **에이전트 프로세스 계정 가장**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-118">Select **Impersonate agent process account** to make connections to the Publisher using the context of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which these agents run, or specify **SQL Server Authentication**, and then enter a value for **Login** and **Password**.</span></span> <span data-ttu-id="1858b-119">**에이전트 프로세스 계정 가장**을 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-119">It is recommended that you select **Impersonate agent process account**.</span></span> <span data-ttu-id="1858b-120">에이전트 보안에 대한 자세한 내용은 [복제 에이전트 보안 모델](security/replication-agent-security-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1858b-120">For more information on agent security, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
 <span data-ttu-id="1858b-121">이러한 에이전트가 실행되는 Windows 계정은 새 게시 마법사에서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-121">The Windows accounts under which these agents run are specified in the New Publication Wizard.</span></span> <span data-ttu-id="1858b-122">이 계정은 다음 대화 상자에서 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-122">These accounts can be changed:</span></span>  
  
-   <span data-ttu-id="1858b-123">큐 판독기 에이전트의 **배포자 속성** 대화 상자</span><span class="sxs-lookup"><span data-stu-id="1858b-123">In the **Distributor Properties** dialog box for the Queue Reader Agent.</span></span>  
  
-   <span data-ttu-id="1858b-124">스냅샷 에이전트 및 로그 판독기 에이전트의 **게시 속성** 대화 상자</span><span class="sxs-lookup"><span data-stu-id="1858b-124">In the **Publication Properties** dialog box for the Snapshot Agent and Log Reader Agent.</span></span>  
  
 <span data-ttu-id="1858b-125">**기타**</span><span class="sxs-lookup"><span data-stu-id="1858b-125">**Miscellaneous**</span></span>  
 <span data-ttu-id="1858b-126">**게시자 유형** 및 **배포 데이터베이스 이름** 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-126">The properties **Publisher Type** and **Distribution Database Name** are read-only.</span></span> <span data-ttu-id="1858b-127">**기본 스냅샷 폴더** 속성은 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-127">The property **Default Snapshot Folder** can be changed.</span></span> <span data-ttu-id="1858b-128">스냅샷 폴더에 대한 자세한 내용은 [스냅샷 폴더 보안 설정](security/secure-the-snapshot-folder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1858b-128">For more information about the snapshot folder, see [Secure the Snapshot Folder](security/secure-the-snapshot-folder.md).</span></span>  
  

## <a name="publication-databases"></a><span data-ttu-id="1858b-129">게시 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="1858b-129">Publication Databases</span></span>
  <span data-ttu-id="1858b-130">**게시자 속성** 대화 상자의 **게시 데이터베이스** 페이지를 사용하여 **sysadmin** 고정 서버 역할의 사용자가 복제용 데이터베이스를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-130">The **Publication Databases** page of the **Publisher Properties** dialog box allows a user in the **sysadmin** fixed server role to enable databases for replication.</span></span> <span data-ttu-id="1858b-131">데이터베이스를 설정한다고 해서 그 데이터베이스가 게시되는 것은 아닙니다. 데이터베이스를 설정하면 설정된 데이터베이스에 대한 **db_owner** 고정 데이터베이스 역할의 사용자가 그 데이터베이스에 하나 이상의 게시를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-131">Enabling a database does not publish that database; rather, it allows any user in the **db_owner** fixed database role for that database to create one or more publications on the database.</span></span>  
  
### <a name="options"></a><span data-ttu-id="1858b-132">옵션</span><span class="sxs-lookup"><span data-stu-id="1858b-132">Options</span></span>  
 <span data-ttu-id="1858b-133">**트랜잭션**</span><span class="sxs-lookup"><span data-stu-id="1858b-133">**Transactional**</span></span>  
 <span data-ttu-id="1858b-134">**db_owner** 고정 데이터베이스 역할의 사용자가 데이터베이스에 스냅샷 게시 또는 트랜잭션 게시를 만들 수 있게 하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-134">Select this check box to allow users in the **db_owner** fixed database role to create snapshot publications or transactional publications in the database.</span></span> 
  
 <span data-ttu-id="1858b-135">**병합**</span><span class="sxs-lookup"><span data-stu-id="1858b-135">**Merge**</span></span>  
 <span data-ttu-id="1858b-136">**db_owner** 고정 데이터베이스 역할의 사용자가 데이터베이스에 병합 게시를 만들 수 있게 하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-136">Select this check box to allow users in the **db_owner** fixed database role to create merge publications in the database.</span></span>  

## <a name="subscribers"></a><span data-ttu-id="1858b-137">게시자 속성</span><span class="sxs-lookup"><span data-stu-id="1858b-137">Subscribers</span></span>

  <span data-ttu-id="1858b-138">**게시자 속성** 대화 상자의 **구독자** 페이지는  이전 버전의 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행하는 게시자에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-138">The **Subscribers** page of the **Publisher Properties** dialog box is used for Publishers running versions of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="1858b-139">이 페이지를 사용하여 구독자가 이 게시자의 게시에서 데이터를 받도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-139">The page allows you to enable Subscribers to receive data from publications on this Publisher.</span></span> <span data-ttu-id="1858b-140">구독자가 이 게시자에서 데이터를 받도록 설정해도 이 게시자의 게시에 대한 구독이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-140">Enabling a Subscriber to receive data from this Publisher does not create subscriptions to publications on this Publisher.</span></span> <span data-ttu-id="1858b-141">구독을 만들려면 새 구독 마법사를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-141">To create a subscription, you must use the New Subscription Wizard.</span></span>  
  
### <a name="options"></a><span data-ttu-id="1858b-142">옵션</span><span class="sxs-lookup"><span data-stu-id="1858b-142">Options</span></span>  
 <span data-ttu-id="1858b-143">**게시자 속성**</span><span class="sxs-lookup"><span data-stu-id="1858b-143">**Subscribers**</span></span>  
 <span data-ttu-id="1858b-144">**구독자** 속성 표에서는 이 게시자의 게시에서 데이터를 받도록 설정된 구독자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-144">The **Subscribers** property grid shows Subscribers that are enabled to receive data from publications on this Publisher.</span></span> <span data-ttu-id="1858b-145">추가 속성을 보고 설정하려면 구독자 옆에 있는 속성 단추 (**...**)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-145">Click the properties button (**...**) next to a Subscriber to view and set additional properties.</span></span>  
  
 <span data-ttu-id="1858b-146">**추가**</span><span class="sxs-lookup"><span data-stu-id="1858b-146">**Add**</span></span>  
 <span data-ttu-id="1858b-147">구독자를 추가하려면 **추가** 를 클릭한 다음 **SQL Server 구독자 추가** 또는 **SQL Server 이외 구독자 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1858b-147">Click **Add** to add a Subscriber, and then click **Add SQL Server Subscriber** or **Add Non-SQL Server Subscriber**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="1858b-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1858b-148">See Also</span></span>  
 [<span data-ttu-id="1858b-149">배포자 및 게시자 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="1858b-149">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)   

  
  
