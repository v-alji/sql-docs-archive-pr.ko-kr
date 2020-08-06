---
title: '옵션 (텍스트 편집기: XML: 탭 페이지) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Tabs
ms.assetid: 13bf5f8c-aba3-4c05-b8bb-eb475797c9bd
author: rothja
ms.author: jroth
ms.openlocfilehash: 3047d6c05ffb88d07a4bf2e5b1d4143412046c04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727320"
---
# <a name="options-text-editorxmltabs-page"></a><span data-ttu-id="f7353-102">옵션(텍스트 편집기:XML:탭 페이지)</span><span class="sxs-lookup"><span data-stu-id="f7353-102">Options (Text Editor:XML:Tabs Page)</span></span>
  <span data-ttu-id="f7353-103">이 대화 상자에서는 XML 문서를 편집하는 데 사용되는 XML 편집기의 탭 이동 동작을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-103">This dialog box lets you change the tabbing behavior of the XML Editor, which is used to edit XML documents.</span></span> <span data-ttu-id="f7353-104">이 설정을 표시하려면 **도구** 메뉴에서 **옵션** 을 클릭하고 **텍스트 편집기** 폴더와 **XML** 하위 폴더를 차례로 확장한 다음 **탭**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-104">To display these settings, click **Options** on the **Tools** menu, expand the **Text Editor** folder, expand the **XML** subfolder and then click **Tabs**.</span></span>  
  
## <a name="setting-options-in-multiple-locations"></a><span data-ttu-id="f7353-105">여러 위치에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="f7353-105">Setting Options in Multiple Locations</span></span>  
 <span data-ttu-id="f7353-106">XML 편집기에 대한 옵션은 **모든 언어** 대화 상자(일반)에서도 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-106">Options for the XML Editor can also be set in the **All Languages General** dialog.</span></span> <span data-ttu-id="f7353-107">**모든 언어** 대화 상자를 사용 하 여 DMX 또는 MDX 편집기 등의 다른 편집기에 대해 다른 옵션을 설정 하는 경우에는 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 이 대화 상자를 사용 하 여 XML 편집기 옵션을 다시 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-107">If you use the **All Languages** dialogs to set different options for the other [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] editors, such as the DMX or MDX editors, you must reset the XML Editor options using this dialog.</span></span>  
  
## <a name="indenting"></a><span data-ttu-id="f7353-108">들여쓰기</span><span class="sxs-lookup"><span data-stu-id="f7353-108">Indenting</span></span>  
 <span data-ttu-id="f7353-109">**없음**</span><span class="sxs-lookup"><span data-stu-id="f7353-109">**None**</span></span>  
 <span data-ttu-id="f7353-110">이 옵션을 선택하면 Enter 키를 누를 때 생성되는 새 줄을 들여쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-110">When this option is selected, the new line created when you press ENTER is not indented.</span></span> <span data-ttu-id="f7353-111">커서는 새 줄의 첫 번째 열에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-111">The cursor is placed at the first column of the new line.</span></span>  
  
 <span data-ttu-id="f7353-112">**차단**</span><span class="sxs-lookup"><span data-stu-id="f7353-112">**Block**</span></span>  
 <span data-ttu-id="f7353-113">이 옵션을 선택하면 Enter 키를 누를 때 생성되는 새 줄을 자동으로 앞 줄과 동일하게 들여씁니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-113">When this option is selected, the new line created when you press ENTER is automatically indented the same distance as the previous line.</span></span>  
  
 <span data-ttu-id="f7353-114">**스마트**</span><span class="sxs-lookup"><span data-stu-id="f7353-114">**Smart**</span></span>  
 <span data-ttu-id="f7353-115">이 옵션을 선택하면 Enter 키를 누를 때 생성되는 새 줄의 위치가 컨텍스트에 따라 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-115">When this option is selected, the new line created when you press ENTER is positioned according to the context.</span></span> <span data-ttu-id="f7353-116">예를 들어 여는 중괄호({) 뒤에 포함되는 줄은 자동으로 추가 탭 정지를 사용하여 들여씁니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-116">For example, after an opening brace ({), the included lines are automatically indented an extra tab stop.</span></span> <span data-ttu-id="f7353-117">닫는 중괄호(})의 위치는 해당 여는 중괄호에 맞게 다시 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-117">The matching closing brace (}) is realigned with its opening brace.</span></span>  
  
## <a name="tabs"></a><span data-ttu-id="f7353-118">탭</span><span class="sxs-lookup"><span data-stu-id="f7353-118">Tabs</span></span>  
 <span data-ttu-id="f7353-119">**탭 크기**</span><span class="sxs-lookup"><span data-stu-id="f7353-119">**Tab size**</span></span>  
 <span data-ttu-id="f7353-120">탭 정지 간의 거리를 공백 수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-120">Sets the distance in spaces between tab stops.</span></span> <span data-ttu-id="f7353-121">기본값은 공백 4개입니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-121">The default is four spaces.</span></span>  
  
 <span data-ttu-id="f7353-122">**들여쓰기 크기**</span><span class="sxs-lookup"><span data-stu-id="f7353-122">**Indent size**</span></span>  
 <span data-ttu-id="f7353-123">자동 들여쓰기의 크기를 공백 수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-123">Sets the size in spaces of an automatic indentation.</span></span> <span data-ttu-id="f7353-124">기본값은 공백 4개입니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-124">The default is four spaces.</span></span> <span data-ttu-id="f7353-125">탭 문자나 공백 문자 또는 두 가지 문자 모두를 삽입하여 지정한 크기를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-125">Tab characters, space characters, or both are inserted to fill the specified size.</span></span>  
  
 <span data-ttu-id="f7353-126">**공백 삽입**</span><span class="sxs-lookup"><span data-stu-id="f7353-126">**Insert spaces**</span></span>  
 <span data-ttu-id="f7353-127">이 옵션을 선택하면 들여쓰기 작업에서 탭 문자 대신 공백 문자만 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-127">When this option is selected, indent operations insert only space characters, not tab characters.</span></span> <span data-ttu-id="f7353-128">예를 들어 **들여쓰기 크기** 를 5로 설정 하면 TAB 키를 누르거나 주 창에서 도구 모음의 **들여쓰기** 단추를 클릭할 때마다 5 개의 공백 문자가 삽입 됩니다 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f7353-128">If **Indent size** is set to 5, for example, then five space characters are inserted whenever you press the TAB key or click the **Increase Indent** button on the toolbar in the main [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] window.</span></span>  
  
 <span data-ttu-id="f7353-129">**탭 유지**</span><span class="sxs-lookup"><span data-stu-id="f7353-129">**Keep tabs**</span></span>  
 <span data-ttu-id="f7353-130">이 옵션을 선택하면 들여쓰기 작업에서 가능한 한 많은 탭 문자를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-130">When this option is selected, indent operations insert as many tab characters as possible.</span></span> <span data-ttu-id="f7353-131">각 탭 문자는 **탭 크기**에 지정된 공백 수를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-131">Each tab character fills the number of spaces specified in **Tab size**.</span></span> <span data-ttu-id="f7353-132">**들여쓰기 크기** 가 **탭 크기**의 짝수 배수가 아니면 공백 문자가 추가되어 차이를 메웁니다.</span><span class="sxs-lookup"><span data-stu-id="f7353-132">If **Indent size** is not an even multiple of **Tab size**, space characters are added to fill in the difference.</span></span>  
  
  
