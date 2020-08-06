---
title: SQL Server 에이전트 오류 로그 이름 바꾸기(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- renaming SQL Server Agent error log
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: dee2b199-48af-44cb-9177-d029a5edb169
author: stevestein
ms.author: sstein
ms.openlocfilehash: c1c85550a29bfff316ffc275ba2d4e4df10686d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660814"
---
# <a name="rename-a-sql-server-agent-error-log-sql-server-management-studio"></a><span data-ttu-id="b424d-102">Rename a SQL Server Agent Error Log (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="b424d-102">Rename a SQL Server Agent Error Log (SQL Server Management Studio)</span></span>
  <span data-ttu-id="b424d-103">이 항목에서는를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용 하 여에서 에이전트 오류가 기록 된 파일의 이름을 바꾸는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b424d-103">This topic describes how to rename the file where [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent errors are written in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="b424d-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="b424d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b424d-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="b424d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b424d-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="b424d-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b424d-107">보안</span><span class="sxs-lookup"><span data-stu-id="b424d-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="b424d-108">SQL Server Management Studio를 사용하여 SQL Server 에이전트 오류 로그의 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="b424d-108">To rename a SQL Server Agent error log using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b424d-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b424d-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b424d-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="b424d-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="b424d-111">사용 권한이 있는 경우에만 개체 탐색기에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 노드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b424d-111">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b424d-112">에이전트에서 새 로그 파일에 기록하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b424d-112">Agent will not write to the new log file until the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is restarted.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b424d-113">보안</span><span class="sxs-lookup"><span data-stu-id="b424d-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b424d-114">권한</span><span class="sxs-lookup"><span data-stu-id="b424d-114">Permissions</span></span>  
 <span data-ttu-id="b424d-115">해당 기능을 수행하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 **sysadmin** 고정 서버 역할 멤버인 계정의 자격 증명을 사용하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b424d-115">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b424d-116">이 계정에는 다음과 같은 Windows 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b424d-116">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="b424d-117">서비스로 로그온(SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="b424d-117">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="b424d-118">프로세스 수준 토큰 바꾸기(SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="b424d-118">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="b424d-119">트래버스 검사 무시(SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="b424d-119">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="b424d-120">프로세스의 메모리 할당량 조정(SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="b424d-120">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="b424d-121">에이전트 서비스 계정에 필요한 Windows 사용 권한에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 에이전트 서비스에 대 한 계정 선택](select-an-account-for-the-sql-server-agent-service.md) 및 [Windows 서비스 계정 및 권한 구성](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b424d-121">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b424d-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b424d-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-sql-server-agent-error-log"></a><span data-ttu-id="b424d-123">SQL Server 에이전트 오류 로그 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="b424d-123">To rename a SQL Server Agent error log</span></span>  
  
1.  <span data-ttu-id="b424d-124">**개체 탐색기**에서 더하기 기호를 클릭하여 이름을 바꾸려는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 오류 로그가 포함된 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b424d-124">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log that you want to rename.</span></span>  
  
2.  <span data-ttu-id="b424d-125">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b424d-125">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="b424d-126">**오류 로그** 폴더를 마우스 오른쪽 단추로 클릭한 다음 **구성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b424d-126">Right-click the **Error Logs** folder and select **Configure**.</span></span>  
  
4.  <span data-ttu-id="b424d-127">**SQL Server 에이전트 오류 로그 구성** 대화 상자의 **오류 로그 파일** 상자에서 오류 로그에 대한 새 파일 경로 및 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b424d-127">In the **Configure SQL Server Agent Error Logs** dialog box, in the **Error log file** box, enter the new file path and file name for the error log.</span></span> <span data-ttu-id="b424d-128">또는 줄임표 **(...)** 를 클릭하여 **에이전트 오류 로그 위치를 지정하십시오.** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b424d-128">Alternately, click the ellipsis **(...)** to open the **Specify agent error log location** dialog box.</span></span>  
  
5.  <span data-ttu-id="b424d-129">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b424d-129">When finished, click **OK**.</span></span>  
  
  
