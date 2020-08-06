---
title: 솔루션 탐색기 소스 제어 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Visual SourceSafe
- SQL Server Management Studio [SQL Server], source control services
- source-controlled files [SQL Server]
- source controls [SQL Server Management Studio], services
- version control services [SQL Server]
- file source control services [SQL Server]
- VSS [Visual SourceSafe]
ms.assetid: 6373adb8-3d81-4945-a9fc-1d0d5799d29a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 46471ba8149c26f80e78006bc3a8befc2e81b416
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652982"
---
# <a name="solution-explorer-source-control"></a><span data-ttu-id="5bf21-102">솔루션 탐색기 원본 제어</span><span class="sxs-lookup"><span data-stu-id="5bf21-102">Solution Explorer Source Control</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="5bf21-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]솔루션 탐색기 별도의 원본 제어 시스템에 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Solution Explorer can be integrated into a separate source control system.</span></span> <span data-ttu-id="5bf21-104">솔루션 또는 프로젝트가 원본 제어 시스템에 통합된 경우 프로젝트에서 스크립트 및 쿼리에 대한 파일 액세스와 버전을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-104">Once a solution or project is integrated into a source control system, you can control file access and versioning for the scripts and queries in your projects.</span></span>  
  
## <a name="solution-and-project-source-control"></a><span data-ttu-id="5bf21-105">솔루션 및 프로젝트 원본 제어</span><span class="sxs-lookup"><span data-stu-id="5bf21-105">Solution and Project Source Control</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="5bf21-106">소스 제어란 서버 소프트웨어의 중심부에서 파일 버전을 저장 및 추적하고 파일에 대한 액세스를 제어하는 시스템을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-106">Source control refers to a system in which a central piece of server software stores and tracks file versions, and also controls access to files.</span></span> <span data-ttu-id="5bf21-107">일반 원본 제어 시스템에는 원본 제어 공급자 및 둘 이상의 원본 제어 클라이언트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-107">A typical source control system includes a source control provider and two or more source control clients.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]<span data-ttu-id="5bf21-108">를 원본 제어 서비스와 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-108">can be integrated with a source control service.</span></span> <span data-ttu-id="5bf21-109">이는 원본 제어 공급자를 위한 클라이언트로서 이 도구를 사용할 수 있다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-109">This means you can use the tool as a client for your source control provider.</span></span> <span data-ttu-id="5bf21-110">현재 환경에서 이동하지 않은 상태로 개별 및 팀 프로젝트를 쉽게 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-110">Without leaving the environment, you can manage your individual and team projects easily.</span></span> <span data-ttu-id="5bf21-111">원본 제어 공급자는 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]와 함께 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-111">The source control provider is not included with [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
#### <a name="to-select-a-source-control-provider"></a><span data-ttu-id="5bf21-112">원본 제어 공급자를 선택하려면</span><span class="sxs-lookup"><span data-stu-id="5bf21-112">To select a source control provider</span></span>  
  
1.  <span data-ttu-id="5bf21-113">원본 제어 공급자의 클라이언트 부분을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-113">Install the client portion of your source control provider.</span></span>  
  
2.  <span data-ttu-id="5bf21-114">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]의 **도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-114">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], on the **Tools** menu, click **Options**.</span></span>  
  
3.  <span data-ttu-id="5bf21-115">**옵션** 대화 상자에서 **소스 제어**를 확장 한 다음 **플러그 인 선택** 페이지를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-115">In the **Options** dialog box, expand **Source Control**, and then click the **Plug-in Selection** page.</span></span>  
  
4.  <span data-ttu-id="5bf21-116">**현재 소스 제어 플러그** 인 상자에서 소스 제어 플러그 인을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-116">In the **Current source control plug-in** box, select the source control plug-in.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5bf21-117">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="5bf21-117">In This Section</span></span>  
  
|<span data-ttu-id="5bf21-118">항목</span><span class="sxs-lookup"><span data-stu-id="5bf21-118">Topic</span></span>|<span data-ttu-id="5bf21-119">Description</span><span class="sxs-lookup"><span data-stu-id="5bf21-119">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5bf21-120">원본 제어 기본 사항</span><span class="sxs-lookup"><span data-stu-id="5bf21-120">Source Control Basics</span></span>](../../2014/database-engine/source-control-basics.md)|<span data-ttu-id="5bf21-121">기본 원본 제어 용어를 정의하고 원본 제어 서비스를 사용할 경우 프로젝트에 어떤 이점이 있는지에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-121">Defines basic source control terminology, and explains how your project can benefit from using source control services.</span></span>|  
|[<span data-ttu-id="5bf21-122">원본 제어에 솔루션 및 프로젝트 추가</span><span class="sxs-lookup"><span data-stu-id="5bf21-122">Add Solutions and Projects to Source Control</span></span>](../../2014/database-engine/add-solutions-and-projects-to-source-control.md)|<span data-ttu-id="5bf21-123">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 환경을 사용하여 솔루션과 프로젝트를 원본 제어에 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-123">Explains how to use the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment to add solutions and projects to source control.</span></span>|  
|[<span data-ttu-id="5bf21-124">원본 제어에서 솔루션 및 프로젝트 열기</span><span class="sxs-lookup"><span data-stu-id="5bf21-124">Open Solutions and Projects from Source Control</span></span>](../../2014/database-engine/open-solutions-and-projects-from-source-control.md)|<span data-ttu-id="5bf21-125">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 환경을 사용하여 원본 제어 솔루션과 프로젝트를 여는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-125">Explains how to use the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment to open source-controlled solutions and projects.</span></span>|  
|[<span data-ttu-id="5bf21-126">체크 아웃 관리</span><span class="sxs-lookup"><span data-stu-id="5bf21-126">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)|<span data-ttu-id="5bf21-127">솔루션과 파일을 원본 제어에서 체크 아웃하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-127">Explains how to check out solutions and files from source control.</span></span>|  
|[<span data-ttu-id="5bf21-128">체크 인 관리</span><span class="sxs-lookup"><span data-stu-id="5bf21-128">Manage Checkins</span></span>](../../2014/database-engine/manage-checkins.md)|<span data-ttu-id="5bf21-129">솔루션과 파일을 원본 제어로 체크 인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-129">Explains how to check solutions and files into source control.</span></span>|  
|[<span data-ttu-id="5bf21-130">버전 정보 설정 및 검색</span><span class="sxs-lookup"><span data-stu-id="5bf21-130">Set and Retrieve Version Information</span></span>](../../2014/database-engine/set-and-retrieve-version-information.md)|<span data-ttu-id="5bf21-131">프로젝트 또는 항목의 기록을 검색하거나 항목의 로컬 복사본을 검색하거나 두 항목 버전을 비교하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf21-131">Explains how to retrieve the history of a project or item, retrieve a local copy of an item, or compare two item versions.</span></span>|  
|||  
  
## <a name="see-also"></a><span data-ttu-id="5bf21-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5bf21-132">See Also</span></span>  
 <span data-ttu-id="5bf21-133">[솔루션 탐색기](../ssms/solution/solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="5bf21-133">[Solution Explorer](../ssms/solution/solution-explorer.md) </span></span>  
 <span data-ttu-id="5bf21-134">[솔루션 &#40;SQL Server Management Studio&#41;](../ssms/sql-server-management-studio-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="5bf21-134">[Solutions &#40;SQL Server Management Studio&#41;](../ssms/sql-server-management-studio-ssms.md) </span></span>  
 <span data-ttu-id="5bf21-135">[프로젝트 &#40;SQL Server Management Studio&#41;](../ssms/solution/projects-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="5bf21-135">[Projects &#40;SQL Server Management Studio&#41;](../ssms/solution/projects-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="5bf21-136">솔루션 및 프로젝트 관리 파일</span><span class="sxs-lookup"><span data-stu-id="5bf21-136">Files That Manage Solutions and Projects</span></span>](../ssms/solution/files-that-manage-solutions-and-projects.md)  
  
  
