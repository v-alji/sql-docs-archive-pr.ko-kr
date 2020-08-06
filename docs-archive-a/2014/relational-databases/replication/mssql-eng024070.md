---
title: MSSQL_ENG024070 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG024070 error
ms.assetid: 23ac7e00-fab6-429b-9f85-2736a322aa65
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07fcfcb96b284d46d46f63af4a650f925ef2de73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730487"
---
# <a name="mssql_eng024070"></a><span data-ttu-id="06cfc-102">MSSQL_ENG024070</span><span class="sxs-lookup"><span data-stu-id="06cfc-102">MSSQL_ENG024070</span></span>
    
## <a name="message-details"></a><span data-ttu-id="06cfc-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="06cfc-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="06cfc-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="06cfc-104">Product Name</span></span>|<span data-ttu-id="06cfc-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="06cfc-105">SQL Server</span></span>|  
|<span data-ttu-id="06cfc-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="06cfc-106">Event ID</span></span>|<span data-ttu-id="06cfc-107">24070</span><span class="sxs-lookup"><span data-stu-id="06cfc-107">24070</span></span>|  
|<span data-ttu-id="06cfc-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="06cfc-108">Event Source</span></span>|<span data-ttu-id="06cfc-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="06cfc-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="06cfc-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="06cfc-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="06cfc-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="06cfc-111">Symbolic Name</span></span>||  
|<span data-ttu-id="06cfc-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="06cfc-112">Message Text</span></span>|<span data-ttu-id="06cfc-113">클라이언트에 필수 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="06cfc-113">A required privilege is not held by the client.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="06cfc-114">설명</span><span class="sxs-lookup"><span data-stu-id="06cfc-114">Explanation</span></span>  
 <span data-ttu-id="06cfc-115">이 오류는 복제가 사용 중인지 여부에 관계없이 발생할 수 있는 일반 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="06cfc-115">This is a general error that can be raised regardless of whether replication is being used.</span></span> <span data-ttu-id="06cfc-116">복제 토폴로지의 서버에서 이 오류는 일반적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자 대신 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 서비스 제어 관리자를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 계정을 변경한 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="06cfc-116">For a server in a replication topology, the error is typically raised because the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account is changed by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Service Control Manager instead of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="06cfc-117">해당 서비스 계정을 변경한 후 에이전트 작업을 실행하려고 하면 작업이 실패하고 다음과 유사한 오류 메시지가 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06cfc-117">When you try to run an agent job after changing the service account, the job might fail with an error message that is similar to the following:</span></span>  
  
 <span data-ttu-id="06cfc-118">"사용자로 실행 됨 \<UserAccount> :</span><span class="sxs-lookup"><span data-stu-id="06cfc-118">"Executed as user: \<UserAccount>.</span></span> <span data-ttu-id="06cfc-119">복제-복제 스냅숏 하위 시스템: 에이전트가 \<AgentName> 실패 했습니다.</span><span class="sxs-lookup"><span data-stu-id="06cfc-119">Replication-Replication Snapshot Subsystem: agent \<AgentName> failed.</span></span> <span data-ttu-id="06cfc-120">사용자로 실행 됨 \<UserAccount> :</span><span class="sxs-lookup"><span data-stu-id="06cfc-120">Executed as user: \<UserAccount>.</span></span> <span data-ttu-id="06cfc-121">클라이언트에 필수 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="06cfc-121">A required privilege is not held by the client.</span></span> <span data-ttu-id="06cfc-122">단계가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="06cfc-122">The step failed.</span></span> <span data-ttu-id="06cfc-123">`[SQLSTATE 42000] (Error 14151)`.</span><span class="sxs-lookup"><span data-stu-id="06cfc-123">`[SQLSTATE 42000] (Error 14151)`.</span></span> <span data-ttu-id="06cfc-124">단계가 실패했습니다."</span><span class="sxs-lookup"><span data-stu-id="06cfc-124">The step failed."</span></span>  
  
 <span data-ttu-id="06cfc-125">이 문제는 Windows 서비스 제어 관리자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트의 새 서비스 계정에 필요한 권한을 부여할 수 없기 때문에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="06cfc-125">This problem occurs because the Windows Service Control Manager cannot grant the required permissions to the new service account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="06cfc-126">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="06cfc-126">User Action</span></span>  
 <span data-ttu-id="06cfc-127">앞으로 이 문제가 발생하지 않도록 하려면 항상 Windows 서비스 제어 관리자 대신 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 서비스 계정과 암호를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06cfc-127">To avoid this problem in the future, always use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager instead of the Windows Service Control Manager to change service accounts and passwords.</span></span>  
  
 <span data-ttu-id="06cfc-128">이 문제를 해결하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 서비스 계정을 다시 원래 계정으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="06cfc-128">To resolve this problem, use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to change the service account back to the original account.</span></span> <span data-ttu-id="06cfc-129">그런 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 새 계정으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="06cfc-129">Then, use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to change to the new account.</span></span> <span data-ttu-id="06cfc-130">이렇게 하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자는 다음 보안 그룹에 새 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="06cfc-130">When you do this, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager adds the new account to the following security group:</span></span>  
  
 <span data-ttu-id="06cfc-131">SQLServer2008SQLAgentUser$ComputerName$InstanceName</span><span class="sxs-lookup"><span data-stu-id="06cfc-131">SQLServer2008SQLAgentUser$ComputerName$InstanceName</span></span>  
  
 <span data-ttu-id="06cfc-132">이 보안 그룹의 멤버가 되는 새 사용자 계정에는 복제 에이전트 작업을 실행하는 데 필요한 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="06cfc-132">Being a member of this security group grants to the new account the required permissions to run the replication agent job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06cfc-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="06cfc-133">See Also</span></span>  
 <span data-ttu-id="06cfc-134">[오류 및 이벤트 참조&#40;복제&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="06cfc-134">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="06cfc-135">[복제의 로그인 및 암호 관리](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="06cfc-135">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 [<span data-ttu-id="06cfc-136">SQL Server 구성 관리자</span><span class="sxs-lookup"><span data-stu-id="06cfc-136">SQL Server Configuration Manager</span></span>](../sql-server-configuration-manager.md)  
  
  
