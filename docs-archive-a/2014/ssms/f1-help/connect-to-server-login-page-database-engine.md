---
title: 서버에 연결(로그인 페이지) 데이터베이스 엔진 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttosqlserver.login.f1
ms.assetid: e08cfbc3-bed5-4401-a13b-1c66d902fe32
author: stevestein
ms.author: sstein
ms.openlocfilehash: 665a5c491b0bea1145c60d15f1006de97281a30d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733483"
---
# <a name="connect-to-server-login-page-database-engine"></a><span data-ttu-id="1f638-102">서버에 연결(로그인 페이지) 데이터베이스 엔진</span><span class="sxs-lookup"><span data-stu-id="1f638-102">Connect to Server (Login Page) Database Engine</span></span>
  <span data-ttu-id="1f638-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]에 연결할 때 이 탭을 사용하여 옵션을 확인하거나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-103">Use this tab to view or specify options when connecting to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f638-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증으로 연결하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 Windows 인증 모드로 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-104">To connect with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be configured in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows Authentication mode.</span></span> <span data-ttu-id="1f638-105">인증 모드를 확인 하 고 인증 모드를 변경 하는 방법에 대 한 자세한 내용은 [서버 인증 모드 변경](../../database-engine/configure-windows/change-server-authentication-mode.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f638-105">For more information about how to determine the authentication mode and to change the authentication mode, see [Change Server Authentication Mode](../../database-engine/configure-windows/change-server-authentication-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1f638-106">옵션</span><span class="sxs-lookup"><span data-stu-id="1f638-106">Options</span></span>  
 <span data-ttu-id="1f638-107">**서버 유형**</span><span class="sxs-lookup"><span data-stu-id="1f638-107">**Server type**</span></span>  
 <span data-ttu-id="1f638-108">개체 탐색기에서 서버를 등록할 때 연결할 서버 유형을 [!INCLUDE[ssDE](../../includes/ssde-md.md)], Analysis Services, Reporting Services 또는 Integration Services 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-108">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="1f638-109">대화 상자의 나머지 부분에는 선택한 서버 유형에 적용되는 옵션만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-109">The rest of the dialog box shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="1f638-110">등록된 서버에서 서버를 등록하는 경우 **서버 유형** 상자는 읽기 전용이며 등록된 서버 구성 요소에 표시된 서버 유형과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-110">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="1f638-111">다른 유형의 서버를 등록하려면 새 서버를 등록하기 전에 등록된 서버 도구 모음에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)], Analysis Services, Reporting Services 또는 Integration Services를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-111">To register a different type of server, select [!INCLUDE[ssDE](../../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="1f638-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 통해 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]데이터베이스 엔진 인스턴스에 연결할 때는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용해야 하며 **서버에 연결** 대화 상자의 **연결 속성** 탭에서 데이터베이스를 지정해야 합니다. **연결 암호화** 확인란을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-112">When connecting to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine through [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], you must use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication and specify a database in the **Connect to Server** dialog box, on the **Connection Properties** tab. Ensure that you select the **Encrypt connection** checkbox.</span></span>  
  
 <span data-ttu-id="1f638-113">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 **master**에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-113">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to **master**.</span></span> <span data-ttu-id="1f638-114">사용자 데이터베이스를 지정하면 개체 탐색기에서 해당 데이터베이스와 해당 개체만 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-114">If you specify a user database, you will only see that database and its objects in Object Explorer.</span></span> <span data-ttu-id="1f638-115">**master**에 연결하면 모든 데이터베이스를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-115">If you connect to **master**, you will be able to see all databases.</span></span> <span data-ttu-id="1f638-116">자세한 내용은 [Azure SQL Database 개요](/azure/sql-database/sql-database-technical-overview)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f638-116">For more information, see the [Azure SQL Database Overview](/azure/sql-database/sql-database-technical-overview).</span></span>  
  
 <span data-ttu-id="1f638-117">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="1f638-117">**Server name**</span></span>  
 <span data-ttu-id="1f638-118">연결할 서버 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-118">Select the server instance to connect to.</span></span> <span data-ttu-id="1f638-119">마지막으로 연결한 서버 인스턴스가 기본적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-119">The server instance last connected to is displayed by default.</span></span>  
  
 <span data-ttu-id="1f638-120">**인증**</span><span class="sxs-lookup"><span data-stu-id="1f638-120">**Authentication**</span></span>  
 <span data-ttu-id="1f638-121">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]인스턴스에 연결할 때는 두 가지 인증 모드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-121">Two authentication modes are available when connecting to an instance of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1f638-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 통해 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]데이터베이스 엔진 인스턴스에 연결할 때는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용해야 하며 **서버에 연결** 대화 상자의 **연결 속성** 탭에서 데이터베이스를 지정해야 합니다. **연결 암호화** 확인란을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-122">When connecting to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine through [!INCLUDE[ssSDS](../../includes/sssds-md.md)], you must use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication and specify a database in the **Connect to Server** dialog box, on the **Connection Properties** tab. Ensure that you select the **Encrypt connection** checkbox.</span></span>  
  
 <span data-ttu-id="1f638-123">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 **master**에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-123">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to **master**.</span></span> <span data-ttu-id="1f638-124">사용자 데이터베이스를 지정하면 개체 탐색기에서 해당 데이터베이스와 해당 개체만 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-124">If you specify a user database, you will only see that database and its objects in Object Explorer.</span></span> <span data-ttu-id="1f638-125">**master**에 연결하면 모든 데이터베이스를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-125">If you connect to **master**, you will be able to see all databases.</span></span> <span data-ttu-id="1f638-126">자세한 내용은 [Azure SQL Database 개요](/azure/sql-database/sql-database-technical-overview)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f638-126">For more information, see the [Azure SQL Database Overview](/azure/sql-database/sql-database-technical-overview).</span></span>  
  
 <span data-ttu-id="1f638-127">**Windows 인증 모드(Windows 인증)**</span><span class="sxs-lookup"><span data-stu-id="1f638-127">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="1f638-128">Windows 인증 모드에서는 사용자가 Windows 사용자 계정을 통해 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-128">Windows Authentication mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="1f638-129">**SQL Server 인증**</span><span class="sxs-lookup"><span data-stu-id="1f638-129">**SQL Server Authentication**</span></span>  
 <span data-ttu-id="1f638-130">사용자가 지정한 로그인 이름과 암호를 사용하여 트러스트되지 않은 연결로부터 연결하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 계정이 설정되고 지정한 암호가 전에 기록한 암호와 일치하는지를 확인하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 자체적으로 인증을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-130">When a user connects with a specified login name and password from a non-trusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication itself by checking to see if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="1f638-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 로그인 계정이 설정되어 있지 않으면 인증이 실패하고 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-131">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1f638-132">가능하면 Windows 인증을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="1f638-132">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="1f638-133">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="1f638-133">**User name**</span></span>  
 <span data-ttu-id="1f638-134">연결에 사용할 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-134">Enter the user name to connect with.</span></span> <span data-ttu-id="1f638-135">이 옵션은 Windows 인증을 사용하여 연결하도록 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-135">This option is only available if you have selected to connect using Windows Authentication.</span></span>  
  
 <span data-ttu-id="1f638-136">**로그인**</span><span class="sxs-lookup"><span data-stu-id="1f638-136">**Login**</span></span>  
 <span data-ttu-id="1f638-137">연결 시 사용할 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-137">Enter the login to connect with.</span></span> <span data-ttu-id="1f638-138">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하도록 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-138">This option is only available if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="1f638-139">**암호**</span><span class="sxs-lookup"><span data-stu-id="1f638-139">**Password**</span></span>  
 <span data-ttu-id="1f638-140">로그인 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-140">Enter the password for the login.</span></span> <span data-ttu-id="1f638-141">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하도록 선택한 경우에만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-141">This option is only editable if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="1f638-142">**암호 기억**</span><span class="sxs-lookup"><span data-stu-id="1f638-142">**Remember password**</span></span>  
 <span data-ttu-id="1f638-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 입력한 암호를 저장하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-143">Click to have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] store the password you have entered.</span></span> <span data-ttu-id="1f638-144">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하도록 선택한 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-144">This option is only displayed if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="1f638-145">**연결**</span><span class="sxs-lookup"><span data-stu-id="1f638-145">**Connect**</span></span>  
 <span data-ttu-id="1f638-146">위에서 선택한 서버에 연결하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-146">Click to connect to the server selected above.</span></span>  
  
 <span data-ttu-id="1f638-147">**Options**</span><span class="sxs-lookup"><span data-stu-id="1f638-147">**Options**</span></span>  
 <span data-ttu-id="1f638-148">대화 상자를 변경하여 암호 저장과 같은 추가 서버 연결 옵션을 숨기려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f638-148">Click to change the dialog box and hide the additional server connection options, such as remembering the password.</span></span>  
  
  
