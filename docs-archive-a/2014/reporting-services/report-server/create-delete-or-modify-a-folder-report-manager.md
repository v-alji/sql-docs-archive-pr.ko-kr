---
title: 폴더 만들기, 삭제 또는 수정(보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing folders
- modifying folders
- deleting folders
- folders [Reporting Services], creating
- folders [Reporting Services], deleting
- folders [Reporting Services], modifying
ms.assetid: d62159a8-ec67-4e28-a9f1-05a9250065bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9bd7d5ceebdb7b3a48ded66ed108bddda25d8a46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652582"
---
# <a name="create-delete-or-modify-a-folder-report-manager"></a><span data-ttu-id="3d326-102">폴더 만들기, 삭제 또는 수정(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="3d326-102">Create, Delete, or Modify a Folder (Report Manager)</span></span>
  <span data-ttu-id="3d326-103">폴더를 만들어 보고서 서버에 게시하는 항목을 구성하고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-103">You can create folders to organize and manage the items you publish to a report server.</span></span> <span data-ttu-id="3d326-104">폴더를 만들면 관심 있는 보고서를 찾는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-104">Creating folders can help users find reports of interest to them.</span></span> <span data-ttu-id="3d326-105">내용 관리자의 경우 폴더는 사용 권한을 적용하는 프레임워크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-105">For content managers, folders provide a framework for applying permissions.</span></span> <span data-ttu-id="3d326-106">개발 중인 보고서나 배포되면 안 되는 보고서에 대한 액세스를 제한하기 위해 특정 폴더에 역할 할당을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-106">You can create role assignments on specific folders to restrict access to reports that are in development or that should not be widely distributed.</span></span>  
  
### <a name="to-create-a-folder"></a><span data-ttu-id="3d326-107">폴더를 만들려면</span><span class="sxs-lookup"><span data-stu-id="3d326-107">To create a folder</span></span>  
  
1.  <span data-ttu-id="3d326-108">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-108">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="3d326-109">보고서 관리자에서 홈 폴더를 선택하고 **새 폴더**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-109">In Report Manager, select the Home folder and click **New Folder**.</span></span> <span data-ttu-id="3d326-110">또는 기존 폴더 아래에 폴더를 만들려면 **내용** 페이지에서 해당 폴더로 이동한 후 폴더를 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-110">Or, to create a folder under an existing folder, navigate to that folder in the **Contents** page and click the folder to open it.</span></span> <span data-ttu-id="3d326-111">그런 후 **새 폴더**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-111">Then click **New Folder**.</span></span>  
  
     <span data-ttu-id="3d326-112">**새 폴더** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-112">The **New Folder** page opens.</span></span>  
  
3.  <span data-ttu-id="3d326-113">폴더 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-113">Type a folder name.</span></span> <span data-ttu-id="3d326-114">폴더 이름에 공백을 사용할 수 있지만 다음과 같은 URL 인코딩용으로 예약된 문자는 사용할 수 없습니다. ; ?</span><span class="sxs-lookup"><span data-stu-id="3d326-114">A folder name can include spaces, but cannot include reserved characters that are used for URL encoding: ; ?</span></span> <span data-ttu-id="3d326-115">: \@ & = +, $/\* \< > |입니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-115">: \@ & = + , $ / \* \< > |.</span></span> <span data-ttu-id="3d326-116">한 번에 여러 개의 폴더 이름을 입력하여 여러 폴더를 만들 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-116">You cannot type a series of folder names to create several folders at once.</span></span>  
  
4.  <span data-ttu-id="3d326-117">설명을 입력합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="3d326-117">Optionally type a description.</span></span>  
  
5.  <span data-ttu-id="3d326-118">**내용** 페이지의 기본 보기에서 폴더를 표시하지 않으려면 **목록 뷰에서 숨기기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-118">Select **Hide in list view** if you do not want to display the folder in the default view of the **Contents** page.</span></span> <span data-ttu-id="3d326-119">**내용** 페이지에서 **자세한 정보 표시** 를 클릭하면 숨겨진 폴더가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-119">The folder will be visible to users only when they click **Show Details** on the **Contents** page.</span></span>  
  
6.  <span data-ttu-id="3d326-120">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-120">Click **OK**.</span></span>  
  
### <a name="to-delete-a-folder"></a><span data-ttu-id="3d326-121">폴더를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="3d326-121">To delete a folder</span></span>  
  
1.  <span data-ttu-id="3d326-122">보고서 관리자에서 **내용** 페이지로 이동한 다음 수정할 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-122">In Report Manager, navigate to the **Contents** page, and locate the item that you want to modify.</span></span>  
  
2.  <span data-ttu-id="3d326-123">항목 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-123">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="3d326-124">드롭다운 메뉴에서 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-124">In the drop-down menu, click **Delete**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-modify-or-delete-a-folder"></a><span data-ttu-id="3d326-125">폴더를 수정하거나 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="3d326-125">To modify or delete a folder</span></span>  
  
1.  <span data-ttu-id="3d326-126">보고서 관리자에서 **내용** 페이지로 이동한 다음 수정할 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-126">In Report Manager, navigate to the **Contents** page, and locate the item that you want to modify.</span></span>  
  
2.  <span data-ttu-id="3d326-127">항목 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-127">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="3d326-128">드롭다운 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-128">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="3d326-129">일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-129">The General Properties page opens.</span></span>  
  
4.  <span data-ttu-id="3d326-130">폴더 위치를 변경하려면 **이동**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-130">To change the folder location, click **Move**.</span></span> <span data-ttu-id="3d326-131">대상 폴더의 위치를 입력하거나 트리에서 대상 폴더를 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-131">Type the location of the destination folder, or choose the destination folder from the tree, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="3d326-132">또는 다음과 같은 방법으로 폴더 속성을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-132">Or, modify folder properties in the following ways:</span></span>  
  
    -   <span data-ttu-id="3d326-133">폴더에 대한 표시 텍스트를 수정하려면 이름이나 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-133">To modify display text about the folder, type a name or description.</span></span>  
  
    -   <span data-ttu-id="3d326-134">**내용** 페이지에서 폴더를 기본 보기로 표시하려면 **목록 뷰에서 숨기기**의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-134">To display the folder in the default view on the **Contents** page, clear **Hide in list view**.</span></span>  
  
6.  <span data-ttu-id="3d326-135">또는 폴더 및 해당 내용을 제거하려면 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-135">Or, to remove the folder and its contents, click **Delete**.</span></span>  
  
7.  <span data-ttu-id="3d326-136">**적용**을 클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3d326-136">Click **Apply** to save changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d326-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3d326-137">See Also</span></span>  
 <span data-ttu-id="3d326-138">[새 폴더 페이지 &#40;보고서 관리자&#41;](../new-folder-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="3d326-138">[New Folder Page &#40;Report Manager&#41;](../new-folder-page-report-manager.md) </span></span>  
 <span data-ttu-id="3d326-139">[내용 페이지 &#40;보고서 관리자&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="3d326-139">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 [<span data-ttu-id="3d326-140">보고서 찾기, 보기 및 관리&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3d326-140">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
