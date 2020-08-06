---
title: 종속 항목 페이지 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4dcfb311-e9c3-4c5d-b2e0-018d79f37d2e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 488b10d7d7985972274340897ee3975618a12639
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647529"
---
# <a name="dependent-items-page-report-manager"></a><span data-ttu-id="d0df1-102">종속 항목 페이지(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="d0df1-102">Dependent Items Page (Report Manager)</span></span>
  <span data-ttu-id="d0df1-103">종속 항목 페이지를 사용하여 공유 데이터 원본을 참조하는 보고서 및 모델 목록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-103">Use the Dependent Items page to view a list of reports and models that reference a shared data source.</span></span> <span data-ttu-id="d0df1-104">각 항목 유형에 대한 아이콘을 통해 보고서인지 또는 모델인지 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-104">The icon for each item type indicates whether it is a report or a model.</span></span> <span data-ttu-id="d0df1-105">이 페이지는 목록 뷰 또는 자세히 보기로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-105">This page can be viewed in list view or details view.</span></span> <span data-ttu-id="d0df1-106">각 항목에 대해 보다 자세한 정보를 표시하려면 자세히 보기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-106">Use details view to show more information about each item.</span></span> <span data-ttu-id="d0df1-107">자세히 보기에서는 추가 페이지 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-107">Additional page options are available in details view.</span></span> <span data-ttu-id="d0df1-108">이 페이지는 공유 데이터 원본 관리를 지원하기 위해 해당 데이터 원본을 사용하는 보고서 및 모델에 대한 링크, 보고서 또는 모델이 마지막으로 실행 또는 수정된 시점에 대한 메트릭, 그리고 삭제 및 이동 단추를 제공하므로 더 이상 사용되지 않는 보고서 및 모델을 손쉽게 제거하거나 아직 필요한지 여부를 판단할 동안 다른 위치로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-108">To help you manage the shared data source, this page provides links to reports and models that use the data source, metrics on when the report or model was last run or modified, and Delete and Move buttons so that you can easily remove reports and models that are no longer used, or move them to a different location while you determine whether they are still needed.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="d0df1-109">탐색</span><span class="sxs-lookup"><span data-stu-id="d0df1-109">Navigation</span></span>  
 <span data-ttu-id="d0df1-110">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0df1-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-dependent-items-page"></a><span data-ttu-id="d0df1-111">종속 항목 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="d0df1-111">To open the Dependent Items page</span></span>  
  
1.  <span data-ttu-id="d0df1-112">보고서 관리자를 열고 종속 항목을 보려는 공유 데이터 원본을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-112">Open Report Manager, and locate the shared data source for which you want to view dependent items.</span></span>  
  
2.  <span data-ttu-id="d0df1-113">항목 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-113">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="d0df1-114">드롭다운 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-114">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="d0df1-115">데이터 원본의 일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-115">This opens the General properties page for the data source.</span></span>  
  
4.  <span data-ttu-id="d0df1-116">**종속 항목** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-116">Select the **Dependent Items** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d0df1-117">옵션</span><span class="sxs-lookup"><span data-stu-id="d0df1-117">Options</span></span>  
 <span data-ttu-id="d0df1-118">**이름**</span><span class="sxs-lookup"><span data-stu-id="d0df1-118">**Name**</span></span>  
 <span data-ttu-id="d0df1-119">보고서 또는 모델의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-119">Shows the name of the report or model.</span></span> <span data-ttu-id="d0df1-120">보고서를 열려면 보고서 이름을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0df1-120">Click the name of the report to open it.</span></span> <span data-ttu-id="d0df1-121">해당 속성 페이지를 열려면 모델 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-121">Click the name of the model to open its property pages.</span></span>  
  
 <span data-ttu-id="d0df1-122">**설명**</span><span class="sxs-lookup"><span data-stu-id="d0df1-122">**Description**</span></span>  
 <span data-ttu-id="d0df1-123">보고서 또는 모델에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-123">Shows the description of the report or model.</span></span>  
  
 <span data-ttu-id="d0df1-124">**삭제**</span><span class="sxs-lookup"><span data-stu-id="d0df1-124">**Delete**</span></span>  
 <span data-ttu-id="d0df1-125">보고서 서버 데이터베이스에서 보고서나 모델을 삭제하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-125">Click to delete the report or model from the report server database.</span></span> <span data-ttu-id="d0df1-126">**삭제**를 클릭하기 전에 삭제할 각 항목 옆의 확인란을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0df1-126">Before clicking **Delete**, select the check box next to each item that you want to delete.</span></span>  
  
 <span data-ttu-id="d0df1-127">**이동**</span><span class="sxs-lookup"><span data-stu-id="d0df1-127">**Move**</span></span>  
 <span data-ttu-id="d0df1-128">폴더 계층 구조에서 보고서나 모델의 위치를 다시 지정하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-128">Click to relocate a report or model within the folder hierarchy.</span></span> <span data-ttu-id="d0df1-129">**이동**을 클릭하기 전에 이동할 각 항목 옆의 확인란을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0df1-129">Before clicking **Move**, select the check box next to each item that you want to move.</span></span> <span data-ttu-id="d0df1-130">이렇게 하면 폴더를 이동하여 새 위치를 선택할 수 있는 항목 이동 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-130">This opens the Move Items page, where you can browse through folders to select a new location.</span></span>  
  
 <span data-ttu-id="d0df1-131">**편집**</span><span class="sxs-lookup"><span data-stu-id="d0df1-131">**Edit**</span></span>  
 <span data-ttu-id="d0df1-132">보고서 또는 모델의 속성 페이지에 액세스하려면 속성 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-132">Click the Property icon to access the property pages of a report, or model.</span></span>  
  
 <span data-ttu-id="d0df1-133">**형식**</span><span class="sxs-lookup"><span data-stu-id="d0df1-133">**Type**</span></span>  
 <span data-ttu-id="d0df1-134">해당 항목 유형의 아이콘을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-134">Shows the icon of the item type.</span></span>  
  
 <span data-ttu-id="d0df1-135">**수정한 날짜**</span><span class="sxs-lookup"><span data-stu-id="d0df1-135">**Modified Date**</span></span>  
 <span data-ttu-id="d0df1-136">보고서 또는 모델을 마지막으로 수정한 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-136">Shows the date and time when the report or model was last modified.</span></span>  
  
 <span data-ttu-id="d0df1-137">**수정한 사람**</span><span class="sxs-lookup"><span data-stu-id="d0df1-137">**Modified By**</span></span>  
 <span data-ttu-id="d0df1-138">해당 항목 속성을 마지막으로 수정한 사람의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-138">Shows the name of the user who last modified the item properties.</span></span>  
  
 <span data-ttu-id="d0df1-139">**실행 날짜**</span><span class="sxs-lookup"><span data-stu-id="d0df1-139">**When Run**</span></span>  
 <span data-ttu-id="d0df1-140">보고서 실행 스냅샷으로 실행되는 보고서의 경우 보고서를 마지막으로 새로 고친 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d0df1-140">For reports that run as report execution snapshots, displays the date and time at which the report was last refreshed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0df1-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d0df1-141">See Also</span></span>  
 <span data-ttu-id="d0df1-142">[F1 도움말 보고서 관리자](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="d0df1-142">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="d0df1-143">[보고서 관리자&#40;SSRS 기본 모드&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="d0df1-143">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="d0df1-144">[내용 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="d0df1-144">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 [<span data-ttu-id="d0df1-145">보고서 관리자 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="d0df1-145">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
