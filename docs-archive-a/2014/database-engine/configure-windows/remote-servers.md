---
title: 원격 서버 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- server management [SQL Server], remote servers
- remote servers [SQL Server], configuring
- remote servers [SQL Server]
- servers [SQL Server], remote
- remote access option
ms.assetid: abf0fa24-f199-4273-9a1a-e8787ac9bee1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1d42fc2ed6acd4e46e383c0a56afcc8a8b27d3aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651267"
---
# <a name="remote-servers"></a><span data-ttu-id="4ca6e-102">원격 서버</span><span class="sxs-lookup"><span data-stu-id="4ca6e-102">Remote Servers</span></span>
  <span data-ttu-id="4ca6e-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 이전 버전과의 호환성을 위해서만 원격 서버를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-103">Remote servers are supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for backward compatibility only.</span></span> <span data-ttu-id="4ca6e-104">새 애플리케이션은 그 대신 연결된 서버를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-104">New applications should use linked servers instead.</span></span> <span data-ttu-id="4ca6e-105">자세한 내용은 [연결된 서버&#40;데이터베이스 엔진&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-105">For more information, see [Linked Servers &#40;Database Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md).</span></span>  
  
 <span data-ttu-id="4ca6e-106">원격 서버를 구성하면 별도의 연결을 설정하지 않고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스에 연결된 클라이언트가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 다른 인스턴스에서 저장 프로시저를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-106">A remote server configuration allows for a client connected to one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to execute a stored procedure on another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without establishing a separate connection.</span></span> <span data-ttu-id="4ca6e-107">대신 클라이언트가 연결된 서버는 클라이언트 요청을 수락하고 해당 클라이언트를 대신해서 원격 서버에 요청을 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-107">Instead, the server to which the client is connected accepts the client request and sends the request to the remote server on behalf of the client.</span></span> <span data-ttu-id="4ca6e-108">원격 서버는 요청을 처리하고 원래 서버에 결과를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-108">The remote server processes the request and returns any results to the original server.</span></span> <span data-ttu-id="4ca6e-109">원래 서버는 클라이언트에 다시 결과를 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-109">This server in turn passes those results to the client.</span></span> <span data-ttu-id="4ca6e-110">원격 서버 구성을 설정할 때는 보안을 설정하는 방법도 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-110">When you set up a remote server configuration, you should also consider how to establish security.</span></span>  
  
 <span data-ttu-id="4ca6e-111">다른 서버에서 저장 프로시저를 실행하기 위해 서버 구성을 설정할 때 기존의 원격 서버 구성이 없는 경우 원격 서버 대신에 연결된 서버를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-111">If you want to set up a server configuration to execute stored procedures on another server and do not have existing remote server configurations, use linked servers instead of remote servers.</span></span> <span data-ttu-id="4ca6e-112">저장 프로시저와 분산 쿼리는 둘 다 연결된 서버에 대해 허용되지만 원격 서버에 대해서는 저장 프로시저만이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-112">Both stored procedures and distributed queries are allowed against linked servers; however, only stored procedures are allowed against remote servers.</span></span>  
  
## <a name="remote-server-details"></a><span data-ttu-id="4ca6e-113">원격 서버 정보</span><span class="sxs-lookup"><span data-stu-id="4ca6e-113">Remote Server Details</span></span>  
 <span data-ttu-id="4ca6e-114">원격 서버는 쌍으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-114">Remote servers are set up in pairs.</span></span> <span data-ttu-id="4ca6e-115">한 쌍의 원격 서버를 설정하려면 양쪽 서버가 서로를 원격 서버로 인식하도록 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-115">To set up a pair of remote servers, configure both servers to recognize each other as remote servers.</span></span>  
  
 <span data-ttu-id="4ca6e-116">대개 원격 서버에 대한 구성 옵션은 설정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-116">Most of the time, you should not have to set configuration options for remote servers.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4ca6e-117">Set은 로컬 및 원격 컴퓨터 모두에 기본값을 설정하여 원격 서버 연결을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-117">Set sets the defaults on both the local and remote computers to allow for remote server connections.</span></span>  
  
 <span data-ttu-id="4ca6e-118">원격 서버에 액세스하려면 **remote access** 구성 옵션을 로컬 컴퓨터와 원격 컴퓨터에서 1로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-118">For remote server access to work, the **remote access** configuration option must be set to 1 on both the local and remote computers.</span></span> <span data-ttu-id="4ca6e-119">이것은 기본 설정입니다.  **원격 액세스** 는 원격 서버로부터의 로그인을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-119">(This is the default setting.)  **remote access** controls logins from remote servers.</span></span> <span data-ttu-id="4ca6e-120">[!INCLUDE[tsql](../../includes/tsql-md.md)] **sp_configure** 저장 프로시저 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 이 구성 옵션을 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-120">You can reset this configuration option by using either the [!INCLUDE[tsql](../../includes/tsql-md.md)] **sp_configure** stored procedure or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="4ca6e-121">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 옵션을 설정하려면 **서버 속성 연결** 페이지에서 **이 서버에 대한 원격 연결 허용**을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-121">To set the option in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **Server Properties Connections** page, use **Allow remote connections to this server**.</span></span> <span data-ttu-id="4ca6e-122">**서버 속성 연결** 페이지에 접근하려면 개체 탐색기에서 서버 이름을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-122">To reach the **Server Properties Connections** page, in Object Explorer, right-click the server name, and then click **Properties**.</span></span> <span data-ttu-id="4ca6e-123">**서버 속성** 페이지에서 **연결** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-123">On the **Server Properties** page, click the **Connections** page.</span></span>  
  
 <span data-ttu-id="4ca6e-124">로컬 서버에서 원격 서버 구성을 해제하여 쌍을 이루는 원격 서버의 사용자가 해당 로컬 서버에 액세스하는 것을 차단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-124">From the local server, you can disable a remote server configuration to prevent access to that local server by users on the remote server with which it is paired.</span></span>  
  
## <a name="security-for-remote-servers"></a><span data-ttu-id="4ca6e-125">원격 서버의 보안</span><span class="sxs-lookup"><span data-stu-id="4ca6e-125">Security for Remote Servers</span></span>  
 <span data-ttu-id="4ca6e-126">원격 서버에 대한 RPC(원격 프로시저 호출)를 설정하려면 해당 원격 서버 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스가 실행되는 로컬 서버에서 로그인 매핑을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-126">To enable remote procedure calls (RPC) against a remote server, you must set up login mappings on the remote server and possibly on the local server that is running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4ca6e-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 RPC는 기본적으로 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-127">RPC is disabled by default in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4ca6e-128">이 구성은 공격 받을 수 있는 노출 영역을 줄여 서버의 보안을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-128">This configuration enhances the security of your server by reducing its attackable surface area.</span></span> <span data-ttu-id="4ca6e-129">RPC를 사용하기 전에 이 기능을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-129">Before using RPC you must enable this feature.</span></span> <span data-ttu-id="4ca6e-130">자세한 내용은 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-130">For more information see [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>  
  
### <a name="setting-up-the-remote-server"></a><span data-ttu-id="4ca6e-131">원격 서버 설정</span><span class="sxs-lookup"><span data-stu-id="4ca6e-131">Setting Up the Remote Server</span></span>  
 <span data-ttu-id="4ca6e-132">원격 서버에서 원격 로그인 매핑을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-132">Remote login mappings must be set up on the remote server.</span></span> <span data-ttu-id="4ca6e-133">원격 서버에서는 이 매핑을 사용하여 지정된 서버와의 RPC 연결에 대한 수신 로그인을 로컬 로그인으로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-133">Using these mappings, the remote server maps the incoming login for an RPC connection from a specified server to a local login.</span></span> <span data-ttu-id="4ca6e-134">원격 로그인 매핑은 원격 서버에서 **sp_addremotelogin** 저장 프로시저를 사용하여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-134">Remote login mappings can be set up by using the **sp_addremotelogin** stored procedure on the remote server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4ca6e-135">**에서는** sp_remoteoption  **의** trusted [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]옵션이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-135">The **trusted** option of  **sp_remoteoption** is not supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="setting-up-the-local-server"></a><span data-ttu-id="4ca6e-136">로컬 서버 설정</span><span class="sxs-lookup"><span data-stu-id="4ca6e-136">Setting Up the Local Server</span></span>  
 <span data-ttu-id="4ca6e-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 로컬 로그인에 대해서는 로컬 서버에 로그인 매핑을 설정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-137">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authenticated local logins, you do not have to set up a login mapping on the local server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4ca6e-138">는 원격 서버 연결에 로컬 로그인과 암호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-138">uses the local login and password to connect to the remote server.</span></span> <span data-ttu-id="4ca6e-139">Windows 인증 로그인에 대해서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스가 원격 서버에 RPC 연결을 할 때 사용할 로그인과 암호를 정의하는 로컬 로그인 매핑을 로컬 서버에 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-139">For Windows authenticated logins, set up a local login mapping on a local server that defines what login and password are used by an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] when it makes an RPC connection to a remote server.</span></span>  
  
 <span data-ttu-id="4ca6e-140">Windows 인증에서 만든 로그인의 경우 사용자는 **sp_addlinkedservlogin** 저장 프로시저를 사용하여 로그인 이름 및 암호에 대한 매핑을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-140">For logins created by Windows Authentication, you must create a mapping to a login name and password by using the **sp_addlinkedservlogin** stored procedure.</span></span> <span data-ttu-id="4ca6e-141">이 로그인 이름과 암호는 원격 서버에서 예상하는 **sp_addremotelogin**이 만든 수신 로그인 및 암호와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-141">This login name and password must match the incoming login and password expected by the remote server, as created by **sp_addremotelogin**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4ca6e-142">가능하면 Windows 인증을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-142">When possible, use Windows Authentication.</span></span>  
  
### <a name="remote-server-security-example"></a><span data-ttu-id="4ca6e-143">원격 서버 보안 예</span><span class="sxs-lookup"><span data-stu-id="4ca6e-143">Remote Server Security Example</span></span>  
 <span data-ttu-id="4ca6e-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serverSend **및** serverReceive **와 같은**설치를 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-144">Consider these [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations: **serverSend** and **serverReceive**.</span></span> <span data-ttu-id="4ca6e-145">**serverReceive** 는 **serverSend**로부터의 **Sales_Mary**라는 수신 로그인을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serverReceive **의**Alice **라는**인증 로그인에 매핑하도록 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-145">**serverReceive** is configured to map an incoming login from **serverSend**, called **Sales_Mary**, to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authenticated login in **serverReceive**, called **Alice**.</span></span> <span data-ttu-id="4ca6e-146">**serverSend**로부터의 **Joe**라는 또 다른 수신 로그인은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**serverReceive**_의_**Joe** 라는 인증 로그인에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-146">Another incoming login from **serverSend**, called **Joe**, is mapped to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authenticated login in **serverReceive**_,_ called **Joe**.</span></span>  
  
 <span data-ttu-id="4ca6e-147">다음 Transact-SQL 코드 예제는 `serverSend` 에 대해 RPC를 수행하도록 `serverReceive`를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-147">The following Transact-SQL code example configures `serverSend` to perform RPCs against `serverReceive`.</span></span>  
  
```  
--Create remote server entry for RPCs   
--from serverSend in serverReceive.  
EXEC sp_addserver 'serverSend';  
GO  
  
--Create remote login mapping for login 'Sales_Mary' from serverSend  
--to Alice.  
EXEC sp_addremotelogin 'serverSend', 'Alice', 'Sales_Mary';  
GO  
--Create remote login mapping for login Joe from serverReceive   
--to same login.  
--Assumes same password for Joe in both servers.  
EXEC sp_addremotelogin 'serverSend', 'Joe', 'Joe';  
GO  
```  
  
 <span data-ttu-id="4ca6e-148">`serverSend`에서 Windows 인증 로그인 `Sales\Mary` 에 대해 로그인 `Sales_Mary`으로의 로컬 로그인 매핑이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-148">On `serverSend`, a local login mapping is created for a Windows authenticated login `Sales\Mary` to a login `Sales_Mary`.</span></span> <span data-ttu-id="4ca6e-149">동일한 로그인 이름과 암호를 사용하는 것이 기본값이고 `Joe`가 `serverReceive` 에 대한 매핑을 가지고 있으므로 `Joe`에게는 로컬 매핑이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-149">No local mapping is required for `Joe`, because the default is to use the same login name and password, and `serverReceive` has a mapping for `Joe`.</span></span>  
  
```  
--Create a remote server entry for RPCs from serverReceive.  
EXEC sp_addserver 'serverReceive';  
GO  
--Create a local login mapping for the Windows authenticated login.  
--Sales\Mary to Sales_Mary. The password should match the  
--password for the login Sales_Mary in serverReceive.  
EXEC sp_addlinkedsrvlogin 'serverReceive', false, 'Sales\Mary',  
   'Sales_Mary', '430[fj%dk';  
GO  
```  
  
## <a name="viewing-local-or-remote-server-properties"></a><span data-ttu-id="4ca6e-150">로컬 서버 또는 원격 서버 속성 보기</span><span class="sxs-lookup"><span data-stu-id="4ca6e-150">Viewing Local or Remote Server Properties</span></span>  
 <span data-ttu-id="4ca6e-151">**xp_msver** 확장 저장 프로시저를 사용하여 로컬 서버 또는 원격 서버의 특성을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-151">You can use the **xp_msver** extended stored procedure to review server attributes for local or remote servers.</span></span> <span data-ttu-id="4ca6e-152">이러한 특성에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전 번호, 컴퓨터의 프로세서 유형과 개수 및 운영 체제 버전이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-152">These attributes include the version number of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the type and number of processors in the computer, and the version of the operating system.</span></span> <span data-ttu-id="4ca6e-153">로컬 서버에서는 원격 서버의 데이터베이스, 파일, 로그인 및 도구를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-153">From the local server, you can view databases, files, logins, and tools for a remote server.</span></span> <span data-ttu-id="4ca6e-154">자세한 내용은 [xp_msver&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/xp-msver-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ca6e-154">For more information, see [xp_msver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/xp-msver-transact-sql).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="4ca6e-155">관련 작업</span><span class="sxs-lookup"><span data-stu-id="4ca6e-155">Related Tasks</span></span>  
 [<span data-ttu-id="4ca6e-156">연결된 서버&#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="4ca6e-156">Linked Servers &#40;Database Engine&#41;</span></span>](../../relational-databases/linked-servers/linked-servers-database-engine.md)  
  
## <a name="related-content"></a><span data-ttu-id="4ca6e-157">관련 내용</span><span class="sxs-lookup"><span data-stu-id="4ca6e-157">Related Content</span></span>  
 [<span data-ttu-id="4ca6e-158">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4ca6e-158">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
 [<span data-ttu-id="4ca6e-159">remote access 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="4ca6e-159">Configure the remote access Server Configuration Option</span></span>](configure-the-remote-access-server-configuration-option.md)  
  
 [<span data-ttu-id="4ca6e-160">RECONFIGURE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4ca6e-160">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
