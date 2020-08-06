---
title: SQL Server Management Studio를 사용하여 데이터베이스 프로젝트 빌드 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], database projects
- database projects [SQL Server]
- projects [SQL Server Management Studio], about projects
- projects [SQL Server Management Studio]
ms.assetid: c2e80045-894d-44cf-b65c-e547ed738947
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3ddf3f61e69623716b2987c5c4d849398e822d18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638542"
---
# <a name="build-database-projects-by-using-sql-server-management-studio"></a><span data-ttu-id="a1d57-102">SQL Server Management Studio를 사용하여 데이터베이스 프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="a1d57-102">Build Database Projects by Using SQL Server Management Studio</span></span>
  <span data-ttu-id="a1d57-103">데이터베이스 스크립트 프로젝트는 데이터베이스와 관련되거나 데이터베이스의 일부인 스크립트, 연결 정보 및 템플릿으로 구성된 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-103">A database script project is an organized set of scripts, connection information, and templates that are all associated with a database or one part of a database.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="a1d57-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 스크립트 프로젝트의 컨텍스트 내에서 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 데이터베이스를 관리하고 디자인할 수 있는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provides the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] for administering and designing [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] databases within the context of a script project.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="a1d57-105">사용자의 데이터베이스 개발, 배포 및 유지 관리를 도와 주는 디자이너, 편집기, 지침 및 마법사가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-105">includes designers, editors, guides and wizards to assist users in developing, deploying and maintaining databases.</span></span>  
  
## <a name="sql-server-management-studio"></a><span data-ttu-id="a1d57-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a1d57-106">SQL Server Management Studio</span></span>  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]<span data-ttu-id="a1d57-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 속한 구성 요소를 관리하는 관리 도구 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-107">is a suite of administrative tools for managing the components belonging to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a1d57-108">이 통합 환경에서는 단일 인터페이스로 데이터 백업, 쿼리 편집, 일반 기능 자동화 등의 다양한 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-108">This integrated environment allows users to perform a variety of tasks, such as backing up data, editing queries, and automating common functions within a single interface.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="a1d57-109">다음 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-109">includes the following tools:</span></span>  
  
-   <span data-ttu-id="a1d57-110">스크립트를 작성하고 편집할 수 있는 유용한 스크립트 편집기인 코드 편집기 -</span><span class="sxs-lookup"><span data-stu-id="a1d57-110">Code Editor is a rich script editor for writing and editing scripts.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]<span data-ttu-id="a1d57-111">[!INCLUDE[ssDE](../includes/ssde-md.md)] 스크립트용 [!INCLUDE[tsql](../includes/tsql-md.md)] 쿼리 편집기, DMX 쿼리 편집기, MDX 쿼리 편집기 및 XML/A 쿼리 편집기라는 4가지 버전의 코드 편집기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-111">provides four versions of the Code Editor; the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor for [!INCLUDE[tsql](../includes/tsql-md.md)] scripts, the DMX Query Editor, the MDX Query Editor, and the XML/A Query Editor.</span></span>  
  
-   <span data-ttu-id="a1d57-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에 속한 개체를 찾고 수정하고 스크립팅하거나 실행하는 개체 탐색기</span><span class="sxs-lookup"><span data-stu-id="a1d57-112">Object Explorer for locating, modifying, scripting or running objects belonging to instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="a1d57-113">템플릿을 찾고 스크립팅하는 템플릿 탐색기</span><span class="sxs-lookup"><span data-stu-id="a1d57-113">Template Explorer for locating and scripting templates.</span></span>  
  
-   <span data-ttu-id="a1d57-114">관련 스크립트를 프로젝트의 일부로 구성하고 저장하는 솔루션 탐색기</span><span class="sxs-lookup"><span data-stu-id="a1d57-114">Solution Explorer for organizing and storing related scripts as parts of a project.</span></span>  
  
-   <span data-ttu-id="a1d57-115">선택한 개체의 현재 속성을 표시하는 속성 창</span><span class="sxs-lookup"><span data-stu-id="a1d57-115">Properties Window for displaying the current properties of selected objects.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="a1d57-116">다음을 제공하여 효율적인 작업 프로세스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-116">supports efficient work processes by providing:</span></span>  
  
-   <span data-ttu-id="a1d57-117">연결이 끊긴 액세스 -</span><span class="sxs-lookup"><span data-stu-id="a1d57-117">Disconnected access.</span></span> <span data-ttu-id="a1d57-118">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에 연결하지 않고도 스크립트를 작성하고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-118">You can write and edit scripts without connecting to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="a1d57-119">모든 대화 상자에서 스크립팅 -</span><span class="sxs-lookup"><span data-stu-id="a1d57-119">Scripting from any dialog box.</span></span> <span data-ttu-id="a1d57-120">어떤 대화 상자에서든 스크립트를 작성한 후 읽고 수정하고 저장하거나 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-120">You can create a script from any dialog box so that you can read, modify, store and reuse the scripts after you create them.</span></span>  
  
-   <span data-ttu-id="a1d57-121">비모달 대화 상자 -</span><span class="sxs-lookup"><span data-stu-id="a1d57-121">Nonmodal dialog boxes.</span></span> <span data-ttu-id="a1d57-122">UI 대화 상자에 액세스할 때 대화 상자를 닫지 않고도 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 의 다른 리소스를 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-122">When you access a UI dialog box you can browse other resources in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] without closing the dialog box.</span></span>  
  
## <a name="solutions-and-script-projects"></a><span data-ttu-id="a1d57-123">솔루션 및 스크립트 프로젝트</span><span class="sxs-lookup"><span data-stu-id="a1d57-123">Solutions and Script Projects</span></span>  
 <span data-ttu-id="a1d57-124">솔루션 탐색기는 데이터베이스 솔루션을 저장하고 다시 열기 위한 유틸리티입니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-124">Solution Explorer is a utility to store and reopen database solutions.</span></span> <span data-ttu-id="a1d57-125">솔루션은 관련 스크립트 프로젝트와 파일로 구성되며</span><span class="sxs-lookup"><span data-stu-id="a1d57-125">Solutions organize related script projects and files.</span></span> <span data-ttu-id="a1d57-126">스크립트 프로젝트는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 스크립트 파일, SQL 템플릿, 연결 정보 및 기타 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-126">Script projects store [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] script files, SQL templates, connection information and other miscellaneous files.</span></span> <span data-ttu-id="a1d57-127">스크립트가 스크립트 프로젝트에 저장되어 있을 경우 다음 작업을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-127">When a script is saved in a script project, users are able to:</span></span>  
  
-   <span data-ttu-id="a1d57-128">스크립트 버전 제어를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-128">Maintain version control on scripts.</span></span>  
  
-   <span data-ttu-id="a1d57-129">스크립트와 함께 결과 옵션을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-129">Store results options with a script.</span></span>  
  
-   <span data-ttu-id="a1d57-130">단일 스크립트 프로젝트로 관련 스크립트를 조직화합니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-130">Organize related scripts in a single script project.</span></span>  
  
-   <span data-ttu-id="a1d57-131">스크립트와 함께 연결 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-131">Save connection information with scripts.</span></span>  
  
 <span data-ttu-id="a1d57-132">솔루션 탐색기는 같은 프로젝트에 관련된 스크립트를 작성하고 다시 사용하기 위한 개발자용 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-132">Solution Explorer is a tool for developers who are creating and reusing scripts that are related to the same project.</span></span> <span data-ttu-id="a1d57-133">나중에 유사한 태스크가 필요할 경우 프로젝트에 저장된 스크립트 그룹을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-133">If a similar task is required later, you can use group of scripts that were stored in a project.</span></span> <span data-ttu-id="a1d57-134">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 사용하여 애플리케이션을 만들어 본 경험이 있다면 솔루션 탐색기가 전혀 낯설지 않을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-134">If you have created applications by using [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], you will find Solution Explorer very familiar.</span></span>  
  
 <span data-ttu-id="a1d57-135">솔루션은 하나 이상의 스크립트 프로젝트로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-135">A solution consists of one or more script projects.</span></span> <span data-ttu-id="a1d57-136">프로젝트는 하나 이상의 스크립트 또는 연결로 구성되며</span><span class="sxs-lookup"><span data-stu-id="a1d57-136">A project consists of one or more scripts or connections.</span></span> <span data-ttu-id="a1d57-137">스크립트가 아닌 파일도 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1d57-137">A project may also include nonscript files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1d57-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1d57-138">See Also</span></span>  
 <span data-ttu-id="a1d57-139">[SQL Server Management Studio 사용](../database-engine/use-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="a1d57-139">[Use SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="a1d57-140">[쿼리 및 텍스트 편집기 &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="a1d57-140">[Query and Text Editors &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="a1d57-141">솔루션&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a1d57-141">Solutions &#40;SQL Server Management Studio&#41;</span></span>](solution/solutions-sql-server-management-studio.md)  
  
  
