---
title: 파일 체크 아웃 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- Visual Studio.SourceControl.CheckOutDialog
helpviewer_keywords:
- checking out files
ms.assetid: cc033727-51bb-4b58-a12b-8977ce61ff56
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 151f554742bd6c381b27b58155d3f0e40e9eeb0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652361"
---
# <a name="check-out-files"></a><span data-ttu-id="cd2ec-102">파일 체크 아웃</span><span class="sxs-lookup"><span data-stu-id="cd2ec-102">Check Out Files</span></span>
  <span data-ttu-id="cd2ec-103">체크 인한 파일을 편집하는 것을 허용하도록 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 환경을 구성하지 않은 경우 파일을 수정할 수 있으려면 체크 아웃해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-103">Unless you have configured the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment to permit checked-in files to be edited, you must check out a file before you can modify it.</span></span> <span data-ttu-id="cd2ec-104">파일을 체크 아웃하면 파일 버전의 복사본이 로컬 디스크에 복사되며 파일의 읽기 전용 특성이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-104">When you check out a file, a copy of the file version is copied to your local disk, and the read-only attribute of the file is removed.</span></span>  
  
 <span data-ttu-id="cd2ec-105">파일을 배타적으로 또는 공유 모드로 체크 아웃할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-105">You can check files out either exclusively or in shared mode.</span></span> <span data-ttu-id="cd2ec-106">파일이 배타적으로 체크 아웃되면 체크 아웃한 사용자가 체크 인할 때까지 다른 사용자가 파일을 체크 아웃할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-106">When you check out a file exclusively, no other user can check out the file until you check it in.</span></span> <span data-ttu-id="cd2ec-107">파일이 공유 모드로 체크 아웃되면 다른 사용자가 파일을 체크 아웃 및 수정할 수 있으며 파일을 체크 인할 경우에는 자신이 체크 아웃한 버전과 다른 사용자가 만든 버전을 병합해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-107">When you check out a file in shared mode, other users can check out and modify the file, and when you check it in, you may need to merge the version you have checked out with the versions created by other users.</span></span>  
  
 <span data-ttu-id="cd2ec-108">**체크 아웃** 명령을 사용하여 원본 제어 프로젝트와 파일을 체크 아웃할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-108">Use the **Check Out** command to check out source-controlled projects and files.</span></span> <span data-ttu-id="cd2ec-109">이 명령을 사용 하 여 솔루션이 나 프로젝트를 체크 아웃 하면 솔루션이 나 프로젝트의 모든 파일도 체크 아웃 됩니다. 그러나 개별 원본 코드 파일을 체크 아웃 하면 해당 파일에 속한 프로젝트 또는 솔루션이 체크 아웃 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-109">If you use this command to check out a solution or project, all the files in the solution or project are also checked out. However, checking out an individual source code file does not result in the check out of the project or solution to which it belongs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd2ec-110">프로젝트에 대한 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe 데이터베이스가 여러 체크 아웃을 허용하도록 구성된 상태에서 파일을 배타적으로 체크 아웃하려는 경우에는 파일을 체크 아웃하기 전에 **고급 체크 아웃 옵션** 대화 상자에서 **여러 체크 아웃 허용** 옵션을 선택 취소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-110">If the [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe database for your project is configured to allow multiple checkouts, and you want to check out a file exclusively, you must clear the **Allow multiple checkouts** option in the **Advanced Check Out Options** dialog box before checking out the file.</span></span> <span data-ttu-id="cd2ec-111">이 설정을 적용하려면 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-111">You must restart the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] for this setting to take effect.</span></span>  
  
### <a name="to-check-out-a-file"></a><span data-ttu-id="cd2ec-112">파일을 체크 아웃하려면</span><span class="sxs-lookup"><span data-stu-id="cd2ec-112">To check out a file</span></span>  
  
1.  <span data-ttu-id="cd2ec-113">솔루션 탐색기에서 프로젝트나 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-113">In Solution Explorer, select the project or file.</span></span>  
  
2.  <span data-ttu-id="cd2ec-114">**파일** 메뉴에서 **원본 제어**를 가리킨 다음 **편집하기 위해 체크 아웃**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-114">On the **File** menu, point to **Source Control**, and then click **Check Out for Edit**.</span></span>  
  
3.  <span data-ttu-id="cd2ec-115">**편집 하기 위해 체크 아웃** 대화 상자가 표시 되 면 원하는 항목을 선택 하 고 **체크 아웃**을 클릭 합니다. [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] **체크 아웃** 대화 상자를 표시 하지 않도록 환경을 구성한 경우 솔루션 탐색기에서 선택한 항목과 해당 항목이 있을 수 있는 모든 자식 항목이 즉시 체크 아웃 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-115">If the **Check Out for Edit** dialog box is displayed, select the items you want, and click **Check Out**. If you have configured the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment not to display the **Check Out** dialog box, the items selected in Solution Explorer and any children they might have are checked out immediately.</span></span>  
  
     <span data-ttu-id="cd2ec-116">**체크 아웃**</span><span class="sxs-lookup"><span data-stu-id="cd2ec-116">**Check Out**</span></span>  
     <span data-ttu-id="cd2ec-117">선택한 항목을 모두 체크 아웃합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-117">Check out all the selected items.</span></span>  
  
     <span data-ttu-id="cd2ec-118">**열**</span><span class="sxs-lookup"><span data-stu-id="cd2ec-118">**Columns**</span></span>  
     <span data-ttu-id="cd2ec-119">표시할 열 및 열이 표시되는 순서를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-119">Identify the columns to display and the order in which they are displayed.</span></span>  
  
     <span data-ttu-id="cd2ec-120">**설명**</span><span class="sxs-lookup"><span data-stu-id="cd2ec-120">**Comments**</span></span>  
     <span data-ttu-id="cd2ec-121">체크 아웃 작업과 관련한 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-121">Specify a comment to associate with the checkout operation.</span></span>  
  
     <span data-ttu-id="cd2ec-122">**체크 아웃할 때 체크 아웃 대화 상자 표시 안 함**</span><span class="sxs-lookup"><span data-stu-id="cd2ec-122">**Don't Show Check Out dialog box when checking out items**</span></span>  
     <span data-ttu-id="cd2ec-123">체크 아웃 작업을 실행하는 동안 대화 상자를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-123">Suppress the dialog box during checkout operations.</span></span>  
  
     <span data-ttu-id="cd2ec-124">**기본 뷰**</span><span class="sxs-lookup"><span data-stu-id="cd2ec-124">**Flat View**</span></span>  
     <span data-ttu-id="cd2ec-125">체크 아웃하는 항목을 해당 원본 제어 연결 아래에 기본 목록으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-125">Display the items you are checking out as flat lists under their source control connection.</span></span>  
  
     <span data-ttu-id="cd2ec-126">**편집**</span><span class="sxs-lookup"><span data-stu-id="cd2ec-126">**Edit**</span></span>  
     <span data-ttu-id="cd2ec-127">항목을 체크 아웃 하지 않고 수정 합니다. **편집** 단추는 체크 인 된 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 파일의 편집을 지원 하도록를 구성한 경우에만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-127">Modify an item without checking it out. The **Edit** button appears only if you have [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] configured to support the editing of checked-in files.</span></span>  
  
     <span data-ttu-id="cd2ec-128">**이름**</span><span class="sxs-lookup"><span data-stu-id="cd2ec-128">**Name**</span></span>  
     <span data-ttu-id="cd2ec-129">체크 아웃할 수 있는 항목의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-129">Displays the names of the items available for checkout.</span></span> <span data-ttu-id="cd2ec-130">항목은 옆에 있는 확인란이 선택된 상태로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-130">Items that are selected appear with check boxes next to them.</span></span> <span data-ttu-id="cd2ec-131">특정 항목을 체크 아웃하지 않으려면 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-131">If you do not want to check out a particular item, clear its check box.</span></span>  
  
     <span data-ttu-id="cd2ec-132">**Options**</span><span class="sxs-lookup"><span data-stu-id="cd2ec-132">**Options**</span></span>  
     <span data-ttu-id="cd2ec-133">단추 오른쪽의 화살표를 클릭하면 원본 제어 플러그 인의 체크 아웃 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-133">Displays source control plug-in-specific checkout options when the arrow to the right of the button is clicked.</span></span>  
  
     <span data-ttu-id="cd2ec-134">**Sort**</span><span class="sxs-lookup"><span data-stu-id="cd2ec-134">**Sort**</span></span>  
     <span data-ttu-id="cd2ec-135">표시된 열의 순서를 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-135">Sort the order of the displayed columns.</span></span>  
  
     <span data-ttu-id="cd2ec-136">**트리 뷰**</span><span class="sxs-lookup"><span data-stu-id="cd2ec-136">**Tree View**</span></span>  
     <span data-ttu-id="cd2ec-137">체크 아웃하는 항목의 폴더 및 파일 계층 구조를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2ec-137">Display the folder and file hierarchy for the item you are checking out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd2ec-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd2ec-138">See Also</span></span>  
 <span data-ttu-id="cd2ec-139">[체크 인 한 파일 편집](../../2014/database-engine/edit-checked-in-files.md) </span><span class="sxs-lookup"><span data-stu-id="cd2ec-139">[Edit Checked-In Files](../../2014/database-engine/edit-checked-in-files.md) </span></span>  
 <span data-ttu-id="cd2ec-140">[편집 시 자동으로 파일 체크 아웃](../../2014/database-engine/automatically-check-out-files-upon-edit.md) </span><span class="sxs-lookup"><span data-stu-id="cd2ec-140">[Automatically Check Out Files Upon Edit](../../2014/database-engine/automatically-check-out-files-upon-edit.md) </span></span>  
 <span data-ttu-id="cd2ec-141">[체크 아웃 취소](../../2014/database-engine/undo-checkouts.md) </span><span class="sxs-lookup"><span data-stu-id="cd2ec-141">[Undo Checkouts](../../2014/database-engine/undo-checkouts.md) </span></span>  
 [<span data-ttu-id="cd2ec-142">체크 아웃 관리</span><span class="sxs-lookup"><span data-stu-id="cd2ec-142">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
