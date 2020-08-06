---
title: 새 서버 등록 또는 서버 등록 편집 (일반 탭) (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.general.reportserver.f1
ms.assetid: 5f899a8e-52ef-46b5-b7a9-f200ccd9f724
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 195756498dcefe4686d4b06e758dba9919c0b304
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660128"
---
# <a name="new-or-edit-server-registration-general-tab-reporting-services"></a><span data-ttu-id="e8683-102">새 서버 등록 또는 서버 등록 편집(일반 탭)(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="e8683-102">New or Edit Server Registration (General Tab) (Reporting Services)</span></span>
  <span data-ttu-id="e8683-103">이 탭을 사용하여 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]인스턴스의 등록 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-103">Use this tab to specify options when registering an instance of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e8683-104">이 페이지에 액세스하려면 등록된 서버에서 **등록된 서버** 도구 모음의 **Reporting Services** 를 클릭하고 **Reporting Services**와 같은 등록된 서버 그룹을 마우스 오른쪽 단추로 클릭한 다음 **새로 만들기**를 가리키고 **서버 등록**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-104">To access this page, in Registered Servers, click **Reporting Services** on the **Registered Servers** toolbar, right-click any registered servers group such as **Reporting Services**, point to **New**, and then click **Server Registration**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e8683-105">옵션</span><span class="sxs-lookup"><span data-stu-id="e8683-105">Options</span></span>  
 <span data-ttu-id="e8683-106">**서버 유형**</span><span class="sxs-lookup"><span data-stu-id="e8683-106">**Server type**</span></span>  
 <span data-ttu-id="e8683-107">등록 된 서버에서 서버를 등록 하는 경우 **서버 유형** 상자는 읽기 전용 이며 **등록 된 서버** 창에 표시 된 서버 유형과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-107">When a server is registered from Registered Servers, the **Server type** box is read-only, and it matches the type of server displayed in the **Registered Servers** pane.</span></span> <span data-ttu-id="e8683-108">다른 유형의 서버를 등록하려면 새 서버를 등록하기 전에 **등록된 서버** 도구 모음에서 원하는 서버를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-108">To register a different type of server, click the server you want on the **Registered Servers** toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="e8683-109">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="e8683-109">**Server name**</span></span>  
 <span data-ttu-id="e8683-110">연결할 보고서 서버 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-110">Specify the report server instance to connect to.</span></span> <span data-ttu-id="e8683-111">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]에서는 해당 인스턴스 이름을 통해 보고서 서버에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-111">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], you can access a report server through its instance name.</span></span> <span data-ttu-id="e8683-112">설치하는 각 SQL Server 인스턴스에 대해 하나의 보고서 서버 인스턴스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-112">You can have one report server instance for each SQL Server instance that you install.</span></span> <span data-ttu-id="e8683-113">기본 인스턴스를 사용하는 경우에는 SQL Server 인스턴스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-113">If you are using the default instance, type the name of the SQL Server instance.</span></span> <span data-ttu-id="e8683-114">명명된 인스턴스를 사용하는 경우에는 MSSQL$InstanceName 형식으로 보고서 서버에 연결할 명명된 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-114">If you are using a named instance, specify the named instance to connect to the report server in the format MSSQL$InstanceName.</span></span>  
  
 <span data-ttu-id="e8683-115">**인증**</span><span class="sxs-lookup"><span data-stu-id="e8683-115">**Authentication**</span></span>  
 <span data-ttu-id="e8683-116">보고서 서버에 대한 인증은 인터넷 정보 서비스(IIS)를 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-116">Authentication to a report server is made through Internet Information Services (IIS).</span></span> <span data-ttu-id="e8683-117">Reporting Services에 연결할 때는 다음 인증 모드 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-117">Select from one of the following authentication modes when connecting to Reporting Services:</span></span>  
  
 <span data-ttu-id="e8683-118">**Windows 인증 모드(Windows 인증)**</span><span class="sxs-lookup"><span data-stu-id="e8683-118">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 <span data-ttu-id="e8683-119">[!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 자격 증명을 사용하여 보고서 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-119">Connect to the report server instance using your [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows credentials.</span></span>  
  
 <span data-ttu-id="e8683-120">**기본 인증**</span><span class="sxs-lookup"><span data-stu-id="e8683-120">**Basic Authentication**</span></span>  
 <span data-ttu-id="e8683-121">Reporting Services 설치에서 기본 인증을 사용하도록 구성되어 있는 경우 **기본 인증** 을 사용하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-121">Connect using **Basic Authentication** if your Reporting Services installation is configured to use Basic Authentication.</span></span>  
  
 <span data-ttu-id="e8683-122">**폼 인증**</span><span class="sxs-lookup"><span data-stu-id="e8683-122">**Forms Authentication**</span></span>  
 <span data-ttu-id="e8683-123">Reporting Services 설치에서 사용자 지정 인증 확장 프로그램을 사용하도록 구성되어 있는 경우 **폼 인증** 을 사용하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-123">Connect using **Forms Authentication** if your Reporting Services installation is configured to use a custom authentication extension.</span></span>  
  
 <span data-ttu-id="e8683-124">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="e8683-124">**User Name**</span></span>  
 <span data-ttu-id="e8683-125">연결에 사용할 로그인 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-125">Enter the login name to use for the connection.</span></span> <span data-ttu-id="e8683-126">이 옵션은 **기본 인증** 또는 **폼 인증**을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-126">This option is only available if you have selected **Basic** or **Forms Authentication**.</span></span>  
  
 <span data-ttu-id="e8683-127">**암호**</span><span class="sxs-lookup"><span data-stu-id="e8683-127">**Password**</span></span>  
 <span data-ttu-id="e8683-128">사용자 이름에 대한 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-128">Enter the password for the user name.</span></span> <span data-ttu-id="e8683-129">이 옵션은 **기본 인증** 또는 **폼 인증**을 선택한 경우에만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-129">This option is only editable if you have selected **Basic** or **Forms Authentication**.</span></span>  
  
 <span data-ttu-id="e8683-130">**암호 기억**</span><span class="sxs-lookup"><span data-stu-id="e8683-130">**Remember password**</span></span>  
 <span data-ttu-id="e8683-131">입력한 암호를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-131">Store the password you have entered.</span></span> <span data-ttu-id="e8683-132">이 옵션은 **기본 인증** 또는 **폼 인증**을 클릭한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-132">This option is only available if you have clicked **Basic** or **Forms Authentication**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8683-133"> 저장한 암호를 더 이상 저장하지 않으려면 이 확인란의 선택을 취소한 다음 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-133">If you have stored the password and want to stop storing it, clear this check box and then click **Save**.</span></span>  
  
 <span data-ttu-id="e8683-134">**등록된 서버 이름**</span><span class="sxs-lookup"><span data-stu-id="e8683-134">**Registered server name**</span></span>  
 <span data-ttu-id="e8683-135">등록된 서버에 표시할 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-135">The name you want to appear in Registered Servers.</span></span> <span data-ttu-id="e8683-136">이 이름은 **서버 이름** 상자에 있는 이름과 일치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-136">This name does not have to match the name in the **Server name** box.</span></span>  
  
 <span data-ttu-id="e8683-137">**등록된 서버 설명**</span><span class="sxs-lookup"><span data-stu-id="e8683-137">**Registered server description**</span></span>  
 <span data-ttu-id="e8683-138">서버에 대한 선택적 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-138">Enter an optional description of the server.</span></span>  
  
 <span data-ttu-id="e8683-139">**Test**</span><span class="sxs-lookup"><span data-stu-id="e8683-139">**Test**</span></span>  
 <span data-ttu-id="e8683-140">**서버 이름**에서 선택한 서버 연결을 테스트하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-140">Click to test the connection to the server selected in **Server name**.</span></span>  
  
 <span data-ttu-id="e8683-141">**저장**</span><span class="sxs-lookup"><span data-stu-id="e8683-141">**Save**</span></span>  
 <span data-ttu-id="e8683-142">등록된 서버 설정을 저장하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8683-142">Click to save the registered server settings.</span></span>  
  
  
