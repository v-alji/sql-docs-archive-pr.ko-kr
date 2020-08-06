---
title: '3단원: 배포 구성 | Microsoft 문서'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f248984a-0b59-4c2f-a56d-31f8dafe72b5
author: rothja
ms.author: jroth
ms.openlocfilehash: 52b284b6186e599b7afe73bd37ab0a8348ec38da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739700"
---
# <a name="lesson-3-configuring-distribution"></a><span data-ttu-id="107f0-102">3단원: 배포 구성</span><span class="sxs-lookup"><span data-stu-id="107f0-102">Lesson 3: Configuring Distribution</span></span>
  <span data-ttu-id="107f0-103">이 단원에서는 게시자에서 배포를 구성하고 게시 및 배포 데이터베이스에서 필수 사용 권한을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-103">In this lesson, you will configure distribution at the Publisher and set the required permissions on the publication and distribution databases.</span></span> <span data-ttu-id="107f0-104">배포자를 이미 구성한 경우 이 단원을 시작하기 전에 우선 게시와 배포를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-104">If you have already configured the Distributor, you must first disable publishing and distribution before you begin this lesson.</span></span> <span data-ttu-id="107f0-105">기존 복제 토폴로지를 유지해야 하는 경우에는 이 작업을 수행하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="107f0-105">Do not do this if you must retain an existing replication topology.</span></span>  
  
 <span data-ttu-id="107f0-106">원격 배포자를 사용한 게시자 구성은 이 자습서의 범위를 벗어납니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-106">Configuring a Publisher with a remote Distributor is outside the scope of this tutorial.</span></span>  
  
### <a name="configuring-distribution-at-the-publisher"></a><span data-ttu-id="107f0-107">게시자에서 배포 구성</span><span class="sxs-lookup"><span data-stu-id="107f0-107">Configuring distribution at the Publisher</span></span>  
  
1.  <span data-ttu-id="107f0-108">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-108">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="107f0-109">**복제** 폴더를 마우스 오른쪽 단추로 클릭한 다음 **배포 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-109">Right-click the **Replication** folder and click **Configure Distribution**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="107f0-110">실제 서버 이름이 아니라 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] localhost **를 사용하여** 에 연결한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 **'localhost'** 서버에 연결할 수 없다는 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-110">If you have connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using **localhost** rather than the actual server name you will be prompted with a warning that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is unable to connect to server **'localhost'**.</span></span> <span data-ttu-id="107f0-111">경고 대화 상자에서 **확인을** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-111">Click **OK** on the warning dialog.</span></span> <span data-ttu-id="107f0-112">**서버에 연결** 대화 상자에서 **서버 이름** 을 **localhost** 에서 실제 서버 이름으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-112">In the **Connect to Server** dialog change the **Server name** from **localhost** to the name of your server.</span></span> <span data-ttu-id="107f0-113">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-113">Click **Connect**.</span></span>  
  
     <span data-ttu-id="107f0-114">배포 구성 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-114">The Distribution Configuration Wizard launches.</span></span>  
  
3.  <span data-ttu-id="107f0-115">**배포자** 페이지에서 ' '을 (를 **)** _\<ServerName>_ **자체 배포자로 작동 합니다. 배포 데이터베이스와 로그를 만든 SQL Server** **다음을 클릭 합니다**.</span><span class="sxs-lookup"><span data-stu-id="107f0-115">On the **Distributor** page, select **'**_\<ServerName>_**' will act as its own Distributor; SQL Server will create a distribution database and log**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="107f0-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 실행되고 있지 않으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**에이전트 시작** 페이지에서 **예**를 선택하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스가 자동으로 시작되도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-116">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not running, on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**Agent Start** page, select **Yes**, configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service to start automatically.</span></span> <span data-ttu-id="107f0-117">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-117">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="107f0-118">**\\\\** \<_Machine_Name> **스냅숏 폴더** 텍스트 상자에 _**\repldata** 를 입력 하 고, 여기서 \<*Machine_Name> \*은 게시자의 이름이 며 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-118">Enter **\\\\**\<_Machine_Name>_**\repldata** in the **Snapshot folder** text box, where \<*Machine_Name>\* is the name of the Publisher, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="107f0-119">마법사의 나머지 페이지에 기본값을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-119">Accept the default values on the remaining pages of the wizard.</span></span>  
  
7.  <span data-ttu-id="107f0-120">**마침** 을 클릭하여 배포를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-120">Click **Finish** to enable distribution.</span></span>  
  
### <a name="setting-database-permissions-at-the-publisher"></a><span data-ttu-id="107f0-121">게시자에서 데이터베이스 권한 설정</span><span class="sxs-lookup"><span data-stu-id="107f0-121">Setting database permissions at the Publisher</span></span>  
  
1.  <span data-ttu-id="107f0-122">에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **보안**을 확장 하 고 **로그인**을 마우스 오른쪽 단추로 클릭 한 다음 **새 로그인**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand **Security**, right-click **Logins**, and then select **New Login**.</span></span>  
  
2.  <span data-ttu-id="107f0-123">**일반** 페이지에서 **검색**을 클릭 하 고 \<_Machine_Name> **선택할 개체 이름을 입력 하십시오** . 상자에 _**\ repl_snapshot** 를 입력 한 \<*Machine_Name> 다음 **이름 확인**을 클릭 하 고 **확인**을 클릭 합니다. 여기서 \*은 로컬 게시자 서버의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-123">On the **General** page, click **Search**, enter \<_Machine_Name>_**\repl_snapshot** in the **Enter the object name to select** box, where \<*Machine_Name>\* is the name of the local Publisher server, click **Check Names**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="107f0-124">**사용자 매핑** 페이지의 **이 로그인으로 매핑된 사용자** 목록에서 **배포** 및 데이터베이스를 모두 선택 합니다 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="107f0-124">On the **User Mapping** page, in the **Users mapped to this login** list select both the **distribution** and [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] databases.</span></span>  
  
     <span data-ttu-id="107f0-125">**데이터베이스 역할 멤버 자격** 목록에서 `db_owner` 두 데이터베이스의 로그인에 대 한 역할을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-125">In the **Database role membership** list select the `db_owner` role for the login for both databases.</span></span>  
  
4.  <span data-ttu-id="107f0-126">**확인** 을 클릭하여 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-126">Click **OK** to create the login.</span></span>  
  
5.  <span data-ttu-id="107f0-127">1-4단계를 반복하여 로컬 repl_logreader 계정에 대한 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-127">Repeat steps 1-4 to create a login for the local repl_logreader account.</span></span> <span data-ttu-id="107f0-128">이 로그인은 `db_owner` **배포** 및 **AdventureWorks** 데이터베이스에서 고정 데이터베이스 역할의 멤버인 사용자 에게도 매핑되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-128">This login must also be mapped to users that are members of the `db_owner` fixed database role in the **distribution** and **AdventureWorks** databases.</span></span>  
  
6.  <span data-ttu-id="107f0-129">1-4단계를 반복하여 로컬 repl_distribution 계정에 대한 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-129">Repeat steps 1-4 to create a login for the local repl_distribution account.</span></span> <span data-ttu-id="107f0-130">이 로그인은 `db_owner` **배포** 데이터베이스에서 고정 데이터베이스 역할의 멤버인 사용자에 게 매핑되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-130">This login must be mapped to a user that is a member of the `db_owner` fixed database role in the **distribution** database.</span></span>  
  
7.  <span data-ttu-id="107f0-131">1-4단계를 반복하여 로컬 repl_merge 계정에 대한 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-131">Repeat steps 1-4 to create a login for the local repl_merge account.</span></span> <span data-ttu-id="107f0-132">이 로그인에는 **배포** 와 **AdventureWorks** 데이터베이스의 사용자 매핑이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="107f0-132">This login must have user mappings in the **distribution** and **AdventureWorks** databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="107f0-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="107f0-133">See Also</span></span>  
 <span data-ttu-id="107f0-134">[배포 구성](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="107f0-134">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="107f0-135">복제 에이전트 보안 모델</span><span class="sxs-lookup"><span data-stu-id="107f0-135">Replication Agent Security Model</span></span>](security/replication-agent-security-model.md)  
  
  
