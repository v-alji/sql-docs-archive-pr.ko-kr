---
title: SQL Server 에이전트 서비스에 대 한 SQL Server 연결 설정 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, connections
- connections [SQL Server], SQL Server Agent service
ms.assetid: 28b6178b-0a9e-4f2c-8562-7a62d2d2a285
author: stevestein
ms.author: sstein
ms.openlocfilehash: 30f68967d6bdb8b0495cbddb1a5b0bd447cd5168
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661485"
---
# <a name="set-the-sql-server-connection-for-the-sql-server-agent-service-sql-server-management-studio"></a><span data-ttu-id="94c07-102">Set the SQL Server Connection for the SQL Server Agent Service (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="94c07-102">Set the SQL Server Connection for the SQL Server Agent Service (SQL Server Management Studio)</span></span>
  <span data-ttu-id="94c07-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 를 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에이전트와 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]간의 연결을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="94c07-103">This topic describes how to set the connection between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent and the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="94c07-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스는 Windows 인증을 사용하여 SQL Server의 로컬 인스턴스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94c07-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service can connect to a local instance of SQL Server by using Windows Authentication.</span></span>  
  
 <span data-ttu-id="94c07-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="94c07-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="94c07-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="94c07-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="94c07-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="94c07-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="94c07-108">보안</span><span class="sxs-lookup"><span data-stu-id="94c07-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="94c07-109">**SQL Server 에이전트에 대한 SQL Server 연결을 설정하려면:**</span><span class="sxs-lookup"><span data-stu-id="94c07-109">**To set the SQL Server Connection for the SQL Server Agent, using:**</span></span>  
  
     [<span data-ttu-id="94c07-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="94c07-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="94c07-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="94c07-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="94c07-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="94c07-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="94c07-113">사용 권한이 있는 경우에만 개체 탐색기에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 노드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="94c07-113">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   <span data-ttu-id="94c07-114">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]부터는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="94c07-114">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent does not support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="94c07-115">이 옵션은 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 관리할 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94c07-115">This option is available only when you administer an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="94c07-116">보안</span><span class="sxs-lookup"><span data-stu-id="94c07-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="94c07-117">권한</span><span class="sxs-lookup"><span data-stu-id="94c07-117">Permissions</span></span>  
 <span data-ttu-id="94c07-118">해당 기능을 수행하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 **sysadmin** 고정 서버 역할 멤버인 계정의 자격 증명을 사용하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="94c07-118">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="94c07-119">이 계정에는 다음과 같은 Windows 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="94c07-119">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="94c07-120">서비스로 로그온(SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="94c07-120">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="94c07-121">프로세스 수준 토큰 바꾸기(SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="94c07-121">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="94c07-122">트래버스 검사 무시(SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="94c07-122">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="94c07-123">프로세스의 메모리 할당량 조정(SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="94c07-123">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="94c07-124">에이전트 서비스 계정에 필요한 Windows 사용 권한에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 에이전트 서비스에 대 한 계정 선택](select-an-account-for-the-sql-server-agent-service.md) 및 [Windows 서비스 계정 및 권한 구성](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="94c07-124">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="94c07-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="94c07-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-the-sql-server-connection"></a><span data-ttu-id="94c07-126">SQL Server 연결을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="94c07-126">To set the SQL Server connection</span></span>  
  
1.  <span data-ttu-id="94c07-127">**개체 탐색기**에서 더하기 기호를 클릭하여 SQL Server 에이전트 서비스에 대한 연결을 사용하여 설정할 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="94c07-127">In **Object Explorer**, click the plus sign to expand the server that you want to set up with a connection to its SQL Server Agent Service.</span></span>  
  
2.  <span data-ttu-id="94c07-128">**SQL Server 에이전트** 를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="94c07-128">Right-click **SQL Server Agent** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="94c07-129">**SQL Server 에이전트 속성** 대화 상자의 **페이지 선택**에서 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="94c07-129">In the **SQL Server Agent Properties** dialog box, under **Select a page**, click **Connection**.</span></span>  
  
4.  <span data-ttu-id="94c07-130">**SQL Server 연결**에서 **Windows 인증 사용**을 선택하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가  Windows 인증을 통해 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]의 인스턴스에 연결할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="94c07-130">Under **SQL Server connection**, select **Use Windows Authentication** to enable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span> <span data-ttu-id="94c07-131">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 데이터베이스에 연결하려면 Windows 인증이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="94c07-131">Connections to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later databases require Windows Authentication.</span></span>  
  
  
