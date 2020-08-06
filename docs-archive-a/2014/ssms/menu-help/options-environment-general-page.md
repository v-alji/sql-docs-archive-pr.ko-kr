---
title: 옵션 (환경-일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.SQLEnvironmentOptions
ms.assetid: c32ccdb8-2cf8-4c78-b474-a3abd3dbbd13
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7712c568b478bd2ba958237ba3204246657b3a72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661477"
---
# <a name="options-environment-general-page"></a><span data-ttu-id="f62fc-102">옵션(환경-일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="f62fc-102">Options (Environment-General Page)</span></span>
  <span data-ttu-id="f62fc-103">**옵션** 대화 상자를 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 시작 동작, 일반 창 관리 옵션 및 기타 일반 설정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-103">Use the **Options** dialog box to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] startup actions, general window management options, and other general settings.</span></span> <span data-ttu-id="f62fc-104">**도구** 메뉴에서 **옵션**을 클릭하고 **환경** 폴더를 확장한 다음 **일반**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-104">On the **Tools** menu, click **Options**, expand the **Environment** folder, and then click **General**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="f62fc-105">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="f62fc-105">UI element list</span></span>  
 <span data-ttu-id="f62fc-106">**시작 시**</span><span class="sxs-lookup"><span data-stu-id="f62fc-106">**At startup**</span></span>  
 <span data-ttu-id="f62fc-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 시작할 때 수행할 동작을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-107">Select the action for [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to perform when it is started.</span></span> <span data-ttu-id="f62fc-108">옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-108">The options are:</span></span>  
  
-   <span data-ttu-id="f62fc-109">**개체 탐색기 열기** 를 선택하면 연결 설정 대화 상자를 표시한 다음 개체 탐색기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-109">**Open Object Explorer** prompts for a connection and then opens Object Explorer.</span></span>  
  
-   <span data-ttu-id="f62fc-110">**새 쿼리 창 열기** 를 선택하면 연결 설정 대화 상자를 표시한 다음 SQL 쿼리 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-110">**Open new query window** prompts for a connection and then opens SQL Query Editor.</span></span>  
  
-   <span data-ttu-id="f62fc-111">**개체 탐색기 및 새 쿼리 열기** 를 선택하면 연결 설정 대화 상자를 표시한 다음 해당 연결을 사용하여 개체 탐색기와 SQL 쿼리 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-111">**Open Object Explorer and new query** prompts for a connection, then opens both Object Explorer and SQL Query Editor with that connection.</span></span>  
  
-   <span data-ttu-id="f62fc-112">**빈 환경 열기** 를 선택하면 SQL 쿼리 편집기 창을 열거나 개체 편집기를 서버에 연결하지 않고 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-112">**Open empty environment** opens [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] without a SQL Query editor window and without connecting Object Explorer to a server.</span></span>  
  
 <span data-ttu-id="f62fc-113">**개체 탐색기에서 시스템 개체 숨기기**</span><span class="sxs-lookup"><span data-stu-id="f62fc-113">**Hide system objects in Object Explorer**</span></span>  
 <span data-ttu-id="f62fc-114">개체 탐색기의 트리 뷰에서 시스템 데이터베이스, 시스템 테이블, 시스템 뷰 및 시스템 저장 프로시저를 제거하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-114">Select this check box to remove the system databases, system tables, system views, and system stored procedures from tree view in Object Explorer.</span></span> <span data-ttu-id="f62fc-115">시스템 함수와 시스템 데이터 형식은 숨겨지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-115">System functions and system data types are not hidden.</span></span> <span data-ttu-id="f62fc-116">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스에만 적용되고 개체 탐색기에 이미 연결되어 있는 서버에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-116">This option only applies to instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and does not affect servers already connected in Object Explorer.</span></span>  
  
## <a name="environment-layout"></a><span data-ttu-id="f62fc-117">환경 레이아웃</span><span class="sxs-lookup"><span data-stu-id="f62fc-117">Environment Layout</span></span>  
 <span data-ttu-id="f62fc-118">탭 문서 및 MDI(다중 문서 인터페이스) 환경 모드 간에 전환하려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 닫은 다음 다시 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-118">You must close and reopen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to change between tabbed document and multiple-document interface (MDI) environment mode.</span></span>  
  
 <span data-ttu-id="f62fc-119">**탭 문서**</span><span class="sxs-lookup"><span data-stu-id="f62fc-119">**Tabbed documents**</span></span>  
 <span data-ttu-id="f62fc-120">편집기에서 탭으로 분류되어 있는 문서 창을 표시하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-120">Select this option to display document windows that are tabbed together within editors.</span></span> <span data-ttu-id="f62fc-121">탭 문서 창은 열려 있는 여러 문서를 구성하거나 여러 문서 간에 전환하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-121">Tabbed document windows are useful for organizing and switching between multiple open documents.</span></span>  
  
 <span data-ttu-id="f62fc-122">**MDI 환경**</span><span class="sxs-lookup"><span data-stu-id="f62fc-122">**MDI environment**</span></span>  
 <span data-ttu-id="f62fc-123">MDI 환경에서 문서를 열려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-123">Select this option to open documents in a MDI environment.</span></span> <span data-ttu-id="f62fc-124">MDI 문서 창을 사용하면 탭 문서 환경에서 탭이 차지하는 화면 공간을 확보할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-124">MDI document windows are useful for gaining the screen space that is otherwise taken up by the tabs in the tabbed documents environment.</span></span> <span data-ttu-id="f62fc-125">MDI 모드로 작업하는 경우 Ctrl+Tab을 눌러 문서 간에 전환하거나 **창** 메뉴에 있는 바둑판식 배열 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-125">When working in MDI mode, you can switch between documents by pressing CTRL+TAB, or you can use the tile options located on the **Window** menu.</span></span>  
  
## <a name="docked-tool-window-behavior"></a><span data-ttu-id="f62fc-126">도킹된 도구 창 동작</span><span class="sxs-lookup"><span data-stu-id="f62fc-126">Docked Tool Window Behavior</span></span>  
 <span data-ttu-id="f62fc-127">**[닫기] 단추를 누르면 활성 탭만 닫힘**</span><span class="sxs-lookup"><span data-stu-id="f62fc-127">**Close button affects active tab only**</span></span>  
 <span data-ttu-id="f62fc-128">이 확인란을 선택하면 도킹된 집합의 모든 도구 창을 닫는 것이 아니라 현재 포커스가 있는 도구 창만 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-128">Specifies that when this check box is selected, only the tool window that has focus currently is closed and not all of the tool windows in the docked set.</span></span> <span data-ttu-id="f62fc-129">이 확인란은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-129">By default, this check box is selected.</span></span>  
  
 <span data-ttu-id="f62fc-130">**[자동 숨기기] 단추를 누르면 활성 탭만 숨김**</span><span class="sxs-lookup"><span data-stu-id="f62fc-130">**Auto Hide button affects active tab only**</span></span>  
 <span data-ttu-id="f62fc-131">이 확인란을 선택하면 도킹된 집합의 모든 도구 창을 숨기는 것이 아니라 현재 포커스가 있는 도구 창만 자동으로 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-131">Specifies that when this check box is selected, only the tool window that has focus currently is hidden automatically, not all of the tool windows in the docked set.</span></span> <span data-ttu-id="f62fc-132">이 확인란은 기본적으로 선택되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-132">By default, this check box is cleared.</span></span>  
  
## <a name="display"></a><span data-ttu-id="f62fc-133">표시</span><span class="sxs-lookup"><span data-stu-id="f62fc-133">Display</span></span>  
 <span data-ttu-id="f62fc-134">**최근 사용 목록에 n개 파일 표시**</span><span class="sxs-lookup"><span data-stu-id="f62fc-134">**Display n files in recently used list**</span></span>  
 <span data-ttu-id="f62fc-135">**파일** 메뉴에 표시할 최근 프로젝트 및 최근 파일 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-135">Customizes the number of recent projects and recent files that appear on the **File** menu.</span></span> <span data-ttu-id="f62fc-136">1과 24 사이의 숫자를 입력하며</span><span class="sxs-lookup"><span data-stu-id="f62fc-136">Type a number between 1 and 24.</span></span> <span data-ttu-id="f62fc-137">기본값은 4입니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-137">The default is 4.</span></span> <span data-ttu-id="f62fc-138">이 옵션을 사용하면 최근에 사용한 스크립트 프로젝트 및 파일은 물론 다른 스크립트 프로젝트도 쉽게 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f62fc-138">This is an easy way to retrieve recently used script projects and files and script projects.</span></span>  
  
  
