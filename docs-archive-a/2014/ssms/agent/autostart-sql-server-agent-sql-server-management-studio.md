---
title: SQL Server 에이전트 자동 시작(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, starting
- autostart SQL Server Agent
ms.assetid: 2ea332da-0ede-4d2b-b122-c4c10eaca191
author: stevestein
ms.author: sstein
ms.openlocfilehash: a39c7c7a112370797a965cfa601bc07f983a7a37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652539"
---
# <a name="autostart-sql-server-agent-sql-server-management-studio"></a><span data-ttu-id="b1a87-102">Autostart SQL Server Agent (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="b1a87-102">Autostart SQL Server Agent (SQL Server Management Studio)</span></span>
  <span data-ttu-id="b1a87-103">이 항목 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는에서 예기치 않게 중지 되어야 하는 경우 자동으로 다시 시작 되도록 에이전트를 구성 하는 방법에 대해 설명 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a87-103">This topic describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to automatically restart if it should stop unexpectedly in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="b1a87-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="b1a87-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b1a87-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="b1a87-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b1a87-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="b1a87-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b1a87-107">보안</span><span class="sxs-lookup"><span data-stu-id="b1a87-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="b1a87-108">SQL Server Management Studio를 사용하여 자동으로 시작되도록 SQL Server 에이전트를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="b1a87-108">To configure SQL Server Agent to automatically restart, using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b1a87-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b1a87-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b1a87-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="b1a87-110">Limitations and Restrictions</span></span>  
 <span data-ttu-id="b1a87-111">사용 권한이 있는 경우에만 개체 탐색기에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 노드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1a87-111">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b1a87-112">보안</span><span class="sxs-lookup"><span data-stu-id="b1a87-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b1a87-113">권한</span><span class="sxs-lookup"><span data-stu-id="b1a87-113">Permissions</span></span>  
 <span data-ttu-id="b1a87-114">해당 기능을 수행하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 **sysadmin** 고정 서버 역할 멤버인 계정의 자격 증명을 사용하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a87-114">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b1a87-115">이 계정에는 다음과 같은 Windows 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a87-115">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="b1a87-116">서비스로 로그온(SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="b1a87-116">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="b1a87-117">프로세스 수준 토큰 바꾸기(SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="b1a87-117">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="b1a87-118">트래버스 검사 무시(SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="b1a87-118">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="b1a87-119">프로세스의 메모리 할당량 조정(SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="b1a87-119">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="b1a87-120">에이전트 서비스 계정에 필요한 Windows 사용 권한에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 에이전트 서비스에 대 한 계정 선택](select-an-account-for-the-sql-server-agent-service.md) 및 [Windows 서비스 계정 및 권한 구성](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b1a87-120">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b1a87-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b1a87-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-sql-server-agent-to-automatically-restart"></a><span data-ttu-id="b1a87-122">자동으로 다시 시작되도록 SQL Server 에이전트를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="b1a87-122">To configure SQL Server Agent to automatically restart</span></span>  
  
1.  <span data-ttu-id="b1a87-123">**개체 탐색기**에서 더하기 기호를 클릭하여 자동으로 다시 시작되도록 SQL Server 에이전트를 구성할 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a87-123">In **Object Explorer**, click the plus sign to expand the server where you want to configure SQL Server Agent to automatically restart.</span></span>  
  
2.  <span data-ttu-id="b1a87-124">**SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a87-124">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="b1a87-125">**일반** 페이지에서 **SQL Server 에이전트가 갑자기 작동을 멈추면 자동으로 다시 시작**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a87-125">On the **General** page, check **Auto restart SQL Server Agent if it stops unexpectedly**.</span></span>  
  
  
