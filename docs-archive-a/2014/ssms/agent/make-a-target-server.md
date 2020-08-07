---
title: 대상 서버 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.tsxwiz.msx.f1
- sql12.ag.tsxwiz.cover.f1
- sql12.ag.tsxwiz.credentials.f1
- sql12.ag.tsxwiz.complete.f1
helpviewer_keywords:
- Target Server Wizard
- SQL Server Agent jobs, target servers
- target servers [SQL Server], creating
ms.assetid: 13aabe2d-67fe-4c67-8d49-2928dd705b7a
author: stevestein
ms.author: sstein
ms.openlocfilehash: bd60a19234d186bb0912978589fa60fd8e8a8c22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727900"
---
# <a name="make-a-target-server"></a><span data-ttu-id="5fd09-102">대상 서버 만들기</span><span class="sxs-lookup"><span data-stu-id="5fd09-102">Make a Target Server</span></span>
  <span data-ttu-id="5fd09-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]또는 SMO(SQL Server 관리 개체)를 사용하여 대상 서버를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-103">This topic describes how to make a target server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects (SMO).</span></span>  
  
 <span data-ttu-id="5fd09-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="5fd09-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5fd09-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="5fd09-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5fd09-106">보안</span><span class="sxs-lookup"><span data-stu-id="5fd09-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5fd09-107">**대상 서버를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="5fd09-107">**To make a target server, using:**</span></span>  
  
     [<span data-ttu-id="5fd09-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5fd09-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5fd09-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5fd09-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="5fd09-110">SMO</span><span class="sxs-lookup"><span data-stu-id="5fd09-110">SMO</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5fd09-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="5fd09-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5fd09-112">보안</span><span class="sxs-lookup"><span data-stu-id="5fd09-112">Security</span></span>  
 <span data-ttu-id="5fd09-113">프록시와 연관된 단계가 있는 배포된 작업은 대상 서버의 프록시 계정 컨텍스트로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-113">Distributed jobs that have steps which are associated with a proxy run under the context of the proxy account on the target server.</span></span> <span data-ttu-id="5fd09-114">다음 조건이 만족되는지 또는 프록시와 연관된 작업 단계가 마스터 서버에서 대상으로 다운로드되지 않는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="5fd09-114">Make sure that the following conditions are met or job steps that are associated with a proxy will not be downloaded from the master server to the target:</span></span>  
  
-   <span data-ttu-id="5fd09-115">마스터 서버 레지스트리 하위 키 **\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server \\ < *instance_name*> \sql server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD)는 1 (true)로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-115">The master server registry subkey **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<*instance_name*>\SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) is set to 1 (true).</span></span> <span data-ttu-id="5fd09-116">기본적으로 이 하위 키는 0(false)으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-116">By default, this subkey is set to 0 (false).</span></span>  
  
-   <span data-ttu-id="5fd09-117">프록시 계정이 작업 단계가 실행되는 마스터 서버 프록시 계정과 동일한 이름을 가진 대상 서버에 있는지 여부</span><span class="sxs-lookup"><span data-stu-id="5fd09-117">A proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
 <span data-ttu-id="5fd09-118">마스터 서버에서 대상 서버로 다운로드할 때 프록시 계정을 사용하는 작업 단계가 실패한 경우 **msdb** 데이터베이스의 **sysdownloadlist** 테이블에 있는 **error_message** 열에서 다음 오류 메시지를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-118">If job steps that use proxy accounts fail when downloading them from the master server to the target server, you can check the **error_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:</span></span>  
  
-   <span data-ttu-id="5fd09-119">"작업 단계에 프록시 계정이 필요하지만 일치하는 프록시를 대상 서버에서 사용할 수 없습니다."</span><span class="sxs-lookup"><span data-stu-id="5fd09-119">"The job step requires a proxy account, however proxy matching is disabled on the target server."</span></span>  
  
     <span data-ttu-id="5fd09-120">이 오류를 해결하려면 **AllowDownloadedJobsToMatchProxyName** 레지스트리 하위 키를 1로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-120">To resolve this error, set the **AllowDownloadedJobsToMatchProxyName** registry subkey to 1.</span></span>  
  
-   <span data-ttu-id="5fd09-121">"프록시를 찾을 수 없습니다."</span><span class="sxs-lookup"><span data-stu-id="5fd09-121">"Proxy not found."</span></span>  
  
     <span data-ttu-id="5fd09-122">이 오류를 해결하려면 프록시 계정이 작업 단계가 실행되는 마스터 서버 프록시 계정과 동일한 이름을 가진 대상 서버에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-122">To resolve this error, make sure a proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5fd09-123">권한</span><span class="sxs-lookup"><span data-stu-id="5fd09-123">Permissions</span></span>  
 <span data-ttu-id="5fd09-124">이 프로시저를 실행할 수 있는 권한은 기본적으로 `sysadmin` 고정 서버 역할의 멤버로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-124">Permissions to execute this procedure default to members of the `sysadmin` fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5fd09-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="5fd09-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-make-a-target-server"></a><span data-ttu-id="5fd09-126">대상 서버를 만들려면</span><span class="sxs-lookup"><span data-stu-id="5fd09-126">To make a target server</span></span>  
  
1.  <span data-ttu-id="5fd09-127">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-127">In **Object Explorer,** connect to an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="5fd09-128">**SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭하고 **다중 서버 관리**를 가리킨 다음 **대상으로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-128">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Make this a Target**.</span></span> <span data-ttu-id="5fd09-129">**대상 서버 만들기 마법사** 가 대상 서버를 만드는 프로세스를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-129">The **Target Server Wizard** guides you through the process of making a target server.</span></span>  
  
3.  <span data-ttu-id="5fd09-130">**마스터 서버 선택** 페이지에서 이 대상 서버가 작업을 받는 마스터 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-130">From the **Select a Master Server** page, select the master server that this target server will receive jobs from.</span></span>  
  
     <span data-ttu-id="5fd09-131">**서버 선택**</span><span class="sxs-lookup"><span data-stu-id="5fd09-131">**Pick Server**</span></span>  
     <span data-ttu-id="5fd09-132">마스터 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-132">Connect to the master server.</span></span>  
  
     <span data-ttu-id="5fd09-133">**이 서버에 대한 설명**</span><span class="sxs-lookup"><span data-stu-id="5fd09-133">**Description of this server**</span></span>  
     <span data-ttu-id="5fd09-134">이 대상 서버에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-134">Type a description for this target server.</span></span> <span data-ttu-id="5fd09-135">대상 서버는 이 설명을 마스터 서버로 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-135">The target server uploads this description to the master server.</span></span>  
  
4.  <span data-ttu-id="5fd09-136">**마스터 서버 로그인 자격 증명** 페이지에서 필요한 경우 대상 서버에 새 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-136">From the **Master Server Login Credentials** page, create a new login on the target server, if necessary.</span></span>  
  
     <span data-ttu-id="5fd09-137">**필요한 경우 새 로그인을 만들고 MSX에 대한 권한을 할당합니다.**</span><span class="sxs-lookup"><span data-stu-id="5fd09-137">**Create a new login if necessary and assign it rights to the MSX**</span></span>  
     <span data-ttu-id="5fd09-138">지정한 로그인이 없으면 대상 서버에 새 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-138">Create a new login on the target server if the login specified does not already exist.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5fd09-139">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="5fd09-139">Using Transact-SQL</span></span>  
  
#### <a name="to-make-a-target-server"></a><span data-ttu-id="5fd09-140">대상 서버를 만들려면</span><span class="sxs-lookup"><span data-stu-id="5fd09-140">To make a target server</span></span>  
  
1.  <span data-ttu-id="5fd09-141">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5fd09-142">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5fd09-143">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="5fd09-144">이 예에서는 현재 서버를 AdventureWorks1 마스터 서버에 참여시킵니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-144">This example enlists the current server into the AdventureWorks1 master server.</span></span> <span data-ttu-id="5fd09-145">현재 서버의 위치는 Building 21, Room 309, Rack 5입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd09-145">The location for the current server is Building 21, Room 309, Rack 5.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_msx_enlist N'AdventureWorks1',   
        N'Building 21, Room 309, Rack 5' ;   
    GO;  
    ```  
  
     <span data-ttu-id="5fd09-146">자세한 내용은 [sp_msx_enlist &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5fd09-146">For more information, see [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects-smo"></a><a name="PowerShellProcedure"></a><span data-ttu-id="5fd09-147">SQL Server 관리 개체 사용 (SMO)</span><span class="sxs-lookup"><span data-stu-id="5fd09-147">Using SQL Server Management Objects (SMO)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fd09-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5fd09-148">See Also</span></span>  
 [<span data-ttu-id="5fd09-149">기업 내 관리 자동화</span><span class="sxs-lookup"><span data-stu-id="5fd09-149">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
