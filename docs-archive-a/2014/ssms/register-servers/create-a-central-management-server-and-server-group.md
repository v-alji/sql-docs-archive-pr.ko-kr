---
title: 중앙 관리 서버 및 그룹 만들기
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- configuration server
ms.assetid: da265482-3953-440a-ac23-0ab7e42a55eb
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f53b75966a14dbc6fd6cdc9bea0929ccac7780c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727848"
---
# <a name="create-a-central-management-server-and-server-group-sql-server-management-studio"></a><span data-ttu-id="e3f0d-102">중앙 관리 서버 및 서버 그룹 만들기(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e3f0d-102">Create a Central Management Server and Server Group (SQL Server Management Studio)</span></span>
  <span data-ttu-id="e3f0d-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]인스턴스를 중앙 관리 서버로 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-103">This topic describes how to designate an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a central management server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="e3f0d-104">중앙 관리 서버는 하나 이상의 중앙 관리 서버 그룹으로 구성된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스 목록을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-104">Central management servers store a list of instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is organized into one or more central management server groups.</span></span> <span data-ttu-id="e3f0d-105">중앙 관리 서버 그룹을 사용하여 수행되는 동작은 서버 그룹의 모든 서버에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-105">Actions that are taken by using a central management server group act on all servers in the server group.</span></span> <span data-ttu-id="e3f0d-106">여기에는 개체 탐색기를 사용하여 서버에 연결하는 동작 및 여러 서버에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문과 정책 기반 관리 정책을 동시에 실행하는 동작이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-106">This includes connecting to servers by using Object Explorer and executing [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and Policy-Based Management policies on multiple servers at the same time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e3f0d-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이전의 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 버전은 중앙 관리 서버로 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-107">Versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] cannot be designated as a central management server.</span></span>  
  
 <span data-ttu-id="e3f0d-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="e3f0d-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e3f0d-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="e3f0d-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e3f0d-110">보안</span><span class="sxs-lookup"><span data-stu-id="e3f0d-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e3f0d-111">**중앙 관리 서버 및 서버 그룹을 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="e3f0d-111">**To create a Central Management Server and Server Group, using:**</span></span>  
  
     [<span data-ttu-id="e3f0d-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e3f0d-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e3f0d-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e3f0d-113">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e3f0d-114">보안</span><span class="sxs-lookup"><span data-stu-id="e3f0d-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e3f0d-115">권한</span><span class="sxs-lookup"><span data-stu-id="e3f0d-115">Permissions</span></span>  
 <span data-ttu-id="e3f0d-116">msdb 데이터베이스의 두 데이터베이스 역할을 통해 중앙 관리 서버에 대한 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-116">Two database roles in the msdb database grant access to central management servers.</span></span> <span data-ttu-id="e3f0d-117">이 중 ServerGroupAdministratorRole 역할의 멤버만 중앙 관리 서버를 관리할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="e3f0d-117">Only members of the ServerGroupAdministratorRole role can manage the central management server.</span></span> <span data-ttu-id="e3f0d-118">중앙 관리 서버에 연결하려면 ServerGroupReaderRole 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-118">Membership in the ServerGroupReaderRole role is required to connect to a central management server.</span></span>  
  
 <span data-ttu-id="e3f0d-119">중앙 관리 서버에서 유지 관리하는 연결은 Windows 인증을 사용하여 사용자 컨텍스트 내에서 실행되므로 등록된 서버에 대한 유효 사용 권한은 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-119">Because the connections that are maintained by a central management server execute in the context of the user, by using Windows Authentication, the effective permissions on the registered servers might vary.</span></span> <span data-ttu-id="e3f0d-120">예를 들어 사용자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A 인스턴스에서는 sysadmin 고정 서버 역할의 멤버이지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B 인스턴스에서는 제한된 사용 권한을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-120">For example, the user might be a member of the sysadmin fixed server role on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A, but have limited permissions on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e3f0d-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="e3f0d-121">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="e3f0d-122">다음 절차에서는 다음 단계를 수행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-122">The following procedures describe how to perform the following steps.</span></span>  
  
1.  <span data-ttu-id="e3f0d-123">중앙 관리 서버를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-123">Create a central management server.</span></span>  
  
2.  <span data-ttu-id="e3f0d-124">중앙 관리 서버에 하나 이상의 서버 그룹을 추가하고 서버 그룹에 하나 이상의 등록된 서버를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-124">Add one or more server groups to the central management server and add one or more registered servers to the server groups.</span></span>  
  
#### <a name="create-a-central-management-server"></a><span data-ttu-id="e3f0d-125">중앙 관리 서버 만들기</span><span class="sxs-lookup"><span data-stu-id="e3f0d-125">Create a central management server</span></span>  
  
1.  <span data-ttu-id="e3f0d-126">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 **보기** 메뉴에서 **등록된 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-126">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
2.  <span data-ttu-id="e3f0d-127">등록된 서버에서 **데이터베이스 엔진**을 확장하고 **중앙 관리 서버**를 마우스 오른쪽 단추로 클릭한 다음 **중앙 관리 서버 등록**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-127">In Registered Servers, expand **Database Engine**, right-click **Central Management Servers**, and then  click **Register Central Management Server**.</span></span>  
  
3.  <span data-ttu-id="e3f0d-128">\*\*새 서버 등록[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대화 상자의 서버 드롭다운 목록에서 중앙 관리 서버로 만들 \*\* 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-128">In the **New Server Registration** dialog box, select the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to become the central management server from the drop-down list of servers.</span></span> <span data-ttu-id="e3f0d-129">중앙 관리 서버를 만들려면 Windows 인증을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-129">You must use Windows Authentication for the central management server.</span></span>  
  
4.  <span data-ttu-id="e3f0d-130">**등록된 서버**에서 서버 이름과 설명(선택 사항)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-130">In **Registered Server**, enter a server name and optional description.</span></span>  
  
5.  <span data-ttu-id="e3f0d-131">**연결 속성** 탭에서 네트워크 및 연결 속성을 검토하거나 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-131">From the **Connection Properties** tab, review or modifiy the network  and connection properties.</span></span> <span data-ttu-id="e3f0d-132">자세한 내용은 [서버에 연결&#40;연결 속성 페이지&#41; 데이터베이스 엔진](../f1-help/connect-to-server-connection-properties-page-database-engine.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-132">For more information, see [Connect to Server &#40;Connection Properties Page&#41; Database Engine](../f1-help/connect-to-server-connection-properties-page-database-engine.md)</span></span>  
  
6.  <span data-ttu-id="e3f0d-133">**테스트**를 클릭하여 연결을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-133">Click **Test**, to test the connection.</span></span>  
  
7.  <span data-ttu-id="e3f0d-134">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-134">Click **Save**.</span></span> <span data-ttu-id="e3f0d-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 중앙 관리 서버 **폴더 아래에** 인스턴스가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-135">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will appear under the **Central Management Servers** folder.</span></span>  
  
#### <a name="create-a-new-server-group-and-add-servers-to-the-group"></a><span data-ttu-id="e3f0d-136">새 서버 그룹을 만들고 그룹에 서버 추가</span><span class="sxs-lookup"><span data-stu-id="e3f0d-136">Create a new server group and add servers to the group</span></span>  
  
1.  <span data-ttu-id="e3f0d-137">**등록된 서버**에서 **중앙 관리 서버**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-137">From **Registered Servers**, expand **Central Management Servers**.</span></span> <span data-ttu-id="e3f0d-138">위 절차에서 추가한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 서버 그룹**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-138">Right-click the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] added in the procedure above and select **New Server Group**.</span></span>  
  
2.  <span data-ttu-id="e3f0d-139">**새 서버 그룹 속성**에서 그룹 이름과 설명(선택 사항)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-139">In **New Server Group Properties**, enter a group name and optional description.</span></span>  
  
3.  <span data-ttu-id="e3f0d-140">**등록된 서버**에서 서버 그룹을 마우스 오른쪽 단추로 클릭하고 **새 서버 등록**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-140">From **Registered Servers**, right-click the server group and click **New Server Registration**.</span></span>  
  
4.  <span data-ttu-id="e3f0d-141">새 서버 등록에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-141">From New Server Registration, select an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e3f0d-142">자세한 내용은 [새 등록된 서버 만들기&#40;SQL Server Management Studio&#41;](create-a-new-registered-server-sql-server-management-studio.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-142">For more information, see [Create a New Registered Server &#40;SQL Server Management Studio&#41;](create-a-new-registered-server-sql-server-management-studio.md).</span></span> <span data-ttu-id="e3f0d-143">필요에 따라 서버를 더 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-143">Add more servers as appropriate.</span></span>  
  
#### <a name="to-execute-queries-against-several-configuration-targets-at-the-same-time"></a><span data-ttu-id="e3f0d-144">여러 구성 대상에 대해 동시에 쿼리를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="e3f0d-144">To execute queries against several configuration targets at the same time</span></span>  
  
-   <span data-ttu-id="e3f0d-145">하나의 중앙 관리 서버, 하나 이상의 서버 그룹 및 하나 이상의 등록된 서버를 만든 후에는 전체 그룹에 대해 동시에 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-145">After you create a central management server, one or more server groups, and one or more registered servers, you can execute queries against a whole group at the same time.</span></span> <span data-ttu-id="e3f0d-146">서버 그룹의 서버에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 동시에 실행하는 방법에 대한 자세한 내용은 [여러 서버에 대해 동시에 문 실행&#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e3f0d-146">For more information about how to execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements on the servers in a server group at the same time, see [Execute Statements Against Multiple Servers Simultaneously &#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3f0d-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3f0d-147">See Also</span></span>  
 [<span data-ttu-id="e3f0d-148">중앙 관리 서버를 사용하여 여러 서버 관리</span><span class="sxs-lookup"><span data-stu-id="e3f0d-148">Administer Multiple Servers Using Central Management Servers</span></span>](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
