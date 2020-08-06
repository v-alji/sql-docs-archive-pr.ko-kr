---
title: 옵션 (텍스트 편집기-Transact-sql-일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.General
dev_langs:
- TSQL
ms.assetid: 7021ecb7-8fb5-4d8c-b984-3d34fcde8be2
author: rothja
ms.author: jroth
ms.openlocfilehash: f008d0d84a15cfbf0bfa988232015e6619f4f5c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652993"
---
# <a name="options-text-editor---transact-sql--general-page"></a><span data-ttu-id="23b7f-102">옵션 (텍스트 편집기-Transact-sql-일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="23b7f-102">Options (Text Editor - Transact-SQL- General Page)</span></span>
  <span data-ttu-id="23b7f-103">**일반 옵션** 대화 상자를 사용하여 [!INCLUDE[ssDE](../includes/ssde-md.md)] 스크립트를 편집하는 데 사용되는 [!INCLUDE[tsql](../includes/tsql-md.md)] 쿼리 편집기의 일반 편집 동작을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-103">Use the **General** options dialog box to change the general editing behavior of the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor, which is used to edit [!INCLUDE[tsql](../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="23b7f-104">이러한 설정을 표시하려면 **도구** 메뉴에서 **옵션**을 클릭하고 **Transact-SQL** 하위 폴더를 확장한 다음 **일반**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-104">To display these settings, click **Options** on the **Tools** menu, expand the **Transact-SQL** subfolder, and then click **General**.</span></span>  
  
## <a name="setting-options-in-multiple-locations"></a><span data-ttu-id="23b7f-105">여러 위치에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="23b7f-105">Setting Options in Multiple Locations</span></span>  
 <span data-ttu-id="23b7f-106">[!INCLUDE[ssDE](../includes/ssde-md.md)] 쿼리 편집기에 대한 옵션은 **모든 언어** 대화 상자(일반)에서도 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-106">Options for the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor can also be set in the **All Languages General** dialog.</span></span> <span data-ttu-id="23b7f-107">**모든 언어** 대화 상자를 사용 하 여 DMX 또는 MDX 편집기 등의 다른 편집기에 대해 다른 옵션을 설정 하는 경우에는 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] 이 대화 상자를 사용 하 여 쿼리 편집기 옵션을 다시 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-107">If you use the **All Languages** dialogs to set different options for the other [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] editors, such as the DMX or MDX editors, you must reset the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor options using this dialog.</span></span>  
  
## <a name="statement-completion"></a><span data-ttu-id="23b7f-108">문 완성</span><span class="sxs-lookup"><span data-stu-id="23b7f-108">Statement Completion</span></span>  
 <span data-ttu-id="23b7f-109">**멤버 목록 자동 표시**</span><span class="sxs-lookup"><span data-stu-id="23b7f-109">**Auto list members**</span></span>  
 <span data-ttu-id="23b7f-110">이 확인란을 선택하면 편집기에 입력할 때 사용 가능한 데이터베이스, 스키마 개체, 열, 테이블 반환 함수 또는 함수 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-110">When this check box is selected, lists of available database and schema objects, columns, table-valued functions, or functions are displayed as you type in the editor.</span></span> <span data-ttu-id="23b7f-111">팝업 목록에서 항목을 선택하면 코드에 해당 항목이 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-111">Choose any item from the pop-up list to insert it into your code.</span></span>  
  
 <span data-ttu-id="23b7f-112">**고급 멤버 숨기기**</span><span class="sxs-lookup"><span data-stu-id="23b7f-112">**Hide advanced members**</span></span>  
 <span data-ttu-id="23b7f-113">이 확인란은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-113">This check box is unavailable.</span></span>  
  
 <span data-ttu-id="23b7f-114">**매개 변수 정보**</span><span class="sxs-lookup"><span data-stu-id="23b7f-114">**Parameter information**</span></span>  
 <span data-ttu-id="23b7f-115">이 확인란을 선택하면 삽입 지점(커서)의 바로 왼쪽에 있는 저장 프로시저 또는 함수에 대한 매개 변수 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-115">When this check box is selected, parameter information is displayed for a stored procedure or function that is immediately to the left of the insertion point (cursor).</span></span> <span data-ttu-id="23b7f-116">이 정보에는 사용 가능한 매개 변수, 매개 변수 이름, 데이터 형식이 나열된 목록이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-116">The information includes a list of the available parameters with their names and data types.</span></span>  
  
## <a name="settings"></a><span data-ttu-id="23b7f-117">설정</span><span class="sxs-lookup"><span data-stu-id="23b7f-117">Settings</span></span>  
 <span data-ttu-id="23b7f-118">**가상 공간 활성화**</span><span class="sxs-lookup"><span data-stu-id="23b7f-118">**Enable virtual space**</span></span>  
 <span data-ttu-id="23b7f-119">이 확인란을 선택하면 코드 줄 끝 뒤에 있는 어느 위치든 클릭하여 내용을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-119">When this check box is selected, you can click anywhere beyond the end of a line of code and type.</span></span> <span data-ttu-id="23b7f-120">이 확인란을 선택하면 코드 옆의 일정한 위치에 설명을 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-120">Select this check box to position comments at a consistent point next to your code.</span></span> <span data-ttu-id="23b7f-121">이 확인란을 선택하면 **자동 줄 바꿈** 확인란이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-121">Selecting this check box disables the **Word wrap** check box.</span></span>  
  
 <span data-ttu-id="23b7f-122">**자동 줄 바꿈**</span><span class="sxs-lookup"><span data-stu-id="23b7f-122">**Word wrap**</span></span>  
 <span data-ttu-id="23b7f-123">이 확인란을 선택하면 가로로 표시되는 편집기 영역을 벗어나는 줄 부분이 자동으로 다음 줄에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-123">When this check box is selected, any portion of a line that extends horizontally beyond the viewable editor area is automatically displayed on the next line.</span></span> <span data-ttu-id="23b7f-124">이 확인란을 선택하면 **자동 줄 바꿈 시각 문자 표시** 확인란이 활성화되고 **가상 공간 활성화** 확인란이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-124">Selecting this check box enables the **Show visual glyphs for word wrap** check box and disables the **Enable virtual space** check box.</span></span>  
  
 <span data-ttu-id="23b7f-125">**자동 줄 바꿈 시각 문자 표시**</span><span class="sxs-lookup"><span data-stu-id="23b7f-125">**Show visual glyphs for word wrap**</span></span>  
 <span data-ttu-id="23b7f-126">이 확인란을 선택하면 긴 줄이 다음 줄로 줄 바꿈될 때 리턴 화살표 표시가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-126">When this check box is selected, a return arrow indicator is displayed where a long line wraps to the next line.</span></span>  
  
 <span data-ttu-id="23b7f-127">**선택 영역이 없는 경우 잘라내기 또는 복사 명령을 빈 줄에 적용**</span><span class="sxs-lookup"><span data-stu-id="23b7f-127">**Apply Cut/Copy commands to blank lines when there is no selection**</span></span>  
 <span data-ttu-id="23b7f-128">이 확인란은 빈 줄에 삽입 포인터를 두고 어떤 영역도 선택하지 않은 채 **복사** 또는 **잘라내기**를 클릭한 경우의 편집기 동작을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-128">This check box sets the behavior of the editor when you place the insertion point on a blank line, select nothing, and then click **Copy** or **Cut**.</span></span>  
  
 <span data-ttu-id="23b7f-129">이 확인란을 선택하면 빈 줄을 복사하거나 잘라냅니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-129">When this check box is selected, the blank line is copied or cut.</span></span> <span data-ttu-id="23b7f-130">그런 다음 **붙여넣기**를 클릭하면 새로운 빈 줄이 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-130">If you then click **Paste**, a new, blank line is inserted.</span></span>  
  
 <span data-ttu-id="23b7f-131">이 확인란의 선택을 취소하면 아무 것도 복사하거나 잘라내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-131">When this check box is cleared, nothing is copied or cut.</span></span> <span data-ttu-id="23b7f-132">그런 다음 **붙여넣기**를 클릭하면 가장 최근에 복사한 내용을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-132">If you then click **Paste**, the content most recently copied is pasted.</span></span> <span data-ttu-id="23b7f-133">이전에 복사한 내용이 없으면 아무 것도 붙여 넣지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-133">If nothing has been copied previously, nothing is pasted.</span></span>  
  
 <span data-ttu-id="23b7f-134">줄이 비어 있지 않으면 이 설정은 **복사** 또는 **잘라내기** 에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-134">This setting has no effect on **Copy** or **Cut** when a line is not blank.</span></span> <span data-ttu-id="23b7f-135">어떤 영역도 선택하지 않으면 줄 전체를 복사하거나 잘라냅니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-135">If nothing is selected, the entire line is copied or cut.</span></span> <span data-ttu-id="23b7f-136">그런 다음 **붙여넣기**를 클릭하면 줄 전체의 텍스트와 줄 끝 문자를 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-136">If you then click **Paste**, the text of the entire line and its end line character are pasted.</span></span>  
  
## <a name="display"></a><span data-ttu-id="23b7f-137">표시</span><span class="sxs-lookup"><span data-stu-id="23b7f-137">Display</span></span>  
 <span data-ttu-id="23b7f-138">**줄 번호**</span><span class="sxs-lookup"><span data-stu-id="23b7f-138">**Line numbers**</span></span>  
 <span data-ttu-id="23b7f-139">이 확인란을 선택하면 각 코드 줄 옆에 줄 번호가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-139">When this check box is selected, a line number appears next to each line of code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="23b7f-140">이러한 줄 번호는 코드에 추가되거나 인쇄되지 않으며</span><span class="sxs-lookup"><span data-stu-id="23b7f-140">These line numbers are not added to your code, and they do not print.</span></span> <span data-ttu-id="23b7f-141">참조용으로만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-141">They are for reference only.</span></span>  
  
 <span data-ttu-id="23b7f-142">**한 번 클릭으로 URL 탐색**</span><span class="sxs-lookup"><span data-stu-id="23b7f-142">**Enable single-click URL navigation**</span></span>  
 <span data-ttu-id="23b7f-143">이 확인란을 선택하면 편집기에서 URL 위로 커서를 가져갈 때 커서가 가리키는 손 모양으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-143">When this check box is selected, the cursor changes to a pointing hand as it passes over a URL in the editor.</span></span> <span data-ttu-id="23b7f-144">URL을 클릭하면 웹 브라우저에 해당 페이지를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-144">You can click the URL to display the indicated page in your Web browser.</span></span>  
  
 <span data-ttu-id="23b7f-145">**탐색 모음**</span><span class="sxs-lookup"><span data-stu-id="23b7f-145">**Navigation bar**</span></span>  
 <span data-ttu-id="23b7f-146">이 확인란은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23b7f-146">This check box is unavailable.</span></span>  
  
  
