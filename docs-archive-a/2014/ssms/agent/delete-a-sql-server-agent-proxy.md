---
title: SQL Server 에이전트 프록시 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting SQL Server Agent proxies
- proxies [SQL Server Agent], deleting
- removing SQL Server Agent proxies
ms.assetid: 9248841d-7294-47d4-94f3-b34a0521fabc
author: stevestein
ms.author: sstein
ms.openlocfilehash: a672c6392e2ffed3ca2a7ed655b806d9d093b10c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653107"
---
# <a name="delete-a-sql-server-agent-proxy"></a><span data-ttu-id="d6277-102">Delete a SQL Server Agent Proxy</span><span class="sxs-lookup"><span data-stu-id="d6277-102">Delete a SQL Server Agent Proxy</span></span>
  <span data-ttu-id="d6277-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 을 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 [!INCLUDE[tsql](../../includes/tsql-md.md)]에이전트 프록시를 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-103">This topic describes how to delete a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy account in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="d6277-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="d6277-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d6277-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="d6277-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d6277-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d6277-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d6277-107">보안</span><span class="sxs-lookup"><span data-stu-id="d6277-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d6277-108">**다음을 사용하여 SQL Server 에이전트 프록시 계정을 삭제합니다.**</span><span class="sxs-lookup"><span data-stu-id="d6277-108">**To delete a SQL Server Agent proxy account, using:**</span></span>  
  
     [<span data-ttu-id="d6277-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d6277-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d6277-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d6277-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d6277-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d6277-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d6277-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d6277-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="d6277-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 프록시 계정을 삭제할 때 프록시가 활성 작업 단계를 참조하지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-113">When you delete a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy account, make sure the proxy does not reference any active job steps.</span></span> <span data-ttu-id="d6277-114">프록시를 참조하는 작업 단계를 확인하려면 프록시를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택한 후 _proxy_name_**프록시 계정 속성** 대화 상자에서 **참조** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-114">To check for any job steps that reference the proxy, right-click the proxy, select **Properties**, and then, in the _proxy_name_**Proxy Account Properties** dialog box, select the **References** page.</span></span> <span data-ttu-id="d6277-115">프록시를 삭제한 경우 **개체 삭제** 대화 상자에서 해당 프록시를 사용하는 모든 작업 단계를 재할당할 수 있는 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-115">If you delete a proxy, you are given the option to reassign all job steps that use that proxy in the **Delete Object** dialog box.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d6277-116">에이전트 프록시는 자격 증명을 사용하여 Windows 사용자 계정에 대한 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-116">Agent proxies use credentials to store information about Windows user accounts.</span></span> <span data-ttu-id="d6277-117">자격 증명에 지정된 사용자에게 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 실행 중인 컴퓨터에 대한 "일괄 작업으로 로그온" 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-117">The user specified in the credential must have "Log on as a batch job" permission on the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d6277-118">에이전트는 프록시에 대한 하위 시스템 액세스 권한을 확인하고 작업 단계가 실행될 때마다 프록시에 대한 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-118">Agent checks subsystem access for a proxy and gives access to the proxy each time the job step runs.</span></span> <span data-ttu-id="d6277-119">프록시에 하위 시스템에 대한 액세스 권한이 없으면 작업 단계가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-119">If the proxy no longer has access to the subsystem, the job step fails.</span></span> <span data-ttu-id="d6277-120">그렇지 않으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 프록시에 지정된 사용자를 가장하여 작업 단계를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-120">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent impersonates the user that is specified in the proxy and runs the job step.</span></span>  
  
-   <span data-ttu-id="d6277-121">사용자의 로그인에 프록시에 대한 액세스 권한이 있거나 사용자가 프록시에 대한 액세스 권한이 있는 역할에 속하는 경우 해당 사용자는 작업 단계에서 프록시를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-121">If the login for the user has access to the proxy, or the user belongs to any role with access to the proxy, the user can use the proxy in a job step.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d6277-122">보안</span><span class="sxs-lookup"><span data-stu-id="d6277-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d6277-123">권한</span><span class="sxs-lookup"><span data-stu-id="d6277-123">Permissions</span></span>  
 <span data-ttu-id="d6277-124">**sysadmin** 고정 서버 역할의 멤버만 프록시 계정을 만들거나 수정하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-124">Only members of the **sysadmin** fixed server role can create, modify, or delete proxy accounts.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d6277-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="d6277-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a><span data-ttu-id="d6277-126">SQL Server 에이전트 프록시 계정을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="d6277-126">To delete a SQL Server Agent proxy account</span></span>  
  
1.  <span data-ttu-id="d6277-127">**개체 탐색기**에서 더하기 기호를 클릭하여 삭제하려는 프록시 계정이 포함된 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-127">In **Object Explorer**, click the plus sign to expand a server that contains the proxy account that you want to delete.</span></span>  
  
2.  <span data-ttu-id="d6277-128">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-128">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="d6277-129">더하기 기호를 클릭하여 **프록시** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-129">Click the plus sign to expand the **Proxies** folder.</span></span>  
  
4.  <span data-ttu-id="d6277-130">더하기 기호를 클릭하여 삭제하려는 프록시 계정이 포함된 하위 시스템을 확장합니다(예: **ActiveX 스크립트**).</span><span class="sxs-lookup"><span data-stu-id="d6277-130">Click the plus sign to expand the subsystem that contains the proxy account you want to delete (for example, **ActiveX Script)**.</span></span>  
  
5.  <span data-ttu-id="d6277-131">삭제하려는 프록시 계정을 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-131">Right-click the proxy account that you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="d6277-132">**개체 삭제** 대화 상자에서 올바른 프록시 계정이 선택되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-132">In the **Delete Object** dialog box, confirm that the correct proxy account is selected.</span></span> <span data-ttu-id="d6277-133">**재할당 대상** 확인란을 선택하여 이 프록시 계정을 참조하는 작업 단계를 다른 계정에 재할당합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-133">Check the **Reassign to** check box to reassign the job steps that reference this proxy account to another account.</span></span>  
  
7.  <span data-ttu-id="d6277-134">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-134">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d6277-135">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="d6277-135">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a><span data-ttu-id="d6277-136">SQL Server 에이전트 프록시 계정을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="d6277-136">To delete a SQL Server Agent proxy account</span></span>  
  
1.  <span data-ttu-id="d6277-137">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d6277-138">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d6277-139">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6277-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- deletes the proxy "Catalog application proxy"  
    USE msdb ;  
    GO  
    EXEC dbo.sp_delete_proxy  
        @proxy_name = N'Catalog application proxy' ;  
    GO  
    ```  
  
 <span data-ttu-id="d6277-140">자세한 내용은 [sp_delete_proxy &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d6277-140">For more information, see [sp_delete_proxy &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql).</span></span>  
  
  
