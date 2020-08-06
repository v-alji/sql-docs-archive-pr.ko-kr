---
title: 일반 속성 페이지, 폴더 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 31d99d9b-2303-4bae-9466-fb67b97cf11a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb1c3fbf2e9020ac5d1fe5ebbd1e9ed48b45adb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660359"
---
# <a name="general-properties-page-folders-report-manager"></a><span data-ttu-id="76c01-102">일반 속성 페이지, 폴더(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="76c01-102">General Properties Page, Folders (Report Manager)</span></span>
  <span data-ttu-id="76c01-103">폴더의 일반 속성 페이지를 사용하여 만든 폴더의 속성을 보거나 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-103">Use the General properties page for folders to view and set properties for the folders that you create.</span></span> <span data-ttu-id="76c01-104">폴더를 만들거나 수정한 사람 및 폴더를 수정한 시간에 대한 정보가 일반 속성 페이지 맨 위에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-104">Information about who created or modified the folder and when the folder was modified appear at the top of the General properties page.</span></span>  
  
 <span data-ttu-id="76c01-105">폴더 속성에는 보안 설정도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-105">Folder properties also include security settings.</span></span> <span data-ttu-id="76c01-106">폴더 보안에 대 한 자세한 내용은 [폴더](security/secure-folders.md)보안을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="76c01-106">For more information about folder security, see [Secure Folders](security/secure-folders.md).</span></span>  
  
 <span data-ttu-id="76c01-107">특수한 용도의 폴더(예: 홈, 내 보고서 및 사용자 폴더)는 보고서 서버 네임스페이스 내에서 이름을 바꾸거나 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-107">Special-purpose folders such as Home, My Reports, and Users folders cannot be renamed or moved within the report server namespace.</span></span> <span data-ttu-id="76c01-108">이 폴더에 대해서는 일반 속성 페이지를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-108">The General properties page is not available for these folders.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="76c01-109">탐색</span><span class="sxs-lookup"><span data-stu-id="76c01-109">Navigation</span></span>  
 <span data-ttu-id="76c01-110">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="76c01-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-general-properties-page-for-a-folder"></a><span data-ttu-id="76c01-111">폴더의 일반 속성 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="76c01-111">To open the General properties page for a folder</span></span>  
  
1.  <span data-ttu-id="76c01-112">보고서 관리자를 열고 속성을 보거나 구성하려는 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-112">Open Report Manager, and open the folder for which you want to view or configure properties.</span></span>  
  
2.  <span data-ttu-id="76c01-113">폴더 배너 아래의 도구 모음에서 **폴더 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-113">Under the folder banner, in the toolbar, click **Folder Settings**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="76c01-114">옵션</span><span class="sxs-lookup"><span data-stu-id="76c01-114">Options</span></span>  
 <span data-ttu-id="76c01-115">**이름**</span><span class="sxs-lookup"><span data-stu-id="76c01-115">**Name**</span></span>  
 <span data-ttu-id="76c01-116">폴더의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-116">Specify a name for the folder.</span></span> <span data-ttu-id="76c01-117">이름은 하나 이상의 영숫자 문자를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-117">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="76c01-118">공백과 특정 기호도 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-118">It can also include spaces and some symbols.</span></span> <span data-ttu-id="76c01-119">이름을 지정할 때 ; ?</span><span class="sxs-lookup"><span data-stu-id="76c01-119">Do not use the characters ; ?</span></span> <span data-ttu-id="76c01-120">: \@ & = +, $ \* \< > | "로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-120">: \@ & = + , $ \* \< > | " or / when specifying a name.</span></span>  
  
 <span data-ttu-id="76c01-121">**설명**</span><span class="sxs-lookup"><span data-stu-id="76c01-121">**Description**</span></span>  
 <span data-ttu-id="76c01-122">폴더 내용에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-122">Type a description of the folder contents.</span></span> <span data-ttu-id="76c01-123">이 설명은 해당 폴더 액세스 권한이 있는 사용자의 내용 페이지에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-123">This description appears on the Contents page for users who have permission to access the folder.</span></span>  
  
 <span data-ttu-id="76c01-124">**목록 뷰에서 숨기기**</span><span class="sxs-lookup"><span data-stu-id="76c01-124">**Hide in list view**</span></span>  
 <span data-ttu-id="76c01-125">보고서 관리자에서 목록 뷰 모드를 사용하는 사용자가 볼 수 없게 폴더를 숨기려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-125">Select this option to hide the folder from users who are using list view mode in Report Manager.</span></span> <span data-ttu-id="76c01-126">목록 뷰 모드는 보고서 서버 폴더 계층을 검색할 때 표시되는 기본 뷰 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-126">List view mode is the default view format when browsing the report server folder hierarchy.</span></span> <span data-ttu-id="76c01-127">목록 뷰에서 항목 이름과 설명은 페이지에 가로로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-127">In list view, item names and descriptions flow across the page.</span></span> <span data-ttu-id="76c01-128">이 외에도 자세히 보기를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-128">The alternate format is details view.</span></span> <span data-ttu-id="76c01-129">자세히 보기는 설명을 표시하지 않지만 항목에 대한 다른 정보는 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-129">Details view omits descriptions, but includes other information about the item.</span></span> <span data-ttu-id="76c01-130">목록 뷰에서는 항목을 숨길 수 있지만 자세히 보기에서는 항목을 숨길 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-130">Although you can hide an item in list view, you cannot hide an item in details view.</span></span> <span data-ttu-id="76c01-131">항목에 대한 액세스를 제한하려면 역할 할당을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-131">If you want to restrict access to an item, you must create a role assignment.</span></span>  
  
 <span data-ttu-id="76c01-132">**적용**</span><span class="sxs-lookup"><span data-stu-id="76c01-132">**Apply**</span></span>  
 <span data-ttu-id="76c01-133">클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-133">Click to save your changes.</span></span>  
  
 <span data-ttu-id="76c01-134">**삭제**</span><span class="sxs-lookup"><span data-stu-id="76c01-134">**Delete**</span></span>  
 <span data-ttu-id="76c01-135">폴더 및 포함된 내용을 제거하려면 &lt;B&gt;삭제&lt;/B&gt;를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-135">Click to remove the folder and its contents.</span></span>  
  
 <span data-ttu-id="76c01-136">**이동**</span><span class="sxs-lookup"><span data-stu-id="76c01-136">**Move**</span></span>  
 <span data-ttu-id="76c01-137">보고서 서버 네임스페이스 내에서 보고서나 폴더의 위치를 다시 지정하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-137">Click to relocate a report or folder within the report server namespace.</span></span> <span data-ttu-id="76c01-138">이 단추를 클릭하면 폴더를 검색하여 새 폴더 위치를 찾을 수 있는 항목 이동 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="76c01-138">Clicking this button opens the Move Items page that allows you to browse folders for a new folder location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76c01-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76c01-139">See Also</span></span>  
 <span data-ttu-id="76c01-140">[보고서 관리자&#40;SSRS 기본 모드&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="76c01-140">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="76c01-141">보고서 관리자 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="76c01-141">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
