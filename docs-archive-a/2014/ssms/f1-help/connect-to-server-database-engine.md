---
title: 서버에 연결(데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.connectoserverunknownservertype.f1
- sql12.swb.connection.login.sqlserver.f1
- sql12.swb.connection.login.sqlce.f1
- sql12.swb.manageSS2k.f1
- sql12.swb.connecttoce.f1
- sql12.swb.connecttoce.connectionproperties.f1
ms.assetid: ee9017b4-8a19-4360-9003-9e6484082d41
author: stevestein
ms.author: sstein
ms.openlocfilehash: ca227d1a3bbc13160962ba2fcad23ff011c950f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733480"
---
# <a name="connect-to-server-database-engine"></a><span data-ttu-id="c56de-102">서버에 연결(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="c56de-102">Connect to Server (Database Engine)</span></span>
  <span data-ttu-id="c56de-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]에 연결할 때 이 대화 상자를 사용하여 옵션을 확인하거나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-103">Use this dialog to view or specify options when connecting to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="c56de-104">대부분의 경우 **서버 이름** 상자에서 데이터베이스 서버의 컴퓨터 이름을 입력한 다음 **연결**을 클릭하여 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-104">In most cases, you can connect by entering the computer name of the database server in the **Server name** box and then clicking **Connect**.</span></span> <span data-ttu-id="c56de-105">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]에 연결하는 경우 컴퓨터 이름과 그 뒤에 **\sqlexpress**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-105">If you are connecting to [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], use the computer name followed by **\sqlexpress**.</span></span>  
  
 <span data-ttu-id="c56de-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결하는 데 다양한 요인이 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-106">Many factors can affect your ability to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="c56de-107">옵션</span><span class="sxs-lookup"><span data-stu-id="c56de-107">Options</span></span>  
 <span data-ttu-id="c56de-108">**서버 유형**</span><span class="sxs-lookup"><span data-stu-id="c56de-108">**Server type**</span></span>  
 <span data-ttu-id="c56de-109">개체 탐색기에서 서버를 등록하는 경우 연결할 서버 유형을 [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-109">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="c56de-110">대화 상자의 나머지 부분에는 선택한 서버 유형에 적용되는 옵션만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-110">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="c56de-111">등록된 서버에서 서버를 등록하는 경우 **서버 유형** 상자는 읽기 전용이며 등록된 서버 구성 요소에 표시된 서버 유형과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-111">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="c56de-112">다른 유형의 서버를 등록하려면 새 서버를 등록하기 전에 등록된 서버 도구 모음에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssEW](../../includes/ssew-md.md)]또는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-112">To register a different type of server, select [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssEW](../../includes/ssew-md.md)], or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="c56de-113">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="c56de-113">**Server name**</span></span>  
 <span data-ttu-id="c56de-114">연결할 서버 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-114">Select the server instance to connect to.</span></span> <span data-ttu-id="c56de-115">마지막으로 연결한 서버 인스턴스가 기본적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-115">The server instance last connected to is displayed by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c56de-116">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 의 활성 사용자 인스턴스에 연결하려면 np:\\\\.\pipe\3C3DF6B1-2262-47\tsql\query와 같이 파이프 이름을 지정하는 명명된 파이프 프로토콜을 사용하여 연결합니다. 자세한 내용은 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c56de-116">To connect to an active user instance of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] connect using named pipes protocol specifying the pipe name, such as np:\\\\.\pipe\3C3DF6B1-2262-47\tsql\query For more information, see the [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] documentation.</span></span>  
  
 <span data-ttu-id="c56de-117">**인증**</span><span class="sxs-lookup"><span data-stu-id="c56de-117">**Authentication**</span></span>  
 <span data-ttu-id="c56de-118">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결할 때는 두 가지 인증 모드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-118">Two authentication modes are available when connecting to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="c56de-119">**Windows 인증 모드(Windows 인증)**</span><span class="sxs-lookup"><span data-stu-id="c56de-119">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="c56de-120">Windows 인증 모드에서는 사용자가 Windows 사용자 계정을 통해 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-120">Windows Authentication mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="c56de-121">**SQL Server 인증**</span><span class="sxs-lookup"><span data-stu-id="c56de-121">**SQL Server Authentication**</span></span>  
 <span data-ttu-id="c56de-122">사용자가 지정한 로그인 이름과 암호를 사용하여 트러스트되지 않은 연결로부터 연결하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 계정이 설정되고 지정한 암호가 전에 기록한 암호와 일치하는지를 확인하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 자체적으로 인증을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-122">When a user connects with a specified login name and password from a non-trusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication itself by checking to see if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="c56de-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 로그인 계정이 설정되어 있지 않으면 인증이 실패하고 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-123">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c56de-124">가능하면 Windows 인증을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="c56de-124">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="c56de-125">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="c56de-125">**User name**</span></span>  
 <span data-ttu-id="c56de-126">연결에 사용할 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-126">Enter the user name to connect with.</span></span> <span data-ttu-id="c56de-127">이 옵션은 Windows 인증을 사용하여 연결하도록 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-127">This option is only available if you have selected to connect using Windows Authentication.</span></span>  
  
 <span data-ttu-id="c56de-128">**로그인**</span><span class="sxs-lookup"><span data-stu-id="c56de-128">**Login**</span></span>  
 <span data-ttu-id="c56de-129">연결 시 사용할 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-129">Enter the login to connect with.</span></span> <span data-ttu-id="c56de-130">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하도록 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-130">This option is only available if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="c56de-131">**암호**</span><span class="sxs-lookup"><span data-stu-id="c56de-131">**Password**</span></span>  
 <span data-ttu-id="c56de-132">로그인 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-132">Enter the password for the login.</span></span> <span data-ttu-id="c56de-133">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하도록 선택한 경우에만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-133">This option is only editable if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="c56de-134">**연결**</span><span class="sxs-lookup"><span data-stu-id="c56de-134">**Connect**</span></span>  
 <span data-ttu-id="c56de-135">위에서 선택한 서버에 연결하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-135">Click to connect to the server selected above.</span></span>  
  
 <span data-ttu-id="c56de-136">**Options**</span><span class="sxs-lookup"><span data-stu-id="c56de-136">**Options**</span></span>  
 <span data-ttu-id="c56de-137">서버 등록, 암호 저장 등의 추가 서버 연결 옵션을 표시하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c56de-137">Click to display additional server connection options, such as registering a server and remembering the password.</span></span>  
  
  
