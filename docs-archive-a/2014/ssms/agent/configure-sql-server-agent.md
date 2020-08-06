---
title: SQL Server 에이전트 구성 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, configuring
- accounts [SQL Server], SQL Server Agent
- SQL Server Agent, permissions
- security [SQL Server], SQL Server Agent
ms.assetid: 2e361a62-9e92-4fcd-80d7-d6960f127900
author: stevestein
ms.author: sstein
ms.openlocfilehash: 81c78faf733fac5ffb9a6e74dbf03f8caaff03d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650360"
---
# <a name="configure-sql-server-agent"></a><span data-ttu-id="b378c-102">Configure SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="b378c-102">Configure SQL Server Agent</span></span>
  <span data-ttu-id="b378c-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 중에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트의 일부 구성 옵션을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b378c-103">This topic describes how to specify some configuration options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent during installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b378c-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 구성 옵션의 전체 집합은 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], SMO( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관리 개체) 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 저장 프로시저 내에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b378c-104">The full set of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent configuration options is only available within [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO), or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent stored procedures.</span></span>  
  
 <span data-ttu-id="b378c-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="b378c-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b378c-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="b378c-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b378c-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="b378c-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b378c-108">보안</span><span class="sxs-lookup"><span data-stu-id="b378c-108">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="b378c-109">SQL Server 에이전트를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="b378c-109">To configure SQL Server Agent</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b378c-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b378c-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b378c-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="b378c-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="b378c-112">**개체 탐색기에서** SQL Server 에이전트 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 클릭하여 작업, 연산자, 경고 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="b378c-112">Click **SQL Server Agent** in Object Explorer of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to administer jobs, operators, alerts, and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span> <span data-ttu-id="b378c-113">그러나 사용 권한이 있는 경우에만 개체 탐색기에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 노드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b378c-113">However, Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   <span data-ttu-id="b378c-114">장애 조치(Failover) 클러스터 인스턴스에 대한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스에 자동 다시 시작을 사용하도록 설정하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b378c-114">Auto-restart should not be enabled for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service on failover cluster instances.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b378c-115">보안</span><span class="sxs-lookup"><span data-stu-id="b378c-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b378c-116">권한</span><span class="sxs-lookup"><span data-stu-id="b378c-116">Permissions</span></span>  
 <span data-ttu-id="b378c-117">해당 기능을 수행하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 **sysadmin** 고정 서버 역할 멤버인 계정의 자격 증명을 사용하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b378c-117">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b378c-118">이 계정에는 다음과 같은 Windows 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b378c-118">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="b378c-119">서비스로 로그온(SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="b378c-119">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="b378c-120">프로세스 수준 토큰 바꾸기(SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="b378c-120">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="b378c-121">트래버스 검사 무시(SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="b378c-121">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="b378c-122">프로세스의 메모리 할당량 조정(SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="b378c-122">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="b378c-123">에이전트 서비스 계정에 필요한 Windows 사용 권한에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 에이전트 서비스에 대 한 계정 선택](select-an-account-for-the-sql-server-agent-service.md) 및 [Windows 서비스 계정 및 권한 구성](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b378c-123">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b378c-124">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b378c-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-sql-server-agent"></a><span data-ttu-id="b378c-125">SQL Server 에이전트를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="b378c-125">To configure SQL Server Agent</span></span>  
  
1.  <span data-ttu-id="b378c-126">**시작** 단추를 클릭한 다음 **시작**  메뉴에서 **제어판**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b378c-126">Click the **Start** button, and then, on the **Start**  menu, click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="b378c-127">제어판에서 **시스템 및 보안**, **관리 도구**를 차례로 클릭한 다음 **로컬 보안 정책**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b378c-127">In Control Panel, click **System and Security**, click **Administrative Tools**, and then select **Local Security Policy**.</span></span>  
  
3.  <span data-ttu-id="b378c-128">로컬 보안 정책에서 펼침 단추를 클릭하여 **로컬 정책** 폴더를 확장하고 **사용자 권한 할당** 폴더를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b378c-128">In Local Security Policy, click the chevron to expand the **Local Policies** folder, and then click the **User Rights Assignment** folder.</span></span>  
  
4.  <span data-ttu-id="b378c-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 와 함께 사용하도록 구성할 사용 권한을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b378c-129">Right-click a permission that you want to configure for use with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="b378c-130">사용 권한의 속성 대화 상자에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 실행되는 계정이 나열되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b378c-130">In the permission's properties dialog box, verify that the account under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs is listed.</span></span> <span data-ttu-id="b378c-131">나열되지 않으면 **사용자 또는 그룹 추가**를 클릭하고 **사용자, 컴퓨터, 서비스 계정 또는 그룹 선택** 대화 상자에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 실행되는 계정을 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b378c-131">If not, click **Add User or Group**, enter the account under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs in the **Select Users, Computers, Service Accounts, or Groups** dialog box, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="b378c-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트와 함께 실행하기 위해 추가할 각 사용 권한에 대해 이 작업을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="b378c-132">Repeat for each permission that you want to add to run with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="b378c-133">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b378c-133">When finished, click **OK**.</span></span>  
  
  
