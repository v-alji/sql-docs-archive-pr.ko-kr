---
title: 새 서버 등록 또는 서버 등록 편집 (일반 탭) (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.general.dts.f1
ms.assetid: b586b736-344b-4e42-83ee-96f66ad433a5
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4968c3f98b8bab5b2e641e6fb1e30a6d682f9b50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660124"
---
# <a name="new-or-edit-server-registration-general-tab-ssis"></a><span data-ttu-id="2a607-102">새 서버 등록 또는 서버 등록 편집(일반 탭)(SSIS)</span><span class="sxs-lookup"><span data-stu-id="2a607-102">New or Edit Server Registration (General Tab) (SSIS)</span></span>
  <span data-ttu-id="2a607-103">이 탭을 사용하여 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]등록 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a607-103">Use this tab to specify options when registering [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2a607-104">이 페이지에 액세스하려면 등록된 서버의 **등록된 서버** 도구 모음에서 **Integration Services** 를 클릭하고 등록된 서버 그룹을 마우스 오른쪽 단추로 클릭한 다음 **새로 만들기**를 가리키고 **서버 등록**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a607-104">To access this page, in Registered Servers, click **Integration Services** on the **Registered Servers** toolbar, right-click any registered servers group, point to **New**, and then click **Server Registration**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2a607-105">옵션</span><span class="sxs-lookup"><span data-stu-id="2a607-105">Options</span></span>  
 <span data-ttu-id="2a607-106">**서버 유형**</span><span class="sxs-lookup"><span data-stu-id="2a607-106">**Server type**</span></span>  
 <span data-ttu-id="2a607-107">등록된 서버에서 서버를 등록하는 경우 **서버 유형** 상자는 읽기 전용이며 등록된 서버에 표시된 서버 유형과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="2a607-107">When a server is registered in Registered Servers, the **Server type** box is read-only, and it matches the type of server displayed in Registered Servers.</span></span> <span data-ttu-id="2a607-108">다른 유형의 서버를 등록하려면 새 서버를 등록하기 전에 **등록된 서버** 도구 모음에서 **데이터베이스 엔진**, **Analysis Server**, **Reporting Services**, **SQL Server Compact** **Edition** 또는 **Integration Services**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a607-108">To register a different type of server, click **Database Engine**, **Analysis Server**, **Reporting Services**, **SQL Server Compact** **Edition**, or **Integration Services** on the **Registered Servers** toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="2a607-109">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="2a607-109">**Server name**</span></span>  
 <span data-ttu-id="2a607-110">연결할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2a607-110">Select the server to which to connect.</span></span> <span data-ttu-id="2a607-111">기본적으로 마지막으로 연결한 서버가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a607-111">The server last connected to is displayed by default.</span></span>  
  
 <span data-ttu-id="2a607-112">**인증**</span><span class="sxs-lookup"><span data-stu-id="2a607-112">**Authentication**</span></span>  
 <span data-ttu-id="2a607-113">Windows 인증 모드를 사용하면 사용자는 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 사용자 계정을 통해 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a607-113">Windows Authentication mode allows a user to connect through a [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows user account.</span></span>  
  
 <span data-ttu-id="2a607-114">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="2a607-114">**User name**</span></span>  
 <span data-ttu-id="2a607-115">이 릴리스에서는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a607-115">This option is not available in this release.</span></span>  
  
 <span data-ttu-id="2a607-116">**암호**</span><span class="sxs-lookup"><span data-stu-id="2a607-116">**Password**</span></span>  
 <span data-ttu-id="2a607-117">이 릴리스에서는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a607-117">This option is not available in this release.</span></span>  
  
 <span data-ttu-id="2a607-118">**암호 기억**</span><span class="sxs-lookup"><span data-stu-id="2a607-118">**Remember password**</span></span>  
 <span data-ttu-id="2a607-119">이 릴리스에서는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a607-119">This option is not available in this release.</span></span>  
  
 <span data-ttu-id="2a607-120">**등록된 서버 이름**</span><span class="sxs-lookup"><span data-stu-id="2a607-120">**Registered server name**</span></span>  
 <span data-ttu-id="2a607-121">**등록된 서버**에 표시할 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2a607-121">The name you want to appear in **Registered Servers**.</span></span> <span data-ttu-id="2a607-122">이 이름은 **서버 이름** 상자와 일치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a607-122">This name does not have to match the **Server name** box.</span></span>  
  
 <span data-ttu-id="2a607-123">**등록된 서버 설명**</span><span class="sxs-lookup"><span data-stu-id="2a607-123">**Registered server description**</span></span>  
 <span data-ttu-id="2a607-124">서버에 대한 선택적 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2a607-124">Enter an optional description of the server.</span></span>  
  
 <span data-ttu-id="2a607-125">**Test**</span><span class="sxs-lookup"><span data-stu-id="2a607-125">**Test**</span></span>  
 <span data-ttu-id="2a607-126">**서버 이름**에서 선택한 서버 연결을 테스트하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a607-126">Click to test the connection to the server selected in **Server name**.</span></span>  
  
 <span data-ttu-id="2a607-127">**저장**</span><span class="sxs-lookup"><span data-stu-id="2a607-127">**Save**</span></span>  
 <span data-ttu-id="2a607-128">등록된 서버 설정을 저장하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a607-128">Click to save the Registered Servers settings.</span></span>  
  
  
