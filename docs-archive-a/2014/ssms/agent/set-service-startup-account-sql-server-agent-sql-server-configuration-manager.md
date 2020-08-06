---
title: SQL Server 에이전트 (SQL Server 구성 관리자)에 대 한 서비스 시작 계정을 설정 합니다. Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- startup accounts [SQL Server]
- service startup accounts [SQL Server Agent]
ms.assetid: 46ffe818-ebb5-43a0-840b-923f219a2472
author: stevestein
ms.author: sstein
ms.openlocfilehash: 63e5ba7c24f1aa1a3f79f80e5ca28c02a0cd5812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731323"
---
# <a name="set-the-service-startup-account-for-sql-server-agent-sql-server-configuration-manager"></a><span data-ttu-id="e11e8-102">Set the Service Startup Account for SQL Server Agent (SQL Server Configuration Manager)</span><span class="sxs-lookup"><span data-stu-id="e11e8-102">Set the Service Startup Account for SQL Server Agent (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="e11e8-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 시작 계정은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 실행되는 Windows 계정과 해당 네트워크 권한을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service startup account defines the Windows account that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs as, as well as its network permissions.</span></span> <span data-ttu-id="e11e8-104">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 구성 관리자를 통해 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에이전트 서비스 계정을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-104">This topic describes how to set the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="e11e8-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="e11e8-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e11e8-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="e11e8-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e11e8-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="e11e8-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e11e8-108">보안</span><span class="sxs-lookup"><span data-stu-id="e11e8-108">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="e11e8-109">SQL Server Management Studio를 사용하여 SQL Server 에이전트에 대해 서비스 시작 계정을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="e11e8-109">To set the Service Startup Account for SQL Server Agent using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e11e8-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e11e8-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e11e8-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="e11e8-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e11e8-112">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]부터는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 시작 계정이 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Administrators 그룹의 멤버가 아니어도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-112">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent no longer requires that the service startup account be a member of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Administrators group.</span></span> <span data-ttu-id="e11e8-113">하지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 시작 계정은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sysadmin 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-113">However, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service startup account must be a member of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sysadmin fixed server role.</span></span> <span data-ttu-id="e11e8-114">다중 서버 작업 처리를 사용하려면 계정이 마스터 서버의 msdb 데이터베이스 역할인 TargetServersRole의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-114">The account must also be a member of the msdb database role TargetServersRole on the master server if multiserver job processing is used.</span></span>  
  
-   <span data-ttu-id="e11e8-115">사용 권한이 있는 경우에만 개체 탐색기에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 노드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-115">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e11e8-116">보안</span><span class="sxs-lookup"><span data-stu-id="e11e8-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e11e8-117">권한</span><span class="sxs-lookup"><span data-stu-id="e11e8-117">Permissions</span></span>  
 <span data-ttu-id="e11e8-118">해당 기능을 수행 하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sysadmin` 에서 고정 서버 역할의 멤버인 계정의 자격 증명을 사용 하도록 에이전트를 구성 해야 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e11e8-118">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the `sysadmin` fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e11e8-119">이 계정에는 다음과 같은 Windows 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-119">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="e11e8-120">서비스로 로그온(SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="e11e8-120">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="e11e8-121">프로세스 수준 토큰 바꾸기(SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="e11e8-121">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="e11e8-122">트래버스 검사 무시(SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="e11e8-122">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="e11e8-123">프로세스의 메모리 할당량 조정(SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="e11e8-123">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="e11e8-124">에이전트 서비스 계정에 필요한 Windows 사용 권한에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 에이전트 서비스에 대 한 계정 선택](select-an-account-for-the-sql-server-agent-service.md) 및 [Windows 서비스 계정 및 권한 구성](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e11e8-124">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e11e8-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="e11e8-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-the-service-startup-account-for-sql-server-agent"></a><span data-ttu-id="e11e8-126">SQL Server 에이전트에 대한 서비스 시작 계정을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="e11e8-126">To set the Service Startup Account for SQL Server Agent</span></span>  
  
1.  <span data-ttu-id="e11e8-127">**등록된 서버**에서 더하기 기호를 클릭하여 **데이터베이스 엔진**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-127">In **Registered Servers**, click the plus sign to expand **Database Engine**.</span></span>  
  
2.  <span data-ttu-id="e11e8-128">더하기 기호를 클릭하여 **로컬 서버 그룹** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-128">Click the plus sign to expand the **Local Server Groups** folder.</span></span>  
  
3.  <span data-ttu-id="e11e8-129">서비스 시작 계정을 설정하려는 서버 인스턴스를 마우스 오른쪽 단추로 클릭하고 **SQL Server 구성 관리자...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-129">Right-click the server instance where you want set up the Service Startup Account, and select **SQL Server Configuration Manager...**.</span></span>  
  
4.  <span data-ttu-id="e11e8-130">**사용자 계정 컨트롤** 대화 상자에서 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-130">In the **User Account Control** dialog box, click **Yes**.</span></span>  
  
5.  <span data-ttu-id="e11e8-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자의 콘솔 창에서 **SQL Server 서비스**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-131">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the console pane, select **SQL Server Services**.</span></span>  
  
6.  <span data-ttu-id="e11e8-132">세부 정보 창에서 **SQL Server 에이전트**_(server_name)_ 을 마우스 오른쪽 단추로 클릭 하 고, 여기서 *server_name* 은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 시작 계정을 변경 하려는 에이전트 인스턴스의 이름입니다. 그런 다음 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-132">In the details pane, right-click **SQL Server Agent**_(server_name)_, where *server_name* is the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent instance for which you want to change the service startup account, and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="e11e8-133">**SQL Server 에이전트**_(server_name)_ **속성** 대화 상자의 **로그온** 탭에 있는 다음 **계정으로 로그온**아래에서 다음 옵션 중 하나를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-133">In the **SQL Server Agent**_(server_name)_ **Properties** dialog box, in the **Log On** tab, select one of the following options under **Log on as**:</span></span>  
  
    -   <span data-ttu-id="e11e8-134">**기본 제공 계정**: 로컬 서버의 리소스만 작업에 필요한 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-134">**Built-in account**: select this option if your jobs require resources from the local server only.</span></span> <span data-ttu-id="e11e8-135">Windows 기본 제공 계정 유형을 선택하는 방법은 [SQL Server 에이전트 서비스에 대한 계정 선택](https://msdn.microsoft.com/library/ms191543.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e11e8-135">For information about how to choose a Windows built-in account type, see [Selecting an Account for SQL Server Agent Service.](https://msdn.microsoft.com/library/ms191543.aspx)</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="e11e8-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스는 \*\*\*\* 에서 로컬 서비스 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]계정을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-136">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service does not support the **Local Service** account in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
    -   <span data-ttu-id="e11e8-137">**이 계정**: 작업을 수행하는 데 애플리케이션 리소스를 포함하여 네트워크의 리소스가 필요할 경우나, 다른 Windows 애플리케이션 로그에 이벤트를 전달하거나, 전자 메일 또는 호출기로 운영자에게 알리려고 할 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-137">**This account**: select this option if your jobs require resources across the network, including application resources; if you want to forward events to other Windows application logs; or if you want to notify operators through e-mail or pagers.</span></span>  
  
         <span data-ttu-id="e11e8-138">이 옵션을 선택한 경우:</span><span class="sxs-lookup"><span data-stu-id="e11e8-138">If you select this option:</span></span>  
  
        1.  <span data-ttu-id="e11e8-139">**계정 이름** 상자에 SQL Server 에이전트를 실행하기 위해 사용할 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-139">In the **Account Name** box, enter the account that will be used to run SQL Server Agent.</span></span> <span data-ttu-id="e11e8-140">또는 **찾아보기** 를 클릭하여 **사용자 또는 그룹 선택** 대화 상자를 열고 사용할 계정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-140">Alternately, click **Browse** to open the **Select User or Group** dialog box and select the account to use.</span></span>  
  
        2.  <span data-ttu-id="e11e8-141">**암호** 상자에 계정 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-141">In the **Password** box, enter the password for the account.</span></span> <span data-ttu-id="e11e8-142">**암호 확인** 상자에 암호를 다시 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-142">Re-enter the password in the **Confirm password** box.</span></span>  
  
8.  <span data-ttu-id="e11e8-143">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-143">Click **OK**.</span></span>  
  
9. <span data-ttu-id="e11e8-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자에서 **닫기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e11e8-144">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, click the **Close** button.</span></span>  
  
  
