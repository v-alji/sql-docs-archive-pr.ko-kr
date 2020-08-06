---
title: 옵션 (텍스트 편집기-모든 언어-탭 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: bd715d6b-f873-41d4-aa10-57b7098b61cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 13f791e34b2099e8c0492c25886ee6b37ef1a1a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659638"
---
# <a name="options-text-editor---all-languages--tabs-page"></a><span data-ttu-id="6c588-102">옵션(텍스트 편집기 - 모든 언어 - 탭 페이지)</span><span class="sxs-lookup"><span data-stu-id="6c588-102">Options (Text Editor - All Languages -Tabs Page)</span></span>
  <span data-ttu-id="6c588-103">이 대화 상자를 사용하여 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에 포함된 5개 편집기 모두의 탭 이동 동작을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-103">Use this dialog box to set the tabbing behavior in all five of the editors in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="6c588-104">이 옵션을 표시하려면 **도구** 메뉴에서 **옵션** 을 클릭하고</span><span class="sxs-lookup"><span data-stu-id="6c588-104">To display these options, click **Options** on the **Tools** menu.</span></span> <span data-ttu-id="6c588-105">**텍스트 편집기** 폴더를 선택한 다음 **모든 언어** 폴더를 확장하고 **탭**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-105">Select the **Text Editor** folder, expand the **All Languages** folder and then click **Tabs**.</span></span>  
  
## <a name="tabbing-options-by-editor"></a><span data-ttu-id="6c588-106">편집기별 탭 이동 옵션</span><span class="sxs-lookup"><span data-stu-id="6c588-106">Tabbing Options by Editor</span></span>  
 <span data-ttu-id="6c588-107">DMX, MDX 및 SQL Server Compact 편집기에 대해 옵션을 설정하려면 **모든 언어** 대화 상자를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-107">You must use the **All Languages** dialogs to set options for the DMX, MDX, and SQL Server Compact editors.</span></span> <span data-ttu-id="6c588-108">여기서 설정한 옵션은 일반 텍스트, Transact-SQL 및 XML 편집기에도 적용되지만 이러한 언어에 대한 하위 폴더를 확장하고 해당 옵션 페이지를 선택하여 각 편집기에 대해 옵션을 별도로 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-108">Options set here are also applied to the Plain Text, Transact-SQL, and XML editors, but you can set options separately for those editors by expanding the subfolders for those languages and selecting their option pages.</span></span> <span data-ttu-id="6c588-109">일부 탭 이동 옵션만 지원하는 언어도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-109">Some languages do not support all of the tabbing options.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="6c588-110">이 대화 상자에서 옵션을 설정하되 일반 텍스트, Transact-SQL 또는 XML 편집기에는 다른 설정을 지정하려면 **모든 언어** 대화 상자에서 선택 항목을 적용한 후에 해당 편집기에 대한 옵션을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-110">If you set an option using this dialog, but want a different setting for the Plain Text, Transact-SQL, or XML editors, you must set the options for those editors after applying your selections in the **All Languages** dialog.</span></span>  
  
 <span data-ttu-id="6c588-111">특정 편집기에 대해 다른 설정을 선택한 경우 "개별 텍스트 형식에 대한 들여쓰기(또는 탭) 설정이 서로 충돌합니다."라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-111">The message "The indentation (or tab) settings for individual text formats conflict with each other" is displayed when different settings have been selected for particular editors.</span></span> <span data-ttu-id="6c588-112">예를 들어 **일반 텍스트**에 대해서는 **들여쓰기 차단** 옵션을 선택하고 **XML**에 대해서는 **없음**을 선택하면 이 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-112">For example, this reminder is displayed if the **Block indenting** option is selected for **Plain Text**, but **None** is selected for **XML**.</span></span>  
  
## <a name="indenting"></a><span data-ttu-id="6c588-113">들여쓰기</span><span class="sxs-lookup"><span data-stu-id="6c588-113">Indenting</span></span>  
 <span data-ttu-id="6c588-114">**없음**</span><span class="sxs-lookup"><span data-stu-id="6c588-114">**None**</span></span>  
 <span data-ttu-id="6c588-115">이 옵션을 선택하면 Enter 키를 누를 때 생성되는 새 줄을 들여쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-115">When this option is selected, the new line created when you press ENTER is not indented.</span></span> <span data-ttu-id="6c588-116">커서는 새 줄의 첫 번째 열에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-116">The cursor is placed at the first column of the new line.</span></span>  
  
 <span data-ttu-id="6c588-117">**차단**</span><span class="sxs-lookup"><span data-stu-id="6c588-117">**Block**</span></span>  
 <span data-ttu-id="6c588-118">이 옵션을 선택하면 Enter 키를 누를 때 생성되는 새 줄을 자동으로 앞 줄과 동일하게 들여씁니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-118">When this option is selected, the new line created when you press ENTER is automatically indented the same distance as the previous line was indented.</span></span>  
  
 <span data-ttu-id="6c588-119">**스마트**</span><span class="sxs-lookup"><span data-stu-id="6c588-119">**Smart**</span></span>  
 <span data-ttu-id="6c588-120">이 옵션을 선택하면 Enter 키를 누를 때 생성되는 새 줄의 위치가 컨텍스트에 따라 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-120">When this option is selected, the new line created when you press ENTER is positioned according to the context.</span></span>  
  
## <a name="tabs"></a><span data-ttu-id="6c588-121">탭</span><span class="sxs-lookup"><span data-stu-id="6c588-121">Tabs</span></span>  
 <span data-ttu-id="6c588-122">**탭 크기**</span><span class="sxs-lookup"><span data-stu-id="6c588-122">**Tab size**</span></span>  
 <span data-ttu-id="6c588-123">탭 정지 간의 거리를 공백 수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-123">Sets the distance in spaces between tab stops.</span></span> <span data-ttu-id="6c588-124">기본값은 공백 4개입니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-124">The default is four spaces.</span></span>  
  
 <span data-ttu-id="6c588-125">**들여쓰기 크기**</span><span class="sxs-lookup"><span data-stu-id="6c588-125">**Indent size**</span></span>  
 <span data-ttu-id="6c588-126">자동 들여쓰기의 크기를 공백 수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-126">Sets the size in spaces of an automatic indentation.</span></span> <span data-ttu-id="6c588-127">기본값은 공백 4개입니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-127">The default is four spaces.</span></span> <span data-ttu-id="6c588-128">탭 문자나 공백 문자 또는 두 가지 문자 모두를 삽입하여 지정한 크기를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-128">Tab characters, space characters, or both will be inserted to fill the specified size.</span></span>  
  
 <span data-ttu-id="6c588-129">**공백 삽입**</span><span class="sxs-lookup"><span data-stu-id="6c588-129">**Insert spaces**</span></span>  
 <span data-ttu-id="6c588-130">이 옵션을 선택하면 들여쓰기 작업에서 탭 문자 대신 공백 문자만 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-130">When this option is selected, indent operations insert only space characters, not tab characters.</span></span> <span data-ttu-id="6c588-131">예를 들어 **들여쓰기 크기**를 5로 설정하면 Tab 키를 누르거나 기본 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 창에서 도구 모음의 **들여쓰기** 단추를 클릭할 때마다 5개의 공백 문자가 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-131">If **Indent size** is set to 5, for example, then five space characters are inserted whenever you press the TAB key or click the **Increase Indent** button on the toolbar of the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] main window.</span></span>  
  
 <span data-ttu-id="6c588-132">**탭 유지**</span><span class="sxs-lookup"><span data-stu-id="6c588-132">**Keep tabs**</span></span>  
 <span data-ttu-id="6c588-133">이 옵션을 선택하면 들여쓰기 작업에서 가능한 한 많은 탭 문자를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-133">When this option is selected, indent operations insert as many tab characters as possible.</span></span> <span data-ttu-id="6c588-134">각 탭 문자는 **탭 크기**에 지정된 공백 수를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-134">Each tab character fills the number of spaces specified in **Tab size**.</span></span> <span data-ttu-id="6c588-135">**들여쓰기 크기** 가 **탭 크기**의 짝수 배수가 아니면 공백 문자가 추가되어 차이를 메웁니다.</span><span class="sxs-lookup"><span data-stu-id="6c588-135">If **Indent size** is not an even multiple of **Tab size**, space characters are added to fill in the difference.</span></span>  
  
  
