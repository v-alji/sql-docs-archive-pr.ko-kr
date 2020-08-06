---
title: 파일 체크 인 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourceControl.CheckInDialog
helpviewer_keywords:
- checking in files
ms.assetid: 0657a387-8411-4406-bef9-d262a5bfa269
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 070c1dfa5dd057cf777980f7022752a97a4dc84c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652362"
---
# <a name="check-in-files"></a><span data-ttu-id="04b5f-102">파일 체크 인</span><span class="sxs-lookup"><span data-stu-id="04b5f-102">Check In Files</span></span>
  <span data-ttu-id="04b5f-103">수정한 원본 제어 파일을 다른 사용자가 사용할 수 있게 만들려면 파일을 원본 제어로 체크 인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-103">To make source-controlled files that you have modified available to other users, you must check the files into source control.</span></span> <span data-ttu-id="04b5f-104">파일을 체크 인하면 체크 인한 버전이 원본 제어 공급자에 기록되며 파일의 최신 버전이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-104">When you check in a file, the version you check in is written to the source control provider and becomes the latest version of the file.</span></span>  
  
 <span data-ttu-id="04b5f-105">**체크 인** 명령을 사용하여 파일을 체크 인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-105">You can use the **Check In** command to check in files.</span></span> <span data-ttu-id="04b5f-106">이 명령을 사용하여 솔루션이나 프로젝트를 체크 인하면 솔루션이나 프로젝트의 모든 파일도 체크 인됩니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-106">If you use this command to check in a solution or project, all the files in the solution or project are also checked in.</span></span> <span data-ttu-id="04b5f-107">그러나 개별 원본 코드 파일을 체크 인할 경우 해당 파일이 속하는 프로젝트나 솔루션이 체크 인되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-107">However, checking in an individual source code file does not result in the check-in of the project or solution to which it belongs.</span></span>  
  
### <a name="to-check-in-a-file"></a><span data-ttu-id="04b5f-108">파일을 체크 인하려면</span><span class="sxs-lookup"><span data-stu-id="04b5f-108">To check in a file</span></span>  
  
1.  <span data-ttu-id="04b5f-109">솔루션 탐색기에서 체크 인할 파일을 마우스 오른쪽 단추로 클릭한 다음 **체크 인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-109">In Solution Explorer, right-click the file to check in, and then click **Check In**.</span></span>  
  
2.  <span data-ttu-id="04b5f-110">**체크 인** 대화 상자가 나타나면 적절한 옵션을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-110">If the **Check In** dialog box appears, select the appropriate options, and then click **OK**.</span></span>  
  
     <span data-ttu-id="04b5f-111">**체크인**</span><span class="sxs-lookup"><span data-stu-id="04b5f-111">**Check In**</span></span>  
     <span data-ttu-id="04b5f-112">선택한 항목을 모두 체크 인합니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-112">Check in all the selected items.</span></span>  
  
     <span data-ttu-id="04b5f-113">**열**</span><span class="sxs-lookup"><span data-stu-id="04b5f-113">**Columns**</span></span>  
     <span data-ttu-id="04b5f-114">표시할 열 및 열이 표시되는 순서를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-114">Identify the columns to display and the order in which they are displayed.</span></span>  
  
     <span data-ttu-id="04b5f-115">**설명**</span><span class="sxs-lookup"><span data-stu-id="04b5f-115">**Comments**</span></span>  
     <span data-ttu-id="04b5f-116">체크 인 작업과 관련한 주석을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-116">Add a comment to associate with the check-in operation.</span></span>  
  
     <span data-ttu-id="04b5f-117">**체크 인할 때 체크 인 대화 상자 표시 안 함**</span><span class="sxs-lookup"><span data-stu-id="04b5f-117">**Don't show Check in dialog box when checking in items**</span></span>  
     <span data-ttu-id="04b5f-118">체크 인 작업을 수행하는 동안 대화 상자를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-118">Suppress the dialog box during check-in operations.</span></span>  
  
     <span data-ttu-id="04b5f-119">**기본 뷰**</span><span class="sxs-lookup"><span data-stu-id="04b5f-119">**Flat View**</span></span>  
     <span data-ttu-id="04b5f-120">체크 인하는 파일을 해당 파일의 원본 제어 연결 아래에 기본 목록으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-120">Display the files you are checking in as flat lists under their source control connection.</span></span>  
  
     <span data-ttu-id="04b5f-121">**이름**</span><span class="sxs-lookup"><span data-stu-id="04b5f-121">**Name**</span></span>  
     <span data-ttu-id="04b5f-122">체크 인할 항목의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-122">Displays the names of the items to check in.</span></span> <span data-ttu-id="04b5f-123">항목은 옆에 있는 확인란이 선택된 상태로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-123">Items appear with the check boxes next to them selected.</span></span> <span data-ttu-id="04b5f-124">특정 항목을 체크 인하지 않으려면 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-124">If you do not want to check in a particular item, clear its check box.</span></span>  
  
     <span data-ttu-id="04b5f-125">**Options**</span><span class="sxs-lookup"><span data-stu-id="04b5f-125">**Options**</span></span>  
     <span data-ttu-id="04b5f-126">단추 오른쪽의 화살표를 클릭하면 원본 제어 플러그 인의 체크 인 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-126">Displays source control plug-in-specific check-in options when the arrow to the right of the button is clicked.</span></span>  
  
     <span data-ttu-id="04b5f-127">**Sort**</span><span class="sxs-lookup"><span data-stu-id="04b5f-127">**Sort**</span></span>  
     <span data-ttu-id="04b5f-128">열 표시의 순서를 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-128">Sort the order of the display columns.</span></span>  
  
     <span data-ttu-id="04b5f-129">**트리 뷰**</span><span class="sxs-lookup"><span data-stu-id="04b5f-129">**Tree View**</span></span>  
     <span data-ttu-id="04b5f-130">체크 인하는 항목의 폴더 및 파일 계층 구조를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-130">Display the folder and file hierarchy for the items you are checking in.</span></span>  
  
 <span data-ttu-id="04b5f-131">체크 인한 파일이 공유 체크 아웃의 일부가 아니면 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 환경은 파일을 즉시 체크 인하며</span><span class="sxs-lookup"><span data-stu-id="04b5f-131">If the file you have checked in is not part of a shared checkout, the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment checks in the file immediately.</span></span> <span data-ttu-id="04b5f-132">공유 체크 아웃의 일부이면 해당 버전을 다른 사용자가 만든 버전과 병합하라는 메시지가 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04b5f-132">Otherwise, it may prompt you to merge your version with versions created by other users.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b5f-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="04b5f-133">See Also</span></span>  
 <span data-ttu-id="04b5f-134">[수정 된 파일 목록 보기](../../2014/database-engine/view-a-list-of-modified-files.md) </span><span class="sxs-lookup"><span data-stu-id="04b5f-134">[View a List of Modified Files](../../2014/database-engine/view-a-list-of-modified-files.md) </span></span>  
 [<span data-ttu-id="04b5f-135">체크 인 관리</span><span class="sxs-lookup"><span data-stu-id="04b5f-135">Manage Checkins</span></span>](../../2014/database-engine/manage-checkins.md)  
  
  
