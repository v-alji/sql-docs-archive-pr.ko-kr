---
title: 편집기 및 보기 모드 관리
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Query Editor [SQL Server Management Studio], managing window behavior
- workbench view modes [SQL Server Management Studio]
- full screen mode [SQL Server Management Studio]
- fonts [SQL Server Management Studio]
- word wraps [SQL Server Management Studio]
- virtual space mode [SQL Server Management Studio]
- splitting document views
- displaying line numbers
- view modes [SQL Server Management Studio]
ms.assetid: 25c58a14-9f94-4296-9770-7d84c6bc3969
author: rothja
ms.author: jroth
ms.openlocfilehash: 36788b1fe831a6c15c4aa0668d1759c088fcaa73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659932"
---
# <a name="manage-the-editor-and-view-mode"></a><span data-ttu-id="21153-102">편집기 및 보기 모드 관리</span><span class="sxs-lookup"><span data-stu-id="21153-102">Manage the Editor and View Mode</span></span>
  <span data-ttu-id="21153-103">편집기에서 여러 가지 방법으로 코드 보기를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21153-103">The Editor gives you a number of ways to control the view of your code.</span></span>  
  
## <a name="changing-the-view-mode"></a><span data-ttu-id="21153-104">보기 모드 변경</span><span class="sxs-lookup"><span data-stu-id="21153-104">Changing the View Mode</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="21153-105">에는 **탭 문서**라는 보기 모드가 있는데 이 기능을 사용하면 여러 개의 편집기와 문서를 동시에 열어서 편집기 상단 탭을 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21153-105">features a view mode called **Tabbed Documents**, which allows you to open multiple editors and documents simultaneously and access them through tabs at the top of the Editor.</span></span> <span data-ttu-id="21153-106">또는 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 MDI(다중 문서 인터페이스) 모드로 열 수도 있습니다. 이 모드에서는 탭이 없는 창을 여러 개 열어 바둑판식으로 배열하거나 창 크기를 최소화할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21153-106">You can alternatively open the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] environment in Multiple Document Interface (MDI) mode, which joins windows without the tabs, and allows each window to be tiled, minimized, and so on.</span></span>  
  
#### <a name="to-switch-between-view-modes"></a><span data-ttu-id="21153-107">보기 모드를 전환하려면</span><span class="sxs-lookup"><span data-stu-id="21153-107">To switch between view modes</span></span>  
  
1.  <span data-ttu-id="21153-108">**도구** 메뉴에서 **옵션** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-108">Click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="21153-109">**환경**을 클릭하고</span><span class="sxs-lookup"><span data-stu-id="21153-109">Click **Environment**.</span></span> <span data-ttu-id="21153-110">**일반**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-110">Click **General**.</span></span>  
  
3.  <span data-ttu-id="21153-111">**탭 문서** 또는 **MDI 환경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-111">Click **Tabbed documents** or **MDI environment**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="21153-112">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 다시 시작할 때까지 변경 내용이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21153-112">The changes will not take effect until [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is restarted.</span></span>  
  
## <a name="splitting-the-view"></a><span data-ttu-id="21153-113">보기 분할</span><span class="sxs-lookup"><span data-stu-id="21153-113">Splitting the View</span></span>  
 <span data-ttu-id="21153-114">보다 손쉽게 편집하기 위해 편집기 창을 두 부분으로 분할할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21153-114">An Editor window can be split into two separate parts for easier editing.</span></span>  
  
#### <a name="to-split-a-window"></a><span data-ttu-id="21153-115">창을 분할하려면</span><span class="sxs-lookup"><span data-stu-id="21153-115">To split a window</span></span>  
  
1.  <span data-ttu-id="21153-116">스크롤 막대 위에 있는 분할 막대를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-116">Click the splitter bar (located above the scroll bar).</span></span>  
  
2.  <span data-ttu-id="21153-117">분할 막대를 아래로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="21153-117">Drag the splitter bar downward.</span></span>  
  
3.  <span data-ttu-id="21153-118">단일 창으로 돌아가려면 두 창을 분할하는 분할 막대를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-118">To go back to a single pane, double-click the splitter bar dividing the two panes.</span></span>  
  
 <span data-ttu-id="21153-119">새 창에는 동일한 문서가 포함되어 있습니다. 두 창에 동일한 문서 위치를 표시하고 한 창에서 내용을 변경하면 해당 내용이 다른 창에도 반영됩니다.</span><span class="sxs-lookup"><span data-stu-id="21153-119">The new pane contains the same document, and any changes made to one pane are reflected in the other pane as long as that pane displays the same place in the document.</span></span>  
  
## <a name="word-wrap"></a><span data-ttu-id="21153-120">자동 줄 바꿈</span><span class="sxs-lookup"><span data-stu-id="21153-120">Word Wrap</span></span>  
 <span data-ttu-id="21153-121">자동 줄 바꿈을 활성화하면 가로 스크롤 막대가 제거되고 편집기 창 너비를 초과하는 코드 줄은 창 밖으로 스크롤되지 않고 다음 줄로 자동 줄 바꿈되어 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="21153-121">When you activate Word Wrap, the horizontal scrollbar is removed and lines of code that exceed the width of the Editor's window size automatically wraps to the next displayed line rather than scrolling off the side of the window.</span></span>  
  
#### <a name="to-activate-word-wrap"></a><span data-ttu-id="21153-122">자동 줄 바꿈을 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="21153-122">To activate word wrap</span></span>  
  
1.  <span data-ttu-id="21153-123">**도구** 메뉴에서 **옵션** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-123">Click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="21153-124">**텍스트 편집기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-124">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="21153-125">해당 언어 폴더(모든 언어에 적용하려면 **모든 언어** )를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="21153-125">Open the appropriate language folder (or **All Languages** to affect all languages).</span></span>  
  
4.  <span data-ttu-id="21153-126">**자동 줄 바꿈**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-126">Select **Word wrap**.</span></span>  
  
## <a name="enabling-virtual-space-mode"></a><span data-ttu-id="21153-127">가상 공간 모드 설정</span><span class="sxs-lookup"><span data-stu-id="21153-127">Enabling Virtual Space Mode</span></span>  
 <span data-ttu-id="21153-128">**가상 공간** 모드로 편집기를 열면 각 줄의 끝을 넘어서는 공간은 무한한 공간처럼 보이기 때문에 표시되는 화면 영역 밖으로 코드 줄이 계속 이어집니다.</span><span class="sxs-lookup"><span data-stu-id="21153-128">In **Virtual Space** mode, the Editor acts as if the space past the end of each line is filled with an infinite number of spaces, allowing code lines to continue off the side of the visible screen area.</span></span>  
  
#### <a name="to-enable-virtual-space-mode"></a><span data-ttu-id="21153-129">가상 공간 모드를 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="21153-129">To enable Virtual Space mode</span></span>  
  
1.  <span data-ttu-id="21153-130">**도구** 메뉴에서 **옵션** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-130">Click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="21153-131">**텍스트 편집기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-131">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="21153-132">해당 언어 폴더(모든 언어에 적용하려면 **모든 언어** )를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="21153-132">Open the appropriate language folder (or **All Languages** to affect all languages).</span></span>  
  
4.  <span data-ttu-id="21153-133">**가상 공간 활성화**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-133">Select **Enable virtual space**.</span></span>  
  
 <span data-ttu-id="21153-134">가상 공간 모드를 활성화하지 않은 경우 커서는 한 줄의 끝에서 다음 줄의 첫 번째 문자로 또는 그 반대로 줄 바꿈됩니다.</span><span class="sxs-lookup"><span data-stu-id="21153-134">When Virtual Space mode is not enabled, the cursor wraps from the end of one line to the first character of the next line and vice-versa.</span></span>  
  
## <a name="displaying-line-numbers"></a><span data-ttu-id="21153-135">줄 번호 표시</span><span class="sxs-lookup"><span data-stu-id="21153-135">Displaying Line Numbers</span></span>  
 <span data-ttu-id="21153-136">코드에 줄 번호 매기기를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21153-136">You can turn on line numbering in your code.</span></span> <span data-ttu-id="21153-137">줄 번호는 코드를 이동할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-137">Line numbers are useful for navigating code.</span></span> <span data-ttu-id="21153-138">자세한 내용은 [코드 및 텍스트 이동](navigate-code-and-text.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21153-138">For more information, see [Navigate Code and Text](navigate-code-and-text.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="21153-139">줄 번호 매기기를 설정하더라도 문서에 자동으로 줄 번호가 표시되어 출력되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21153-139">Turning on line numbering does not mean that the document will print with line numbers.</span></span> <span data-ttu-id="21153-140">줄 번호를 출력하려면 **파일** 메뉴의 **페이지 설정** 명령에서 **줄 번호** 확인란을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-140">For line numbers to print, you must select the **Line numbers** check box in the **Page Setup** command on the **File** menu.</span></span>  
  
#### <a name="to-display-line-numbers-in-code"></a><span data-ttu-id="21153-141">코드에 줄 번호를 표시하려면</span><span class="sxs-lookup"><span data-stu-id="21153-141">To display line numbers in code</span></span>  
  
1.  <span data-ttu-id="21153-142">**도구** 메뉴에서 **옵션** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-142">Click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="21153-143">**텍스트 편집기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-143">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="21153-144">**모든 언어**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-144">Click **All Languages**.</span></span>  
  
4.  <span data-ttu-id="21153-145">**일반**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-145">Click **General**.</span></span>  
  
5.  <span data-ttu-id="21153-146">**줄 번호**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-146">Select **Line numbers**.</span></span>  
  
 <span data-ttu-id="21153-147">일부 프로그래밍 언어에만 줄 번호 매기기를 지정하려면 해당 폴더에서 **줄 번호** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-147">To specify line numbering for only some programming languages, select **Line Numbers** in the appropriate folder.</span></span>  
  
## <a name="enabling-full-screen-mode"></a><span data-ttu-id="21153-148">전체 화면 모드 설정</span><span class="sxs-lookup"><span data-stu-id="21153-148">Enabling Full Screen Mode</span></span>  
 <span data-ttu-id="21153-149">전체 화면 모드를 설정하면 모든 도구 창을 숨기고 문서 창만 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21153-149">You can choose to hide all tool windows and view only document windows by enabling Full Screen mode.</span></span>  
  
#### <a name="to-enable-full-screen-mode"></a><span data-ttu-id="21153-150">전체 화면 모드를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="21153-150">To enable Full Screen mode</span></span>  
  
1.  <span data-ttu-id="21153-151">Alt+Shift+Enter를 눌러 전체 화면 모드를 설정/해제합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-151">Press ALT+SHIFT+ENTER to toggle Full Screen mode.</span></span>  
  
## <a name="using-auto-hide-all"></a><span data-ttu-id="21153-152">모두 자동 숨기기 사용</span><span class="sxs-lookup"><span data-stu-id="21153-152">Using Auto Hide All</span></span>  
  
#### <a name="to-hide-all-the-tool-windows-at-once"></a><span data-ttu-id="21153-153">모든 도구 창을 한 번에 숨기려면</span><span class="sxs-lookup"><span data-stu-id="21153-153">To hide all the tool windows at once</span></span>  
  
1.  <span data-ttu-id="21153-154">**창** 메뉴에서 **모두 자동 숨기기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21153-154">Select **Auto Hide All** on the **Window** menu.</span></span>  
  
  
