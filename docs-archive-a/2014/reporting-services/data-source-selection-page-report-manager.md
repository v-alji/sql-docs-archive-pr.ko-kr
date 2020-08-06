---
title: 데이터 원본 선택 페이지 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7f7e8b19-0c0b-4b1f-9cc1-057099aa07eb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 03c5558397786b02b764b78d47584d9b190290cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652632"
---
# <a name="data-source-selection-page-report-manager"></a><span data-ttu-id="125c4-102">데이터 원본 선택 페이지(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="125c4-102">Data Source Selection Page (Report Manager)</span></span>
  <span data-ttu-id="125c4-103">데이터 원본 선택 페이지를 사용하여 보고서나 보고서 모델에서 사용할 기존의 공유 데이터 원본 항목을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="125c4-103">Use the Data Source Selection page to select an existing shared data source item to use with a report or a report model.</span></span> <span data-ttu-id="125c4-104">다른 데이터 원본을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="125c4-104">You can also use this page to select a different data source.</span></span> <span data-ttu-id="125c4-105">데이터 원본 유형 또는 연결 문자열을 보려면 공유 데이터 원본을 탐색하고 속성 페이지를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="125c4-105">To view the data source type or connection string, you must navigate to the shared data source and open the property pages.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="125c4-106">탐색</span><span class="sxs-lookup"><span data-stu-id="125c4-106">Navigation</span></span>  
 <span data-ttu-id="125c4-107">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="125c4-107">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-data-source-selection-page"></a><span data-ttu-id="125c4-108">데이터 원본 선택 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="125c4-108">To open the Data Source Selection page</span></span>  
  
1.  <span data-ttu-id="125c4-109">보고서 관리자를 열고 데이터 원본을 선택할 보고서나 모델을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="125c4-109">Open Report Manager, and locate the report or model for which you want to select a data source.</span></span>  
  
2.  <span data-ttu-id="125c4-110">보고서 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="125c4-110">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="125c4-111">드롭다운 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="125c4-111">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="125c4-112">보고서나 모델의 일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="125c4-112">This opens the General properties page for the report or model.</span></span>  
  
4.  <span data-ttu-id="125c4-113">**데이터 원본** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="125c4-113">Select the **Data Sources** tab.</span></span>  
  
5.  <span data-ttu-id="125c4-114">속성 창에서 **공유 데이터 원본** 을 선택한 다음 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="125c4-114">In the properties pane, select **A shared data source** and then click **Browse**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="125c4-115">옵션</span><span class="sxs-lookup"><span data-stu-id="125c4-115">Options</span></span>  
 <span data-ttu-id="125c4-116">**위치**</span><span class="sxs-lookup"><span data-stu-id="125c4-116">**Location**</span></span>  
 <span data-ttu-id="125c4-117">공유 데이터 원본 항목에 루트 폴더 이름으로 시작하는 전체 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="125c4-117">Specify the full path to the shared data source item, beginning with the root folder name.</span></span> <span data-ttu-id="125c4-118">경로 이름을 입력하거나 트리 보기를 사용하여 원하는 공유 데이터 원본으로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="125c4-118">You can type the path name or use the tree view to navigate to the shared data source you want.</span></span>  
  
 <span data-ttu-id="125c4-119">**트리 보기**</span><span class="sxs-lookup"><span data-stu-id="125c4-119">**Tree view**</span></span>  
 <span data-ttu-id="125c4-120">보고서 서버 네임스페이스의 폴더 구조를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="125c4-120">Shows the folder structure of the report server namespace.</span></span> <span data-ttu-id="125c4-121">공유 데이터 원본 항목을 클릭하여 전체 경로를 **위치** 필드에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="125c4-121">Click a shared data source item to add the full path to the **Location** field.</span></span>  
  
 <span data-ttu-id="125c4-122">**확인**</span><span class="sxs-lookup"><span data-stu-id="125c4-122">**OK**</span></span>  
 <span data-ttu-id="125c4-123">데이터 원본 선택 항목을 데이터 원본 속성 페이지에 복사하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="125c4-123">Click to copy the data source selection to the Data Sources properties page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="125c4-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="125c4-124">See Also</span></span>  
 <span data-ttu-id="125c4-125">[보고서 데이터 원본 관리](report-data/manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="125c4-125">[Manage Report Data Sources](report-data/manage-report-data-sources.md) </span></span>  
 <span data-ttu-id="125c4-126">[보고서 데이터 원본에 대한 자격 증명 및 연결 정보 지정](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="125c4-126">[Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span></span>  
 <span data-ttu-id="125c4-127">[데이터 원본 속성 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="125c4-127">[Data Sources Properties Page &#40;Report Manager&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md) </span></span>  
 <span data-ttu-id="125c4-128">[새 데이터 원본 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/new-data-source-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="125c4-128">[New Data Source Page &#40;Report Manager&#41;](../../2014/reporting-services/new-data-source-page-report-manager.md) </span></span>  
 [<span data-ttu-id="125c4-129">보고서 관리자 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="125c4-129">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
