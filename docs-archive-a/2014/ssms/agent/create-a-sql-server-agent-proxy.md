---
title: SQL Server 에이전트 프록시 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], creating
ms.assetid: 142e0c55-a8b9-4669-be49-b9dc602d5988
author: stevestein
ms.author: sstein
ms.openlocfilehash: a7582aef38d57b15de968d96357e56c1974d733e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653111"
---
# <a name="create-a-sql-server-agent-proxy"></a><span data-ttu-id="c4cc6-102">SQL Server 에이전트 프록시 만들기</span><span class="sxs-lookup"><span data-stu-id="c4cc6-102">Create a SQL Server Agent Proxy</span></span>
  <span data-ttu-id="c4cc6-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 SQL Server 에이전트 프록시를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-103">This topic describes how to create a SQL Server Agent proxy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="c4cc6-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 프록시 계정은 작업 단계를 실행할 수 있는 보안 컨텍스트를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-104">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy account defines a security context in which a job step can run.</span></span> <span data-ttu-id="c4cc6-105">각 프록시는 보안 자격 증명에 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-105">Each proxy corresponds to a security credential.</span></span> <span data-ttu-id="c4cc6-106">특정 작업 단계의 사용 권한을 설정하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 하위 시스템에 대한 필요 권한을 가진 프록시를 만든 다음 해당 프록시를 작업 단계에 할당하세요.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-106">To set permissions for a particular job step, create a proxy that has the required permissions for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent subsystem, and then assign that proxy to the job step.</span></span>  
  
 <span data-ttu-id="c4cc6-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="c4cc6-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c4cc6-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="c4cc6-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c4cc6-109">제한 사항</span><span class="sxs-lookup"><span data-stu-id="c4cc6-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="c4cc6-110">보안</span><span class="sxs-lookup"><span data-stu-id="c4cc6-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c4cc6-111">**SQL Server 에이전트 프록시를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="c4cc6-111">**To create a SQL Server Agent proxy, using:**</span></span>  
  
     [<span data-ttu-id="c4cc6-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c4cc6-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c4cc6-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c4cc6-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c4cc6-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c4cc6-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c4cc6-115">제한 사항</span><span class="sxs-lookup"><span data-stu-id="c4cc6-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c4cc6-116">사용 가능한 자격 증명이 없는 경우 프록시를 만들기 전에 먼저 자격 증명을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-116">You must create a credential before you create a proxy if one is not already available.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c4cc6-117">에이전트 프록시는 자격 증명을 사용하여 Windows 사용자 계정에 대한 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-117">Agent proxies use credentials to store information about Windows user accounts.</span></span> <span data-ttu-id="c4cc6-118">자격 증명에 지정된 사용자에게 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 실행 중인 컴퓨터에 대한 "일괄 작업으로 로그온" 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-118">The user specified in the credential must have "Log on as a batch job" permission on the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c4cc6-119">에이전트는 프록시에 대한 하위 시스템 액세스 권한을 확인하고 작업 단계가 실행될 때마다 프록시에 대한 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-119">Agent checks subsystem access for a proxy and gives access to the proxy each time the job step runs.</span></span> <span data-ttu-id="c4cc6-120">프록시에 하위 시스템에 대한 액세스 권한이 없으면 작업 단계가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-120">If the proxy no longer has access to the subsystem, the job step fails.</span></span> <span data-ttu-id="c4cc6-121">그렇지 않으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 프록시에 지정된 사용자를 가장하여 작업 단계를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-121">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent impersonates the user that is specified in the proxy and runs the job step.</span></span>  
  
-   <span data-ttu-id="c4cc6-122">프록시를 만들 때 프록시에 대한 자격 증명에 지정된 사용자의 권한은 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-122">Creation of a proxy does not change the permissions for the user that is specified in the credential for the proxy.</span></span> <span data-ttu-id="c4cc6-123">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스에 연결할 수 있는 권한이 없는 사용자에 대한 프록시를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-123">For example, you can create a proxy for a user that does not have permission to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c4cc6-124">이 경우 해당 프록시를 사용하는 작업 단계에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-124">In this case, job steps that use that proxy are unable to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="c4cc6-125">사용자의 로그인에 프록시에 대한 액세스 권한이 있거나 사용자가 프록시에 대한 액세스 권한이 있는 역할에 속하는 경우 해당 사용자는 작업 단계에서 프록시를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-125">If the login for the user has access to the proxy, or the user belongs to any role with access to the proxy, the user can use the proxy in a job step.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c4cc6-126">보안</span><span class="sxs-lookup"><span data-stu-id="c4cc6-126">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c4cc6-127">권한</span><span class="sxs-lookup"><span data-stu-id="c4cc6-127">Permissions</span></span>  
  
-   <span data-ttu-id="c4cc6-128">**sysadmin** 고정 서버 역할의 멤버만 프록시 계정을 생성, 수정 또는 삭제할 수 있는 권한을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-128">Only members of the **sysadmin** fixed server role have permission to create, modify, or delete proxy accounts.</span></span> <span data-ttu-id="c4cc6-129">프록시를 사용하려면 **sysadmin** 고정 서버 역할의 멤버가 아닌 사용자를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **데이터베이스의** 에이전트 고정 데이터베이스 역할 **SQLAgentUserRole**, **SQLAgentReaderRole**또는 **SQLAgentOperatorRole**중 하나에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-129">Users who are not members of the **sysadmin** fixed server role must be added to one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the **msdb** database to use proxies: **SQLAgentUserRole**, **SQLAgentReaderRole**, or **SQLAgentOperatorRole**.</span></span>  
  
-   <span data-ttu-id="c4cc6-130">프록시와 자격 증명을 만드는 경우 `ALTER ANY CREDENTIAL` 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-130">Requires `ALTER ANY CREDENTIAL` permission if creating a credential in addition to the proxy.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c4cc6-131">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="c4cc6-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a><span data-ttu-id="c4cc6-132">SQL Server 에이전트 프록시를 만들려면</span><span class="sxs-lookup"><span data-stu-id="c4cc6-132">To create a SQL Server Agent proxy</span></span>  
  
1.  <span data-ttu-id="c4cc6-133">**개체 탐색기**에서 더하기 기호를 클릭하여 SQL Server 에이전트에 프록시를 만들려는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-133">In **Object Explorer**, click the plus sign to expand the server where you want to create a proxy on SQL Server Agent.</span></span>  
  
2.  <span data-ttu-id="c4cc6-134">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-134">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="c4cc6-135">**프록시** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 프록시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-135">Right-click the **Proxies** folder and select **New Proxy**.</span></span>  
  
4.  <span data-ttu-id="c4cc6-136">**새 프록시 계정** 대화 상자의 **일반** 페이지에서 **인덱스 이름** 상자에 프록시 계정의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-136">On the **New Proxy Account** dialog box, on the **General** page, enter the name of the proxy account in the **Proxy name** box.</span></span>  
  
5.  <span data-ttu-id="c4cc6-137">**자격 증명 이름** 대화 상자에서 프록시 계정에 사용할 보안 자격 증명의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-137">In the **Credential name** box, enter the name of the security credential that the proxy account will use.</span></span>  
  
6.  <span data-ttu-id="c4cc6-138">**설명** 상자에 프록시 계정에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-138">In the **Description** box, enter a description for the proxy account</span></span>  
  
7.  <span data-ttu-id="c4cc6-139">**다음 하위 시스템에 대해 활성화**에서 이 프록시에 대한 적절한 하위 시스템을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-139">Under **Active to the following subsystems**, select the appropriate subsystem or subsystems for this proxy.</span></span>  
  
8.  <span data-ttu-id="c4cc6-140">**보안 주체** 페이지에서 프록시 계정에 대한 액세스 권한을 부여 또는 제거할 로그인이나 역할을 추가하거나 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-140">On the **Principals** page, add or remove logins or roles to grant or remove access to the proxy account.</span></span>  
  
9. <span data-ttu-id="c4cc6-141">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-141">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c4cc6-142">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="c4cc6-142">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a><span data-ttu-id="c4cc6-143">SQL Server 에이전트 프록시를 만들려면</span><span class="sxs-lookup"><span data-stu-id="c4cc6-143">To create a SQL Server Agent proxy</span></span>  
  
1.  <span data-ttu-id="c4cc6-144">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-144">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c4cc6-145">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-145">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c4cc6-146">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-146">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- creates credential CatalogApplicationCredential  
    USE msdb ;  
    GO  
    CREATE CREDENTIAL CatalogApplicationCredential WITH IDENTITY = 'REDMOND/TestUser',   
        SECRET = 'G3$1o)lkJ8HNd!';  
    GO  
    -- creates proxy "Catalog application proxy" and assigns the credential 'CatalogApplicationCredential' to it.  
    EXEC dbo.sp_add_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 1,  
        @description = 'Maintenance tasks on catalog application.',  
        @credential_name = 'CatalogApplicationCredential' ;  
    GO  
    -- grants the proxy "Catalog application proxy" access to the ActiveX Scripting subsystem.  
    EXEC dbo.sp_grant_proxy_to_subsystem  
        @proxy_name = N'Catalog application proxy',  
        @subsystem_id = 2 ;  
    GO  
    ```  
  
 <span data-ttu-id="c4cc6-147">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c4cc6-147">For more information, see:</span></span>  
  
-   [<span data-ttu-id="c4cc6-148">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c4cc6-148">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-credential-transact-sql)  
  
-   [<span data-ttu-id="c4cc6-149">Transact-sql&#41;sp_add_proxy &#40;</span><span class="sxs-lookup"><span data-stu-id="c4cc6-149">sp_add_proxy &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-proxy-transact-sql)  
  
-   [<span data-ttu-id="c4cc6-150">Transact-sql&#41;sp_grant_proxy_to_subsystem &#40;</span><span class="sxs-lookup"><span data-stu-id="c4cc6-150">sp_grant_proxy_to_subsystem &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql)  
  
  
