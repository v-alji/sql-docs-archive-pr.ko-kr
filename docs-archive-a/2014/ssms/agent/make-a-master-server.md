---
title: 마스터 서버 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.msxwiz.complete.f1
- sql12.ag.msxwiz.target.f1
- sql12.ag.msxwiz.login.f1
- sql12.ag.msxwiz.cover.f1
- sql12.ag.msxwiz.operator.f1
helpviewer_keywords:
- master servers [SQL Server], creating
- wizards [SQL Server Management Studio], Master Server Wizard
- SQL Server Agent jobs, master servers
- Master Server Wizard
ms.assetid: 05739a73-1fdf-4d9d-92a6-70f328380322
author: stevestein
ms.author: sstein
ms.openlocfilehash: ce8e7428aaf8ba459bcf6831988c61da3f192bac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650353"
---
# <a name="make-a-master-server"></a><span data-ttu-id="1a006-102">Make a Master Server</span><span class="sxs-lookup"><span data-stu-id="1a006-102">Make a Master Server</span></span>
  <span data-ttu-id="1a006-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 마스터 서버 [!INCLUDE[tsql](../../includes/tsql-md.md)]를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-103">This topic describes how to make a master server [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1a006-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="1a006-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1a006-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="1a006-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1a006-106">보안</span><span class="sxs-lookup"><span data-stu-id="1a006-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1a006-107">**마스터 서버를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="1a006-107">**To make a master server, using:**</span></span>  
  
     [<span data-ttu-id="1a006-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1a006-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1a006-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1a006-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1a006-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="1a006-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1a006-111">보안</span><span class="sxs-lookup"><span data-stu-id="1a006-111">Security</span></span>  
 <span data-ttu-id="1a006-112">프록시와 연관된 단계가 있는 배포된 작업은 대상 서버의 프록시 계정 컨텍스트로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-112">Distributed jobs that have steps which are associated with a proxy run under the context of the proxy account on the target server.</span></span> <span data-ttu-id="1a006-113">다음 조건이 만족되는지 또는 프록시와 연관된 작업 단계가 마스터 서버에서 대상으로 다운로드되지 않는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="1a006-113">Make sure that the following conditions are met or job steps that are associated with a proxy will not be downloaded from the master server to the target:</span></span>  
  
-   <span data-ttu-id="1a006-114">마스터 서버 레지스트리 하위 키 **\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server \\ < *instance_name*> \sql server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD)는 1 (true)로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-114">The master server registry subkey **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<*instance_name*>\SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) is set to 1 (true).</span></span> <span data-ttu-id="1a006-115">기본적으로 이 하위 키는 0(false)으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-115">By default, this subkey is set to 0 (false).</span></span>  
  
-   <span data-ttu-id="1a006-116">프록시 계정이 작업 단계가 실행되는 마스터 서버 프록시 계정과 동일한 이름을 가진 대상 서버에 있는지 여부</span><span class="sxs-lookup"><span data-stu-id="1a006-116">A proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
 <span data-ttu-id="1a006-117">마스터 서버에서 대상 서버로 다운로드할 때 프록시 계정을 사용하는 작업 단계가 실패한 경우 **msdb** 데이터베이스의 **sysdownloadlist** 테이블에 있는 **error_message** 열에서 다음 오류 메시지를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-117">If job steps that use proxy accounts fail when downloading them from the master server to the target server, you can check the **error_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:</span></span>  
  
-   <span data-ttu-id="1a006-118">"작업 단계에 프록시 계정이 필요하지만 일치하는 프록시를 대상 서버에서 사용할 수 없습니다."</span><span class="sxs-lookup"><span data-stu-id="1a006-118">"The job step requires a proxy account, however proxy matching is disabled on the target server."</span></span>  
  
     <span data-ttu-id="1a006-119">이 오류를 해결하려면 **AllowDownloadedJobsToMatchProxyName** 레지스트리 하위 키를 1로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-119">To resolve this error, set the **AllowDownloadedJobsToMatchProxyName** registry subkey to 1.</span></span>  
  
-   <span data-ttu-id="1a006-120">"프록시를 찾을 수 없습니다."</span><span class="sxs-lookup"><span data-stu-id="1a006-120">"Proxy not found."</span></span>  
  
     <span data-ttu-id="1a006-121">이 오류를 해결하려면 프록시 계정이 작업 단계가 실행되는 마스터 서버 프록시 계정과 동일한 이름을 가진 대상 서버에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-121">To resolve this error, make sure a proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1a006-122">권한</span><span class="sxs-lookup"><span data-stu-id="1a006-122">Permissions</span></span>  
 <span data-ttu-id="1a006-123">이 프로시저를 실행할 수 있는 권한은 기본적으로 `sysadmin` 고정 서버 역할의 멤버로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-123">Permissions to execute this procedure default to members of the `sysadmin` fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1a006-124">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="1a006-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-make-a-master-server"></a><span data-ttu-id="1a006-125">마스터 서버를 만들려면</span><span class="sxs-lookup"><span data-stu-id="1a006-125">To make a master server</span></span>  
  
1.  <span data-ttu-id="1a006-126">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-126">In **Object Explorer,** connect to an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="1a006-127">**SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭하고 **다중 서버 관리**를 가리킨 다음 **마스터로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-127">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Make this a Master**.</span></span> <span data-ttu-id="1a006-128">**마스터 서버 마법사** 는 마스터 서버를 만들고 대상 서버를 추가하는 프로세스를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-128">The **Master Server Wizard** guides you through the process of making a master server and adding target servers.</span></span>  
  
3.  <span data-ttu-id="1a006-129">**마스터 서버 운영자** 페이지에서 마스터 서버 운영자를 구성합니다. 전자 메일 또는 호출기를 사용하여 운영자에게 알림을 보내려면 전자 메일을 보내도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-129">From the **Master Server Operator** page, configure an operator for the master server To send notifications to operators by using e-mail or pagers, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to send e-mail.</span></span> <span data-ttu-id="1a006-130">**net send**를 사용하여 운영자에게 알림을 보내려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 설치된 서버에서 메신저 서비스가 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-130">To send notifications to operators by using **net send**, the Messenger service must be running on the server where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent resides.</span></span>  
  
     <span data-ttu-id="1a006-131">**전자 메일 주소**</span><span class="sxs-lookup"><span data-stu-id="1a006-131">**E-mail address**</span></span>  
     <span data-ttu-id="1a006-132">운영자의 전자 메일 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-132">Sets the e-mail address for the operator.</span></span>  
  
     <span data-ttu-id="1a006-133">**호출기 주소**</span><span class="sxs-lookup"><span data-stu-id="1a006-133">**Pager address**</span></span>  
     <span data-ttu-id="1a006-134">운영자의 호출기 전자 메일 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-134">Sets the pager e-mail address for the operator.</span></span>  
  
     <span data-ttu-id="1a006-135">**Net Send 주소**</span><span class="sxs-lookup"><span data-stu-id="1a006-135">**Net send address**</span></span>  
     <span data-ttu-id="1a006-136">운영자에 대한 **net send** 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-136">Sets the **net send** address for the operator.</span></span>  
  
4.  <span data-ttu-id="1a006-137">**대상 서버** 페이지에서 마스터 서버의 대상 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-137">From the **Target Server** page, select target servers for the master server.</span></span>  
  
     <span data-ttu-id="1a006-138">**등록된 서버**</span><span class="sxs-lookup"><span data-stu-id="1a006-138">**Registered Servers**</span></span>  
     <span data-ttu-id="1a006-139">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에 등록된 서버 중 대상 서버가 아닌 서버를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-139">Lists the servers registered in Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] that are not already target servers.</span></span>  
  
     <span data-ttu-id="1a006-140">**대상 서버**</span><span class="sxs-lookup"><span data-stu-id="1a006-140">**Target Servers**</span></span>  
     <span data-ttu-id="1a006-141">대상 서버를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-141">Lists the servers that are target servers.</span></span>  
  
     **>**  
     <span data-ttu-id="1a006-142">선택한 서버를 대상 서버 목록으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-142">Move the selected server to the target server list.</span></span>  
  
     **>>**  
     <span data-ttu-id="1a006-143">모든 서버를 대상 서버 목록으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-143">Move all servers to the target server list.</span></span>  
  
     **<**  
     <span data-ttu-id="1a006-144">선택한 서버를 대상 서버 목록에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-144">Remove the selected server from the target server list.</span></span>  
  
     **<<**  
     <span data-ttu-id="1a006-145">모든 서버를 대상 서버 목록에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-145">Remove all servers from the target server list.</span></span>  
  
     <span data-ttu-id="1a006-146">**연결 추가**</span><span class="sxs-lookup"><span data-stu-id="1a006-146">**Add connection**</span></span>  
     <span data-ttu-id="1a006-147">서버를 등록하지 않고 대상 서버 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-147">Add a server to the target server list without registering the server.</span></span>  
  
     <span data-ttu-id="1a006-148">**연결**</span><span class="sxs-lookup"><span data-stu-id="1a006-148">**Connection**</span></span>  
     <span data-ttu-id="1a006-149">선택한 서버의 연결 속성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-149">Change the connection properties for the selected server.</span></span>  
  
5.  <span data-ttu-id="1a006-150">**마스터 서버 로그인 자격 증명** 페이지에서 대상 서버에 대해 새 로그인을 만들지 여부와 필요한 경우 해당 로그인에 마스터 서버에 대한 권한을 부여할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-150">From the **Master Server Login Credentials** page to specify if you want to create a new login for the target server, if necessary, and assign it rights to the master server.</span></span>  
  
     <span data-ttu-id="1a006-151">**필요한 경우 새 로그인을 만들고 MSX에 대한 권한을 할당합니다.**</span><span class="sxs-lookup"><span data-stu-id="1a006-151">**Create a new login if necessary and assign it rights to the MSX**</span></span>  
     <span data-ttu-id="1a006-152">지정한 로그인이 없으면 대상 서버에 새 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-152">Create a new login on the target server if the login specified does not already exist.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1a006-153">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="1a006-153">Using Transact-SQL</span></span>  
  
#### <a name="to-make-a-master-server"></a><span data-ttu-id="1a006-154">마스터 서버를 만들려면</span><span class="sxs-lookup"><span data-stu-id="1a006-154">To make a master server</span></span>  
  
1.  <span data-ttu-id="1a006-155">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-155">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1a006-156">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-156">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1a006-157">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-157">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1a006-158">이 예에서는 현재 서버를 AdventureWorks1 마스터 서버에 참여시킵니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-158">This example enlists the current server into the AdventureWorks1 master server.</span></span> <span data-ttu-id="1a006-159">현재 서버의 위치는 Building 21, Room 309, Rack 5입니다.</span><span class="sxs-lookup"><span data-stu-id="1a006-159">The location for the current server is Building 21, Room 309, Rack 5.</span></span>  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_msx_enlist N'AdventureWorks1',   
    N'Building 21, Room 309, Rack 5' ;   
GO;  
```  
  
 <span data-ttu-id="1a006-160">자세한 내용은 [sp_msx_enlist &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1a006-160">For more information, see [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a006-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1a006-161">See Also</span></span>  
 <span data-ttu-id="1a006-162">[다중 서버 환경 만들기](create-a-multiserver-environment.md) </span><span class="sxs-lookup"><span data-stu-id="1a006-162">[Create a Multiserver Environment](create-a-multiserver-environment.md) </span></span>  
 [<span data-ttu-id="1a006-163">기업 내 관리 자동화</span><span class="sxs-lookup"><span data-stu-id="1a006-163">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
  
  
