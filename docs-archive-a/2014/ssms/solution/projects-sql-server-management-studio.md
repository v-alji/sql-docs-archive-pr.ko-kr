---
title: 프로젝트(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c13af859-ca66-4e43-b76a-0650ac6566c0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8fed02e84b154a86788b350812ad8fd5137c14b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660286"
---
# <a name="projects-sql-server-management-studio"></a><span data-ttu-id="dc3ba-102">프로젝트(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="dc3ba-102">Projects (SQL Server Management Studio)</span></span>
  <span data-ttu-id="dc3ba-103">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 프로젝트는 데이터베이스 관리 및 개발을 위해 함께 저장할 수 있는 논리적으로 연관된 스크립트 및 파일 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-103">A [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] project is a collection of logically related scripts and files that can be saved together for database administration and development.</span></span>  
  
## <a name="script-project-overview"></a><span data-ttu-id="dc3ba-104">스크립트 프로젝트 개요</span><span class="sxs-lookup"><span data-stu-id="dc3ba-104">Script Project Overview</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="dc3ba-105">스크립트 프로젝트는 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 솔루션 탐색기 구성 요소에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-105">script projects are displayed in the Solution Explorer component of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="dc3ba-106">스크립트 프로젝트는 없거나 1개 이상의 프로젝트 파일을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-106">A script project can contain zero or more project files.</span></span> <span data-ttu-id="dc3ba-107">프로젝트를 솔루션에 추가하거나 솔루션 내에서 둘 이상의 프로젝트를 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-107">You can add a project to a solution or combine more than one project within a solution.</span></span>  
  
 <span data-ttu-id="dc3ba-108">프로젝트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-108">Projects can include the following:</span></span>  
  
-   <span data-ttu-id="dc3ba-109">**연결**.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-109">**Connections**.</span></span> <span data-ttu-id="dc3ba-110">프로젝트 내에서 유지되는 연결은 로그인 정보, 서버 이름, 기본 데이터베이스, 기본 설정 프로토콜, 인증 유형, 연결 속성 등을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-110">A connection, as persisted within a project, will contain login information, server name, default database, preferred protocol, authentication type, and connection properties.</span></span> <span data-ttu-id="dc3ba-111">연결 정보를 선택적으로 스크립트와 함께 저장할 수 있습니다(아래 참조).</span><span class="sxs-lookup"><span data-stu-id="dc3ba-111">Connection information may optionally be stored with a script (see below).</span></span>  
  
-   <span data-ttu-id="dc3ba-112">**SQLScripts**.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-112">**SQLScripts**.</span></span> <span data-ttu-id="dc3ba-113">사용자를 위한 자주 사용되는 SQL 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-113">Frequently used SQL scripts for the user.</span></span> <span data-ttu-id="dc3ba-114">프로젝트 내의 .sql 파일을 두 번 클릭하면 SQL 편집기에서 선택한 스크립트가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-114">Double-clicking a .sql file within the project will cause the SQL Editor to open the selected script.</span></span>  
  
-   <span data-ttu-id="dc3ba-115">**MDX, DMX 및 XMLAScripts**.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-115">**MDX, DMX, and XMLAScripts**.</span></span> <span data-ttu-id="dc3ba-116">사용자를 위한 자주 사용되는 MDX 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-116">Frequently used MDX scripts for the user.</span></span> <span data-ttu-id="dc3ba-117">프로젝트 내의 .mdx 파일을 두 번 클릭하면 편집기에서 선택한 스크립트가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-117">Double-clicking an .mdx file within the project will cause the Editor to open the selected script.</span></span>  
  
-   <span data-ttu-id="dc3ba-118">**기타**. 다른 기본 노드 유형에 들어맞지 않는 파일(예: 프로젝트 목표를 포함하는 텍스트 파일)에 이 폴더를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-118">**Misc**. This folder can be used for files that do not neatly fit into any of the other default node types, such as a text file that contains the project objectives.</span></span>  
  
 <span data-ttu-id="dc3ba-119">또한 프로젝트를 원본 코드 제어 시스템에 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-119">Projects can also be integrated into a source code control system.</span></span>  
  
## <a name="connecting-to-an-instance-of-sql-server-from-a-script-project"></a><span data-ttu-id="dc3ba-120">스크립트 프로젝트에서 SQL Server의 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="dc3ba-120">Connecting to an Instance of SQL Server from a Script Project</span></span>  
 <span data-ttu-id="dc3ba-121">스크립트 프로젝트는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 대한 연결을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-121">A script project may contain connections to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="dc3ba-122">해당 연결을 클릭하여 프로젝트에 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-122">You can connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a project by clicking the connection.</span></span> <span data-ttu-id="dc3ba-123">이렇게 하면 선택한 연결에 정의된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결된 SQL 스크립트 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-123">This will open an SQL Script window that is connected to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] defined in the connection you selected.</span></span> <span data-ttu-id="dc3ba-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 연결로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 MDX 스크립트를 열 경우 편집기가 열리고 스크립트가 로드된 후에 **SQL Server에 연결** 대화 상자에서 암호를 입력하라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-124">If you open a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or MDX script with a connection that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentication, you will be prompted for the password using the **Connect to SQL Server** dialog box after the Editor has been opened and the script loaded.</span></span>  
  
 <span data-ttu-id="dc3ba-125">해당 창이 닫히면 연결이 끊어집니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-125">The connection will be closed after the corresponding window is closed.</span></span>  
  
 <span data-ttu-id="dc3ba-126">연결에 대한 정보를 수정하려면 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 속성 창을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-126">To modify information about a connection, use the properties window in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
## <a name="project-tasks"></a><span data-ttu-id="dc3ba-127">프로젝트 태스크</span><span class="sxs-lookup"><span data-stu-id="dc3ba-127">Project Tasks</span></span>  
  
|<span data-ttu-id="dc3ba-128">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="dc3ba-128">Task Description</span></span>|<span data-ttu-id="dc3ba-129">항목</span><span class="sxs-lookup"><span data-stu-id="dc3ba-129">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="dc3ba-130">솔루션에서 새 프로젝트를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-130">Describes how to create a new project in a solution.</span></span>|[<span data-ttu-id="dc3ba-131">프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="dc3ba-131">Create a Project</span></span>](create-a-project.md)|  
|<span data-ttu-id="dc3ba-132">솔루션에 기존 프로젝트를 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-132">Describes how to add an existing project to a solution.</span></span>|[<span data-ttu-id="dc3ba-133">솔루션에 기존 프로젝트 추가</span><span class="sxs-lookup"><span data-stu-id="dc3ba-133">Add an Existing Project to a Solution</span></span>](add-an-existing-project-to-a-solution.md)|  
|<span data-ttu-id="dc3ba-134">프로젝트 파일을 저장할 기본 위치를 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-134">Describes how to change the default location at which project files are saved.</span></span>|[<span data-ttu-id="dc3ba-135">프로젝트 기본 위치 변경</span><span class="sxs-lookup"><span data-stu-id="dc3ba-135">Change the Default Location for Projects</span></span>](change-the-default-location-for-projects.md)|  
|<span data-ttu-id="dc3ba-136">프로젝트에 대한 현재 속성을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-136">Describes how to view the current properties for a project.</span></span>|[<span data-ttu-id="dc3ba-137">프로젝트 속성 보기</span><span class="sxs-lookup"><span data-stu-id="dc3ba-137">View Project Properties</span></span>](view-project-properties.md)|  
|<span data-ttu-id="dc3ba-138">프로젝트에 연결, 스크립트 파일 등과 같은 새 항목을 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-138">Describes how to add new items, such as connections or script files, to a project.</span></span>|[<span data-ttu-id="dc3ba-139">프로젝트에 새 항목 추가</span><span class="sxs-lookup"><span data-stu-id="dc3ba-139">Add New Items to a Project</span></span>](add-new-items-to-a-project.md)|  
|<span data-ttu-id="dc3ba-140">쿼리에 대한 연결 정보를 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-140">Describes how to establish the connection information for a query.</span></span>|[<span data-ttu-id="dc3ba-141">쿼리를 프로젝트의 연결 정보로 연결</span><span class="sxs-lookup"><span data-stu-id="dc3ba-141">Associate a Query with a Connection in a Project</span></span>](associate-a-query-with-a-connection-in-a-project.md)|  
|<span data-ttu-id="dc3ba-142">쿼리에 대한 연결 정보를 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-142">Describes how to change the connection information for a query.</span></span>|[<span data-ttu-id="dc3ba-143">쿼리와 연관된 연결 변경</span><span class="sxs-lookup"><span data-stu-id="dc3ba-143">Change the Connection Associated with a Query</span></span>](change-the-connection-associated-with-a-query.md)|  
|<span data-ttu-id="dc3ba-144">연결 속성을 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dc3ba-144">Describes how to change connection properties.</span></span>|[<span data-ttu-id="dc3ba-145">프로젝트의 연결 속성 보기 및 변경</span><span class="sxs-lookup"><span data-stu-id="dc3ba-145">View or Change the Properties of a Connection in a Project</span></span>](view-or-change-the-properties-of-a-connection-in-a-project.md)|  
  
## <a name="see-also"></a><span data-ttu-id="dc3ba-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dc3ba-146">See Also</span></span>  
 <span data-ttu-id="dc3ba-147">[솔루션 탐색기](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="dc3ba-147">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="dc3ba-148">[솔루션 &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="dc3ba-148">[Solutions &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="dc3ba-149">솔루션 탐색기 원본 제어</span><span class="sxs-lookup"><span data-stu-id="dc3ba-149">Solution Explorer Source Control</span></span>](../../database-engine/solution-explorer-source-control.md)  
  
  
