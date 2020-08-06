---
title: SQL Server 에이전트 오류 로그에 실행 추적 메시지 쓰기 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- writing trace messages
- traces [SQL Server], SQL Server Agent logs
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: 90e3731e-6fae-43db-833e-9accecdd1c03
author: stevestein
ms.author: sstein
ms.openlocfilehash: 38b08452ef2680b654dd735b901488cb5f5f5f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734887"
---
# <a name="write-execution-trace-messages-to-the-sql-server-agent-error-log-sql-server-management-studio"></a><span data-ttu-id="d53ea-102">Write Execution Trace Messages to the SQL Server Agent Error Log (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="d53ea-102">Write Execution Trace Messages to the SQL Server Agent Error Log (SQL Server Management Studio)</span></span>
  <span data-ttu-id="d53ea-103">이 항목에서는를 사용 하 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 여 오류 로그에 실행 추적 메시지를 포함 하도록 에이전트를 구성 하는 방법에 대해 설명 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="d53ea-103">This topic describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to include execution trace messages in its error log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="d53ea-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="d53ea-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d53ea-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="d53ea-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d53ea-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d53ea-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d53ea-107">보안</span><span class="sxs-lookup"><span data-stu-id="d53ea-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="d53ea-108">SQL Server Management Studio를 사용하여 실행 추적 메시지를 SQL Server 에이전트 오류 로그에 기록하려면</span><span class="sxs-lookup"><span data-stu-id="d53ea-108">To write execution trace messages to the SQL Server Agent Error Log using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d53ea-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d53ea-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d53ea-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d53ea-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="d53ea-111">사용 권한이 있는 경우에만 개체 탐색기에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 노드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d53ea-111">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   <span data-ttu-id="d53ea-112">이 옵션으로 오류 로그가 더욱 커질 수 있으므로 특정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 문제를 조사할 때만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 오류 로그에 실행 추적 메시지를 포함하세요.</span><span class="sxs-lookup"><span data-stu-id="d53ea-112">Because this option can cause the error log to become large, only include execution trace messages in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error logs when investigating a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent problem.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d53ea-113">보안</span><span class="sxs-lookup"><span data-stu-id="d53ea-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d53ea-114">권한</span><span class="sxs-lookup"><span data-stu-id="d53ea-114">Permissions</span></span>  
 <span data-ttu-id="d53ea-115">해당 기능을 수행하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 **sysadmin** 고정 서버 역할 멤버인 계정의 자격 증명을 사용하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d53ea-115">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d53ea-116">이 계정에는 다음과 같은 Windows 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d53ea-116">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="d53ea-117">서비스로 로그온(SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="d53ea-117">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="d53ea-118">프로세스 수준 토큰 바꾸기(SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="d53ea-118">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="d53ea-119">트래버스 검사 무시(SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="d53ea-119">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="d53ea-120">프로세스의 메모리 할당량 조정(SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="d53ea-120">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="d53ea-121">에이전트 서비스 계정에 필요한 Windows 사용 권한에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 에이전트 서비스에 대 한 계정 선택](select-an-account-for-the-sql-server-agent-service.md) 및 [Windows 서비스 계정 및 권한 구성](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d53ea-121">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="SSMSProcedure"></a>   
#### <a name="to-write-execution-trace-messages-to-the-sql-server-agent-error-log"></a><span data-ttu-id="d53ea-122">실행 추적 메시지를 SQL Server 에이전트 오류 로그에 쓰려면</span><span class="sxs-lookup"><span data-stu-id="d53ea-122">To write execution trace messages to the SQL Server Agent error log</span></span>  
  
1.  <span data-ttu-id="d53ea-123">**개체 탐색기**에서 더하기 기호를 클릭하여 실행 추적 메시지를 기록하려는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 오류 로그가 포함된 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d53ea-123">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log to which you want to write execution trace messages.</span></span>  
  
2.  <span data-ttu-id="d53ea-124">**SQL Server 에이전트** 를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d53ea-124">Right-click **SQL Server Agent** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="d53ea-125">**SQL Server 에이전트 속성-**_Server_name_ 대화 상자의 **일반** 페이지에 있는 **오류 로그** 에서 **실행 추적 메시지 포함** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d53ea-125">In the **SQL Server Agent Properties -**_server_name_ dialog box, under **Error log** on the **General** page, select the **Include execution trace messages** check box.</span></span>  
  
4.  <span data-ttu-id="d53ea-126">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d53ea-126">Click **OK**.</span></span>  
  
  
