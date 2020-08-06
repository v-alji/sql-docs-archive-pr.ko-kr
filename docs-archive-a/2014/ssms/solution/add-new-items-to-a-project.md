---
title: 프로젝트에 새 항목 추가 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 76af8692-324f-4f5e-b1a0-d72ca8a107e3
author: stevestein
ms.author: sstein
ms.openlocfilehash: c73c58952c7801b3a0e2c86652feb461292cf37c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660795"
---
# <a name="add-new-items-to-a-project"></a><span data-ttu-id="b9af0-102">프로젝트에 새 항목 추가</span><span class="sxs-lookup"><span data-stu-id="b9af0-102">Add New Items to a Project</span></span>
  <span data-ttu-id="b9af0-103">프로젝트에 새 항목을 추가하여 애플리케이션 기능을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-103">Add new items to a project to extend application functionality.</span></span> <span data-ttu-id="b9af0-104">새 항목은 쿼리나 연결이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-104">A new item can be a query or a connection.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="b9af0-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 스크립트 프로젝트 및 Analysis Services 스크립트 프로젝트의 두 가지 프로젝트 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-105">has two project types: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Script Project, and Analysis Services Script Project.</span></span> <span data-ttu-id="b9af0-106">프로젝트 형식에 따라 프로젝트에 추가할 수 있는 항목이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-106">The project type determines the items that you can add to the project.</span></span> <span data-ttu-id="b9af0-107">예를 들어 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 프로젝트에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 쿼리(확장명이 .sql인 파일)를 추가할 수 있지만 Analysis Services 스크립트 프로젝트에는 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-107">For example, you can add a [!INCLUDE[tsql](../../includes/tsql-md.md)] query (a file with a .sql extension) to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Script project, but you cannot add it to an Analysis Services Script Project.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="b9af0-108">프로젝트 내에서 폴더를 만드는 것이 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-108">does not allow you to create folders within projects.</span></span> <span data-ttu-id="b9af0-109">작업을 구성하려면 솔루션 내에서 여러 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-109">To organize your work, create multiple projects within the solution.</span></span>  
  
### <a name="to-add-a-new-query-to-an-existing-project"></a><span data-ttu-id="b9af0-110">기존 프로젝트에 새 쿼리를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="b9af0-110">To add a new query to an existing project</span></span>  
  
1.  <span data-ttu-id="b9af0-111">솔루션 탐색기에서 대상 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-111">In Solution Explorer, select a target project.</span></span>  
  
2.  <span data-ttu-id="b9af0-112">**프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-112">On the **Project** menu, click **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="b9af0-113">**새 항목 추가** 대화 상자에서 왼쪽 창의 범주를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-113">In the **Add New Item** dialog box, select a category in the left pane.</span></span>  
  
4.  <span data-ttu-id="b9af0-114">오른쪽 창에서 쿼리 템플릿을 선택한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-114">Select a query template in the right pane, and then click **Add**.</span></span> <span data-ttu-id="b9af0-115">프로젝트의 **쿼리** 폴더에 새 쿼리가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-115">The new query is added in the **Queries** folder of the project.</span></span>  
  
5.  <span data-ttu-id="b9af0-116">**데이터베이스 엔진에 연결** 대화 상자에서 새 쿼리에 대한 연결을 지정한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-116">In the **Connect to Database Engine** dialog box, specify a connection for the new query, and then click **Connect**.</span></span> <span data-ttu-id="b9af0-117">연결을 새 쿼리에 연결하지 않으려는 경우 연결 대화 상자에서 **취소** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-117">You can click **Cancel** on the connection dialog if you do not want to associate a connection to the new query.</span></span>  
  
6.  <span data-ttu-id="b9af0-118">원할 경우 솔루션 탐색기에서 쿼리의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-118">Rename the query in Solution Explorer if you wish.</span></span>  
  
### <a name="to-add-a-new-connection-to-an-existing-project"></a><span data-ttu-id="b9af0-119">기존 프로젝트에 새 연결을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="b9af0-119">To add a new connection to an existing project</span></span>  
  
1.  <span data-ttu-id="b9af0-120">솔루션 탐색기에서 대상 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-120">In Solution Explorer, select a target project.</span></span>  
  
2.  <span data-ttu-id="b9af0-121">**프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-121">On the **Project** menu, click **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="b9af0-122">왼쪽 창에서 **연결** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-122">Select **Connection** in the left pane.</span></span>  
  
4.  <span data-ttu-id="b9af0-123">오른쪽 창에서 **새 연결** 을 선택한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-123">Select **New Connection** in the right pane, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="b9af0-124">**데이터베이스 엔진에 연결** 대화 상자에서 새 쿼리에 대한 연결을 지정한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-124">In the **Connect to Database Engine** dialog box, specify a connection for the new query, and then click **Connect**.</span></span> <span data-ttu-id="b9af0-125">프로젝트의 **연결** 폴더에 새 연결이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9af0-125">The new connection gets added in the **Connections** folder of the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9af0-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b9af0-126">See Also</span></span>  
 <span data-ttu-id="b9af0-127">[솔루션 탐색기](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="b9af0-127">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="b9af0-128">[파일 확장명을 코드 편집기에 연결](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md) </span><span class="sxs-lookup"><span data-stu-id="b9af0-128">[Associate File Extensions to a Code Editor](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md) </span></span>  
 <span data-ttu-id="b9af0-129">[프로젝트에 기존 항목 추가](add-existing-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="b9af0-129">[Add Existing Items to a Project](add-existing-items-to-a-project.md) </span></span>  
 [<span data-ttu-id="b9af0-130">항목이나 프로젝트 제거 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="b9af0-130">Remove or Delete an Item or Project</span></span>](remove-or-delete-an-item-or-project.md)  
  
  
