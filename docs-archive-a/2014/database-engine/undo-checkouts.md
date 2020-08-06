---
title: 체크 아웃 취소 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourcControl.UndoCheckDialog
helpviewer_keywords:
- checking out files
- checkout source controls [SQL Server]
- undoing checkouts
ms.assetid: a6596b20-3aa5-4dc4-a4c5-3649f1f5a20e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ff6e6041b59caa75bf7f8530d915db48e0379338
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646596"
---
# <a name="undo-checkouts"></a><span data-ttu-id="a16ad-102">체크 아웃 취소</span><span class="sxs-lookup"><span data-stu-id="a16ad-102">Undo Checkouts</span></span>
  <span data-ttu-id="a16ad-103">**체크 아웃 취소** 명령을 사용하여 기존 체크 아웃을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a16ad-103">You can use the **Undo Checkout** command to cancel an existing checkout.</span></span> <span data-ttu-id="a16ad-104">파일을 수정 및 저장한 다음 나중에 변경 내용을 롤백해야 하는 경우에 이 명령이 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a16ad-104">This is particularly useful when you have modified and saved a file, and then later need to roll back your changes.</span></span>  
  
 <span data-ttu-id="a16ad-105">**체크 아웃 취소 고급 옵션** 대화 상자에서 설정한 옵션에 따라서 Studio 환경은 항목의 작업 복사본을 로컬 디스크에 그대로 두거나 해당 복사본을 최신 원본 제어 버전으로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="a16ad-105">Depending on the options you set in the **Undo Checkout Advanced Options** dialog box, the Studio environment either leaves the working copy of the item on your local disk or replaces it with the latest source-controlled version.</span></span> <span data-ttu-id="a16ad-106">임의의 사용자가 원본 제어 시스템의 컨텍스트 외부에서 항목을 수정한 경우 검색된 버전은 최신 버전이 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a16ad-106">If someone has modified the item outside the context of the source control system, the retrieved version may not be the latest one.</span></span>  
  
### <a name="to-undo-a-checkout"></a><span data-ttu-id="a16ad-107">체크 아웃을 취소하려면</span><span class="sxs-lookup"><span data-stu-id="a16ad-107">To undo a checkout</span></span>  
  
1.  <span data-ttu-id="a16ad-108">솔루션 탐색기에서 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a16ad-108">In Solution Explorer, select the project.</span></span>  
  
2.  <span data-ttu-id="a16ad-109">**파일** 메뉴에서 **원본 제어**를 가리킨 다음 **체크 아웃 취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a16ad-109">On the **File** menu, point to **Source Control**, and then click **Undo Checkout**.</span></span>  
  
3.  <span data-ttu-id="a16ad-110">**체크 아웃 취소** 대화 상자에서 적절한 옵션을 선택한 다음 **체크 아웃 취소** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a16ad-110">In the **Undo Checkout** dialog box, select the appropriate options, and then click the **Undo Checkout** button.</span></span>  
  
     <span data-ttu-id="a16ad-111">**열**</span><span class="sxs-lookup"><span data-stu-id="a16ad-111">**Columns**</span></span>  
     <span data-ttu-id="a16ad-112">표시할 열 및 열이 표시되는 순서를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="a16ad-112">Identify the columns to display and the order in which they are displayed.</span></span>  
  
     <span data-ttu-id="a16ad-113">**기본 뷰**</span><span class="sxs-lookup"><span data-stu-id="a16ad-113">**Flat View**</span></span>  
     <span data-ttu-id="a16ad-114">항목을 해당 원본 제어 연결 아래에 기본 목록으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a16ad-114">Display the items as flat lists under their source control connection.</span></span>  
  
     <span data-ttu-id="a16ad-115">**이름**</span><span class="sxs-lookup"><span data-stu-id="a16ad-115">**Name**</span></span>  
     <span data-ttu-id="a16ad-116">체크 아웃을 취소할 항목의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a16ad-116">Displays the names of the items for which to undo the checkout.</span></span> <span data-ttu-id="a16ad-117">항목은 옆에 있는 확인란이 선택된 상태로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a16ad-117">Items appear with the check boxes next to them selected.</span></span> <span data-ttu-id="a16ad-118">항목의 체크 아웃을 취소하지 않으려면 해당 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="a16ad-118">If you do not want to undo the checkout of an item, clear its check box.</span></span>  
  
     <span data-ttu-id="a16ad-119">**Options**</span><span class="sxs-lookup"><span data-stu-id="a16ad-119">**Options**</span></span>  
     <span data-ttu-id="a16ad-120">단추 오른쪽의 화살표를 클릭하면 원본 제어 플러그 인의 체크 아웃 취소 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a16ad-120">Displays source control plug-in-specific undo checkout options when the arrow to the right of the button is clicked.</span></span>  
  
     <span data-ttu-id="a16ad-121">**Sort**</span><span class="sxs-lookup"><span data-stu-id="a16ad-121">**Sort**</span></span>  
     <span data-ttu-id="a16ad-122">열 표시의 순서를 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="a16ad-122">Sort the order of the display columns.</span></span>  
  
     <span data-ttu-id="a16ad-123">**트리 뷰**</span><span class="sxs-lookup"><span data-stu-id="a16ad-123">**Tree View**</span></span>  
     <span data-ttu-id="a16ad-124">체크 아웃을 되돌리고 있는 항목의 폴더 및 항목 계층 구조를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a16ad-124">Display the folder and item hierarchy for items on which you are reversing the checkout.</span></span>  
  
     <span data-ttu-id="a16ad-125">**체크 아웃 취소**</span><span class="sxs-lookup"><span data-stu-id="a16ad-125">**Undo Checkout**</span></span>  
     <span data-ttu-id="a16ad-126">체크 아웃된 파일의 모든 변경 내용을 삭제하고 체크 아웃을 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="a16ad-126">Revert the checkout, discarding any changes to the checked-out file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a16ad-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a16ad-127">See Also</span></span>  
 <span data-ttu-id="a16ad-128">[파일 체크 아웃](../../2014/database-engine/check-out-files.md) </span><span class="sxs-lookup"><span data-stu-id="a16ad-128">[Check Out Files](../../2014/database-engine/check-out-files.md) </span></span>  
 [<span data-ttu-id="a16ad-129">체크 아웃 관리</span><span class="sxs-lookup"><span data-stu-id="a16ad-129">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
