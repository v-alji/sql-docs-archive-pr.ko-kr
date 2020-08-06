---
title: SQL Server 에이전트 작업을 만들고 관리하도록 사용자 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, user configuration
- jobs [SQL Server Agent], user configuration
- SQLAgentUserRole database role
- proxy accounts [SQL Server Agent]
ms.assetid: 67897e3e-b7d0-43dd-a2e2-2840ec4dd1ef
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83313389b3b872004fb23b0babdad19cfb5b8e7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660840"
---
# <a name="configure-a-user-to-create-and-manage-sql-server-agent-jobs"></a><span data-ttu-id="cfaf8-102">Configure a User to Create and Manage SQL Server Agent Jobs</span><span class="sxs-lookup"><span data-stu-id="cfaf8-102">Configure a User to Create and Manage SQL Server Agent Jobs</span></span>
  <span data-ttu-id="cfaf8-103">이 항목에서는 에이전트 작업을 만들거나 실행 하도록 사용자를 구성 하는 방법에 대해 설명 합니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cfaf8-103">This topic describes how to configure a user to create or execute [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>  
  
-   <span data-ttu-id="cfaf8-104">**시작하기 전 주의 사항:**  [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="cfaf8-104">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="cfaf8-105">**다음을 사용하여 SQL Server 에이전트 작업을 만들고 관리하도록 사용자 구성**  [SQL Server Management Studio](#SSMS)</span><span class="sxs-lookup"><span data-stu-id="cfaf8-105">**To configure a user to create and manage SQL Server Agent jobs, using:**  [SQL Server Management Studio](#SSMS)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cfaf8-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="cfaf8-106">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cfaf8-107">보안</span><span class="sxs-lookup"><span data-stu-id="cfaf8-107">Security</span></span>  
 <span data-ttu-id="cfaf8-108">사용자가 에이전트 작업을 만들거나 실행할 수 있도록 구성 하려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 먼저 기존 SQL Server 로그인 또는 msdb 역할을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb 데이터베이스의 에이전트 고정 데이터베이스 역할 SQLAgentUserRole, SQLAgentReaderRole 또는 SQLAgentOperatorRole 중 하나에 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-108">To configure a user to create or execute [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs, you must first add an existing SQL Server login or msdb role to one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the msdb database: SQLAgentUserRole, SQLAgentReaderRole, or SQLAgentOperatorRole.</span></span>  
  
 <span data-ttu-id="cfaf8-109">기본적으로 이러한 데이터베이스 역할의 멤버는 자신의 계정으로 실행되는 고유한 작업 단계를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-109">By default, members of these database roles can create their own job steps that run as themselves.</span></span> <span data-ttu-id="cfaf8-110">관리 권한이 없는 이러한 사용자가 다른 작업 단계 유형(예: [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지)을 실행하는 작업을 실행하려면 프록시 계정에 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-110">If these non-administrative users want to run jobs that execute other job step types (for example, [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages), they will need to have access to a proxy account.</span></span> <span data-ttu-id="cfaf8-111">sysadmin 고정 서버 역할의 모든 멤버에게는 프록시 계정을 만들고 수정하고 삭제할 수 있는 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-111">All members of the sysadmin fixed server role have permission to create, modify, and delete proxy accounts.</span></span> <span data-ttu-id="cfaf8-112">이러한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 고정 데이터베이스 역할과 관련된 사용 권한에 대한 자세한 내용은 [SQL Server 에이전트 고정 데이터베이스 역할](sql-server-agent-fixed-database-roles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-112">For more information about the permissions that are associated with these [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cfaf8-113">권한</span><span class="sxs-lookup"><span data-stu-id="cfaf8-113">Permissions</span></span>  
 <span data-ttu-id="cfaf8-114">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="cfaf8-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="cfaf8-115">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="cfaf8-116">**SQL Server 에이전트 고정 데이터베이스 역할에 SQL 로그인이나 msdb 역할을 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="cfaf8-116">**To add a SQL login or msdb role to a SQL Server Agent fixed database role**</span></span>  
  
1.  <span data-ttu-id="cfaf8-117">**개체 탐색기**에서 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-117">In **Object Explorer**, expand a server.</span></span>  
  
2.  <span data-ttu-id="cfaf8-118">**보안**을 확장한 다음 **로그인**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-118">Expand **Security**, and then expand **Logins**.</span></span>  
  
3.  <span data-ttu-id="cfaf8-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 고정 데이터베이스 역할에 추가하려는 로그인을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-119">Right-click the login you wish to add to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database role, and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="cfaf8-120">**로그인 속성** 대화 상자의 **사용자 매핑** 페이지에서을 포함 하는 행을 선택 `msdb` 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-120">On the **User Mapping** page of the **Login Properties** dialog box, select the row containing `msdb`.</span></span>  
  
5.  <span data-ttu-id="cfaf8-121">**데이터베이스 역할 멤버 자격: msdb**에서 적합한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 고정 데이터베이스 역할을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-121">Under **Database role membership for: msdb**, check the appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database role.</span></span>  
  
 <span data-ttu-id="cfaf8-122">**SQL Server 에이전트 작업 단계를 만들고 관리하는 프록시 계정을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="cfaf8-122">**To configure a proxy account to create and manage SQL Server Agent job steps**</span></span>  
  
1.  <span data-ttu-id="cfaf8-123">**개체 탐색기**에서 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-123">In **Object Explorer**, expand a server.</span></span>  
  
2.  <span data-ttu-id="cfaf8-124">**SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-124">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="cfaf8-125">**프록시** 를 마우스 오른쪽 단추로 클릭하고 **새 프록시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-125">Right-click **Proxies** and select **New Proxy**.</span></span>  
  
4.  <span data-ttu-id="cfaf8-126">**새 프록시 계정** 대화 상자의 **일반** 페이지에서 새 프록시의 프록시 이름, 자격 증명 이름 및 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-126">On the **General** page of the **New Proxy Account** dialog, specify the proxy name, credential name, and description for the new proxy.</span></span> <span data-ttu-id="cfaf8-127">SQL Server 에이전트 프록시를 만들기 전에 자격 증명을 먼저 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-127">Note that you must create a credential first before creating a SQL Server Agent proxy.</span></span> <span data-ttu-id="cfaf8-128">자격 증명을 만드는 방법에 대 한 자세한 내용은 [자격 증명 만들기](../../relational-databases/security/authentication-access/create-a-credential.md) 및 [자격 증명 만들기 &#40;transact-sql&#41;](/sql/t-sql/statements/create-credential-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-128">For more information about creating a credential, see [Create a Credential](../../relational-databases/security/authentication-access/create-a-credential.md) and [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).</span></span>  
  
5.  <span data-ttu-id="cfaf8-129">이 프록시에 대한 적절한 하위 시스템을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-129">Check the appropriate subsystems for this proxy.</span></span>  
  
6.  <span data-ttu-id="cfaf8-130">**보안 주체** 페이지에서 프록시 계정에 대한 액세스 권한을 부여 또는 제거할 로그인이나 역할을 추가하거나 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="cfaf8-130">On the **Principals** page, add or remove logins or roles to grant or remove access to the proxy account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfaf8-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cfaf8-131">See Also</span></span>  
 [<span data-ttu-id="cfaf8-132">SQL Server 에이전트 보안 구현</span><span class="sxs-lookup"><span data-stu-id="cfaf8-132">Implement SQL Server Agent Security</span></span>](implement-sql-server-agent-security.md)  
  
  
