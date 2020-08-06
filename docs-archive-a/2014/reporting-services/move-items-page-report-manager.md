---
title: 항목 이동 페이지 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fc83b8d2-bc79-4b56-8970-34a1cbbcc176
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 98ff306caf634a5f0478e2eba03c2313b24be274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739526"
---
# <a name="move-items-page-report-manager"></a><span data-ttu-id="0d51d-102">항목 이동 페이지(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="0d51d-102">Move Items Page (Report Manager)</span></span>
  <span data-ttu-id="0d51d-103">항목 이동 페이지를 사용하여 보고서, 폴더 또는 기타 항목을 보고서 서버의 새 위치로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-103">Use the Move Items page to move a report, folder, or other item to a new location on the report server.</span></span> <span data-ttu-id="0d51d-104">새 위치의 경로를 입력하거나 트리 뷰를 사용하여 보고서 서버 네임스페이스에서 새 위치를 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-104">You can type the path of the new location or use a tree view to browse to a new location in the report server namespace.</span></span> <span data-ttu-id="0d51d-105">현재 보고서 서버에 저장되어 있고 이동 권한 있는 항목만 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-105">You can only move items that you have permission to move and that are stored on the current report server.</span></span>  
  
 <span data-ttu-id="0d51d-106">다른 항목에서 참조하는 항목(예: 많은 보고서가 참조하는 공유 데이터 원본 또는 모델)을 이동할 때는 해당 항목에 대한 경로 정보가 자동으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-106">When you move an item that is referenced by another item (for example, a shared data source or model that is referenced by many reports), the path information for that item is updated automatically.</span></span> <span data-ttu-id="0d51d-107">공유 데이터 원본을 이동해도 이를 사용하는 보고서 및 모델에 대한 데이터 원본 연결은 끊어지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-107">Moving a shared data source does not disrupt a data source connection to the reports and models that use it.</span></span> <span data-ttu-id="0d51d-108">사용자에게 사용 권한이 없는 폴더로 공유 데이터 원본 또는 모델을 이동하는 경우 사용자는 이를 참조하는 보고서를 계속 실행할 수 있지만 폴더 계층 구조에서 이러한 항목을 볼 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-108">If you move a shared data source or model to a folder for which users do not have permission, they will still be able to run any report that references the data source or model, however the item will not be visible to them in the folder hierarchy.</span></span>  
  
 <span data-ttu-id="0d51d-109">**위치**에 루트 폴더 이름으로 시작하는 전체 폴더 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-109">For **Location**, specify the full path to folder, beginning with the root folder name.</span></span> <span data-ttu-id="0d51d-110">경로 이름을 입력하거나 트리 뷰를 사용하여 원하는 폴더로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-110">You can type the path name or use the tree view to navigate to the folder you want.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d51d-111">모든 항목을 이동할 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-111">Not all items are movable.</span></span> <span data-ttu-id="0d51d-112">홈, 내 보고서, 사용자 폴더와 같이 예약된 폴더는 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-112">You cannot move reserved folders such as Home, My Reports, or Users Folders.</span></span> <span data-ttu-id="0d51d-113">보고서 기록이나 스냅샷은 다른 위치로 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-113">You cannot move report history or snapshots to different locations.</span></span> <span data-ttu-id="0d51d-114">기록 및 스냅샷은 항상 기반이 되는 보고서와 함께 저장되며 이 보고서를 통해 액세스됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-114">History and snapshots are always located with, and accessed through, the report on which they are based.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="0d51d-115">탐색</span><span class="sxs-lookup"><span data-stu-id="0d51d-115">Navigation</span></span>  
 <span data-ttu-id="0d51d-116">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="0d51d-116">Use the following procedures to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-move-items-page-from-the-contents-page-in-details-view"></a><span data-ttu-id="0d51d-117">자세히 보기의 내용 페이지에서 항목 이동 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="0d51d-117">To open the Move Items page from the Contents page in Details View</span></span>  
  
1.  <span data-ttu-id="0d51d-118">보고서 관리자를 열고 이동할 항목이 있는 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-118">Open Report Manager, and navigate to the folder that contains an item you want to move.</span></span> <span data-ttu-id="0d51d-119">보고서 관리자 홈 페이지에서 항목을 이동할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-119">You can also move items from the Report Manager Home page.</span></span>  
  
2.  <span data-ttu-id="0d51d-120">도구 모음에서 **자세히 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-120">In the toolbar, click **Details View**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0d51d-121">**바둑판식 배열 보기**만 표시된다면 이미 **자세히 보기**상태인 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-121">If you see only **Tiles View**, you are already in **Details View**.</span></span>  
  
3.  <span data-ttu-id="0d51d-122">항목 옆의 확인란을 선택한 다음 도구 모음에서 **이동** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-122">Select the box next to an item, and then click **Move** in the toolbar.</span></span> <span data-ttu-id="0d51d-123">항목 여러 개를 동일한 새 위치로 이동하려는 경우 확인란 여러 개를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-123">You can select more than one box if you want to move multiple items to the same new location.</span></span>  
  
###### <a name="to-open-the-move-items-page-from-the-contents-page-in-tiles-view"></a><span data-ttu-id="0d51d-124">바둑판식 배열 보기의 내용 페이지에서 항목 이동 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="0d51d-124">To open the Move Items page from the Contents page in Tiles View</span></span>  
  
1.  <span data-ttu-id="0d51d-125">보고서 관리자를 열고 이동할 항목이 있는 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-125">Open Report Manager, and navigate to the folder that contains an item you want to move.</span></span> <span data-ttu-id="0d51d-126">보고서 관리자 홈 페이지에서 항목을 이동할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-126">You can also move items from the Report Manager Home page.</span></span>  
  
2.  <span data-ttu-id="0d51d-127">도구 모음에서 **바둑판식 배열 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-127">In the toolbar, click **Tiles View**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0d51d-128">**자세히 보기**만 표시된다면 이미 **바둑판식 배열 보기**상태인 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-128">If you see only **Details View**, you are already in **Tiles View**.</span></span>  
  
3.  <span data-ttu-id="0d51d-129">항목 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-129">Hover over an item, and click the drop-down arrow.</span></span>  
  
4.  <span data-ttu-id="0d51d-130">드롭다운 메뉴에서 **이동**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-130">In the drop-down menu, click **Move**.</span></span>  
  
###### <a name="to-open-the-move-items-page-from-the-general-properties-page-of-an-item"></a><span data-ttu-id="0d51d-131">항목의 일반 속성 페이지에서 항목 이동 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="0d51d-131">To open the Move Items page from the General Properties page of an item</span></span>  
  
1.  <span data-ttu-id="0d51d-132">보고서 관리자를 열고 이동할 항목이 있는 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-132">Open Report Manager, and navigate to the folder that contains an item you want to move.</span></span> <span data-ttu-id="0d51d-133">보고서 관리자 홈 페이지에서 항목을 이동할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-133">You can also move items from the Report Manager Home page.</span></span>  
  
2.  <span data-ttu-id="0d51d-134">항목 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-134">Hover over an item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="0d51d-135">드롭다운 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-135">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="0d51d-136">항목의 일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-136">This opens the General properties page for an item.</span></span>  
  
4.  <span data-ttu-id="0d51d-137">항목 도구 모음에서 **이동**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0d51d-137">In the item toolbar, click **Move**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d51d-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0d51d-138">See Also</span></span>  
 <span data-ttu-id="0d51d-139">[보고서 관리자&#40;SSRS 기본 모드&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="0d51d-139">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="0d51d-140">[일반 속성 페이지, 폴더 &#40;보고서 관리자&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="0d51d-140">[General Properties Page, Folders &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md) </span></span>  
 <span data-ttu-id="0d51d-141">[일반 속성 페이지, 보고서 &#40;보고서 관리자&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="0d51d-141">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 <span data-ttu-id="0d51d-142">[일반 속성 페이지, 리소스 &#40;보고서 관리자&#41;](../../2014/reporting-services/general-properties-page-resources-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="0d51d-142">[General Properties Page, Resources &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-resources-report-manager.md) </span></span>  
 <span data-ttu-id="0d51d-143">[일반 속성 페이지, 공유 데이터 원본 &#40;보고서 관리자&#41;](../../2014/reporting-services/general-properties-page-shared-data-sources-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="0d51d-143">[General Properties Page, Shared Data Sources &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-shared-data-sources-report-manager.md) </span></span>  
 [<span data-ttu-id="0d51d-144">보고서 관리자 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="0d51d-144">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
