---
title: 서버에 연결(Analysis Services) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connection.login.analysisserver.f1
ms.assetid: 7e277d22-8d4b-422e-8882-7c5dd7a6d915
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b3530f38534e09ef19e77293880129274dfc211b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727343"
---
# <a name="connect-to-server-analysis-services"></a><span data-ttu-id="3637e-102">서버에 연결(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="3637e-102">Connect to Server (Analysis Services)</span></span>
  <span data-ttu-id="3637e-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에 연결할 때 이 대화 상자를 사용하여 옵션을 확인하거나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3637e-103">Use this dialog to view or specify options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="3637e-104">옵션</span><span class="sxs-lookup"><span data-stu-id="3637e-104">Options</span></span>  
 <span data-ttu-id="3637e-105">**서버 유형**</span><span class="sxs-lookup"><span data-stu-id="3637e-105">**Server type**</span></span>  
 <span data-ttu-id="3637e-106">개체 탐색기에서 서버를 등록할 때 연결할 서버 유형을 [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services 또는 Integration Services 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3637e-106">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="3637e-107">대화 상자의 나머지 부분에는 선택한 서버 유형에 적용되는 옵션만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3637e-107">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="3637e-108">등록된 서버에서 서버를 등록하는 경우 **서버 유형** 상자는 읽기 전용이며 등록된 서버 구성 요소에 표시된 서버 유형과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="3637e-108">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="3637e-109">다른 유형의 서버를 등록하려면 새 서버를 등록하기 전에 등록된 서버 도구 모음에서 [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services 또는 Integration Services를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3637e-109">To register a different type of server, select [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="3637e-110">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="3637e-110">**Server name**</span></span>  
 <span data-ttu-id="3637e-111">연결할 서버 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3637e-111">Select the server instance to connect to.</span></span> <span data-ttu-id="3637e-112">마지막으로 연결한 서버 인스턴스가 기본적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3637e-112">The server instance last connected to is displayed by default.</span></span>  
  
 <span data-ttu-id="3637e-113">**인증**</span><span class="sxs-lookup"><span data-stu-id="3637e-113">**Authentication**</span></span>  
 <span data-ttu-id="3637e-114">Analysis Services의 인스턴스에 연결하는 경우 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 인증 모드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3637e-114">The following authentication modes are supported when connecting to an instance of Analysis Services: [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="3637e-115">**Windows 인증 모드(Windows 인증)**</span><span class="sxs-lookup"><span data-stu-id="3637e-115">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 <span data-ttu-id="3637e-116">**Windows 인증** 모드에서는 사용자가 windows 사용자 계정을 통해 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3637e-116">**Windows Authentication** mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="3637e-117">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="3637e-117">**User name**</span></span>  
 <span data-ttu-id="3637e-118">이 릴리스에서는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3637e-118">This option is not available in this release.</span></span> <span data-ttu-id="3637e-119">연결에 사용할 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3637e-119">Enter the user name to connect with.</span></span> <span data-ttu-id="3637e-120">이 옵션은 **Windows 인증**을 사용하여 연결하도록 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3637e-120">This option is only available if you have selected to connect using **Windows Authentication**.</span></span>  
  
 <span data-ttu-id="3637e-121">**암호**</span><span class="sxs-lookup"><span data-stu-id="3637e-121">**Password**</span></span>  
 <span data-ttu-id="3637e-122">이 릴리스에서는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3637e-122">This option is not available in this release.</span></span> <span data-ttu-id="3637e-123">로그인 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3637e-123">Enter the password for the login.</span></span> <span data-ttu-id="3637e-124">이 옵션은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하여 연결하도록 선택한 경우에만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3637e-124">This option is only editable if you have selected to connect using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="3637e-125">**연결**</span><span class="sxs-lookup"><span data-stu-id="3637e-125">**Connect**</span></span>  
 <span data-ttu-id="3637e-126">위에서 선택한 서버에 연결하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3637e-126">Click to connect to the server selected above.</span></span>  
  
 <span data-ttu-id="3637e-127">**Options**</span><span class="sxs-lookup"><span data-stu-id="3637e-127">**Options**</span></span>  
 <span data-ttu-id="3637e-128">서버 등록, 암호 저장 등의 추가 서버 연결 옵션을 표시하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3637e-128">Click to display additional server connection options, such as registering a server and remembering the password.</span></span>  
  
  
