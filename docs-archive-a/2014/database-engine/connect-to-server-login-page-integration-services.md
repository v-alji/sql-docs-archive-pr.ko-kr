---
title: 서버에 연결(로그인 페이지) Integration Services | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttodtsserver.login.f1
- sql12.swb.connecttodts.login.f1
ms.assetid: 402c2de4-f4ea-40b0-909f-3ddf3bd59950
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 285518f4a1f3d9180d2c3c07a41bf75a00ea3593
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740365"
---
# <a name="connect-to-server-login-page-integration-services"></a><span data-ttu-id="bf0b4-102">서버에 연결(로그인 페이지) Integration Services</span><span class="sxs-lookup"><span data-stu-id="bf0b4-102">Connect to Server (Login Page) Integration Services</span></span>
  <span data-ttu-id="bf0b4-103">에 연결할 때이 탭을 사용 하 여 다음 옵션을 확인 하거나 지정할 수 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf0b4-103">Use this tab to view or specify the following options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="bf0b4-104">옵션</span><span class="sxs-lookup"><span data-stu-id="bf0b4-104">Options</span></span>  
 <span data-ttu-id="bf0b4-105">**서버 유형**</span><span class="sxs-lookup"><span data-stu-id="bf0b4-105">**Server type**</span></span>  
 <span data-ttu-id="bf0b4-106">개체 탐색기에서 서버를 등록할 때 연결할 서버 유형을 [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services 또는 Integration Services 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bf0b4-106">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="bf0b4-107">대화 상자의 나머지 부분에는 선택한 서버 유형에 적용되는 옵션만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf0b4-107">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="bf0b4-108">등록된 서버에서 서버를 등록하는 경우 **서버 유형** 상자는 읽기 전용이며 등록된 서버 구성 요소에 표시된 서버 유형과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="bf0b4-108">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="bf0b4-109">다른 유형의 서버를 등록하려면 새 서버를 등록하기 전에 등록된 서버 도구 모음에서 [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services 또는 Integration Services를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bf0b4-109">To register a different type of server, select [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="bf0b4-110">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="bf0b4-110">**Server name**</span></span>  
 <span data-ttu-id="bf0b4-111">연결할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bf0b4-111">Select the server to connect to.</span></span> <span data-ttu-id="bf0b4-112">마지막으로 연결한 서버 인스턴스가 기본적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf0b4-112">The server instance last connected to is displayed by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bf0b4-113">*\<servername>* \\ *\<instancename>* [!INCLUDE[ssIS](../includes/ssis-md.md)] 는 컴퓨터에서 여러 인스턴스를 지원 하지 않으므로을 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="bf0b4-113">Do not use *\<servername>*\\*\<instancename>*, because [!INCLUDE[ssIS](../includes/ssis-md.md)] does not support multiple instances on a computer.</span></span>  
  
 <span data-ttu-id="bf0b4-114">**인증**</span><span class="sxs-lookup"><span data-stu-id="bf0b4-114">**Authentication**</span></span>  
 <span data-ttu-id="bf0b4-115">[!INCLUDE[msCoName](../includes/msconame-md.md)] 에는 [!INCLUDE[ssIS](../includes/ssis-md.md)]Windows 인증만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf0b4-115">Only [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span> <span data-ttu-id="bf0b4-116">Windows 인증 모드에서는 사용자가 Windows 사용자 계정을 통해 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf0b4-116">Windows Authentication mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="bf0b4-117">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="bf0b4-117">**User name**</span></span>  
 <span data-ttu-id="bf0b4-118">[!INCLUDE[ssIS](../includes/ssis-md.md)]에는 Windows 인증만 사용 가능하므로 이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf0b4-118">This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="bf0b4-119">**암호**</span><span class="sxs-lookup"><span data-stu-id="bf0b4-119">**Password**</span></span>  
 <span data-ttu-id="bf0b4-120">[!INCLUDE[ssIS](../includes/ssis-md.md)]에는 Windows 인증만 사용 가능하므로 이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf0b4-120">This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="bf0b4-121">**암호 기억**</span><span class="sxs-lookup"><span data-stu-id="bf0b4-121">**Remember password**</span></span>  
 <span data-ttu-id="bf0b4-122">[!INCLUDE[ssIS](../includes/ssis-md.md)]에는 Windows 인증만 사용 가능하므로 이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf0b4-122">This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="bf0b4-123">**연결**</span><span class="sxs-lookup"><span data-stu-id="bf0b4-123">**Connect**</span></span>  
 <span data-ttu-id="bf0b4-124">위에서 선택한 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bf0b4-124">Connect to the server selected above.</span></span>  
  
 <span data-ttu-id="bf0b4-125">**Options**</span><span class="sxs-lookup"><span data-stu-id="bf0b4-125">**Options**</span></span>  
 <span data-ttu-id="bf0b4-126">대화 상자를 변경하고 암호 저장과 같은 추가 서버 연결 옵션을 숨기려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf0b4-126">Click to change the dialog and hide the additional server connection options, such as remembering the password.</span></span>  
  
  
