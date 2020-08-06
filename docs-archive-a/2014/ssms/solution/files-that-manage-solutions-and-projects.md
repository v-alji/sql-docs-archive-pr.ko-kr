---
title: 솔루션 및 프로젝트 관리 파일 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], files
- .ssmssln files
- .ssmsmobileproj files
- .ssmsasproj files
- .ssmssqlproj files
- .sqlsuo files
- files [SQL Server Management Studio], projects
ms.assetid: e19d2859-0b97-4727-ac27-c4c226d86b2f
author: stevestein
ms.author: sstein
ms.openlocfilehash: c94f1f853263c3969961de91ec95b921f5d78ead
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732248"
---
# <a name="files-that-manage-solutions-and-projects"></a><span data-ttu-id="5bc55-102">솔루션 및 프로젝트 관리 파일</span><span class="sxs-lookup"><span data-stu-id="5bc55-102">Files That Manage Solutions and Projects</span></span>
  <span data-ttu-id="5bc55-103">이 문서에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 고유한 파일 형식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc55-103">This topic describes the file types that are specific to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="5bc55-104">기본적으로 모든 솔루션과 해당 프로젝트는 \My Documents\SQL Server Management Studio Projects에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bc55-104">By default, all solutions and their projects are created in \My Documents\SQL Server Management Studio Projects.</span></span>  
  
## <a name="management-studio-solution-files"></a><span data-ttu-id="5bc55-105">Management Studio 솔루션 파일</span><span class="sxs-lookup"><span data-stu-id="5bc55-105">Management Studio Solution Files</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="5bc55-106">는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio와 다른 파일 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc55-106">uses different file types than [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio.</span></span> <span data-ttu-id="5bc55-107">이는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 솔루션을 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 또는 Visual Studio에서 열 수 없다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc55-107">This means you cannot open a [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] solution in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or in Visual Studio.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="5bc55-108">솔루션 파일의 경우 솔루션 탐색기에서 파일을 관리하기 위한 그래픽 인터페이스를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bc55-108">solution files allow Solution Explorer to display a graphical interface for managing your files.</span></span>  
  
|<span data-ttu-id="5bc55-109">내선 번호</span><span class="sxs-lookup"><span data-stu-id="5bc55-109">Extension</span></span>|<span data-ttu-id="5bc55-110">파일 형식</span><span class="sxs-lookup"><span data-stu-id="5bc55-110">File type</span></span>|<span data-ttu-id="5bc55-111">Description</span><span class="sxs-lookup"><span data-stu-id="5bc55-111">Description</span></span>|<span data-ttu-id="5bc55-112">만든 사람</span><span class="sxs-lookup"><span data-stu-id="5bc55-112">Created by</span></span>|  
|---------------|---------------|-----------------|----------------|  
|<span data-ttu-id="5bc55-113">.ssmssln</span><span class="sxs-lookup"><span data-stu-id="5bc55-113">.ssmssln</span></span>|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="5bc55-114">솔루션 개체</span><span class="sxs-lookup"><span data-stu-id="5bc55-114">Solution Object</span></span>|<span data-ttu-id="5bc55-115">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로젝트, 프로젝트 항목 및 솔루션의 디스크 위치에 대한 참조를 환경에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc55-115">Provides the environment with references to the location on disk of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] projects, project items, and solution</span></span>|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
  
## <a name="management-studio-project-files"></a><span data-ttu-id="5bc55-116">Management Studio 프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="5bc55-116">Management Studio Project Files</span></span>  
 <span data-ttu-id="5bc55-117">솔루션의 개체를 관리하는 솔루션 파일을 솔루션이 포함하는 것과 같은 방식으로 프로젝트는 프로젝트 파일을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc55-117">In the same way that solutions contain solution files that manage objects in a solution, projects contain project files.</span></span> <span data-ttu-id="5bc55-118">프로젝트에 대해 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 가 만드는 프로젝트 파일의 형식은 프로젝트는 만드는 데 사용되는 템플릿에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="5bc55-118">The type of project file that [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] creates for a project depends on the template used to create the project.</span></span> <span data-ttu-id="5bc55-119">다음 표에서는 각 프로젝트에 대해 작성되는 파일 유형을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc55-119">The following table describes the type of file created for each project.</span></span>  
  
|<span data-ttu-id="5bc55-120">내선 번호</span><span class="sxs-lookup"><span data-stu-id="5bc55-120">Extension</span></span>|<span data-ttu-id="5bc55-121">프로젝트 템플릿</span><span class="sxs-lookup"><span data-stu-id="5bc55-121">Project template</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="5bc55-122">.ssmssqlproj</span><span class="sxs-lookup"><span data-stu-id="5bc55-122">.ssmssqlproj</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5bc55-123">스크립트 프로젝트</span><span class="sxs-lookup"><span data-stu-id="5bc55-123">Scripts Project</span></span>|  
|<span data-ttu-id="5bc55-124">.ssmsasproj</span><span class="sxs-lookup"><span data-stu-id="5bc55-124">.ssmsasproj</span></span>|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="5bc55-125">스크립트 프로젝트</span><span class="sxs-lookup"><span data-stu-id="5bc55-125">Scripts Project</span></span>|  
  
## <a name="location-of-solution-level-files"></a><span data-ttu-id="5bc55-126">솔루션 수준 파일의 위치</span><span class="sxs-lookup"><span data-stu-id="5bc55-126">Location of Solution-Level Files</span></span>  
 <span data-ttu-id="5bc55-127">기본적으로 솔루션 수준 파일은 솔루션을 사용하여 만든 첫 번째 프로젝트의 물리적 디렉터리에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bc55-127">By default, solution-level files are created in the physical directory of the first project that is created with the solution.</span></span> <span data-ttu-id="5bc55-128">솔루션을 만들어 솔루션의 디렉터리를 지정하거나 새 프로젝트를 만들 때 디렉터리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bc55-128">You can specify a directory for the solution by creating a solution, or you can specify the directory when you create a new project.</span></span>  
  
 <span data-ttu-id="5bc55-129">솔루션 탐색기에 표시되는 논리적 구조와 비슷한 디렉터리 구조를 갖고 있을 경우 프로젝트 및 솔루션 파일을 더 쉽게 찾고 팀의 다른 개발자와 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bc55-129">If you have a directory structure similar to the logical structure shown in Solution Explorer, project and solution files are easier to locate and share with other developers on a team.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc55-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5bc55-130">See Also</span></span>  
 <span data-ttu-id="5bc55-131">[인코딩을 사용 하 여 파일 관리](manage-files-with-encoding.md) </span><span class="sxs-lookup"><span data-stu-id="5bc55-131">[Manage Files with Encoding](manage-files-with-encoding.md) </span></span>  
 <span data-ttu-id="5bc55-132">[기타 파일](miscellaneous-files.md) </span><span class="sxs-lookup"><span data-stu-id="5bc55-132">[Miscellaneous Files](miscellaneous-files.md) </span></span>  
 <span data-ttu-id="5bc55-133">[솔루션 탐색기](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="5bc55-133">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="5bc55-134">[솔루션 &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="5bc55-134">[Solutions &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="5bc55-135">[프로젝트 &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="5bc55-135">[Projects &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="5bc55-136">솔루션 탐색기 원본 제어</span><span class="sxs-lookup"><span data-stu-id="5bc55-136">Solution Explorer Source Control</span></span>](../../database-engine/solution-explorer-source-control.md)  
  
  
