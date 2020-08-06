---
title: SQL Server 에이전트 프록시 수정 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], modifying
- modifying SQL Server Agent proxy
ms.assetid: 6e1dfbaa-8089-4813-940c-d5a2e13d8552
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2f86793a8ddcc6fe8f981d6b367d2178c5a794ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649337"
---
# <a name="modify-a-sql-server-agent-proxy"></a><span data-ttu-id="7b234-102">Modify a SQL Server Agent Proxy</span><span class="sxs-lookup"><span data-stu-id="7b234-102">Modify a SQL Server Agent Proxy</span></span>
  <span data-ttu-id="7b234-103">이 항목에서는 또는을 사용 하 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 여에서 에이전트 프록시를 수정 하는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7b234-103">This topic describes how to modify a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="7b234-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="7b234-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7b234-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="7b234-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7b234-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="7b234-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="7b234-107">보안</span><span class="sxs-lookup"><span data-stu-id="7b234-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7b234-108">**다음을 사용하여 SQL Server 에이전트 프록시를 수정합니다.**</span><span class="sxs-lookup"><span data-stu-id="7b234-108">**To modify a SQL Server Agent proxy, using:**</span></span>  
  
     [<span data-ttu-id="7b234-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7b234-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7b234-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7b234-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7b234-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="7b234-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7b234-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="7b234-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7b234-113">에이전트 프록시는 자격 증명을 사용하여 Windows 사용자 계정에 대한 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="7b234-113">Agent proxies use credentials to store information about Windows user accounts.</span></span> <span data-ttu-id="7b234-114">자격 증명에 지정된 사용자에게 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 실행 중인 컴퓨터에 대한 "일괄 작업으로 로그온" 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b234-114">The user specified in the credential must have "Log on as a batch job" permission on the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7b234-115">에이전트는 프록시에 대한 하위 시스템 액세스 권한을 확인하고 작업 단계가 실행될 때마다 프록시에 대한 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="7b234-115">Agent checks subsystem access for a proxy and gives access to the proxy each time the job step runs.</span></span> <span data-ttu-id="7b234-116">프록시에 하위 시스템에 대한 액세스 권한이 없으면 작업 단계가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="7b234-116">If the proxy no longer has access to the subsystem, the job step fails.</span></span> <span data-ttu-id="7b234-117">그렇지 않으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 프록시에 지정된 사용자를 가장하여 작업 단계를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7b234-117">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent impersonates the user that is specified in the proxy and runs the job step.</span></span>  
  
-   <span data-ttu-id="7b234-118">사용자의 로그인에 프록시에 대한 액세스 권한이 있거나 사용자가 프록시에 대한 액세스 권한이 있는 역할에 속하는 경우 해당 사용자는 작업 단계에서 프록시를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b234-118">If the login for the user has access to the proxy, or the user belongs to any role with access to the proxy, the user can use the proxy in a job step.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7b234-119">보안</span><span class="sxs-lookup"><span data-stu-id="7b234-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7b234-120">권한</span><span class="sxs-lookup"><span data-stu-id="7b234-120">Permissions</span></span>  
 <span data-ttu-id="7b234-121">**sysadmin** 고정 서버 역할의 멤버만 프록시 계정을 만들거나 수정하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b234-121">Only members of the **sysadmin** fixed server role can create, modify, or delete proxy accounts.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7b234-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="7b234-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-ssnoversion-agent-proxy"></a><span data-ttu-id="7b234-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 프록시를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="7b234-123">To modify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy</span></span>  
  
1.  <span data-ttu-id="7b234-124">**개체 탐색기**에서 더하기 기호를 클릭하여 수정하려는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 프록시 계정이 포함된 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="7b234-124">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy account that you want to modify.</span></span>  
  
2.  <span data-ttu-id="7b234-125">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="7b234-125">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="7b234-126">더하기 기호를 클릭하여 **프록시** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="7b234-126">Click the plus sign to expand the **Proxies** folder.</span></span>  
  
4.  <span data-ttu-id="7b234-127">더하기 기호를 클릭하여 프록시에 대한 하위 시스템 노드(예: **ActiveX 스크립트**)를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="7b234-127">Click the plus sign to expand the subsystem node for the proxy (for example, **ActiveX Script**).</span></span>  
  
5.  <span data-ttu-id="7b234-128">수정하려는 프록시 계정을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b234-128">Right-click the proxy account you want to modify and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="7b234-129">_Proxy_name_**프록시 계정 속성** 대화 상자에서 필요에 따라 프록시 계정을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b234-129">In the _proxy_name_**Proxy Account Properties** dialog box, make changes to the proxy account as necessary.</span></span> <span data-ttu-id="7b234-130">이 대화 상자의 옵션에 대한 자세한 내용은 [SQL Server 에이전트 프록시 만들기](create-a-sql-server-agent-proxy.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7b234-130">For more information on the options in this dialog box, see [Create a SQL Server Agent Proxy](create-a-sql-server-agent-proxy.md).</span></span>  
  
7.  <span data-ttu-id="7b234-131">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b234-131">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7b234-132">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="7b234-132">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-ssnoversion-agent-proxy"></a><span data-ttu-id="7b234-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 프록시를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="7b234-133">To modify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy</span></span>  
  
1.  <span data-ttu-id="7b234-134">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7b234-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7b234-135">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b234-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7b234-136">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b234-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Disables the proxy named 'Catalog application proxy'.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 0;  
    GO  
    ```  
  
 <span data-ttu-id="7b234-137">자세한 내용은 [sp_update_proxy &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-proxy-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7b234-137">For more information, see [sp_update_proxy &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-proxy-transact-sql).</span></span>  
  
  
