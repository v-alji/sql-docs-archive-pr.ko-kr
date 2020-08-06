---
title: 솔루션 탐색기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], solutions
- projects [SQL Server Management Studio], about projects
- SQL Server Management Studio [SQL Server], projects
- solutions [SQL Server Management Studio], about solutions
- SQL Server Management Studio [SQL Server], items
- items [SQL Server]
ms.assetid: 0df09843-0d4f-4925-bc6c-99265035a0c1
author: stevestein
ms.author: sstein
ms.openlocfilehash: fa312f5e097fa1c59b9ba545709dc964a184c3f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649305"
---
# <a name="solution-explorer"></a><span data-ttu-id="de30c-102">솔루션 탐색기</span><span class="sxs-lookup"><span data-stu-id="de30c-102">Solution Explorer</span></span>
  <span data-ttu-id="de30c-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 솔루션 탐색기 창은 데이터베이스 스크립트, 쿼리, 데이터 연결 및 파일을 관리하기 위해 프로젝트라는 컨테이너를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="de30c-103">The Solution Explorer pane in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] provides containers called projects for managing items such as database scripts, queries, data connections, and files.</span></span> <span data-ttu-id="de30c-104">서로 관련된 하나 이상의 프로젝트를 솔루션이라는 하나의 컨테이너에 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de30c-104">One or more projects that are related to each other can be combined in a container called a solution.</span></span>  
  
 <span data-ttu-id="de30c-105">솔루션은 하나 이상의 프로젝트와 솔루션을 전체적으로 정의할 수 있는 파일 및 메타데이터로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="de30c-105">A solution includes one or more projects, plus files and metadata that help define the solution as a whole.</span></span> <span data-ttu-id="de30c-106">프로젝트는 파일 집합과 연결 정보 같은 관련 메타데이터로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="de30c-106">A project is a set of files, plus related metadata such as connection information.</span></span> <span data-ttu-id="de30c-107">솔루션과 프로젝트에는 데이터베이스 솔루션을 만드는 데 필요한 스크립트, 쿼리, 연결 정보 및 파일을 나타내는 항목이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de30c-107">Solutions and projects contain items that represent the scripts, queries, connection information and files that you need to create your database solution.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="benefits-of-using-solutions"></a><span data-ttu-id="de30c-108">솔루션 사용의 이점</span><span class="sxs-lookup"><span data-stu-id="de30c-108">Benefits of Using Solutions</span></span>  
 <span data-ttu-id="de30c-109">이러한 컨테이너를 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de30c-109">Use these containers to:</span></span>  
  
-   <span data-ttu-id="de30c-110">쿼리나 스크립트에서 소스 제어를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="de30c-110">Implement source control on queries and scripts.</span></span>  
  
-   <span data-ttu-id="de30c-111">전체로서의 솔루션이나 개별 프로젝트의 설정을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="de30c-111">Manage settings for your solution as a whole or for individual projects.</span></span>  
  
-   <span data-ttu-id="de30c-112">데이터베이스 솔루션을 구성하는 항목에 중점을 두고 파일 관리의 세부 정보를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="de30c-112">Handle the details of file management while you focus on items that make up your database solution.</span></span>  
  
-   <span data-ttu-id="de30c-113">각 프로젝트의 항목을 참조하지 않고 솔루션의 여러 프로젝트나 솔루션 자체에 유용한 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="de30c-113">Add items that are useful to multiple projects in the solution or to the solution without referencing the item in each project.</span></span>  
  
-   <span data-ttu-id="de30c-114">솔루션이나 프로젝트와 독립적인 기타 파일에 대한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="de30c-114">Work on miscellaneous files that are independent from solutions or projects.</span></span>  
  
 <span data-ttu-id="de30c-115">프로젝트에 포함된 항목은 프로젝트 유형과 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하고 있는지 여부에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="de30c-115">The items contained in projects depend on the project type and whether you are using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="de30c-116">관련 작업</span><span class="sxs-lookup"><span data-stu-id="de30c-116">Related Tasks</span></span>  
 <span data-ttu-id="de30c-117">다음 항목을 사용하여 SQL Server 솔루션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="de30c-117">Use the following topics to get started with SQL Server Solutions:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="de30c-118">**설명**</span><span class="sxs-lookup"><span data-stu-id="de30c-118">**Description**</span></span>|<span data-ttu-id="de30c-119">**항목**</span><span class="sxs-lookup"><span data-stu-id="de30c-119">**Topic**</span></span>|  
|<span data-ttu-id="de30c-120">솔루션에서 하나 이상의 프로젝트를 수집하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="de30c-120">Describes how to collect one or more projects in a solution.</span></span>|[<span data-ttu-id="de30c-121">솔루션&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="de30c-121">Solutions &#40;SQL Server Management Studio&#41;</span></span>](solutions-sql-server-management-studio.md)|  
|<span data-ttu-id="de30c-122">프로젝트를 만들고 스크립트 및 연결과 같은 항목을 추가하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="de30c-122">Describes how to create a project and add items like scripts and connections.</span></span>|[<span data-ttu-id="de30c-123">프로젝트&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="de30c-123">Projects &#40;SQL Server Management Studio&#41;</span></span>](projects-sql-server-management-studio.md)|  
|<span data-ttu-id="de30c-124">솔루션 또는 개별 프로젝트를 원본 코드 제어 시스템에 통합하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="de30c-124">Describes how to integrate solutions or individual projects into a source code control system.</span></span>|[<span data-ttu-id="de30c-125">솔루션 탐색기 원본 제어</span><span class="sxs-lookup"><span data-stu-id="de30c-125">Solution Explorer Source Control</span></span>](../../database-engine/solution-explorer-source-control.md)|  
|<span data-ttu-id="de30c-126">솔루션과 파일을 관리하기 위해 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에 사용되는 파일에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="de30c-126">Provides information about the files used by [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to manage solutions and files.</span></span>|[<span data-ttu-id="de30c-127">솔루션 및 프로젝트 관리 파일</span><span class="sxs-lookup"><span data-stu-id="de30c-127">Files That Manage Solutions and Projects</span></span>](files-that-manage-solutions-and-projects.md)|  
  
  
