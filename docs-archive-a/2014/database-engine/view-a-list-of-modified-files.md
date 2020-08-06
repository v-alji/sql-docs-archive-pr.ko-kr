---
title: 수정 된 파일 목록 보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourceControl.CheckinWindow
helpviewer_keywords:
- listing modified files
- modified files list [SQL Server]
- checking in files
ms.assetid: 1b053719-8500-4300-a169-fffca5801dd0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a2899ab9889908089d17b3c929e7bf4b2dfe2185
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653501"
---
# <a name="view-a-list-of-modified-files"></a><span data-ttu-id="5fae5-102">수정된 파일의 목록 보기</span><span class="sxs-lookup"><span data-stu-id="5fae5-102">View a List of Modified Files</span></span>
  <span data-ttu-id="5fae5-103">**보류 중인 체크 인** 창을 사용 하 여 현재 솔루션의 체크 아웃 된 파일 목록을 항상 표시 하 고 한 번의 단추 클릭으로 이러한 파일을 체크 인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fae5-103">You can use the **Pending Checkins** window to display at all times a list of the checked-out files in the current solution, and to check in these files with a single button click.</span></span>  
  
### <a name="to-view-a-list-of-modified-files"></a><span data-ttu-id="5fae5-104">수정된 파일의 목록을 보려면</span><span class="sxs-lookup"><span data-stu-id="5fae5-104">To view a list of modified files</span></span>  
  
1.  <span data-ttu-id="5fae5-105">**보기** 메뉴에서 **보류 중인 체크 인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fae5-105">On the **View** menu, click **Pending Checkins**.</span></span>  
  
2.  <span data-ttu-id="5fae5-106">선택한 파일을 체크 인하려면 **체크**인을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fae5-106">To check in the selected files, click **Check In**.</span></span> <span data-ttu-id="5fae5-107">또는 작업을 마치면 파일을 체크 인할 수 있도록 **보류 중인 체크 인** 창을 환경의 오른쪽에 도킹할 수 있습니다 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5fae5-107">Alternatively, you can dock the **Pending Checkins** window on the right side of the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment so that you can check in the files when you are finished working.</span></span>  
  
     <span data-ttu-id="5fae5-108">**체크인**</span><span class="sxs-lookup"><span data-stu-id="5fae5-108">**Check In**</span></span>  
     <span data-ttu-id="5fae5-109">솔루션을 체크 인합니다.</span><span class="sxs-lookup"><span data-stu-id="5fae5-109">Checks in the solution.</span></span>  
  
     <span data-ttu-id="5fae5-110">**설명**</span><span class="sxs-lookup"><span data-stu-id="5fae5-110">**Comments**</span></span>  
     <span data-ttu-id="5fae5-111">일반 텍스트 설명을 보류 중인 체크 인에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5fae5-111">Associates a plain text comment with the pending check in.</span></span> <span data-ttu-id="5fae5-112">만들어진 설명은 각 버전의 프로젝트와 연결되며 원본 제어 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fae5-112">A comment is created and associated with each version of a project, and stored in the source control database.</span></span>  
  
     <span data-ttu-id="5fae5-113">**Options**</span><span class="sxs-lookup"><span data-stu-id="5fae5-113">**Options**</span></span>  
     <span data-ttu-id="5fae5-114">**체크 인** 단추를 클릭할 때 원본 제어에서 수행 해야 하는 동작을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fae5-114">Specifies the actions that source control should take when you click the **Check In** button.</span></span>  
  
    -   <span data-ttu-id="5fae5-115">**모든 체크 아웃 유지**</span><span class="sxs-lookup"><span data-stu-id="5fae5-115">**Keep All Checked Out**</span></span>  
  
         <span data-ttu-id="5fae5-116">변경 내용이 원본 제어 공급자에 기록되지만 파일의 체크 아웃 상태는 유지하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5fae5-116">Specifies that your changes should be written to the source control provider but that the files should remain checked out.</span></span>  
  
     <span data-ttu-id="5fae5-117">**Sort**</span><span class="sxs-lookup"><span data-stu-id="5fae5-117">**Sort**</span></span>  
     <span data-ttu-id="5fae5-118">항목 목록에 표시되는 열의 정렬 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5fae5-118">Specifies the sort order for the columns displayed in the Items list.</span></span>  
  
     <span data-ttu-id="5fae5-119">**열**</span><span class="sxs-lookup"><span data-stu-id="5fae5-119">**Columns**</span></span>  
     <span data-ttu-id="5fae5-120">창의 항목 목록에 추가할 수 있는 열 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5fae5-120">Displays a list of the columns you can add to the window's Items list.</span></span>  
  
     <span data-ttu-id="5fae5-121">**트리 뷰**</span><span class="sxs-lookup"><span data-stu-id="5fae5-121">**Tree View**</span></span>  
     <span data-ttu-id="5fae5-122">체크 인하고 있는 솔루션이나 프로젝트의 폴더와 파일 계층 구조를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5fae5-122">Displays the folder and file hierarchy for the solution or project you are checking in.</span></span>  
  
     <span data-ttu-id="5fae5-123">**기본 뷰**</span><span class="sxs-lookup"><span data-stu-id="5fae5-123">**Flat View**</span></span>  
     <span data-ttu-id="5fae5-124">체크 인하고 있는 파일을 해당 원본 제어 연결 아래에 기본 목록으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5fae5-124">Displays the files you are checking in as flat lists under their source control connection.</span></span>  
  
     <span data-ttu-id="5fae5-125">**버전 비교**</span><span class="sxs-lookup"><span data-stu-id="5fae5-125">**Compare Versions**</span></span>  
     <span data-ttu-id="5fae5-126">개발 환경 프로젝트에서 선택한 파일을 선택한 다른 파일과 비교 하 고 차이점 (있는 경우)을 보여 주는 Visual SourceSafe **차이점 옵션** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5fae5-126">Opens the Visual SourceSafe **Difference Options** dialog box, which compares a selected file in your development environment project to any other selected file and shows you the differences, if any.</span></span>  
  
     <span data-ttu-id="5fae5-127">**체크 아웃 취소**</span><span class="sxs-lookup"><span data-stu-id="5fae5-127">**Undo checkout**</span></span>  
     <span data-ttu-id="5fae5-128">**보류 중인 체크 인** 창에서 선택한 모든 항목의 체크 아웃을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fae5-128">Reverses the checkout of all items selected in the **Pending Checkins** window.</span></span>  
  
     <span data-ttu-id="5fae5-129">**이름**</span><span class="sxs-lookup"><span data-stu-id="5fae5-129">**Name**</span></span>  
     <span data-ttu-id="5fae5-130">체크 인에 사용할 수 있는 항목 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5fae5-130">Displays a list of the items available for check in.</span></span> <span data-ttu-id="5fae5-131">선택한 항목 옆에는 확인란이 함께 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5fae5-131">Items appear with the check box next to them selected.</span></span> <span data-ttu-id="5fae5-132">특정 항목을 체크 인하지 않으려면 옆에 있는 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="5fae5-132">If you do not want to check in a particular item, clear the check box next to it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fae5-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5fae5-133">See Also</span></span>  
 <span data-ttu-id="5fae5-134">[체크 인 관리](../../2014/database-engine/manage-checkins.md) </span><span class="sxs-lookup"><span data-stu-id="5fae5-134">[Manage Checkins](../../2014/database-engine/manage-checkins.md) </span></span>  
 [<span data-ttu-id="5fae5-135">체크 아웃 관리</span><span class="sxs-lookup"><span data-stu-id="5fae5-135">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
