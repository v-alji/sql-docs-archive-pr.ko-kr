---
title: 데이터 수집기 보안 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
- security [data collector]
- data collector [SQL Server], security
ms.assetid: e75d6975-641e-440a-a642-cb39a583359a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c89f1658f6ae1b5bd79de96f20222b0b19529df2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647705"
---
# <a name="data-collector-security"></a><span data-ttu-id="bd6bd-102">데이터 수집기 보안</span><span class="sxs-lookup"><span data-stu-id="bd6bd-102">Data Collector Security</span></span>
  <span data-ttu-id="bd6bd-103">데이터 수집기는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 구현하는 역할 기반 보안 모델을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-103">The data collector uses the role-based security model implemented by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="bd6bd-104">이 모델을 사용하면 데이터베이스 관리자가 해당 태스크를 수행하는 데 반드시 필요한 사용 권한만 있는 보안 컨텍스트에서 다양한 데이터 수집기 태스크를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-104">This model lets the database administrator run the various data collector tasks in a security context that has only the permissions required to perform that task.</span></span> <span data-ttu-id="bd6bd-105">이 방법은 저장 프로시저 또는 뷰를 사용해야만 액세스할 수 있는 내부 테이블 관련 작업에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-105">This approach is also used for operations involving internal tables, which can only be accessed by using a stored procedure or view.</span></span> <span data-ttu-id="bd6bd-106">내부 테이블에 대한 사용 권한이 부여되지 않는 대신,</span><span class="sxs-lookup"><span data-stu-id="bd6bd-106">No permissions are granted to internal tables.</span></span> <span data-ttu-id="bd6bd-107">해당 테이블에 액세스하는 데 사용되는 저장 프로시저 또는 뷰의 사용자에 대해 사용 권한을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-107">Instead, permissions are checked on the user of the stored procedure or view that is used to access a table.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bd6bd-108">이 보안 모델의 다른 핵심 요소는 공통적 사용 권한입니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-108">Another key aspect of this security model is concentric permissions.</span></span> <span data-ttu-id="bd6bd-109">공통적 사용 권한에서는 개체(예: 경고, 운영자, 작업, 일정 및 프록시)에 대해 사용 권한이 많은 역할이 사용 권한이 적은 역할의 사용 권한을 상속받습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-109">Under concentric permissions, more privileged roles inherit the permissions of less privileged roles on objects (including alerts, operators, jobs, schedules, and proxies).</span></span> <span data-ttu-id="bd6bd-110">자세한 내용은 [SQL Server Agent Fixed Database Roles](../../ssms/agent/sql-server-agent-fixed-database-roles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-110">For more information, see [SQL Server Agent Fixed Database Roles](../../ssms/agent/sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="bd6bd-111">다음 섹션에서는 일반적인 데이터 컬렉션 보안을 비롯하여 데이터 수집기를 구성 및 사용하고 관리 데이터 웨어하우스 관련 태스크를 수행할 수 있도록 사용자에게 부여해야 하는 역할에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-111">The following sections describe data collection security in general, as well as the roles you must grant to users so they can configure and use the data collector, and carry out tasks associated with the management data warehouse.</span></span>  
  
## <a name="general-security"></a><span data-ttu-id="bd6bd-112">일반 보안</span><span class="sxs-lookup"><span data-stu-id="bd6bd-112">General Security</span></span>  
 <span data-ttu-id="bd6bd-113">데이터 수집기는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에 대해 지정된 문서화된 표준에 따라 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-113">The data collector is installed according to the documented standards specified for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
### <a name="network-security"></a><span data-ttu-id="bd6bd-114">네트워크 보안</span><span class="sxs-lookup"><span data-stu-id="bd6bd-114">Network Security</span></span>  
 <span data-ttu-id="bd6bd-115">대상 인스턴스, 구성 서버와 연결된 관계형 인스턴스, 실행 중인 컬렉션 집합 및 관리 데이터 웨어하우스를 호스팅하는 서버 간에 중요한 정보를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-115">Sensitive information can be passed between target instances, the relational instance associated with the configuration server, the collection sets that are running, and the server that hosts the management data warehouse.</span></span>  
  
 <span data-ttu-id="bd6bd-116">네트워크를 통해 전송되는 데이터를 보호하기 위해 [!INCLUDE[tsql](../../includes/tsql-md.md)]에 대한 프로토콜 암호화와 같은 표준 보안 메커니즘이 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-116">To protect any data that is transferred over a network, the standard security mechanisms are implemented, such as protocol encryption for [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
## <a name="permissions-for-configuring-and-using-the-data-collector"></a><span data-ttu-id="bd6bd-117">데이터 수집기 구성 및 사용 권한</span><span class="sxs-lookup"><span data-stu-id="bd6bd-117">Permissions for Configuring and Using the Data Collector</span></span>  
 <span data-ttu-id="bd6bd-118">태스크에 따라 사용자는 데이터 수집기에 대해 제공된 하나 이상의 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-118">Depending on the task, users must be members of one or more of the fixed database roles provided for the data collector.</span></span> <span data-ttu-id="bd6bd-119">역할은 액세스 권한이 많은 것부터 적은 순서대로 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-119">In order of most-privileged to least-privileged access, the roles are as follows:</span></span>  
  
-   `dc_admin`  
  
-   <span data-ttu-id="bd6bd-120">**dc_operator**</span><span class="sxs-lookup"><span data-stu-id="bd6bd-120">**dc_operator**</span></span>  
  
-   <span data-ttu-id="bd6bd-121">**dc_proxy**</span><span class="sxs-lookup"><span data-stu-id="bd6bd-121">**dc_proxy**</span></span>  
  
 <span data-ttu-id="bd6bd-122">이러한 역할은 msdb 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-122">These roles are stored in the msdb database.</span></span> <span data-ttu-id="bd6bd-123">기본적으로 사용자는 이러한 데이터베이스 역할의 멤버가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-123">By default, no user is a member of these database roles.</span></span> <span data-ttu-id="bd6bd-124">이러한 역할의 사용자 멤버 자격은 명시적으로 부여되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-124">User membership in these roles must be granted explicitly.</span></span>  
  
 <span data-ttu-id="bd6bd-125">고정 서버 역할의 멤버인 사용자는 `sysadmin` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 개체 및 데이터 수집기 뷰에 대 한 모든 액세스 권한을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-125">Users who are members of the `sysadmin` fixed server role have full access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent objects and data collector views.</span></span> <span data-ttu-id="bd6bd-126">단, 데이터 수집기 역할에 명시적으로 추가되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-126">However, they need to be explicitly added to data collector roles.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bd6bd-127">db_ssisadmin 및 dc_admin 역할의 멤버는 해당 권한을 sysadmin으로 승격할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-127">Members of the db_ssisadmin role and the dc_admin role may be able to elevate their privileges to sysadmin.</span></span> <span data-ttu-id="bd6bd-128">이러한 권한 승격이 발생할 수 있는 것은 이러한 역할이 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 수정할 수 있고 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트의 sysadmin 보안 컨텍스트를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 패키지를 실행할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-128">This elevation of privilege can occur because these roles can modify [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages can be executed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the sysadmin security context of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="bd6bd-129">유지 관리 계획, 데이터 컬렉션 집합 및 기타 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 실행할 때 이러한 권한 상승이 발생하지 않도록 하려면 패키지를 실행하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업이 제한된 권한을 갖는 프록시 계정을 사용하도록 구성하거나 db_ssisadmin 및 dc_admin 역할에 sysadmin 멤버만 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-129">To guard against this elevation of privilege when running maintenance plans, data collection sets, and other [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs that run packages to use a proxy account with limited privileges or only add sysadmin members to the db_ssisadmin and dc_admin roles.</span></span>  
  
### <a name="dc_admin-role"></a><span data-ttu-id="bd6bd-130">dc_admin 역할</span><span class="sxs-lookup"><span data-stu-id="bd6bd-130">dc_admin Role</span></span>  
 <span data-ttu-id="bd6bd-131">역할에 할당 된 사용자는 `dc_admin` 서버 인스턴스의 데이터 수집기 구성에 대 한 모든 관리자 권한 (만들기, 읽기, 업데이트 및 삭제)을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-131">Users assigned to the `dc_admin` role have full administrator access (Create, Read, Update, and Delete) to the data collector configuration on a server instance.</span></span> <span data-ttu-id="bd6bd-132">이 역할의 멤버는 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-132">Members of this role can perform the following operations:</span></span>  
  
-   <span data-ttu-id="bd6bd-133">수집기 수준 속성 설정</span><span class="sxs-lookup"><span data-stu-id="bd6bd-133">Set collector-level properties.</span></span>  
  
-   <span data-ttu-id="bd6bd-134">새 컬렉션 집합 추가</span><span class="sxs-lookup"><span data-stu-id="bd6bd-134">Add new collection sets.</span></span>  
  
-   <span data-ttu-id="bd6bd-135">새 컬렉션 유형 설치</span><span class="sxs-lookup"><span data-stu-id="bd6bd-135">Install new collection types.</span></span>  
  
-   <span data-ttu-id="bd6bd-136">**dc_operator** 역할에 허용된 모든 작업 수행</span><span class="sxs-lookup"><span data-stu-id="bd6bd-136">Perform all the operations permitted to the **dc_operator** role.</span></span>  
  
 <span data-ttu-id="bd6bd-137">`dc_admin`역할은 다음 역할의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-137">The `dc_admin` role is a member of the following roles:</span></span>  
  
-   <span data-ttu-id="bd6bd-138">**SQLAgentUserRole**.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-138">**SQLAgentUserRole**.</span></span> <span data-ttu-id="bd6bd-139">이 역할은 일정을 만들고 작업을 실행하기 위해 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-139">This role is required to create schedules and run jobs.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bd6bd-140">데이터 수집기에 대해 생성 된 프록시는에 대 한 액세스 권한을 부여 하 여 `dc_admin` 프록시를 필요로 하는 모든 작업 단계에서이를 만들어 사용할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-140">Proxies created for the data collector must grant access to `dc_admin` to create them and use them in any job steps that require a proxy.</span></span>  
  
-   <span data-ttu-id="bd6bd-141">**dc_operator**.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-141">**dc_operator**.</span></span> <span data-ttu-id="bd6bd-142">의 멤버 `dc_admin` 는 **dc_operator**에 지정 된 권한을 상속 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-142">Members of `dc_admin` inherit the permissions given to **dc_operator**.</span></span>  
  
### <a name="dc_operator-role"></a><span data-ttu-id="bd6bd-143">dc_operator 역할</span><span class="sxs-lookup"><span data-stu-id="bd6bd-143">dc_operator Role</span></span>  
 <span data-ttu-id="bd6bd-144">**dc_operator** 역할의 멤버는 읽기 및 업데이트 권한을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-144">Members of the **dc_operator** role have Read and Update access.</span></span> <span data-ttu-id="bd6bd-145">이 역할은 컬렉션 집합 실행 및 구성과 관련된 작업 태스크를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-145">This role supports operations tasks related to running and configuring collection sets.</span></span> <span data-ttu-id="bd6bd-146">이 역할의 멤버는 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-146">Members of this role can perform the following operations:</span></span>  
  
-   <span data-ttu-id="bd6bd-147">컬렉션 집합 시작 또는 중지</span><span class="sxs-lookup"><span data-stu-id="bd6bd-147">Start or stop a collection set.</span></span>  
  
-   <span data-ttu-id="bd6bd-148">기존 컬렉션 집합 열거</span><span class="sxs-lookup"><span data-stu-id="bd6bd-148">Enumerate existing collection sets.</span></span>  
  
-   <span data-ttu-id="bd6bd-149">컬렉션 항목 및 컬렉션 빈도와 같은 컬렉션 집합 관련 세부 정보 확인</span><span class="sxs-lookup"><span data-stu-id="bd6bd-149">View the detailed information (for example, collection items, and collection frequency) associated with a collection set.</span></span>  
  
-   <span data-ttu-id="bd6bd-150">기존 컬렉션 집합의 업로드 빈도 변경</span><span class="sxs-lookup"><span data-stu-id="bd6bd-150">Change the upload frequency for existing collection sets.</span></span>  
  
-   <span data-ttu-id="bd6bd-151">기존 컬렉션 집합의 일부인 컬렉션 항목의 컬렉션 빈도 변경</span><span class="sxs-lookup"><span data-stu-id="bd6bd-151">Change the collection frequency for collection items that are part of an existing collection set.</span></span>  
  
 <span data-ttu-id="bd6bd-152">**dc_operator** 역할은 데이터 수집기 패키지를 열거하고 보는 데 필요한 다음 역할의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-152">The **dc_operator** role is a member of the following roles that are required for enumerating and viewing data collector packages:</span></span>  
  
-   <span data-ttu-id="bd6bd-153">**db_ssisltduser**</span><span class="sxs-lookup"><span data-stu-id="bd6bd-153">**db_ssisltduser**</span></span>  
  
-   <span data-ttu-id="bd6bd-154">**db_ssisoperator**</span><span class="sxs-lookup"><span data-stu-id="bd6bd-154">**db_ssisoperator**</span></span>  
  
 <span data-ttu-id="bd6bd-155">자세한 내용은 [Integration Services 경로&#40;SSIS Service&#41;](../../integration-services/security/integration-services-roles-ssis-service.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-155">For more information, see [Integration Services Roles &#40;SSIS Service&#41;](../../integration-services/security/integration-services-roles-ssis-service.md).</span></span>  
  
### <a name="dc_proxy-role"></a><span data-ttu-id="bd6bd-156">dc_proxy 역할</span><span class="sxs-lookup"><span data-stu-id="bd6bd-156">dc_proxy Role</span></span>  
 <span data-ttu-id="bd6bd-157">**dc_proxy** 역할의 멤버는 데이터 수집기 컬렉션 집합 및 수집기 수준 속성에 대한 읽기 권한을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-157">Members of the **dc_proxy** role have Read access to data collector collection sets and collector-level properties.</span></span> <span data-ttu-id="bd6bd-158">이 역할의 멤버는 자신이 소유하는 작업을 실행할 수 있으며 기존 프록시 계정으로 실행되는 작업 단계를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-158">Members of this role can also execute jobs that they own and create job steps that run as an existing proxy account.</span></span>  
  
 <span data-ttu-id="bd6bd-159">이 역할의 멤버는 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-159">Members of this role can perform the following operations:</span></span>  
  
-   <span data-ttu-id="bd6bd-160">컬렉션 항목에 대한 입력 매개 변수 및 이러한 항목의 컬렉션 빈도와 같은 컬렉션 집합 구성 정보 확인</span><span class="sxs-lookup"><span data-stu-id="bd6bd-160">View collection set configuration information (for example, input parameters for collection items, and the collection frequency for these items).</span></span>  
  
-   <span data-ttu-id="bd6bd-161">데이터 업로드에 사용되는 데이터 웨어하우스 연결 정보와 같이 서명된 저장 프로시저로만 액세스할 수 있는 암호화된 내부 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="bd6bd-161">Obtain internal encrypted information that can only be accessed by a signed stored procedure (for example, data warehouse connection information used for data uploads).</span></span>  
  
-   <span data-ttu-id="bd6bd-162">컬렉션 집합 런타임 이벤트 기록</span><span class="sxs-lookup"><span data-stu-id="bd6bd-162">Log collection-set run-time events.</span></span>  
  
 <span data-ttu-id="bd6bd-163">**dc_proxy** 역할은 데이터 수집기 패키지를 열거하고 보는 데 필요한 다음 역할의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-163">The **dc_proxy** role is a member of the following roles that are required for enumerating and viewing data collector packages:</span></span>  
  
-   <span data-ttu-id="bd6bd-164">**db_ssisltduser**.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-164">**db_ssisltduser**.</span></span>  
  
-   <span data-ttu-id="bd6bd-165">**db_ssisoperator**</span><span class="sxs-lookup"><span data-stu-id="bd6bd-165">**db_ssisoperator**</span></span>  
  
 <span data-ttu-id="bd6bd-166">자세한 내용은 [Integration Services 경로&#40;SSIS Service&#41;](../../integration-services/security/integration-services-roles-ssis-service.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-166">For more information, see [Integration Services Roles &#40;SSIS Service&#41;](../../integration-services/security/integration-services-roles-ssis-service.md).</span></span>  
  
## <a name="permissions-for-configuring-and-using-the-management-data-warehouse"></a><span data-ttu-id="bd6bd-167">관리 데이터 웨어하우스 구성 및 사용 권한</span><span class="sxs-lookup"><span data-stu-id="bd6bd-167">Permissions for Configuring and Using the Management Data Warehouse</span></span>  
 <span data-ttu-id="bd6bd-168">태스크에 따라 사용자는 관리 데이터 웨어하우스에 액세스하기 위해 제공된 하나 이상의 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-168">Depending on the task, users must be members of one or more of the fixed database roles provided for accessing the management data warehouse.</span></span> <span data-ttu-id="bd6bd-169">역할은 액세스 권한이 많은 것부터 적은 순서대로 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-169">In order of most-privileged to least-privileged access, the roles are as follows:</span></span>  
  
-   <span data-ttu-id="bd6bd-170">**mdw_admin**</span><span class="sxs-lookup"><span data-stu-id="bd6bd-170">**mdw_admin**</span></span>  
  
-   <span data-ttu-id="bd6bd-171">**mdw_writer**</span><span class="sxs-lookup"><span data-stu-id="bd6bd-171">**mdw_writer**</span></span>  
  
-   <span data-ttu-id="bd6bd-172">**mdw_reader**</span><span class="sxs-lookup"><span data-stu-id="bd6bd-172">**mdw_reader**</span></span>  
  
 <span data-ttu-id="bd6bd-173">이러한 역할은 msdb 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-173">These roles are stored in the msdb database.</span></span> <span data-ttu-id="bd6bd-174">기본적으로 사용자는 이러한 데이터베이스 역할의 멤버가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-174">By default, no user is a member of these database roles.</span></span> <span data-ttu-id="bd6bd-175">이러한 역할의 사용자 멤버 자격은 명시적으로 부여되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-175">User membership in these roles must be granted explicitly.</span></span>  
  
 <span data-ttu-id="bd6bd-176">고정 서버 역할의 멤버인 사용자는 `sysadmin` 데이터 수집기 뷰에 대 한 모든 액세스 권한을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-176">Users who are members of the `sysadmin` fixed server role have full access to data collector views.</span></span> <span data-ttu-id="bd6bd-177">하지만 다른 작업을 수행하기 위한 데이터베이스 역할에 명시적으로 추가되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-177">However, they need to be explicitly added to database roles to perform other operations.</span></span>  
  
### <a name="mdw_admin-role"></a><span data-ttu-id="bd6bd-178">mdw_admin 역할</span><span class="sxs-lookup"><span data-stu-id="bd6bd-178">mdw_admin Role</span></span>  
 <span data-ttu-id="bd6bd-179">**mdw_admin** 역할의 멤버는 관리 데이터 웨어하우스에 대한 읽기, 쓰기, 업데이트 및 삭제 권한을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-179">Members of the **mdw_admin** role have Read, Write, Update, and Delete access to the management data warehouse.</span></span>  
  
 <span data-ttu-id="bd6bd-180">이 역할의 멤버는 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-180">Members of this role can perform the following operations:</span></span>  
  
-   <span data-ttu-id="bd6bd-181">새 컬렉션 유형 설치 시 새 테이블을 추가하는 것과 같이 필요 시 관리 데이터 웨어하우스 스키마 변경.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-181">Change the management data warehouse schema when required (for example, adding a new table when a new collection type is installed).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bd6bd-182">스키마가 변경 된 경우에는 사용자가 `dc_admin` 새 수집기 유형을 설치 하려면 역할의 멤버 이기도 해야 합니다 .이 작업을 수행 하려면 msdb의 데이터 수집기 구성을 업데이트할 수 있는 권한이 필요 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-182">Where there is a schema change, the user must also be a member of the `dc_admin` role to install a new collector type, since this action requires permission to update the data collector configuration in msdb.</span></span>  
  
-   <span data-ttu-id="bd6bd-183">관리 데이터 웨어하우스에 대한 보관 또는 정리와 같은 유지 관리 작업 실행</span><span class="sxs-lookup"><span data-stu-id="bd6bd-183">Run maintenance jobs on the management data warehouse, such as archive or cleanup.</span></span>  
  
### <a name="mdw_writer-role"></a><span data-ttu-id="bd6bd-184">mdw_writer 역할</span><span class="sxs-lookup"><span data-stu-id="bd6bd-184">mdw_writer Role</span></span>  
 <span data-ttu-id="bd6bd-185">**mdw_writer** 역할의 멤버는 관리 데이터 웨어하우스에 데이터를 업로드하고 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-185">Members of the **mdw_writer** role can upload and write data to the management data warehouse.</span></span> <span data-ttu-id="bd6bd-186">관리 데이터 웨어하우스에 데이터를 저장하는 모든 데이터 수집기는 이 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-186">Any data collector that stores data in the management data warehouse has to be a member of this role.</span></span>  
  
### <a name="mdw_reader-role"></a><span data-ttu-id="bd6bd-187">mdw_reader 역할</span><span class="sxs-lookup"><span data-stu-id="bd6bd-187">mdw_reader Role</span></span>  
 <span data-ttu-id="bd6bd-188">**mdw_reader** 역할의 멤버는 관리 데이터 웨어하우스에 대한 읽기 권한을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-188">Members of the **mdw_reader** role have Read access to the management data warehouse.</span></span> <span data-ttu-id="bd6bd-189">이 역할은 기록 데이터에 대한 액세스를 제공하여 문제 해결을 지원하기 위한 것이므로 이 역할의 멤버는 관리 데이터 웨어하우스 스키마의 다른 요소를 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bd6bd-189">Because the purpose of this role is to support troubleshooting by providing access to historical data, members of this role cannot view other elements of the management data warehouse schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd6bd-190">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bd6bd-190">See Also</span></span>  
 [<span data-ttu-id="bd6bd-191">SQL Server 에이전트 보안 구현</span><span class="sxs-lookup"><span data-stu-id="bd6bd-191">Implement SQL Server Agent Security</span></span>](../../ssms/agent/implement-sql-server-agent-security.md)  
  
  
