---
title: SQL Server 에이전트 서비스 (SQL Server Management Studio)의 SQL Server 별칭을 설정 합니다. Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- aliases [SQL Server], creating
- SQL Server Agent, aliases
ms.assetid: 02d6295d-ab52-44f0-8f1b-f3910a507d8f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b178d91a47d907b182ef7962b98c7f22d4454094
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646615"
---
# <a name="set-a-sql-server-alias-for-the-sql-server-agent-service-sql-server-management-studio"></a><span data-ttu-id="4596d-102">Set a SQL Server Alias for the SQL Server Agent Service (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4596d-102">Set a SQL Server Alias for the SQL Server Agent Service (SQL Server Management Studio)</span></span>
  <span data-ttu-id="4596d-103">이 항목에서는를 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 사용 하 여 에이전트에서에 연결 하는 데 사용할 별칭 [!INCLUDE[ssDE](../includes/ssde-md.md)] 을 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 설정 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4596d-103">This topic describes how to set a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] alias for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent to use to connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="4596d-104">기본적으로 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 서비스는 추가 클라이언트 구성이 필요 없는 동적 서버 이름을 사용하여 명명된 파이프에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4596d-104">By default, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service connects to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] over named pipes by using dynamic server names that require no additional client configuration.</span></span> <span data-ttu-id="4596d-105">기본 네트워크 전송을 사용하지 않는 경우나 다른 명명된 파이프에서 수신하는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 인스턴스에 연결 중인 경우에만 서버 연결 별칭을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4596d-105">You need to configure a server connection alias only if you are not using the default network transport or if you are connecting to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that listens on an alternate named pipe.</span></span>  
  
 <span data-ttu-id="4596d-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="4596d-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4596d-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="4596d-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4596d-108">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4596d-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4596d-109">보안</span><span class="sxs-lookup"><span data-stu-id="4596d-109">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="4596d-110">SQL Server Management Studio를 사용하여 SQL Server 에이전트 서비스에 대한 SQL Server 별칭을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="4596d-110">To set a SQL Server Alias for the SQL Server Agent Service using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4596d-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="4596d-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4596d-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4596d-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="4596d-113">의 로컬 인스턴스를 참조하는 별칭을 선택하지 않으면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에이전트가 제대로 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4596d-113">Agent will not work correctly unless you select an alias that refers to the local instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="4596d-114">사용 권한이 있는 경우에만 개체 탐색기에 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 노드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4596d-114">Object Explorer only displays the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4596d-115">보안</span><span class="sxs-lookup"><span data-stu-id="4596d-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4596d-116">권한</span><span class="sxs-lookup"><span data-stu-id="4596d-116">Permissions</span></span>  
 <span data-ttu-id="4596d-117">해당 기능을 수행하려면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 **sysadmin** 고정 서버 역할 멤버인 계정의 자격 증명을 사용하도록 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에이전트를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4596d-117">To perform its functions, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4596d-118">이 계정에는 다음과 같은 Windows 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4596d-118">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="4596d-119">서비스로 로그온(SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="4596d-119">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="4596d-120">프로세스 수준 토큰 바꾸기(SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="4596d-120">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="4596d-121">트래버스 검사 무시(SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="4596d-121">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="4596d-122">프로세스의 메모리 할당량 조정(SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="4596d-122">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="4596d-123">에이전트 서비스 계정에 필요한 Windows 사용 권한에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [SQL Server 에이전트 서비스에 대 한 계정 선택](../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) 및 [Windows 서비스 계정 및 권한 구성](configure-windows/configure-windows-service-accounts-and-permissions.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4596d-123">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4596d-124">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="4596d-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-a-sql-server-alias-for-the-sql-server-agent-service"></a><span data-ttu-id="4596d-125">SQL Server 에이전트 서비스에 대한 SQL Server 별칭을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="4596d-125">To set a SQL Server Alias for the SQL Server Agent Service</span></span>  
  
1.  <span data-ttu-id="4596d-126">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4596d-126">In the **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="4596d-127">**SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4596d-127">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="4596d-128">**SQL Server 에이전트 속성**_server_name_ 대화 상자의 **페이지 선택**에서 **연결**을 선택 하 고</span><span class="sxs-lookup"><span data-stu-id="4596d-128">In the **SQL Server Agent Properties**_server_name_ dialog box, under **Select a page**, select **Connection**, and</span></span>  
  
4.  <span data-ttu-id="4596d-129">**로컬 호스트 서버 별칭** 상자에 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트에서 연결할 서버의 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4596d-129">In the **Alias local host server** box, type the alias of the server to which [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent should connect.</span></span>  
  
5.  <span data-ttu-id="4596d-130">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4596d-130">Click **OK**.</span></span>  
  
  
