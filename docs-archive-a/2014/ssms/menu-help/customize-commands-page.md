---
title: 사용자 지정(명령 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.vs.customizecom.f1
ms.assetid: c8965f2c-51d9-437d-a6f3-8ac2075ede6b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 684fb9a6266fafae00b9881eb64a3642e6c98c79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733448"
---
# <a name="customize-commands-page"></a><span data-ttu-id="753ad-102">사용자 지정(명령 페이지)</span><span class="sxs-lookup"><span data-stu-id="753ad-102">Customize (Commands Page)</span></span>
  <span data-ttu-id="753ad-103">이 대화 상자를 사용하여 도구 모음과 메뉴에서 명령을 추가하거나 제거할 수 있을 뿐만 아니라 도구 모음 단추 또는 메뉴 명령에 사용되는 이미지를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="753ad-103">This dialog box enables you to add and remove commands on toolbars and menus as well as change the images used for toolbar buttons or menu commands.</span></span> <span data-ttu-id="753ad-104">**도구** 메뉴에서 **사용자 지정** 을 클릭한 다음 **명령** 을 클릭하면 **명령**페이지에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="753ad-104">You can access the **Commands** page by clicking **Customize** on the **Tools** menu and then clicking **Commands**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="753ad-105">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="753ad-105">UI element list</span></span>  
 <span data-ttu-id="753ad-106">**범주**</span><span class="sxs-lookup"><span data-stu-id="753ad-106">**Categories**</span></span>  
 <span data-ttu-id="753ad-107">**명령** 목록 상자에 표시되는 명령 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="753ad-107">Specifies the set of commands that are displayed in the **Commands** list box.</span></span> <span data-ttu-id="753ad-108">명령의 범주는 현재 환경이 지원하는 도구와 디자이너에서 제공하는 메뉴 제목에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="753ad-108">The categories of commands are based on menu titles provided by the tools and designers that the environment is currently supporting.</span></span> <span data-ttu-id="753ad-109">이 제목 목록은 동적이며 도구와 디자이너 및 해당 도구와 디자이너에 적용된 사용자 지정에 따라 범주 및 메뉴 제목의 순서가 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="753ad-109">This list of titles is dynamic so that the order of categories and the menu titles change, depending on the tools and the designer, as well as any customizations made to them.</span></span> <span data-ttu-id="753ad-110">따라서 디자이너에 따라 서로 다른 메뉴의 이름이 같을 수도 있기 때문에 같은 제목이 두 번 표시되더라도 제공하는 명령 집합은 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="753ad-110">Therefore, it is possible for two menus from different designers to have the same name, so the same title can appear twice but offer different command sets.</span></span>  
  
 <span data-ttu-id="753ad-111">**명령**</span><span class="sxs-lookup"><span data-stu-id="753ad-111">**Commands**</span></span>  
 <span data-ttu-id="753ad-112">선택한 범주를 기준으로 명령과 명령 이미지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="753ad-112">Displays the commands and command images based on the category you selected.</span></span> <span data-ttu-id="753ad-113">명령을 도구 모음으로 끌어 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="753ad-113">You can drag a command onto the toolbar you want to customize.</span></span>  
  
 <span data-ttu-id="753ad-114">**선택 사항 수정**</span><span class="sxs-lookup"><span data-stu-id="753ad-114">**Modify Selection**</span></span>  
 <span data-ttu-id="753ad-115">도구 모음에 표시되는 단추를 사용자 지정하는 데 사용할 수 있는 명령 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="753ad-115">Displays a list of commands you can use to customize the display of the button on the toolbar.</span></span> <span data-ttu-id="753ad-116">예를 들어 이미지 또는 액셀러레이터 키를 변경하고 명령의 이미지 대신 텍스트를 표시하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="753ad-116">For example, you can change the image or accelerator keys, as well as specify whether to display text instead of an image for the command.</span></span> <span data-ttu-id="753ad-117">이 단추는 도구 모음에서 사용자 지정할 명령 단추를 선택하면 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="753ad-117">This button is available after you select a command button on a toolbar you want to customize.</span></span>  
  
 <span data-ttu-id="753ad-118">**명령 다시 정렬**</span><span class="sxs-lookup"><span data-stu-id="753ad-118">**Rearrange Commands**</span></span>  
 <span data-ttu-id="753ad-119">메뉴 및 도구 모음에서 명령의 순서를 바꾸거나 명령을 추가 또는 제거하거나 명령의 이름을 바꾸는 것은 물론 단추 이미지와 명령 이미지를 변경할 수 있는 **명령 다시 정렬** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="753ad-119">Displays the **Rearrange Commands** dialog box, which allows you to rename, reorder, add, and remove commands on menus and toolbars as well as change button and command images.</span></span>  
  
 <span data-ttu-id="753ad-120">**키보드**</span><span class="sxs-lookup"><span data-stu-id="753ad-120">**Keyboard**</span></span>  
 <span data-ttu-id="753ad-121">명령에 대한 바로 가기 키 조합을 지정할 수 있는 **옵션** 대화 상자의 **키보드** 페이지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="753ad-121">Displays the **Keyboard** page of the **Options** dialog box so you can specify shortcut key combinations for commands.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="753ad-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="753ad-122">See Also</span></span>  
 [<span data-ttu-id="753ad-123">메뉴 및 바로 가기 키 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="753ad-123">Customize Menus and Shortcut Keys</span></span>](../customize-menus-and-shortcut-keys.md)  
