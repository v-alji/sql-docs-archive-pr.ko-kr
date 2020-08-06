---
title: 프로젝트 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], creating
ms.assetid: 7897be19-365b-4b06-bcf0-8a669f67a673
author: stevestein
ms.author: sstein
ms.openlocfilehash: 269feee7225ceb09b1c2ed86419b19ec4001c1f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652518"
---
# <a name="create-a-project"></a><span data-ttu-id="55d43-102">프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="55d43-102">Create a Project</span></span>
  <span data-ttu-id="55d43-103">기존 솔루션 내에 하나 이상의 프로젝트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-103">You can create one or more projects within an existing solution.</span></span>  
  
### <a name="to-create-a-new-project-and-add-it-to-a-solution"></a><span data-ttu-id="55d43-104">새 프로젝트를 만들어 솔루션에 추가하려면</span><span class="sxs-lookup"><span data-stu-id="55d43-104">To create a new project and add it to a solution</span></span>  
  
1.  <span data-ttu-id="55d43-105">솔루션 탐색기에서 솔루션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-105">In Solution Explorer, select the solution.</span></span>  
  
2.  <span data-ttu-id="55d43-106">**파일** 메뉴에서 **추가**를 가리키고 **새 프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-106">On the **File** menu, point to **Add**, and click **New Project**.</span></span>  
  
3.  <span data-ttu-id="55d43-107">**새 프로젝트** 대화 상자에서 프로젝트의 유형을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-107">In the  **New Project** dialog box, click a type of project.</span></span>  
  
     <span data-ttu-id="55d43-108">**템플릿**</span><span class="sxs-lookup"><span data-stu-id="55d43-108">**Templates**</span></span>  
     <span data-ttu-id="55d43-109">**템플릿** 상자에서 템플릿을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-109">In the **Templates** box, select a template.</span></span> <span data-ttu-id="55d43-110">선택한 프로젝트 템플릿에 대한 간략한 설명이 **템플릿** 상자 아래에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-110">A brief description of the selected project template appears beneath the **Templates** box.</span></span>  
  
     <span data-ttu-id="55d43-111">**이름**</span><span class="sxs-lookup"><span data-stu-id="55d43-111">**Name**</span></span>  
     <span data-ttu-id="55d43-112">만들려는 스크립트 프로젝트의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-112">Enter the name of the script project you want to create.</span></span> <span data-ttu-id="55d43-113">**위치** 필드에 표시된 위치에 프로젝트와 동일한 이름을 가진 폴더도 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-113">A folder with the same name as the project is also created in the location displayed in the **Location** field.</span></span> <span data-ttu-id="55d43-114">일부 프로젝트의 경우 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 는 원본 파일과 기타 지원 파일을 만들어 새 프로젝트 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-114">For some projects, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] creates source and other supporting files and adds them to the new project folder.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="55d43-115">일부 프로젝트 유형의 경우 위치를 지정하면 이름이 설정되기 때문에 **이름** 입력란을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-115">For some project types, the **Name** text box is unavailable because specifying the location sets the name.</span></span> <span data-ttu-id="55d43-116">예를 들어 웹 애플리케이션과 웹 서비스는 웹 서버에 있으며 해당 서버에서 지정한 가상 디렉터리로부터 이름이 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-116">For example, Web applications and Web services are located on a Web server and derive their name from the virtual directory specified on that server.</span></span>  
  
     <span data-ttu-id="55d43-117">이름은 다음 문자를 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-117">Names cannot contain the following characters:</span></span>  
  
    -   <span data-ttu-id="55d43-118">파운드(#)</span><span class="sxs-lookup"><span data-stu-id="55d43-118">Pound (#)</span></span>  
  
    -   <span data-ttu-id="55d43-119">백분율(%)</span><span class="sxs-lookup"><span data-stu-id="55d43-119">Percent (%)</span></span>  
  
    -   <span data-ttu-id="55d43-120">앰퍼샌드 (&)</span><span class="sxs-lookup"><span data-stu-id="55d43-120">Ampersand (&)</span></span>  
  
    -   <span data-ttu-id="55d43-121">별표(\*)</span><span class="sxs-lookup"><span data-stu-id="55d43-121">Asterisk (\*)</span></span>  
  
    -   <span data-ttu-id="55d43-122">세로 막대(|)</span><span class="sxs-lookup"><span data-stu-id="55d43-122">Vertical bar (|)</span></span>  
  
    -   <span data-ttu-id="55d43-123">백슬래시(\\)</span><span class="sxs-lookup"><span data-stu-id="55d43-123">Backslash (\\)</span></span>  
  
    -   <span data-ttu-id="55d43-124">콜론(:)</span><span class="sxs-lookup"><span data-stu-id="55d43-124">Colon (:)</span></span>  
  
    -   <span data-ttu-id="55d43-125">따옴표(")</span><span class="sxs-lookup"><span data-stu-id="55d43-125">Quotation mark (")</span></span>  
  
    -   <span data-ttu-id="55d43-126">보다 작음(\<)</span><span class="sxs-lookup"><span data-stu-id="55d43-126">Less than (\<)</span></span>  
  
    -   <span data-ttu-id="55d43-127">보다 큼(>)</span><span class="sxs-lookup"><span data-stu-id="55d43-127">Greater than (>)</span></span>  
  
    -   <span data-ttu-id="55d43-128">물음표(?)</span><span class="sxs-lookup"><span data-stu-id="55d43-128">Question mark (?)</span></span>  
  
    -   <span data-ttu-id="55d43-129">슬래시(/)</span><span class="sxs-lookup"><span data-stu-id="55d43-129">Forward slash (/)</span></span>  
  
    -   <span data-ttu-id="55d43-130">선행 또는 후행 공백(' ')</span><span class="sxs-lookup"><span data-stu-id="55d43-130">Leading or trailing spaces (' ')</span></span>  
  
    -   <span data-ttu-id="55d43-131">Microsoft Windows 또는 MS-DOS에 예약된 이름(예: "nul", "aux", "con", "com1", "lpt1" 등)</span><span class="sxs-lookup"><span data-stu-id="55d43-131">Names reserved for Microsoft Windows or MS-DOS, such as ("nul", "aux", "con", "com1", "lpt1", and so on)</span></span>  
  
     <span data-ttu-id="55d43-132">**위치**</span><span class="sxs-lookup"><span data-stu-id="55d43-132">**Location**</span></span>  
     <span data-ttu-id="55d43-133">프로젝트를 만들 위치를 입력하거나 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-133">Enter the location where you want to create your project, or choose one from the list.</span></span>  
  
     <span data-ttu-id="55d43-134">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="55d43-134">**Browse**</span></span>  
     <span data-ttu-id="55d43-135">프로젝트를 저장할 새 디렉터리로 이동할 수 있는 **프로젝트 위치** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-135">Displays the **Project Location** dialog box, allowing you to navigate to a new directory in which to save the project.</span></span>  
  
     <span data-ttu-id="55d43-136">**해결 방법**</span><span class="sxs-lookup"><span data-stu-id="55d43-136">**Solution**</span></span>  
     <span data-ttu-id="55d43-137">솔루션 탐색기에서 솔루션을 만들려면 **새 솔루션 만들기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-137">Select **Create new Solution** to create a solution in Solution Explorer.</span></span> <span data-ttu-id="55d43-138">현재 솔루션 탐색기에 열려 있는 솔루션에 새 프로젝트를 추가하려면 **솔루션에 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-138">Select **Add to Solution** to add the new project to the solution currently open in Solution Explorer.</span></span>  
  
     <span data-ttu-id="55d43-139">**솔루션용 디렉터리 만들기**</span><span class="sxs-lookup"><span data-stu-id="55d43-139">**Create directory for Solution**</span></span>  
     <span data-ttu-id="55d43-140">**(솔루션) 이름** 입력란을 활성화하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-140">Select to enable the **(Solution) Name** text box.</span></span> <span data-ttu-id="55d43-141">이 옵션은 프로젝트 및 솔루션 이름으로 선택한 것과 같은 이름으로 새 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-141">This option creates a new directory of the name you choose for your project and solution.</span></span>  
  
     <span data-ttu-id="55d43-142">**솔루션 이름**</span><span class="sxs-lookup"><span data-stu-id="55d43-142">**Solution Name**</span></span>  
     <span data-ttu-id="55d43-143">프로젝트를 만들 새 솔루션의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-143">Enter the name of the new solution in which you want your project to be created.</span></span> <span data-ttu-id="55d43-144">기본적으로 이 필드에서는 **이름** 필드에 입력한 것과 동일한 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-144">By default, this field uses the same name as entered in the **Name** field.</span></span>  
  
     <span data-ttu-id="55d43-145">**참고** 이 옵션에 액세스하려면 **솔루션** 에서 **새 솔루션 만들기** 확인란을 선택해야 하며 **솔루션용 디렉터리 만들기** 확인란도 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-145">**Note** To access this option, you must select both the **Create New Solution** in the **Solution** and the **Create directory for Solution** check boxes.</span></span> <span data-ttu-id="55d43-146">웹 애플리케이션 등 일부 프로젝트 템플릿에서는 이 옵션이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-146">Some project templates do not support this option, such as Web applications.</span></span>  
  
     <span data-ttu-id="55d43-147">**소스 제어에 추가**</span><span class="sxs-lookup"><span data-stu-id="55d43-147">**Add to Source Control**</span></span>  
     <span data-ttu-id="55d43-148">이 확인란을 선택한 경우 **확인**을 클릭하면 원본 제어 애플리케이션이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-148">When this check box is selected, your source control application opens when you click **OK**.</span></span> <span data-ttu-id="55d43-149">계속하려면 원본 제어 애플리케이션에 필요한 모든 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-149">Complete any information required by your source control application to continue.</span></span> <span data-ttu-id="55d43-150">이 옵션을 사용하려면 원본 제어 클라이언트 애플리케이션이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-150">You must have a source control client application installed to use this option.</span></span>  
  
4.  <span data-ttu-id="55d43-151">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-151">Click **OK**.</span></span>  
  
 <span data-ttu-id="55d43-152">스크립트 프로젝트의 이름을 설정할 수 있지만 폴더 이름은 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에 의해 설정되며 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-152">You can set a name for the script project, but the folder names are established by [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and cannot be changed.</span></span> <span data-ttu-id="55d43-153">**새 프로젝트 추가** 대화 상자를 사용하여 공통 폴더 집합에 대한 드라이브 및 경로 지정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-153">You can configure the drive and path specification for the common set of folders by using the **Add New Project** dialog box.</span></span> <span data-ttu-id="55d43-154">**솔루션 탐색기**에서 솔루션 아이콘을 마우스 오른쪽 단추로 클릭한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-154">Right-click the solution icon in **Solution Explorer**, and then click **Add**.</span></span> <span data-ttu-id="55d43-155">스크립트 프로젝트 폴더에 대한 기본 위치는 C:\Documents and Settings\\*username*\My Documents\SQL Server Management Studio\Projects\\입니다.</span><span class="sxs-lookup"><span data-stu-id="55d43-155">The default location for script project folders is: C:\Documents and Settings\\*username*\My Documents\SQL Server Management Studio\Projects\\.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55d43-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="55d43-156">See Also</span></span>  
 <span data-ttu-id="55d43-157">[솔루션 탐색기](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="55d43-157">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="55d43-158">[솔루션에 기존 프로젝트 추가](add-an-existing-project-to-a-solution.md) </span><span class="sxs-lookup"><span data-stu-id="55d43-158">[Add an Existing Project to a Solution](add-an-existing-project-to-a-solution.md) </span></span>  
 <span data-ttu-id="55d43-159">[프로젝트에 새 항목 추가](add-new-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="55d43-159">[Add New Items to a Project](add-new-items-to-a-project.md) </span></span>  
 <span data-ttu-id="55d43-160">[프로젝트에 기존 항목 추가](add-existing-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="55d43-160">[Add Existing Items to a Project](add-existing-items-to-a-project.md) </span></span>  
 <span data-ttu-id="55d43-161">[프로젝트의 기본 위치 변경](change-the-default-location-for-projects.md) </span><span class="sxs-lookup"><span data-stu-id="55d43-161">[Change the Default Location for Projects](change-the-default-location-for-projects.md) </span></span>  
 <span data-ttu-id="55d43-162">[항목 또는 프로젝트 제거 또는 삭제](remove-or-delete-an-item-or-project.md) </span><span class="sxs-lookup"><span data-stu-id="55d43-162">[Remove or Delete an Item or Project](remove-or-delete-an-item-or-project.md) </span></span>  
 [<span data-ttu-id="55d43-163">솔루션 삭제</span><span class="sxs-lookup"><span data-stu-id="55d43-163">Delete a Solution</span></span>](delete-a-solution.md)  
  
  
