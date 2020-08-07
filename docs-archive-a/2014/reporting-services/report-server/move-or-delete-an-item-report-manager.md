---
title: 항목 이동 또는 삭제(보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- moving items
- items [Reporting Services], moving
ms.assetid: 980a66c7-a18b-4af7-8954-45726fa517d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3a61ad56ea9e20e7fdf38d5acf05529b685ee896
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727924"
---
# <a name="move-or-delete-an-item-report-manager"></a><span data-ttu-id="719ad-102">항목 이동 또는 삭제(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="719ad-102">Move or Delete an Item (Report Manager)</span></span>
  <span data-ttu-id="719ad-103">보고서 서버에 게시하는 보고서 및 보고서 관련 항목은 폴더에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-103">Reports and report-related items that you publish to a report server are stored in folders.</span></span> <span data-ttu-id="719ad-104">항목을 다른 폴더로 이동할 수 있으며 해당 항목에 대한 참조는 보고서 서버에서 자동으로 유지 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-104">You can move items to a different folder and references to those items are maintained automatically by the report server.</span></span> <span data-ttu-id="719ad-105">항목을 삭제하기 전에 해당 항목에 다른 항목이 종속되어 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="719ad-105">Before you delete an item, consider whether other items depend on it.</span></span>  
  
## <a name="move-an-item"></a><span data-ttu-id="719ad-106">항목 이동</span><span class="sxs-lookup"><span data-stu-id="719ad-106">Move an Item</span></span>  
 <span data-ttu-id="719ad-107">보고서 서버 항목을 보고서 서버 폴더 계층의 다른 폴더 위치로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-107">You can move report server items to different folder locations in the report server folder hierarchy.</span></span> <span data-ttu-id="719ad-108">항목을 이동하면 모든 속성(보안 설정 포함)도 항목과 함께 새 위치로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-108">When you move an item, all properties (including security settings) move with the item to the new location.</span></span> <span data-ttu-id="719ad-109">폴더를 이동하면 폴더 내의 모든 항목이 함께 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-109">When you move a folder, all the items in the folder move with it.</span></span>  
  
 <span data-ttu-id="719ad-110">보고서 관리자에서 이동할 수 있는 항목은 폴더 계층 구조에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-110">In Report Manager, the items that you can move are indicated in the folder hierarchy.</span></span> <span data-ttu-id="719ad-111">다음 표에서는 이동 가능한 각 항목의 아이콘을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-111">The following table shows the icon for each movable item.</span></span>  
  
|<span data-ttu-id="719ad-112">아이콘</span><span class="sxs-lookup"><span data-stu-id="719ad-112">Icon</span></span>|<span data-ttu-id="719ad-113">이동 가능한 항목</span><span class="sxs-lookup"><span data-stu-id="719ad-113">Moveable item</span></span>|  
|----------|-------------------|  
|<span data-ttu-id="719ad-114">![Report icon](../media/hlp-16doc.gif "보고서 아이콘")</span><span class="sxs-lookup"><span data-stu-id="719ad-114">![Report icon](../media/hlp-16doc.gif "Report icon")</span></span>|<span data-ttu-id="719ad-115">보고서</span><span class="sxs-lookup"><span data-stu-id="719ad-115">Report</span></span>|  
|<span data-ttu-id="719ad-116">![링크된 보고서 아이콘](../media/hlp-16linked.gif "링크된 보고서 아이콘")</span><span class="sxs-lookup"><span data-stu-id="719ad-116">![Linked report icon](../media/hlp-16linked.gif "Linked report icon")</span></span>|<span data-ttu-id="719ad-117">링크된 보고서</span><span class="sxs-lookup"><span data-stu-id="719ad-117">Linked report</span></span>|  
|<span data-ttu-id="719ad-118">![폴더 아이콘](../media/hlp-16folder.gif "폴더 아이콘")</span><span class="sxs-lookup"><span data-stu-id="719ad-118">![Folder icon](../media/hlp-16folder.gif "Folder icon")</span></span>|<span data-ttu-id="719ad-119">폴더</span><span class="sxs-lookup"><span data-stu-id="719ad-119">Folder</span></span>|  
|<span data-ttu-id="719ad-120">![일반 리소스 아이콘](../media/hlp-16file.gif "일반 리소스 아이콘")</span><span class="sxs-lookup"><span data-stu-id="719ad-120">![generic resource icon](../media/hlp-16file.gif "generic resource icon")</span></span>|<span data-ttu-id="719ad-121">일반 리소스</span><span class="sxs-lookup"><span data-stu-id="719ad-121">Generic resource</span></span>|  
|<span data-ttu-id="719ad-122">![Shared data source icon](../media/hlp-16datasource.png "공유 데이터 원본 아이콘")</span><span class="sxs-lookup"><span data-stu-id="719ad-122">![Shared data source icon](../media/hlp-16datasource.png "Shared data source icon")</span></span>|<span data-ttu-id="719ad-123">공유 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="719ad-123">Shared data source</span></span>|  
||<span data-ttu-id="719ad-124">공유 데이터 세트</span><span class="sxs-lookup"><span data-stu-id="719ad-124">Shared dataset</span></span>|  
  
 <span data-ttu-id="719ad-125">작업하는 모든 항목을 이동할 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-125">Not all items that you work with can be moved.</span></span> <span data-ttu-id="719ad-126">구독이나 보고서 기록과 같이 보고서와 연결된 항목은 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-126">You cannot move items that are associated with a report, such as subscriptions or report history.</span></span> <span data-ttu-id="719ad-127">이러한 항목은 연결된 보고서와 함께 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-127">Those items move with their associated reports.</span></span> <span data-ttu-id="719ad-128">마찬가지로 공유 일정과 같이 폴더 계층 밖에 있는 항목도 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-128">Similarly, you cannot move items, such as shared schedules, that exist outside of the folder hierarchy.</span></span> <span data-ttu-id="719ad-129">항목 이동 권한이 없으면 항목을 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-129">You cannot move items if you lack permission to do so.</span></span> <span data-ttu-id="719ad-130">항목 이동 권한은 해당 항목에 대한 역할 할당에서 "보고서 관리," "모델 관리," "폴더 관리" 및 "데이터 원본 관리" 태스크를 선택한 경우에만 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-130">Permission to move an item is conveyed when the following tasks are selected in your role assignment for the item in question: "Manage reports," "Manage models", "Manage folders," and "Manage data sources."</span></span>  
  
#### <a name="to-move-an-item-from-within-the-contents-page"></a><span data-ttu-id="719ad-131">내용 페이지에서 항목을 이동하려면</span><span class="sxs-lookup"><span data-stu-id="719ad-131">To move an item from within the Contents page</span></span>  
  
1.  <span data-ttu-id="719ad-132">[보고서 관리자 &#40;SSRS 기본 모드&#41;]를 시작 합니다. /report-manager-ssrs-native-mode.md).</span><span class="sxs-lookup"><span data-stu-id="719ad-132">Start [Report Manager  &#40;SSRS Native Mode&#41;]../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="719ad-133">보고서 관리자에서 **내용** 페이지로 이동한 다음 이동할 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-133">In Report Manager, navigate to the **Contents** page, and locate the item that you want to move.</span></span>  
  
3.  <span data-ttu-id="719ad-134">항목 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-134">Hover over the item, and click the drop-down arrow.</span></span>  
  
4.  <span data-ttu-id="719ad-135">드롭다운 메뉴에서 **이동**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-135">In the drop-down menu, click **Move**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="719ad-136">**위치**에서 항목을 이동할 폴더를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-136">For **Location**, specify the folder you want to move the item to.</span></span> <span data-ttu-id="719ad-137">정규화된 폴더 이름을 입력하거나 트리 컨트롤을 사용하여 해당 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-137">You can type the fully qualified folder name or use the tree control to navigate to the folder.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="719ad-138">또는 이동할 개체로 이동하고 **속성**을 클릭한 후 페이지 맨 위에서 **이동** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-138">Alternatively, you can navigate to the object you want to move, click **Properties**, and then click **Move** at the top of the page.</span></span>  
  
## <a name="delete-an-item"></a><span data-ttu-id="719ad-139">항목 삭제</span><span class="sxs-lookup"><span data-stu-id="719ad-139">Delete an item</span></span>  
 <span data-ttu-id="719ad-140">항목을 삭제하기 전에 해당 항목이 다른 항목에 사용되고 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="719ad-140">Before you delete an item, determine if it is used by other items.</span></span> <span data-ttu-id="719ad-141">예를 들어 공유 데이터 원본을 삭제하는 경우 해당 데이터 원본을 사용하는 보고서와 모델이 더 이상 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-141">For example, if you delete a shared data source, reports and models that use that data source will no longer run.</span></span> <span data-ttu-id="719ad-142">보고서를 삭제하는 경우 해당 보고서와 관련된 구독 및 보고서 기록도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-142">If you delete a report, subscriptions and report history associated with that report are also deleted.</span></span> <span data-ttu-id="719ad-143">항목에 대 한 종속 항목을 찾으려면 [종속 항목 페이지 &#40;보고서 관리자&#41;]를 참조 하세요. /dependent-items-page-report-manager.md).</span><span class="sxs-lookup"><span data-stu-id="719ad-143">To find dependent items for an item, see [Dependent Items Page &#40;Report Manager&#41;]../dependent-items-page-report-manager.md).</span></span>  
  
#### <a name="to-delete-a-report-or-item"></a><span data-ttu-id="719ad-144">보고서 또는 항목을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="719ad-144">To delete a report or item</span></span>  
  
1.  <span data-ttu-id="719ad-145">[보고서 관리자 &#40;SSRS 기본 모드&#41;]를 시작 합니다. /report-manager-ssrs-native-mode.md).</span><span class="sxs-lookup"><span data-stu-id="719ad-145">Start [Report Manager  &#40;SSRS Native Mode&#41;]../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="719ad-146">보고서 관리자에서 **내용** 페이지로 이동한 다음 삭제할 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-146">In Report Manager, navigate to the **Contents** page, and locate the item that you want to delete.</span></span>  
  
3.  <span data-ttu-id="719ad-147">항목 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-147">Hover over the item, and click the drop-down arrow.</span></span>  
  
4.  <span data-ttu-id="719ad-148">드롭다운 메뉴에서 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="719ad-148">In the drop-down menu, click **Delete**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="719ad-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="719ad-149">See Also</span></span>  
 <span data-ttu-id="719ad-150">[내용 페이지 &#40;보고서 관리자&#41;]. /contents-page-report-manager.md)</span><span class="sxs-lookup"><span data-stu-id="719ad-150">[Contents Page &#40;Report Manager&#41;]../contents-page-report-manager.md)</span></span>   
 [<span data-ttu-id="719ad-151">보고서 찾기, 보기 및 관리&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="719ad-151">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
