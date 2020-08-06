---
title: MSSQL_ENG021797 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021797 error
ms.assetid: 54d83a1e-43fd-449c-a2b2-fdda2609a534
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d33ade7e7eea9fa9e95453a5b232447f7b222b18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730495"
---
# <a name="mssql_eng021797"></a><span data-ttu-id="26329-102">MSSQL_ENG021797</span><span class="sxs-lookup"><span data-stu-id="26329-102">MSSQL_ENG021797</span></span>
    
## <a name="message-details"></a><span data-ttu-id="26329-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="26329-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="26329-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="26329-104">Product Name</span></span>|<span data-ttu-id="26329-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="26329-105">SQL Server</span></span>|  
|<span data-ttu-id="26329-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="26329-106">Event ID</span></span>|<span data-ttu-id="26329-107">21797</span><span class="sxs-lookup"><span data-stu-id="26329-107">21797</span></span>|  
|<span data-ttu-id="26329-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="26329-108">Event Source</span></span>|<span data-ttu-id="26329-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="26329-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="26329-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="26329-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="26329-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="26329-111">Symbolic Name</span></span>||  
|<span data-ttu-id="26329-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="26329-112">Message Text</span></span>|<span data-ttu-id="26329-113">‘%s’은(는) '머신\\로그인' 또는 '도메인\\로그인' 형식의 올바른 Windows 로그인이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26329-113">'%s' must be a valid Windows Login in the form: 'MACHINE\Login' or 'DOMAIN\Login'.</span></span> <span data-ttu-id="26329-114">'%s'에 대한 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="26329-114">Please see the documentation for '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="26329-115">설명</span><span class="sxs-lookup"><span data-stu-id="26329-115">Explanation</span></span>  
 <span data-ttu-id="26329-116">이 오류는 매개 변수에 지정 된 값이 null 이거나 잘못 된 경우 다음 복제 저장 프로시저에 의해 발생 **@job_login** 합니다.</span><span class="sxs-lookup"><span data-stu-id="26329-116">This error is raised by the following replication stored procedures if the value specified for the **@job_login** parameter is null or not valid.</span></span> <span data-ttu-id="26329-117">이 오류는 **db_owner** 고정 데이터베이스 역할의 멤버가 이전 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전의 스크립트를 실행하는 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26329-117">This error can occur if a member of the **db_owner** fixed database role runs scripts from previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="26329-118">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서는 보안 모델이 변경되었으므로 이러한 스크립트를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26329-118">The security model changed in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], and these scripts must be updated.</span></span>  
  
-   [<span data-ttu-id="26329-119">sp_addlogreader_agent&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26329-119">sp_addlogreader_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql)  
  
-   [<span data-ttu-id="26329-120">sp_addqreader_agent&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26329-120">sp_addqreader_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql)  
  
-   [<span data-ttu-id="26329-121">sp_addpublication_snapshot&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26329-121">sp_addpublication_snapshot &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql)  
  
-   [<span data-ttu-id="26329-122">sp_addpushsubscription_agent&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26329-122">sp_addpushsubscription_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)  
  
-   [<span data-ttu-id="26329-123">sp_addpullsubscription_agent&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26329-123">sp_addpullsubscription_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)  
  
-   [<span data-ttu-id="26329-124">sp_addmergepushsubscription_agent&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26329-124">sp_addmergepushsubscription_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql)  
  
-   [<span data-ttu-id="26329-125">sp_addmergepullsubscription_agent&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26329-125">sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)  
  
 <span data-ttu-id="26329-126">이러한 저장 프로시저는 적절한 서버의 **sysadmin** 고정 서버 역할의 멤버나 적절한 데이터베이스의 **db_owner** 고정 데이터베이스 역할의 멤버만 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26329-126">These stored procedures can be executed by a member of the **sysadmin** fixed server role on the appropriate server or a member of the **db_owner** fixed database role in the appropriate database.</span></span> <span data-ttu-id="26329-127">저장 프로시저는 각각 에이전트 작업을 만들어 에이전트가 실행되는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 계정을 지정할 수 있게 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="26329-127">The stored procedures each create an agent job and allow you to specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the agent runs.</span></span> <span data-ttu-id="26329-128">역할이 **sysadmin** 인 사용자의 경우 Windows 계정이 지정되어 있지 않더라도(계정이 지정된 경우에는 올바른 계정이어야 함) 에이전트 작업이 암시적으로 생성됩니다. 에이전트는 적절한 서버의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 계정 컨텍스트 아래에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="26329-128">For users in the **sysadmin** role, agent jobs are created implicitly even if a Windows account is not specified (if an account is specified, it must be valid); agents run under the context of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account at the appropriate server.</span></span> <span data-ttu-id="26329-129">계정이 반드시 필요한 것은 아니지만 에이전트에 대해 별도의 계정을 지정하는 것은 보안을 위한 최선의 구현 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="26329-129">Although the account is not required, it is a security best practice to specify a separate account for the agents.</span></span> <span data-ttu-id="26329-130">자세한 내용은 [복제 에이전트 보안 모델](security/replication-agent-security-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26329-130">For more information, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="26329-131">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="26329-131">User Action</span></span>  
 <span data-ttu-id="26329-132">각 프로시저의 매개 변수에 대해 올바른 Windows 계정을 지정 해야 **@job_login** 합니다.</span><span class="sxs-lookup"><span data-stu-id="26329-132">Ensure you specify a valid Windows account for the **@job_login** parameter of each procedure.</span></span> <span data-ttu-id="26329-133">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 가져온 복제 스크립트를 사용할 경우 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에 필요한 저장 프로시저와 매개 변수를 포함하도록 스크립트를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="26329-133">If you have replication scripts from previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], update these scripts to include the stored procedures and parameters required by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="26329-134">자세한 내용은 [복제 스크립트 업그레이드&#40;복제 Transact-SQL 프로그래밍&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26329-134">For more information, see [Upgrade Replication Scripts &#40;Replication Transact-SQL Programming&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26329-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="26329-135">See Also</span></span>  
 [<span data-ttu-id="26329-136">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="26329-136">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
