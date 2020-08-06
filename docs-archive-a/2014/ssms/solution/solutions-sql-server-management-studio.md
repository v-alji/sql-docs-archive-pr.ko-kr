---
title: 솔루션(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- solutions [SQL Server Management Studio]
- SQL Server Management Studio [SQL Server], solutions
- projects [SQL Server Management Studio], about projects
- SQL Server Management Studio [SQL Server], projects
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: d06a8a05-7201-4055-8cf3-21bcb4e82c25
author: stevestein
ms.author: sstein
ms.openlocfilehash: 836d3b3002d72541ad88ae55eac6d951530e0ca2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649303"
---
# <a name="solutions-sql-server-management-studio"></a><span data-ttu-id="84a39-102">솔루션(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="84a39-102">Solutions (SQL Server Management Studio)</span></span>
  <span data-ttu-id="84a39-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 솔루션은 하나 이상의 관련 프로젝트의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="84a39-103">A [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] solution is a collection of one or more related projects.</span></span> <span data-ttu-id="84a39-104">프로젝트는 일반적으로 사용되는 관리 스크립트와 같이 개발자가 관련 파일을 구성하는 데 사용되는 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="84a39-104">Projects are containers that developers use to organize related files, such as sets of commonly used administration scripts.</span></span>  
  
## <a name="solution-overview"></a><span data-ttu-id="84a39-105">솔루션 개요</span><span class="sxs-lookup"><span data-stu-id="84a39-105">Solution Overview</span></span>  
 <span data-ttu-id="84a39-106">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 및 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]를 위한 스크립트 개발 플랫폼으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84a39-106">You can use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] as a script development platform for [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="84a39-107">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 코드 편집기를 사용하여 관계형 및 다차원 데이터베이스에 대한 스크립트 및 쿼리를 개발하고 프로젝트에서 관련 스크립트와 쿼리를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84a39-107">Use the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] code editors to develop scripts and queries for relational and multidimensional databases, and collect related scripts and queries together in projects.</span></span>  
  
 <span data-ttu-id="84a39-108">프로젝트에 포함되는 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="84a39-108">Projects can contain:</span></span>  
  
-   <span data-ttu-id="84a39-109">프로덕션 프로세스를 구현하는 쿼리 및 스크립트</span><span class="sxs-lookup"><span data-stu-id="84a39-109">Queries and scripts that implement production processes.</span></span>  
  
-   <span data-ttu-id="84a39-110">쿼리 및 스크립트에 사용되는 연결 정보와 파일</span><span class="sxs-lookup"><span data-stu-id="84a39-110">Connection information and files used by the queries and scripts.</span></span>  
  
 <span data-ttu-id="84a39-111">솔루션에 하나 이상의 관련 프로젝트를 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84a39-111">One or more related projects can be combined in a solution.</span></span> <span data-ttu-id="84a39-112">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 솔루션 탐색기 창을 사용하여 솔루션 및 프로젝트를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84a39-112">Solutions and projects can be managed by using the Solution Explorer pane in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="84a39-113">개발 변경 내용 추적 및 주기 관리를 위해 솔루션 및 프로젝트를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] VSS(Visual SourceSafe) 데이터베이스 또는 다른 타사 원본 제어 공급자에 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84a39-113">Solutions and projects can be integrated into a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe (VSS) database or other third-party source control providers, for development change tracking and life-cycle management.</span></span>  
  
## <a name="solution-tasks"></a><span data-ttu-id="84a39-114">솔루션 태스크</span><span class="sxs-lookup"><span data-stu-id="84a39-114">Solution Tasks</span></span>  
  
|<span data-ttu-id="84a39-115">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="84a39-115">Task Description</span></span>|<span data-ttu-id="84a39-116">항목</span><span class="sxs-lookup"><span data-stu-id="84a39-116">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="84a39-117">하나 이상의 프로젝트를 포함하는 데 사용할 수 있는 새 솔루션을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84a39-117">Describes how to create a new solution that can then be used to contain one or more projects.</span></span>|[<span data-ttu-id="84a39-118">새 솔루션 만들기</span><span class="sxs-lookup"><span data-stu-id="84a39-118">Create a New Solution</span></span>](create-a-new-solution.md)|  
|<span data-ttu-id="84a39-119">솔루션 탐색기에서 기존 솔루션을 여는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84a39-119">Describes how to open an existing solution in Solution Explorer.</span></span>|[<span data-ttu-id="84a39-120">기존 솔루션 열기</span><span class="sxs-lookup"><span data-stu-id="84a39-120">Open an Existing Solution</span></span>](open-an-existing-solution.md)|  
|<span data-ttu-id="84a39-121">솔루션을 닫는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84a39-121">Describes how to close a solution.</span></span>|[<span data-ttu-id="84a39-122">솔루션 닫기</span><span class="sxs-lookup"><span data-stu-id="84a39-122">Close a Solution</span></span>](close-a-solution.md)|  
|<span data-ttu-id="84a39-123">솔루션을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84a39-123">Describes how to delete a solution.</span></span>|[<span data-ttu-id="84a39-124">솔루션 삭제</span><span class="sxs-lookup"><span data-stu-id="84a39-124">Delete a Solution</span></span>](delete-a-solution.md)|  
|<span data-ttu-id="84a39-125">프로젝트 간에 항목을 복사하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84a39-125">Describes how to copy items between projects.</span></span>|[<span data-ttu-id="84a39-126">솔루션에서 항목 복사</span><span class="sxs-lookup"><span data-stu-id="84a39-126">Copy Items in a Solution</span></span>](copy-items-in-a-solution.md)|  
|<span data-ttu-id="84a39-127">단일 프로젝트 또는 전체 프로젝트에서 항목을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84a39-127">Describes how to delete items in a project, or an entire project.</span></span>|[<span data-ttu-id="84a39-128">항목이나 프로젝트 제거 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="84a39-128">Remove or Delete an Item or Project</span></span>](remove-or-delete-an-item-or-project.md)|  
|<span data-ttu-id="84a39-129">솔루션의 프로젝트 간에 항목을 이동하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84a39-129">Describes how to move items between projects in a solution.</span></span>|[<span data-ttu-id="84a39-130">솔루션에서 항목 이동</span><span class="sxs-lookup"><span data-stu-id="84a39-130">Move Items in a Solution</span></span>](move-items-in-a-solution.md)|  
|<span data-ttu-id="84a39-131">솔루션 또는 솔루션 항목의 이름을 바꾸는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84a39-131">Describes how to rename a solution or the items in the solution.</span></span>|[<span data-ttu-id="84a39-132">솔루션 및 프로젝트 항목의 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="84a39-132">Rename Solutions and Project Items</span></span>](rename-solutions-and-project-items.md)|  
  
## <a name="see-also"></a><span data-ttu-id="84a39-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="84a39-133">See Also</span></span>  
 <span data-ttu-id="84a39-134">[솔루션 탐색기](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="84a39-134">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="84a39-135">[프로젝트 &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="84a39-135">[Projects &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="84a39-136">솔루션 탐색기 원본 제어</span><span class="sxs-lookup"><span data-stu-id="84a39-136">Solution Explorer Source Control</span></span>](../../database-engine/solution-explorer-source-control.md)  
  
  
