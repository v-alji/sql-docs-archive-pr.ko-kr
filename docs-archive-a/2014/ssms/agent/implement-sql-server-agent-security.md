---
title: SQL Server 에이전트 보안 구현 | Microsoft 문서
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, security
- security [SQL Server Agent], about security
- security [SQL Server Agent]
- security [SQL Server], SQL Server Agent
ms.assetid: d770d35c-c8de-4e00-9a85-7d03f45a0f0d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8b70449ace66d4e33a547eca1c0b19eafabde5a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731351"
---
# <a name="implement-sql-server-agent-security"></a><span data-ttu-id="0e4e7-102">SQL Server 에이전트 보안 구현</span><span class="sxs-lookup"><span data-stu-id="0e4e7-102">Implement SQL Server Agent Security</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0e4e7-103">에이전트를 사용하면 데이터베이스 관리자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 프록시에 의해 결정된 각 작업 단계를 수행하는 데 필요한 사용 권한만 있는 보안 컨텍스트에서 각 작업 단계를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-103">Agent lets the database administrator run each job step in a security context that has only the permissions required to perform that job step, which is determined by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy.</span></span> <span data-ttu-id="0e4e7-104">특정 작업 단계의 사용 권한을 설정하려면 필요 사용 권한을 가진 프록시를 만든 다음 해당 프록시를 작업 단계에 할당하십시오.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-104">To set the permissions for a particular job step, you create a proxy that has the required permissions and then assign that proxy to the job step.</span></span> <span data-ttu-id="0e4e7-105">프록시는 둘 이상의 작업 단계에 대해 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-105">A proxy can be specified for more than one job step.</span></span> <span data-ttu-id="0e4e7-106">동일 사용 권한이 필요한 작업 단계에 대해서는 동일한 프록시를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-106">For job steps that require the same permissions, you use the same proxy.</span></span>  
  
 <span data-ttu-id="0e4e7-107">다음 섹션에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 사용하여 작업을 만들거나 실행할 수 있도록 사용자에게 부여해야 하는 데이터베이스 역할에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-107">The following section explains what database role you must grant to users so they can create or execute jobs by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
## <a name="granting-access-to-sql-server-agent"></a><span data-ttu-id="0e4e7-108">SQL Server 에이전트에 액세스 부여</span><span class="sxs-lookup"><span data-stu-id="0e4e7-108">Granting Access to SQL Server Agent</span></span>  
 <span data-ttu-id="0e4e7-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 사용하려면 사용자가 다음 고정 데이터베이스 역할 중 하나 이상의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-109">To use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, users must be a member of one or more of the following fixed database roles:</span></span>  
  
-   <span data-ttu-id="0e4e7-110">**SQLAgentUserRole**</span><span class="sxs-lookup"><span data-stu-id="0e4e7-110">**SQLAgentUserRole**</span></span>  
  
-   <span data-ttu-id="0e4e7-111">**SQLAgentReaderRole**</span><span class="sxs-lookup"><span data-stu-id="0e4e7-111">**SQLAgentReaderRole**</span></span>  
  
-   <span data-ttu-id="0e4e7-112">**SQLAgentOperatorRole**</span><span class="sxs-lookup"><span data-stu-id="0e4e7-112">**SQLAgentOperatorRole**</span></span>  
  
 <span data-ttu-id="0e4e7-113">이러한 역할은 **msdb** 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-113">These roles are stored in the **msdb** database.</span></span> <span data-ttu-id="0e4e7-114">기본적으로 사용자는 이러한 데이터베이스 역할의 멤버가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-114">By default, no user is a member of these database roles.</span></span> <span data-ttu-id="0e4e7-115">이러한 역할의 멤버는 명시적으로 부여되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-115">Membership in these roles must be granted explicitly.</span></span> <span data-ttu-id="0e4e7-116">**sysadmin** 고정 서버 역할의 멤버인 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에 대해 모든 권한을 가지며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 사용하기 위해 이러한 고정 데이터베이스 역할의 멤버일 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-116">Users who are members of the **sysadmin** fixed server role have full access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, and do not need to be a member of these fixed database roles to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="0e4e7-117">이러한 데이터베이스 역할 또는 **sysadmin** 역할의 멤버가 아닌 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결할 때 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에이전트 노드를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-117">If a user is not a member of one of these database roles or of the **sysadmin** role, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node is not available to them when they connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="0e4e7-118">이러한 데이터베이스 역할의 멤버는 자신이 소유하는 작업을 보고 실행할 수 있으며 기존 프록시 계정으로 실행되는 작업 단계를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-118">Members of these database roles can view and execute jobs that they own, and create job steps that run as an existing proxy account.</span></span> <span data-ttu-id="0e4e7-119">이러한 각 역할과 관련된 특정 사용 권한에 대한 자세한 내용은 [SQL Server 에이전트 고정 데이터베이스 역할](sql-server-agent-fixed-database-roles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-119">For more information about the specific permissions that are associated with each of these roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="0e4e7-120">**sysadmin** 고정 서버 역할의 멤버에게는 프록시 계정을 만들고 수정하고 삭제할 수 있는 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-120">Members of the **sysadmin** fixed server role have permission to create, modify, and delete proxy accounts.</span></span> <span data-ttu-id="0e4e7-121">**sysadmin** 역할의 멤버는 프록시를 지정하지 않는 작업 단계를 만들 수 있는 권한이 있지만 그 대신 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 시작하는 데 사용되는 계정인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 계정으로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-121">Members of the **sysadmin** role have permission to create job steps that do not specify a proxy, but instead run as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, which is the account that is used to start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="0e4e7-122">지침</span><span class="sxs-lookup"><span data-stu-id="0e4e7-122">Guidelines</span></span>  
 <span data-ttu-id="0e4e7-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 구현에 대한 보안을 향상시키려면 다음 지침을 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-123">Follow these guidelines to improve the security of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent implementation:</span></span>  
  
-   <span data-ttu-id="0e4e7-124">프록시에 대한 전용 사용자 계정을 만들고 이러한 프록시 사용자 계정만 사용하여 작업 단계를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-124">Create dedicated user accounts specifically for proxies, and only use these proxy user accounts for running job steps.</span></span>  
  
-   <span data-ttu-id="0e4e7-125">프록시 사용자 계정에 필요한 사용 권한만 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-125">Only grant the necessary permissions to proxy user accounts.</span></span> <span data-ttu-id="0e4e7-126">특정 프록시 계정에 할당된 작업 단계를 실행하는 데 실제로 필요한 사용 권한만 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-126">Grant only those permissions actually required to run the job steps that are assigned to a given proxy account.</span></span>  
  
-   <span data-ttu-id="0e4e7-127">Windows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Administrators **그룹의 멤버인 Microsoft Windows 계정을 사용하여** 에이전트 서비스를 실행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-127">Do not run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service under a Microsoft Windows account that is a member of the Windows **Administrators** group.</span></span>  
  
-   <span data-ttu-id="0e4e7-128">프록시는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 자격 증명 저장소만큼만 안전합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-128">Proxies are only as secure as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credential store.</span></span>  
  
-   <span data-ttu-id="0e4e7-129">사용자 쓰기 작업으로 NT 이벤트 로그에 쓸 수 있는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 통해 경고를 올립니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-129">If user write operations can write to the NT Event log, they can raise alerts via [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
-   <span data-ttu-id="0e4e7-130">NT 관리 계정은 서비스 계정 또는 프록시 계정으로 지정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-130">Do not specify the NT Admin account as a service account or proxy account.</span></span>  
  
-   <span data-ttu-id="0e4e7-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트는 서로의 자산에 대한 액세스 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-131">Note that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent have access to each other's assets.</span></span> <span data-ttu-id="0e4e7-132">두 서비스가 단일 프로세스 공간을 공유하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스의 sysadmin입니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-132">The two services share a single process space and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is a sysadmin on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="0e4e7-133">TSX를 MSF에 등록할 때 MSX sysadmins는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 TSX 인스턴스에 대한 총 제어 권한을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-133">When a TSX enlists with an MSX, the MSX sysadmins gets total control over the TSX instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="0e4e7-134">ACE는 확장 파일이며 그 자체를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-134">ACE is an extension and cannot invoke itself.</span></span> <span data-ttu-id="0e4e7-135">ACE는 Microsoft.SqlServer.Chainer.Setup.exe라는 Chainer ScenarioEngine.exe에서 호출되거나 다른 호스트 프로세스에서 호출될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-135">ACE is invoked by Chainer ScenarioEngine.exe - also known as Microsoft.SqlServer.Chainer.Setup.exe - or it can be invoked by another host process.</span></span>  
  
-   <span data-ttu-id="0e4e7-136">ACE는 해당 API의 DLL이 ACE에서 호출되기 때문에 SSDP에서 소유된 다음 구성 DLL에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="0e4e7-136">ACE depends on the following configuration DLL's owned by SSDP, because those API's of DLL's are called by ACE:</span></span>  
  
    -   <span data-ttu-id="0e4e7-137">**SCO** -가상 계정에 대한 새 SCO 자격 증명이 포함된 Microsoft.SqlServer.Configuration.Sco.dll</span><span class="sxs-lookup"><span data-stu-id="0e4e7-137">**SCO** - Microsoft.SqlServer.Configuration.Sco.dll, including new SCO validations for virtual accounts</span></span>  
  
    -   <span data-ttu-id="0e4e7-138">**클러스터** - Microsoft.SqlServer.Configuration.Cluster.dll</span><span class="sxs-lookup"><span data-stu-id="0e4e7-138">**Cluster** - Microsoft.SqlServer.Configuration.Cluster.dll</span></span>  
  
    -   <span data-ttu-id="0e4e7-139">**SFC** - Microsoft.SqlServer.Configuration.SqlConfigBase.dll</span><span class="sxs-lookup"><span data-stu-id="0e4e7-139">**SFC** - Microsoft.SqlServer.Configuration.SqlConfigBase.dll</span></span>  
  
    -   <span data-ttu-id="0e4e7-140">**확장** – Microsoft.SqlServer.Configuration.ConfigExtension.dll</span><span class="sxs-lookup"><span data-stu-id="0e4e7-140">**Extension** - Microsoft.SqlServer.Configuration.ConfigExtension.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e4e7-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e4e7-141">See Also</span></span>  
 <span data-ttu-id="0e4e7-142">[미리 정의 된 역할](../../reporting-services/security/role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="0e4e7-142">[Predefined Roles](../../reporting-services/security/role-definitions-predefined-roles.md) </span></span>  
 <span data-ttu-id="0e4e7-143">[Transact-sql&#41;sp_addrolemember &#40;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0e4e7-143">[sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) </span></span>  
 <span data-ttu-id="0e4e7-144">[Transact-sql&#41;sp_droprolemember &#40;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0e4e7-144">[sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) </span></span>  
 [<span data-ttu-id="0e4e7-145">SQL Server 데이터베이스 엔진 및 Azure SQL Database 보안 센터</span><span class="sxs-lookup"><span data-stu-id="0e4e7-145">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
