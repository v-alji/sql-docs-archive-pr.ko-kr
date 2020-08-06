---
title: SQL Server Management Studio 도구 창 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], tool windows
- tool windows [SQL Server Management Studio]
ms.assetid: d3be5062-234c-43a8-8d47-cce111dd3c25
author: stevestein
ms.author: sstein
ms.openlocfilehash: c3cc4c44e00e4c16a6211086b16861f3e9233357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727844"
---
# <a name="tool-windows-in-sql-server-management-studio"></a><span data-ttu-id="197ef-102">SQL Server Management Studio 도구 창</span><span class="sxs-lookup"><span data-stu-id="197ef-102">Tool Windows in SQL Server Management Studio</span></span>
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="197ef-103">모든 단계의 개발 및 관리를 위한 강력한 여러 도구 창을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="197ef-103">provides many powerful tool windows for all phases of development and administration.</span></span> <span data-ttu-id="197ef-104">일부 도구는 모든 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 요소에서 사용할 수 있지만 일부 도구는 특정 구성 요소에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="197ef-104">Some tools can be used on any [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] component, and others are for certain components only.</span></span> <span data-ttu-id="197ef-105">다음 표에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 모든 구성 요소에서 사용할 수 있는 도구를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="197ef-105">The following table identifies the tools that can be used for all components of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="197ef-106">**도구**</span><span class="sxs-lookup"><span data-stu-id="197ef-106">**Tool**</span></span>|<span data-ttu-id="197ef-107">**용도**</span><span class="sxs-lookup"><span data-stu-id="197ef-107">**Purpose**</span></span>|  
|[<span data-ttu-id="197ef-108">개체 탐색기</span><span class="sxs-lookup"><span data-stu-id="197ef-108">Object Explorer</span></span>](object/object-explorer.md)|<span data-ttu-id="197ef-109">서버 탐색, 개체 작성 및 찾기, 데이터 원본 관리, 로그 보기 등을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="197ef-109">Browse servers, create and locate objects, manage data sources, and view logs.</span></span> <span data-ttu-id="197ef-110">이 도구는 **보기** 메뉴에서 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="197ef-110">This tool is accessed from the **View** menu.</span></span>|  
|[<span data-ttu-id="197ef-111">솔루션 탐색기</span><span class="sxs-lookup"><span data-stu-id="197ef-111">Solution Explorer</span></span>](solution/solution-explorer.md)|<span data-ttu-id="197ef-112">스크립트와 관련 연결 정보를 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 스크립트라는 프로젝트에 저장 및 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="197ef-112">Store and organize scripts and related connection information in projects called [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Scripts.</span></span> <span data-ttu-id="197ef-113">여러 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 스크립트를 솔루션으로 저장하고 원본 제어를 사용하여 시간이 지남에 따라 증가하는 스크립트를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="197ef-113">You can store several [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Scripts as Solutions and use source control to manage scripts as they evolve over time.</span></span> <span data-ttu-id="197ef-114">이 도구는 **보기** 메뉴에서 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="197ef-114">This tool is accessed from the **View** menu.</span></span>|  
|[<span data-ttu-id="197ef-115">템플릿 탐색기</span><span class="sxs-lookup"><span data-stu-id="197ef-115">Template Explorer</span></span>](template/template-explorer.md)|<span data-ttu-id="197ef-116">기존 템플릿에 기초하여 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="197ef-116">Create queries based on existing templates.</span></span> <span data-ttu-id="197ef-117">특정 시나리오에 맞게 사용자 지정 쿼리를 만들거나 기존 템플릿을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="197ef-117">You can also create your custom queries or alter the existing templates to fit your scenarios.</span></span> <span data-ttu-id="197ef-118">이 도구는 **보기** 메뉴에서 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="197ef-118">This tool is accessed from the **View** menu.</span></span>|  
|[<span data-ttu-id="197ef-119">동적 도움말</span><span class="sxs-lookup"><span data-stu-id="197ef-119">Dynamic Help</span></span>](sql-server-management-studio-ssms.md)|<span data-ttu-id="197ef-120">구성 요소를 클릭하거나 코드를 입력할 때 연관된 도움말 항목의 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="197ef-120">Show a list of related Help topics as you click on a component or type code.</span></span>|  
  
 <span data-ttu-id="197ef-121">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 의 도구는 함께 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="197ef-121">The tools in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] work together.</span></span> <span data-ttu-id="197ef-122">예를 들어, 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="197ef-122">For example, you can:</span></span>  
  
-   <span data-ttu-id="197ef-123">개체 탐색기로 서버를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="197ef-123">Register a server with Object Explorer.</span></span>  
  
-   <span data-ttu-id="197ef-124">개체 탐색기에서 특정 데이터베이스에 연결된 SQL 편집기 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="197ef-124">Open a SQL Editor window connected to a specific database from Object Explorer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="197ef-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="197ef-125">See Also</span></span>  
 [<span data-ttu-id="197ef-126">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="197ef-126">Use SQL Server Management Studio</span></span>](../database-engine/use-sql-server-management-studio.md)  
  
  
