---
title: 프로젝트에 기존 항목 추가 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 084b3879-e96b-45a7-b421-6a4b0db2b92b
author: stevestein
ms.author: sstein
ms.openlocfilehash: cffa683bfa2a2c81c059d887231531f03d5c892b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660796"
---
# <a name="add-existing-items-to-a-project"></a><span data-ttu-id="98eb3-102">프로젝트에 기존 항목 추가</span><span class="sxs-lookup"><span data-stu-id="98eb3-102">Add Existing Items to a Project</span></span>
  <span data-ttu-id="98eb3-103">프로젝트에 새 항목을 추가하여 애플리케이션 기능을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-103">Add new items to a project to extend application functionality.</span></span> <span data-ttu-id="98eb3-104">기존 항목은 쿼리나 기타 파일이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-104">An existing item can be a query or a miscellaneous file.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="98eb3-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 스크립트 프로젝트 및 Analysis Services 스크립트 프로젝트의 두 가지 프로젝트 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-105">has two project types: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Script Project, and Analysis Services Script Project.</span></span> <span data-ttu-id="98eb3-106">프로젝트 형식에 따라 프로젝트에 추가할 수 있는 쿼리 파일이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-106">The project type determines the query files that you can add to the project.</span></span> <span data-ttu-id="98eb3-107">예를 들어 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 프로젝트에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 쿼리(확장명이 .sql인 파일)를 추가할 수 있지만 Analysis Services 스크립트 프로젝트에는 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-107">For example, you can add a [!INCLUDE[tsql](../../includes/tsql-md.md)] query (a file with a .sql extension) to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Script project, but you cannot add it to an Analysis Services Script Project.</span></span> <span data-ttu-id="98eb3-108">추가 파일 확장명을 프로젝트 형식에 연결 하려면 [파일 확장명을 코드 편집기에 연결](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="98eb3-108">To associate additional file extensions to a project type, see [Associate File Extensions to a Code Editor](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md).</span></span>  
  
### <a name="to-add-an-existing-query-or-a-miscellaneous-file-to-a-project"></a><span data-ttu-id="98eb3-109">기존 쿼리나 기타 파일을 프로젝트에 추가하려면</span><span class="sxs-lookup"><span data-stu-id="98eb3-109">To add an existing query or a miscellaneous file to a project</span></span>  
  
1.  <span data-ttu-id="98eb3-110">솔루션 탐색기에서 대상 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-110">In Solution Explorer, select a target project.</span></span>  
  
2.  <span data-ttu-id="98eb3-111">**프로젝트** 메뉴에서 **기존 항목 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-111">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
     <span data-ttu-id="98eb3-112">**Look in**</span><span class="sxs-lookup"><span data-stu-id="98eb3-112">**Look in**</span></span>  
     <span data-ttu-id="98eb3-113">이 목록에서 프로젝트에 추가할 파일 또는 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-113">Locate the files or folders to add to your project from this list.</span></span> <span data-ttu-id="98eb3-114">XML 웹 서비스와 ASP.NET 웹 애플리케이션의 경우에는 파일이 웹 서버에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-114">For XML Web services and ASP.NET Web applications, the files are located on the Web server.</span></span>  
  
     <span data-ttu-id="98eb3-115">**바탕 화면**</span><span class="sxs-lookup"><span data-stu-id="98eb3-115">**Desktop**</span></span>  
     <span data-ttu-id="98eb3-116">바탕 화면에 있는 파일과 폴더를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-116">Displays the files and folders located on the desktop.</span></span>  
  
     <span data-ttu-id="98eb3-117">**내 프로젝트**</span><span class="sxs-lookup"><span data-stu-id="98eb3-117">**My Projects**</span></span>  
     <span data-ttu-id="98eb3-118">기본 **내 프로젝트** 위치에 있는 파일과 폴더를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-118">Displays the files and folders at the default **My Projects** location.</span></span>  
  
     <span data-ttu-id="98eb3-119">**내 컴퓨터**</span><span class="sxs-lookup"><span data-stu-id="98eb3-119">**My Computer**</span></span>  
     <span data-ttu-id="98eb3-120">**내 컴퓨터** 폴더의 내용을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-120">Displays the contents of your **My Computer** folder.</span></span>  
  
     <span data-ttu-id="98eb3-121">**파일 이름**</span><span class="sxs-lookup"><span data-stu-id="98eb3-121">**File name**</span></span>  
     <span data-ttu-id="98eb3-122">표시되는 파일과 폴더를 필터링하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-122">Use this option to filter the files and folders that are displayed.</span></span> <span data-ttu-id="98eb3-123">필터링할 파일 이름 전체를 입력하거나 와일드카드 문자로 별표(`*`)를 사용하여 파일 이름 일부를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-123">Enter the full or partial file name on which to filter; use an asterisk (`*`) as a wildcard.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="98eb3-124">**파일 이름** 상자에 URL이나 네트워크 경로를 입력하여 웹 및 네트워크 위치로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-124">Navigate to Web and network locations by entering the URL or network path in the **File name** box.</span></span> <span data-ttu-id="98eb3-125">예를 들어 **http://mywebsite** 를 입력하면 mywebsite 웹 위치에서 사용 가능한 파일이 표시되고 **\\myserver\myshare**의 myserver 위치에서 사용 가능한 파일이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-125">For example, **http://mywebsite** displays the files available at the mywebsite Web location, and **\\\myserver\myshare** displays the files available at the myshare location on myserver.</span></span>  
  
     <span data-ttu-id="98eb3-126">**파일 형식**</span><span class="sxs-lookup"><span data-stu-id="98eb3-126">**Files of type**</span></span>  
     <span data-ttu-id="98eb3-127">파일 확장명을 기준으로 파일을 필터링하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-127">Use this option to filter files based on file extension.</span></span> <span data-ttu-id="98eb3-128">각 제품별로 가장 일반적인 파일 형식에 대한 기본 필터가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-128">Each product lists default filters of the most common file types.</span></span>  
  
     <span data-ttu-id="98eb3-129">**추가**</span><span class="sxs-lookup"><span data-stu-id="98eb3-129">**Add**</span></span>  
     <span data-ttu-id="98eb3-130">이 드롭다운 단추를 사용하여 프로젝트에 항목을 추가하고 기본 편집기에서 이 항목을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-130">Use this drop-down button to add the item to the project and open the item in its default editor.</span></span>  
  
    -   <span data-ttu-id="98eb3-131">**추가**</span><span class="sxs-lookup"><span data-stu-id="98eb3-131">**Add**</span></span>  
  
         <span data-ttu-id="98eb3-132">기존 항목을 디스크의 프로젝트 폴더에 복사하고 솔루션 탐색기에서 선택한 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-132">Copies the existing item to your project folder on disk and adds the item under the selected project in Solution Explorer.</span></span> <span data-ttu-id="98eb3-133">항목에서 변경한 내용은 원래 위치에 있는 항목에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-133">Any changes made to the item are not reflected in the item at the original location.</span></span> <span data-ttu-id="98eb3-134">이 파일 형식에 대한 기본 편집기입니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-134">This is the default editor for the file type.</span></span>  
  
    -   <span data-ttu-id="98eb3-135">**링크로 추가**</span><span class="sxs-lookup"><span data-stu-id="98eb3-135">**Add As Link**</span></span>  
  
         <span data-ttu-id="98eb3-136">선택한 파일을 프로젝트에 추가하고 파일 형식에 대한 기본 편집기로 엽니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-136">Adds the selected file to the project and opens it with the default editor for the file type.</span></span> <span data-ttu-id="98eb3-137">이 옵션은 원래 선택한 파일을 열고 파일을 프로젝트 폴더로 복사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-137">This option opens the originally selected file and does not copy the file to the project folder.</span></span>  
  
3.  <span data-ttu-id="98eb3-138">쿼리 파일을 추가하는 경우 쿼리의 연결을 지정하라는 메시지가 연결 대화 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-138">If you are adding query files, the connection dialog will prompt you to specify a connection for the query.</span></span> <span data-ttu-id="98eb3-139">연결을 쿼리에 연결하지 않으려는 경우 연결 대화 상자에서 **취소** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-139">You can click **Cancel** on the connection dialog if you do not want to associate a connection to the query.</span></span>  
  
4.  <span data-ttu-id="98eb3-140">파일은 프로젝트의 **쿼리** 또는 **기타 파일** 폴더에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="98eb3-140">The file will be added to the **Queries** or **Miscellaneous Files** folder of the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98eb3-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98eb3-141">See Also</span></span>  
 <span data-ttu-id="98eb3-142">[솔루션 탐색기](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="98eb3-142">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="98eb3-143">[프로젝트에 새 항목 추가](add-new-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="98eb3-143">[Add New Items to a Project](add-new-items-to-a-project.md) </span></span>  
 [<span data-ttu-id="98eb3-144">항목이나 프로젝트 제거 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="98eb3-144">Remove or Delete an Item or Project</span></span>](remove-or-delete-an-item-or-project.md)  
  
  
