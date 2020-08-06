---
title: SQL Server (SQL Server 구성 관리자)에서 사용 하는 계정의 암호 변경 | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- expired password [SQL Server], SQL Server Agent
- passwords [SQL Server], SQL Server Agent service
- passwords [SQL Server], changing
- expired password [SQL Server], Database Engine
- passwords [SQL Server], SQL Server service
- Database Engine [SQL Server], passwords
- changing passwords used by SQL Server
- modifying passwords
ms.assetid: 5b6dcc03-6cae-45d3-acef-6f85ca6d615f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7da2b5f60187d7e3060dc6616686c493c893c21d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742576"
---
# <a name="change-the-password-of-the-accounts-used-by-sql-server-sql-server-configuration-manager"></a><span data-ttu-id="a946d-102">SQL Server에서 사용하는 계정의 암호 변경(SQL Server 구성 관리자)</span><span class="sxs-lookup"><span data-stu-id="a946d-102">Change the Password of the Accounts Used by SQL Server (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="a946d-103">이 항목에서는 SQL Server 구성 관리자를 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에이전트에 사용되는 계정의 암호를 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-103">This topic describes how to change the password of the accounts used by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="a946d-104">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트는 설치 중에 처음 제공된 자격 증명을 사용하여 컴퓨터에서 서비스로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-104">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent run on a computer as a service using credentials that are initially provided during setup.</span></span> <span data-ttu-id="a946d-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 도메인 계정으로 실행되고 있으며 해당 계정의 암호가 변경된 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 사용하는 암호를 새 암호로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-105">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running under a domain account and the password for that account is changed, the password used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be updated to the new password.</span></span> <span data-ttu-id="a946d-106">암호를 업데이트하지 않으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 일부 도메인 리소스에 액세스하지 못할 수 있으며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 중지되면 암호를 업데이트할 때까지 서비스가 다시 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-106">If the password is not updated, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may lose access to some domain resources and if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stops, the service will not restart until the password is updated.</span></span>  
  
 <span data-ttu-id="a946d-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 암호를 변경하려면 [암호 만료](../password-expired.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a946d-107">To change [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication passwords, see [Password Expired](../password-expired.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a946d-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="a946d-108">Before You Begin</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a946d-109">구성 관리자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스의 설정을 변경하도록 디자인 되고 권한이 부여된 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-109">Configuration Manager is the tool designed and authorized to change the settings of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.</span></span> <span data-ttu-id="a946d-110">Windows 서비스 제어 관리자( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.msc **) 애플리케이션을 사용하여**서비스를 변경하면 일부 필수 설정은 변경되지 않으며 서비스가 제대로 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-110">Changing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service by using the Windows Service Control Manager (**services.msc**) application does not always change all of the necessary settings and might prevent the service from functioning properly.</span></span> <span data-ttu-id="a946d-111">그러나 클러스터형 환경에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 액티브 노드의 암호를 변경한 후에는 서비스 제어 관리자를 사용하여 패시브 노드의 암호를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-111">However, in a clustered environment, after changing the password on the active node by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, you must change the password on the passive node by using the Service Control Manager.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a946d-112">보안</span><span class="sxs-lookup"><span data-stu-id="a946d-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a946d-113">권한</span><span class="sxs-lookup"><span data-stu-id="a946d-113">Permissions</span></span>  
 <span data-ttu-id="a946d-114">서비스에 사용되는 암호를 변경하려면 컴퓨터의 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-114">You must be an administrator of the computer to change the password used by a service.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a946d-115">SQL Server 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="a946d-115">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-change-the-password-used-by-the-sql-server-database-engine-service"></a><span data-ttu-id="a946d-116">SQL Server(데이터베이스 엔진) 서비스에 사용되는 암호를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="a946d-116">To change the password used by the SQL Server (Database Engine) service</span></span>  
  
1.  <span data-ttu-id="a946d-117">**시작** 단추를 클릭하고 **모든 프로그램**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-117">Click the **Start** button, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a946d-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자는 독립 실행형 프로그램이 아니라 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console 프로그램용 스냅인이므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자는 최신 버전의 Windows에서 애플리케이션으로 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-118">Because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager is a snap-in for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console program and not a stand-alone program, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager does not appear as an application in newer versions of Windows.</span></span>  
    >   
    >  -   <span data-ttu-id="a946d-119">**Windows 10**:</span><span class="sxs-lookup"><span data-stu-id="a946d-119">**Windows 10**:</span></span>  
    >          <span data-ttu-id="a946d-120">Configuration Manager를 열려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **시작 페이지**에서 sqlservermanager12.msc (의 경우)를 입력 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-120">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager12.msc (for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]).</span></span> <span data-ttu-id="a946d-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이전 버전의 경우 12를 더 작은 수로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-121">For previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replace 12 with a smaller number.</span></span> <span data-ttu-id="a946d-122">SQLServerManager12.msc를 클릭하면 구성 관리자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-122">Clicking SQLServerManager12.msc opens the Configuration Manager.</span></span> <span data-ttu-id="a946d-123">Configuration Manager를 시작 페이지나 작업 표시줄에 고정 하려면 Sqlservermanager12.msc를 마우스 오른쪽 단추로 클릭 한 다음 **파일 위치 열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-123">To pin the Configuration Manager to the Start Page or Task Bar, right-click SQLServerManager12.msc, and then click **Open file location**.</span></span> <span data-ttu-id="a946d-124">Windows 파일 탐색기에서 Sqlservermanager12.msc를 마우스 오른쪽 단추로 클릭 한 다음 **시작 화면에 고정** 또는 **작업 표시줄에 고정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-124">In the Windows File Explorer, right-click SQLServerManager12.msc, and then click **Pin to Start** or **Pin to taskbar**.</span></span>  
    > -   <span data-ttu-id="a946d-125">**Windows 8**:</span><span class="sxs-lookup"><span data-stu-id="a946d-125">**Windows 8**:</span></span>  
    >          <span data-ttu-id="a946d-126">Configuration Manager를 열려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **검색** 참의 **앱**아래에 \*\*SQLServerManager \<version> \*\* 를 입력 한 `SQLServerManager12.msc` 다음 **enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-126">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager\<version>.msc** such as `SQLServerManager12.msc`, and then press **Enter**.</span></span>  
  
2.  <span data-ttu-id="a946d-127">SQL Server 구성 관리자에서 **SQL Server 서비스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-127">In SQL Server Configuration Manager, click **SQL Server Services**.</span></span>  
  
3.  <span data-ttu-id="a946d-128">세부 정보 창에서 **SQL Server(** \<instancename> **)** 를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-128">In the details pane, right-click **SQL Server (**\<instancename>**)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="a946d-129">**SQL Server(** \<instancename> **) 속성** 대화 상자의 [로그온] 탭에서 **계정 이름** 상자에 나열된 계정에 대한 새 암호를 **암호** 및 **암호 확인** 상자에 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-129">In the **SQL Server (**\<instancename>**) Properties** dialog box, on the Log On tab, for the account listed in the **Account Name** box, type the new password in the **Password** and **Confirm Password** boxes, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a946d-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 다시 시작하지 않아도 암호가 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-130">The password takes effect immediately, without restarting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="to-change-the-password-used-by-the-sql-server-agent-service"></a><span data-ttu-id="a946d-131">SQL Server 에이전트 서비스에 사용되는 암호를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="a946d-131">To change the password used by the SQL Server Agent service</span></span>  
  
1.  <span data-ttu-id="a946d-132">**시작** 단추를 클릭하고 **모든 프로그램**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-132">Click the **Start** button, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="a946d-133">SQL Server 구성 관리자에서 **SQL Server 서비스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-133">In SQL Server Configuration Manager, click **SQL Server Services**.</span></span>  
  
3.  <span data-ttu-id="a946d-134">세부 정보 창에서 **SQL Server 에이전트(** \<instancename> **)** 를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-134">In the details pane, right-click **SQL Server Agent (**\<instancename>**)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="a946d-135">**SQL Server 에이전트(** \<instancename> **) 속성** 대화 상자의 [로그온] 탭에서 **계정 이름** 상자에 나열된 계정에 대한 새 암호를 **암호** 및 **암호 확인** 상자에 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-135">In the **SQL Server Agent (**\<instancename>**) Properties** dialog box, on the Log On tab, for the account listed in the **Account Name** box, type the new password in the **Password** and **Confirm Password** boxes, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a946d-136">독립 실행형 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 다시 시작하지 않아도 암호가 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-136">On a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the password takes effect immediately, without restarting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a946d-137">클러스터형 인스턴스에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 리소스를 오프라인 상태로 만들 수 있으므로 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a946d-137">On a clustered instance, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might take the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource offline, and require a restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a946d-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a946d-138">See Also</span></span>  
 [<span data-ttu-id="a946d-139">서비스 관리 방법 도움말 항목&#40;SQL Server 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="a946d-139">Managing Services How-to Topics &#40;SQL Server Configuration Manager&#41;</span></span>](../managing-services-how-to-topics-sql-server-configuration-manager.md)  
  
  
