---
title: 배포자 속성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distdbproperties.f1
- sql12.rep.configdistwizard.distproperties.general.f1
- sql12.rep.configdistwizard.distproperties.publishers.f1
- sql12.rep.configdistwizard.distproperties.publishers.f1
ms.assetid: f643c7c3-f238-4835-b81e-2c2b3b53b23f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 501c7931d651498fea49749be38af374c02424ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646912"
---
# <a name="sql-server-replication-distributor-properties"></a><span data-ttu-id="714dd-102">SQL Server 복제 배포자 속성</span><span class="sxs-lookup"><span data-stu-id="714dd-102">SQL Server Replication Distributor Properties</span></span>
<span data-ttu-id="714dd-103">이 항목에서는 **배포자 속성** 창 내에서 **일반**, **게시자**및 **배포 데이터베이스** 페이지에 있는 속성에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-103">This topic discusses the properties found on the **General**, **Publishers**, and **Distribution Database** pages within the **Distributor Properties** window.</span></span> 

## <a name="general"></a><span data-ttu-id="714dd-104">일반</span><span class="sxs-lookup"><span data-stu-id="714dd-104">General</span></span>
  <span data-ttu-id="714dd-105">**배포자 속성** 의 **일반** 페이지에서 배포 데이터베이스를 추가 및 삭제하고 배포 데이터베이스 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-105">The **General** page of the **Distributor Properties** dialog box allows you to add and delete distribution databases and set distribution database properties.</span></span>  
  
 <span data-ttu-id="714dd-106">배포 데이터베이스는 모든 유형의 복제에 대한 메타데이터 및 기록 데이터와 트랜잭션 복제에 대한 트랜잭션을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-106">The distribution database stores metadata and history data for all types of replication, and transactions for transactional replication.</span></span> <span data-ttu-id="714dd-107">대부분의 경우 배포 데이터베이스는 하나면 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-107">In many cases, a single distribution database is sufficient.</span></span> <span data-ttu-id="714dd-108">그러나 여러 게시자가 단일 배포자를 사용하는 경우에는 각 게시자에 대해 배포 데이터베이스를 만들어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="714dd-108">But if multiple Publishers use a single Distributor, consider creating a distribution database for each Publisher.</span></span> <span data-ttu-id="714dd-109">이렇게 하면 각 배포 데이터베이스를 통한 데이터 흐름이 고유하게 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-109">Doing so ensures that the data flowing through each distribution database is distinct.</span></span>  
  
### <a name="options"></a><span data-ttu-id="714dd-110">옵션</span><span class="sxs-lookup"><span data-stu-id="714dd-110">Options</span></span>  
 <span data-ttu-id="714dd-111">**데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="714dd-111">**Databases**</span></span>  
 <span data-ttu-id="714dd-112">**데이터베이스** 속성 표는 배포자에 있는 배포 데이터베이스의 이름 및 보존 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-112">The **Databases** property grid shows the name and retention properties of the distribution databases on the Distributor.</span></span> <span data-ttu-id="714dd-113">**트랜잭션 보존** 은 트랜잭션 복제에 대해 트랜잭션을 저장하는 시간입니다. 트랜잭션 보존을 배포 보존이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-113">**Transaction Retention** is the length of time transactions are stored for transactional replication (transaction retention is also known as distribution retention).</span></span> <span data-ttu-id="714dd-114">**기록 보존** 은 모든 유형의 복제에 대해 기록 메타데이터를 저장하는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-114">**History Retention** is the length of time history metadata is stored for all types of replication.</span></span> <span data-ttu-id="714dd-115">배포 기간에 대한 자세한 내용은 [구독 만료 및 비활성화](subscription-expiration-and-deactivation.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="714dd-115">For more information about distribution retention, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
 <span data-ttu-id="714dd-116">**배포 데이터베이스 속성**대화 상자를 시작하려면 **데이터베이스** 속성 표의 속성 단추 ( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-116">Click the properties button (**...**) in the **Databases** property grid to launch the **Distribution Database Properties** dialog box.</span></span>  
  
 <span data-ttu-id="714dd-117">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="714dd-117">**New**</span></span>  
 <span data-ttu-id="714dd-118">새 배포 데이터베이스를 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-118">Click to create a new distribution database.</span></span>  
  
 <span data-ttu-id="714dd-119">**Delete**</span><span class="sxs-lookup"><span data-stu-id="714dd-119">**Delete**</span></span>  
 <span data-ttu-id="714dd-120">**데이터베이스** 속성 표에서 기존 배포 데이터베이스를 선택하고 **삭제** 를 클릭하여 데이터베이스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-120">Select an existing distribution database in the **Databases** property grid, and click **Delete** to delete the database.</span></span> <span data-ttu-id="714dd-121">배포 데이터베이스가 하나만 있는 경우 배포 데이터베이스를 삭제할 수 없습니다. 각 배포자에는 배포 데이터베이스가 최소한 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-121">You cannot delete the distribution database if there is only one such database; each Distributor must have at least one distribution database.</span></span> <span data-ttu-id="714dd-122">배포 데이터베이스를 모두 삭제하려면 컴퓨터에서 배포를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-122">To delete all distribution databases, you must disable distribution on the computer.</span></span> <span data-ttu-id="714dd-123">자세한 내용은 [게시 및 배포 해제](disable-publishing-and-distribution.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="714dd-123">For more information, see [Disable Publishing and Distribution](disable-publishing-and-distribution.md).</span></span>  
  
 <span data-ttu-id="714dd-124">**프로필 기본값**</span><span class="sxs-lookup"><span data-stu-id="714dd-124">**Profile Defaults**</span></span>  
 <span data-ttu-id="714dd-125">**에이전트 프로필** 대화 상자의 복제 에이전트 프로필에 액세스하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-125">Click to access replication agent profiles in the **Agent Profiles** dialog box.</span></span> <span data-ttu-id="714dd-126">프로필에 대한 자세한 내용은 [Replication Agent Profiles](agents/replication-agent-profiles.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="714dd-126">For more information about profiles, see [Replication Agent Profiles](agents/replication-agent-profiles.md).</span></span>  

## <a name="publishers"></a><span data-ttu-id="714dd-127">게시자</span><span class="sxs-lookup"><span data-stu-id="714dd-127">Publishers</span></span>

  <span data-ttu-id="714dd-128">**배포자 속성** 대화 상자의 **게시자** 페이지를 사용하여 게시자가 이 배포자를 사용하도록 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-128">The **Publishers** page of the **Distributor Properties** dialog box allows you to enable Publishers to use this Distributor.</span></span> <span data-ttu-id="714dd-129">해당 게시자와 연결된 속성을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-129">You can also set properties associated with those Publishers.</span></span> <span data-ttu-id="714dd-130">현재 서버를 원격 배포자로 사용하도록 게시자를 설정해도 해당 서버가 게시자가 되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-130">Be aware that enabling a Publisher to use this server as its remote Distributor does not make that server a Publisher.</span></span> <span data-ttu-id="714dd-131">게시자에 연결하여 이를 게시자로 구성하고, 이 서버를 배포자로 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-131">You must connect to the Publisher, configure it for publishing, and choose this server as the Distributor.</span></span> <span data-ttu-id="714dd-132">새 게시 마법사를 통해 게시자를 구성하고 배포자를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-132">You can configure the Publisher and choose a Distributor through the New Publication Wizard.</span></span>  
  
### <a name="options"></a><span data-ttu-id="714dd-133">옵션</span><span class="sxs-lookup"><span data-stu-id="714dd-133">Options</span></span>  
 <span data-ttu-id="714dd-134">**게시자**</span><span class="sxs-lookup"><span data-stu-id="714dd-134">**Publishers**</span></span>  
 <span data-ttu-id="714dd-135">이 배포자를 사용하도록 허용할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-135">Select the servers that are allowed to use this Distributor.</span></span> <span data-ttu-id="714dd-136">게시자 옆의 속성 단추 ( **...** )를 클릭하여 추가 속성을 보고 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-136">Click the Properties button **(...)** next to a Publisher to view and set additional properties.</span></span>  
  
 <span data-ttu-id="714dd-137">**추가**</span><span class="sxs-lookup"><span data-stu-id="714dd-137">**Add**</span></span>  
 <span data-ttu-id="714dd-138">허용할 서버가 나열되지 않으면 **추가**를 클릭하여 사용 가능한 게시자 목록에 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자 또는 Oracle 게시자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-138">If the server you want to allow is not listed, click **Add** to add a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher or Oracle Publisher to the list of available Publishers.</span></span> <span data-ttu-id="714dd-139">추가한 서버가 이 배포자를 원격 배포자로 사용하는 첫 번째 서버이면 관리 연결 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-139">If the server you add is the first server to use this Distributor as a remote Distributor, you are prompted to provide an administrative link password.</span></span>  
  
 <span data-ttu-id="714dd-140">**관리 연결 암호**</span><span class="sxs-lookup"><span data-stu-id="714dd-140">**Administrative link password**</span></span>  
 <span data-ttu-id="714dd-141">복제에서 **distributor_admin** 로그인을 사용하여 게시자와 원격 배포자 간에 구성하는 연결의 암호를 지정하거나 업데이트하려면 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-141">Use to specify or update the password for the connection replication makes between the Publisher and the remote Distributor using the **distributor_admin** login:</span></span>  
  
-   <span data-ttu-id="714dd-142">배포자가 로컬 배포자로만 사용되는 경우 이 암호는 임의로 생성되고 자동으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-142">If the Distributor serves only as a local Distributor, this password is randomly generated and automatically configured.</span></span>  
-   <span data-ttu-id="714dd-143">배포자에 원격 게시자가 있으면 이 페이지 또는 배포 구성 마법사의 **배포자 암호** 페이지에서 암호를 이미 입력한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-143">If the Distributor already has a remote Publisher, a password was initially supplied on this page or the **Distributor Password** page of the Configure Distribution Wizard.</span></span>    
-   <span data-ttu-id="714dd-144">이 배포자에 대해 원격 게시자를 처음으로 설정하는 경우 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-144">If you enable the first remote Publisher for this Distributor, you are prompted to enter a password.</span></span>  
  
 <span data-ttu-id="714dd-145">배포자 보안에 자세한 내용은 [배포자 보안 설정](security/secure-the-distributor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="714dd-145">For more information on security for Distributors, see [Secure the Distributor](security/secure-the-distributor.md).</span></span>  

## <a name="distribution-database"></a><span data-ttu-id="714dd-146">배포 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="714dd-146">Distribution Database</span></span>
 <span data-ttu-id="714dd-147">**배포 데이터베이스 속성** 대화 상자를 사용하여 많은 속성을 보고 데이터베이스의 트랜잭션 보존 기간과 기록 보존 기간을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-147">The **Distribution Database Properties** dialog box allows you to view a number of properties and to set the transaction retention period and history retention period for the database.</span></span>  
  
### <a name="options"></a><span data-ttu-id="714dd-148">옵션</span><span class="sxs-lookup"><span data-stu-id="714dd-148">Options</span></span>  
 <span data-ttu-id="714dd-149">**이름**</span><span class="sxs-lookup"><span data-stu-id="714dd-149">**Name**</span></span>  
 <span data-ttu-id="714dd-150">배포 데이터베이스의 이름으로 기본값은 'distribution'입니다(읽기 전용).</span><span class="sxs-lookup"><span data-stu-id="714dd-150">The name of the distribution database, which defaults to 'distribution' (read-only).</span></span>  
  
 <span data-ttu-id="714dd-151">**파일 위치**</span><span class="sxs-lookup"><span data-stu-id="714dd-151">**File locations**</span></span>  
 <span data-ttu-id="714dd-152">데이터베이스 파일과 로그 파일의 위치입니다(읽기 전용).</span><span class="sxs-lookup"><span data-stu-id="714dd-152">The location of the database file and the log file (read-only).</span></span>  
  
 <span data-ttu-id="714dd-153">**트랜잭션 보존 기간**</span><span class="sxs-lookup"><span data-stu-id="714dd-153">**Transaction retention period**</span></span>  
 <span data-ttu-id="714dd-154">배포 보존 기간이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-154">Also known as the distribution retention period.</span></span> <span data-ttu-id="714dd-155">트랜잭션 복제에서 트랜잭션이 저장되는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-155">The length of time transactions are stored for transactional replication.</span></span> <span data-ttu-id="714dd-156">자세한 내용은 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="714dd-156">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
 <span data-ttu-id="714dd-157">**기록 보존 기간**</span><span class="sxs-lookup"><span data-stu-id="714dd-157">**History retention period**</span></span>  
 <span data-ttu-id="714dd-158">모든 복제 유형에서 기록 메타데이터가 저장되는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-158">The length of time history metadata is stored for all types of replication.</span></span>  
  
 <span data-ttu-id="714dd-159">**큐 판독기 에이전트 보안**</span><span class="sxs-lookup"><span data-stu-id="714dd-159">**Queue Reader Agent security**</span></span>  
 <span data-ttu-id="714dd-160">큐 판독기 에이전트는 지연 업데이트 구독이 있는 트랜잭션 복제에서 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-160">The Queue Reader Agent is used by transactional replication with queued updating subscriptions.</span></span> <span data-ttu-id="714dd-161">새 게시 마법사의 **게시 유형** 페이지에서 **업데이트할 수 있는 구독이 있는 트랜잭션 게시** 를 선택하면 큐 판독기 에이전트가 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-161">A Queue Reader Agent is created automatically if you select **Transactional publication with updating subscriptions** on the **Publication Type** page of the New Publication Wizard.</span></span> <span data-ttu-id="714dd-162">**보안 설정...** 을 클릭하여 에이전트를 실행하고 배포자에 연결되는 계정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-162">Click **Security Settings...** to change the account under which the agent runs and makes connections to the Distributor.</span></span>  
  
 <span data-ttu-id="714dd-163">이 페이지에서 **큐 판독기 에이전트 만들기** 를 선택하여 큐 판독기 에이전트를 만들 수도 있습니다. 에이전트가 이미 생성된 경우에는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-163">A Queue Reader Agent can also be created by selecting **Create Queue Reader Agent** on this page (this option is disabled if the agent has already been created).</span></span>  
  
 <span data-ttu-id="714dd-164">큐 판독기 에이전트에 대한 추가 연결 정보는 다음 두 위치에서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-164">Additional connection information for the Queue Reader Agent is specified in two places:</span></span>    
-   <span data-ttu-id="714dd-165">에이전트는 **게시자 속성** 대화 상자에서 지정한 자격 증명을 사용하여 게시자에 연결합니다. 이 대화 상자는 **배포자 속성** 대화 상자의 **게시자** 페이지에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-165">The agent connects to the Publisher using the credentials specified in the **Publisher Properties** dialog box, which is available from the **Publishers** page of the **Distributor Properties** dialog box.</span></span>    
-   <span data-ttu-id="714dd-166">에이전트는 새 구독 마법사에서 배포 에이전트에 대해 지정된 자격 증명을 사용하여 구독자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="714dd-166">The agent connects to the Subscriber using the credentials specified for the Distribution Agent in the New Subscription Wizard.</span></span>  
  
 <span data-ttu-id="714dd-167">자세한 내용은 \\ [Replication Agent Security Model](security/replication-agent-security-model.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="714dd-167">For more information, see  \\[Replication Agent Security Model](security/replication-agent-security-model.md).</span></span> 

  
## <a name="see-also"></a><span data-ttu-id="714dd-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="714dd-168">See Also</span></span>  
 <span data-ttu-id="714dd-169">[배포 구성](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="714dd-169">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="714dd-170">배포자 및 게시자 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="714dd-170">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)   

  
  
