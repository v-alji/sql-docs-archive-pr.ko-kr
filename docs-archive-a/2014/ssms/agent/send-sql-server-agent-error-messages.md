---
title: SQL Server 에이전트 오류 메시지 보내기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- messages [SQL Server], SQL Server Agent
- sending messages
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: 2597d0d7-951a-48cf-989f-abb67b9fdb36
author: stevestein
ms.author: sstein
ms.openlocfilehash: 03e38b02188eaced65a86b22ed4f22cb6984ce0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652531"
---
# <a name="send-sql-server-agent-error-messages"></a><span data-ttu-id="dba3a-102">Send SQL Server Agent Error Messages</span><span class="sxs-lookup"><span data-stu-id="dba3a-102">Send SQL Server Agent Error Messages</span></span>
  <span data-ttu-id="dba3a-103">이 항목에서는를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용 하 여에서 net send를 통해 오류 메시지를 보내도록 에이전트를 구성 하는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="dba3a-103">This topic describes how to how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to send its error messages by way of net send in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="dba3a-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="dba3a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="dba3a-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="dba3a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="dba3a-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="dba3a-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="dba3a-107">보안</span><span class="sxs-lookup"><span data-stu-id="dba3a-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="dba3a-108">SQL Server Management Studio를 사용하여 SQL Server 에이전트 오류 메시지를 보내려면</span><span class="sxs-lookup"><span data-stu-id="dba3a-108">To send SQL Server Agent error messages using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="dba3a-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="dba3a-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="dba3a-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="dba3a-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="dba3a-111">사용 권한이 있는 경우에만 개체 탐색기에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 노드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dba3a-111">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   <span data-ttu-id="dba3a-112">net send 이벤트를 수신하려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Messenger 서비스를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dba3a-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Messenger service must be running to receive net send events.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="dba3a-113">보안</span><span class="sxs-lookup"><span data-stu-id="dba3a-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="dba3a-114">권한</span><span class="sxs-lookup"><span data-stu-id="dba3a-114">Permissions</span></span>  
 <span data-ttu-id="dba3a-115">해당 기능을 수행하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 **sysadmin** 고정 서버 역할 멤버인 계정의 자격 증명을 사용하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dba3a-115">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="dba3a-116">이 계정에는 다음과 같은 Windows 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="dba3a-116">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="dba3a-117">서비스로 로그온(SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="dba3a-117">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="dba3a-118">프로세스 수준 토큰 바꾸기(SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="dba3a-118">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="dba3a-119">트래버스 검사 무시(SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="dba3a-119">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="dba3a-120">프로세스의 메모리 할당량 조정(SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="dba3a-120">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="dba3a-121">에이전트 서비스 계정에 필요한 Windows 사용 권한에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 에이전트 서비스에 대 한 계정 선택](select-an-account-for-the-sql-server-agent-service.md) 및 [Windows 서비스 계정 및 권한 구성](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dba3a-121">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="dba3a-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="dba3a-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-send-sql-server-agent-error-messages"></a><span data-ttu-id="dba3a-123">SQL Server 에이전트 오류 메시지를 보내려면</span><span class="sxs-lookup"><span data-stu-id="dba3a-123">To send SQL Server Agent error messages</span></span>  
  
1.  <span data-ttu-id="dba3a-124">**개체 탐색기**에서 더하기 기호를 클릭하여 net send를 통해 오류 메시지를 보내려는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 오류 로그가 포함된 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="dba3a-124">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log from which you want to send error messages via net send.</span></span>  
  
2.  <span data-ttu-id="dba3a-125">**SQL Server 에이전트** 를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dba3a-125">Right-click **SQL Server Agent** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="dba3a-126">**SQL Server 에이전트 속성-**_Server_name_ 대화 상자의 **일반** 페이지에 있는 **오류 로그** 에서 **Net send 수신자** 상자에 오류 메시지를 보내려는 사용자 이름 또는 컴퓨터 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="dba3a-126">In the **SQL Server Agent Properties -**_server_name_ dialog box, under **Error log** on the **General** page, , type the user name or computer name to which you want to send error messages in the **Net send recipient** box.</span></span>  
  
4.  <span data-ttu-id="dba3a-127">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dba3a-127">Click **OK**.</span></span>  
  
  
