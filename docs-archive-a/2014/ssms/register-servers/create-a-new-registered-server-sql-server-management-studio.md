---
title: 새로 등록된 서버 만들기
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.general.sqlce.f1
- sql12.swb.registerserver.general.sqlserver.f1
helpviewer_keywords:
- Registered Servers [SQL Server], creating new registered servers
ms.assetid: 716ea070-a3b5-4514-9de2-82ce8a96514b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 43cdb06179531a739f6595dc5ade9eeb79ea65ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638515"
---
# <a name="create-a-new-registered-server-sql-server-management-studio"></a><span data-ttu-id="9955c-102">새 등록된 서버 만들기(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9955c-102">Create a New Registered Server (SQL Server Management Studio)</span></span>
  <span data-ttu-id="9955c-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 등록된 서버 구성 요소에 서버를 등록하여 자주 액세스하는 서버에 대한 연결 정보를 저장하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-103">This topic describes how to save the connection information for servers that you access frequently, by registering the server in the Registered Servers component of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="9955c-104">서버는 연결 전이나 개체 탐색기에서 연결할 때 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-104">A server can be registered before connecting, or when connecting from Object Explorer.</span></span> <span data-ttu-id="9955c-105">로컬 컴퓨터에 있는 서버 인스턴스를 등록하는 특별한 메뉴 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-105">There is a special menu option to register the server instances on the local computer.</span></span>  
  
 <span data-ttu-id="9955c-106">등록된 서버의 종류는 다음 두 가지입니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-106">There are two kinds of registered servers:</span></span>  
  
-   <span data-ttu-id="9955c-107">로컬 서버 그룹</span><span class="sxs-lookup"><span data-stu-id="9955c-107">Local server groups</span></span>  
  
     <span data-ttu-id="9955c-108">로컬 서버 그룹을 사용하여 자주 관리하는 서버에 쉽게 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-108">Use local server groups to easily connect to servers that you frequently manage.</span></span> <span data-ttu-id="9955c-109">로컬 서버와 로컬이 아닌 서버가 모두 로컬 서버 그룹에 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-109">Both local and non-local servers are registered into local server groups.</span></span> <span data-ttu-id="9955c-110">로컬 서버 그룹은 각 사용자에게 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-110">Local server groups are unique to each user.</span></span> <span data-ttu-id="9955c-111">등록된 서버 정보를 공유하는 방법은 [등록된 서버 정보 내보내기&#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) 및 [등록된 서버 정보 가져오기&#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md)의 등록된 서버 구성 요소에 서버를 등록하여 자주 액세스하는 서버에 대한 연결 정보를 저장하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-111">For information about how to share registered server information, see [Export Registered Server Information &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) and [Import Registered Server Information &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9955c-112">가능하면 Windows 인증을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-112">We recommend that you use Windows Authentication whenever possible.</span></span>  
  
-   <span data-ttu-id="9955c-113">중앙 관리 서버</span><span class="sxs-lookup"><span data-stu-id="9955c-113">Central Management Servers</span></span>  
  
     <span data-ttu-id="9955c-114">중앙 관리 서버에서는 파일 시스템 대신 중앙 관리 서버에 서버 등록을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-114">Central Management Servers store server registrations in the Central Management Server instead of on the file system.</span></span> <span data-ttu-id="9955c-115">중앙 관리 서버와 등록된 하위 서버는 Windows 인증을 사용해서만 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-115">Central Management Servers and subordinate registered servers can be registered only by using Windows Authentication.</span></span> <span data-ttu-id="9955c-116">중앙 관리 서버를 등록하면 연결된 등록된 서버가 자동으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-116">After a Central Management Server has been registered, its associated registered servers will be automatically displayed.</span></span> <span data-ttu-id="9955c-117">중앙 관리 서버에 대한 자세한 내용은 [중앙 관리 서버를 사용하여 여러 서버 관리](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9955c-117">For more information about Central Management Servers, see [Administer Multiple Servers Using Central Management Servers](../../relational-databases/administer-multiple-servers-using-central-management-servers.md).</span></span> <span data-ttu-id="9955c-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이전의 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 버전은 중앙 관리 서버로 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-118">Versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] cannot be designated as a Central Management Server.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9955c-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="9955c-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-automatically-register-the-local-server-instances"></a><span data-ttu-id="9955c-120">로컬 서버 인스턴스를 자동으로 등록하려면</span><span class="sxs-lookup"><span data-stu-id="9955c-120">To automatically register the local server instances</span></span>  
  
-   <span data-ttu-id="9955c-121">등록된 서버에서 등록된 서버 트리의 노드를 마우스 오른쪽 단추로 클릭한 다음 **로컬 서버 등록 업데이트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-121">In Registered Servers, right-click any node in the Registered Servers tree, and then click **Update Local Server Registration**.</span></span>  
  
#### <a name="to-create-a-new-registered-server"></a><span data-ttu-id="9955c-122">새 등록된 서버를 만들려면</span><span class="sxs-lookup"><span data-stu-id="9955c-122">To create a new registered server</span></span>  
  
1.  <span data-ttu-id="9955c-123">등록된 서버가 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에 표시되지 않으면 **보기** 메뉴에서 **등록된 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-123">If Registered Servers is not visible in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
     <span data-ttu-id="9955c-124">**서버 유형**</span><span class="sxs-lookup"><span data-stu-id="9955c-124">**Server type**</span></span>  
     <span data-ttu-id="9955c-125">등록된 서버에서 서버를 등록하는 경우 **서버 유형** 상자는 읽기 전용이며 등록된 서버 창에 표시된 서버 유형과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-125">When a server is registered from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers pane.</span></span> <span data-ttu-id="9955c-126">다른 유형의 서버를 등록하려면 새 서버를 등록하기 전에 **등록된 서비스**도구 모음에서 **데이터베이스 엔진**, **분석 서버**, **Reporting Services** 또는 **Integration Services** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-126">To register a different type of server, click **Database Engine**, **Analysis Server**, **Reporting Services**, or **Integration Services** on the **Registered Servers** toolbar before starting to register a new server.</span></span>  
  
     <span data-ttu-id="9955c-127">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="9955c-127">**Server name**</span></span>  
     <span data-ttu-id="9955c-128">[] 형식으로 등록할 서버 인스턴스를 선택 *\<servername>* 합니다. \\ *\<instancename>*</span><span class="sxs-lookup"><span data-stu-id="9955c-128">Select the server instance to register in the format: *\<servername>*[\\*\<instancename>*].</span></span>  
  
     <span data-ttu-id="9955c-129">**인증**</span><span class="sxs-lookup"><span data-stu-id="9955c-129">**Authentication**</span></span>  
     <span data-ttu-id="9955c-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결할 때는 두 가지 인증 모드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-130">Two authentication modes are available when connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="9955c-131">**Windows 인증**</span><span class="sxs-lookup"><span data-stu-id="9955c-131">**Windows Authentication**</span></span>  
     <span data-ttu-id="9955c-132">Windows 인증 모드를 사용하면 사용자는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 사용자 계정을 통해 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-132">Windows Authentication mode allows a user to connect through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user account.</span></span>  
  
     <span data-ttu-id="9955c-133">**SQL Server 인증**</span><span class="sxs-lookup"><span data-stu-id="9955c-133">**SQL Server Authentication**</span></span>  
     <span data-ttu-id="9955c-134">사용자가 지정한 로그인 이름과 암호를 사용하여 트러스트되지 않은 연결로부터 연결하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 계정이 설정되고 지정한 암호가 전에 기록한 암호와 일치하는지를 확인하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 자체적으로 인증을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-134">When a user connects with a specified login name and password from a nontrusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication itself by checking whether a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and whether the specified password matches the one previously recorded.</span></span> <span data-ttu-id="9955c-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 로그인 계정이 설정되어 있지 않으면 인증이 실패하고 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-135">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)] <span data-ttu-id="9955c-136">자세한 내용은 [인증 모드 선택](../../relational-databases/security/choose-an-authentication-mode.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9955c-136">For more information, see [Choose an Authentication Mode](../../relational-databases/security/choose-an-authentication-mode.md).</span></span>  
  
     <span data-ttu-id="9955c-137">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="9955c-137">**User name**</span></span>  
     <span data-ttu-id="9955c-138">연결 중인 현재 사용자 이름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-138">Shows the current user name you are connecting with.</span></span> <span data-ttu-id="9955c-139">이 읽기 전용 옵션은 Windows 인증을 사용하여 연결하도록 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-139">This read-only option is only available if you have selected to connect using Windows Authentication.</span></span> <span data-ttu-id="9955c-140">**사용자 이름**을 변경하려면 다른 사용자로 컴퓨터에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-140">To change **User names**, log in to the computer as a different user.</span></span>  
  
     <span data-ttu-id="9955c-141">**로그인**</span><span class="sxs-lookup"><span data-stu-id="9955c-141">**Login**</span></span>  
     <span data-ttu-id="9955c-142">연결 시 사용할 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-142">Enter the login to connect with.</span></span> <span data-ttu-id="9955c-143">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하도록 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-143">This option is available only if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="9955c-144">**암호**</span><span class="sxs-lookup"><span data-stu-id="9955c-144">**Password**</span></span>  
     <span data-ttu-id="9955c-145">로그인 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-145">Enter the password for the login.</span></span> <span data-ttu-id="9955c-146">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하도록 선택한 경우에만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-146">This option can be edited only if you have selected to connect by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="9955c-147">**암호 저장**</span><span class="sxs-lookup"><span data-stu-id="9955c-147">**Remember password**</span></span>  
     <span data-ttu-id="9955c-148">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 사용자가 입력한 암호를 암호화하여 저장하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-148">Select to have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] encrypt and store the password you have entered.</span></span> <span data-ttu-id="9955c-149">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하도록 선택한 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-149">This option is displayed only if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9955c-150">저장한 암호를 더 이상 저장하지 않으려면 이 확인란의 선택을 취소하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-150">If you have stored the password and want to stop storing it, clear this check box, and then click **Save**.</span></span>  
  
     <span data-ttu-id="9955c-151">**등록된 서버 이름**</span><span class="sxs-lookup"><span data-stu-id="9955c-151">**Registered server name**</span></span>  
     <span data-ttu-id="9955c-152">등록된 서버에 표시할 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-152">The name you want to appear in Registered Servers.</span></span> <span data-ttu-id="9955c-153">이 이름은 **서버 이름** 상자와 일치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-153">This name does not have to match the **Server name** box.</span></span>  
  
     <span data-ttu-id="9955c-154">**등록된 서버 설명**</span><span class="sxs-lookup"><span data-stu-id="9955c-154">**Registered server description**</span></span>  
     <span data-ttu-id="9955c-155">서버에 대한 선택적 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-155">Enter an optional description of the server.</span></span>  
  
     <span data-ttu-id="9955c-156">**Test**</span><span class="sxs-lookup"><span data-stu-id="9955c-156">**Test**</span></span>  
     <span data-ttu-id="9955c-157">**서버 이름**에서 선택한 서버 연결을 테스트하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-157">Click to test the connection to the server selected in **Server name**.</span></span>  
  
     <span data-ttu-id="9955c-158">**저장**</span><span class="sxs-lookup"><span data-stu-id="9955c-158">**Save**</span></span>  
     <span data-ttu-id="9955c-159">등록된 서버 설정을 저장하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-159">Click to save the registered server settings.</span></span>  
  
## <a name="multiserver-queries"></a><span data-ttu-id="9955c-160">다중 서버 쿼리</span><span class="sxs-lookup"><span data-stu-id="9955c-160">Multiserver Queries</span></span>  
 <span data-ttu-id="9955c-161">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 의 쿼리 편집기 창은 여러 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 동시에 연결하여 쿼리를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-161">The Query Editor window in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] can connect to and query multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] at the same time.</span></span> <span data-ttu-id="9955c-162">쿼리에서 반환되는 결과는 단일 결과 창에 병합되거나 별도의 결과 창에 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-162">The results that are returned by the query can be merged into a single results pane, or they can be returned in separate results panes.</span></span> <span data-ttu-id="9955c-163">선택적으로 쿼리 편집기는 각 행을 생성한 서버의 이름을 제공하는 열과 각 행을 제공한 서버에 연결하는 데 사용된 로그인을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-163">As an option, Query Editor can include columns that provide the name of the server that produced each row, and also the login that was used to connect to the server that provided each row.</span></span> <span data-ttu-id="9955c-164">다중 서버 쿼리를 실행하는 방법은 [여러 서버에 대해 동시에 문 실행&#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9955c-164">For more information about how to execute multiserver queries, see [Execute Statements Against Multiple Servers Simultaneously &#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md).</span></span>  
  
 <span data-ttu-id="9955c-165">로컬 서버 그룹의 모든 서버에 대해 쿼리를 실행하려면 서버 그룹을 마우스 오른쪽 단추로 클릭하고 **연결**을 가리켜 클릭한 다음 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-165">To execute queries against all the servers in a local server group, right-click the server group, point to click **Connect**, and then click **New Query**.</span></span> <span data-ttu-id="9955c-166">새 쿼리 편집기 창에서 쿼리를 실행하면 사용자 인증 컨텍스트를 비롯한 저장된 연결 정보를 사용하여 그룹의 모든 서버에 대해 해당 쿼리가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-166">When queries are executed in the new Query Editor window, they will execute against all servers in the group, using the stored connection information including the user authentication context.</span></span> <span data-ttu-id="9955c-167">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 등록되었지만 암호를 저장하지 않는 서버는 연결에 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-167">Servers registered by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication but not saving the password will fail to connect.</span></span>  
  
 <span data-ttu-id="9955c-168">중앙 관리 서버에 등록된 모든 서버에 대해 쿼리를 실행하려면 중앙 관리 서버를 확장하고 서버 그룹을 마우스 오른쪽 단추로 클릭한 다음 **연결**을 가리켜 클릭하고 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-168">To execute queries against all the servers that are registered with a Central Management Server, expand the Central Management Server, right-click the server group, point to click **Connect**, and then click **New Query**.</span></span> <span data-ttu-id="9955c-169">새 쿼리 편집기 창에서 쿼리를 실행하면 저장된 연결 정보와 사용자의 Windows 인증 컨텍스트를 사용하여 서버 그룹의 모든 서버에 대해 해당 쿼리가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9955c-169">When queries are executed in the new Query Editor window, they will execute against all of the servers in the server group, using the stored connection information and using the Windows Authentication context of the user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9955c-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9955c-170">See Also</span></span>  
 <span data-ttu-id="9955c-171">[개체 탐색기에서 시스템 개체 숨기기](../object/hide-system-objects-in-object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="9955c-171">[Hide System Objects in Object Explorer](../object/hide-system-objects-in-object-explorer.md) </span></span>  
 <span data-ttu-id="9955c-172">[등록된 서버 정보 내보내기&#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="9955c-172">[Export Registered Server Information &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="9955c-173">등록된 서버 정보 가져오기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="9955c-173">Import Registered Server Information &#40;SQL Server Management Studio&#41;</span></span>](import-registered-server-information-sql-server-management-studio.md)  
  
  
