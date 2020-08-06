---
title: 항목 위치 선택 페이지 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4a53a1a8-d1e1-47ef-b1fc-63352ece7d3c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 82c044731552033ddd7fc0d8150cf83f300c7d9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729144"
---
# <a name="choose-item-location-page-report-manager"></a><span data-ttu-id="068ea-102">항목 위치 선택 페이지(Report Manager)</span><span class="sxs-lookup"><span data-stu-id="068ea-102">Choose Item Location Page (Report Manager)</span></span>
  <span data-ttu-id="068ea-103">항목 위치 선택 페이지를 사용하여 새 링크된 보고서 또는 새 모델의 폴더를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-103">Use the Choose Item Location page to select a folder for a new linked report or a new model.</span></span> <span data-ttu-id="068ea-104">특정 사용자 그룹에 대해 링크된 보고서 또는 모델을 만드는 경우 이 사용자 그룹이 사용하는 다른 보고서 및 모델이 포함된 폴더에 이 항목을 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-104">If you are creating a linked report or a model for a specific group of users, you may want to place the item in a folder that contains other reports and models they use.</span></span> <span data-ttu-id="068ea-105">이미 존재하는 폴더 중에서 내용 추가 권한이 있는 폴더를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-105">You must choose a folder that already exists and for which you have permission to add contents.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="068ea-106">탐색</span><span class="sxs-lookup"><span data-stu-id="068ea-106">Navigation</span></span>  
 <span data-ttu-id="068ea-107">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="068ea-107">Use the following procedures to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-choose-item-location-page-for-a-report"></a><span data-ttu-id="068ea-108">보고서의 항목 위치 선택 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="068ea-108">To open the Choose Item Location page for a report</span></span>  
  
1.  <span data-ttu-id="068ea-109">보고서 관리자를 열고 링크된 보고서를 추가할 보고서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-109">Open Report Manager, and locate the report for which you want to add a linked report.</span></span>  
  
2.  <span data-ttu-id="068ea-110">보고서 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-110">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="068ea-111">드롭다운 메뉴에서 다음 단계 중 하나를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="068ea-111">In the drop-down menu, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="068ea-112">새 링크된 보고서 페이지를 열려면 **링크된 보고서 만들기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-112">Click **Create Linked Report** to open the New Linked Report page.</span></span>  
  
    -   <span data-ttu-id="068ea-113">**관리** 를 클릭하여 보고서의 일반 속성 페이지를 연 다음</span><span class="sxs-lookup"><span data-stu-id="068ea-113">Click **Manage** to open the General properties page for the report.</span></span> <span data-ttu-id="068ea-114">**링크된 보고서 만들기** 를 클릭하여 새 링크된 보고서 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-114">Then click **Create Linked Report** to open the New Linked Report page.</span></span>  
  
4.  <span data-ttu-id="068ea-115">속성 페이지의 **일반** 탭에서 **위치 변경** 을 클릭하여 항목 위치 선택 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-115">On the **General** tab, on the properties page, click **Change Location** to open the Choose Item Location page.</span></span>  
  
###### <a name="to-open-the-choose-item-location-page-for-a-model"></a><span data-ttu-id="068ea-116">모델의 항목 위치 선택 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="068ea-116">To open the Choose Item Location page for a model</span></span>  
  
1.  <span data-ttu-id="068ea-117">보고서 관리자를 열고 모델을 추가할 데이터 원본을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-117">Open Report Manager, and locate the data source for which you want to add a model.</span></span>  
  
2.  <span data-ttu-id="068ea-118">데이터 원본 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-118">Hover over the data source, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="068ea-119">드롭다운 메뉴에서 다음 단계 중 하나를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="068ea-119">In the drop-down menu, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="068ea-120">**보고서 모델 생성** 을 클릭하여 새 모델 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-120">Click **Generate Report Model** to open the New Model page.</span></span>  
  
    -   <span data-ttu-id="068ea-121">**관리** 를 클릭하여 데이터 원본의 일반 속성 페이지를 연 다음</span><span class="sxs-lookup"><span data-stu-id="068ea-121">Click **Manage** to open the General properties page for the data source.</span></span> <span data-ttu-id="068ea-122">**모델 생성** 을 클릭하여 새 모델 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-122">Then click **Generate Model** to open the New Model page.</span></span>  
  
4.  <span data-ttu-id="068ea-123">속성 페이지의 **일반** 탭에서 **위치 변경** 을 클릭하여 항목 위치 선택 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-123">On the **General** tab, on the properties page, click **Change Location** to open the Choose Item Location page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="068ea-124">옵션</span><span class="sxs-lookup"><span data-stu-id="068ea-124">Options</span></span>  
 <span data-ttu-id="068ea-125">**위치**</span><span class="sxs-lookup"><span data-stu-id="068ea-125">**Location**</span></span>  
 <span data-ttu-id="068ea-126">항목을 만들어서 넣을 폴더의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-126">Specify the name of the folder to contain the item you are creating.</span></span> <span data-ttu-id="068ea-127">전체 이름을 입력할 수도 있고 트리 보기를 사용하여 사용할 폴더로 이동할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-127">You can type the full name or use the tree view to navigate to the folder you want to use.</span></span>  
  
 <span data-ttu-id="068ea-128">**트리 보기**</span><span class="sxs-lookup"><span data-stu-id="068ea-128">**Tree view**</span></span>  
 <span data-ttu-id="068ea-129">보고서 서버 네임스페이스의 폴더 구조를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-129">Shows the folder structure of report server namespace.</span></span> <span data-ttu-id="068ea-130">전체 경로를 **위치** 필드에 추가하려면 폴더 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-130">Click a folder name to add the full path to the **Location** field.</span></span>  
  
 <span data-ttu-id="068ea-131">트리 뷰에서 확장(+) 및 축소(-) 아이콘을 클릭하면 **위치** 필드에 폴더 이름을 추가하지 않아도 폴더를 열고 닫을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-131">Click the expand (+) and collapse (-) icons in the tree view to open and close folders without adding the folder names to the **Location** field.</span></span> <span data-ttu-id="068ea-132">**위치** 필드에 폴더 이름을 추가하려면 폴더의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="068ea-132">To add a folder name to the **Location** field, click the name of the folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="068ea-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="068ea-133">See Also</span></span>  
 <span data-ttu-id="068ea-134">[새 링크 된 보고서 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/new-linked-report-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="068ea-134">[New Linked Report Page &#40;Report Manager&#41;](../../2014/reporting-services/new-linked-report-page-report-manager.md) </span></span>  
 <span data-ttu-id="068ea-135">[새 모델 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/new-model-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="068ea-135">[New Model Page &#40;Report Manager&#41;](../../2014/reporting-services/new-model-page-report-manager.md) </span></span>  
 [<span data-ttu-id="068ea-136">보고서 관리자 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="068ea-136">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
