---
title: SQL Server 에이전트 서비스 시작, 중지 또는 일시 중지 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, starting
- SQL Server Agent, pausing
- SQL Server Agent, stopping
ms.assetid: c95a9759-dd30-4ab6-9ab0-087bb3bfb97c
author: stevestein
ms.author: sstein
ms.openlocfilehash: f2feb6a18c602271b1bec871fbfc9793979b100e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727888"
---
# <a name="start-stop-or-pause-the-sql-server-agent-service"></a><span data-ttu-id="1dacb-102">Start, Stop, or Pause the SQL Server Agent Service</span><span class="sxs-lookup"><span data-stu-id="1dacb-102">Start, Stop, or Pause the SQL Server Agent Service</span></span>
  <span data-ttu-id="1dacb-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 SQL Server 에이전트 서비스를 시작, 중지 또는 다시 시작하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1dacb-103">This topic describes how to start, stop, or restart the SQL Server Agent Service in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="1dacb-104">운영 체제 시작 시 자동으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스가 시작되도록 구성하거나 작업을 완료해야 할 때 수동으로 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dacb-104">You can configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service to start automatically when the operating system starts, or you can start it manually when you need to complete jobs.</span></span> <span data-ttu-id="1dacb-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스를 중지 또는 일시 중지하면 작업, 운영자 알림 및 경고를 일시 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dacb-105">You can stop or pause the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service to suspend jobs, operator notifications, and alerts.</span></span>  
  
 <span data-ttu-id="1dacb-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="1dacb-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1dacb-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="1dacb-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1dacb-108">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1dacb-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1dacb-109">보안</span><span class="sxs-lookup"><span data-stu-id="1dacb-109">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="1dacb-110">SQL Server Management Studio를 사용하여 SQL Server 에이전트 서비스를 시작, 중지 또는 다시 시작하려면</span><span class="sxs-lookup"><span data-stu-id="1dacb-110">To start, stop, or restart the SQL Server Agent Service using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1dacb-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="1dacb-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1dacb-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1dacb-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="1dacb-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트는 관리 작업을 자동화 하기 위해 서비스로 실행 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dacb-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be running as a service in order to automate administrative tasks.</span></span> <span data-ttu-id="1dacb-114">자세한 내용은 [Configure SQL Server Agent](configure-sql-server-agent.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dacb-114">For more information, see [Configure SQL Server Agent](configure-sql-server-agent.md).</span></span>  
  
-   <span data-ttu-id="1dacb-115">사용 권한이 있는 경우에만 개체 탐색기에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 노드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dacb-115">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1dacb-116">보안</span><span class="sxs-lookup"><span data-stu-id="1dacb-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1dacb-117">권한</span><span class="sxs-lookup"><span data-stu-id="1dacb-117">Permissions</span></span>  
 <span data-ttu-id="1dacb-118">해당 기능을 수행하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 **sysadmin** 고정 서버 역할 멤버인 계정의 자격 증명을 사용하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dacb-118">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1dacb-119">이 계정에는 다음과 같은 Windows 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1dacb-119">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="1dacb-120">서비스로 로그온(SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="1dacb-120">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="1dacb-121">프로세스 수준 토큰 바꾸기(SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="1dacb-121">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="1dacb-122">트래버스 검사 무시(SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="1dacb-122">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="1dacb-123">프로세스의 메모리 할당량 조정(SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="1dacb-123">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="1dacb-124">에이전트 서비스 계정에 필요한 Windows 사용 권한에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 에이전트 서비스에 대 한 계정 선택](select-an-account-for-the-sql-server-agent-service.md) 및 [Windows 서비스 계정 및 권한 구성](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1dacb-124">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1dacb-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="1dacb-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-start-stop-or-restart-the-sql-server-agent-service"></a><span data-ttu-id="1dacb-126">SQL Server 에이전트 서비스를 시작, 중지 또는 다시 시작하려면</span><span class="sxs-lookup"><span data-stu-id="1dacb-126">To start, stop, or restart the SQL Server Agent Service</span></span>  
  
1.  <span data-ttu-id="1dacb-127">**개체 탐색기**에서 더하기 기호를 클릭하여 SQL Server 에이전트 서비스를 관리할 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1dacb-127">In **Object Explorer**, click the plus sign to expand the server where you want to manage SQL Server Agent Service.</span></span>  
  
2.  <span data-ttu-id="1dacb-128">**SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭한 다음 **시작**, **중지**또는 **다시 시작**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1dacb-128">Right-click **SQL Server Agent**, and then select either **Start**, **Stop**, or **Restart**.</span></span>  
  
3.  <span data-ttu-id="1dacb-129">**사용자 계정 컨트롤** 대화 상자에서 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dacb-129">In the **User Account Control** dialog box, click **Yes**.</span></span>  
  
4.  <span data-ttu-id="1dacb-130">작업을 수행할지 묻는 메시지가 표시되면 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dacb-130">When prompted if you want to perform the action, click **Yes**.</span></span>  
  
 <span data-ttu-id="1dacb-131">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dacb-131">For more information, see:</span></span>  
  
-   [<span data-ttu-id="1dacb-132">데이터베이스 엔진, SQL Server 에이전트 또는 SQL Server Browser 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작</span><span class="sxs-lookup"><span data-stu-id="1dacb-132">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
-   [<span data-ttu-id="1dacb-133">SQL Server 에이전트 자동 시작&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1dacb-133">Autostart SQL Server Agent &#40;SQL Server Management Studio&#41;</span></span>](autostart-sql-server-agent-sql-server-management-studio.md)  
  
  
