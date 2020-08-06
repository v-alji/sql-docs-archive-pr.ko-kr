---
title: MSSQL_ENG021798 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021798 error
ms.assetid: 596f5092-75ab-4a19-8582-588687c7b089
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 327b4a373c28376701ea12400215ab00367df66a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730491"
---
# <a name="mssql_eng021798"></a><span data-ttu-id="77ac6-102">MSSQL_ENG021798</span><span class="sxs-lookup"><span data-stu-id="77ac6-102">MSSQL_ENG021798</span></span>
    
## <a name="message-details"></a><span data-ttu-id="77ac6-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="77ac6-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77ac6-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="77ac6-104">Product Name</span></span>|<span data-ttu-id="77ac6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="77ac6-105">SQL Server</span></span>|  
|<span data-ttu-id="77ac6-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="77ac6-106">Event ID</span></span>|<span data-ttu-id="77ac6-107">21798</span><span class="sxs-lookup"><span data-stu-id="77ac6-107">21798</span></span>|  
|<span data-ttu-id="77ac6-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="77ac6-108">Event Source</span></span>|<span data-ttu-id="77ac6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="77ac6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="77ac6-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="77ac6-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="77ac6-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="77ac6-111">Symbolic Name</span></span>||  
|<span data-ttu-id="77ac6-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="77ac6-112">Message Text</span></span>|<span data-ttu-id="77ac6-113">계속하려면 먼저 '%s'을(를) 통해 '%s' 에이전트 작업을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77ac6-113">The '%s' agent job must be added through '%s' before continuing.</span></span> <span data-ttu-id="77ac6-114">'%s'에 대한 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="77ac6-114">Please see the documentation for '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="77ac6-115">설명</span><span class="sxs-lookup"><span data-stu-id="77ac6-115">Explanation</span></span>  
 <span data-ttu-id="77ac6-116">게시를 만들려면 게시자의 **sysadmin** 고정 서버 역할의 멤버 또는 게시 데이터베이스의 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77ac6-116">To create a publication, you must be a member of the **sysadmin** fixed server role on the Publisher or a member of the **db_owner** fixed database role in the publication database.</span></span> <span data-ttu-id="77ac6-117">**db_owner** 역할의 멤버인 경우 다음과 같은 상황에서 이 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="77ac6-117">If you are a member of the **db_owner** role, this error is raised if:</span></span>  
  
-   <span data-ttu-id="77ac6-118">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서 스크립트를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="77ac6-118">You run scripts from [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="77ac6-119">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서는 보안 모델이 변경되었으므로 이러한 스크립트를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77ac6-119">The security model changed in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], and these scripts must be updated.</span></span>  
  
-   <span data-ttu-id="77ac6-120">저장 프로시저 **sp_addpublication**은 [sp_addlogreader_agent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql)가 실행되기 전에 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="77ac6-120">The stored procedure **sp_addpublication** is executed before executing [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql).</span></span> <span data-ttu-id="77ac6-121">이 조건은 모든 트랜잭션 게시에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="77ac6-121">This applies to all transactional publications.</span></span>  
  
-   <span data-ttu-id="77ac6-122">저장 프로시저 **sp_addpublication**은 [sp_addqreader_agent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql)가 실행되기 전에 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="77ac6-122">The stored procedure **sp_addpublication** is executed before executing [sp_addqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql).</span></span> <span data-ttu-id="77ac6-123">이는 지연 업데이트 구독에 대해 설정 된 트랜잭션 게시에 적용 됩니다 (sp_addpublication 매개 변수의 값이 TRUE 인 경우 **@allow_queued_tran** ). **sp_addpublication**</span><span class="sxs-lookup"><span data-stu-id="77ac6-123">This applies to transactional publications that are enabled for queued updating subscriptions (a value of TRUE for the **@allow_queued_tran** parameter of **sp_addpublication**).</span></span>  
  
 <span data-ttu-id="77ac6-124">저장 프로시저 **sp_addlogreader_agent** 와 **sp_addqreader_agent** 는 각각 에이전트 작업을 만들고 에이전트가 실행되는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 계정을 지정할 수 있게 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="77ac6-124">The stored procedures **sp_addlogreader_agent** and **sp_addqreader_agent** each create an agent job and allow you to specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the agent runs.</span></span> <span data-ttu-id="77ac6-125">**sysadmin** 역할의 사용자인 경우 **sp_addlogreader_agent** 와 **sp_addqreader_agent** 가 실행되지 않으면 에이전트 작업이 암시적으로 생성됩니다. 에이전트는 배포자의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="77ac6-125">For users in the **sysadmin** role, agent jobs are created implicitly if **sp_addlogreader_agent** and **sp_addqreader_agent** are not executed; agents run under the context of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account at the Distributor.</span></span> <span data-ttu-id="77ac6-126">**sysadmin** 역할의 사용자에 **sp_addlogreader_agent** 와 **sp_addqreader_agent** 가 필요한 것은 아니지만 에이전트에 대해 별도의 계정을 지정하는 것이 보안을 위한 최선의 구현 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="77ac6-126">Although **sp_addlogreader_agent** and **sp_addqreader_agent** are not required for users in the **sysadmin** role, it is a security best practice to specify a separate account for the agents.</span></span> <span data-ttu-id="77ac6-127">자세한 내용은 [복제 에이전트 보안 모델](security/replication-agent-security-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="77ac6-127">For more information, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="77ac6-128">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="77ac6-128">User Action</span></span>  
 <span data-ttu-id="77ac6-129">프로시저를 올바른 순서로 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="77ac6-129">Ensure you execute procedures in the correct order.</span></span> <span data-ttu-id="77ac6-130">자세한 내용은 [게시 만들기](publish/create-a-publication.md)를 참조 하 고,이 스크립트를 업데이트 하 여 이상 버전에 필요한 저장 프로시저와 매개 변수를 포함 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="77ac6-130">For more information, see [Create a Publication](publish/create-a-publication.md), update these scripts to include the stored procedures and parameters required by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="77ac6-131">자세한 내용은 [복제 스크립트 업그레이드&#40;복제 Transact-SQL 프로그래밍&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="77ac6-131">For more information, see [Upgrade Replication Scripts &#40;Replication Transact-SQL Programming&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77ac6-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="77ac6-132">See Also</span></span>  
 [<span data-ttu-id="77ac6-133">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="77ac6-133">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
