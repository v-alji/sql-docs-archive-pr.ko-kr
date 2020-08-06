---
title: 코드 서식 관리
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- indenting code [SQL Server]
- displaying URLs
- code formatting [SQL Server Management Studio]
- collapsing text
- formats [SQL Server], code formatting in SQL Server Management Studio
- hiding text
- formats [SQL Server]
- text [SQL Server], code formats
- automatic indentation
- converting text to lower case
- Query Editor [SQL Server Management Studio], managing code formats
- URL displayed in code [SQL Server Management Studio]
- converting text to upper case
- text [SQL Server]
- unindenting code
ms.assetid: ddbac4d2-6bdc-4467-a352-e869ec880eed
author: rothja
ms.author: jroth
ms.openlocfilehash: 873848c8aee575b47f7a3d8c31d8392cba5ed12e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660990"
---
# <a name="manage-code-formatting"></a><span data-ttu-id="04511-102">코드 서식 관리</span><span class="sxs-lookup"><span data-stu-id="04511-102">Manage Code Formatting</span></span>
  <span data-ttu-id="04511-103">편집기를 사용하면 들여쓰기, 숨겨진 텍스트, URL 등으로 코드의 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04511-103">With the Editor you can format your code with indenting, hidden text, URLs, and so forth.</span></span> <span data-ttu-id="04511-104">또한 스마트 들여쓰기를 사용하여 입력 시에 코드의 서식을 자동으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04511-104">You can also auto-format your code as you type by using Smart Indenting.</span></span>  
  
## <a name="indenting"></a><span data-ttu-id="04511-105">들여쓰기</span><span class="sxs-lookup"><span data-stu-id="04511-105">Indenting</span></span>  
 <span data-ttu-id="04511-106">세 가지 다른 스타일의 텍스트 들여쓰기 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04511-106">You can choose three different styles of text indenting.</span></span> <span data-ttu-id="04511-107">또한 단일 들여쓰기나 탭을 구성하는 공백 수와 들여쓰기 시에 편집기에서 탭이나 공백 문자를 사용하는지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04511-107">You can also specify how many spaces compose a single indentation or tab, and whether the Editor uses tabs or space characters when indenting.</span></span>  
  
#### <a name="to-choose-an-indenting-style"></a><span data-ttu-id="04511-108">들여쓰기 스타일을 선택하려면</span><span class="sxs-lookup"><span data-stu-id="04511-108">To choose an indenting style</span></span>  
  
1.  <span data-ttu-id="04511-109">**도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-109">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="04511-110">**텍스트 편집기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-110">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="04511-111">폴더를 클릭하고 **모든 언어** 를 선택하여 모든 언어에 들여쓰기를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-111">Click the folder, and select **All Languages** to set indenting for all languages.</span></span>  
  
4.  <span data-ttu-id="04511-112">**탭**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-112">Click **Tabs**.</span></span>  
  
5.  <span data-ttu-id="04511-113">다음 옵션 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-113">Click one of the following options:</span></span>  
  
    -   <span data-ttu-id="04511-114">**없음**.</span><span class="sxs-lookup"><span data-stu-id="04511-114">**None**.</span></span> <span data-ttu-id="04511-115">커서를 다음 줄의 시작으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-115">The cursor goes to the beginning of the next line.</span></span>  
  
    -   <span data-ttu-id="04511-116">**블록**.</span><span class="sxs-lookup"><span data-stu-id="04511-116">**Block**.</span></span> <span data-ttu-id="04511-117">커서가 다음 줄을 이전 줄에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="04511-117">The cursor aligns the next line with the previous line.</span></span>  
  
    -   <span data-ttu-id="04511-118">**스마트** (기본값).</span><span class="sxs-lookup"><span data-stu-id="04511-118">**Smart** (Default).</span></span> <span data-ttu-id="04511-119">사용할 적절할 들여쓰기 스타일을 언어 서비스로 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-119">The language service determines the appropriate indenting style to use.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="04511-120">모든 언어에서 세 가지 들여쓰기 옵션이 모두 제공되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="04511-120">Some languages do not offer all three indenting options.</span></span>  
  
#### <a name="to-change-indent-tab-settings"></a><span data-ttu-id="04511-121">들여쓰기 탭 설정을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="04511-121">To change indent tab settings</span></span>  
  
1.  <span data-ttu-id="04511-122">**도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-122">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="04511-123">**텍스트 편집기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-123">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="04511-124">**모든 언어** 에 대한 폴더를 선택하여 모든 언어에 들여쓰기를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-124">Select the folder for **All Languages** to set indenting for all languages.</span></span>  
  
4.  <span data-ttu-id="04511-125">**탭**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-125">Click **Tabs**.</span></span>  
  
5.  <span data-ttu-id="04511-126">탭 및 들여쓰기 작업에 대한 탭 문자를 지정하려면 **탭 유지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-126">To specify tab characters for tab and indent operations, click **Keep tabs**.</span></span> <span data-ttu-id="04511-127">공백 문자를 지정하려면 **공백 삽입**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-127">To specify space characters, select **Insert spaces**.</span></span>  
  
     <span data-ttu-id="04511-128">**공백 삽입**을 선택한 경우 각 탭이나 들여쓰기가 나타내는 공백 문자 수를 각각 **탭 크기** 또는 **들여쓰기 크기**아래에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-128">If you select **Insert Spaces**, enter the number of space characters each tab or indent represents under **Tab Size** or **Indent Size**, respectively.</span></span>  
  
#### <a name="to-indent-code"></a><span data-ttu-id="04511-129">코드를 들여쓰려면</span><span class="sxs-lookup"><span data-stu-id="04511-129">To indent code</span></span>  
  
1.  <span data-ttu-id="04511-130">들여쓸 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-130">Select the text you want to indent.</span></span>  
  
2.  <span data-ttu-id="04511-131">Tab 키를 누르거나 표준 도구 모음에서 **들여쓰기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-131">Press TAB, or click the **Indent** button on the Standard toolbar.</span></span>  
  
#### <a name="to-unindent-code"></a><span data-ttu-id="04511-132">코드를 내어쓰려면</span><span class="sxs-lookup"><span data-stu-id="04511-132">To unindent code</span></span>  
  
1.  <span data-ttu-id="04511-133">내어쓸 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-133">Select the text you want to unindent.</span></span>  
  
2.  <span data-ttu-id="04511-134">Shift+Tab 키를 누르거나 표준 도구 모음에서 **내어쓰기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-134">Press SHIFT+TAB, or click the **Unindent** button on the Standard toolbar.</span></span>  
  
#### <a name="to-automatically-indent-all-of-your-code"></a><span data-ttu-id="04511-135">모든 코드를 자동으로 들여쓰려면</span><span class="sxs-lookup"><span data-stu-id="04511-135">To automatically indent all of your code</span></span>  
  
1.  <span data-ttu-id="04511-136">**도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-136">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="04511-137">**텍스트 편집기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-137">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="04511-138">**모든 언어**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-138">Click **All Languages**.</span></span>  
  
4.  <span data-ttu-id="04511-139">**탭**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-139">Click **Tabs**.</span></span>  
  
5.  <span data-ttu-id="04511-140">**스마트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-140">Click **Smart**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="04511-141">일부 언어에서는 **스마트** 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="04511-141">The **Smart** option is not available for some languages.</span></span>  
  
#### <a name="to-convert-white-space-to-tabs"></a><span data-ttu-id="04511-142">공백을 탭으로 변환하려면</span><span class="sxs-lookup"><span data-stu-id="04511-142">To convert white space to tabs</span></span>  
  
1.  <span data-ttu-id="04511-143">탭으로 변환할 공백이 있는 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-143">Select the text whose white space you want to convert to tabs.</span></span>  
  
2.  <span data-ttu-id="04511-144">**편집** 메뉴에서 **고급**을 가리킨 다음 **선택 영역의 공백을 탭으로**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-144">On the **Edit** menu, point to **Advanced**, and click **Tabify Selection**.</span></span>  
  
#### <a name="to-convert-tabs-to-spaces"></a><span data-ttu-id="04511-145">탭을 공백으로 변환하려면</span><span class="sxs-lookup"><span data-stu-id="04511-145">To convert tabs to spaces</span></span>  
  
1.  <span data-ttu-id="04511-146">공백으로 변환할 탭이 있는 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-146">Select the text whose tabs you want to convert to spaces.</span></span>  
  
2.  <span data-ttu-id="04511-147">**편집** 메뉴에서 **고급**을 가리킨 다음 **선택 영역의 탭을 공백으로**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-147">On the **Edit** menu, point to **Advanced**, and click **Untabify Selection**.</span></span>  
  
 <span data-ttu-id="04511-148">이러한 명령의 동작은 **옵션** 대화 상자의 탭 설정에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="04511-148">The behavior of these commands depends on the tab settings in the **Options** dialog box.</span></span> <span data-ttu-id="04511-149">예를 들어 탭 설정이 4이면 **선택 영역의 공백을 탭으로** 는 4개의 연속된 공백마다 탭을 만들고 **선택 영역의 탭을 공백으로** 는 모든 탭마다 4개의 공백을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04511-149">For example, if the tab setting is 4, **Tabify Selection** creates a tab for every 4 contiguous spaces, and **Untabify Selection** creates 4 spaces for every tab.</span></span>  
  
## <a name="converting-text-to-upper-and-lower-case"></a><span data-ttu-id="04511-150">텍스트를 대문자 및 소문자로 변환</span><span class="sxs-lookup"><span data-stu-id="04511-150">Converting Text to Upper and Lower Case</span></span>  
 <span data-ttu-id="04511-151">명령을 사용하여 텍스트를 모두 대문자나 소문자로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04511-151">You can use commands to convert text to all uppercase or lower case.</span></span>  
  
#### <a name="to-switch-text-to-upper-or-lower-case"></a><span data-ttu-id="04511-152">텍스트를 대문자나 소문자로 변환하려면</span><span class="sxs-lookup"><span data-stu-id="04511-152">To switch text to upper or lower case</span></span>  
  
1.  <span data-ttu-id="04511-153">변환할 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-153">Select the text you want to convert.</span></span>  
  
2.  <span data-ttu-id="04511-154">텍스트를 대문자로 변환하려면 Ctrl+Shift+U를 누르거나 **편집** 메뉴의 **고급** 하위 메뉴에서 **대문자로** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-154">To convert text to uppercase, press CTRL+SHIFT+U, or click **Make Uppercase** on the **Advanced** submenu of the **Edit** menu.</span></span>  
  
3.  <span data-ttu-id="04511-155">텍스트를 소문자로 변환하려면 Ctrl+Shift+L을 누르거나 **편집** 메뉴의 **고급** 하위 메뉴에서 **소문자로** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-155">To convert text to lowercase, press CTRL+SHIFT+L, or click **Make Lowercase** on the **Advanced** submenu of the **Edit** menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="04511-156">바로 가기 키의 전체 목록을 보려면 [SQL Server Management Studio 바로 가기 키](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="04511-156">For a complete list of keyboard shortcut keys, see [SQL Server Management Studio Keyboard Shortcuts](../../ssms/sql-server-management-studio-keyboard-shortcuts.md).</span></span>  
  
## <a name="displaying-and-linking-to-urls"></a><span data-ttu-id="04511-157">URL 표시 및 연결</span><span class="sxs-lookup"><span data-stu-id="04511-157">Displaying and Linking to URLs</span></span>  
 <span data-ttu-id="04511-158">코드에서 클릭 가능한 URL을 만들고 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04511-158">You can create and display clickable URLs in your code.</span></span> <span data-ttu-id="04511-159">기본적으로 URL은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="04511-159">By default, the URLs:</span></span>  
  
-   <span data-ttu-id="04511-160">밑줄이 그어집니다.</span><span class="sxs-lookup"><span data-stu-id="04511-160">Are underlined.</span></span>  
  
-   <span data-ttu-id="04511-161">마우스 포인터를 위로 이동하면 손 모양으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="04511-161">Change the mouse pointer to a hand when you move over them.</span></span>  
  
-   <span data-ttu-id="04511-162">클릭하면 URL이 열립니다(URL이 유효한 경우).</span><span class="sxs-lookup"><span data-stu-id="04511-162">Open the URL when clicked, if the URL is valid.</span></span>  
  
#### <a name="to-display-a-clickable-url"></a><span data-ttu-id="04511-163">클릭 가능한 URL을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="04511-163">To display a clickable URL</span></span>  
  
1.  <span data-ttu-id="04511-164">**도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-164">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="04511-165">**텍스트 편집기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-165">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="04511-166">특정 언어에 대한 옵션만 변경하려면 해당 언어 폴더를 클릭한 다음 **일반**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-166">To change the option for only one language, click that language folder and then click **General**.</span></span> <span data-ttu-id="04511-167">모든 언어에 대한 옵션을 변경하려면 **모든 언어** 를 클릭한 다음 **일반**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-167">To change the option for all languages, click **All Languages** and then click **General**.</span></span>  
  
4.  <span data-ttu-id="04511-168">**한 번 클릭으로 URL 탐색**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="04511-168">Select **Enable single-click URL navigation**.</span></span>  
  
  
