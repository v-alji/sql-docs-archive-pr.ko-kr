---
title: 서버에 연결(Reporting Services) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connection.login.reportserver.f1
ms.assetid: ef81b658-8eb5-4636-ac81-eead10cc7b9f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 10c613af00e343f1f147c4ad293dfa300a95b50d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740354"
---
# <a name="connect-to-server-reporting-services"></a><span data-ttu-id="693b1-102">서버에 연결(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="693b1-102">Connect to Server (Reporting Services)</span></span>
  <span data-ttu-id="693b1-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]에 연결할 때 이 대화 상자를 사용하여 옵션을 확인하거나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-103">Use this dialog to view or specify options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="693b1-104">옵션</span><span class="sxs-lookup"><span data-stu-id="693b1-104">Options</span></span>  
 <span data-ttu-id="693b1-105">**서버 유형**</span><span class="sxs-lookup"><span data-stu-id="693b1-105">**Server type**</span></span>  
 <span data-ttu-id="693b1-106">**개체 탐색기**에서 서버를 등록 하는 경우 연결할 서버 유형을 [!INCLUDE[ssDE](../includes/ssde-md.md)] , Analysis Services, Reporting Services 또는 Integration Services 중에서 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-106">When registering a server from **Object Explorer**, select the type of server to connect to: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="693b1-107">대화 상자의 나머지 부분에는 선택한 서버 유형에 적용되는 옵션만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-107">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="693b1-108">**등록 된 서버**에서 서버를 등록 하는 경우 **서버 유형** 상자는 읽기 전용 이며 **등록 된 서버** 구성 요소에 표시 된 서버 유형과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-108">When registering a server from **Registered Servers**, the **Server type** box is read-only, and matches the type of server displayed in the **Registered Servers** component.</span></span> <span data-ttu-id="693b1-109">다른 유형의 서버를 등록 하려면 [!INCLUDE[ssDE](../includes/ssde-md.md)] 새 서버를 등록 하기 전에 **등록 된 서버** 도구 모음에서, Analysis Services, Reporting Services 또는 Integration Services를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-109">To register a different type of server, select [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the **Registered Servers** toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="693b1-110">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="693b1-110">**Server name**</span></span>  
 <span data-ttu-id="693b1-111">연결하려는 보고서 서버 인스턴스의 서버 모드에 따라 입력해야 하는 값이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-111">The server mode of the report server instance you are connecting to determines the value you must enter.</span></span>  
  
 <span data-ttu-id="693b1-112">기본 모드로 실행되는 보고서 서버의 경우 연결할 보고서 서버 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-112">For a report server that runs in native mode, specify the report server instance to connect to.</span></span> <span data-ttu-id="693b1-113">기본 인스턴스를 사용하는 경우 서버 이름은 대개 컴퓨터 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-113">If you are using the default instance, the server name is typically the name of the computer.</span></span> <span data-ttu-id="693b1-114">명명 된 인스턴스를 설치한 경우 인스턴스 이름을<InstanceName 형식으로 서버 이름에 추가 \<servername> \\ \> 합니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-114">If you installed a named instance, append the instance name to the server name in this format: \<servername>\\<InstanceName\>.</span></span> <span data-ttu-id="693b1-115">Reporting Services는 백슬래시 문자를 사용하여 인스턴스 이름을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-115">Reporting Services uses the backslash character to delimit the instance name.</span></span>  
  
 <span data-ttu-id="693b1-116">SharePoint 통합 모드로 실행되는 보고서 서버의 경우 SharePoint 사이트를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-116">For a report server that runs in SharePoint integrated mode, you must specify a SharePoint site.</span></span> <span data-ttu-id="693b1-117">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]와 통합된 사이트 컬렉션에 있는 아무 사이트나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-117">You can specify any site in a site collection that is integrated with [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="693b1-118">URL을 지정할 때는 HTTP 또는 HTTPS 접두사를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-118">The URL that you provide must include the HTTP or HTTPS prefix.</span></span> <span data-ttu-id="693b1-119">Management Studio에서 보고서 서버 인스턴스에 연결하려면 SharePoint에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-119">You must have permission to access the SharePoint site in order to connect to it in Management Studio.</span></span> <span data-ttu-id="693b1-120">할당 받은 권한 수준에 따라 보고 관리할 수 있는 항목이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-120">The permission level you are assigned to will determine which items you can view and manage.</span></span> <span data-ttu-id="693b1-121">자세한 내용은 [Management Studio에서 보고서 서버에 연결](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="693b1-121">For more information, see [Connect to a Report Server in Management Studio](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md).</span></span>  
  
 <span data-ttu-id="693b1-122">**인증**</span><span class="sxs-lookup"><span data-stu-id="693b1-122">**Authentication**</span></span>  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="693b1-123">제공한 사용자 지정 인증 확장 프로그램이 처리하는 Windows 인증 요청 또는 폼 인증 요청을 받아들이도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-123">can be configured to accept Windows Authentication requests or Forms authentication requests that are handled by a custom authentication extension that you provide.</span></span> <span data-ttu-id="693b1-124">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]에 연결할 때는 다음 인증 모드 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-124">Select from one of the following authentication modes when connecting to [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]:</span></span>  
  
 <span data-ttu-id="693b1-125">**Windows 인증 모드(Windows 인증)**</span><span class="sxs-lookup"><span data-stu-id="693b1-125">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 <span data-ttu-id="693b1-126">[!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 자격 증명을 사용하여 보고서 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-126">Connect to the report server instance using your [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows credentials.</span></span>  
  
 <span data-ttu-id="693b1-127">**기본 인증**</span><span class="sxs-lookup"><span data-stu-id="693b1-127">**Basic Authentication**</span></span>  
 <span data-ttu-id="693b1-128">Reporting Services 설치에서 기본 인증을 사용하도록 구성되어 있는 경우 **기본 인증** 을 사용하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-128">Connect using **Basic Authentication** if your Reporting Services installation is configured to use Basic Authentication.</span></span>  
  
 <span data-ttu-id="693b1-129">**폼 인증**</span><span class="sxs-lookup"><span data-stu-id="693b1-129">**Forms Authentication**</span></span>  
 <span data-ttu-id="693b1-130">Reporting Services 설치에서 사용자 지정 인증 확장 프로그램을 사용하도록 구성되어 있는 경우 **폼 인증** 을 사용하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-130">Connect using **Forms Authentication** if your Reporting Services installation is configured to use a custom authentication extension.</span></span>  
  
 <span data-ttu-id="693b1-131">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="693b1-131">**User Name**</span></span>  
 <span data-ttu-id="693b1-132">연결에 사용할 로그인 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-132">Enter the login name to use for the connection.</span></span> <span data-ttu-id="693b1-133">이 옵션은 **기본 인증** 또는 **폼 인증**을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-133">This option is only available if you have selected **Basic** or **Forms Authentication**.</span></span>  
  
 <span data-ttu-id="693b1-134">**암호**</span><span class="sxs-lookup"><span data-stu-id="693b1-134">**Password**</span></span>  
 <span data-ttu-id="693b1-135">사용자 이름에 대한 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-135">Enter the password for the user name.</span></span> <span data-ttu-id="693b1-136">이 옵션은 **기본 인증** 또는 **폼 인증**을 선택한 경우에만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-136">This option is only editable if you have selected **Basic** or **Forms Authentication**.</span></span>  
  
 <span data-ttu-id="693b1-137">**연결**</span><span class="sxs-lookup"><span data-stu-id="693b1-137">**Connect**</span></span>  
 <span data-ttu-id="693b1-138">위에서 선택한 서버에 연결하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-138">Click to connect to the server selected above.</span></span>  
  
 <span data-ttu-id="693b1-139">**Options**</span><span class="sxs-lookup"><span data-stu-id="693b1-139">**Options**</span></span>  
 <span data-ttu-id="693b1-140">서버 등록, 암호 저장 등의 추가 서버 연결 옵션을 표시하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="693b1-140">Click to display additional server connection options, such as registering a server and remembering the password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="693b1-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="693b1-141">See Also</span></span>  
 <span data-ttu-id="693b1-142">[SSRS Configuration Manager &#40;보고서 서버 데이터베이스 연결 구성&#41;](../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="693b1-142">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="693b1-143">[Management Studio에서 보고서 서버에 연결](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="693b1-143">[Connect to a Report Server in Management Studio](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="693b1-144">보고서 서버 인증</span><span class="sxs-lookup"><span data-stu-id="693b1-144">Authentication with the Report Server</span></span>](../reporting-services/security/authentication-with-the-report-server.md)  
  
  
