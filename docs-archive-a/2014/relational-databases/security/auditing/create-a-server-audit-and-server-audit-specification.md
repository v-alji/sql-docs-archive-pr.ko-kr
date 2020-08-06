---
title: 서버 감사 및 서버 감사 사양 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.SQLAUDIT.FILTER.F1
- sql12.swb.sqlaudit.srvaudit.general.f1
- sql12.swb.sqlaudit.general.f1
helpviewer_keywords:
- server audit [SQL Server]
- audits [SQL Server], specification
ms.assetid: 6624b1ab-7ec8-44ce-8292-397edf644394
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a648a975ae9f2c4139a8ebd584f6998f4d0fa1a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732515"
---
# <a name="create-a-server-audit-and-server-audit-specification"></a><span data-ttu-id="5581f-102">서버 감사 및 서버 감사 사양 만들기</span><span class="sxs-lookup"><span data-stu-id="5581f-102">Create a Server Audit and Server Audit Specification</span></span>
  <span data-ttu-id="5581f-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 서버 감사 및 서버 감사 사양을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-103">This topic describes how to create a server audit and server audit specification in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="5581f-104">*인스턴스 또는* 데이터베이스 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 감사 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에는 시스템에서 발생하는 추적 이벤트 및 로깅 이벤트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-104">*Auditing* an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database involves tracking and logging events that occur on the system.</span></span> <span data-ttu-id="5581f-105">*SQL Server Audit* 개체는 사용자가 모니터링하려는 서버 또는 데이터베이스 수준 동작 및 동작 그룹에 대한 하나의 인스턴스를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-105">The *SQL Server Audit* object collects a single instance of server- or database-level actions and groups of actions to monitor.</span></span> <span data-ttu-id="5581f-106">감사는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스 수준으로 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-106">The audit is at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance level.</span></span> <span data-ttu-id="5581f-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스별로 여러 개의 감사를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-107">You can have multiple audits per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="5581f-108">*서버 감사 사양* 개체는 감사에 속해 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-108">The *Server Audit Specification* object belongs to an audit.</span></span> <span data-ttu-id="5581f-109">서버 감사 사양과 감사는 모두 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스 범위에서 생성되므로 감사당 하나의 서버 감사 사양을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-109">You can create one server audit specification per audit, because both are created at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance scope.</span></span> <span data-ttu-id="5581f-110">자세한 내용은 [SQL Server Audit&#40;데이터베이스 엔진&#41;](sql-server-audit-database-engine.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5581f-110">For more information, see [SQL Server Audit &#40;Database Engine&#41;](sql-server-audit-database-engine.md).</span></span>  
  
 <span data-ttu-id="5581f-111">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="5581f-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5581f-112">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="5581f-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5581f-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="5581f-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="5581f-114">보안</span><span class="sxs-lookup"><span data-stu-id="5581f-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5581f-115">**다음을 사용하여 서버 감사 및 서버 감사 사양을 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="5581f-115">**To create a server audit and server audit specification, using:**</span></span>  
  
     [<span data-ttu-id="5581f-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5581f-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5581f-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5581f-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5581f-118">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="5581f-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="5581f-119">제한 사항</span><span class="sxs-lookup"><span data-stu-id="5581f-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="5581f-120">감사가 있어야 이에 대한 서버 감사 사양을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-120">An audit must exist before creating a server audit specification for it.</span></span> <span data-ttu-id="5581f-121">서버 감사 사양을 처음 만들 때는 사용할 수 없는 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-121">When a server audit specification is created, it is in a disabled state.</span></span>  
  
-   <span data-ttu-id="5581f-122">CREATE SERVER AUDIT 문은 트랜잭션 범위 내에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-122">The CREATE SERVER AUDIT statement is in a transaction's scope.</span></span> <span data-ttu-id="5581f-123">트랜잭션이 롤백되면 이 문도 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-123">If the transaction is rolled back, the statement is also rolled back.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5581f-124">보안</span><span class="sxs-lookup"><span data-stu-id="5581f-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5581f-125">권한</span><span class="sxs-lookup"><span data-stu-id="5581f-125">Permissions</span></span>  
  
-   <span data-ttu-id="5581f-126">서버 감사를 생성, 변경 또는 삭제하려면 보안 주체에게 ALTER ANY SERVER AUDIT 또는 CONTROL SERVER 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-126">To create, alter, or drop a server audit, principals require the ALTER ANY SERVER AUDIT or the CONTROL SERVER permission.</span></span>  
  
-   <span data-ttu-id="5581f-127">ALTER ANY SERVER AUDIT 권한이 있는 사용자는 서버 감사 사양을 만들어 모든 감사에 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-127">Users with the ALTER ANY SERVER AUDIT permission can create server audit specifications and bind them to any audit.</span></span>  
  
-   <span data-ttu-id="5581f-128">만들어진 서버 감사 사양은 CONTROL SERVER 또는 ALTER ANY SERVER AUDIT 권한이 있는 보안 주체, sysadmin 계정 또는 감사에 대한 명시적인 액세스가 있는 보안 주체가 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-128">After a server audit specification is created, it can be viewed by principals with the CONTROL SERVER or ALTER ANY SERVER AUDIT permissions, the sysadmin account, or principals having explicit access to the audit.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5581f-129">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="5581f-129">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-server-audit"></a><span data-ttu-id="5581f-130">서버 감사를 만들려면</span><span class="sxs-lookup"><span data-stu-id="5581f-130">To create a server audit</span></span>  
  
1.  <span data-ttu-id="5581f-131">개체 탐색기에서 **보안** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-131">In Object Explorer, expand the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="5581f-132">**감사** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 감사...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-132">Right-click the **Audits** folder and select **New Audit...**.</span></span>  
  
     <span data-ttu-id="5581f-133">**감사 만들기** 대화 상자의 **일반** 페이지에는 다음과 같은 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-133">The following options are available on the **General** page of the **Create Audit** dialog box.</span></span>  
  
     <span data-ttu-id="5581f-134">**감사 이름**</span><span class="sxs-lookup"><span data-stu-id="5581f-134">**Audit name**</span></span>  
     <span data-ttu-id="5581f-135">감사의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-135">The name of the audit.</span></span> <span data-ttu-id="5581f-136">이는 새 감사를 만들 때 자동으로 생성되지만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-136">This is generated automatically when you create a new audit but is editable.</span></span>  
  
     <span data-ttu-id="5581f-137">**큐 지연(밀리초)**</span><span class="sxs-lookup"><span data-stu-id="5581f-137">**Queue delay (in milliseconds)**</span></span>  
     <span data-ttu-id="5581f-138">감사 동작이 강제 처리되기 전까지 허용되는 시간(밀리초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-138">Specifies the amount of time in milliseconds that can elapse before audit actions are forced to be processed.</span></span>  <span data-ttu-id="5581f-139">값이 0인 경우 동기 배달을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-139">A value of 0 indicates synchronous delivery.</span></span> <span data-ttu-id="5581f-140">기본 최소값은 **1000** (1초)입니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-140">The default minimum value is **1000** (1 second).</span></span> <span data-ttu-id="5581f-141">최대값은 2,147,483,647로 2,147,483.647초 또는 24일, 20시간, 31분, 23.647초에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-141">The maximum is 2,147,483,647 (2,147,483.647 seconds or 24 days, 20 hours, 31 minutes, 23.647 seconds).</span></span>  
  
     <span data-ttu-id="5581f-142">**감사 로그 실패 시:**</span><span class="sxs-lookup"><span data-stu-id="5581f-142">**On Audit Log Failure:**</span></span>  
     <span data-ttu-id="5581f-143">**계속**</span><span class="sxs-lookup"><span data-stu-id="5581f-143">**Continue**</span></span>  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="5581f-144">작업을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-144">operations continue.</span></span> <span data-ttu-id="5581f-145">감사 레코드는 보존되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-145">Audit records are not retained.</span></span> <span data-ttu-id="5581f-146">감사는 계속해서 이벤트 기록을 시도하며 실패 조건이 해결되면 재개됩니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-146">The audit continues to attempt to log events and will resume if the failure condition is resolved.</span></span> <span data-ttu-id="5581f-147">**계속** 옵션을 선택하면 감사되지 않는 작업이 허용되어 보안 정책을 위반할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-147">Selecting the **Continue** option can allow unaudited activity which could violate your security policies.</span></span> <span data-ttu-id="5581f-148">전체 감사를 유지 관리하는 것보다 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 의 작업을 계속하는 것이 더 중요하면 이 옵션을 선택하세요.</span><span class="sxs-lookup"><span data-stu-id="5581f-148">Select this option when continuing operation of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] is more important than maintaining a complete audit.</span></span> <span data-ttu-id="5581f-149">이 옵션이 기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-149">This is the default selection.</span></span>  
  
     <span data-ttu-id="5581f-150">**서버 종료**</span><span class="sxs-lookup"><span data-stu-id="5581f-150">**Shut down server**</span></span>  
     <span data-ttu-id="5581f-151">대상에 쓰기 작업을 수행하는 서버 인스턴스가 감사 대상에 데이터를 쓰지 못할 경우 서버를 강제 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-151">Forces a server shut down when the server instance writing to the target cannot write data to the audit target.</span></span> <span data-ttu-id="5581f-152">이 함수를 실행하는 로그인에는 `SHUTDOWN` 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-152">The login issuing this must have the `SHUTDOWN` permission.</span></span> <span data-ttu-id="5581f-153">이 권한이 없으면 이 함수가 실패하고 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-153">If the logon does not have this permission, this function will fail and an error message will be raised.</span></span> <span data-ttu-id="5581f-154">감사된 이벤트가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-154">No audited events occur.</span></span> <span data-ttu-id="5581f-155">감사 실패로 인해 시스템 무결성 또는 보안이 손상될 수 있는 경우 이 옵션을 선택하세요.</span><span class="sxs-lookup"><span data-stu-id="5581f-155">Select this option when an audit failure could compromise the security or integrity of the system.</span></span>  
  
     <span data-ttu-id="5581f-156">**작업 실패**</span><span class="sxs-lookup"><span data-stu-id="5581f-156">**Fail operation**</span></span>  
     <span data-ttu-id="5581f-157">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 감사에서 감사 로그에 쓸 수 없는 경우 이 옵션을 선택하면 정상적인 경우에는 감사된 이벤트를 발생시키는 데이터베이스 동작이 실패하며,</span><span class="sxs-lookup"><span data-stu-id="5581f-157">In cases where the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit cannot write to the audit log this option causes database actions to fail if they would otherwise cause audited events.</span></span> <span data-ttu-id="5581f-158">감사된 이벤트가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-158">No audited events occur.</span></span> <span data-ttu-id="5581f-159">감사된 이벤트를 발생시키지 않는 동작은 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-159">Actions which do not cause audited events can continue.</span></span> <span data-ttu-id="5581f-160">감사는 계속해서 이벤트 기록을 시도하며 실패 조건이 해결되면 재개됩니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-160">The audit continues to attempt to log events and will resume if the failure condition is resolved.</span></span> <span data-ttu-id="5581f-161">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]에 대한 모든 권한을 얻는 것보다 전체 감사를 유지 관리하는 것이 더 중요하면 이 옵션을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="5581f-161">Select this option when maintaining a complete audit is more important than full access to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="5581f-162">감사가 실패한 상태여도 관리자 전용 연결에서는 감사된 이벤트를 계속 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-162">When the audit is in a failed state, the Dedicated Administrator Connection can continue to perform audited events.</span></span>  
  
     <span data-ttu-id="5581f-163">**감사 대상** 목록</span><span class="sxs-lookup"><span data-stu-id="5581f-163">**Audit destination** list</span></span>  
     <span data-ttu-id="5581f-164">데이터를 감사할 대상을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-164">Specifies the target for auditing data.</span></span> <span data-ttu-id="5581f-165">이진 파일, Windows 애플리케이션 로그, Windows 보안 로그 등이 감사 대상이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-165">The available options are a binary file, the Windows Application log, or the Windows Security log.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="5581f-166">가 Windows 보안 로그에 쓸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-166">cannot write to the Windows Security log without configuring additional settings in Windows.</span></span> <span data-ttu-id="5581f-167">자세한 내용은 [보안 로그에 SQL Server Audit 이벤트 쓰기](write-sql-server-audit-events-to-the-security-log.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5581f-167">For more information, see [Write SQL Server Audit Events to the Security Log](write-sql-server-audit-events-to-the-security-log.md).</span></span>  
  
     <span data-ttu-id="5581f-168">**파일 경로**</span><span class="sxs-lookup"><span data-stu-id="5581f-168">**File path**</span></span>  
     <span data-ttu-id="5581f-169">**감사 대상** 이 파일인 경우 감사 데이터를 쓸 폴더의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-169">Specifies the location of the folder where audit data is written when the **Audit destination** is a file.</span></span>  
  
     <span data-ttu-id="5581f-170">**줄임표(...)**</span><span class="sxs-lookup"><span data-stu-id="5581f-170">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="5581f-171">파일 경로를 지정 하거나 감사 파일이 기록 된 폴더를 만들 폴더 **찾기-**_server_name_ 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-171">Opens the **Locate Folder -**_server_name_ dialog box to specify a file path or create a folder where the audit file is written.</span></span>  
  
     <span data-ttu-id="5581f-172">**감사 파일의 최대 제한:**</span><span class="sxs-lookup"><span data-stu-id="5581f-172">**Audit File Maximum Limit:**</span></span>  
     <span data-ttu-id="5581f-173">**최대 롤오버 파일**</span><span class="sxs-lookup"><span data-stu-id="5581f-173">**Maximum rollover files**</span></span>  
     <span data-ttu-id="5581f-174">감사 파일의 최대 수에 도달하면 가장 오래된 감사 파일을 새 파일 내용으로 덮어쓰도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-174">Specifies that, when the maximum number of audit files is reached, the oldest audit files are overwritten by new file content.</span></span>  
  
     <span data-ttu-id="5581f-175">**최대 파일**</span><span class="sxs-lookup"><span data-stu-id="5581f-175">**Maximum files**</span></span>  
     <span data-ttu-id="5581f-176">최대 감사 파일 수에 도달하면 추가 감사 이벤트를 생성하는 동작이 실패하며 오류가 발생하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-176">Specifies that, when the maximum number of audit files is reached, any action that causes additional audit events to be generated will fail with an error.</span></span>  
  
     <span data-ttu-id="5581f-177">**무제한** 확인란</span><span class="sxs-lookup"><span data-stu-id="5581f-177">**Unlimited** check box</span></span>  
     <span data-ttu-id="5581f-178">**최대 롤오버 파일** 아래의 **무제한** 확인란이 선택된 경우 만들려는 감사 파일 수에 대한 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-178">When the **Unlimited** check box under **Maximum rollover files** is selected, there is no limit imposed on the number of audit files that will be created.</span></span> <span data-ttu-id="5581f-179">**무제한** 확인란은 기본적으로 선택되며 **최대 롤오버 파일** 및 **최대 파일** 선택 사항에 모두 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-179">The **Unlimited** check box is selected by default and applies to both the **Maximum rollover files** and **Maximum files** selections.</span></span>  
  
     <span data-ttu-id="5581f-180">**파일 수** 상자</span><span class="sxs-lookup"><span data-stu-id="5581f-180">**Number of files** box</span></span>  
     <span data-ttu-id="5581f-181">만들려는 감사 파일 수를 최대 2,147,483,647까지 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-181">Specifies the number of audit files to be created, up to 2,147,483,647.</span></span> <span data-ttu-id="5581f-182">이 옵션은 **무제한** 을 선택 취소한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-182">This option is only available if **Unlimited** is unchecked.</span></span>  
  
     <span data-ttu-id="5581f-183">**최대 파일 크기**</span><span class="sxs-lookup"><span data-stu-id="5581f-183">**Maximum file size**</span></span>  
     <span data-ttu-id="5581f-184">MB(메가바이트), GB(기가바이트) 또는 TB(테라바이트) 단위로 감사 파일의 최대 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-184">Specifies the maximum size for an audit file in either megabytes (MB), gigabytes (GB), or terabytes (TB).</span></span> <span data-ttu-id="5581f-185">1,024MB와 2,147,483,647TB 사이로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-185">You can specify between 1024 MB and 2,147,483,647 TB.</span></span> <span data-ttu-id="5581f-186">**무제한** 확인란을 선택하면 파일 크기에 대한 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-186">Selecting the **Unlimited** check box does not place a limit on the size of the file.</span></span> <span data-ttu-id="5581f-187">1024MB보다 작은 값을 지정하면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-187">Specifying a value lower than 1024 MB will fail, returning an error.</span></span> <span data-ttu-id="5581f-188">**무제한** 확인란은 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-188">The **Unlimited** check box is selected by default.</span></span>  
  
     <span data-ttu-id="5581f-189">**디스크 공간 예약** 확인란</span><span class="sxs-lookup"><span data-stu-id="5581f-189">**Reserve disk space** check box</span></span>  
     <span data-ttu-id="5581f-190">지정된 최대 파일 크기와 동일한 공간이 디스크에 미리 할당되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-190">Specifies that space is pre-allocated on the disk equal to the specified maximum file size.</span></span> <span data-ttu-id="5581f-191">이 설정은 **최대 파일 크기** 아래에서 **무제한** 을 선택하지 않은 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-191">This setting can only be used if the **Unlimited** check box under **Maximum file size** is not selected.</span></span> <span data-ttu-id="5581f-192">이 확인란은 기본적으로 선택되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-192">This check box is not selected by default.</span></span>  
  
3.  <span data-ttu-id="5581f-193">또는 **필터** 페이지에서 조건자를 입력하거나 `WHERE` 절을 서버 감사에 입력하여 **일반** 페이지에서 사용할 수 없는 추가 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-193">Optionally, on the **Filter** page, enter a predicate, or `WHERE` clause, to the server audit to specify additional options not available from the **General** page.</span></span> <span data-ttu-id="5581f-194">조건자를 괄호로 묶습니다. 예: `(object_name = 'EmployeesTable')`</span><span class="sxs-lookup"><span data-stu-id="5581f-194">Enclose the predicate in parentheses; for example: `(object_name = 'EmployeesTable')`.</span></span>  
  
4.  <span data-ttu-id="5581f-195">옵션 선택을 마쳤으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-195">When you are finished selecting options, click **OK**.</span></span>  
  
#### <a name="to-create-a-server-audit-specification"></a><span data-ttu-id="5581f-196">서버 감사 사양을 만들려면</span><span class="sxs-lookup"><span data-stu-id="5581f-196">To create a server audit specification</span></span>  
  
1.  <span data-ttu-id="5581f-197">개체 탐색기에서 더하기 기호를 클릭하여 **보안** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-197">In Object Explorer, click the plus sign to expand the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="5581f-198">**서버 감사 사양** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 서버 감사 사양...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-198">Right-click the **Server Audit Specifications** folder and select **New Server Audit Specification...**.</span></span>  
  
     <span data-ttu-id="5581f-199">**서버 감사 사양 만들기** 대화 상자에는 다음과 같은 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-199">The following options are available on the **Create Server Audit Specification** dialog box.</span></span>  
  
     <span data-ttu-id="5581f-200">**이름**</span><span class="sxs-lookup"><span data-stu-id="5581f-200">**Name**</span></span>  
     <span data-ttu-id="5581f-201">서버 감사 사양의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-201">The name of the server audit specification.</span></span> <span data-ttu-id="5581f-202">새 서버 감사 사양을 만들 때 자동 생성되지만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-202">This is generated automatically when you create a new server audit specification but is editable.</span></span>  
  
     <span data-ttu-id="5581f-203">**감사**</span><span class="sxs-lookup"><span data-stu-id="5581f-203">**Audit**</span></span>  
     <span data-ttu-id="5581f-204">기존 서버 감사의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-204">The name of an existing server audit.</span></span> <span data-ttu-id="5581f-205">감사 이름을 입력하거나 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-205">Either type in the name of the audit or select it from the list.</span></span>  
  
     <span data-ttu-id="5581f-206">**감사 동작 유형**</span><span class="sxs-lookup"><span data-stu-id="5581f-206">**Audit Action Type**</span></span>  
     <span data-ttu-id="5581f-207">캡처할 서버 수준 감사 동작 그룹 및 감사 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-207">Specifies the server-level audit action groups and audit actions to capture.</span></span> <span data-ttu-id="5581f-208">서버 수준 감사 동작 그룹 및 감사 동작의 목록과 여기에 포함된 이벤트에 대한 설명은 [SQL Server Audit 동작 그룹 및 동작](sql-server-audit-action-groups-and-actions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5581f-208">For the list of server-level audit action groups and audit actions and a description of the events they contain, see [SQL Server Audit Action Groups and Actions](sql-server-audit-action-groups-and-actions.md).</span></span>  
  
     <span data-ttu-id="5581f-209">**개체 스키마**</span><span class="sxs-lookup"><span data-stu-id="5581f-209">**Object Schema**</span></span>  
     <span data-ttu-id="5581f-210">지정된 **개체 이름**에 대한 스키마를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-210">Displays the schema for the specified **Object Name**.</span></span>  
  
     <span data-ttu-id="5581f-211">**개체 이름**</span><span class="sxs-lookup"><span data-stu-id="5581f-211">**Object Name**</span></span>  
     <span data-ttu-id="5581f-212">감사할 개체의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-212">The name of the object to audit.</span></span> <span data-ttu-id="5581f-213">이 이름은 감사 동작에만 사용할 수 있으며 감사 그룹에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-213">This is only available for audit actions; it does not apply to audit groups.</span></span>  
  
     <span data-ttu-id="5581f-214">**줄임표(...)**</span><span class="sxs-lookup"><span data-stu-id="5581f-214">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="5581f-215">**개체 선택** 대화 상자를 열고 지정된 **감사 동작 유형**에 따라 사용 가능한 개체를 찾아 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-215">Opens the **Select Objects** dialog to browse for and select an available object, based on the specified **Audit Action Type**.</span></span>  
  
     <span data-ttu-id="5581f-216">**보안 주체 이름**</span><span class="sxs-lookup"><span data-stu-id="5581f-216">**Principal Name**</span></span>  
     <span data-ttu-id="5581f-217">감사 중인 개체에 대한 감사 필터링의 기준이 되는 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-217">The account to filter the audit by for the object being audited.</span></span>  
  
     <span data-ttu-id="5581f-218">**줄임표(...)**</span><span class="sxs-lookup"><span data-stu-id="5581f-218">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="5581f-219">**개체 선택** 대화 상자를 열고 지정된 **개체 이름**에 따라 사용 가능한 개체를 찾아 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-219">Opens the **Select Objects** dialog to browse for and select an available object, based on the specified **Object Name**.</span></span>  
  
3.  <span data-ttu-id="5581f-220">작업을 마쳤으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-220">When you are finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5581f-221">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="5581f-221">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-server-audit"></a><span data-ttu-id="5581f-222">서버 감사를 만들려면</span><span class="sxs-lookup"><span data-stu-id="5581f-222">To create a server audit</span></span>  
  
1.  <span data-ttu-id="5581f-223">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-223">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5581f-224">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-224">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5581f-225">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-225">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates a server audit called "HIPAA_Audit" with a binary file as the target and no options.  
    CREATE SERVER AUDIT HIPAA_Audit  
        TO FILE ( FILEPATH ='\\SQLPROD_1\Audit\' );  
    ```  
  
#### <a name="to-create-a-server-audit-specification"></a><span data-ttu-id="5581f-226">서버 감사 사양을 만들려면</span><span class="sxs-lookup"><span data-stu-id="5581f-226">To create a server audit specification</span></span>  
  
1.  <span data-ttu-id="5581f-227">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-227">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5581f-228">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-228">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5581f-229">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5581f-229">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    /*Creates a server audit specification called "HIPAA_Audit_Specification" that audits failed logins for the SQL Server audit "HIPAA_Audit" created above.  
    */  
  
    CREATE SERVER AUDIT SPECIFICATION HIPAA_Audit_Specification  
    FOR SERVER AUDIT HIPAA_Audit  
        ADD (FAILED_LOGIN_GROUP);  
    GO  
    -- Enables the audit.   
  
    ALTER SERVER AUDIT HIPAA_Audit  
    WITH (STATE = ON);  
    GO  
    ```  
  
 <span data-ttu-id="5581f-230">자세한 내용은 [CREATE SERVER AUDIT&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql) 및 [CREATE SERVER AUDIT SPECIFICATION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-specification-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5581f-230">For more information, see [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql) and [CREATE SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-specification-transact-sql).</span></span>  
  
  
